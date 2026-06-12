---
title: "Setting up dual-boot"
date: 2005-01-16
forum: Installation &amp; Upgrades
---

### Post by Nikkiru on 2005-01-16
I'm about at my wits' end. I recently Installed ubuntu on my Dell laptop, then discovered that I couldn't install partition magic on it.  So that meant  that if I wanted to be able to have a dual boot system, and be able to resize partitions without some impossibly complicated rigamarole I don't know how to perform (and neither does anybody else I know),    I had to reinstall Windows. 

So I use my  my Dell recovery disk to repartition and  reformat the drive,  and reinstall windows,  and  when my system rebooted I got the following error message: 

> GRUB loading stage1.5
GRUB loading, please wait ...
Error 17
HUH???  After all those warnings that I was about to destroy ALL the data on my hard drive, how could this *be?* 

So even after  I've ostensibly wiped all information off my hard drive,  I have  the ghost of an  operating system that's supposed to be GONE, from a hdd that's ostensibly been wiped clean of all data, refusing to allow the Windows installation to go forward.  Even after "C" drive had been established and formatted, and the Windows  setup files installed. 

BTW, the same thing happens when I run fdisk from a WIN 98 start disk,  set the DOS partition as active, and then go to reinstall Windows. I have now ostensibly wiped all data from my hard dtrive at least 6 or 7 times, and still this error message  refuses to go away, and refuses to let me have my computer back in anything but a Linux OS . Yes, it WILL allow me to reinstall Ubuntu - but that's ALL it will allow me to do with my hard drive. 

So here's question #1:
Is there any way for me to have Windows on my laptop's hard drive again? Or has  Linux taken over and corrupted my hard drive to the point where I will have to replace it?  

Question #2:
Is there a reasonably understandable way to create a dual-boot system within Linux?   In other words, is there a Linux equivalent to Partition Magic? 

Question #3:
Is there any reasonably understandable  way to  install Ubuntu onto a clean drive,  leaving some room for a reasonably sized DOS partition?   So far, the only option I've been able to make sense out of uses the whole disk.  


I'm sorry if my frustration is making me into an obnoxoius newbie here. But  I'm really at my wits' end. 


I named this thread "setting up dual-boot" because that really is my ultimate goal. But this seemingly insurmoutable  snag has left me in near total  despair.

---

### Post by Lachlan on 2005-01-21
You could try using Knoppix live CD.Call up the Knoppix root terminal,mount /dev/hda,etc,etc and run cfdisk or fdisk to delete your partitions.

Lachlan

---

### Post by CbrPad on 2005-01-21
I've been running Ubuntu, but have just installed Win2k onto a spare partition as I need dvd burning and haven't been able to get it work.  

When it rebooted after copying over the files during installation, it also popped into the grub menu and I couldn't continue with setting up Win2k.  I solved by booting up with the Windows boot floppy I had, and running "fdisk /mbr" (without the quotes) which wiped the linux grub, replaced with windows and let me continue the install.  HTH.

---

