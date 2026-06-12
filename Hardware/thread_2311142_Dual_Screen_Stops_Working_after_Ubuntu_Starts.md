---
title: "Dual Screen Stops Working after Ubuntu Starts"
date: 2016-01-24
forum: Hardware
---

### Post by cirelosborn on 2016-01-24
I attached a second screen to my laptop and everything worked beautifully.  After an update and restart the dual screen shows up for the bios and grub, but once Ubuntu starts the second screen loses the signal.  It's connected VGA.  I looked at the displays settings and it shows three monitors (Built-in, unknown, unknown).  I have no idea were the third monitor came from.  The proper second monitor only shows up as an unknown, I can unplug and replug and still shows up as unknown with very limited resolutions.

Here is my xrandr:

```
Screen 0: minimum 320 x 200, current 1440 x 1476, maximum 4096 x 4096LVDS-1 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 367mm x 229mm
   1440x900       60.0*+
   1152x864       60.0  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 connected (normal left inverted right x axis y axis)
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
TV-1 connected 720x576+93+900 (normal left inverted right x axis y axis) 0mm x 0mm
   720x576        50.0*+
   1024x768       50.0  
   800x600        50.0  
   720x480        50.0  
   640x480        50.0  
   400x300        50.0  
   320x240        50.0  
   320x200        50.0 
``` 

I don't know what TV-1 is.

I've tried other video drivers

```
== /sys/devices/pci0000:00/0000:00:12.0 ==vendor   : NVIDIA Corporation
model    : C67 [GeForce 7150M / nForce 630M]
modalias : pci:v000010DEd00000531sv0000103Csd000030CFbc03sc00i00
driver   : nvidia-304 - distro non-free recommended
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-173 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin



```

But the Open source driver is the only one that shows a GUI.

Can any one help, please?

---

