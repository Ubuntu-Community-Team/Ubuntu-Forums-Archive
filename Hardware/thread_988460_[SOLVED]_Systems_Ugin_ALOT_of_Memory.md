---
title: "[SOLVED] Systems Ugin ALOT of Memory"
date: 2008-11-20
forum: Hardware
---

### Post by jairom70 on 2008-11-20
Just chked my memory usage and this is wat i get .. any suggestions?


Mem:   3370860k total,  3067252k used,   303608k free,   116868k buffers
Swap:  9871900k total,     4964k used,  9866936k free,  2357196k cached

---

### Post by sdennie on 2008-11-20
That looks like normal memory usage to me.  You are only using 650M of RAM total.  The 2.35G of cache is technically being used but, it gets out of the way if your applications actually need it.  A better way to check free RAM is to use:

```

free -m

```

The second line (-/+ buffers/cache) is the interesting one.

---

### Post by jairom70 on 2008-11-20
this is wats confisinh me i usd free-m and i get 

             total       used       free     shared    buffers     cached
Mem:          3291       2997        294          0        115       2313
-/+ buffers/cache:        569       2722
Swap:         9640          4       9635



so thats say i only have 294 free ??

---

### Post by amauk on 2008-11-20
don't see anything particular wrong there

the memory shown in "buffers" is free memory (so you can add that to the "free" value)
It's just memory currently being used to store commonly accessed disk blocks (cache, in other words)

---

### Post by oldos2er on 2008-11-20
Free memory is unused memory.

---

### Post by sdennie on 2008-11-20
> **jairom70 said:**
> this is wats confisinh me i usd free-m and i get 

             total       used       free     shared    buffers     cached
Mem:          3291       2997        294          0        115       2313
-/+ buffers/cache:        569       2722
Swap:         9640          4       9635



so thats say i only have 294 free ??

No, that says you have 2.7GB free.  As I said, it's the second line, "-/+ buffers/cache" that is the interesting one.

---

### Post by jairom70 on 2008-11-20
OOooo i see. so the top line where is says Used 2997 why does it say that?

---

### Post by sdennie on 2008-11-20
That's counting the cache.  While technically that is used memory, it's not used directly by applications and the system frees it up if your applications need it.  It's memory that's caching disk reads.  An example of this would be to reboot your machine and then start some slow starting application like Open Office.  Now close Open Office and start it again.  The second time you start it, it should start much faster.  That's the cache.

---

