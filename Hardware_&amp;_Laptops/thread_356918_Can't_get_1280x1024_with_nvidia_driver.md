---
title: "Can't get 1280x1024 with nvidia driver"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by jabster on 2007-02-08
Hi.

I am having a problem with my video card.

I can get 1280x1024 with the nv driver, but nvidia limits me to 1024x768.

Is there some way to get 1280x1024 with the nvidia driver?

xorg.conf & monitor info follows.

Thanks,
John


xorg.conf
```
Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "Device"
  identifier "NVIDIA Corporation NV40? [Unknown nVidia Card]"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nv"
  screen 0
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  modelname "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV40? [Unknown nVidia Card]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1280x960@60" "1280x854" "1152x768@54" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection
```

Monitor info:
Cybervision ds69
1024x768 @ 70 Hz, 56.48 Hz, 70.07 Hz
1024x768 @ 75 Hz, 60.24 Hz, 74.93 Hz
1024x768 @ 75 Hz, 60.03 Hz, 75.03 Hz
1280x1024 @ 60 Hz, 63.98 Hz, 60.00 Hz

---

### Post by taurus on 2007-02-08
Did you install nvidia driver and how did you install it?  Right now, you are using nv.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by jabster on 2007-02-09
> **taurus said:**
> Did you install nvidia driver and how did you install it?  Right now, you are using nv.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

taurus,

Sorry, perhaps I should have been a bit more clear.

I have the nvidia driver installed just fine (yes, the xorg.conf shown is for nv because that is what I'm using right now, as that is the only way I can get 1280x1024). I can switch over to the nvidia driver, and it does indeed work: nvidia splash screen, glxgears, quake3, penguin racer, etc, all work. (And I can switch back to nv again with no problem.) Installing the nvidia driver and using it are (unfortunately) not the problem.

I can not get the resolution above 1024x768 when using the nvidia driver.

Running kubuntu edgy btw, fully updated.

Any ideas?

thanks,
john

---

### Post by taurus on 2007-02-09
How did you install the nVidia driver and what is the model of your card anyway?

---

### Post by jabster on 2007-02-09
I installed the nvidia driver using Adept, then ran that command in a konsole (something like nividia-gl enable) and restarted X.

-john

---

### Post by taurus on 2007-02-09
Try the link in #2 and see if the latest nVidia driver works or not.

---

### Post by jabster on 2007-02-09
> **taurus said:**
> Try the link in #2 and see if the latest nVidia driver works or not.

will do.

FX 6800-128M btw. AGP.

-john

---

### Post by jabster on 2007-02-10
> **taurus said:**
> Try the link in #2 and see if the latest nVidia driver works or not.

Well, that was no good.
Did this (using the stable version):
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And no I get failed to load modules nvidia & glx, no drivers available. Fatal server error: no screens found.

So now I don't have X at all.

So what now?

-john

p.s. I also rebooted the machine after envy finished.

p.p.s. Correction: It's a 6200 card.

---

### Post by jabster on 2007-02-10
well, jusy for S-n-G, I ran envy again.

A bit better. Maybe.

Now I get the spiffy nvidia splash screen, and the system comes to a complete halt. It never leaves that screen, and I can't even switch to a terminal (ctrl-alt-f1 for example). I need to do a hard reboot.

Checking the Xorg log, shows:
(WW) NVIDIA(0): Wait (0,6,0x8000,0x00000520,0x00000520)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX

-john

---

### Post by jabster on 2007-02-16
well,

I using envy, I uninstalled the nvidia driver, then installed it again.

now it works. got 1280x1024 too.

-john

---

