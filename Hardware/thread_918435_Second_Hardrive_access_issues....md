---
title: "Second Hardrive access issues..."
date: 2008-09-12
forum: Hardware
---

### Post by swirlz on 2008-09-12
Hi all...

I just installed a second hardrive for extra storage and am having issues accessing it.

it installed properly and I used gparted to partion it but I can't find it.

Here some output that might help??

j@j-desktop:~$ sudo fdisk -l
[sudo] password for j: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77efe401

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f14b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux


thanks!!...

---

### Post by swirlz on 2008-09-13
nvm... got it!

---

### Post by knattlhuber on 2008-09-13
Create a mountpoint by doing

```
sudo mkdir /media/data
```

Then mount the drive

```
sudo mount -t ext3 /dev/sdb1 /media/data
```

To automount on boot, you should add an entry for your drive in /etc/fstab, e.g.

```
/dev/sdb1   /media/data   ext3   defaults   0   0
```

(I'm assuming it's an ext3 formatted drive, if not replace 'ext3' accordingly)

---

