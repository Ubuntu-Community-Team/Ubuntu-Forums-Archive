---
title: "my acer laptop periodically buzzes"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by powerfox on 2007-02-17
Hi! I have a problem with my acer aspire 7112wsmi (Celeron 420 M, SCSI).
At first I lose control of some GUI elements (lineEdit - I type, but have no text on screen), then system locks up (also I lose sounds), some air from radiator,  I here "Boolk" ----> everything works.
There is no such problem with vanilla sources and openSUSE (and also windows). Only with ubuntu kernel.  Now I'm using 2.6.17.14-ubuntu1.
I found in log such thing:
> 
Feb 16 14:28:14 pfx-car kernel: [17186841.644000]     Additional sense: Scsi parity error
Feb 16 14:47:14 pfx-car kernel: [17187981.308000] ata1 is slow to respond, please be patient
Feb 16 14:47:39 pfx-car kernel: [17188006.284000] ata1 failed to respond (30 secs)
Feb 16 14:47:39 pfx-car kernel: [17188006.296000] ata1: command 0xa0 timeout, stat 0xd0 host_stat 0x60
Feb 16 14:47:39 pfx-car kernel: [17188006.296000] ata1: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Feb 16 14:48:28 pfx-car kernel: [17188054.964000] ata1 is slow to respond, please be patient
Feb 16 14:48:53 pfx-car kernel: [17188079.940000] ata1 failed to respond (30 secs)
Feb 16 14:48:53 pfx-car kernel: [17188079.952000] ata1: command 0xa0 timeout, stat 0xd0 host_stat 0x60
Feb 16 14:48:53 pfx-car kernel: [17188079.952000] ata1: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Feb 16 14:48:53 pfx-car kernel: [17188079.964000] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
Feb 16 14:48:53 pfx-car kernel: [17188079.964000] sr: Current [descriptor]: sense key: Aborted Command
Feb 16 14:48:53 pfx-car kernel: [17188079.964000]     Additional sense: Scsi parity error

I think that the same time I have problems. But not sure.

---

### Post by powerfox on 2007-02-17
Hear are the logs: [http://itmo.vingrad.ru/messages](http://itmo.vingrad.ru/messages)

---

### Post by powerfox on 2007-02-20
Ok. If nobody knows how to solve the problem, please, say how I may find all ubuntu patches for vanilla kernel?

---

