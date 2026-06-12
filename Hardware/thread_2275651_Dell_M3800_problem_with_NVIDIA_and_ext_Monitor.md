---
title: "Dell M3800 problem with NVIDIA and ext Monitor"
date: 2015-04-27
forum: Hardware
---

### Post by rafanto on 2015-04-27
Hi,
I have problems with my notebook DELL Precision M3800 with NVIDIA Quadro K1100 and Intel. 
I need to use the proprietary driver nvidia (I tested both the 331 that 349) with an external monitor. 
My external monitor (DELL) has a resolution of 1920*1200,  I connect via DVI-miniDP adapt but my system at each session view this error: *could not set the configuration for CRTC 64*.

Notebook Resolution: 1920*1080 
Ext Monitor: 1920*1200

```
antodc@gandalf:~$ xrandr
Screen 0: minimum 8 x 8, current 3840 x 1200, maximum 16384 x 16384
eDP1 connected 1920x1080+0+0 346mm x 194mm
   3840x2160      60.0 +   48.0  
   2048x1536      60.0  
   1920x1440      60.0  
   1856x1392      60.0  
   1792x1344      60.0  
   1920x1200      60.0  
   1920x1080      59.9* 
   1600x1200      60.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected
HDMI1 disconnected
DP1 disconnected
HDMI2 connected 1920x1200+1920+0 518mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1680x1050      59.9  
   1280x1024      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  
VIRTUAL1 disconnected
```


```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:2@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

```

I am trying in every way but I can not make them work. Do you have any idea to suggest?

---

