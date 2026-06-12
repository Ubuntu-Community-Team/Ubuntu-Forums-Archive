---
title: "Can't mount partitions from HDA, But will mount partitions from HDB"
date: 2008-08-08
forum: Hardware
---

### Post by ScottWilson1990 on 2008-08-08
Linux Version: Xubuntu (Latest Stable Release)
Window Manager: Xfce

Hi, I have 2 hard drives plugged in on this computer; a 120gb Maxtor Diamondmax +9 IDE which is called SDA in Linux and a 160gb Maxtor Diamondmax +9 IDE which is called SDB in Linux.

The 160 gig is partitioned into 5 partitions. 1 of which is my Linux install and one of which is the SWAP partition. The rest of the partitions are NTFS and just hold music/movies/backup files. All these are fine and I can mount them with no trouble what so ever, However the problems come when I try to mount the Master hard drive (the 120gig one).

The 120gig is partitioned into 4 partitions, all NTFS, one with my Windows Install on. When I try to mount any of the partitions from this hard drive, it doesn't let me, it acts as if the partitions don't exist. However in Fdisk -l all the partitions and both hard drives are clearly visible. I have pasted my FDISK for you to view below:


Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd065d065

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3824 30716248+ 7 HPFS/NTFS
/dev/sda2 3825 14946 89337465 5 Extended
/dev/sda5 3825 13614 78638143+ 7 HPFS/NTFS
/dev/sda6 13615 14946 10699258+ 7 HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e7e7e7e

Device Boot Start End Blocks Id System
/dev/sdb1 2 19929 160071660 f W95 Ext'd (LBA)
/dev/sdb5 2 2549 20466778+ 7 HPFS/NTFS
/dev/sdb6 3825 19929 129363381 7 HPFS/NTFS
/dev/sdb7 2550 3764 9759456 83 Linux
/dev/sdb8 3765 3824 481918+ 82 Linux swap / Solaris



The message I get when I try to mount any of the partitions is:

sudo mount -t ntfs /dev/sda5 /mnt/SDA5

ntfs-3g: Failed to access volume '/dev/sda5': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.



I have also tried:

sudo mount -t ntfs-3g /dev/sda5 /mnt/harddrive1
sudo mount -t ntfs-3g /dev/sda5 /mnt/harddrive1 -o force
sudo mount -t ntfs /dev/sda5 /mnt/harddrive1 -o force

and I've read through 1. man mount.ntfs, 2. /sbin/mount.ntfs --help and 3. /sbin/mount.ntfs-3g --help and countless numbers of forums.


I have also booted into an Arch Linux cd and from that console I was able to mount all of the partitions on the other hard drive. So that proves that its something in Xubuntu that's causing it not to mount them.

-Could it be something they have done to Xubuntu to make it even lighter?


It is as if its not registering that there is another hard drive there. But it obviously knows there is one because it shows it in fdisk. 



Thanks for any help in advance,
Scott.

---

