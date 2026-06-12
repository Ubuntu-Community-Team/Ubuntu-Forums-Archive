---
title: "Graphics Driver Resolutions"
date: 2013-10-10
forum: Hardware
---

### Post by Prakash_Thapa on 2013-10-10
I have DELL OptiPlex 3010 machine with Ubuntu 13.04 Installation.
I already updated my OS by issuing a command ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```.
Furthermore, I have also installed Intel Linux Graphics from a installer (Intel(R) Linux* Graphics Installer version 1.0.2) download from [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)
But still ubuntu shows 1366 x 768 (16:9) as a largest resolution.

Below are more information about my machine:

output of "xrandr"
```

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1366x768       59.8*+
   1360x768       60.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

```

output of "sudo lspci -nnk | grep -A5 VGA"
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:0152] (rev 09)
    Subsystem: Dell Device [1028:0585]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Dell Device [1028:0585]
    Kernel driver in use: mei

```

I want to have a larger resolution, so can anyone help me on how can I change the resolution?

---

### Post by grahammechanical on 2013-10-10
The screen can go to a maximum of 8192x8192 but that does not mean that it will be good to go that high.

What is the graphic adapter capable of outputting? Did the Intel video driver install a video settings manager? It is a combination of graphic adapter and video driver that determine the resolution we get and not Ubuntu.

The Ubuntu Screen Displays utility is deactivated when we use a proprietary video driver and Screen Displays will not allow us to go beyond what the screen manufacture has set as the optimum screen resolution. Ubuntu reads the Extended Display Identification Data (EDID) from the monitor and sets the resolution accordingly.

This is what xrandr says about my monitor

> Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
DVI-I-1 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
VGA-1 disconnected (normal left inverted right x axis y axis)

I see that Ubuntu is running the monitor at the manufacturer's recommended optimum settings and I am thankful for that. By the way, 1680x1050 is the highest resolution that Screen Displays will give me although the monitor can take a high resolution.

Regards.

---

### Post by Yellow Pasque on 2013-10-10
What kind of screen/monitor do you have? What is the native resolution of it if it's not 1366x768?

---

