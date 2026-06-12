---
title: "Slow SATA drive with nVidia 405 chipset"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by gareththered on 2007-10-28
I recently bought an Abit NF-M2S motherboard to build my MythTV box.  It worked fine until I went out and bought a 320Gb Hitachi SATA drive for it purely for recording (with the original 80Gb IDE drive staying as the system drive).
All of a sudden MythTV started to hang.  I checked the mythfrontend.log and noticed it was full of errors along the line of:-
```
WriteAudio: buffer underrun
NVP: prebuffering pause
NVP: Timed out waiting for free video buffers.
```If I unmount the SATA drive and let MythTV record to the IDE drive then there are far less error mssages.  Running 'hdparm -tT' on the drives resulted in:-```
mythuser@MythTV:~$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   654 MB in  2.00 seconds = 326.33 MB/sec
 Timing buffered disk reads:  158 MB in  3.01 seconds =  52.57 MB/sec
mythuser@MythTV:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   758 MB in  2.00 seconds = 378.92 MB/sec
 Timing buffered disk reads:  200 MB in  3.00 seconds =  66.57 MB/sec
```The CPU is an Athlon 64 Dual Core 4400, the RAM is 1Gb of 800Mhz DDR2 and the video is an onboard nVidia 6100 which should be able to cope without any trouble.  The 'top' command shows CPU usage at a mere 15% when viewing TV.
Has anyone had any issues with this chipset and SATA.  I've had a quick google and someone suggested a driver from nVidia, but others suggested that this driver is already in later kernels.  'dmesg' showed the driver running.
Thanks in advance.

---

