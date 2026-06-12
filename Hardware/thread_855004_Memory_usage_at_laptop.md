---
title: "Memory usage at laptop"
date: 2008-07-10
forum: Hardware
---

### Post by areskz on 2008-07-10
Hello.
Couple of days ago I launched KSysGuard to learn how much of 2GB of my laptop's memory is really used. I've learnt that** ~1,9GB is used**! How could that be? I just can't believe that my launched apps need **SO** much memory.

I attach a screenshot for you to ensure that there is no any problems with my eyes and I see that number clearly.

So, guys, what do you think about this? Maybe I am doing something wrong?

P.S. Sometimes Firefox uses around 180MB =\

---

### Post by StormPCs on 2008-07-10
Nice screen shot but I see no number.

---

### Post by Vivaldi Gloria on 2008-07-10
See

```
free -m
```

Look at "-/+ buffers/cache" column. That shows the real usage.

> The biggest place it's [RAM] being used is in the disk cache. ... This is reported by top as "cached". Cached memory is essentially free, in that it can be replaced quickly if a running (or newly starting) program needs the memory.

The reason Linux uses so much memory for disk cache is because the RAM is wasted if it isn't used. Keeping the cache means that if something needs the same data again, there's a good chance it will still be in the cache in memory. Fetching the information from there is around 1,000 times quicker than getting it from the hard disk. If it's not found in the cache, the hard disk needs to be read anyway, but in that case nothing has been lost in time. 

Quoted from

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

