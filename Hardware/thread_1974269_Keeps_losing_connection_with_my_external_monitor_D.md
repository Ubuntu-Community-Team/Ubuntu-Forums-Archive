---
title: "Keeps losing connection with my external monitor DisplayPort/HDMI, fine on VGA"
date: 2012-05-05
forum: Hardware
---

### Post by exacube on 2012-05-05
I own a Lenovo X220 and I am connecting my external DELL monitor via a DisplayPort (from laptop) -> HDMI cable, which is hooked up to a HDMI -> DVI adapter to the monitor.

When hooked up, xrandr shows that:
```
$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 277mm x 156mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

```

and then the connection "drops" -- monitor works and i can use it as secondary, but xrandr shows that HDMI1 is disconnected.  consequently, many applications focused on my monitor like Chrome and Flash keep displaying popups/fullscreen windows on my laptop screen.  xrandr shows this:

```
$ xrandr
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192
LVDS1 connected 1366x768+1920+0 (normal left inverted right x axis y axis) 277mm x 156mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
  1920x1080 (0xb7)  148.5MHz
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
```

My X220 has an Intel HD Graphics 3000.
When I connect using VGA (VGA on my laptop -> VGA on monitor), it works flawlessly.

I have two DisplayPort -> HDMI cables and this happens on both of them, so I'm not sure if it's the cable either..

Is this a driver issue?

My environment:

```
$ uname -a
Linux vardhan-ThinkPad-X220 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

Thanks!

---

