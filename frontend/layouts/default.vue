<template>
  <div id="app">
    <v-app>
      <v-toolbar app dark>
        <v-toolbar-title>Todo list app</v-toolbar-title>
        <v-spacer />
        <div v-if="isLoggedIn()">
          {{ $auth.user.email }}
          <v-btn icon nuxt @click="logout">
            <v-icon>exit_to_app</v-icon>
          </v-btn>
        </div>
        <v-btn icon nuxt to="/">
          <v-icon>home</v-icon>
        </v-btn>
      </v-toolbar>
      <v-content>
        <div :style="{ backgroundImage: `url(${backgroundUrl})` }" class="body-image" />
        <v-container fluid fill-height class="body-content" >
          <nuxt />
        </v-container>
      </v-content>
    </v-app>
  </div>
</template>

<script>
import { loginMixin } from '~/mixins/global'
import backgroundUrl from '~/assets/bg.jpeg'

export default {
  mixins: [loginMixin],
  data() {
    return {
      backgroundUrl
    }
  },
  methods: {
    logout () {
      this.$auth.logout()
    }
  }
}
</script>

<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

.body-image {
    filter: blur(8px);
    -webkit-filter: blur(8px);
    height: 100%; 
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}

.body-content {
  background-color: rgba(0,0,0, 0.4);
  color: white;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  padding: 20px;
  text-align: center;
}
</style>
