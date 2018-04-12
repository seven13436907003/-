<!-- 结构层 -->
<template>
  <div id="index">
        <header class="index_header clearfix">
            <div class="position">
                <div class="send">
                    <img src="static/index_images/ci_20171025_1.png" alt="">
                </div>
                <div class="map">萧山区</div>
                <i class="icon_down"></i>
            </div>
            <i class="iconfont icon-icon-fangdajing"></i>
        </header>
        <div class="banner clearfix">
            <swiper :options="swiperOption">
                <swiper-slide v-for="(imgs, index) in banners" :key="index">
                    <img :src="imgs.img" alt="">
                </swiper-slide>
                <div class="swiper-pagination" slot="pagination"></div>
            </swiper>
        </div>
        <section class="index_section">
            <div class="list1 clearfix">
                <a href="">
                    <img src="../assets/index_img/index_list01.jpg" class="a1">
                </a>
                <a href="">
                    <img src="../assets/index_img/index_list02.jpg" class="a2">
                </a>
            </div>
            <div class="list2 clearfix">
                <a href="">
                    <img src="../assets/index_img/index_list03.gif" alt="">
                </a>
            </div>
            <div class="hotbuy clearfix">
                <a href="">
                    <h2>果园热卖</h2>
                </a>
                <span class="a13"></span>
            </div>
            <div class="hotbuy_list clearfix" v-for="item in hotbuy">
                <img :src="item.img" alt="">
                <div class="hotbox">
                    <h3>{{item.title}}</h3>
                    <p>{{item.content}}</p>
                    <div class="parge">{{item.price}}</div>
                    <span>{{item.money}} /</span>
                    <i>{{item.kg}}</i>
                    <em class="num">+</em>
                </div>
            </div>
            <div class="hotbuy_swiper">
                <swiper :options="hotbuy_swiper">
                    <swiper-slide v-for="(haha, index) in hotbuy_list" :key="index">
                        <img :src="haha.img" alt="">
                            <em v-if="haha.title">{{haha.title}}</em>
                        <p>{{haha.content}}</p>
                        <span class="iconfont icon-qian"><b class="iconfont icon-jiahao"></b>{{haha.price}}</span>
                    </swiper-slide>
                </swiper>
            </div>
            <div class="hotbuy clearfix">
                <a href="">
                    <h2>新品首发</h2>
                </a>
                <span class="a13"></span>
            </div>
            <div class="new">
                <a href="">
                    <img :src="NewImg.img" alt="">
                </a>
            </div>
            <div class="hotbuy_swiper">
                <swiper :options="hotbuy_swiper">
                    <swiper-slide v-for="(popo, index) in new_swiper" :key="index">
                        <img :src="popo.img" alt="">
                            <em v-if="popo.title">{{popo.title}}</em>
                        <p>{{popo.content}}</p>
                        <span class="iconfont icon-qian"><b class="iconfont icon-jiahao"></b>{{popo.price}}</span>
                    </swiper-slide>
                </swiper>
            </div>
            <div class="hotbuy clearfix">
                <a href="">
                    <h2>精选专题</h2>
                </a>
                <span class="a13"></span>
            </div>
            <div class="hotbuy_swiper">
                <swiper :options="hotbuy_swiper">
                    <swiper-slide v-for="(popo, index) in new_swiper" :key="index">
                        <img :src="popo.img" alt="">
                            <em v-if="popo.title">{{popo.title}}</em>
                        <p>{{popo.content}}</p>
                        <span class="iconfont icon-qian"><b class="iconfont icon-jiahao"></b>{{popo.price}}</span>
                    </swiper-slide>
                </swiper>
            </div>
        </section>
        <footer class="footer_nav clearfix">
            <a href="" class="home">
                <i class="iconfont icon-home"></i>
                <span>首页</span>
            </a>
            <a href="" class="classify">
                 <i class="iconfont icon-fenlei"></i>
                <span>分类</span>
            </a>
            <a href="" class="shopcar">
                <i class="iconfont icon-gouwuche"></i>
                <span>购物车</span>
            </a>
            <a href="" class="myOrchard">
                <i class="iconfont icon-wode"></i>
                <span>我的果园</span>
            </a>
        </footer>
  </div>
</template>
<!-- 逻辑层 -->
<script>
export default {
  name: 'index',
  data () {
    return {
        hotbuy: [],
        banners: [],
        hotbuy_list: [],
        NewImg: {},
        new_swiper: [],
        swiperOption: {
            autoplay: true,
            pagination: {
                el: '.swiper-pagination'
            }
        },
        hotbuy_swiper: {
            slidesPerView: 3.3,
            //滑动延迟特效
            freeMode: true
        }

    }
  },
  created() {
        //轮播图banner接口
        this.$axios.get('https://www.easy-mock.com/mock/5abc80bb87dd535c7d26ce4b/abc_copy/banner')
                .then(res => {
                    this.banners = res.data.banners;
                })
                .catch(error => {
                    console.log(error);
                })
        //果园热卖接口
        this.$axios.get('https://www.easy-mock.com/mock/5abc80bb87dd535c7d26ce4b/abc_copy/hotbuy'
        )
        .then(res => {
            this.hotbuy = res.data.hotbuy;
        })
        .catch(error => {
            console.log(error)
        })
        //热卖滑动列表接口
        this.$axios.get('https://www.easy-mock.com/mock/5abc80bb87dd535c7d26ce4b/abc_copy/hotbuy_list').then(res => {
                this.hotbuy_list = res.data.hotbuy_list;
            })
            .catch(error => {
                console.log(error);
            })
        //新品首发图片
        this.$axios.get('https://www.easy-mock.com/mock/5abc80bb87dd535c7d26ce4b/abc_copy/NewImg').then(res => {
                this.NewImg = res.data.NewImg;
            })
            .catch(error => {
                console.log(error);
            })
        //新品swiper请求
        this.$axios.get('https://www.easy-mock.com/mock/5abc80bb87dd535c7d26ce4b/abc_copy/new_swiper').then(res => {
                this.new_swiper = res.data.new_swiper;
            })
            .catch(error => {
                console.log(error);
            })
  }
}
</script>

<!-- 样式层 -->
<style scoped lang="less">
    @rem: 50rem;
    @h_line: 36/@rem;
    .clearfix:after {
        display: block;
        content: '';
        clear: both;
    }
    .index_header{
        position: fixed;
        display: block;
        width: 100%;
        height: 36/@rem;
        background-color: #fff;
        z-index: 999;
        border-bottom: 4/@rem solid rgba(0,0,0,.2);
    }
    .position {
        float: left;
        height: 36/@rem;
        margin-left: 16/@rem;
    }
    .send {
        float: left;
        width: 56/@rem;
        height: 36/@rem;
        line-height: @h_line;
        margin-right: 5/@rem;
    }
    .send img {
        text-align: center;
        width: 56/@rem;
        height: 14/@rem;
        margin-bottom: 8/@rem;
    }
    .map {
        width: 45/@rem;
        float: left;
        font-size: 14/@rem;
        color: #65a032;
        line-height: @h_line;
    }
    .icon_down {
        float: left;
        line-height: @h_line;
        border-color: #57af1a transparent transparent transparent;
        border-style: solid;
        border-width: 8/@rem 4/@rem 0 4/@rem;
        height: 0;
        width: 0;
        display: inline-block;
        margin-top: 14/@rem;
        margin-left: 4/@rem;
    }
    .icon-icon-fangdajing {
        float: right;
        font-size: 23/@rem;
        color: #8a8a8a;
        line-height: @h_line;
        margin-right: 16/@rem;
    }
    /* 轮播图 */
    .banner {
        padding-top: 40/@rem;
    }
    .index_section {
        width: 100%;
        overflow: hidden;
        height: 10000/@rem;
    }
    /* 新品试吃 */
    .list1 {
        width: 100%;
        height: 100/@rem;
        margin-top: 10/@rem;
    }
    .list1 a img{
        display: block;
        width: 175/@rem;
        height: 95/@rem;
    }
    .list1 a .a1 {
        float: left;
        margin-left: 7.5/@rem;
    }
    .list1 a .a2 {
        float: right;
        margin-right: 7.5/@rem;

    }
    /* 历9弥鲜 */
    .list2 {
        width: 100%;
        height: 160/@rem;
        text-align: center;
        border-bottom: 10/@rem solid #f5f5f5;
    }
    /* 果园热卖 */
    .hotbuy {
        width: 100%;
        height: 64/@rem;
        border-bottom: 1/@rem solid #fafafa;
        position: relative;
    }
    .hotbuy a {
        float: left;
        text-align: center;
        line-height: 64/@rem;
        display: block;
        width: 100%;
    }
    .hotbuy a h2 {
        font-size: 17/@rem;

        color: #000;
    }
    .a13 {
        width: 14/@rem;
        height: 14/@rem;
        display: block;
        background: url("../assets/index_img/youjiantou.png") no-repeat;
        position: absolute;
        left: 230/@rem;
        top: 25/@rem;
    }

    .height {
        height: 800/@rem;
    }

    .hotbuy_list {
        width: 100%;
        height: 160.5/@rem;
        padding: 0 25/@rem 12/@rem;
    }
    .hotbuy_list img {
        display: block;
        float: left;
        width: 120/@rem;
        height: 120/@rem;
        margin-top: 25/@rem;
    }
    .hotbuy_list .hotbox{
        margin-left: 25/@rem;
        margin-top: 36/@rem;
        height: 95/@rem;
        float: left;
    }
    .hotbuy_list h3 {
        font-size: 17/@rem;
        margin-bottom: 5/@rem;
    }
    .hotbuy_list p {
        font-size: 14/@rem;
        color: #878787;
        margin-bottom: 5/@rem;
    }
    .hotbox .parge {
        width: 76.69/@rem;
        height: 22/@rem;
        text-align: center;
        line-height: 22/@rem;
        font-size: 9/@rem;
        color: #fff;
        background-color: #ff8a65;
        border-radius: 4/@rem 4/@rem;
        margin-bottom: 5/@rem;
    }
    .hotbox span {
        float: left;
        height: 21/@rem;
        display: block;
        font-size: 16/@rem;
        line-height: 23/@rem;
        color: #ff8000;
        padding-left: 17/@rem;
        position: relative;
    }
    .hotbox span::before{
        content: "";
        width: 15/@rem;
        height: 15/@rem;
        display: block;
        position: absolute;
        left: 0;
        top: 4/@rem;
        background: url("../assets/index_img/money.png") no-repeat;
        background-size: 12/@rem 15/@rem;
        color: #ff8000;
    }
    .hotbox i {
        width: 26.69/@rem;
        height: 14/@rem;
        font-size: 10/@rem;
        color: #ff8000;
        text-align: center;
        line-height: 26/@rem;
        float: left;
        margin-left: 3/@rem;
    }
    .hotbox .num {
        width: 23/@rem;
        height: 23/@rem;
        float: left;
        margin-left: 70/@rem;
        text-align: center;
        line-height: 23/@rem;
        font-size: 22/@rem;
        color: #ff8000;
        border: 1/@rem solid #bfbfbf;
        border-radius: 50%;
        font-weight: bold;
        display: block;
    }
    .hotbuy_swiper {
        height: 170/@rem;
        border-bottom: 10/@rem solid #f5f5f5;
    }
    .hotbuy_swiper .swiper-container {
        height: 170/@rem;
    }
    .hotbuy_swiper .swiper-slide{
        width: 96/@rem;
        padding: 10/@rem 8/@rem 15/@rem;
        box-sizing: border-box;
        position: relative;
    }
    .hotbuy_swiper img {
        display: block;
        width: 96/@rem;
        height: 96/@rem;
        float: left;
        
    }
    .hotbuy_swiper em {
        position: absolute;
        top: 98/@rem; left: 25/@rem;
        display: block;
        font-style: normal;
        background-color: #ff8a65;
        text-align: center;
        padding: 3/@rem 6/@rem;
        font-size: 12/@rem;
        color: #fff;
        border-radius: 4/@rem 4/@rem 4/@rem 4/@rem;
    }
    .hotbuy_swiper p {
        position: absolute;
        bottom: 30/@rem; left: 10/@rem;
        width: 96/@rem;
        height: 17/@rem;
        overflow: hidden;
        text-align: center;
        text-overflow: ellipsis;
        white-space: nowrap;
        font-size: 13/@rem;
        color: #3a3a3a;
        font-weight: 300;
    }
    .hotbuy_swiper span {
        position: absolute;
        display: block;
        width: 84/@rem;
        bottom: 13/@rem; left: 20/@rem;
        color: #ff8000;
        height: 16/@rem;
        font-size: 12/@rem;

    }
    .icon-qian::before {
        font-size: 12/@rem;
        font-weight: bold;
    }
    .hotbuy_swiper span i {
        display: block;
        width: 8/@rem;
        height: 8/@rem;
        float: left;
        font-size: 8/@rem;
    }
    .hotbuy_swiper b {
        position: absolute;
        bottom: -3/@rem; right: -4/@rem;
        display: block;
        width: 16/@rem;
        height: 16/@rem;
        border-radius: 50%;
        text-align: center;
        line-height: 16/@rem;
        border: 1/@rem solid #bfbfbf;
        color: #ff8a65;
        font-size: 12/@rem;
    }
    .new {
        width: 100%;
        height: 160/@rem;

    }
    /* 头部 */
    .footer_nav {
        position: fixed;
        bottom: 0/@rem;
        width: 100%;
        height: 42/@rem;
        background-color: #fff;
        border-top: 2/@rem solid #d7d7d7;
        z-index: 999;
    }
    .footer_nav a {
        float: left;
        display: block;
        width: 93.75/@rem;
        height: 42/@rem;
        text-align: center;
    }
    .footer_nav i{
        width: 93.75/@rem;
        height: 26/@rem;
        font-size: 24/@rem;
        color: #939393;
        float: left;
    }
    .footer_nav a span {
        width: 93.75/@rem;
        display: block;
        float: left;
        height: 14/@rem;
        font-size: 12/@rem;
        color: #898989;
    }
</style>
