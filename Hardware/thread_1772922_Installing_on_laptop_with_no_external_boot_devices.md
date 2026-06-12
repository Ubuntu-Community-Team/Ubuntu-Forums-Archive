---
title: "Installing on laptop with no external boot devices"
date: 2011-06-01
forum: Hardware
---

### Post by JohnBN on 2011-06-01
Instructional post - medium difficulty.
 

Installing on an older notebook (or other system) with no external bootable device available:
[LIST]
[*]No CD/DVD drive
[*]No floppy
[*]No boot to USB capability
[*]No (usable) OS on HD
[/LIST]Solution went like this:[LIST=1]
[*]Remove target HD from notebook.*
[*]Disconnect HD from a desktop.**
[*]Use adapter cable set to install target drive in desktop.***
[*]Boot desktop to Ubuntu install CD or USB stick.
[*]Install to target HD.
[*]When install tells you to restart your system, shut it down (you may have to do it manually).
[*]Remove target HD from desktop and re-install in notebook.
[*]Boot notebook to HD.
[*]Enjoy Ubuntu.
[/LIST]* - Or other system; if a desktop, I'd suggest (at least temporarily) installing a CDROM drive instead.
** - Not necessary, but a little safer!
*** - A PATA (IDE) adapter cable set would work too. I used a USB adapter so there's no obvious reason this wouldn't work with another notebook or externally on a desktop - just make sure you install onto the right drive! 
*** - Also your opportunity to backup anything on the target drive as Ubuntu install will erase/format the drive.

---

### Post by helpad on 2011-06-01
years ago, I installed an OS over a network using plop boot manager that allows boot via USB.

---

