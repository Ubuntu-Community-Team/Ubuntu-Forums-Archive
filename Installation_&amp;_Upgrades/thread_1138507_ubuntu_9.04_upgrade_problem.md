---
title: "ubuntu 9.04 upgrade problem"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by edice on 2009-04-26
I downloaded ubuntu alternate cd. 
I made them.

[LIST=1]
[*] Download the **alternate** installation CD
[*] [Burn the ISO to a CD]("https://help.ubuntu.com/community/BurningIsoHowto#InUbuntu") and insert it into the CD-ROM drive of the computer to be upgraded.
[LIST]
[*] If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by [mounting the ISO as a drive]("https://help.ubuntu.com/community/ManageDiscImages#MountISOFiles") with a command like: 
 sudo mount -o loop ~/Desktop/ubuntu-9.04-alternate-i386.iso /media/cdrom0
[/LIST]
 
[*]A dialog will be displayed offering you the opportunity to upgrade using that CD.
[*]Follow the on-screen instructions.
[/LIST]
 If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 
 gksu "sh /cdrom/cdromupgrade" 

 but upgrade manager still trying to download from the Internet. it does not install from cd. What I can do.

Thanks for your help.

---

### Post by belbo on 2009-04-27
Same problem here. Anyone able to help ?

---

