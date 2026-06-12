---
title: "[SOLVED] cannot boot"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by fboxall on 2008-12-14
I have windows XP-2 Pro.  I downloaded Ubuntu 8.10 file (hash checked OK), burned CD (disc checked OK), and booted from it.  Everything looked OK.  Then I installed it and that procedure seemed to go OK.  But I can't boot it.  Maybe I screwed up the partition.  I have only one hard drive and it was all winXP.  I used manual partition, set the swap to 2048 KB, and used the rest for Ubuntu which I set as logical, extension 3, and entered mount point as /.  I think there was a choice of "beginning" or "end" which I did not understand, so that might be the problem.
	Windows continues to work OK.  I don't get a screen for choosing Windows or Ubuntu.  I have visited BIOS and do not learn anything there.  My computer acts as if Ubuntu is not there.  Can anyone help me out?

---

### Post by Partyboi2 on 2008-12-14
You could try restoring grub and see what happens. You can do this by booting the ubuntu live cd and following [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by caljohnsmith on 2008-12-14
How about booting your Live CD, download the attached "boot_info6.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info6.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will greatly clarify your setup and what your problem might be.

---

### Post by fboxall on 2008-12-15
I solved the problem by re-installing.  I think that the first install didn't work because I failed to check the format option in the partition dialog.  In any case, I believe I am ok now.  Thanks for your help.

---

