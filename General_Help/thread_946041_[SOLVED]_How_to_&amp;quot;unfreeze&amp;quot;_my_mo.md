---
title: "[SOLVED] How to &amp;quot;unfreeze&amp;quot; my mouse?  Is there a command line to reset the mouse?"
date: 2008-10-12
forum: General Help
---

### Post by patrickballeux on 2008-10-12
Hi,

Sometimes, when a bad OpenGL games crashes or freeze and I had to kill it, my mouse won't move until I log out and login again (restarting the xorg server...).

I would like to know if there is a command that I could run from a terminal (or using alt-F2) that would reinitialize the mouse driver in X so it would move again?

For example, xmoto is freezing when I close it (new problem probably related to my graphic card driver (ATI)).  So I have to kill the process to get rid of it.  I do "ALT-F2", "xkill" and click on the window of xmoto.  Everthing works but my mouse, that is stuck in the middle of my desktop.

I can logout and login to regain control of the mouse, but if it would be possible to "reset" the mouse without leaving the desktop, it would be great. 

Thanks!

---

### Post by patrickballeux on 2008-10-13
Hi,

I solved the problem myself.  The problem with opengl games was not my graphic card but the use of the pulseaudio server.

You have to install the package **libsdl1.2debian-pulseaudio** so the SDL layer will connect directly to the pulseaudio server.  In my setup, libsdl1.2debian-alsa was installed.

The games were simply using the ALSA interface thru pulseaudio and they were not able to exit because of this.

Thanks to me :guitar:

Have a nice day!

---

