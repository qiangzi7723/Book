- 变量名称区分大小写
- 标识符以_ $ 以及字母开头。标识符包括变量名称和对象属性。

### 不使用var声明的变量

>> 如果在任何当前作用域链中找到num，则会执行对num属性赋值； 如果没有找到num，它才会在全局对象（即当前作用域链的最顶层对象，如window对象）中创造num属性并赋值。

不使用var声明的变量，并且如果在当前作用域链中没有找到对应的变量可以赋值，那么这个变量会作为window对象的一个属性而存在。

区分属性跟变量的方法就是属性可以通过delete进行删除，但是变量却不行。同时注意，在严格模式下，不使用var声明变量会报错。

- 尝试使用这种方式声明变量。


    var a=1,
        b=2,
        c=3

- 5种基本数据类型
    - Undefined
    - Null
    - Number
    - String
    - Boolean


    typeof function a(){}
    "function"
    var a=function(){}
    typeof a
    "function"

- 使用typeof对一个对象或者null操作时，会返回object。因为null一般用来作为空对象的引用。


### 可重写的undefined

undefined是全局对象的一个属性，自es5标准以来，这个属性都被规定成可写。

    Object.getOwnPropertyDescriptor(window, "undefined");

    configurable:false
    enumerable:false
    value:undefined
    writable:false

所以在全局的变量中，重写undefined是不会成功的，但是假设自己创建一个作用域，并使用var声明一个undefined变量是可以被重写成功的，原因不明。

    (function(){
        var undefined=2;
        console.log(undefined);
    }())

---

    (function(undefined){
        undefined=2;
        console.log(undefined);
    }())

所以有时候使用undefined进行一些判断也存在一定的风险性，不能确保当前的undefined是否被重写了。

- 使用typeof操作符检测未声明的变量不会报错。


    // 未声明的变量使用console打印会报错
    console.log(value);
    // 但是使用typeof不会报错，返回undefined
    typeof value;
