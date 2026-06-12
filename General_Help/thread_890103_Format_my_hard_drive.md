---
title: "Format my hard drive"
date: 2008-08-14
forum: General Help
---

### Post by loganbell on 2008-08-14
Hi :popcorn:
(Sorry about that :D)
I want to format my hard drive and start fresh, i have ubuntu 8.04 installed, but i've suped up my pc now and i have ubuntu on my laptop anyways, i want to completely format my hard disk drive back to factory settings, with nothing at all on it, no OS, no grub, nothing.

But being a windows user for the last 15 years of my life, i have no clue how to do this on ubuntu :( im not dual booting and dont intend to either, i want a pc with a hard drive that is completely empty (probably said that like 100x by now :lolflag: ) im then planning to boot a windows or mac OS from a cd or dvd. 

If you can help please do !
Thanks in advance :D

EDIT:
By boot from cd, i mean im going to boot the cd then install either a mac of windows OS

---

### Post by lisati on 2008-08-14
Gparted might be of some help here, you can use it to delete partitions. Be sure to do your planning carefully, and make sure you have a backup of important data (just in case your fingers slip and you accidentally delete the wrong thing)

edit: If you're replacing what's on the disk with, say, Ubuntu, you might be able to avoid the "delete partition" stage: Ubuntu has a "guided - use entire disk" option. The recovery DVD that came with my Toshiba laptop has a similar option.

---

### Post by loganbell on 2008-08-14
Cool, im  not good with partitions though... when i installed ubuntu i gave it full privalleges (bad spelling :P) so would i just erase all of the partitions? is there a piece of software i can burn to disc then boot at start up and erase everything? im a true linux n00by cake... i dont even use terminal to install \\:D/
i just use the add/remove software...

---

### Post by Too Late on 2008-08-14
I'm quite sure that you can delete all the partitions at the beginning of the Windows (or Mac) install. Deleting partitions won't actually delete all the data, but it doesn't matter unless you are selling your computer to someone else and you have some sensitive information on the disk.

For that reasons, there's a bootable CD, which will erase EVERYTHING on the disk: [http://www.dban.org/](http://www.dban.org/)

---

### Post by loganbell on 2008-08-14
Excellent :D
So i go find a windows or mac OS i like, boot the nuke thing, then isntall the OS :D that sounds great, after i run the nuke thing and get to the installing part, i may well do the default partition work aswell (im seriously worried about GRUB turning round and biting me in the ***...) if i burn that ISO to a usb drive, how do i get it to boot at start up? in my BIOS the options are: FLoppy group (i dont even have a floppy drive \\:D/ ) cd rom group , hard drive group (which would boot ubuntu currently) and network boot group. so i dont know how to boot fom a flash dive, can someone help me with that too ? thanks for all your great answers!

---

