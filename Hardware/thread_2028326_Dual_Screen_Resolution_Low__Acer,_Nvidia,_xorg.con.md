---
title: "Dual Screen Resolution Low | Acer, Nvidia, xorg.conf"
date: 2012-07-18
forum: Hardware
---

### Post by enewe101 on 2012-07-18
Hi,

I've been trying to get my screen resolution to display correctly for the past few days.  I've read many solutions but none have worked for me yet, so I thought I'd reach out for some help.

I have 2 acer monitors, both having a resolution of 1440x900 (specs [http://www.newegg.com/Product/Product.aspx?Item=N82E16824009235](http://www.newegg.com/Product/Product.aspx?Item=N82E16824009235))

I have an nvidia GeForce 8400 GS graphics card.  I am trying to run both monitors, which take VGA input, one from the gfx card's VGA output, the other from its DVI-I output (using an adaptor).  This does give me two working screens in extended mode without any fussing, however, the resolution is wrong.  The correct resolution is not available:

```

enewe101@enewe101-PCL:~$ xrandr
Screen 0: minimum 8 x 8, current 1792 x 1024, maximum 8192 x 8192
DVI-I-0 connected 1024x768+768+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1360x768       60.0     59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
VGA-0 connected 768x1024+0+0 left (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1360x768       60.0     59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)

```So I tried adding and setting a new mode:

```

enewe101@enewe101-PCL:~$ cvt 1440 900 75
# 1440x900 74.98 Hz (CVT 1.30MA) hsync: 70.64 kHz; pclk: 136.75 MHz
Modeline "1440x900_75.00"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
enewe101@enewe101-PCL:~$ xrandr --newmode "1440x900_75" 136.75 1440 1536 1688 1936 900 903 909 942 -hsync +vsync
enewe101@enewe101-PCL:~$ xrandr --addmode VGA-0 1440x900_75
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32

```I've searched around for what could be wrong.  The coherent explanations have been that "you're device is not capable of displaying that resolution", however, it definitely is.  I booted into windows, and could select 1400x900 and it looked great!

Also, I don't think its related to the video card not being capable of that output.  If I connect ONLY one monitor to my INTEGRATED graphics card output from my motherboard, I am still constrained, and attempting to create a new mode gives a similar error.

I also tried setting the resolutions using my ```
/etc/X11/xorg.conf
``` file.  Interestingly, if I create a xorg.conf file (by default I don't have one), it almost always causes the screen to go black once I boot into the login screen for Ubuntu. I've worked from many examples, adapted for the difference with my hardware, but always get the black screen.  If interested I could post an example. If I'm lucky I can get out to a tty and delete the file, but sometimes even that won't work.

Anybody know why I'm not able to get the desired resolution?

---

### Post by enewe101 on 2012-07-19
Anything else I can post?  Main problem is that trying to add new mode gives ```
 X Error of failed request:  BadMatch 
```... but I can't see why, because I know my monitors can handle the 1400x900 resolution...

---

