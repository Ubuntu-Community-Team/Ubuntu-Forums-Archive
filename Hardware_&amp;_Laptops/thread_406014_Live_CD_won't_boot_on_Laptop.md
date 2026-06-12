---
title: "Live CD won't boot on Laptop"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by Stonecougar on 2007-04-10
Okay, so I snagged the 7.04 beta and burned it to a live CD. Tried to install it on my snazzy little laptop. When it goes to start the live demo mode before installation, well, it won't. It says that my X server isn't configured, and that it will shut down. Tried the same thing with a full release version of 6.10. No dice. So I'm left sitting here wondering what the heck is going on here. Laptop is a brand new Alienware M5550 with the following specs:

1.63 ghz Intel Core 2 Duo
1 GB RAM
ATI X1400 Radeon Mobility
1280x400 native res screen

I'm somewhat annoyed... I love Ubuntu and have been using it on my desktop for a while now. I'd kind of like to at least have a dual boot on this laptop, but that doesn't seem to be particularly feasible. Anyone know what the problem could be? I know ATI cards don't play nicely with any flavor of Linux, but it's what I have to work with...

---

### Post by blazercist on 2007-04-10
Have we tried safe graphics mode? I know its obvious but hey who knows.

---

### Post by Stonecougar on 2007-04-10
We have indeed, to the same unfortunate result.

---

### Post by haden9 on 2007-06-09
Yes am having the same issue as well, except that I went ahead and upgrade from Ubuntu 6.10 to 7.04, after loading it displayed that the x server failed to start. I have tried running numerous times sudp dkpg-reconfigure xserver-xorg without any luck. Any ideas or is it just that the my vc is not supported.


My system specs (M5550):

CPU: Intel 1.83GHz
Mem: 1GB DDR2
VC: ATI Mobility Radeon x1400
Monitor Brand & Resolution: AU Optronics Corporation 1280(W) × 768(H) pixels

Please help me as well in finding a solution. Thanks!

:popcorn:

---

### Post by jynyl on 2007-06-10
The problem here is black screen when booting off the live cd (Kubuntu 7.04)
My solution was based on this page ...
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103945/comments/1](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103945/comments/1)

After booting up and getting the black screen, press ctrl-alt-F1, then
$ sudo dpkg-reconfigure -phigh xserver-xorg
  select the vesa driver and only 640x480 screen resolution
$ sudo killall kdm
$ sudo kdm
  This gives the live CD desktop.  Choose gdm instead of kdm if you are using gnome (Ubuntu).
From the live install, choose the install icon to install your system.

Hardware here is HP laptop nc8430, intel duo core 2, ATI mobility radeon X1600, 1680x1050.

HTH

Peter

---

### Post by haden9 on 2007-06-11
Thank you for the useful information jynyl, but sadly it didnt work for me with the Ubuntu 7.04. Good thing though it help me achieve native resolution in 6.10 lol, one solution to another problem I had so I thank you none the less :) now I gotta deal with compiz lol. Anyways I will try out installations of Ubuntu 7.04 and if I succeed I will let everyone know.

Thanks,

Haden9

---

### Post by jynyl on 2007-06-13
> **haden9 said:**
>  sadly it didnt work for me with the Ubuntu 7.04.

It will help if you can describe more clearly what did happen with your system.  What symptoms? Any error messages?

---

### Post by haden9 on 2007-06-16
> **jynyl said:**
> It will help if you can describe more clearly what did happen with your system.  What symptoms? Any error messages?

The issue I am still having is that I cant install ubuntu 7.04 with an ati x1400 video card I just get a blank screen. Thanks :)

---

### Post by haden9 on 2007-06-16
I know what you mean now jynyl, the situation is this, whenever I try:

$ sudo dpkg-reconfigure -phigh xserver-xorg

vesa
resolution 640x480

I only get this, 

(EE) VESA(0): No matching modes
(EE) Screens(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I still havent been able to install feisty on my m5550 :(

---

### Post by bone43 on 2007-06-16
> **haden9 said:**
> I know what you mean now jynyl, the situation is this, whenever I try:

$ sudo dpkg-reconfigure -phigh xserver-xorg

vesa
resolution 640x480

I only get this, 

(EE) VESA(0): No matching modes
(EE) Screens(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I still havent been able to install feisty on my m5550 :(


 Follow this guide works great Ive done it with my X1400..

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Have Fun :D

Opps heres a link to the alternate insatll CD..

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by haden9 on 2007-06-17
thanks a lot bone43!!!! I was able now to load on my m5550 feisty 7.04 without any issues!!!!!!

Plus i got beryl running i love the watery effects and the cube w00t!!!!!111:popcorn:

---

