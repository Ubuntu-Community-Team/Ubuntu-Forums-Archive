---
title: "can not copy from one SATA drive to another"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by damien.yep on 2006-07-24
Hello everybody,

I have problems with my sata drives. I'm able to use them (read/write), but when I whant to transfer files from one sata drive to an other sata drive, it's not working.

First here is my hardware configuration:
Motherboard: ASROCK K7VT4A Pro
SATA chipset: VIA VT6420

```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]

```

My linux version:
```

$ uname -a
Linux kubuntu 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux

```

I have 3 Hdd:
1 pata WD 120GB with my Linux, home, swap
2 sata WD 400GB for data storage

I can copy files from my pata to any of my sata without problems, but when I copy file from one sata to an other, I have messages like:

```

Jul 20 21:35:03 kubuntu kernel: [17181303.608000] ata2: translated ATA stat/err 0x51/84 to SCSI SK/ASC/ASCQ 0xb/47/00
Jul 20 21:35:03 kubuntu kernel: [17181303.608000] ata2: status=0x51 { DriveReady SeekComplete Error }
Jul 20 21:35:03 kubuntu kernel: [17181303.608000] ata2: error=0x84 { DriveStatusError BadCRC }

```

And the copy is freezed.

At the beginning I wanted to make a RAID1 array with my sata drive, but everytime I was synchronizing it was crashing, so I used them without RAID, however the problem is still here when I copy from one sata to an other sata. ](*,) 

Is it a known problem? (I could not find any post about it)
If not, does anybody has ideas how to solve my problem?

Thanks!
Damien.

---

### Post by damien.yep on 2006-07-25
Any ideas??? :???:

---

