---
title: "win7 + ubuntu9.10 parition problem"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by SafirXP on 2009-11-03
Tried installing Ubuntu right after Windows 7. It can't find my paritions. Shows the whole drive as empty. I've included a screenshot to show the way my drive is partitioned. I've installed XP, Vista & older Ubuntu versions without any issues.

Since it didn't work I tried the Wubi install method. Even that failed, while loading Ubuntu it said "no root partition found." Really very disappointed. Was looking forward to this version because my XFI sound card would be fully supported.

Any suggestions? All I can think of is backing up all the data in my HDD, redo Win7 again and then try Ubuntu. Would that fix the problem? Cause I'm wondering if the last 419GB partition is the root of the issue here.

My config:
Athlon64 X2 3800
MSI NForce 4 SLI
2GB RAM
GeForce 7900GT
XFI sound card
500GB Samsung HDD
300GB Seagate HDD

---

### Post by OriginalName on 2009-11-03
Windows can't read Ext3 / 4 filesystems so shows it as unallocated.

---

### Post by sliketymo on 2009-11-03
Heres something that may help :

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by SafirXP on 2009-11-03
Yeah, I know that. Posted the screen shot to show how the HDD is partitioned. Currently backing up all my files. So I'll start from an empty HDD, do Win7 again and then give Ubuntu another try.

Was scared of trying some partition tweaking and risk taking because all my important files were in that 400GB+ partition. Copying all my stuff to dad's PC, he's got plenty of space! :D Hoping all this effort will help somehow. And also will try that "sudo apt-get remove dmraid" commands that I've found in the forum.

Thanks for the link to that guide, I'll give that a try if my method doesn't work.

---

### Post by OriginalName on 2009-11-03
Sorry... thought maybe that was a bit too obvious! 

That howto looks like what you need to know... If reinstalling partition with Ubuntu livecd... (windows 7 will need a primary partition to install on)... install windows... install ubuntu... should work :D

---

### Post by Mark Phelps on 2009-11-03
Wish you luck -- but it's most probably NOT going to work.

The combination of GRUB2 (in 9.10) and the new Windows 7 partitioning scheme seems to be more than Ubuntu can handle.

LOTS of posts from folks with the same problem -- not seen any solutions, though.

---

### Post by SafirXP on 2009-11-04
WRONG, it worked! :D

After cleaning up my HDD I installed Win7 & then installed Ubuntu after booting from the LiveCD. Partitioned it from the Ubuntu installer and didn't touch the boot loader settings. Everything worked perfectly.

Got sound for the first time in linux! Although I'm not getting any sound from the center speakers, I miss Foobar & its upmixing plugin! There's no equaliser in the RhythmnBox player. Gonna give Amarok, Audacious, Listen & the ALSA player a try.

Anyways, thanks for all the advice. I'm so happy & excited about running Ubuntu properly! :) Making two of my friends install it too!

---

### Post by jlowtek on 2009-11-04
I was able to dual boot win7 and ubuntu as well by following the instructions from this link.

[http://www.gacosta.net/Linux-Apache-MySQL-PHP/dual-boot-windows-7-and-ubuntu-904.html](http://www.gacosta.net/Linux-Apache-MySQL-PHP/dual-boot-windows-7-and-ubuntu-904.html)

---

