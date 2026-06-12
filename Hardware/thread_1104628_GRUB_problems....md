---
title: "GRUB problems..."
date: 2009-03-23
forum: Hardware
---

### Post by psxiiuk on 2009-03-23
Firstly I'd just like to say I'm a total noob so please go easy with me!

I installed Ubuntu on my laptop a few months ago with a 30gb partition but discovered it wouldn't work with my wireless card, so never used it. Lately my Vista partition has been getting full so I figured I'd delete Ubuntu to free up some space. I used the Vista partition manager to delete the two Linux partitions (a bad idea so I now hear), resized the Vista partition to fill the HDD and carried on using windows as normal. My laptop then decided to freeze so I turned it off 'manually' by holding the power button in. 

When I try to turn it back on again I get the message:

GRUB loading stage1.5.

GRUB loading, please wait...
Error 22
_

This happens almost immediately. The only options I get before this are to press ESC to change boot order (1.CD/2.HDD) or F10 to go into settings to mess with frivilous stuff like key beeps and system time. The Vista recovery disc has no effect, it simply whirrs a bit longer than usual and then comes up with the above screen.

I can get Ubuntu to run off the CD and have been trawling Linux forums for a solution I can run in a Terminal, but as Vista was not given a 'clean shutdown' it wont let me run any mounting/GRUB resetting/partition resizing, pretty much anything at all really on /dev/sda1 (the Vista partition). I'm pretty stumped as to where to turn now, any advice you guys can give will be seriously appreciated! :)

---

### Post by cariboo on 2009-03-23
If you don't have Ubuntu on your hard drive, you certainly don't need grub any more. If you have a Vista install cd just boot from it and at the menu select repair. If you don't have a Vista install CD go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the version you need.

Jim

---

### Post by psxiiuk on 2009-03-25
I've not got a Vista install CD thanks to Compaq being incredibly stingy with their laptops, and have tried the link to make a recovery CD to no effect (as mentioned in first post it just whirrs for longer but then comes up with the same error screen - its as if it doesn't recognise the disc). Thanks anyway Jim, any further help from anyone would be much appreciated!

---

