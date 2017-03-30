<template>
  <div class="searchResult">
    <h1>{{ msg }}</h1>
    <h2>{{ bbb }}</h2>
    <li v-for="item in list">
      {{ item.name }}
    </li>
  </div>
</template>


<script>
  import axios from 'axios'
  export default {
    name: 'searchResult',
    data () {
      return {
        msg: 'Search Result',
        bbb: '',
        list: []
      }
    },
    mounted: function () {
      this.aaa()
    },
    methods: {
      aaa: function () {
        console.log('aaaaa')
        axios.get('http://localhost:9004/search?keyword=Cap&price=&color=&brand=&type=', {
        })
          .then((response) => {
            console.log(response)
            this.bbb = response.data.keyword
            this.list = response.data.results
          })
          .catch(function (error) {
            console.log(error)
          })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
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
