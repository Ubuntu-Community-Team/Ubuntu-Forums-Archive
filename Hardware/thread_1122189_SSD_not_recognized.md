---
title: "SSD not recognized"
date: 2009-04-10
forum: Hardware
---

### Post by toneman77 on 2009-04-10
Hello
I just bought new components for my new living room machine, especially:
- asus p5n7a-vm
- hama 8GB SATA SSD drive

First thing i tried was the 9.04 beta minimal cd and when harddisks get scanned I was asked for a driver. 
Then I tried the 8.10 live cd. After booting I get the following error messages:
```

ubuntu@ubuntu:~$ dmesg|grep ata1
[    4.453923] ata1: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76100 irq 221
[    5.160034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.160065] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   10.868038] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   10.868069] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   16.576037] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   16.576079] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   22.284038] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   22.284055] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t4
[   22.284060] ata1: irq_stat 0x08000000, interface fatal error
```

The SSD drive is invisible for ubuntu. I also tried setting the controller to SATA,AHCI and RAID, always the same result. I also tried to put the sata cable in all of the 5 slots on the board, no luck.

Anyone got an idea what I can do to make ubuntu recognize that drive?

EDIT: In sheer desperation in put in an old XP CD and Windows installs without a problem. :(

---

### Post by toneman77 on 2009-04-13
After fiddling with almost all kernel parameters there are I found out the following:

Jaunty Live: disk with error
```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.28-9-generic #31-Ubuntu SMP Wed Mar 11 15:43:58 UTC 2009 i686 GNU/Linux
```

dmesg: [http://pastebin.ca/1390892]("http://pastebin.ca/1390892")

Intrepid Live: disk with error

```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
```

dmesg: [http://pastebin.ca/1390900]("http://pastebin.ca/1390900")

Gutsy: **success** !!!

```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.22-12-generic #1 SMP Sun Sep 23 18:11:30 GMT 2007 i686 GNU/Linux
```

(sda is the disk, sdb is the usb stick i needed to copy the files over)

```
ubuntu@ubuntu:~$ cat /proc/partitions 
major minor  #blocks  name

   8     0    7962192 sda
   8     1      32098 sda1
   8     2    7928077 sda2
   7     0     648272 loop0
   8    16    2015232 sdb
   8    17    2015216 sdb1
```

dmesg: [http://pastebin.ca/1390924]("http://pastebin.ca/1390924")

Gutsy sees the disk, Intrepid and Jaunty not.
What could be the problem here?

Any help appreciated

How can I find out what the other live cds make different?

---

### Post by toneman77 on 2009-04-19
*bump*
anyone got an idea?

---

### Post by toneman77 on 2009-04-25
After a lot of fiddling I don't know what else to try

2.6.22 does:
```

[    5.580000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.580000] ata1.00: ATA-7: External Disk 0, 1.1516, max UDMA/133
[    5.580000] ata1.00: 15924384 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    5.580000] ata1.00: configured for UDMA/133
...
[    7.140000] scsi 0:0:0:0: Direct-Access     ATA      External Disk 0  1.15 PQ: 0 ANSI: 5
[    7.148000] sd 0:0:0:0: [sda] 15924384 512-byte hardware sectors (8153 MB)
[    7.148000] sd 0:0:0:0: [sda] Write Protect is off
[    7.148000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.148000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.148000] sd 0:0:0:0: [sda] 15924384 512-byte hardware sectors (8153 MB)
[    7.148000] sd 0:0:0:0: [sda] Write Protect is off
[    7.148000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.148000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.148000]  sda:<6>ata1: D2H reg with I during NCQ, this message won't be printed again
[    7.148000] ata1: DMAS FIS during NCQ, this message won't be printed again
[    7.148000]  sda1 sda2
[    7.148000] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.152000] sd 0:0:0:0: Attached scsi generic sg0 type 0

```

2.6.28 does:
```

[    1.847181] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 21 (level, low) -> IRQ 21
[    1.847231] ahci 0000:00:0b.0: irq 2301 for MSI/MSI-X
[    1.847303] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.847307] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pmp pio slum part 
[    1.847311] ahci 0000:00:0b.0: setting latency timer to 64
...
[    1.848885] ata1: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76100 irq 2301
...
[    2.556031] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.556063] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[    8.264024] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.264044] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[    8.264049] ata1: limiting SATA link speed to 1.5 Gbps
[   13.972024] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   13.972045] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   19.680023] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   19.680036] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t4
[   19.680099] ata1: irq_stat 0x08000000, interface fatal error

```

What I found out with the 2.6.22:
Vendor ID for the disk/controller is 0x10de
Device ID is 0x0ab8

Funny thing is that this device id is known in 2.6.28 in the file ahci.c but not in 2.6.22
2.6.22 kernels recognize the disk (ubuntu 7.10 gutsy, debian lenny), 2.6.28 dont.

Any ideas?

---

### Post by toneman77 on 2009-05-14
*bump*

---

### Post by bluedalek on 2010-11-27
I agree... any ideas?

---

