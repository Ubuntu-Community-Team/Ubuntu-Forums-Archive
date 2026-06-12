---
title: "External monitor screen resolution issue"
date: 2008-12-10
forum: Hardware
---

### Post by davsinc2007 on 2008-12-10
I am a newbie.  I read through some threads and am still having difficulty getting 1600x1050 screen resolution on my external monitor.  I tried using xrandr to add the resolution but it still does not show up when I go to change my resolution.  Would appreciate any help.  I will paste my steps below:

dsinclai@dsinclai-laptop:~$ xrandr --newmode 1600x1050_60.00  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
dsinclai@dsinclai-laptop:~$ xrandr --addmode VGA 1600x1050_60.00dsinclai@dsinclai-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1600 x 2000
VGA connected 1400x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1600x1200      65.0     60.0  
   1600x1024      60.2  
   1400x1050      74.8*    70.0     60.0  
   1280x1024      75.0     60.0     60.0  
   1440x900       75.0     59.9     60.0  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1280x800       60.0  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
   1600x1050_60.00   60.0  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
  1600x1050_60 (0xc4)   85.9MHz
        h: width  1368 start 1440 end 1584 total 1800 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz

---

