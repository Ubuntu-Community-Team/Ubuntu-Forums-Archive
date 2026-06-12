---
title: "grub reloads grub"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by ran1wil on 2009-04-16
i had xp and added ubuntu to the second partition the first time.
and kept getting an error message when trying to boot xp
so i formated an reinstalled ubunto i left the xp partition untouched
now when i try to boot xp it flashes some message to fast to read and goes 
back to the grub boot menu..


help

---

### Post by Herman on 2009-04-16
It sounds like you have made a mistake somewhere along the line and accidentally installed GRUB to your Windows 'boot sector'.
You can install GRUB to the MBR of any hard disk or to the first sector, (boot sector) of a Linux partition, but you shouldn't install GRUB to the first sector (boot sector) of any Windows partition.

Nevermind, it's easy to if, just boot your Windows XP 'Installation CD', and run FIXBOOT, and that should fix your Windows boot sector for you.

Don't run 'FIXMBR though, because that will overwrite the GRUB boot code in your MBR, which will mean you'll only be able to boot Windows then, until you re-install GRUB.

I'm just guessing that's your problem, it might be something else, but from experience that's what usually causes GRUB to be returned every time you try to boot Windows from GRUB. :D

---

### Post by Herman on 2009-04-16
Here's a link to help you with the Windows Recovery Console in case you need it,  [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm").

Another way, in case you don't have a Windows XP 'Installation Disc', is to use TestDisc in Ubuntu.
```
sudo apt-get install testdisk
```
```
sudo testdisk
```
... and follow the steps detailed in this link: [12 NTFS Boot sector recovery]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery")

---

