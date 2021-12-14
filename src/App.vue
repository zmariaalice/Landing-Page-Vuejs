<template>
  <v-app id="inspire">
    <v-app-bar app flat dark class="ma-3">
      <v-container class="py-0 fill-height">
        <v-icon v-for="link in teste" :key="link" text class="mr-6">
          {{ link }}
        </v-icon>

        <v-spacer></v-spacer>
        <div class="right">
        <img src="https://static.todamateria.com.br/upload/ba/nd/bandeira_americana_bb.jpg" class="mr-10" color="grey darken-1" size="32" style="height: 1rem" alt="">
        <p class="mr-10" color="grey darken-1" size="32">English</p>
        <v-icon>mdi-white-balance-sunny</v-icon>
        <v-icon>mdi-magnify</v-icon>
        <v-icon>mdi-bell-outline</v-icon>
        <div class="name">
          <p>John snow</p>
          <p>King of the North</p>
        </div>
        <v-avatar class="mr-10" color="grey darken-1" size="32"></v-avatar>
      </div>
      </v-container>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app dark>
      <v-sheet class="pa-4">
        <div class="text-h5 pb-3 deep-purple--text">ASSSSS</div>
        <v-icon class="pr-3">mdi-home</v-icon>
        <span>Dashboards</span>
      </v-sheet>

      <v-sheet class="pl-4 pt-4"> APPS & PAGES </v-sheet>
      <v-list>
        <v-list-item
          v-for="([icon, text], index) in links"
          :key="index"
          link
          v-bind:class="{ selected: index === 7 }"
        >
          <v-list-item-icon>
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-navigation-drawer class="v-main" app right>
        <v-container>
          <v-row>
            <template v-for="recent in recents">
              <v-col :key="recent" class="mt-2" cols="12" style="display: flex">
                <v-img width="90" :src="recent.imageUrl"></v-img>
                <v-container>
                  <strong class="white--text">{{ recent.title }}</strong>
                  <p class="white--text">{{ recent.date }}</p>
                </v-container>
              </v-col>
            </template>
          </v-row>
        </v-container>
      </v-navigation-drawer>

      <v-sheet class="pa-4 white--text" style="background-color: transparent">
        <div class="text-h5 pb-3">Blog List</div>
      </v-sheet>
      <v-row>
        <v-col class="py-8 px-6" fluid v-for="card in cards" :key="card">
          <template>
            <v-card max-width="374" dark>
              <template slot="progress">
                <v-progress-linear
                  color="deep-purple"
                  height="10"
                  indeterminate
                ></v-progress-linear>
              </template>

              <v-img height="250" :src="card.imageUrl"></v-img>

              <v-card-title>{{ card.title }}</v-card-title>

              <v-card-text>
                <v-chip-group
                  v-model="selection"
                  active-class="deep-purple accent-4 white--text"
                  column
                  v-for="tag in card.tags"
                  :key="tag"
                >
                  <v-chip>{{ tag }}</v-chip>
                </v-chip-group>
              </v-card-text>

              <v-card-text>

                <div>
                  {{ card.descript }}
                </div>
              </v-card-text>
            </v-card>
          </template>
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    links: [
      ["mdi-email", "Email"],
      ["mdi-message", "Chat"],
      ["mdi-format-list-checks", "Todo"],
      ["mdi-calendar", "Calendar"],
      ["mdi-file-multiple", "Invoice"],
      ["mdi-cart-outline", "eCommerce"],
      ["mdi-account", "User"],
      ["mdi-file-star-outline", "Pages"],
    ],
    tags: [{ name: "Quote", color: "#4e96ac", backgroundcolor: "#4e96ac" }],
    teste: [
      "mdi-calendar",
      "mdi-message",
      "mdi-email",
      "mdi-format-list-checks",
      "mdi-star",
    ],

    cards: [
      {
        title: "The Best Features Coming to iOS and Web design",
        author: "Chani Pradita",
        tags: ["Quote", "Fashion"],
        descript:
          "Donut fruitcake soufflé apple pie candy canes jujubes croissant...",
        imageUrl:
          "https://images.pexels.com/photos/7932264/pexels-photo-7932264.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      },
      {
        title: "Latest Quirky Opening Sentence or Paragraph",
        author: "Jorge Griffin",
        tags: ["Gaming", "Video"],
        descript:
          "Apple pie caramels lemon drops halvah liquorice carrot cake...",
        imageUrl:
          "https://images.pexels.com/photos/8960464/pexels-photo-8960464.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940",
      },
    ],
    recents: [
      {
        title: "Why Should Forget Facebook",
        date: "Jan 14 2020",
        imageUrl:
          "https://images.unsplash.com/photo-1481349518771-20055b2a7b24?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8M3x8cmFuZG9tfGVufDB8fDB8fA%3D%3D&w=1000&q=80",
      },
      {
        title: "Why Should Forget Facebook",
        date: "Jan 14 2020",
        imageUrl:
          "https://images.unsplash.com/photo-1481349518771-20055b2a7b24?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8M3x8cmFuZG9tfGVufDB8fDB8fA%3D%3D&w=1000&q=80",
      },
      {
        title: "Why Should Forget Facebook",
        date: "Jan 14 2020",
        imageUrl:
          "https://images.unsplash.com/photo-1481349518771-20055b2a7b24?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8M3x8cmFuZG9tfGVufDB8fDB8fA%3D%3D&w=1000&q=80",
      },
      {
        title: "Why Should Forget Facebook",
        date: "Jan 14 2020",
        imageUrl:
          "https://images.unsplash.com/photo-1481349518771-20055b2a7b24?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8M3x8cmFuZG9tfGVufDB8fDB8fA%3D%3D&w=1000&q=80",
      },
      {
        title: "Why Should Forget Facebook",
        date: "Jan 14 2020",
        imageUrl:
          "https://images.unsplash.com/photo-1481349518771-20055b2a7b24?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8M3x8cmFuZG9tfGVufDB8fDB8fA%3D%3D&w=1000&q=80",
      },
    ],
  }),
};
</script>

<style lang="scss">
.v-main {
  background-color: #161d30;
}

.v-navigation-drawer__content,
.theme--dark.v-sheet {
  background-color: #292f45 !important;
}

.v-card__text {
  display: flex;
}

  .selected{
    .theme--dark.v-icon{
      color: gray !important;
    }
    background-color: white !important;
    color: gray !important;
  }

  .name{
    >p{
      margin: 0 !important;
    }
  }

  .right{
    display: flex;
    align-items: center;
    justify-content: space-around;
    width: 34rem;
  }

.selected {
  .theme--dark.v-icon {
    color: gray !important;
  }
  background-color: white !important;
  color: gray !important;
}
</style>
