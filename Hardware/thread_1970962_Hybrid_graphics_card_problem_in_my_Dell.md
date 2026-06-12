---
title: "Hybrid graphics card problem in my Dell"
date: 2012-05-01
forum: Hardware
---

### Post by masterserver on 2012-05-01
Hi to every one. 

My problem is that I think that in my laptop none of the two graphic cards work. 

I have a Dell Inspiron with

OS: Ubuntu 12.04
CPU: N5110 with an i7 2630QM processor @ 2GHz
Graphic Card: NVidia GeForce GT 525M 1GB
Motherboard: Intel HM67 Express Chipset Family LPC Controller 

One thing that i did while i was trying to uninstall the NVIDIA driver is that i run this command "sudo rmmod nvidia". I don't know if this changed something in my system because the command didn't gave me feedback. 

When i run this command "glxinfo |grep renderer" i get this result

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

I think that this shouldn't be like that. It should say something about the VGA that is using currently. So i assume that something is going wrong in my system. (also some graphic features doesn't work like the windows snapping and the transparency)

I tried to install bumblebee using this tutorial [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
but when i installed it and rebooted my machine the Unity bar on the left and the bar on the top on the Desktop had disappeared (but the snapping feature was working) so I uninstalled it and now i am again in the same situation.

Just to know when I run "lsmod" there is a line with 

nvidia              12319264  0 

How can i make my system to use the nvidia card?

I hope that i gave a good explanation of my problem. 

Thanks in advance

---

### Post by lazifyre on 2012-05-02
have the same problem with the same configuration, though haven't tried bumblebee because didn't actually have time for trying it out

---

### Post by masterserver on 2012-05-04
I found the solution to my problem. I installed Compiz Confit Settings Manager with the following commands 

sudo apt-get install -y compiz compizconfig-settings-manager && sudo apt-get install -y compiz-fusion-plugins-extra

and then I installed bumblebee. The reason why o couldn't see my Unity bar on the left and on top is because bumblebee disables the Unity plugin. So after having installed bumblebee you open the Compiz Confit Settings Manager and you just enable the Unity plugin by ticking the appropriate icon and then all should be working perfectly.

---

