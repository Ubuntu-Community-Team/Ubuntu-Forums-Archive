---
title: "What do these vmstat values indicate?"
date: 2008-09-23
forum: General Help
---

### Post by Asham on 2008-09-23
Hello,

I am not quite sure if these stats indicate that we need more hardware. The server is running a little slow at times and I've seen the CPU meter spike so perhaps we need to optimize our code further... or can you tell (by looking at the figures) if there's a hardware bottleneck?

```
websrv:~ # vmstat 3 10
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0    112 140652 115600 1253320    0    0     1     2    2    1  1  1 98  0
 1  0    112 140916 115600 1253324    0    0     0    91   74  621 11  1 84  3
 2  0    112 141388 115600 1253336    0    0     0    12   94  545  9  0 91  0
 0  0    112 141404 115604 1253336    0    0     0   121  120  161  2  1 89  9
 0  0    112 141496 115608 1253332    0    0     0    48   41  507  8  1 89  2
 0  0    112 142936 115608 1253340    0    0     0    13   64 1453 24  2 74  0
 0  0    112 142932 115616 1253348    0    0     0    72  144  466  9  1 88  2
 0  0    112 142940 115616 1253348    0    0     0     0   18  507  9  0 91  0
 0  0    112 143208 115624 1253352    0    0     0    67  198  829 13  4 82  1
 0  0    112 136192 115624 1253364    0    0     0     0  213 1841 39  7 54  0
```
 TIA!

---

### Post by Asham on 2008-09-24
No message.

---

