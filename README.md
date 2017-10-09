# jquery-on-user
jquery中on事件使用注意事项

### 1.首先要了解的是

```javascript
bind()是直接绑定在元素上;

live()则是通过冒泡的方式来绑定到元素上的。更适合列表类型的，绑定到document DOM节点上。较.bind()的优势是支持动态数据。（注高版本jq中已经移除此方法）
delegate()则是更精确的小范围使用事件代理，性能优于.live();

on()则是最新的1.9版本整合了之前的三种方式的新事件绑定机制（高版本jq中，最好都是用on方法）;

```
### 2.on主要是考虑在动态添加数据时，用bind失效，只能用on来实现事件绑定，方法如下：

```javascript
$(document).on("click",".btn",function(){})//这样写能实现动态数据，事件绑定;

$(".btn").on("click",function(){})//这样能实现静态事件绑定，但不能实现动态数据，事件绑定;

```

### 3.on事件在ios系统中失效

```javascript
实现事件的动态绑定确实可以，该方法在android中成功，但在ios中失效，具体原因这边不做详细说明；解决方法：在需要点击的Dom事件上添加onclick=""空事件可解决.

例如：HTML:<span onclick=""></span>

JS :   $(document).on("click","span",function(){})
```
