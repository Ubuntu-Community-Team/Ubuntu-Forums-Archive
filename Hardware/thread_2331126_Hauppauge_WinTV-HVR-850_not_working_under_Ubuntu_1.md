---
title: "Hauppauge WinTV-HVR-850 not working under Ubuntu 16.04"
date: 2016-07-18
forum: Hardware
---

### Post by mtbdrew on 2016-07-18
Tuner cards worked fine on previously installed 14.04. However on 16.04 I get following error when it is plugged in:

 dmesg | grep lgdt33
[    5.473396] lgdt3305_read_reg: error (addr 0e reg 0001 error (ret == -32)
[    5.473397] lgdt3305_attach: error -32 on line 1143
[    5.473398] lgdt3305_attach: unable to detect LGDT3305 hardware

lsusb output shows:

Bus 003 Device 002: ID 2040:b140 Hauppauge 


/lib/firmware contains both:

dvb-fe-xc5000-1.6.114.fw
dvb-fe-xc5000c-4.1.30.7.fw

---

### Post by mtbdrew on 2016-07-21
Anyone have any suggestions at all?

---

### Post by QDR06VV9 on 2016-07-21
One poster had success here:[https://ubuntuforums.org/showthread.php?t=1840373](https://ubuntuforums.org/showthread.php?t=1840373)
That's about all I can add though.
EDIT have a look here:[http://keverets.livejournal.com/3722.html](http://keverets.livejournal.com/3722.html)

---

### Post by mtbdrew on 2016-08-10
Doesn't seem to be V4L-DVB drivers for Ubuntu 16.04. Never had to do anything with the modprobe in previous versions of Ubuntu. My issue is that this version has the LG chip which doesn't seem to be properly supported in 16.04.

---

