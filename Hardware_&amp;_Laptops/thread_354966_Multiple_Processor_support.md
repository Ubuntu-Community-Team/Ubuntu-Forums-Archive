---
title: "Multiple Processor support"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by Slothman on 2007-02-06
Hi, 

I've just installed Xubuntu (Edgy) on my laptop (Core Duo 1.66GHz), but it looks like only 1 core is being used. I ran "sudo cat /proc/cpuinfo" and it only shows 1 proc, any ideas how to get the other one to work?

Thanks

---

### Post by firefly2442 on 2007-02-06
You need to install a different kernel image.  Go into Synaptic and search for the same kernel except the SMP version.  SMP stands for Symmetric Multiprocessing.  :)

---

