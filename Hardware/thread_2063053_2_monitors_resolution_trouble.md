---
title: "2 monitors resolution trouble"
date: 2012-09-26
forum: Hardware
---

### Post by woodyart on 2012-09-26
Hello, I have two monitors one model, but I can't select the same resolution for them. First monitor DVI-I-0 have correct resolution - 1280x1024 and second monitor DVI-I-1 - 1024x768.

I have a nvidia graphics card, driver version 304.43, Ubuntu 12.04 x64

```

sudo lspci | grep -i vga
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 9800 GTX] (rev a2)
```I tried to add the necessary resolution, but the system generates an error

```

xrandr -q

Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 8192 x 8192
DVI-I-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DVI-I-1 connected (normal left inverted right x axis y axis)
   1024x768       60.0 +
   1360x768       60.0     59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 disconnected (normal left inverted right x axis y axis)


xrandr --auto --output DVI-I-0 --mode 1280x1024 --right-of DVI-I-1
xrandr --auto --output DVI-I-1 --mode 1280x1024 --left-of DVI-I-0

xrandr: cannot find mode 1280x1024


cvt 1280 1024

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode DVI-I-1 1280x1024_60.00

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34

```How to copy the resolution settings from the first to the second monitor?:(

---

