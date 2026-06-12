---
title: "Weird problem with mouse."
date: 2009-12-19
forum: Hardware
---

### Post by aklo on 2009-12-19
UNR on acer aspire one work fine for me but there is this weird problem about my mouse. 
An old mouse i had worked perfectly find but a brand new mouse i bought had this strange problem.

Sometimes it works for a while then sometimes it became unresponsive. When the mouse because unresponsive, the red laser below the mouse will blink and flash, when it recovers, the laser will be right back up. All this happens only to me new mouse. 

Right now i back to my old mouse till i solve this problem.

---

### Post by hansdown on 2009-12-19
Hi aklo.

Could you please tell us the make and model of the mouse that works, and the one that doesn't work?

Thanks.

---

### Post by aklo on 2009-12-19
Well my mouse are all really cheap types, the old mouse i could not get the model...and it is not stated on the mouse either... as for my new mouse the brand is prolink (made in taiwan) which i bought for $12.

I will be trying it on my desktop later on winxp and ubuntu it might be a hardware problem.

---

### Post by Jive Turkey on 2009-12-19
try plugging in both mice and type "lsusb" in a terminal, and post the output related to the mice.

---

### Post by aklo on 2009-12-19
This is the out put when both mice are plugged in 

Bus 001 Device 004: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

There are no changes when i unplug my new (problematic) mouse. Seems like it is unable to detect it?

Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. disappear when i unplug my good mouse.


it appears my new mouse was faulty. Even in windows, it just flashes usb device not recognized...

---

