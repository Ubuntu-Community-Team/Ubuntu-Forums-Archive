---
title: "External hardrive"
date: 2008-06-12
forum: Hardware
---

### Post by machosos on 2008-06-12
I am having issues when connecting my external hard drive.  i am running hardy heron but it does not load my seagate drive....any ideas???

---

### Post by tamoneya on 2008-06-12
can you go into terminal and post the result of:```
sudo fdisk -l
```

---

### Post by machosos on 2008-06-12
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfed8fed8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

---

### Post by tamoneya on 2008-06-12
```
sudo mkdir /media/external
sudo mount -t ntfs /dev/sdb1 /media/external
```Then look in /media/external for you files.

---

### Post by machosos on 2008-07-07
sorry for the delay!!! thanks for the help...it worked!!!

---

