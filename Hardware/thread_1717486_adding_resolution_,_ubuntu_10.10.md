---
title: "adding resolution , ubuntu 10.10"
date: 2011-03-29
forum: Hardware
---

### Post by jstnhickey2 on 2011-03-29
I have followed a few instructions with no avail online.  I have tried to use xrandr to no avail.  
I have this computer
[http://support.gateway.com/s/notebook/2009/gateway/nv/nv52/NV52sp2.shtml](http://support.gateway.com/s/notebook/2009/gateway/nv/nv52/NV52sp2.shtml)

The highest resolution I can select is 1366x768.

I have ATI Catalyst Control Panel installed, there are no additional options that I have found useful in there.

When I got to additional drivers I see that I have the ATI FGLRX driver installed.

when I do an xrandr I get this

> Screen 0: minimum 320 x 200, current 1366 x 768, maximum 1600 x 1600
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1280x768       60.0 +
   1280x720       60.0 +
   1024x768       60.0 +
   1280x600       60.0 +
   1024x600       60.0 +
   800x600        60.0 +
   800x480        60.0 +
   720x480        60.0 +
   640x480        60.0 +
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
  1600x900_60.00 (0xd4)  118.2MHz
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock   56.0KHz
        v: height  900 start  903 end  908 total  934           clock   59.9Hz
  1920x1080_60.00 (0xdf)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz

I added the 1600x900 and 1920x1080 modelines, not sure if its correct, but when I try to addmode using xrandr I get this error.

> $ xrandr --addmode LVDS 1600x900_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  27
  Current serial number in output stream:  28

any ideas?  I'm a beginner, so I'm not too great terminal and such.

---

### Post by jstnhickey2 on 2011-03-30
top

---

### Post by jstnhickey2 on 2011-04-01
still looking for some help

---

### Post by BicyclerBoy on 2011-04-01
The internal panel LVDS is only 1366x768 (native)..
There is no good reason to drive it at any other resolution.
It will just look terrible an any resolution that is not native..

You can normally set the GPU to do all scaling (of any resolution selected by video player etc) to your set resolution (native).

The internal panels (LVDS) only have a very limited video modes & refresh rates (50 & 60Hz). 
AFAIK they do not have any pre-scaler, the different video modes are virtually handled by the GPU.

If you add a mode that is not a pre-defined one, you have to use
xrandr --newmode "name" modeline-stuff
xrandr --addmode VGA-0 "name"

---

### Post by xenakaaii on 2011-04-04
I'm having a similar problem here.  
I've used to run my machine at 1920x1080 resolution, but sometime after upgrading to 10.10, 1920x1080 is no longer a valid option.  I've tried xrandr to add the resoltion, but I get the same error as above.  
The weirdest thing is that if I attach my laptop to my external monitor, it suddenly detects that 1920x1080 is an option, but if I unplug and reboot, it resets the resolution.

heres what I get from xrandr without the monitor plugged in
```
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1440 x 1440
LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1400x1050      59.9* 
   1280x1024      59.9  
   1440x900       59.9  
   1280x960       59.9  
   1280x768       59.9  
   1280x720       59.9  
   1024x768       59.9  
   1024x600       59.9  
   800x600        59.9  
   800x480        59.9  
   640x480        59.9  
DFP1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)

```

and heres with the external monitor plugged in
```
Screen 0: minimum 320 x 200, current 3200 x 1080, maximum 3840 x 1080
LVDS connected 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      59.9*+
   1680x1050      59.9  
   1400x1050      59.9  
   1600x900       59.9  
   1280x1024      59.9  
   1440x900       59.9  
   1280x960       59.9  
   1280x768       59.9  
   1280x720       59.9  
   1024x768       59.9  
   1024x600       59.9  
   800x600        59.9  
   800x480        59.9  
   640x480        59.9  
DFP1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1280x1024+1920+0 (normal left inverted right x axis y axis) 300mm x 225mm
   1024x768       85.0 +   75.0  
   1280x1024      60.0* 
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x600       85.0     75.0                                                                                                                                                                                                                    
   800x600        85.1     75.0  
   800x480        85.1     75.0  
   640x480        85.0     59.9  

```

---

