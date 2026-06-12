---
title: "Secondary Hard Drive Problems"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by SuperCow56 on 2007-03-07
I have a 2nd hard drive in my computer, and when I installed Ubuntu it didn't recognize it. How can I make my 2nd hard drive work?

---

### Post by taurus on 2007-03-07
Does the BIOS detect that harddrive at all?  And if it does, then boot with the LiveCD and at prompt, post this output here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by SuperCow56 on 2007-04-28
The BIOS does recognize it, and when I do sudo fdisk -l it says:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4791    38483676   83  Linux
/dev/sda2            4792        4998     1662727+   5  Extended
/dev/sda5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by RAKninja on 2007-04-28
it might be in a format ubuntu cant do anything wth (without a additional package) or it might just need to be mounted.

---

### Post by taurus on 2007-04-28
> **SuperCow56 said:**
> The BIOS does recognize it, and when I do sudo fdisk -l it says:

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4791    38483676   83  Linux
/dev/sda2            4792        4998     1662727+   5  Extended
/dev/sda5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Looks to me like you need to create a filesystem on /dev/sdb before you can use it.  Since you only have Ubuntu on your machine, I recommend you create /dev/sdb1 and format it to ext3.  You can do that with gparted.  

```
sudo aptitude update
sudo aptitude install gparted
```
System -> Administration

---

