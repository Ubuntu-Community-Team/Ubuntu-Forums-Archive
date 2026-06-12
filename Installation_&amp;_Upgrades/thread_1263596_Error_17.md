---
title: "Error 17"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by edsonarantes on 2009-09-11
hi,
 
i have some questions about installation of ubuntu 9.04 desktop, i have installed ubuntu at one of my hard disks.
 
i have 3 hd on my computer, 1 sata and 2 ide
 
on sata i have wxp
 
and on the master ide i have ubuntu
 
when i installed ubuntu i restarted the system and a new messaje appears:
 
Grub loading.....
 
Error 17.
 
I read the web forums but there are some things i dont understand
 
how can i solve my problem?

---

### Post by steinaro on 2009-09-11
I think this link should help.
[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/)
 
Just boot into your ubuntu live CD, open terminal and follow the instructions. 
I hope it helps.

---

### Post by presence1960 on 2009-09-11
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

