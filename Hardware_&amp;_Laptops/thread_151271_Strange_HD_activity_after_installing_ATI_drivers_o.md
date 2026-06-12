---
title: "Strange HD activity after installing ATI drivers on Acer Travelmate 4002"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by outofsync on 2006-03-27
Hi,

Did anybody manage to get _sweet_ operation of ATI drivers on Acer TravelMate 4002 (Mobility 9700) ?

My story:

I installed the version 8.16.20 of ATI drivers from the Ubuntu repository (I tried first with the latest version from ATI, but the installer didn't work, so I installed the version from the ubuntu repository, which did work -see my recent post in the Video and Sound forum-).

First of all, I'm no longer able to use the native resolution of this TravelMate, which is 1280x800. It's set as 1024x768 now.

But, worst of all, I can hear HD activity at regular intervals (every two seconds or so). It's a very brief access to the hard disk, and it happens on seemingly exactly-regular intervals. It's so brief that the LED doesn't light, but you can hear it.

I checked the /var/log/Xorg.0.log file, but no errors were displayed

Btw, hardware acceleration works, although I admit I prefer the previous situation (with no hard disk activity, and with the native monitor resolution)

If I can't enhance the situation, I expect there's an easy procedure to uninstall these drivers and revert to the previous scenario...

---

### Post by outofsync on 2006-03-27
I don't know if it's related to this hard-disk activity, but when I shutdown, I see a couple of warnings claiming "tmpfs busy". IIRC, these warnings weren't there before installing the ATI drivers...

---

### Post by outofsync on 2006-03-29
I've been able to install the latest ATI version, and it fixes all problems, except the HD activity. However, this HD activity might be unrelated to the ATI drivers, because I uninstalled them and it still happens. Also, you only notice it when in a silent room, so it's possible that it was always there since I installed Ubuntu but didn't notice it before.

---

