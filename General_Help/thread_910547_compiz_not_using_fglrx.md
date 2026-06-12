---
title: "compiz not using fglrx"
date: 2008-09-04
forum: General Help
---

### Post by JakeK23 on 2008-09-04
I'm using Mint 5, but I figured since its build on ubuntu and this forum gets more hits that I could get help here.  I installed Mint two days ago and got everything up-to-date and such but noticed that desktop cube wasn't working (my favorite Compiz feature).  I ran compiz-check and heres what I got:

> Gathering information about your system...

Distribution: Linux Mint
Desktop environment: GNOME
Graphics chip: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
Driver in use: fglrx
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [ OK ]
Checking for non power of two support... [ OK ]
Checking for composite extension... [ OK ]
Checking for FBConfig... [ OK ]
Checking for hardware/setup problems... [FAIL]

There has been (at least) one error detected with your setup:
Error: Fglrx driver not properly installed, you are using the Mesa driver. 

I don't understand why the hardware failed when I am using fglrx.  And it says I'm using Mesa drivers?  I am confused.

---

### Post by luxorvan on 2008-09-04
[QUOTE=JakeK23;5727930]I'm using Mint 5, but I figured since its build on ubuntu and this forum gets more hits that I could get help here.  I installed Mint two days ago and got everything up-to-date and such but noticed that desktop cube wasn't working (my favorite Compiz feature).  I ran compiz-check and heres what I got:



I don't understand why the hardware failed when I am using fglrx.  And it says I'm using Mesa drivers?  I am confused.

When I do a first install I always start with a terminal and install xserver-xgl before enabling and installing the restricted driver.

It is easy fix and you may need to reconfigure the driver first for the best results because adding xgl now will require you to reconfig the driver or your display will be extremely slow!
Have you done any of this yet? These three steps remain faithful to me time and time again I hope this helps! Although I'm not sure for the command to reconfigure the ati graphics driver. And this will work for ati-offbrand cards as well! And make sure to run one command at a time!

sudo apt-get update

sudo apt-get install xserver-xgl

sudo apt-get install xorg-driver-fglrx

---

### Post by JakeK23 on 2008-09-05
Nope, haven't tried any of that yet.  I'll do it and report back.

---

### Post by JakeK23 on 2008-09-05
Whoa you weren't kidding.  My display is going really really slow.  Yeah, I am not sure how to configure them either, as I am pretty new to all this stuff.  :(  anyways, I re-ran compiz-check and here are the results.

> Gathering information about your system...

 Distribution:          Linux Mint 
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
 Driver in use:         fglrx
 Rendering method:      Xgl

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Fglrx driver not properly installed, you are using the Mesa driver. 

---

