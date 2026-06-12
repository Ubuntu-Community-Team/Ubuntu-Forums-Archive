---
title: "Repairing Ubuntu"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by waseempki on 2009-08-28
I want to repair ubuntu grub.when i try to repair grub.following errors occured.

---

### Post by rrplay on 2009-08-29
take a look here ::[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by waseempki on 2009-08-31
tanks for reply.but still my problem is not solved.i give you some information of my pc.i has installed windows xp and then installed ubuntu 9.04.
winxp installed at /dev/sda1 and ubuntu is installed at /dev/sda8.

---

### Post by presence1960 on 2009-08-31
unfortunately your stage 1 is not being found so any other command to set up GRUB will fail. 

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

