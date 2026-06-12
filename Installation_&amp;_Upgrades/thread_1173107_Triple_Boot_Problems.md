---
title: "Triple Boot Problems"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Tutigan on 2009-05-29
I don't know if this is the correct place to post this, but I'm going to anyway...
I love testing out all new software on my PC, and as such have decided to triple boot it with Windows Vista, XP and Ubuntu. I followed the guide found at [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm) (although, I changed it to include XP of course).
I have installed XP on one HDD and split another to have Vista and Ubuntu installed on it. I installed the windows OS's first, but after installing Ubuntu, I couldn't get the GRUB menu, I only got the Vista menu which allowed me to boot XP and Vista. I have followed several guides to allow me to use the vista bootloader, but so far, I have been unable to boot Ubuntu. Short of re-installing everything... What are my options? Anyone have any ideas?

---

### Post by Grafixx01 on 2009-05-29
Try EasyBCD on the Vista. It allows you to add lines to the Vista Boot Loader and it will add in Linux partitions to it. It's free, if you want to do it through a GUI / Vista. If you want to do it through Linux and GRUB, then someone else will have to help you out with that one since I'm still learning Linux.

---

### Post by Tutigan on 2009-05-29
Thanks for the suggestion graffix!
I've tried using easyBCD and I got Vista and XP to boot... But I'm unable to work out how to get Ubuntu loading.. If anyone has any advice or links to tutorials to use this tool properly... Any help would be great!

---

### Post by Grafixx01 on 2009-05-30
I believe that EasyBCD has documentation on how to make it work but I know they also have a forum like this that you can ask or view since I know others have probably had your same issue.

---

