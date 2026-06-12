---
title: "Third Monitor on Docking-Station not working"
date: 2021-05-19
forum: Hardware
---

### Post by tziegler on 2021-05-19
Hi,
I have a Dell XPS15 9500 Laptop with the Dell WD19TBS | 180W Dock.
I'm using Dual Boot and in Bios, on Booting and in Windows all three external Monitors are working fine.
Only in Ubuntu I can only active two monitors although Ubuntu detected all three.

```

uname -r
5.8.0-53-generic

```

```

xrandr --current
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 16384 x 16384
eDP-1 connected (normal left inverted right x axis y axis)
   1920x1200     59.95 +  59.88    47.96  
   1920x1080     60.01    59.97    59.96    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-1-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 597mm x 336mm
   1920x1080    144.00*+ 120.00   119.88   119.98    60.00    60.00    50.00    59.94  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1366x768      59.79  
   1280x800      59.81  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DP-1-2 connected (normal left inverted right x axis y axis)
   1920x1080    144.00 + 120.00   119.88   119.98    60.00    60.00    50.00    59.94  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1366x768      59.79  
   1280x800      59.81  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DP-1-3 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   1920x1080    144.00*+ 120.00   119.88   119.98    60.00    60.00    50.00    59.94  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1366x768      59.79  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  

```

when activating the monitor, I get this log entries:

```

May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Allocate new frame buffer 5760x1080 stride
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (EE) modeset(0): failed to set mode: No space left on device
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Allocate new frame buffer 3840x1080 stride
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): EDID vendor "DEL", prod id 16872
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Using hsync ranges from config file
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Using vrefresh ranges from config file
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Printing DDC gathered Modelines:
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  339.88  1920 1948 1980 2040  1080 1083 1088 1157 +hsync +vsync (166.6 kHz eP)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  285.50  1920 1968 2000 2080  1080 1083 1088 1144 +hsync -vsync (137.3 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  297.00  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (135.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): EDID vendor "DEL", prod id 16872
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Using hsync ranges from config file
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Using vrefresh ranges from config file
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Printing DDC gathered Modelines:
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  339.88  1920 1948 1980 2040  1080 1083 1088 1157 +hsync +vsync (166.6 kHz eP)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  285.50  1920 1968 2000 2080  1080 1083 1088 1144 +hsync -vsync (137.3 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  297.00  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (135.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 /usr/libexec/gdm-x-session[1783]: (II) modeset(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
May 19 14:55:28 tilo-XPS-15-9500 gnome-shell[1939]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
May 19 14:55:28 tilo-XPS-15-9500 gnome-shell[1939]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
May 19 14:55:28 tilo-XPS-15-9500 gnome-shell[1939]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
May 19 14:55:28 tilo-XPS-15-9500 gnome-shell[1939]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
May 19 14:55:28 tilo-XPS-15-9500 gnome-shell[1939]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
May 19 14:55:28 tilo-XPS-15-9500 gnome-shell[1939]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
May 19 14:55:28 tilo-XPS-15-9500 gnome-shell[1939]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
May 19 14:55:28 tilo-XPS-15-9500 gnome-shell[1939]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
May 19 14:55:28 tilo-XPS-15-9500 gnome-shell[1939]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).

```

I think it have something todo with 
```
(EE) modeset(0): failed to set mode: No space left on device
```
but I have no clue what I can do.

I hope any of you have an idea what I can do.
If the post is in the wrong section or lacking important information, please give me a short feedback.

TY and stay healthy

Edit:
After Updating the Bios, the Docking station firmware and ubuntu it worked. Pls close / delete the post.

---

