---
title: "ATi 8.36.5 graphics driver not working"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by PuRity on 2007-05-19
Hi all, I recently tried to install the "new" ATi drivers for linux (version 8.36.5). Everything install fine, until I type "fglrxinfo" in terminal.. It displays the following:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

:confused:

I know that it ain't supposed to look like this.. Ive tried to reinstall the driver twice, but without success. I followed this guide when I installed the drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)


What am I doing wrong here?

Btw, I have an ATi Radeon x1650 PRO in my computer..

---

### Post by lord bacon on 2007-05-20
did u make sure u did all the post installation checks etc, secondly do you know if your x1650 is actually supported by ATi in linux (i remember reading some where that it isnt, but that may be fixed), also did the normal ubuntu drivers work (the short version of the guide)
 if that fails try altering /etc/X11/xorg.conf and replacing the string "ati" with "fglrx"

that is all i can think of atm.

---

### Post by PuRity on 2007-05-20
hmm, I think that it is supported.. 

When I tried to edit xorg.conf with "gedit", the file opened were completely blank.. I then moved to the /etc/X11/ folder, only to find out that there were no xorg.conf file. Just a backup created by the ATi drivers.. I renamed the backup, and enabled the "Restricted ATI Drivers" from menu: System->Administration->Restricted Drivers Manager, and suddenly everything works just fine.. :D   my output of "fglrxinfo" in terminal:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6458 (8.36.5)

Apperently, I also have direct rendering, but "Composite" in xorg.conf is set to "0".. Without it I won't be able to run Beryl, right? Is there a way fix this to? 

Anyway thanx for your help! ;)

---

