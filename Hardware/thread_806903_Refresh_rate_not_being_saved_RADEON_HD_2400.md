---
title: "Refresh rate not being saved *RADEON HD 2400*"
date: 2008-05-25
forum: Hardware
---

### Post by astute on 2008-05-25
I am currently feeding my HDTV via HDMI from a Radeon HD 2400 graphics card.  Using ubuntu 8.04 and proprietary fglrx drivers the HDTV is automatically recognised and Xorg generates the required modelines using EDID:

Xorg.0.log:
```

......
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.47.3
        ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 3:0.0.
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: DFP on internal TMDS [tmds1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: HTC  Model: 62  Serial#: 0
(II) fglrx(0): Year: 2006  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 16  vert.: 9
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.665 redY: 0.321   greenX: 0.223 greenY: 0.727
(II) fglrx(0): blueX: 0.146 blueY: 0.051   whiteX: 0.270 whiteY: 0.274
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 74.2 MHz   Image Size:  16 x 9 mm
(II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) fglrx(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 74.2 MHz   Image Size:  16 x 9 mm
(II) fglrx(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
(II) fglrx(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
(II) fglrx(0): Monitor name: PDP MONITOR
(II) fglrx(0): Ranges: V min: 49  V max: 61 Hz, H min: 15  H max: 46 kHz, PixClock max 80 MHz
(II) fglrx(0): Number of EDID sections to follow: 1
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):  00ffffffffffff002283620000000000
(II) fglrx(0):  00100103801009780a5081aa5239ba25
(II) fglrx(0):  0d454620000001010101010101010101
(II) fglrx(0):  010101010101011d8018711c1620582c
(II) fglrx(0):  250010090000009e011d007251d01e20
(II) fglrx(0):  6e28550010090000001e000000fc0050
(II) fglrx(0):  4450204d4f4e49544f520a20000000fd
(II) fglrx(0):  00313d0f2e08000a202020202020016c
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 24 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1080 (pitch 0)
(**) fglrx(0): *Mode "1920x1080": 74.2 MHz (scaled from 0.0 MHz), 33.8 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace (33.8 kHz)
(**) fglrx(0):  Default mode "1920x1080": 74.2 MHz (scaled from 0.0 MHz), 28.1 kHz, 25.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace (28.1 kHz)
(**) fglrx(0):  Default mode "1776x1000": 69.2 MHz (scaled from 0.0 MHz), 31.1 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1776x1000"x30.0   69.18  1776 1824 2000 2224  1000 1001 1004 1037 interlace +hsync (31.1 kHz)
(**) fglrx(0):  Default mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +vsync (65.3 kHz)
(**) fglrx(0):  Default mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0):  Default mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0):  Default mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0):  Default mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 (45.0 kHz)
(**) fglrx(0):  Default mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 37.5 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 (37.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1152x648": 59.9 MHz (scaled from 0.0 MHz), 40.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x648"x60.0   59.90  1152 1200 1320 1488  648 649 652 671 +hsync (40.3 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "720x576": 27.0 MHz (scaled from 0.0 MHz), 31.2 kHz, 50.0 Hz
(II) fglrx(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 +hsync +vsync (31.2 kHz)
(**) fglrx(0):  Default mode "720x480": 27.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   27.00  720 736 798 858  480 489 495 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x432": 21.1 MHz (scaled from 0.0 MHz), 26.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"x60.0   21.07  640 648 712 784  432 433 436 448 +hsync (26.9 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (160, 90) mm
(--) fglrx(0): DPI set to (304, 304)
(--) fglrx(0): Virtual size is 1920x1080 (pitch 1920)
..........

```

The screen always defaults to 1920x1080 at 30Hz (interlaced) on startup.  I have changed this value to 25Hz (PAL) using System-> Preferences->Screen Resolution and in the ATI Catalyst Control Center.  Whilst this makes an immediate adjustment, on reboot the refresh rate always defaults to 30Hz.  I have tried changing the "Modes" line in xorg.conf to "1920x1080_25" / "1920x1080@25" / "1920x1080"x25 to no effect, sometimes causing X to start in failsafe mode.

The 25Hz preference is stored in ~/.gnome2/monitors.xml, but seems to be doing nothing:
```
<configuration>
    <clone>no</clone>
    <output name="default">
        <vendor>???</vendor>
        <product>0x0000</product>
        <serial>0x00000000</serial>
        <width>1920</width>
        <height>1080</height>
        <rate>25</rate>
        <x>0</x>
        <y>0</y>
        <rotation>normal</rotation>
        <reflect_x>no</reflect_x>
        <reflect_y>no</reflect_y>
    </output>
</configuration>

```

Any suggestions gratefully received.

xorg.conf:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        SubSection "Display"
                Modes "1920x1080"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

---

