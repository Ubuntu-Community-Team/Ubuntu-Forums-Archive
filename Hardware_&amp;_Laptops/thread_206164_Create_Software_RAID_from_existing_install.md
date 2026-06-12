---
title: "Create Software RAID from existing install"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by mozmac on 2006-06-29
Hey, great site here.  I use it ALL THE TIME.  Looking forward to the day when I'll have enough knowledge to help others out on this site.

I already have 6.06 server installed on my box.  I threw a second, 30GB (it was free, okay?) drive in there and would like to get both drives working together in a Software RAID.  I would not like to reinstall the system as it's currently hosting a website.  The second drive is on the second IDE bus inside the computer as is already formatted to ext3 to match the boot drive.

Is is possible to set this up without affecting my currently running system (other than a couple restarts)?  When I first installed Ubuntu I formatted the drive with LVM.  Any pointers?  Links?  Insight?  Please let me know.  Thanks!

---

### Post by ohgod on 2006-06-29
This kind of thing is possible, but it's a big pain in the neck.  Basically you have to make a degraded array with the new disk while leaving the current disk alone (so it doesn't overwrite the os).  Then you'll need to copy all the files from the current disk to the new degraded array.  After that's done you can make the current disk an active member of the array, and it'll start syncing the disks.  

Here's a debian guide for doing this kind of thing:  [http://www.debian-administration.org/articles/238](http://www.debian-administration.org/articles/238)

---

