微信分享

应用签名：是jsk的md5

如果闪退就重装一下微信

微信支付：

//    字段名 变量名 类型 必填 示例值 描述

//    应用ID appid String(32) 是 wx8888888888888888 微信开放平台审核通过的应用APPID

//    商户号 partnerid String(32) 是 1900000109 微信支付分配的商户号

//    预支付交易会话ID prepayid String(32) 是 WX1217752501201407033233368018 微信返回的支付交易会话ID

//    扩展字段 package String(128) 是 Sign=WXPay 暂填写固定值Sign=WXPay

//    随机字符串 noncestr String(32) 是 5K8264ILTKCH16CQ2502SI8ZNMTM67VS 随机字符串，不长于32位。推荐随机数生成算法

//    时间戳 timestamp String(10) 是 1412000000 时间戳，请见接口规则-参数规定

//    签名 sign String(32) 是 C380BEC2BFD727A4B6845133519F3AD6 签名，详见签名生成算法注意：签名方式一定要与统一下单接口使用的一致


//    回调中errCode值列表：
//
//    名称  描述 解决方案

//0 成功 展示成功页面

//-1 错误 可能的原因：签名错误、未注册APPID、项目设置APPID不正确、注册的APPID与设置的不匹配、其他异常等。

//  -2 用户取消 无需处理。发生场景：用户不支付了，点击取消，返回APP。


    public PayWX() {
    }

    String partnerid="1515849941";
    String appId= "wxefd4941cb12bede4";
    String prepayId= "wx2611502384334995a32fca4d4243880999";

    String packageValue="Sign=WXPay";
    String nonceStr="8me8dynhjvs7rkkuin3z1q6f6svtri7j";
    String timeStamp="1543204223";
    String sign="0E9FCFF364689AB77D491CF282ED9AA4";
    private IWXAPI api;
    public  void pay_wx(String partnerid,String appId,String prepayId,String packageValue,String nonceStr,String timeStamp,String sign){
        if (null==api){
            api = WXAPIFactory.createWXAPI(APP.getInstance().getApplicationContext(),C.wxAPP_ID);
            api.registerApp(C.wxAPP_ID);
        }
        PayReq request = new PayReq();
//        request.appId = "wxd930ea5d5a258f4f";
        request.appId =appId;
//        request.partnerId = "1900000109";
        request.partnerId = partnerid;
//        request.prepayId= "1101000000140415649af9fc314aa427";
        request.prepayId=prepayId;
//        request.packageValue = "Sign=WXPay";
        request.packageValue = packageValue;
//        request.nonceStr= "1101000000140429eb40476f8896f4c9";
        request.nonceStr=nonceStr;
//        request.timeStamp= "1398746574";
        request.timeStamp=timeStamp;
//        request.sign= "7FFECB600D7157C5AA49810D2D8F28BC2811827B";
        request.sign=sign;
        api.sendReq(request);

    }
