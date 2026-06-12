---
title: "Ubuntu 7.10 &amp; Ati Xpress X1150 problems"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by waehuun on 2008-03-18
Hello!

I am new to Ubuntu and Linux, and what I have seen so far looks great! However, I would like to install drivers for my graphics card so that I can use diplay effects. So far I have tried several things and read a few hint pages but it seems like I can't get it working, so it would be very nice if you could give me some hints what might cause the problem.

My system: Ubuntu 7.10, installed on a MSI notebook with Ati X1150 graphics card (I think that this is basically the same as M200 or X1100)

What I have tried so far:

I downloaded the driver from the ati site and executed the .run file as root and followed the installation procedure. This installed the catalys control center, but the display effects still didn't work. 

So I read the guides at 
wiki.ubuntuusers.de/ATI-Grafikkarten/fglrx
wiki.ubuntuusers.de/ATI-Grafikkarten/radeon
wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide

I installed packages via sudo apt-get that various sites recommended:
xorg-driver-fglrx
linux-restricted-modules-generic

Then I changed xorg.conf and wrote "fglrx" instead of "ati" in the respective section and added the two sections concerning AIGLX and (as described in the guides) . After reboot, Ubuntu started in low-graphics mode ("graphics card not detected correctly"). Terminal command "fglrxinfo" returned:

Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

I also tried using the "radeon" driver, as described in the guide. High resolution is availible, visual effects are not.

I also tried reinstalling the driver by resetting xorg.conf and then using the restricted driver administration, and I got the same problems as I did when I installed fglrx manually.


I hope you can help me. If there is anything else I should write or try, please say so!

Thanks a lot!

---

### Post by nickdbliss on 2008-06-08
i would suggest uninstall the ATI driver and then reinstall using Restricted Hardware Drivers which can be found system>administration>Restricted hardware drivers.

---

