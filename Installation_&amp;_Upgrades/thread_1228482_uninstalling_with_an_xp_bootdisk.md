---
title: "uninstalling with an xp bootdisk"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by tega2919 on 2009-07-31
Well, to be frank, my ubuntu is now FUBAR.
How can I boot from the windows XP disk to format the drive? I only have one partition.

I put in the disk to start up from it but it automatically goes and loads up ubuntu. How do I get it to boot from the disk instead? Is there a button I can press to get to a menu to choose what to boot up or what?

I really am an uber-noob at ubuntu.

---

### Post by sonu 1807 on 2009-08-01
Press F2,F3 (see the message below when you boot your computer before the grub starts ...there should be something like "Press F2 to enter setup". It will take you to bios setting. Go to boot menu in the BIOS setting and change the boot order so that your CD drive is at the top. There should be instructions written at the bottom regarding how to change the boot order like by pressing F5 or F6 to move up/below the highlighted matter...the save and exit (most probably by pressing F10 button)

BTW...whats your problem with ubuntu..In my view to go back to XP (an outdated and much less powerful OS) is a great step backwards. If you post your problems with ubuntu in detail and in proper manner you will get prompt replies to solve those issues.I converted to ubuntu last September and I am not using XP/Vista in spite of having legal copies of both. But any way, its your choice...but I would suggest u to be a bit patient otherwise you will miss the great computing experience that ubuntu offers

---

### Post by tega2919 on 2009-08-01
Oh, no, I'm not reinstalling XP, I would never do that after switching to this.

I just want to format the drive with the disk. That's all I need the disk for.

I can't install XP anyways, I got this computer second-hand with a pirated version of it. The main reason I switched is because I wanted to run the computer legally, and I couldn't install from the XP disk I had.

So I burned Jaunty onto a disk, after formatting XP and I've been using this ever since.

I am NOT going back to XP.

---

### Post by Bucky Ball on 2009-08-01
Do you have a working computer you can download the Gparted ISO? That will wipe the drive for you so you can start again (will delete NTFS partitions or whatever). If you have EXT3 Linux partition on your drive (as I suspect) the windows disk won't get you far. It will report 'unrecognised file type' and do nothing. It has no idea what EXT3 parititions are and consequently is of no help to you at all.

The reason you need to boot from the gparted disk is that the partition you are attempting to manipulate or delete has to be UNMOUNTED before you can do anything.

(Actually, re-reading your post, you could boot from the Jaunty disk and run 'live' from the disk. That will allow you to unmount all your partitions and wipe as you are running from the disk, not from a drive (which would need to be mounted for you to run a hard-drive install of the OS, if you get me). You will find Gparted in:

System->Admin->Partition Editor

---

### Post by tega2919 on 2009-08-01
when I restart the computer and go into the setup menu (it says "press esc to go into setup menu, so I do that), a bunch of choices come up which are:

Ubuntu 9.04 Kernel 2.6.28-14 (generic)
Ubuntu 9.04 Kernel 2.6.28-14 (recovery mode)
Ubuntu 9.04 Kernel 2.6.28-13
Ubuntu 9.04 Kernel 2.6.28-13 (recovery mode)
Ubuntu 9.04 Kernel 2.6.28-11
Ubuntu 9.04 Kernel 2.6.28-11 (recovery mode
Ubuntu 9.04 Kernel memtest


wat

---

### Post by sonu 1807 on 2009-08-01
Sorry mate that my tiny brain and pathetic comprehension ability led me to completely misunderstood your post ...there are two options

1. You can reinstall by booting from the ubuntu CD (just as you press power button of your computer you have to press something like F2/F3 or F9/F10 to change boot order depending on your computer)...look for it when u power on your computer and before grub starts to load at the bottom of the screen..it stays there only for a second...
the ubuntu setup will give you option of using entire disk....

2. If u dont want to reinstall...you can use gparted to format your harddrive...if any unformatted space is there....the software is avaliable from Application --> Add/Remove...in the box type gparted....the click apply change it will be installed

---

### Post by Bucky Ball on 2009-08-01
Okay, right at post you need to get into the BIOS to change your boot order. You are not getting there, you are getting to the grub boot menu list.

A screen pops up when you switch the machine on giving you the details of the machine and checking things. THEN is when you should see something like 'Hit delete to enter BIOS/setup' or however it is worded. You need to change the boot device in there.

f1, f2, delete and escape ... I have seen them all used. Just as soon as you switch the computer on, start pressing one of them is the best bet. You will see something on that first screen different. It should be saying 'Entering BIOS/setup' rather than 'Hit Delete ...' or whatever.

---

### Post by tega2919 on 2009-08-01
alright because my computer is a piece of crap it shows a blue intel screen before the grub screen, with no prompts whatsoever, so I just button mashed f1, f2, esc, del, etc. and I eventually got into my bios.
I'm good from here.
That's all I needed to do?!

Sorry to trouble you two with my stupidity.

---

### Post by Bucky Ball on 2009-08-01
That's what the forums are for. :)

Good luck with it all and welcome.

---

