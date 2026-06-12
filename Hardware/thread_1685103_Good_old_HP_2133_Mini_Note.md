---
title: "Good old HP 2133 Mini Note"
date: 2011-02-10
forum: Hardware
---

### Post by stevanicus on 2011-02-10
Hi There,

having extreme difficulty getting ubuntu 10.10 running unity.

When updating the VIA graphics card XORG fails to boot
and I get this message

```

: ... dlopen : ... via_drv.so : undefined symbol : miEmptyData
Failed to load ...via_drv.so
Failed to load modle "via" (loader failed, 7)
No drivers available
Fatal server Error: no screen found
```I have tried every tutorial, thread and post out there... and it driving me nuts :)

any help would be greatly appreciated before I pull my hair out :D

p.s. its gotta be possible since it works on 10.04
[http://www.youtube.com/watch?v=GwwGDDHx-yA](http://www.youtube.com/watch?v=GwwGDDHx-yA)

---

### Post by stevanicus on 2011-02-10
Just installed 10.04 and unity works straight upon installation.

Anyone know how to upgrade to 10.10 - preserving the drivers?

Thanks

*edit* i dont think 10.04 uses via drivers.

---

### Post by stevanicus on 2011-02-10
The VIA do install and run using the following steps

[https://help.ubuntu.com/community/OpenChrome#Beta%20Drivers%20for%20Ubuntu%2010.04]("https://help.ubuntu.com/community/OpenChrome#Beta%20Drivers%20for%20Ubuntu%2010.04")

However, I get that xorg generator by ./vinstall - configuration is wrong and the xorg from

[https://wiki.ubuntu.com/LaptopTestingTeam/Old/HP2133/DisplayConfig810](https://wiki.ubuntu.com/LaptopTestingTeam/Old/HP2133/DisplayConfig810)

doesnt work either

I get "Screens found, but non have a usable configuration"

Any ideas?

---

### Post by stevanicus on 2011-02-11
Finally got a working xorg to run the VIA graphics on the HP 2133 with 1024x600 resolution. (with limits)

The xorg was from
[http://www.hpminiguide.com/forum/other-linux-distributions/1183-solved-xorg-conf-1024x600-models.html](http://www.hpminiguide.com/forum/other-linux-distributions/1183-solved-xorg-conf-1024x600-models.html)

here is the code just incase
```
### VIA template edited by luvit with some modifications by Fr4gZ0n3###

Section "ServerFlags"
#    Option        "DefaultServerLayout"    "LCD-clone"
#    Option        "DefaultServerLayout"    "CRT-clone"
#    Option        "DefaultServerLayout"    "LCD-only"
#    Option        "DefaultServerLayout"    "CRT-only"

    Option        "AllowMouseOpenFail"    "on"
    Option        "Pixmap"        "32"
    EndSection

# Default locations of font files - change if required.

    Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

    ModulePath    "/usr/lib/xorg/modules"
    InputDevices    "/dev/gpmdata"
    InputDevices    "/dev/input/mice"
    EndSection

    Section "DRI"
    Group 0
    Mode 0666
    EndSection

    Section "InputDevice"
    Identifier    "Keyboard 0"
    Driver        "kbd"
    Option        "Protocol"        "Standard"
    Option        "XkbLayout"       "us"
    Option        "XkbModel"        "pc104"
    Option        "XkbRules"        "xfree86"
    EndSection

    Section "InputDevice"
    Identifier    "Mouse 0"
    Driver        "synaptics"
    Option        "Buttons"         "5"
    Option        "Device"          "/dev/input/mice"
    Option        "Emulate3Buttons" "on"
    Option        "InputFashion"    "Mouse"
    Option        "Name"            "Synaptics Touchpad"
    Option        "Protocol"        "explorerps/2"
    Option        "SHMConfig"       "on"  # GUI setting access
    Option        "ZAxisMapping"    "4 5"
    EndSection

    Section "InputDevice"
    Identifier    "Mouse 1"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Buttons"         "5"
    Option        "Device"          "/dev/input/mice"
    Option        "Emulate3Buttons" "on"
    Option        "Name"            "Generic Mouse"
    Option        "Protocol"        "Auto"
    Option        "Vendor"          "Sysp"
    Option        "ZAxisMapping"    "4 5"
    EndSection

    Section "Module"
    Load  "glx"
    Load  "dri"
    Load  "extmod"
    Load    "dbe"
    Load    "freetype"
    Load    "record"
    Load    "v4l"
    EndSection

# Device outputs not connected in the HP-2133

    Section "Monitor"
    Identifier "Monitor"
    ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
    ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
    ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
    ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
    ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
    ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
    Modeline "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622 -HSync +Vsync
    ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
    ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
    ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
    ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
    ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
    ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
    ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
    ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
    ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
    ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
    ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
    ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
    ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
    ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
    ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
    ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
    ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
    ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
    ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
    ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
    ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
    ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
    ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
    ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
    ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
    ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
    ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
    ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
    Option        "Ignore"    "true"
    EndSection

    Section "Monitor"
    Identifier "Monitor"
    ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
    ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
    ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
    ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
    ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
    ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
    ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
    ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
    Modeline "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622 -HSync +Vsync
    ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
    ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
    ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
    ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
    ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
    ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
    ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
    ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
    ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
    ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
    ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
    ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
    ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
    ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
    ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
    ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
    ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
    ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
    ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
    ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
    ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
    ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
    ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
    ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
    ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
    ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
    Option        "Ignore"    "true"
    EndSection

# Internal LCD does not return DDC information.
# Define first channel:

    Section "Modes"    # See also "HP-2133 Known Modes" at file end.
    Identifier    "HP-2133 LCD Modes"
    # Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
    Modeline "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622 -HSync +Vsync
    # Default mode "1280x720": 74.6 MHz, 44.2 kHz, 59.2 Hz
    # Modeline "1280x720-59.2"   74.60  1280 1341 1474 1688  720 721 724 746 -hsync +vsync
    # Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
    #Modeline "1024x768-60.0"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
    EndSection

    Section "Monitor"
    Identifier "Monitor"
    ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
    ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
    ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
    ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
    ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
    ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
    ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
    ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
    Modeline "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622 -HSync +Vsync
    ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
    ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
    ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
    ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
    ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
    ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
    ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
    ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
    ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
    ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
    ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
    ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
    ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
    ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
    ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
    ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
    ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
    ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
    ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
    ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
    ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
    ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
    ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
    ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
    ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
    ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
    VertRefresh    50.00-100.00            # X11 discovery claim
    HorizSync    30.00-113.00            # X11 discovery claim
    # Dot clock range: 20.00-270.00MHz      # X11 discovery claim
    # Typical dot pitch is: .1515mm x .1515mm
    # Native resolution is: 1280x768
    DisplaySize    193 116                 # Actual: 193.9 116.4
    UseModes    "HP-2133 LCD Modes"
    Option        "PreferredMode"        "1024x600"
    Option        "DPMS"
    EndSection

    Section "Device"
    Driver "via"
    VendorName  "VIA Tech"
    BoardName   "via"
            #Option "PanelID" "0"    #640x480,    Single,    Dithering
    Identifier    "via-P4M900 Device 0"
    BusID        "PCI:1:0:0"
    Option        "Monitor-LCD"        "HP-2133 LCD"
#    Option        "PanelID"        "17"    # 1280x720 Single, Dithering
#    Option        "PanelID"           "12"    # 1280x768 Single, Non-Dithering
    Option        "NoDDCValue"
    EndSection

    Section "Screen"
    Monitor  "Monitor"
    SubSection "Display"
        Modes  "1024x600" 
        #Virtual 1024 600
        Depth  24
    EndSubSection
    Identifier    "via-P4M900 Screen 0"
    Device        "via-P4M900 Device 0"
    Subsection    "Display"
        Depth    24             # Depth 16 broke
#        Modes    "1280x768-60.0" "1280x720-59.2" "1024x768-60.0"
            Modes    "1024x600"
#        Virtual    1024 600
    EndSubsection
    # Device section options:
    Option        "ForceLCD"        "true"    # BIOS setting over-ride
    Option        "ActiveDevice"        "LCD"
    Option        "VideoOnDevice"        "LCD"    # Broke ?
    Option        "SetMpegFBNumber"    "true"    # Unknown if required
    EndSection

# External device expected to return DDC information.
# Flying on full auto here, the smoke you smell may be your monitor:

    Section "Monitor"
    Identifier "Monitor"
    ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
    ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
    ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
    ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
    ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
    ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
    ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
    ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
    Modeline "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622 -HSync +Vsync
    ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
    ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
    ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
    ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
    ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
    ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
    ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
    ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
    ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
    ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
    ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
    ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
    ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
    ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
    ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
    ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
    ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
    ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
    ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
    ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
    ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
    ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
    ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
    ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
    ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
    ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
    Option        "DPMS"
    EndSection

    Section "Device"
    Driver "via"
    VendorName  "VIA Tech"
    BoardName   "via"
            #Option "PanelID" "0"    #640x480,    Single,    Dithering
    Identifier    "via-P4M900 Device 1"
    BusID        "PCI:1:0:0"
    Option        "Monitor-CRT"        "HP-2133 External"
    EndSection

    Section "Screen"
    Monitor  "Monitor"
    SubSection "Display"
        Modes  "1024x600" 
        #Virtual 1024 600
        Depth  24
    EndSubSection
    Identifier    "via-P4M900 Screen 1"
    Device        "via-P4M900 Device 1"
    Subsection    "Display"
        Depth    24             # Depth 16 broke
#        Virtual    2048 1536
    EndSubsection
    # Device section options:
    Option        "ActiveDevice"        "CRT"
    Option        "VideoOnDevice"        "CRT"    # Broke ?
    Option        "SetMpegFBNumber"    "true"    # Unknown if required
    EndSection

# Single channel, dual outputs driven, screen descriptions

    Section "Screen"
    Monitor  "Monitor"
    SubSection "Display"
        Modes  "1024x600" 
        #Virtual 1024 600
        Depth  24
    EndSubSection
    Identifier    "via-P4M900 Clone 0"
    Device        "via-P4M900 Device 0"
    Subsection    "Display"
        Depth    24            # Depth 16 broke
#        Modes    "1024x600" "1200x720" "1024x768"
            Modes    "1024x600"
#        Virtual    2048 1536
    EndSubsection
    # Device section options:
    Option        "ActiveDevice"        "LCD,CRT"
    Option        "ForceLCD"        "true"
    Option        "VideoOnDevice"        "LCD"    # Broke ?
    # Option true turned off mouse on LCD:
    Option        "Simultaneous"        "false"
    EndSection

    Section "Screen"
    Monitor  "Monitor"
    SubSection "Display"
        Modes  "1024x600" 
        #Virtual 1024 600
        Depth  24
    EndSubSection
    Identifier    "via-P4M900 Clone 1"
    Device        "via-P4M900 Device 1"
    Subsection    "Display"
        Depth    24             # Depth 16 broke
#        Virtual    2048 1536
    EndSubsection
    # Device section options:
    Option        "ActiveDevice"        "CRT,LCD"
    Option        "ForceLCD"        "true"
    Option        "VideoOnDevice"        "CRT"    # Broke ?
    # Option true turned off mouse on LCD:
    Option        "Simultaneous"        "false"
    EndSection

# RandR is broken, in various places, for various reasons:
# The driver does not recognize the RandR naming conventions:
# (WW) VIA(0): Option "Monitor-LCD" is not used
# (WW) VIA(0): Option "Monitor-CRT" is not used
# (WW) VIA(0): Option "Monitor-DVI" is not used
# (WW) VIA(0): Option "Monitor-TV" is not used
# (==) RandR enabled
# And if you can't name them, xrandr can't select them.  Bummer.

# Old-school layouts

    Section "ServerLayout"
    Option "RandR" "False"
    Identifier    "LCD-clone"
    InputDevice    "Keyboard 0"    "CoreKeyBoard"
    InputDevice    "Mouse 0"    "SendCoreEvents"
    InputDevice    "Mouse 1"    "SendCoreEvents"
    Screen        "via-P4M900 Clone 0"
    EndSection

    Section "ServerLayout"
    Option "RandR" "False"
    Identifier    "CRT-clone"
    InputDevice    "Keyboard 0"    "CoreKeyBoard"
    InputDevice    "Mouse 0"    "SendCoreEvents"
    InputDevice    "Mouse 1"    "SendCoreEvents"
    Screen        "via-P4M900 Clone 1"
    EndSection

    Section "ServerLayout"
    Option "RandR" "False"
    Identifier    "LCD-only"
    InputDevice    "Keyboard 0"    "CoreKeyBoard"
    InputDevice    "Mouse 0"    "SendCoreEvents"
    InputDevice    "Mouse 1"    "SendCoreEvents"
    Screen        "via-P4M900 Screen 0"
    EndSection

    Section "ServerLayout"
    Option "RandR" "False"
    Identifier    "CRT-only"
    InputDevice    "Keyboard 0"    "CoreKeyBoard"
    InputDevice    "Mouse 0"    "SendCoreEvents"
    InputDevice    "Mouse 1"    "SendCoreEvents"
    Screen        "via-P4M900 Screen 1"
    EndSection

Section "Modes"
    Identifier  "HP-2133 Known Modes"
    ## X11 discovered modes are marked "Default mode";
    ## VIA reference file modes are marked "Extra mode" in this list.
    ## All have been renamed to include refresh rate and not conflict
    ## with the standard VESA names (most are VESA standard rates).

    ## Refresh rate 60Hz - The prefered LCD refresh rate.

    # Default mode "2048x1536": 266.9 MHz, 95.3 kHz, 60.0 Hz
    Modeline "2048x1536-60.0"  266.95  2048 2200 2424 2800  1536 1537 1540 1589 -hsync +vsync
    # Default mode "1920x1440": 234.0 MHz, 90.0 kHz, 60.0 Hz
    Modeline "1920x1440-60.0"  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync
    # Default mode "1920x1200": 193.2 MHz, 74.5 kHz, 60.0 Hz
    Modeline "1920x1200-60.0"  193.16  1920 2048 2256 2592  1200 1201 1204 1242

    ## 1080p (image 16:9, pixel 1:1)
    # Default mode "1920x1080": 172.9 MHz, 67.1 kHz, 60.0 Hz
    Modeline "1920x1080-60.0"  172.90  1920 2043 2249 2578  1080 1081 1084 1118 -hsync +vsync

    # Default mode "1856x1392": 218.3 MHz, 86.4 kHz, 60.0 Hz
    Modeline "1856x1392-60.0"  218.30  1856 1952 2176 2528  1392 1393 1396 1439 -hsync +vsync
    # Default mode "1856x1392": 218.6 MHz, 86.5 kHz, 60.0 Hz
    Modeline "1856x1392-60.0"  218.57  1856 1992 2192 2528  1392 1393 1396 1441 -hsync +vsync
    # Default mode "1792x1344": 204.8 MHz, 83.7 kHz, 60.0 Hz
    Modeline "1792x1344-60.0"  204.80  1792 1920 2120 2448  1344 1345 1348 1394 -hsync +vsync
    # Default mode "1792x1344": 203.0 MHz, 83.5 kHz, 60.0 Hz
    Modeline "1792x1344-60.0"  202.97  1792 1920 2112 2432  1344 1345 1348 1391 -hsync +vsync
    # Default mode "1680x1050": 147.1 MHz, 65.2 kHz, 60.0 Hz
    Modeline "1680x1050-60.0"  147.14  1680 1784 1968 2256  1050 1051 1054 1087
    # Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
    Modeline "1600x1200-60.0"  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
    # Default mode "1600x1024": 136.4 MHz, 63.6 kHz, 60.0 Hz
    Modeline "1600x1024-60.0"  136.36  1600 1704 1872 2144  1024 1025 1028 1060 -hsync +vsync
    # Default mode "1600x900": 119.0 MHz, 55.9 kHz, 60.0 Hz
    Modeline "1600x900-60.0"  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync
    # Default mode "1440x1050": 126.2 MHz, 65.2 kHz, 60.0 Hz
    Modeline "1440x1050-60.0"  126.20  1440 1536 1688 1936  1050 1051 1054 1087 -hsync +vsync
    # Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
    Modeline "1440x900-60.2"  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync
    # Default mode "1440x900": 106.5 MHz, 55.9 kHz, 60.0 Hz
    Modeline "1440x900-60.0"  106.47  1440 1520 1672 1904  900 901 904 932 -hsync +vsync
    # Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
    Modeline "1400x1050-60.0"  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync

    ## Alternate version of 720p (image approx 16:9, pixel 1:1)
    # Default mode "1366x768": 85.9 MHz, 47.7 kHz, 60.0 Hz
    Modeline "1366x768-60.0"   85.86  1366 1440 1584 1800  768 769 772 795 -hsync +vsync

    # Default mode "1360x768": 85.5 MHz, 49.0 kHz, 60.7 Hz
    Modeline "1360x768-60.7"   85.50  1360 1392 1712 1744  768 783 791 807 +hsync +vsync
    Modeline "1024x600" 48.96 1024 1064 1168 1312 600 601 604 622 -HSync +Vsync
    # Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
    Modeline "1280x1024-60.0"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
    # Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
    Modeline "1280x960-60.0"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
    # Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
    Modeline "1280x800-60.0"   83.46  1280 1344 1480 1680  800 801 804 828
    # Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
    Modeline "1280x768-60.0"   80.14  1280 1344 1480 1680  768 769 772 795

    ## One version of 720p (image 16:9, pixel 1:1)
    # Default mode "1280x720": 74.6 MHz, 44.2 kHz, 59.2 Hz
    Modeline "1280x720-59.2"   74.60  1280 1341 1474 1688  720 721 724 746 -hsync +vsync

    # Default mode "1280x600": 61.5 MHz, 37.3 kHz, 60.0 Hz
    Modeline "1280x600-60.0"   61.50  1280 1336 1464 1648  600 601 604 622 -hsync +vsync
    # Default mode "1200x720": 70.2 MHz, 44.8 kHz, 60.0 Hz
    Modeline "1200x720-60.0"   70.18  1200 1256 1384 1568  720 721 724 746 -hsync +vsync
    # Default mode "1152x720": 67.3 MHz, 44.8 kHz, 60.0 Hz
    Modeline "1152x720-60.0"   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync
    # Default mode "1088x612": 53.0 MHz, 38.0 kHz, 60.0 Hz
    Modeline "1088x612-60.0"   52.95  1088 1128 1240 1392  612 613 616 634 -hsync +vsync
    # Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
    Modeline "1024x768-60.0"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
    # Default mode "1024x600": 49.0 MHz, 37.3 kHz, 60.0 Hz
    Modeline "1024x600-60.0"   48.96  1024 1064 1168 1312  600 601 604 622 -hsync +vsync
    # Default mode "1024x512": 41.3 MHz, 31.9 kHz, 60.0 Hz
    Modeline "1024x512-60.0"   41.30  1024 1056 1160 1296  512 513 516 531 -hsync +vsync
    # Default mode "1000x600": 48.1 MHz, 37.3 kHz, 60.0 Hz
    Modeline "1000x600-60.0"   48.07  1000 1040 1144 1288  600 601 604 622 -hsync +vsync
    # Default mode "960x600": 46.0 MHz, 37.3 kHz, 60.0 Hz
    Modeline "960x600-60.0"   45.98  960 1000 1096 1232  600 601 604 622 -hsync +vsync
    # Default mode "856x480": 31.7 MHz, 29.8 kHz, 59.9 Hz
    Modeline "856x480-59.9"   31.70  856 872 960 1064  480 481 484 497 -hsync +vsync
    # Default mode "848x480": 31.5 MHz, 29.8 kHz, 60.0 Hz
    Modeline "848x480-60.0"   31.50  848 864 952 1056  480 481 484 497 -hsync +vsync
    # Extra mode
    ModeLine "800x480-x" 29.58 800 816 896 992 480 481 484 497
    # Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
    Modeline "800x600-60.3"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
    # Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
    Modeline "800x600-56.2"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
    # Default mode "800x480": 40.0 MHz, 37.9 kHz, 60.3 Hz
    Modeline "800x480-60.3"   40.00  800 832 960 1056  480 541 545 628 -hsync +vsync
    # Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
    Modeline "720x576-60.1"   32.70  720 744 816 912  576 577 580 597 -hsync +vsync

    ## NTSC-M  (actually 710.9x486 active area)
    # Default mode "720x480": 26.7 MHz, 29.8 kHz, 60.0 Hz
    Modeline "720x480-60.0"   26.70  720 736 808 896  480 481 484 497 -hsync +vsync

    # Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
    Modeline "640x480-59.9"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
    # Default mode "480x640": 24.8 MHz, 39.8 kHz, 60.0 Hz
    Modeline "480x640-60.0"   24.82  480 504 552 624  640 641 644 663 -hsync +vsync

    ## Refresh rate 65Hz

    # Default mode "1600x1200": 175.5 MHz, 81.2 kHz, 65.0 Hz
    Modeline "1600x1200-65.0"  175.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync

    ## Refresh rate 70Hz

    # Default mode "1600x1200": 189.0 MHz, 87.5 kHz, 70.0 Hz
    Modeline "1600x1200-70.0"  189.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
    # Default mode "1400x1050": 151.0 MHz, 77.0 kHz, 70.0 Hz
    Modeline "1400x1050-70.0"  151.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync
    # Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
    Modeline "1024x768-70.1"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync

    ## Refresh rate 72Hz

    # Default mode "1920x1200": 230.0 MHz, 91.0 kHz, 72.8 Hz
    Modeline "1920x1200-72.8"  230.00  1920 1936 2096 2528  1200 1201 1204 1250 -hsync -vsync
    # Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
    Modeline "800x600-72.2"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
    # Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
    Modeline "640x480-72.8"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync

    ## Refresh Rate 75Hz

    # Default mode "1792x1344": 261.0 MHz, 106.3 kHz, 75.0 Hz
    Modeline "1792x1344-75.0"  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync
    # Default mode "1600x1200": 202.5 MHz, 93.8 kHz, 75.0 Hz
    Modeline "1600x1200-75.0"  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
    # Extra mode "1440x1050"
    ModeLine "1440x1050-x" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
    # Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
    Modeline "1400x1050-74.8"  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync
    # Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
    Modeline "1280x1024-75.0"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
    # Extra mode "1280x768"
    ModeLine "1280x768-x" 103.0 1280 1360 1496 1712 768 769 772 802
    # Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
    Modeline "1152x864-75.0"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
    # Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
    Modeline "1024x768-75.0"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
    # Extra mode "1024x512"
    ModeLine "1024x512-x" 53.3 1024 1072 1176 1328 512 513 516 535
    # Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
    Modeline "800x600-75.0"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
    # Extra mode "856x480"
    ModeLine "856x480-x" 41.3 856 888 976 1096 480 481 484 502
    # Extra mode "848x480"
    ModeLine "848x480-x" 41.0 848 880 968 1088 480 481 484 502
    # Extra mode "720x576"
    ModeLine "720x576-x" 42.6 720 760 832 944 576 577 580 602
    # Extra mode "720x480"
    ModeLine "720x480-x" 34.9 720 752 824 928 480 481 484 502
    # Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
    Modeline "640x480-75.0"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync

    ## Refresh rate 85Hz

    # Default mode "1600x1200": 229.5 MHz, 106.2 kHz, 85.0 Hz
    Modeline "1600x1200-85.0"  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync
    # Default mode "1400x1050": 184.0 MHz, 93.9 kHz, 85.3 Hz
    Modeline "1400x1050-85.3"  184.00  1400 1464 1656 1960  1050 1051 1054 1100 +hsync +vsync
    # Extra mode "1440x1050"
    ModeLine "1440x1050-x" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
    # Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
    Modeline "1280x1024-85.0"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
    # Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
    Modeline "1280x960-85.0"  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync
    # Extra mode "1280x768"
    ModeLine "1280x768-x" 118.5 1280 1368 1504 1728 768 769 772 807
    # Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
    Modeline "1152x864-85.1"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
    # Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
    Modeline "1024x768-85.0"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
    # Extra mode "848x480"
    ModeLine "848x480-x" 47.4 848 888 976 1104 480 481 484 505
    # Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
    Modeline "800x600-85.1"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
    # Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
    Modeline "640x480-85.0"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
EndSection


```I cant seem to get RandR working, it crashes to the XORG configuration.

It will boot when RandR is disabled. Grateful for any input, thanks

---

### Post by stevanicus on 2011-02-11
Above settings do work with ubuntu 10.10 but unity cannot run and crashed when you attempt logout

---

### Post by stevanicus on 2011-02-11
well this has been fun, posting to myself :) but I have finally found a solution (3 days later) :P thought i'd post it for anyone else having the same issue.

For anyone out there running ubuntu 10.10 on HP2133 can use the VIA Chrome9 driver below. Inside is the xorg.conf file for the HP2133 - its set for 1280x768 but simply change the number to 1024x600 and it will run.

This HP2133 xorg file has RandR working and running. And monitors is able to identifiy the monitor :D:D

use: [https://help.ubuntu.com/community/OpenChrome#Beta%20Drivers%20for%20Ubuntu%2010.04]("https://help.ubuntu.com/community/OpenChrome#Beta%20Drivers%20for%20Ubuntu%2010.04")

to install the driver

file: [http://www.mediafire.com/?zq7acrnm3bkp444](http://www.mediafire.com/?zq7acrnm3bkp444)

You should be all set to go then.

Note: The only problem I have is unable to log out... sticks on background.
So I havent been able to test netbook unity yet. we'll get there:)
**Could be because i've been tampering with ubuntu constantly**

NOTE1:
Unity does not load -> say frame buffer objects not supported on GPU, which is rubbish coz it boots unity in 10.04 with generic drivers.

_**UPDATE:**_
Reverted back to 10.04 -> unity wouldnt load.. as Framebuffer objects didnt run on via drivers in 10.10.
As for getting flash videos to run -> youtube etc. use this

link: [http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

user _**DRIVERS**_ [http://www.viaarena.com/Driver/5.75.32.87a-u1004-55689.tar.gz](http://www.viaarena.com/Driver/5.75.32.87a-u1004-55689.tar.gz) for _**10.04**_

---

### Post by oliman99 on 2011-02-16
Hi stevanicus,

great to hear UNR is working on the 2133.

I've two questions:

Did UNR work out of the box with 10.04, or were you following the steps described on [https://help.ubuntu.com/community/OpenChrome#Beta%20Drivers%20for%20Ubuntu%2010.04](https://help.ubuntu.com/community/OpenChrome#Beta%20Drivers%20for%20Ubuntu%2010.04) ?

And how is the performance of UNR on 2133 respectively how hard is CPU and fan working?

---

### Post by stevanicus on 2011-02-16
> **oliman99 said:**
> Hi stevanicus,

great to hear UNR is working on the 2133.

I've two questions:

Did UNR work out of the box with 10.04, or were you following the steps described on [https://help.ubuntu.com/community/OpenChrome#Beta%20Drivers%20for%20Ubuntu%2010.04]("https://help.ubuntu.com/community/OpenChrome#Beta%20Drivers%20for%20Ubuntu%2010.04") ?

And how is the performance of UNR on 2133 respectively how hard is CPU and fan working?

UNR worked out the box for me in 10.04 only, not 10.10. 

Use the install instructions titled **Beta Drivers for Ubuntu 10.04**

In my last post (above yours) use the second 4th link to download the correct drivers for 10.04.

Everything seems to be pretty responsive and my battery life is fine. Just full screen flash doesn't work.

---

### Post by MWaddams on 2011-03-07
> **stevanicus said:**
> 
For anyone out there running ubuntu 10.10 on HP2133 can use the VIA Chrome9 driver below. Inside is the xorg.conf file for the HP2133 - its set for 1280x768 but simply change the number to 1024x600 and it will run.


to install the driver

file: [http://www.mediafire.com/?zq7acrnm3bkp444](http://www.mediafire.com/?zq7acrnm3bkp444)


Could you post this one for the 2.6.38 kernel? Works fine on 10.10 but natty with the new kernel doesn't compile (error: implicit declaration of function ‘DRM_IOCTL_DEF’).

---

### Post by stevanicus on 2011-03-08
I didn't use 10.10 ubuntu any more.... As it came with too many problems for me.

U can compile your own via driver in the VIA_Chrome9 driver folder.

The best solution was to use ubuntu 10.04 as unity worked there and so did RandR

---

### Post by MWaddams on 2011-03-08
> **stevanicus said:**
> 
U can compile your own via driver in the VIA_Chrome9 driver folder.

That's what I'm trying :)

It doesn't compile (error: implicit declaration of function ‘DRM_IOCTL_DEF’).

I guess I'll have to fix it myself, I was hoping you would do it for me :)

---

### Post by stevanicus on 2011-03-08
> **MWaddams said:**
> That's what I'm trying :)

It doesn't compile (error: implicit declaration of function ‘DRM_IOCTL_DEF’).

I guess I'll have to fix it myself, I was hoping you would do it for me :)

try "sudo apt-get install build-essential" (might be "essentials")

also compile everything with sudo.

What os are you using?

---

### Post by MWaddams on 2011-03-08
> **stevanicus said:**
> try "sudo apt-get install build-essential" (might be "essentials")

also compile everything with sudo.

What os are you using?
On ubuntu 10.10 it compiles fine, and I have no complaints, works like a charm, nice compiz effects etc.

I'm also trying out 11.04 (Natty), and I guess drmP.h from the linux-headers has changed... Too bad, because otherwise I might already upgrade, for an Alpha 3 it works pretty damned good.

---

### Post by Meins321 on 2011-03-28
can you pack your current version somehow and post it here or a _how to_ would be nice!

you did use Ubuntu 10.10 Desktop right? Which kernel do you run on?

my problem is that 10.10 Netbook won't boot, and 10.10 Desktop is dead after driver install...

on 10.04 i was able to install the via driver which was not 100% stable ( Ok beta )

contrary to that 10.10 desktop dies if i install any via driver ( which should have 3D\RandR)

if i replace or delete the xorg.conf file which was not there before, ubuntu 10.10 won't boot in normal mode any more.

There are no: How to install via 3d/RandR working driver on Ubuntu 10.10 HP Mininote 2133....

most people say they had success, but why then no one post their kernel version/screen shots?? i tried it more than 10 times with all different versions an i might roll back to 9.* because it never worked ( okay 10.04 worked a bit )...

---

### Post by MWaddams on 2011-03-30
[http://www.mediafire.com/?zq7acrnm3bkp444](http://www.mediafire.com/?zq7acrnm3bkp444) works for me.

xorg.conf:

Section "ServerLayout"
       Identifier	"Default Layout"
       Screen		"Default Screen"
       InputDevice	"Mouse"
       InputDevice	"Keyboard"
EndSection

Section "Files"
#     RgbPath      "/usr/local/share/X11/rgb"
       ModulePath   "/usr/lib/xorg/modules"
#     FontPath     "/usr/share/fonts/X11/misc/"
#     FontPath     "/usr/share/fonts/X11/TTF/"
#     FontPath     "/usr/share/fonts/X11/OTF"
#     FontPath     "/usr/share/fonts/X11/Type1/"
#     FontPath     "/usr/share/fonts/X11/100dpi/"
#     FontPath     "/usr/share/fonts/X11/75dpi/"
EndSection

Section "InputDevice"
       Identifier	"Keyboard"
       Driver		"kbd"
       Option		"XkbRules"	"xorg"
       Option		"XkbModel"	"pc105"
       Option		"XkbLayout"	"cn"
EndSection

Section "InputDevice"
       Identifier	"Mouse"
       Driver		"mouse"
       Option		"CorePointer"
EndSection

Section "Monitor"
       Identifier	"CRT"
       Option	"Enable"	"true"            
EndSection

Section "Monitor"
       Identifier	"LCD"
       Option    "Enable"       "true"
        Option  "Type"          "HardWired"
        Option  "PanelSize"     "1024x600"
	Option	"PreferredMode"	"1024x600"
        Option  "DIPort"        "DFP_LOW"
EndSection	

Section "Monitor"
       Identifier	"DVI"
       Option	 "Enable"	"false"
EndSection	

Section "Monitor"
       Identifier	"TV"
       Option  "Ignore"	"true"
EndSection	

Section "Monitor"
       Identifier	"HDMI"
       Option  "Ignore"	"true"
EndSection	

Section "Monitor"
       Identifier	"CRT-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"LCD-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"DVI-2"
       Option	  "Ignore"	"true"
EndSection

Section "Monitor"
       Identifier	"TV-2"
       Option	  "Ignore"	"true"
EndSection

Section "Device"
	#BusID "PCI:01:00:0"
	Driver 	"via"
	VendorName  	"VIA Tech"
	BoardName   	"via"
	Identifier	"Configured Video Device"
	Option		"MigrationHeuristic" "greedy"
EndSection

Section "Screen"
       DefaultDepth 24
       SubSection "Display"
#             Virtual 2000 2000 
#              Modes "1024x600"
              Depth  24
       EndSubSection
       Identifier	"Default Screen"
       Device		"Configured Video Device"
EndSection

Section "Module"
      Load  "glx"
      Load  "dri"
      Load  "extmod"
EndSection

Section "DRI"
       Group 0
       Mode 0666
EndSection

Section "Extensions"
	Option	"Composite"			"Enable"
EndSection

---

### Post by AnnieM on 2011-04-06
Sorry, total newb here...

Ok, so does the 10.10 Unity interface work with the HP Mini 2133 or not?  My guess is, not so much since, from what I can gather, everyone is reverting back to 10.04 with mixed results according to this thread.  Just wondering if anyone has since been able to get 10.10 to work.

I installed Netbook edition on one of our Mini 2133's at work, since Windows runs like a dog on it  and it just doesn't work visually on a 9" screen...too small for old eyes.  So, I decided to install Ubuntu Netbook to use the Unity interface...looks nice on the screen shots.   When I try to login with the netbook edition, I get the "no required driver detected for unity" message and have to login on  the desktop edition--which is about as visually useful as Windows, but, at least it runs faster :D (though, wireless is now broken--was working just fine...thinking about replacing the much hated broadcom card).

Am I right to assume that the required driver is the Via driver?  I'd like to get all of this working before Natty is in general release.  Anyone experimenting with it, yet?

---

### Post by MWaddams on 2011-04-11
The driver from [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) or post #15 works (only if I use the xorg.conf as above).
10.10 Desktop with compiz works. Unity doesn't seem to work, screen keeps going black and then back to normal, and black again... I don't see why anyone would want to use unity on a netbook, the screen is small enough as it is, just tweak the standard desktop edition.
I tried natty, but you'll have to use openchrome for now, the current via driver isn't compatible.

---

