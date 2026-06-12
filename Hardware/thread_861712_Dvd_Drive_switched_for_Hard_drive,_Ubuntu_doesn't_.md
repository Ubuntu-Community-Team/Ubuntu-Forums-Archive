---
title: "Dvd Drive switched for Hard drive, Ubuntu doesn't detect"
date: 2008-07-16
forum: Hardware
---

### Post by desktop668 on 2008-07-16
I recently installed Ubuntu onto an ancient Acer.  The MoBo supports three drives(not including floppy).  I had a DVD drive and a HD connected when I installed Ubuntu. After I installed Ubuntu, I tried to connect the second HD, but the PC tried to load XP (which was on the second HD.)  I then replaced the DVD drive with the second HD.  Ubuntu loads, but doesn't detect the second HD.
I've got the master/slaves jumped properly, so that isn't the problem.  I'm self-taught about pc's and my basic knowledge is lacking. In addition, this is my first real jump into Ubuntu.  How can I detect the second (XP) drive to move my files onto Ubuntu?

Thanks in advance - DESK

---

### Post by logos34 on 2008-07-17
> **desktop668 said:**
> After I installed Ubuntu, I tried to connect the second HD, but the PC tried to load XP (which was on the second HD.)  I then replaced the DVD drive with the second HD.  Ubuntu loads, but doesn't detect the second HD.  

Try reconnecting the dvd, then make sure the Bios **device** boot order is 1) cdrom/dvd 2) hard disk.  Then go into the **hard disk boot priority** submenu: set the ubuntu disk to first place if you can.  For some reason the minute you connected the second HDD it jumped ahead in the boot sequence.

As for ubuntu not seeing xp, that's because it wasn't connected during installation.

[Follow this]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") to add windows with read+write access (ntfs-config).

Add windows to menu.lst [this way]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

