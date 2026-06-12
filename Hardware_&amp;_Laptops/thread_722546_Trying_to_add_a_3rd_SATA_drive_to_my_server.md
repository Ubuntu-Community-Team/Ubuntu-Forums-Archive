---
title: "Trying to add a 3rd SATA drive to my server"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by hsweet on 2008-03-12
My current setup.

/sda1 is the (edu)buntu system, root, et. al.
/sdb1 mounted as /home. 
There is a 2nd unused partition on /sdb.

I tried to add a 3rd drive but can't log in on gnome... /home is not mounted correctly

The 3rd drive used to mount on /media/drbl but I took that out of fstab when I added the new /home drive.

So the ques is.. how do I get the system to add an /sdc1 drive and still recognize sdb1=/home?

thanks

---

### Post by Fire_Chief on 2008-03-12
You may want to check the SATA ports you are connecting the drives to on the Motherboard or PCI card. They are probably numbered. Be sure that the two existing drives are in the first two ports (in order) and that the system works. If so, then try adding the 3rd drive in the 3rd port and see if the system accepts it properly then.

You could also adjust your mount points to reflect the new drive layout.
-switch to a virtual console at the Gnome login screen by pressing ALT + F1
-login as root
-determine which drive contains /home (i.e. /dev/sdc) and mount it manually```
mount /dev/sdc1 /home
```
-edit the /etc/fstab file```
nano -w /etc/fstab
```
-adjust the line for /home to reflect the correct device and partition. Then save the file
-reboot to verify system is working well again
-add new drive by formatting the new disk, creating a mount point, and then mounting the partition.
:)

Cheers!

---

