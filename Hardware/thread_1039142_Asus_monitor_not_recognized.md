---
title: "Asus monitor not recognized"
date: 2009-01-14
forum: Hardware
---

### Post by egalua on 2009-01-14
Hi all, 

I have just bought a new pc: the components are

CPU: intel core2duo with 4 Gb of RAM
MB: asus p5ql-em
VGA: intel g43 (integrated on the MB)
Monitor: asus vw198s

I installed ubuntu 8.10 (amd64).

The problem is that the correct resolution of the monitor (1680x1050) is not recognized out of the box: after installation, it ran 
at a lower resolution (1360x768) and I was not able to change it.

The monitor is marked as unknown

The output of xrandr -q is:

Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1360
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8
   1152x864       60.0*
   1024x768       60.0
   800x600        60.3
   640x480        59.9
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)

If necessary, I can post also the X logs.

For the moment, using powerstrip I got the modeline

Modeline "1680x1050" 147.600 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync

(I couldn't find any help on the web).

Should I file a bug for this? In the case, where?

Anyway this still leave me with a problem with the framebuffer: when I logout 
to change user, sometime instead of the usual gdm greeting I get that the monitor 
has no signal and goes automatically in poweroff: the only thing that I can do is an hard reboot of the pc.

I bought an intel vga thinking that in view of its openness it were more stable... :frown:

Thanks

Fabio

---

