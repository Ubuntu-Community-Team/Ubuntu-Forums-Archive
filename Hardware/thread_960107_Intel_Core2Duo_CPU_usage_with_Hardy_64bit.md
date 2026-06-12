---
title: "Intel Core2Duo CPU usage with Hardy 64bit"
date: 2008-10-27
forum: Hardware
---

### Post by philipp_aus_koeln on 2008-10-27
Dear all,
I have a lenovo thinkpad  x61 tablet and installed hardy 64bit about three weeks ago. Everything is running so far and I'm quite satisfied. However there is one issue left that concerns me. 
When I monitor the cpu activity and temperature (under "normal" conditions) in Windows XP it appears the two processors are simultaneously used by the system and seldomly go over 60% of usage each resulting in temperatures <50C. In Hardy the situation is quite different: when I run the same application instead of using the two processors equivalently one remains at 0% whereas the other one shoots to 100% - this is heating up the system to temperatures around 70C - I know these temperatures are not something to worry about, but I am wondering if the CPU usage by XP is better and if there is something I can do to optimize my system.

Thanks for your replies in advance!

Philipp

---

### Post by dazzled on 2008-10-27
It may well depend on the software you run. I have a Gutsy 64 bit desktop with a fast Core 2 Duo that is used for 64 bit floating point physics simulations - very heavy duty calculating that can run for days. The apps are all compiled from C++ and Fortran source on the machine, or are interpreted by Matlab.  For me, both cores are always used, about equally.

---

### Post by zgornel on 2008-10-27
> **philipp_aus_koeln said:**
> Dear all,
I have a lenovo thinkpad  x61 tablet and installed hardy 64bit about three weeks ago. Everything is running so far and I'm quite satisfied. However there is one issue left that concerns me. 
When I monitor the cpu activity and temperature (under "normal" conditions) in Windows XP it appears the two processors are simultaneously used by the system and seldomly go over 60% of usage each resulting in temperatures <50C. In Hardy the situation is quite different: when I run the same application instead of using the two processors equivalently one remains at 0% whereas the other one shoots to 100% - this is heating up the system to temperatures around 70C - I know these temperatures are not something to worry about, but I am wondering if the CPU usage by XP is better and if there is something I can do to optimize my system.

Thanks for your replies in advance!

Philipp
What application are you using ? It might not have optimizations for multithreaded opperations.

---

### Post by sdennie on 2008-10-27
The difference is probably the way the respective kernels choose to schedule processes across the available CPUs.  I don't see why it would make a temperature difference (at least not one that large) so, maybe something else is going on.  Is it possible that XP was keep your CPU fan running faster?

---

