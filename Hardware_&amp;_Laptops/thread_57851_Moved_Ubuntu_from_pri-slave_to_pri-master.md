---
title: "Moved Ubuntu from pri-slave to pri-master"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by musther on 2005-08-18
I have a box based on a really horrible old HP machine, the only way I could get it to accept both the HDD and CD-ROM was to have the CD as primary master and the HD as primary slave.  I installed ubuntu in this config, and now it's time to take out the CD drive, the machine won't let me leave the HD as slave, so I've changed it to primary master.  I've updated /boot/grub/menu.lst (I've changed all the hdb references to hda) and now ubuntu boots, kind of.  It gets stuck when trying to access hdb3, which of course is now hda3 (this is the /home partition).  Is there some way to change any reference to hdb to hda in order to solve my problem?

Cheers

---

### Post by MrCheese on 2005-08-18
[QUOTE=musther]I have a box based on a really horrible old HP machine, the only way I could get it to accept both the HDD and CD-ROM was to have the CD as primary master and the HD as primary slave.  I installed ubuntu in this config, and now it's time to take out the CD drive, the machine won't let me leave the HD as slave, so I've changed it to primary master.  I've updated /boot/grub/menu.lst (I've changed all the hdb references to hda) and now ubuntu boots, kind of.  It gets stuck when trying to access hdb3, which of course is now hda3 (this is the /home partition).  Is there some way to change any reference to hdb to hda in order to solve my problem?

Cheers[/QUOTE]

You need to edit /etc/fstab (as sudo root user). Temprarily reinstall the cd & set the master/slave jumpers back to how it was installed. You'll need to change the grub config back to hdb for the hdd of course...... 

When you have booted the system, edit /etc/fstab & change the entries for /dev/hdb(x) to /dev/hda(x) whenre (x) is the partition nos.

Return the system to your intended config, reconfigure grub & off you go!

---

