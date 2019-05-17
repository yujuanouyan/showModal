## showModal  

uni-app的跨端显示弹层，接口参数与uni-app 中的showModal参数一致  
~~~
this.$showModal({
  title: '提示',
  content: '这是一个模态弹窗',
  success(res) {
    if (res.confirm) {
      console.log('用户点击确定')
    } else if (res.cancel) {
      console.log('用户点击取消')
    }
  }
})
~~~

如果对您有帮助麻烦点个星星 我会持续更新的~ [gitHub](https://github.com/zxzhgk/showModal)

**注意项**  

1. 依赖于 vuex 如没有安装请先安装vuex
**一个简单的初始化vuex的main.js 内容**

~~~
import Vue from 'vue'
import App from './App'
import Vuex from 'vuex';
Vue.use(Vuex)
Vue.config.productionTip = false

import initModal from "@/components/zhangxu-showModal/initModal.js";
import showModal from '@/components/zhangxu-showModal/show-modal';
initModal(Vue);
Vue.component('show-modal',showModal);

App.mpType = 'app'


const store = new Vuex.Store();
const app = new Vue({
	store,
    ...App
})
app.$mount()
~~~


2. 样式使用scss 请安装或修改 样式为你的预处理语言  


## 使用方式   

在main.js中
~~~
// 注册全局modal组件
import initModal from "@/components/zhangxu-showModal/initModal.js";
import showModal from '@/components/zhangxu-showModal/show-modal';
initModal(Vue);
Vue.component('show-modal',showModal);

~~~

在需要的页面中 （注 需要的页面每个都要引入）  

~~~
<template>
	<div>
		<show-modal></show-modal>
	</div>
</template>
~~~

在函数中（注  此组件在main.js 中全局引入不需要在子组件中再注册组件）  

~~~
this.$showModal({
  title: '提示',
  content: '这是一个模态弹窗',
  success(res) {
    if (res.confirm) {
      console.log('用户点击确定')
    } else if (res.cancel) {
      console.log('用户点击取消')
    }
  }
})

~~~  

## OBJECT参数说明  


| 参数  | 类型 |必填	|说明|
| ------ |------ |------ |------ |
|title|	String|	是|	提示的标题	|
|content|	String|	是	|提示的内容	|
|showCancel|	Boolean|	否|	是否显示取消按钮，默认为 true	|
|cancelText	|String	|否	|取消按钮的文字，默认为"取消"，|
|cancelColor|	HexColor|否|	取消按钮的文字颜色，默认为"#000000"|
|confirmText|	String	|否|确定按钮的文字，默认为"确定"，|
|confirmColor|	HexColor|否|确定按钮的文字颜色|
|success|	Function|	否|	接口调用成功的回调函数	|
|hideTabBar|Boolean|	否|	是否隐藏tabBar在APP和小程序中隐藏tabBar 可以让遮罩层全屏|
	 
## success返回参数说明

|参数	|类型	|说明|
| ------ |------ |------ |
|confirm|	Boolean|	为 true 时，表示用户点击了确定按钮|
|cancel	|Boolean|	为 true 时，表示用户点击了取消|




