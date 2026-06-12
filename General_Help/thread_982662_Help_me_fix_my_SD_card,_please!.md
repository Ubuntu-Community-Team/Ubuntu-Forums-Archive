---
title: "Help me fix my SD card, please!"
date: 2008-11-14
forum: General Help
---

### Post by ArmchairArmada on 2008-11-14
I have a little usb sd card pen-drive type thing and somehow while trying to copy some files over to it everything became completely messed up.  File names were scrambled, the size of the drive was wrong, etc.  When I tried to reformat, it in hopes that I could at least get it back to a usable state, it stopped working completely.  I don't think it has any file system on it anymore, so when I try to plug it into my usb port Ubuntu doesn't mount it.  Because it no longer mounts I have no idea how to be able to reformat it to a FAT16 file system.  It worked perfectly before, so I don't think the card is dead.

Before anyone asks, I don't have a digital camera to try reformatting it in.

---

### Post by ArmchairArmada on 2008-11-15
I tried some different search terms than I had been previously using and finally found some helpful information about [installing Ubuntu on a pen]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") drive, which contained information on how to format a usb drive the way I needed to format mine.

---

### Post by cariboo on 2008-11-15
If you have gparted installed you can format the sd card as it was origionally. Go to System-->Administration-Partition Editor-->Gparted-->Device, and select your device, it should be highlighted like in the attached screenshot. Right-click on the device and select Format-->Fat16

Jim

---

