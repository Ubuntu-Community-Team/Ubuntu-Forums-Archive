---
title: "Install Errors, live CD wont work"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by nscreed15 on 2009-04-27
While trying to use an Ubuntu Live CD (attempted using 7.10, 8.04, and 9.04. All received the same error. CDs were checked for errors and worked correctly on a different machine), when I attempt to install or run straight from the CD, it hangs on the loading screen. If I wait it eventually changes to command line and outputs:

```
*Loading hardware drivers...
udevd-event[2404]: '/sbin/modprobe -b pci:v00008086d00002770sv0008086sd0000D606bc06sc00i00' abnormal exit
                         [ OK ]
init: rc-default main process (3012) terminated with status 127
```

The "main process (XXXX)" changes each time I attempt to recreate the error.

since I saw "pci:..." I thought it might be an issue with my sound card (PCI interface) so I removed it and got a slightly different error

```
init: rc-default main process (2903) terminated with status 2
```
^^It also shows the abnormal exit for the Loading hardware drivers^^

System specs;
Motherboard: Intel D945GCNL
CPU: Intel Pentium D 830
RAM: OCZ S.O.E. 2GB 240-pin DDR2 SDRAM (PC5200   667)
Video: XFX 8600GTS
Sound: Creative Sound Blaster Audigy 2 ZS Platinum

Any help would be greatly appreciated

Nate

---

### Post by moe46 on 2009-04-28
Hi

I would burn a new cd and try that first 
the status 2 error your getting means

2 : Bad file or directory type This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 

im assuming that its going for a driver it needs and cant get it
but as the other computer u tested it on has different hardware?
that it could get those drivers

give that a try,
Mushiden

---

