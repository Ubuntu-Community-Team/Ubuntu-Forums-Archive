---
title: "ITE RAID driver compile"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by fowie on 2007-12-30
I still cannot get my ITE 8212 RAID controller to work quite right under ubuntu.  I did a custom kernel compile and disabled the pata_it821x driver and instead used the old ide it82x controller which made my RAID0 drive actually show up in Linux--a good start.  But now when I try to access the drives after a short amount of time coyping or manipulating files I start to get input/output errors and can no longer use the drives.  ITE has a linux driver on their website, but of course there's no pre-compiled version for Ubuntu.  There is a debian 3.0 precompiled if that's easier.  Otherwise, they include the source but I don't know how to install it?  the src folder of the driver has a 2.6.x folder for my kernel and inside that there's just:
```

iteraid.c
iteraid.h
Makefile

```
I tried a simple ./configure and make but that doesn't work, I think it needs to be compiled into the kernel.  Can anyone help me out with this?

---

