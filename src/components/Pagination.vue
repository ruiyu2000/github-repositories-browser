<template>
  <ul>
    <li v-for="page in pages" :key="page">
      <a :href="'/'+page" >{{page}}</a>
    </li>
  </ul>
</template>


<script>
export default {
  name: 'pagination',
  props: ['length', 'pagination'],

  computed: {
    pages () {
      let pages = []
      pages.push(1)
      if (this.pagination.page > 3) {
        for (let i = this.pagination.page - 2; i < this.pagination.page + 3; i++) {
          pages.push(i)
        }
      }
      pages.push(this.length / this.pagination.rowsPerPage)

      let res = pages.filter(function(item, pos, self) {
        return self.indexOf(item) == pos
      })

      return res
    }
  },
}
</script>


<style lang="scss" scoped>

</style>