---
title: "Reinstallation Ubuntu 9.04 in dual boot config"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by azbeachbum on 2009-10-03
I installed Ubuntu 9.04 on a laptop in a Windows XP dual boot configuration. After damaging the video drivers to a point I couldn't figure out how to correct, I reinstalled Ubuntu 9.041. 
 
WHen booting after the first install, I had the option of booting to WIndows XP or Ubuntu. After reinstalling, there are many more options (Ubuntu generic, Ubuntu recovery mode, memtest, XP). When I boot under Windows XP, I am then given the choice to boot under Windows XP or my initial Linux installation.
 
I would prefer to have a single Linux boot session (with more HDD space allocated than my second installation) and Windows XP still loaded.
 
Is this possible or am I stuck?
 
Thank you,
John

---

### Post by scragar on 2009-10-03
Your first install must have been via wubi, it's not installed normally as such, but rather installed to an image on the windows partition, you should be able to remove that whole install from inside the add and remove programs menu of windows.

---

### Post by presence1960 on 2009-10-03
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

