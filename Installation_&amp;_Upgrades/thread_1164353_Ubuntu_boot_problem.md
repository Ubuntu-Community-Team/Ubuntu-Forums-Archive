---
title: "Ubuntu boot problem"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by anuj27 on 2009-05-19
I have installed Ubuntu 8.10 on my system which had WindowsXP installed on it. After the installation got over, when i restart my comp Ubuntu does not appear in the boot menu. I mean no boot menu appeared and WindowsXP started of it own. How to boot into Ubuntu and make it appear in the boot menu?

Moreover when i was in the process of installing Ubuntu, I was getting a bunch of I/O errors. Something like "buffer I/O error on device...". Then i left the comp like that only, with the errors keep on emerging on the screen, and went off to sleep. When i woke up i saw the regular setup window again and the installation continued normally without anymore errors. And now i am facing the problem mentioned above. I could not boot into Ubuntu even once after the installation.

Plz help. Thanks!

---

### Post by ajgreeny on 2009-05-19
Sounds as if you had a bad CD to install from, or the iso file you used to burn the CD was bad.  Did you check them, the iso with md5sum after downloading and the CD from the first menu that appears.

---

### Post by enz1m3 on 2009-05-19
Do you have more than one disk? or more than one partition? Seems like you didn't install or installed on another partition/disk which isn't being booted (which can be changed on bios)

If you need help or have any doubt, don't be afraid to ask!

---

### Post by anuj27 on 2009-05-19
At first i thought my CD or the iso was damaged but i have written many CDs from that iso and those CDs worked fine previously, so the iso seemed OK. I changed my CD-ROM and wrote a fresh copy of CD from the same iso after i got this error for the first time, but the error msg continued. This proves both my CD and CD-ROM are fine. So the CD, CD-ROM and iso is not a problem.

While installing i chose the partition properly. Ya i have one more HDD installed in my system which already had a copy of Ubuntu installed in it previously, as i use this HDD in my college, but that copy of Ubuntu got somehow corrupt. So is it possible that the installation took place in the other HDD (though i am certain that i chose the partition correctly)? And y those error msges?

Plz reply!

---

### Post by enz1m3 on 2009-05-20
I'm not saying you dind't choose the partition properly, just that your bios may be choosing your other disk to boot instead of the one where you have ubuntu.

This may also happen because you have windows disk set to master and ubuntu disk set to slave, try switching (check your disk manufacturer for jumper reference).

---

### Post by presence1960 on 2009-05-20
to get a better picture of your setup Boot from the Live CD and download the Boot Info Script to your Desktop : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal Applications > Accessories > Terminal and run this 
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on your desktop. Post the contents of this file back here. Highlight all text then click # from the toolbar to place code tags around the text.

---

### Post by anuj27 on 2009-05-25
I disconnected my second (Sata) harddisk and installed Ubuntu in this first (ATA) one... and the installation took place quite smoothly, without any error msg mentioned above. 

Now when i boot into Ubuntu, it starts smoothly with no error msg (if the second hdd is disconnected) but if I connect the second hdd and try to boot into Ubuntu same error msgs keep appearing for 5-6 mins and then the OS starts normally. What can be the problem?

---

### Post by anuj27 on 2009-09-21
There was some problem with my hdd. Previously installed Ubuntu was not uninstalled properly. I performed a LOW LEVEL FORMAT to the partitioned which had Ubuntu installed and then my problem was solved :)

Anuj

---

