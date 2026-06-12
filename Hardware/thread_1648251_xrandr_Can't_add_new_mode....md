---
title: "xrandr: Can't add new mode..."
date: 2010-12-18
forum: Hardware
---

### Post by samialtas on 2010-12-18
After enabling NVIDIA drivers for my **9600M GS** in Ubuntu 10.10, Ubuntu sets monitor refresh rate to 50 Hz. When I try to change it to 60 Hz, I get this error:

**CVT Output**

$ cvt 1280 800

1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz Modeline "1280x800_60.00" 83.50 1280 1352 1480 1680 800 803 809 831 -hsync +vsync

**xrandr Error Message**

xrandr --newmode "1280X800_60.00" 83.50 1280 1352 1480 1680 800 803 809 831 -hsync +vsync

xrandr: Failed to get size of gamma for output default
X Error of failed request: BadName (named color or font does not exist)
Major opcode of failed request: 154 (RANDR)
Minor opcode of failed request: 16 (RRCreateMode)
Serial number of failed request: 19
Current serial number in output stream: 19

---

### Post by IcarusR on 2010-12-18
Try using a lower case x in your resolution ie like this

```
xrandr --newmode "1280[COLOR="Red"]x[/COLOR]800_60.00" 83.50 1280 1352 1480 1680 800 803 809 831 -hsync +vsync
```

---

### Post by samialtas on 2010-12-19
> **IcarusR said:**
> Try using a lower case x in your resolution ie like this

```
xrandr --newmode "1280[COLOR="Red"]x[/COLOR]800_60.00" 83.50 1280 1352 1480 1680 800 803 809 831 -hsync +vsync
```

No luck again. I get the same error:

```
xrandr: Failed to get size of gamma for output default
```

---

### Post by efflandt on 2010-12-19
xrandr might work with default nouveau driver (dib't know), but I know it does NOT work properly with nvidia drivers.  For example if I simply type xrandr, the first part of it shows this

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0*    51.0     52.0     53.0     54.0     55.0  
   1680x1050      56.0     57.0  
   1600x1024      58.0  
   1440x900       59.0  
   1400x1050      60.0     61.0     62.0  
   1360x768       63.0     64.0  
   1280x1024      65.0     66.0     67.0  
   1280x960       68.0     69.0  
   1280x720       70.0     71.0  
...
```The * indicates that xrandr thinks I am currently connected at 50 Hz and does not even show a 60 Hz mode, but Nvidia X Server Settings (nvidia-settings) correctly shows it is currently 60 Hz.  And 720p HDTV modes 1360x768 or 1280x720 which it can do fine would also be 60 Hz.  So you probably need to figure out how to plug a modeline into /etc/X11/xorg.conf, but not sure exactly how or where to plug that into xorg.conf because I have not had to do that.  Although, I have used xrandr in scripts to set modes for Intel and old legacy ATI with default video drivers (external VGA display on laptops).

Using DVI to HDMI or HDMI, my xorg.conf is the minimal default.  If you use VGA, X often only comes up with its list of default video modes, which may not include the resolution you need.  This is something from nvidia which I assume goes in the Screen section [http://http.download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-j.html](http://http.download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-j.html)

---

### Post by samialtas on 2010-12-20
> **efflandt said:**
> xrandr might work with default nouveau driver (dib't know), but I know it does NOT work properly with nvidia drivers.  For example if I simply type xrandr, the first part of it shows this

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0*    51.0     52.0     53.0     54.0     55.0  
   1680x1050      56.0     57.0  
   1600x1024      58.0  
   1440x900       59.0  
   1400x1050      60.0     61.0     62.0  
   1360x768       63.0     64.0  
   1280x1024      65.0     66.0     67.0  
   1280x960       68.0     69.0  
   1280x720       70.0     71.0  
...
```The * indicates that xrandr thinks I am currently connected at 50 Hz and does not even show a 60 Hz mode, but Nvidia X Server Settings (nvidia-settings) correctly shows it is currently 60 Hz.  And 720p HDTV modes 1360x768 or 1280x720 which it can do fine would also be 60 Hz.  So you probably need to figure out how to plug a modeline into /etc/X11/xorg.conf, but not sure exactly how or where to plug that into xorg.conf because I have not had to do that.  Although, I have used xrandr in scripts to set modes for Intel and old legacy ATI with default video drivers (external VGA display on laptops).

Using DVI to HDMI or HDMI, my xorg.conf is the minimal default.  If you use VGA, X often only comes up with its list of default video modes, which may not include the resolution you need.  This is something from nvidia which I assume goes in the Screen section [http://http.download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-j.html](http://http.download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-j.html)

I suppose with some graphics cards like my NVIDIA 9600M GS, NVIDIA driver work with xrandr 1.2 even though I have xrandr 2.0 in my system.

I checked out the link that you sent and it didn't work. Thanks, by the way..

---

