---
title: "uninstall ubuntu"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by uninstall on 2009-08-10
i tried to find a thread on this, but they're all for dual boot systems. i switched from vista to ubuntu only, but now i want to go back. simply booting from the vista recovery dvd's doesn't work. my XP cd wont install either. it seems they dont find a partition? i'm no computer expert...

if there is a thread for this and i didn't find it, i apologize in advance. thanks!

---

### Post by faizan_comsian on 2009-08-10
i think u put window 2000 cd in and boot through it....and after going into instalation...just delete this ubuntu partition and after that just come out...and the put vista in...i think it will boot ur vista now

---

### Post by uninstall on 2009-08-11
thanks for the info, but it did not work. going into 2000 setup i get:
 
INACCESSABLE_BOOT_DEVICE
 
then no more install. it still seems to boot into ubuntu without trouble.

---

### Post by Sef on 2009-08-11
> simply booting from the vista recovery dvd's doesn't work.

> thanks for the info, but it did not work. going into 2000 setup i get:
 
INACCESSABLE_BOOT_DEVICE
 
then no more install. it still seems to boot into ubuntu without trouble. 	

Windows is looking for the Windows boot device: NTLOADER.   Because it is a recovery disk, it needs to find NTLOADER or NTKERNEL.    Since it cannot, it gives you that message.

---

### Post by uninstall on 2009-08-11
> **Sef said:**
> Windows is looking for the Windows boot device: NTLOADER. Because it is a recovery disk, it needs to find NTLOADER or NTKERNEL. Since it cannot, it gives you that message.
 
so why does the XP installation (not recovery) disk not work?
 
from command prompt "sudo fdisk -l" it appears there is no FAT or NTFS partition, only Linux? how do i get set up?

---

### Post by phillw on 2009-08-11
Sadly, XP has problems't doing a clean install - i recall this from many a time of grief with it.

My simple work round was to put on 98SE ....  If you don't have a copy to hand, then this tutorial should work for you.

[http://lifehacker.com/157578/geek-to-live--how-to-format-your-hard-drive-and-install-windows-xp-from-scratch](http://lifehacker.com/157578/geek-to-live--how-to-format-your-hard-drive-and-install-windows-xp-from-scratch)

regards,

Phill.

P.S. (you could always put XP on as well ubunt)u .. so you can still play with ubuntu. the instructions for doing that can be found here ....

[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

Choose the XP after Linux method.

---

### Post by raymondh on 2009-08-11
> **uninstall said:**
> i tried to find a thread on this, but they're all for dual boot systems. i switched from vista to ubuntu only, but now i want to go back. simply booting from the vista recovery dvd's doesn't work. my XP cd wont install either. it seems they dont find a partition? i'm no computer expert...

if there is a thread for this and i didn't find it, i apologize in advance. thanks!

Quick thoughts/questions....

1.  When you went solely Ubuntu, did you erase (as well) the recovery partition for Vista?
2.  The XP CD ... is it a recovery CD or an original installation disc?
3.  Can you load/boot the ubuntu liveCD, access gparted and post back a screenshot of what it (gparted) outputs?

---

### Post by uninstall on 2009-08-11
> **raymondhenson said:**
> Quick thoughts/questions....
 
1. When you went solely Ubuntu, did you erase (as well) the recovery partition for Vista??
yes
 
> **raymondhenson said:**
> 2. The XP CD ... is it a recovery CD or an original installation disc??
XP original installation cd
 
> **raymondhenson said:**
> 3. Can you load/boot the ubuntu liveCD, access gparted and post back a screenshot of what it (gparted) outputs?
 
i put in the ubuntu CD and reinstalled manually setting up a fat32 partition, then tried windows, but this did not work either.
 
i have screenshot (below)

---

### Post by uninstall on 2009-08-11
attached

---

