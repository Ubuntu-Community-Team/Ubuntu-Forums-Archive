---
title: "Mounting SATA partition on boot"
date: 2004-12-06
forum: Hardware &amp; Laptops
---

### Post by sparx on 2004-12-06
I just installed ubuntu about a week ago and have been using it exclusively, but I still created a partition to share data between it and my existing XP install.

This partition is formatted as fat32, obviously so they can both read it, and is on my secondary drive which is SATA. I was mounting the shared partition (sda4) at /mnt/shared manually every time I started up, and decided to add it to fstab. That isn't working. 

Now when I boot up it says something along the lines of "/dev/sda4 does not exist." I'm sure it's in a log file somewhere, but I'm not sure where, and that's pretty much the extent of the message anyway. If I complete logging in, mounting of the drive is no problem at all. 

Any ideas? I'm thinking the easiest, unless I'm missing something obvious, would be to add the mount command to a startup file somewhere, any suggestions as to where? (I'm still figuring out where everything is under linux.. quite the noob)

Thanks for your time

---

### Post by sparx on 2004-12-06
Fixed it.. had to put an entry for the sata module (sata_sil) in my /etc/modules. All is good now.  :D

---

