<template>
<v-app>
  <div>
    <v-alert
      border="top"
      color="red lighten-2"
      dark
    >
      I'm an alert with a top border and red color
    </v-alert>
    <v-alert
      border="right"
      color="blue-grey"
      dark
    >
      I'm an alert with a right border and blue-grey color
    </v-alert>
    <v-alert
      border="bottom"
      color="pink darken-1"
      dark
    >
      I'm an alert with a bottom border and pink color
    </v-alert>
    <v-alert
      border="left"
      color="indigo"
      dark
    >
      I'm an alert with a border left type info
    </v-alert>
  </div>
  <hr>
  <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="374"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      height="250"
      src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
    ></v-img>

    <v-card-title>Cafe Badilico</v-card-title>

    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >
        <v-rating
          :value="4.5"
          color="amber"
          dense
          half-increments
          readonly
          size="14"
        ></v-rating>

        <div class="grey--text ml-4">
          4.5 (413)
        </div>
      </v-row>

      <div class="my-4 subtitle-1">
        $ • Italian, Cafe
      </div>

      <div>Small plates, salads & sandwiches - an intimate setting with 12 indoor seats plus patio seating.</div>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-title>Tonight's availability</v-card-title>

    <v-card-text>
      <v-chip-group
        v-model="selection"
        active-class="deep-purple accent-4 white--text"
        column
      >
        <v-chip>5:30PM</v-chip>

        <v-chip>7:30PM</v-chip>

        <v-chip>8:00PM</v-chip>

        <v-chip>9:00PM</v-chip>
      </v-chip-group>
    </v-card-text>

    <v-card-actions>
      <v-btn
        color="deep-purple lighten-2"
        text
        @click="reserve"
      >
        Reserve
      </v-btn>
    </v-card-actions>
  </v-card>
  <hr>
   <v-carousel :show-arrows="false">
    <v-carousel-item
      v-for="(item,i) in imgitems"
      :key="i"
      :src="item.src"
    ></v-carousel-item>
  </v-carousel> 
  <hr>
   <div class="text-center">
    <v-btn
      v-if="!chip1 && !chip2 && !chip3 && !chip4"
      close
      color="primary"
      dark
      @click="chip1 = true, chip2 = true, chip3 = true, chip4= true"
    >
      Reset Chips
    </v-btn>

    <v-chip
      v-if="chip1"
      class="ma-2"
      close
      @click:close="chip1 = false"
    >
      Closable
    </v-chip>

    <v-chip
      v-if="chip2"
      class="ma-2"
      close
      color="red"
      text-color="white"
      @click:close="chip2 = false"
    >
      Remove
    </v-chip>

    <v-chip
      v-if="chip3"
      class="ma-2"
      close
      color="green"
      outlined
      @click:close="chip3 = false"
    >
      Success
    </v-chip>

    <v-chip
      v-if="chip4"
      class="ma-2"
      close
      color="orange"
      label
      outlined
      @click:close="chip4 = false"
    >
      Complete
    </v-chip>
  </div>
  <hr>
   <v-footer
    dark
    padless
  >
    <v-card
      flat
      tile
      class="indigo lighten-1 white--text text-center"
    >
      <v-card-text>
        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4 white--text"
          icon
        >
          <v-icon size="24px">
            {{ icon }}
          </v-icon>
        </v-btn>
      </v-card-text>

      <v-card-text class="white--text pt-0">
        Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris cursus commodo interdum. Praesent ut risus eget metus luctus accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis commodo vitae velit et faucibus. Morbi vehicula lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text">
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-card-text>
    </v-card>
  </v-footer>
  <hr>
   <div class="text-center">
    <v-progress-circular
      :rotate="360"
      :size="100"
      :width="15"
      :value="value"
      color="teal"
    >
      {{ value }}
    </v-progress-circular>

    <v-progress-circular
      :rotate="-90"
      :size="100"
      :width="15"
      :value="value"
      color="primary"
    >
      {{ value }}
    </v-progress-circular>

    <v-progress-circular
      :rotate="90"
      :size="100"
      :width="15"
      :value="value"
      color="red"
    >
      {{ value }}
    </v-progress-circular>

    <v-progress-circular
      :rotate="180"
      :size="100"
      :width="15"
      :value="value"
      color="pink"
    >
      {{ value }}
    </v-progress-circular>
  </div>
  <hr>
   <v-stepper non-linear>
      <v-stepper-header>
        <v-stepper-step
          editable
          step="1"
        >
          Select campaign settings
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          editable
          step="2"
        >
          Create an ad group
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          step="3"
          editable
        >
          Create an ad
        </v-stepper-step>
      </v-stepper-header>
    </v-stepper>

    <v-stepper
      class="mt-12"
      non-linear
    >
      <v-stepper-header>
        <v-stepper-step
          complete
          editable
          step="1"
        >
          Select campaign settings
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          editable
          step="2"
        >
          Create an ad group
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          complete
          editable
          step="3"
        >
          Create an ad
        </v-stepper-step>
      </v-stepper-header>
    </v-stepper>

    <v-stepper
      class="mt-12"
      non-linear
      value="3"
    >
      <v-stepper-header>
        <v-stepper-step
          complete
          editable
          step="1"
        >
          Select campaign settings
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          complete
          editable
          step="2"
        >
          Create an ad group
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          complete
          editable
          step="3"
        >
          Create an ad
        </v-stepper-step>
      </v-stepper-header>
    </v-stepper>
    <hr>
     <v-card>
    <v-toolbar
      color="deep-purple accent-4"
      dark
      flat
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Page title</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>

      <template v-slot:extension>
        <v-tabs
          v-model="currentItem"
          fixed-tabs
          slider-color="white"
        >
          <v-tab
            v-for="item in items"
            :key="item"
            :href="'#tab-' + item"
          >
            {{ item }}
          </v-tab>

          <v-menu
            v-if="more.length"
            bottom
            left
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                text
                class="align-self-center mr-4"
                v-bind="attrs"
                v-on="on"
              >
                more
                <v-icon right>
                  mdi-menu-down
                </v-icon>
              </v-btn>
            </template>

            <v-list class="grey lighten-3">
              <v-list-item
                v-for="item in more"
                :key="item"
                @click="addItem(item)"
              >
                {{ item }}
              </v-list-item>
            </v-list>
          </v-menu>
        </v-tabs>
      </template>
    </v-toolbar>

    <v-tabs-items v-model="currentItem">
      <v-tab-item
        v-for="item in items.concat(more)"
        :key="item"
        :value="'tab-' + item"
      >
        <v-card flat>
          <v-card-text>
            <h2>{{ item }}</h2>
            {{ text }}
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs-items>
  </v-card>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      loading: false,
      selection: 1,
       imgitems: [
          {
            src: 'https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg',
          },
          {
            src: 'https://cdn.vuetifyjs.com/images/carousel/sky.jpg',
          },
          {
            src: 'https://cdn.vuetifyjs.com/images/carousel/bird.jpg',
          },
          {
            src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg',
          },
        ],
        chip1: true,
        chip2: true,
        chip3: true,
        chip4: true,
        icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
       interval: {},
       value: 0,
       currentItem: 'tab-Web',
      items: [
        'Web', 'Shopping', 'Videos', 'Images',
      ],
      more: [
        'News', 'Maps', 'Books', 'Flights', 'Apps',
      ],
      text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
    }),

    methods: {
      reserve () {
        this.loading = true

        setTimeout(() => (this.loading = false), 2000)
      },
      addItem (item) {
        const removed = this.items.splice(0, 1)
        this.items.push(
          ...this.more.splice(this.more.indexOf(item), 1),
        )
        this.more.push(...removed)
        this.$nextTick(() => { this.currentItem = 'tab-' + item })
      },
    },
    beforeDestroy () {
      clearInterval(this.interval)
    },
    mounted () {
      this.interval = setInterval(() => {
        if (this.value === 100) {
          return (this.value = 0)
        }
        this.value += 10
      }, 1000)
    },
  }
</script>

<style scoped>
.v-progress-circular {
  margin: 1rem;
}
</style>