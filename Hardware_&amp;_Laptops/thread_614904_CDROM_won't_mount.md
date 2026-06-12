---
title: "CDROM won't mount"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by DanMan_7 on 2007-11-16
So i'm running Gutsy, Everything installed fine, My cdrom drive exists, though does not show a mount point.  No cd is detected by unbuntu.  Here's what Fstab command gives:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0d31364a-f522-47bd-bf0e-f5eb76c92408 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=98da9ed9-7830-4a98-aee7-bc0986cde2d2 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Any Ideas on how to get a cd working on my drive?  Thank You kindly, Dan

---

### Post by Battlemarz on 2007-11-16
First thing. Can you boot from a CD and is the drive seen by the BIOS? I had a similar problem while dualbooting Ubuntu 7.10 that carried over to windows. If your drive is seen by the BIOS the problem may be with GRUB. From what i have read and experienced GRUB does not like laptop CD/DVD drives and the fix that worked for me can be found [[COLOR="RoyalBlue"]here.[/COLOR]]("http://forum.notebookreview.com/showthread.php?t=186062")

---

### Post by DanMan_7 on 2007-11-18
I installed ubuntu off of a cd, so yes my bios see's my cdrom drive... I'm using an ECS motherboard and this is a desktop computer, not a laptop.  Ubuntu shows the cdrom drive, but gives an error saying its unable to detect any media.  When I check the mount point in the GUI, it doesn't show any.   

    Any suggestions?

---

### Post by polhen on 2007-11-23
hi !

i have similar problem with my cdrom and dvd ...
computer shows devices, but when i try to open them there is an error message
"unable to mount media...there is probably no media in the drive"
so...what i do now....how to mount the devices and make them work...

regards
pol

---

