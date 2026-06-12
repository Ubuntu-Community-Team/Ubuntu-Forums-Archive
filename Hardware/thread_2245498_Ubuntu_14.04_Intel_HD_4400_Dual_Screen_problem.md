---
title: "Ubuntu 14.04 Intel HD 4400 Dual Screen problem"
date: 2014-09-24
forum: Hardware
---

### Post by metanoya on 2014-09-24
Hi guys,

I've got a dual screen setup that used to work fine until about 2 days ago. I have a Dell u2412m monitor as primary display (connected via DVI) and an older Acer monitor as a secondary (connected via CRT). At the Ubuntu login screen, the secondary monitor does not show anything (it used to be that both of them showed the login screen). Also, after logging in, if I unplug and plug the secondary monitor back in, it stays on for a couple of seconds and turns off again. The secondary monitor does display text while the computer is booting, so it seems to work.

Here are some outputs:

xrandr -q

```

Screen 0: minimum 320 x 200, current 3360 x 1200, maximum 32767 x 32767
VGA1 connected 1440x900+1920+300 (normal left inverted right x axis y axis) 410mm x 256mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
HDMI1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1680x1050      59.9  
   1280x1024      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

xrandr -q --q1

```

 SZ:    Pixels          Physical       Refresh
*0   1920 x 1200   ( 518mm x 324mm )  *60  
 1   1600 x 1200   ( 518mm x 324mm )   60  
 2   1680 x 1050   ( 518mm x 324mm )   60  
 3   1280 x 1024   ( 518mm x 324mm )   60  
 4   1280 x 960    ( 518mm x 324mm )   60  
 5   1024 x 768    ( 518mm x 324mm )   60  
 6    800 x 600    ( 518mm x 324mm )   60  
 7    640 x 480    ( 518mm x 324mm )   60  
 8    720 x 400    ( 518mm x 324mm )   70  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis

```

tail -10 /var/log/Xorg.0.log

```

[   121.501] (II) intel(0): resizing framebuffer to 3360x1200
[   121.501] (II) intel(0): switch to mode 1440x900@59.9 on VGA1 using pipe 1, position (0, 0), rotation normal, reflection none
[   121.529] (II) intel(0): switch to mode 1920x1200@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[   121.653] (II) intel(0): switch to mode 1440x900@59.9 on VGA1 using pipe 1, position (1920, 300), rotation normal, reflection none
[   804.940] (II) intel(0): resizing framebuffer to 1920x1200
[   804.940] (II) intel(0): switch to mode 1920x1200@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[   813.557] (II) intel(0): resizing framebuffer to 3360x1200
[   813.557] (II) intel(0): switch to mode 1920x1200@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[   813.576] (II) intel(0): switch to mode 1920x1200@60.0 on HDMI1 using pipe 1, position (0, 0), rotation normal, reflection none
[   813.713] (II) intel(0): switch to mode 1440x900@59.9 on VGA1 using pipe 0, position (1920, 300), rotation normal, reflection none

```

Any help would be much appreciated.

---

### Post by metanoya on 2014-10-01
Never mind, turns out the old screen is dying. Tested it in Windows and I get the same problem.

---

### Post by Vladlenin5000 on 2014-10-02
Please mark this thread as solved so others can benefit from your experience.

PS - Here's a valuable lesson for the future. Whenever some hardware suddenly and unexpectedly fails, albeit partially, and no significant changes were made in the OS, always troubleshoot the hardware first.

---

