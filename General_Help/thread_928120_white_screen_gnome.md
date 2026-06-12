---
title: "white screen gnome"
date: 2008-09-23
forum: General Help
---

### Post by blueyez on 2008-09-23
i installed a few apps ( lets say.. many ) :D

and when i rebooted i reach the login screen.. i insert user+pass and i get a white screen and my cursor ( for one seconds i can see my desktop icons, but no top/down bars )

i currently use gnome safe mode 
latest stable version of ubuntu

i edited my /etc/X11/xorg.conf file so to configure X to 96 dpi
i restored my backup and still the same... 


tut used to modify dpi 
[http://warren.guy.net.au/docs/ubuntu-font-configuration.html](http://warren.guy.net.au/docs/ubuntu-font-configuration.html)

i also installed tahoma font from same link

---

### Post by sdowney717 on 2008-09-23
it is not your fault.
I blame white screen of death on the drivers and how they interact with compiz.
What is your video card model?

can you somehow login and turn off desktop effects?

---

### Post by paulmerchant on 2008-09-23
I don't know. Maybe you filled up your Ubuntu partition. Boot to a terminal and type df (disk free).

If you really are out of disk space, start doing some "sudo apt-get remove [packagename]" to free up some space.

---

### Post by mziskandar on 2008-09-23
I guess, you've just installed the graphic driver..

---

### Post by blueyez on 2008-09-24
a fix maybe ?
:confused:

---

### Post by mziskandar on 2008-09-24
During the white screen.. press Ctrl-Alt-Backspace. At the Login menu, click option and choose the Failsafe mode. You may get the (seems) normal screen.

Right Click on the desktop > Change Desktop Background > Click Visual Effect Tab.. Choose None.

Then, reboot.

I think its the driver problem which causing the accelerated gfx processing failed, and I really hope this matter can be resolve soon.

---

### Post by Crafty Kisses on 2008-09-24
Try running this command to reconfigure your X:
```
sudo dpkg-reconfigure xserver-xorg
```

---

