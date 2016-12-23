<template lang="html">
  <div id="TalionNav">
    <header class="TalionNav">
      <div class="TalionNav-primary">
        <nav>
          <ul>
            <li><a href="#/movies" style="color:#2384e8;">电影</a></li>
          </ul>
          <span class="search"></span>
        </nav>
      </header>
      <div class="search">
        <input type="text" class="search-input" v-model.trim="query" @key.enter="search()" name="search" placeholder="请输入搜索内容">
        <img src="../assets/search-btn.png" class="search-btn" @click="search()" alt="">
      </div>
    </div>
</div>
</template>

<script>
export default {
  data(){
    return{
      query:'',
      placeholder:'',
      path:'search-movie'
    }
  },
  mounted(){
    if(this.$route.path === 'index' || this.$route.path.indexOf('movie')){
      this.$path = '/movie/search'
    }else if (this.$route.path.indexOf('book')) {
      this.path = '/book/search'
    }
  },
  method:{
    search(){
      this.$router.push({path:this.path,query:{query:this.query}})
      this.query = ''
    }
  }
}
</script>

<style lang="scss" scoped>
  .search{
    position: relative;
    margin-top: 48px;
    background-color: #fff;
    .search-input{
      -webkit-appearance:none;
      border: 0;
      outline: 0;
      background-color: #f5f5f5;
      padding: 10px 5px;
      width: 100%;
    }
    .search-btn{
      position: absolute;
      right: 5px;
      top: 10px;
      width: 20px;
    }
  }
  .TalionNav{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 100;
    background-color: #fff;
    a{
      text-decoration: none;
    }
    .TalionNav-primary{
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid #f3f3f3;
      padding: 0 20px;
      box-shadow: 0 2px 4px rgba(0, 0, 0, .2),inset 1px 2px 4px rgba(0,0,0,.4);
      box-sizing: border-box;
      min-height: 48px;
      line-height: 48px;
      & > a{
        font-size: 0;
      }
      & > *{
        white-space: nowrap;
      }
      & > *,nav li{
        display: inline-block;
      }
      nav li{
        font-size: 16px;
        margin-right: 20px;
      }
      nav > *{
        vertical-align: middle;
      }
      h1{
        margin: 0;
        padding: 0;
        color: #00b600;
        font-size: 0;
        background-size: cover;
        height: 22px;
        width: 46px;
        display: inline-block;
      }
      .search{
        position: relative;
        font-size: 0;
        background-size: cover;
        width: 24.57143px;
        height: 18.28571px;
        margin-top: 4px;
      }
    }
    ul,li{
      margin: 0;
      padding: 0;
      list-style: none;
    }
  }
</style>
