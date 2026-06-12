---
title: "USB detection problem"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by Bobert on 2007-05-11
Hi, I am using Feisty and having an issue with detection of an external USB HDD.  The drive is a Fantom 1TB, and I am not sure if it is not detecting due to the size of the drive or support for it.  Are there any updates I can get to be able to be recognized?  Thanks

-Bob

---

### Post by taurus on 2007-05-11
Turn the external harddrive on; plug it into Ubuntu; open a terminal and paste the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Bobert on 2007-05-11
I dont know what that LBA means but im guessing it has something to do with it.  

> Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14212   114157858+  83  Linux
/dev/sda2           14213       14589     3028252+   5  Extended
/dev/sda5           14213       14589     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000215674880 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976768033+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24792   199141708+   b  W95 FAT32


---

### Post by taurus on 2007-05-11
Try

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o iocharset=utf8,umask=000
df -h
```

---

### Post by Bobert on 2007-05-11
Wonderful!! 

I wish I had your knowledge!

Thanks

---

