---
title: "500 gb iomega external hard drive"
date: 2012-06-05
forum: Hardware
---

### Post by nate_d099 on 2012-06-05
I'm very new to ubuntu, and unfortunately as it turns out, I cannot for the life of me mount my new hard drive. I've followed many random instructions online for people who seemed to have it halfway correct already, trying to mount random filenames to new directories and toying with and installing ntfs tools.

I'd like to know what to do. How do I find the name of what I'm supposed to mount? How am I supposed to mount such?
Thank you

---

### Post by dandnsmith on 2012-06-07
This somewhat depends on what state the drive is in - whether it has been formatted (and possibly partitioned) and if so what format.
If you post the results of *sudo fdisk -l*, we may be able to advise on suitable actions.

---

### Post by nate_d099 on 2012-06-08
Thanks. I hope this helps 

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b105

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112412672   83  Linux
/dev/sda2           13995       14594     4805633    5  Extended
/dev/sda5           13995       14594     4805632   82  Linux swap / Solaris

```

---

### Post by dandnsmith on 2012-06-08
That's not too promising - there isn't any sign of the external HDD.
Was it plugged in when you did this listing?
If so, then we have some sort of problem with your USB ports (or the HDD just isn't functioning at all)

---

### Post by nate_d099 on 2012-06-08
Well thats disheartening... But thank you

---

