---
title: "Térrible Monitor AOC Resolution in Precise Pangolin"
date: 2012-11-03
forum: Hardware
---

### Post by isabelgobbo on 2012-11-03
After I bought a monitor AOC LED 22", I had to reinstall Ubuntu 12.04 and tried to use the drivers available in the system to VGA, NVIDIA, but resolution becomes at 1024x768 or worse.

Now the active driver It's nvidia-current-updates 304.42 version and also installed the nvidia-current 295.40 version.

My monitor is AOC LED 22 FULL HD LE22H138 PR.
It supports resolution up to 1920 x 1080 pixels. Has 525 mm wide, 351 mm high and 101.8 depth. It has 22-inch and 16:9 formats accept with total fulfillment of the screen and 4:3 for viewing on older formats.

My hardware:

Desktop PC: Asus P5KPL MB, Procesador Intel Core 2 Duo E7400,
1st HD 500 GB Seagate Sata II, 2nd HD 500GB Sata II, Vga GeForce 7300 LE, 2GB DDR2 667, LG GWA-4161B DVDRRW, Corsair VX 450W Power, LED Monitor AOC 22 LE22H138. OS: Ubuntu 12.04, Ubuntu 11.10 and Windows 7 Home Premium 32-bit.

```
xrandr
```
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 4096 x 4096
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   576x432       120.1  
   512x384       120.0  
   400x300       144.4    120.6    112.7  
   320x240       120.1  
DVI-I-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
  1360x768 (0x25b)   85.5MHz
        h: width  1360 start 1424 end 1536 total 1792 skew    0 clock   47.7KHz
        v: height  768 start  771 end  777 total  795           clock   60.0Hz

I already search for answer in many places and when I used a script, the graphic interface disable.:( ](*,)

Sorry bad english, I am from Brazil.:(

---

### Post by grahammechanical on 2012-11-03
How do you know that this is true?

> It supports resolution up to 1920 x 1080 pixels.

xrandr is saying that the current resolution is

> current 1360 x 768

It also saying that the maximum is

> maximum 4096 x 4096

but do not try to set the resolution to that setting. On my machine xrandr says my maxmium is

> maximum 8192 x 8192

This is on a 20 inch HD TV/monitor but the manufacturers set up guide says that the optimum (best or suitable) resolution is 1680 x 1050 and that is the resolution that is set whether I use the Nvidia driver or Nouveau.

1360 x 768 might be the optimum resolution for that screen. When we boot the Xserver reads a configuration file in the monitor. It gets its resolution settings from the monitor.

Regards.

---

### Post by isabelgobbo on 2012-11-03
More message errors:
&#8226; MetaMode 6 of Screen 0  does not have an active display device.

&#8226; MetaMode 6 of Screen 0 is the same as MetaMode 4.  All MetaModes must be unique.

&#8226; MetaMode 7 of Screen 0  does not have an active display device.

&#8226; MetaMode 7 of Screen 0 is the same as MetaMode 4.  All MetaModes must be unique.

&#8226; MetaMode 8 of Screen 0  does not have an active display device.

&#8226; MetaMode 8 of Screen 0 is the same as MetaMode 4.  All MetaModes must be unique.

&#8226; MetaMode 9 of Screen 0  does not have an active display device.

&#8226; MetaMode 9 of Screen 0 is the same as MetaMode 4.  All MetaModes must be unique.

GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Nenhuma interface "org.gnome.SettingsDaemon.XRANDR_2" no objeto no caminho /org/gnome/SettingsDaemon/XRANDR

I get now resolution 1920x1080 but it is too high and only will last until my next start up.

now,

command: xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 4096 x 4096
VGA-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1440x900       59.9  
   1360x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI-I-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)

---

### Post by isabelgobbo on 2012-11-24
The resolution 1360x768       60.0 :  in this resolution only part of the screen is visible.
In all resolutions, the appearance is full of bugs, do not appear boxes for login, passwords and other things, the framework of the text is very bad especially in browsers.
Now I'm using 1440x900 which I have to choose every time I start Ubuntu 12.04 in nvidia-settings.
 ```
 xrandr
```
Screen 0: minimum 8 x 8, current 1440 x 900, maximum 4096 x 4096
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       75.0 +   70.1     60.0  
   1920x1200      60.0  
   1920x1080      59.9  
   1792x1344      60.0  
   1680x1050      74.9     69.9     60.0     59.9  
   1600x1200      65.0     60.0  
   1600x1024      60.2  
   1440x900       59.9* 
   1400x1050      74.8     70.0     60.0  
   1360x768       60.0     59.8  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0     75.0     70.0     60.0  
   960x600       120.0  
   960x540       120.0  
   896x672       120.0  
   840x525       149.9    139.8    120.0    119.8  
   832x624        74.6  
   800x600       130.0    120.0     75.0     72.2     60.3     56.2  
   800x512       120.3  
   720x450       119.8  
   680x384       119.9    119.6  
   640x512       150.0    120.0  
   640x480       120.0     75.0     72.8     59.9  
   576x432       150.0    150.0    140.0    120.1  
   512x384       150.1    140.1    120.0  
   416x312       149.3  
   400x300       150.2    144.4    120.6    112.7  
   320x240       150.0    145.6    120.1  
DVI-I-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)

---

