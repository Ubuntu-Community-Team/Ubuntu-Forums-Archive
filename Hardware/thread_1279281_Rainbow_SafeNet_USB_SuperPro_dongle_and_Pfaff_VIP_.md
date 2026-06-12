---
title: "Rainbow SafeNet USB SuperPro dongle and Pfaff VIP software"
date: 2009-09-30
forum: Hardware
---

### Post by Kilarin on 2009-09-30
My wife's computer gave up the ghost, so I got her a new one, unfortunately with vista on it.  One of the main reasons she uses her computer is to run her Pfaff 2140 Embroidery Machine, which requires Pfaff VIP Creative Suite software to be able to load designs into the sewing machine.

Sadly, the (very expensive) software was written for windows 95 and is 16bit.  Vista refuses to even try to install it.  It also uses a Rainbow SafeNet USB SuperPro dongle for DRM. (very annoying) 

I'm trying to convert my wife to Ubuntu, I set her up with a dual boot and we attempted to install her Pfaff VIP software under wine.  We get partway through the installation procedure, and then, after it installs the dongle drivers, it insists that it can not FIND the dongle, and quits.

I noticed that there was a Windows XP driver available for her dongle:
[http://www.secretsof.com/content/510](http://www.secretsof.com/content/510)
So, I found the windows XP driver and installed that using wine.  (It was worth a try), but still the program can't find the dongle.

when I do an lsusb the dongle shows up as:
Bus 002 Device 007: ID 04b9:0300 Rainbow Technologies, Inc. SafeNet USB SuperPro/UltraPro 

Is there something I have to do to mount this dongle before the program can read it?

If anyone has any clue how to get it working, we might get another convert from windows to Ubuntu. :)

---

