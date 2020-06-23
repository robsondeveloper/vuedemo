<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p v-for="{ id, name } in products" :key="id">{{ id }} {{ name }}</p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      products: []
    }
  },
  created() {
    axios
      .get('http://localhost:8181/products')
      .then(response => (this.products = response.data))
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
