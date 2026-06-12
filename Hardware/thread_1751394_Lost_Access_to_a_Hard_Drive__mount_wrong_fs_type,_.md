---
title: "Lost Access to a Hard Drive:  mount: wrong fs type, bad option, bad superblock on /de"
date: 2011-05-06
forum: Hardware
---

### Post by TimTow on 2011-05-06
I was re-arranging some data on a separate internal hard drive.  I was in the middle of transferring this data when the computer simply turned off.  This was not due to a loss of power.  When I turned the computer back on and tried to mount that same hard drive again my computer replied:

mount: wrong fs type, bad option, bad superblock on /dev/sdc5,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail 

The drive did not house an operating system or anything like that, it was just for storage.  Now I cannot get this thing to remount, it has been over a week and I am stumped.  The contents off the drive are important, and I need to recover it.  Does anybody have any ideas?  I searched all over the place for posts related to this topic but everyone else who has had a problem with this seem to have been mounting a disk that houses an operating system or some functional program, and I haven't been able to use their solutions so I decided to create a new thread.  

?

---

### Post by TimTow on 2011-05-06
when I type dmesg | tail i get:

[214281.101165] ppdev0: registered pardevice
[214281.149346] ppdev0: unregistered pardevice
[214302.271994] usblp0: removed
[271892.835529] usb 1-5: USB disconnect, address 4
[360030.845249] EXT2-fs error (device sdc5): ext2_check_descriptors: Block bitmap for group 256 not in group (block 4)!
[360030.845263] EXT2-fs: group descriptors corrupted!
[360203.019979] EXT2-fs error (device sdc5): ext2_check_descriptors: Block bitmap for group 256 not in group (block 4)!
[360203.019990] EXT2-fs: group descriptors corrupted!
[361634.597455] EXT2-fs error (device sdc5): ext2_check_descriptors: Block bitmap for group 256 not in group (block 4)!
[361634.597466] EXT2-fs: group descriptors corrupted!


when I type sudo fdisk -l i get:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed9a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24316   195318238+  83  Linux
/dev/sda2   *       24317       37799   108302197+   7  HPFS/NTFS
/dev/sda3           37800       38913     8948205    5  Extended
/dev/sda5           37800       38913     8948173+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000170e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008ead4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    5  Extended
/dev/sdc5               1       60801   488383969+  83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009011e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       59436   477419638+  83  Linux
/dev/sdd2           59437       60801    10964362+   5  Extended
/dev/sdd5           59437       60801    10964331   82  Linux swap / Solaris

---

### Post by TimTow on 2011-05-06
sudo fsck /dev/sdc5

[sudo] password for preston: 

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

