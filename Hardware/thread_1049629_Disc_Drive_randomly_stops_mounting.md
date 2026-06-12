---
title: "Disc Drive randomly stops mounting"
date: 2009-01-24
forum: Hardware
---

### Post by RPG Master on 2009-01-24
Some times after I take out a disc and put in another, Ubuntu doesn't mount it. When I go to unmount it says "their is probably no media in drive". The only way I know how to fix this (temporarily) is to reboot. Any help would be appreciated.

This should help:

```
 *-cdrom                 
       description: DVD-RAM writer
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open
  *-disk
       description: ATA Disk
       product: WDC WD1600BEVT-6
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 11.0
       serial: WD-WXE308FP3933
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=33b666e8

```

---

### Post by RPG Master on 2009-01-24
bump

---

### Post by jdawg70 on 2011-09-20
I'm going to go ahead and bump this because I'm experiencing this issue in 11.04 64-bit, and it is driving me insanely bonkers.

CD/DVD media will mount for a while, but eventually no media will ever get recognized and I'll have to reboot my machine.

Most of the time, I get no output from dmesg, though occasionally (in particular with audio CDs) I'll get 'has no tracks I recognize' messages.  After a reboot, all is honky dory again.

When things fail to mount themselves, Disk Utility claims the drive has no media.  Manually trying to 'mount /dev/sr0' results in mount just sitting there doing nothing (I have to CTRL-C out of it).

Any thoughts?

---

