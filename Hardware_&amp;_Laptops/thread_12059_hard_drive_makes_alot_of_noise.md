---
title: "hard drive makes alot of noise"
date: 2005-01-21
forum: Hardware &amp; Laptops
---

### Post by nico on 2005-01-21
Hey,
in Ubuntu my external USB Lacie harddrive makes a lot of noise, especially when accessing a folder with a lot of subfolders. Every write operation is accompanied by very loud rattling. In Windows the harddrive works almost in complete silence. I'm afraid I'm damaging my harddrive or something. I also get the following message in dmesg: 

```
usb 4-3.1: new high speed USB device using address 4
SCSI subsystem initialized
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
  Vendor: Maxtor    Model: 6Y160P0           Rev: YAR4
  Type:   Direct-Access                      ANSI SCSI revision: 02
USB Mass Storage device found at 4
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
SCSI device sda: 320173056 512-byte hdwr sectors (163929 MB)
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 p6 >
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sda4.
udf: registering filesystem
attempt to access beyond end of device
sda4: rw=0, want=68, limit=2
attempt to access beyond end of device
sda4: rw=0, want=1252, limit=2
attempt to access beyond end of device
sda4: rw=0, want=1028, limit=2
UDF-fs: No partition found (1)
attempt to access beyond end of device
sda4: rw=0, want=66, limit=2
isofs_fill_super: bread failed, dev=sda4, iso_blknum=16, block=32
attempt to access beyond end of device
sda4: rw=0, want=3, limit=2
HFS+-fs: unable to find HFS+ superblock
attempt to access beyond end of device
sda4: rw=0, want=3, limit=2
VFS: Can't find a HFS filesystem on dev sda4.
attempt to access beyond end of device
sda4: rw=0, want=4, limit=2
EXT3-fs: unable to read superblock
attempt to access beyond end of device
sda4: rw=0, want=4, limit=2
EXT2-fs: unable to read superblock
attempt to access beyond end of device
sda4: rw=0, want=18, limit=2
ReiserFS: sda4: warning: sh-2006: read_super_block: bread failed (dev sda4, bloc k 8, size 1024)
attempt to access beyond end of device
sda4: rw=0, want=130, limit=2
ReiserFS: sda4: warning: sh-2006: read_super_block: bread failed (dev sda4, bloc k 64, size 1024)
ReiserFS: sda4: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda4
SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
SGI XFS Quota Management subsystem
attempt to access beyond end of device
sda4: rw=0, want=8, limit=2
XFS: SB read failed
attempt to access beyond end of device
sda4: rw=0, want=72, limit=2
attempt to access beyond end of device
sda4: rw=0, want=128, limit=2


```

VFS complains about not finding a valid FAT partition but I formatted all my partitions in Windows in FAT32. And the harddrive does work, but with a lot of noise.

---

### Post by 23meg on 2005-04-14
have you set any preferences for acoustic management under windows with some utility? this sounds like (pardon the pun) such an issue; maybe you can set acoustic management preferences in hdparm? i'm not sure so you'll have to type "man hdparm" and check out. and it wouldn't hurt to google for linux acoustic management. good luck..

---

### Post by 23meg on 2005-04-19
i noticed that my laptop drive is making more noise than it should as well, and i'm almost sure mine is an acoustic management problem. i looked at the hdparm documentation and there *is* acoustic management support in there, but it hasn't helped me, yet. see [this thread](http://www.ubuntuforums.org/showthread.php?p=139976#post139976) .

---

