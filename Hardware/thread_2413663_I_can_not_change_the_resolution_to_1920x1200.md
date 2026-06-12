---
title: "I can not change the resolution to 1920x1200"
date: 2019-02-28
forum: Hardware
---

### Post by sebastian79 on 2019-02-28
[FONT=inherit][FONT=inherit][FONT=inherit][COLOR=#242729][FONT=Arial]I can not change my resolution in Ubuntu 18.04 to 1920x1200. This configuration is compatible since it was used in previous versions of ubuntu. It seems very strange to me that the Xorg does not take any modifications that I add, it is as if I was not reading it.

[/FONT][/COLOR][/FONT][/FONT]
[/FONT]
[FONT=inherit][FONT=Arial][COLOR=#242729]I have the nvidia driver installed

[/COLOR]
```
01:00.0 VGA compatible controller: NVIDIA Corporation GM107GL [Quadro K620] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation GM107GL [Quadro K620]
    Flags: bus master, fast devsel, latency 0, IRQ 126
    Memory at a2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    Memory at a0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

```

[COLOR=#242729]My Xorg.conf is

[/COLOR]```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option         "Xinerama" "0"
EndSection

Section "Files"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "built-ins"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0 
    Modeline "1920x1200_60.00" 193.25 1920 2056 2256 2592 1200 1203 1209 1245 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro K620"
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
# Removed Option "metamodes" "1920x1200 +0+0; nvidia-auto-select +0+0"
# Removed Option "metamodes" "1920x1200 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1600x900 +0+0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "metamodes" "1920x1200 +0+0; nvidia-auto-select +0+0" 
    Option         "metamodes" "1920x1200 +0+0"   
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
        Modes "1920x1200"
    EndSubSection
EndSection
```
[/FONT]
[/FONT]

[COLOR=#242729][FONT=Arial]The output of the xrandr command is


[/FONT][/COLOR]```
Screen 0: minimum 8 x 8, current 1600 x 900, maximum 16384 x 16384
DVI-I-0 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1600x900      59.82* 
   1400x900      59.88  
   1368x768      59.88    59.85  
   1360x768      59.96    59.80  
   1280x800      59.91    59.81  
   1280x720      59.86    59.74  
   1152x864      60.00  
   1024x576      59.90    59.82  
   960x540       59.82    59.63  
   864x486       59.92    59.57  
   800x600       72.19    60.32    56.25  
   800x450       59.82  
   700x450       59.88  
   684x384       59.88    59.85  
   680x384       59.96    59.80  
   640x480       59.94  
   640x400       59.98    59.88  
   640x360       59.86    59.83  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.82    59.63  
   432x243       59.92    59.57  
   400x300       72.19  
   320x240       60.05  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Output of the cvt 1920 1200 command:[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]```

# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync

```

---

### Post by Autodave on 2019-02-28
Are you using the Nvidia driver?  Go to Settings -> Additional Drivers and let it search for and install the most current driver.

---

