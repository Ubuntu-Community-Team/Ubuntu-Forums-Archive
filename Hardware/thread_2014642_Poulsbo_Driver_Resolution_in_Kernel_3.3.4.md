---
title: "Poulsbo Driver Resolution in Kernel 3.3.4"
date: 2012-07-02
forum: Hardware
---

### Post by saascuba1 on 2012-07-02
All:

I have been trying to get an small factor PC hat unfortuntately has the GMA500 as the video driver working with the native resolution of my monitor - 1920 x 1080.

I have read about the updated kernel 3.3.4 offering support for this chipset and have upgraded my installation but still can not get the desired resolution and am not sure about controlling the screen. Various postings seem to indicate that zrandr shold not be used while others seem to contradict this.

Here is some information of my system configuration:

[FONT=Fixedsys]lubuntu@lubuntu1:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 720, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 0mm x 0mm
   1280x720        0.0* 
lubuntu@lubuntu1:~$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
lubuntu@lubuntu1:~[/FONT]

lubuntu@lubuntu1:~$ sudo lshw -c video
[FONT=Fixedsys][sudo] password for lubuntu: 
  *-display               
       description: VGA compatible controller
       product: System Controller Hub (SCH Poulsbo) Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=gma500 latency=0
       resources: irq:16 memory:fe980000-fe9fffff ioport:c880(size=8) memory:d0000000-dfffffff memory:fe940000-fe97ffff[/FONT]
[FONT=Fixedsys]
lubuntu@lubuntu1:~$ lsmod | grep gma
gma500_gfx            192914  2 
lubuntu@lubuntu1:~$ uname -r
3.4.4-030404-generic[/FONT]

What I would like this box to do is drive the VGA port (the only display port) with the native screen resolution of 1920 x 1080 and also rotate the screen 90 degrees.

How do I do this?

Please help

---

