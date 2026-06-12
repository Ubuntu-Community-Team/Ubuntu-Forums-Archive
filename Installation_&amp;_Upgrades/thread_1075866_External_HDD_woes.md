---
title: "External HDD woes"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by dimothy10 on 2009-02-20
So I tried installing 8.10 to an external USB hard disk today so I could have vista on my laptop and then ubuntu when i needed to.  Everything seem to go well, installer could see the USB drive and seemed happy to partition it etc.

Am now recieving GRUB Error 21.  Have fiddled with the boot settings in BIOS but to no avail.  Was wondering therefore if I could install GRUB to my internal MBR that currently has Vista on it, use it to chainload Vista and also load my USB install of Ubuntu when it was connected (or at least add the menu option).  

My trouble is I can't work out how to install GRUB to my Vista MBR?  Am i missing something really simple here?

All help greatly appreciated

---

### Post by dimothy10 on 2009-02-20
ah, so I managed to get it to boot from the external hdd drive.  My trouble is now that i always have to have it connected even to load vista which is a touch cumbersome.  Is there anyway that people know of to get round this perhaps?  From what i understand so far GRUB is looking for all the data it needs, menu.lst, on my External HDD.  Is there anyway perhaps to move this data to my vista partition?

---

### Post by ajgreeny on 2009-02-20
One way, if you haven't really used the ubuntu yet and have no files to retain, is to reinstall but with a separate /boot partition on your internal hard disk.  That will contain everything that is on the /boot folder in your current ubuntu install, and should mean that you will get grub appear, even when the usb disk is not connected, thus allowing you to boot to windows.

Alternatively, install grub on the usb drive, restore the windows MBR, and then set the bios to boot first to the usb, second to the internal hard drive.  Now when the usb is not connected the system will look for the usb but then go to the windows MBR.  All should boot according to your wishes!  Good luck.

---

### Post by dimothy10 on 2009-02-20
Fantastic suggestion about boot order!!  Really could not see the wood for the trees at the moment!  Thanks again

---

