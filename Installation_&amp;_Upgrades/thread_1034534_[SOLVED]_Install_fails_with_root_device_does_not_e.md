---
title: "[SOLVED] Install fails with root device does not exist"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by kwakr on 2009-01-08
[edited to fix title]

Background: I purchased a used PC with 3 hard drives.  Ubunto is the only OS.  I want to remove the 3rd drive and move it to another PC.  I could not find any ubuntu instructions on removing a hard drive only adding a hard drive.  I removed the secondary master (an empty drive) and left the primary master and primary slave drives.  Booting failed.  I assumed a fresh install (to 8.10) would reset the hardware configuration but it didn't.  The install is on the first partition of the primary master drive.  I also tried deleting that partition, creating a new one, and reinstalling to that partition.  Still cannot boot.

Problem: The BIOS correctly detects the 2 drives.  During ubuntu boot I get the message "Gave up waiting for root device", /dev/disk/by-uuid/8186... "does not exist".  I have verified the link given points to /dev/sda1 which is the first partition of the first drive.  So the drive does exist.  Gparted finds it just fine.  I used the script boot_info_script which reports "Boot sector type" for /dev/sda1 is "No boot loader".

What do I do next?

---

### Post by ljwobker on 2009-01-09
this sounds somewhat similar to a problem I was having where grub (the bootloader) wasn't getting installed and/or was pointing to the wrong place.  In my case, i was able to fix it by booting off a liveCD, and running grub from there.  At which point I used the grub "find" command to tell me which hard disk actually had the OS on it, and then I used the "root" and "setup" commands within grub to properly arrange the MBR -- and it booted.

This page is a good reference in addition to the main GRUB manual/docs themselves:
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html)

[GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html#Top") 

hope this helps...

---

### Post by caljohnsmith on 2009-01-09
How about trying this: when you get the Grub menu on start up, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add:
```
rootdelay=120
```
Press enter to save the change, and then "b" to boot. Please let me know if that makes any difference in Ubuntu's booting behavior.

---

### Post by kwakr on 2009-01-09
ljwobker, thanks for the useful links and tips on what to try. From that I learned that "find" wouldn't find stage1 unless I used grub called from the boot sequence.  Even then, specifying things correctly did not work.

caljohnsmith, I'm suprised, but that fixed it.  I guess the default timeout is too quick for my old hardware.

Thanks.

---

