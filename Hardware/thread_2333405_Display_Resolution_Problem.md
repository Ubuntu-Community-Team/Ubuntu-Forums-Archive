---
title: "Display Resolution Problem"
date: 2016-08-09
forum: Hardware
---

### Post by rbscairns on 2016-08-09
My PC:

[INDENT]Memory:  990.0 MiB
Processor:  Intel Atom CPU N270 @ 1.60GHz x 2
Graphics:  Intel 945GME x86/MMX/SSE2
OS:  Ubuntu 16.04
OS Type:  32-bit
Monitor:  ASUS VH202T[/INDENT]

My problem:

[INDENT]Going into Settings>Displays shows Unknown display. The only display resolution options that I have available are 1024 x 768 (4:3) and 800 x 600 (4:3).

I do a lot of graphics work and need my circles to look like circles (not ovals) and my squares to look like squares (not rectangles). For this, I need to set the monitor resolution to 1280 x 768.[/INDENT]

How can I set the monitor resolution to 1280 x 768?

```
sudo lshw -C video
``` returns

```
 *-display:0             
       description: VGA compatible controller
       product: Mobile 945GSE Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fbd00000-fbd7ffff ioport:dc80(size=8) memory:d0000000-dfffffff memory:fbcc0000-fbcfffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fbd80000-fbdfffff

```

---

### Post by mörgæs on 2016-08-11
Though this solution concerns another graphics card it may also work for you:

[https://ubuntuforums.org/showthread.php?t=2322659&p=13523782&viewfull=1#post13523782](https://ubuntuforums.org/showthread.php?t=2322659&p=13523782&viewfull=1#post13523782)

---

### Post by rbscairns on 2016-08-19
Thank you mörgæs. The topic your linked to was for 1280x1024 resolution. I require 1280x768. I then followed the steps given in the link substituting in my required resolution.

The ourput of xrandr is
```
DVI1 unknown connection (normal left inverted right x axis y axis)
   1360x768      59.80  
   1152x864      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
  1280x768_60.00 (0xa6) 79.500MHz -HSync +VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock  47.78KHz
        v: height  768 start  771 end  781 total  798           clock  59.87Hz
```

In terminal, i typed
```
 cvt 1280 768
```

This returned
```
# 1280x768 59.87 Hz (CVT) hsync: 47.78 kHz; pclk: 79.50 MHz
Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync

```

I then typed
```
xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
```

followed by
```
xrandr --addmode VGA1 1280x768_60.00
```

I then clicked on System Settings>Displays and I now have the additional option of selecting 1280x768 resolution. Now my circles are circular and my squares are square!

Now to work out a way to automate the process. If I need help, I will start a new topic.

---

