---
title: "Memory Management - IBM T43"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by dunomous on 2008-02-11
My swap is being used when there is available RAM. But I'm curious as to if I should change the swappiness so that the swap is less used, or if this would be a good idea. I understand that the swap could be in use after a high need for memory at a certain climax, and after such resources were not needed, nothing tells the memory in swap to be redistributed to cache or buffer. This may be in the wrong section, so I apologize if it is.

```
thomas@thomas:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        836        174          0        116        388
-/+ buffers/cache:        331        679
Swap:         2957         33       2924

```

```
thomas@thomas:/proc/sys/vm$ cat swappiness 
60

```

---

