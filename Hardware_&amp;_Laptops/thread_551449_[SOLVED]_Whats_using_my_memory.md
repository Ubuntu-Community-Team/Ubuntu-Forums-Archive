---
title: "[SOLVED] Whats using my memory?"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by dougleduck on 2007-09-15
Adding up my memory currently looking at the processes I get a total of around 130MB.

However when looking at my resources I get 206.7MB of 512 of my RAM 

and also 93.2 of 730MB of SWAP used.

How does 130 MB in processes turn into 300MB in resources?

I'm running Feisty on Dell Inspiron 1100 laptop with 256MB of RAM (which im trying to upgrade to 512) and with 730 MB swap space, so my RAM is important to me.

Any help would be great.

---

### Post by nick_h on 2007-09-15
I think the Inspiron 1100 uses shared video memory so that will account for some.  Some will also be allocated as cache.

You can look at the memory you are using with
```
top
```
or
```
free -m
```

You may also find it useful to read the [Gentoo FAQ](http://gentoo-wiki.com/FAQ_Linux_Memory_Management) on Linux memory management.

---

### Post by dougleduck on 2007-09-15
Thanks thats very helpful. I blatantly know little about memory.

Well I think the cache explains why so much of my memory is being used. Why is so little of the cache free?



             total       used       free     shared    buffers     cached
Mem:           248        235         13          0          3         77
-/+ buffers/cache:        154         94
Swap:          729        141        587

---

### Post by nick_h on 2007-09-16
> Why is so little of the cache free?
This is explained in the third paragraph of the FAQ I posted.  The linux philosophy is that memory unused is memory wasted.  Therefore programs are kept in memory when not used - in this way if they are needed again there is no need to reload them.  If the memory is needed for something else then cache can easily be freed. Linux will try to use as much memory as possible.

---

### Post by dougleduck on 2007-09-16
I meant more specifically why the disparity between used cache and free cache? Or is it that the rest is used by buffers (which to my understanding are 'queuing' up for the processor).

---

