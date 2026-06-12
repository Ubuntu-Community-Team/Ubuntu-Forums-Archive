---
title: "Triple Monitor setup on Thinkpad T420 with nvidia Optimus"
date: 2014-05-26
forum: Hardware
---

### Post by user753 on 2014-05-26
Hello,
I have some problems getting my monitors to work. I am running Ubuntu 14.04 64bit with 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014. I have a Thinkpad T420 with: 
```
lshw -C video
 *-display               
       Beschreibung: VGA compatible controller
       Produkt: GF119M [Quadro NVS 4200M]
       Hersteller: NVIDIA Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Version: a1
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress vga_controller bus_master cap_list rom
       Konfiguration: driver=nvidia latency=0
       Ressourcen: irq:49 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(Größe=128) memory:f1000000-f107ffff
  *-display
       Beschreibung: VGA compatible controller
       Produkt: 2nd Generation Core Processor Family Integrated Graphics Controller
       Hersteller: Intel Corporation
       Physische ID: 2
       Bus-Informationen: pci@0000:00:02.0
       Version: 09
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: msi pm vga_controller bus_master cap_list rom
       Konfiguration: driver=i915 latency=0
       Ressourcen: irq:45 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:6000(Größe=64)


```
I use nvidia-331-updates[331.38-0ubuntu7] as driver and in BIOS settings I have activated Optimus and OS detection for Optimus. Both graphic cards are working. I can plug a monitor to the display port or VGA port and both are working but when i try to use both I can't because only one at a time seems to be detected. I searched the net and found some [info]("https://linuxacademy.com/blog/linux/ubuntu-bumblebee-optimus-and-multi-monitor-support/") [that]("http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/") [it]("https://bbs.archlinux.org/viewtopic.php?id=125207") seems to be possible but this info is quiet old. Playing around with arandr i can activate the DP-0 display port LVDS-1-0 internal LCD and VGA-1-0 VGA port but the screens are messed up. 
Some more info:
```
xrandr --listproviders
Providers: number : 3
Provider 0: id: 0x2bc cap: 0x1, Source Output crtcs: 2 outputs: 8 associated providers: 1 name:NVIDIA-0
Provider 1: id: 0x43 cap: 0x2, Sink Output crtcs: 2 outputs: 2 associated providers: 1 name:modesetting
Provider 2: id: 0x43 cap: 0x2, Sink Output crtcs: 2 outputs: 2 associated providers: 1 name:modesetting

```
```
xrandr -q
Screen 0: minimum 8 x 8, current 1600 x 900, maximum 16384 x 16384
VGA-0 disconnected primary (normal left inverted right x axis y axis)
LVDS-0 disconnected (normal left inverted right x axis y axis)
DP-0 connected (normal left inverted right x axis y axis)
   1600x1200      60.0 +
   1280x1024      75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
LVDS-1-0 connected 1600x900+0+0 309mm x 174mm
   1600x900       60.0*+   40.0  
   1440x900       59.9  
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
VGA-1-0 connected
   1600x1200      60.0 +
   1280x1024      75.0     60.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
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
```
/etc/X11/xorg.conf
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


```
```
.config/monitors.xml
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="VGA-0">
      </output>
      <output name="LVDS-0">
      </output>
      <output name="DP-0">
          <vendor>FUS</vendor>
          <product>0x0555</product>
          <serial>0x00000000</serial>
      </output>
      <output name="DP-1">
      </output>
      <output name="DP-2">
      </output>
      <output name="DP-3">
      </output>
      <output name="DP-4">
      </output>
      <output name="DP-5">
      </output>
      <output name="LVDS-1-0">
          <vendor>AUO</vendor>
          <product>0x213e</product>
          <serial>0x00000000</serial>
          <width>1600</width>
          <height>900</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="VGA-1-0">
          <vendor>FUS</vendor>
          <product>0x0554</product>
          <serial>0x00000000</serial>
      </output>
  </configuration>
</monitors>


```
Any ideas where to start? Editing /usr/share/X11/xorg.conf.d/20-my.conf? Or using nvidia-settings? Or in the unity-control-center? Or create arandr profile? [These]("http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/") [hacks]("https://linuxacademy.com/blog/linux/ubuntu-bumblebee-optimus-and-multi-monitor-support/")? Ask on some other website?

thanks!

Nils

---

### Post by user753 on 2014-05-28
So I can get my screens to work with arandr but I have a panning problem left.
[arandr setup]("http://imgur.com/QHxZSrA")

The result is that all three screen are active but DP-0 and VGA-1-0 are one desktop, so when I put a window in full screen mode both monitors are used. And when I move my mouse to another monitor the whole desktop move until the content of both monitors is identical. 

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
DP-0 connected 1600x1200+0+0 (0x340) normal (normal left inverted right x axis y axis) 408mm x 306mm panning 3200x2100+0+0
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
Screen 0: minimum 8 x 8, current 3200 x 2100, maximum 16384 x 16384
VGA-0 disconnected primary (normal left inverted right x axis y axis)
    Identifier: 0x2c7
    Timestamp:  34578
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
    Identifier: 0x2c8
    Timestamp:  34578
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
DP-0 connected 1600x1200+0+0 (0x63) normal (normal left inverted right x axis y axis) 408mm x 306mm panning 3200x2100+0+0
    Identifier: 0x2c9
    Timestamp:  34578
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
  1600x1200 (0x63)  162.0MHz +HSync +VSync *current +preferred
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1280x1024 (0x64)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x65)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1024x768 (0x2ca)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x4b)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x67)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x68)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x5b)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
DP-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x2cb
    Timestamp:  34578
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
    Identifier: 0x2cc
    Timestamp:  34578
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
    Identifier: 0x2cd
    Timestamp:  34578
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
    Identifier: 0x2ce
    Timestamp:  34578
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
    Identifier: 0x2cf
    Timestamp:  34578
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
    Timestamp:  34578
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
VGA-1-0 connected 1600x1200+1600+0 (0x63) normal (normal) 408mm x 306mm
    Identifier: 0x42
    Timestamp:  34578
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
  1600x1200 (0x63)  162.0MHz +HSync +VSync *current +preferred
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1280x1024 (0x64)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x65)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1024x768 (0x66)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x4b)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x67)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x68)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x69)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  720x400 (0x6a)   28.3MHz -HSync +VSync
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
  1600x1200 (0x63)  162.0MHz
        h: width  1600 start 1664 end 1856 total 2160 skew    0 clock   75.0KHz
        v: height 1200 start 1201 end 1204 total 1250           clock   60.0Hz
  1280x1024 (0x64)  135.0MHz
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1280x1024 (0x65)  108.0MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  800x600 (0x67)   49.5MHz
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  640x480 (0x68)   31.5MHz
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
```

[These guy]("http://ubuntuforums.org/showthread.php?t=2225761") seems to have a similar problem. Has anyone a idea what to do? Or where to ask or what to read to solve the problem?

---

