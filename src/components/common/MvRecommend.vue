<template>
  <div class="mv-recommend-component" >
    <div @click="goToMvPlayer" class="mv-recommend-detail" >
      <img class="mv-recommend-detail-cover" :src="mv.picUrl">
      <div class="mv-listen-count font-size-10">
      <i class="mv-recommend-detail-listen-icon background"></i>{{ mv.playCount | transformNumberCount }}</div>
    </div>
    <div class="mv-recommend-message">
      <h4 class="mv-recommend-name text-ellipsis">{{ mv.name }}</h4>
      <p class="mv-recommend-singer font-size-10 text-ellipsis">{{ mv.artists | transformArtistList }}</p>
    </div>
  </div>
</template>

<script>
  export default{
    props: {
      mv: {
        type: Object,
        required: true
      }
    },
    data () {
      return {
        componentWidth: 0, //  当前组件宽度
        componentHeight: 0 //  当前组件高度
      }
    },
    computed: {
      phoneResolutionWidth () {
        return this.$store.state.phoneResolutionWidth
      }
    },
    methods: {
      goToMvPlayer () { //  跳转到MV播放界面
        this.$router.push({
          name: 'mvPlayer',
          params: {
            id: this.mv.id
          }
        })
      }
    }
  }
</script>


<style scoped>
  .mv-recommend-component {
    margin-bottom: .0625rem;
    height: 2.3rem;
  }
  .mv-recommend-component img{
    width: 100%;
  }
  .mv-recommend-detail {
    position: relative;
  }
  .mv-recommend-detail-cover {
    width: 100%;
    height: 100%;
  }
  .mv-recommend-detail-listen {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height:100%;
    justify-content: flex-end;
    align-items: center;
  }
  .mv-recommend-detail-listen-icon {
    display:block;
    float:left;
    width: 0.3rem;
    height: 0.2rem;
    background-image: url('../../../static/images/index/y_.png');
  }
  .mv-listen-count {  
    color: #fff;
    position:absolute;right:.1rem;top:.1rem;
  }
  .mv-recommend-name,
  .mv-recommend-singer
  {
    padding: 0 0.375rem;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .mv-recommend-singer {
    color: #797a7b;
  }
</style>