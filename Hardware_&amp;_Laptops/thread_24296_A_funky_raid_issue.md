---
title: "A funky raid issue"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by revenazb on 2005-04-06
Hi All,

I'm new to ubuntu (Liking it quite a bit so far) but I am having a strange raid issue.
I have two arrays one raid1 that works perfectly and a small raid0 array that is giving me some trouble.
The raid0 (md1) array doesn't startup during boot with a superblock not found error. However once the system has booted all I need to do is: activate it and mount it and then it works no problem.

```
sudo mdadm -A /dev/md1
sudo mount /dev/md1
```

Here is the relevant part of dmesg:
```

Probing IDE interface ide0...
hda: ST3160021A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
Probing IDE interface ide1...
hdc: TOSHIBA DVD-ROM SD-M1612, ATAPI CD/DVD-ROM drive
hdd: CD-RW IDE4816, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
PDC20276: IDE controller at PCI slot 0000:02:08.0
ACPI: PCI interrupt 0000:02:08.0[A] -> GSI 18 (level, low) -> IRQ 18
PDC20276: chipset revision 1
PDC20276: 100% native mode on irq 18
    ide2: BM-DMA at 0xa400-0xa407, BIOS settings: hde:pio, hdf:pio
    ide3: BM-DMA at 0xa408-0xa40f, BIOS settings: hdg:pio, hdh:pio
Probing IDE interface ide2...
hde: ST3160021A, ATA DISK drive
ide2 at 0x9400-0x9407,0x9802 on irq 18
hde: max request size: 1024KiB
hde: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
hde: cache flushes supported
 /dev/ide/host2/bus0/target0/lun0: p1 p2 p3
Probing IDE interface ide3...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
md: md0 stopped.
md: bind<hda2>
md: bind<hde2>
raid1: raid set md0 active with 2 out of 2 mirrors
VFS: Can't find ext3 filesystem on dev md0.
VFS: Can't find an ext2 filesystem on dev md0.
ReiserFS: md0: found reiserfs format "3.6" with standard journal
ReiserFS: md0: using ordered data mode
ReiserFS: md0: journal params: device md0, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: md0: checking transaction log (md0)
ReiserFS: md0: Using r5 hash to sort names
hdc: ATAPI 48X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
cdrom: open failed.
cdrom: open failed.
ReiserFS: hda1: found reiserfs format "3.6" with standard journal
ReiserFS: hda1: using ordered data mode
ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: hda1: checking transaction log (hda1)
ReiserFS: hda1: Using r5 hash to sort names
ReiserFS: md1: warning: sh-2006: read_super_block: bread failed (dev md1, block 2, size 4096)
ReiserFS: md1: warning: sh-2006: read_super_block: bread failed (dev md1, block 16, size 4096)
ReiserFS: md1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on md1
Real Time Clock Driver v1.12
input: PC Speaker
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected AMD 760MP chipset
agpgart: Maximum main memory to use for agp memory: 1674M

```

And the /etc/mdadm/mdadm.conf file:
```
DEVICE partitions
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=7e414663:9e6cbca8:be641c49:566a059a
   devices=/dev/hde3,/dev/hda3
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=4654b127:9e5048b6:be43d2c7:19271e9c
   devices=/dev/hde2,/dev/hda2

```

Any help would be greatly appreciated.

Thanks
Bert

---

### Post by revenazb on 2005-04-08
Okay, 

Here is a bit more info hopefully this will generate some suggestions...
It seems that md0 gets mounted properly cause it is the root partition and therefore it is already activated (when it is mounted read-only at boot). The only problem I can see is the the md1 array is not activated by the time the boot process tries to mount hence the error message. Any suggestion on what to change in the order of the boot scripts to solve this problem?

Bert

---

### Post by steven_ellis on 2005-06-16
Ive got similar issues with my system and raid 0.

Have you looked at either of these articles.

[http://www.ubuntuforums.org/showthread.php?p=136548#post136548](http://www.ubuntuforums.org/showthread.php?p=136548#post136548) 

or

[http://www.ubuntuforums.org/showthread.php?t=42087&highlight=mdadm+raid](http://www.ubuntuforums.org/showthread.php?t=42087&highlight=mdadm+raid) 

Also have you now managed to fix your problems?

Steve

---

