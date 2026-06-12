---
title: "Stuck configuring external LCD &amp; Intel 915GM"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by jslag on 2007-05-07
Continuing to have trouble getting my Acer AL2051W LCD driven properly by my laptop, an HP DV1000 with an Intel 915GM "chipset" and a D-Sub out. 

I've figured out how to get 915resolution to make a 1680x1050 mode available (the monitor's native resolution), and found that when I add a modeline for that resolution in xorg.conf, it's possible to select that mode from the resolution switcher. 

However, every modeline I've tried has been driving the monitor at odd frequencies, which results in the desktop stretching beyond the visible area. By way of comparison, when this monitor is hooked up to a machine with a Radeon 7200 in it, there's no need to set a modeline and the monitor indicates that it's being driven at 65 kHz / 60Hz, and the display works perfectly. 

When I try the modeline from the Radeon's Xorg.0.log, the monitor claims it's being driven at 70 kHz, 64Hz: Modeline "1680x1050"  147.14  1680 1784 1968 2256  1050 1051 1054 1087 -HSync +Vsync

I tried downloading CVT ([http://www.uruk.org/~erich/projects/cvt/](http://www.uruk.org/~erich/projects/cvt/)) as it's supposed to be better at generating modelines for CRTs, however its 60Hz modeline exhibits the same problem, and the monitor indicates 69 khz / 63 Hz: Modeline "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

A bunch of experimentation got me some reasonable looking numbers from the monitor's onboard display - 65 kHz / 59 Hz - but the display area problem remained: Modeline "1680x1050"  135.00  1680 1784 1960 2240  1050 1053 1059 1087  -HSync +Vsync

With the latter modeline, I tried xvidtune to see if it would be able to shrink the display so that it fit on the screen, but any modification produced the following error: "Sorry: you have requested a mode-line that is not possible, or not supported by your hardware configuration"

At a bit of a loss - any insights out there? Seems pretty clear that this is an X / i810 problem, since XP running on the same laptop is perfectly capable of driving the monitor reasonably.

---

### Post by outlawer on 2007-05-14
Hello i have same problem ( 7.04) monitor LG 226WT driver intel notebook HP nc6220

---

### Post by jslag on 2007-05-18
In case a snapshot of the problem is helpful, here it is with both sides of the screen MIA:
[[IMG]http://farm1.static.flickr.com/192/503776201_c09f18b104_b.jpg[/IMG]]("http://www.flickr.com/photos/18474854@N00/503776201/")

---

### Post by teaker1s on 2007-05-18
```
sudo apt-get install 915resolution
```

resolution modify tool for Intel graphic chipset
915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient.
There is no risk of permanent modification of the BIOS.
This also means that 915resolution must be run every time the
computer boots inorder for it's changes to take effect.
If you want to automatically set the resolution on each boot
and before X is launched, see /usr/share/doc/915resolution/README.Debian
for information about configuring the provided initscript.

Web site: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

---

### Post by jslag on 2007-05-18
> **teaker1s said:**
> ```
sudo apt-get install 915resolution
```


Thanks, but if you read the original post, I've already got 915resolution installed, and x.org is set to the desired 1680x1050 resolution. The problem is that the intel driver keeps insisting on weird frequencies.

---

### Post by teaker1s on 2007-05-18
if your using feisty look at this
[http://ubuntuforums.org/showthread.php?t=420185]("http://ubuntuforums.org/showthread.php?t=420185")

---

### Post by jslag on 2007-05-19
> **teaker1s said:**
> if your using feisty look at this
[http://ubuntuforums.org/showthread.php?t=420185]("http://ubuntuforums.org/showthread.php?t=420185")

I am running feisty. 

I gave the intel driver a try originally ( [http://ubuntuforums.org/showthread.php?t=417140](http://ubuntuforums.org/showthread.php?t=417140) ) without any luck, but I guess it's worth one more crack before giving up on linux and this laptop & monitor.

---

### Post by juunitaki on 2007-11-11
```
root@uf:~# xrandr --newmode  "1680x1050_60" 147.14  1680 1784 1968 2256  1050 1051 1054 1087
root@uf:~# xrandr --output VGA-0 --addmode VGA-0 "1680x1050_60"
root@uf:~# xrandr --output VGA-0 --mode "1680x1050_60"
```

---

