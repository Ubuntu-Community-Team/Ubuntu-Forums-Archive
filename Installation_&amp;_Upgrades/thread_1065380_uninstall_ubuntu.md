---
title: "uninstall ubuntu"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by kobra_877 on 2009-02-09
hey i need some help i want to uninstall ubuntu 8.10 so i can try to get xp back on. could i get some help. right now i ownly have ubuntu8.10 on but i want xp also. and i want to start over fresh thanks in advanced

---

### Post by taurus on 2009-02-09
Boot with Ubuntu LiveCD.  Then use gparted in System -> Administration and delete all the partitions on your harddrive.  You probably have to unmount the swap partition first before you can delete it.  Then, create a partition, /dev/sda1, that takes up the whole harddrive and format it to ntfs filesystem.  Now, reboot with the windows CD in the drive and it should pick up the harddrive.

---

### Post by kobra_877 on 2009-02-09
would you be able to give me a bit more detail please.
 im just a beginer at this

---

