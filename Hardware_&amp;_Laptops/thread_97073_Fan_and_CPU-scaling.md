---
title: "Fan and CPU-scaling"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by ianpeters on 2005-11-30
Hi!

I have a HP ZD7000 (e.g. ZD7150ea) 3GHz P4 which runs Breezy without any greater hassles. One thing that I've been thinking of though is the possibility to scale the CPU-frequency. I've checked the little applet in Gnome but it says scaling is not available. That was my first concern.

My second question is, do you think it's possible to control the CPU-fan? I've been prowling in /proc and found different temperature threshold values that increase/decrease fanspeed. But I don't know how to access it or if it's even possible. I wouldn't mind running the CPU on, lets say, 1Ghz if it would mean a less audible environment when I'm typing in Ooo or reading a PDF-article. 

Any thoughts on this? Thanks in advance!!

---

### Post by shof2k on 2005-12-02
Scaling should be possible, depends on the exact model of your cpu.  If you install powernow, it includes a script to help you find which module you need to do this.

Fan speed scaling is again possible, but depends on your motherboard.  I think you can controll it via lm-sensors, but I can't say for sure as my laptop isn't compatible.

Hope that helps,

---

### Post by Raoul Duke on 2005-12-02
You have to rebuild the kernel to enable scaling...in Ubuntu it is turned off by default for some reason.

---

