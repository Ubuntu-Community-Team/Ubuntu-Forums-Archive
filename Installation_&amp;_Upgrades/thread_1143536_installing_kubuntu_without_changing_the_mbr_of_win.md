---
title: "installing kubuntu without changing the mbr of windows"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by brijraj22 on 2009-04-30
i want to install kubuntu on my portable hdd ( 80 gb) but i want to run kubuntu only when i specifically boot from my portable hdd and do not want any changes in the boot record of windows vista.is that possible?
i have done this on ubuntu but the installation of kubuntu is slightly different and i cant find the option in the kubuntu installer

---

### Post by Zorael on 2009-04-30
Supposedly when you get to the final screen before it starts creating filesystems and copying files, you can hit Advanced and choose not to install the bootloader (grub). I'd make a backup of the mbr first though; I think you can do that with testdisk from the repos.

---

### Post by SuperSonic4 on 2009-04-30
Or you can choose where to install it to. Making a backup as said in post 2 will be a good safety net

I think the easiest method would be to plug in the external drive and unplug the internal drive and so grub will have to install to the external and not see windows.

Once done and shutdown you can plug in the windows drive and should be able to pick whichever via the bios.

---

