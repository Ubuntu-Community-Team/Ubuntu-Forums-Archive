---
title: "Can not boot Windows in my laptop? GRUB error."
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by joe.turion64x2 on 2007-07-09
Hello everybody.

Yesterday I experienced a very weird problem, during the installation of my new MP3's drivers Windows XP hung and I hard rebooted (I had no choice). Afterwards I was unable to boot it again: it would not pass from the loading logo and upon displaying a BSOD rebooted itself. The BSOD appeared for a second only (or less), not enough time to read it, but after capturing the process with my camera, and analyzing the resulting video found it was an error message related to NTFS: the partition was somewhat corrupt. To mount it in Linux it was necessary to use the force option, with which I could backup all the files.

Then I got an idea: if the filesystem is screwed, lets create a new one and copy back the files. So I deleted the partition with Gparted, created another NTFS one (same size) and copied back ALL the files I had already backed up (of course I backed up the entire content). Then I expected that the next time I tried to boot Windows it would do it, however I was wrong because after selecting the proper option in GRUB it displays an error message "Unknown filesystem". It is worth noticing that the error message is not from Windows itself (at least I don't see any resemblance) and since it also shows some of the parameters in my menu.lst file I presume it is GRUB.

What could have run wrong? Is there a further step I still have to accomplish to get away with my cheat.

It is a new NTFS partition (in fact Linux mounts it flawlessly), same size, all the files are back there. The only detail there is that the label has changed (it was "ACER" and now it is empty, I did not figure out how to change it again). GRUB was not even touched.

Thanks.
Joe.

---

### Post by Espreon on 2007-07-09
You should post this in the General Help, not here. Try reinstalling Windows. Do ya really need Windows? If you need it just to run a few Windows exclusive apps try Wine+Wine-Doors ([http://www.winehq.org](http://www.winehq.org)) (After installing Wine turn to my Wine-Doors tutorial at : [http://ubuntuforums.org/showthread.php?t=490382&highlight=wine+made+easy+wine-doors](http://ubuntuforums.org/showthread.php?t=490382&highlight=wine+made+easy+wine-doors) ) Also try CrossOver: [http://www.codeweavers.com](http://www.codeweavers.com). For Gaming try Cedega (only use this if games on Wine fails): [http://www.transgaming.com/products/cedega/](http://www.transgaming.com/products/cedega/) (For a free version made from CVS google Cedega CVS [I believe this is totally legal])

---

### Post by joe.turion64x2 on 2007-07-09
> **Espreon said:**
> You should post this in the General Help, not here. Try reinstalling Windows. Do ya really need Windows? If you need it just to run a few Windows exclusive apps try Wine+Wine-Doors ([http://www.winehq.org](http://www.winehq.org)) (After installing Wine turn to my Wine-Doors tutorial at : [http://ubuntuforums.org/showthread.php?t=490382&highlight=wine+made+easy+wine-doors](http://ubuntuforums.org/showthread.php?t=490382&highlight=wine+made+easy+wine-doors) ) Also try CrossOver: [http://www.codeweavers.com](http://www.codeweavers.com). For Gaming try Cedega (only use this if games on Wine fails): [http://www.transgaming.com/products/cedega/](http://www.transgaming.com/products/cedega/) (For a free version made from CVS google Cedega CVS [I believe this is totally legal])
You are right, it is posted in the General help section now.

I guess I can go through without Windows, however some components of my laptop will be useless in such case. I really want to fix it, mainly for compatibility reasons.

Joe.

---

