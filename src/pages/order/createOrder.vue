<template>
	<view>
		<!-- 地址 -->
		<navigator url="/pages/address/address?source=1" class="address-section">
		  <view class="order-content">
		    <text class="yticon icon-shouhuodizhi"></text>
		    <view class="cen">
		      <template v-if="addr.addr_id">
		        <view class="top">
		          <text class="name">{{addr.name}}</text>
		          <text class="mobile">{{addr.mobile}}</text>
		        </view>
		        <text class="address">{{addr.area_str}} {{addr.addr}}</text>
		      </template>
		      <text v-else>请添加地址</text>
		    </view>
		    <text class="yticon icon-you"></text>
		  </view>

		  <image class="a-bg" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAu4AAAAFCAYAAAAaAWmiAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6Rjk3RjkzMjM2NzMxMTFFOUI4RkU4OEZGMDcxQzgzOEYiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6Rjk3RjkzMjQ2NzMxMTFFOUI4RkU4OEZGMDcxQzgzOEYiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDpGOTdGOTMyMTY3MzExMUU5QjhGRTg4RkYwNzFDODM4RiIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDpGOTdGOTMyMjY3MzExMUU5QjhGRTg4RkYwNzFDODM4RiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PrEOZlQAAAiuSURBVHjazJp7bFvV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"></image>
		</navigator>

		<view class="goods-section">
			<!-- <view class="g-header b-b">
				<image class="logo" src="http://duoduo.qibukj.cn/./Upload/Images/20190321/201903211727515.png"></image>
				<text class="name">西城小店铺</text>
			</view> -->
			<!-- 商品列表 -->
			<template v-if="cartInfo.object.goods.length > 0">
				<view class="g-item" v-for="(item, itemIndex) in cartInfo.object.goods" :key="item.obj_ident">
					<image :src="item.obj_items.products[0].image_url"></image>
					<view class="right">
						<text class="title clamp">{{item.obj_items.products[0].name || ''}}</text>
						<text class="spec">{{item.obj_items.products[0].spec_info || ''}}</text>
						<view class="price-box">
							<text class="price">￥{{item.obj_items.products[0].price.buy_price || 0.00}}</text>
							<text class="number">x {{item.quantity}}</text>
						</view>
					</view>
				</view>
			</template>
		</view>

		<!-- 配送方式 -->
		<view class="yt-list">
			<view class="yt-list-cell b-b" @click="toggleDeliveryMask('show')">
				<text class="cell-tit clamp">配送方式</text>
				<text class="cell-tip" :class="{disabled: selectedDlyType.selected === false}">
					{{selectedDlyType.txt}}
				</text>
				<text class="yticon icon-you"></text>
			</view>
		</view>

		<!-- 支付方式 -->
		<!-- <view class="yt-list">
			<view class="yt-list-cell b-b" @click="togglePaymentsMask('show')">
				<text class="cell-tit clamp">支付方式</text>
				<text class="cell-tip" :class="{disabled: selectedPayment.selected === false}">
					{{selectedPayment.txt}}
				</text>
				<text class="yticon icon-you"></text>
			</view>
		</view> -->

		<!-- 优惠明细 -->
		<view class="yt-list">
			<view class="yt-list-cell b-b" @click="toggleCouponMask('show')">
				<view class="cell-icon">
					券
				</view>
				<text class="cell-tit clamp">优惠券</text>
				<text class="cell-tip" :class="{disabled: selectedCoupon.selected === false}">
					{{selectedCoupon.txt}}
				</text>
				<text class="yticon icon-you"></text>
			</view>
			<view class="yt-list-cell b-b" @click="toggleScoreMask('show')">
				<view class="cell-icon hb">
					抵
				</view>
				<text class="cell-tit clamp">积分抵扣</text>
				<text class="cell-tip" :class="{disabled: selectedScore.selected === false}">
					{{selectedScore.txt}}
				</text>
				<text class="yticon icon-you"></text>
			</view>
		</view>
		<!-- 金额明细 -->
		<view class="yt-list">
			<view class="yt-list-cell b-b">
				<text class="cell-tit clamp">商品金额</text>
				<text class="cell-tip">￥{{cartInfo.subtotal || 0.00}}</text>
			</view>
			<view class="yt-list-cell b-b">
				<text class="cell-tit clamp">优惠金额</text>
				<text class="cell-tip red">-￥{{orderDetail.pmt_amount || 0.00}}</text>
			</view>
			<!-- <view class="yt-list-cell b-b">
				<text class="cell-tit clamp">运费</text>
				<text class="cell-tip">免运费</text>
			</view> -->
			<view class="yt-list-cell desc-cell">
				<text class="cell-tit clamp">备注</text>
				<input class="desc" type="text" v-model="desc" placeholder="请填写备注信息" placeholder-class="placeholder" />
			</view>
		</view>
		
		<!-- 底部 -->
		<view class="footer">
			<view class="price-content">
				<text>实付款</text>
				<text class="price-tip">￥</text>
				<text class="price">{{subtotal || 0.00}}</text>
			</view>
			<text class="submit" @click="createOrder">提交订单</text>
		</view>
		
		<!-- 配送方式面板 -->
		<view class="mask" :class="deliveryMaskState===0 ? 'none' : deliveryMaskState===1 ? 'show' : ''" @click="toggleDeliveryMask">
			<view class="mask-content" @click.stop.prevent="stopPrevent">
				<!-- 配送方式页面，仿mt -->
				<view class="deltype-item" v-for="(item,index) in dlyTypes" :key="item.dt_id" @click="selectDlyType(index)">
					<image class="check-icon" src="/static/selected.png" v-if="item.selected"></image>
					<image class="check-icon" src="/static/select.png" v-else></image>
					<text class="deltype-name">{{item.dt_name}}</text>
					<text class="deltype-price">运费：<text>{{item.money || 0.00}}</text>元</text>
				</view>
			</view>
		</view>

		<!-- 支付方式面板 -->
		<view class="mask" :class="paymentsMaskState===0 ? 'none' : paymentsMaskState===1 ? 'show' : ''" @click="togglePaymentsMask">
			<view class="mask-content" @click.stop.prevent="stopPrevent">
				<!-- 支付方式页面，仿mt -->
				<view class="payment-item" v-for="(item,index) in payments" :key="item.app_id" @click="selectPayment(index)">
					<image class="check-icon" src="/static/selected.png" v-if="item.selected"></image>
					<image class="check-icon" src="/static/select.png" v-else></image>
					<text class="payment-name">{{item.app_name}}</text>
				</view>
			</view>
		</view>

		<!-- 优惠券面板 -->
		<view class="mask" :class="couponMaskState===0 ? 'none' : couponMaskState===1 ? 'show' : ''" @click="toggleCouponMask">
			<view class="mask-content" @click.stop.prevent="stopPrevent">
				<!-- 优惠券页面，仿mt -->
				<view class="coupon-item" v-for="(item,index) in couponList" :key="index">
					<view class="left">
					  <text class="title">{{item.coupons_info.cpns_name}}</text>
					  <text class="time">有效期至 {{item.time.to_time|formatTime(1)}}</text>
					</view>
					<view class="right">
					  <text class="unused" v-if="!item.selected" @click="useCoupon(item.memc_code, index)">立即使用</text>
					  <text class="used" v-else @click="removeCoupon(item.memc_code, index)">取消使用</text>
					</view>
				</view>
			</view>
		</view>

		<!-- 积分面板 -->
		<view class="mask" :class="scoreMaskState===0 ? 'none' : scoreMaskState===1 ? 'show' : ''" @click="toggleScoreMask">
			<view class="mask-content" @click.stop.prevent="stopPrevent">
				<!-- 积分页面，仿mt -->
				<view class="score-area">
					<view class="score-info">
						<view class="left">
							<text class="label">可用积分：</text>
							<text class="value">{{realUsagePoint}}</text>
						</view>
						<view class="right">
							<text class="label">抵扣</text>
							<text class="value">￥{{discountScore}}</text>
						</view>
					</view>
					<view class="score-input">
						<input type="number" v-model="inputPoint" placeholder="请输入积分" @input="inputScore" @confirm="useScore">
					</view>
					<view class="score-notice" v-if="discountRate > 0">
						{{discountRateNotice}}
					</view>
					<view class="score-btn" @click="useScore">确定</view>
				</view>
			</view>
		</view>

	</view>
</template>

<script>
import { formatTime } from '@/common/util';
export default {
	data() {
		return {
			fastbuy: false,
			cartInfo: { // 商品信息
				object: {
					goods: []
				},
				subtotal: 0.00,
				subtotal_price: 0.00,
				subtotal_discount: 0.00,
				items_quantity: 0,
				items_count: 0,
				discount_amount_order: 0,
				discount_amount: 0
			},
			orderDetail: { // 金额信息
				cost_item: 0.00,
				total_amount: 0.00,
				pmt_order: 0.00,
				pmt_amount: 0.00,
				total_consume_score: 0,
				total_gain_score: 0,
				total_score: 0,
				final_amount: 0,
				discount: 0
			},
			addr: {
				addr_id: ''
			},
			dlyTypes: [], // 配送方式
			deliveryMaskState: 0, // 配送方式面板显示状态
			payments: [], // 支付方式
			paymentsMaskState: 0, // 支付方式面板显示状态
			couponMaskState: 0, //优惠券面板显示状态
			scoreMaskState: 0, // 积分面板显示状态
			desc: '', //备注
			couponList: [],
			realUsagePoint: 0, // 可用积分
			usedPoint: 0, // 已用积分
			inputPoint: '',
			discountRate: 0.00, // 积分抵扣率
			maxDiscountValue: 0, // 最多抵扣金额
			requesting: false
		}
	},
	watch: {
		'addr': function (newAddr, oldAddr) {
			console.log(newAddr,oldAddr);
			let that = this;
			let area = newAddr.area || null;
			if (area) {
				let area_id = area.split(':')[2];
				that.getDlyTypes(area_id);
			}
		}
	},
	computed: {
		/**
		 * 配送方式显示
		 */
		selectedDlyType () {
			let that = this;
			let dlytype = {txt: '请选择配送方式', selected: false};
			that.dlyTypes.some(item => {
				if (item.selected === true) {
					dlytype.txt = item.dt_name + '（运费：' + item.money + '元）';
					dlytype.selected = true;
					return true;
				}
				return false;
			});
			return dlytype;
		},
		/**
		 * 支付方式显示
		 */
		selectedPayment () {
			let that = this;
			let payment = {txt: '请选择支付方式', selected: false};
			that.payments.some(item => {
				if (item.selected === true) {
					payment.txt = item.app_name;
					payment.selected = true;
					return true;
				}
				return false;
			});
			return payment;
		},
		/**
		 * 优惠券显示
		 */
		selectedCoupon () {
			let that = this;
			let coupon = {txt: '请选择优惠券', selected: false};
			that.couponList.some(item => {
				if (item.selected === true) {
					coupon.txt = item.coupons_info.cpns_name;
					coupon.selected = true;
					return true;
				}
				return false;
			});
			return coupon;
		},
		/**
		 * 积分规则显示
		 */
		discountRateNotice () {
			let that = this;
			let discountRate = that.discountRate;
			if (discountRate > 0) {
				return `${~~ (1 / discountRate)}积分抵扣1元`;
			}
		},
		/**
		 * 积分抵扣显示
		 */
		selectedScore () {
			let that = this;
			let total = that.realUsagePoint || 0;
			let score = {txt: `可用${total}积分`, selected: false};
			if (that.usedPoint > 0) {
				score.txt = that.usedPoint * that.discountRate >= that.maxDiscountValue ? `-￥${that.maxDiscountValue}元` : `-￥${that.usedPoint * that.discountRate}元`;
				score.selected = true;
			}
			return score;
		},
		/**
		 * 积分使用显示
		 */
		discountScore () {
			let that = this;
			let score = 0;
			if (that.usedPoint > 0) {
				score = that.usedPoint * that.discountRate >= that.maxDiscountValue ? that.maxDiscountValue : that.usedPoint * that.discountRate;
			}
			return score;
		},
		/**
		 * 总金额显示
		 */
		subtotal () {
			let that = this;
			let delivery = 0;
			that.dlyTypes.some(item => {
				if (item.selected === true) {
					delivery = item.money;
					return true;
				}
				return false;
			});
			let total = parseFloat(that.orderDetail.total_amount);
			total = isNaN(total) ? 0 : total;
			return total + (~~delivery); 
		}
	},
	onLoad(option){
		//商品数据
		//let data = JSON.parse(option.data);
		//console.log(data);
		let that = this;

		if (option.hasOwnProperty('fastbuy') && option.fastbuy) {
			that.fastbuy = true;
		}

		that.getDefAddr();
		that.getCartInfo();
		that.getPayments();
	},
	methods: {
		/**
		 * 获取默认收货地址
		 */
		getDefAddr() {
			let that = this;
			that.$http.post(that.$api.user.defAddr).then(res => {
				if (res.return_code === '0000') {
					if (Object.values(res.data).length > 0) {
						res.data.area_str = res.data.area.split(':')[1].split('/').join('');
						that.addr = res.data
					}
				} else {
					console.log(res);
				}
			}).catch(error => {
				console.log(error);
			});
		},
		/**
		 * 获取购物车信息
		 */
		getCartInfo () {
			let that = this;
			let data = {};
			if (that.fastbuy) {
				data.is_fastbuy = 1;
			}
			that.$http.post(
				that.$api.cart.checkout,
				data
			).then(res => {
				if (res.return_code === '0000') {
					that.cartInfo = res.data.aCart;
					that.orderDetail = res.data.order_detail;
					that.couponList = res.data.coupon_lists.map(couponItem => {
						if (res.data.aCart.object.coupon.some(usedItem => {
							if (usedItem.coupon === couponItem.memc_code) {
								return true;
							}
							return false;
						})) {
							couponItem.selected = true;
						}
						return couponItem;
					});
					that.realUsagePoint = res.data.real_usage_point;
					that.discountRate = res.data.discount_rate;
					that.maxDiscountValue = res.data.max_discount_value;
				} else {
					console.log(res);
				}
				that.$nextTick(() => {
					that.loaded = true;
				});
			}).catch(error => {
				console.log(error);
			});
		},
		/**
		 * 获取快递信息
		 */
		getDlyTypes (area_id) {
			let that = this;
			that.$http.post(
				that.$api.ectools.dlytype,
				{area_id: area_id}
			).then(res => {
				if (res.return_code === '0000') {
					that.dlyTypes = res.data;
				} else {
					console.log(res);
				}
			}).catch(error => {
				console.log(error);
			});
		},
		/**
		 * 获取支付方式
		 */
		getPayments () {
			let that = this;
			that.$http.post(
				that.$api.ectools.payment
			).then(res => {
				if (res.return_code === '0000') {
					that.payments = Object.values(res.data);
				} else {
					console.log(res);
				}
			}).catch(error => {
				console.log(error);
			});
		},
		/**
		 * 使用优惠券
		 */
		useCoupon(code, couponIndex) {

		  let that = this;
		  if (that.requesting) {
		    return false;
		  }

		  that.requesting = true;

		  that.$http.post(
				that.$api.cart.add,
				{ coupon: code, response_type: true, type: 'coupon' }
		  ).then(res => {
		    that.requesting = false;
		    if (res.return_code === '0000') {
					that.$toast('使用成功');
					that.couponList[couponIndex].selected = true;
					that.getTotal();
					that.toggleCouponMask();
		    } else {
		      console.log(res);
		      that.$toast('使用失败');
		    }
		  }).catch(error => {
		    that.requesting = false;
		    console.log(error);
		    that.$toast('使用失败');
		  });

		},
		/**
		 * 取消使用优惠券
		 */
		removeCoupon(code, couponIndex) {
			let that = this;
		  if (that.requesting) {
		    return false;
		  }

		  that.requesting = true;

		  that.$http.post(
				that.$api.cart.remove,
				{ cpn_ident: 'coupon_' + code, response_type: true, type: 'coupon' }
		  ).then(res => {
		    that.requesting = false;
		    if (res.return_code === '0000') {
					that.$toast('取消成功');
					that.couponList[couponIndex].selected = false;
					that.getTotal();
					that.toggleCouponMask();
		    } else {
		      console.log(res);
		      that.$toast('取消失败');
		    }
		  }).catch(error => {
		    that.requesting = false;
		    console.log(error);
		    that.$toast('取消失败');
		  });
		},
		/**
		 * 使用积分
		 */
		useScore (e) {
			let that = this;
			that.toggleScoreMask();
			that.getTotal();
		},
		/**
		 * 积分输入
		 */
		inputScore (e) {
			let that = this;
			let inputScore = e.detail.value;

			let disPoint = that.discountRate > 0 ? that.maxDiscountValue / that.discountRate : Infinity;
			let thresholdPoint = disPoint > that.realUsagePoint ? that.realUsagePoint :disPoint;

			if (inputScore >= thresholdPoint) {
				inputScore = thresholdPoint;
			}

			setTimeout(function () {
				that.inputPoint = inputScore;
				that.usedPoint = inputScore;
			}, 100)
			
		},
		/**
		 * 结算总额
		 */
		getTotal () {

			let that = this;

			if (!that.addr.area) {
				return false;
			}

			let area_id = that.addr.area.split(':')[2];

			let shipping_id = 0;

			// if (!that.dlyTypes.some(dlytype => {
			// 	if (dlytype.selected === true) {
			// 		shipping_id = dlytype.dt_id;
			// 		return true;
			// 	}
			// 	return false;
			// })) {
			// 	return false;
			// }

			let pay_app_id = '';

			that.payments.some(payment => {
				if (payment.selected === true) {
					pay_app_id = payment.app_id;
					return true;
				}
				return false;
			});

			let data = { pay_app_id: pay_app_id, shipping_id: shipping_id, area_id: area_id, dis_point: that.usedPoint };

			if (that.fastbuy) {
				data.isfastbuy = true;
			}
			that.$http.post(
				that.$api.cart.total,
				data
		  ).then(res => {
		    if (res.return_code === '0000') {
		      console.log(res.data);
		      that.orderDetail = Object.assign({},
		        that.orderDetail, { total_amount: res.data.total_amount, pmt_amount: res.data.pmt_amount }
		      );
		    } else {
		      console.log(res.error);
		    }
		  }).catch(error => {
		    console.log(error);
		  });
		},
		/**
		 * 显示优惠券面板
		 */
		toggleCouponMask(type){

			if (type === 'show' && this.couponList.length === 0) {
				this.$toast('暂无可用优惠券');
				return false;
			}

			let timer = type === 'show' ? 10 : 300;
			let	state = type === 'show' ? 1 : 0;
			this.couponMaskState = 2;
			setTimeout(()=>{
				this.couponMaskState = state;
			}, timer)
		},
		/**
		 * 显示配送面板
		 */
		toggleDeliveryMask (type) {
			let timer = type === 'show' ? 10 : 300;
			let	state = type === 'show' ? 1 : 0;
			this.deliveryMaskState = 2;
			setTimeout(()=>{
				this.deliveryMaskState = state;
			}, timer)
		},
		/**
		 * 显示支付方式面板
		 */
		togglePaymentsMask (type) {
			let timer = type === 'show' ? 10 : 300;
			let	state = type === 'show' ? 1 : 0;
			this.paymentsMaskState = 2;
			setTimeout(()=>{
				this.paymentsMaskState = state;
			}, timer)
		},
		/**
		 * 显示积分面板
		 */
		toggleScoreMask (type) {
			if (~~this.realUsagePoint <= 0) {
				this.$toast('暂无可用积分');
				return false;
			}
			let timer = type === 'show' ? 10 : 300;
			let	state = type === 'show' ? 1 : 0;
			this.scoreMaskState = 2;
			setTimeout(()=>{
				this.scoreMaskState = state;
			}, timer)
		},
		/**
		 * 选择配送方式
		 */
		selectDlyType (dltypeIndex) {
			let that = this;
			let dlyTypes = that.dlyTypes;

			for (let index=0; index < dlyTypes.length; index++) {
				if (index === dltypeIndex) {
					dlyTypes[index].selected = true;
				} else {
					dlyTypes[index].selected = false;
				}
			}

			that.dlyTypes = [].concat(dlyTypes);
			that.toggleDeliveryMask();
			
		},
		/**
		 * 选择支付方式
		 */
		selectPayment (paymentIndex) {
			let that = this;
			let payments = that.payments;

			for (let index=0; index < payments.length; index++) {
				if (index === paymentIndex) {
					payments[index].selected = true;
				} else {
					payments[index].selected = false;
				}
			}

			that.payments = [].concat(payments);
			that.togglePaymentsMask();
			
		},
		/**
		 * 创建订单
		 */
		createOrder () {

			let that = this;
		  if (that.requesting) {
		    return false;
			}
			
			// 收货地址
			if (!that.addr.addr_id) {
				that.$toast('请先选择收货地址');
				return false;
			}

			let shipping_id = 0;

			if (!that.dlyTypes.some(dlytype => {
				if (dlytype.selected === true) {
					shipping_id = dlytype.dt_id;
					return true;
				}
				return false;
			})) {
				that.$toast('请先选择配送方式');
				return false;
			}

			let pay_app_id = '';

			if (!that.payments.some(payment => {
				pay_app_id = payment.app_id;
				return true;
			})) {
				that.$toast('请先选择支付方式');
				return false;
			}

			// if (!that.payments.some(payment => {
			// 	if (payment.selected === true) {
			// 		pay_app_id = payment.app_id;
			// 		return true;
			// 	}
			// 	return false;
			// })) {
			// 	that.$toast('请先选择支付方式');
			// 	return false;
			// }

			that.requesting = true;

			let data = { pay_app_id: pay_app_id, shipping_id: shipping_id, addr_id: that.addr.addr_id, dis_point: that.usedPoint, memo: that.desc };
			if (that.fastbuy) {
				data.isfastbuy = true;
			}

			that.$http.post(
				that.$api.cart.order,
				data
		  ).then(res => {
				that.requesting = false;
		    if (res.return_code === '0000') {
					console.log(res.data);
					that.$toast('订单创建成功');
					setTimeout(function () {
						uni.redirectTo({
							url: '/pages/money/pay?order_id=' + res.data.order_id
						})
					}, 2000);
		    } else {
					console.log(res);
					that.$toast('订单创建失败');
		    }
		  }).catch(error => {
				that.requesting = false;
				console.log(error);
				that.$toast('订单创建失败');
		  });

		},
		stopPrevent(){}
	}
}
</script>

<style lang="scss">
	page {
		background: $page-color-base;
		padding-bottom: 100rpx;
	}

	.yticon {
		color: $font-color-light;
	}

	.address-section {
		padding: 30rpx 0;
		background: #fff;
		position: relative;

		.order-content {
			display: flex;
			align-items: center;
		}

		.icon-shouhuodizhi {
			flex-shrink: 0;
			display: flex;
			align-items: center;
			justify-content: center;
			width: 90rpx;
			color: #888;
			font-size: 44rpx;
		}

		.cen {
			display: flex;
			flex-direction: column;
			flex: 1;
			font-size: 28rpx;
			color: $font-color-dark;
		}

		.name {
			font-size: 34rpx;
			margin-right: 24rpx;
		}

		.address {
			margin-top: 16rpx;
			margin-right: 20rpx;
			color: $font-color-light;
		}

		.icon-you {
			font-size: 32rpx;
			color: $font-color-light;
			margin-right: 30rpx;
		}

		.a-bg {
			position: absolute;
			left: 0;
			bottom: 0;
			display: block;
			width: 100%;
			height: 5rpx;
		}
	}

	.goods-section {
		margin-top: 16rpx;
		background: #fff;
		padding-bottom: 1px;

		.g-header {
			display: flex;
			align-items: center;
			height: 84rpx;
			padding: 0 30rpx;
			position: relative;
		}

		.logo {
			display: block;
			width: 50rpx;
			height: 50rpx;
			border-radius: 100px;
		}

		.name {
			font-size: 30rpx;
			color: $font-color-base;
			margin-left: 24rpx;
		}

		.g-item {
			display: flex;
			padding: 20rpx 30rpx;

			image {
				flex-shrink: 0;
				display: block;
				width: 140rpx;
				height: 140rpx;
				border-radius: 4rpx;
			}

			.right {
				flex: 1;
				padding-left: 24rpx;
				overflow: hidden;
			}

			.title {
				font-size: 30rpx;
				color: $font-color-dark;
			}

			.spec {
				font-size: 26rpx;
				color: $font-color-light;
			}

			.price-box {
				display: flex;
				align-items: center;
				font-size: 32rpx;
				color: $font-color-dark;
				padding-top: 10rpx;

				.price {
					margin-bottom: 4rpx;
				}
				.number{
					font-size: 26rpx;
					color: $font-color-base;
					margin-left: 20rpx;
				}
			}

			.step-box {
				position: relative;
			}
		}
	}
	.yt-list {
		margin-top: 16rpx;
		background: #fff;
	}

	.yt-list-cell {
		display: flex;
		align-items: center;
		padding: 10rpx 30rpx 10rpx 40rpx;
		line-height: 70rpx;
		position: relative;

		&.cell-hover {
			background: #fafafa;
		}

		&.b-b:after {
			left: 30rpx;
		}

		.cell-icon {
			height: 32rpx;
			width: 32rpx;
			font-size: 22rpx;
			color: #fff;
			text-align: center;
			line-height: 32rpx;
			background: #f85e52;
			border-radius: 4rpx;
			margin-right: 12rpx;

			&.hb {
				background: #ffaa0e;
			}

			&.lpk {
				background: #3ab54a;
			}

		}

		.cell-more {
			align-self: center;
			font-size: 24rpx;
			color: $font-color-light;
			margin-left: 8rpx;
			margin-right: -10rpx;
		}

		.cell-tit {
			flex: 1;
			font-size: 26rpx;
			color: $font-color-light;
			margin-right: 10rpx;
		}

		.cell-tip {
			font-size: 26rpx;
			color: $font-color-dark;

			&.disabled {
				color: $font-color-light;
			}

			&.active {
				color: $base-color;
			}
			&.red{
				color: $base-color;
			}
		}

		&.desc-cell {
			.cell-tit {
				max-width: 90rpx;
			}
		}

		.desc {
			flex: 1;
			font-size: $font-base;
			color: $font-color-dark;
		}
	}
	
	/* 支付列表 */
	.pay-list{
		padding-left: 40rpx;
		margin-top: 16rpx;
		background: #fff;
		.pay-item{
			display: flex;
			align-items: center;
			padding-right: 20rpx;
			line-height: 1;
			height: 110rpx;	
			position: relative;
		}
		.icon-weixinzhifu{
			width: 80rpx;
			font-size: 40rpx;
			color: #6BCC03;
		}
		.icon-alipay{
			width: 80rpx;
			font-size: 40rpx;
			color: #06B4FD;
		}
		.icon-xuanzhong2{
			display: flex;
			align-items: center;
			justify-content: center;
			width: 60rpx;
			height: 60rpx;
			font-size: 40rpx;
			color: $base-color;
		}
		.tit{
			font-size: 32rpx;
			color: $font-color-dark;
			flex: 1;
		}
	}
	
	.footer{
		position: fixed;
		left: 0;
		bottom: 0;
		z-index: 995;
		display: flex;
		align-items: center;
		width: 100%;
		height: 90rpx;
		justify-content: space-between;
		font-size: 30rpx;
		background-color: #fff;
		z-index: 998;
		color: $font-color-base;
		box-shadow: 0 -1px 5px rgba(0,0,0,.1);
		.price-content{
			padding-left: 30rpx;
		}
		.price-tip{
			color: $base-color;
			margin-left: 8rpx;
		}
		.price{
			font-size: 36rpx;
			color: $base-color;
		}
		.submit{
			display:flex;
			align-items:center;
			justify-content: center;
			width: 280rpx;
			height: 100%;
			color: #fff;
			font-size: 32rpx;
			background-color: $base-color;
		}
	}
	
	/* 优惠券面板 */
	.mask{
		display: flex;
		align-items: flex-end;
		position: fixed;
		left: 0;
		top: var(--window-top);
		bottom: 0;
		width: 100%;
		background: rgba(0,0,0,0);
		z-index: 9995;
		transition: .3s;
		
		.mask-content{
			width: 100%;
			min-height: 30vh;
			max-height: 70vh;
			background: #f3f3f3;
			transform: translateY(100%);
			transition: .3s;
			overflow-y:scroll;
		}
		&.none{
			display: none;
		}
		&.show{
			background: rgba(0,0,0,.4);
			
			.mask-content{
				transform: translateY(0);
			}
		}
	}

	.deltype-item {
		display: flex;
		background: #fff;
		justify-content: center;
		align-items: center;
		margin: 20rpx 0;
		padding: 0 24rpx;
		box-sizing: border-box;
		height: 88rpx;
		line-height: 88rpx;
		.check-icon {
			width: 44rpx;
			height: 44rpx;
			flex: none;
		}
		.deltype-name {
			flex: auto;
			padding-left: 20rpx;
		}
		.deltype-price {
			flex: none;
			text {
				color: $uni-color-primary;
			}
		}
	}

	.payment-item {
		display: flex;
		background: #fff;
		justify-content: center;
		align-items: center;
		margin: 20rpx 0;
		padding: 0 24rpx;
		box-sizing: border-box;
		height: 88rpx;
		line-height: 88rpx;
		.check-icon {
			width: 44rpx;
			height: 44rpx;
			flex: none;
		}
		.payment-name {
			flex: auto;
			text-align: right;
		}
	}

	/* 优惠券列表 */
	.coupon-item{
		display: flex;
		margin: 20rpx 24rpx;
		background: #fff;
		box-shadow: 0px 0px 15rpx rgba(0,0,0,0.05);
		border-radius: 16rpx;
		padding: 40rpx 20rpx;
		box-sizing: border-box;
		.left{
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: left;
			flex: auto;
			.title {
			  font-size: 32rpx;
			  font-weight: bold;
			  color: rgba(51, 51, 51, 1);
			}
			.time {
				margin-top: 10rpx;
			  font-size: 22rpx;
			  color: rgba(153, 153, 153, 1);
			}
		}
		.right{
			flex: none;
			display: flex;
			justify-content: center;
			align-items: center;
			font-size: 26rpx;
			color: $font-color-base;
			text {
			  width: 140rpx;
				height: 52rpx;
				line-height: 52rpx;
				text-align: center;
			  background: linear-gradient(92deg, rgba(255, 80, 114, 1) 0%, rgba(255, 136, 128, 1) 100%);
				border-radius: 30rpx;
				color: rgba(255,255,255,1);
			}
			.used {
				border: 1px solid rgba(255,80,114,1);
				color: rgba(255,80,114,1);
				background: #fff;
			}
		}
	}

	.score-area {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: center;
		padding: 45rpx 0 0;
		box-sizing: border-box;
		.score-info {
			display: flex;
			justify-content: space-between;
			align-items: center;
			width: 100%;
			padding: 0 28rpx;
			box-sizing: border-box;
			.left {
				.value {
					color: $uni-color-primary;
				}
			}
			.right {
				.value {
					color: $uni-color-primary;
				}
			}
		}
		.score-input {
			padding: 0 28rpx;
			box-sizing: border-box;
			margin-top: 30rpx;
			input {
				width: 691rpx;
				height: 88rpx;
				background: $page-color-base;
				border: 1px solid rgba(238, 238, 238, 1);
				border-radius: 8rpx;
				text-align: center;
			}
		}
		.score-notice {
			margin-top: 30rpx;
			padding: 0 28rpx;
			box-sizing: border-box;
			width: 100%;
			text-align: left;
		  font-size: 28rpx;
		  line-height: 24rpx;
		  color: $font-color-light;
		}
		.score-btn {
			margin-top: 30rpx;
		  height: 88rpx;
			background: $uni-color-primary;
			color: $page-color-light;
			line-height: 88rpx;
			text-align: center;
			width: 100%;
		}
	}

</style>
