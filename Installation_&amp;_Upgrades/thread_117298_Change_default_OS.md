---
title: "Change default OS"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by Gonte on 2006-01-14
Hi, now I've succesfully installed both Windows ME (Millenium Edition) and Ubuntu 5.10 on my parents computer (I use their computer alot).

Now the computer automaticly loads Ubuntu unless I chose Windows on startup, but because it's not my computer I want to make Windows the default OS, and only load Ubuntu when I chose to that...

Anyone who knows how to change the default OS?

---

### Post by gosh on 2006-01-14
Follow this thread:

[http://www.ubuntuforums.org/showthread.php?t=105146&highlight=%2Fboot%2Fgrub%2Fmenu.list](http://www.ubuntuforums.org/showthread.php?t=105146&highlight=%2Fboot%2Fgrub%2Fmenu.list)

---

### Post by vruum on 2006-01-14
the boot loader Grub, is managed through the file /boot/grub/menu.lst, to edit that open a terminal and type
```
 sudo gedit /boot/grub/menu.lst
```
look for a line that says something like
title windows ME
move the block of code (sould be about three lines looking like
title           windows ME
root            (hd0,2)
savedefault
makeactive
chainloader     +1
)
up just above the line that says 
##debian automatic kernel list##
and make sure that the default line says
default   0
#EDIT or follow the thread gosh pointed at

---

