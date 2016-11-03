| 接口名称        | 接口地址           | 接口参数  |接口方式|header|status code|
| ------------- |-------------| -----|----|----|-----|
| 用户注册      | http://api.junashare.com/juna/user/register.json | name:手机号，pass：密码，code：手机验证码 |post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|401,406,200|
| 用户登录      |http://api.junashare.com/juna/user/login.json      |name:手机号，pass:密码 |post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|401,403,406,200|
| 创建手机验证码 | http://api.junashare.com/juna/user_interface/add_mobilecode.json |name：手机号|post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|401,406,200|
| 用户登出      | http://api.junashare.com/juna/user/logout.json | 无 |post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|401，406,200|
| 易购商品列表      | http://api.junashare.com/juna/product.json | page:页码 ,time：到限时结束的秒数|get|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|401,200|
| 享什么商品列表      | http://api.junashare.com/juna/share_product.json | page:页码 ,time：到限时结束的秒数|get|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|200|
| 商品详情      | http://api.junashare.com/juna/product/商品id/detail.json | 无 |get|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|406,200，返回数据中product为商品信息，seller为商家信息|
| 加入盒子      | http://api.junashare.com/juna/product/addtobox.json | nid：商品id services_token:XXX，token的值来自于 http://api.junashare.com/services/session/token|post|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值|403,406,200|
| 盒子列表      | http://api.junashare.com/juna/boxlist.json | services_token:XXX，token的值来自于 http://api.junashare.com/services/session/token |post|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值|403,,200|
| 购买商品      | http://api.junashare.com/juna/product/buy.json | nid：商品id ,services_token:XXX，token的值来自于 http://api.junashare.com/services/session/token|post|cookie:sessioname=sessionvalue,sessioname和sessionvalue都来自于login接口的返回值|403,406,200|
| 广告      | http://api.junashare.com/juna/banner.json ||post|X-CSRF-Token:XXX，token的值来自于 http://api.junashare.com/services/session/token|200|



|http 状态码|信息|
|----------|---|
|200|成功|
|401|token错误<br/>缺少参数xxx<br/>错误的验证码<br/>用户名或密码错误|
|403|用户名 XXX 尚未激活或已被屏蔽。|用户未登录
|406|用户未登录<br/>已作为XXX登录<br/>验证码已失效<br/>手机号码错误<br/>手机验证码已使用，请重新获取<br/>手机验证码不能为空<br/>错误的验证码<br/>不支持的商品类型<br/>商品未发布<br/>商品不存在<br/>商品id都不能为空<br/>商品限时结束<br/>盒子已满，请先从盒子中删除部分商品<br/>此商品已加入盒子，不能重复加入<br/>商品已下架<br/>商品已售罄<br/>商品今天已购买|

|商品字段|商品字段描述|
|------|-----|
|title|商品名称|
|nid|商品id|
|type|product：一购商品，share_product：享什么商品|
|body.und.0.value|商品描述|
|field_price.und.0.value|一购价格|
|field_origin_price.und.0.value|享什么价格，市场价|
|field_total_num.und.0.value|商品总数|
|field_pictures.und.0.uri|图片原图路径，可以有多个图片，第二个图片地址field_pictures.und.1.uri|
|field_pictures.und.0.thumb|缩略图，可以有多个图片，第二个图片地址field_pictures.und.1.thumb|
|field_inbox_num.und.0.value|加入盒子数量|
|field_image_for_list.und.0.uri|列表页图片|

|我的盒子字段|我的盒子字段描述|
|---|---|
|nid|商品id|
|product_type|商品类型  product：一购商品，share_product：享什么商品|
|inbox_num|加入盒子数量|
|remain_num|剩余数量|
|field.und.0.thumb|商品缩略图|
|remain_boxproduct_num|还可放入盒子的商品数量|
