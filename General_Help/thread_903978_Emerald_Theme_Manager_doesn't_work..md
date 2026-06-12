---
title: "Emerald Theme Manager doesn't work."
date: 2008-08-28
forum: General Help
---

### Post by nerd0795 on 2008-08-28
I was trying to get this cool theme to work for a while.  But Emerald Theme manage 0.7.6 doesn't seem to want to work for me.  So I found solutions online.  So I changed Window's Decorations command like a few people recommended.  It still didn't work.  I copy and pasted a command another person recommends.  After that the screen started flickering and then it was back to normal displaying this message:

```
alex@alex-desktop:~$ compiz --replace &
Checking for Xgl: [1] 7174
alex@alex-desktop:~$ emerald --replace &not present. 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 0300: 1002:7941 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/home/alex/.themes/Glasy/gtk-2.0/gtkrc:1576: Unable to locate image file in pixmap_path: "Tabs/1notebook2.png"
/home/alex/.themes/Glasy/gtk-2.0/gtkrc:1586: Background image options specified without filename
/home/alex/.themes/Glasy/gtk-2.0/gtkrc:1591: Unable to locate image file in pixmap_path: "Tabs/2notebook2.png"
/home/alex/.themes/Glasy/gtk-2.0/gtkrc:1601: Background image options specified without filename
/home/alex/.themes/Glasy/gtk-2.0/gtkrc:1606: Unable to locate image file in pixmap_path: "Tabs/3notebook2.png"
/home/alex/.themes/Glasy/gtk-2.0/gtkrc:1616: Background image options specified without filename
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
alex@alex-desktop:~$ emerald --replace &Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
alex@alex-desktop:~$ emerald --replace &Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed

```

Does anyone know how to fix this?

EDIT:  Also Compiz fusion effects don't work anymore.  Don't know what happened (happened about a few months ago)

EDIT2:  I have an ATi Radeon Xpress 200 Graphic Card.

---

### Post by belorix on 2008-08-28
Hello, Try using the following command to solve your problem, If your using Emerald (most likely) try doing **emerald --replace & disown**

---

