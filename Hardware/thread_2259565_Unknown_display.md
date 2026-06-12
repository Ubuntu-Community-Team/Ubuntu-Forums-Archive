---
title: "Unknown display"
date: 2015-01-05
forum: Hardware
---

### Post by KingA on 2015-01-05
Hi,

I have the "unknown display" thingy and cannot change the resolution to something higher than 1366x768 (my monitor supports up to 1600x900). I've tried most of the things i've found online but nothing works. I installed mesa-utils and ran glxgears and it works (3d gears spinning)

I have nvidia drivers installed and currently being used (Additional Drivers says "this device is using the recommended driver"). In "Details" my graphics is being recognized as "GeForce GTX 650/PCIe/SSE2". I'm using Ubuntu 14.04 LTS and nvidia drivers version 331.113

How to fix this ?

---

### Post by KingA on 2015-01-06
xrandr output:

```

Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
VGA-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-1 disconnected (normal left inverted right x axis y axis)

```

When trying to add new display modes:

```

$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
$ xrandr --addmode VGA-0 1600x900_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  35
  Current serial number in output stream:  36

```

---

