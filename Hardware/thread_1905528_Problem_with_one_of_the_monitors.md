---
title: "Problem with one of the monitors"
date: 2012-01-07
forum: Hardware
---

### Post by coverup1128 on 2012-01-07
I have Ubuntu 11.04 running on Lenovo Thinkpad T420, with two monitors connected via an advanced port replicator. Monitor 1 is connected to the VGA port, Monitor 2 is connected using the DVI cable.

Here is the output of xrandr -q:

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 8192 x 8192
LVDS1 connected (normal left inverted right x axis y axis)
   1600x900       60.0 +
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0* 
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 connected 1680x1050+1280+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x720       50.0     60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
```
Every time I switch to the external monitors by pressing Fn+F7, the image on the VGA display comes up distorted. Also, despite "Same images on all screens" is unchecked,  the distorted screen is the mirror of the image on the DVI display (for some reason, it is reported as HDMI3).  

The only way to fix this is to turn the VGA display off through System -> Preferences -> Monitors, select 75Hz frequency, then turn the display back again. This produces extended desktop on both screens, as it should. 

On a distribution which uses xorg.conf I would simply try adding the correct modeline to xorg.conf. But on ubuntu, I could not even generate an xorg.conf file,
```
sudo X -configure
```
produced some errors and failed. Any suggestions please?

---

