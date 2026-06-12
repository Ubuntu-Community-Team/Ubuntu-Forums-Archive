---
title: "Unkown display,xrandr badmatch,resolution undetected."
date: 2018-04-20
forum: Hardware
---

### Post by alborz3 on 2018-04-20
Hi,


I have a somewhat strange monitor with a resolution of **1280x390**.
When connected to my PC through HDMI-HDMI it automatically sets itself up as a [B]1280x1024.

[/B]Below I have tried to add as much information as possible:

see output of xrandr below (DP-1).
```

:~$ xrandr
Screen 0: minimum 8 x 8, current 3200 x 1080, maximum 16384 x 16384
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 connected 1280x1024+1920+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024     60.02*+
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.01*+  40.01  
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
DP-6 disconnected (normal left inverted right x axis y axis)[/QUOTE]

```

Hardware:
```

:~$ lspci -vk | grep -iA15 vga
01:00.0 VGA compatible controller: NVIDIA Corporation GM107GLM [Quadro M2000M] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company GM107GLM [Quadro M2000M]
    Flags: bus master, fast devsel, latency 0, IRQ 131
    Memory at e3000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_390, nvidia_390_drm

```



Content of get-edid | parse-edid:
```

:~$ sudo get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 6
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
1 potential busses found: 5
128-byte EDID successfully retrieved from i2c bus 5
Looks like i2c was successful. Have a good day.
Checksum Correct


Section "Monitor"
    Identifier ""
    ModelName ""
    VendorName "GSD"
    # Monitor Manufactured week 3 of 2005
    # EDID version 1.3
    # Digital Display
    DisplaySize 340 270
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 30-71
    VertRefresh 56-75
    # Maximum pixel clock is 110MHz
    #Not giving standard mode: 640x480, 75Hz
    #Not giving standard mode: 800x600, 75Hz
    #Not giving standard mode: 1024x768, 75Hz
    #Not giving standard mode: 1280x1024, 60Hz
    Modeline     "Mode 0" 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync 
EndSection

```

I have upgraded to the latest Nvidia driver, which at the moment of writing is **390.30**.
I also tried to connect the monitor via **DVI-HDMI** cable without any success.


I also tried to create the resolution using xrandr.


```

:~$ cvt 1280 390
# 1280x390 59.89 Hz (CVT) hsync: 24.38 kHz; pclk: 39.00 MHz
Modeline "1280x390_60.00"   39.00  1280 1320 1440 1600  390 393 403 407 -hsync +vsync

:~$ xrandr --newmode "1280x390_60.00"   39.00  1280 1320 1440 1600  390 393 403 407 -hsync +vsync

:~$ xrandr --addmode DP-1 "1280x390_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  43
  Current serial number in output stream:  44

```

I can not seem to find anywhere on the internet what the above error actually means.
Any help would be appreciated.

---

### Post by cmartinkc on 2018-04-22
Sounds like you have an ultra wide bar display.  I have one one on order from China and the manufacturer is warning me that the interface board reports the resolution as much taller than what the monitor can display causing only the top half of the desktop to show.  Curious, when you go to the screen menus do they show properly? If not this would seem to confirm we are in the same boat. I am starting the same process you are going through by experimenting with a standard monitor. My plan is to use Xrandr to "clip" the desktop to the active area which the bar monitor can show.  BTW, what are you using the monitor for?

---

### Post by alborz3 on 2018-04-22
Yes, you are correct, it is an ultra wide display from China. The original panel must have been taller and then it has been cut and turned into an widescreen monitor.
If I maximize a window then it goes outside the visible area.
I will be making my own QT application to run on this display so I could potentially make the application to show up only on the top part of the monitor which is visible.
But that does not really work for me since I have a touch-panel that I need to place in front on the screen (turning it into a touch screen) and the touch calibration will be super difficult if the resolution is completely wrong.

---

