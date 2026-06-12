---
title: "Missing GLX for Intel Graphics Card"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by skunkwerk on 2007-12-13
I'm trying to get a program using OpenGL working on my Ubuntu 7.04.  I keep getting the error "extension GLX missing on display: 0.0" and get similar output when I try glxgears or glxinfo.  My graphics card is an Intel 945GM.  This is the output from my Xorg.conf log.  The only advice anyone seems to have is uncomment #load "glx" in my Xorg.conf but it wasn't commented out to start with.  Any help much appreciated.

thanks

LoadModu: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor = "NVIDIA Corporation"
     compiled for 4.0.2, module version = 1.0.9639
     Module class: X.Org Server Extension
     ABI class: X.Org Server Extension, version 0.1
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded

---

### Post by Dark_Stang on 2007-12-13
According to that you're using the nvidia driver for an intel card...? You should use the intel drivers instead.

Open up a terminal. Quit X by running "sudo /etc/init.d/gdm stop"
Now login and enter "sudo dpkg-reconfigure xserver-xorg"
Now pick all the right drivers, the correct screen resolution, your keyboard, mouse, etc...
After that enter "sudo /etc/init.d/gdm start" and gnome display manager will come back up, and everything should be golden.

---

### Post by skunkwerk on 2007-12-13
thanks, but the thing is I am using an intel driver.

I did what you said, and reconfigured x, selected the intel mobile 945gm integrated graphics controller driver, but it didn't make any difference - it still can't load glx.

any further suggestions?

thanks

---

### Post by skunkwerk on 2007-12-14
glx loaded fine when I reinstalled with ubuntu 7.10, not kubuntu.  don't know why it wasn't working in the latter.

---

