---
title: "Set monitor resolution"
date: 2014-05-25
forum: Hardware
---

### Post by ion3 on 2014-05-25
Kubuntu 14.04 64bit 

New Ubuntu user. Installation did not recognize monitor. Following instructions at [http://askubuntu.com/questions/138408/how-to-add-display-resolution-fo-an-lcd-in-ubuntu-12-04-xrandr-problem](http://askubuntu.com/questions/138408/how-to-add-display-resolution-fo-an-lcd-in-ubuntu-12-04-xrandr-problem) I did the following.

```
xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  

```

Then...

```
cvt 1280 1024 60
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```

Then...

```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

Then checked...

```
xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
  1280x1024_60.00 (0x2bc)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

```

Then...

```
xrandr --addmode VGA-1 1280x1024_60.00
```

...and now I can set that resolution through the KDE>Settings>System Settings>Display and Montor>Display Configuration>VGA-1, and I get a correct resolution. Then following the instructions, I create a /usr/share/X11/xorg.conf.d/10-monitor.conf file that looks like...

```
cat /usr/share/X11/xorg.conf.d/10-monitor.conf

Section "Monitor"
  Identifier "Monitor0"
Modeline  "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection
Section "Screen"
  Identifier "Screen0"
  Device "VGA-1"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1280x1024"
  EndSubSection
EndSection

```

Now I reboot, and I am back at 1024x768. What did I do wrong?

Thanks in advance.

---

### Post by SeijiSensei on 2014-05-25
Just a guess, but the Modes directive in the Screen section probably needs to read "1280x1024_60.00" so it matches the entry in the Modeline.

---

### Post by ion3 on 2014-05-25
> **SeijiSensei said:**
> Just a guess, but the Modes directive in the Screen section probably needs to read "1280x1024_60.00" so it matches the entry in the Modeline.

Thanks for the quick response. I tried that. No change.

---

