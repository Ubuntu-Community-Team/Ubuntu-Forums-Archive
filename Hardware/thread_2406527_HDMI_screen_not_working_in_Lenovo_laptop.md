---
title: "HDMI screen not working in Lenovo laptop"
date: 2018-11-21
forum: Hardware
---

### Post by fedebaka2 on 2018-11-21
I have a Lenovo ideapad 310, with an AMD A12 APU and kubuntu 18.10. My graphics driver are the mesa drivers from ppa:oibaf/graphics-drivers, of which the current version is 19.0~git1811211930.
When I plug an HDMI cable to a TV, there is no image on the TV. In kubuntu's screen settings, only the laptop display appears. But xrandr says it has detected the HDMI TV:

```
 xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
eDP connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.05*+
   1680x1050     60.05  
   1280x1024     60.05  
   1440x900      60.05  
   1280x800      60.05  
   1280x720      60.05  
   1024x768      60.05  
   800x600       60.05  
   640x480       60.05  
HDMI-A-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1152mm x 648mm
   1920x1080     60.00*+  50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1680x1050     60.00  
   1280x1024     60.02  
   1440x900      60.00  
   1280x960      60.00  
   1360x768      59.80  
   1280x800      60.00  
   1280x720      60.00    60.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
```

And in kubuntu's screen configuration, clicking on the (i) button which I presume is for identifying the screens, both screen names appear superimposed on the laptop display:
[ATTACH=CONFIG]281735[/ATTACH]

Also commands such as:
```
xrandr --output HDMI-A-0 --mode 1920x1080
xrandr --output HDMI-A-0 --auto --same-as eDP
xrandr --output HDMI-A-0 --auto --left-of eDP
```

do nothing.

I downloaded and live usb tried xubuntu and ubuntu also, with the same result.

Any help? thanks!

---

### Post by fedebaka2 on 2018-11-23
UPDATE: My TV is a NOBLEX 32LD868HI, which is equivalent to the SANYO LCE32IH13, JVC LT32DA950 and PHILCO PLD3214HI smart TVs.
HDMI with linux works on another TV, a regular (not smart) LED tv, only the KDE screen settings do nothing. I only could change  from clone to extend desktop, etc., using xrandr.

The same laptop on my smart TV, using Windows 10 , works OK.

---

