---
title: "Hibernate and suspend problem in 10.04 on Latitude D830 due to nvidia"
date: 2010-06-28
forum: Hardware
---

### Post by Johan Gambolputty on 2010-06-28
Hi
I'm just sticking this here for the reference of others. I recently installed 10.04 on a Dell Latitude D830 with Nvidia graphics chip/s. Found that hibernate and suspend caused the chipset to crash or something and had just blank screen on laptop after resuming even though the computer seemed to otherwise resume ok. Seems the problem was due to the new open source drivers for Nvidia which are used in 10.04 instead of the proprietary nvidia ones. The solution is to go to System -> Administration -> Hardware Drivers and select "NVIDIA accelerated graphics driver (version current)". That fixed the problem for me and can now happily hibernate/suspend and resume without problems. (the version 173 did not work, IIRC)

Have to say that i'm slightly surprised that Ubuntu would make a change like that in an LTS release without doing a chipset check and warning the user that if they encounter errors (which can also look like complete system hangs to the uninitiated) they try changing back to the proprietary nvidia driver. Hope they're not being pushed around by some ideological zealots amongst them.

---

