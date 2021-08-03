#### js

##### 数据

##### 1.转数值

方法一：使用`parseInt()` 和 `parseFloat()` 函数，将被转换的数据传入`parseInt()`或者`parseFloat()`函数中

方法二：`Number()`函数，将被转换的数据传入Number()函数中

###### 转换规则：

- 如果字符串中有非数字的内容，则转换为NaN
- 如果字符串是一个空串或者是一个全是空格的字符串，则转换为0
- `true` 转成` 1`,` false` 转成 `0`
- `null `转成`0`
- `undefined`转成`NaN`

##### 2.隐士转数值

方法一：对需要转化的数据使用减法(`-`) 乘法(`*`) 除法(`/`) 比较(`==`) 运算

###### 转换规则：

- `undefined == null` 返回`true`,而`undefined === null` 返回`false`
- 隐式转换实际上调用了`Number()`函数

##### 3.转字符串

方法一：`toString()`方法,调用被转换数据类型的`toString()`方法

###### 转换规则：

- `null`和`undefined`这两个值没有`toString()`方法，如果调用他们的方法，会报错
- 该方法不会影响到原变量，它会将转换的结果返回
- 数值类型的`toString()`，可以携带一个参数，输出对应进制的值

方法二：`String()`函数将被转换的数据传入`String()`函数中

###### 转换规则：

- 有些值没有`toString()`，这个时候可以使用`String()`函数。比如：`undefined`和`null`
- 对于`Number`和`Boolean`实际上就是调用的`toString()`方法
- 对于`null`和`undefined`，就不会调用`toString()`方法.而是在内部生成一个新的字符串

方法三：被转换的数据`+''`,其实就是将被转换的数据和一个空字符串进行字符串拼接



------

##### 数组

###### 1.修改器方法

| 方法名                                           | 作用                                                         | 返回值               |
| ------------------------------------------------ | ------------------------------------------------------------ | -------------------- |
| `push(元素)`                                     | 在数组末尾添加元素                                           | 添加后数组的长度     |
| `unshift(元素)`                                  | 在数组头部添加元素                                           | 添加后数组的长度     |
| `pop()`                                          | 删除数组的末尾元素                                           | 返回删除的元素       |
| `shift()`                                        | 删除数组的第一个元素                                         | 返回删除的元素       |
| `splice(起始下标,删除个数[,插入值1,插入值2...])` | 在任意的位置给数组添加,删除或者替换任意个元素,具体方法参考: **1.删除** `splice(起始下标,删除个数)` **2.插入**`splice(起始下标,0,插入值1,插入值2...)` **3.替换**`splice(起始下标,删除个数,插入值1,插入值2...)` | 删除内容组成的新数组 |
| `reverse()`                                      | 反转数组的顺序                                               | 反转后的原数组       |

###### 2.访问方法

| 方法名                           | 作用                                                         | 返回值                                                    |
| -------------------------------- | ------------------------------------------------------------ | --------------------------------------------------------- |
| `join(字符)`                     | 用指定的字符把数组的每一项连接成字符串                       | 连接的成字符串                                            |
| `数组1.concat(数组2)`            | 把数组1和数组2合并生成一个新的数组                           | 合并后的新数组                                            |
| `slice(起始下标[,结束下标])`     | 抽取当前数组(包含起始数据,不包含结束数据)的元素创建一个新数组,省略结束下标默认截至到最后 | 创建的新数组                                              |
| `indexOf(查找项[,起始下标])`     | 从起始下标开始在数组中从前向后查找查找项,省略起始下标默认从第0开始 | 返回查找到全等匹配的数组的第一个下标,如果没有找到返回`-1` |
| `lastIndexOf(查找项[,起始下标])` | 从起始下标开始在数组中从后向前查找查找项,省略起始下标默认从最后一个元素开始 | 返回查找到全等匹配的数组的第一个下标,如果没有找到返回`-1` |

###### 3.数组的迭代方法

1.`for`循环遍历

```javascript
for(var i = 0,len = arr.length;i<len;i++){
    console.log(arr[i])
}
```

2.`forEach`遍历

遍历不会生成新的数组，没有返回值

```javascript
arr.forEach(function(value,index){
    console.log(value);
})
```

3.`map`映射

遍历数组，把函数的每一次返回值映射成新的数组并返回

```javascript
var newArr = arr.map(function(value,index){
	return value*10
})
```

4.`filter`过滤

遍历数组，把函数的每一次返回值为真的原数组中的值组成新的数组并返回

```javascript
var newArr = arr.filter(function(value,index){
	return value>10;
})
```

5.`find` 查找

遍历数组，找到满足条件的第一个元素并返回，如果没有找到返回`undefined`

```javascript
var val = arr.find(function(value,index){
	return value >10;
})
```

6.`every` 全真判断

遍历数组，所有值为真的情况下返回真，否则返回假

```javascript
var isAllTrue = arr.every(function(value,index){
	return value > 10;
})
```

7.`some`有真判断

遍历数组，有一个值为真的情况下返回真，否则返回假

```javascript
var isHasTrue = arr.some(function(value,index){
    return value > 10;
})
```

###### 3.数组排序

1.冒泡排序

- 对每一对相邻的元素进行比较。如果前面的比后面的大，就交换它们两个,从开始第一对到结尾的最后一对比较结束后最后的元素是最大的数；

```javascript
function bubbleSort(arr) {
	let len = arr.length;
	for(let i = 0; i< len-1;i++) {
		for(let j = 0; j < len-i-1; j++) {
			if(arr[j] > arr[j+1]) {
				let temp = arr[j+1];
				arr[j+1] = arr[j];
				arr[j] = temp
			}
		}
	}
	return arr
}
```

2.选择排序

- 在未排序的序列中找到最小元素，存放到排序序列的末尾。
- 再从剩余未排序元素中继续寻找最小元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。

```javascript
function selectionSort(arr) {
	let len = arr.length;
	let minIndex,temp;
	//比较的轮数
	for(let i = 0; i < len; i++) {
		minIndex = i;
		for(var j = i+1; j < len; j++){
			if(arr[j] < arr[minIndex]) {
				minIndex = j;
			}
		}
		temp = arr[i];
		arr[i] = arr[minIndex]
		arr[minIndex] = temp
	}
}
```

3.数组排序方法

- `sort()`方法默认升序排序数组,该方法会修改原数组并返回原数组

```javascript
arr.sort(function(n1,n2){
	return n1-n2
})
```

###### 4.数组去重

1.遍历数组去重

新建一个数组，遍历要去重的数组，当值不在新数组的时候`indexof==-1`就加入该新数组中

```javascript
function uniqueArray(arr){
	//初始化目标数组为空数组用来存放去除重复后的值
	let result = []
	//遍历原数组
	for(let i=0;len=arr.length; i<len;i++){
		 /**
        用原始数组中的每一项和目标数组中每一项比较
        如果有相等的值存在说明在原始数组中是重复值,则不添加该值
        如果整个目标数组都没有相等的值说明当前原数组的值不是重复值,则添加
         */
        if(result.indexOf(arr[i]) == -1){
            result.push(arr[i])
        }
    }
    return result;  
	}
}
```

2.数组下标判断法

新建一个数组，遍历要去重的数组，添加当前值是第一个找到的元素到该新数组中

```javascript
function uniqueArray(arr) {
	let result = []
	for(let i = 0, len = arr.length; i<len; i++) {
		if(arr.indexOf(arr[i]==i){
			result.push(arr[i])
		})
	}
	return result
}
```

3.先排序再去重

先将原数组排序，在与相邻的进行比较，如果不同则存入新数组

```javascript
function unique(arr){
	let arr2 = arr.sort();
	let res = [arr2[0]]
	for(let i=1;i<arr2.length;i++){
		if(arr2[i] !== res[res.length-1]){
			res.push(arr2[i])
		}
	}
	return res
}
```

4.利用对象属性唯一的特征去除数组重复值

```javascript
function uniqueArray(arr) {
	let result = []
	let obj = {}
	for(let i = 0, len = arr.length; i< len; i++) {
		obj[arr[i]] = ''
	}
	for(let attr in obj) {
		result.push(attr)
	}
	return result
}
```

###### 5.将类数组转为数组对象

```javascript
Array.prototype.slice.call(arguments)
//相当于
arguments.call()
```

