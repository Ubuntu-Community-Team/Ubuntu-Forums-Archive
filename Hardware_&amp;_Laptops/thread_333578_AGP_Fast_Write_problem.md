---
title: "AGP Fast Write problem"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by Asix on 2007-01-07
Heya everyone,
the other day I installed Kubuntu Edgy Eft and I've managed to install the latest ATI Radeon open source drivers on my system and I got them working. But then, something strange started to happen...
I needed to tweak my xorg.conf file so I could get AIGLX working the way I wanted, because I wanted to try out something on my Radeon 9600 Generic (that's what glxinfo says).
When I add this to the Device section of my xorg.conf file
```
Option     "AGPFastWrite"     "True"
```
and restart the system it just shows black screen and nothing happens.
But the point is that AGP Fast Write is enabled in my motherboard BIOS (the motherboard is MSI KT4V with VIA KT400 chipset, by the way), so probably the problem is in my Kubuntu system.
Is there any solution to this, because I really need to set up Fast Write so I could test the performance of some applications on my system.
For your reference, I've attached my current xorg.conf file so you can examine it and tell me what to do.
Thanks in advance for your help.

---

### Post by zgornel on 2007-01-08
KT266/333/400 chipsets always had serious stability problems with the fast writes option enabled, I recommend disabling it, you won't get a major performance increase.

---

### Post by Asix on 2007-01-08
Yeah but I just want to turn it on for a while until I'm finished with some thorough graphics software testing and then  to turn it off again. Is there actually a way to get past that chipset instability issue and get AGP Fast Writes working?

---

### Post by zgornel on 2007-01-08
> **Asix said:**
> Yeah but I just want to turn it on for a while until I'm finished with some thorough graphics software testing and then  to turn it off again. Is there actually a way to get past that chipset instability issue and get AGP Fast Writes working?I'm not sure but I think there's no way to achieve stability with Fast Writes in any way. You might want to check for some kernel updates or patches.

---

