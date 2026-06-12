---
title: "big boot failure after xp"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Ampi on 2009-11-06
I had a ubuntu 9.10/windows 7 dualboot and then I formatted windows 7 to a fat32 partition in the ubuntu partition editor. 
Then I tried to install XP on that partition, for that I had to change my SATA mode to IDE mode (even though I have a SATA). 
During the XP preparation for the install  choosing my windows partition I got suddely an error, disk failure. The computer got stuck and I rebooted, now it reads nothing. 
WHen I restart it only shows failures (there is nothing graphical) and when I put in my old 9.04 Ubuntu live CD it also reads nothing but errors (again not graphical). 

I thought I could make a clean install (and forget Windows for the rest of my life) because I have my home and data and ubuntu on a different partition, but if I cant even read live CDs or get a terminal or somethign then how am I suppose to do so?? 

If someone can help me I would be very very happy!

P.S. In the BIOS I changed the IDE mode back to SATA.


EDIT:  I rebooted again, now the live CD is read, but when I "Try Ubuntu without installing" it stops and reboots again. WHen I reboot without the live CD it just says that the disk is not bootable, insert bootable something, floppy or so...

---

### Post by Ampi on 2009-11-06
thank god :)

I found an old gparted live CD, and it was read correctly. Thanks to that I could open a terminal and install grub again (with sudo grub, root (hd0,4) etc.) so no Ubuntu restarted and is checking my filesystem as we speak. I do hope all goes well.

Still a question, I have two options on what to do now:
1. Forget about Windows and adding that primary Windows partition to Ubuntu (question would be how), or
2. Still install XP on the primary partition. But then what do I do with my SATA harddisk if XP doesnt read it? And make sure it doesn't ruin my boot again?

Sorry, should I make a new thread?

---

### Post by dandnsmith on 2009-11-06
Are you convinced enough of the superiorities of using the HDD in SATA mode rather than as IDE - my understanding is that it doesn't give much extra in practice?

The XP install problem is, to some extent, that you'd need SATA drivers to feed to the XP install process in order to succeed.

Another thing which may be confounding you (if you got the machine with Windows7 installed is that the HDD setup is different in the way it handles booting and the partition table (there is help on this if you google for it), and trying to get XP may itself be ruining the existing setup.

I think I'd go for a complete redo of the HDD, creating it from scratch, whatever you decide you want to end up with.

---

### Post by Ampi on 2009-11-07
Okay, I haven't used Windows in 4 years, all the times I tried to add it to my comp it has just given me problems. I do have an extra very old laptop running Ubuntu which I dont use. I'll just put XP on there, it doesnt have any data I need to keep so failure is an option. 
Who need Windows anyway!

My question now is how to add the extra primary partition to my Ubuntu. 
I have the typical primary empty partition meant for Windows and an extended partition for Ubuntu (root, swap), home and data. 

1. Could I add the primary partition to Ubuntu in an easy way?

2. Could I move my HOME-files to my DATA partition and then do a clean install of Karmic on a primary partition and keep DATA and HOME on a extended partition?
 
3. Is there any way of doing a quicker backup instead of copying to an external HDD? In that case, a clean install would be more a consideration :)

---

### Post by dandnsmith on 2009-11-08
1. Its not the easiest thing to add primary and extended together, unless they happen to be adjacent (then you can remove the unwanted, and resize to fill the space - but you'll need more than that to add the ubuntu as you'll have to resize it after resizing the extended partition). After that you may find you have trouble with partition UUIDs (get Ubuntu from a live CD to tell you about them), and grub may have problems (depends where its files are, and which version it is).

2. As stated, it sounds feasible (but, as always, the devil is in the detail).

3. You could backup up to a 'data' file - if you have enough space where it won't get messed with. The external medium is safer.

---

### Post by Ampi on 2009-11-22
I already made a backup of my important data. Maybe a clean install is also a good idea when making your own LiveCD/DVD from your own current system..
Then next time I won't need to install all the extra programs...

---

