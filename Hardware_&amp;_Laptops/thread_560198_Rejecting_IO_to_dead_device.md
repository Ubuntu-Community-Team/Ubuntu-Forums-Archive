---
title: "Rejecting I/O to dead device"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by gwi on 2007-09-26
My Ubuntu Feisty system is having problems accessing the harddisk. The system freezes, only showing messages on tty1 like (taken from handwritten notes while watching the messages appear during boot):
```
ata2: softreset failed, port not ready
ata2: softreset failed (timeout)
ata2.00: exception Emask 0x0 sAct 0x3C SErr 0x0 action 0x2 frozen
ata2.00: exception Emask 0x0 sAct 0x47 SErr 0x0 action 0x2 frozen
ata2: hardreset failed (PHY debouncing failed)
ata2.00: exception Emask 0x0 sAct 0x0 SErr 0x40d0000 action 0x2 frozen
irq_stat 0x00060002 failed to transmit command FIS
scsi 3:0:0:0: rejecting I/O to dead device
```
Above messages are not necessarily in the order they appeared in (as I said: handtaken notes while watching the screen). Some are there one time, some are repeated dozens of times.

Trying to solve the problem I tried:[LIST]
[*]three different motherboards (Asus A8N, Abit KN9, Asus M2N32);
[*]three different processors (Athlon64 3200+, Opteron165, AthlonX2 4800+);
[*]three different chipsets (nForce4, nForce570, nForce590);
[*]four different SATA controlers (in the chipsets mentioned above, and a SiI3124);
[*]two different SATA harddisks (Seagate Barracuda 7200.9, Western Digital WD5000AAKS);
[*]several cables and ports on the controllers.
[/LIST]
So far after every reinstall the system runs stable, but after a few weeks the problems start, at a rapidly increasing frequency. I use my computer for a few hours almost every day, and shutdown after use.

I have one SATA harddisk and one ATAPI DVDRW drive, so no raid, no SCSI, no ATA.
Right now, the system freezes before I can login, so forget about collecting logs.

Would be nice to see this problem solved. I is really starting to piss me off (and thinking "how would Vista do?"). The last four months I've spent more time trying to get my system running, than doing real work on it.

Edit:
Rebooting the system after a freeze does not help. Problems only get worse, up to the point where even grub can not access the disk (gives a "Read Error"). Harddisk, system and CPU temps are all around 30 - 35&#8451; (with ambient temp between 20 and 25&#8451;).

---

### Post by cragdor on 2008-02-12
Experiencing this issue with fixed SATA HD in Gentoo, Think it is directly related to HotPlugSATA feature in the kernel! Got worried when the disk stopped working after a reboot of my server so ran Western Digital Disk Diagnostics (DOS urgh!), however the disk checked out fine. I think the kernel is setting the disk status to suspend, thinking your about to unplug it! Then the disk is nolonger accessible till a HARD(not soft) reset. Going to recompile the kernel minus this option! its only effecting a Western Digital Disk on a nforce board. The maxtor hd on nforce and the other Maxtor disks on the sis raid card uneffected!!! Once i have recompiled the kernel then i will post the results!
Wish me luck,
         Craig AKA Cragdor

---

### Post by gwi on 2008-02-13
Forgot I posted the problem here, else I would have posted an update earlier.

In december I bought a new cable, marked "SATA II". It did not look any different than the bunch of cables I already tried. The connector on the motherboard side has a metal clip to keep the connector in position.
After replacing the cable with this "SATA II" one, the problem disappeared. I haven't had one single ATA problem in the past two months.
This might be an option for you. The €5,- investment was worth it...

---

