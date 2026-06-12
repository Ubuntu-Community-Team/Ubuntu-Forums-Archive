---
title: "How to optimize a RAM-only (swapless) system?"
date: 2010-12-22
forum: Hardware
---

### Post by coolaj86 on 2010-12-22
I'm not actually running Ubuntu, so if there's anything that Ubuntu does ahead of time to optimize for this case, I'd also like to here about it.

I'm looking for a list of settings - **sysctl**, **kernel** config, **/etc**, and otherwise - that will prevent me from banging my head against the wall.



The bugs I've already been bitten by is that if you have no swap the kernel will default to sending the **oom (out-of-memory) killer** on any random process and kill it in a fashion that to the casual observer appears to be a segfault (a segfault that nor gdb nor the powers of above will tell you isn't a segfault at all - only the kernel log).

/etc/sysctl.conf must be configured like so for a system with no swap:
```
vm.overcommit_memory = 2
vm.overcommit_ratio = 100
```


I found that **/dev/shm** has a **memory leak** in a few different versions of the kernel that are particularly profound if continuously writing and unlinking files there.

Recently someone also suggested that I look into using compressed RAM as swap (sounds like a good idea actually).
[http://code.google.com/p/compcache/](http://code.google.com/p/compcache/)

---

