---
title: "Can't get 3rd Monitor to work via HDMI adapter"
date: 2017-04-19
forum: Hardware
---

### Post by ramon72 on 2017-04-19
Hi, i'm experiencing problems trying to activate my 3rd monitor on a GeForce GT 705/PCIe/SSE2, Ubuntu 14.04.5 LTS x86_64, the card has 3 outputs: DVI and VGA monitors work fine, while plugging a VGA monitor via a HDMI adapter into the 3rd connector, does not work, i'm getting this result:


```
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1440x900       59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     59.9  
DVI-I-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x1200      60.0  
   1440x900       59.9  
   1280x1024      60.0  
   1280x960       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-0 connected (normal left inverted right x axis y axis)
   1440x900       59.9 +
   1920x1080      59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       59.9  
   1152x720       60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x480        59.9     59.9  
   640x480        75.0     59.9  
my@lilith:~$ xrandr --auto
xrandr: cannot find crtc for output HDMI-0
my@lilith:~$ 

```

```
my@lilith:~$ xrandr --verbose
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x27c
    Timestamp:  171700754
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CscMatrix: 65536 0 0 0 0 0 0 0 0 0 65536 0 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: VGA 
        supported: VGA
    ConnectorType: DVI-I 
    ConnectorNumber: 1 
    _ConnectorLocation: 1 
VGA-0 connected primary 1920x1080+0+0 (0x27e) normal (normal left inverted right x axis y axis) 476mm x 268mm
    Identifier: 0x27d
    Timestamp:  171700754
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
    CscMatrix: 65536 0 0 0 0 0 0 0 0 0 65536 0 
    EDID: 
        00ffffffffffff000469fd228f3d0200
        2718010368301b782a2ac5a4564f9e28
        0f5054b7ef00d1c0814081809500b300
        714f81c08100023a801871382d40582c
        4500dc0c1100001e000000ff0045394c
        4d54463134363833310a000000fd0032
        4b185311000a202020202020000000fc
        00415355532056533232380a2020003e
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: VGA 
        supported: VGA
    ConnectorType: VGA 
    ConnectorNumber: 0 
    _ConnectorLocation: 0 
  1920x1080 (0x27e)  148.5MHz +HSync +VSync *current +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
  1680x1050 (0x27f)  146.2MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1440x900 (0x280)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1280x1024 (0x281)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x282)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x960 (0x283)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1280x800 (0x284)   83.5MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  803 end  809 total  831           clock   59.8Hz
  1280x720 (0x285)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1152x864 (0x286)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1024x768 (0x287)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x288)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x289)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x28a)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x28b)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x28c)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x28d)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x28e)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x28f)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
DVI-I-1 connected 1920x1080+1920+0 (0x27e) normal (normal left inverted right x axis y axis) 476mm x 268mm
    Identifier: 0x290
    Timestamp:  171700754
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       1
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CscMatrix: 65536 0 0 0 0 0 0 0 0 0 65536 0 
    EDID: 
        00ffffffffffff0022f08a2801010101
        3113010380301b782eabd5a5554d9d25
        115054a1080081c0814081809500a940
        b300d1c00101023a801871382d40582c
        4500dc0c1100001e000000fd00324c18
        5e11000a202020202020000000fc0048
        5020323231300a2020202020000000ff
        00334351393439345748580a2020003d
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: DVI-I 
    ConnectorNumber: 1 
    _ConnectorLocation: 1 
  1920x1080 (0x27e)  148.5MHz +HSync +VSync *current +preferred
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
  1680x1050 (0x27f)  146.2MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1600x1200 (0x291)  162.0MHz +HSync +VSync
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1440x900 (0x280)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1280x1024 (0x282)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x960 (0x283)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1280x720 (0x285)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1024x768 (0x289)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x28c)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x28f)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
HDMI-0 connected (normal left inverted right x axis y axis)
    Identifier: 0x292
    Timestamp:  171700754
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    CscMatrix: 65536 0 0 0 0 0 0 0 0 0 65536 0 
    EDID: 
        00ffffffffffff0022f0a22600000080
        2611010380291a782e8585a6574a9c26
        125054a56b8081807100814095000101
        0101010101019a29a0d0518422305098
        360098ff1000001c000000fd00324c18
        530e000a202020202020000000fc0048
        502077313930370a20202020000000ff
        00434e4e373338343131520a202001ad
        02031b61230907078301000067030c00
        2000802d43908402e2000f8c0ad08a20
        e02d10103e9600a05a00000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000000
        00000000000000000000000000000029
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: HDMI 
    ConnectorNumber: 2 
    _ConnectorLocation: 2 
  1440x900 (0x280)  106.5MHz -HSync +VSync +preferred
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1920x1080 (0x293)  148.3MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.4KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   59.9Hz
  1280x1024 (0x281)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x282)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x960 (0x283)  108.0MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1280x720 (0x294)   74.2MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   59.9Hz
  1152x720 (0x295)   67.3MHz -HSync +VSync
        h: width  1152 start 1208 end 1328 total 1504 skew    0 clock   44.8KHz
        v: height  720 start  721 end  724 total  746           clock   60.0Hz
  1024x768 (0x287)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x289)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x28a)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x28c)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  720x480 (0x296)   27.0MHz -HSync +VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  720x480 (0x297)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  640x480 (0x28e)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x28f)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
my@lilith:~$ 

```

the HDMI-VGA adapter used is this one
[adattatore]("http://www.ebay.it/itm/222426180267")



any suggestions? thanks in advance for your attention guys

---

