---
title: "Cannot Access External USB Drive"
date: 2010-08-24
forum: Hardware
---

### Post by quickwitt on 2010-08-24
I am booting 10.04 from a persistent install on an 8GB SD card on a Lenovo X201. Everything works as it should and the system is quick and stable. My problem is that my 500GB Seagate USB hard drive is not accessible. I have searched the forums and tried any number of things but cannot see anywhere that the exact issue was repeated. 

Here is what I have tried so far:

Booting into windows and using "safely remove". CHECK
Removing auto-mount options from Nautilus via gconf. CHECK
Manually mounting the hard drive with Disk Utility. CHECK 

There were a number of duplicate entries in /media which I removed. Now when I go to mount the drive I get an error 

"Error mounting: mount exited with exit code 21: mount: according to mtab, /dev/sdb1 is already mounted on /media/Expansion Drive"

When I try to view /etc/mtab I get an input/output error.

From within Disk Utility the disk is showing as unmounted.

This is extremely frustrating. I've used Ubuntu for years with many USB devices and have never experienced any problems. Any help would be greatly appreciated.

Thanks in advance.

---

### Post by ellgor on 2010-08-24
Hi,

I was having mounting and permission issues as well, found a post that mentioned an app called "usbmount" was causing the problems, removed said app, problem gone.

Regards, Ellgor.

---

### Post by quickwitt on 2010-08-24
USBmount isn't installed on my system. Any other thoughts?

When I browse to *Computer* the three partitions of the drive are shown. If I click on any of them i get the following:

"Error mounting: mount exited with exit code 21: mount: according to mtab, /dev/sdc1 is already mounted on /media/Expansion Drive" which doesn't make sense. There is no /etc/mtab file, only mtab.fuselock which is empty. There is no enry in /media for the drive either.

Fdisk -l returns:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaef61a68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       41278   312055172    7  HPFS/NTFS
/dev/sda2           41278       41346      512000   27  Unknown

Disk /dev/sdb: 7969 MB, 7969177600 bytes
221 heads, 20 sectors/track, 3521 cylinders
Units = cylinders of 4420 * 512 = 2263040 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2        3522     7778304    b  W95 FAT32

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd94f777e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       35305   283584032+   7  HPFS/NTFS
/dev/sdc2           35306       46778    92156872+   7  HPFS/NTFS
/dev/sdc4   *       46779       60802   112640000    7  HPFS/NTFS

Attempting to mount any of the partitions results in the same error message as above. Umount any of them returns *not mounted*.

---

### Post by quickwitt on 2010-08-25
<BUMP>

Anybody? Please?

---

