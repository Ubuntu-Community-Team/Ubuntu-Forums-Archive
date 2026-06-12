---
title: "After XP installtion, i can't boot ubuntu :S"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by markomk on 2008-12-07
hi, 
i just format partion (windows) and install Windows XP,after the installtion i can't boot ubuntu :( i try to reinstall but ubuntu partition is OK :S and i stop reinstall. i try many forums but nothing help. i hope here i can find the solution 
tnx

maybe this can help a little

grub> find /boot/grub/stage1
 (hd0,4)

---

### Post by Rocket2DMn on 2008-12-07
Did you format your whole hard drive with XP?  If so, then you lost your Ubuntu install and need to reinstall Ubuntu.  If you kept your dual boot setup, what you are experiencing is normal - Windows overwrites the MBR so GRUB isn't available.  That means you need to reinstall GRUB - there are a number of ways to do this.  Please see [uhelp]community/RecoveringUbuntuAfterInstallingWindows[/uhelp]
I suggest option 3, using the SuperGrubDisk, as it is the easiest.  I've never used the Auto Super Grub Disk, but that may be worth a try, otherwise getting the standalone image and burning it (as an image) to a cd works as well.  It is OK to overwrite the Windows Bootloader.

---

### Post by markomk on 2008-12-07
i have 1 HDD drive..with 320 GB HDD
160 GB for Windows XP
160 GB for Ubuntu

i format only Windows Xp partition

---

### Post by Rocket2DMn on 2008-12-07
OK, then assuming you did your XP install correctly, Ubuntu should still be there.  That just means you have to reinstall GRUB.  Follow the directions I gave above, and if you have any specific questions, please feel free to ask - don't feel you have to do anything you aren't comfortable with, ask first.

---

### Post by markomk on 2008-12-07
I just wanna say BIG TNX :) i'm on ubuntu now :):popcorn:
you save me hours hours hours of work.):P
btw sorry for the bad English

---

