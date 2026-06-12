---
title: "[SOLVED] Cannot change resolution or refresh rate intel 865 graphics"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by fowie on 2008-12-04
See [my other post]("http://ubuntuforums.org/showthread.php?p=6310093#post6310093") for my xorg.conf and Xorg.0.log
I need 1360x768 60Hz resolution (that's what worked in XP) but my only 1360x768 option is 75Hz which doesn't display on my LCD TV.  I'm trying to use xrandr, but this is all I get:
```

fowie@fowie-mc:~$ xrandr --newmode "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync
fowie@fowie-mc:~$ xrandr
Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 (normal left inverted right) 0mm x 0mm
   1600x1200      60.0* 
   1360x768       75.0  
   1024x768       75.0  
   800x600        75.0  
   640x480        75.0  
  1360x768_60.00 (0x69)   84.7MHz
        h: width  1360 start 1424 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
fowie@fowie-mc:~$ xrandr --addmode default 1360x768_60.00
fowie@fowie-mc:~$ xrandr
Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 (normal left inverted right) 0mm x 0mm
   1600x1200      60.0* 
   1360x768       75.0  
   1024x768       75.0  
   800x600        75.0  
   640x480        75.0  
   1360x768_60.00   60.0  
fowie@fowie-mc:~$ xrandr --output default --mode 1360x768_60.00
xrandr: Configure crtc 0 failed

```
Help, PLEASE!

---

### Post by Mark Phelps on 2008-12-05
Have you tried System --> Preferences --> Screen Resolution, selecting generic, clicking on wide screen, and selecting the resolution you want?

---

### Post by fowie on 2008-12-09
That option doesn't exist in XFCE, it's a gnome applet.  Regardless, I did solve the problem, though not in the way I would like.  It seems that Xorg does not do well detecting and using available resolution modes over an analog VGA connector.  My video card has DVI out and I was using a DVI-VGA adapter.  When I switched to a DVI-HDMI connector it came right up with plenty of options (including the 1360x768@60Hz)

---

