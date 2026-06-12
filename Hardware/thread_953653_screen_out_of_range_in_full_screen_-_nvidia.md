---
title: "screen out of range in full screen - nvidia"
date: 2008-10-20
forum: Hardware
---

### Post by trawler on 2008-10-20
I'm using a separate X configuration. An LG1960TR 19" lcd screen (connected through vga) and an lcd tv connected through the dvi.

I ran into a weird problem whenever I try to run a game in cedega in full screen on the 19" screen (main screen). The game seems to load, but the screen goes blank with a message: **Out Of Range 81.3@65**.

From the LG manual:
Horizontal Freq. Analog : 30 - 83 kHz (Automatic)
Vertical Freq. 56 - 75 Hz (Automatic)

So I configured it in my xorg.conf file:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L1960TR"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

```

The Modelines above are taken from the automatic configuration in kde. I used it to configure the screen according to specific model. As you can see, the vsync and hsync values are identical to the manufacturer's manual, and still I can't play anything in full screen.

I tried using wine to run the same game, and got the same result. So i doubt it has anything to do with cedega configuration itself.

Anybody knows how I can solve this?

---

### Post by Joeb454 on 2008-10-20
Please do not create duplicate threads on the same subject

[http://ubuntuforums.org/showthread.php?t=953649](http://ubuntuforums.org/showthread.php?t=953649)

---

