---
title: "i5 M520 HD Graphics poor performance"
date: 2019-11-30
forum: Hardware
---

### Post by stevenjrees on 2019-11-30
I have a Getac X500 laptop with i5 M520 CPU and Intel HD Graphics. 
```
lspciglx
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```
```
glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 19.0.8
OpenGL shading language version string: 1.20
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 19.0.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
```

With win10 the performance was fine, but Win10 broke after the 2016 version, so i thought to put Linux on it to get some more life out of it. 
The performance is horrible, but i believe this is primarily HD Graphics related.

 The only info i can seem to find suggests using Intel drivers, but that seems to be for much older versions of ubuntu and have dependency problems now.

---

### Post by mörgæs on 2019-11-30
This is cool hardware. It deserves to shine.

As a first step: Try a fresh install of a recent X/Lubuntu to see if there is any progress.

---

### Post by Yellow Pasque on 2019-11-30
> **stevenjrees said:**
>  The only info i can seem to find suggests using Intel drivers.

You're already using them. There are ways to upgrade to the absolute latest version of those drivers, but it's doubtful that will make much of a difference for an older GPU. What leads you to believe the slowness is caused by the graphics?

---

### Post by stevenjrees on 2019-12-01
- compared to the win10 that was on it, screen is slow opening/closing windows, etc
- youtube videos and playing via kodi videos from plex server, don't play smoothly (they did under win10)
- with 2nd screen connected, black blocks appear on the laptop screen when mouse is over open windows
- firefox/chromium after both quiet slow in screen changes

so far i have done a couple of things that seems to have helped a bit. 

1) add [COLOR=#2E8B57][FONT=monospace]/etc/X11/xorg.conf
[COLOR=#2E8B57][FONT=Monaco]Section "Device" 
   Identifier   "intel"    
Driver   "intel" 
   Option  "AccelMethod"  "sna"                
EndSection[/FONT][/COLOR][/FONT][/COLOR]

2) added add-apt-repository ppa:ubuntu-x-swat/updates

- this has fixed the issue of the black boxes i.e. both screens seem to work fine now.
- youtube in chromium is still somewhat jumpy (its better on firefox)
- kodi is still a little jumpy (was smooth on win10)

*** further update ***
I added the following to grub which seems to have fixed the performance issue, but now only the extend monitor is recognized and not the device display.
i915.modeset=1 video=LVDS-1:d

---

### Post by mörgæs on 2019-12-01
Please post the output of ```
xrandr
```

---

### Post by stevenjrees on 2019-12-05
[I]Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
LVDS1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 340mm x 190mm
   1920x1080     60.00*+  59.93  
   1680x1050     59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1368x768      60.00    59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.81    59.91  
   1152x864      60.00  
   1280x720      59.86    60.00    59.74  
   1024x768      60.00  
   1024x576      60.00    59.90    59.82  
   960x540       60.00    59.63    59.82  
   800x600       60.32    56.25  
   864x486       60.00    59.92    59.57  
   640x480       59.94  
   720x405       59.51    60.00    58.99  
   640x360       59.84    59.32    60.00  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VGA1 connected (normal left inverted right x axis y axis)
   1680x1050     59.95 +
   1600x1000     60.01  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   832x624       74.55  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/I]

---

### Post by mörgæs on 2019-12-06
For me the output is 
```
Screen 0: minimum 320 x 200, current 2646 x 1024, maximum 8192 x 8192
LVDS connected primary 1366x768+1280+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.04*+
   1280x720      59.97  
   1152x768      59.95  
   1024x768      59.95  
   800x600       59.96  
   848x480       59.94  
   720x480       59.94  
   640x480       59.94  
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024     60.02*+  75.02  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08  
HDMI-0 disconnected (normal left inverted right x axis y axis)

```
which gives a fine output on both screens.

You also have twice 'connected' in the output. I was hoping to find a clue here...

Anyone else has an idea?

---

