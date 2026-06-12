---
title: "Basic Update Changed my xorg.conf file"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by tir38 on 2009-08-22
I just ran a basis update through Update Manager. I've done this a million times but this time, after restart, my screen resolution was reset to 800 x 600 (instead of  1024). I looked in the System->Preferences->Display window and it shows my monitor as "Monitor: Unknown". After looking at my xorg.conf file it shows only:

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```I don't know what was there before but surely it must be more specific than that. I've never had to change my xorg.conf file in the past; Ubuntu always detected my monitor correctly. How can I either fix this or roll back whatever changes were made?

---

### Post by tir38 on 2009-08-22
so maybe my xorg.conf file didn't change. After looking through my /etc/X11 folder I see several files:

```
jason@black:/etc/X11$ ls -l
total 64
drwxr-xr-x 2 root root 4096 2009-07-27 01:25 app-defaults
drwxr-xr-x 2 root root 4096 2008-10-29 19:10 cursors
-rw-r--r-- 1 root root   14 2008-10-29 19:07 default-display-manager
drwxr-xr-x 6 root root 4096 2008-10-29 19:02 fonts
lrwxrwxrwx 1 root root   13 2008-12-27 09:09 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root 4096 2008-10-29 19:03 xinit
drwxr-xr-x 2 root root 4096 2009-07-27 01:24 xkb
-rw-r--r-- 1 root root 1065 2009-08-22 17:56 xorg.conf
-rw-r--r-- 1 root root 1037 2009-08-22 17:42 xorg.conf.20090822174255
-rw-r--r-- 1 root root 1037 2009-08-22 17:56 xorg.conf.20090822175625
-rw-r--r-- 1 root root 1037 2009-07-27 09:09 xorg.conf.dist-upgrade-200907270909
drwxr-xr-x 2 root root 4096 2009-07-27 00:41 Xresources
-rwxr-xr-x 1 root root 3730 2008-10-23 09:40 Xsession
drwxr-xr-x 2 root root 4096 2009-07-27 08:56 Xsession.d
-rw-r--r-- 1 root root  265 2008-10-23 09:40 Xsession.options
-rw-r--r-- 1 root root   13 2007-07-24 05:59 XvMCConfig
-rw------- 1 root root  614 2008-10-29 18:58 Xwrapper.config
```

of the four xorg.conf files (including the dist-upgrade, from when i upgraded to 9.04 last month) they all show the same thing.

So, what else could have caused my monitor to be "unknown"?

---

### Post by Farmer of Bricks on 2009-08-30
I'm having the same problem. you could try ```
sudo cp /etc/X11/xorg.conf.20090822175625 /etc/X11/xorg.conf
``` to overwrite your xorg.conf with the most recent update, but that may not work. Didn't for me. 
If you watch the startup messages and hit ESC when GRUB asks you to, you can boot into safe mode and try running xfix, but, again, that didn't work for me. I think that the problem is that the latest round of updates somehow prevents the video card from properly detecting the monitor. 

Other than that, I don't know.

---

