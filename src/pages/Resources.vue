<template>
  <Layout :show-logo="true">

    <div class="resources">
      <h1 class="page_title center">
        Resources
      </h1>

      <div id="brands" class="responsive_table_block">

        <div class="functionalities_block">

          <input
          class="search input"
          placeholder="Search (ex: organic)" />

          <button
          class="sort button"
          data-sort="products"
          @click="onClick">
            Sort by Products
          </button>

          <button
          class="sort button"
          data-sort="brand">
            Sort by Brand
          </button>
          
        </div>

        <table class="green_pages_table responsive_table">

          <thead>
            <tr class="green_pages_table_header_row">
              <td class="brand table_header_brand">Brand</td>
              <td class="products table_header_product">Products</td>
              <td class="address hide">Address</td>
              <td class="country hide">Country</td>
              <td class="email"><IcoMail /></td>
              <td class="localphone"><IcoPhone /></td>
              <td class="whatsapp"><IcoWhatsapp /></td>
              <td class="location"><IcoLocation /></td>
              <td class="twitter"><IcoTwitter /></td>
              <td class="youtube"><IcoYoutube /></td>
              <td class="instagram"><IcoInstagram /></td>
              <td class="website"><IcoLink /></td>
            </tr>
          </thead>

          <tbody class="list">
            <tr
              v-for="company in companies"
              :key="company.brand"
              :id="company.brand"
              class="green_pages_table_row"
              itemscope itemtype="http://schema.org/Organization">

              <!--01-->
              <td
              class="brand sortable"
              data-th="Brand"
              itemprop="brand">{{ company.brand }}</td>

              <!--02-->
              <td
              class="products sortable"
              data-th="Products"
              itemscope itemtype="http://schema.org/Product">
              {{ company.products }}</td>

              <!--03-->
              <td
              class="address show_on_phones 1024 sortable"
              data-th="Address"
              itemscope itemtype="http://schema.org/PostalAddress">
              {{ company.address }}</td>

              <!--04-->
              <td
              class="country show_on_phones 1024 sortable"
              data-th="Country"
              itemprop="addressLocality">
              {{ company.country }}</td>





              <!--05-->
              <td
              class="icon_only email"
              itemprop="email">
                <a
                  v-if="company.email"
                  class="sober_link"
                  title="email"
                  target="_blank"
                  :href="`mailto:${company.email}`">
                  <IcoMail />
                </a>
              </td>

              <!--06-->
              <td
              class="icon_only telephone"
              itemprop="telephone">
                <a
                  v-if="company.telephone"
                  class="sober_link"
                  target="_blank"
                  :title="`tel:+${company.telephone}`"
                  :href="`tel:+${company.telephone}`">
                  <IcoPhone />
                </a>
              </td>

              <!--07-->
              <td
              class="icon_only whatsapp"
              itemprop="whatsapp">
                <a
                  v-if="company.whatsapp"
                  class="sober_link"
                  target="_blank"
                  :title="`tel:+${company.whatsapp}`"
                  :href="`https:\/\/wa\.me/${company.whatsapp}`">
                  <IcoWhatsapp />
                </a>
              </td>

              <!--08-->
              <td
              class="icon_only location"
              itemprop="location">
                <a
                  v-if="company.location"
                  class="sober_link"
                  title="location"
                  target="_blank"
                  :href="`${company.location}`">
                  <IcoLocation />
                </a>
              </td>

              <!--09-->
              <td
              class="icon_only twitter"
              itemprop="twitter">
                <a
                  v-if="company.twitter"
                  title="twitter"
                  class="sober_link"
                  target="_blank"
                  :href="`https:\/\/twitter\.com\/${company.twitter}`">
                  <IcoTwitter />
                </a>
              </td>

              <!--10-->
              <td
              class="icon_only youtube"
              itemprop="youtube">
                <a
                  v-if="company.youtube"
                  title="twitter"
                  class="sober_link"
                  target="_blank"
                  :href="`https:\/\/youtube\.com\/${company.youtube}`">
                  <IcoYoutube />
                </a>
              </td>

              <!--11-->
              <td
              class="icon_only instagram"
              itemprop="instagram">
                <a
                  v-if="company.instagram"
                  title="instagram"
                  class="sober_link"
                  target="_blank"
                  :href="`https:\/\/instagram\.com\/${company.instagram}`">
                  <IcoInstagram />
                </a>
              </td>

              <!--12-->
              <td
              class="icon_only website"
              itemprop="website">
                <a
                  v-if="company.website"
                  title="website"
                  class="sober_link"
                  target="_blank"
                  :href="`${company.website}`">
                  <IcoLink />
                </a>
              </td>

            </tr>
          </tbody>

        </table>

      </div>
    </div>


  </Layout>
</template>

<page-query>
  query {
    links: allPost(filter: { published: { eq: true }}) {
      edges {
        node {
          id
          title
          ad
          path
        }
      }
    }
    posts: allPost {
  		edges {
  			node {
  				id
  				title
  				...on Post {
  				id
  				title
  				path
  				}
  			}
  		}
  	}
  }
</page-query>

<script>
import companies from '~/assets/data/companies.yml'
import IcoMail from '~/assets/svgs/email.svg'
import IcoPhone from '~/assets/svgs/localphone.svg'
import IcoLink from '~/assets/svgs/link.svg'
import IcoLocation from '~/assets/svgs/location.svg'
import IcoInstagram from '~/assets/svgs/instagram.svg'
import IcoTwitter from '~/assets/svgs/twitter.svg'
import IcoYoutube from '~/assets/svgs/youtube.svg'
import IcoWhatsapp from '~/assets/svgs/whatsapp.svg'

export default {
  components: {
    IcoMail,
    IcoPhone,
    IcoLink,
    IcoLocation,
    IcoInstagram,
    IcoTwitter,
    IcoYoutube,
    IcoWhatsapp,
    companies
  },
  data() {
    return {
      companies
    }
  },
  methods: {
    onClick () {
      this.message = 'Here you go :)'
    }
  },
  metaInfo () {
    return {
      meta: [
        {
          key: 'og:title',
          property: 'og:title',
          content: 'Resources | MagicGreen'
        },
        {
          key: "twitter:title",
          name: "twitter:title",
          content: 'Resources | MagicGreen'
        },
        {
          key: 'description',
          name: 'description',
          content: 'To solve big problems we need resources. These organisations are doing the right thing and can help. Make a wise choice and support them.'        }
      ],
      bodyAttrs: {
          class: 'resources'
      }
    }
  }
}
</script>

<style lang="scss" scoped >
  svg {
    stroke: var(--title_color);
  }

  .page_title {
  	@media screen and (min-width: 900px) {
  		display: none;
  	}
  }

  //search
  .functionalities_block {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    -ms-flex-direction: column;
    flex-direction: column;
    @media screen and (min-width: 900px) {
      -webkit-box-orient: horizontal;
      -webkit-box-direction: normal;
      -ms-flex-direction: row;
      flex-direction: row;
      -webkit-box-pack: center;
      -ms-flex-pack: center;
      justify-content: center;
    }
  }

  .sort:after {
    display: inline-block;
    width: 0;
    height: 0;
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-bottom: 5px solid transparent;
    content: "";
    position: relative;
    top: -10px;
    right: -3px;
  }

  .sort.asc:after {
    width: 0;
    height: 0;
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-top: 5px solid var(--black);
    content: "";
    position: relative;
    top: 4px;
    right: -3px;
  }

  .sort.desc:after {
    width: 0;
    height: 0;
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-bottom: 5px solid var(--black);
    content: "";
    position: relative;
    top: -4px;
    right: -3px;
  }

  .hide_on_phones {
    display: none!important;
    @media screen and (min-width: 900px) {
      display: table-cell;
    }
  }
</style>
