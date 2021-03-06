

# Python学习笔记

[官网:www.python.org](www.python.org)

[参考视频](https://www.bilibili.com/video/BV1qh411273b)

## 特性：

>- `解释型`、面向对象的语言、可移植性和跨平台
>- 性能较低、语法简洁
>- 应用范围：科学计算、人工智能、大数据、云计算...

Python的解释器：`CPython[主流]`、Jython...

解释器的版本：2.x 3.x

*从Python3开始学习*

![解释器和编译器的区别](vx_images/141323000246706.png)
>编译型语言：`Python、PHP、JavaScript、Ruby...`
>解释型语言：`C、C++、Go、Java...`

IDE集成开发环境：IDLE、PyCharm

>操作系统：
>- linux：centos、ubuntu、redhat等
>- mac：Catalina、Mojave、Sierra等

## 第一行代码
![第一行代码](vx_images/374370800226540.png)

## 一、基础
### 1.Python的编码

Python解释器默认编码：`utf-8`

```python
## 文本顶部修改更改编码
# -*- coding:编码 -*-

# Python相关的编码：
字符串（str）    "你好，世界"    unicode处理    一般在内存
字节（byte）    b"wofaniu..."    utf-8编码 or gbk编码    一般用于文件或网络

# 压缩成字节存储到文件中，用utf-8编码模式
data = "我".encode("utf-8")
print(data)
# b'\xe6\x88\x91'
# e6 88 91

# 将字节转换回字符串
data1 = data.decode("utf-8")
print(data1)
# 我

# ord获取单个字符的Unicode码
# ord("我")获取unicode的十进制表示

```
Python关键字

| False  | None   | True    | and      | as       | assert | async |
| ------ | ------ | ------- | -------- | -------- | ------ | ----- |
| await  | break  | class   | continue | def      | del    | elif  |
| else   | except | finally | for      | from     | global | if    |
| import | in     | is      | lambda   | nonlocal | not    | or    |
| pass   | raise  | return  | try      | while    | with   | yield |

### 2.输入语句和输出语句

关键字：`input、print`

#### input

格式：`input(prompt=None,/)`

`promp`：表示提示信息，默认为空，如果不空，则显示提示信息

`/`：函数参数最后一个斜线表示该函数只接收位置参数而不接收关键参数，但是在Python中并不允许自定义这样的函数。这样的函数一般是用C语言开发的内置函数或特定对象的方法。

Python 中的 None

`None`是一个特殊的常量`：
None和False不同。
None不是0。
None不是空字符串。
None和任何其他的数据类型比较永远返回False。
None有自己的数据类型NoneType。
你可以将None复制给任何变量，但是你不能创建其他NoneType对象。

```python
# 用户输入的任何内容本质上都是字符串，默认返回字符串
name = input("请输入用户名：")
type(name)
# <class 'str'>

# 多个变量赋值
x,y = input("请输入x,y值：")
# 请输入x,y值：ab
# x=a y=b

>>>m= input("请输入x,y值：")
请输入x,y值：ab cd
>>> m
'ab cd'
>>> m.split()
['ab', 'cd']
>>> x,y=map(str,m.split())
>>> x
'ab'
>>> y
'cd'
```

#### print

格式：`print(value, ..., sep=' ', end='\n',file=sys.stdout, flush=False)`

`value`： 表示需要输出的对象，一次可以输出一个或者多个对象（其中...表示任意多个对象），当输出多个对象时，对象之间要用逗号（，）分隔；

`sep`：表示输出时对象之间的间隔符，默认用一个空格分隔；

`end`：表示输出以何字符结尾，默认值是换行符；

`file`：表示输出位置，可将输出到文件，`file`指定的对象要有“写”的方法，默认值是`sys.stdout`（标准输出）；

`flush`：将缓存里面的内容是否强制刷新输出，默认值是False。

```python

# 会自动换行
print("Hello World")

# 一次输出三个对象，中间默认用空格隔开
>>> print('hello','world','!')
# hello world !

# 一次输出三个对象，中间用*隔开
>>> print('hello','world','!',sep='*')
# hello*world*!

# 一次输出三个对象，中间无分隔，因为sep参数值被设置为空字符串了
>>> print('hello','world','!',sep='')
# helloworld!

# 一次输出三个对象，以*结尾。
>>> print('hello','world','!',end='*')
# hello world !*

# 将输出helloworld!写入到c盘test文件夹中ok.txt文件
>>> with open('c:\\test\\ok.txt','w') as f:
	print('helloworld!',file=f)

```
### 3.注释
关键字：`#、"""`
~~~python
# 我是注释
"""
我是多行注释
我是多行注释
我是多行注释
"""
# print会自动在末尾加换行符
print("Hello World")

# 不加换行符
print("Hello World",end="")
~~~
### 4.数据类型
关键字：`int（整型）、bool（布尔）、str（字符）、list（列表）、tuple（元组）、dict（字典）、set（集合）、float（浮点）`
- 可变类型:列表(内部元素可修改)
- 不可变类型:字符串 、布尔 、整型
#### 4.1整型（int）
关键字：`bit_length()`
- py2：整型、长整型long （超出int范围自动转换long）
- py3：整型(无限制)

~~~python
# 获取二进制有多少个位组成(字节长度)
t1 = 8
result1 = t1.bit_length()
print(result1)    # 4

t2 = 9/2
print(t2)    # 4.5
~~~

#### 4.2 字符串（str）
##### 4.2.1静态方法
关键字：`startswith()、endswith()、isdecimal()、strip()、upper()、lower()、replace()、split()、format()、center()、zfill()`
> 字符串内部元素不可被修改

```python
# 判断字符串是否以XX开头或以XX结尾，返回布尔值
# startswith() 、endswith() 语法
"str".startswith("st")
"str"endswith("r")


# 判断是否是十进制数，返回布尔值
# isdecimal()【推】 、isdigit() 语法
"str".isdecimal()


# 去除字符串两边的 空格、换行符、制表符，返回一个新字符串
# strip() 、lstrip()除左边 、rstrip()除右边
"  str ".strip()
"str".strip("r")    # 去除两边的r
## 应用：验证码判断


# 字符串变大写、小写，返回新字符串
# upper()、lower()
## 应用：验证码判断


# 字符串替换，返回新字符串
# replace()
"str".replace("oldStr","newStr")


# 字符串切割，返回一个列表
# spilt() 、rsplit() 从右向左切割
"str1|str2|str3".spilt("|")
"str1|str2|str3".spilt("|",1)    # 切割一次
## 应用：找文件后缀名


# 字符串拼接，返回新字符串
# join()
"拼接字符".join(List)    # 将列表的内容拼接成字符串


# 将字符串内容居中、居右、居左，返回新字符串
# center()、ljust()、rjust()
"str".center(填充数量,"填充物")


# 填充0，返回新字符串
# zfill()
"str".zfill(限定长度，不足补0)
## 应用：处理二进制数

```

~~~python
# 单行显示
print("Hello World")
print('Hello World')
# 多行显示
print("""我是第一行
我是第二行
我是第三行
""")
print('''我是第一行
我是第二行
我是第三行
''')

print('Hello Wo "r" ld')

# 拼接字符串
print("Hello" + "World")
# 字符串重复出现,并拼接
print(3 * "我是笨蛋")
~~~

##### 4.2.2方法
关键字：`len()`
```python
# 获取长度
data = "str字符串"
len = len(data)
print(len)
# 获取字符串中的字符，索引
print(data[0]+data[1]+data[3])
print(data[-1]+data[-2]+data[-3])

# 获取字符串中的子字符串，切片
data[开始序列:取的数量]
data = "str字符串"
print(data[0:2])    # 从0开始取两个    st
print(data[0:])    # 从0开始，取到底    str字符串
print(data[:2])    # 从0开始，取两个    st
print(data[1:-1])    # 从1开始，取到倒数第一个    tr字符

# 跳着取字符串，步长
data[开始:结束:取的间隔（步长）]
data = "str字符串"
print(data[0:5:1])    # str字符
print(data[0:5:2])    # sr符

print(data[len(data):1:-1])    # 串符字r
print(data[-1:1:-2])    # 串字
print(data[::-1])    # 串符字rts

```
#### 4.3 布尔类型（bool）
~~~python
# 输出False
print(1 > 2)
print(2 > 1)
print(1 == "tom")
~~~

#### 4.4 列表（list）
关键字:`append，extend，insert，remove，clear，index，sort`
>有序可修改的,可存放不同元素类型的容器
>索引：0，1，2，3，4...oo

```python
# 定义
data_list = ["zou","data",123]
print(data_list)    # ["zou","data",123]

# 单个元素追加
list.append(元素)

# 批量元素追加
list1.extend(list2)    # 将列表2追加到列表1里
list1.extend([1,2,3,4])

# 指定位置插入
list.insert(位置,元素)

# 根据值删除
list.remove(元素)

# 根据索引删除
list.pop(元素所在序号)
list.pop()    # 默认最后一个值

# 清空列表
list.clear()

# 根据值获取索引位置（找不到元素，会报错）
list.index(元素)

# 列表排序
list.sort()    # 从小到大排序
list.sort(reverse=True)    # 从大到小排序
## sort的排序的原理：根据unicode的码表排序
## 字符串排序，比较第一个不相等的unicode码的大小，进行排序

### list中的 字符串 和 整数不能比较(报错)

# 反转列表
list.reverse()

```

```python
# 相加
data = [1,2,3,4] + [5,6,7,8,9]    # [1,2,3,4,5,6,7,8,9] 

# 相乘
data = ["你好","世界"] * 2    # ["你好","世界","你好","世界"]
```

#### 4.5 运算符in

```
# 判断元素是否在列表中
```

#### 4.6 元组（tuple）

关键字：`len()`

>有序不可修改的,可存放不同元素类型的容器
>
>“我儿子永远不能换成别人，但我儿子可用长大”

```python
V1 = (True,123,"儿子",[11,22,33,44])
# 儿子：列表[11，22，33]可增加

# 建议:在元组的最后多加一个逗号，用于标识是一个元组（当一个元素的时候让python识别为元组）
v2 = (1)	# 整型
v3 = (1,)	# 元组
v4 = ((1,),(2,),(3,))
v5 = ((1),(2),(3))
```

可相加（返回新的元组），相乘（与列表相似），获取长度len ，索引 ，切片 ，步长 。

> 索引，切片，步长均生成新的元组

字符串和列表转元组

```python
name = "你好啊"
data = tuple(name)
print(data)	# ("你","好"，"啊")
```

### 5.相互转换
关键字：`int 、str 、bool`
~~~python
# 其他所有类型转换成 bool类型，除了空字符串、整数0、空列表、空元组、空字典 以外 都是True
bool("") False
bool(" ") True
str()
int()
bool()
int('25.4')# 非法，不接受带小数的数字字符串
int('25')# 可以
float('5.64')# 可以
float('abc')# 无穷大
~~~

### 6.变量和变量名

变量名规范：
- 由`字母、数字、下划线`组成
- 不能以`数字`开头
- 不能用Python内置`关键字`
~~~python
# 给值取变量名(给变量赋值)
name = "ZOU"
age = 20
print("姓名：" + name)
print(age)
~~~

### 7.条件语句
关键字：`if、elif、else、pass`
```python
# 单条件判断语法
if 条件 :
    执行代码
else：
    执行代码


# 多条件判断语句
if 条件A:
    执行代码
elif 条件B：
    执行代码
elif 条件C:
    执行语句
else:
    执行语句


# 条件嵌套
if 条件A:
    if 条件A1:
        执行语句
    else:
        执行语句
elif 条件B:
    ...


# 统一缩进（四个空格或者Tab键）否则报错
username = input(请输入用户名：)
password = input("请输入登录密码：")
if username == "zou" and password == "123456":
    print("登录成功！")
else：
    print("登录失败！")
#一级代码，不在else里面
print("结束")

data = input("请输入一个整型：")
if int(data) % 2 == 1:
    print(data + "为偶数")
else：
    print(data + "为奇数")
    
# pass语句
if a==5
	# 没想好
	pass
else
	print("OK")
```

### 8.循环语句 
关键词：`while、while else、break、continue、for in、range`
#### 8.1 while循环（无限制循环）
```ptython
# 语法
while 条件:
    ...
    ...
    ...

# 条件不成立执行else
whle 条件
    ...
    break # 跳出整个循环，不执行else
else:
    ...
```
#### 8.2 for循环（已知数量的循环）
```python
# 相当于Java中的forach？
data = "你来打我呀"
for char in data:
    print(char)
# 你
# 来
# 打
# 我
# 呀
```
#### 8.3 range
```python
# 创建一串有序的数字，返回列表
range(开始,结束,步长)
range(5)    # range(0, 5) [0,1,2,3,4]
data = "你来打我呀"
for i in range(len(data)):
    print(data[i])
```
### 9.字符串格式化
关键字：`%、format(推荐)、f(py3.6版本)`
#### 9.1 %
```python
# 占位符%
name = "zou"
age = 20
text = "我叫%s" %name
text = "我叫%s，今年%d岁" %(name,age)
print(text)


# 可复用
text = "我叫%(name)s" %{"name":"邹"}
print(text)


text = "我叫%s"
data1 = text %("邹")
data2 = text %("zou")
print(text)

# 有占位符时，百分号%%

```
####  9.2 format
```python
#format
# 可命名,可复用
text1 = "我叫{0},今年{1}岁".format("邹",20)
text2 = "我叫{0},今年{1}岁,姓名为{0}".format("邹",20)
text3 = "我叫{name},今年{age}岁".format(name="邹",age=20)
print(text1)
print(text2)
print(text3)
# 我叫邹,今年20岁
# 我叫邹,今年20岁,姓名为邹
# 我叫邹,今年20岁


# 可复用模板
text = "我叫{0},今年{1}岁"
data1 = text.format("邹",20)
data2 = text.format("zou",18)
print(data1)
print(data2)
# 我叫邹,今年20岁
# 我叫zou,今年18岁

# 不能复用，默认{0}、{1}、{2}
text1 = "我叫{},今年{}岁".format("邹",20)
print(text1)

```
#### 9.3 f
```python
name = "邹"
age = 20
text1 = f"我是{name},今年{age}岁"
print(text1)

# {}内可执行代码运算
text2 = f"我是邹,今年{20+1}岁"
print(text2)
# 我是邹,今年21岁

text3 = f"我是{'邹'},今年{20+1=}岁"
print(text3)
# 我是邹,今年20+1=21岁

# 进制转换
text4 = f"今年{20:#o}"
print(text4)
# 今年0o24
# 十进制转16进制
```

### 10.运算符
算数运算：`// 、** `
比较运算符：``!=(python3不支持`<>`的不等于) 、%= 、**= 、//=``
```python
# x//y 取返回商的整数
# x**y 返回x的y次幂
```
成语运算：`in 、not in`
```python
# 包不包含
text1 = "le" in "AAAA" # 返回True/False
```

逻辑运算:`and 、or 、not`
```python
# and
text = "zou" and "18"
# 转换成布尔值：True and True
# text最终结果取决于最后一个为True的值
text1 = "" and "18"
# 转换成布尔值：False and True
# text最终结果取决于前面为False的值

# or的值
# 有一个为True就停止往后运算，该值为最终结果
# 有False就继续往后运算，直到有一个为True，该值为最终结果否则最终结果为最后一个为False的值


# 多个not、and和or, 先计算not，再计算and，最后计算or
text = not 0 or 4 and 3 or 7 or 9 and 6
# True or 3 or 7 or 9 and 6
# True or 3 or 7 or 6
# True or 7 or 6
# True or 6
# True
print(text)
```

#### 10.1 运算符优先级
- 算数优先级 大于 比较运算符
- 比较运算符 大于 逻辑运算符
- 逻辑运算符 not > and >or

从高到底：`加减乘除 >比较 >not and or`

### 11.Python代码运行方式
- 脚本式
![脚本提交给解释器解释](vx_images/121270317220247.png)
- 交互式（代码测试）
 ![](vx_images/463020417238673.png)
  退出交互式环境： `exit()`

### 12.Python中的各进制存在方式及转换
关键字:`bin、oct、hex`
>10进制（整型）
>2进制、8进制、16进制（字符串）

![进制转换图](vx_images/274141817226540.png)
```python
# 十进制转二进制等
# 2进制bin

t1 = bin(19) # 0b10011 0b为二进制标识
# t1 = "0b10011"
print(t1)

# 8进制oct
t2 = oct(23) # 0o27
print(t2)

# 16进制hex
t3 = hex(29) # 0x1d
print(t3)
```
```python
# 二进制转十进制等
# base=2/8/16
# base基数，可取范围0，2-36，默认十进制
i1 = int("0b10011",base=2)
i2 = int("10011",2）
# 字符串中不能出现小数点
i1 = int("0b100.11",base=2）# 非法
```
### 13.计算机中的单位
关键字：`b(bit)、B(byte)、KB(kilobyte)、、、`
- b（bit），位
```
1 ，1位
10 ，2位
101 ，3位
1001 ，4位
```
- B（byte）, 字节
```
8位是一个字节
1001 0110 ，1个字节
1001 0110 1001 0110 ，2个字节
```
- KB（kilobyte），千字节
```
1024个字节=1个千字节
1KB = 1024B = 1024*8 b
```
- M（Megabyte），兆
```
1024KB = 1M
```
- G（Gigabyte），千兆
```
1024M = 1G
```
- T（Terbyte），万亿字节
```
1024G = 1T
```
### 14.编码
关键字：`ascii 、gbk 、unicode 、utf8`
>将各种人类语言文字翻译成计算机语言（二进制）
#### 14.1 ascii（包含字母和特殊字符）
```
一个字节来表示字母与二进制的对应关系
1KB = 8位
1001100110011001 8位
2**8 = 256种可能性
```
#### 14.2 gbk（包含中日韩等文字）
> GB-2312国家信息标准委员会制作（1980年）
> GBK编码，对GB-2312的扩展，包含中日韩等文字（1995年）
>
> - 汉字2个字节
- 单字节表示，用一个字节表示对应的关系。（兼容ASCII码）
- 双字节表示，用两个字节表示对应的关系。2**16 = 65536种可能性

#### 14.3 unicode（万国码包含表情）
[Unicode官网](https://unicode.org/)
##### 14.3.1 两种标准
- Ucs2
```
用固定的2个字节表示一个文字
00000000 00000000
```
- Ucs4
```
用固定的4个字节表示一个文字
00000000 00000000 00000000 00000000
2**32 = 4294967296种可能
```
缺点：浪费空间
unicode的应用：在文件存储和网络传输时，不会直接使用unicode，在内存中会用unicode。
#### 14.4 utf-8(应用最广泛)
是对unicode的压缩，用尽量少的二进制去与文字进行对应
- 汉字3个字节
##### 压缩流程：
- 1.选用模板
```file:///E:/Project/Notebook_/Git/git使用总结.md
Unicode符号范围     |        UTF-8编码方式
(十六进制)          |              （二进制）
----------------------+----------------------------------
0000 0000-0000 007F | 0xxxxxxx
0000 0080-0000 07FF | 110xxxxx 10xxxxxx
0000 0800-0000 FFFF | 1110xxxx 10xxxxxx 10xxxxxx
0001 0000-0010 FFFF | 11110xxx 10xxxxxx 10xxxxxx 10xxxxxx
```
- 2.在模板中填入数据
```
"B" -> unicode码：0042 -> utf-8模板：0xxxxxxx
对应的二进制：1000010
填入模板：01000010
```
utf-8的应用：在文件存储和网络传输时，可将unicode转换为utf-8进行存储与传输。





## 函数

关键字：`eval`

### eval()

格式：`eval(source, globals=None, locals=None, /)`

功能：将`source`当做一个python表达式进行`解析和计算`，返回计算结果。

参数说明：`source`是一个字符串，这个字符串能表示成Python表达式，或者是能够通过编译的代码；

`globals`是可选的参数，默认为None，如果设置属性不为None的话，就必须是`dictionary`对象；

`locals`也是可选的参数，默认为None，如果设置属性不为None的话，可以是任何`map`对象。

```python
x=3
eval('x+1')
# 4
eval('3+5')
# 8
eval('{1:23,2:32}')
# {1: 23, 2: 32}
eval("__import__('os').getcwd()") #获取当前目录
'C:\\Users\\lq\\AppData\\Local\\Programs\\Python\\Python37

x=eval(input("请输入x值："))
# 请输入x值：100+200
# x=300

x=eval(input("请输入x值："))
# 请输入x值：100.36
# x=100.36

""" 
eval()函数接收一个字符串参数时，如果字符串中是表达式可以返回表达式的值；
如果字符串中是列表、元组或字典还能得到真正的列表、元组或字典；
如果字符串中是能够通过编译的代码，则可以执行代码。
"""
```

### map()

`map(function, iterable, ...)`

`function`:表示我们指定的函数

`iterable`表示要作用的序列，这个序列可以是一个也可以是多个

```python
>>> def square(x) :         # 计算平方数
...     return x ** 2
...
>>> map(square, [1,2,3,4,5]) # 计算列表各个元素的平方

# 映射多个函数
地址 = input("请输入你的地址：")
省, 市, 县 = map(str, 地址.split())
print(省, 市, 县)
"""
请输入你的地址：广东省 河源市 龙川县
广东省 河源市 龙川县
省=广东省 市=河源市  县=龙川县
"""

```

