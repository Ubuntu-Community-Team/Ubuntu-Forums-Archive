---
title: "Dual Booting With Grub on Intel Matrix Raid"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by Ruu1989 on 2009-09-27
I have recently been trying to install Windows 7 and Karmic Koala side-by-side on my desktop.  My HDD layout is as follows...

SATA RAID0 #1 -> (80gb + 80gb)
SATA RAID0 #2 -> (320 + 500gb)

Both on the matrix raid, found in /dev/mapper/isw*

There is also a random 160gb IDE drive aswell.  Dont ask :P


I first installed Win7 onto the larger driveset, which went pleasently well as per usual.

Proceeded to boot and begin installation off the x64 9.10 alternative CD image, which immediately recognised that there was a RAID present and found all the drives, including the NTFS windows partitions.  I partitioned, deciding it would be smart to leave /boot on the 160gb drive to ease potential confusion later.  When it got the GRUB part of the installation, I got the large red screen saying grub installation had failed.  It then installed LILO by itsself, and the system restarted, and booted!

Linux was booting, fantastic!  LILO, unfortunately didnt want to talk to windows, so I began installing grub (which I have done once or twice before successfully, but never on a RAID).  Got it installed to the point where it would boot Karmic, but still refused to show a menu.lst when I gave it one, although it did recognise, but ignored the windows partition with a grub.cfg.

Its too late to fix the system as it was now, as I gave up and installed Windows onto a 4disk raid of all the sata drives for now, but I was wondering if there is any known way of forcing grub to talk to win7 when it is installed onto a matrix Raid 0!

Apologies for the life story, I'm just trying to give as much information as possible! :D

~Ruu

---

