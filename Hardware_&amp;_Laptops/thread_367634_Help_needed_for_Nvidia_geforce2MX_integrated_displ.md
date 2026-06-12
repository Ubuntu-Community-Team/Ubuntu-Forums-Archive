---
title: "Help needed for Nvidia geforce2MX integrated display"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by adityadeva on 2007-02-22
Hi, 
I've been using ubuntu for quite some time and have discarded all other distros. my machine comprises of AMD AthlonXP 2100+ ; Asus Nforce A7N266  Main Board with Nvidia Gforce2MX intergrated graphics card. 256MB RAM with 32 MB shared for graphics.

I've been using Dapper and now upgraded to edgy. in dapper i could install composite extensions Xgl and all . Now in edgy after installing nvidia-legecy-glx 

i get the output 

Xlib:  extension "GLX" missing on display ":0.0" 

when I run the command

$ glxinfo | grep direct
 please help 

I wish to install Beryl 

also i faced a lack of perfomance in video play back when Xgl in Dapper was installed, because of which i uninstalled the same.

Hope my Ubuntu buddies will fish me out of these troubled waters.

---

### Post by pay on 2007-02-23
When you update to a new version the kernel gets reinstalled and the nvidia kernel module is still installed with the old kernel. You need to reinstall the nvidia drivers with the new kernel.

---

