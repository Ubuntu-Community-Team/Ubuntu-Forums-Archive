---
title: "Driver for Tuner DVB with LinuxTV [usb dongle PCTV 60e]"
date: 2013-12-14
forum: Hardware
---

### Post by gilga2 on 2013-12-14
Hi!
I've got a tuner TV that I'm trying to make it work with Ubuntu 13.10
I already know it's possible thanks to this thread (but now closed) : [http://ubuntuforums.org/showthread.php?t=511676&page=11](http://ubuntuforums.org/showthread.php?t=511676&page=11)

Apparently, it's the same driver than for another model, PCTV 200e. SO I'm following the tutorial from LinuxTV : [http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_200e](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_200e)
1) I've installed LinuxTV thanks to the "basic" method. 

2)In this, I must add the driver for my tuner since it's not in the main tree.
When I try to "apply the PCTV200e patch to the tree", I've got this error :
```
~/Documents/television/media_build$ sudo git apply pctv200e.diff
error: linux/drivers/media/dvb/dvb-usb/Kconfig: No such file or directory
error: linux/drivers/media/dvb/dvb-usb/Makefile: No such file or directory
error: linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h: No such file or directory
```

So apparently, the folder systems of all the tree has been changed since the patch so I don't know where this patch must go now...
Any help??
Thanks a lot in advance !

---

