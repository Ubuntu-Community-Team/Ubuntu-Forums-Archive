---
title: "[SOLVED] keyboard layout at boot tim"
date: 2008-08-09
forum: General Help
---

### Post by hastala on 2008-08-09
Hi,

i had installed Hardy on my PC choosing german keyboard layout while installing. 
I found out how to change that to english layout in GNOME on a per-user basis, but how do it change the layout that's used while booting and for the GNOME logon screen?

---

### Post by hastala on 2008-08-11
<SOLVED>

i removed /etc/console-setup/boottime.kmap.gz and then ran dpkg-reconfigure console-data

it asked me for the keyboard layout and console setup i'd like to use and activated that, so it's available at boot time (don't know how to call this... the time the kernel goes up and starts everything)

voila

---

### Post by Vivaldi Gloria on 2008-08-11
```
sudo dpkg-reconfigure console-setup
```

shows the options menu.

---

