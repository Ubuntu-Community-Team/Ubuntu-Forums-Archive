---
title: "T61P logon screen not full size (1680x1050)"
date: 2008-08-07
forum: Hardware
---

### Post by tertius on 2008-08-07
My Logon screen seems too small.  The prompt to enter my username is to the bottom right (not in the corner but def. to the bottom right).

Here are the sections of my xorg.conf which apply.

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1680 1050
        Depth       24
        Modes      "1680x1050@60" "800x600@60" "1024x768@60" "800x600@56" "1280x960@60" "640x480@60" "1280x1024@60" "1400x1050@60"
    EndSubSection
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1680x1050"
    HorizSync       31.5 - 65.5
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection



In the monitor section it only goes up to 1400x1050 (I think the problem might be here, not sure)

Thanks for any help,
T

---

### Post by tertius on 2008-08-08
bump :(

---

