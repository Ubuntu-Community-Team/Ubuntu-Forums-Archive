---
title: "Will ATI Radeon HD 4200 work on Ubuntu?"
date: 2009-11-30
forum: Hardware
---

### Post by gamelux on 2009-11-30
Hi, I am a one year Ubuntu user and I need to change my two years Lenovo Thinkpad T61 because it's motherboard just died. As a replacement I am considering an HP Pavilion dv4-2041nr which comes with an ATI Radeon HD 4200, simply because it costs $100 less than the Intel/NVidia version. But I've heard of problems with ATI on Ubuntu/Linux. I don't play games, but I love Compiz, will it work? What you people heard/can comment about this?

---

### Post by gradinaruvasile on 2009-11-30
Well compiz should work. But beware, the drivers are not as stable as nvidias - i have seen many random X crashes on Ati cards.

So i recomment nvidia. The nvidia cards are far more stable than ati. From personal experience.
The NVS 140M (or something like it) card on thinkpads also supports VDPAU - meaning smooth HD movie playback with minimal CPU utilisation.

---

### Post by mr chip on 2009-11-30
Short version: yes, it does work, although from my experience there's more faffing around than with the Nvidia drivers.  Once they're working, they were stable until the system updated itself and broke a few things.

I installed 9.10 on an Asus M4A785-M, and to get hardware acceleration of video and desktop effects (i.e. Compiz, including those terrible wobbly window animations) I had to download the drivers from AMD/ATI's support pages.   The restricted binaries didn't work at all, and the default Radeon drivers were very basic.  Last night the system updated to the 2.6.31-15 kernel, and now the now the ATI binaries don't work and the system's reverted to the default Radeon drivers.

---

### Post by kronictokr on 2010-04-29
works flawlessly

[http://ubuntuforums.org/showthread.php?t=1464748](http://ubuntuforums.org/showthread.php?t=1464748)

---

### Post by djscribe on 2010-07-23
Hey Kronic, 

First and foremost, I thank you and all others that contribute to our evolution in overall computing within the Open Source community - you guys don't get thanked enough. 2nd, I'm a conservatively experienced user when it comes to Linux/Ubuntu, so I apologize if I've failed to follow anything to the T or anything else I may've overlooked. That having been said, please take my feedback with the best of intentions. 

Not sure where I went wrong, but the [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/lucid/main/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/lucid/main/) repositories were unreachable, even after tried pointing to dists/lucid/main/amd-64 in my case etc. Also the r600_rlc and 700 bins were not found either in the following command you cited:

sudo wget [http://people.freedesktop.org/~agd5f...e/R600_rlc.bin](http://people.freedesktop.org/~agd5f...e/R600_rlc.bin) [http://people.freedesktop.org/~agd5f...e/R700_rlc.bin](http://people.freedesktop.org/~agd5f...e/R700_rlc.bin) 

Get an ERROR 404: Not Found.

Was this fix ONLY for intel? Here's what I'm running just in case:

MoBo: M4A89GTD PRO USB3
OnBoard ATI Radeon HD4200
CPU: AMD Phenom II X6 1090T 3.2GHz
RAM: 4GB
640GB 64MBCache 6gb/s WD SATA Drive

Any info would be cool, as I'm still running on generic drivers, so no OpenGL.

---

### Post by kronictokr on 2010-07-23
im going to answer your question at this thread, to the best of my ability. as most of the info i can use to help is [there]("http://ubuntuforums.org/showthread.php?t=1463472"). <<<------

---

### Post by slooksterpsv on 2010-07-23
I have a Gateway NV53 and it has an ATI Radeon HD 4200 in it, and it works for games, for compiz, for everything (except flash, flash is not hardware accelerated on Linux (yet)). So all in all I'm very happy with the ATI Drivers in Linux, at least for the 4200. -- Also I'm running the 64-bit version of Ubuntu 10.04

---

### Post by kronictokr on 2010-07-23
> **gradinaruvasile said:**
> Well compiz should work. But beware, the drivers are not as stable as nvidias - i have seen many random X crashes on Ati cards.

So i recomment nvidia. The nvidia cards are far more stable than ati. From personal experience.
The NVS 140M (or something like it) card on thinkpads also supports VDPAU - meaning smooth HD movie playback with minimal CPU utilisation.


the ati driver and gfx are great i havent had a problem with them, either with repositories or custom, some drivers may work better with diferent gfx cards, make sure you use the proper one for you  machine.

---

### Post by natomasboy on 2011-05-21
> **kronictokr said:**
> the ati driver and gfx are great i havent had a problem with them, either with repositories or custom, some drivers may work better with diferent gfx cards, make sure you use the proper one for you  machine.

What about HD playback?  In linux have you gotten 1080p24 hd playback with say mplayer, mythtv, or xbmc?

---

