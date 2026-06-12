---
title: "radeon open source driver 3D performance on ATI 9800 Pro"
date: 2010-06-23
forum: Hardware
---

### Post by kallew on 2010-06-23
Hey,

is there someone here with an AGP ATI Radeon 9800 (pro) card using the open source radeon driver and caring to share his experience? I get a terrible performance among 3D applications, presumably because of a faulty setup. The radeon driver can not possibly be that bad, can it?

I was upgrading from 9.04 or .10 to lucid lynx (10.04), running plain fluxbox with DRI supposedly enabled:
```
kallew@rom:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
...
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
...
GLX version: 1.2
GLX extensions:
...
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (R350 4E48) 20090101 x86/MMX+/3DNow!+/SSE TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:
...
```Running glxgears leaves me with around 300, at most 600fps per 5 seconds. 3D applications like worldwind are practically not usable and leave my cpu running at 100%.

There is no measurable difference for me between EXA and XAA - even with "EnablePageFlip" on - only setting "ColorTiling" to "1" gives me a bosst from around 300fps to 600fps. This is quite strange because according to "man radeon" that setting should be enabled by default. :confused:

I tried using an empty xorg.conf, a system generated one and my adjustments with around 600fps tops. That is, iirc, around 1/10 or even less of what I once got.
```
kallew@rom:~$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "radeon"
    BusID        "PCI:1:0:0"
    Option        "AGPMode" "4"
    Option          "DynamicClocks"            "on"
    Option        "ColorTiling"            "1"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"        "true"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection    "Display"
        Depth    16
        Modes    "1920x1200 1600x1200 1024x768 800x600 600x480"
    EndSubSection
    SubSection    "Display"
        Depth    24
        Modes    "1920x1200"
    EndSubSection
EndSection

Section "DRI"
    Mode    0666
EndSection
```There is no difference with:
```
kallew@rom:~$ cat /etc/modprobe.d/radeon-kms.conf
options radeon modeset=0
```nor reinstalling
```
kallew@rom:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-video-radeon xserver-xorg-core
```nor using
```
ppa:ubuntu-x-swat/x-updates
```The loaded modules seem to be okay, I am running an AGP Radeon 9800 Pro on an Asus A7S333 with SIS chipset, Athlon XP 2200+ and 1GB Ram.
```
kallew@rom:~$ lsmod
Module                  Size  Used by
...
i2c_sis630              4757  0 
i2c_sis96x              3024  0 
fbcon                  35102  73 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
radeon                674135  2 
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
drm                   162471  4 radeon,ttm,drm_kms_helper
sis_agp                 4047  1 
i2c_algo_bit            5028  1 radeon
agpgart                31724  3 ttm,drm,sis_agp
``````
kallew@rom:~$ dmesg | grep -e agp -e drm
[    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
[    1.749099] Linux agpgart interface v0.103
[    1.821730] agpgart-sis 0000:00:00.0: SiS chipset [1039/0745]
[    1.828084] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd8000000
[    1.873022] [drm] Initialized drm 1.1.0 20060810
[    2.726114] [drm] radeon defaulting to kernel modesetting.
[    2.726123] [drm] radeon kernel modesetting enabled.
[    2.732723] [drm] radeon: Initializing kernel modesetting.
[    2.732868] [drm] register mmio base: 0xD7800000
[    2.732871] [drm] register mmio size: 65536
[    2.735434] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[    2.735459] [drm] Generation 1 PCI interface in multifunction mode
[    2.735462] [drm] Limiting VRAM to one aperture
[    2.735474] agpgart-sis 0000:00:00.0: AGP 2.0 bridge
[    2.735501] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x mode
[    2.735580] [drm] radeon: VRAM 128M
[    2.735583] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[    2.735585] [drm] radeon: GTT 64M
[    2.735588] [drm] radeon: GTT from 0xD8000000 to 0xDBFFFFFF
[    2.735619] [drm] radeon: irq initialized.
[    2.735799] [drm] Detected VRAM RAM=128M, BAR=128M
[    2.735809] [drm] RAM width 256bits DDR
[    2.736110] [drm] radeon: 128M of VRAM memory ready
[    2.736113] [drm] radeon: 64M of GTT memory ready.
[    2.736380] [drm] radeon: 2 quad pipes, 1 Z pipes initialized.
[    2.736396] [drm] radeon: cp idle (0x10000C00)
[    2.736476] [drm] Loading R300 Microcode
[    2.762716] [drm] radeon: ring at 0x00000000D8000000
[    2.762747] [drm] ring test succeeded in 1 usecs
[    2.780532] [drm] radeon: ib pool ready.
[    2.780820] [drm] ib test succeeded in 0 usecs
[    2.781578] [drm] Default TV standard: NTSC
[    2.781582] [drm] 27.000000000 MHz TV ref clk
[    2.781588] [drm] DFP table revision: 4
[    2.781897] [drm] Default TV standard: NTSC
[    2.781900] [drm] 27.000000000 MHz TV ref clk
[    2.781976] [drm] Radeon Display Connectors
[    2.781979] [drm] Connector 0:
[    2.781981] [drm]   VGA
[    2.781985] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    2.781987] [drm]   Encoders:
[    2.781990] [drm]     CRT1: INTERNAL_DAC1
[    2.781992] [drm] Connector 1:
[    2.781994] [drm]   DVI-I
[    2.781996] [drm]   HPD1
[    2.781998] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    2.782001] [drm]   Encoders:
[    2.782003] [drm]     CRT2: INTERNAL_DAC2
[    2.782005] [drm]     DFP1: INTERNAL_TMDS1
[    2.782007] [drm] Connector 2:
[    2.782009] [drm]   S-video
[    2.782011] [drm]   Encoders:
[    2.782013] [drm]     TV1: INTERNAL_DAC2
[    2.964326] [drm] fb mappable at 0xF0040000
[    2.964332] [drm] vram apper at 0xF0000000
[    2.964334] [drm] size 9216000
[    2.964337] [drm] fb depth is 24
[    2.964339] [drm]    pitch is 7680
[    2.964789] fb0: radeondrmfb frame buffer device
[    2.964805] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
``````
kallew@rom:~$ uname -a
Linux rom 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
```I do not expect to get get a gazillion fps and I know that glxgears is no benchmark, but the current performance is just plain wrong. Is there a problem on my side or is the open source driver under lucid lynx really not suitable for anything 3D related? The information on ubuntu.net at least got me hoping ...

Thanks for any help!

---

### Post by kallew on 2010-07-01
Am I missing something obvious here? A hint in the right direction would be sufficient. :sad:

---

### Post by kallew on 2010-07-29
A software update these days seems to have solved the issue. Some X related things including the kernel were updated, so now hardware acceleration is back to normal - with glxinfo showing the same information as before.

---

