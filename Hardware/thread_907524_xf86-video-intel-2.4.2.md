---
title: "xf86-video-intel-2.4.2"
date: 2008-09-01
forum: Hardware
---

### Post by sdmike on 2008-09-01
I looked around and I can't find how to install this driver for my on board graphics.

I got it straight off of the [www.intellinuxgraphics.org/](www.intellinuxgraphics.org/) site.

There isn't an install/read me file or directions on the site.

So how should I install this driver?

---

### Post by sdmike on 2008-09-02
Bump!

---

### Post by sdmike on 2008-09-02
Bump!!!!

---

### Post by sdmike on 2008-09-08
Bump!!!!!!!!!

---

### Post by sbergman27 on 2008-09-12
Intrepid Alpha 5 has version 2.4.1.  I've compiled 2.4.2 for it, but not for earlier versions of Ubuntu.

You will need at least xorg-dev, and probably some other stuff. So:

sudo apt-get install xorg-dev

Then in the top level directory of the driver source:

./configure
make
sudo make install

Configure will probably complain about some missing stuff, and it may not be obvious what packages are needed:

sudo apt-get install apt-file
apt-file update
apt-file search file-name-that-configure-complains-about

This will tell you what package you need to install to get the file.

Once you get it compiled and installed, the driver name in /etc/X11/xorg.conf will be "intel". For example:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Can you give some more detail about your situation?  Version of Ubuntu?  Motherboard chipset?  I've just been through all this with my new G43/X4500 motherboard.

-Steve

---

### Post by lbharti on 2008-09-29
Is there any performance improvement using this driver? I am compiling it right now.

It compiled alright, but after installing, it did not work. I uninstalled the original driver with the hope that it will work, but to no avail. I had to install the old driver back. How do I enable the new driver after installation? 

Also my system is Hardy heron on an X61 with intel 965GM graphics card.

---

### Post by mclaren191 on 2008-11-27
I just installed 8.10 on my system with an Intel G43/X4500 and am trying to get the driver to update and running into trouble with the make command:

/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from i810.h:64,
                 from i810_accel.c:55:
/usr/include/GL/glxint.h:95: error: expected specifier-qualifier-list before ‘GLboolean’
make[3]: *** [i810_accel.lo] Error 1
make[3]: Leaving directory `/home/seann/xf86-video-intel-2.4.2/src'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/seann/xf86-video-intel-2.4.2/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/seann/xf86-video-intel-2.4.2/src'
make: *** [install-recursive] Error 1


this is what i see in my terminal after make has finished and when i check xorg.conf I am still using defaults, any help would be appreciated.

---

### Post by iRPM on 2008-12-12
```
 sudo apt-get install mesa-common-dev
```

fix`es da error

after installation still nothing good:

> sergejus@sergejus-laptop:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
sergejus@sergejus-laptop:~$ glxinfo | grep render
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
OpenGL renderer string: Mesa DRI Intel(R) 965GM 20061102 x86/MMX/SSE2


> sergejus@sergejus-laptop:~$ glxgears 
617 frames in 5.1 seconds = 120.000 FPS
660 frames in 5.0 seconds = 131.666 FPS
760 frames in 5.1 seconds = 149.471 FPS
580 frames in 5.1 seconds = 113.717 FPS






----
P.S. If it help`s you can always say Thanks ;)

---

### Post by Zapadlo on 2008-12-12
Anyone with patience willing to help out? I'm also trying to install video drivers, but really lost. Running 8.10, I have 4500mhd intel. I have downloaded drivers from: "http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=1cfe769c74d1a3a392bf1aaaf5c2dcc8273daf66" not really sure if thats the right ones, but thats the closet thing thing I found to making sense. Running autogen.sh does nothing. Tips, comments, guidelines will be most appreciated, forgive the primitave nature of the question.

---

