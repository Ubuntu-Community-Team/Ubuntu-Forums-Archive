---
title: "External USB drive not recognised??"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by dooper on 2007-11-22
Hello,
this is only slightly ubuntu related.


I have a toshiba a120-12u newish laptop. I recently bought a USB 2 external drive enclosure and fitted an old IDE drive in it with the intention of doing an ubuntu install on it.

The lappy has windows vista prem on it and when i plug the USB drive into the lappy,it sees the drive and loads the drivers. 

In windows device manager  USB section,you can see the drive and its actually named i.e western digital model no etc.

Howver if i flick over to MY COMPUTER,the drive isnt there. 

Also if i run drive management in admin tools,it isnt there either.
So then the bios sees it,the device manager sees it,but parts of the OS dont see it.

Now it may have something to do with the fact that the drive previously lived in a desktop machine and has a full install of pc linux PCLOS on it.

Does this use a different file system that perhaps vista cant see?

Can anyone suggest a way of accessing this drive and reformatting it to fat or ntfs and hopefully making it visible?

ta

---

### Post by tact on 2007-11-22
presumably the drive is formatted ext2 or ext3 - the native formats for linux - if it was in a linux box last.  (sorry I do not know what commands to give in windows....vista...etc... to identify which file system is on that disk)

there are free ext2/3 drivers for windows..  just google for them.  I recently did that and installed on my wife's XP box so she could access music etc on an external USB drive.

---

### Post by moulla on 2008-01-19
I had the same problem with an unformated/unrecognised format usb drive.  In my case I needed to go to the disk management section of the computer management panel to format it ... since vista didn't prompt or show the drive in "my computer" despite it being in the device manager.

the drive manager is in control panel>admin tool>computer management>drive manager

the direct command using (WIndows + r) is  mmc.exe compmgmt.msc /s

---

