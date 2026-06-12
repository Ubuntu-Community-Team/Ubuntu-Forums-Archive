---
title: "Unrecognized device"
date: 2014-12-28
forum: Hardware
---

### Post by vcell on 2014-12-28
I've connected my Android tablet via USB to my Ubuntu desktop 14.04 LTS. I've enabled developer mode on the tablet. In files the tablet is recognized and I can browse it's contents. But I can't get it recognized as a device.

[INDENT]~$ adb kill-server
~$ adb devices
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
List of devices attached 

~$ 
[/INDENT]
My end game is to backup the Android for re-install later if necessary, and to flash Ubuntu to the tablet. But it has to be recognized as a device first, correct?

---

