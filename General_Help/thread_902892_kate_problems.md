---
title: "kate problems"
date: 2008-08-27
forum: General Help
---

### Post by Yaja on 2008-08-27
Hey im running kubuntu. 

Very new and im trying to get my wireless to work following [http://ubuntuforums.org/showpost.php?p=4808350](http://ubuntuforums.org/showpost.php?p=4808350)

it asks me to use the following command 

sudo gedit /etc/modprobe.d/blacklist


and edit the file but i get the message 

sudo: gedit: command not found


same result with 

sudo kate /etc/modprobe.d/blacklist



opening blacklist without root thing just wont let me save the change.
please can i have some help as its annoying sitting next to the modem when i could be watching tv as well :popcorn:

---

### Post by aysiu on 2008-08-27
It really should be ```
kdesu kate /etc/modprobe.d/blacklist
``` The command *kate* isn't found in Kubuntu?

Are you running KDE 4?

---

