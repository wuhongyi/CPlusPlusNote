<!-- README.md --- 
;; 
;; Description: 
;; Author: Hongyi Wu(吴鸿毅)
;; Email: wuhongyi@qq.com 
;; Created: 三 8月 10 19:41:07 2016 (+0800)
;; Last-Updated: 三 8月 10 19:46:41 2016 (+0800)
;;           By: Hongyi Wu(吴鸿毅)
;;     Update #: 1
;; URL: http://wuhongyi.github.io -->

# 

### 关键字

```cpp
auto bool break case catch char class const const_cast continue default delete do double dynamic_cast else enum explicit extern false float for friend goto if inline int long mutable namespace new operator private protected public register reinterpret_cast return short signed sizeof static static_east struct switch template this throw true try typedef typeid typename union unsigned using virtual void volatile while 
```

### 类型名 取值范围

```cpp
bool  false、true
char(signed char) -128~127
unsigned char 0~255
short(signed short)   -32768~32767
unsigned short0~65535
int(signed int)   -2147483648~2147483647
unsigned int  0~4294967295
long(signed long) -2147483648~2147483647
unsigned long 0~4294967295
float -3.4e-38~3.4e38
double-1.7e-308~1.7e308
long double   -1.7e-308~1.7e308
```


浮点数的相等比较，一般总是使用两者相减的值是否落在0的邻域中来判断的。abs(d1-d2)<1e-05


用new申请动态内存空间  
new 数据类型名； 或 new 数据类型名[整型常量(元素个数)]；或 new 数据类型(初始值)；

用delete释放动态内存空间  
delete 指针变量名； 或  delete []指针变量名；  
其中delete []指针变量名用于释放指针所指向的连续存储空间，即释放数组所占用的内存空间，如果被删除的是类对象，则该对象的析构函数被自动调用。对于用new建立的对象，只能使用delete进行一次运算。

使用delete释放内存空间时应注意以下几点：

	1）delete只能删除由new分配的堆内存。
	2）对于一个指针只能使用一次delete操作。
	3）当delete用于释放由new创建的数组的连续内存空间时，无论是一维数组还是高维数组，指针变量名前必须使用一对方括号，而且方括号内没有数字。


----

inline：
嵌入到主调函数中的函数称为内置函数。指定内置函数的方法很简单,只需在函数首行的左端加一个关键字inline即可。
使用内置函数可以节省运行时间,但却增加了目标程序的长度。因此一般只将规模很小(一般为5个语句以下)而使用频繁的函数(如定时采集数据的函数)声明为内置函数。
内置函数中不能包括复杂的控制语句,如循环语句和switch语句。
应当说明: 对函数作inline声明,只是程序设计者对编译系统提出的一个建议,也就是说它是建议性的,而不是指令性的。并非一经指定为inline,编译系统就必须这样做。编译系统会根据具体情况决定是否这样做。



函数的重载:
C++允许用同一函数名定义多个函数,这些函数的参数个数和参数类型不同。这就是函数的重载。即对一个函数名重新赋予它新的含义,使一个函数名可以多用。
重载函数的参数个数、参数类型或参数顺序3者中必须至少有一种不同,函数返回值类型可以相同也可以不同。在使用重载函数时,同名函数的功能应当相同或相近,不要用同一函数名去实现完全不相干的功能,虽然程序也能运行,但可读性不好,使人莫名其妙。


函数模板:
template<typename T>   //模板声明,其中T为类型参数
定义函数模板的一般形式为template < typename T> 或 template <class T>。即用虚拟的类型名T代替具体的数据类型。
用函数模板比函数重载更方便,程序更简洁。但应注意它只适用于函数的参数个数相同而类型不同,且函数体相同的情况,如果参数的个数不同,则不能用函数模板。

### 构造函数
构造函数是一种特殊的成员函数,与其他成员函数不同,不需要用户来调用它,而是在建立对象时自动执行。构造函数的名字必须与类名同名,而不能由用户任意命名,以便编译系统能识别它并把它作为构造函数处理。它不具有任何类型,不返回任何值。构造函数的功能是由用户定义的,用户根据初始化的要求设计函数体和函数参数。

有关构造函数的使用,有以下说明:

	(1) 在类对象进入其作用域时调用构造函数。
	(2) 构造函数没有返回值,因此也不需要在定义构造函数时声明类型,这是它和一般函数的一个重要的不同之点。
	(3) 构造函数不需用户调用,也不能被用户调用。
	(4) 在构造函数的函数体中不仅可以对数据成员赋初值,而且可以包含其他语句。但是一般不提倡在构造函数中加入与初始化无关的内容,以保持程序的清晰。
	(5) 如果用户自己没有定义构造函数,则C++系统会自动生成一个构造函数,只是这个构造函数的函数体是空的,也没有参数,不执行初始化操作。
	
可以采用带参数的构造函数,在调用不同对象的构造函数时,从外面将不同的数据传递给构造函数,以实现不同的初始化。构造函数首部的一般格式为:构造函数名(类型 1 形参1,类型2 形参2,...)
前面已说明: 用户是不能调用构造函数的,因此无法采用常规的调用函数的方法给出实参。实参是在定义对象时给出的。定义对象的一般格式为:类名 对象名(实参1,实参2,...);

说明:

	(1) 调用构造函数时不必给出实参的构造函数,称为默认构造函数。显然,无参的构造函数属于默认构造函数。一个类只能有一个默认构造函数。
	(2) 如果在建立对象时选用的是无参构造函数,应注意正确书写定义对象的语句。
	(3) 尽管在一个类中可以包含多个构造函数,但是对于每一个对象来说,建立对象时只执行其中一个构造函数,并非每个构造函数都被执行。

### 析构函数

具体地说如果出现以下几种情况,程序就会执行析构函数: 1.如果在一个函数中定义了一个对象(它是自动局部对象),当这个函数被调用结束时,对象应该释放,在对象释放前自动执行析构函数。2.static局部对象在函数调用结束时对象并不释放,因此也不调用析构函数,只在main函数结束或调用exit函数结束程序时,才调用static局部对象的析构函数。3.如果定义了一个全局对象,则在程序的流程离开其作用域时(如main函数结束或调用exit函数) 时,调用该全局对象的析构函数。4.如果用new运算符动态地建立了一个对象,当用delete运算符释放该对象时,先调用该对象的析构函数。   
析构函数的作用并不是删除对象,而是在撤销对象占用的内存之前完成一些清理工作,使这部分内存可以被程序分配给新对象使用。程序设计者事先设计好析构函数,以完成所需的功能,只要对象的生命期结束,程序就自动执行析构函数来完成这些工作。   
析构函数不返回任何值,没有函数类型,也没有函数参数。因此它不能被重载。一个类可以有多个构造函数,但只能有一个析构函数。  
实际上,析构函数的作用并不仅限于释放资源方面,它还可以被用来执行“用户希望在最后一次使用对象之后所执行的任何操作”,例如输出有关的信息。这里说的用户是指类的设计者,因为,析构函数是在声明类的时候定义的。也就是说,析构函数可以完成类的设计者所指定的任何操作。

调用对象既可以通过对象名,也可以通过指针。用new建立的动态对象一般是不用对象名的,是通过指针访问的,它主要应用于动态的数据结构,如链表。访问链表中的结点,并不需要通过对象名,而是在上一个结点中存放下一个结点的地址,从而由上一个结点找到下一个结点,构成链接的关系。在不再需要使用由new建立的对象时,可以用delete运算符予以释放。如果用一个指针变量先后指向不同的动态对象,应注意指针变量的当前指向,以免删错了对象。在执行delete运算符时,在释放内存空间之前,自动调用析构函数,完成有关善后清理工作。  
对象的赋值只对其中的数据成员赋值,而不对成员函数赋值。类的数据成员中不能包括动态分配的数据,否则在赋值时可能出现严重后果。

###对象的复制

有时需要用到多个完全相同的对象。此外,有时需要将对象在某一瞬时的状态保留下来。这就是对象的复制机制。用一个已有的对象快速地复制出多个完全相同的对象。如Box box2(box1);其作用是用已有的对象box1去克隆出一个新对象box2。其一般形式为:类名 对象2(对象1);用对象1复制出对象2。



<!-- README.md ends here -->