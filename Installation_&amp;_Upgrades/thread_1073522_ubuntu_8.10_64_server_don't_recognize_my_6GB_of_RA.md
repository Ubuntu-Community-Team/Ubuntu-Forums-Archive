---
title: "ubuntu 8.10 64 server don't recognize my 6GB of RAM"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by nandelbosc on 2009-02-18
**UPDATE... This machine only can address up to 4GB... ;( However, still around 800MB of memory... Darco, now I try to update the BIOS. Thank's!**

Hi!

I have a fresh install of ubuntu 8.10 64bits on my dell vostro 220 with 6GB of RAM, but the system only recognize 3,2GB... WHY?!?!

```
marc@papito:~$ uname -a
Linux papito 2.6.27-7-server #1 SMP Fri Oct 24 07:20:47 UTC 2008 x86_64 GNU/Linux
marc@papito:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3258        113       3144          0          4         31
-/+ buffers/cache:         77       3181
Swap:         4761          0       4761

```

What I'm missing?

I have 2 modules of 2GB and 2 modules of 1GB. The RAM is tested, and works ok!

---

### Post by darco on 2009-02-18
Boot into the BIOS and see if its recognized there. If not, then you may need to flash the BIOS w/the latest. 

darco

---

