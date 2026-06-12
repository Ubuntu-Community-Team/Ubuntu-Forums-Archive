---
title: "sil3112 controller - dual 1TB drives show on desktop system but not server?"
date: 2015-04-11
forum: Hardware
---

### Post by r0d3nt on 2015-04-11
Hi All,

I've got a Silicon Image 3112 raid card that I've flashed to the latest available firmware [4.4.02] that turns it into just a SATA controller from the Silicon Image website.

When I install the card in a desktop based Ubuntu 14.10 with two 1TB drives, the system sees the two individual drives properly.  However, I want to use this card in a server based system.  On both systems when they boot, the sil3112 bios detects both drives properly.  The server system though is recognizing both drives, just like how the desktop system does, but is only assigning a device reference to one of the two drives.

dmesg snippet output from the desktop syste.  The sil3112 controller sees both drives properly:
[FONT=courier new]```
[    0.543216] sata_sil 0000:04:01.0: version 2.4[    0.546220] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    0.546222] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    0.594194] scsi1 : sata_sil
[    0.594326] scsi0 : pata_jmicron
[    0.594445] scsi3 : sata_sil
[    0.594495] ata3: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffc80 irq 17
[    0.594498] ata4: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffcc0 irq 17
[    0.594829] scsi4 : pata_jmicron
[    0.594881] ata1: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[    0.594883] ata2: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
```
[/FONT]The first drive is seen and configured properly:
```
[FONT=courier new][    0.920048] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    0.928349] ata3.00: ATA-8: WDC WD10EACS-22D6B0, 01.01A01, max UDMA/133
[    0.928352] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.936043] ata12: SATA link down (SStatus 0 SControl 300)
[    0.936086] ata11: SATA link down (SStatus 0 SControl 300)
[    0.944035] usb 2-4: new high-speed USB device number 2 using ehci-pci
[    0.944358] ata3.00: configured for UDMA/100
[    0.944473] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EACS-22D 1A01 PQ: 0 ANSI: 5
[    0.944745] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    0.944753] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    0.944797] sd 1:0:0:0: [sda] Write Protect is off
[    0.944800] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.944819] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA[/FONT]
```
As is the second:
```
[FONT=courier new][    1.264046] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.272342] ata4.00: ATA-8: WDC WD10EACS-22D6B0, 01.01A01, max UDMA/133
[    1.272345] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.288343] ata4.00: configured for UDMA/100
[    1.288432] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EACS-22D 1A01 PQ: 0 ANSI: 5
[    1.288680] sd 3:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.288682] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.288718] sd 3:0:0:0: [sdb] Write Protect is off
[    1.288721] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.288735] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA[/FONT]
```
Both the drives are part of a software raid 1 array and are assembled properly:
```
[FONT=courier new][    8.689807]  sda: sda1
[    8.690248] sd 1:0:0:0: [sda] Attached SCSI disk
[    8.894223]  sdb: sdb1
[    8.894626] sd 3:0:0:0: [sdb] Attached SCSI disk
[    9.052424] md: bind<sda1>
[    9.053487] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    9.055814] md: bind<sdb1>
[    9.057557] md/raid1:md127: active with 2 out of 2 mirrors
[    9.057696] created bitmap (8 pages) for device md127
[    9.057978] md127: bitmap initialized from disk: read 1 pages, set 0 of 14903 bits
[    9.082195] md127: detected capacity change from 0 to 1000068874240
[    9.092273]  md127: unknown partition table[/FONT]
```
From dmesg snippet on the server, both drives are "seen" but only one seems to be activated:
```
[FONT=courier new][    7.202236] sata_sil 0000:05:02.0: version 2.4
[    7.202802] hidraw: raw HID events driver (C) Jiri Kosina
[    7.206105] scsi0 : sata_sil
[    7.206315] scsi1 : sata_sil
[    7.206387] ata1: SATA max UDMA/100 mmio m512@0xc8300000 tf 0xc8300080 irq 28
[    7.206389] ata2: SATA max UDMA/100 mmio m512@0xc8300000 tf 0xc83000c0 irq 28
[    7.524043] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)[/FONT]
```
More detail on the one drive "seen":
```
[FONT=courier new][    8.148034] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    8.471305] ata2.00: ATA-8: WDC WD10EACS-22D6B0, 01.01A01, max UDMA/133
[    8.471306] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    8.484950] ata2.00: configured for UDMA/100
[    [/FONT][FONT=courier new]8.485099] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EACS-22D 1A01 PQ: 0 ANSI: 5
[    [/FONT][FONT=courier new]8.485417] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    [/FONT][FONT=courier new]8.485446] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    [/FONT][FONT=courier new]8.485489] sd 1:0:0:0: [sda] Write Protect is off
[    [/FONT][FONT=courier new]8.485491] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    [/FONT][FONT=courier new]8.485521] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    [/FONT][FONT=courier new]8.498106]  sda: sda1
[    [/FONT][FONT=courier new]8.498313] sd 1:0:0:0: [sda] Attached SCSI disk[/FONT]
```

And that's it for the server, it doesn't properly assign a hardware device to the second drive.

I'm looking for any advice on how to make this second drive work properly with this server motherboard.

I'm attaching the full dmesg output from both systems in case anyone sees something that might be preventing the second drive from being seen on my server.

---

### Post by weatherman2 on 2015-04-11
If the array is assembled successfully, then both drives should be being used. Otherwise, the mdadm command to assemble the mirror should fail.  You should be able to verify this by unplugging one of the drives and trying to boot.  It should complain.

What's the output of this command:

```
sudo ls /dev | grep sd
```

?

(As a side question, why are you using 14.10 and not say 14.04 for a server?   14.10 has only a short support window and will need to be upgraded in July when support ends.  14.04 is an LTS version that is supported until 2019.)

---

### Post by r0d3nt on 2015-04-11
The array would assemble correctly if the other drive would get assigned a device id but it never does on the server.  On the desktop system, both drives are seen properly and are given a device id in /dev/.

Here's the output of the command,
```
uquevedo@bigbox:~$ sudo ls /dev | grep sd[sudo] password for uquevedo: 
sda
sda1
sdb
sdb1
sdb2
sdb3
sdb5
sdc
sdc1
sdc2
sdc3
sdc5
sdd
sdd1
sde
sde1
sdf
sdf1
sdg
sdg1

```
All of the raid 1 arrays I have plugged into the onboard Intel raid controller are configured through the md software raid and are working fine, it's just that /dev/md3 can't assemble because the other drive attached to the sil3112 isn't given a proper device id [probably was supposed to be /dev/sdb given how the add-in card took /dev/sda].

Here's the output for my arrays:
```
root@bigbox:~# for X in /dev/md?;do mdadm --detail $X;done
/dev/md0:
        Version : 1.2
  Creation Time : Tue Mar 17 17:07:34 2015
     Raid Level : raid1
     Array Size : 471548928 (449.70 GiB 482.87 GB)
  Used Dev Size : 471548928 (449.70 GiB 482.87 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sat Apr 11 14:37:03 2015
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : bigbox:0  (local to host bigbox)
           UUID : dd18f02d:a1894256:900d051b:39edeceb
         Events : 168913


    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       2       8       34        1      active sync   /dev/sdc2
/dev/md1:
        Version : 1.2
  Creation Time : Tue Mar 17 17:07:50 2015
     Raid Level : raid1
     Array Size : 16207872 (15.46 GiB 16.60 GB)
  Used Dev Size : 16207872 (15.46 GiB 16.60 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Sat Apr 11 01:34:10 2015
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : bigbox:1  (local to host bigbox)
           UUID : 0bff6729:3f827abd:bc68fc25:c1c2f3f8
         Events : 344


    Number   Major   Minor   RaidDevice State
       0       8       21        0      active sync   /dev/sdb5
       2       8       37        1      active sync   /dev/sdc5
/dev/md2:
        Version : 1.2
  Creation Time : Tue Mar 17 17:07:58 2015
     Raid Level : raid1
     Array Size : 976629760 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976629760 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sat Apr 11 14:37:03 2015
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : bigbox:2  (local to host bigbox)
           UUID : 8ab87492:4498f81d:fc0e578b:7de11213
         Events : 92206


    Number   Major   Minor   RaidDevice State
       2       8       49        0      active sync   /dev/sdd1
       1       8       65        1      active sync   /dev/sde1
/dev/md3:
        Version : 1.2
     Raid Level : raid0
  Total Devices : 1
    Persistence : Superblock is persistent


          State : inactive


           Name : bigbox:3  (local to host bigbox)
           UUID : 4cfbb1b2:f3428f56:c481ab55:d9e66ee7
         Events : 7382


    Number   Major   Minor   RaidDevice


       -       8        1        -        /dev/sda1
/dev/md4:
        Version : 1.2
  Creation Time : Tue Mar 17 17:08:40 2015
     Raid Level : raid1
     Array Size : 1953382400 (1862.89 GiB 2000.26 GB)
  Used Dev Size : 1953382400 (1862.89 GiB 2000.26 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sat Apr 11 11:49:38 2015
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : bigbox:4  (local to host bigbox)
           UUID : a8b54303:f0e6843a:ca722c91:1d4eebde
         Events : 6951


    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8       97        1      active sync   /dev/sdg1
```
Here's the mdadm examination of the drives:
```
root@bigbox:~# for X in /dev/sd*[1-5];do mdadm --examine $X;done
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 4cfbb1b2:f3428f56:c481ab55:d9e66ee7
           Name : bigbox:3  (local to host bigbox)
  Creation Time : Tue Mar 17 17:08:29 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 976629760 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : fbb240c4:f6ad0d66:13b406be:1ad091d4


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 11 03:00:43 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : d4e84d0c - correct
         Events : 7382




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
mdadm: No md superblock detected on /dev/sdb1.
/dev/sdb2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd18f02d:a1894256:900d051b:39edeceb
           Name : bigbox:0  (local to host bigbox)
  Creation Time : Tue Mar 17 17:07:34 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 943097856 (449.70 GiB 482.87 GB)
     Array Size : 471548928 (449.70 GiB 482.87 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : active
    Device UUID : e9fa950f:36aa714c:df3e0988:4732edae


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 11 14:42:33 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 745bdfe1 - correct
         Events : 168914




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb3:
   MBR Magic : aa55
Partition[0] :     32432128 sectors at            2 (type fd)
/dev/sdb5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0bff6729:3f827abd:bc68fc25:c1c2f3f8
           Name : bigbox:1  (local to host bigbox)
  Creation Time : Tue Mar 17 17:07:50 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 32415744 (15.46 GiB 16.60 GB)
     Array Size : 16207872 (15.46 GiB 16.60 GB)
    Data Offset : 16384 sectors
   Super Offset : 8 sectors
   Unused Space : before=16296 sectors, after=0 sectors
          State : clean
    Device UUID : b920bece:5cf6a189:39e3cb54:b849bb59


    Update Time : Sat Apr 11 01:34:10 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : f75c41e8 - correct
         Events : 344




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
mdadm: No md superblock detected on /dev/sdc1.
/dev/sdc2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : dd18f02d:a1894256:900d051b:39edeceb
           Name : bigbox:0  (local to host bigbox)
  Creation Time : Tue Mar 17 17:07:34 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 943097856 (449.70 GiB 482.87 GB)
     Array Size : 471548928 (449.70 GiB 482.87 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : active
    Device UUID : 3ed12f13:56705991:5ba54668:a9bc1978


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 11 14:42:33 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 66476d36 - correct
         Events : 168914




   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc3:
   MBR Magic : aa55
Partition[0] :     32432128 sectors at            2 (type fd)
/dev/sdc5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0bff6729:3f827abd:bc68fc25:c1c2f3f8
           Name : bigbox:1  (local to host bigbox)
  Creation Time : Tue Mar 17 17:07:50 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 32415744 (15.46 GiB 16.60 GB)
     Array Size : 16207872 (15.46 GiB 16.60 GB)
    Data Offset : 16384 sectors
   Super Offset : 8 sectors
   Unused Space : before=16296 sectors, after=0 sectors
          State : clean
    Device UUID : 4be54e5d:ae819c15:ebd0c9f5:c300f387


    Update Time : Sat Apr 11 01:34:10 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : e11d368b - correct
         Events : 344




   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8ab87492:4498f81d:fc0e578b:7de11213
           Name : bigbox:2  (local to host bigbox)
  Creation Time : Tue Mar 17 17:07:58 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 976629760 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 08e353e8:e4055b33:a76b582c:99af61aa


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 11 14:42:33 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 11e7f63b - correct
         Events : 92206




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 8ab87492:4498f81d:fc0e578b:7de11213
           Name : bigbox:2  (local to host bigbox)
  Creation Time : Tue Mar 17 17:07:58 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 976629760 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 1a45ab31:f4c9bc59:72ef5536:c400773e


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 11 14:42:33 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 1fb3f151 - correct
         Events : 92206




   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : a8b54303:f0e6843a:ca722c91:1d4eebde
           Name : bigbox:4  (local to host bigbox)
  Creation Time : Tue Mar 17 17:08:40 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 1953382400 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 4ed8cfd6:411cb6e8:c08357d6:dbaf7991


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 11 11:49:38 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 90be010d - correct
         Events : 6951




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : a8b54303:f0e6843a:ca722c91:1d4eebde
           Name : bigbox:4  (local to host bigbox)
  Creation Time : Tue Mar 17 17:08:40 2015
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 1953382400 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : b2946b6c:e17e600b:7ffbd8a4:70c61bc3


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Apr 11 11:49:38 2015
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 4927ae65 - correct
         Events : 6951




   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
```

So back to my original problem, why is it that on my desktop based system both drives are seen independently correctly, but with the same card/drives on my server system they are not?

To answer your side question, this server that was just rebuilt and used to be a Fedora server that I decided to redo as a Ubuntu server.  It's my own personal server for home, so I don't mind the short release windows since I'll likely just upgrade it when the next release is out.

---

### Post by weatherman2 on 2015-04-11
So to be clear, the RAID on the Silicon Image card is also a software RAID, which you wish to assemble with mdadm, even though this could be (or was) a hardware RAID card?

I would unplug all of the other drives from the motherboard (except the one that has the OS) and see if that works any differently.   If not, plug those two drives into the motherboard SATA ports and see if you can assemble the array.  If you can, then that tells you the drives themselves are not causing any problems.

You're certain the Silicon Image card isn't trying to turn them into a hardware array?  Yes, I know it works differently on the desktop version - and I don't know why.

---

### Post by r0d3nt on 2015-04-12
The drives attached to the sil3112 controller are configured for software RAID through linux, not through the controller card [there was never any hardware RAID].

A little back story on this problem...
I used to have all of the drives connected through two mini SAS connections from an onboard LSI 1068 raid controller that broke out into four connections each for a total of eight connections that connect through a backplane that enables hot swapping of the drives.  I never used the onboard LSI raid, and had all of the drives configured through software RAID.  I started to encounter I/O errors with the arrays and drives were starting to drop from the arrays because there were false positives for errors.  I have S.M.A.R.T. monitoring configured and the drives are tested regularly, and there are no errors ever registered.

For troubleshooting purposes, I swtiched from the mini SAS cables [which I suspected were causing the I/O errors] and plugged the drives into the SATA connections for this motherboard.  This motherboard has only six SATA connectors built-in which are only all fully accessible by turning on the Intel "hardware" RAID, otherwise I'm limited to only just four working SATA ports [weirdly limiting, but that's how it works].  The drives aren't configured through the Intel RAID though.  This is why I had to use an old sil3112 card that I had lying around to be able to get the two extra ports I needed.  The 6 drives that I have connected to the motherboard SATA connectors into the backplane with worked fine and was tested by booting into a live Desktop 14.10 session where I was able to access the RAID arrays from those 6 drives.  When I installed the sil3112 controller, I thought there was something wrong because it was only seeing only one of the two drives that were attached to it.

The sil3112 controller card used to be a Mac specific card [Sonnet Tempo SATA PCI], but I force flashed it to the latest available firmware for the Silicon Image site [which was a bit of a pain] that turns the card into a non-raid controller [it only sees the drives and doesn't give any options to RAID them on boot up].  Once I got the card flashed, I tested it on my Desktop based system with two random drives [and old 36GB Velociraptor and 500GB WD Black], and the system assigned /dev/sd type devices to both drives.  I even tested with the two 1TB drives I was using for my server, and both were assigned /dev/sd devices and the raid assembled just fine on the Desktop system [I was able to access the RAID array from MATE Caja].

With that successfully tested, I then plugged the card into the server motherboard only to confusingly have only one of the 1TB drives be given a /dev/sd device while the other seems to be seen, but not given a /dev/sd device.  This occurs from the Live Desktop 14.10 session and the booted Server 14.10, so I'm thinking it has something to do with the BIOS of this server mother board that is conflicting with how the sil3112 card is working.

I would disconnect all of the drives from the on board SATA ports except for the booth drive, but my /home partition is on one the arrays connected to the onboard SATA ports, which without a /home partition, I don't think I'd get very far past booting.

What I will try though is disconnecting all of the internal SATA connectors leaving only the two 1TB drives connected to the sil3112 controller and see if they are seen properly.

I'll report back my findings.

Also, from my initial dmesg snippet from the server, I forgot to include one part that might explain what is going on, specifically at 7.828043:
```
[    7.202236] sata_sil 0000:05:02.0: version 2.4
[    7.202802] hidraw: raw HID events driver (C) Jiri Kosina
[    7.206105] scsi0 : sata_sil
[    7.206315] scsi1 : sata_sil
[    7.206387] ata1: SATA max UDMA/100 mmio m512@0xc8300000 tf 0xc8300080 irq 28
[    7.206389] ata2: SATA max UDMA/100 mmio m512@0xc8300000 tf 0xc83000c0 irq 28
[    7.524043] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    7.601178] pps_core: LinuxPPS API ver. 1 registered
[    7.667679] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    7.735589] ahci 0000:00:1f.2: version 3.0
[    7.735924] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    7.804196] ahci 0000:00:1f.2: flags: 64bit ncq pm led pmp slum part 
[    7.828043] ata1.00: both IDENTIFYs aborted, assuming NODEV
[    7.872192] md: multipath personality registered for level -4
```
I'll do some research on this, but it just baffles me that this all worked properly on my desktop system without issue but is giving me so many problems on this server!

---

### Post by r0d3nt on 2015-04-12
...oK, I was coming back here to post on how I disconnected all of the internal SATA connectors and booted off of the USB Live Desktop 14.10 that I've been using for my testing and how the drives were still not showing up properly, but in the action of re-connecting the SATA cables to the motherboard and backplane...the two 1TB drives were now being detected properly and my other raid array is now active and seen.
```
root@bigbox:~# cat /proc/mdstatPersonalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdc5[0] sdd5[2]
      16207872 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdc2[0] sdd2[2]
      471548928 blocks super 1.2 [2/2] [UU]
      bitmap: 3/4 pages [12KB], 65536KB chunk


md2 : active raid1 sde1[2] sdf1[1]
      976629760 blocks super 1.2 [2/2] [UU]
      bitmap: 3/8 pages [12KB], 65536KB chunk


md3 : active raid1 sda1[1] sdb1[2]
      976629760 blocks super 1.2 [2/2] [UU]
      bitmap: 0/8 pages [0KB], 65536KB chunk


md4 : active raid1 sdh1[1] sdg1[0]
      1953382400 blocks super 1.2 [2/2] [UU]
      bitmap: 0/15 pages [0KB], 65536KB chunk


unused devices: <none>
root@bigbox:~# mdadm --detail /dev/md3
/dev/md3:
        Version : 1.2
  Creation Time : Tue Mar 17 17:08:29 2015
     Raid Level : raid1
     Array Size : 976629760 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976629760 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sun Apr 12 18:02:15 2015
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : bigbox:3  (local to host bigbox)
           UUID : 4cfbb1b2:f3428f56:c481ab55:d9e66ee7
         Events : 7382


    Number   Major   Minor   RaidDevice State
       2       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1
```
I did have to disconnect/reconnect the sata cables attached to the sil3112 card, so perhaps in reconnecting them, I exposed that perhaps one of the cables was loose and wasn't being fully seen?

I'm relieved that this looks to be working again, but annoyed that "it fixed itself".

I do know way more about mdadm, dmesg, and other low level linux stuff that I didn't quite know before, so I suppose there's that.

---

