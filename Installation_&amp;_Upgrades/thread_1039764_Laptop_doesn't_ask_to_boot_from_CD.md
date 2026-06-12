---
title: "Laptop doesn't ask to boot from CD"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by Hermanocleas on 2009-01-14
Hello,

I have a Windows based laptop currently running an older version (7.x) of Ubuntu (that I've forgotten the password for) and Windows XP. On startup I am presented with the "Grub" menu. I have a CD with the Ubuntu ISO burned onto it in the drive but it won't ask to boot from the CD on startup.

---

### Post by Tim Sharitt on 2009-01-14
Check your bios settings to make sure the CD drive is ahead of the hard disk in the boot order.
 If that checks out, there may be a problem with the cd or the iso image it was burned from. Check the MD5 sum of the image, if that checks out, try burning another cd at the lowest possible speed.

---

### Post by Hermanocleas on 2009-01-14
Here's what is going on. On a Gateway laptop upon startup I hit ESC to enter the boot menu, with the Ubuntu install disc in the drive I select CD-ROM/DVD-ROM drive and hit enter.

The Pc starts loading some stuff then gets to a line that says: 
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

(nothing more happens)

Please HELP!

d\

---

### Post by Hermanocleas on 2009-01-15
Here's what is going on. On a Gateway laptop upon startup I hit ESC to enter the boot menu, with the Ubuntu install disc in the drive I select CD-ROM/DVD-ROM drive and hit enter.

The Pc starts loading some stuff then gets to a line that says: 
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

(nothing more happens)

Please HELP!

---

