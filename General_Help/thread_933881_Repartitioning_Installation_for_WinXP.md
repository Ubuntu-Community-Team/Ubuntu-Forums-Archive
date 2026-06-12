---
title: "Repartitioning Installation for WinXP"
date: 2008-09-29
forum: General Help
---

### Post by freshtealeaf on 2008-09-29
Hello all,

Currently I have Xubuntu installed on a 250gb sata harddrive. I'm loving it so far, however due to work I need to install WinXP onto this machine also. I only have that one HD all of it's space is partitioned using whatever FS Xubuntu uses natively to install (I assume XFS??). 

My question is: Can I repartition this harddrive so Xubuntu only uses about 100gb and the rest is an NTFS partition where I can install (and subsequently dual boot) WinXP?? 

Thanks,

---

### Post by Bakon Jarser on 2008-09-29
I've never used xubuntu so I hope it's similar.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you have some system resources to spare you could load XP in virtualbox.  That would avoid having to dual boot.  Also a lot of windows programs run in wine.

---

### Post by Nano_ext3 on 2009-02-24
Resizing your linux partition is not a great idea, but I dont think its impossible.  Because system files are folder based in linux, be sure what you are doing.  What you should do is back up your linux files, and any config files you edited, and install xp first then xubuntu, but partition your hard drive FIRST (to prepare), 

If you wish to resize xubuntu to 100 gigs without re-installing , use Gparted in Xubuntu.

Use Gparted, located under applications , system.  If its not there open up the terminal and enter "sudo gparted" or "sudo su" then "gparted."  Gparted is really easy.

If you want to make a partition 100 gigs, open up a calculator and do 1024 * 100 (which will make it a perfect 100 gigs).  Dont question why, its complicated and related to the relationship of bits, bytes, megabytes and so on.  Resize your partition to this size with the slider on the graph or manually.  IF you are going to resize your ENTIRE hard drive to prepare for BOTH xp and linux, then use the Gparted live CD, located here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

If you install xp after , if xp uses the boot loader it has, it does not love linux, and may not show it or error.  See this post about the topic:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_windows_AFTER_Linux](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Installing_windows_AFTER_Linux)


So, you see its , reallyyyyyy a pain to install windows AFTER linux, but it can be done, just a royal pain.  I suggest backing up your linux data and using gparted to delete the partitions (using the Gparted LIVE cd), and make your new partitions according to the size you want.  The reason you do it AFTER xp is because of the Grub Bootloader which can handle ANY operating system, easily, unlike the XP bootloader, or Mac OSX boot loader (thats why bootcamp was made for xp).

Cheers!

Nano

---

