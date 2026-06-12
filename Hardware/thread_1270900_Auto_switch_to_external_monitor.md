---
title: "Auto switch to external monitor"
date: 2009-09-20
forum: Hardware
---

### Post by matshofman on 2009-09-20
Hi,

I've got a laptop and Ubuntu works great on it but when i'm at home i want to connect my laptop to a external monitor and turn my laptop screen of. I want Ubuntu to switch automatically.

Here is the output of "xrandr -q" with the external monitor connected

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 3840 x 1600
LCD connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  
DFP_EXTTMDS disconnected (normal left inverted right x axis y axis)
CRT1 connected (normal left inverted right x axis y axis)
   1680x1050      59.9 +
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       75.0     60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     60.0  
   640x400        75.1     59.9  
   512x384        60.0     74.9  
   400x300        75.0     60.7  
   320x240        75.6     60.0  
   320x200        75.5     60.1  
TV disconnected (normal left inverted right x axis y axis)
```I already tryed this from a [website]("http://linux-tipps.blogspot.com/2009/03/automatically-switch-to-connected.html") but that didn't work for me

```
'xrandr -q | grep \'CRT1 connected\' && xrandr --output LCD --off --output CRT1 --auto' | sudo tee /etc/X11/Xsession.d/98vgaonly && sudo chmod a+x /etc/X11/Xsession.d/98vgaonly
```I hope anyone got a solution for me!

---

### Post by mathfeel on 2009-09-20
> **matshofman said:**
> Hi,
```
'xrandr -q | grep \'CRT1 connected\' && xrandr --output LCD --off --output CRT1 --auto' | sudo tee /etc/X11/Xsession.d/98vgaonly && sudo chmod a+x /etc/X11/Xsession.d/98vgaonly
```I hope anyone got a solution for me!

You can either issue the ```
xrandr --output LCD --off --output CRT1 --auto'
``` command without restarting the X server. Better yet, bind some kind of hot key to it.

Or just restart the X server, at which point the CRT would become the primary display (not sure if this is true for all laptops, but for the two I have/had, it's true).

If you want it to be fully automatic when you plugin the monitor, you would have to write an ACPI handling script to trigger when
```
/sys/devices/virtual/video_output/acpi_video1/state
```
changes. Not something I have off the top of my head.

---

### Post by matshofman on 2009-09-20
I managed to make some shortcuts and that works good enough for me, thanks

If anyone has a better solution, i would love to know

---

