---
title: "Help - Installed Ubuntu but now can't start Windows!"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by tranceybowler on 2005-01-28
Ok, after considerable confusion over partitioning last night I managed to install Ubuntu, which works reasonably well. However now the GRUB boot menu only shows Ubuntu, no Windows. I'm pretty sure windows is still on there as I partitioned the drive in Partitionmagic in Windows before running the Ubuntu installer.

I may have made a mistake the first time I ran the ubuntu installer as I selected the new partition to be formatted but chose to make it bootable. The installer crashed after about 89%, saying something to do with a Kernel file. I then restarted and ran the installer again, this time selecting the empty partition for formatting but not selecting the bootable option. This time it installed relatively well, a couple of fail messages popped up but essentially it worked.

I now have ubuntu but can't run windows XP. Where do I start? Any assistance greatly appreciated! If you need any clarification just ask.

Many Thanks!
Matt

---

### Post by rudi on 2005-01-28
could you post your partitioning scheme? 
 
 If you have choosen Grub as a bootloader:
  ```
If windows is on the first partition edit the file: /boot/grub/menu.lst and add this entry:

title		   Bill's OS
root			(hd0,0)
makeactive
chainloader	 +1
``` 
 That should start Windows from the first partition (change to hd0,1 for the second etc.)

---

