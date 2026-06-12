---
title: "wubi and application configuration error"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by davebridges on 2009-10-31
I am trying a clean install.  I installed windows but then when i try to start wubi, i get an error that there is an application configuration error.  If i boot with the install cd, the windows partition appears to take up the whole hard drive (it shouldnt be that big).  Any suggestions?

---

### Post by Mark Phelps on 2009-10-31
Wubi installs INSIDE MS Windows, using a special file that Ubuntu treats as a partition.  You will not see any separate partitions for Ubuntu when you install via Wubi.

---

### Post by garvinrick4 on 2009-11-01
Treat it like an App in windows. You will find it located in C:  in a Folder next to Users

Load thru WUBI tell what password is, tell how big you want Ubuntu. At least 10 gig.
It will come in/dev/loop0       Host will always be your Windows partition.

You can copy Windows files into your Ubuntu but not Ubuntu files into Windows.
Will be in  computer/filesystem/host/user/your user name

If you want to put some linux files into Windows, copy to external and then into Windows.

fsck    every so often to make sure you are clean. 

Any trouble  fsck   in root will usually fix problem.  

If you are 64 bit capable and you have 32 bit Windows, you can still use 64 bit Ubuntu.

Maintain your Machine. Maintain your Machine. Maintain your Machine.

If you mess it up, you can just uninstall in your Windows side and reinstall from disk
takes 12 minutes to install.   Nice to keep a .iso burned image on cd   of version you want handy.  

Uses grubdos4 from Windows to boot.  Does not use Linux Grub2  or Grub legacy.

---

