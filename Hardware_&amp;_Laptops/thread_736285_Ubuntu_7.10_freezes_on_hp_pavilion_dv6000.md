---
title: "Ubuntu 7.10 freezes on hp pavilion dv6000"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by Zedzero on 2008-03-26
processor is amd64, but installed ubuntu i386 version, (amd64 needed too much work for a newbie), i'm using restricted drivers for wireless and display adapters. anyway, i installed and ran ubuntu with noapic parameter for a few days (otherwise it won't even boot)

everything is fine, except:

- every 5-6 minutes, everything freezes except mouse cursor. and then everything turns to normal. but sometimes it locks up and i have to reboot. i tried to read log files at /log/var/ but couldn't find anything. also i can't seem to be able to read dmesg even if i sudo. (it says something about acpi being busy). and yes, i've tried booting with pci=noacpi, doesn't make a difference.

- i couldn't find any webcam drivers, it doesn't work.

- which packages are needed for divx xvid and mp3 codecs?

thanks...

---

### Post by Sadist on 2008-03-27
try ```
acpi=off
```

about webcam, show me output from
```
lsusb
```

for codecs see [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Limbic on 2008-03-27
About the webcam:  which program are you using for it?  I've got an HP dv2715nr and it was just a matter of using the right app for it.  I tried Camorama and it didn't work at all, then I tried Cheese (it's in the repositores) and it immediately detected it and worked just fine.

I'd definitely recommend giving Cheese a try before you start messing around with drivers too much.

---

