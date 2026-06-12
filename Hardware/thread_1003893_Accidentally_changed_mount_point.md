---
title: "Accidentally changed mount point"
date: 2008-12-06
forum: Hardware
---

### Post by addiebk on 2008-12-06
Due to personal stupidity, I have accidentally changed the mount point for my flash drive.  Now whenever I try to mount the drive, I get the following error:

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I did, in fact, add a / to the mount point, which explains why it wouldn't mount.  Now I don't know how to edit the mount point back to the original, as I can't mount the device to access its settings.

Please help!

---

### Post by addiebk on 2008-12-09
Anybody?  I tried asking my friends, most of whom know quite a bit about Linux, but none of them had any ideas.

---

### Post by capn_hector on 2008-12-09
how did you change the mount point, the other thing you might try is the mount points are stored in /etc/fstab so i would also look there to see if the changes are there then all you do is either remove the line or change it so its correct.

---

### Post by addiebk on 2008-12-12
I changed the mount point by right clicking on the flash drive and hitting 'properties'.  There was a tab that had a bit labeled 'change mount point' or 'mount point' or something similar to that.  I wound up typing things into the box, and now it's not working.

I'm not quite de-n00b-ified yet; I can't seem to find (or edit, but that tends to require finding) /etc/fstab.  I tried a cd, but that doesn't work.

---

### Post by addiebk on 2008-12-12
Also, I feel kind of silly.  I threw in a gedit /etc/fstab and this was the file output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5d493286-f316-4446-ae64-f70d1c4e6edb /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=1f40403a-a198-412e-9f36-8b8083ec5a44 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

I don't think I see my flash drive in there.  I'm not so hot at reading these, but UUID maybe has something to do with my university's network (UUID=University of Utah ID), and /dev/scd0 is the cd rom?  the usbfs, I'm not sure... maybe that's it?

I'm a bit lost here.

---

### Post by addiebk on 2008-12-18
bump

---

