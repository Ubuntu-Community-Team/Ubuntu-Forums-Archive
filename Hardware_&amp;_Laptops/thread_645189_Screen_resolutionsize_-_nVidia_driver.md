---
title: "Screen resolution/size - nVidia driver"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by arctica2 on 2007-12-19
Alright, so I've spent 6 hours on this...time to seek some knowledgeable help. This is ridiculous.

I just installed the restricted nVidia driver for my Toshiba Satellite laptop (running a GeForce4 Go 420 gfx card) and everything works great -- except the operating system is confined to an 800x600 box on the screen surrounded by black. If I switch settings and try to get it to 1024x768 (what it should be), it just lets me scroll around the desktop...the black stays.

I've tried tons of things, but I need help now. Here's what nVidias xconfig wrote to my xorg.conf ... but nvidia-settings is misinterpreting my monitor's native resolution as 968x768, which might be part of the problem. I tried turning Ignore EDID on but maybe I did it wrong.

Suggestions?? :confused::confused:

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1024x768"
        Horizsync       31.5-48.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
        Gamma   1.0
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV17 [GeForce4 420 Go]"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 420 Go]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"
        Option          "UseDisplayDevice"      "DFP"
        Option          "IgnoreDisplayDevice"   "CRT"
        Option          "ExactModeTimingsDVI"   "True"
        Option          "AddARGBVisuals"        "True"
        Option          "NoLogo"        "True"
        SubSection "Display"
                Depth   24
                Virtual 1024    768
                Modes           "1024x768@60"   "800x600@60"    "800x600@56"   $
        EndSubSection
EndSection


Thanks sooo much!!!

---

### Post by dwanders on 2007-12-19
Sounds like your much more experienced than I with your description and all, but I had terrible times with my NVida card until I used this:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It was a "Make my ship go" kinda thing.

---

### Post by arctica2 on 2007-12-20
Thanks for the tip Dwanders but no cigar -- Envy didn't work.

However, after two more hours... I got it.

Solution: [http://www.edwiget.name/content/view/144/26/](http://www.edwiget.name/content/view/144/26/)

It works!!!!!!!!!!!!!

---

