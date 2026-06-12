---
title: "Screen Resolution Problem on Netbook"
date: 2012-01-31
forum: Hardware
---

### Post by sboz on 2012-01-31
Hi all.

I've looked for this problem before but can't see an exact resolution for it.  I've got an Asus eeePC 1000E netbook on which I've got Ubuntu 11.10 installed.  I've got a problem in that I'm only able to have a screen resolution of 1024 x 600, which isn't very satisfying.  This is the resolution on the lcd screen of the netbook, not an external monitor.

I've tried using xrandr to solve the problem.  When I type in *xrandr* I get:

```

Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+   65.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

```I then try to add a resolution to the options by typing* cvt 1024 800* and get the response

```

# 1024x800 59.77 Hz (CVT) hsync: 49.67 kHz; pclk: 66.75 MHz
Modeline "1024x800_60.00"   66.75  1024 1080 1184 1344  800 803 813 831 -hsync +vsync

```I then type *xrandr --newmode "1024x800_60.00"   66.75  1024 1080 1184 1344  800 803 813 831 -hsync +vsync *and then *xrandr *again which returns

```

Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+   65.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
  1024x800_60.00 (0xba)   66.8MHz
        h: width  1024 start 1080 end 1184 total 1344 skew    0 clock   49.7KHz
        v: height  800 start  803 end  813 total  831           clock   59.8Hz

```It seems like the newmode command adds the resolution to the VGA1 output, rather than the LVDS1.  So when I proceed with the next step *xrandr --addmode LVDS1 "1024x800_60.00" *I get the error:

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

```If it's of any use, typing *lspci | grep VGA* shows the graphics card to be:

```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

```Any ideas? 
Thanks!

---

### Post by sboz on 2012-01-31
I should add that I'm using 11.10.

EDIT: Actually, I've already said that above!

---

