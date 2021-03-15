## 目录

- [描述](#描述)
- [基础函数类型和语法](#基础函数类型和语法)
    - [格式化输入输出](#格式化输入输出)
    - [if和else](#if和else)
    - [while和for](#while和for)
    - [import导入模块](#import导入模块)
    - [range函数生成一个数据集合列表](#range函数生成一个数据集合列表)
    - [序列和切片](#序列和切片)
    - [列表](#列表)
    - [元组](#元组)
    - [字典](#字典)
    - [字符串和方法](#字符串和方法)
    - [得到对象的地址](#得到对象的地址)
    - [获得字符串长度和容器元素个数](#获得字符串长度和容器元素个数)
    - [系统提供的排序方法](#系统提供的排序方法)
    - [公用方法](#公用方法)
    - [散列表](#散列表)
    - 











## 描述

- **python 是解释型语言(脚本)**

- python3 不支持 python2版本 的源代码
- **python有非常严格的强制缩进语法**

- GIL全局解释锁,  保证了在多线程中, 同一时刻只有一个线程在运行

- **''#''号是python的注释符号(和脚本一样), 但却是单行注释**
    - **多行注释需要 ''' 或者 """ 来进行**

```python
#!/usr/bin/python3           
# -*- coding=utf-8 -*-
一个声明使用解释器, 一个声明该文件的编码
```



## 基础函数类型和语法

```python
a=1
print(type(a))     #type输出类型, print打印: <class 'int'>  

a="sasdtr"
print(type(a))     #输出字符串类型 <class 'str'>  

aa,bb = 1,2      #aa=1, bb= 2

b=()   #元组类型   <class 'tuple'>  
c=[]   #列表类型   <class 'list'>  
d={}   #字典类型   <class 'dict'>  

addText=2**5    # **是指数运算. 得到 2的5次方 = 32
addText**=2     # addText原有的值作为底数, 2是指数, 进行幂运算,结果给 addText
eraseText =10.5//2.7   #除法运算地板擦, 让运算结果抛除小数点,得到 3.0 整数, 不会进行四舍五入


#python不支持 && || ! 这样的逻辑运算符, 替换成 and , or , not
#但 |  &  ~ 还是支持的 , 或运算,与运算,取反
#优先级:  () -> not ->  and  ->or     not最大
c,d=2,1
e=~c           # e=-2
d= not c>d     #d= False   是个布尔类型, c大于了d,但结果取反,所以是 False
```

### 格式化输入输出

```python
#使用 input("提示语") 来进行输入, 但却会造成阻塞,输入结束后,会自动解除
strd=input("请输入字符串")
intd=int(input("请输入数字"))     #将输入转换为 int 类型


#格式化数据输出, 没有逗号, %() 所有的变量都在这里, 会自动换行
# {} 也是占位符, 配合 .format() 来输出.会自动进行格式化转换
inum,fun=20,30.3
print("str%s , int %d , float %.2f" %( "STR", inum, fun))
print("str{} , int {} , float{}" .format("STR",inum, fun))


#将末尾自动添加的换行删除掉
print("%d,%d\t",%(1,2), end='')    
```







### if和else

**if是靠 缩进 来判断下面的代码块是否属于需要执行的内容, 一旦缩进不正确就会报错.**

```python
#单 if语句
num=1
bre=2
if num==1 and bre==2:       #条件成立 直接进入 ,and , or ,not
    print("这里会执行")
    print("这里持续向下会执行")
    pass    #空语句,什么都不做, 也可以用来结束if, 也可以不写




#if和else配合语句
num=1
if    num > 1 :  #num并不大于2, 但是进行了 not 取反
	print("执行块")
    pass   #空语句,什么都不做, 也可以用来结束if
elif num == 1:
	print("elif执行块结束")    
    pass   



#if和elif 以及else
#一定要注意缩进
import random
num=random.randint(0,2)
bre=9
if  num > 1 :  #num并不大于2, 但是进行了 not 取反
    if bre==9:
        print("执行块",end='')
        print("bre==9")
    print("num>1")
elif num == 1 :
    print("elif执行块结束2",end='') 
    print("num==0")
elif num < 0 :
    print("elif执行块结束4",end='')
    print("num<0")
else:
    print("asdadas")
print("结束")
```



### while和for

```python
#while 打印99乘法表的范例

right=9
left=1
while right > 0 :
    while  left <= right :
        print("{}*{}={}   ".format(left,right,left*right),end='')
        left+=1
    right-=1
    left=1
    print()
    pass      #可有可无


#for 循环赋值 自动遍历
tags='abcds'
for item in tags :
    print(item)

    
#for 与 else: 
# 当 for正常结束,else会执行, 当for是通过 break 终止退出的, else就不会执行
#while 也适用于下面的语法
strS='abcd'
for item in strS :
    if item == 'b' :
	    break
else:
    print('这里不会执行')
print('done')

```



### import导入模块

```python
import random     #直接倒入产生随机数的模块

num=random.randint(0,2)    #使用模块, 代表num 会得到一个 0 1 2中的某个int类型元素, 范围随机数
```





### range函数生成一个数据集合列表

`range` 生成出来的是对象. 里面存放数据 `<class 'range>'`

```python
#range(开始,结束,步长) , 步长就是跳跃式取值,包括开始处. 步长不能为0

tags=range(10,20)
for item in tags :
    print(item)

#会输出 10 , 11, 12 .... 19 

ppt=range(10,20,2)
for item in ppt :
    print(item)
#会输出  10 ,12 , 14 , 16 .... 19
    
```





### 序列和切片

- **序列就是数组**
- 字符串,  列表,  元组.   (字典并不属于序列)
- **优点: 可以支持 索引和切片的操作**
    - **下标会越界, 切片不会**
        - **切片语法: [起始下标 : 结束下标 : 步长]**
- **特征: 第一个索引是0** 
    - **当第一个索引位负数的时候,指向的是右端最后的那个元素**

```python
c=[]   #列表类型   <class 'list'>  

#字符串列表输出和方法
text='abcdefgh'
print(text[2:4])  #输出 cd    .属于左闭右开原则. (a,c]
print(text[3:])   #输出 defgh 从下标 3 开始,到末尾
print(text[:5])   #输出 abcde
print(text[::-1])  #倒叙输入, hgfedcba ,  -1表示方向, 从右向左进行
print(text[1:6:2])  #输出 bdf, 每隔2进行输出, 计算截取出来的串
print(text[-4:-1])  #输出 efg  从左到右进行输出, 从左到右进行计算元素下标 输出中间元素(不能反过来)
```



### 列表

- **列表与序列表示方法是相同的**
    - **有序的数据集合, 就是list容器**
    - **使用方式和函数均以list容器相同**

```python
c=[]   #列表类型   <class 'list'>  

resd=list(range(10))  #将range类型的数据 转换为list列表类型,并赋值给resd, 普通类型不能转换

#直接插入元素
li=[1,2,3,"字符串",0.5]    #可以混合插入,不限制类型

li.append(1)    #在末尾插入元素
li.extend(resd) #拓展, 批量添加,就是将另一个列表的所有元素插入到 li 这个元素内,还可以直接[1,23]
li.count(1)     #在列表中,寻找1这个元素, 并显示出现的次数
li.index(1)     #获得 1 这个元素, 第一次出现的下标
li.pop(0)       #删除括号内设置的下标元素, 如果没有参数,就默认删除结尾的
del li[0:5]     #删除0到5范围的元素, 也就是下标元素
li.remove(20)   #移除指定的元素
li.reverse()    #反转列表
li.sort()       #排序

print(li)       #会打印列表内的所有元素, 并用逗号间隔  [1,2,3]

for item in li:     #for 循环遍历,仅仅输出元素
	print(item, end=' ')    
```



### 元组

- **元组是不可变的序列, 创建之后不能做任何修改**
- **用() 来创建元组类型,数据项用 , 分割**
    - **当元组内只有一个元素时,末尾要加上逗号,不然解释器会当作整形来处理**

```python
b=()   #元组类型   <class 'tuple'>  

tupleA=(1,2,"字符串",[5,4,"列表类型"])

print(tupleA[1:2])   #切片操作, 只输出 2 这个元素
print(tupleA[::-1])  #切片操作, 倒叙输出, 如果是-2 ,则每两个取一个
print(tupleA[-2:-1])  #切片操作,从右到左的第二个和 从右到左的第一个元素, 会输出 "字符串" 这个元素

tupleB=tuple(range(10))   #强制类型转换
```



### 字典

- 使用 {} 来创建字典
    - **就是 map 二叉树容器**
- **键值对方式存储数据. { 'key1' : 'value1', 'key2':'value2' }**
    - key不可重复, 且不可修改, 如果key重复,那么会发生覆盖操作
- **可以使用key的值当作下标进行访问.**

```python
dictA={1:2, "asd":"asd" }    #字典类型   <class 'dict'>  

dictA['name']='Linus'    #插入一个键值对元素
dictA[1]=2               #同样可以插入
dictA['name']='luke'     #修改键值对应的value值	
dictA.update({'na':1})   #增加或修改, 存在即修改, 不存在就增加 
del dictA['name']        #删除指定的键值对
dictA.pop('name')        #删除指定的键值对

print(dictA.keys())  # 输出所有的 键
print(dictA.values())  #输出所有的值
print(dictA.items())   #输出所有的键值对

print(dictA['name'])    # 输出 1 这个键值内的value值
print(len(dictA))   # 输出元素的个数

for key,value in dictA.items():
    print('%s==%s' %(key,value))    #输出 键==值
```







### 字符串和方法

```python
#常用字符串方法
.capitalize()     #首字母变大写
.endswith('c')    #字符串是否以 字符c 结尾
.startswith('c')  #字符串是否以 字符c 开头
.find()           #查找,返回的是下标位置, -1 表示不存在

.isalnum()        #判断是否是字母和数字
.isalpha()        #判断是否是字母
.isdigit()        #判断是否是数字
.islower()        #判断是否是小写

.join()           #循环取出所有值 用 新值去连接

.lower()          #所有字符转换为小写
.upper()          #所有转换为大写
.swapcase()       #所有字符大写变小写, 小写边大写

.lstrip()         #移除左侧空白
.rstrip()         #移除右侧空白
.strip()          #移除两侧空白

.split()          #切割字符串
```



### 得到对象的地址

```python
text='abcd'
print(id(text))
# id 会输出找个对象的地址,一般为 4374549424 这样的一串数字
```



### 获得字符串长度和容器元素个数

```python
a=[1,2,3,4,"asda"]
print(len(a))     #输出5
```

### 系统提供的排序方法

```python
iia=["asd","bb"]
resiia = sorted(iia)     #通过 ascii 编码进行排序从小到大

pa={'a':'aa' , 'b':'bb' , 'c' : 'cc' }
respa = sorted(pa.items(), key=lambda d:d[0])    #0按照键排序, 1按照值排序. 必须同类型
```

### 公用方法

```python
#合并操作 ,两个对象相加操作,会合并两个对象 , 适用于 字符串,列表,元组
listA=list(range(10))
listB=list(range(10,20))
print(listA+listB)   

#复制,  对象自按指定次数进行+操作, 适用于 字符串,列表,元组
print("字符串"*3)      #会输出三次字符串 和一个换行

#in 判断元素是否存在,  判断元素是否存在于对象中, 适用于字符串,列表,元组,字典
print('生' in "生生不息" )   #生 存在于 生生不息中, 输出 True
```



### 散列表

```python
book = dict()       #dict 函数会创建散列表 , 字典类型   <class 'dict'> 
book2 = {}          #也是散列表, 简写形式

book['apple']=0.67    #添加apple键, 值为0.67
book['red'] = ['a', 'b', 'c']   #一个键值,可以对应多个实值

print(book['apple'])  #会查询散列表,获得 0.68这个值, 并输出

value = book.get('apple')  #查询 apple 是否存在于散列表中,存在则返回 值0.67 ,否则 None
```

