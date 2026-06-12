---
title: "Assigning SATA /dev/sda"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by DRVS on 2008-02-06
I am using Ubuntu at work to backup up several computers with none standard (scsi) partitions such as  Motorola's MVME187, Charles Rivers Data Systems, and AIX. 

I use the growisofs -Z /dev/dvd=/dev/sda to copy an image onto a DVD, and dd bs=32 if=/dev/dvd of=/dev/sda to put the dvd image back onto a hard drive. This works great

Once I added a 500g SATA hard drive so I can store a second image, things began to unravel.  About 75% of the time the SATA drive shows up as /dev/sda and the scsi drive shows up as /dev/sdb. The rest of the time the SATA drive shows up as /dev/sdb and the scsi shows up as /dev/sda. This makes it difficult to write a script. These drives keep changing even if I just reboot and do not make any changes.

Is it possible to lock the SATA drive as /dev/sda? 

I have tried not scanning the scsi during the BIOS, loading Ubuntu on the SATA drive, and other Linuxes. Mounting the SATA using the UUID will not help because I can not mount the scsi drive and need to read/write using

---

### Post by chrisdeckard on 2008-02-06
Could you use UUID by using the /dev/disk/by-id path instead?

```
root@auryn:/dev/disk/by-id# ls -l ata-ST3500630AS_9QXXXXXX
lrwxrwxrwx 1 root root 9 2008-01-20 23:24 ata-ST3500630AS_9QXXXXXX -> ../../sdg
```

At least for my Seagate 500GB drive, that last chunk there is the serial number.  There will be -partN (where N is the partition number) for each partition, so you can get the raw device, or each partition as needed.

-Chris

---

### Post by DRVS on 2008-02-22
Thanks Chris, I learned something new. Since this computer is used to back up over a hundred disks(10 different Part No), and I will not know the Part number of the disk I want to backup or restore, I am not sure this will work. I might be able to write a script to exclude the SATA. More importantly, I was looking for a good way to read the part number of the new hard drive.
Thanks again. David

---

### Post by chrisdeckard on 2008-02-22
I think it would be a nightmare to keep track of all that using my suggestion.  Are you hotswapping these disks?  You could probably setup something where by when you scan for new disks, it could detect them and then do "the right thing", whatever that is.  Good luck.  I'd be interested in your solution.

-Chris

---

