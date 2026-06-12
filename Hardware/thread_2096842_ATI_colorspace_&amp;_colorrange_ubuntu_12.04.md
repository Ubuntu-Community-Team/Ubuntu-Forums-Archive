---
title: "ATI colorspace &amp; colorrange ubuntu 12.04"
date: 2012-12-21
forum: Hardware
---

### Post by peeal on 2012-12-21
hello 

has anyone truly got full rgb working with ati in ubuntu? im using ati radeon hd6450 and im trying to configure this to work with xbmc. Now problem is that i have Panasonic PT-AE4000 projector + Onkyo TX-SR609 AV receiver and they accept full rgb and i have full rgb in projector settings. I have popcorn hour C-200 which outputs full rgb signal and its calibrated using popcorn hour. 

ive had couple ati gpu htpc:s and all of them have had this problem, ubuntu desktop and xbmc colors are washed / greyish. 

xorg.conf looks like this

```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        Option      "ColorSpace" "RGB"
        Option      "ColorRange" "Full"
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```xorg.0.log has couple odd markings 

```
[  [  6182.438] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[  6182.438] X Protocol Version 11, Revision 0
[  6182.438] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[  6182.438] Current Operating System: Linux Mustalaatikko 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64
[  6182.438] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-35-generic root=/dev/mapper/Mustalaatikko-root ro
[  6182.438] Build Date: 29 August 2012  12:12:33AM
[  6182.438] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[  6182.438] Current version of pixman: 0.24.4
[  6182.438]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[  6182.438] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  6182.438] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 21 01:02:02 2012
[  6182.438] (==) Using config file: "/etc/X11/xorg.conf"
[  6182.438] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  6182.439] (==) ServerLayout "amdcccle Layout"
[  6182.439] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[  6182.439] (**) |   |-->Monitor "<default monitor>"
[  6182.439] (**) |   |-->Device "aticonfig-Device[0]-0"
[  6182.439] (==) No monitor specified for screen "aticonfig-Screen[0]-0".
        Using a default monitor configuration.


[  6182.902] (II) fglrx(0): Connected Display0: DFP1
[  6182.902] (II) fglrx(0): Display0 EDID data ---------------------------
[  6182.902] (II) fglrx(0): Manufacturer: ONK  Model: b62  Serial#: 0
[  6182.902] (II) fglrx(0): Year: 2011  Week: 0
[  6182.902] (II) fglrx(0): EDID Version: 1.3
[  6182.902] (II) fglrx(0): Digital Display Input
[  6182.902] (II) fglrx(0): Indeterminate output size
[  6182.902] (II) fglrx(0): Gamma: 2.20
[  6182.902] (II) fglrx(0): No DPMS capabilities specified
[  6182.902] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  6182.902] (II) fglrx(0): First detailed timing is preferred mode

[  6182.934] (II) LoadModule: "glesx"
[  6182.934] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[  6182.935] (II) Module glesx: vendor="X.Org Foundation"
[  6182.935]    compiled for 1.4.99.906, module version = 1.0.0
[  6182.935] (II) Loading extension GLESX
[  6182.935] (II) fglrx(0): GLESX enableFlags = 592
[  6182.935] (II) fglrx(0): GLESX is enabled
[  6182.935] (II) LoadModule: "amdxmm"
[  6182.936] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[  6182.936] (II) Module amdxmm: vendor="X.Org Foundation"
[  6182.936]    compiled for 1.4.99.906, module version = 2.0.0
[  6182.948] (II) Loading extension AMDXVOPL
[  6182.948] (II) Loading extension AMDXVBA
[  6182.950] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[  6182.953] (EE) fglrx(0): allocate shared exclusive (EE) fglrx(0): 
[  6182.970] (II) fglrx(0): Enable composite support successfully
[  6182.970] (WW) fglrx(0): Option "ColorSpace" is not used
[  6182.970] (WW) fglrx(0): Option "ColorRange" is not used
[  6182.970] (II) fglrx(0): X context handle = 0x1
[  6182.970] (II) fglrx(0): [DRI] installation complete
[  6182.971] (==) fglrx(0): Silken mouse enabled
[  6182.971] (==) fglrx(0): Using HW cursor of display infrastructure!
[  6182.971] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[  6182.981] (II) fglrx(0): User Preference Output DFP1 using refresh rate 24.0 Hz.


```everything else works like a charm in ubuntu and xbmc. 1080p and dts sound etc. but cant replace my popcorn hour if i cant get full rgb signal :( ive tryed to change colorspace to YCrCb and colorrange to limited but nothing changes its allways the same washed out picture.

---

