---
title: "Second Monitor stopped working"
date: 2014-08-15
forum: Hardware
---

### Post by doubleeagle on 2014-08-15
Hi,

I have been happily running a dual screen environment for almost 2 years on Ubuntu 12.04. Today it my second screen just stopped working all of a sudden. I had been running a software update but I think it had finished a while before the issue occurred.

It does not seem to be a cable issue as when I switch ports at the back of my workstation xrandr shows the opposite display ports as disconnected. Also, before switching the left hand side monitor is displaying my desktop and the right is blank. After switching the left goes blank and the right displays for a few seconds, before the left starts displaying again and the right goes blank again.

My xorg.conf hasn't changed since Nov 2012.

Any help in diagnosing the issue would be greatly appreciated. Thanks!

Here is my xrandr output before and after switching the cables in the ports:

```
~ $  xrandr --verbose
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 3840 x 1920
DisplayPort-1 connected 1920x1200+0+0 (0x43) normal (normal left inverted right x axis y axis) 518mm x 324mm
    Identifier: 0x41
    Timestamp:  7189
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff0010ac15f04c394330
        2f14010380342078ee1ec5ae4f34b126
        0e5054a54b008180a940d100714f0101
        010101010101283c80a070b023403020
        360006442100001a000000ff00463532
        354d30424a3043394c0a000000fc0044
        454c4c2055323431300a2020000000fd
        00384c1e5111000a2020202020200050
    scaler: off
    coherent_mode: 1 (0x00000001)    range:  (0,1)
  1920x1200 (0x43)  154.0MHz +HSync -VSync *current +preferred
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   74.0KHz
        v: height 1200 start 1203 end 1209 total 1235           clock   60.0Hz
  1600x1200 (0x44)  162.0MHz +HSync +VSync
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1280x1024 (0x45)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x46)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1152x864 (0x47)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1024x768 (0x48)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x49)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4a)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x4b)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4c)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x4d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x4e)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x42
    Timestamp:  7189
    Subpixel:   horizontal rgb
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    scaler: off
    coherent_mode: 1 (0x00000001)    range:  (0,1)

```

```
~ $  xrandr --verbose
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 3840 x 1920
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x41
    Timestamp:  311384
    Subpixel:   horizontal rgb
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    scaler: off
    coherent_mode: 1 (0x00000001)    range:  (0,1)
DisplayPort-0 connected 1920x1200+0+0 (0x43) normal (normal left inverted right x axis y axis) 518mm x 324mm
    Identifier: 0x42
    Timestamp:  311384
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff0010ac15f04c394330
        2f14010380342078ee1ec5ae4f34b126
        0e5054a54b008180a940d100714f0101
        010101010101283c80a070b023403020
        360006442100001a000000ff00463532
        354d30424a3043394c0a000000fc0044
        454c4c2055323431300a2020000000fd
        00384c1e5111000a2020202020200050
    scaler: off
    coherent_mode: 1 (0x00000001)    range:  (0,1)
  1920x1200 (0x43)  154.0MHz +HSync -VSync *current +preferred
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock   74.0KHz
        v: height 1200 start 1203 end 1209 total 1235           clock   60.0Hz
  1600x1200 (0x44)  162.0MHz +HSync +VSync
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1280x1024 (0x45)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x46)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1152x864 (0x47)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1024x768 (0x48)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x49)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x4a)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x4b)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4c)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x4d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x4e)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz

```

---

### Post by doubleeagle on 2014-08-15
Very strange! It just started working again. I switched cables and rebooted the machine. Still broken when I logged in. Then pressed Ctrl-Alt-F1 to get to a tty and then Ctrl-Alt-F7 to get back to the desktop environment again. Magic! Both screens in play.

Probably no help to anyone else, but working for me now.

---

