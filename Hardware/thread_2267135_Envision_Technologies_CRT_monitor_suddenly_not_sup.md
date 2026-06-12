---
title: "Envision Technologies CRT monitor suddenly not supported"
date: 2015-02-27
forum: Hardware
---

### Post by tcll5850 on 2015-02-27
I'd been using this monitor as my primary monitor since I installed linux...

just now I got an update that messed up my screen orientation, and positioned the mouse on my right monitor slightly to the left,
while offsetting the windows of my left monitor slightly to the left...

after restarting, my left monitor (the envision technologies) could no longer draw at 1600x1200 at 75Hz...
now it's name is either "Monitor" or "Digital Monitor" and can only draw at lower resolutions at 60Hz.

I don't believe my monitor is the problem...

---

### Post by tcll5850 on 2015-02-27
just tried adding the mode with xrandr... no luck

```

tcll@tcll-AY589AAR-ABA-a4317c:~$ cvt 1600 1200 75
# 1600x1200 74.98 Hz (CVT 1.92M3) hsync: 94.09 kHz; pclk: 204.75 MHz
Modeline "1600x1200_75.00"  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync
tcll@tcll-AY589AAR-ABA-a4317c:~$ xrandr --newmode "1600x1200_75.00"  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync
tcll@tcll-AY589AAR-ABA-a4317c:~$ xrandr --addmode VGA-0 1600x1200_75.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  3

```
modes:
```

tcll@tcll-AY589AAR-ABA-a4317c:~$ xrandr
Screen 0: minimum 8 x 8, current 2752 x 1200, maximum 16384 x 16384
DVI-I-0 connected primary 1600x1200+1152+0 (normal left inverted right x axis y axis) 350mm x 260mm
   1280x1024      75.0 +   85.0  
   1600x1200      75.0* 
   1024x768       85.0  
   800x600        85.1  
   640x480        85.0     59.9  
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0     59.8  
   1152x864       60.0* 
   800x600        72.2     60.3     56.2  
   680x384        60.0     59.8  
   640x480        59.9  
   512x384        60.0  
   400x300        72.2  
   320x240        60.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
  1600x1200_75.00 (0x324)  204.8MHz
        h: width  1600 start 1720 end 1888 total 2176 skew    0 clock   94.1KHz
        v: height 1200 start 1203 end 1207 total 1255           clock   75.0Hz

```
^I don't understand that HDMI one as I have nothing that can connect to it...


is there anything else I could try?? :/

---

### Post by tcll5850 on 2015-02-28
just booted up this morning and noticed my primary was acting funny again (after just configuring my largest 4x3 resolution 11**x8** (I forget exactly)), 
so I took a look at my displays and found my "Envision Peripherals" monitor again ^_^

it must've done a background update before I shut down last night (while I was working on the last message).

if this message was what got developers to fix my issue:
to whoever did the update, Thank You! :)

---

