---
title: "During install a problem occured"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by sundarrajan on 2008-12-07
Please Help me i used the entire memory space 160 GB of 
my hard disk for Ubuntu Installation.


But it Failed because it showing the error message like this


" The Creation of swap space in partition #5 of 
  SCSI3(0,0) (sda) failed"

help me to get rid of this error message and to Complete the

Ubuntu Installation in My System.


I want to use the Entire Memory Space of My Computer System for Ubuntu.

---

### Post by Pumalite on 2008-12-07
Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Delete everything in your hard drive. Then format ext3.
At installation; go with 'Use Entire Disk'
This will install the system and make a /swap partition for you. It will also install Grub to the MBR.

---

