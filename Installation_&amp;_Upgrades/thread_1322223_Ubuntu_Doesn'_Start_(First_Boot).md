---
title: "Ubuntu Doesn' Start (First Boot)"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by not me on 2009-11-10
Hi.

I've just finished installing Ubuntu 9.1 Desktop 386.

When the instalation finishes, the CD ejects, I take it out, close the tray, and the notebook reboots.

When the BIOS presentation ends, I get this

---------------------------------------------------

GRUB Loading
Error: no such device: 83d79e62-2763-473f-9ef7-51ee8b2d49df

----------------------------------------------------

for one half of a second and then my screen goes blank

Just to be certain, I installed it twice, with the same result

This notebook use to have 6, hours ago, Fedora 11 and worked fine

The hardware info is Compaq EVO N610c
1.5 GB
160 GB IDE Disk

Please guide me to detect the failure.

Thanks

---

### Post by jimbo99 on 2009-11-10
Grub is the boot loader.  It is pointing to a HDD that doesn't exist (at least as far as that reference goes).  Did you do an upgrade?  Did you change the boot sequence of your HDD in bios?

---

### Post by mr_steve on 2009-11-10
This is Bug #[lpbug]403408[/lpbug] which is apparently not getting fixed in any big hurry. There's some pointers in that bug report for getting it to work. Also see this thread for more help: [http://ubuntuforums.org/showthread.php?t=1321712&goto=newpost](http://ubuntuforums.org/showthread.php?t=1321712&goto=newpost)

---

