---
title: "Installation failures, help needed"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by Werrf on 2009-06-20
Hi, newbie here, experienced with Windows but just starting out with Linux and about ready to smash things with installation failures.

After much hemming and hawing, I finally decided to go ahead and try installing Ubuntu as a dual-boot on my old Windows XP machine.  Running from the live CD went fine, so I went ahead and installed.  Installation was fine, all was hunky-dory until I tried to boot back into Windows, which resulted in a freeze on boot.  I tried reinstalling Windows, but no joy - now neither OS would boot.  So I went ahead and re-installed Ubuntu.  The problem was that I could not get Ubuntu to go back onto the same partition it was on before - it insisted on creating a new partition.

Okay, I can live with a little lost disk space from an extra partition, so I went ahead.  After instllation, I was informed of an update, which I ran.  Big mistake.  The update failed somehow, and was unable to boot into the OS.  It gave me the mouse cursor and a blank screen, nothing else.

So, foolishly, I decided to re-install instead of asking for help.  That's when all hell broke loose.  I have now ended up with ELEVEN partitions, and the last two attempts at installation failed due to insufficient disk space.  I can't delete any of the partitions with the partition manager, because each one tells me I must delete the partition with a higher number.  The one with the highest number doesn't give me the delete option at all.  Windows is still not working, Ubuntu is still not working, and I'm about ready to throw my computer through the walls.

Help?

Apologies if there are answers to this in other threads, I'm just too aggravated andtired to find anything right now - I will cheerfully delete this if you can point me in the right direction.

---

### Post by wanderingarticfox on 2009-06-20
I understand your frustration and wish I could help but it's late and I'm a noobie too you can see my post under yours. I did a similar thing when I installed 8.10 the first time and was able to use my OEM factory reinstall disc but I  really do not know if you have a set or not; try to enter BIOS to boot from CD and try those MS disc if you have them. I  'think' that might allow you to reformat the drive but I'm not positive because though Ubuntu sees windows windows is blind to Linux.

---

### Post by Werrf on 2009-06-20
> **wanderingarticfox said:**
> I understand your frustration and wish I could help but it's late and I'm a noobie too you can see my post under yours. I did a similar thing when I installed 8.10 the first time and was able to use my OEM factory reinstall disc but I  really do not know if you have a set or not; try to enter BIOS to boot from CD and try those MS disc if you have them. I  'think' that might allow you to reformat the drive but I'm not positive because though Ubuntu sees windows windows is blind to Linux.
Yeah, I tried reinstalling Windows using the onboard 'recovery' partition, but it failed - that's what screwed up my first installation.  I'm not quite ready to wipe the disk yet, not given up on my Windows installation (ever the optimist, me).  What I really need is a way to delete these breeding partitions that are popping up everywhere, but the 'manual' option on the installer lets me delete them but not install, while the 'guided' option lets me install but not delete.  I think the best option would be if one of the resident experts could explain how to get past the "no root file system" error I get on the manual partitioning - but we will see.

Still, thanks for letting me know I'm not alone :)

---

### Post by raymondh on 2009-06-21
Hello Werrf,

Some readings to get you familiar with what you are about to do.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)
[http://gparted.sourceforge.net/larry/resize/resizing.ht](http://gparted.sourceforge.net/larry/resize/resizing.ht)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)


Boot into the liveCD and TRY UBUNTU WITHOUT CHANGING YOUR SYSTEM.  That will give you a live session. Access gparted (system > administration > partition editor) to work on the partitions ... NOTE : Gparted will not work on a partition (or HD) that is mounted hence it needs to be unmounted. 

How do you want to proceed?  

-Do you want to delete partitions and then install? 
-Do you want to delete partitions and then create partitions so when you install, you can just choose manual and point the installation to the partition you created.

Read the above links and post back if you need clarifications.

Good luck.

---

