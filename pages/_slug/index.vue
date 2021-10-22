<template>
  <main class="main">
    <h1 class="title">
      {{ title }}
    </h1>
    <p class="publishedAt">
      {{ publishedAt }}
    </p>
    <img style="width: 100%;" :src="mainVisual.url" alt="">
    <div class="post" v-html="content"></div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData ({ params }) {
    const { data } = await axios.get(
      `https://sugoi-app.microcms.io/api/v1/blog/${params.slug}`,
      {
        headers: { 'X-MICROCMS-API-KEY': '42f5893e-86cb-40c5-b836-aa625fb08b95' }
      }
    )
    return data
  }

}

</script>
