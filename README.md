# HashFunctionTree
Hash算法技术研究


<pre>
常用的构造散列函数的方法
      1：直接寻址法
      2：数字分析法
      3：平方取中法
      5：折叠法
      6：随机数法
      7：除留余数法
</pre>

<pre>
一般的说，Hash函数可以简单的划分为如下几类：
     1. 加法Hash；
     2. 位运算Hash；
     3. 乘法Hash；
     4. 除法Hash；
     5. 查表Hash；
     6. 混合Hash；
</pre>

<pre>
对Java集合进行遍历删除时务必要使用迭代器

      Java集合遍历删除的方法：
            1：遍历与移除操作分离，在遍历的过程中，将要删除的数据存放在另外一个集合中，遍
               历结束之后，统一删除。
            2：使用Iterator遍历删除

      使用Iterator遍历删除的原因
            Iterator是工作在一个独立的线程中，并且拥有一个mutex锁，Iterator被创建之后会
         建立一个指向原来对象的单链索引表，当原来的对象数量变化时，这个索引表的内容不会同步
         改变，所以当索引指针往后移动时就找不到要迭代的对象，java.util.ConcurrentModificationException 异常。
         所以 Iterator 在工作的时候是不允许被迭代的对象被改变的。但你可以使用 Iterator本
         身的方法 remove() 来删除对象， Iterator.remove() 方法会在删除当前迭代对象的同时维护索引的一致性。

     基本上ArrayList采用size属性来维护自已的状态，而Iterator采用cursor来来维护自已的状态。

     当size出现变化时，cursor并不一定能够得到同步，除非这种变化是Iterator主动导致的。

     从上面的代码可以看到当Iterator.remove方法导致ArrayList列表发生变化时，他会更新
     cursor来同步这一变化。但其他方式导致的ArrayList变化，Iterator是无法感知的。
     ArrayList自然也不会主动通知Iterator们，那将是一个繁重的工作。Iterator到底还是做了努
     力：为了防止状态不一致可能引发的无法设想的后果，Iterator会经常做
     checkForComodification检查，以防有变。如果有变，则以异常抛出，所以就出现了上面的异常。
</pre>