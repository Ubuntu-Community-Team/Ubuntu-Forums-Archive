---
title: "Dual Graphic card Vaio Problem !!! :("
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by Veskit on 2007-06-22
Hello,

I've just installed Ubuntu Feisty (amd64) on my vaio SZ4, and of course I want to make both graphic cards work (INTEL GMA 950 an Geforce 7400 Go)
I've found some explanation on how to make a "xorg-switcher" (thanks to collins_ )

1) I've installed Feisty with intel GMA 950 all is working great (3D, beryl ....)

2) Then I wanted to install NVIDIA 7400, everything is great with nvidia drivers, my xorg.conf is edited and all is working (3D, beryl ...)

3)I'm preparing the xorg-switcher having a xorg.conf.stamina (for intel GMA) and xorg.conf.speed (for nvidia). I'm creating a xorg switcher

> 
#!/bin/bash
#switch xorg

VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf.speed /etc/X11/xorg.conf
else
cp -f /etc/X11/xorg.conf.stamina /etc/X11/xorg.conf
fi
then
# chmod +x /etc/init.d/xorg-switcher
# ln -s /etc/init.d/xorg-switcher /etc/rc2.d/S12xorg-switcher


ok the switcher is working great my 2 cards are working

BUT ! when I switch to the intel GMA and check for "direct rendering" I have

> 
$ glxinfo | grep direct

Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ": 0.0".
Error: couldn't find RGB GLX visual
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ": 0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0 ".

Installing NVIDIA drivers have removed "direct rendering" for intel GMA
can someone help me with that ? I've lost 3D acc on intel GMA and can't use beryl

I'm a big newb on ubuntu I've just starded. I've thought of something like this:

> 
#!/bin/bash
#switch xorg

VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf.speed /etc/X11/xorg.conf
cp -f /etc/X11/xserver.speed /etc/X11/xserver
else
cp -f /etc/X11/xorg.conf.stamina /etc/X11/xorg.conf
cp -f /etc/X11/xserver.speed /etc/X11/xserver
fi


but I don't know if it'll work since I don't know what file I need to copy paste.

Can someone help me with that ? to have on both NVIDIA and INTEL GMA 3D acceleration activated ?

Thanks a lot

Veskit

---

