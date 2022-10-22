# 【JavaScript】改变this的指向

默认情况下，this指向调用函数的对象。

``` javascript
function show(x,y){
    alert(this);
    alert(x+','+y);
}
show(10,20);
//在js中所有函数都有调用对象，而如果函数的调用对象为window，则可以省略不写。
//show(10,20)等价于window.show(10,20),this指向调用函数的对象window
```

可以通过call、apply、bind方法改变函数中this的指向。

``` javascript
window.show.call("hello",10,20);
window.show.apply("hello",[10,20]);
//将this由指向window改为指向字符串“hello”并执行
window.show.bind("hello");
//返回该函数中this的指向对象不为调用对象而是指定的固定对象的函数
```

bind的使用

``` javascript
var res=show.bind('bind');
res(10,20);
```

apply函数的使用小技巧

``` javascript
Math.min();
Math.max();
//返回传入参数的最值
//缺点，如果有一个存储数据的数组，需要将数组的元素一个一个拿出来再传入。使用apply可以解决这个问题。
var arr=[1,2,3,4,5];
alert(Math.min.apply(null,arr));
```

