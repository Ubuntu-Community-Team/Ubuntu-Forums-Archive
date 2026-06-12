---
title: "Low graphics mode"
date: 2010-12-26
forum: Hardware
---

### Post by maksim_m on 2010-12-26
I used ubuntu 10.04 flawlessly but after installing glib and dbus(installation is done according to 'README' file: ./configure then make && make install) and rebooting the system, the desktop doesn't boot up and pops up the follow message:
 
"Ubuntu is running in low graphics mode.The screen,graphics card and input devise setting ciold not be detected properly.You should reconfigure those by yourself."
 
I've reinstalled the system and before installing dbus and glib it works well.I tried add 'nomodeset' in grub but it is not helpfull.

---

### Post by maksim_m on 2010-12-26
It strange that I managed install bluez before the problem appeared and run my bluetooth application.After system reinstallation I tried install bluez but it asks install glib,dbus,expat.....and from this point, after rebooting the problem begins.

---

