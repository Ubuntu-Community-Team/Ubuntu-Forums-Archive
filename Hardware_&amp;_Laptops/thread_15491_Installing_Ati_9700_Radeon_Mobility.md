---
title: "Installing Ati 9700 Radeon Mobility"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by Jezze on 2005-02-15
Hi, I've searched the forum and found a bunch of semi-tutorials but all of them are crap because they are either too strange or they don't apply to my system in certain aspects... Can't someone give me an easy step by step explenation on how to install the newest drivers for my Mobility 9700 on MY system...

Some specs:
I have version 2.6.8.1-4-686 (uname -r) of the kernel and is currently using the drivers provided from the repository (fglxr-driver).

If anyone could do that it would save my day :)

---

### Post by snop on 2005-02-15
Hi,

I own a laptop that uses radeon 9700 mobility too (an Acer Travelmate 4001Wlmi). If you're using fglrx driver then you are already using ATI's driver.

If you don't get proper 3d accel. then perhaps it's because you must change the driver that XFree (or Xorg) uses. 

You must change the line

Driver "ati"
to
Driver "fglrx"

If you're using Ubuntu Warthy (the stable branch) you should edit /etc/X11/XF86Config-4. If you're using Hoary branch then you probably have x.org installed. Then the file to edit is /etc/X11/xorg.conf

In order to check if you driver's working properly you can issue the command "glxinfo" form a terminal and see if you can see the line "direct rendering: Yes" or something like that. (Hint: try "glxinfo | grep direct" to filter the output from glxinfo that could be quite long).

Hope this helps.

Bye

PD: I wrote all of this "by memory". I'm at work know and can't check if name files are the right ones but I guess so.

---

### Post by Jezze on 2005-02-15
I have the same computer as well.... yeah I have changed that information so that is not the problem... are you sure you have tried your 3d card to the fullest because if you try to run something that uses some of the more later 3d card features like shaders it doesnt render properly even though the Mobility 9700 should support it... (i know for a fact that it does on Windows)... this leeds me to believe that the fglxr drivers from  the repository is not working properly...

anyone who can explain to me what i should do?

---

### Post by snop on 2005-02-15
Hi,

> I have the same computer as well....

Good laptop, poor linux support (damn Acer).

> if you try to run something that uses some of the more later 3d card features like shaders

I've actually tried very few 3d apps. Among them are glxgears ;) and neverball ([http://icculus.org/neverball](http://icculus.org/neverball)). They both work fine. What does not work for you ?

If you are using Warthy (and, so, XFree) you are using an old driver (well, at least not the latest driver from ATI). That might be the problem.

Also, on Hoary, trying to use xcompmgr brings more garbage than dropshadows using mobility radeon 9700 ;)

Bye

SnOp

PD: I don't know if it's because I switched from ESD to dmix (I'm talking about sound mixing here, check [http://www.ubuntuforums.org/showthread.php?t=8882&highlight=dmix+esd](http://www.ubuntuforums.org/showthread.php?t=8882&highlight=dmix+esd)) but now Neverball is not as fluent as it was. I remember it worked fine on this computer. Anyway ATI drivers are still far from Nvidia.

---

### Post by Jezze on 2005-02-15
Hi, I've tried Neverballs (which was a very nice game) and it ran perfectly... I'm having problem with the Ogre3d demos ... [www.ogre3d.org](www.ogre3d.org)... you could try to download and compile and you will notice a few problem in some of the demos... I know that Ogre is an incredibly well programmed and should work because it does on windows so it is not a problem Ogre.

---

### Post by songochain on 2005-02-17
Hi! check [it](http://www.ubuntuforums.org/showthread.php?t=13843) May be it help u

---

### Post by snop on 2005-02-19
[QUOTE=Jezze]Hi, I've tried Neverballs (which was a very nice game) and it ran perfectly... I'm having problem with the Ogre3d demos ... [www.ogre3d.org](www.ogre3d.org)... you could try to download and compile and you will notice a few problem in some of the demos... I know that Ogre is an incredibly well programmed and should work because it does on windows so it is not a problem Ogre.[/QUOTE]
 Hi,

I've tried ogre demos. There are some demos that fail. But I don't know the reason. What kind of problems did you encounter ?

Can this be due to some Nvidia specific extensions or something ?

---

### Post by Jezze on 2005-02-21
I'm gonna research this further but it does seem like there are quite a few issues because there are so many things that doesnt work... I know that none of these demos have some Nvidia specific extensions because they should work on Ati cards just as well (they work perfectly on windows)... remember that these demos are perfect for researching bugs because they use many of the latest features...

The demos that didn't work properly was:

Fresnel - The fresnel effect (water effects) doesn't work
Grass - When you move the static geometry (the grass) is moving around which it should not...
Terrain - The culling doesn't work
SkeletalAnimation - The robot models doesn't even show up
TextureFX - Doesn't show anything

---

