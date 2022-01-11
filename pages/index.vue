<template>
  <div>
    <button
      type="button"
      name="button"
      @click="getMsg"
    >
      RailsからAPIを取得する
    </button>
    <div v-for="(blog, i) in blogs" :key="i">
      タイトル：{{ blog.title }}
      本文：{{ blog.body }}
    </div>
  </div>
</template>

<script lang="ts">
export type DataType = {
  blogs: string[];
}

export default {
  data(): DataType {
    return {
      blogs: []
    }
  },
  methods: {
    getMsg () {
      this.$axios.$get('/api/v1/blogs')
        .then((res) => {
          console.log(res)
          this.blogs = res
        })
    }
  }
}
</script>
