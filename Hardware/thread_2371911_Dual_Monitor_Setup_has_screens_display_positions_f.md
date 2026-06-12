---
title: "Dual Monitor Setup has screens display positions flipped, Display Manager can't tell"
date: 2017-09-19
forum: Hardware
---

### Post by brutikk on 2017-09-19
I have a dual monitor setup, one Acer (on the right) and one BenQ (on the left).  My display manager defaults to having the BenQ treated as the monitor on the right, and the Acer treated as the monitor on the left.  The Acer is attached via DVI, and the BenQ is attached via HDMI, both going to my Nvidia GTX 1050 ti.  In my display manager, if I move the BenQ monitor to the left of the Acer monitor (reflecting how the monitors are actually set up), things start to not work.  Although the cursor now moves intuitively (with the BenQ on the left and Acer on the right), any click that I perform happens on the wrong monitor.  So, I will be moving my mouse around on the Acer monitor, I will click something on the Acer monitor, but the click happens at the same coordinates as the Acer monitor, but on the BenQ instead.

I have tried to attach a screen shot in which I have clicked and dragged my mouse on my Acer Monitor (the one with this thread open on it), but the action is clearly taking place on my BenQ monitor (the one with the display manager open).  However, this was not possible, as the screenshot actually has the screens reversed from what I am seeing.  I don't know what is going on.

I am using Ubuntu 17.04, and I am not using the proprietary nvidia drivers.

> xrandrScreen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DVI-D-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
1920x1080 60.00*+ 59.93 
1680x1050 69.88 59.95 59.88 
1600x1024 60.17 
1400x1050 74.76 70.00 59.98 
1280x1024 75.02 60.02 
1440x900 74.98 59.89 59.90 
1280x960 60.00 
1360x768 59.80 59.96 
1280x800 59.91 
1152x864 75.00 75.00 70.00 60.00 
1024x768 75.05 60.04 75.03 70.07 60.00 
960x720 75.00 60.00 
928x696 75.00 60.05 
896x672 75.05 60.01 
960x600 60.00 
832x624 74.55 
960x540 59.99 
800x600 75.00 70.00 65.00 60.00 72.19 75.00 60.32 56.25 
840x525 74.96 69.88 60.01 59.88 
800x512 60.17 
700x525 74.76 70.06 59.98 
640x512 75.02 60.02 
720x450 59.89 
640x480 60.00 75.00 72.81 75.00 66.67 59.94 
720x400 70.08 
680x384 59.80 59.96 
576x432 75.00 75.00 70.00 60.06 
512x384 75.03 70.07 60.00 
416x312 74.66 
400x300 72.19 75.12 60.32 56.34 
320x240 72.81 75.00 60.05 
HDMI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
1920x1080 60.00*+ 50.00 59.94 59.93 
1920x1080i 60.00 50.00 59.94 
1680x1050 69.88 59.95 59.88 
1600x1024 60.17 
1400x1050 74.76 70.00 59.98 
1600x900 60.00 
1280x1024 75.02 60.02 
1440x900 59.89 
1280x960 60.00 
1360x768 59.80 59.96 
1280x800 59.91 
1152x864 75.00 75.00 70.00 60.00 
1280x720 60.00 50.00 59.94 
1024x768 75.05 60.04 75.03 70.07 60.00 
960x720 75.00 60.00 
928x696 75.00 60.05 
896x672 75.05 60.01 
960x600 60.00 
832x624 74.55 
960x540 59.99 
800x600 75.00 70.00 65.00 60.00 72.19 75.00 60.32 56.25 
840x525 74.96 69.88 60.01 59.88 
720x576 50.00 
800x512 60.17 
700x525 74.76 70.06 59.98 
720x480 60.00 59.94 
640x512 75.02 60.02 
720x450 59.89 
640x480 60.00 75.00 72.81 75.00 60.00 59.94 
720x400 70.08 
680x384 59.80 59.96 
576x432 75.00 75.00 70.00 60.06 
512x384 75.03 70.07 60.00 
416x312 74.66 
400x300 72.19 75.12 60.32 56.34 
320x240 72.81 75.00 60.05 
DP-1 disconnected (normal left inverted right x axis y axis)


> sudo lshw -C display *-display 
description: VGA compatible controller
product: GP107 [GeForce GTX 1050 Ti]
vendor: NVIDIA Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
configuration: driver=nouveau latency=0
resources: irq:44 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff

---

### Post by brutikk on 2017-09-24
Please let me know if there are more commands to run that would help you guys out.

---

