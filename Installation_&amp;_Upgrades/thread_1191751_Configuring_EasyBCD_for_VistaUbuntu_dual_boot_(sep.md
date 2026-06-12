---
title: "Configuring EasyBCD for Vista/Ubuntu dual boot (separate drives)"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by egernant on 2009-06-19
I have 2 drives on my PC and Vista has been installed on the first for over a year while the second has been empty.  The second drive (which is slaved) now has Ubuntu on it (I unplugged the other drive to make sure it installed to the second drive).  I need Vista to boot automatically unless Ubuntu is chosen at the boot menu.  Using EasyBCD, I created an entry for Ubuntu and restarted.  The menu came up as it should on reboot, and Vista was chosen automatically as it should have been. I tried again and chose Ubuntu and it gave me a Disk Boot Failure, Insert System Disk and Press Enter error.  I figure I am just configuring Ubuntu wrong in EasyBCD since Ubuntu boots fine when it is the only drive plugged in.

In EasyBCD 1.7.2, I simply went to Add/Remove Entries and under Add an Entry, clicked the Linux tab.  I made the type Grub, the Name Ubuntu (NeoSmart Linux was default...) and the drive "Drive 1 Partition 0 (Linux Native - 143 GB)" as opposed to the Swap partition and of course drive 0 which is Vista.

What am I doing wrong?

EDIT:  Without EasyBCD, Windows (from the Master drive) boots automatically.  I cannot figure out a way to even get ubuntu booted.  GRUB does not come up.  And I tried to change the boot sequence to boot from the ubuntu drive, but the boot sequence menu on this comp sucks and only had "hard disk" as an option... I wonder why that is?

EDIT2:  More Details:  This is what pops up when I hit the Ubuntu entry on startup.

BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
loading new partition
Bootsector from C.H. Hochstatter
Cannot load from harddisk.

plz help, is the bootloader in the wrong place for Ubuntu? How can I ensure during an install that the boot information is in the right place?
Insert Systemdisk and press any key.

---

### Post by dstew on 2009-06-19
Probably, your Linux boot sector does not have any boot loader in it. You can install grub there (same as installing grub to MBR, except you use setup **(hd1,0)** instead of setup (hd1)). You can also install a boot loader to the Linux boot sector using the BCD setup program. The boot loader is called **neogrub**. See [this How-To]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5").

---

### Post by Mark Phelps on 2009-06-19
Don't want to discourage you from posting here, but for EasyBCD questions, you would do better to contact the NeoSmart forums.  They deal with these issues all the time and have some How-to's you can download and read.

---

