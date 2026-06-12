---
title: "Resolution wont go above 800x600"
date: 2008-08-18
forum: General Help
---

### Post by HpZ on 2008-08-18
Just got Ubuntu running on my brand new laptop (got it yesterday due to problems with my desktop PC). And It's dual booting with Vista. My problem is that the screen resolution wont go above 800x600. I go to System>Preferences>Screen Resolution and the only options are 800x600 and 640x480. Vista runs perfectly and looks very high res so I know my laptop can handle it.

---

### Post by Dejavou42 on 2008-08-18
what video card do you have?

if you have a nvidia or ati video card installed, the easiest thing to do is open application manager and download Envy. It will auto configure your graphics card and allow you more resolution options.

---

### Post by linuxisfree on 2008-08-18
> **HpZ said:**
> Just got Ubuntu running on my brand new laptop (got it yesterday due to problems with my desktop PC). And It's dual booting with Vista. My problem is that the screen resolution wont go above 800x600. I go to System>Preferences>Screen Resolution and the only options are 800x600 and 640x480. Vista runs perfectly and looks very high res so I know my laptop can handle it.

Just asking, what is your video card? Maybe knowing what it is, we might be able to help.

EDIT: Oops, Dejavou42 beat me to it.

EDIT: You can try to Install 915resolution (it's in the repositories), i've installed it in mine, and now my res is 1280 x 800.

---

### Post by HpZ on 2008-08-18
It's a NVIDIA GeForce 7000M / nForce 610m

---

### Post by Dejavou42 on 2008-08-18
download and install envy from the application manager and install the nividia drivers using automatic detection.

---

### Post by HpZ on 2008-08-18
I've heard bad things about Ubuntu installing drivers. Also, i searched envy in synaptic package manager but which one is it?

---

### Post by lackoblacko on 2008-08-18
type
"sudo apt-get install envyng-gtk"
in terminal

or go to 
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
for more instructions

---

### Post by aman.agx on 2008-08-18
I had the same problem with my NVIDIA drivers. The restricted drivers from NVIDIA site installed fine the system also ran fine. But when I rebooted it it didnt work. but a small change solved the problem.

What I would suggest is install the restricted drivers. for this follow below steps.
1. Go to NVIDIA website. 
2. download latest linux drivers for your graphics card and configuration. (64 bit or 386 architecture). The instuction to run these are there on the site.
3. you might need to install some development libraries when you run the driver file.

4. After you have installed drivers open /etc/default/linux-restricted-modules-common

it should look like this 

Code:
```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```Code

make it DISABLED_MODULES="nv"

And reboot.


This should work. Hope it helps. 

Regards
Aman

---

### Post by aman.agx on 2008-08-18
you have to download the correct drivers from the NVIDIA website. There are different drivers for Ubuntu x86 architecture and 64-bit architechture

---

