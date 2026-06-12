---
title: "Dual monitors, dual graphics (GPU+iGPU)"
date: 2013-06-14
forum: Hardware
---

### Post by PsYcHoTiC_MaDmAn on 2013-06-14
brief summary, have a new 1440p monitor that requires a DVI-D port, unfortunately thats also the VGA port that I used for my old 1080p monitor. (note both monitors have a single input only, so cant get around it that way)

computer specs are, i5 3570k, Asus P8Z77-V LX, 8GB DDR3, XFX HD 7950 DD.

spent most of the evening trying to get it to work, then trying to recover ubuntu (first failsafex screwed up and wouldn't display anything but error messages, then grub ended up FUBAR) so have a clean install of ubuntu 12.04 (all up to date)

now I've managed to enable it in windows 7 (via lucid Virtu MVP) and since doing that there is a change hardware wise, the monitor thinks its recieving a signal (screen is active, but black screen) however its not detected in ubuntu as a second monitor.

any thoughts on enabling this, (only thing, having done clean install, there are no intel graphics drivers installed)

---

### Post by PsYcHoTiC_MaDmAn on 2013-06-15
quick update.

second screen displays the startup/shut-down screens, so its sort of working there.

however it does not detect any other screens within ubuntu itself.

possibly useful for a fix (was thinking maybe xorg.conf file)

output from $ lshm -c video
```
 *-display               
       description: VGA compatible controller
       product: Tahiti PRO [Radeon HD 7950]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:48 memory:e0000000-efffffff memory:f7c00000-f7c3ffff ioport:e000(size=256) memory:f7c40000-f7c5ffff
  *-display
       description: Display controller
       product: Ivy Bridge Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f7800000-f7bfffff memory:d0000000-dfffffff ioport:f000(size=64)
```

and $ xrandr (done with and without discrete GPU)
```
Screen 0: minimum 320 x 200, current 2560 x 1440, maximum 2560 x 2560
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
DFP3 disconnected (normal left inverted right x axis y axis)
DFP4 disconnected (normal left inverted right x axis y axis)
DFP5 disconnected (normal left inverted right x axis y axis)
DFP6 disconnected (normal left inverted right x axis y axis)
DFP7 disconnected (normal left inverted right x axis y axis)
DFP8 disconnected (normal left inverted right x axis y axis)
DFP9 disconnected (normal left inverted right x axis y axis)
DFP10 disconnected (normal left inverted right x axis y axis)
DFP11 connected 2560x1440+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440      60.0*+
   1800x1440      60.0  
   1856x1392      60.0  
   1792x1344      60.0  
   1920x1200      60.0  
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      60.0  
   1440x900       60.0  
   1280x960       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.0  
   640x480        60.0  
CRT1 disconnected (normal left inverted right x axis y axis)


Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080      60.0*+
   1280x1024      60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
```

---

### Post by martin13 on 2013-08-12
Hi PsYcHoTiC_MaDmAn,

Have you found a solution for your problem yet? I have the same problem.
My system is i5 3570k, AsusP8B75-M it has an integrated graphics card, which I enabled in the setup, and a NVidia GT610.
I want to use them both to have a 3 monitor setup. When Ubuntu starts/stops I can see the ubuntu logo in the 3rd screen that is connected to the integrated graphics card, the other two screens connected to the Nvidia card work well. But while I'm in Ubuntu I can't enable the 3rd screen. Spent a few hours with this and I don't know what else to try.

Martin

---

