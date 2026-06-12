---
title: "Not recognizing three screens on Ubuntu 14.04, Intel HD 4600"
date: 2015-01-15
forum: Hardware
---

### Post by manuel23 on 2015-01-15
Hi,

I installed Ubuntu 14.04 on my new computer L440, which is able to handle three screens, which means for me the internal and two external monitors. First starting, there were only two displays that were recognized as NOT mirrored, the second was a mirror of the third external monitor:

1: Internal Display: independent screen
2: Big external screen: independent HDMI
3: small external screen: mirror of 2 VGA

Xrandr -q gives following output, when 3. is not connected:

```
Screen 0: minimum 320 x 200, current 3520 x 1080, maximum 32767 x 32767
eDP1 connected 1600x900+1920+180 (normal left inverted right x axis y axis) 309mm x 174mm
   1600x900       60.0*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080      60.0*+   50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1920x1080i     60.1     50.0     60.0  
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1366x768       59.8  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0     50.0     59.9  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        75.0     72.8     66.7     60.0     59.9  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

this is correct, but when connecting 3. it gives following output:

```
Screen 0: minimum 320 x 200, current 3280 x 1050, maximum 32767 x 32767
eDP1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1600x900       60.0*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP2 connected 1680x1050+1600+0 (normal left inverted right x axis y axis) 450mm x 300mm
   1680x1050      60.0*+
   3360x1050      60.0  
   2560x1024      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0     59.9  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

Means for me it now uses the 3. as second screen and mirrors it to 2, without recognizing the screen 2. By the way there is no LVDS any more, this seems to be eDP1 now.

I tried installing intel driver for linux, but didnt help. I searched for /etc/X11/xorg.conf or xorg.conf.d, but it doesnt exist.
As I already read, maybe I would have to enlarge the total screen range, but how without any xorg.conf?

Can anyone help me with that? My aim is to have three screen independently, one aside the other.

---

### Post by Sally_Joshua on 2015-01-15
use Sapphire HD6770 fleX Edition card or any of the ATI "Eyefinity" cards. The Sapphire fleX cards can work with 2xDVI + 1xHDMI (which can be easily converted to DVI - in fact they supply the adapter in the box). This card supports 3 monitors with the open source "radeon" driver without any need to create or edit an xorg.conf file. Standard xrandr tools work with it. 3D acceleration is active (enough to run glxgears and compositing at least) and no xinerama is needed

---

### Post by QIII on 2015-01-15
Suggesting that the user purchase a new card does not address their problem.

Please keep the thread related to the problem at hand.

---

### Post by manuel23 on 2015-01-15
Yes, unfortunately this doesnt help, because its a laptop and theres no way to replace the card easily.

By the way the intel hd 4600 is able to handle three screens, because it works on windows and it was one reason to buy it.

---

