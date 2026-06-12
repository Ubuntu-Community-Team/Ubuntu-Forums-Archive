---
title: "Horrible performance ubuntu 9.04"
date: 2009-08-14
forum: Hardware
---

### Post by jagrock on 2009-08-14
Hi every there,

I got some problems here, because the performance in my laptop Acer Aspire 4535 is to bad and the transfers between a usb storage and the laptop are very very slow. The CPU usage its always over 30% and when i see youtube videos this increase to 70%, i dont now whats going on.

The features of my laptop are:

Turion 64 x2
3 GB ddr2 @ 667 mhz
ATI HD3200 graphics
320 gb sata 5400 rpm

Im using ubuntu 9.04, ati drivers installed and ahci activated. I have this issue even using amd64 version.

I have a desktop with similar features, but the performace is much better.

Thanks for your help.

---

### Post by galileolajara on 2009-08-14
As far I know, this might be Xserver problem. Are you sure that ATI drivers are loaded by X? Try looking xorg.conf ATI setups from google

---

### Post by tomasrey88 on 2009-08-14
I have been having "issues" with Ubuntu with my laptops, as well. I have 4 laptops and none of them seem to work right with Ubuntu nor Xubuntu. My Dell Inspiron 8500's screen flickers. My Toshiba will not run. My Sony and my other Dell has jumpy video. None of my 3 wireless cards work in any of them, either. 

However, Ubuntu works like a dream for my desktops. 

Install Puppy Linux on your laptops. It will run fine. Puppy's graphics are grainy and the number of software that comes with it is spartan, but it works fine for portable devices like laptops. Wireless setup is a breeze.

---

### Post by jagrock on 2009-08-14
> **galileolajara said:**
> As far I know, this might be Xserver problem. Are you sure that ATI drivers are loaded by X? Try looking xorg.conf ATI setups from google

This is it:

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "fglrx"
EndSection

---

### Post by jerrrys on 2009-08-14
i run 8.04LTS on both laptop and desktop without issues, may want to give 804 a try...

---

### Post by jagrock on 2009-08-14
> **jerrrys said:**
> i run 8.04LTS on both laptop and desktop without issues, may want to give 804 a try...

Yeah, i was thinking about that...

I go to try with that version, but i am perplex because the bad performace that i got...

I steel loking for solution.

---

### Post by jagrock on 2009-08-14
Ok, i installed hardy amd64, and every thing its going well except for the audio and wifi drivers.

---

### Post by edwardtilbury on 2009-08-14
man that sucks,

I'm lucky that my Toshiba P105-S9339 has an nvidia gpu.. I will try to avoid ATI from now on since I hear bad stuff about their cards and linux.

Try loading it up and logging off, then VNC-ing via LAN to your laptop and see how it runs? maybe this can help you determine if it's GPU related..

---

### Post by edwardtilbury on 2009-08-16
try disabling the cube and switch to wall mode.. keep you other effects.. I like wall better now anyways.. more practical.


Mine was actually going super slow too on 9.04... compiz is 16%... then I disabled the cube.. compiz but left wall mode and effects on, compiz is now at 3% and it's going super fast, even with virtualbox running an xp guest.


I also put new wallpapers on all three of my walls, I'm really liking this wall mode..

---

