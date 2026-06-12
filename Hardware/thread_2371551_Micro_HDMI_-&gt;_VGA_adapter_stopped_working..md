---
title: "Micro HDMI -&gt; VGA adapter stopped working."
date: 2017-09-15
forum: Hardware
---

### Post by cowpicket on 2017-09-15
```

Manufacturer: ASUSTeK COMPUTER INC.
Product Name: UX305FA
Version: 1.0       

```

uname -ar
```

Linux 4.10.0-33-generic #37~16.04.1-Ubuntu SMP Fri Aug 11 14:07:24 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

lspci | grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Broadwell-U Integrated Graphics
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f6000000 (64-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```

I have a UGreen Micro HDMI to HDMI/VGA converter that i was using to connect to my external Samsung SyncMaster933, it worked right out of the box. 

Recently I unplugged everything and used the other end of the adapter to connect my laptop to another external screen (also Samsung) from  Micro HDMI -> HDMI it also worked perfectly. 

When I removed everything for the last and final time to connect my laptop back to the SyncMaster the screen isn't recognized. 

xrandr -q        Connected to Samsung SyncMaster933
```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 293mm x 165mm
   1920x1080     60.00*+  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
HDMI-1 disconnected (normal left inverted right x axis y axis)


```

xrandr -q         Connected to Samsung LN-T1953H
```

Screen 0: minimum 320 x 200, current 3280 x 1080, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 293mm x 165mm
   1920x1080     60.00*+  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
HDMI-1 connected 1360x768+1920+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1360x768      60.02*+
   1920x1080i    60.00    59.94  
   1280x720      60.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
   720x400       70.08 

```

I have tried adding modes at various resolutions to HDMI using xrandr but to no effect.

```

$ xrandr --addmode HDMI-1 1360x768
$ xrandr --output HDMI-1 --mode 1360x768 --right-of eDP-1
xrandr: Configure crtc 1 failed


```

---

