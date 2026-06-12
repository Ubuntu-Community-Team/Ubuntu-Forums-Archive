---
title: "Is there any way to read files to access partition type 0x83?"
date: 2010-07-04
forum: Hardware
---

### Post by mooyoul on 2010-07-04
HI, I have HDD which is in tv settop box(STB).
and i connected it to my desktop.
It recognize hdd-drive but cannot read filesystem.
I use windows os, so checked it out with 'Acronis Disk Director' and it says partition type 0x83(Linux Native).
Is there any way to read files to access partition?
 
I've been solving this problem with commands so far, but they didn't work.
Here are commands lists used.
 
[IMG]http://61.79.23.155:7777/public/disk.png[/IMG]
===================================================================
sudo file -s /dev/sdc1
/dev/sdc1: data
 
fdisk -l
 
 
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x56420c29
Device Boot Start End Blocks Id System
/dev/sdc1 1 1275 10241437 83 Linux
/dev/sdc2 1276 1913 5124735 83 Linux
/dev/sdc3 1914 2551 5124735 83 Linux
/dev/sdc4 2552 19457 135797445 83 Linux
 
 
 
 
 
/etc/fstab
 
/dev/sdc1 /media/disk_ext2 ext2 defaults 0 2
 
 
 
 
 
 
 
 
mount -a
 
root@ubuntu:/home/prescott# sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so 
 
 
 
 
 
 
dmesg | tail
 
[ 7.937291] sd 8:0:0:1: [sde] Write Protect is off
[ 7.937296] sd 8:0:0:1: [sde] Mode Sense: 03 00 00 00
[ 7.937300] sd 8:0:0:1: [sde] Assuming drive cache: write through
[ 7.940913] sd 8:0:0:1: [sde] Assuming drive cache: write through
[ 7.940920] sde: sde1
[ 7.946543] sd 8:0:0:1: [sde] Assuming drive cache: write through
[ 7.946551] sd 8:0:0:1: [sde] Attached SCSI removable disk
[ 17.764010] eth0: no IPv6 routers present
[ 476.656334] VFS: Can't find an ext2 filesystem on dev sdc1.
 
 
 
prescott@ubuntu:~$ sudo blkid
[sudo] password for prescott: 
/dev/loop0: UUID="86a2de08-fccd-4811-ad7f-be3a20fe513e" TYPE="ext4" 
/dev/sda1: LABEL="RECOVERY" UUID="EAC4D143C4D11325" TYPE="ntfs" 
/dev/sda2: UUID="68B0BF03B0BED6B2" TYPE="ntfs" 
/dev/sda3: UUID="584CD3D44CD3AB50" TYPE="ntfs" 
/dev/sdb4: SEC_TYPE="msdos" LABEL="LiveREX_XP_" UUID="2310-19D9" TYPE="vfat" 
/dev/sde1: SEC_TYPE="msdos" LABEL="CANON_DC" UUID="73CB-4EBC" TYPE="vfat" 
prescott@ubuntu:~$ sudo blkid /dev/sdc1
prescott@ubuntu:~$ sudo blkid /dev/sdc2
prescott@ubuntu:~$ sudo blkid /dev/sdc3
prescott@ubuntu:~$ sudo blkid /dev/sdc4
===================================================================
 
 
I'm waitin for your relplies thank you, and please understand my poor English.
Have a good day.
 
 
David Prescott.

---

### Post by mooyoul on 2010-07-08
Add : Drive Information - Control Panel
 
 
 
[IMG]http://farm5.static.flickr.com/4119/4775061032_9c91e9d338_b.jpg[/IMG]
[http://www.flickr.com/photos/41107791@N05/4775061032/](http://www.flickr.com/photos/41107791@N05/4775061032/)

---

