---
title: "DVD drive freezing computer"
date: 2006-11-28
forum: Hardware &amp; Laptops
---

### Post by pichalsi on 2006-11-28
Hi I reinstalled Ubuntu yesterday and found out my PC was freezing all the time after some time from reboot. I found out its some dvd drive problem, my dvd drive is /dev/hdb, some notebook DVD-RW. I found out many people had this problem before but i still couldnt fix it :(

/var/log/messages
```
Nov 28 19:37:56 pichalsi kernel: [ 1759.156000] hdb: status timeout: status=0xd0 { Busy }
Nov 28 19:37:56 pichalsi kernel: [ 1759.156000] ide: failed opcode was: unknown
```

hdparm /dev/hdb
```
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

---

### Post by pichalsi on 2006-11-28
Ive found out i should change the Cabel select on the drive to Master/Secondary but i cant really do it cuz it a laptop... :(

Also [http://groups.google.sk/group/fa.linux.kernel/browse_thread/thread/eccb248b32f2b5e2/a8d8d1bae2e550bc%23a8d8d1bae2e550bc](http://groups.google.sk/group/fa.linux.kernel/browse_thread/thread/eccb248b32f2b5e2/a8d8d1bae2e550bc%23a8d8d1bae2e550bc) tt

---

