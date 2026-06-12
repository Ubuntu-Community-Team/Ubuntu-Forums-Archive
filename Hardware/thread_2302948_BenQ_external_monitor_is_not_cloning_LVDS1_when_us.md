---
title: "BenQ external monitor is not cloning LVDS1 when using HDMI connection"
date: 2015-11-14
forum: Hardware
---

### Post by jagandecapri on 2015-11-14
System:
1. Dell Inspiron
2. Ubuntu 15.04
3. Intel graphics

I have installed Intel Graphics driver from [https://01.org/linuxgraphics](https://01.org/linuxgraphics)

I am using HDMI both-sides cable to connect to BenQ EQ2440 monitor from my laptop. However, my external monitor always appears blank.

System Settings -> Display does show the monitor as connected.

[ATTACH=CONFIG]265577[/ATTACH]

Output of `xrandr --verbose` is as below. There is one line showing that **HDMI1 clones VGA1** which is actually disconnected. Could that be the problem? If yes, how do I change **HDMI1 to clone the LVDS1** instead?

```
Screen 0: minimum 8 x 8, current 3046 x 1050, maximum 32767 x 32767
LVDS1 connected primary 1366x768+0+0 (0x49) normal (normal left inverted right x axis y axis) 309mm x 173mm
    Identifier: 0x43
    Timestamp:  19132
    Subpixel:   horizontal rgb
    Gamma:      0.97:1.0:0.98
    Brightness: 0.98
    Clones:    
    CRTC:       0
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff0006af3c3000000000
        00150104901f11780210b59758579226
        1e505400000001010101010101010101
        010101010101ec1d56e850001e302616
        360035ad1000001af31356e850001e30
        2616360035ad1000001a000000fe0050
        314e5831804231343058573300000000
        00014121940111000001010a20200055
    BACKLIGHT: 244 
        range: (0, 4882)
    Backlight: 244 
        range: (0, 4882)
    scaling mode: Full aspect 
        supported: None, Full, Center, Full aspect
  1366x768 (0x49)   76.6MHz +HSync -VSync *current +preferred
        h: width  1366 start 1404 end 1426 total 1598 skew    0 clock   47.9KHz
        v: height  768 start  771 end  777 total  798           clock   60.1Hz
  1366x768 (0x4a)   51.1MHz +HSync -VSync
        h: width  1366 start 1404 end 1426 total 1598 skew    0 clock   32.0KHz
        v: height  768 start  771 end  777 total  798           clock   40.0Hz
  1360x768 (0x4b)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x4c)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1280x720 (0x4d)   74.5MHz -HSync +VSync
        h: width  1280 start 1336 end 1472 total 1664 skew    0 clock   44.8KHz
        v: height  720 start  721 end  724 total  746           clock   60.0Hz
  1024x768 (0x4e)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  1024x576 (0x4f)   47.0MHz -HSync +VSync
        h: width  1024 start 1064 end 1168 total 1312 skew    0 clock   35.8KHz
        v: height  576 start  577 end  580 total  597           clock   60.0Hz
  960x540 (0x50)   40.8MHz -HSync +VSync
        h: width   960 start  992 end 1088 total 1216 skew    0 clock   33.5KHz
        v: height  540 start  541 end  544 total  559           clock   60.0Hz
  800x600 (0x51)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x52)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  864x486 (0x53)   32.9MHz -HSync +VSync
        h: width   864 start  888 end  976 total 1088 skew    0 clock   30.2KHz
        v: height  486 start  487 end  490 total  504           clock   60.0Hz
  640x480 (0x54)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x405 (0x55)   22.2MHz -HSync +VSync
        h: width   720 start  728 end  800 total  880 skew    0 clock   25.2KHz
        v: height  405 start  406 end  409 total  420           clock   60.0Hz
  680x384 (0x56)   19.7MHz -HSync +VSync
        h: width   680 start  688 end  752 total  824 skew    0 clock   23.9KHz
        v: height  384 start  385 end  388 total  398           clock   60.0Hz
  640x360 (0x57)   17.2MHz -HSync +VSync
        h: width   640 start  640 end  704 total  768 skew    0 clock   22.4KHz
        v: height  360 start  361 end  364 total  373           clock   60.0Hz
DP1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x44
    Timestamp:  19132
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
HDMI1 connected 1680x1050+1366+0 (0x5e) normal (normal left inverted right x axis y axis) 531mm x 298mm
    Identifier: 0x45
    Timestamp:  19132
    Subpixel:   unknown
    Gamma:      0.97:1.0:0.98
    Brightness: 0.98
    Clones:     VGA1
    CRTC:       1
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff0009d1387945540000
        1419010380351e782e30a5a455539f27
        0d5054a56b80d1c081c081008180a9c0
        b30001010101023a801871382d40582c
        4500132a2100001e000000ff00333546
        3033353536534c300a20000000fd0032
        4c1e5311000a202020202020000000fc
        0042656e51204557323434304c0a01be
        020322f14f9005040302011112131406
        0715161f2309070765030c0010008301
        0000023a801871382d40582c4500132b
        2100001f011d8018711c1620582c2500
        132b2100009f011d007251d01e206e28
        5500132b2100001e8c0ad08a20e02d10
        103e9600132b21000018000000000000
        000000000000000000000000000000e7
    aspect ratio: Automatic 
        supported: Automatic, 4:3, 16:9
    Broadcast RGB: Automatic 
        supported: Automatic, Full, Limited 16:235
    audio: auto 
        supported: force-dvi, off, auto, on
  1920x1080 (0x58)  148.5MHz +HSync +VSync +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
  1920x1080 (0x59)  148.5MHz +HSync +VSync
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   56.2KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   50.0Hz
  1920x1080 (0x5a)  148.4MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.4KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   59.9Hz
  1920x1080i (0x5b)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.8KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   60.1Hz
  1920x1080i (0x5c)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   28.1KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   50.0Hz
  1920x1080i (0x5d)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.7KHz
        v: height 1080 start 1084 end 1094 total 1125           clock   60.0Hz
  1680x1050 (0x5e)  119.0MHz +HSync -VSync *current
        h: width  1680 start 1728 end 1760 total 1840 skew    0 clock   64.7KHz
        v: height 1050 start 1053 end 1059 total 1080           clock   59.9Hz
  1600x900 (0x5f)  119.0MHz -HSync +VSync
        h: width  1600 start 1696 end 1864 total 2128 skew    0 clock   55.9KHz
        v: height  900 start  901 end  904 total  932           clock   60.0Hz
  1280x1024 (0x60)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x61)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x800 (0x62)   71.0MHz +HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock   49.3KHz
        v: height  800 start  803 end  809 total  823           clock   59.9Hz
  1152x864 (0x63)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1280x720 (0x64)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1280x720 (0x65)   74.2MHz +HSync +VSync
        h: width  1280 start 1720 end 1760 total 1980 skew    0 clock   37.5KHz
        v: height  720 start  725 end  730 total  750           clock   50.0Hz
  1280x720 (0x66)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   59.9Hz
  1024x768 (0x67)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x4e)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x68)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x69)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x51)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  720x576 (0x6a)   27.0MHz -HSync -VSync
        h: width   720 start  732 end  796 total  864 skew    0 clock   31.2KHz
        v: height  576 start  581 end  586 total  625           clock   50.0Hz
  720x576i (0x6b)   13.5MHz -HSync -VSync Interlace
        h: width   720 start  732 end  795 total  864 skew    0 clock   15.6KHz
        v: height  576 start  580 end  586 total  625           clock   50.1Hz
  720x480 (0x6c)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   60.0Hz
  720x480 (0x6d)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  720x480i (0x6e)   13.5MHz -HSync -VSync Interlace
        h: width   720 start  739 end  801 total  858 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  525           clock   60.1Hz
  720x480i (0x6f)   13.5MHz -HSync -VSync Interlace
        h: width   720 start  739 end  801 total  858 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  525           clock   60.1Hz
  640x480 (0x70)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x71)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  640x480 (0x54)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x72)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
VGA1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x46
    Timestamp:  19132
    Subpixel:   unknown
    Clones:     HDMI1
    CRTCs:      0 1 2
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x47
    Timestamp:  19132
    Subpixel:   no subpixels
    Clones:    
    CRTCs:      3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter:

```

---

