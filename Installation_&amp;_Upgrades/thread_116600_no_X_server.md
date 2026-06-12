---
title: "no X server"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by Gustav on 2006-01-13
Hi!

A friend of mine is trying to install ubuntu on a quite old computer (266mhz 64mb). I advised him to do a server install and then install xubuntu-desktop and gdm but X won't start and he just get:
```
Failed to start the X server (your graphical interface).
   It is likely that it is not set up correctly. Would you
   like to view the X server output to diagnose the
   problem ?
               Yes                   No 
```
and after yes:
```
GDM: Xserver not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth
     /var/lib/gdm/:0.Xauth -nolisten tcp vt7
    Error: Command could not be executed!
    Please install the X server or correct GDM configuration and restart
    GDM. 
```
And he has tried sudo dpkg-reconfigure xserver-xorg.

Do anyone have any ideas?

---

### Post by Kipper on 2006-01-13
Putting the software together in this piecemeal way can be a probelm unless you know exactly what to download. Even if you have all the Xorg software and GDM, you'll find the "startx" scripts are trying to load a GUI environment, GNOME  or KDE etc., and you haven't got that.

I'd be tempted to do a normal install, assuming the machine has sufficient hard disk space and see how, or if, GNOME runs. Then you can install one of the lightweight desktop environments like Xfce which you should find in the Ubuntu repositories.

There's probably a how-to guide about how use alternative destops in Unbuntu somewhere.

---

### Post by kaamos on 2006-01-13
installing xubuntu-desktop and gdm should do the trick, I've done this on three machines now. You could try if the "startxfce4" script gets the gui going. Otherwise I'd go for reinstalling X.

---

### Post by Gustav on 2006-01-13
[QUOTE=kaamos]installing xubuntu-desktop and gdm should do the trick, I've done this on three machines now. You could try if the "startxfce4" script gets the gui going. Otherwise I'd go for reinstalling X.[/QUOTE]
Tried that.

I'm going for the standard install and then xubuntu on top of that way.

---

