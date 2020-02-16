### 数据库论文阅读目录

该仓库将会介绍一些数据库领域的经典论文，包括SIGMOD、VLDB、ICDE、FAST、ATC中的best paper，分组了部分论文，根据自己的理解，可能不全面。

#### **论文介绍**

* Bloom Filter
2018 sigmod best paper，该论文出自andy pavlo的学生。andy在数据库方面有独特的见解。bloom filter在disk-oriented database management system中有特别
的作用：在内存快读判断一个key是否存在，这些key就是存储的磁盘上的数据本身。该结构存在两个主要问题：（1）bloom filter存在“one-side error”也就是说：if key
is present, then bloom filter returns true. 该命题的逆否命题是：如果bloom filter返回false，那么说明key一定不存在。（2）bloom filter只支持point query，
但是不支持range query。针对bloom filter存在的第一个问题，要从设计合适的hash function等角度入手解决，比较难。针对第二个问题，SuRF采用了FST数据结构解决了
不支持范围查询的问题，能够给出开区间[key, +inf）,[key1, key2], (-inf, +inf)上的range query问题。具体技术请参见原文：
SuRF: Practical Range Query Filtering with Fast Succinct Tries
