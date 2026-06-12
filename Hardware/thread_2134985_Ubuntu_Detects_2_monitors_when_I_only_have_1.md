---
title: "Ubuntu Detects 2 monitors when I only have 1"
date: 2013-04-12
forum: Hardware
---

### Post by HomeTheaterGuy on 2013-04-12
Ubuntu Detects 2 monitors when I only have 1. This causes an issue when booting up because it's detecting 2 monitors and by default it is mirroring the display; which is causing a distorted picture since it's trying to create a mirror image on 1 display. xrandr output.... The VGA1 is the phantom monitor and I need to remove it so it boots to LVDS1 and NOT mirrored. Any suggestions on how to permanently remove VGA1?
:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 connected (normal left inverted right x axis y axis)
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080      59.6*+
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

---

### Post by HomeTheaterGuy on 2013-04-12
Forgot to add that I'm on 12.10

---

### Post by HomeTheaterGuy on 2013-04-19
This seems to be an issue with certain motherboards that have an HDMI and a Display Port. I figured out that either my Gateway ZX6800 Touch-Screen is using a certain Laptop motherboard with the on-board Intel HD chipset that supports this or it is seeing the IR Blaster or TV Tuner and driving it as a monitor.

Either way the fix is: Edit /etc/default/grub add "video=VGA-1:d" between the quotes in the GRUB_CMDLINE_LINUX line update-grub

***Look in /sys/class/drm for a list of your computers outputs.Mine was labelled as "card0-VGA-1". Just remove the "card0-" and that's the name of the output in question.***

---

