---
title: "Dual Boot HD and SD card"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Rich2112 on 2009-07-06
I suspect that someone has addressed this, but I've searched the forum and couldn't get any of the solutions in other threads to solve my issue. I am new to linux and Ubuntu and have tried to set up a dual boot system on my new netbook (running XP) using an SD card for Ubuntu.
 
I have installed Jaunty on the SD card and in my bios set this to be my 1st hard disk drive and my hd as the second drive. Doing this successfully boots to the sd card. Upon startup, I go into grub and if I choose the Ubuntu option, it boots smoothly.
 
The issue is if I try to boot from my HD, I get an error "Error 13: Invalid or unsupported executable format"
 
Going into a terminal and running fdisk -l, I see that my hard drive and boot partition is listed as /dev/sda1 (and my SD card, which boots fine is /dev/sdb1 if that matters).
 
Upon installation, I have two windows options when I boot up in grub, and each lists the steps:
 
>>rootnoverify (hd0,X)
>>savedefault
>>chainloader +1
 
The two options set X as 0 and 2 respectively and both yield the error 13.
 
I can't figure out the right settings to access the HD to boot windows and hope this is an easy question for someone to answer (since I am new and will occassionally still use Windows, although maybe someday...:). Thanks.

---

### Post by Rich2112 on 2009-07-06
Rather than editing my earlier post, I am posting the solution in case others may stumble upon this question in their search as I have pieced together the solution from other posts...
 
You can set up an SD card and HD as I listed above with the SD card as the first drive in the bios.  You then need to edit the section of menu.lst in the /boot/grub directory to change the code that was defaulted (clear which was /dev/sda1 from the comments).
 
For other total newbies open a terminal window:
change the directory:$ cd /boot/grub
edit the file: $ sudo gedit menu.lst
 
original section:
>>rootnoverify (hd0,0)
>>savedefault
>>chainloader +1
 
change above to:
>>rootnoverify (hd1,0)
>>map (hd1) (hd0)
>>map (hd0) (hd1)
>> chainloader +1
 
Hope this may be useful to someone else trying to run a similar configuration...

---

