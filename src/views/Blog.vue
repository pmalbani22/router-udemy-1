<template>
  <Titulo texto="Título de mi blog"/>
  <button @click="consumirApi">Consumir API</button>
  <div v-for="item in arrayBlog" :key="item.id">
      <router-link>
            {{ item.title }} - 
      </router-link>
  </div>
</template>

<script>
import Titulo from '@/components/Titulo'

export default {
  data() {
    return {
        arrayBlog : []
    }
  },
    components: {
        Titulo
    },
    methods: {
        async consumirApi(){
          try {
            const data = await fetch('https://jsonplaceholder.typicode.com/posts')
            const array = await data.json()
            console.log(array)
            this.arrayBlog = array

          } catch (error) {
              console.log(error)
          }
        }
    },
    created() {
        this.consumirApi()
    }

}
</script>

<style>

</style>