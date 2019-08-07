<template>
	<view id="SHAREPAGE">
		<scroll-view scroll-y :style="'height:'+height+'px'">
			<view class="share_title">邀请好友  得优惠券</view>
			<view class="share_bgimg_box">
				<image src="../../static/share/3.png" mode=""></image>
				<view class="share_item_top">
					<view class="share_item_code">邀请码：Q859</view>
					<view class="share_top_title">邀请一位好友注册APP商城获得</view>
					<view class="share_top_money"><text class="money">10</text>元</view>
					<view class="share_top_text">洗衣优惠券无门槛，全场通用</view>
				</view>
				<view class="share_item_bottom">
					<view class="share_item_button">
						<view class="item_button_box" @click="shareWX">
							<view class="item_img_box">
								<image src="../../static/share/u7276.png" mode=""></image>
							</view>
							<view class="item_text_box">微信好友</view>
						</view>
						<view class="item_button_box" @click="shareFriend">
							<view class="item_img_box">
								<image src="../../static/share/u7278.png" mode=""></image>
							</view>
							<view class="item_text_box">朋友圈</view>
						</view>
						<view class="item_button_box" @click="shareQQ">
							<view class="item_img_box">
								<image src="../../static/share/u7280.png" mode=""></image>
							</view>
							<view class="item_text_box">QQ好友</view>
						</view>
					</view>
					<view class="share_item_rescode">
						<view class="share_item_input">
							<input type="text" placeholder="请输入邀请码"/>
						</view>
						<view class="share_item_get">
							<button type="primary" style="background-color: #FF3333;">领 取</button>
						</view>
					</view>
				</view>
			</view>
			<view class="share_tips_box">
				<view class="share_tips_title">邀请攻略</view>
				<view class="share_tips_main">
					<view class="share_tips_num">1</view>
					<view class="share_tips_line"></view>
					<view class="share_tips_num">2</view>
					<view class="share_tips_line"></view>
					<view class="share_tips_num">3</view>
				</view>
				<view class="share_tips_side">
					<view class="share_tips_text">发送邀请给好友</view>
					<view class="share_tips_blank"></view>
					<view class="share_tips_text">好友注册进入分享输入邀请码领取</view>
					<view class="share_tips_blank"></view>
					<view class="share_tips_text">无门槛优惠券到账</view>
				</view>
				<view class="share_tips_footer">
					获得的优惠券请到<text class="tips_link" @click="goRouter">我的-优惠券</text>中查看
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			height: 0
		}
	},
	onNavigationBarButtonTap: function () {
		uni.switchTab({url:"../my/my"});
	},
	onLoad: function () {
		this.height = uni.getSystemInfoSync().windowHeight - 10;
	},
	methods: {
		shareWX: function () {
			uni.share({
				provider: "weixin",
				scene: "WXSceneSession",
				type: 0,
				href: "http://uniapp.dcloud.io/",
				title: "uni-app分享",
				summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
				imageUrl: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
				success: function (res) {
					console.log("success:" + JSON.stringify(res));
				},
				fail: function (err) {
					console.log("fail:" + JSON.stringify(err));
				}
			});
		},
		shareFriend: function () {
			uni.share({
				provider: "weixin",
				scene: "WXSenceTimeline",
				type: 0,
				href: "http://uniapp.dcloud.io/",
				title: "uni-app分享",
				summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
				imageUrl: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
				success: function (res) {
					console.log("success:" + JSON.stringify(res));
				},
				fail: function (err) {
					console.log("fail:" + JSON.stringify(err));
				}
			});
		},
		shareQQ: function () {
			if (uni.getSystemInfoSync().platform == "ios") {
				uni.share({
					provider: "qq",
					type: 0,
					href: "http://uniapp.dcloud.io/",
					title: "uni-app分享",
					summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
					imageUrl: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
					success: function (res) {
						console.log("success:" + JSON.stringify(res));
					},
					fail: function (err) {
						console.log("fail:" + JSON.stringify(err));
					}
				});
			}else{
				uni.share({
					provider: "qq",
					type: 2,
					href: "http://uniapp.dcloud.io/",
					title: "uni-app分享",
					summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
					imageUrl: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/uni@2x.png",
					success: function (res) {
						console.log("success:" + JSON.stringify(res));
					},
					fail: function (err) {
						console.log("fail:" + JSON.stringify(err));
					}
				});
			}
		},
		goRouter: function () {
			uni.reLaunch({url:'../coupon/coupon?type=my'});
		}
	}
}
</script>

<style scoped>
#SHAREPAGE{
	background-color: #FF6666;
	padding-bottom: 10px;
}
.share_title{
	color: white;
	font-size: 1.5em;
	text-align: center;
	font-weight: bold;
	padding: 5% 0px;
}
.share_bgimg_box{
	width: 76%;
	height: 0px;
	padding-bottom: 96%;
	position: relative;
	margin: 0px auto 20px;
}
.share_bgimg_box image{
	position: absolute;
	width: 100%;
	height: 100%;
}
.share_item_top{
	position: absolute;
	width: 100%;
	height: 50%;
	text-align: center;
}
.share_item_code{
	padding: 4% 0px;
	font-size: 1em;
	font-weight: bold;
}
.share_top_title{
	font-size: 0.8em;
	color: #FF0000;
}
.share_top_money{
	color: #FF0000;
	padding: 4% 0px;
}
.money{
	font-size: 2.5em;
	font-weight: bold;
}
.share_top_text{
	font-size: 0.8em;
	color: #666666;
}
.share_item_bottom{
	position: absolute;
	width: 100%;
	height: 36%;
	bottom: 0px;
}
.share_item_button{
	display: flex;
	align-items: center;
	width: 99%;
	margin: auto;
	margin-bottom: 10px;
}
.item_button_box{
	width: 33%;
}
.item_img_box{
	width: 45%;
	height: 0px;
	padding-bottom: 45%;
	position: relative;
	margin: auto;
}
.item_img_box image{
	width: 100%;
	height: 100%;
	position: absolute;
}
.item_text_box{
	color: #CCCC33;
	font-size: 0.8em;
	text-align: center;
	padding-top: 5px;
}
.share_item_rescode{
	display: flex;
	align-items: center;
	width: 90%;
	margin: auto;
	background-color: white;
	border: 1px solid white;
}
.share_item_input{
	width: 70%;
	height: 100%;
}
.share_item_input input{
	font-size: 0.8em;
}
.share_item_get{
	width: 30%;
	height: 100%;
}
.share_item_get button{
	font-size: 0.8em;
	border-radius: 0px;
	color: white;
}
.share_tips_box{
	background-color: white;
	border: 1px solid #797979;
	border-radius: 8px;
	width: 78%;
	margin: auto;
}
.share_tips_title{
	text-align: center;
	padding: 10px 0px;
	font-size: 1em;
	color: #666666;
	font-weight: bold;
}
.share_tips_main{
	display: flex;
	align-items: center;
	width: 88%;
	margin: auto;
}
.share_tips_line{
	width: 26%;
	border: 1px solid #FF0000;
	height: 0px;
}
.share_tips_num{
	width: 16%;
	text-align: center;
	font-size: 1.5em;
	color: #FF0000;
}
.share_tips_side{
	display: flex;
	align-items: flex-start;
	width: 98%;
	margin: auto;
}
.share_tips_blank{
	width: 10%;
	height: 0px;
}
.share_tips_text{
	font-size: 0.7em;
	text-align: center;
	width: 28%;
	color: #666666;
}
.share_tips_footer{
	font-size: 0.7em;
	color: #666666;
	text-align: center;
	padding: 10px 0px;
}
.tips_link{
	color: #FF0000;
}
</style>
