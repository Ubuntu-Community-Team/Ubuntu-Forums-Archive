---
title: "X Server problem in 8.10"
date: 2008-11-20
forum: General Help
---

### Post by cptsteiny on 2008-11-20
I'm running a two display system with a Daewoo Insignia 19" (CRT) and a Sceptre (X20WG-Naga) 20" (Widescreen LCD) using an NVidia GeForce 7300 GT video card.

This setup worked in Ubuntu 8.04 using two separate X servers.  However, since upgrading to Ubuntu 8.10, the secondary X server does not operate properly.  The primary server is set to run on the Sceptre 20" and runs properly with no observed bugs (yet).

The secondary X server runs on the Insignia 19".  Nothing runs on this server, except a terminal every once in a while.  It seems to display properly, and I can look into all of the menus ("Applications", "Places", "System", etcetera).  However, if I try to run ANY program, like Firefox or anything else, a error window pops up.  Nothing is displayed inside the error window, only the titlebar says "Error".  I cannot close the error window.  When this error window pops up, all of the Gnome Panels (the top and bottom bars) cease functioning, this includes the panels on the PRIMARY X server as well.  The only way to get out of this situation is to Ctrl-Alt-Delete and log out.  During the logout it asks if I want to quit the non-responsive Panel application, which I do.

Does anyone have any idea what's going on?
Thanks!

---

### Post by NT4usB on 2008-11-20
No idea what's going on but...
Have you tried reconfiguring using nvidia-settings? (install and) run:```
sudo nvidia-settings
``` Just go in, change some settings, and save it. See if that shakes something loose. Then go back and set it the way you want it.

---

### Post by cptsteiny on 2008-11-20
Thanks for the reply.

Unfortunatly, I have tried that, it seems to not do anything at all.  Making any changes in the nvidia utility doesn't seem to affect how the x servers opperate in any way.  In fact, the nvidia utility has the X Server arrangement wrong, it says that the Secondary server is to the right of the Primary, which in actuallity the reverse is true, both physically and in how Ubuntu is currently responding to mouse movements.

This makes me think that perhaps Ubuntu is currently ignorning the xorg.conf altogether.

---

### Post by NT4usB on 2008-11-21
Well, you could rename xorg and see if the video still works. 
Have you tried: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```That will rebuild xorg.

---

### Post by cptsteiny on 2008-11-22
I've now gotten to the point were changing the xorg.conf file does something.  However, I'm still unable to correct the problem.

Programs still crash Ubuntu when I try to launch them in the secondary X server.

---

