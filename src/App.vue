<template>
  <div id="app">
    <NavigationBar />
    <Menu />
    <div id="view">
      <keep-alive>
        <router-view></router-view>
      </keep-alive>
    </div>
    <FooterBar />
  </div>
</template>

<script>
// import { mapMutations } from "vuex";
import NavigationBar from '@/components/base/NavigationBar.vue';
import FooterBar from '@/components/base/FooterBar.vue';
import Menu from '@/components/base/Menu.vue';

export default {
  name: 'App',
  components: { NavigationBar, Menu, FooterBar },
  data: () => ({}),
  mounted() {
    // 100vh #app solution for mobile devices
    // https://stackoverflow.com/a/53883824
    let vh = window.innerHeight * 0.01;
    document.documentElement.style.setProperty('--vh', `${vh}px`);
    window.addEventListener('resize', () => {
      let vh = window.innerHeight * 0.01;
      document.documentElement.style.setProperty('--vh', `${vh}px`);
    });
  },
  methods: {
    // ...mapMutations({
    //   setWidth: "set_width",
    // }),
  },
};
</script>

<style>
:root {
  --bg-main: #ffffff;
  --bg-scnd: #f2f2f2;
  --bg-third: #fafafa;
  --bg-alt: #191919;
  --txt-main: #191919;
  --txt-accent: #959595;
  --txt-accent-dark: #696969;
  --txt-main-od: #ffffff; /* on dark */
  --accent: #0057ff;
}
body {
  margin: 0px;
  padding: 0px;
}
#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  cursor: default;
  /* height: calc(var(--vh, 1vh) * 100); */
  display: grid;
  grid-auto-rows: auto 1fr;
  overflow: auto;
  height: auto;
}
#view {
  grid-row: 2;
  grid-column: 1;
  padding: 60px 0px;
}

button,
a {
  cursor: pointer;
  transition: color 0.1s;
  text-decoration: none;
}
a:visited {
  color: var(--txt-accent);
}
</style>
