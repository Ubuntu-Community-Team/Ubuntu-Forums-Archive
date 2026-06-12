---
title: "How do I alter screen refresh rates and add extra resolution options?"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by Sleeper Service on 2005-08-01
I've just got hold of a nice 21" monitor - a Hitachi CM802ET.  Also, I'm working with a fresh install of Hoary 5.04, done with this graphics card (NVIDIA Corporation NV11 [GeForce2 MX/MX 400]) and monitor.

I can alter the screen resolution up to 1280x1024, but that gives me a refresh rate of only 60Hz, which is pretty flickery.

The next option down is 1024x768.  With the more healthy refresh rate of 75Hz, this feels very comfortable, but I'm not really getting the full benefit of my larger screen with this relatively standard setting.

I've tried putting an option for 1152x864 into my /etc/X11/xorg.conf file, but it just seems to get ignored (and 1024x768 is still the maximum setting).

Is it possible to add extra "in-between" screen resolutions to Ubuntu?  Is it possible to manually mess around with the refresh rates?  Is my graphics card likely to be getting in the way at all, or imposing any limitations?

Cheers :)

---

### Post by heimo on 2005-08-01
Couple links:
[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by frodon on 2005-08-01
The question is  ... does your screen support more than 60Hz with 1280*1024 resolution ?
Before doing anything, have a look to your sreen specification to know which resolution you can reach. After that, put the good (specified in the screen specification) hsinc and vsync parameters in xorg.conf file will allow you to select all the possible resolutions of your screen.
If you want some help editing your xorg.conf file just post it here : ```
sudo gedit /etc/X11/xorg.conf
```
EDIT : you're right varunus, where is my mind !!!

---

### Post by varunus on 2005-08-01
There's a typo above, it should be
```
sudo gedit /etc/X11/xorg.conf
```

---

