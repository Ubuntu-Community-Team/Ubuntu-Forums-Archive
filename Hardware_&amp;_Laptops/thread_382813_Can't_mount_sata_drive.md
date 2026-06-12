---
title: "Can't mount sata drive"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by bballs91 on 2007-03-12
Hey whenever i type "sudo fdisk -l" it shows me my sata drive, but it won't mount when i run "sudo mount -t ntfs /dev/sda1 /media/sda1".  Im running edgy with all the lastest updates as well as ntfs-3g installed. The strange thing is during my previous installations of ubuntu it automatically mounted the same drive/partition for me, but now it wont.

> 
fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**_/dev/sda1               1       13611   109330326    7  HPFS/NTFS_**

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3825    30724281    7  HPFS/NTFS
/dev/hda2            3826       19929   129355380    f  W95 Ext'd (LBA)
/dev/hda5            7651       19929    98631034    7  HPFS/NTFS
/dev/hda6            7520        7650     1052226   82  Linux swap / Solaris
/dev/hda7            3826        7519    29671992   83  Linux


---

### Post by John.Michael.Kane on 2007-03-12
Methods for mounting windows partitions.

[** Mounting Windows Partitions in Ubuntu**]("http://www.psychocats.net/ubuntu/mountwindows")

[**ntfs-3g how to**]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntsf-3g")

---

### Post by bballs91 on 2007-03-12
Nah those didn't work, heres the output of the mount command if it helps at all:

> mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Edit: Here's the output of "dmesg | tail"

> 
[17179623.532000] eth1: no IPv6 routers present
[17182981.836000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17182981.836000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17182981.836000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[17183044.620000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17183044.620000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17183044.620000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
[17193750.772000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17193750.772000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17193750.772000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.


---

