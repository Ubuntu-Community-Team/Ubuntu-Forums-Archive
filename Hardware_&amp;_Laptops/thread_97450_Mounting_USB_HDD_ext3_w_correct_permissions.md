---
title: "Mounting USB HDD ext3 w/ correct permissions"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by psyguy92 on 2005-12-01
How do I do that?  I have an external IDE drive in a USB case that I reformated as ext3.  My automounting of USB devices and the CDROM haven't been working properly for a while now, so I've been manually mounting things when I need them (pita, but that's another problem).

My drive is at sdb1.  I tried to do:
```
mount /dev/sdb1 /media/usb120 -t ext3 -o rw,umask=0000,uid=1000
```
but as I found out, those options are invalid with ext3 (I read man mount).

The System -> Admin -> Disks graphical application is able to mount this disc, but does it as read only.  I want read/write access to it, and have user id 1000 as it's owner, not root.  How it is now, I can't really use the drive :(

Please help

---

### Post by psyguy92 on 2005-12-01
Oh, I just did an fdisk -l and this was the output:
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        7881    63239872+   7  HPFS/NTFS
/dev/sda3           11707       12161     3654787+  db  CP/M / CTOS / ...
/dev/sda4            7882       11706    30724312+   5  Extended
/dev/sda5   *        7882       11546    29439081   83  Linux
/dev/sda6           11547       11706     1285168+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    c  W95 FAT32 (LBA)

```

It *looks* like, from this, that sdb1 is actually vfat.  But I reformated using the disks manager application, and viewing the drive with disks manager, it shows up as ext3.  Maybe this has something to do with something?  This is going over my head a bit ...

---

### Post by psyguy92 on 2005-12-01
Well, I opened a nautilus as root, and changed the permissions/owner on the mounted drive using the permissions tab.  I was then able to write to the drive as a normal user.  This is a really convoluted way of doing this.  Can someone tell me the correct command to use, or a better way of doing this?  Currently, I have to open a shell, mount using sudo, then open nautilus as root, navigate to the correct folder, then change the permissions.

---

### Post by ember on 2005-12-06
Well - at the moment I can't help, but I can confirm there is a problem. My automounting works flawless except for my ext3-partition on the external usb-harddisk - yet the fat32 partitions work.

I actually can mount it respectively it gets mounted automatically, but the ext3 partition is root/755 in contrast to the fat32 partitions which have ember/700 (ember is my standard user).

I just can't find where to adjust the standard permissions for the ext3 partition.

Best,
ember

---

