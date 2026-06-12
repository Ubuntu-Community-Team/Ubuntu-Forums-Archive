---
title: "black screen with sound with nvidia drivers"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by spiderworm on 2005-04-10
EDIT: THIS HAS BEEN RESOLVED.  SCROLL DOWN TO FIND RESOLUTION.

Hello,

I posted this on nvnews.net and don't seem to be getting much of a response, so I thought I'd bring it up here.  From the nvnews.net posting:

___________________________________________________________________________________________________
Hi all,

I'm running Linux/WinXP on a HP Pavilion zv5430us laptop that I recently purchased. The video card is an Nvidia GForce4 440 Go 64MB. I'm running Ubuntu (Debian based) 5.04. I have installed Nvidia drivers on Linux many times in the past and have never had a problem like this. Basically, when it starts gdm or any x session, the screen is black but the x session responds to keyboard and mouse input (I can tell because of the pretty sounds Ubuntu comes with when starting gdm, gnome, and opening and closing applications). I think that the system thinks everything is dandy with the x session even though I can't ses any of it. I've done a lot of googling and a lot of hacking the xorg.conf file to no avail. I've installed the drivers using the precompiled packages on the Ubuntu servers, as well as downloading the drivers from the NVidia site and building the package, all to no avail. Same black screen problem every time. Has anybody else run into this issue, and is there a known resolution?

I've posted the x server output when using the nvidia driver at the link below. I didn't see anything that would be related to my problem in it, but maybe you're smarter than I am
[http://www.tellim.com/linux_nvidia_problem/Xorg.0.log](http://www.tellim.com/linux_nvidia_problem/Xorg.0.log)

Here is the xorg.conf:
[http://www.tellim.com/linux_nvidia_problem/nvidia-xorg.conf](http://www.tellim.com/linux_nvidia_problem/nvidia-xorg.conf)

uname -a output:
Linux VENOM 2.6.10-5-amd64-generic #1 Tue Apr 5 12:21:57 UTC 2005 x86_64 GNU/Linux

Please let me konw if you have any ideas, or if you need any more information. Thanx!

spiderworm2

---

### Post by edubarr on 2005-04-10
I had a similar problem when I configured my kernel to run with frame buffer. I got the black screen with sounds exactly like you did. All I had to do was boot in recovery mode and reconfigure gdm to work with frame buffer. Try running 'dpkg-reconfigure gdm' and answer the questions. 

Hope this helps. :-)

---

### Post by spiderworm on 2005-04-10
Hmm I tried that but actually when I do dpkg-reconfigure gdm it doesn't give me any questions, no options to select, just says:

 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.      [ ok ]

Am I doing something wrong???

spiderworm

---

### Post by spiderworm on 2005-04-11
any other ideas on this?  please?

---

### Post by BairroAlto on 2005-04-12
Does the display work fine if you have: Driver "nv" instead of Driver "nvidia" in your xorg.conf file?

---

### Post by spiderworm on 2005-04-12
Yes, the 'nv' driver works just fine, no 3D accel of course.  This is only when using the 'nvidia' driver.

spiderworm

---

### Post by vnbuddy2002 on 2005-04-12
Make sure your monitor support the specified resolution with the specified frequency. If the frequency is too high for the monitor, it will return a black screen.

What are the resolutions that supported by your monitor? and also the frequency. LCD  s usually support up to 75hz,60hz for laptop screens, 85hz for crt monitors ( for the highest resolution ).

---

### Post by spiderworm on 2005-04-12
Ok after finding and spending some time at [http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/) I figured out that I need to have the nvidia load with the following parameters: 

NVreg_SoftEDIDs=0 NVreg_Mobile=0

The way I did this was to edit /etc/modules and change the line that just read:

nvidia

to:

nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=0

It's that easy!  Yay!

Please note THIS IS A FIX FOR NVIDIA DRIVERS ON HP Pavilion zv5430us LAPTOPS AND APPARENTLY MANY OTHER LAPTOPS IN THE zv5400 SERIES!!!

---

