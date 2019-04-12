最近一个月的时间，工作上的事情特别多，要同时开发维护三四个项目，让人觉得有些憔悴，也没有时间去学习了，正好今天要聚餐，趁着下午的时间，把之前没有写完的Mint UI教程继续写一写。

接着上一篇：Vue移动端框架Mint UI教程-搭建环境引入框架（一）：https://www.jianshu.com/p/874e5152b3c5
开始来写代码：

1：在components里面新建一个vue文件，将底部的Tab抽取出来成为一个组件使用。
![](https://upload-images.jianshu.io/upload_images/5640239-b842505cf389900c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



2：app.vue代码
打开app.vue，引入组件，写相关代码
```
<script>
  import Footer from './components/FooterBar.vue'
  export default {
    name: 'app',
    components: {
      'footer-bar': Footer
    },
    computed: {}
  }
</script>
```

![](https://upload-images.jianshu.io/upload_images/5640239-7d98ecb6f6dfc3f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)





3：在pages里面新建三个页面
接下来就是编写三个tabbar对应的 路由出口界面，并且配置到路由对象中。（main.vue,my.vue,tool.vue）
![](https://upload-images.jianshu.io/upload_images/5640239-668bd444b6b8b300.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




4：打开index.js文件
将这三个界面配置到router文件夹下的index.js中去：
```
import Vue from 'vue'
import Router from 'vue-router'
import Main from '../pages/main.vue'
import Tool from '../pages/tool.vue'

import My from '../pages/my.vue'

Vue.use(Router);

export default new Router({
  routes: [
    {
      path: "/", component: Main
    },
    {
      path: '/main', component: Main
    }, {
      path: '/tool', component: Tool
    }, {
      path: '/my', component: My
    }
  ]
})

```
![](https://upload-images.jianshu.io/upload_images/5640239-199553fd69845ea7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


5：接着我们修改项目的main.js文件，将路由和其他组件也都引入进来使用。
没有则不需要
```
// The Vue build version to load with the `import` command
// (runtime-only or standalone) has been set in webpack.base.conf with an alias.
import Vue from 'vue'
import App from './App'
import router from './router'
import Mint from 'mint-ui'
import 'mint-ui/lib/style.css'
Vue.config.productionTip = false

// 引入全部组件 

Vue.use(Mint);

/* eslint-disable no-new */
new Vue({
	el: '#app',
	router,
	components: { App },
	template: '<App/>'
})
```
![](https://upload-images.jianshu.io/upload_images/5640239-e9ebf3026a5790d5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6：代码写好之后，来查看一下效果，嗯，底部导航栏完成
![](https://upload-images.jianshu.io/upload_images/5640239-e93e2a1319fd7fbb.gif?imageMogr2/auto-orient/strip)

github链接：

