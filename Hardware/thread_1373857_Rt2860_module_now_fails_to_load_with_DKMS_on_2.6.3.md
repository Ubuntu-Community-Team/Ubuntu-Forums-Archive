---
title: "Rt2860 module now fails to load with DKMS on 2.6.31.5 kernel build."
date: 2010-01-06
forum: Hardware
---

### Post by Dave_Connor on 2010-01-06
Hey, ugh... I have been working on this issue for 3 hours to get this (language) working again. For some reason ra0 interface for my wireless stopped working and I tried to remove the module and re-modprobe and that did not work. I rebooted in an older kernel and the same thing. I reinstalled the current newer kernel I am running and it is failing to build on startup and doesn't work at on older kernels. I can't figure out why this is happening and I am tearing my hair out at this problem. Do I need to download one of the more recent kernels and compile it ? If so I can do that and transfer via USB but for the love of me I can't figure out this issue.

---

### Post by Dave_Connor on 2010-01-25
Nevermind with this topic. Fixed the issue with a simple BIOs option that somehow was disabled. So SOLVED for this topic.

---

