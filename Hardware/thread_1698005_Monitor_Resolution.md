---
title: "Monitor Resolution"
date: 2011-03-01
forum: Hardware
---

### Post by jda8818 on 2011-03-01
Hello all:

I just pieced together a ten year old Asus P4T motherboard (1.7gHz P4, 1GB) and successfully installed 10.04.2.  I'm using an equally old ATI Rage 128 PRO video card in conjunction with a beautifully old Viewsonic P815 21' monitor.  On a windows box with an Nvidia GeForce FX 5700 this monitor runs all day long at 1920x1440 and 75 Hz.

The problem with the new install is that the monitor resolution maxes out at 800x600 and 60 Hz.

Thanks to Jmate at [http://ubuntuforums.org/showthread.php?t=1651904](http://ubuntuforums.org/showthread.php?t=1651904)  apparently my monitor is not detected, so a default lo-res monitor and video card are substituted instead.

So I guess I need to create an /etc/x11/xorg.conf file that lists the P815 monitor and its properties as well as the (UNCLAIMED) ATI Rage PF/PRO AGP 4x TMDS card.

Other than that which was provided by jmate in his final post, does anyone know of a template for such a file?  Mainly I need to know how to describe the capabilities of the P815 monitor.  I'm also unsure as to which sections of such a file would be necessary.  

also, if it does not work and i boot into a blank screen, what is my strategy to get back to square one?

as always, thanks in advance for any and all comments or suggestions ...

JA

---

### Post by jda8818 on 2011-03-04
Hello All:

Thank you for your overwhelming response!

After several attempts at conjuring up an xorg.conf file from scratch (without success), I noticed that /etc/X11/ contains a file named "xorg.conf.failsafe" which when renamed "xorg.conf" doesn't break the system at reboot.

So it was possible to incrementally edit this file to define my old (but beautiful) Viewsonic P815 21' monitor.  I'm so happy I'm going to post the first successful xorg.conf:
```
Section "Device"
    Identifier    "ATI Rage PRO 128"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "ViewsonicP815"
    HorizSync       30-115
    VertRefresh     50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "ViewsonicP815"
    Device        "ATI Rage PRO 128"
EndSection

```Defaults into 1280x1024 @ 86 Hz.

I won't close this thread yet; there may be other old fools out there (like me) that might need more information.  There are as yet lots of modes to accurately define ...

Thanks again to everyone,

JA

---

### Post by fjgaude on 2011-03-04
I don't offer any help other than to say I thought, since 9.10, Ubuntu no longer uses xorg.conf files. The whole system is such that I've not spent the time to understand how to manually setup for video drivers and monitors. I do think that all that is in the kernels since 10.04, but I could be wrong.

Maybe someone else can really help with your issues.

---

### Post by jda8818 on 2011-03-04
fjgaude

10.04.2: You're right, xorg.conf does not exist in /etc/X11/ any more on a new, clean install, only the file xorg.conf.failsafe which I modified and named /etc/X1/xorg.conf. 

As far as I can tell, new installations have other means to establish video hardware parameters.  I have no idea what they are.  So apparently xorg.conf can be implemented, if necessary, to deal with unusual or old hardware.  Which is a good thing in this case particularly, since the Viewsonic P818 is a spectacular monitor.

So no, xorg.conf does not exist anymore, and yes, it does, if you need it ...

JA

---

### Post by FoAlBo on 2011-03-04
I'm working on the same problem. Check here:
[http://ubuntuforums.org/showthread.php?t=1661168&highlight=S3+UniChrome+Pro+integrated+graphics](http://ubuntuforums.org/showthread.php?t=1661168&highlight=S3+UniChrome+Pro+integrated+graphics)

The answer in the above post might do the trick:

[http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

---

### Post by FoAlBo on 2011-03-04
found this too may help [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

