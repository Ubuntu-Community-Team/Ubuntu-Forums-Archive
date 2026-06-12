---
title: "Lenovo - T60 - Resolution"
date: 2010-06-01
forum: Hardware
---

### Post by alan.gustavo on 2010-06-01
Hi,

I try to change my Laptop resolution (Lenovo T60) from 1024 x 768 for 1280 x 960. When i try it:

**~$ xrandr**

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 285mm x 214mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0*    50.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     60.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0x11c)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
  1280x960_60.00 (0x177)  101.0MHz
        h: width  1280 start 1360 end 1488 total 1696 skew    0 clock   59.6KHz
        v: height  960 start  963 end  967 total  996           clock   59.8Hz

Then i run cvt

**~$ cvt 1280 960 60**

# 1280x960 59.94 Hz (CVT 1.23M3) hsync: 59.70 kHz; pclk: 101.25 MHz
Modeline "1280x960_60.00"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync

Then i add this mode

**~$ xrandr --newmode "1280x960_60.00"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync**

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  25
  Current serial number in output stream:  25

Can you help me?

Alan

---

