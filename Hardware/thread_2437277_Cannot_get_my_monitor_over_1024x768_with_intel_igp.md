---
title: "Cannot get my monitor over 1024x768 with intel igpu over display port"
date: 2020-02-20
forum: Hardware
---

### Post by pizztry on 2020-02-20
Computer has an Intel N3150 cpu on Lubuntu 19.10 but have tried many different versions of Ubuntu and always get the same problem. There is no discrete GPU, only the igpu. It works fine when connected over HDMI to another monitor but there is a problem with my monitor when connected over display port. This will not be a multi-monitor setup.

It's limited to 1024x768 resolution when using display port and it sees the monitor simply as Screen 0 with the name DP-1. Adding and switching to higher resolutions with xrandr results in blank black screens and crtc 0 failed errors. 

Would really appreciate any ideas that people may have to get this monitor working (Acer XB270HU). 

Monitor and cable have been tested on another Ubuntu machine with an Nvidia gpu and it ran at 2560x1440 144hz no problem.

```

[FONT=monospace]ilok@ilok-pc:~$ sudo xrandr
[sudo] password for ilok: 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 16384 x 16384
HDMI-1 disconnected primary (normal left inverted right x axis y axis)
DP-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-3 disconnected (normal left inverted right x axis y axis)
[/FONT]
```[FONT=monospace]
[/FONT]```

ilok@ilok-pc:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 16384 x 16384
HDMI-1 disconnected primary (normal left inverted right x axis y axis)
        Identifier: 0x42
        Timestamp:  8069
        Subpixel:   unknown
        Clones:    
        CRTCs:      0 1
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        content type: No Data 
                supported: No Data, Graphics, Photo, Cinema, Game
        Colorspace: Default 
                supported: Default, SMPTE_170M_YCC, BT709_YCC, XVYCC_601, XVYCC_709, SYCC_601, opYCC_601, opRGB, BT2020_CYCC, BT2020_RGB, BT2020_YCC, DCI-P3_RGB_D65, DCI-P3_RGB_Theater
        aspect ratio: Automatic 
                supported: Automatic, 4:3, 16:9
        Broadcast RGB: Automatic 
                supported: Automatic, Full, Limited 16:235
        audio: auto 
                supported: force-dvi, off, auto, on
        link-status: Good 
                supported: Good, Bad
        CONNECTOR_ID: 83 
                supported: 83
        non-desktop: 0 
                range: (0, 1)
DP-1 connected 1024x768+0+0 (0x48) normal (normal left inverted right x axis y axis) 0mm x 0mm
        Identifier: 0x43
        Timestamp:  8069
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
        max bpc: 10 
                range: (6, 10)
        Broadcast RGB: Automatic 
                supported: Automatic, Full, Limited 16:235
        audio: auto 
                supported: force-dvi, off, auto, on
        link-status: Good 
                supported: Good, Bad
        CONNECTOR_ID: 90 
                supported: 90
        non-desktop: 0 
                range: (0, 1)
  1024x768 (0x48) 65.000MHz -HSync -VSync *current
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x49) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x4a) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  848x480 (0x4b) 33.750MHz +HSync +VSync
        h: width   848 start  864 end  976 total 1088 skew    0 clock  31.02KHz
        v: height  480 start  486 end  494 total  517           clock  60.00Hz
  640x480 (0x4c) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
HDMI-2 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x44
        Timestamp:  8069
        Subpixel:   unknown
        Clones:    
        CRTCs:      0 1
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        content type: No Data 
                supported: No Data, Graphics, Photo, Cinema, Game
        Colorspace: Default 
                supported: Default, SMPTE_170M_YCC, BT709_YCC, XVYCC_601, XVYCC_709, SYCC_601, opYCC_601, opRGB, BT2020_CYCC, BT2020_RGB, BT2020_YCC, DCI-P3_RGB_D65, DCI-P3_RGB_Theater
        aspect ratio: Automatic 
                supported: Automatic, 4:3, 16:9
        Broadcast RGB: Automatic 
                supported: Automatic, Full, Limited 16:235
        audio: auto 
                supported: force-dvi, off, auto, on
        link-status: Good 
                supported: Good, Bad
        CONNECTOR_ID: 93 
                supported: 93
        non-desktop: 0 
                range: (0, 1)
DP-2 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x45
        Timestamp:  8069
        Subpixel:   unknown
        Clones:    
        CRTCs:      2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        max bpc: 10 
                range: (6, 10)
        Broadcast RGB: Automatic 
                supported: Automatic, Full, Limited 16:235
        audio: auto 
                supported: force-dvi, off, auto, on
        link-status: Good 
                supported: Good, Bad
        CONNECTOR_ID: 96 
                supported: 96
        non-desktop: 0 
                range: (0, 1)
HDMI-3 disconnected (normal left inverted right x axis y axis)
        Identifier: 0x46
        Timestamp:  8069
        Subpixel:   unknown
        Clones:    
        CRTCs:      2
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
        content type: No Data 
                supported: No Data, Graphics, Photo, Cinema, Game
        Colorspace: Default 
                supported: Default, SMPTE_170M_YCC, BT709_YCC, XVYCC_601, XVYCC_709, SYCC_601, opYCC_601, opRGB, BT2020_CYCC, BT2020_RGB, BT2020_YCC, DCI-P3_RGB_D65, DCI-P3_RGB_Theater
        aspect ratio: Automatic 
                supported: Automatic, 4:3, 16:9
        Broadcast RGB: Automatic 
                supported: Automatic, Full, Limited 16:235
        audio: auto 
                supported: force-dvi, off, auto, on
        link-status: Good 
                supported: Good, Bad
        CONNECTOR_ID: 99 
                supported: 99
        non-desktop: 0 
                range: (0, 1)

```

```


ilok@ilok-pc:~$ cvt 2560 1440 60
# 2560x1440 59.96 Hz (CVT 3.69M9) hsync: 89.52 kHz; pclk: 312.25 MHz
Modeline "2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync

ilok@ilok-pc:~$ sudo xrandr --newmode "2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync

ilok@ilok-pc:~$ sudo xrandr --addmode DP-1 2560x1440_60.00

ilok@ilok-pc:~$ sudo xrandr --output DP-1 --mode 2560x1440_60.00
xrandr: Configure crtc 0 failed

```

---

### Post by CatKiller on 2020-02-20
The issue is that your monitor isn't providing EDID, which is how resolutions and timings are automatically detected. That might be related to the GSync, or it might be coincidental.

Without EDID you can still specify the information to allow the resolution to be automatically detected. You just need to create a configuration snippet, in xorg.conf.d, that defines the capabilities of the monitor. HorizSync and VertRefresh are the frequency ranges that you're most interested in.

I haven't been able to find those values from a quick search. They might be listed in your monitor's manual or, since the monitor is working properly when connected to your nVidia card, you could use that to read the information that you need.

---

### Post by pizztry on 2020-02-21
thanks for the response. 

managed to generate an edid file via windows and hobbled together a xorg.conf file and got the one resolution I need working

---

