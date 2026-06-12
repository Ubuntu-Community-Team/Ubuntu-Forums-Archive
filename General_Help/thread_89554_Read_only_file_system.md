---
title: "Read only file system"
date: 2005-11-12
forum: General Help
---

### Post by GeneM on 2005-11-12
I have installed Breezy and have been using it for a few days now. It seems to be switching the file system from a read/write file system to a read only file system. This always happens after I have left the computer on overnight. This is driving me nuts. I have to reboot to be able to edit files, add or delete files. This seems to be happening to only one file system, /data. I mount it the same as I do all my other file systems and they all still allow to write to them. Jus this one file system seems to be changing from read/write to read only.  When I cat mtab I get
    /dev/sdb2 /data reiserfs rw 0 0
and when I cat fstab I get 
    /dev/sdb2       /data                   reiserfs        defaults        0       2
for the /data file system.  So it looks like I should be able to write to the /data file system but I can not.  Not even using sudo.

Does anyone know what is happening and how to fix it?  Help will be greatly appreciated.  

Gene

---

### Post by Eleaf on 2005-11-12
This was happening to my iBook.  Whenever I would open every other application or file, the hard drive would click a little and then go into read only mode.  It turns out the hard drive was messed up and reinstalling / repairing didn't help.  So I got a new hard drive and it works fine.

It may be a hard drive problem.  There might be a linux program that may be able to repair it if that may be the case.

Otherwise, I'm not sure!

---

