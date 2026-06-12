---
title: "rebuild fstab"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by AllesMeins on 2007-01-23
Hi,

i recently made some bigger changes on my harddisc partitions (i did it out of windows). Merged some partitions, changed one from ntfs to ext3 and so on. My problem is now, that these changes are not reflected in my /etc/fstab giving me errors during bootup. Is there a way to auto rebuild the fstab (like it was done, when installing ubuntu) or do i have to make all the changes manualy?

Marc

---

### Post by Stephen Howard on 2007-01-23
I know that some other distros include scripts for automatically generating fstabs, but I don't think there's anything available on an installed Ubuntu system (I had a quick look and couldn't find anything).

I might be able to help you manually do it if you were to provide a copy of your current [FONT="Fixedsys"]fstab,[/FONT]  a copy of [FONT="Fixedsys"]/proc/partitions[/FONT].  A list of errors would also be useful.

---

### Post by taurus on 2007-01-23
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by AllesMeins on 2007-01-23
```

$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sda5               2        1532    12297726    7  HPFS/NTFS
/dev/sda6            1533        3062    12289693+   b  W95 FAT32
/dev/sda7            3063        5101    16378236    7  HPFS/NTFS
/dev/sda8            5102       11476    51207156   83  Linux
/dev/sda9           11477       19457    64107351    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2        1532    12297726    7  HPFS/NTFS
/dev/sdb6            1533        3062    12289693+   b  W95 FAT32
/dev/sdb7            3063        5101    16378236    7  HPFS/NTFS
/dev/sdb8            5102       11476    51207156   83  Linux
/dev/sdb9           11477       19457    64107351    7  HPFS/NTFS

Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276       14595   106992900    f  W95 Ext'd (LBA)
/dev/hda5            1276        3187    15358108+   7  HPFS/NTFS
/dev/hda6            3188        8924    46082421    7  HPFS/NTFS
/dev/hda7            8925       11535    20972826   83  Linux
/dev/hda8           11536       14085    20482843+  83  Linux
/dev/hda9           14086       14595     4096543+  82  Linux swap / Solaris



$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=e58ad035-274f-43f1-9217-3d87ab32cad3 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda8
UUID=fcf1673a-3723-430c-bf2f-844fe11a6148 /home           ext3    defaults
  0       2
# /dev/hda1
UUID=E46413B564138A06 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/hda5
UUID=00000000424EEB21 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/hda6
UUID=00000000849DEB3A /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/sda5
UUID=0000000040DC42CB /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/sda6
UUID=81B8-89BE  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=625C13605C132E73 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/sda8
UUID=20306AFB306AD776 /media/sda8     ntfs    defaults,nls=utf8,u
mask=777,gid=46 0       1
# /dev/sda9
UUID=706879A568796AAC /media/sda9     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/sdb5
UUID=0000000040DC42CB /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/sdb6
UUID=81B8-89BE  /media/sdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb7
UUID=625C13605C132E73 /media/sdb7     ntfs    defaults,nls=utf8,umask=007,gid=46                                                                           0       1
# /dev/sdb8
UUID=20306AFB306AD776 /media/sdb8     ntfs    defaults,nls=utf8,umask=007,gid=46                                                                           0       1
# /dev/sdb9
UUID=706879A568796AAC /media/sdb9     ntfs    defaults,nls=utf8,umask=007,gid=46                                                                           0       1
# /dev/hda9
UUID=4e9b3460-2198-4ab9-8db9-6352421d8a2d none            swap    sw                                                                                        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

#Linkstation
#//192.168.0.150/share   /media/share    smbfs     username=none,password=,gid=100                                                                          ,uid=1000,fmask=700,iocharset=utf8,codepage=cp850,noauto 0 0
#//192.168.0.150/share   /mnt/share    cifs     uid=1000,username=none,guest,iocha                                                                          rset=utf8

```

---

### Post by taurus on 2007-01-23
I would modify /etc/fstab and replace all the entries with UUID with the actual device name like /dev/hda1 thing.

```
gksudo gedit /etc/fstab
```

---

### Post by ishkabibble on 2008-03-23
AllesMeins, did this work for you?  Please post what your fstab looks like now.  I'm having the same issues and am hesitant to get rid of the UUIDs in fstab.

---

### Post by AllesMeins on 2008-03-23
Yes it worked fine for me. Just keep a backup of your old fstab somewhere until your sure that your changes work.
If you don't like using the device-names you can also use the label of the partition (thats what I did). In fact I'm using now a pretty random mixture of the different methods 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=e58ad035-274f-43f1-9217-3d87ab32cad3 /                 ext3    defaults,errors=remount-ro 0       1
# /dev/hda8
UUID=fcf1673a-3723-430c-bf2f-844fe11a6148 /home             ext3    defaults        0       2
# /dev/sda6
LABEL=downloads          /home/gedinixan/downloads/         ext3    defaults       0       2
LABEL=arbeit             /home/gedinixan/arbeit             ext3    defaults       0       2
LABEL=backups            /home/gedinixan/backups/           ext3    defaults       0       2


# /dev/hda1
/dev/hda1        /media/hda1     ntfs-3g   defaults,nls=utf8                    0       1
# /dev/hda5
/dev/hda5        /media/hda5     ntfs-3g    defaults,nls=utf8                   0       1
[...]

```

---

