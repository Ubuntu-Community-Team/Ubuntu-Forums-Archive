---
title: "Intel X.Org driver grows Xorg.0.log"
date: 2009-01-09
forum: Hardware
---

### Post by glaze on 2009-01-09
I'm using X4500HD chip that's integrated in motherboard DG45ID. OS is Kubuntu 8.10 64-bit. There's  sometimes quick horizontal distortion on the screen and Xorg.0.log grows many tens of MBs a day. It repeats the following lines:
> (II) intel(0): EDID vendor "GSM", prod id 20047
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   81.80  1024 1080 1192 1360  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) intel(0): Modeline "800x600"x75.0   48.91  800 840 920 1040  600 601 604 627 -hsync +vsync (47.0 kHz)
(II) intel(0): Modeline "640x480"x60.0   23.86  640 656 720 800  480 481 484 497 -hsync +vsync (29.8 kHz)
(II) intel(0): Modeline "1600x1200"x60.0  160.96  1600 1704 1880 2160  1200 1201 1204 1242 -hsync +vsync (74.5 kH

Has anyone else gotten similar problems and are they fixed in Kubuntu 9.04's X.Org Intel driver?

---

