---
title: "new install on a blank hard drive"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by devo1974 on 2006-01-27
hi guys, well I have looked everywhere to someone having this problem with no luck.........so here goes.........

I inherited a laptop from work, an old pent 3 IBM thinkpad, before I got it they deleted EVERYTHING from the hard drive ( for security reasons i guess, so fair enough) so I made an iso of ubuntu 5.10 (tested this on win XP machine and the CD seems OK as is it unpacks OK) then i fire up laptop using an old win 98 startup disk to give the laptop CDROM support and have also tried "sbootmgr" software to boot to the cd rom drive first. when i boot the CD i get an error message in sbootmgr saying "bad disk" but as i say i have tried the disk on win XP machine and it seems to read it OK as it starts to unpack the disk. is there any other software i need on the laptop to allow it to install unbuntu as at present all that is on the C: drive is of course command.com .......... whew...... TIA for any (not too technical) suggestions......... very (very very!!!) new to linux as in this is my one and only attempt so far............. as you can probably guess, this is to be a spare mahine simply top learn a little about linux.............cheers
DEVO

---

### Post by stalefries on 2006-01-27
Um, from what I gather it seems that your Ubuntu CD has been burned improperly, or is corrupt. By the way, did you set your BIOS to boot from the CD? There's a million reasons why this may have gone wrong. It may be good if you explained what sbootmgr is and what it does, as it seems that may also be significant.

---

### Post by devo1974 on 2006-01-27
hiya sbootmgr is short for smart boot manager, it enter te bios to reorder the startup so I can boot he laptop from the CDROM, i initially thought the disk was corrupt as well, but as i said, using my winXP mahine it seems to be reading it OK, but as you point out there could be a million reasons for this........:-( thanks for the help though.

DEVO

---

### Post by qwazert on 2006-01-27
Did you burn the .iso disk image or merely copy the .iso file to a CD?

This is how I pulled off my install:
Burnt an .iso image of the INSTALL disk.
Using a Win98SE bootdisk from Bootdisk.com I deleted and re-created the partition on a 4.3Gb HD
Remove bootdisk and Boot with INSTALL CD.
Followed instructions, choosing the highlighted default in most cases, including letting the INSTALL program re-partition the HD as required.
Done.

There were issues with video-resolution and printer, but they were resolved with the help of this site.

---

### Post by Ocxic on 2006-01-27
get rid of the boot manager, that prolly what is couseing the problems, ubuntu will install the grub boot loader anyway. so try and get rid of that boot manager.

---

### Post by devo1974 on 2006-01-28
thanks for that, the issue i have i guess is that the HDD is completly blank, I tried loading up a win 98 startup disk to at least try and give the computer CDROM support, then loaded the linux disk without luck, so tried the boot manager to get the computer to boot to the CDROM drive, I cant get my way into the bios to change the boot order to CDROM first :-( ... will try your idea though.......not having any luck with anything else...... so thanks

---

### Post by Nightwind on 2006-01-28
[QUOTE=devo1974]thanks for that, the issue i have i guess is that the HDD is completly blank, I tried loading up a win 98 startup disk to at least try and give the computer CDROM support, then loaded the linux disk without luck, so tried the boot manager to get the computer to boot to the CDROM drive, I cant get my way into the bios to change the boot order to CDROM first :-( ... will try your idea though.......not having any luck with anything else...... so thanks[/QUOTE]
Please explain why you cannot get to the BIOS to change the boot manager? What happens when you attempt to go to the BIOS?
What model is the IBM?
Depending on your model  go here:[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-50273](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-50273) 
for instructions on IBM BIOS: note be sure that this applies to your model, if not search IBM site for the relevant information.

---

### Post by devo1974 on 2006-01-28
hey thanks for that, i tried F2 instead and it worked, so slowly making progress... but it still wont recognise the disk i made... so am starting to suspect maybe that is at fault :( it starts to unpack when i try it on my win XP machine, so i thought it was OK, mind you I made the disk on this machine as well, so maybe it only works on here because of that, dont know... will try a few more things to burn a disk that works........ thanks for the help though... small steps....:D :D

---

### Post by Nightwind on 2006-01-28
[QUOTE=devo1974]hey thanks for that, i tried F2 instead and it worked, so slowly making progress... but it still wont recognise the disk i made... so am starting to suspect maybe that is at fault :( it starts to unpack when i try it on my win XP machine, so i thought it was OK, mind you I made the disk on this machine as well, so maybe it only works on here because of that, dont know... will try a few more things to burn a disk that works........ thanks for the help though... small steps....:D :D[/QUOTE]
Glad that helped. As far as burning the ISO image, you should slow it down and burn it as slow as you can, that will prevent errors. Also I'd use the install ISO image instead of the live CD.

---

### Post by devo1974 on 2006-01-29
thanks for that :-)

---

