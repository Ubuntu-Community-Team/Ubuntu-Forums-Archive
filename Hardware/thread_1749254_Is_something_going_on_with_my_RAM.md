---
title: "Is something going on with my RAM?"
date: 2011-05-04
forum: Hardware
---

### Post by ClientAlive on 2011-05-04
Running Ubuntu 10.04 i386 on a HP ze2000 (roughly 5 yrs old). Supposed to be 1 gig of memory (1024 mb) in it.

I notice that it seems like my computer bogs down real bad and I don't even have much stuff open/ going on. When I look at:

```
free -m
```

What it tells me doesn't seem to fit. It lists my total memory as "875" not 1024 (for one thing), then it seems that it's using a lot more memory than it ought to for what I have running.

Below is the output of "free -m" run just minutes ago. I have only one application open - Opera - with two tabs open in it. One is this thread, the other is a google search results page.

What do you thing?


```
~$ free -m
             total       used       free     shared    buffers     cached
Mem:           875        716        158          0         91        274
-/+ buffers/cache:        351        523
Swap:         1609        162       1447
```

---

### Post by leviathan8 on 2011-05-04
Can you post the output of "free" without any other arguments? It seems to me like incorrect value showed up, but your RAM memory is there and fully usable. free -m also shows on my laptop 1,8 GiB of RAM instead of 2,0 GiB. I don't really think it's a problem.

---

### Post by ClientAlive on 2011-05-04
> **leviathan8 said:**
> Can you post the output of "free" without any other arguments? It seems to me like incorrect value showed up, but your RAM memory is there and fully usable. free -m also shows on my laptop 1,8 GiB of RAM instead of 2,0 GiB. I don't really think it's a problem.

Sure! This is just "free"

```

~$ free
             total       used       free     shared    buffers     cached
Mem:        896060     800060      96000          0      69244     389820
-/+ buffers/cache:     340996     555064
Swap:      1648632          0    1648632

```

Thanks.

---

