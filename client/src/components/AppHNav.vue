<template>
  <!-- #### h-nav Code #### -->
  <nav id="h-nav" class="clearfix">
    <ul>
      <li><router-link to="/">Home</router-link></li>
      <li>
        <router-link to="../category"
          >Book Categories <font-awesome-icon icon="fa-solid fa-angle-down"
        /></router-link>
        <ul>
          <li
            v-for="category in $store.state.categories"
            :key="category.categoryId"
          >
            <router-link :to="'../category/' + category.name">{{
              category.name.replace(":", ": ")
            }}</router-link>
          </li>
        </ul>
      </li>
      <li><router-link to="../contact">Contact Us</router-link></li>
    </ul>
    <app-h-nav-right></app-h-nav-right>
  </nav>
  <!-- #### End h-nav Code #### -->
</template>

<script>
import AppHNavRight from "@/components/AppHNavRight";
export default {
  name: "AppHNav",
  components: { AppHNavRight },
};
</script>

<style scoped>
nav {
  width: 100%;
  height: 35px;
  background-color: var(--LightShade);
  border-bottom: 1px #000 solid;
}

nav a {
  color: #000;
}

nav ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

nav ul li {
  padding-left: 15px;
  padding-right: 15px;
  float: left;
  display: block;
  position: relative;
}

nav ul li ul li {
  background-color: var(--LightShade);
}

nav ul li a,
nav ul li ul li a {
  display: block;
  text-decoration: none;
  text-align: left;
  padding-top: 8px;
  padding-bottom: 8px;
  border-bottom: 0;
}

nav li:hover,
nav li:focus-within {
  background-color: var(--LightGrey);
  color: #fff;
  cursor: pointer;
}

nav ul li ul {
  visibility: hidden;
  opacity: 0;
  position: absolute;
  transition: all 0.5s ease;
  margin-top: 0;
  left: 0;
  display: none;
}

/*
  Source https://css-tricks.com/solved-with-css-dropdown-menus/
   for accessibilty and tabbing support
*/
nav ul li:hover > ul,
nav ul li:focus-within > ul,
nav ul li ul:hover,
nav ul li ul:focus {
  visibility: visible;
  opacity: 1;
  display: block;
}

nav ul li ul li {
  clear: both;
  width: 100%;
}
</style>
