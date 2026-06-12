---
title: "TV losing signal HDMI (screen goes all funny until input is changed a few times)"
date: 2013-12-22
forum: Hardware
---

### Post by fishleg2 on 2013-12-22
Completely new to Ubuntu I've just barely learnt how to open the  terminal but I've got as far as looking at the modelines use xrandr and  viewing the xorg.conf, anyway...

My problem is on boot the TV fires up I get a purple screen the launch  screen then just as the desktop fires up the screen goes crackers as if  I'm tuned in to an old analogue tv channel with no signal just aload of  noise. Now if I switch channel then come back a few times the desktop  fires up perfect and I can use it all day. Its driving me bonkers I used  to have a windows pc connected the TV absolutely fine, so is it  something with Ubuntu that I've missed?

So on boot I get purple boot up screen then static but if I switch  inputs on the tv and back a few times it shows up perfect. I've also  noticed sometimes when it goes to the lock screen it goes to static and I  gotta do the same again. If I use xrandr and manually change the  resolution a few times through a remote vnc connection the TV will some  times kick out of it and display the desktop fine with out having to  change inputs.

I'll post up the xrandr results later but it looks like its picking up  the edid fine as it lists all the modes you'd expect from the TV.

Intel I3 Ivy Bridge HM77 chipset built in gpu. Fresh install no random drivers just what Ubuntu came with.

Its LG 42" screen its from 2008 so its only got HDMI 1.2 if that would effect anything. I've tried a different port through a splitter changed the pixel ration 1:1 16:9 etc still does it...

Any help or advice please its driving bonkers... ><.

>  xrandr
HDMI1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 1000mm x 550mm
   1920x1080      59.9*+   60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1920x1080i     60.1     50.0     60.0  
   1600x1200      60.0  
   1400x1050      59.9  
   1280x1024      60.0  
   1360x768       59.8  
   1280x768       60.4  
   1280x720       59.7     60.0     50.0     59.9  
   1440x576i      50.1  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     60.0     59.9     59.9  
   720x400        70.1  


> TV Service Manual
HDMI Input (PC)
No Resolution H-freq(kHz) V-freq.(Hz) Pixel clock(MHz) Proposed
1. 720*400 31.468 70.08 28.32
2. 640*480 31.469 59.94 25.17 VESA
3 800*600 37.879 60.31 40.00 VESA
4. 832*624 49.725 74.55 57.283 Macintosh 
5 1024*768 56.476 70.00 75.00 VESA
6 1280*768 47.693 59.99 80.125 WXGA
7 1360*768 47.649 59.94 84.625 WXGA
8 1366*768 47.649 59.94 84.625 WXGA
9 1280*1024 63.595 60.0 108.875 SXGA
10 1400*1050 65.160 60.0 122.50 SXGA
11 1600*1200 74.077 60.0 130.375 UXGA
12 1920*1080 66.647 59.988 138.625 WUXGA 


> Xorg log
[   791.491] (II) intel(0): EDID vendor "GSM", prod id 40124
[   791.491] (II) intel(0): Using hsync ranges from config file
[   791.491] (II) intel(0): Using vrefresh ranges from config file
[   791.491] (II) intel(0): Printing DDC gathered Modelines:
[   791.491] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz eP)
[   791.491] (II) intel(0): Modeline "1360x768"x0.0   84.75  1360 1432 1568 1776  768 771 776 798 -hsync +vsync (47.7 kHz e)
[   791.491] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1344 1472 1664  720 723 728 748 +hsync +vsync (44.6 kHz e)
[   791.491] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   791.491] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   791.491] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   791.491] (II) intel(0): Modeline "1280x768"x0.0   80.14  1280 1344 1472 1664  768 771 778 798 -hsync -vsync (48.2 kHz e)
[   791.491] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   791.491] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   791.491] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   791.491] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   791.491] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   791.491] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   791.491] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   791.491] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   791.491] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   791.491] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   791.491] (II) intel(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz e)
[   791.491] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[   791.491] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   791.491] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   791.491] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   791.491] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   791.491] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[   791.491] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   791.491] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[   791.491] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[   791.492] (II) intel(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   791.492] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   791.492] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   791.517] (II) intel(0): switch to mode 1920x1080@60.0 on pipe 0 using HDMI1, position (0, 0), rotation normal

---

