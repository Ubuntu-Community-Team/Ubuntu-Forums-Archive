---
title: "[SOLVED] Login screen off-center"
date: 2008-09-23
forum: General Help
---

### Post by pwaugh on 2008-09-23
With my Hardy installation, after changing my resolution to 1280x1024, my screen is fine, but the login screen is off-center, as-if it was on a 1600x1200 screen, but there is no scrolling it as a virtual screen.

Ideas on how to fix it?

Patrick

---

### Post by GandalfTheNerd on 2008-11-05
You can fiddle with the "virtual" line in /etc/X11/xorg.conf if you wish.  The resolution there seems to have to match the resolution in use, or you get this misalignment problem.  There's lots of help about this if you search for it.

In my case, I fixed it by upgrading to Ibex and then running "sudo dpkg-reconfigure -phigh xserver-xorg" which generated a nice new (and rather slim) xorg.conf file.  Ibex seems to handle this sort of thing much better.

---

### Post by pwaugh on 2008-11-05
** deleted duplicate **

---

### Post by pwaugh on 2008-11-05
> **GandalfTheNerd said:**
> You can fiddle with the "virtual" line in /etc/X11/xorg.conf if you wish.  The resolution there seems to have to match the resolution in use, or you get this misalignment problem.  There's lots of help about this if you search for it.


I tried searching and found nothing, which is why I posted, but perhaps my search was for the wrong thing, as I'm sure this is a common question.

However, once I changed (rather than delete as I had tried before) the Virtual line to match my resolution, it works!  Thanks!


> 
In my case, I fixed it by upgrading to Ibex and then running "sudo dpkg-reconfigure -phigh xserver-xorg" which generated a nice new (and rather slim) xorg.conf file.  Ibex seems to handle this sort of thing much better.

What is Ibex, and where do I get it?

Patrick

---

### Post by stoneage on 2008-11-05
Ubuntu 8.10 Intrepid Ibex

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by pwaugh on 2008-11-05
Ah, I knew I had heard of it, haha.  :D

---

