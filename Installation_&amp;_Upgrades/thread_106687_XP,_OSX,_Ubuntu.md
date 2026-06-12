---
title: "XP, OSX, Ubuntu"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by brewno on 2005-12-21
Hello!
I'm having a problem with GRUB to recognize my OSX partition. I want a triple boot, but GRUB only recognizes Windows and Ubuntu.
On Grub, my XP is on (hd0,0) and my Ubuntu is on  (hd0,6) with root=/dev/sda7.
My OSX is on dev/sda6, so what should I add on menu.lst?
Any help would be much appreciated. :D

---

### Post by jasmuz on 2005-12-21
/dev/sda6 is an SCSI emulated drive (probably SATA)....GRUB mostly fails to recognize and boot such partitions.

Maybe this can help you out a bit...
[http://www.ubuntuforums.org/showthread.php?t=30233]("http://www.ubuntuforums.org/showthread.php?t=30233")

---

### Post by brewno on 2005-12-21
can I change grub to lilo? will it be better for me?

---

### Post by brewno on 2005-12-21
:confused:

---

### Post by Lofticus on 2005-12-22
AFAIK you can forget lilo, and so that's a no (:

---

