---
title: "Compiz : Desktop Effects could not be enabled"
date: 2008-10-01
forum: General Help
---

### Post by hamzamusa on 2008-10-01
Hi , i installed gOS ( ubuntu based distro ) on my laptop ( dell inspiron 1525  ) installed without any problems ,though its working without any problem .

My Video driver Intel is working , and i installed 
sudo apt-get install xserver-xorg-video-intel .

it`s not showing up in /etc/X11/xorg.config

> Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection




However Desktop effects could not be enabled at all .

so i ran : "compiz" in the terminal i got this :
got this error 

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed

```

Any suggestions ?!

Ps : i made sure the Intel driver is not blacklisted in : /usr/bin/compiz

Note : i tried to post a post in dell support section , how to use MediaDriect ( dell laptop setup and configuration package ) to make a dual boot windows , and ubuntu , partitioning the HDD , but i can't post in there

---

