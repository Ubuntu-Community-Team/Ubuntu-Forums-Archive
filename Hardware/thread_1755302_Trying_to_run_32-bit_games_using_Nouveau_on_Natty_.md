---
title: "Trying to run 32-bit games using Nouveau on Natty x64"
date: 2011-05-11
forum: Hardware
---

### Post by UrbenLegend on 2011-05-11
I've been playing around with the Nouveau 3D driver from the xorg-edgers ppa. So far I can get 64-bit games like Trine and Sauerbraten to work, although they're a bit slow. I can't seem to load 32-bit games like Doom or Prey however. It keeps saying:
```
Loading GL driver '(default)' through SDL
WARNING: SDL_GL_LoadLibrary (null) failed: Failed loading libGL.so.1
```

I have a very strong feeling it is because I don't have the 32-bit versions of Nouveau and Mesa. Where can I get these 32 bit compatibility libraries? I've tried downloading the i386 versions from the xorg-edgers ppa, but dpkg keeps saying its the wrong architecture when I try to install them.

---

### Post by Zokul on 2011-06-27
I can't believe this, really, ..but I might have a solution for your error message.

(The part I can't believe, is why this worked / that this worked.)

But, here's what happened for me..

I installed the Nouveau driver on my Ubuntu 11.04 install (using the additional drivers tool). Then I tried to run the glxgears program to test my system's graphics capability. (I had to do a sudo apt-get install mesa-utils to be able to get the glxgears program.) 

But when I tried to run the glxgears program, I was getting an error message about libGL.so.1, so I went searching for more info on this issue. That's when I found your post in the forums here.

But then I thought maybe the issue was related to my having tried all of the Nvidia driver options first (I couldn't get anything whatsoever as far as drivers from Nvidia to work on Natty, and I tried every which way, but I don't care about that now since Nouveau is working alright).

So, I decided to try to install the very newest Nouveau driver manually that I could and see if that might kill the error.

But, I didn't even need to install Nouveau (again), because in the course of trying to do that, I had done the following two commands:

sudo apt-get install libsdl1.2-dev

sudo apt-get install xorg-dev libdrm-dev git git-core libtool mesa-common-dev automake autoconf 

After doing that, 

I found that (for some reason I don't quite get), glxgears is now working (with my current Nouveau driver) with no libGL.so.1 error being shown.

I had a suspicion something might have changed between installing mesa-common-dev and xorg-dev, that's why I had checked if it was working, so it was probably because of one of those being installed that it's working now, but I don't know for sure.

(So all I'm sure about is that in some way installing any or all of those packages shown in those two apt-get lines above might have done it (knocked out the error), as weird as that might be.)

(Maybe it was just installing the libsdl1.2-dev or mesa-common-dev package that did it, not sure though. I'm just gonna keep all of the stuff from those two apt-get lines installed, since I think none of it is of any concern.)

This is the page where I had found those commands originally (  [http://nouveau.freedesktop.org/wiki/DebianTips](http://nouveau.freedesktop.org/wiki/DebianTips)    )

Cheers and good luck!

---

