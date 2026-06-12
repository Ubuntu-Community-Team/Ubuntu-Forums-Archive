---
title: "Default Display settings incorrect"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2009-06-02
I just installed 9.04. I was running 8.04. When I was running 8.04, the default Htz was incorrect for the display. I had to run displayconfig-gtk in order to set it correctly. 

As I feared, that command has been removed from Ubuntu 9.04. There is not a selection for the correct (59Htz) refresh rate.

How can I get around this?

Thanx in advance!

---

### Post by lsutiger on 2009-06-02
UPDATE: I installed the nvidia drivers. When I go to display settings, it tells me to use the vendors tools which runs the Nvidia X Server Settings.

But the problem is the same. The refresh rate is not listed. It is detecting my monitor correctly. But the refresh rate is incorrect and the correct one is not listed.

Any body know how to get around this?

Attached is my xorg.conf

---

### Post by torchfire on 2009-06-06
I'm certainly no expert, lsutiger.  I'm having problems getting my resolution to 'stick' after an upgrade to Jaunty, and a new monitor.  But I looked at your file, compared it to mine, and I see some major differences. 

I've been looking here for help: 
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

Here are my "Monitor" and "Device" sections from xorg.conf:


```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD Hanns.G HG281"
    HorizSync       24.0 - 80.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1920x1200@60" 193.160 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
    ModeLine       "1600x1200@60" 162.000 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1400x1050@60" 122.610 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1280x1024@75" 135.000 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x1024@60" 108.000 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.860 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1280x960@60" 102.100 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1152x864@75" 108.000 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1024x768@75" 78.800 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.000 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.000 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "800x600@75" 49.500 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@72" 50.000 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@60" 40.000 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "800x600@56" 36.000 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "640x480@75" 31.500 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@72" 31.500 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@60" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
    Option         "DPMS"
    Option         "PreferredMode" "1920x1200@60"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection

Section "Screen"

# Removed Option "metamodes" "1400x1050 +0+0; 1280x1024@75 +0+0; 1280x960@60 +0+0; 1152x864@75 +0+0; 1280x1024@60 +0+0; 1024x768@60 +0+0; 1280x960@75 +0+0; #1024x768@70 +0+0; 1400x1050@60 +0+0; 1024x768@75 +0+0; 832x624@75 +0+0; 800x600@60 +0+0; 800x600@75 +0+0; 800x600@72 +0+0; 800x600@56 +0+0; 640x480@75 +0+0; #640x480@72 +0+0; 640x480@60 +0+0"
# Removed Option "metamodes" "1400x1050 +0+0; 1920x1200 +0+0; 1920x1200@60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1200@60 +0+0; 1400x1050 +0+0; 1920x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Perhaps you need a modeline.  There is a command that will generate one for you.  I'm trying to find it now.  I'll let you know when I do. 
I hope this helps a bit to guide you. 
Torch

edited to add:  the instructions for generating a modeline are on the page I linked to at the beginning of the post, under Adding Undetected Resolutions.

---

### Post by torchfire on 2009-06-06
Here's another link: 

[https://wiki.ubuntu.com/X/Troubleshooting/Resolution?highlight=(modeline)]("https://wiki.ubuntu.com/X/Troubleshooting/Resolution?highlight=(modeline)")

---

### Post by lsutiger on 2009-06-08
Thanx for the help...the resolution was defaulting to the incorrect res...when I fixed that, the correct refresh rate showed, but that setting does not stick. So now I am i your boat....

---

### Post by torchfire on 2009-06-09
Hi lsutiger, 
My answer is at the bottom of this post...

[http://ubuntuforums.org/showthread.php?t=1179083](http://ubuntuforums.org/showthread.php?t=1179083)

When I reviewed my log file, /var/log/Xorg.0.log, it indicated many errors regarding many of the resolutions in my list.  I ignored those, actually, because none of them were regarding My resolution.

(Eventually, I'll go in and remove all the unnecessary lines from my xorg.conf file, to get rid of those errors.)

Below that, there was an error shown on the 'meta' modes.  I had 1920x1200@60 in the list, along with 1920x1200 +0+0.  The second was correct.  The one with @60 was incorrect.  I removed it, and put 1920x1200 +0+0 in the first spot, and viola.  Reboot, and all is well. 

Here is the bad line from my xorg.conf file, Section "Screen"...

Option "metamodes" "1920x1200@60 +0+0; 1400x1050 +0+0; 1920x1200 +0+0"

Here's what I replaced it with...

Option "metamodes" "1920x1200 +0+0; 1400x1050 +0+0"

Hope that helps!!  Good luck.  Let me know if these help you. 

Torch

---

