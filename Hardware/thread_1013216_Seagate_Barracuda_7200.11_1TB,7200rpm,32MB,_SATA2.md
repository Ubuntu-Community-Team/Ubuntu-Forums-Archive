---
title: "Seagate Barracuda 7200.11 1TB,7200rpm,32MB, SATA2"
date: 2008-12-16
forum: Hardware
---

### Post by kinap on 2008-12-16
Hello everyone,

i have bought this disk : Seagate Barracuda 7200.11 1TB,7200rpm,32MB, SATA2
as it should be fast, but it isn't working right

root@mam:~# hdparm -I /dev/sda|grep SATA
	   *	SATA-I signaling speed (1.5Gb/s)

but my other SATA-2 disks give me

root@mam:~# hdparm -I /dev/sdb|grep SATA
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)
root@mam:~# hdparm -I /dev/sdc|grep SATA
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	SATA-II signaling speed (3.0Gb/s)

it looks like the seagate isn't doing sata-II
anyone have any hints how to cure this?




dmesg gives:
[   28.410606] ata5: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 20
[   28.889356] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.897849] ata5.00: ATA-8: ST31000340AS, SD15, max UDMA/133
[   28.897852] ata5.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   28.914754] ata5.00: configured for UDMA/133

on my other disks it is.
[   29.236806] ata7: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc800 irq 23
[   29.704579] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   29.756432] ata7.00: ATA-7: ST3750840AS, 3.AAK, max UDMA/133
[   29.756435] ata7.00: 1465149168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   29.822929] ata7.00: configured for UDMA/133

[   29.236808] ata8: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc808 irq 23
[   30.286321] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.295356] ata8.00: ATA-7: Maxtor 7H500F0, HA431DN0, max UDMA/133
[   30.295358] ata8.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   30.311849] ata8.00: configured for UDMA/133

Felix

---

### Post by taurus on 2008-12-16
Did you remember to remove the jumper on the back of the drive to get 3.0Gb/s?

The default from Seagate has that jumper in there (1.5Gb/s) so you need to remove it to get 3.0Gb/s.

---

### Post by kinap on 2008-12-17
> **taurus said:**
> Did you remember to remove the jumper on the back of the drive to get 3.0Gb/s?

The default from Seagate has that jumper in there (1.5Gb/s) so you need to remove it to get 3.0Gb/s.


hmmm i should have guessed :)

that did the trick, i was sure i had read that the drive was already in 3GB/sec.

but anyway thanks a lot.

Kinap

---

