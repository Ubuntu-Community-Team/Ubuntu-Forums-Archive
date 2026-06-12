---
title: "3 monitor setup with 2 cards (intel+nvidia) on laptop"
date: 2014-05-23
forum: Hardware
---

### Post by icest0rm on 2014-05-23
hi all...

i have this setup:

dell e6520 laptop with docking station and 3 external montitors (2 connected trough DVI to nvidia card, 1 connected through VGA to intel card).

i'm using nvidia-331 drivers with nvidia-prime...

all was working flawlessy out of the box (i have one 19" monitor on the left, 1 apple display 20" in the middle with unity dock, and another 19" on the right)...only when I disconnected laptop from docking stationa dn reconnected it I had some garbage in config so restarting laptop made always things work again.

Last day this didn't happen and it seems i cannot go back to my working config.

the best i can reach is monitor on the left and in the center working...monitor in the right working too but only showing background....central monitor is panning (when i go to the right with mouse the image shift to the left...) and it seems i cannot disable it even with xrandr...

here's the output of xrandr -q:

DP-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm panning 2560x1024+0+0 tracking 4240x1050+0+0 border 0/0/0/0
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DP-1 connected primary 1680x1050+1280+0 (normal left inverted right x axis y axis) 433mm x 270mm panning 2960x1050+1280+0 tracking 4240x1050+0+0 border 0/0/0/0
   1680x1050      59.9*+   60.0  
VGA-1-0 connected 1280x1024+2960+0 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  

here's xorg.conf:

Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
EndSection

and here's monitors.xml:

<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="VGA-0">
      </output>
      <output name="LVDS-0">
      </output>
      <output name="DP-0">
          <vendor>MAX</vendor>
          <product>0x0793</product>
          <serial>0x00000037</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="DP-1">
          <vendor>APP</vendor>
          <product>0x921d</product>
          <serial>0x02fe02bb</serial>
          <width>1680</width>
          <height>1050</height>
          <rate>60</rate>
          <x>1280</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="HDMI-0">
      </output>
      <output name="DP-2">
      </output>
      <output name="DP-3">
      </output>
      <output name="LVDS-1-0">
          <vendor>SEC</vendor>
          <product>0x5448</product>
          <serial>0x00000000</serial>
      </output>
      <output name="VGA-1-0">
          <vendor>MAX</vendor>
          <product>0x0793</product>
          <serial>0x000004de</serial>
          <width>1280</width>
          <height>1024</height>
          <rate>60</rate>
          <x>2960</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
</monitors>

any hint??

thanks..

---

### Post by dannyboy79 on 2014-05-23
install arandr and run it, and see if you can use arandr to set up the monitors where you want them.

---

### Post by icest0rm on 2014-05-25
I did used it, but it's the same then using xrandr...and can't disable panning for central monitor...it just ignores my commands..

---

### Post by icest0rm on 2014-05-26
the problem is this:

nbr@nbr-nb:~$ xrandr -q|more
Screen 0: minimum 8 x 8, current 4240 x 1050, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 disconnected (normal left inverted right x axis y axis)
[B]DP-0 connected 1280x1024+260+0 (normal left inverted right x axis y axis) 376mm 
x 301mm panning 2560x1024+0+0 tracking 4240x1050+0+0 border 0/0/0/0[/B]
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
[B]DP-1 connected primary 1680x1050+1280+0 (normal left inverted right x axis y axi
s) 433mm x 270mm panning 2960x1050+1280+0 tracking 4240x1050+0+0 border 0/0/0/0[/B]
   1680x1050      59.9*+   60.0  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
LVDS-1-0 connected
   1920x1080      60.0 +   59.9     40.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0     60.0  
   960x720        60.0  
   928x696        60.1  
   896x672        60.0  
   960x600        60.0  
   960x540        60.0  
   800x600        60.0     60.3     56.2  
   840x525        60.0     59.9  
   800x512        60.2  
   700x525        60.0  
   640x512        60.0  
   720x450        59.9  
   640x480        60.0     59.9  
   680x384        59.8     60.0  
   576x432        60.1  
   512x384        60.0  
   400x300        60.3     56.3  
   320x240        60.1  
**VGA-1-0 connected 1280x1024+2960+0 376mm x 301mm**
LVDS-1-0 connected
   1920x1080      60.0 +   59.9     40.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0     60.0  
   960x720        60.0  
   928x696        60.1  
   896x672        60.0  
   960x600        60.0  
   960x540        60.0  
   800x600        60.0     60.3     56.2  
   840x525        60.0     59.9  
   800x512        60.2  
   700x525        60.0  
   640x512        60.0  
   720x450        59.9  
   640x480        60.0     59.9  
   680x384        59.8     60.0  
   576x432        60.1  
   512x384        60.0  
   400x300        60.3     56.3  
   320x240        60.1  
VGA-1-0 connected 1280x1024+2960+0 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
  1680x1050 (0x47)  146.2MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz
  1680x1050 (0x48)  119.0MHz
        h: width  1680 start 1728 end 1760 total 1840 skew    0 clock   64.7KHz
        v: height 1050 start 1053 end 1059 total 1080           clock   59.9Hz
  1280x1024 (0x4b)  108.0MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x960 (0x4d)  108.0MHz
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock   60.0KHz
        v: height  960 start  961 end  964 total 1000           clock   60.0Hz
  1024x768 (0x52)   65.0MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x59)   40.0MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x5a)   36.0MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x62)   25.2MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  1280x1024 (0x6a)  135.0MHz
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1152x864 (0x6b)  108.0MHz
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1024x768 (0x6d)   75.0MHz
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  800x600 (0x6f)   50.0MHz
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x70)   49.5MHz
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  640x480 (0x71)   31.5MHz
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz


whenever I try to set without panning like using:

nbr@nbr-nb:~$ xrandr --output DP-0 --mode 1280x1024
nbr@nbr-nb:~$ xrandr --output DP-1 --mode 1680x1050
nbr@nbr-nb:~$ xrandr --output VGA-1-0 --mode 1280x1024
nbr@nbr-nb:~$ xrandr --output DP-0 --left-of-DP-1
nbr@nbr-nb:~$ xrandr --output DP-0 --left-of DP-1
nbr@nbr-nb:~$ xrandr --output VGA-1-0 --right-of DP-1


I still get panning between monitors..

and the value changes without meaning to me:

Screen 0: minimum 8 x 8, current 4240 x 1050, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 disconnected (normal left inverted right x axis y axis)
DP-0 connected 1280x1024+531+0 (normal left inverted right x axis y axis) 376mm 
x 301mm **panning 3091x1024+0+0** tracking 3091x1050+0+0 border 0/0/0/0
[cut...]
DP-1 connected primary 1680x1050+1280+0 (normal left inverted right x axis y axi
s) 433mm x 270mm **panning 2960x1050+1280+0 **tracking 4240x1050+0+0 border 0/0/0/0
   1680x1050      59.9*+   60.0  
[cut...]
VGA-1-0 connected 1280x1024+2960+0 376mm x 301mm

any clue?

---

### Post by icest0rm on 2014-05-27
any more hints?

---

### Post by user753 on 2014-05-28
[My monitor problem]("http://ubuntuforums.org/showthread.php?t=2226291") seems to be connected to yours. I can get my screens to work with arandr but I have the same panning problem as you have. 

```
xrandr -q --verbose
Screen 0: minimum 8 x 8, current 3200 x 2100, maximum 16384 x 16384
VGA-0 disconnected primary (normal left inverted right x axis y axis)
    Identifier: 0x2bf
    Timestamp:  7281767
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: VGA 
        supported: VGA
    ConnectorType: VGA 
    ConnectorNumber: 1 
    _ConnectorLocation: 1 
LVDS-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x2c0
    Timestamp:  7281767
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: LVDS 
        supported: LVDS
    ConnectorType: Panel 
    ConnectorNumber: 0 
    _ConnectorLocation: 0 
DP-0 connected 1600x1200+0+0 (0x340) normal (normal left inverted right x axis y axis) 408mm x 306mm **panning 3200x2100+0+0**
    Identifier: 0x2c1
    Timestamp:  7281767
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Panning:    3200x2100+0+0
    Tracking:   3200x2100+0+0
    Border:     0/0/0/0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff001ab3550500000000
        200f010380291f782a2945a459499824
        125054a54b00a9408180010101010101
        010101010101483f403062b0324040c0
        130098321100001e000000fd00334b1e
        5211000a202020202020000000fc0050
        32302d320a20202020202020000000ff
        00594548463031303833310a20200050
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: DisplayPort 
    ConnectorNumber: 2 
    _ConnectorLocation: 2 
  1600x1200 (0x340)  162.0MHz +HSync +VSync *current +preferred
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1280x1024 (0x341)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x342)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1024x768 (0x348)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x4b)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x344)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x345)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x5b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
DP-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x2c2
    Timestamp:  7281767
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: DisplayPort 
    ConnectorNumber: 3 
    _ConnectorLocation: 3 
DP-2 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x2c3
    Timestamp:  7281767
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: DisplayPort 
    ConnectorNumber: 4 
    _ConnectorLocation: 4 
DP-3 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x2c4
    Timestamp:  7281767
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: DisplayPort 
        supported: DisplayPort
    ConnectorType: DisplayPort 
    ConnectorNumber: 2 
    _ConnectorLocation: 2 
DP-4 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x2c5
    Timestamp:  7281767
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: DisplayPort 
        supported: DisplayPort
    ConnectorType: DisplayPort 
    ConnectorNumber: 3 
    _ConnectorLocation: 3 
DP-5 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x2c6
    Timestamp:  7281767
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: DisplayPort 
        supported: DisplayPort
    ConnectorType: DisplayPort 
    ConnectorNumber: 4 
    _ConnectorLocation: 4 
LVDS-1-0 connected 1600x900+0+1200 (0x44) normal (normal) 309mm x 174mm
    Identifier: 0x41
    Timestamp:  163635418
    Subpixel:   horizontal rgb
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       2
    CRTCs:      2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff0006af3e2100000000
        21140104901f11780261959c59528f26
        21505400000001010101010101010101
        010101010101f82a409a61840c30402a
        330035ae10000018a51c409a61840c30
        402a330035ae10000018000000fe0041
        554f0a202020202020202020000000fe
        004231343052573032205631200a00d0
    scaling mode: Full aspect 
        supported: None, Full, Center, Full aspect
  1600x900 (0x44)  110.0MHz -HSync -VSync *current +preferred
        h: width  1600 start 1664 end 1706 total 2010 skew    0 clock   54.7KHz
        v: height  900 start  903 end  906 total  912           clock   60.0Hz
  1600x900 (0x45)   73.3MHz -HSync -VSync
        h: width  1600 start 1664 end 1706 total 2010 skew    0 clock   36.5KHz
        v: height  900 start  903 end  906 total  912           clock   40.0Hz
  1440x900 (0x46)  106.5MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz
  1360x768 (0x47)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1360x768 (0x48)   72.0MHz +HSync -VSync
        h: width  1360 start 1408 end 1440 total 1520 skew    0 clock   47.4KHz
        v: height  768 start  771 end  781 total  790           clock   60.0Hz
  1152x864 (0x49)   81.6MHz -HSync +VSync
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1024x768 (0x4a)  133.5MHz -HSync +VSync DoubleScan
        h: width  1024 start 1100 end 1212 total 1400 skew    0 clock   95.3KHz
        v: height  768 start  768 end  770 total  794           clock   60.0Hz
  1024x768 (0x4b)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  960x720 (0x4c)  117.0MHz -HSync +VSync DoubleScan
        h: width   960 start 1024 end 1128 total 1300 skew    0 clock   90.0KHz
        v: height  720 start  720 end  722 total  750           clock   60.0Hz
  928x696 (0x4d)  109.2MHz -HSync +VSync DoubleScan
        h: width   928 start  976 end 1088 total 1264 skew    0 clock   86.4KHz
        v: height  696 start  696 end  698 total  719           clock   60.1Hz
  896x672 (0x4e)  102.4MHz -HSync +VSync DoubleScan
        h: width   896 start  960 end 1060 total 1224 skew    0 clock   83.7KHz
        v: height  672 start  672 end  674 total  697           clock   60.0Hz
  960x600 (0x4f)   77.0MHz +HSync -VSync DoubleScan
        h: width   960 start  984 end 1000 total 1040 skew    0 clock   74.0KHz
        v: height  600 start  601 end  604 total  617           clock   60.0Hz
  960x540 (0x50)   69.2MHz +HSync -VSync DoubleScan
        h: width   960 start  984 end 1000 total 1040 skew    0 clock   66.6KHz
        v: height  540 start  541 end  544 total  555           clock   60.0Hz
  800x600 (0x51)   81.0MHz +HSync +VSync DoubleScan
        h: width   800 start  832 end  928 total 1080 skew    0 clock   75.0KHz
        v: height  600 start  600 end  602 total  625           clock   60.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x53)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  840x525 (0x54)   73.1MHz -HSync +VSync DoubleScan
        h: width   840 start  892 end  980 total 1120 skew    0 clock   65.3KHz
        v: height  525 start  526 end  529 total  544           clock   60.0Hz
  840x525 (0x55)   59.5MHz +HSync -VSync DoubleScan
        h: width   840 start  864 end  880 total  920 skew    0 clock   64.7KHz
        v: height  525 start  526 end  529 total  540           clock   59.9Hz
  800x512 (0x56)   51.6MHz +HSync +VSync DoubleScan
        h: width   800 start  800 end  828 total  832 skew    0 clock   62.0KHz
        v: height  512 start  512 end  514 total  515           clock   60.2Hz
  700x525 (0x57)   61.0MHz +HSync +VSync DoubleScan
        h: width   700 start  744 end  820 total  940 skew    0 clock   64.9KHz
        v: height  525 start  526 end  532 total  541           clock   60.0Hz
  640x512 (0x58)   54.0MHz +HSync +VSync DoubleScan
        h: width   640 start  664 end  720 total  844 skew    0 clock   64.0KHz
        v: height  512 start  512 end  514 total  533           clock   60.0Hz
  720x450 (0x59)   53.2MHz -HSync +VSync DoubleScan
        h: width   720 start  760 end  836 total  952 skew    0 clock   55.9KHz
        v: height  450 start  451 end  454 total  467           clock   59.9Hz
  640x480 (0x5a)   54.0MHz +HSync +VSync DoubleScan
        h: width   640 start  688 end  744 total  900 skew    0 clock   60.0KHz
        v: height  480 start  480 end  482 total  500           clock   60.0Hz
  640x480 (0x5b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  680x384 (0x5c)   42.4MHz -HSync +VSync DoubleScan
        h: width   680 start  716 end  784 total  888 skew    0 clock   47.7KHz
        v: height  384 start  385 end  390 total  399           clock   59.8Hz
  680x384 (0x5d)   36.0MHz +HSync -VSync DoubleScan
        h: width   680 start  704 end  720 total  760 skew    0 clock   47.4KHz
        v: height  384 start  385 end  390 total  395           clock   60.0Hz
  576x432 (0x5e)   40.8MHz -HSync +VSync DoubleScan
        h: width   576 start  608 end  668 total  760 skew    0 clock   53.7KHz
        v: height  432 start  432 end  434 total  447           clock   60.1Hz
  512x384 (0x5f)   32.5MHz -HSync -VSync DoubleScan
        h: width   512 start  524 end  592 total  672 skew    0 clock   48.4KHz
        v: height  384 start  385 end  388 total  403           clock   60.0Hz
  400x300 (0x60)   20.0MHz +HSync +VSync DoubleScan
        h: width   400 start  420 end  484 total  528 skew    0 clock   37.9KHz
        v: height  300 start  300 end  302 total  314           clock   60.3Hz
  400x300 (0x61)   18.0MHz +HSync +VSync DoubleScan
        h: width   400 start  412 end  448 total  512 skew    0 clock   35.2KHz
        v: height  300 start  300 end  301 total  312           clock   56.3Hz
  320x240 (0x62)   12.6MHz -HSync -VSync DoubleScan
        h: width   320 start  328 end  376 total  400 skew    0 clock   31.5KHz
        v: height  240 start  245 end  246 total  262           clock   60.1Hz
VGA-1-0 connected 1600x1200+1600+0 (0x340) normal (normal) 408mm x 306mm
    Identifier: 0x42
    Timestamp:  163635418
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       3
    CRTCs:      2 3
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff001ab3540500000000
        200f010368291f782a2945a459499824
        125054a54b00a9408180010101010101
        010101010101483f403062b0324040c0
        130098321100001e000000fd00334b1e
        5211000a202020202020000000fc0050
        32302d320a20202020202020000000ff
        00594548463031313134320a2020006d
  1600x1200 (0x340)  162.0MHz +HSync +VSync *current +preferred
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1280x1024 (0x341)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x342)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1024x768 (0x343)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x4b)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x344)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x345)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x346)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  720x400 (0x347)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz
  1024x768 (0x4b)   65.0MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x52)   40.0MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x5b)   25.2MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  1600x1200 (0x340)  162.0MHz
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1280x1024 (0x341)  135.0MHz
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x342)  108.0MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  800x600 (0x344)   49.5MHz
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  640x480 (0x345)   31.5MHz
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
```

Unfortunately I have not found a solution yet.

---

### Post by icest0rm on 2014-05-28
what is strange is that i was not having this behaviour when i installed 14.04...and didn't have the need to configure it with xrandr|arandr, nvidia-settings or smtg else...just unity control center...something changed...an update maybe?

---

### Post by user753 on 2014-05-28
Okay I think that i have made some progress.
```
nils@Nils-Laptop:~$ xrandr --verbose --output  LVDS-1-0 --mode 1600x900 --pos 0x0 --panning 0x0+0+0 --output DP-0 --mode 1600x1200 --pos 1600x0 --output VGA-1-0 --mode 1600x1200 --pos 3200x0

 screen 0: 4800x1200 1269x317 mm  96.05dpi
crtc 0:    1600x1200   60.0 +1600+0 "DP-0"
crtc 2:     1600x900   60.0 +0+0 "LVDS-1-0"
crtc 3:    1600x1200   60.0 +3200+0 "VGA-1-0"


```

Now I have all three monitors active. The two monitors on VGA and DP acting as single desktop and the LVDS as another.  Does that help?


 Any idea how i can configure the two monitors on DP and VGA to act as desktop own their own and not as a huge one?

edit: you maybe have to disable the additional and unused monitor ports at first: ```
arandr --output PORTNAME --off
```

---

### Post by icest0rm on 2014-06-05
Ok I tried as you suggested....


here's situation before:

```

VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 disconnected (normal left inverted right x axis y axis)
[B]DP-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm panning 2560x1024+0+0 tracking 4240x1050+0+0 border 0/0/0/0
DP-1 connected primary 1680x1050+1280+0 (normal left inverted right x axis y axis) 433mm x 270mm panning 2960x1050+1280+0 tracking 4240x1050+0+0 border 0/0/0/0[/B]
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
LVDS-1-0 connected
**VGA-1-0 connected 1280x1024+2960+0 376mm x 301mm**

```

in this situation all three monitors DP-0, DP-1 and VGA-1-0 are working...DP-0 and DP-1 are connected to the Nvidia card, VGA-1-0 is connected to the Intel one....and there is panning in DP-1...

I tried:

```

nbr@nbr-nb:~$ xrandr --verbose --output DP-0 --mode 1280x1024 --pos 0x0 --panning 0x0+0+0 --output DP-1 --mode 1680x1050 --pos 1280x0 --panning 0x0+0+0 --output VGA-1-0 --mode 1280x1024 --pos 2960x0 --panning 0x0+0+0
crtc 0:    1280x1024   60.0 +0+0 "DP-0"
crtc 1:    1680x1050   59.9 +1280+0 "DP-1"
crtc 2:    1280x1024   60.0 +2960+0 "VGA-1-0"

```

but monitor DP-0 and DP-1 was then showing the same thing as duplicates..so not better...

with Ubuntu control center I can again set 3 monitors working indipendently but DP-0 and DP-1 are panning....and I want to disable it :-\

---

### Post by rosshadden on 2014-10-10
I have been fighting very similar panning issues on Arch Linux for almost a year now.  I actually got it to work earlier this week, though you're not going to like how because it's non-deterministic.  It doesn't work every time.

1. First I disabled all monitors except my HDMI (which is attached to my NVIDIA card in my laptop... the other outputs *all* go through the integrated Intel card including the actual built-in laptop display, and I have to offload them through the main card).
2. Next, I enabled them in such an order that my HDMI monitor was not first.  That is, I arranged them using arandr as LVDS -> HDMI -> DVI.
3. Now this step actually fails, as for some bizarre reason the HDMI monitor *has* to be the leftmost monitor.  So what happens is a weird thing where LVDS and HDMI actually overlap each other, and DVI is way off to the right somewhere.
4. I then disable all monitors except the HDMI one again, just like the first step.
5. Lastly, I enable the monitors and arrange them in the way that I want them and apply the settings.

What happens is that some very low percentage of the time, this actually removes the panning issue and everything is perfect.  So I end up repeating these 5 steps over and over again until either I get made fun of for wasting thousands of hours on my monitor issues at work (as I have become notorious for), or it actually works at some point.  These past few days the first outcome happened before the second, so I just dealt with the panning like I've been doing for the past 6 months.  I suspect this information won't help you guys, and in fact it hardly helps me.  But there are so few people in these situations making commotion on the internet I've found.

---

