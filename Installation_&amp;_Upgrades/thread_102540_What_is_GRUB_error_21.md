---
title: "What is GRUB error 21?"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by niño bomba on 2005-12-12
Hello. After unsuccesfully trying to install Ubuntu on one machine I decided I'd try on a second one. (unwise as it may seem)
Installation seemed to go fine until restart. GRUB starts loading but becomes halted and displays a Error 21 message. What could this mean? How can I fix it?
I'm really interested in learning Linux but have yet failed in my efforts to get Ubuntu installed (or perhaps it is installed just not running yet). 
Needless to say I want to keep my old windows and make dual boot systems, while I learn.

---

### Post by Topsiho on 2005-12-12
I advise you to find a solution to this problem using Google (Grub error 21). I found there several solutions, some of which with changing your BIOS- settings, but you better see for yourself which is the correct answer.

Success,

Topsiho

---

### Post by az on 2005-12-12
Bios detects your hardware and configures it and then boots your OS.

Linux detects harddrives on your IDE bus (or Serial or raid or whatever) in a different way than your bios does.  Since Grub uses the information given to it by the BIOS, it can sometimes not think things are in the same place or in the same order.

This is what error 21 is all about -  Grub cannot figure out where linux put the files.  Grub is partly on your boot sector and partly on another part of the disk.

You need to either play around with your bios settings or help grub out in finding the drives.  There is a setting to swap out device order in grub.  I am not at home and cannot give you more detail about this right now, sorry.

I think it is the grub device map. (regurgitation of information, there)

---

### Post by niño bomba on 2005-12-16
Yay! Google helped out... so i tweaked the primary master and primary slave also secondary master and secondary slave in the CMOS BIOS utility that you get into before anything loads.... I made them automatic and LBA (without knowing what that means) and now....
I GOT A DUAL BOOT MACHINE!! yay!
:) :) :eek: :) 
:D I finally got into ubuntu and enjoyed the sassy look...Now to solve the getting online problem.....
but i guess that is a new thread.. so thanks and bye!

---

