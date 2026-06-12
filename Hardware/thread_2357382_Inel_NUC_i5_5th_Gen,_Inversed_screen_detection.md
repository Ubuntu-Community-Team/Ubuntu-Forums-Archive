---
title: "Inel NUC i5 5th Gen, Inversed screen detection"
date: 2017-04-01
forum: Hardware
---

### Post by levynger on 2017-04-01
I have a wired situation,  i have installed ubuntu desktop 16.10 on i5 5th gen NUC (GMA 6000), which conneted to my Leaving Room Samsung TV using Native HDMI output.
i'm having some issues with the output, and sometimes error "could not set configuration for crtc" with error code 63, the display vanishes from the displays of the unity and kodi doesnt show (although work with some errors in its logs - irrelevant at the moment)

i have tested xrandr output, and found out that when the TV is off (stanby), the xrander detects the screen as connecrted.
```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192HDMI-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 1209mm x 680mm
   1920x1080i    60.00*   59.94  
   1366x768      59.79  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       66.67    60.00    59.94  
   720x400       70.08  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)



```

however when i turn on the TV into the relevant input (HDMI1) , im getting the xrandr to detect it as [B]Disconneted.

[/B]```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192HDMI-1 disconnected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
  1920x1080i (0xcd) 74.250MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  33.75KHz
        v: height 1080 start 1084 end 1094 total 1125           clock  60.00Hz



```

I have tried to install latest intel GPU drivers with thier update tool, and xorg-edgers team - no sucess.. still same behaviour..
Help much appreciated.

---

