@[toc]
# 前记
一直想要对python的几种数据结构进行一下对比，刚好复习了一波y总的课程，这里对比一下python中的这些数据结构，方便自己使用时候会更加清晰

# 数据结构介绍
## 字符串
### 表示方法
`''` `""` `"""..."""` 或 `'''...'''`
### 字符串运算
`*` :表示重复

`+`: 表示合并  空格也可以合并（**统一用加号就行**）空格对于变量不行
```python
    3  *  'un'  +  'ium'
    'unununium'
```
### 字符串索引
正向和负向索引
```python
    word  =  'Python'
    >>> word[0]  # character in position 0
    'P'
    >>> word[5]  # character in position 5
    'n'
    
    word[-1]  # last character
    'n'
    >>> word[-2]  # second-last character
    'o'
    >>> word[-6]
    'P'
```

### 字符串切片
满足前闭后开规则

```python
word  =  'Python'
word[0:2]  # characters from position 0 (included) to 2 (excluded)
'Py'
word[2:5]  # characters from position 2 (included) to 5 (excluded)
'tho'
```
- 省略开始索引时，默认值为 0，省略结束索引时，默认为到字符串的结尾：

- 索引不可以越界

- 切片能自动处理越界问题

- 字符串不能修改，是immutable的，修改会报错

- 要生成不同字符串，只能新建一个

- `len()` 返回字符串的长度

## 列表
### 表示方法
使用中括号
```python
    squares  =  [1,  4,  9,  16,  25]
    >>> squares
    [1, 4, 9, 16, 25]
```
### 索引与切片
```python
    squares[0]  # indexing returns the item1
    >>> squares[-1]
    25
    >>> squares[-3:]  # slicing returns a new list
    [9, 16, 25]
```
切片操作返回包含请求元素的新列表

```python
    squares[:]
    [1, 4, 9, 16, 25]
```
### 运算规则
- 合并

```python
    squares  +  [36,  49,  64,  81,  100]
    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

```
### 列表可编辑
```python
    >>> cubes  =  [1,  8,  27,  65,  125]  # something's wrong here
    >>> 4  **  3  # the cube of 4 is 64, not 65!
    64
    >>> cubes[3]  =  64  # replace the wrong value
    >>> cubes
    [1, 8, 27, 64, 125]
```
为切片赋值会改变原来的值
```python
    >>> letters  =  ['a',  'b',  'c',  'd',  'e',  'f',  'g']>>> letters
    ['a', 'b', 'c', 'd', 'e', 'f', 'g']
    >>> 修改切片的值
    >>> letters[2:5]  =  ['C',  'D',  'E']
    >>> letters['a', 'b', 'C', 'D', 'E', 'f', 'g']
    >>> 清除部分值
    >>> letters[2:5]  =  []
    >>> letters['a', 'b', 'f', 'g']
    >>> # 清空列表
    >>> letters[:]  =  []
    >>> letters[]
```


### 常用成员函数
- `append()` 方法可以在列表结尾添加新元素:  string 没有append()操作

```python
    >>> cubes.append(216)  # add the cube of 6
    >>> cubes.append(7  **  3)  # and the cube of 7
    >>> cubes
    [1, 8, 27, 64, 125, 216, 343]
```
- 内置函数`len()` 也可以支持列表
```python
    >>> letters  =  ['a',  'b',  'c',  'd']
    >>> len(letters)
    4
```
-  sort()
```python
a = [1, 3, 2]
a.sort()
[1, 2, 3]
```
- reverse()
```python
a = [1, 3, 2]
a.reverse()
[2, 3, 1]
```
或者
`a[::-1]` 也可以实现翻转的效果
### 嵌套操作
```python
    >>> a  =  ['a',  'b',  'c']
    >>> n  =  [1,  2,  3]
    >>> x  =  [a,  n]
    >>> x
    [['a', 'b', 'c'], [1, 2, 3]]
    >>> x[0]
    ['a', 'b', 'c']
    >>> x[0][1]
    'b'
```

### 列表遍历操作
```python
    >>> words  =  ['cat',  'window',  'defenestrate']
    >>> for  w  in  words:
            print(w,  len(w))
```


### 列表奇技淫巧
```python
    a = [0] * 10
    b = [0 for i in range(10)]
```
赋值操作
```python
    a = []
    for i in range(10):
        a.append(i*i)
    
    b = [i*i, for i in range(10)]
```

## 元组
列表可以修改，元组不能修改
### 表示方法
小括号或者是不用括号

```python
    b = (1, 2, 3)
    b[1]   # 2
    b[1] = 1  # 错误，元组对象不能修改
```
元组可以多元赋值
```python
    x,y,z = b # 实际上是(x, y, z) = b
    # x = 1, y = 2, z = 3
```


### 元组奇技淫巧
复合赋值方式
```python
    a,  b  =  b,  a  # 交换两个变量
```
```python
    >>> a,  b  =  0,  1
    >>> while  a  <  100:   
            print(a,  end=',')  # 可以取消最后换行，以另一种方式结尾
            a,  b  =  b,  a+b
    
    0,1,1,2,3,5,8,13,21,34,55,89
```


## 集合
和`C++` 集合定义一样，会去重操作, 用`{}` 表示




### 方法

添加元素使用`add`操作，对比列表的`append`
```python
    a = set() # 定义一个集合
    a.add(1)  # {1}
    a.add(2)  # {1,2}
    a.add(1)  # {1,2}
```

### 应用：去重
```python
    a = [1,2,3,2,5]
    b = set(a) # b = {1,2,3,5}
    c = list(b) # c = [1,2,3,5] 
```

## 字典
对应`C++`的`map`, 一堆key-value对, 字典可以进行修改


```python
    tel  =  {'jack':  4098,  'sape':  4139}
    tel['guido']  =  4127 #添加一个新的元素 
    # {'jack': 4098, 'sape': 4139, 'guido': 4127}
    tel['jack']  # 查看一个元素的值
    del  tel['sape'] # 删除一个元素
    tel['irv']  =  4127 # 修改一个元素
    list(tel)        # key形成一个列表 ['jack', 'guido', 'irv']
    sorted(tel)      # 按key进行排序成一个列表 ['guido', 'irv', 'jack']
    
    # 构造函数可以直接用键值对序列创建字典
    dict([('sape',  4139),  ('guido',  4127),  ('jack',  4098)]) 

```

### 字典遍历
```python
    # Create a sample collectionusers  =  {'Hans':  'active',  'Éléonore':  'inactive',  '景太郎':  'active'}
    # Strategy:  Iterate over a copy
    for  user,  status  in  users.copy().items(): 
        if  status  ==  'inactive': 
            del  users[user]
    # Strategy:  Create a new collection
    active_users  =  {}
    for  user,  status  in  users.items(): 
        if  status  ==  'active': 
            active_users[user]  =  status

```
# 表格对比
|名称  | 可修改性 | append  | 合并性  |  索引&切片| len|
|--|--|--|  --|--|-- |
|字符串 | × | × | √   |√| √ |
|列表 | √ |  √ |  √  | √ | √ |
|元组 | × |  × |  √  | √ | √ |
