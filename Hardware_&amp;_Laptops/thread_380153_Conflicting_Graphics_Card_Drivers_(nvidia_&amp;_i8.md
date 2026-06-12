---
title: "Conflicting Graphics Card Drivers (nvidia &amp; i810)"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by matburton on 2007-03-09
Hey,

I have a laptop with two graphics cards. One is a Intel i915 (think the GMA 900) on the motherboard and the other is a nvidia 6600 on an MXM slot. They're controlled by a switch on the front of the laptop so when I start my computer I can control if the nvidia card even has power (handy for battery, heat and noise!).

So! I made this little script to swap between the two

```
#!/bin/bash
rm /etc/X11/xorg.conf
lspci | grep "GeForce Go 6600"
if [ "$?" = "0" ];then
	echo "Swap in xorg.conf for nvidia"
        ln -s /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
else   
	echo "Swap in xorg.conf for i915"
	ln -s /etc/X11/xorg.conf.i915 /etc/X11/xorg.conf
fi 

```

and put it in init.d and linked to it in rc2.d so it ran before gdm. And that worked great!

Problem is that when I install the nvidia driver instead of the nv driver then opengl just doesn't work anymore on the i810 driver! glxgears gives me the age old > Xlib: extension "XFree86-DRI" missing on display ":0.0".

Anyway I can get round this or is it only possible to have one graphics driver at once :(

Thanks, Mat

---

### Post by matburton on 2007-03-14
Anyone?

It must be something simple?
A config file for GLX or something?
Something linking the hardware acceleration to the driver?

Any hints or pointers would be great!

---

### Post by Sparkster185 on 2007-05-22
Maybe you could try using Envy to set up the nvidia driver, and then save that xorg.conf file somewhere (xorg.conf.nvidia)?

Envy worked like a charm for me after I was having lots of headaches from nVidia driver install/configuration.

---

### Post by matburton on 2007-05-22
Sadly envy does the same. As soon as I install the nvidia driver (either apt-get or using envy) then my i810 using becomes useless.

The xorg.conf isn't wrong because I'm using two different ones, one for the i810 and one for the nvidia. The xorg.conf for the i810 works perfectly before the nvidia install but not after :(

Thanks for replying tho!

---

### Post by Enverex on 2007-05-22
You need to swap the OpenGL libraries at the same time (part of the drivers) as only one can be in that place at once. Not sure of the specific names or locations though. Check the package contents.

---

### Post by matburton on 2007-05-23
Ooooh!

That sounds promising :D
I'll have a look into that!

Thanks!

---

