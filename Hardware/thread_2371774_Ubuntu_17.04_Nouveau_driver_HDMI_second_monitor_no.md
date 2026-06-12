---
title: "Ubuntu 17.04 Nouveau driver HDMI second monitor not detected, kernel 4.12"
date: 2017-09-18
forum: Hardware
---

### Post by brutikk on 2017-09-18
I recently did a purge of nvidia drivers and swapped back to nouveau.  However, my HDMI monitor is no longer detected.

When updating initramfs, I get a bunch of message like so:

> W: Possible missing firmware /lib/firmware/nvidia/gp10b/gr/fecs_inst.bin for module nouveauW: Possible missing firmware /lib/firmware/nvidia/gp10b/gr/fecs_bl.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gp10b/acr/ucode_load.bin for module nouveau
W: Possible missing firmware /lib/firmware/nvidia/gp10b/acr/bl.bin for module nouveau


output of xrandr:
> xrandrxrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080      0.00* 
   1280x1024      0.00  
   1024x768       0.00  
   800x600        0.00  
   640x480        0.00  

and output of sudo lshw -C display
> sudo lshw -C display
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GP107 [GeForce GTX 1050 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff


Any help resolving this issue is appreciated.

---

### Post by Autodave on 2017-09-18
I have never had any luck getting HDMI working w/o the correct driver.  Why did you remove the driver?  What driver was it? What model is your card?

---

### Post by Yellow Pasque on 2017-09-19
You need an updated linux-firmware package. Maybe grab the current one from artful: [https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.168_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.168_all.deb)

---

### Post by brutikk on 2017-09-19
> **Temüjin said:**
> You need an updated linux-firmware package. Maybe grab the current one from artful: [https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.168_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/linux-firmware_1.168_all.deb)
Out of curiosity, where did you see that I needed an updated linux firmware package?  This did fix the issue of the monitor not being detected, but now my monitors are acting as being mirrored even though I have turned off the mirrored display.  Specifically, when mirror displays is unchecked, I can move my mouse from monitor to monitor.  However, every window I open displays on both monitors.  When I have the display manager open, it claims both of my monitors are my main monitor.  I will close this thread and ask this question as a new post.

> xrandrScreen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DVI-D-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080     60.00*+  59.93  
   1680x1050     69.88    59.95    59.88  
   1600x1024     60.17  
   1400x1050     74.76    70.00    59.98  
   1280x1024     75.02    60.02  
   1440x900      74.98    59.89    59.90  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1280x800      59.91  
   1152x864      75.00    75.00    70.00    60.00  
   1024x768      75.05    60.04    75.03    70.07    60.00  
   960x720       75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   960x600       60.00  
   832x624       74.55  
   960x540       59.99  
   800x600       75.00    70.00    65.00    60.00    72.19    75.00    60.32    56.25  
   840x525       74.96    69.88    60.01    59.88  
   800x512       60.17  
   700x525       74.76    70.06    59.98  
   640x512       75.02    60.02  
   720x450       59.89  
   640x480       60.00    75.00    72.81    75.00    66.67    59.94  
   720x400       70.08  
   680x384       59.80    59.96  
   576x432       75.00    75.00    70.00    60.06  
   512x384       75.03    70.07    60.00  
   416x312       74.66  
   400x300       72.19    75.12    60.32    56.34  
   320x240       72.81    75.00    60.05  
HDMI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+  50.00    59.94    59.93  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     69.88    59.95    59.88  
   1600x1024     60.17  
   1400x1050     74.76    70.00    59.98  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1280x800      59.91  
   1152x864      75.00    75.00    70.00    60.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.05    60.04    75.03    70.07    60.00  
   960x720       75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   960x600       60.00  
   832x624       74.55  
   960x540       59.99  
   800x600       75.00    70.00    65.00    60.00    72.19    75.00    60.32    56.25  
   840x525       74.96    69.88    60.01    59.88  
   720x576       50.00  
   800x512       60.17  
   700x525       74.76    70.06    59.98  
   720x480       60.00    59.94  
   640x512       75.02    60.02  
   720x450       59.89  
   640x480       60.00    75.00    72.81    75.00    60.00    59.94  
   720x400       70.08  
   680x384       59.80    59.96  
   576x432       75.00    75.00    70.00    60.06  
   512x384       75.03    70.07    60.00  
   416x312       74.66  
   400x300       72.19    75.12    60.32    56.34  
   320x240       72.81    75.00    60.05  
DP-1 disconnected (normal left inverted right x axis y axis)


> sudo lshw -C display  *-display                 
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

> **Autodave said:**
> I have never had any luck getting HDMI working w/o the correct driver. Why did you remove the driver? What driver was it? What model is your card?

I had to remove the proprietary drivers because they didn't support kernel 4.12 yet, so I couldn't use my display at all.  The card is a GTX1050ti

---

### Post by Yellow Pasque on 2017-09-20
> **brutikk said:**
> Out of curiosity, where did you see that I needed an updated linux firmware package?

I got it from the output you gave, and then looked through the linux-firmware changelog to see which version added the appropriate files.

---

