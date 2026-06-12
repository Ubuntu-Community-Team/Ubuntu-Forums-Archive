---
title: "xbacklight setting wrong max/min screen brightness"
date: 2014-12-18
forum: Hardware
---

### Post by brunobeltran0 on 2014-12-18
The path I've gone down to discover the source of the problem is the same as in: [http://ubuntuforums.org/showthread.php?t=2156265](http://ubuntuforums.org/showthread.php?t=2156265)

I can set the laptop's brightness to max/min via
```
~# cat /sys/class/backlight/intel_backlight/max_brightness
5273
~# cat /sys/class/backlight/intel_backlight/max_brightness > /sys/class/backlight/intel_backlight/brightness
```

but if I do, xrandr thinks my backlight is off:
```

$ xrandr --verbose
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected 1920x1080+0+0 (0x48) normal (normal left inverted right x axis y axis) 344mm x 193mm
    Identifier: 0x43
    Timestamp:  59629224
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff0006afed3000000000
        001601049022137802d1159e59539b27
        1e505400000001010101010101010101
        010101010101b03680b470381e403064
        310058c1100000180000000f00000000
        00000000000000000020000000fe0041
        554f0a202020202020202020000000fe
        004231353648544e30332e30200a0003
    BACKLIGHT: 0 
        range: (0, 1)
    Backlight: 0 
        range: (0, 1)
    scaling mode: Full aspect 
        supported: None, Full, Center, Full aspect
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
  1920x1080 (0x48)  140.0MHz -HSync -VSync *current +preferred
        h: width  1920 start 1968 end 2068 total 2100 skew    0 clock   66.7KHz
        v: height 1080 start 1083 end 1084 total 1110           clock   60.1Hz
  1920x1080 (0xc7)  138.5MHz +HSync -VSync
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   66.6KHz
        v: height 1080 start 1083 end 1088 total 1111           clock   59.9Hz
  1680x1050 (0xc8)  146.2MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1680x1050 (0xc9)  119.0MHz +HSync -VSync
        h: width  1680 start 1728 end 1760 total 1840 skew    0 clock   64.7KHz
        v: height 1050 start 1053 end 1059 total 1080           clock   59.9Hz
  1600x1024 (0xca)  103.1MHz +HSync +VSync
        h: width  1600 start 1600 end 1656 total 1664 skew    0 clock   62.0KHz
        v: height 1024 start 1024 end 1029 total 1030           clock   60.2Hz
  1400x1050 (0xcb)  122.0MHz +HSync +VSync
        h: width  1400 start 1488 end 1640 total 1880 skew    0 clock   64.9KHz
        v: height 1050 start 1052 end 1064 total 1082           clock   60.0Hz
  1280x1024 (0xcc)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1440x900 (0xcd)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1280x960 (0xce)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1360x768 (0xcf)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0xd0)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1152x864 (0xd1)   81.6MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1024x768 (0xd2)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0xd3)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0xd4)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0xd5)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
VGA1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x44
    Timestamp:  59629224
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
HDMI1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x45
    Timestamp:  59629224
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x46
    Timestamp:  59629224
    Subpixel:   no subpixels
    Clones:    
    CRTCs:      3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 

```

Furthermore, trying to set the backlight via xbacklight doesn't leave anywhere near the right numbers in there.
i.e. 
```

~# xbacklight -set 0
~# cat /sys/class/backlight/intel_backlight/brightness 
516
```
 and
```

~# xbacklight -set 100
~# cat /sys/class/backlight/intel_backlight/brightness 
785
```


Finally, I'm not sure if this helps, but it seems that using xrandr directly, as in 
```

~# xrandr --output eDP1 --brightness 0.5
```
only allows me to adjust the *apparent* brightness between 0 and the *last value it was set to in /sys/.../brightness*.
xrandr does not change the actual value in /sys/.../brightness. I'm not sure if this is expected behavior.

Right now, I have a simple bash script set up to run on boot and resume that sets the backlight to max for me via the /sys/.../brightness file. With this is place I can use xrandr as a wordaround to get intermediate brightness values without root priveleges. But was wondering where to even submit a bug report? I'm not even sure where the problem is really coming from. xbacklight? xrandr?

Any help is appreciated.

---

### Post by pqwoerituytrueiwoq on 2014-12-18
maybe this script i made some time ago will be useful to you
[http://pastebin.com/HzzHrS2g](http://pastebin.com/HzzHrS2g)

---

### Post by brunobeltran0 on 2014-12-19
Thank you! That's pretty much the next script I was planning on writing, but I'm no bash expert, so I appreciate the help.

---

