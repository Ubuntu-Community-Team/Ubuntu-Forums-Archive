---
title: "add 1920x1080 resolution option, xrandr badmatch &amp; more"
date: 2019-06-16
forum: Hardware
---

### Post by dez93_2000 on 2019-06-16
Hi  all. I'm trying to add a 1920x1080x60 resolution option to my Display  dropdown. My monitor is 3440x1440 widescreen but I want this option so  when I VNC into the machine, the resolution matches the remote machine's  monitor.
With nvidia-settings I can select this resolution scaled  but that means the right edge of the screen is simply inaccessible - the  menus aren't reachable etc.

 I've tried a few of the multiple suggestions but I'm sensing that  there have been many changes behind the scenes over the years so I'm  reluctant to keep punching commands into the terminal and hoping for the  best, in case I break my system.
I don't have an xorg.conf file  currently, and don't know whether xrandr is seen as depreciated,  especially since I have nvidia-settings.

 
```
sudo xrandr --addmode DP-4 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  43
  Current serial number in output stream:  44
```


 ```
sudo get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0:6, 8:10
1 potential busses found: 7
256-byte EDID successfully retrieved from i2c bus 7
Looks like i2c was successful. Have a good day.
Checksum Correct

 Section "Monitor"
    Identifier "SAMSUNG"
    ModelName "SAMSUNG"
    VendorName "SAM"
 # Monitor Manufactured week 47 of 2009
# EDID version 1.3
# Digital Display
DisplaySize 160 90
Gamma 2.20
Option "DPMS" "false"
Horizsync 26-81
VertRefresh 24-75
# Maximum pixel clock is 230MHz
#Not giving standard mode: 1152x864, 75Hz
#Not giving standard mode: 1280x800, 60Hz
#Not giving standard mode: 1280x960, 60Hz
#Not giving standard mode: 1280x1024, 60Hz
#Not giving standard mode: 1440x900, 60Hz
#Not giving standard mode: 1440x900, 75Hz
#Not giving standard mode: 1680x1050, 60Hz
#Not giving standard mode: 1600x1200, 60Hz

#Extension block found. Parsing...
Modeline     "Mode 8" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
Modeline     "Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
Modeline     "Mode 1" 85.50 1360 1424 1536 1792 768 771 777 795 +hsync +vsync
Modeline     "Mode 2" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
Modeline     "Mode 3" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
Modeline     "Mode 4" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
Modeline     "Mode 5" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
Modeline     "Mode 6" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
Modeline     "Mode 7" 74.250 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
Modeline     "Mode 9" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
Modeline     "Mode 10" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync
Option "PreferredMode" "Mode 8"
``` ```
xrandr
Screen 0: minimum 8 x 8, current 3440 x 1440, maximum 32767 x 32767
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected (normal left inverted right x axis y axis)
   1920x1080     60.00 +  59.94    29.97    23.98    60.05    60.00
   1680x1050     59.95
   1600x1200     60.00
   1440x900      74.98    59.89
   1360x768      60.02
   1280x1024     75.02    60.02
   1280x960      60.00
   1280x800      59.81
   1280x720      60.00    59.94
   1152x864      75.00
   1024x768      75.03    70.07    60.00
   800x600       75.00    72.19    60.32
   720x480       59.94
   640x480       75.00    72.81    59.94
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 connected 3440x1440+0+0 (normal left inverted right x axis y axis) 819mm x 346mm
   3440x1440     59.97*+ 100.00    84.96    49.99
   1024x768      60.00
   800x600       60.32
   640x480       59.94
DP-5 disconnected (normal left inverted right x axis y axis)
```


 ```
sudo lshw -c video
  *-display
       description: VGA compatible controller
       product: GP102 [GeForce GTX 1080 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:73 memory:f6000000-f6ffffff  memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128)  memory:c0000-dffff
```


 ```
 cvt -r 1920 1080

 **1920x1080 59.93 Hz (CVT 2.07M9-R) hsync: 66.59 kHz; pclk: 138.50 MHz**

 Modeline "1920x1080R"  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync
```


 Does anyone know what the best way forward would be?
Build an xorg.conf file?
Try to set a new resolution with a different refresh rate maybe? I read that switching from 60 to (e.g.) 59.94 might work?
I  presume there's no tool that will automatically work out all the  viable/common resolution configurations one's system supports then add  them to each monitor thing in xrandr?
Cheers in advance for any  pointers. I'd happy use the nvidia-settings option if only it didn't cut  off the screen. I tried setting it to 1920x1080 then rebooting via  terminal (since I can't see the panel corner) but it rebooted in  3440x1440 again.

---

