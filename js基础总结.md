# js
                 函数在严格模式下的限制：

1.不能把函数名命名为eval或arguments

2.不能把参数名命名为eval或arguments

3.不能出现两个命名参数同名的情况


                  小结：

ECMAScript中的基本数据类型包括undefined/null/Boolean/Number/和String

与其他语言不同，ECMAScript没有为整数和浮点数值分别定义不同的数据类型，Number类型可以用于表示所有数据

ECMAScript中也有一种复杂的数据类型，即Object类型，该类型是这门语言中所有对象的基础类型

严格模式为这门语言中容易出错的地方施加了限制

ECMAScript提供了很多C及其他类C语言中相同的基本操作符，包括算术运算符、布尔操作符、关系操作符、相等操作符及赋值操作符等

ECMAScript从其他语言中借鉴了很多流控制语句，例如if语句、for语句和switch语句等

ECMAScript中的函数与其他语言中的函数有许多的不同之处。

无须指定函数的返回值，因为任何ECMAScript函数都可以在任何时候返回任何值

实际上，未指定返回值的函数返回的是一个特殊的undefined值

ECMAScript中也没有函数签名的概念，因为其函数参数是意一个包含零或多个值得数组的形式传递的

可以向ECMAScript函数传递任意数量的参数，并且可以通过arguments对象来访问这些参数

由于不存在函数签名的特性，ECMAScript函数不能重载


                        变量、作用域和内存的问题

传递参数方式：1.引用方式传递
              
              2.值方式传递

typeof操作符是确定一个变量是字符串、数值、布尔值、还是undefined的最佳工具

if语句的变量声明会将变量添加到当前的执行环境中


              执行环境及作用域

全局执行环境的变量对象始终都是作用域链中的最后一个对象

                引用计数

示例：var element=document.getElementById("some_element");

      var myObject=new Object();

      myObject.element=element;
  
      element.someObject=myObject;


                  声明变量

使用var声明的变量会自动被添加到最接近的环境中

                     小结：

JavaScript变量可以用来保存两种类型的值：基本类型值和引用类型值。基本类型的值有自以下5种基本数据类型：

Undefined、Null、Boolean、Number和String。基本类型值和引用类型值具有以下特点：

1、基本类型值在内存中占据固定大小的空间，因此被保存在栈内存中；

2、从一个变量向另一个变量复制基本类型的值，会创建这个值得一个副本；

3、引用类型的值是对象，保存在堆内存中；

4、包含引用类型值得变量实际上包含的并不是对象本身，而是一个指向该对象的指针；

5、从一个变量向另一个变量复制引用类型的值，复制的其实是指针，因此两个变量最终都指向同一个对象；

6、确定一个值是哪种基本类型可以使用typeof操作符，而确定一个值是哪种引用类型可以使用instanceof操作符

所有变量（包括基本类型和引用类型）都存在于一个执行环境（也称作用域）当中，这个执行环境决定了变量的生命周期，以及哪一部分代码可以访问其中的变量

                       引用类型

1.使用new操作符后跟Object构造函数，示例如下：

var person = new Object();

person.name = "lucy";

person.age = 22;

2.使用对象字面量表示法,属性名也可以使用字符串，也可省略

    var person = {

        "name":"lily",

        "age":22,

        5:true
    }
      
3.对象字面量也是向函数传递大量可选参数的可选方式，示例如下：

function displayInfo(args){

var output="";

if(typeof args.name == "string"){

output+="Name:"+args.name+"\n";

}

if(typeof args.age=="number"){

putput+="Age:"+args.age+"\n";

}

alert(output);

}

display Info({

name:"lucy",

age:22

});

displayInfo({

name:"lily"

});

Javascript也可以使用方括号表示法来访问对象的属性。方括号语法的主要优点是可以通过变量来访问属性(除非必须使用变量来访问属性，否则建议使用点表示法)

例如：

alert(person[name]);

alert(person.name);点表示法

                            Array类型

数组的length属性很有特点-----它不是只读的。

Array.isArray()方法检测该值是不是数组

if(Array.isArray(value)){

//对数组执行某些操作

}

如果数组中的某一项的值是null或者undefined，那么该值在join()、toLocaleString()、toString()和Valueof方法返回的结果中以空字符串表示

                          重排序方法

数组中有两个可以重排序的方法：

reverse()反转数组项的排序

示例：

var values = [1,2,3,4,5];

values.reverse();

document.write(values);//5,4,3,2,1

sort()按升序排列数组项-即最小的值位于最前面，最大的值排在最后面。为了实现排序，sort()方法会调用每个数组项的toString()转型方法，然后比较得到的字符串

确定如何排序。即使数组中的每一项都是数值，sort()方法比较的也是字符串。

示例如下：

var values = [0,1,5,10,15];

values.sort();

document.write(values);//0,1,10,15,5

在比较函数传递sort()方法之后，数值仍然保持了正确的升序。当然，也可以通过比较函数产生降序排序的结果，只要交换比较函数返回的值即可。

示例：

function compare(value1,value2){

if(value1<value2){

return 1;

}else if(value1>value2){

return -1;

}else{

return 0;

}

}

var values=[0,1,5,10,15];

values.sort(compare);

document.write(values);//15/10/5/1/0

                       slice()方法 和splice 方法的区别。。。

 定义

splice() 方法 用于插入、删除或替换数组的元素。

slice() 方法 可提取字符串的某个部分，并以新的字符串返回被提取的部分。

 用法 

splice 的参数 ：splice (start, deleteCount, [item1[, item2[, . . . [,itemN]]]])

数组从 start下标开始，删除deleteCount 个元素，并且可以在这个位置开始添加 n个元素

当start ,deleteCount 均为0 的时候，也就是在数组的最前面插入新的元素。

当 参数只有 start，deleteCount 就是从start 下标开始删除deleteCount 个数组的元素，

当参数只有start参数时，就是删除 从start下标起至最后 的元素

当参数 为负的时 则该参数规定的是从数组元素的尾部开始算起的位置 （-1 指的是 数组中倒数第一个元素， -2 指的是，数组中倒数第二个元素。）

slice 参数 ： slice（start，end）；

slice 方法，在string对象和array对象 的用法上类似。 

对于数组对象来说，slice 方法提取 从 start下标起 以end下标 为结尾的 一段元素（但不包括end下标的元素），然后返回新的数组，对原数组没有任何是影响，

当参数为负时 则该参数 是从 数组的末尾 索引 开始算起，（-1 指的是 数组中倒数第一个元素， -2 指的是，数组中倒数第二个元素。）

当参数为一个参数，当为一个参数时，提取 是以 start下标起 至末尾的 部分元素。

当start 为0 时， 等于说是 克隆一个新的数组，克隆后 两个数组进行各自的操作，都互不影响，

var clone = array.slice(0)；

当然 克隆 数组还有其他办法

借用concat()函数进行数组的复制:

concat() 用于进行数组的合并。使用语法为:  arrayObject.concat(arrayX,arrayX,......,arrayX)  

concat()用于多个数组的合并，但是返回的结果是一个新的数组，而不再引用用于合并的任何一个数组。可以利用它的这个特性来用一个数组连接空数组或直接不传参数完成clone的功能.
 
var clone = array.concat();

                                           位置方法


indexof() and lastIndexof()这两个方法都接收两个参数：要查找的项和（可选的）表示查找起点位置的索引。其中indexof()方法从数组的开头（位置0）开始向后查找，lastIndexof()

方法则从数组的末尾开始向前查找。

                                            迭代方法

ECMAScript中有以下五种迭代方法：every()/filter()/forEach()/map()/some()

五种迭代方法的作用：

every()：对数组中的每一项运行给定函数，如果该函数对每一项都返回true，则返回true。

filter()：对数组中每一运行给定函数，返回该函数会返回true的项组成的数组。

forEach()：对数组中的每一项运行给定函数。这个方法没有返回值。

map()：对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组。

some()：对数组中的每一项运行给定函数，如果该函数对任一项返回true，就返回true。注：以上五种迭代方式都不会修改数组中包含的值。

                                              归并方法

ECMAScript 5 新增了两个归并数组的方法：reduce() and reduceRight()这两个方法都会迭代数组的所有项，然后构建一个返回值。

reduce()方法从数组的第一项开始，逐个遍历到最后。

reduceRight()方法则从数组的最后一项开始，向前遍历到第一项。

                                              Date类型

Date类型是在早期Java中的Java.util.Date类基础上构建的。

创建一个日期对象，使用new操作符和Date构造函数即可，示例如下：

var now = new Date();

Date.parse()和Date.UTC()

Date.parse()方法接收一个表示日期的字符串参数，然后尝试根据这个字符串返回相应日期的毫秒数。

Date.UTC()方法同样也返回表示日期的毫秒数，但它与Date.parse()在构建值时使用不同的信息.Date.UTC()的参数分别是年份，基于0的月份（一月是0，二月是1，以此类推），如果没有提供

月中的天数，则假设天数为1；如果省略其他参数，则统统假设为0.

Date.UTC()方法示例：

//GMT时间2000年1月1日午夜零时

var y2k = new Date(Date.UTC(2000,0));

//CMT时间2005年5月5日下午5:55：55

var allFives = new Date(Date.UTC(2005,4,5,17,55,55));

Date.now()方法，返回表示调用这个方法时的日期和时间的毫秒数。这个方法简化了使用Date对象分析代码的工作。

使用+操作符取得Date对象的时间戳，也可以达到同样的目的。

示例：

//取得时间

var start = Date.now();    var start = +new Date();

//调用函数

doSomething();              doSomething();

//取得停止时间
 
var stop = Date.now(),       var stop = +new Date(),
     
    result = top-start;           result = top-start;

                                        继承的方法

toLocaleString()/toString()/valueOf()

Date类型的valueOf()方法，则根本不返回字符串，而是返回日期的毫秒表示。

可以方便使用比较操作符(大于或小于)来比较日期。示例如下：

var date1 = new Date(2007,0,1); //"January 1,2007"

var date2 = new Date(2007,1,1); // "February 1,2007"

document.write(date1<date2); //true

document.write(date1>date2); //false

                                      日期格式化方法

Date类型还有一些专门用于将日期格式转化为字符串的方法，如下所示：

1、toDateString()--以特定于实现的格式显示星期几、月、日和年；

2、toTimeString()--以特定于实现的格式显示时、分、秒和时区；

3、toLocaleDateString()--以特定于地区的格式显示星期几、月、日和年；

5、toLocaleTimeString()--以特定于实现的格式显示时、分、秒；

4、toUTCString()--以特定于实现的格式完整的UTC日期。

与toLocaleString()和toString()方法一样，以上这些字符串格式方法的输出也是因浏览器而异的，因此没有哪一个方法能够用来在用户见面中显示一致的日期信息。

                                        RegExp类型

ECMAScript通过RegExp类型来支持正则表达式。使用下面类似Perl的语法，就可以创建正则表达式

var expression = /pettern/flag;

pattern部分可以是任何简单活复杂的正则表达式，每个正则表达式都可带有一活多个标识（flag），用以表示正则表达式的行为。

正则表达式的匹配模式支持下列3个标志：

g:表示全局（global）模式，即模式将被应用于所有字符串，而非在发现第一个匹配项时立即停止；

i:表示不区分大小写（case-insensitive）模式，即在确定匹配项时忽略模式与字符串的大小写；

m:表示多行（multiline）模式，即在到达一行文本末尾时还会继续查找下一行中是否存在于模式匹配的项。

示例：

//匹配字符串中所有"alt"的实例

var pattern1 = /at/g;

//匹配第一个"bat"或"cat",不区分大小写

var patten2 = /[bc]at/i;

//匹配所有已"at"结尾的3个字符组合，不区分大小写

var patten3 = /.at/gi;

其他语言中的正则表达式类似，模式中使用的所有元字符都必须转义。正则表达式中的元字符包括：

（[{\^$|)?*+.]}

这些元字符在正则表达式中都有一或多种用途，因此如果想要匹配字符串中包含的这些字符，就必须对它们进行转义。

示例：

//匹配第一个"bat"或"cat",不区分大小写

var patten1 = /[bc]at/i;

//匹配第一个"[bc]at",不区分大小写

var patten2 = /\[bc\]at/i; //转义

//匹配所有"at"结尾的3个字符的组合，不区分大小写

var patten3 = /.at/gi;

//匹配 ".at",不区分大小写

var patten4 = /\.at/gi;  //转义 

                                       RegExp实例属性

RegExp的每个实例都具有下列属性，通过这些属性可以取得有关模式的各种信息。

1.global:布尔值，表示是否设置了g标志。

2.ingnoreCase:布尔值，表示是否设置了i标志。

3.lastIndex：整数，表示开始搜索下一个配置项的字符位置，从0算起。

4.multiline:布尔值，表示是否设置了m标志。

5.source：正则表达式的字符串表示，按照字面量形式而非传入构造函数中的字符串模式返回。

面试题解答

1.块级元素：div,section,ul,dl,ol,li,dt,dd,p,h1-h6,nav...

   行内元素：span,em,time,mark,strong,a....

2.html5新增的元素属性：
 
（5个）section,nav,time,mark,header,footer.....

3.data-属性作用是什么？

  data自定义属性，本质就是给元素添加了个自定义属性

本来就没有什么特殊的，只是一个官方化的自定义属性的添加方式，在js中可以通过
datasrt统一管理。

   通常的作用，一般我们会在data中存储一些和当前元素关联度比较大的数据；
   
   一般也会用来做元素关联，比如给元素加索引。

4.css选择器的优先级顺序

id>class>tag>*  注：有坑

5.书写一个三列布局，左右各200px,中间自适应宽度

-- css --
.left {
    position: absolute;
    left: 0;
    top: 0;
    width: 200px;
}
.right {
    position: absolute;
    right: 0;
    top: 0;
    width: 200px;
}
.center {
    margin: 0 200px;
}

-- html --

< div class="left" ></div>
< div class="center" ></div>
< div class="right" ></div>

6.描述下javascript事件冒泡机制

参考：

当页面中某个元素的事件被触发以后，比如点击了页面中的某个按钮，

就触发了当前按钮的点击事件，但是 JavaScript 并不是简单就直接触发该元素的相应

事件，

而是会首先从 DOM 树的最顶层（window）依次的去触发目标（被直接点击的）元素所有

父级的同类事件，

直到触发到目标元素，然后又会再一次的从目标元素开始触发其所有父级的所有同类事

件直到window，

也就是同类型事件的目标元素与 window 之间触发一个来回，

window 到目标的触发阶段，我们称为捕获阶段，

目标触发事件的时候我们称为目标阶段，

而最后目标到 window 的触发阶段，我们称为冒泡阶段。

这种机制我们称为事件流（event flow），冒泡机制其实就是事件流机制中的冒泡阶段

规则。

出处：https://www.w3.org/TR/2016/WD-uievents-20160804/ 中的

8. "==" 和 "===" 有什么不同

又是一个经典问题，可能够真正说出原理的人，应该不多。

1. 相同的是：== 和 === 都是比较等值比较运算符，返回的布尔类型的比较结果。

2. 不同的是：

    1) == 是等值比较运算符，使用的是 抽象等值 比较算法。

       === 是严格等值比较运算符，使用的 严格等值 比较算法。

    2) == 运算符在比较值的时候，会根据两者类型是否相同而做不同的处理，

    在两者不同类型的时候，会转换类型后进行比较：

    基本类型会转成数字，引用类型会转成对象原始值，然后再进行比较。

    而 === 首先也会判断类型是否一致，不同的是如果类型不一致则直接返回 false。

资料参考：

==

- [等值比较运算符 ( == )](http://www.ecma-international.org/ecma-262/5.1/#sec-11.9.1)

- [抽象比较算法](http://www.ecma-international.org/ecma-262/5.1/#sec-11.9.3)

===

- [严格等值比较运算符 ( === )](http://www.ecma-international.org/ecma-262/5.1/#sec-11.9.4)

- [严格比较算法](http://www.ecma-international.org/ecma-262/5.1/#sec-11.9.6)

9.window.foo||(window.foo="bar"),返回值是多少？

参考："bar"


分析：

|| 又称为短路或，短路：如果左侧为真，则不再进行右侧运算，同时返回左侧表达式运

算结果。

如果左侧为假则执行右侧表达式运算，并返回右侧计算结果。

上面window.foo是不存在的，所有结果为undefined，转成boolean就是false，

那么就会运算 window.foo = "bar"，

把 "bar" 赋值给 window.foo 的同时，

返回值也是 "foo"，所以打印返回结果是 "bar"

10.$(".foo div#bar.eq(0)")请优化这段jquery选择器？

参考：$("#bar")


11.请解释jquery中.end()的用途？

参考：

返回当前jq对象的上级jq对象

分析：

1. 当我们通过$()会得到一个对象

$jq1 = $('#div1');

2. jq对象下有一系列的方法，有的方法会返回一个新的对象

// 通过$jq1的find返回了一个新的jquery对象

var $jq2 = $jq1.find('p');

3. 这个时候在$jq2下面有一个属性 prevObject，该属性保存的就是 $jq1，通过比较 

$jq2.prevObject == $jq1，会发现返回true。

4. 通过 prevObject 属性会产生一个类似原型链的引用，

而 .end() 方法就是返回就是当前 JQ 对象的 prevObject 对象，

也就是当我们 $jq2.end() 的时候，返回的就是上层的 $jq1。

12.注册号要求以字母开头，可以包含字母、数字、下划线、请写出验证该账号的正则表达式：

参考：/^[a-zA-Z]\w+$/

13.请举三种减低页面加载时间的方法。（加载时间指感知时间或者实际加载时间）

参考：

1.减少实际加载时间

  减少http请求（合并文件、合并图片） 压缩javascript、css代码
 
  启用服务器压缩传输（如gzip）

2.减少感知时间
  
   script外部脚本加载放到HTML最后进行
   
   按需加载资源（如：只加载当前能看到的区域的图片）

14."I'm lasagha hog".split("").reverse().join("");语句返回值是什么？

参考：goh angasal m'l

分析：1. split("")，拆分字符串，得到数组：

["I", "'", "m", " ", "l", "a", "s", "a", "g", "n", "a", " ", "h", "o", "g"]

2. 对数组使用.reverse()，翻转数组，得到：

["g", "o", "h", " ", "a", "n", "g", "a", "s", "a", "l", " ", "m", "'", "I"]

3. 最后使用join("")，把数组再次拼接成字符串，得到字符串：goh angasal m'I

15.$(function(){console.log(1)});和window.onload = function(){console.log(2)});

试问：上面代码执行结果是什么？能否详细说明原因？

参考：

先输出1，在输出2

分析：

这里重点是：JQ的$(function(){})和window.onload = function(){},并不的等同

1.window.onload是页面资源加载完成后触发的事件，

比如页面中有图片需要加载，那么onload是等图片加载完成以后才触发的。

2.而JQ中$(function)监听的是DOMContentLoaded事件，而该事件只需要把HTML结构加载

完成就会触发（一般我们js操作的就是页面元素，所以只需要等结构加载完成能操作页

面元素就可以了）所以该事件会比onload 事件要先触发，所以1先执行。

16.请先指出jquery中".bind()"/".live()"和"delegate()"的区别？

参考：

 bind:把函数直接绑定到指定元素的指定事件上。

 live:把函数绑定到document上，接收选择器和事件类型做为参数，当触发一个元素的事件的时候，会利

用事件冒泡到document上这一特性，判断事件目标元素和绑定参数中的选择器是否匹配，如果匹配则执行

绑定函数的执行。

 delegate:和live有点类似，但是可以指定绑定元素，而不是document，其他和live一致，但是比live更
加灵活。

17.请使用标准 的JSON格式 封装一组学生信息数据，内容包括：姓名、性别、住址（包括城市、街道、门
牌号、地铁线）

参考：

[
    {
        "name": "北京妙味",

        "gender": "男",

        "address": {

            "city": "北京",

            "street": "西二旗辉煌国际"

            "RoomNo": "6楼319室",

            "subwayLine": "13"
        }
    },
    {
        "name": "上海妙味",

        "gender": "男",

        "address": {

            "city": "上海",

            "street": "闵行区新龙路七宝宝龙城"

            "RoomNo": "T4楼9层902室",

            "subwayLine": "9"
        }
    }
]

18. 客户查询手机消费清单要求：

实现 A、B、C 三个异步接口，A 接口需传参 user_name、mobi（用户姓名和手机号码），请求成功返回该

用户此手机号码的消费清单信息，user_name 可通过接口 B 获取，mobi 可通过接口 C 获取，请使用 

JQuery 写出具体的实现方法？

参考：

function getUserName() {

    return $.ajax('/get_user_name.php');

}
function getMobi() {

    return $.ajax('/get_mobi.php');

}

$.when(getUserName(), getMobi()).then(function(data1, data2) {

    $.ajax({

        url: 'getConsumerList.php',

        data: {

            user_name: data1[0],

            mobi: data2[0],
        }

    }).success(function(consumerList) {

        //consumerList

    });
}, function() {

    console.log('获取用户名或手机号未成功');
});

js读书笔记

1.object 是向函数传递大量可选参数的首选。
   
Array类型：
   
  数组长度可改（修改此长度可以从数组的末尾溢出项或添加新页。添加新项值为undefined）

  push/unshift可传入多个参数（push多个参数从前往后插入，unshift多个参数从后往前插入数组，参数插入前后顺序不变）

var a = [];a.unshift("red","green");console.log(a) // ["red", "green"]var a = [];a.push("red","green");console.log(a)//["red", "green"]
 
 3.重排序

 a.sort排序会调用每个项的toString，排序时比较的是字符串，可接收比较函数作为参数。

var values = [10,5,2,15,3];

values.sort();

console.log(values);//[10, 15, 2, 3, 5]values.sort(compare);

console.log(values);//[2, 3, 5, 10, 15]function compare(val1,val2){

return val2-val1;
}

4.concat可接收多个参数（基于当前数组构建新数组）

var number = [3,1,2];var number2 = number.contat("red",[4,5],[6,7];console.log(number2)//[3,1,2,"red",4,5,6,7])

5.slice给当前数组中的一个或多个项创建一个新数组（取值为[2,4]包含第一个不包含第二个）
  
      var colors = ["red","green","blue","yellow","purple"];

      var color2 = colors.slice(1);

      var color3 = colors.slice(1,4);

      console.log(color2);//["green", "blue", "yellow", "purple"]console.log(color3);//["green", "blue", "yellow"]

6、splice（index，num，insertvalue1，insertvalue2，insertvalue3.。。。）以数组的方式返回被删除的项

7.位置方法

indexOf&&lastIndexOf从头往后和从后往前找

接收两个参数，查找和开始查找的index（查找遵循严格相等）

8.迭代方法

every：对数组中的每一项运行给定函数，如果函数对每一项都返回true，则返回true；

some：对数组中的每一项运行给定函数，如果该函数中的某一项返回true，则返回true；

filter：对数组中的每一项运行给定函数，返回该韩式会返回true的项的数组；（过滤筛选）

forEach：对数组中的每一项运行给定函数，无返回值。

9.缩小方法（IE9+）

reduce&&reduceRight

var val = [1,2,3,4,5];

var sum=val.reduce(function(prev,cur,index,array){

return prev+cur

});

console.log(sum)//15 第一次prev是1，cur是2.。。。。。

前端和计算机相关知识

1.你能描叙一下渐进增强和优雅降级之间的不同吗？

定义:

  优雅降级：一开始就构建站点的完整功能，然后针对浏览器测试和修复

  渐进增强：一开始只构建站点的最少特性，然后不断针对各浏览器追加功能。

  都关注于同一网站在不同设备里不同浏览器下的表现程度

区别：

 “优雅降级”观点认为应该针对那些最高级、最完善的浏览器来设计网站，而将那些被认为“过时”或有功能缺失的浏览器下的测试工作
    
请你谈谈cookie的弊端
  
 cookie虽然在持久保存客户端数据提供了方便，分担了服务器存储的负担，但还是有很多局限性的。

 第一：每个特定的域名下最多生成20个cookie。

     1.  IE6或更低版本最多20个cookie

     2. IE7和之后的版本最后可以有50个cookie

     3.Firefox最多50个cookie。
   
     4.chrome和Safari，没有做到硬性限制。

      IE和Opera会清理近期最少使用的cookie、Firefox会随机清理cookie。

     cookie的最大大约为4096字节，为了兼容，一般不能超过4095字节。

    IE 提供了一种存储可以持久化用户数据，叫做uerData，从IE5.0就开始支持。每个数据最多128K，每个域名下最多1M。这个持久化数据放在缓存中，如果缓存没有清理，那么会一直存在。

    优点：极高的扩展性和可用性

 1.通过良好的编程，控制保存在cookie中的session对象的大小。

 2.通过加密和安全传输技术（SSL），减少cookie被破解的可能性。

 3.只在cookie中存放不敏感数据，即使被盗也不会有重大损失。

 4.控制cookie的生命周期，使之不会永远有效。偷盗者很可能难道一个过期的cookie

 缺点：

1.`Cookie`数量和长度的限制。每个domain最多只能有20条cookie，每个cookie长度不能超过4KB，否则会被截掉。

2.安全性问题。如果cookie被人拦截了，那人就可以取得所有的session信息。即使加密也与事无补，因为拦截者并不需要知道cookie的意义，他只要原样转发cookie就可以达到目的了。

3.有些状态不可能保存在客户端。例如，为了防止重复提交表单，我们需要在服务器端保存一个计数器。如果我们把这个计数器保存在客户端，那么它起不到任何作用。
