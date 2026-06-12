---
title: "problems with hard disk"
date: 2011-07-26
forum: Hardware
---

### Post by feddozz on 2011-07-26
hi,

I was trying to install an operating system on one partition of a 30GB hard drive. I presume, because i did not pay attention to the order of the events until I realized that: 'Houston, we have a problem'. Anyway I presume that for some reason the machine shut off during the installation. After that I tried to install UBUNTU 11.04 and WattOS several times and I always got the same error: input/output error. Apparrently writing to the hard drive caused and error. Systematically it happened after say 5 minutes the installer started copying files to the drive. The error message sayd it was possible that the image I was using for installation was faulty, so I downloaded the images of the above OS's several times and unebootined them on my USB many times. Also I tried to install Tyne core on the HD with no success.

I tried different variants installing the systems on the whole disk, deleting all the existing partitions. I also created three 10GB partitions and tried installing in all of them, presuming that a sector could be damaged. No difference.

Also when I run WattOS live I cannot mount the partitions at all. 

I run smartmontools but it looks that the disk is ok!!?? Maybe I got it wrong. Soon I'll post the listings, I cannot now. 

It looks to me that there is a general problem with the disk. Would you suggest different analysis tools? 

Any idea?

---

### Post by 2F4U on 2011-07-26
Can you get the exact error message that occurred during installation? To me it looks more as if the usb installation media is faulty. Did you verify the downloaded iso?

---

### Post by feddozz on 2011-07-26
> **2F4U said:**
> Can you get the exact error message that occurred during installation? To me it looks more as if the usb installation media is faulty. Did you verify the downloaded iso?

that is very unlikely, in fact I tried to install three OS's, I  downloaded the images several times and checked check sums, as I said above. It is difficult that all of them where corrupted even after sum checks.

And if you consider that I can't mount the partitions of the drive...it's got nothing to do with the opartition media. The error message says that the media could be corrupted as well as the drive.

It looks to me like I screwed some setting on the drive. But I don't know where to look at.

---

### Post by feddozz on 2011-07-27
UPDATE: after running testdisk and rewriting the partition table the drive can be mounted again bu i still can't install operating systems yet.

Any help?

---

