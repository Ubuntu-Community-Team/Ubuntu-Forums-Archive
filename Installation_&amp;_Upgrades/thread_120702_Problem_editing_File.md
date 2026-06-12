---
title: "Problem editing File"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by Rollo Tamasi on 2006-01-23
Hi guys, i'm having trouble editing the fstab file in the etc folder. I'm logged in as root in the terminal and when i go to run gedit /etc/fstab

I get the following error message:-
> 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gedit:12547): Gtk-WARNING **: cannot open display:
root@ubuntu:/home/cormac# gedit /etc/fstab/
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

does anybody have any idea why i'm not getting access to this file? any help appricated. Thanks, Rollo.

---

### Post by MartinG on 2006-01-23
[QUOTE=Rollo Tamasi]Hi guys, i'm having trouble editing the fstab file in the etc folder. I'm logged in as root in the terminal and when i go to run gedit /etc/fstab

I get the following error message:-


does anybody have any idea why i'm not getting access to this file? any help appricated. Thanks, Rollo.[/QUOTE]The X server by default limits those allowed to connect to it to the main login. Using sudo you still qualify, but if you run as root in a terminal rather than sudo you will only be allowed to do command-line operations.

To get around this do "xhost +localhost" before you do su.  Alternatively install sux, and then use the command sux in place of su, which will transfer your X access privileges to root.

---

