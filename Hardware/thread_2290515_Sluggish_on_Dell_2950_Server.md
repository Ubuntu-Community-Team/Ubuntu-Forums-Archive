---
title: "Sluggish on Dell 2950 Server"
date: 2015-08-12
forum: Hardware
---

### Post by EnderUSAF on 2015-08-12
I installed Ubuntu on a Dell 2950 III server and it is running extremely sluggish.  I had windows on it prior to installing Linux and it ran very smoothly.  Any Ideas what might be causing this?  The server is running the desktop version of the latest stable release.  If I SSH into the box, everything runs nice and smoothly there, but if I login to it locally everything on the GUI side is very slow.  To include moving the mouse, opening pages, installing programs.  Another issue I'm having is RDP'n to it from a Mac via XRDP.

---

### Post by weatherman2 on 2015-08-12
FYI, Ubuntu has something built-in called "Desktop Sharing," and you access it with a VNC viewer, not RDP.  You have to enable "Desktop Sharing" in Ubuntu first, though.

I have found that some graphics card don't have good default drivers in Ubuntu - you may find an Additional Driver that improves things as far as performance.  Even then, I have found that performance over VNC is much better if you use a lighter desktop besides the default "Ubuntu Desktop" (Unity).  I use "Gnome Flashback" (aka "Gnome Fallback") which gives you an old-style "Gnome" Gui not the "tiles" appearance of Unity - but if you choose the "Metacity" version (not "Compiz") of Gnome Flashback, it works much faster over VNC, if you can live with limited graphics effects.  (For a server, who cares?)

You can install Gnome Flashback from Ubuntu Software Center or from the terminal.  Then, logout and log back in by choosing the new session:

[http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html](http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html)

---

### Post by Yellow Pasque on 2015-08-12
From specs, it seems this server uses an old ATI ES1000 video chip (with 16MB of video RAM). Those chips don't support a lot of 3D/OpenGL features, and they will not run Unity well.  So yes, use a lighter desktop environment as suggested in previous post. [https://help.ubuntu.com/community/RadeonDriver#Supported.2C_but_Hardware_is_Too_Old_for_Unity](https://help.ubuntu.com/community/RadeonDriver#Supported.2C_but_Hardware_is_Too_Old_for_Unity)

---

### Post by EnderUSAF on 2015-08-13
Thanks!  I'll look into running something lighter.

---

### Post by EnderUSAF on 2015-08-13
After getting the server up and running, it really does seem graphical only.  It still streams plex media server to the rest of my devices like a champ.

---

