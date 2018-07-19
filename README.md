# setcookie
设置cookie有效时长


```
// setCookie
function setCookie(name,value,time) {
	var strsec;
	var time1 = time.substring(1,time.length)*1;
	var time2 = time.substring(0,1);
	if( time2 == 's'){
	strsec =  time1*1000;
	}
	if( time2 == 'h'){
	strsec = time1*60*60*10000;
	}
	if( time2 == 'd'){
	strsec = time1*24*60*60*1000;
	}
	var ext = new Date();
	ext.getTime(ext.setTime()+strsec*1);
	document.cookie = name + '=' + value +'; expires='+ ext.toGMTString();
 };
 
 /*设置cookie 参数为小时*/
var setCookieHours = function(c_name, value, expiredays){
  //写cookies
  var exdate=new Date();
  // 北京时间和格林尼治时间相差8小时，所以在需要的小时基础上＋8
  exdate.setHours(exdate.getHours() + expiredays + 8);
  document.cookie=c_name+ "=" + escape(value) + ((expiredays==null) ? "" : ";expires="+exdate.toGMTString()) + ";path=/;domain=aldwx.com";
}

// delcookie
function delCookie(name) {
  var exp = new Date();
  exp.setTime(exp.getTime() + (-1 * 24 * 60 * 60 * 1000));
  var cval = GetCookieValue(name);
  document.cookie = name + "=" + cval + "; expires=" + exp.toGMTString();
};
```
```
setCookie('token',this.token,'h12');
delCookie('token');
```
