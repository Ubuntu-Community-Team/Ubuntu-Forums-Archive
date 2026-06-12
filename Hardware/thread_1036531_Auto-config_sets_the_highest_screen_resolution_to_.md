---
title: "Auto-config sets the highest screen resolution to my CRT  monitor as 800x600"
date: 2009-01-10
forum: Hardware
---

### Post by nllittle on 2009-01-10
I have a Viewsonic 20G CRT monitor. Sure its old, but it cost me nothing and I want to continue using it.

[SIZE="3"]**The Problem**[/SIZE]
The auto-configure function for xorg will only allow me to set the highest resolution of my CRT monitor to 800x600 when it's top resolution is at least 1600x1280.

[SIZE="3"]**In the past**[/SIZE]
Previous versions of ubuntu and kubuntu one was allowed to manually set video card, monitor type and screen resolutions. For some reason this was discontinued. It appears that for those of us who are still using older and perfectly serviceable hardware are destined to hang and twist in the agony of xorg heck.

[SIZE="3"]**What I have Tried**[/SIZE]
I have tried using using Envyng using the proprietary drivers and setting xorg.conf configurations on the fly. 

[SIZE="3"]**Envyng failed**[/SIZE]
Using the method makes things even worse as it will only set the highest screen resolution to 640x480. this was even worse. The result of this project was to remove Envyng and the Nvidia drivers so that I could get at least the 800x600 resolution back.

[SIZE="3"]**What to do now**[/SIZE]
It appears that my only recourse is to manually configure xorg.conf to alow me to set the screen resolution to an appropriate level better than what I have now.

[SIZE="3"]**What I need**[/SIZE]
I need to know how to configure xorg.conf to allow me to set the screen resolution on my CRT monitor.

Thanks,

Neil

---

### Post by camionrouge on 2009-01-11
Hope this helps.

Take at look at the following link ( item 13 Problem involves wrong resolutions etc. ...)
[https://wiki.ubuntu.com/X/Troubleshooting](https://wiki.ubuntu.com/X/Troubleshooting)

This gives some useful troubleshooting procedures which should help.
Look at the X log file, usually at /var/log/Xorg.O.log
This will show you what the system detects and what modules it tries to load.
Good Luck

---

### Post by nllittle on 2009-04-10
Since I started this thread I have been studying on my CRT display issue now off and on now since the first of the year. I have finally come to the answer that caused the problem and a solution to fix it.

The culprit is plug and play (or as we used say back in the pentium I days "Prug n Pray"). I have learned more than I ever wanted to about xorg and EDID. In the end I did resolve my problem. I thought I would post what I found so another poor lost soul could benefit from my pain.

So here it is...

Modern monitors use something called EDID (Extended Display Identification Data). When computer systems start up devices are queried and monitors respond with some data. In the case of xorg this is where the device is configured.
```

(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: ACR  Model: d  Serial#: 2432756056
(II) NV(0): Year: 2009  Week: 10
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
(II) NV(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329

```

You can see where xorg found and configured the monitor

```

(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached

```

Here you can see in my case xorg did not find an EDID

```

(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff0004720d0058e90091
(II) NV(0): 	0a130103082f1e78eade95a3544c9926
(II) NV(0): 	0f5054bfef90a940714f81408bc09500
(II) NV(0): 	950f9040010121399030621a274068b0
(II) NV(0): 	3600da2811000019000000fd00384d1f
(II) NV(0): 	5411000a202020202020000000ff004c
(II) NV(0): 	41563043303531343031330a000000fc
(II) NV(0): 	0058323233570a202020202020200083

```

Later on in the process xorg even displays the EDID data in hex.

So why I asked myself (self? why?) why? I found specs on the ViewSonic 20G at Monitor World and after much intensive googling found the repair manual on some site (9 parts in RAR format). The short answer is my 20G did not have the ability to have a EDID.

This monitor was used on SUN SPARK hardware. In the back the output for the monitor are BNC (RBG) connectors. Connection to a computer is accomplished using an adapter cable that converts the output from BNC to 15 pin sub-D VGA connector.

On the VGA connector there are two pins for the DDC (Display Data Channel pins 5 - DDC-Return, 12 - DDC-Serial Data). Looking at the VGA connector and the pin-out from the repair manual I found that these connections/pins are missing from the cable.

Cant get there from here.

The next step is to see if I can manually configure Xorg.conf. I finally came up with this:

```

Section "Monitor"
    Identifier     "Monitor[0]"
    UseModes       "Modes[0]"
    VendorName     "VIEWSONIC"
    ModelName      "20G"
    DisplaySize     406 305
    HorizSync       30.0 &#8722; 82.0
    VertRefresh     50.0 &#8722; 90.0
    Option         "DPMS"
EndSection

Section "Modes"
    Identifier     "Modes[0]"
    Modeline       "1280x768" 125.82 1280 1368 1504 1824 768 769 772 809
    Modeline       "1024x768" 100.19 1024 1088 1200 1376 768 769 772 809
    Modeline       "1024x768" 88.50 1024 1088 1200 1376 768 769 772 804
    Modeline       "1024x768" 76.16 1024 1080 1192 1360 768 769 772 800
    Modeline       "1024x768" 64.11 1024 1080 1184 1344 768 769 772 795
    Modeline       "1280x600" 96.47 1280 1352 1488 1696 600 601 604 632
    Modeline       "1280x600" 84.54 1280 1344 1480 1680 600 601 604 629
    Modeline       "1280x600" 72.80 1280 1336 1472 1664 600 601 604 625
    Modeline       "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622
    Modeline       "1024x600" 77.36 1024 1080 1192 1360 600 601 604 632
    Modeline       "1024x600" 67.63 1024 1080 1184 1344 600 601 604 629
    Modeline       "1024x600" 58.10 1024 1072 1176 1328 600 601 604 625
    Modeline       "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622
    Modeline       "800x600" 60.07 800 840 928 1056 600 601 604 632
    Modeline       "800x600" 53.14 800 840 928 1056 600 601 604 629
    Modeline       "800x600" 45.50 800 840 920 1040 600 601 604 625
    Modeline       "800x600" 38.22 800 832 912 1024 600 601 604 622
    Modeline       "768x576" 55.94 768 816 896 1024 576 577 580 607
    Modeline       "768x576" 48.71 768 808 888 1008 576 577 580 604
    Modeline       "768x576" 41.66 768 800 880 992 576 577 580 600
    Modeline       "768x576" 34.96 768 792 872 976 576 577 580 597
    Modeline       "640x480" 37.89 640 672 736 832 480 481 484 506
    Modeline       "640x480" 33.48 640 672 736 832 480 481 484 503
    Modeline       "640x480" 28.56 640 664 728 816 480 481 484 500
    Modeline       "640x480" 23.86 640 656 720 800 480 481 484 497
    Modeline       "1152x864" 128.42 1152 1232 1360 1568 864 865 868 910
    Modeline       "1152x864" 112.36 1152 1224 1352 1552 864 865 868 905
    Modeline       "1152x864" 96.77 1152 1224 1344 1536 864 865 868 900
    Modeline       "1152x864" 81.62 1152 1216 1336 1520 864 865 868 895
    Modeline       "1024x768" 88.50 1024 1088 1200 1376 768 769 772 804
    Modeline       "1024x768" 76.16 1024 1080 1192 1360 768 769 772 800
    Modeline       "1024x768" 64.11 1024 1080 1184 1344 768 769 772 795
    Modeline       "1024x600" 67.63 1024 1080 1184 1344 600 601 604 629
    Modeline       "1024x600" 58.10 1024 1072 1176 1328 600 601 604 625
    Modeline       "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622
    Modeline       "800x600" 53.14 800 840 928 1056 600 601 604 629
    Modeline       "800x600" 45.50 800 840 920 1040 600 601 604 625
    Modeline       "800x600" 38.22 800 832 912 1024 600 601 604 622
    Modeline       "768x576" 48.71 768 808 888 1008 576 577 580 604
    Modeline       "768x576" 41.66 768 800 880 992 576 577 580 600
    Modeline       "768x576" 34.96 768 792 872 976 576 577 580 597
    Modeline       "640x480" 33.48 640 672 736 832 480 481 484 503
    Modeline       "640x480" 28.56 640 664 728 816 480 481 484 500
    Modeline       "640x480" 23.86 640 656 720 800 480 481 484 497
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       15
        Modes      "1152x864" "1024x768" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       16
        Modes      "1152x864" "1024x768" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       24
        Modes      "1152x864" "1024x768" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       32
        Modes      "1280x768" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       8
        Modes      "1152x864" "1024x768" "1024x600" "800x600" "768x576" "640x480"
    EndSubSection
EndSection

```

To get this Xorg.conf I cheated a little.
I have dual boot system that had a Winders XP/Fedora Core 3 load. There was code that configured Xorg.conf with these parameters. This system failed 9 months ago and I wont go into the steps I had to go to resurrect the hard drive and find this code. Its never easy.

Not being satisfied I decided in the end to find something better.  I spotted a cheap 22" Acer (X223Wbd) LCD monitor on NewEgg and bought it.

Thus ends my stroll in hardware Heck (the Dilbert bunny suit and spoon kind)  ;)

---

### Post by heyho on 2009-04-10
Congrats for finding out all that info - you remind me of me!

I usually can't rest before I've discovered what the problem is - but sorting my current edid/resolution problems are driving me insane.

Your post has made me think though - all of my problem displays are connected using a cheap ebay 3metre VGA cable - the one monitor that works has it's cable hard-wired internally hmmm - think I may check for a full compliment of pins...

---

### Post by heyho on 2009-04-25
I would just like to confirm that my problem was a vga cable with only 5 of the 15 pins connected.

Tried another generic lead with all pins connected, and bingo!  What a plank!  This might help someone else out!

---

