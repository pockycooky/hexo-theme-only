<template lang="html">
  <div>
    <only-container v-if="themeCfg.page404 == null">
      <h1>404 Not Found</h1>
      <h3> 迷路了么？这里什么也不存在 </h3>
      <p> 回到 <router-link
        :to="{name: 'Splash'}"
      >最开始的地方吧</router-link> </p>
      <img src="https://as.bitinn.net/upload/cite0l5z200oiz35nbv8t5xox.1200.jpg" alt="">
    </only-container>
    <only-page v-else layout="page404" />
  </div>
</template>

<script>
import Container from '@/components/Container'
import Page from '@/views/Page'
import { mapGetters } from 'vuex'

export default {
  created () {
    if (this.$route.query.redirect) {
      this.$router.replace(this.$route.query.redirect)
    }
  },
  components: {
    'only-container': Container,
    'only-page': Page
  },
  computed: {
    ...mapGetters(['themeCfg'])
  },
  watch: {
    '$route.path' (to, from) {
      this.$store.commit('updateStatus', 200)
    }
  }
}
</script>

<style lang="css">
</style>
