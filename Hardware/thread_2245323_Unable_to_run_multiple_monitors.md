---
title: "Unable to run multiple monitors"
date: 2014-09-22
forum: Hardware
---

### Post by Only1KW on 2014-09-22
Today, I've been trying to add a second monitor over DVI to my laptop running Ubuntu 14.04, with no luck.  Linux successfully detects that the monitor is attached along with all its config, but when I attempt to start it, I have issues.  On Unity, the screen toggles between powered on and in power-save mode every few seconds, and I never see an image on the screen.  One time right after a reboot I was able to get it to show up, but then I modified another config setting (changed the second monitor's position relative to the first) and it failed again, and restoring the previous configuration didn't bring it back.

I've also tried several other window managers, including lxde, xfce, and flashback.  lxde did allow the second monitor to show up, but I then tried to use the configuration tool to move its position relative to the primary monitor, but lxde did not respond to my requested changes.

Any ideas what I can try to get this to work?

```
------@Latitude-E7440:~$ lspci | grep VGA00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
```
xrandr when the second monitor was disabled:
```
------@Latitude-E7440:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
xrandr when the second monitor was enabled
```
------@Latitude-E7440:~$ xrandr
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by Only1KW on 2014-09-24
Anyone?  Is multi-monitors even supported in Ubuntu?

---

