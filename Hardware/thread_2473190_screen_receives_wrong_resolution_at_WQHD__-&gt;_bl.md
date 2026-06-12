---
title: "screen receives wrong resolution at WQHD  -&gt; blurry picture"
date: 2022-03-27
forum: Hardware
---

### Post by norbertneumarrn on 2022-03-27
Hello everybody.


I'm having a problem with my screen resolution and it differs from all slightly similar looking problems out there in the forum so I'm opening up this thread.
This is the case for both my GPUs, a GTX 1660 Super and a GT730: When I plug in my CS270 screen via DVI, which is capable of 2560 x 1440 (via both DVI and displayport according to manual) everything looks blurry, when I set the resolution to 2560x1440 in the ubuntu settings. I tried all available drivers in the additional drivers that were available and nothing made a difference. Then I noticed in the Eizo screen menu that it receives  a resolution of only 1280 x 1440 (and this, in case its relevant: dF: 120,8 MHz  fH: 88,7kHz  fV: 5939Hz). When I set the resolution to 1920x1080 or 1920x1200 in the ubuntu settings the screen receives the correct resolution and everything looks ok. So somehow the graphic cards send out a different resolution than what the ubuntu settings and nvidia X server settings say.

By The way this is not the case for the Displayport connection that I have available on the GTX1660. There I can get a crisp 2560x1440 picture. I need DVI on the other graphics card though for a hackintosh project.

In case my xrandr --verbose result tells anybody something:

```
Screen 0: minimum 8 x 8, current 2560 x 1440, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x27d
    Timestamp:  1112182
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: VGA 
        supported: VGA
    ConnectorType: VGA 
    ConnectorNumber: 2 
    _ConnectorLocation: 2 
    non-desktop: 0 
        supported: 0, 1
DVI-D-0 connected primary 2560x1440+0+0 (0x27f) normal (normal left inverted right x axis y axis) 597mm x 336mm
    Identifier: 0x27e
    Timestamp:  1112182
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    _MUTTER_PRESENTATION_OUTPUT: 0 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    EDID: 
        00ffffffffffff0015c395262385d801
        20190103803c2278ea12e5b14e37b625
        0c5054a10800a94081808140d1c00101
        010101010101565e00a0a0a029503020
        350055502100001a283c80a070b02340
        3020360055502100001a000000fd003b
        3d1f5919000a202020202020000000fc
        0043533237300a20202020202020000c
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: DVI-D 
    ConnectorNumber: 0 
    _ConnectorLocation: 0 
    non-desktop: 0 
        supported: 0, 1
  2560x1440 (0x27f) 241.500MHz +HSync -VSync *current +preferred
        h: width  2560 start 2608 end 2640 total 2720 skew    0 clock  88.79KHz
        v: height 1440 start 1443 end 1448 total 1481           clock  59.95Hz
  1920x1200 (0x280) 154.000MHz +HSync -VSync
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock  74.04KHz
        v: height 1200 start 1203 end 1209 total 1235           clock  59.95Hz
  1920x1080 (0x281) 148.500MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1600x1200 (0x282) 162.000MHz +HSync +VSync
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock  75.00KHz
        v: height 1200 start 1201 end 1204 total 1250           clock  60.00Hz
  1280x1024 (0x283) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x960 (0x284) 108.000MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock  60.00KHz
        v: height  960 start  961 end  964 total 1000           clock  60.00Hz
  1024x768 (0x285) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x286) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  640x480 (0x287) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
HDMI-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x288
    Timestamp:  1112182
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1 2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: HDMI 
    ConnectorNumber: 1 
    _ConnectorLocation: 1 
    non-desktop: 0 
        supported: 0, 1



```



My System:
Ubuntu 20.04.4 LTS
Monitor: Eizo CS270
MSI NVIDIA GeForce GT 730
AMD® Ryzen 7 1800x

---

### Post by Yellow Pasque on 2022-03-27
Are you using a dual-link DVI cable? [https://en.wikipedia.org/wiki/Digital_Visual_Interface#Connector](https://en.wikipedia.org/wiki/Digital_Visual_Interface#Connector)

---

### Post by norbertneumarrn on 2022-03-27
hahaha oh well. Didnt know there were several dvis and I just took the one from the eizo package which apparently was just single-link. Thank you!!!

---

### Post by Yellow Pasque on 2022-03-27
Really? It seems strange that Eizo would give you a single link cable with your monitor, especially for its price.

---

