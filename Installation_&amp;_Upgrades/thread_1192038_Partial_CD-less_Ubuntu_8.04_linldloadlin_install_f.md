---
title: "Partial CD-less Ubuntu 8.04 linld/loadlin install failure."
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by emoafterall on 2009-06-19
My Toshiba Portege 3480ct can only through USB floppy emulation, since I do not posses a docking station with a CD drive.

I would take the hard drive out and put it in another computer via a 2.5"->3.5" adapter and install Ubuntu that way, but I'm too lazy to order one.

So I used what I had at hand. I found my old Windows 95 boot floppy that has some driver files for my ancient four speed Addonics PC Card CD-ROM, and I put linld on it. The process I use goes something like this (I use this for Windows installs sometimes):
-DOS boots off of an old Dell USB floppy
-Card Socket Services loads and looks for slots
-The PCMCIA bus is found
-CDROM driver loads and searches for a drive
-The Addonics drive is found and loaded as drive letter D:\
-The A:\ prompt comes up

Then I run linld.

However, when I entered "a:\linld image=d:\casper\vmlinuz" I got "image file not found." So I tried loadlin and got "cannot open image."

This was strange, so I tried to browse the Ubuntu CD. The directory command worked fine for the root folder, but when I tried to use the change directory command, it failed. I popped the disc out and put in my Windows XP disc, and changing directories worked fine. Same with Windows 2000, and a CD of random files. I even tried other copies of the Ubuntu disc, including one ordered from Canonical, but none of the Ubuntu discs worked.

I then tried using a FreeDOS disc, but I got the same results.

Would anyone know why only the Ubuntu discs are doing this?

---

### Post by emoafterall on 2009-06-19
Bump, because this is bugging me.

---

