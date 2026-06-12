---
title: "What do these memory numbers tell me?"
date: 2023-03-29
forum: Hardware
---

### Post by sofasurfer on 2023-03-29
I increased my memory from 4g to 16g. Heres my new $ free -h output. ```
  $ free -h
              total        used        free      shared  buff/cache   available
Mem:           15Gi       2.8Gi       4.5Gi       309Mi       8.2Gi        12Gi
Swap:         2.0Gi          0B       2.0Gi
 
```
It shows my total memory at 15gig. But my used mem is 2.8gig and my free mem is 4.5gig. Shouldn't "used" and "free" equal "total". Please interpret these numbers and tell me of any changes I should make. 
I also intend to increase my swap space.

I am using an Dell Inspiron 660 motherboard rated for 8gig total memory but some websites said it would use up to 16gig so thats what I am doing.

---

### Post by Doug S on 2023-03-29
You have recoverable memory cache and buffers. The relevant number is "available memory". Here is an example where I specifically tell the kernel to delete memory caches and buffers between the 2 free commands:

```
doug@s19:~/c$ sudo /home/doug/c/flush_memory
              total        used        free      shared  buff/cache   available
Mem:          31924         388         286           3       31249       31067
Swap:          2047           0        2047
              total        used        free      shared  buff/cache   available
Mem:          31924         293       31475           3         156       31286
Swap:          2047           0        2047
```and the script:
```
doug@s19:~/c$ cat /home/doug/c/flush_memory
#! /bin/bash
free -m
sync
echo 3 > /proc/sys/vm/drop_caches
free -m
```

---

