---
title: "gnome-display-properties wrongly detects LG42&quot;  display size"
date: 2009-10-02
forum: Hardware
---

### Post by mika_buntu on 2009-10-02
Hi everyone

I have the following setup:
ubuntu 9.04
ati 3600HD 
Samsung 22 LCD monitor, connected via DVI
LG 42 TV, connected via DVI as second display

all works fine in default config, except that the LG 42 is detected as a 52" display, and so the desktop is larger than the actual screen. if I try to play movies on it, I only see about 60%-70% of the image.

how can I solve this?
thanks a bunch! :D

$ xrandr -q
Screen 0: minimum 320 x 200, current 3600 x 1080, maximum 3600 x 1080
DVI-1 connected 1680x1050+0+30 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
DVI-0 connected 1920x1080+1680+0 (normal left inverted right x axis y axis) 1150mm x 650mm
   1920x1080      60.0*+
   1280x1024      60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   720x400        70.1

---

### Post by nixscripter on 2009-10-03
What is the contents of your **/etc/X11/xorg.conf** file? If it doesn't specify screen sizes, there may be a way to work around it with a Virtual Screen size.

(Also, it makes technical posts more readable to put [code] forum tags around them.)

---

