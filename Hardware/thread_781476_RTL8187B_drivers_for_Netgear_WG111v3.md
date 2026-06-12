---
title: "RTL8187B drivers for Netgear WG111v3"
date: 2008-05-04
forum: Hardware
---

### Post by DrCoolSanta on 2008-05-04
I have a 64 bit copy of Ubuntu Hardy installed, and have the WG111v3 wifi card. Since Netgear has no linux drivers, nor any 64 bit XP drivers, I have been having bad luck. Finally I did some research and found that it has the RTL8187B chipset. THe site [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/) had the drivers and got them, and then this driver wouldn't recognise my hardware probably because the device strings were modded for Netgear. I opened up the rtl8187b_core.c and added support for my card in the list of hardware that was supported, and the part where it initiallises the driver, I added case 0x4260, like how that person added support for RTL8187B. After all this hardwork, i found that my device would have it's light on, and I could scan for networks, but unfortunately my computer would hang, and as many times I do it, it would.

Please try to help me out, I can't live without internet.

---

