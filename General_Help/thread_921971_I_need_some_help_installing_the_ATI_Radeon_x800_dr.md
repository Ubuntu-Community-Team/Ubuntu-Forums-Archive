---
title: "I need some help installing the ATI Radeon x800 drivers"
date: 2008-09-16
forum: General Help
---

### Post by Reddington on 2008-09-16
I downloaded the Linux drivers for my Radeon x800 graphics card from the ATI site. When I tried to run the installer it just tries to open the drivers in gedit.

The drivers came as a .run file and I don't know what program I need to use a .run file. 

Any help will be much appreciated.

---

### Post by Washer on 2008-09-17
[apt:envyng-core]("apt:envyng-core")
[apt:envyng-gtk]("apt:envyng-gtk")
[apt:envyng-qt]("apt:envyng-qt")

---

### Post by jonian_g on 2008-09-17
Install envy. Type in a terminal:
```
sudo apt-get install envyng-gtk
```

Go to Applications>Sys tools>EnvyNG, install the drivers from there, reboot and you're done.

---

