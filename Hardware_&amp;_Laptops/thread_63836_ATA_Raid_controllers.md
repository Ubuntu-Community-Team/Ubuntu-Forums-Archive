---
title: "ATA Raid controllers"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by Belfast on 2005-09-09
I have an apdatec raid controller in my ubuntu box. I'm not using it for raid, i just use it as an ide controller to allow me to add 4 extra drives. it's an Adaptec 1200A PCI ATA100 RAID - Two-channel RAID 0/1 card supports up to four ATA/100 drives. I had an                                                                                                                                                                           Deskstar 7K250 Ultra ATA 160GB attached to it and i stared getting inode errors, i wided the drive and stared again, same thing happened, more inode errors.

I decided it was a faulty disk and was about to RMA it as it's only about 8 months old and hardly used. I put another 2  IBM DTLA-307075, 76.8GB disks on the same channel that i knew where healthy and they both came up with inode errors.

could it be the ide raid controller thats reading the drive wrong ?


uname -a
Linux sushi 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux


dmesg output

HPT370: IDE controller at PCI slot 0000:00:0b.0
HPT370: chipset revision 3
HPT37X: using 50MHz internal PLL
HPT370: 100% native mode on irq 10
    ide2: BM-DMA at 0xa000-0xa007, BIOS settings: hde: DMA, hdf: DMA
    ide3: BM-DMA at 0xa008-0xa00f, BIOS settings: hdg: DMA, hdh: DMA
Probing IDE interface ide2...
hde: IBM-DTLA-307075, ATA DISK drive
hdf: IBM-DTLA-307075, ATA DISK drive
ide2 at 0xb400-0xb407,0xb002 on irq 10
hde: max request size: 128KiB
hde: 150136560 sectors (76869 MB) w/1916KiB Cache, CHS=65535/16/63, UDMA(66)
hde: cache flushes not supported
 /dev/ide/host2/bus0/target0/lun0: p1
hdf: max request size: 128KiB
hdf: 150136560 sectors (76869 MB) w/1916KiB Cache, CHS=65535/16/63, UDMA(66)
hdf: cache flushes not supported
 /dev/ide/host2/bus0/target1/lun0: p1
Probing IDE interface ide3...
hdg: IC35L180AVV207-1, ATA DISK drive
hdh: HDS722512VLAT80, ATA DISK drive
ide3 at 0xa800-0xa807,0xa402 on irq 10
hdg: max request size: 1024KiB
hdg: 361882080 sectors (185283 MB) w/7965KiB Cache, CHS=22526/255/63, UDMA(100)
hdg: cache flushes supported
 /dev/ide/host2/bus1/target0/lun0: p1
hdh: max request size: 1024KiB
hdh: 241254720 sectors (123522 MB) w/7938KiB Cache, CHS=16383/255/63, UDMA(100)
hdh: cache flushes supported
 /dev/ide/host2/bus1/target1/lun0: p1


EXT3-fs error (device hde1): ext3_check_descriptors: Inode table for group 74 not in group (block 10813442)!
EXT3-fs: group descriptors corrupted !
EXT3-fs error (device hdf1): ext3_check_descriptors: Inode table for group 32 not in group (block 9437186)!
EXT3-fs: group descriptors corrupted !
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdh1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
EXT3-fs error (device hdf1): ext3_check_descriptors: Inode table for group 32 not in group (block 9437186)!
EXT3-fs: group descriptors corrupted !


thanks all

---

### Post by Belfast on 2005-09-09
some others having similar problems
seem its a buggy driver for the raid controller

[http://forums.gentoo.org/viewtopic.php?p=1799291&sid=dcffb5f80fe2e48ea311a8223dbd78b4](http://forums.gentoo.org/viewtopic.php?p=1799291&sid=dcffb5f80fe2e48ea311a8223dbd78b4)

---

