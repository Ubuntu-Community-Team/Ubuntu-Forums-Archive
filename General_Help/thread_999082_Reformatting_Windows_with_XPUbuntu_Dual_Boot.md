---
title: "Reformatting Windows with XP/Ubuntu Dual Boot"
date: 2008-12-01
forum: General Help
---

### Post by ncanna1 on 2008-12-01
I am planning on reformatting my Windows drive, and wanted to make sure of a few things first.  I have XP and Ubuntu installed on different drives, but GRUB itself is on the Windows drive.  I'll refer to my win drive as sda1, my ubuntu drive as sdc1, and I also have a storage drive, which is sdb1.  

I want to repartition sda1 so that I can install Vista and also make some free space on the drive to experiment around with other linux distributions (Windows doesn't need the entire 160GB, obviously.) 

I know that Windows will remove GRUB and replace it with its own bootloader.  I was having some issues with GRUB with my first Ubuntu install, so I'm somewhat familiar with editing the menu.lst to manage which partition the system is booting from. 

I have a couple of questions, though.  Whenever I was installing Ubuntu, I set it to install on sdc1, but to boot from sda1.  Did this just tell the live disk where to install GRUB, or will this make my Ubuntu install unbootable?  Also, I was planning on using Super Grub Disk to reinstall GRUB.  Should this take care of anything that Windows removes, or is there something further that I should get?  

For some additional information, I originally installed Gutsy 7.10, and have since upgraded to Intrepid 8.10.  I already plan to back up all of my irreplaceable files to sdb1 (most of them are already there, out of practice), for the case that I have to reinstall ubuntu as well.

---

### Post by Het Irv on 2008-12-01
If you are planning on using Super Grub Disk, then I wouldn't try anything eles.  If you use SGD to put GRUB in the MBR you should be okay on all accounts.

---

