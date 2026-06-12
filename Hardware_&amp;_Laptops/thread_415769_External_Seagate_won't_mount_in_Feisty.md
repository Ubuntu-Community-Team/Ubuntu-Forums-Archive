---
title: "External Seagate won't mount in Feisty"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by petgraveyard on 2007-04-20
I have an external 400GB (expensive!) Seagate HD.  Output of fdisk -l

```
zach@ubuntu-desktop:~$ fdisk -l

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    c  W95 FAT32 (LBA)
zach@ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2341    18804051    7  HPFS/NTFS
/dev/sda2            2404        3649    10008495   83  Linux
/dev/sda3            2342        2403      498015   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    c  W95 FAT32 (LBA)
zach@ubuntu-desktop:~$ 

```

The hard drive will not mount.  I can manually mount to /media/windows, however, functionality there is limited, there's no icon on my HD, and when I reboot it doesn't mount.  WTF?  It worked fine in Edgy and Dapper.

Please help?

---

### Post by petgraveyard on 2007-04-20
And I have no idea why it listed the 400GB external twice.  It just started doing that after I manually mounted to /windows (used to be /dev/hdc)

---

### Post by taurus on 2007-04-20
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/windows   vfat   iocharset=utf8,umask=000   0   0
```
Save the change and reboot.

---

### Post by petgraveyard on 2007-04-20
Cool, it mounted when I started it up in that folder.  HOWEVER, how do I get it to show up as a drive on the Desktop and in the places menu?

Thanks for the help so far, man (or woman)!  :guitar:

---

