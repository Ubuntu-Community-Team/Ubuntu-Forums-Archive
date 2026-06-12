---
title: "Setting up the third monitor on the built in graphics card"
date: 2016-02-28
forum: Hardware
---

### Post by edina2 on 2016-02-28
Hi,

I read a good few articles here this is the first time when I did not find the solution to my issue.

System: Ubuntu 14.04LTS
Graphics card: nvdia geforce gtx550 and the built in intel

The system is working well in 2 monitors environment. Both monitors connected to the nvdia (with dvi and hdmi) (main and left).
Tried to add the third monitor, connected to the built in intel graphics card with hdmi. 
The monitors were setup in main, left and top of the left style.

Main and left still working, but the top (connected to the built-in card) shows only the mouse cursor on the black screen. 
If I click on the black screen launcher area (not visible) the applications are starting up.
If I click on the workspace switcher 4 desktop visible.
[ATTACH=CONFIG]267578[/ATTACH]
I can drag windows to the top left desktop but on the third monitor that desktop is not visible, only the black.

Please help.
Thanks,
Edina

**xrandr -q**
```

Screen 0: minimum 8 x 8, current 3840 x 2280, maximum 16384 x 16384
DVI-I-0 connected primary 1920x1200+1920+1080 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      60.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-0 connected 1920x1080+0+1080 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080      60.0*+   59.9     50.0     60.0     50.0  
   1680x1050      60.0  
   1440x900       59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0     59.9     50.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        75.0     72.8     59.9     59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+   50.0     59.9  
   1920x1080i     60.1     50.0     60.0  
   1680x1050      59.9  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x720       60.0     50.0     59.9  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     72.8     66.7     60.0     59.9  
   720x400        70.1  
DP2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0x2b9)  148.5MHz
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
  1920x1080 (0x2c3)  148.5MHz
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   56.2KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   50.0Hz
  1280x1024 (0x2c7)  135.0MHz
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x2bc)  108.0MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x960 (0x2bd)  108.0MHz
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1280x720 (0x2c8)   74.2MHz
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1280x720 (0x2ca)   74.2MHz
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock   37.5KHz
        v: height  720 start  725 end  730 total  750           clock   50.0Hz
  1024x768 (0x2cc)   75.0MHz
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x2be)   65.0MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x2ce)   50.0MHz
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x2cd)   49.5MHz
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x2bf)   40.0MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x2cf)   36.0MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  720x576 (0x2d0)   27.0MHz
        h: width   720 start  732 end  796 total  864 skew    0 clock   31.2KHz
        v: height  576 start  581 end  586 total  625           clock   50.0Hz
  720x480 (0x2d1)   27.0MHz
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  640x480 (0x2d2)   31.5MHz
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x2c0)   25.2MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz


```

**lshw -C video**
```

  *-display               
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:55 memory:f4000000-f5ffffff memory:e0000000-e7ffffff memory:e8000000-ebffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:53 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

**lspci | grep VGA**
```

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)

```

**Nvidia driver: **
```

NVIDIA binary driver - version 352.63 from nvidia-352-updates (proprietary)

```

**xorg.conf**
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
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

```

---

