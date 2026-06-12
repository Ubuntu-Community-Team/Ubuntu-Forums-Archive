---
title: "Need some installation advice"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by denzilla on 2005-05-07
The place I work for wants me to setup about 4 computers in areas for kids to use. Unfortunately, this is a non-profit childrens organization and money is somewhat tight. Basically what I'm working with is 4 old emachines with these specs:

Cpu - 300/400 MHZ
Memory - 128 meg SDRAM
Hard Drive - 4.3 Gigabyte
Gfx - ATI integrated 3D Rage ( crap )

I'm at the 1st installation on one of these emachines and having a bitch of a time with the installation. At first Ubuntu moaned about a bootstrap error when coping files form the CD. I've had alot of trouble with the OEM emachine CD-rom units, so I swaped it with another CD-Rom and got past the problem. Now its moaning about running out of space during the installation. Is 4.3 gig not enough to install Ubuntu? I'm allowing it to erase the entire HDD and its using the default partitioning scheme.

Thanks in advance for any help given :)

---

### Post by crmanski on 2005-05-07
I would take a look at this how to...
Ubuntu Mini-RAM HOW
[http://www.ubuntuforums.org/showthread.php?t=8338](http://www.ubuntuforums.org/showthread.php?t=8338)

---

### Post by az on 2005-05-07
You need just under two gigs for the default installation.  I do not know why you are getting that error.

You may want to run a lighter window environment, as suggested by the mini-howto link.  XFCE4 or icewm will allow you to not grant access to certain aspects of the operating system easily.

You should also look into the package search site and find all that ubuntu has to offer kids.  Specifically, there is the debian-jr project - all of the packages are available to ubuntu.

---

### Post by denzilla on 2005-05-07
Well, after the 3rd attempt, Ubuntu decided to install. However, I might end up taking it off :( I'm not too sure how well the whole mount/unmount of drives is going to go over with the kids in our program. I'm not going to be around to explain it to them and telling a staff member and having them pass it on won't cut it either. I can already here the whining if they try to save something to floppy and take it out without unmounting. I could put up 50 foot banner in the living areas giving clear instructions and they still wouldn't get it. Nothing against Ubuntu, since its a Linux problem by nature, but the way Linux handles drives is somewhat retarded. For the life of me, and I can't understand why Linus would replace \ in command lines with / because it irritated him and then design drive handling so back asswards.

---

### Post by JLF65 on 2005-05-10
Linux didn't replace "\" with "/". DOS replaced "/" with "\" just to be different. Linux follows the "standard" like nearly every other OS out. Macs used to be even more contrary by using ":" but with OSX are now using the standard "/".

You might reconsider whether kids too young to understand the need to mount/dismount floppies should even be allowed to use floppies on the machines. What you usually find is that when kids are allowed to use floppies on computers, those computer quickly become infected with every virus known to man. At least that's not that much of a problem in linux, but if you switch to Windows to make floppy usage easier, it will be a MAJOR concern.

---

### Post by denzilla on 2005-05-10
Hmm....I read somewhere that Linux father Linus Torvalds (or whatever his name is) always hated the \ in windows and he changed it to / in Linux because it irritated him so much. Guess the source was fulla crap....

Regarding the floppy use. These aren't terribly young kids. They're between the ages of 10-17. I thought about just leaving the floppy drive unhooked, but then they and the staff will complain that the kids have no way to save their school projects so they can be transported. I could show them how to mount/unmount all day and someone would still screw it up. I should also add these are "troubled" youth, which means easily frustrated and destructive when something doesn't go their way.

---

