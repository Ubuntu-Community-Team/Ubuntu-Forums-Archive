---
title: "Ubuntu Resolutions and why do no new OS's work?"
date: 2012-06-11
forum: Hardware
---

### Post by Ov3rTheTop on 2012-06-11
Hey everyone,
I have just recently gotten into Linux and Ubuntu and so I wanted to try them out on my computer... unfortunately it appears that Ubuntu 10.4 and lower, and Linux Mint 9 and lower are the only ones that work. This is upsetting however I am more than willing to look past this if I can get them to work at full resolution on my 1600 x 900 monitor.. I have a dual monitor setup as well the second monitor being 1378 x 768. Ubuntu 10.4 only supported up to 1280 x 760 or something like that. I am running off of my graphics card and feel that that might have had something to do with it however I did not want to do a full install just in case it didn't work. So two questions here... can I get some form of modification where I can run it al full resolution on my dual screens.. aand does anyone know why these older versions are the only ones that work...
Thanks a heap everyone :D
my system specs:
AMD FX-6100 3.3GHz
Asus M5A78L-M LX Motherboard
8GB dual channel DDR3 memory
Nvidia GTX 550 ti

extra info: I built the PC myself and that was only last month.

---

### Post by juanbuntu on 2012-07-07
I have a system similar to yours and I also experienced problems. The only version I could install was 10.10, but strangely, the i386 version. Once I had the system fully installed I upgraded to 11.04, then to 11.10, and things went real well until I tried 12.04, which so far is just not working. Maybe AMD CPUs ane nVidia chipset are the problem.

---

### Post by Bucky Ball on 2012-07-07
If you are not running a hard drive install (you are using 'Try Ubuntu' from a Live boot) you wouldn't have any drivers installed for your video card (except the default open-source one) and that is possibly the reason you are not getting your resolution. 

You won't be able to answer this without a hard drive install (or a persistent install to a medium that is capable of installing and saving drivers and apps, which a Live boot is not).

---

### Post by Karlchen on 2012-07-07
Hello, Ov3rTheTop.
> it appears that Ubuntu 10.4 and lower, and Linux Mint 9 and lower are the only ones that work. This *might* be true for your machine. But this does definitely not apply to all machines.
I am running

[LIST]
[*]Linux Mint 12, 32-bit, on a Zotac computer (1.72 GB of RAM, 256 MB of video RAM, 2 dual cores atom processors)
[*]Linux Mint 13, 32-bit, Cinnamon Desktop, on a Dell Latitude E6400 notebook (dual core intel processor, 4 GB of RAM, 64 MB of internal video RAM)
[*]Ubuntu 12.04, 64-bit, on a 4 year old Medion desktop machine ( 4 GB of RAM, 256 MB of video RAM, Intel quadcore processor)
[/LIST]


>  to work at full resolution on my 1600 x 900 monitor.. I have a dual monitor setup as well the second monitor being 1378 x 768. The Dell notebook has got an internal resolution of 1280x800 and the external monitor has got 1600x1050. Works fine using Ubuntu 10.04 as well as Linux Mint 13.

>  Ubuntu 10.4 only supported up to 1280 x 760 or something like that. More something like that, see above.

About your graphics card: I assume you will get much  better results once you have installed the genuine Nvidia graphics drivers. Yet, this can only be done after installing Ubuntu on your harddisk. This has been explained also in the post above.

Unless you have put components into your self-built machine for which Ubuntu cannot offer appropriate drivers yet, more recent versions of Ubuntu should run better than older versions, because versions which are older than your hardware can hardly bring along all needed drivers for this hardware.

Kind regards,
Karl

---

### Post by efflandt on 2012-07-08
Video is most likely to be in its native resolution if your monitor is connected with DVI or HDMI.  VGA tends to use a list of default video modes.

Install CD or install iso on USB uses nouveau open source drivers that may not be optimum.  For example nouveau defaults to something like 1024x768 my 1080p HDTV.  
But once installed, nvidia drivers default to 1920x1080.

I found that once I had 11.10 installed with nvidia drivers, I had to use **nomodeset** kernel boot parameter, or my screen would just say "no signal".

12.04 is just the opposite.  I had to use **nomodeset** during install (hit any key during 1st purple screen with symbols at bottom), but did not need any parameters once it was installed.

And a side note is that with 8 GB RAM you would likely want to use 64-bit Linux versions because 32-bit typically cannot access more than about 3 GB RAM, although, Ubuntu does have optional 32-bit pae kernels that can.

---

### Post by Bucky Ball on 2012-07-08
> **efflandt said:**
> 

And a side note is that with 8 GB RAM you would likely want to use 64-bit Linux versions because 32-bit typically cannot access more than about 3 GB RAM, although, Ubuntu does have optional 32-bit pae kernels that can.

And another side note; as long as OP has a 64bit processor (which I presume the AMD FX-6100 3.3GHz is). Processor is what it's worked out on, not amount of RAM (although you probably know this). 

If OP has a 32bit processor, don't attempt a 64bit install. It won't install. If they have a 64bit processor, I wouldn't install anything but 64bit system, unless there is some obscure, or otherwise, reason to do so. ;)

Not flaming. Just mentioning. ;)

---

