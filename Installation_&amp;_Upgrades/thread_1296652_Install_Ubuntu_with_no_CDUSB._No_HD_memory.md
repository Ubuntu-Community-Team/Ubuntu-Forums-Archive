---
title: "Install Ubuntu with no CD/USB. No HD memory"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by daniruiz93 on 2009-10-20
Mhm ok. I think im in the right section. Anyways, I installed Ubuntu cause i got tired of XP, and my computer was old so it didnt have USB boot and my CD drive broke. It was a mission to install linux and when i did i partitioned my HD in 2 sections. Windows and Ubuntu. I formatterd my ubuntu section to EXT3 and the other one to Linux/swap something like that. The problem is that ubuntu didnt install in those partitions and i only have 1014KB of memory and my HD is suposely corrupted. WTF! 
So i need a way to run the live disk without USB/ CD and i cant copy or paste anything in the partitions cause like i said, they are corrupted. 
I just want to have a decent computer, my XP had viruses and it was HELL to install ubuntu without knowing there was PLoP.
Help? 
Sometimes i think i am just an unlucky person ; __ ;

---

### Post by dominiquec on 2009-10-20
How did you partition your hard disk in the first place?

---

### Post by daniruiz93 on 2009-10-20
Gpart.
When i ran the live disk.
looked pretty simple. but for some reason everything went all wrong.
It could be so much easier if i had a working CD drive, but No. and i cant afford replacement cause its a laptop.

---

### Post by dominiquec on 2009-10-20
How did you run the live disk without a CD-ROM drive?

---

### Post by KhanTG on 2009-10-20
Sounds like you tried to install Ubuntu while you were running it IN Windows?  Runing gparted in that environment, on your machine while using it to run your primary OS (being Windows).  You will have to get a CDROM that works and install it that way; provided that you didn't turn your HD into a paperweight.
  Another option could be to install it in another machine (using your intended target HDD), and just transplant the HDD... there are generally no issues using that method (in my experience.. and, btw, I'm not any kind of expert on Linux)

---

### Post by oldfred on 2009-10-20
If it is that old of a computer you still have a floppy drive?

I have not tried it but supergrub supposedly will create a grub boot disk that they you can use to load the USB drive.

[http://www.supergrubdisk.org/wiki/USB_Boot](http://www.supergrubdisk.org/wiki/USB_Boot)
[http://www.supergrubdisk.org/w/index.php5?title=SuperGrubDisk](http://www.supergrubdisk.org/w/index.php5?title=SuperGrubDisk)

---

