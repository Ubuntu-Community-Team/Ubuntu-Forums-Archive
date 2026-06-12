---
title: "Dual boot ubuntu windows xp not working"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Shwick2 on 2009-04-27
First I installed windows xp sp3, defragged it, then I installed Ubuntu 9.04.  For its partition I selected "choose between operating system at startup" and i gave ubuntu half the drive, 125GB.  

Now when I start my computer windows starts and asks me to do a disk check.  I don't get to select which OS i boot from.

---

### Post by Shwick2 on 2009-04-27
Nevermind fixed it.

I have two 250GB hard drives.  I installed windows/ubuntu on the hard drive which was given first boot priority in the bios.  However, Grub was loaded onto the second hard drive.

Since the first hard drive had boot priority it looked there for the boot loader so it found windows and loaded that.

I switched the boot priority of the hard drives in the bios and now grub loads and I can select which OS I boot from.

TY myself :P

---

