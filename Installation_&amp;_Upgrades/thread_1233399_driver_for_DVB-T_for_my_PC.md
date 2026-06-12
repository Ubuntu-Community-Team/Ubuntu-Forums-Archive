---
title: "driver for DVB-T for my PC"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by helen_prag on 2009-08-06
I have an adaptor for TV in the computer.
It's Jett.
The problem is that the installation CD is only for Windows.
It's called "TV Jukebox 3.0 S/N.
It is similar to the SW on this link:
[http://www.ptvrosat.com/images/products/DVB-T-USB968/image008.jpg](http://www.ptvrosat.com/images/products/DVB-T-USB968/image008.jpg)

So now I'm looking for something similar that could be used in Linux.

On my PC I have this version of ubuntu:
Pro X 86 Ubuntu 904.

Thanks.

---

### Post by realzippy on 2009-08-07
..without the name of your device/chipset nobody can/will help you...

---

### Post by madman100 on 2009-08-07
hi i has the same problem last night with my dvb-t USB dongle but manage to fix it with the help for people on this forum first you must do a probe to find out what chip set it is using then google it that then should tell you who the makers are and what drivers you can you from vl4-dvb drivers you need to check with 
dmesg | grep dvb   or if USB the sudo lsusb  or if pic sudo lspci
as i found last night the firmware for my hardware was on the cd that came with it but it was a windows version witch you can rename to use in ubuntu this will then give some indention of what chip set it is using   This file can also be found on your driver CD, called EC168BDA.bin. This has to be
renamed to dvb-usb-ec168.fw
Remember This Is Only A Example you might not have the same chip set if you do let me know or just have a look at my post  from last night i hope this helps

Thanks
madman100

---

