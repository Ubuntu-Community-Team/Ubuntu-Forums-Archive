---
title: "[SOLVED] Syntax to make Windows boot.ini load Linux (Ubuntu)"
date: 2008-07-16
forum: General Help
---

### Post by rated727 on 2008-07-16
The short version of the question is as follows:
.  Does anyone know where I can find specific information to phrase a load option in Windows boot.ini to load Ubuntu or other Linux distribution?  I am sure that it will be quite different from GRUB or LILO loader syntax (which are themselves not too similar).

The long version:
Recently, I have been having more fun than I ever thought possible (at least with my pants on).

A harddrive failure spoiled my fully updated and operational installations of Windows XP Pro AND Ubuntu.  I installed a small (160gB) hard drive and started the wonderful project of reinstalling, configuring, and updating the two operating systems (who needs sleep?!).

Here are a few things that I learned by sheer determination and refusal to accept defeat. I think of myself as being smarter than simple machines and therefore, I should be smart enough to determine the problem and fix it, and usually I do.

A few of the lessons that I have learned:
a.)  If you reinstall Windows XP you have to manually reload the Microsoft Validation tool in order to do updates (a few updates will install, but after that, they will download, but NONE will install).
b.)  I found GRUB error 18 which is connected in some way to Large Block Addressing (LBA mode) of the hard drive.  My BIOS and WinXP have no trouble in accessing the full drive, but GRUB seems to trip.
c.)  Linux order of storage devices sometimes has NOTHING in common with the BIOS order.  My integrated RAID controller with stripped 6.1gB hard drives showed in the Linux boot order before the 160gB drive.  Yet, the BIOS order puts the 160gB on IDE channel 1, CD R/W and DVD R/W drives on IDE channel 2, and the RAID on IDE channels 3 & 4, and my 2 gB IDE pen drive at the last position.
d.)  (this was one of the most fun) If GRUB bombs (error 18 ) your boot sector (and Windows) are basically trashed. (or are they?)
e.)  It is possible to recover Windows XP but it is not for the faint of heart, nor for those with command line fears. (If there is truely enough interested, I'll detail that ugly procedure in a seperate post)

---

### Post by bodhi.zazen on 2008-07-16
They are but a short search away ...

[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

[http://ubuntuforums.org/showthread.php?t=80508](http://ubuntuforums.org/showthread.php?t=80508)

---

### Post by rated727 on 2008-07-16
The answer that you get is very often a function of the way you ask the question.  My searches didn't yield any useful results.
Thanks for the links. jl

---

