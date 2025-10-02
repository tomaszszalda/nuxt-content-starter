<script setup lang="ts">
const route = useRoute()
console.log("LAYER")
const { data: page } = await useAsyncData(  () => {
  
  return queryCollection('content').path('/'+route.params.slug[0]).first()
})
console.log("LAYER", page.value, route.params.slug[0])
// if (!page.value) {
//   throw createError({ statusCode: 404, statusMessage: 'Page not found', fatal: true })
// }
</script>

<template>
  <ContentRenderer
    v-if="page"
    :value="page"
  />
</template>
