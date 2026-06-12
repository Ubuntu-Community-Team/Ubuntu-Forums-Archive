---
title: "ubuntu &amp; vista dual boot problem"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by davewickett on 2009-07-26
ok i have vist and ubuntu dual boot with grub and i want to get rid of ubuntu and just keep vista so i can put backtrack on i only want vista in case i have problems with linux so if some1 could help me to just grt vista up again i would be so greatfull thanks 
dave :thumbsup::thumbsup::thumbsup:

---

### Post by presence1960 on 2009-07-26
If you installed via wubi then uninstall wubi via vista in control panel. if you have ubuntu on a dedicated partition(s) then boot Ubuntu live CD and choose "try ubuntu without any changes..." When the desktop loads open a terminal and run ```
gksu gparted
``` Use gparted to remove Ubuntu partitions. reboot. Now you are going to have to restore Vista's bootloader to MBR. If you have a vista install DVD (not a recovery DVD) do this; [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you have a recovery partition/recovery DVD use [super grub disk]("http://stmaarten.globat.com/~supergrubdisk.org/") or [go here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download and burn to CD/DVD the vista recovery console since you won't have one with the recovery partition/DVD. Then boot from that disc and follow the instructions in my first link to restore vista's bootloader to MBR

---

### Post by Sef on 2009-07-26
How did you install Ubuntu?

---

### Post by davewickett on 2009-07-26
thanks alot for comments really helpfull and i installed ubuntu 9.04 from cd that went threw things with me and done my partition on it aswell 

ill keep this post so i know how to do it because people are saying they are having problems uninstalling fron dual boot but some1 as told me not to install backtrack and just run it from iso and it would be ok and quick to use still as i want it to crack my wifi and test my laptop im just learning but really loving learning it aswell

i have an atheros ar5007eg card that ive got ubuntu up and runnig with , with madwifi and seems ok and i do have a usb belkin f5d7050 wifig aswell but dont know how to get my card working with bt iso because you can not save changes can you i dont mind doing something each time just dont know what

so i am keeping ubuntu as im just getting used to it and i do really like it aswell

---

