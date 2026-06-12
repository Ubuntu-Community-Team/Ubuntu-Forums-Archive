---
title: "Linux using a docking station / port replicator."
date: 2010-10-04
forum: Hardware
---

### Post by joshuamcdo on 2010-10-04
I have a dell M6500, and have searched far and wide for information to make XORG function correctly with the docking station.
  I can get the 2 monitors to work by using NVIDIAS config utility for Xorg and adding "do nothing" to the power saving scheme for "Lid".  
But what I can't do, is make it so that I can dock and undock on the fly.  If I remove it from the dock and place it back, it's behavior with the displays is un-predictable.

Does anyone have any information out there?  Am I missing some super app or widget that takes over for X and does all this changing on the fly?

 Thanks,
 Joshua McDowell

---

### Post by joshuamcdo on 2010-10-05
Bump...  Anyone?

---

### Post by utnubuuser on 2010-10-05
I think you'd need for the dock to be in your fstab file.

For my ThinkPad, the dock/base shows up in fstab as a floppy disk.

Copy of my fstab> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7e1a84aa-9589-4c03-9da7-28c1e583332f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6cb7792f-70b1-44d9-9298-b26d96999ea2 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=b4e88adc-61f1-4717-9d3b-2515d3306ca3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


maybe try to get some information about the dock with > sudo hwinfo

---

### Post by joshuamcdo on 2010-10-06
Thats interesting, and it gives me a place to look around a little.  But the first question I would ask is. Is there a floppy drive attached to that dock in any way?

 Thanks,
 Joshua McDowell

---

