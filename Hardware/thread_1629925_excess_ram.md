---
title: "excess ram"
date: 2010-11-24
forum: Hardware
---

### Post by u_kapaley256 on 2010-11-24
Hey guys,
         My laptop has 8 gigs of RAM and  a mediocre 2.2 ghz dual core processor.Ofcourse only upto 2 gigs of that is used.Can i do something to improve the performance of the system using the excess RAM (like more caching).I already do not use swap ...

Thanks

---

### Post by CharlesA on 2010-11-24
Any excess RAM is used for disk caching.

Post the output of this:

```
free -m
```

---

### Post by endotherm on 2010-11-24
the system shoudl use the unused ram for caching anyway (you can see it in GSM; the dark green is allocated to processes, the light green to cache).

are you running a 64 bit system so you can make use of all that ram?

---

### Post by sikander3786 on 2010-11-24
And here is some more useful usage of huge amounts of RAM ;-)

[http://ubuntuforums.org/showthread.php?t=1499338](http://ubuntuforums.org/showthread.php?t=1499338)

Updated version here,

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by u_kapaley256 on 2010-11-24
Thanks for the replies guys.I am using a 64 bit system.The output of the free is the reason for this post :-

udayan@udayanszz:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7747       1824       5922          0         91        511
-/+ buffers/cache:       1221       6525
Swap:            0          0          0

---

