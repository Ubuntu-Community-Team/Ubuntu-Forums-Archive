---
title: "Xp Vista Ubuntu boot help"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by Tyson S on 2009-09-14
Hi i have had xp and ubuntu installed for a while now, but 2 days ago i installed VISTA big mistake now i cannot acccess ubuntu (8.10) i have tried supergrub and moving my something .lst (the add to easy bcd) and doing this i was able to get access to ubuntu 8.10 bootscreen (which shows xp and all ubuntu) but when i enter it says Booting 'Ubuntu 8.1, Kernal 2.6 27-14-generic' 

Error 17 file not found:|

i know this is not true because when i use live cd i can see all my ubuntu documents.

Plzz help me.

Thank you even if you cant help:mrgreen:):P
-----------------------------------------------------------------------------------------------------------
Thank you it worked, thankx for your time:):P

---

### Post by cholericfun on 2009-09-14
strange that supergrub didnt do the job.

theres tons of advice on using GRUB after installing windows.
its really just a few lines in the terminal

you shouldnt neet to edit anything in menu.lst
however i had  a problem with the updated GRUB that it pointed to the wrong partitions in menu.lst - i guess that wasnt a common problem though cause it would have temporarily caused a huge amount of forum traffic.


so check this Manual:
[https://help.ubuntu.com/community/WindowsDualBoot#Recovering](https://help.ubuntu.com/community/WindowsDualBoot#Recovering) GRUB after reinstalling Windows


or (copy past from there...)
   1. Boot into a LiveCD
   2. Open a terminal
   3. Open the GRUB Command line utility by typing 

sudo grub

   4. Tell GRUB where your Ubuntu partition is by entering 

root (hdA,B)

Where 'A' is the hard-drive number, starting at 0, and 'B' is the partition number, starting at 0. For example, if Ubuntu was installed on the second partition of the first hard-drive, the command should be

root (hd0,1)

   5. Tell GRUB which drive to put the boot sector on 

setup (hd0)

(replacing 0, as above, if a drive other than the first is used as the boot device)

   6. Leave the GRUB Command line 

quit

and reboot.

---

