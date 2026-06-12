---
title: "External screen resolution"
date: 2011-05-19
forum: Hardware
---

### Post by Salleman on 2011-05-19
Hi..

I have an Acer Aspire 3820TG with radeon 5650.

I'm trying to connect a projector through HDMI so I can watch some movies. Running Natty with ATI drivers.

When I plug in the cable I don't get the correct resolution. The max. available resolution is 1600x1200 (probably because I buy cheap cables), and my pj supports full hd.

I've tried editing xorg.conf, adding modeline from cvt/gtf. 
Messed around with xrandr, doing the same.
Rebooted and reconnected the cable around a hundred times.

Still only 1600x1200.

I dont't know what I'm doing wrong, all help will be appreciated.

Thanks from copenhagen..

---

### Post by Salleman on 2011-05-24
I've tried

> ...@...:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
...@...:~$ xrandr --newmode "1920x1080"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
...@...:~$ xrandr --addmode DFP1 "1920x1080"X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28


Also tried adding

Section "Monitor"
	Identifier   "0-DFP1"
   >  Modeline        "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    Modeline	    "1920x1080_50.00"  141.50  1920 2032 2232 2544  1080 1083 1088 1114 -hsync +vsync
    Modeline  	    "1920x1080_24.00"   63.00  1920 1976 2160 2400  1080 1083 1088 1098 -hsync +vsync  
    Option          "PreferredMode" "1920x1080_60.00"

to generated xorg.conf 


Still no luck.

---

### Post by Salleman on 2011-05-28
Apparently the is no solution?

Can I provide some additional info to help the guru's out there?

---

