<template>
  <div>
    <h1>Finished Projects</h1>
    <li v-for="post of posts" :key="post.slug">
      <NuxtLink :to="post.slug">{{ post.title }}</NuxtLink>
    </li>

    <h2>Timeline</h2>
    <li v-for="article of articles" :key="article.slug">
      <NuxtLink :to="article.slug">{{ article.title }}</NuxtLink>
    </li>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content("blog").fetch()
    const articles = await $content("timeline").fetch()

    return {
      posts,
      articles,
    }
  },
}
</script>
