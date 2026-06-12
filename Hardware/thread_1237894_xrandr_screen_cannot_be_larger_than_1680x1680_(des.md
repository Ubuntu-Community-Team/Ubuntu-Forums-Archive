---
title: "xrandr: screen cannot be larger than 1680x1680 (desired size 3360x1050)"
date: 2009-08-11
forum: Hardware
---

### Post by cevjr on 2009-08-11
I have two ViewSonic monitors that can display 1680x1050 each
I want to use xrandr to extend my desktop to 3360x1050.

It has an intel dual core 2 and integrated intel GMA x4500 grpahics.
and I am running Ubuntu 9.04 (Jaunty)

I know the extended view is working under Vista.

But linux is limiting me:
$ xrandr --output HDMI-2 --auto --right-of VGA
xrandr: screen cannot be larger than 1680x1680 (desired size 3360x1050)

I have tried editing the xorg.conf as the many forums suggest but I am getting nowhere.

Supporting info below
------------------------------------------------------
#####lspci | grep Graphics######

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset     Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

#### xrandr -q #####

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
VGA connected 1680x1050+0+0 (normal left inverted right x axis y axis) 495mm x 291mm
   1680x1050      60.0*+   60.0* 
   1600x1200      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
HDMI-2 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 495mm x 291mm
   1680x1050      60.0*+   59.9  
   1600x1200      60.0  
   1400x1050      59.9  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
   640x400        70.0  

#### xorg.conf  #### 

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

