---
title: "Cannot mount NTFS flash drive"
date: 2011-05-22
forum: Hardware
---

### Post by TBhX£2760R8@nK7§r on 2011-05-22
I'm running ubuntu 10.10 off a flash drive, and am trying to mount an 8 GB flash drive. I had it mounted, and everything worked fine. Now, when I try to mount it, I get 
```
mark@ubuntu:/media$ sudo mount /dev/sdb1 /media/8GB/ -o mode=777
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

```
```
sudo fuser /dev/sdb1
Cannot stat file /proc/3776/fd/21: Stale NFS file handle
Cannot stat file /proc/3850/fd/21: Stale NFS file handle
Cannot stat file /proc/3854/fd/21: Stale NFS file handle

```

And as most help topics around this problem ask for the output of 
sudo fdisk -l:
```
Disk /dev/sda: 2017 MB, 2017459712 bytes
4 heads, 32 sectors/track, 30783 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30784     1970159+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         984     7897056+   7  HPFS/NTFS
Partition 1 has different physical/logical endin
```
sudo blkid
```
/dev/loop0: TYPE="squashfs"
/dev/loop1: LABEL="casper-rw" UUID="de8c3e2f-e737-434a-abf1-383254f88a83" TYPE="ext2"
/dev/sda1: LABEL="PENDRIVE" UUID="1908-1506" TYPE="vfat"
/dev/sdb1: LABEL="8GB" UUID="1EE8524FE8522575" TYPE="ntfs"

```
cat /etc/fstab
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

What am I doing wrong?
Thanks for any help.


Oh, and it's not already mounted,
```
sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted
```
I also checked the GUI on this.

---

