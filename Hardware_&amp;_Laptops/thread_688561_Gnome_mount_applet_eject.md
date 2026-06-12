---
title: "Gnome mount applet eject"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by snafle on 2008-02-05
I'm using gnome mounting applets, and have noticed that when I try to eject the CD drive by clicking on the CD icon and selecting eject, it doesn't work- it unmounts the drive, then tells me I don't have permission to eject. And yet, when I press the eject button on my laptop it just blats the disc out, no problem.

My fstab has my group in it:
/dev/scd0       /media/cdrom0   udf,iso9660 users,noauto,exec 0       0

I can't eject the drive with "eject cdrom0" but I can with sudo- this leads me to suspect I've borked something with permissions or groups. I have no idea what though, heh.

---

### Post by snafle on 2008-02-09
I'd managed to remove myself from the cdrom group. Readded it and all's well.

---

