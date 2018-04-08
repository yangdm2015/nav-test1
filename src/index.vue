<template>
  <div class="wrapper">
    <image :src="logo" class="logo"/>
    <text class="greeting">The environment is ready!</text>
    <wxc-button text="Open Popup"
                @wxcButtonClicked="bc">
    </wxc-button>
    <HelloWorld/>
  </div>
</template>

<script>
  var navigator = weex.requireModule('navigator')
  const modal = weex.requireModule('modal')
  import { WxcButton, WxcPopup } from 'weex-ui';
  import HelloWorld from './components/HelloWorld.vue'
  export default {
    name: 'App',
    components: {
      HelloWorld, WxcButton
    },
    data () {
      return {
        logo: 'https://gw.alicdn.com/tfs/TB1yopEdgoQMeJjy1XaXXcSsFXa-640-302.png'
      }
    },
    methods: {
      bc(){
        let toUrl = weex.config.bundleUrl.split('/').slice(0, -1).join('/') + '/'+'components/na1.js'
        console.log('toUrl = ',toUrl)
//        modal.alert({
//          message: toUrl,
//          duration: 0.3
//        })
        navigator.push({
          url: toUrl,
          animated: "true"
        })
      }
    }
  }
</script>

<style scoped>
  .wrapper {
    justify-content: center;
    align-items: center;
  }

  .logo {
    width: 424px;
    height: 200px;
  }

  .greeting {
    text-align: center;
    margin-top: 70px;
    font-size: 50px;
    color: #41B883;
  }

  .message {
    margin: 30px;
    font-size: 32px;
    color: #727272;
  }
</style>
