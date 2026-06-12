---
title: "Really slow cdrom reading speed"
date: 2013-09-17
forum: Hardware
---

### Post by teqqan on 2013-09-17
Hi,

I have a problem with my cdrom performance. The reading speed when ripping with, for example, brasero disc burner is below 1x speed.
When testing timing and cache performance using hdparm, I get errors..

[ATTACH=CONFIG]246316[/ATTACH]

> teqqan@server:~$ sudo hdparm -Tt /dev/sr0

/dev/sr0:
read() failed: Input/output error
 Timing buffered disk reads: read() failed: Input/output error

> teqqan@server:~$ hdparm /dev/sr0

/dev/sr0:
 HDIO_DRIVE_CMD(identify) failed: Bad address
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

From lshw:
> *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7200S
             vendor: Optiarc
             physical id: 0.1.0
             bus info: scsi@5:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.06
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom


Spec:
Ubuntu 13.04
Asus sabertooth 990FX
AMD FX-8350

---

