---
title: "install a liveusb system and keep the settings and programs installed"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by fjodork on 2009-04-17
Hi.

Iv been running the 9.04 liveusb for a few weeks now on my laptop with no reboot or nothing, and have made some changes/tweaks and installed some programs and stuff. Now i want to install the system to the hdd(hdd was formated wrong so files got lost until PhotoRec came to the rescue) but i want to keep all the programs i installed and the changes i made to the liveusb system while runnig it.

How can i do that? If i just run install, it will install a stock system, right? Can i somehow "move" the system from the liveusb to my hdd?

Or do i have to do it all over again? I know i can save some off the settings and changes if i cope the content off /home/ubuntu to my home dir once i got it installed, but that wont keep the programs and sure as hell not systemsettings.. 

Hope there is some simple way:P eheh

br fjodork

---

### Post by pastalavista on 2009-04-17
If you have an 8 gig or larger flash drive, you can install a distro to it like you would an internal drive... dual boot with bios control (make sure to put grub on the flash drive). But the Ubuntu probably wouldn't work right on any other PC. There may be a way to install all the drivers like the live CD but I couldn't tell you how, sorry.

edit: I see what you mean.. you want to save all the changes you made to the live usb system. You might try [Clonezilla]("http://clonezilla.org/")

---

### Post by tamas305 on 2009-04-17
If you have a large enough USB drive than you could perform a full install onto the drive. I recommend 5gb or larger. However windows will not be able to recognize the ext3 partition that Ubuntu makes. If you want a win partition as well, check post 3 on this [thread]("http://ubuntuforums.org/showthread.php?t=1116206")

-tamas

---

