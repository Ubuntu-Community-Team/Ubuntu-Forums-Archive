---
title: "usb flash drive performance - random read/write better?"
date: 2012-04-25
forum: Hardware
---

### Post by bababooey on 2012-04-25
I have 2 usb flash drives im comparing, one has great sustained read writes, but slow random read performance. The other is the opposite, slower sustained read/write performance but not too bad, but has faster small random read performance on smaller file sizes. I was wondering which would make a better drive to use as a live enviornment. Both have similar random write speeds, but the small file random read performance is such a huge difference if you look below at the benchmarks. Its as accurate as it gets, because I did the test about 5 times each drive, and the stats are about the same. Im guessing the second drive is what I want as Im not going to be making huge transfers, but when I use both drives and boot up ubuntu, its hard to tell the difference, even when I was upgrading in synaptic a bunch of files, it still took a long time to do that on both drives, regardless what the benches show. As far as usability, they both are similar, I need to find more benchmarking tools..

```



Heres the 1st one's bench
8 MB File       1          2          3          4          5
Writing MB/sec  3.31       6.51       6.25       3.27      11.28
Reading MB/sec  20.83      21.65      21.27      21.59      21.40

16 MB File      1          2          3          4          5
Writing MB/sec 4.39       6.22       8.07       4.33       5.04
Reading MB/sec 21.25      21.64      21.60      20.75      21.29

32 MB File       1          2          3          4          5
Writing MB/sec  2.65       5.39       9.32       7.44       5.52
Reading MB/sec  21.16      11.96       1.39      21.20      20.81
1KB Blocks File MB >2      4      8     16     32     64    128 
Random Read  msecs 0.74   0.73   0.73   0.76   0.73   0.73   0.73
Random Write msecs 8.35   8.29   8.50  19.75 223.39 858.68 809.26

500 Files   Write             Read             Delete
File KB     MB/sec  ms/File   MB/sec  ms/File  Seconds
2       0.42     4.93     2.92     0.70    0.002
4       3.18     1.29     4.75     0.86    0.002
8       0.87     9.43     7.07     1.16    0.002
16      1.67     9.81     9.87     1.66    0.002
32      2.97    11.04    13.26     2.47    0.002
64      2.74    23.91    15.00     4.37    0.004


Second Drive, Medium Sustained, Faster Small Random R/W

8 MB File       1          2          3          4          5
Writing MB/sec  4.64       6.72       4.15       4.35       7.07
Reading MB/sec  17.79      17.14      17.03      16.68      16.72
16 MB File      1          2          3          4          5
Writing MB/sec  4.62       5.08       4.05       2.79       3.73
Reading MB/sec  16.14      17.19      15.30      16.87      17.44
32 MB File      1          2          3          4          5
Writing MB/sec 2.59       5.29       2.88       4.44       5.53
Reading MB/sec 16.90      16.28      17.42       7.70      15.27

1KB Blocks File MB >2      4      8     16     32     64    128
Random Read  msecs 0.70   0.72   0.70   0.70   1.03   1.18   1.00
Random Write msecs 20.59   5.81  21.60  22.38  51.56  62.27  11.32

500 Files   Write             Read             Delete
File KB     MB/sec  ms/File   MB/sec  ms/File  Seconds
2           0.12    17.18     1.33     1.53    0.002
4           0.68     6.06     2.31     1.77    0.002
8           1.12     7.29     3.84     2.14    0.002
16          1.54    10.64     6.09     2.69    0.002
32          2.75    11.92    11.28     2.90    0.002
64          1.89    34.72     8.72     7.51    0.004


```

---

### Post by cmont899 on 2012-04-25
Raid0 across both :D

---

