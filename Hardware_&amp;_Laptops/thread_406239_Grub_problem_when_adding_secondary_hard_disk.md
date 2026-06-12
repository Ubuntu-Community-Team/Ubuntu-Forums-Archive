---
title: "Grub problem when adding secondary hard disk"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by fable on 2007-04-10
I have a P4 1.6GHz platform running fine with Ubuntu 6.06 and a single 20GB primary master hard drive.  LVM is enabled on this platform.  

Because I am running out of disk space, yesterday I installed an older 6GB hard drive into the platform as a primary slave disk.  The BIOS recognized both the primary master and slave disks.  In the BIOS, both hard disks are set as manual and LBA.  The slave hard disk has a single DOS partition but not formated.

When I boot the platform with the slave hard disk, I get a GRUB loading .... Error 25.  The platform will freeze at that point.

When I unplug the power to the slave hard disk and boot again, the platform will boot fine into Ubuntu as before.

Can any tell me what causes the Grub boot problem and how I can fix it?

:confused:

---

### Post by volksolwagen57 on 2007-04-11
double check that your original boot drive is set to master/w slave present or maybe just master
there should be a jumper map displayed on the top of your drive
if they are and everything is still jacked up then check the boot sequence
this is my boot sequence:
floppy
cd/dvd
primary ide (master hard drive)
secondary ide (slave)
make sure your master is the first hard drive that boots
hope this helps, good luck!

---

### Post by fable on 2007-04-11
Thanks for your suggestion.

I checked all as suggested and everything looks fine.  I am still getting the same Grub Error 25.

:confused:

---

### Post by stchman on 2007-04-11
> **fable said:**
> I have a P4 1.6GHz platform running fine with Ubuntu 6.06 and a single 20GB primary master hard drive.  LVM is enabled on this platform.  

Because I am running out of disk space, yesterday I installed an older 6GB hard drive into the platform as a primary slave disk.  The BIOS recognized both the primary master and slave disks.  In the BIOS, both hard disks are set as manual and LBA.  The slave hard disk has a single DOS partition but not formated.

When I boot the platform with the slave hard disk, I get a GRUB loading .... Error 25.  The platform will freeze at that point.

When I unplug the power to the slave hard disk and boot again, the platform will boot fine into Ubuntu as before.

Can any tell me what causes the Grub boot problem and how I can fix it?

:confused:

I gather that you are using this 6GB hard drive for extra storage?  If so the GRUB will not need to be modified.  You will need to modify the /etc/fstab file.  Just have GRUB boot Ubuntu from the 20G and then use the 6G for extra space.

---

### Post by fable on 2007-04-11
I found out the Grub Error 25 problem is caused by a bad hard disk.  It turns out that the 6GB hard disk is not working right.  I replaced it with another hard disk and now no more Grub Error 25.

I will modify the /etc/fstab file as suggested so that it is mounted every time I boot the PC.

:D

---

