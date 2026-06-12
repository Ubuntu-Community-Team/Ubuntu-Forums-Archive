---
title: "silicon SATA Controller"
date: 2008-07-16
forum: Hardware
---

### Post by schuppianer on 2008-07-16
Hi everybody,

I have a server (8.04.1) running with two 500gb hard disks connected on a PCI SATA Controller
```
#lsusb
00:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)

```
My problem is that the hard disks arn't shown by
```
#fdisk -l
Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ba553

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1158     9301603+  83  Linux
/dev/sda2            1159        1216      465885    5  Extended
/dev/sda5            1159        1216      465853+  82  Linux swap / Solaris

```
the controller should run with the sata_sil modul
```
#lsmod | grep sil
sata_sil               12296  0 
libata                159344  4 ata_generic,pata_sis,pata_acpi,sata_sil

``` but it does not work.... any ideas?

Schuppianer

---

### Post by Celeb on 2008-07-17
Im working on the same here with my sil3124, there ius some post's that maybe help you, basicaly you should:

get dmraid pakage, this maps your 2 hard drives into /dev/mapper/sil_something

then you partitioned that map

sudo fdisk /dev/mapper/sil_something 

and your happy :) but read it your self.

[http://www.ubuntu-es.org/index.php?q=node/95304]("http://www.ubuntu-es.org/index.php?q=node/95304")

[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

good luck, and let my know how it went.

Celeb

---

### Post by schuppianer on 2008-07-21
hi Celeb,
thanks for your answer!
Does the controller run on your system?
My hard drives are available now, but I don't know which thing it repaird. I had a bit trouble with the mainboard so I made a BIOS reset and changed some options in the RAID-Controller BIOS.
Thanks for the Links, it brought me farther too.
I hope it will stay at this status and I'll now install a software-raid.

---

