---
title: "[SOLVED] CDRom went missing after upgrade"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by frogbots on 2008-02-10
I did a fresh install of 7.04 and then allowed the update manager upgrade to 7.10.  The upgrade worked fine and all systems worked except the CDROM.  If kernal 2.6.20-16 is used the CDROM works fine.  If kernal 2.6.22-14 is used the CDROM does not work, as well as it does not show up in the device manager.  Reviewed similar posts and tried the various recommendations.  I have changed the fstab line to different values for the CD.  The  Computer in file browser shows the CD with the title of CD-ROM 1.  If I try and mount it I receive this "mount: special device /dev/hdb does not exist"  When I changed the  FSTAB line  "/dev/hdb      /media/cdrom0   udf,iso9660 user,noauto,exec    0       0" to  "/dev/cdrom      /media/cdrom0   udf,iso9660 user,noauto,exec    0       0" Kernal 2.6.20-16 the computer in file browser shows the CD with the title of CD ROM.  Attached is copes of the device manager for both the 2.6.20-16 Kernal and the 2.6.22-14 Kernal, and the FDISK listing.  I noticed that the 2.6.22-14 kernal has the drives changed from IDE to SCSI.  Is this the problem?  How do I fix it?

Thank you for your time
Duane

---

### Post by f1ff134 on 2008-02-10
hey if you could read my post

[http://ubuntuforums.org/showthread.php?t=693220](http://ubuntuforums.org/showthread.php?t=693220)

and tell me if that sounds like your prob? if so and if i solve it i will let you know if you do the same

---

### Post by frogbots on 2008-02-18
We can mark this one as solved.  After looking at many other posts, I found this information on a post about busybox errors.  I followed the directions and the CDrom is working fine.

I hope that it works for you!

Duane

************
edit /etc/initramfs-tools/modules, and adding this lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

**************

Credit for this 7.40 slow boot fix goes to "Fabio Povoledo". He had it posted in a forum somewhere and I was days finding the solution. I saw a lot of people trying to fix the slow boot issue. I assume none of these people could do a fresh 7.10 install.

---

