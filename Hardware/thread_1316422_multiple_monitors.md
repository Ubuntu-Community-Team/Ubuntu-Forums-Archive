---
title: "multiple monitors"
date: 2009-11-05
forum: Hardware
---

### Post by barna on 2009-11-05
Hi,
Can somebody explain how to make a multiple-monitor setup (where my screen is spread across several monitors)?

I tried to play with xrandr:
```

xrandr --output VGA-0 --left-of LVDS
xrandr: screen cannot be larger than 1440x1440 (desired size 2048x768)

```

Indeed, xrandr -q reports:
```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1440 x 1440
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0*
   1400x1050      60.0
   1280x1024      75.0     60.0
   1440x900       59.9
   1280x960       60.0
   1280x800       59.8
   1152x864       75.0     70.0
   1280x720       60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     59.9
   720x400        70.1
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm panning 1024x768+0+0
   1024x768       61.3*+
   800x600        59.9
   640x480        59.4
S-video disconnected (normal left inverted right x axis y axis)

```

So from the first line it seems that my screen is limited to 1440x1440 max. Why? How can I make it larger?

In KDE's System Settings/Display/Multiple monitors I have an error message:
This module is only for configuring systems with a single desktop spread across multiple monitors. You do not appear to have this configuration.
So how can I have this configuration? 

I have libxinerama1 installed. Should it be specifically enabled? Where?
Here somebody is saying that xinerama is deprecated:
[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/403610](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/403610)
Are xrandr and xinerama two exclusive tools, or they complete each other?

Some people suggest that I should edit xorg.conf, adding a 'Virtual' line to the screen section, however, I would like to avoid this (by the way I don't even find the /etx/X11/xorg.conf, X seems to be using an automatic dynamic configuration...).


Total confusion. 
Any help is appreciated. Thanks

---

### Post by Tallivant on 2009-11-30
What graphics card are you using?
You should be able to do the whole thing by editing your xorg.conf file
try "sudo gedit /etc/X11/xorg.conf"

---

### Post by Gralgrathor on 2010-01-23
Same problem here. Could find no useable workarounds. I have a HP flaptop with intel graphics, a second monitor to my VGA out, registered as VGA1 in the settings. The dual display setup screen reports "You do not appear to have this config". My system does not use NVIDIA, nor is there a /etc/X11/xorg.conf file to edit.

Finally, I typed this:

```
# xrandr --output LVDS1 --mode 1280x800
# xrandr --output VGA1 --mode 1280x1024
# xrandr --output VGA1 --pos 1280x0
```

Which works.

Edit: until the next time you login. Perhaps I should add these lines to the boot sequence.

---

