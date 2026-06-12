---
title: "Trouble with external drives"
date: 2010-10-16
forum: Hardware
---

### Post by pdesopo on 2010-10-16
I've previously tried some Ubuntu rel. and I never got any trouble connecting external USB drives NTFS, Ubuntu always correctly mounted the drives. Today I've installed Ubuntu Netbook Edition 10.10 and when I plug in an external drive, here's the message I get:

```

mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

```I don't understand what's the problem, any hints?

---

### Post by luvshines on 2010-10-16
It's just an external NTFS, right ??

Should not it be something like /dev/sdb or /dev/sdc, why is it recognizing it as /dev/sda1
What does this say:
```
sudo fdisk -l
```

---

### Post by pdesopo on 2010-10-16
here's what it says:

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00053816

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241127424   83  Linux
/dev/sda2           30020       30402     3068929    5  Extended
/dev/sda5           30020       30402     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8a300d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

```

---

### Post by luvshines on 2010-10-16
Can you mount it manually:```

sudo mkdir -p /media/myhdd
sudo mount /dev/sdb1 /media/myhdd
```

---

### Post by pdesopo on 2010-10-16
Yes, it worked! I don't understand why it doesn't work automatically though.

---

### Post by luvshines on 2010-10-16
Looks like for some reason (which is unknown to me), it's being treated as /dev/sda1 instead of /dev/sdb1 and since sda1 is already root partition, it says that it is already mounted on /

---

### Post by cbemerine on 2010-10-16
I bet if you list the contents of your FSTAB, mtab and the blkid command someone will be able to help you.  

cat /etc/FSTAB 
cat /etc/mtab
blkid


This link will give you all the information you ever wanted to know about FSTAB: 

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)


you can also grep through your dmesg for messages related to the drives in question.

dmesg | grep sda

---

