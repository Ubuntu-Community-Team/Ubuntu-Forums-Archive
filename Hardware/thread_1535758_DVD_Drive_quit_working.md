---
title: "DVD Drive quit working"
date: 2010-07-21
forum: Hardware
---

### Post by JKyleOKC on 2010-07-21
When I booted my system this morning, I was greeted by dozens of messages about an i/o error on /dev/sdb -- which was a puzzlement, since the system has only one hard drive and it comes up as /dev/sda! After a full two minutes of this (as shown by the log elapsed-time clock) I woke up enough to suspect that it might have something to do with the CD/DVD drive (which is normally /dev/scd0), opened the tray, and removed the disk. The flood of errors stopped and the system booted up with no additional problem.

However I did not trust it since /var/log/syslog showed a few more errors (probably due to the excessively long time getting through the boot process) so I immediately re-started it, this time with no disk in the drive. It booted normally. However it no longer detects the insertion of a disk, and attempting to manually mount one gets the error message "mount: special device /dev/scd0 does not exist" and similarly for sdb1.

At this point I suspect hardware failure, hopefully in the drive itself rather than in the mobo controller involved. The system is Hardy LTS 8.04.04 with all updates, on a Compaq CQ5110F with Athlon 7550 dual-core processor, 3 GB RAM, 500 GB HDD, and the CD hasn't shown any signs of impending disaster. However a search of the forum indicates lots of almost-similar problems that might be software related...

My question is "How should I troubleshoot to determine where the problem lies, and how to fix it?"

---

### Post by JKyleOKC on 2010-07-21
Here's some additional information from the logs:

First, yesterday morning's boot when all went well...
```
Jul 20 07:05:58 mehitabel kernel: [   21.246993] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 20 07:05:58 mehitabel kernel: [   21.414770] ata2.00: ATAPI: TSSTcorp CDDVDW TS-H653R, 0301, max UDMA/33
Jul 20 07:05:58 mehitabel kernel: [   21.590451] ata2.00: configured for UDMA/33
Jul 20 07:05:58 mehitabel kernel: [   21.594967] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
Jul 20 07:05:58 mehitabel kernel: [   21.600534] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653R  0301 PQ: 0 ANSI: 5
```

Next, today's first time around (just the tail end of it):
```
Jul 21 06:37:55 mehitabel kernel: [  123.162785] sd 1:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Jul 21 06:37:55 mehitabel kernel: [  123.167714] sd 1:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
Jul 21 06:37:55 mehitabel kernel: [  123.172591] end_request: I/O error, dev sdb, sector 96
Jul 21 06:37:55 mehitabel kernel: [  123.177394] Buffer I/O error on device sdb, logical block 24
Jul 21 06:37:55 mehitabel kernel: [  123.184054] sd 1:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Jul 21 06:37:55 mehitabel kernel: [  123.188814] sd 1:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present
Jul 21 06:37:55 mehitabel kernel: [  123.193514] end_request: I/O error, dev sdb, sector 100
Jul 21 06:37:55 mehitabel kernel: [  123.198192] Buffer I/O error on device sdb, logical block 25
Jul 21 06:37:59 mehitabel kernel: [  129.346230] sd 1:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Jul 21 06:37:59 mehitabel kernel: [  129.346236] sd 1:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present - tray open
Jul 21 06:37:59 mehitabel kernel: [  129.346240] end_request: I/O error, dev sdb, sector 0
Jul 21 06:37:59 mehitabel kernel: [  129.346243] Buffer I/O error on device sdb, logical block 0
Jul 21 06:37:59 mehitabel kernel: [  129.352683] Buffer I/O error on device sdb, logical block 1
Jul 21 06:37:59 mehitabel kernel: [  129.355901] Buffer I/O error on device sdb, logical block 2
Jul 21 06:37:59 mehitabel kernel: [  129.359027] Buffer I/O error on device sdb, logical block 3
Jul 21 06:37:59 mehitabel kernel: [  129.362068] Buffer I/O error on device sdb, logical block 4
Jul 21 06:37:59 mehitabel kernel: [  129.365654] sd 1:0:0:0: [sdb] Device not ready: Sense Key : Not Ready [current] 
Jul 21 06:37:59 mehitabel kernel: [  129.365658] sd 1:0:0:0: [sdb] Device not ready: Add. Sense: Medium not present - tray open
Jul 21 06:37:59 mehitabel kernel: [  129.365663] end_request: I/O error, dev sdb, sector 0
Jul 21 06:40:05 mehitabel kernel: [   21.963807] sd 1:0:0:0: [sdb] Attached SCSI disk
jim@mehitabel:~$ 
```

Finally, the working boot from this morning:
```
jim@mehitabel:~$ cat /var/log/syslog.0|grep ata2
Jul 21 06:37:55 mehitabel kernel: [   20.577881] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf608 irq 19
Jul 21 06:37:55 mehitabel kernel: [   21.556372] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 21 06:37:55 mehitabel kernel: [   21.724148] ata2.00: ATAPI: TSSTcorp CDDVDW TS-H653R, 0301, max UDMA/33
Jul 21 06:37:55 mehitabel kernel: [   21.899830] ata2.00: configured for UDMA/33
Jul 21 06:40:05 mehitabel kernel: [   19.847052] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf708 irq 19
Jul 21 06:40:05 mehitabel kernel: [   20.826191] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 21 06:40:05 mehitabel kernel: [   20.989978] ata2.00: ATAPI: TSSTcorp CDDVDW TS-H653R, 0301, max UDMA/33
Jul 21 06:40:05 mehitabel kernel: [   21.165654] ata2.00: configured for UDMA/33
jim@mehitabel:~$ 
```

I note that yesterday, SCSI 1.0.0.0 was assigned to the CD/DVD drive while today, it was different -- and today's final effort apparently did not assign it at all. Does this indicate a software problem in the boot processing, or is it more likely a hardware error -- and if it's hardware, is it in the controller or the drive itself?

I don't mind replacing the drive; newegg has one for only $18 that ought to work. However if it's the mobo controller that won't do any good and I should get a new controller card to use the existing drive instead. Help!!!

---

