---
title: "Brand new Dual-Core"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by tonybeccar on 2009-02-25
Hi, I don't know if this is the right section for this thread but it's not much related to the hardware. 
The thing is I bought yesterday a new Intel Dual Core E5200, with 2.5ghz, 2mb cache L2, 800mhz bus, etc.

I installed it on the motherboard and then booted ubuntu, just like that. I wanna know if I have to upgrade something, maybe the kernel or something like that, because I don't feel that my computer is going too much faster. 

In fact, when i convert a movie using DeVeDe, it just goes a little faster, and my cores are not in 100%, one is at 60% constantly and the other is 100% and 20% half of the times. I don't know, i think it must go much faster.

I googled and read something about upgrading the motherboard bios or something like that, please tell me whatever changes and upgrades i have to do in order for my new cpu work properly.

I'd like your opinions please, thank you!

---

### Post by bazzer on 2009-03-13
If you have your cpu frequency set to 'ondemand' it'll ramp up when it's needed and slow when it's not, to conserve power etc.

Look in gconf-editor under /apps/gnome-power-manager/cpufrequency for more clues.
:)

---

### Post by skymera on 2009-03-13
> **tonybeccar said:**
> Hi, I don't know if this is the right section for this thread but it's not much related to the hardware. 
The thing is I bought yesterday a new Intel Dual Core E5200, with 2.5ghz, 2mb cache L2, 800mhz bus, etc.

I installed it on the motherboard and then booted ubuntu, just like that. I wanna know if I have to upgrade something, maybe the kernel or something like that, because I don't feel that my computer is going too much faster. 

In fact, when i convert a movie using DeVeDe, it just goes a little faster, and my cores are not in 100%, one is at 60% constantly and the other is 100% and 20% half of the times. I don't know, i think it must go much faster.

I googled and read something about upgrading the motherboard bios or something like that, please tell me whatever changes and upgrades i have to do in order for my new cpu work properly.

I'd like your opinions please, thank you!

In order to use more than one core, the application needs to support multi-threading.

---

