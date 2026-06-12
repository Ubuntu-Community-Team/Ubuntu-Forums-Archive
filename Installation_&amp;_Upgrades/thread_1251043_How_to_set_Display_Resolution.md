---
title: "How to set Display Resolution"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by sixonqjz on 2009-08-27
I've install Ubuntu 9.04 and display resolution is 800x600. I want to set it 1024x768 but there is no choice...my display driver is NVDIA...but I don't know how to install it...the CD driver is Windows version....thank you...

---

### Post by pandabeer on 2009-08-27
Hello, you can install your drivers from the nvidia website
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

also you can use the restricted driver options in ubuntu
system->administration->restricted drivers

I guess it's like this (my ubuntu is in dutch so I'm not sure of the naming)


I hope I understood your question and that I might have helped you

---

### Post by rhythmiccycle on 2009-09-21
i'm  trying to use this code, but i'm getting stuck

i'm reading this page: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) 

and this page: [http://ubuntuforums.org/showthread.php?t=1112186](http://ubuntuforums.org/showthread.php?t=1112186)

this is what I tried
```

mrm@mrm-laptop:~$ xrandr | grep maximum
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1664
mrm@mrm-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1664
VGA connected (normal left inverted right x axis y axis)
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)
  1360x768_60.00 (0xd5)   84.8MHz
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
mrm@mrm-laptop:~$ man gtf
mrm@mrm-laptop:~$ gtf 1440 900 59.9

  # 1440x900 @ 59.90 Hz (GTF) hsync: 55.83 kHz; pclk: 106.29 MHz
  Modeline "1440x900_59.90"  106.29  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

mrm@mrm-laptop:~$ xrandr | grep maximum
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1664
mrm@mrm-laptop:~$ xrandr --addmode VGA 1360x768_60.00
mrm@mrm-laptop:~$ xrandr --output VGA --mode 1360x768_60.00
xrandr: screen cannot be larger than 1280x1664 (desired size 1360x800)
mrm@mrm-laptop:~$ 


```

How do i add virtual resoultion?

---

