---
title: "A few problems stemming from upgrading to 8.10"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by PWill21 on 2009-03-05
Being a novice linux user, I'll do my best to recount what happened.

I dual-boot 8.04 alongside Windows XP, and was looking to upgrade from 8.04 to 8.10. After using the LiveCD for a couple days I was satisfied and decided to install from the disk. The install went fine, but I wanted to completely replace the 8.04 partition with the newly installed 8.10. 

After some research about deleting/resizing partitions with GParted, I eventually came across a guide [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading") on how to upgrade. My thinking that this would "upgrade" 8.04 instead of installing 8.10 alongside it, so I deleted the new partition and left 8.04 intact.

Following the steps in the guide, Step 5 is where everything went downhill and I started to become completely lost. I was getting an error after checking for updates with Update Manager, and googling that error brought me to a possible solution posted here [http://siking.wordpress.com/2009/02/18/launchpadnet-ppa-changes/]("http://siking.wordpress.com/2009/02/18/launchpadnet-ppa-changes/"). From there it's a whirlwind. I used that info, which seemed to counter the error, but a new update check gave me a different error (I apologize for not remembering, but it was some sort of "fetch" error. Well, I tried, but it's just over my head.

After a restart (which I wish I hadn't done b/c I can't post the errors), no GRUB at boot. I'm totally lost now. I've spent the last couple hours backing up docs and such from the 8.04 partition, and all I want to do now is reinstall 8.10 alongside WinXP. Here's a screenshot of the current partitions.

I have no idea where to (re)begin now. I do not have access to either 8.04 or XP anymore, just the LiveCD. I'm looking to get XP and GRUB back with a fresh install of 8.10. Any suggestions? Sorry if this was long winded, but hopefully the info is useful.

---

### Post by PWill21 on 2009-03-05
I forgot to mention, if it helps, that the partitions are sda1/WinXP; sda5/8.04; and the unallocated partition is where 8.10 previously sat.

---

### Post by skillllllz on 2009-03-06
Backup all your important documents from sda5 and then use GParted to completely remove sda5, sda6, and sda2. Be careful not to remove sda1. Once you are finished, you should only have sda1 and the rest should be unallocated space. Next, properly shutdown and restart the computer, once again booting using the LiveCD. Begin the Ubuntu installation and when you get to the part about hard drive space/partitions, be sure to choose "guided - use unallocated space". Ubuntu will detect the Windows partion and create a grub entry for it automatically.

If you do not understand, or do not see exactly what I have outlined, then do not change anything or go further. Come back here first and explain what you are seeing; I will do my best to guide you.

---

### Post by PWill21 on 2009-03-06
Thank you for the reply skilllz. I'm running into a problem right off the bat in trying to delete those partitions. The right-click options are grayed out, and I can't find another way to delete them. 

Ok, I unmounted the drives, sda5 was the only one that was able to Delete. However, when I tried to delete, I received the error "Please unmount any logical partitions having a number higher than 5". Yet I still cannot delete sda6 or sda2.

---

### Post by skillllllz on 2009-03-06
Sometimes GParted (annoyingly) mounts partitions automatically. If you right click on a partition from withing GParted, you should be able to unmount it, then delete it. Repeat that for each partition, one-by-one, start with sda6, then do sda5, and then do sda2 last. sda2 must be deleted last because it is essentially a container that holds sda5 and sda6, and those need to be removed before removing the container.

---

### Post by PWill21 on 2009-03-06
Still no go, I can't delete sda6 or sda2 which GParted shows as active or busy (key icons?). Right-clicking on each partition shows /dev/sda6 as 'Active' and /dev/sda2 as 'Busy (At least one logical partition is mounted)'. I'm running everything from the LiveCD, how would these partitions currently be used?

---

### Post by PWill21 on 2009-03-06
A current screenshot of GParted

---

### Post by PWill21 on 2009-03-06
Well, I finally got everything back and running. In order to re-adjust the partitions, I first needed to get grub back, and this [http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/]("http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/") worked perfectly. After that I was able to get back into 8.04 and resize that partition. I should note that the original problem was NOT with installing 8.10, but in updating/upgrading in 8.04

---

### Post by skillllllz on 2009-03-06
I'm glad you got it working again. :-)

---

