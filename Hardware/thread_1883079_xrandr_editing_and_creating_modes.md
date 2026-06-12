---
title: "xrandr editing and creating modes"
date: 2011-11-18
forum: Hardware
---

### Post by Scapegoat Technology on 2011-11-18
My main laptop runs on two screens. I setup an Ubuntu Tower to do testing and mundane tasks so I installed a switch to share the Dell E172fp (VGA1) and usb hub with my keyboard & mouse between the two. 

My laptop no longer detects VGA1's model and is using a ?generic? resolution range instead. How do I edit modes and remove the one I created?

My response has been to learn more about xrandr and how to use it to force an appropriate resolution or mode. The E172fp's Optimum resolution is 1280x1024 60Hz

with the command:

User@Computer:~$ xrandr

[B]What I started with
[/B]Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 4096 x 4096
VGA1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

[B]

With the switch[/B]
Screen 0: minimum 320 x 200, current 2304 x 800, maximum 4096 x 4096
VGA1 connected 1024x768+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

[B]
I attempted to create a mode and now have this to show for it:[/B]

user@computer:~$ xrandr --newmode VGA1 " 1280x1024" 60.00 1280 1024 800 640 768 600 480 -hsync +vsync

Screen 0: minimum 320 x 200, current 2304 x 800, maximum 4096 x 4096
VGA1 connected 1024x768+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)
  VGA1 (0xc7) 1280.0MHz
        h: width    60 start 1280 end 1024 total  800 skew    0 clock 1600.0KHz
        v: height  640 start  768 end  600 total  480           clock 3333.3Hz

---

### Post by Scapegoat Technology on 2011-11-18
Also, could someone please explain to me what all the digits mean in:

xrandr --newmode VGA1 " 1280x1024" **60.00 1280 1024 800 640 768 600 480** -hsync +vsync

I obviously screwed it up.

Thank you,
Fred

---

