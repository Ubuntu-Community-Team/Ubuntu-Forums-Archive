---
title: "Elitbook and DisplayPort - connects but isn't functional"
date: 2013-09-16
forum: Hardware
---

### Post by Klainn on 2013-09-16
I have a HP Elitebook 8200 with an intel graphics card and a DisplayPort on the back. I have a monitor connected to the vga port working fine but the monitor I have hooked to the DisplayPort displays a desktop image, but does not function fully. 

The displayport monitor draws a desktop but when I attempt to move my mouse to that new desktop I only get the extreme right edge of my vga desktop. So it's there, but completely unusable. The system seems to see it just fine, but for some reason I have no use out of it.

Some details:

dmesg:[   11.748005] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3

Xorg.0.log:[    20.924] (II) intel(0): Output HDMI1 has no monitor section
Xorg.0.log:[    21.428] (II) intel(0): EDID for output HDMI1
Xorg.0.log:[    21.428] (II) intel(0): Printing probed modes for output HDMI1
Xorg.0.log:[    21.476] (II) intel(0): Output HDMI1 connected
Xorg.0.log:[    21.476] (II) intel(0): Output HDMI1 using initial mode 1680x1050
Xorg.0.log:[    22.286] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event3)

I am using 13.04 64bit with Enlightenment.

Thanks for reading.

---

