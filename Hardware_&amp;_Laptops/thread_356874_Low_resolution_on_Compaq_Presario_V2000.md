---
title: "Low resolution on Compaq Presario V2000"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by Bosonator on 2007-02-08
EDIT: Never mind. I realized I could, y'know, *try* my first idea to see if it worked. It did! Gotta love backed-up files!

Hello,

Last night I tested connecting an external monitor to my laptop. I was able to get it to work, but somewhere in the process my laptop (built-in) monitor's maximum resolution was set to 640X480. I recently (successfully) installed the fglrx drivers for my ATI Radeon xpress 220M graphics card (using this process [http://www.ubuntuforums.org/showthread.php?t=321766&highlight=radeon)](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=radeon)). My question is, would that process have backed up an appropriate xorg configuration that I can just reinstate? The output of "ls /etc/X11/xorg*" is 

```

xorg.conf    xorg.conf_20070107-bkup  xorg.conf.fglrx-0
xorg.conf.1  xorg.conf_20070207-bkup  xorg.conf.original-0
xorg.conf.2  xorg.conf_bkup070131

```

If it's not that easy, could someone look at my xorg.conf file below and suggest how to fix it? Thanks muchly!
```

Section "Monitor"
  Identifier "Generic Monitor"
  option "DPMS"
EndSection

Section "Monitor"
  identifier "aticonfig-Monitor[0]"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

Section "Device"
  Identifier "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
  Driver "ati"
  BusID "PCI:1:5:0"
EndSection

Section "Device"
  identifier "aticonfig-Device[0]"
  boardname "ati"
  busid "PCI:1:5:0"
  driver "fglrx"
  screen 0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    Depth 1
    Modes "1280x768"
  EndSubSection
  SubSection "Display"
    Depth 4
    Modes "1280x768"
  EndSubSection
  SubSection "Display"
    Depth 8
    Modes "1280x768"
  EndSubSection
  SubSection "Display"
    Depth 15
    Modes "1280x768"
  EndSubSection
  SubSection "Display"
    Depth 16
    Modes "1280x768"
  EndSubSection
  SubSection "Display"
    Depth 24
    Modes "1280x768"
  EndSubSection
EndSection

Section "Screen"
  Identifier "aticonfig-Screen[0]"
  Device "aticonfig-Device[0]"
  Monitor "aticonfig-Monitor[0]"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 640 480
    modes "640x480@60"
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  option "Composite" "Disable"
EndSection

Section "device" #
  identifier "device1"
  boardname "ati"
  busid "PCI:1:5:0"
  driver "fglrx"
  screen 1
EndSection
Section "screen" #
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "640x480@60" "800x600@56" "800x600@60" "1024x768@60" "1152x768@54" "1280x854"
  EndSubSection
EndSection
Section "monitor" #
  identifier "monitor1"
  vendorname "Generic"
  modelname "1024x768 @ 60 Hz"
  HorizSync 31.5-48.5
  VertRefresh 50-70
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection


```

---

