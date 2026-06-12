---
title: "ATI x600 problem!!!"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by naverone on 2008-01-01
I have an HP zd8000 Laptop with a 256mb ATI Mobility x600 graphics card in it running Ubuntu Gutsy.  The laptop works, I have the resolution working well.  But I'm having some issues with the graphics card.

when i run glxgears I am only getting about 220 fps which I understand should be about 10x that.

when I run fglrxinfo I still get the following.
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```

I have installed the ati drivers and my xorg.conf file does have fglrx as the driver, And whenever I go into the Restricted Drivers and try to enable "ATI accelerated graphics driver" it pops up asking if I want to enable driver or cancel.  Of course I enable driver but then the window just greys out and all I can do is click close.

Does anyone know what I'm doing wrong here?

---

### Post by empthollow on 2008-01-01
i've had lots of problems installing ati cards.  have you checked to see if the kernel module is loaded?
```
lsmod | grep fglrx
```
also how did you install the driver the first time.
to check to see if you have 3d enabled run this command
```
fgl_glxgears
```
this is glxgears but only works with direct rendering.  if it fails it will give you an error with some sometimes useful and sometimes useless info but i found it more useful than glxgears with ati cards.

---

### Post by naverone on 2008-01-03
I installed the drivers using the proprietary driver installer, then I had some issues and downloaded an xorg.conf from this site that got it working.

Here are the results of the commands you suggested
```

$ lsmod | grep fglrx
fglrx          656352   0
agpgart    35016     2    fglrx,intel_agp

$ fgl_glxgears
Using GLX_SGIX_pbuffer
Segmentation fault (core dumped)

```

Not sure what most of that means, I'm relatively new to linux, I've only dabbled in the past.

Again, any help that anyone can offer would be amazing!

---

### Post by Jaxilian on 2008-01-03
I followed this guide for my ATi x600 mobility and got it working good. I got about 2500-3400 FPS in glxgears after that.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by naverone on 2008-01-04
That is actually the guide I used to install it and I'm still having the same problems.  Should I simply re-install and start over and follow that guide without having tried other solutions prior?

---

### Post by empthollow on 2008-01-04
i would try that, i have used that guide to get mine working as well, i used "the ubuntu way".

---

### Post by rufius on 2008-01-04
I'd recommend the restricted drivers route anymore when dealing with that kinda stuff. The guides are good but at some level its better to trust automagical way, at least in my experience with the fglrx stuff.

Hope that helps :)

---

### Post by the_blur on 2008-01-13
Be careful, there is a good chance that your laptop will experience the shutdown problem when rendering with the proprietary drivers once you get them working.

My ZD8000 will crap out by suddenly shutting down when I run any kind of 3d app on it, including glx gears , I'm still unaware ofa fix for this issue.

---

