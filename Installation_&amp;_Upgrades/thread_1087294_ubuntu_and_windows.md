---
title: "ubuntu and windows"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by phillip1882 on 2009-03-04
now that  i got the internet up and running, i would like to try permanently installing ubuntu on my computer. however i'm a little concerned that i won't be able to get into windows if i do so. i don't play cd games much any more, but every now and then i enjoy doing so, and most games require windows. can i go ahead and run the installation, or should i hold off for some reason?

---

### Post by RedSingularity on 2009-03-04
Do the install but when you get to the formating part do the "auto" or "smart" format.  This will leave the windows partition alone.  Whatever you do dont format the entire drive by mistake!!

---

### Post by phillip1882 on 2009-03-04
i double clicked the install icon in ubuntu, but when i got to step 4, it looks like it's not detecting windows.
can i still install and get into windows, or what?

---

### Post by RedSingularity on 2009-03-04
No no no dont do that.  You will lose windows.  Is windows on the same HDD?  For some reason its not showing up.  Try manual and look for the windows NTFS file system.

---

### Post by lindsay7 on 2009-03-04
I had the same problem on one of my computers that I was installing a dual boot of Ubunto with vista already on the sysem.  What I did wrong was started the Ubuntu install and had the auto install for the partition look at the drive. I was not sure that I was doing this corrctly and I backed out of the installation.  When I went back in to do the install it would not see the windows partition on the drive. What I did was go into windows storage management in the control panel and look at the drive. It had been partially partitioned (if that makes sense). I exteneded the windows partition back to where it was (the full drive) and then started the unbuntu install again. This time it showed the windows system on the drive and suggested how it would set up the dual boot.  I choose to make the Ubuntu partition smaller that what was suggested. Ubuntu installed just fine and the dual boot works with no problem

One other suggestion for you.. when you get Ubuntu installed, install the Start-Up Manager from Synaptic. This way you can set up the default startup to be either Ubuntu or Windows when it starts by itself.

---

### Post by Sef on 2009-03-04
What windows are you running?

---

### Post by phillip1882 on 2009-03-04
i dont see windows as part of the partition under manual.
edit, i have windows xp.

---

### Post by lindsay7 on 2009-03-04
I think you should restart your computer and see if it starts with windows. If I does look at the partition with Computer management -Storage.

---

### Post by RedSingularity on 2009-03-04
/dev/sda1 is your windows install.  It looks like it is taking over the whole HDD.  Can you resize it under "edit partition"?  You need some free space for the Ext3 File system of Ubuntu.

---

### Post by phillip1882 on 2009-03-04
okay, i went back into windows just to make sre nothing was wrong, and got into windows fine. then i went back into ubuntu, tried running the install, and it partitioned correctly (44 gig for windows, 141 gig for ubuntu) but when i treid going to the next step it came up with an error of could not partition, and aborted the operation. so now what?

---

### Post by lindsay7 on 2009-03-04
I would go into windows and try to extend the windows partition to fill the whole disk and retry the Ubuntu install. Start the control panel, go to Administration Tools, Computer Management, storage, disk management, action, then you want to choose the disk drive, and extend the partion to the max allowed.

I the unbuntu install, once you get to a certain point (it gives you a warning) it starts to set up the partition. If you back out or it stops for some reason, those settings are going to remain.  I think what you are seeing is that when you first looked at doing the installtion the partioning was started and it left something on that drive to that effect. Now you are getting the error because of that. Extending the current windows partition should clean this up. You should be able to install Ubuntu after that.

The instructions that I gave you are for Vista. XP may be a little different.

---

### Post by phillip1882 on 2009-03-05
yeah it's just not working. i'm thinking of going ahead and formating my drive, installing ubuntu,and then installing windows. is this possible?
(read relatively easy?)

---

### Post by lindsay7 on 2009-03-05
I think it is best to install windows first if you do that,

---

### Post by RedSingularity on 2009-03-05
Yeah if you install windows first the grub menu will include windows as an OS at boot time.  So you will be able to select either windows or Ubuntu.

---

### Post by avtolle on 2009-03-05
Hazarding a guess, the Windows partition (covering the entire drive) is fragmented. So, first, defrag the drive (more than once if using the Windows defrag tool); then, use the installer to shrink (since you have XP; if you had Vista, and for anyone reading this having Vista, you should use the Windows tool to shrink the partition, not gparted on the Ubuntu install disk) the partition to create unallocated space onto which you may then install Ubuntu. Good luck.

---

