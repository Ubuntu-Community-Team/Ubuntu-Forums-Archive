---
title: "Problems with libgtk-2.0, maybe?"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by moze on 2009-02-05
Hi,

I have a laptop Dell Latitude D640 with Ubuntu 8.10 installed. Since the latest kernel update (2.6.27-11) I haven't been able to use graphical user interface. Splash screen appears but gdm login screen stays black and pointer is jumping up and down. The result is the same when using older kernels.

First, I tried to fix xorg.conf and reinstall video drivers with no success. Then I installed xfce4 and xdm and noticed that xdm is working correctly. Xfce4 starts but only the background image is shown, not icons or menus. I took a look at logs and from .xsession-errors I found many references to libgtk-x11-2.0.so.0 like this one:

symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_window_remove_redirection

Reinstalling libgtk2.0 packages didn't help. I'm such a newbie so I don't know what to do next or where to search, so it would be great if anyone could give me advices and hints.

---

### Post by moze on 2009-02-08
I managed to solve this problem. There were some libgtk files stored both /usr/lib and /usr/local/lib directories. I made a backup of the original /usr/local/lib directory, deleted all the files starting with libgtk from /usr/local/lib directory and X started working right away.

---

