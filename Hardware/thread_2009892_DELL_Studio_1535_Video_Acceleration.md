---
title: "DELL Studio 1535 Video Acceleration"
date: 2012-06-25
forum: Hardware
---

### Post by divxclub on 2012-06-25
Hi guys, What an amazing system Ubuntu is and I remember about 5 years ago I had a huge problem with all sorts of drivers but no more it usually runs everything. I came up with a little problem here. According to many people video chip in my laptop should be 100% supported with 2D/3D acceleration, yet I can't get it to work. I have DELL Studio 1535 with Intel 965GM Graphics. Can anyone point me to the right directions on how to make this thing work properly ? I am on latest 12.04 Distro.

Thank you !

---

### Post by divxclub on 2012-07-23
Any 1 ?

---

### Post by Redblade20XX on 2012-07-23
Can you please post the output of:
```
glxinfo | grep render
```If direct render is disabled, please use this code:
```
sudo apt-get update
``````
sudo apt-get install xserver-xorg-video-intel
```Can you also post the content of this file?
```
/etc/X11/xorg.conf
```

- Red

---

### Post by divxclub on 2012-07-26
Here it is.


xakep@studio15:~$ glxinfo | grep render
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
xakep@studio15:~$ 

After updating apt-get


xakep@studio15:~$ sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
xakep@studio15:~$ 


and in X11 I do not see xorg.conf file. Beside few folders in root of X11 I see only one config file. Xwrapper.config

See screenshot


P.S.

After installing mesa-utils here is what I got and still no xorg.conf

xakep@studio15:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965GM x86/MMX/SSE2
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
xakep@studio15:~$ 


Thanks !

---

