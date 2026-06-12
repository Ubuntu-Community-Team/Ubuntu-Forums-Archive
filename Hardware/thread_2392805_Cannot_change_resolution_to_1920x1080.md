---
title: "Cannot change resolution to 1920x1080"
date: 2018-05-25
forum: Hardware
---

### Post by marko-obert on 2018-05-25
Hi, 

I have a 4k-screen from Acer model XB281HK. 

Unfortunately this screen has only four native resolutions 640x480, 800x600, 1024x768 and 3840x2160.  

 
 This causes, that I cannot select in Gnome and in some games a different resolution, e.g. 1920x1080.


I tried:  
 1.) .. to add with xrandr --addmode a resolution, but I get &#8220;X Error of failed request: BadMatch&#8221;.
 2.) I added the Option "ModeValidation" "AllowNonEdidModes" to the xorg.conf and restart X11. This enables me to choose the desired resolution, but my screen turns black when I choose 1920x1080.

 
 Additional information:
 - ubuntu 18.04 (gnome)
 - nvidia GTX 1080 (driver 396.24)
 

Any ideas?

---

### Post by marko-obert on 2018-05-26
Finally managed to add some screenshots:

Gnome-settings only shows the native resultions:
[ATTACH=CONFIG]279867[/ATTACH]

Same as xrandr:

```
xrandr
Screen 0: minimum 8 x 8, current 3840 x 2160, maximum 32767 x 32767
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 621mm x 341mm
   3840x2160     60.00*+  29.98    24.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
DP-5 disconnected (normal left inverted right x axis y axis)

```


Nvidia settings allows me to choose 1920x1080 (**scaled**). This solve the issue, if I want to use a different resolution on my desktop, but does not help much in games which only allows choose native resolutions.

[ATTACH=CONFIG]279866[/ATTACH]

Kind regards

---

