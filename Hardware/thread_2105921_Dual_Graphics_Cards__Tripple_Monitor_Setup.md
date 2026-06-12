---
title: "Dual Graphics Cards / Tripple Monitor Setup"
date: 2013-01-17
forum: Hardware
---

### Post by geudrik on 2013-01-17
I've seen many a thread talking about how to get multiple monitors set up, but nothing so far has worked for me. At best, I've gotten two out of three monitors. I'm in the middle of a migration that hinges around getting 3d accelleration working across all three displays.

I have an nVidia GTX 480 and a GTX 670 for cards. No onboard video. Proprietary drivers have been installed. When I open All Settings -> Displays, only one display is shown (GPU-0, DFP-0). 

In the X-Server settings, I can see all three as being detected, but only one is active. So, I've then tried to set things up manually, also to no avail (and yes, I set iommu=pt in grub).

```

sudo nvidia-xconfig --base-mosaic --metamodes="GPU-1.DFP-0: 1920x1200+0+0, GPU-0.DFP-0: 1920x1080+1920+0, GPU-0.DFP-1: 1920x1080+3840+0"
```

After running this command, nothing changes (as expected). Once I reboot, it appears the X crashes (bright red screen on the primary display) before it reboots. It reboots normally, and X starts as if nothing changed (eg: rolled back to a backup config). 

Which leads me to believe that I'm buggering up the xconfig command. Here are the cards...

```

Number of GPUs: 2
GPU #0:
Name : GeForce GTX 670
PCI BusID : PCI:1:0:0
Number of Display Devices: 2
Display Device 0 (DFP-0):
EDID Name : Ancor Communications Inc ASUS VE278
Minimum HorizSync : 24.000 kHz
Maximum HorizSync : 92.000 kHz
Minimum VertRefresh : 50 Hz
Maximum VertRefresh : 85 Hz
Maximum PixelClock : 170.000 MHz
Maximum Width : 1920 pixels
Maximum Height : 1080 pixels
Preferred Width : 1920 pixels
Preferred Height : 1080 pixels
Preferred VertRefresh : 60 Hz
Physical Width : 600 mm
Physical Height : 340 mm
Display Device 1 (DFP-1):
EDID Name : Ancor Communications Inc VE228
Minimum HorizSync : 30.000 kHz
Maximum HorizSync : 83.000 kHz
Minimum VertRefresh : 50 Hz
Maximum VertRefresh : 76 Hz
Maximum PixelClock : 170.000 MHz
Maximum Width : 1920 pixels
Maximum Height : 1080 pixels
Preferred Width : 1920 pixels
Preferred Height : 1080 pixels
Preferred VertRefresh : 60 Hz
Physical Width : 480 mm
Physical Height : 270 mm
GPU #1:
Name : GeForce GTX 480
PCI BusID : PCI:2:0:0
Number of Display Devices: 1
Display Device 0 (DFP-0):
EDID Name : LG Electronics W2600
Minimum HorizSync : 30.000 kHz
Maximum HorizSync : 83.000 kHz
Minimum VertRefresh : 56 Hz
Maximum VertRefresh : 75 Hz
Maximum PixelClock : 170.000 MHz
Maximum Width : 1920 pixels
Maximum Height : 1200 pixels
Preferred Width : 1920 pixels
Preferred Height : 1200 pixels
Preferred VertRefresh : 60 Hz
Physical Width : 550 mm
Physical Height : 340 mm

```

Given that, from left to right, my monitor display is as follows...
[ LG W2600] - [ Asus VE278 ] - [ Asus VE228 ]

Can anyone shed any light at all on this for me? I'm stumped.. :)

---

