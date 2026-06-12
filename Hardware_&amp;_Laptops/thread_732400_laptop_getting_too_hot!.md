---
title: "laptop getting too hot!"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by {spitFire} on 2008-03-22
Whenever I check my temperate from "/proc/acpi/thermal_zone/THM/temperature" I always get a value between 60 - 70C especially when I run compiz-fusion (sometimes even as high as 75 or 76) And if I don't run compiz-fusion or am watching movies in fullscreen my temp drops to somewhere between 45 - 55C. How? And, what's exactly the problem?

My box: Ubuntu Gutsy/Dell Inspiron E1505/ATI Radeon X1300/Compiz-fusion.

---

### Post by zgornel on 2008-03-23
The explanation is that some of the compiz plugins (bluring the window borders for ex.) are quite cpu intensive and not optimized for performance as well as they should. The temperatures are in the normal range for notebooks. My pentium-m 1.73Ghz goes up to 75C under load my the core2 2Ghz up to 65. One solution would be not to run compiz or limit the frequency of the processor. Try also disabling plugins from compiz.

---

### Post by Vyacheslav Sakhno on 2008-03-23
I have ATI mobility radeon X1800. It always overheats in KDE. Even if I do nothing.

The problem is not related to the processor. 

I haven't found a solution yet.

---

### Post by zgornel on 2008-03-23
For Gutsy there might be no easy solution is some cases. My fanfor example  is at max speed with the processor at 43C (this behaviour is random) . I tested a live cd of ubuntu/kubuntu 8.04 and there seemed to be no such problems... Everything revolves around buggy implementations of ACPI for certain laptop models.

---

### Post by Migoo on 2008-03-23
I have the same problem here. There seems to be different if I use Xgl instead of direct rendering with the intel-driver. If I use direct rendering with the intel-driver the laptop is getting realy warm even if I don't do anything at all.
I have tried to solve it with the kernel from hardy (2.6.24.12-generic) but the result is the same.

I have a Dell D830 with amd64 kubuntu Gutsy installed with:
Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

