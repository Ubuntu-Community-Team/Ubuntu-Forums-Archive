---
title: "Resolution and refresh rate on Toshiba Satellite Pro"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by one_ro on 2006-06-12
Hello,

I read a lot of posts regarding problems setting screen resolution and refresh rate after installing/upgrading to Dapper.
My previous version of Kubuntu didn't have these kind of problems... basically everytime I reboot my computer the resolution gets restricted to 640x400 with a refresh rate of 60Hz.
I manually edited my xorg.conf file and added this line

Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

on section Monitor.
On section Screen, the device is corectly detected as:

Device		"NVIDIA Corporation NV17 [GeForce4 420 Go]"
Driver           "nv"   ## BTW should it be "nvidia"?
and "1024x768" at Modes. I can set everything manually, but everything is lost at the next reboot.

Could anybody give me a hint on how to set these options permanently?
Thanks in advance,
Adrian

---

