---
title: "Swapping video card (Nvidia GS760) for an ATI 2600"
date: 2011-04-16
forum: Hardware
---

### Post by danebramaged on 2011-04-16
Greetings to all:  My system is comprised mostly of old junk.  I have a gig of ram and a sempron 3100 plus stuck in a Synchronous Gigabyte mobo with an nforce 250 chip set.  Most importantly I have an 8x agp card in the form of an Nvidia GS760.  All of this runs on Maverick Meerkat just fine and, I would now like to tempt fate because I just got my hands on an ATI 2600 8x agp card.  So, my question is; How do I go about uninstalling the nvidia card (regarding the software) to make sure there are no vestiges of nvidia references in the O/S?  Presumably, ubuntu will just auto-detect and download the appropriate driver for the ATI card once I have it installed.  tayl

---

### Post by K_45 on 2011-04-16
Right down the bottom is the uninstall command, but first, how did you install the drivers in the first place? Additional drivers, from Nvidia's website, or the built in ones?

---

### Post by danebramaged on 2011-04-16
> **K_45 said:**
> Right down the bottom is the uninstall command, but first, how did you install the drivers in the first place? Additional drivers, from Nvidia's website, or the built in ones?

The drivers on my system came to me auto magically through the update manager.

:popcorn: here, have some popcorn.

---

### Post by K_45 on 2011-04-16
Thanks, but I already had pie for lunch.:D

I would open up a terminal and enter

```
gksu jockey-gtk
```

If the drivers are activated, disable them. Then reboot. If they are gone, you'll be running on default drivers and you should be able to make the switch. If you have trouble after switching you can create an Xorg file with the bits you need.

---

### Post by GTMoraes on 2011-04-17
If you have any issues after switching, like K_45 just said, type "aticonfig --initial" to automatically make a new, compatible xorg.conf
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[size=1]|[color=#7FFF00]Microsoft WMM 4000[/color]|[/size]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

