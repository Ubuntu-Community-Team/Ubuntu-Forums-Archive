---
title: "Install 2nd Hard Drive"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by afderrick on 2009-01-25
Okay, so my current setup is this:

I have a 250GB hard drive with a separate partition for my home folder.

I just bought a new 640GB hard drive to house music/movies/etc that I don't want to keep on the main hard drive. 

I plugged everything in, when I turned the machine back on it would boot into Ubuntu but was unable to find my home folder anymore.  I logged into a failsafe terminal mode and when I got into the home folder sure enough it was empty.  Does anyone know any workarounds for this?  

Thanks!

---

### Post by Pumalite on 2009-01-25
Give us an idea of your partitions/drives; post:
```
sudo fdisk -lu

```

---

### Post by afderrick on 2009-01-25
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00073a80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   151492949    75746443+  83  Linux
/dev/sda2       620928315   625137344     2104515    5  Extended
/dev/sda3       151492950   620928314   234717682+  83  Linux
/dev/sda5       620928378   625137344     2104483+  82  Linux swap / Solaris

Partition table entries are not in disk order


Is what currently prints out.  I currently have the new hard drive unplugged.

---

### Post by Pumalite on 2009-01-25
If the second drive is connected; you have to review your wiring.
(it has to be formatted too)

---

### Post by afderrick on 2009-01-25
so once I get it formatted and in the correct order is there anything extra I need to do in order to have my home folder continue to show up?  It was weird that I could boot into ubuntu but not have my home folder show up.

---

