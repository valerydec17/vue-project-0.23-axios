<template>
  <div id="app">
    <ul v-if="posts && posts.length">
      <li v-for="(post, index) in posts" :key="index">
        <p><strong>{{ post.title }}</strong></p>
        <p>{{ post.body }}</p>
      </li>
    </ul>
    <ul v-if="errors && errors.length">
      <li v-for="(error, index) in errors" :key="index">
        {{ error.message }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data: () => ({
    posts: [],
    errors: [],
  }),
  methods: {
  },
  created() {
    axios
      .get(`http://jsonplaceholder.typicode.com/posts`)
      .then((response) => {
        this.posts = response.data;
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>

<style>
</style>
