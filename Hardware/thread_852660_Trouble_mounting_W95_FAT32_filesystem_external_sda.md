---
title: "Trouble mounting W95 FAT32 filesystem external sda"
date: 2008-07-07
forum: Hardware
---

### Post by PaiPimenta on 2008-07-07
Dear Ubuntu Community,

Help! I use fdisk to clear and install a single, full disk sized partition on an external /dev/sda, creating /dev/sda1, type W95 FAT32 (hex code "b") in order to transfer the data from one of my /dev/hdb partitions to this external old laptop drive now in a case (the data being all my old windows xp laptop files).

Despite the trouble I'll have of restoring this old xp system, I am currently not even able to mount the external hard drive, I think due to an incorrect filesystem type.

I even tried formatting the disk on my Mac iBookG4 running OS X 10.3.9 with Disk Utility as an MS-DOS filesystem, and was able to mount and copy the data with something like

sudo mount -t msdos /dev/sda1 /mnt/VieO

..... with eightand.thr filenames!!! (8.3, old school msdos)
This isn't what I want, since I will obviously run into problems with programs calling files by their proper long windows names, and running into ~abbreviated DOS ones.


Man, what do I do?? I want to reformat and reinstall Xubuntu, replacing my command line only ubuntu, which is probably why the X gui is having problems despite fully installing past the 6% software install cut-off bug.... but I've got this important data stuck on my internal hard drive.  

Any help with a filesystem suggestion/mount commands?

Here's what I've done:

sudo fdisk /dev/sda

I make one primary partition to fill the disk, type "b", W95 FAT32.

sudo mount -t vfat /dev/sda1 /mnt/VieO

typical wrong file system mount message...


Do I need to do more DOS/WinXP compatible things in the fdisk?  How about FAT considerations?


Pepper
aka PaiPimenta

---

### Post by glathoud on 2008-08-02
Hello,

I am having a similar problem with a W95 FAT32 (LBA) partition.

 * the old Ubuntu breezy badger mounted it automatically and successfully.

 * the new Ubuntu 8.04 fails:

gl@gl-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3335    26785048+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3336        5535    17671500    c  W95 FAT32 (LBA)
/dev/sda3            5536        9729    33688305    f  W95 Ext'd (LBA)
/dev/sda5            5536        5797     2101648+  82  Linux swap / Solaris
/dev/sda6            5798        9729    31583758+  83  Linux

gl@gl-laptop:~$ sudo mount -t fat32 /dev/sda2 /media/sda2
mount: unknown filesystem type 'fat32'
mount: maybe you meant 'vfat'?
gl@gl-laptop:~$ sudo mount -t vfat /dev/sda2 /media/sda2
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

gl@gl-laptop:~$  dmesg | tail
[ 3090.379189] FAT: invalid media value (0xdb)
[ 3090.379202] VFS: Can't find a valid FAT filesystem on dev sda2.

If it could work, that would be very satisfying !!!

Cheers,

Guillaume

---

### Post by glathoud on 2008-08-02
...well after a reboot on XP (NTFS partition), it appeared that the WIN95 FAT32 (LBA) partition was damaged by the Ubuntu 8.04 install: XP could not recognize it anymore :(

...so I could only format the partition.... I chose NTFS this time since FAT32 sounds risky.... :(

---

### Post by zzats on 2008-08-02
would

mkfs.vfat /dev/targetdrive

solve the problem? One could always use cfdisk to rebuild the partition table, too..

---

