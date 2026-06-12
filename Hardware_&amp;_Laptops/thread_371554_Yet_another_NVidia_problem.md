---
title: "Yet another NVidia problem"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by detroit/zero on 2007-02-27
Hello to all.

I'm a relatively recent convert from Windows. I'm about a week into my very first venture into the Linux OS, and I'm loving Ubuntu so far. XP treated me good for a very long time, but the other day I had some kind of boot-sector error or something pop up while I slept through the night and, despite my best efforts, I ended up losing about 120GB worth of music, pictures, and saved web pages & documents - the straw that broke the camels' back, so to speak. I had some stuff backed up, so it wasn't a total loss, but still...

I'm doing alright, if I do say so myself, but I seem to have run head-first into a brick wall with my NVidia graphics card. I've been reading everything I could for the last few days, and I've seen tried about every idea I've come across, but I still can't get Ubuntu to load with my card. My ultimate goal is to again have a dual-display set up, but for now I'll settle for a single display that has 3D capabilities.

Now, where to start?

As I said, I've been sifting through these forums for a few days now. The very first thing I tried was the the Envy script ([http://albertomilone.com/nvidia_scripts1.html)]("http://albertomilone.com/nvidia_scripts1.html%29"). I had a feeling it wouldn't be that easy, and it wasn't.

A little more research led me to another how-to by tseliot ([http://albertomilone.com/latest_nvidia_udsf_edgy.html)]("http://albertomilone.com/latest_nvidia_udsf_edgy.html%29"). Still no luck.

In my reading, I noticed that the on-board graphics controller could be an issue. I thought for sure I struck gold when I found this page ([http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)]("http://doc.gwos.org/index.php/Nvidia_Intel_Integrated%29"). I couldn't have been more wrong.

While it was one of the first pages I ran across after installing Ubuntu, it took a little time for me to be confident enough to try the procedure outlined here ([http://ubuntuforums.org/showthread.php?t=33142&highlight=nvidia+install+intel)]("http://ubuntuforums.org/showthread.php?t=33142&highlight=nvidia+install+intel%29").

So, OK. Those pages sum up everything I've learned so far about Ubuntu Edgy and NVidia and how to make the two get along, yet none of them seem to apply to me. Whether I use Envy, or one of the methods outlined at the above links, or even install the drivers using Automatix, Synaptic, Add/remove programs, or even using the terminal, X always refuses to start and gives "Module Loader Present" as the reason.

The oddest thing is that I'm running on the display connected to my card right now. When I first started following the procedures in those posts, I could get it to barely work but I was stuck in 640x480 mode. I learned about the "dpkg-reconfigure xserver-xorg"  somewhere along the line which gave me decent resolutions and bit-depths, but I still enjoy none of the benefits of an NVidia card.. I can't even get Google Earth to work, much less a 3D Desktop like Beryl.

I'm sure it's gong to be a simple answer, but it's not something like changing "nv" to "nvidia" in xorg.conf (the result is the same either way). I've been over the previous instructional posts forwards, backwards, and inside out, and tried everything.

Any help will be greatly appreciated. If any more info is required just shout back.

First, my specs (here's the official HP page for my computer- [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00303943&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00303943&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN%29:"))
HP a1030n
3.01GHz P4 dual-processor
1.5GB RAM
Ubuntu Edgy
Intel 82915G Integrated Graphics Controller
NVidia GeForce FX 5500

Here's (what I think is) the relevant section from my xorg.conf file:

[html]
Section "Device"
    Identifier    "NVDIA GEFORCE FX5500"
    Driver        "nv"
    BusID        "PCI:2:03:0"
    VideoRam    256000
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    30-75
    VertRefresh    50-85
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVDIA GEFORCE FX5500"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection[/html]And here's as much of the xorg.0.log file as I'm allowed to fit into the post:
[html]
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux zero-desktop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 27 01:41:38 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVDIA GEFORCE FX5500"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/usr/share/X11/fonts/misc").
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/misc/,
    /usr/share/fonts/X11/TTF/,
    /usr/share/fonts/X11/OTF,
    /usr/share/fonts/X11/Type1/,
    /usr/share/fonts/X11/CID/,
    /usr/share/fonts/X11/100dpi/,
    /usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 1.0
    X.Org XInput driver : 0.6
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 103c,2a08 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2582 card 103c,2a08 rev 04 class 03,80,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 103c,2a0a rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 103c,2a0a rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 103c,2a0a rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 103c,2a0a rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 103c,2a0a rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 103c,2a0a rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 103c,2a0a rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 103c,2a0a rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 103c,2a0a rev 03 class 0c,05,00 hdr 00
(II) PCI: 02:01:0: chip 1106,3044 card 103c,2a0c rev 80 class 0c,00,10 hdr 00
(II) PCI: 02:02:0: chip 10ec,8139 card 103c,2a0b rev 10 class 02,00,00 hdr 00
(II) PCI: 02:03:0: chip 10de,0326 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:04:0: chip 11c1,048c card 11c1,044c rev 03 class 07,80,00 hdr 00
(II) PCI: 02:05:0: chip 1102,0007 card 1102,100a rev 00 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000c000 - 0x0000cfff (0x1000) IX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
    [0] -1    0    0x0000d000 - 0x0000efff (0x2000) IX[b]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xbe000000 - 0xbfffffff (0x2000000) MX[b]
(II) Bus 2 prefetchable memory range:
    [0] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller rev 4, Mem @ 0xbdf80000/19, 0xc0000000/28, 0xbdf40000/18, I/O @ 0xb800/3
(--) PCI:*(2:3:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xbe000000/24, 0xd0000000/28, BIOS @ 0xbffc0000/17
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
    [0] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [1] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [2] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [3] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [4] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [5] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [6] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [7] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [8] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [9] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [10] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [11] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [12] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [13] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [14] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [15] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [16] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [17] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [18] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [19] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [20] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [21] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [22] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [23] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [24] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [25] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [26] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [1] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [2] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [3] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [4] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [5] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [6] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [7] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [8] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [9] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [10] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [11] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [12] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [13] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [14] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [15] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [16] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [17] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [18] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [19] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [20] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [21] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [22] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [23] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [24] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [25] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [26] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [5] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [6] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [7] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [8] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [9] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [10] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [11] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [12] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [13] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [16] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [17] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [18] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [19] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [20] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [21] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [22] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [23] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [24] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [25] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [26] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [27] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [28] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [29] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [30] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [31] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [32] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 7.1.1, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.9746
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.2
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 0.1.1
    ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.1.0
    ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.2.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) v4l driver for Video4Linux
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
    Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
    Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
    GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
    GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
    Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
    GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
    GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
    GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
    GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
    GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
    GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
    Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
    GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
    GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
    GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
    Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
    GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
    Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
    GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
    GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
    GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
    GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
    GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
    GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
    Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
    GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
    GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
    GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
    GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
    GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
    Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
    GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
    GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
    GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
    GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
    Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
    GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
    GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
    GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
    Quadro FX 540, GeForce 6200, GeForce 6500,
    GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
    GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
    GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
    GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
    GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
    GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
    GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
    GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
    GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
    GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
    GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
    GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
    Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
    GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
    GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
    Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
    Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
    GeForce Go 6150, GeForce Go 6100
(II) Primary Device is: PCI 02:03:0
(--) Chipset GeForce FX 5500 found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [5] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [6] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [7] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [8] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [9] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [10] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [11] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [12] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [13] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [16] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [17] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [18] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [19] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [20] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [21] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [22] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [23] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [24] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [25] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [26] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [27] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [28] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [29] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [30] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [31] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [32] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [5] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [6] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [7] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [8] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [9] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [10] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [11] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [12] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [13] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [19] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [20] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [21] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [22] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [23] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [24] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [25] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [26] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [27] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [28] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [29] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [30] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [31] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [32] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [33] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [34] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [35] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
    [36] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [37] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce FX 5500"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xD0000000
(--) NV(0): MMIO registers at 0xBE000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 30.00-75.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 50.00-85.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)[/html]

---

### Post by Jimmey on 2007-02-27
> **detroit/zero said:**
> 
Section "Device"
    Identifier    "NVDIA GEFORCE FX5500"
    Driver        "nv"
    BusID        "PCI:2:03:0"
    VideoRam    256000
EndSection


Notice that the xserver is using the "nv" driver. This is the opensource driver for nVidia cards that ships with Ubuntu. It's good enough to run your desktop on, but as you've discovered, it's not got 3D accelleration. 

So what you need to do, then, is to install nVidia's closed-source drivers. You'll first need to add the "multiverse" repository. Here's how that's done.

Type "gksudo gedit /etc/apt/sources.list" into a terminal. This will open a text file of Ubuntu repositories. You need to make sure that the multiverse and universe repositories are enabled. 

To do this, remove the '#' from infront of the lines containing the world "universe". They usually look something like this:
> deb [http://gb.archive.ubuntu/com/ubuntu/](http://gb.archive.ubuntu/com/ubuntu/) edgy universe
Obviously replacing "gb" with your region code, and "edgy" with your version of Ubuntu (edgy, dapper, breezy, etc.)

After doing that, you'll need to add the multiverse repository. It usually looks like this:
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
Again, editing it as necessary. Once that's done, save and close the file.

Then by typing 
> sudo apt-get update && sudo apt-get install linux-restricted-modules-$(uname -r) && sudo apt-get install nvidia-glx && nvidia-xconfig, you'll download and enable the closed-source nVidia driver. If all goes well, you should be able to press CTRL + Backspace and have the driver work.

---

### Post by kerry_s on 2007-02-27
In edgy it's dirt simple. after you install just ->
press alt+F2, type> gksu synaptic <and click run.
click on settings> repositores
turn on all the repos
click reload
just click to highlight a line,any line> type> nvidia-glx
click on the box> mark for installation
click> apply
after it's done install, close synaptic

press alt+F2 type> xterm
type> sudo nvidia-xconfig
now close that after its done and reboot.

Most of those instructions are for older versions, it's much easier now.

---

### Post by detroit/zero on 2007-02-27
Jimmey, I tried your method first. Since I already had universe and multiverse enabled, it seemed the job was already half done. I was doing Ok until the final command
>  sudo apt-get update && sudo apt-get install linux-restricted-modules-$(uname -r) && sudo apt-get install nvidia-glx && nvidia-xconfigIt finished with an error, ("unable to write to /etc/X11/"). It seemed strange, so I broke it down into the separate commands and did them one at a time. The first few went alright; running nvidia-xconfig is where it screwed up.

Kerry_s, oddly enough, your method seemed to work and  didn't get any error messages while following your instructions.

Both methods ended with the same result, though. It was unable to load the nvidia kernel and couldn't start xserver. Something else, too, about being unable to load some module or another. It's down towards the bottom.

 Here's my latest xorg.0.log file:

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux zero-desktop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 27 07:05:11 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVDIA GEFORCE FX5500"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/usr/share/X11/fonts/misc").
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/misc/,
    /usr/share/fonts/X11/TTF/,
    /usr/share/fonts/X11/OTF,
    /usr/share/fonts/X11/Type1/,
    /usr/share/fonts/X11/CID/,
    /usr/share/fonts/X11/100dpi/,
    /usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 1.0
    X.Org XInput driver : 0.6
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 103c,2a08 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2582 card 103c,2a08 rev 04 class 03,80,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 103c,2a0a rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 103c,2a0a rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 103c,2a0a rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 103c,2a0a rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 103c,2a0a rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 103c,2a0a rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 103c,2a0a rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 103c,2a0a rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 103c,2a0a rev 03 class 0c,05,00 hdr 00
(II) PCI: 02:01:0: chip 1106,3044 card 103c,2a0c rev 80 class 0c,00,10 hdr 00
(II) PCI: 02:02:0: chip 10ec,8139 card 103c,2a0b rev 10 class 02,00,00 hdr 00
(II) PCI: 02:03:0: chip 10de,0326 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:04:0: chip 11c1,048c card 11c1,044c rev 03 class 07,80,00 hdr 00
(II) PCI: 02:05:0: chip 1102,0007 card 1102,100a rev 00 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000c000 - 0x0000cfff (0x1000) IX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
    [0] -1    0    0x0000d000 - 0x0000efff (0x2000) IX[b]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xbe000000 - 0xbfffffff (0x2000000) MX[b]
(II) Bus 2 prefetchable memory range:
    [0] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller rev 4, Mem @ 0xbdf80000/19, 0xc0000000/28, 0xbdf40000/18, I/O @ 0xb800/3
(--) PCI:*(2:3:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xbe000000/24, 0xd0000000/28, BIOS @ 0xbffc0000/17
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
    [0] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [1] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [2] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [3] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [4] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [5] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [6] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [7] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [8] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [9] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [10] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [11] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [12] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [13] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [14] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [15] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [16] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [17] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [18] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [19] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [20] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [21] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [22] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [23] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [24] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [25] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [26] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [1] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [2] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [3] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [4] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [5] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [6] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [7] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [8] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [9] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [10] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [11] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [12] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [13] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [14] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [15] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [16] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [17] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [18] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [19] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [20] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [21] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [22] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [23] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [24] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [25] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [26] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [5] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [6] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [7] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [8] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [9] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [10] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [11] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [12] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [13] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [16] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [17] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [18] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [19] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [20] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [21] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [22] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [23] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [24] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [25] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [26] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [27] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [28] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [29] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [30] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [31] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [32] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 7.1.1, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.9746
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.2
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 0.1.1
    ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.1.0
    ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.9746
    Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 09:56:41 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:03:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [5] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [6] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [7] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [8] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [9] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [10] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [11] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [12] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [13] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [14] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [15] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [16] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [17] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [18] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [19] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [20] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [21] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [22] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [23] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [24] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [25] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [26] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [27] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [28] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [29] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [30] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [31] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [32] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xbffff000 - 0xbffff0ff (0x100) MX[b]
    [5] -1    0    0xbffff400 - 0xbffff4ff (0x100) MX[b]
    [6] -1    0    0xbffff800 - 0xbfffffff (0x800) MX[b]
    [7] -1    0    0xbdf3bc00 - 0xbdf3bfff (0x400) MX[b]
    [8] -1    0    0xbf000000 - 0xbf01ffff (0x20000) MX[b](B)
    [9] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[b](B)
    [10] -1    0    0xbe000000 - 0xbeffffff (0x1000000) MX[b](B)
    [11] -1    0    0xbdf40000 - 0xbdf7ffff (0x40000) MX[b](B)
    [12] -1    0    0xc0000000 - 0xcfffffff (0x10000000) MX[b](B)
    [13] -1    0    0xbdf80000 - 0xbdffffff (0x80000) MX[b](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [19] -1    0    0x0000d400 - 0x0000d41f (0x20) IX[b]
    [20] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [21] -1    0    0x0000e000 - 0x0000e007 (0x8) IX[b]
    [22] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [23] -1    0    0x0000e800 - 0x0000e87f (0x80) IX[b]
    [24] -1    0    0x00000400 - 0x0000041f (0x20) IX[b]
    [25] -1    0    0x00008800 - 0x0000880f (0x10) IX[b]
    [26] -1    0    0x00009000 - 0x00009003 (0x4) IX[b]
    [27] -1    0    0x00009400 - 0x00009407 (0x8) IX[b]
    [28] -1    0    0x00009800 - 0x00009803 (0x4) IX[b]
    [29] -1    0    0x0000a000 - 0x0000a007 (0x8) IX[b]
    [30] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [31] -1    0    0x0000b400 - 0x0000b41f (0x20) IX[b]
    [32] -1    0    0x0000b000 - 0x0000b01f (0x20) IX[b]
    [33] -1    0    0x0000a800 - 0x0000a81f (0x20) IX[b]
    [34] -1    0    0x0000a400 - 0x0000a41f (0x20) IX[b]
    [35] -1    0    0x0000b800 - 0x0000b807 (0x8) IX[b](B)
    [36] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [37] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by kerry_s on 2007-02-27
You need to select the 386 kernel, the nvidia uses the 386 kernel. Your log says your using the generic kernel there is no nvidia driver for that kernel.

Same thing just happened to me in feisty i just installed, before the 386 would be at the top of the selection, but now the generic stays at the top. I always uninstall the generic once i install nvidia it's no good after that.

---

### Post by detroit/zero on 2007-02-27
I ended up screwing some things up pretty good. 

 I installed the 386 kernel, uninstalled the generics, loaded (or so I thought) the NVidia software, and blacklisted my Intel AGP.  The NVidia card still didn't work, and I couldn't remember where the blacklist file was, so I was completely locked out of X. Tired of sifting through backups of backups and restoring this, that, and the other - and completely lost as to what to do about any of it - I started over from scratch.(it's not like  was that far into it, anyhow...)

Here I sit on a completely fresh install of Ubuntu Edgy (with the 386 kernel), and I await further instruction. Neither of the methods from ^^ way up there will work (I just tried).

Remember, I'm a recent convert from Windows - Type slow so I'm sure to understand.

---

### Post by kerry_s on 2007-02-27
Hey sorry man, you need that generic kernel, i just reread everything and see you have dual cpu, only the generic supports dual. so try it in this order.

install "linux-restricted-modules-generic"
then the "nvidia-glx"
then run "sudo nvidia-xconfig"

Sorry if i can't get back to you quick, i'm helping grandma with renovations. and i jump on the computer when i take a break, some times i just speed through because i'm tired.

---

### Post by detroit/zero on 2007-02-27
Alright, back to the generic kernel. Check.
Restricted-modules-generic. Check.
NVida-glx. Check.
Sudo nvidia-xconfig. Check.

This is what happens to xorg.conf after running that:
```
Section "Device"
    Identifier     "Intel 82915G"
    Driver         "nvidia"
EndSection

```Not knowing much about what I'm doing, but knowing full well that that's not right, here are the settings I'm trying to use based on previous readings:

```
Section "Device"
    Identifier     "NVIDIA GEFORCE FX 5500"
    Driver         "nvidia"
    BusID        "PCI:2:3:0"
    VideoRam    256000
    Option        "NvAGP" "1"
EndSection
```By this point, the onboard graphics have to be disabled (and blacklisted in /etc/hotplug/blacklist):
```
agpgart
intel_agp
```(I've tried it both with and without the "NVAGP" switch - the result is the same. Also, somewhere I read to comment out the BusID line, but when  do that, Ubuntu freezes when bootng.) It always says that it can't load some "wsb module" (or something along those lines) and that it can't load the nvidia kernel, then locks up.


It looks right to me (not that I know any better), but if there's no nvidia driver for the generic kernel, and I have to use the generic kernel, am I just chasing the wind, here?

---

### Post by detroit/zero on 2007-02-28
Well, now I'm screwed.

I found a how-to at this page [http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)

It seemed recent enough, so I gave it a whirl and it worked. Or so I thought.

Ubuntu still froze on me during boot up. The little status bar under the logo? It always freezes when it's jumping into it's 3rd segment (what happens at that point, I don't know - you tell me). So I reboot into restore-mode, copy back xorg.conf from the backup and delete the hotplug blacklist.. piece of cake - I've done it a million times now. But after replacing those files and rebootning, it does its forced file system check, and it turned up errors and rebooted.

Now when loading, it says xserver isn't installed or is corrupted, and I'm stuck in the command-prompt.

I'm running off the live cd right now, can't get into my hard disk, and it's looking like I have to do another re-install.

Please tell me I don't.

---

### Post by kerry_s on 2007-02-28
There's drivers for the generic, i just worded that wrong. If you just install nvidia-glx it does not grab the restricted modules on it's own.

```
Section "Device"
    Identifier     "Intel 82915G"
    Driver         "nvidia"
EndSection
```

This is correct, don't add extra settings till it's working and only if you know what there actually for( [http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/index.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/index.html) )

```
By this point, the onboard graphics have to be disabled (and blacklisted in /etc/hotplug/blacklist):

```

Don't blacklist.


It sounds like your in for another reinstall. Try it in this order this time and don't touch the configuration let the nvidia-xconfig do the work.

install "linux-restricted-modules-generic"
then the "nvidia-glx"
then run "sudo nvidia-xconfig"
reboot


If get stuck in command line try looking through the> man nvidia-xconfig

---

### Post by Hedghg88 on 2007-03-01
sudo apt-get install nvidia-glx linux-restricted-modules-$(uname -r)
sudo nvidia-glx-config enable

This code worked great for the 5200. I was having all kinds of problems until I found this.

---

### Post by detroit/zero on 2007-03-02
Didn't work. 

I still freeze up in the same spot. At first it said It didn't have a kernel to load, but I still have the NVidia installer on my drive, so I let it run and compile me a kernel, then when I tried to load X it gave me 8 or 9 screens worth of code that ended with "smp_apic_timer_interrupt" and a bunch of hex. I tried booting Ubuntu with a "-nohotplug" switch (just because it works on my USB SLAX and wtf do I know) and it did the same thing.

All I know is that I had to disable the video card to even run the Live CD and install the OS, so something here wasn't meant to be - either Ubuntu and my video card, or Me & Ubuntu.

I appreciate you guys' help on this, but I think I'm going to have to find someone local to me that can come by and check this thng out & give it a whirl. I've got almost a week's worth of spare time (and then some) wrapped up into reading a million posts and a million ideas on Ubuntu, Suse, Debian, and NVidia forums, and trying to make this thing work - and I haven't made it off square one yet. I guess I don't know enough about what I'm doing to attempt something like this, and if I waste all my time on a video card I'll never have a chance to learn anything else.


Thanks again.

---

