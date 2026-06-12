---
title: "How to select output for &quot;xrandr --newmode&quot;"
date: 2022-06-02
forum: Hardware
---

### Post by squigz on 2022-06-02
I have a Nvidia GT1030 connected to a Dell U2713HM monitor via dual-link DVI-D. I am using the Nvidia proprietary driver (nvidia-driver-510). Display is currently outputting at 1920x1080 and I would like to change this to 2560x1440. I am having trouble using xrandr to define a new mode specifically for the DVI-D output (rather than the HDMI output). 

I tried using xrandr to define the 2560x1440 resolution as follows:

```
xrandr --newmode "2560x1440" 241.50 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync
xrandr --addmode DVI-D-0 2560x1440
```

However, the xrandr --addmode command fails with the following output: 
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26
```

The problem seems to be that xrandr --newmode is adding the new mode only to the unused HDMI output (HDMI-0) rather than the DVI output I am trying to use (DVD-D-0). Here is the output from xrandr --verbose for reference:

```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DVI-D-0 connected primary 1920x1080+0+0 (0x1bc) normal (normal left inverted right x axis y axis) 600mm x 340mm
    Identifier: 0x1bb
    Timestamp:  1058665
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    EDID: 
        00ffffffffffff0010ac7e404c324541
        2a180103803c2278ea4bb5a7564ba325
        0a5054a54b008100b300d100714fa940
        8180d1c00101565e00a0a0a029503020
        350055502100001a000000ff004a4d50
        584b3441474145324c0a000000fc0044
        454c4c205532373133484d0a000000fd
        0031561d711c000a2020202020200057
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
  1920x1080 (0x1bc) 148.500MHz +HSync +VSync *current +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1680x1050 (0x1bd) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1600x1200 (0x1be) 162.000MHz +HSync +VSync
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock  75.00KHz
        v: height 1200 start 1201 end 1204 total 1250           clock  60.00Hz
  1280x1024 (0x1bf) 135.000MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock  79.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  75.02Hz
  1280x1024 (0x1c0) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x800 (0x1c1) 83.500MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock  49.70KHz
        v: height  800 start  803 end  809 total  831           clock  59.81Hz
  1152x864 (0x1c2) 108.000MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock  67.50KHz
        v: height  864 start  865 end  868 total  900           clock  75.00Hz
  1024x768 (0x1c3) 78.750MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.02KHz
        v: height  768 start  769 end  772 total  800           clock  75.03Hz
  1024x768 (0x1c4) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x1c5) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x1c6) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  640x480 (0x1c7) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x1c8) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
HDMI-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x1c9
    Timestamp:  1058665
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
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
  2560x1440 (0x1ea) 241.500MHz +HSync -VSync
        h: width  2560 start 2608 end 2640 total 2720 skew    0 clock  88.79KHz
        v: height 1440 start 1443 end 1448 total 1481           clock  59.95Hz
  2560x1440_reg (0x1ed) 241.500MHz +HSync -VSync
        h: width  2560 start 2608 end 2640 total 2720 skew    0 clock  88.79KHz
        v: height 1440 start 1443 end 1448 total 1481           clock  59.95Hz
```

How can I define the 2560x1440 mode for the DVI-D-0 output?

---

### Post by Yellow Pasque on 2022-06-03
Try:
```
cvt 2560 1440 30
```

---

### Post by Yellow Pasque on 2022-06-03
GT1030 is single link DVI:
[https://www.nvidia.com/en-us/geforce/graphics-cards/gt-1030/specifications/](https://www.nvidia.com/en-us/geforce/graphics-cards/gt-1030/specifications/)

What are the outputs on your GT1030? HDMI? Displayport?

---

### Post by squigz on 2022-06-03
Good catch. The physical connectors are HDMI and DVI-D dual link, so maybe the extra DVI pins aren't active / connected.

---

### Post by squigz on 2022-06-03
cvt 2560 1440 30cvt 2560 1440 30 returns the following

```
# 2560x1440 29.94 Hz (CVT) hsync: 43.95 kHz; pclk: 146.25 MHz
Modeline "2560x1440_30.00"  146.25  2560 2680 2944 3328  1440 1443 1448 1468 -hsync +vsync
```

Trying to add this mode I got the same error as before:

```
xrandr --newmode "2560x1440_30.00"  146.25  2560 2680 2944 3328  1440 1443 1448 1468 -hsync +vsync
xrandr --addmode DVI-D-0 "2560x1440_30.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26
```

Seems like the new mode is still being associated with the HDMI output...

```
xrandr --verbose
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DVI-D-0 connected primary 1920x1080+0+0 (0x1bc) normal (normal left inverted right x axis y axis) 600mm x 340mm
    Identifier: 0x1bb
    Timestamp:  1058665
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CTM: 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 
        0 1 
    CscMatrix: 65536 0 0 0 0 65536 0 0 0 0 65536 0 
    EDID: 
        00ffffffffffff0010ac7e404c324541
        2a180103803c2278ea4bb5a7564ba325
        0a5054a54b008100b300d100714fa940
        8180d1c00101565e00a0a0a029503020
        350055502100001a000000ff004a4d50
        584b3441474145324c0a000000fc0044
        454c4c205532373133484d0a000000fd
        0031561d711c000a2020202020200057
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
  1920x1080 (0x1bc) 148.500MHz +HSync +VSync *current +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock  67.50KHz
        v: height 1080 start 1084 end 1089 total 1125           clock  60.00Hz
  1680x1050 (0x1bd) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1600x1200 (0x1be) 162.000MHz +HSync +VSync
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock  75.00KHz
        v: height 1200 start 1201 end 1204 total 1250           clock  60.00Hz
  1280x1024 (0x1bf) 135.000MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock  79.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  75.02Hz
  1280x1024 (0x1c0) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1280x800 (0x1c1) 83.500MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock  49.70KHz
        v: height  800 start  803 end  809 total  831           clock  59.81Hz
  1152x864 (0x1c2) 108.000MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock  67.50KHz
        v: height  864 start  865 end  868 total  900           clock  75.00Hz
  1024x768 (0x1c3) 78.750MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock  60.02KHz
        v: height  768 start  769 end  772 total  800           clock  75.03Hz
  1024x768 (0x1c4) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x1c5) 49.500MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock  46.88KHz
        v: height  600 start  601 end  604 total  625           clock  75.00Hz
  800x600 (0x1c6) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  640x480 (0x1c7) 31.500MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock  37.50KHz
        v: height  480 start  481 end  484 total  500           clock  75.00Hz
  640x480 (0x1c8) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
HDMI-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x1c9
    Timestamp:  1058665
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
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
  2560x1440 (0x1ea) 241.500MHz +HSync -VSync
        h: width  2560 start 2608 end 2640 total 2720 skew    0 clock  88.79KHz
        v: height 1440 start 1443 end 1448 total 1481           clock  59.95Hz
  2560x1440_reg (0x1ed) 241.500MHz +HSync -VSync
        h: width  2560 start 2608 end 2640 total 2720 skew    0 clock  88.79KHz
        v: height 1440 start 1443 end 1448 total 1481           clock  59.95Hz
  2560x1440_30.00 (0x245) 146.250MHz -HSync +VSync
        h: width  2560 start 2680 end 2944 total 3328 skew    0 clock  43.95KHz
        v: height 1440 start 1443 end 1448 total 1468           clock  29.94Hz

```

---

### Post by Yellow Pasque on 2022-06-03
I can't think of any reason it wouldn't work. At this point, I begin to suspect that you may need to manually specify horizsync and vertrefresh in xorg.conf
> Seems like the new mode is still being associated with the HDMI output...
I don't see any evidence of that.

---

### Post by Yellow Pasque on 2022-06-03
For reference (i.e. from the manual): 
Horizontal scan range 30 kHz to 113 kHz
Vertical scan range 56 Hz to 86 Hz

---

