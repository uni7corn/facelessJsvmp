<a name="b5Rk9"></a>
# facelessJsvmp是什么？
> 单栈实现的js代码虚拟化保护程序，加固代码支持在浏览器和nodejs中运行

<a name="C5UEx"></a>
# 使用说明

<a name="vr9dU"></a>
### 一.WEB页面步骤

1. 打开链接 [https://alanhays.github.io/facelessJsvmp/](https://alanhays.github.io/facelessJsvmp/)
2. 在源代码框（左边）粘贴需要加固的代码
3. 点击执行加固按钮进行加固（如出现“未解析”则表示有未适配的语法）
4. 加固代码输出后，更具需要可选择“下载代码”或“复制代码”
<a name="aA93a"></a>
### 二.项目文件步骤（环境：安装了nodejs即可）

1. test目录下的source.js文件替换为待加固的代码
2. 执行目录下的main.js进行加固（报错则表示有未适配的语法）
3. 加固结果为目录下的output.js文件
<a name="mmcGi"></a>
# 文件目录
```
├── test                    // 测试目录
│   ├── source.js           // 待加固的js源文件
│   ├── preprocess.js       // 编译前预处理的源文件
│   ├── main.js             // js代码加固程序-jsvmp （直接run即可）
│   └── output.js           // 输出的加固文件
├── pass                    // 测试通过文件目录 
│   ├── HMAC-SHA256.js      
│   ├── MD5.js                  
│   ├── SHA1.js                      
│   ├── SHA256.js                    
│   ├── SM3.js                  
│   └── SM4.js   
├── tools                   // 工具目录
│   ├── babelPlugins.js     // 打包好的环境
│   ├── dump.js             // 反编译脚本 
│   └── env.js              
├── index.html 
├── README.md               // 项目的说明文档 
├── package.json            // npm包配置文件，里面定义了项目的npm脚本，依赖包等信息 
└── package-lock.json
```
<a name="23093bb2"></a>
# 更新日志
**1.0.3 日志:**<br />1.新发现一个bug（解释器bug）<br />2.新增dump脚本（MD5反编译示例）<br />**1.0.2 日志:**<br />1.修复一个let变量相关的问题<br />2.新增web页面（丑）[https://alanhays.github.io/facelessJsvmp/](https://alanhays.github.io/facelessJsvmp/)<br />**1.0.1 日志:**<br />1.新增适配SM4加密算法<br />2.修复自执行语法执行异常问题
```javascript
(function (x) {
console.log(x)
})(0)
```
**1.0.0 日志:**<br />1.加固代码支持在浏览器和nodejs中运行
<a name="zvI5D"></a>
# 已知问题
> YieldExpression 语法未实现 ：yield 

```javascript
function* generatorFunction() {
  yield 1;
  yield 2;
  yield 3;
}
```
> SpreadElement 语法未实现：...args 

```javascript
f(...args)
```
> 解释器bug示例，由[零点大佬](https://wx.zsxq.com/dweb2/index/footprint/51514454824814)发现。表现：加固后与执行源代码结果不一致。

```
function test() {
    var list = [1, 2];
    test = function () {
        return list;
    };
    return test();
}

let y = test();
y.push(3);
console.log(test());
```

<a name="wBeMH"></a>
# 参考文献
JSVMP论文和专利：[https://surans.lanzouw.com/inJf30zj41je](https://surans.lanzouw.com/inJf30zj41je)<br />大语言模型机器人AI
