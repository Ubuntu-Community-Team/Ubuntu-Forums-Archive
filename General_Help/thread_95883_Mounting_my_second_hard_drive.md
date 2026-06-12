---
title: "Mounting my second hard drive"
date: 2005-11-27
forum: General Help
---

### Post by Christopherius on 2005-11-27
I have a dual boot of Windows XP and Ubuntu linux. I have them both on hda1 and all of my music is on my second hard drive. My question is how do i get access to my music under ubuntu?

I did sudo fdisk -l in the terminal and got this:

Disk /dev/hda: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2104    16900348+   7  HPFS/NTFS
/dev/hda2            2105        3268     9349830   83  Linux
/dev/hda3            3269        3322      433755    5  Extended
/dev/hda5            3269        3322      433723+  82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10248370176 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1244     9992425+  54  OnTrackDM6

hdb1 should be the second hard drive, right? I dont recognize the system type though. What should I do next? Thanks for any help.

---

### Post by aysiu on 2005-11-27
I don't recognize this system type either (OnTrackDM6).
Have you tried just mounting it anyway?
This guide and a little trial and error may help you out...
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

