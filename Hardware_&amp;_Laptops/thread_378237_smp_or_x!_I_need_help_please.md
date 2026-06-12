---
title: "smp or x?!? I need help please"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by revpfil on 2007-03-07
Hi, I have recently installed 6.10 and am fairly new to linux. I am running the i386 kernel. The problem I am having, though, is that the kernel does not recognize both cores on my computer. I have the linux-generic kernel installed, but every time I boot into it, the xserver crashes. My current setup is:
Asus M2N SLi 
AMD AM2 Athlon XP X2 4400+
2GB DDR2
NVidia GeForce 7300 GT x 2 in SLi configuration.

I have tried reinstalling the nvidia drivers and reconfiguring the xorg.conf with nvidia-xconfigure. This had no effect. Please help, I would really like to have both cores running.

---

### Post by EReckase on 2007-03-09
If the xserver is crashing, it's probably the nvidia drivers, not the kernel.  How are you installing them?  Are you using the envy script?

---

