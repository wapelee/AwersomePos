# awesome_pos

> 快餐店 POS 系统

第 2 节：Vue-cli 搭建开发环境搭建项目架构：

项目采用 Webpack+Vue-router 的架构方式，开始安装（全部在 windows 系统上操作，我也没有 mac 电脑）。

按 Win+R，然后在文本框中输入 cmd，回车打开命令行，输入 vue-cli 安装命令：

mpm install vue-cli -g

这里的-g 代表全局安装。在命令行中初始化项目，我们采用的是 webpack 模板，输入初始化命令：

vue init webpack AwesomePos

这里的 AwesmonePos 是我的项目文件夹名称，你可以起一个自己喜欢的名称。安装时根据项目需要配置所需要的模块。这里有一个小技巧，就是在你已经提前建立好了文件夹的时候，我们也进入了文件夹，这时候我们可以省略这个文件夹名称。如下情况：

mikdir AwesomePos
cd AwesomePos
vue init webpack
在命令行中，进入项目目录，使用 npm install 安装 package.json 里项目的依赖包。如果你网速较慢的话，可以使用淘宝镜像的 cnpm 来进行安装。查看是否安装正确。在命令行中输入 npm run dev ，如果能在浏览器中正常打开页面，说明安装正确。到这里为止，我们的项目架构就建立好了，我们需要对 Vue-cli 给我们生成的文件进行一些必要的修改。

修改项目文件内容：

修改根目录下的 index.html 文件，我们想写一些 CSS 样式，这样作是为了更好的布局，然后修改一下标题栏。让标题符合项目这里起名叫“AwesomePOS-快餐店管理系统”。index.html 修改后内容如下。

<!DOCTYPE html>

<html>
  <head>
    <meta charset="utf-8">
    <title>AwesomePOS-快餐管理系统</title>
    <link rel="stylesheet" href=<"http://at.alicdn.com/t/font_wyhhdpv5lhvbzkt9.css">
    <style>
      html,body,#app{height:100%;padding: 0;margin:0;}
    </style>
  </head>
  <body >

    <div id="app" ></div>
    <!-- built files will be auto injected -->

  </body>

</html>

新建 Pos 组件，这个相当于程序员的入口文件。在 src/components/page/目录下新建 Pos.vue 文件。文件内容写出 vue 模板的架构就可以。

<template>
  <div class="pos">
   Hello Pos Demo!
  </div>
</template>

<script>
export default {
  name: 'Pos'
}
</script>

<style scoped>

</style>

修改路由文件，项目根目录/src/router/index.js，让入口文件变成 Pos 组件。先用 import 引入了 Pos 模板组件，然后修改 routes 里边的内容。如果你对 Vue-router 的知识还不了解，可以去看我以前的课程，这里就不作过多的讲解了。

import Vue from 'vue'
import Router from 'vue-router'
import Pos from '@/components/page/Pos'

Vue.use(Router)

export default new Router({
routes: [
{
path: '/',
name: 'Pos',
component: Pos
}
]
})

这时候看一下浏览器中的网页，如果显示出了 Hello Pos Demo.我们就算成功搭建项目架构了。下节课我们确定一下项目中使用的图标。第 3 节：搞定项目图标 Iconfont
在开发中经常会遇到小图标的使用问题，小图标的使用可以让程序更美观和增加可用性。网上给程序加上小图标的方法有很多。曾经为了寻找一款使用简单，图标美观的图标库，我真的是到处搜索，直到遇到了 IconFont，我觉的它能满足我的大部分要求。那在这里我推荐大家使用 IconFont，这是阿里巴巴的矢量图标库。（这绝对不是广告，只是自己使用的一些感受）

挑选自己喜欢的图标

Iconfont 中有很多图标，我们可以像在超市逛街一样，挑选自己喜欢的商品，然后放入购物车。

挑选图标的过程（共 6 步）

进入网站：Iconfont 网址：http://www.iconfont.cn
点击网站上方的“官方图标库”，选择自己喜欢的图标。在这里我选择天猫的图标库。选择好自己喜欢的图标，你可以有两个选择，下载代码 和 添加至项目。我们这两选择添加至项目，然后新建项目，并输入名称。项目添加好后，会自动给我们转入到我们项目库中。点击查看在线链接。生产 css 引入的代码，生成后就可以在项目首页 index.html 引入了。

 <link rel="stylesheet" href="http://at.alicdn.com/t/font_wyhhdpv5lhvbzkt9.css">

图标的使用：

图标顺利引入到项目中，已经可以使用它们了，在“我的项目中”你会看到图标的 font class 值。可以直接复制代码粘贴，也可以自己写代码。

<i class="icon iconfont icon-hanbao"></i>

这样在页面中就可以看到图标了。

添加更多图标：

如果在项目中觉的图标不够用了，需要添加更多图标。可以利用下面四步进行添加。

去 Iconfont 网站继续挑选，把相中的图标加入购物车中。把购物车中的图标加入到项目中。重新生成在线链接。（这部很重要）在项目主页中(index.html)，更换 css 引入链接。实战项目开发的知识点就是很多，也很杂，但是这些都很实用，你也会快速成长，不要感觉和 Vue 无关就忽略，让我们共同努力，变成更好的自己。

第 4 节：编写独立的侧边栏导航组件上节学习了 inconFont 的使用，可以在项目中加入漂亮的 icon 图标了。这节课我们要快速撸一个侧边栏组件出来。组件的作用就是在可以复用，想在那个页面使用都可以，并且像写 html 标签一样简单。

建立 leftNav.vue 文件：

我们在 src/components 目录下，先新建一个 common 和 page 文件夹。

common 文件夹用来放共用组件，下面写的 leftNav.vue 组件就放到这里。
page 文件夹用来放我们的页面模板组件，页面的模板文件放到这里。在 common 文件夹下，新建 leftNav.vue 文件。

开始动手写代码：

建立好文件后，我们先给 components 来个基本组件结构，你可以复制粘贴也可以手写。

<template>
  <div class="left-nav">

  </div>
</template>

<script>
export default {
  name: 'leftNav',
  data () {
    return {
    }
  }
}
</script>

<style>

</style>

注意：这里你也许和我使用的图标不一样，请自行改成你图标用的代码，不要无脑拷贝，图标会显示不出来。

components（组件）基本结构写好后，开始动手写 CSS 样式，让我们的组件变的好看。

<style>
    .left-nav{
       color:#fff;
       font-size:10px;
       height:100%;
       background-color: #1D8ce0;
       float:left;
       width:5%;
    }
    .iconfont{
       font-size:24px;
    }
    .left-nav ul{
        padding:0px;
        margin: 0px;
    }
    .left-nav li{
        list-style: none;
        text-align: center;
        border-bottom:1px solid #20a0ff;
        padding:10px;
    }
</style>

编写完 CSS 样式，这个组件算是大体写好了，以后根据需求我们会在组件里添加<route-link>标签。但是现在还没有这个需求，所以暂时不添加。

把 leftNav 组件放到模板中

先用 import 在 App.vue 中引入 leftNav 组件。

import leftNav from '@/components/common/leftNav'

引入后在 vue 的构造器里添加 components 属性，并放入我们的 leftNav 组件。

export default {
name: 'app',
components:{
leftNav
}
}

这样组件就算在也页面引入成功了，接下来我们就可以在<template>区域里愉快的使用它（<leftNav></leftNav>）。贴出引入使用全部代码，方便大家学习查看。

<template>
  <div id="app">
    <!--左侧导航-->

        <leftNav></leftNav>

    <!--操作区域-->
    <div class="main">
      <router-view></router-view>
    </div>

  </div>
</template>

<script>
import leftNav from '@/components/common/leftNav'
export default {
  name: 'app',
  components:{
    leftNav
  }
}
</script>

<style>
#app {
  font-family: 'Microsoft YaHei','Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
   height:100%;
}

.main{
  float:left;
  width:95%;
  background-color: #EFF2F7;
  height:100%;
  overflow: auto;

}
</style>

第 5 节：开启 Element 封印

Element 是一套为开发者、设计师和产品经理准备的基于 Vue2.0 的组件库，提供了配套设计资源，帮助你的网站快速成型。在项目中自己写组件虽然灵活，但是效率并不高效，所以要学会站在巨人的肩膀上干活，Element 就是巨人的肩旁，也是现在国内比较成熟的以一套 Vue 的组件库。所以我决定 使用这个组件库开发项目。

npm 安装

这里使用 npm 的方式安装，它能更好地和 webpack 打包工具配合使用。

npm install element-ui --save

如果你网络状况不佳可以使用 cnpm 来进行安装。

完整引入项目

在 main.js 中写入以下内容:

import Vue from 'vue'
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-default/index.css'
import App from './App.vue'

Vue.use(ElementUI)

new Vue({
el: '#app',
render: h => h(App)
})

解决 100%高的问题

在页面中使用了 Element 组件，这样他会自动给我们生产虚拟 DOM，我们无法设置高度 100%；

这时候可以利用 javascript，来设置 100%高度问题。先要给我们的<el-col>标签上添加一个 id，我们这里把 ID 设置为

order-list。然后在 vue 构造器里使用 mounted 钩子函数来设置高度。

mounted:function(){
var orderHeight=document.body.clientHeight;
document.getElementById("order-list").style.height=orderHeight+'px';
},

布局的基本架构，我们已经做好，剩下的就是一些细节。下节课我们将用一节课的时间制作大部分 CSS 样式内容。

第 6 节：利用 Element 快速布局（1）这节课我们将快速利用 Element 进行布局页面，这章视频中我会直接拷贝 Style 代码，因为我觉的你学 Vue，那 CSS 也没有任何问题的，所以不耽误大家的宝贵事件。

el-tabs 标签页组件

用 Element 里提供的 el-tabs 组件可以快速制作我们的 tabs 标签页效果，具体使用方法可以到 Element 的官网查看 API。

基本用法很简单，可以直接在模板中引入<el-tabs>标签，标签里边用<el-tab-pane>来代表每个每个标签页。

先看一个最简单的代码：

<el-tabs>
      <el-tab-pane label="点餐">
       点餐
      </el-tab-pane>
      <el-tab-pane label="挂单">
      挂单
      </el-tab-pane>
      <el-tab-pane label="外卖">
      外卖
     </el-tab-pane>
</el-tabs>

细心的小伙伴会看到每个<el-tab-pane>里会有一个 label 属性，这个属性就是你标签页的标题。内容可以直接写在<el-tab-pane>里。

el-table 组件制作表格

需要在订单的 tab 标签页里放入表格，把点选的食品放入到待结账列表里,可以使用 Element 的内置组件 el-table。如果你对 el-table 不了解， 可以去 Element 官网去查看一下。我这里不作太多的解释，先把代码贴过来，然后根据代码在讲解。

<el-table :data="tableData" border show-summary style="width: 100%" >

    <el-table-column prop="goodsName" label="商品"  ></el-table-column>
    <el-table-column prop="count" label="数量" width="50"></el-table-column>
    <el-table-column prop="price" label="金额" width="70"></el-table-column>
    <el-table-column  label="操作" width="100" fixed="right">
        <template scope="scope">
            <el-button type="text" size="small">删除</el-button>
            <el-button type="text" size="small">增加</el-button>

        </template>
    </el-table-column>

</el-table>

这里我们采用了五列布表格， 在第 1 行中的:data 是用来绑定数据源的， border 代表表格有边框效果。在这视频里我会有详细的讲解。
tableData 中的数据源的值，为了布局方便，所以我们进行了写死，以后会改成动态添加的数据。
PS:
你检查下你的列表组件里，slot 里的 <template> 上面有个 scope 属性，你改成 slot-scope

<template scope="xxx">yyyyyyyy</template>
改成

<template slot-scope="xxx">yyyyyyyy</template>
scope 属性在 2.5 以后的版本中已经废弃， 被 slot-scope 替代
slot-scope 不光可以用在 template 元素上，也可以用在其它元素

tableData: [{

          goodsName: '可口可乐',
          price: 8,
          count:1
        }, {

          goodsName: '香辣鸡腿堡',
          price: 15,
          count:1
        }, {

          goodsName: '爱心薯条',
          price: 8,
          count:1
        }, {

          goodsName: '甜筒',
          price: 8,
          count:1
        }]

你现在可以打开浏览器进行一下预览，看一下效果了。如果效果正常，我们可以继续往下编写了。

el-button 按钮组件

需要在点餐表格的下方放入三个功能性按钮，分别是挂单按钮、删除按钮、结账按钮。同样使用 Element 里的组件，进行快速写入。el-button 的 type 属性是设置按钮样式的，为了学些和区分我们这里用三个属性来设置按钮。

<el-button type="warning" >挂单</el-button>
<el-button type="danger" >删除</el-button>
<el-button type="success" >结账</el-button>

到这里我们左边最重要的订单操作区域就布局完成了，下节课我们布局右侧的商品布局。

第 7 节：利用 Element 快速布局（2）常用商品区域布局：

在<el-col :span=17>标签里增加一个层，然后在层内进行布局。因为里边的商品实际意义上是列表，所以用无序列表<li>来布局商品。贴出布局的 html 代码。

<div class="often-goods">
    <div class="title">常用商品</div>
    <div class="often-goods-list">

        <ul>
            <li>
                <span>香辣鸡腿堡</span>
                <span class="o-price">￥15元</span>
            </li>

        </ul>
    </div>

</div>

有了基本 html 结构后，需要增加一些 css 样式来美化页面：

.title{
height: 20px;
border-bottom:1px solid #D3DCE6;
background-color: #F9FAFC;
padding:10px;
}
.often-goods-list ul li{
list-style: none;
float:left;
border:1px solid #E5E9F2;
padding:10px;
margin:5px;
background-color:#fff;
}
.o-price{
color:#58B7FF;
}
现在页面变的漂亮了，我们这时候为了页面更逼近真实效果，我们在 Vue 的构造器里临时加一个数组，用作常用商品使用。声明的变量叫 oftenGoods（真实项目不能这样起名字，这里只是练习使用）。

oftenGoods:[
{
goodsId:1,
goodsName:'香辣鸡腿堡',
price:18
}, {
goodsId:2,
goodsName:'田园鸡腿堡',
price:15
}, {
goodsId:3,
goodsName:'和风汉堡',
price:15
}, {
goodsId:4,
goodsName:'快乐全家桶',
price:80
}, {
goodsId:5,
goodsName:'脆皮炸鸡腿',
price:10
}, {
goodsId:6,
goodsName:'魔法鸡块',
price:20
}, {
goodsId:7,
goodsName:'可乐大杯',
price:10
}, {
goodsId:8,
goodsName:'雪顶咖啡',
price:18
}, {
goodsId:9,
goodsName:'大块鸡米花',
price:15
}, {
goodsId:20,
goodsName:'香脆鸡柳',
price:17
}

]
有了数据，可以使用 v-for 循环来输出到 html 模板中。

商品分类布局：

这样我们商品的上半部分就布局完成了，现在需要布局下半部分，我们在下半部分先添加一个 tabs 的标签样式。

<div class="goods-type">

    <el-tabs>
        <el-tab-pane label="汉堡">
            汉堡
        </el-tab-pane>
            <el-tab-pane label="小食">
            小食
        </el-tab-pane>
        <el-tab-pane label="饮料">
            饮料
        </el-tab-pane>
        <el-tab-pane label="套餐">
            套餐
        </el-tab-pane>

    </el-tabs>

</div>
有上节课作tabs标签页的经验，这个变的异常简单。

制作商品的无序列表：

<ul class='cookList'>
    <li>
        <span class="foodImg"><img src="http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg" width="100%"></span>
        <span class="foodName">香辣鸡腿堡</span>
        <span class="foodPrice">￥20.00元</span>
    </li>
</ul>

对无序列表进行 CSS 样式编写：

.cookList li{
list-style: none;
width:23%;
border:1px solid #E5E9F2;
height: auot;
overflow: hidden;
background-color:#fff;
padding: 2px;
float:left;
margin: 2px;

}
.cookList li span{

display: block;
float:left;
}
.foodImg{
width: 40%;
}
.foodName{
font-size: 18px;
padding-left: 10px;
color:brown;

}
.foodPrice{
font-size: 16px;
padding-left: 10px;
padding-top:10px;
}

有了基本的样式，我们可以在 Vue 的构造器里添加汉堡类的数据。声明一个 type0Goods 的数据，数据格式如下。

    type0Goods:[
          {
              goodsId:1,
              goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
              goodsName:'香辣鸡腿堡',
              price:18
          }, {
              goodsId:2,
              goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
              goodsName:'田园鸡腿堡',
              price:15
          }, {
              goodsId:3,
              goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
              goodsName:'和风汉堡',
              price:15
          }, {
              goodsId:4,
               goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
              goodsName:'快乐全家桶',
              price:80
          }, {
              goodsId:5,
               goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
              goodsName:'脆皮炸鸡腿',
              price:10
          }, {
              goodsId:6,
               goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
              goodsName:'魔法鸡块',
              price:20
          }, {
              goodsId:7,
               goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
              goodsName:'可乐大杯',
              price:10
          }, {
              goodsId:8,
               goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
              goodsName:'雪顶咖啡',
              price:18
          }, {
              goodsId:9,
               goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
              goodsName:'大块鸡米花',
              price:15
          }, {
              goodsId:20,
               goodsImg:"http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
              goodsName:'香脆鸡柳',
              price:17
          }

      ],

用 v-for 改造我们的无序列表：

<li v-for="goods in type0Goods">
    <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
    <span class="foodName">{{goods.goodsName}}</span>
    <span class="foodPrice">￥{{goods.price}}元</span>
</li>

Elements in iteration expect to have 'v-bind:key' directives 错误的解决办法
Vue 2.2.0+的版本里，当在组件中使用 v-for 时，key 是必须的。更改 vetur 配置 vscode->首选项->设置->搜索（vetur）
"vetur.validation.template": true,
改成：false

页面的基本布局我们已经制作完成，终于看起来像个收银界面了。但是现在的数据都是写死的，下节课我们将从后端用 Axios 拉去数据。

第 8 节：Axios 从远程读取数据

上节课我们利用 Elemnt 已经把页面布局的差不多了，如果你觉的不够美观，可以自己再进行美化，因为课程的原因 css 细节我们这里就不深入美化了。这节课我们开始学习 Axios 的知识，并把商品数据从远端读取到页面上。学这节课时技术胖已经为大家准备好了后端数据，你们只要调用相应的页面就可以调取，在实际开发中，这些后台数据是需要后端程序员和你共同讨论制作的。我们现在只做前端，数据大家只要会调用即可。

安装 Axios

我们直接使用 npm install 来进行安装。

npm install axios --save
由于 axios 是需要打包到生产环境中的，所以我们使用–save 来进行安装。

引入 Axios

我们在 Pos.vue 页面引入 Axios，由于使用了 npm 来进行安装，所以这里不需要填写路径。

import axios from 'axios'
服务端拉取常用商品数据

远端服务器地址：http://jspang.com/DemoApi/oftenGoods.php

（在实际项目中这个后台接口地址是后端程序员提供给你的，你可以随便调用这个接口，我已经放到服务器上了。）

可以先把地址放到地址栏访问一下，是可以正常访问的，并且输出了 json 格式的字符串，这就是我们需要的远端数据了。这里我们使用 Axios 的 get 方式来获得数据。

created(){
axios.get('http://jspang.com/DemoApi/oftenGoods.php')
.then(response=>{
console.log(response);
this.oftenGoods=response.data;
})
.catch(error=>{
console.log(error);
alert('网络错误，不能访问');
})
},
把 axios 的方法写到了 created 钩子函数中，我们使用了 get 方法进行拉取数据，如果拉取成功用远端数据对 oftenGoods 进行赋值。

拉取报错，一般有两种情况：

网络不通：网络状况不是很好，这可以在失败后隔 5 秒再次请求。报决绝访问：这种多是后端程序员设置了不允许跨域访问，需要你和后端程序员一起调试解决。拉取分类商品数据：

远端服务器地址：http://jspang.com/DemoApi/typeGoods.php

依然用 Get 进行拉取，拉取后先用 consoe.log(response)查看一下数据结构，让后进行赋值。由于知识跟上边的很像，文字版我就不多描述了，详细可以查看视频教程。

在这里贴出拉取和分配不同分类代码：

在实际开发中类别也是循环出来的，这里为了教学演示，没有写的那么复杂，你只要明白了如何操作，以后你可以自己增加。就像我这个项目一样，在视频结束后，会慢慢写完善所有功能，最后送给女神，赢得女神芳心。

下节课我们学习订单操作里需要的功能，比如点击商品，添加到左边的订单栏里，增加，删除商品，模拟订单提交到后台。如果下节课一节讲不完，我们就分成两节课来讲。

第 9 节：订单模块制作 核心功能-1

经过上节课的学习，我们已经可以从后台取得数据了。这节课要完成的任务是实现页面左侧的订单列表页面的添加操作。本来我想一节课讲完的，但是内容还是比较多的，又不想让大家每节课学习很长时间，所以我把这个内容进行了划分。我们在 vue 的构造器里加入 methods 方法，在 methods 方法里再加入 addOrderList 方法。这个方法的作用是点击右侧的商品，然后把商品添加到左边的列表里。

addOrderList 方法(也许你只看文字版无法理解，推荐查看视频)：

methods:{
//添加订单列表的方法
addOrderList(goods){
this.totalCount=0; //汇总数量清 0
this.totalMoney=0;
let isHave=false;
//判断是否这个商品已经存在于订单列表
for (let i=0; i<this.tableData.length;i++){
console.log(this.tableData[i].goodsId);
if(this.tableData[i].goodsId==goods.goodsId){
isHave=true; //存在
}
}
//根据 isHave 的值判断订单列表中是否已经有此商品
if(isHave){
//存在就进行数量添加
let arr = this.tableData.filter(o =>o.goodsId == goods.goodsId);
arr[0].count++;
//console.log(arr);
}else{
//不存在就推入数组
let newGoods={goodsId:goods.goodsId,goodsName:goods.goodsName,price:goods.price,count:1};
this.tableData.push(newGoods);

            }

            //进行数量和价格的汇总计算
            this.tableData.forEach((element) => {
                this.totalCount+=element.count;
                this.totalMoney=this.totalMoney+(element.price*element.count);
            });

      }

}

在作这个方法的时候，在订单列表的下方又添加了订单的统计功能，其实也就两项：订单价格汇总和订单商品数量汇总。我们在 data 里声明的值是 totalMoney 和 totalCount。

写完这个方法后，我们还需要在我们的商品上绑定方法，来进行调用添加方法。

@click="addOrderList(goods)"

这样在点击商品时订单列表就会根据我们的程序逻辑发生变化。

订单列表中的增加按钮

商品中绑定 addOrderList 方法是非常容易的，如果在订单列表中绑定是需要特殊处理一下的，需要用到 template 的 scope 值，让后进行绑定。

<el-button type="text" size="small" @click="addOrderList(scope.row)">增加</el-button>

第 10 节：订单模块制作 核心功能-2

继续制作订单模块，这节课主要三个功能的制作，删除列表中的单个商品，删除列表中的全部商品，简单模拟结账。

删除单个商品

在 veu 构造器 methods 属性里增加一个 delSingleGoods 方法，并接收 goods 对象为参数，用数组的 filter 可以轻松删除数组中单个的商品。

    //删除单个商品
      delSingleGoods(goods){
        console.log(goods);
        this.tableData=this.tableData.filter(o => o.goodsId !=goods.goodsId);

      },

现在可以 npm run dev 试一下了，会发现现在商品可以正确的删除了，但是统计的数量和金额是不正确的，我们需要写一些统计的代码。在下手之前你会发现在增加商品方法中也有类似统计的方法，既然两个功能很像，我们就重新写一个方法。

//汇总数量和金额
getAllMoney(){
this.totalCount=0;
this.totalMoney=0;
if(this.tableData){
this.tableData.forEach((element) => {
this.totalCount+=element.count;
this.totalMoney=this.totalMoney+(element.price\*element.count);
});
}

}
需要注意的是，以前我们是单独使用的，所以不用把 totoalCount 和 totalMoney 清零，但是做成公用方法了，记得清零。方法做好了，我们在需要的地方直接用 this.getAllMoney()引用就可以了。

功能做好了，我们还需要为删除按钮绑定事件：

<el-button type="text" size="small" @click="delSingleGoods(scope.row)">删除</el-button>
这样我们就把删除单个订单商品的功能做好了，我们可以测试调试一下。

删除全部订单商品

这个功能其实很简单，只要把 this.tableData 清空就可以了，在 methods 属性中写一个 delAllGoods 的方法。

      //删除所有商品
        delAllGoods() {
            this.tableData = [];
            this.totalCount = 0;
            this.totalMoney = 0;
        },

有的小伙伴会好奇，你完全可以再次复用 getAllMoney()方法进行汇总，为什么不用那？汇总方法里毕竟是有业务逻辑的，我们只做两个清零，这样消耗的资源更少，所以我们没有使用。

模拟结账

因为模拟结账需要 Post 数据到后台，我的服务器又不能提供这样的借口给大家，所以我只说制作思路，大家可以在自己的服务器上去实现。

1、设置我们 Aixos 的 Pos 方法。

2、接受返回值进行处理。

3、如果成功，清空现有构造器里的 tableData，totalMoney，totalCount 数据。

4、进行用户的友好提示。

由于前两个步骤不能演示，所以这里我们只模拟 3 和 4 步。在 methods 里作一个结账方法，清空数据和进行友好提示。

checkout() {
if (this.totalCount!=0) {
this.tableData = [];
this.totalCount = 0;
this.totalMoney = 0;
this.$message({
message: '结账成功，感谢你又为店里出了一份力!',
type: 'success'
});

    }else{
        this.$message.error('不能空结。老板了解你急切的心情！');
    }

}
订单模块基本的功能就制作完成了，我希望大家都能动手练习一下，如果你不动手练习你永远学不会的。

第 11 节：项目打包和上线

一直追看的小伙伴可能知道原来还有一节挂单功能的制作，但是在录制的过程中我发现 90%的知识点都是重复的，不重复的知识点讲的还和 Vue 没有关系，是 html5 的 localStorage 操作，所以我去掉了这节。这节我们主要讲一下打包需要注意的事项和总结一下我们学习的知识。

打包注意事项：

1、把绝对路径改为相对路径

我们打开 config/index.js 会看到一个 build 属性，这里就我们打包的基本配置了。你在这里可以修改打包的目录，打包的文件名。最重要的是一定要把绝对目录改为相对目录。

assetsPublicPath:'./'
这样才能保证我们打包出去的项目可以正常预览。

2、在命令行中用 npm run build 进行打包。

npm run build
