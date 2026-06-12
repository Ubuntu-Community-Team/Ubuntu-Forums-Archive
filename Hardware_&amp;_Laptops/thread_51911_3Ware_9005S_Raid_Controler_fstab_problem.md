---
title: "3Ware 9005S Raid Controler fstab problem"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by Thearnold on 2005-07-25
I have 3ware 9005S 4port Raid Controller install in a Proliant 6000 for backup purposes, but when I put /dev/sda1       /sata           ext3    defaults,errors=remount-ro 1  1 in my fstab I get an error saying it can not mount the 
drive.  But, I can login to the desktop and go to root console and mount the drive with mount -t ext3 /dev/sda1 /sata and access the drive.  I think what the problem is the the 3ware drive is not load at the time the fstab tries to mount the 3ware volume.
How do you edit scripts or change the kernel to load 3ware drivers along with my compaq array controller?

Thanks 
-Glenn

---

