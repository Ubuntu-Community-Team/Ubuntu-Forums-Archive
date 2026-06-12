---
title: "Treating SD card as permanent storage"
date: 2008-08-27
forum: Hardware
---

### Post by lotus49 on 2008-08-27
I have a laptop (Acer Aspire One) which has a small internal SSD.  It also has two card slots one of which is SDHC compliant and which is intended to be used as permanent storage, that is the card is expected to be inserted and then left there indefinitely.

I have an entry in /etc/fstab and my 16GB SDHC card is mounted on /home fine.

However, I end up with SD/MMC icons (two as it happens) on my desktop and in the file manager but since this is really permanent storage I do not want my laptop to treat this disk as removable.  However, I do want cards inserted into the other slot still to be treated as removable.

The left hand (semi-permanent) slot is always /dev/mmcblk0. EDIT This turns out not to be true.

Does anyone know of any way I can tell the OS not to treat this device as removable storage in the same way it does with the internal SSD?

---

### Post by sdennie on 2008-08-27
I don't have a way to try this but, one thing you could try would be to write a udev rule for the card and map it to something other than /dev/mmcblk0 (say, for instance, /dev/sdb).  In theory, I believe that will make gnome think the disk is just a regular disk and it doesn't do any special reporting when /dev/sd? partitions are mounted as /home.  Here is a guide for writing udev rules: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by lotus49 on 2008-08-27
Thanks for the suggestion.  I hadn't needed to write udev rules before and although the .rules files initially looked fairly complex, it wasn't that hard writing a rule which correctly identified a specific SD card and changed the device name.

However, I still ended up with the desktop icons just the same.  It looks like the OS knows the SD cards are removable by some other mechanism than the name.  I do think writing a udev rule is along the right lines so I need to delve into the documentation a bit more.  In  particular, I am wondering whether it is possible to change the "removable" attribute.

BTW, I seem to have one icon for each SD card device (mounted or not) and one for each mount point (only if mounted obviously).  So if I have /dev/mmcblk0p1 mounted on /media/disk, I will have two icons on my desktop.  This behaviour strikes me as somewhat broken anyway, even if I wanted a desktop icon.

---

