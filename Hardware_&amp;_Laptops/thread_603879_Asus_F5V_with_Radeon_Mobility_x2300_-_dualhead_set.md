---
title: "Asus F5V with Radeon Mobility x2300 - dualhead setup is a lot of fun"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by cronfy on 2007-11-05
Hello,

I am using Ubuntu 7.10 (installed from CD).

I am trying to get dualhead configuration working for Asus F5V laptop with Mobility  Radeon X2300. I have to use fglrx, because neither radeon, nor radeonhd drivers do not handle this video card. 

Dualhead does not work as desired though.  Here is my unsuccessfull experience:

1. First I was trying to follow ATI Big Desktop topic in this forum: [http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)

But if I use aticonfig tool, fglrx makes my screen black when it meets PairModes option. The system is still alive, I may turn it off blindly (Power button + Enter), but it becomes unusable: even console (Alt-F1) does not show anything.

If I edit xorg.conf manually as described there:

```

Option "DesktopSetup"  "horizontal" #Enable Big Desktop
Option "Mode2"         "1280x1024" #Resolution for second monitor
Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 
Option "VRefresh2" "60" #This sets the refresh rate of the secondary display.

```

I have second monitor working on GDM login screen and I even may move mouse cursor on it ;-) But after Nautilus is loaded, second screen becomes blank and I can not move mouse cross desktop borders on my first monitor.


2. Nest step was Big Desktop setup from this wiki: [http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

```
sudo aticonfig --dtop=horizontal --overlay-on=1
```

But I get blank screen in GDM and cloned output in Nautilus.




3. Final step was aticonfig --initial=dual-head

At least it is working as designed ;-) I have two independent desktops now, one on the right side of another. But

 - why I may drag icons between desktops, but not windows (Nautilus)? I have to launch application on that desktop that I want to use it and there is no ability to move it to another desktop. 
 - big desktop is more preferred solution, still looking for working configuration.




Did anyone have luck to make big desktop working with fglrx + ati mobility radeon + gnome? What am I doing wrong?

Thanks in advance.

---

### Post by narcisgarcia on 2008-06-03
I don't know if this will help you, but you can look these results with Ubuntu 8.04 version:

[https://wiki.ubuntu.com/LaptopTestingTeam/AsusF5V-AP097C](https://wiki.ubuntu.com/LaptopTestingTeam/AsusF5V-AP097C)

---

