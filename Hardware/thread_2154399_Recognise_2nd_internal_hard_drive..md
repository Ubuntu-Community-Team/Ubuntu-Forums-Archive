---
title: "Recognise 2nd internal hard drive."
date: 2013-06-14
forum: Hardware
---

### Post by Cantigrp on 2013-06-14
Hi,

I am new to Ubuntu and your forums have been a great help in getting me started. Most of my questions have been answered by looking at previous posts from other users, however I am now a bit stuck and cannot find the answer to my specific setup anywhere so thought I would ask for some help. 

I have a HP Proliant server  with two internal hard drives fitted. I bought this server second hand with no o/s on it and no history of what has been on it.
I installed Ubuntu Desktop 32 bit 12.4  version which is running great, really like it.
I have virtual box running with two further virual machines running Ubuntu dekstop on them also.

However, Ubuntu only seems to be able to see 1 of the Hard Drives, not both. I have tried everything I can from posts on here but am stuck for what to do, I wondered if I posted the following whether someone might be able to help me.

The machine is a HP Proliant DC580 G5 with 16 processors and 20 MB RAM
The two Hard Disc Drives are HP ones. They are 146GB HD.
When the system is booted,and you look at the HP Smart Array P400 controller it shows both hard disc drives as present.

Info shown when viewing Logical drive gives:

Logical Drive #1, RAID 1+0, 136.7GB      OK
Port 1I, Box 1, Bay 1, 146.8GB   SAS HDD OK
Port 1I, Box 1, Bay 2, 146.8GB   SAS HDD OK

When I look at the sudo fdisk -l I get this : -


  Disk /dev/cciss/c0d0: 146.8 GB, 146778685440 bytes
  255 heads, 63 sectors/track, 17844 cylinders, total 286677120 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x000955e0
   
             Device Boot      Start         End      Blocks   Id  System
  /dev/cciss/c0d0p1   *        2048   244740095   122369024   83  Linux
  /dev/cciss/c0d0p2       244742142   286676991    20967425    5  Extended
  /dev/cciss/c0d0p5       244742144   286676991    20967424   82  Linux swap / Solaris
  
Obviously only showing the one hard drive and when I do [FONT=&quot]cat /var/log/dmesg |grep ata I get this.

[/FONT]  [    0.000000] BIOS-e820: [mem 0x00000000cfd33000-0x00000000cfd3bfff] ACPI data
  [    0.000000] Memory: 20728524k/21757948k available (6051k kernel code, 239676k reserved, 2976k data, 760k init, 20055252k highmem)
  [    0.000000]       .data : 0xc15e8d55 - 0xc18d0e80   (2976 kB)
  [    0.064003] PEBS disabled due to CPU errata.
  [    0.505071] libata version 3.00 loaded.
  [    0.717555] ata_piix 0000:00:1f.1: version 2.13
  [    0.717569] ata_piix 0000:00:1f.1: can't derive routing for PCI INT A
  [    0.717617] ata_piix 0000:00:1f.1: setting latency timer to 64
  [    0.717995] scsi0 : ata_piix
  [    0.718085] scsi1 : ata_piix
  [    0.718128] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x500 irq 14
  [    0.718131] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x508 irq 15
  [    0.904352] ata1.00: ATAPI: TSSTcorpDVD-ROM TS-L332A, HG00, max UDMA/33
  [    0.952222] ata1.00: configured for UDMA/33
  [    1.081053] Write protecting the kernel read-only data: 2476k
  [    1.081055] NX-protecting the kernel data: 4188k
  [    1.807085] EXT4-fs (cciss!c0d0p1): mounted filesystem with ordered data mode. Opts: (null)
  
If anyone could help point me in the right direction to get me going that would be great, I am a bit stumped what to do, as I say I have read other threads in relation to this but the result has been problems with hard drive not present in BIOS which is not what is happening here. Much appreciated. Ben.

---

### Post by sanderj on 2013-06-14
Your post says "RAID 1+0", so the net space visible seems correct to me. See [https://en.wikipedia.org/wiki/RAID#RAID_10](https://en.wikipedia.org/wiki/RAID#RAID_10)

EDIT:

So, if you want to see two seperate drives, remove the RAID config.

HTH

---

### Post by Cantigrp on 2013-06-14
Ahhhh, thank you very much, sorry new to the server side of life. Thanks again!

---

