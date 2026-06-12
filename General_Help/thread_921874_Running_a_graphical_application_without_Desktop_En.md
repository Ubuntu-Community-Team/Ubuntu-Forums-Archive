---
title: "Running a graphical application without Desktop Enviorment"
date: 2008-09-16
forum: General Help
---

### Post by Chris017 on 2008-09-16
Hello there, This is my first post here. Ive got a a small question, How can i start GUI applications like Firefox with out a Desktop Environment i know how to get gnome and XFCE... But is there a way to boot an application with out the Desktop environment? 

Example when i run Firefox from a server Ubuntu it says error: No Display Specified? Is there a way to set a display up? Like a desktop environment that runs just for apps like Firefox?

seems kinda dumb just wondering because im not looking for a Desktop environment.

---

### Post by rsambuca on 2008-09-16
You can run the X server without a Window Manager or Desktop Environment.  Firefox will run fine just in X.

---

### Post by tuxxy on 2008-09-16
You need the xserver to run graphical apps, the best way to di run this is from a DE

---

### Post by kerry_s on 2008-09-16
[http://tldp.org/HOWTO/Framebuffer-HOWTO.html](http://tldp.org/HOWTO/Framebuffer-HOWTO.html)

---

### Post by rsambuca on 2008-09-16
> **tuxxy said:**
> You need the xserver to run graphical apps, the best way to di run this is from a DE

A Desktop Environment is certainly one way, but not necessarily the best way.  It depends on the user's particular needs.

---

