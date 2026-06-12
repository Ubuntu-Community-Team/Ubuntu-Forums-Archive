---
title: "external drive permissions problem"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by komaroveli on 2007-01-01
hi all,
i've got external drive, which i have formatted using Gparted to fat32 fs so i could share it with winxp partition, for backups and such. well, no surprise here that my external drive after format belongs to root, that is i can't read or write on it. i could go to my winxp partition and format from there to solve permission issue, but i rather learn how to do it from ubuntu. so would you be kind to tell me how can i change permanently permissions on external drive?

thnx

---

### Post by taurus on 2007-01-01
How do you mount your external harddrive, from a terminal or through /etc/fstab?

---

### Post by komaroveli on 2007-01-01
> **taurus said:**
> How do you mount your external harddrive, from a terminal or through /etc/fstab?
hi taurus,
i wish i could tell you. i turn drive on and it's mounted automatically. 
but this is strange. yesterday i looked in properties and it told me mount point /dev/sda. so i ran command : ```
sudo chmod -R 777 /dev/sda
``` . but it didn't change anything. even i unmounted (eject) disk and turned it back again it was still under root permissions. and just now when i was reading your post i wanted to look again at mount point of the disk and i saw that it's not under root any more. i can read and write on it ](*,) 
i really don't understand this.
but if it's not much troubles please tell me how to mount from terminal and through /etc/fstab. i'm trying to learn as much as i can, so...help will be appreciated.

---

### Post by taurus on 2007-01-01
Okay, what's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by komaroveli on 2007-01-01
> **taurus said:**
> Okay, what's the output of this command from a terminal?

```
sudo fdisk -l
```

here it is
```
Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1567    12586896   83  Linux
/dev/hda2            1568        1741     1397655   82  Linux swap / Solaris
/dev/hda3            1742        5005    26218080   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1896    15229588+   7  HPFS/NTFS
/dev/hdb2            1897        9728    62910540    f  W95 Ext'd (LBA)
/dev/hdb5            1897        9728    62910508+   e  W95 FAT16 (LBA)

Disk /dev/sda: 300.0 GB, 300090727936 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666    b  W95 FAT32

```

---

### Post by taurus on 2007-01-01
And /dev/sda1 is the one you want to mount with read/write permission for all users.  

Open a terminal, Applications -> Accessories -> Terminal, and edit your /etc/fstab.

```
gksudo gedit /etc/fstab
```
Scroll to the end and add the following line to it.

```
/dev/sda1   /media/sda1   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then, create a new mount point for it.

```
sudo mkdir /media/sda1
```
Reboot and /dev/sda1 will be mounted to /media/sda1 everytime and you can write to it.

---

