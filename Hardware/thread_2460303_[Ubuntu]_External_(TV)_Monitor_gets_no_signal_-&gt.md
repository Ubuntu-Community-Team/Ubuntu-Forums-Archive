---
title: "[Ubuntu] External (TV) Monitor gets no signal -&gt; Ubuntu 20.04.2 LTS, i915"
date: 2021-04-06
forum: Hardware
---

### Post by mikethe1wheelnut on 2021-04-06
An external (TV) monitor connected via hdmi doesn't get a signal.  See the information provided.  I'll add more as I continue my research..

output of:
> lsb_release -a
> 
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal


output of:
> lshw -c video
> 
WARNING: you should run this program as super-user.
  *-display                 
       description: VGA compatible controller
       product: HD Graphics 5500
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:51 memory:f6000000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


output of:
> xrandr
> 
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1920x1080     60.00*+  59.97    59.96    59.93    48.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 885mm x 498mm
   1360x768     104.59 +
   1920x1080     60.00*   50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     60.02  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00    50.00  
   720x576i      50.00  
   720x480       60.00    59.94    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    60.00    59.94  
   720x400       70.08  
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)



and a screen-shot of the display switcher:


[ATTACH=CONFIG]288227[/ATTACH]

I also know now that Fn+F8 are the hotkeys for switching display modes, but in this case, it has no effect.

..so.., how do I get a signal to the TV screen?  Will keep researching, post the answer if I find it..  I've tried re-booting with the screen already plugged in.

Ok, I have a suspicion that the answer to this [https://unix.stackexchange.com/questions/353626/external-screen-recognized-but-black](https://unix.stackexchange.com/questions/353626/external-screen-recognized-but-black) question is what I need.  It looks like this monitor isn't programmed to accept hdmi input, even if it has a place to plug it in, so I'll need to get an html/vga adaptor..

---

### Post by CelticWarrior on 2021-04-06
Welcome.

Try selecting the HDMI input on the TV. It seldom is automatic. And make sure the resolution is supported.
This has nothing to do with Ubuntu.

---

