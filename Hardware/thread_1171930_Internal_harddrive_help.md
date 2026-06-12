---
title: "Internal harddrive help"
date: 2009-05-27
forum: Hardware
---

### Post by Mil Doc Jr on 2009-05-27
I used Gparted formatted my second internal harddrive sdb1 from NTFS to EXT3 and now it will not mount. Much less even show up in "Places" or anywhere else in my filesystem for that matter I ran ```
sudo fdisk -lu
``` and this is what was listed

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e045244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   224829674   112414806   83  Linux
/dev/sda2       224829675   234436544     4803435    5  Extended
/dev/sda5       224829738   234436544     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dad90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   234436544   117218241   83  Linux


What do I need to do to get my second harddrive to show up?  I googled around for a while and didn't see anything so I'm hoping someone here can help me out a little thanks.

---

### Post by x33a on 2009-05-27
you'll need to edit your fstab file.

post the output of
```
cat /etc/fstab
```

and 
```
sudo blkid
```

---

### Post by Mil Doc Jr on 2009-05-28
Thanks alot for the help

---

