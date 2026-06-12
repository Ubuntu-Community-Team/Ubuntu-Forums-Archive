---
title: "refresh rates 'disappear' with SLI"
date: 2018-09-23
forum: Hardware
---

### Post by akos.maroy on 2018-09-23
Hi,

I'm trying to set up an SLI config, and I'm experiencing that refresh rate options 'disappear' when using SLI.

without SLI, I can set up to 100Hz:

```
$ xrandr
Screen 0: minimum 8 x 8, current 3440 x 1440, maximum 32767 x 32767
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 connected primary 3440x1440+0+0 (normal left inverted right x axis y axis) 798mm x 335mm
   3440x1440     59.97 + 100.00*   94.99    89.96    84.96    79.98    49.99  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
DP-5 disconnected (normal left inverted right x axis y axis)
```

with SLI, I get:

```
$ xrandr 
Screen 0: minimum 8 x 8, current 3440 x 1440, maximum 32767 x 32767
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 connected primary 3440x1440+0+0 (normal left inverted right x axis y axis) 798mm x 335mm
   3440x1440     59.97*+  49.99  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
DP-5 disconnected (normal left inverted right x axis y axis)
```

by 'SLI' I mean having set nvidia-xconfig --sli=On or --sli=Auto.

EDID output seems to be the same, in both cases I get:

```
$ xrandr --verbose | edid-decode 
Extracted contents:
header:          00 ff ff ff ff ff ff 00
serial number:   04 69 33 34 2f 8a 01 00 0c 1c
version:         01 04
basic params:    a5 50 22 78 06
chroma info:     ee 91 a3 54 4c 99 26 0f 50 54
established:     21 08 00
standard:        01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01
descriptor 1:    e7 7c 70 a0 d0 a0 29 50 30 20 3a 00 1e 4f 31 00 00 1a
descriptor 2:    00 00 00 ff 00 23 41 53 4d 38 4b 31 43 6a 30 6c 58 64
descriptor 3:    00 00 00 fd 00 1e 64 49 97 36 01 0a 20 20 20 20 20 20
descriptor 4:    00 00 00 fc 00 52 4f 47 20 50 47 33 34 38 51 0a 20 20
extensions:      01
checksum:        b9

Manufacturer: ACI Model 3433 Serial Number 100911
Made week 12 of 2018
EDID version: 1.4
Digital display
8 bits per primary color channel
DisplayPort interface
Maximum image size: 80 cm x 34 cm
Gamma: 2.20
Supported color formats: RGB 4:4:4
Default (sRGB) color space is primary color space
First detailed timing is preferred timing
Established timings supported:
  640x480@60Hz
  800x600@60Hz
  1024x768@60Hz
Standard timings supported:
Detailed mode: Clock 319.750 MHz, 798 mm x 335 mm
               3440 3488 3520 3600 hborder 0
               1440 1443 1453 1481 vborder 0
               +hsync -vsync 
Serial number: #ASM8K1Cj0lXd
Monitor ranges (bare limits): 30-100Hz V, 73-151kHz H, max dotclock 540MHz
Monitor name: ROG
Has 1 extension blocks
Checksum: 0xb9 (valid)

CEA extension block
Extension version: 3
14 bytes of CEA data
  Audio data block
    Linear PCM, max channels 2
    Supported sample rates (kHz): 48 44.1 32
    Supported sample sizes (bits): 16
  Speaker allocation data block
    Speaker map: FL/FR
  Vendor-specific data block, OUI 00044b
Basic audio support
1 native detailed modes
Detailed mode: Clock 265.250 MHz, 798 mm x 335 mm
               3440 3488 3520 3600 hborder 0
               1440 1443 1453 1474 vborder 0
               +hsync -vsync 
Detailed mode: Clock 531.520 MHz, 798 mm x 335 mm
               3440 3448 3480 3520 hborder 0
               1440 1496 1504 1510 vborder 0
               +hsync -vsync 
Detailed mode: Clock 515.000 MHz, 798 mm x 335 mm
               3440 3488 3520 3600 hborder 0
               1440 1443 1453 1506 vborder 0
               +hsync -vsync 
Detailed mode: Clock 486.750 MHz, 798 mm x 335 mm
               3440 3488 3520 3600 hborder 0
               1440 1443 1453 1503 vborder 0
               +hsync -vsync 
Detailed mode: Clock 458.500 MHz, 798 mm x 335 mm
               3440 3488 3520 3600 hborder 0
               1440 1443 1453 1499 vborder 0
               +hsync -vsync 
Detailed mode: Clock 430.750 MHz, 798 mm x 335 mm
               3440 3488 3520 3600 hborder 0
               1440 1443 1453 1496 vborder 0
               +hsync -vsync 
Checksum: 0x8f (valid)

EDID block does NOT conform to EDID 1.3!
	Detailed block string not properly terminated
```

I wonder what I'm doing wrong, and how to make higher refresh rates like 100Hz work with an SLI setup


Akos

---

