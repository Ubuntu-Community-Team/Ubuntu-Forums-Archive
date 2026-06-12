---
title: "Screen resolution can't be set to maximum"
date: 2008-10-21
forum: Hardware
---

### Post by Radiotic on 2008-10-21
I've got a Asus laptop dual boot (Windows XP, Ubuntu) system going. Under XP, my display settings are 1280x800, 32bit color at 60 hertz. The max I can seem to squeeze out of Ubuntu is 1024x768. I'm not sure about the color, but it's not at maximum. I can clearly see gradient lines on the standard heron wallpaper, but the strange thing is, when I capture a screenshot of it and view it on another computer, it looks perfect - gradients are smooth and delicious.

When I set up the screen resolution, I choose 1200x800, but even then the maximum available for selection is 1024x768. I guess I can edit my xorg.conf file, but I'm kinda nervous about doing something wrong. Which section, monitor or screen, is the one to edit (snippet below)? Or should I just grin and bear it?

I'm not particularly interested in getting the names of things correct, if it is generic that's ok.

I also noticed that if I boot up using the Ubuntu live CD, I get better resolution (1200x800). So I looked at that xorg.conf file which just had a bunch of stuff like "configured monitor", "configured screen". I copied that over to the one one the HDD install and restarted X, but that just screwed things back up. 

Cheers. 


```
Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1024x768"
    Horizsync    31.5-48.0
    Vertrefresh    56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Modes        "1024x768@60"    "800x600@60"    "800x600@56"    "640x480@60"
    EndSubSection
EndSection
```

---

