---
title: "No monitor found error with XServer"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by StubornAH on 2006-01-18
I installed Ubuntu tonight on my Gateway laptop.  After the installation it tried to enter XWindows but it got an error.  The log said that no monitor was found.  I checked my Windows partition and it uses the default monitor driver.  Ubuntu also tried its default monitor driver.  Any suggestions?  Before installing I talked to Gateway and they said there were no foreseeable problems with dual-booting with Linux and Windows.

So, I guess my question is what do I need to fix this and how do I do it from the command line that you get on booting.  I read some man pages and tried startx -- -dpi 96 and xinit but I don't really know what I am doing.  I am sumwhat familiar with a Unix like environment as that is what I use at school but I always use GUI stuff when available.

Thanks for the help.

---

### Post by StubornAH on 2006-01-19
bump...

Anyone got any idea?

---

### Post by StubornAH on 2006-01-20
I found this post and tried to reconfigure xserver and it didn't work.  So, here is the log that I got, maybe someone will understand what it means.

Thanks.

Other Post
[http://www.ubuntuforums.org/showthread.php?t=119574](http://www.ubuntuforums.org/showthread.php?t=119574)


Log


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux PhucLinux 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 19 22:51:44 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2590 card 107b,0604 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2591 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,2658 card 107b,0604 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 107b,0604 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 107b,0604 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 107b,0604 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 107b,0604 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d3 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 107b,0604 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1e:3: chip 8086,266d card 107b,0604 rev 03 class 07,03,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2641 card 107b,0604 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 107b,0604 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 107b,0604 rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5653 card 107b,0604 rev 00 class 03,00,00 hdr 00
(II) PCI: 06:00:0: chip 14e4,1654 card 107b,0604 rev 03 class 02,00,00 hdr 00
(II) PCI: 06:04:0: chip 8086,4220 card 8086,2701 rev 05 class 02,80,00 hdr 00
(II) PCI: 06:09:0: chip 104c,8031 card 4000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 06:09:2: chip 104c,8032 card 107b,0604 rev 00 class 0c,00,10 hdr 80
(II) PCI: 06:09:3: chip 104c,8033 card 107b,0604 rev 00 class 01,80,00 hdr 80
(II) PCI: 06:09:4: chip 104c,8034 card 107b,0604 rev 00 class 08,05,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc8100000 - 0xc81fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,7), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xc8200000 - 0xc82fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:9:0), (6,7,10), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x5653) rev 0, Mem @ 0xd0000000/27, 0xc8100000/16, I/O @ 0x3000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xc8217800 - 0xc82178ff (0x100) MX[B]
	[1] -1	0	0xc8217c00 - 0xc8217cff (0x100) MX[B]
             .
             .
             .
	[23] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc8217800 - 0xc82178ff (0x100) MX[B]
	[1] -1	0	0xc8217c00 - 0xc8217cff (0x100) MX[B]
             .
             .
             .
	[23] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
             .
             .
             .
	[30] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 6.5.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
             .
             .
             .
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI Radeon Mobility M7 LW (AGP),
             .
             .
             .
	ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
	ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon Mobility X700 (RV410)".
(WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by StubornAH on 2006-01-20
I used the command 'lspci' to find out where my video card was and now I see it is listed in the log.

Anyway it said something like 0000:01:00.0 VGA ATI ..., unknown 5653.

I have never been a hardware person, I like to program software; so I am a little lost here.

---

### Post by dueY on 2006-01-20
Are you sure it's not your video card?  I'm not really an expert on this, though I have had to jump through way more than my fair share of hoops to configure my X and video card when I first started.

```
(WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected!
(EE) No devices detected.

```

Looks like it's the video card, but again; I'm no expert.

Have you tried using different video drivers?  If ATI is anything like NVIDIA then there is probably an "ati" driver that is defaulted.  If so try using the "vesa" one, that one worked for me.  If that one doesn't work try using "vga" which really sucks with a super low resolution and 4-bit colors but may work.  If these work and you can get into a GUI and go to ATI's web page and download their proprietary driver.  Hope this helps.

---

### Post by adam.tropics on 2006-01-20
Not sure of your specific card but if you do ***$sudo dpkg-reconfigure xserver-xorg*** and follow through that picking defaults except use vesa (temporarily) for video card driver, then go to this [howto]("http://ubuntuforums.org/showpost.php?p=423584") you may have some luck. Again though I am not sure about that exact card, but vesa should at least get you an X session from where you can better deal with all this. Good luck.

---

### Post by StubornAH on 2006-01-20
Thanks guys, running in vesa worked.

So, I downloaded ATI's driver program and can't run it.  

My command was
sudo ./ati-driver-installer-8.21.7-i386.run   then I enter my password and it replies

"sudo: ./ati-driver-installer-8.21.7-i386.run: command not found"

Now I am in the correct directory, is there something special I have to do?

Thanks.

---

### Post by InvIsiBlekID on 2006-01-20
I'm having the same problem with my Gateway laptop.  I havent tried vesa yet, but I will when I get home from work.  Hey StubornAH, what model Gateway do you have?

---

### Post by InvIsiBlekID on 2006-01-20
I may have found something of use for this problem.  Try to comment dri in your xorg.conf.

```
Load dri
```

change to

```
#Load dri
```

[http://ubuntuforums.org/showthread.php?t=75590&page=2&highlight=ati+radeon+xpress+200m](http://ubuntuforums.org/showthread.php?t=75590&page=2&highlight=ati+radeon+xpress+200m)

that's where i got the idea.  good luck!

---

### Post by dueY on 2006-01-20
[QUOTE=StubornAH]Thanks guys, running in vesa worked.

So, I downloaded ATI's driver program and can't run it.  

My command was
sudo ./ati-driver-installer-8.21.7-i386.run   then I enter my password and it replies

"sudo: ./ati-driver-installer-8.21.7-i386.run: command not found"

Now I am in the correct directory, is there something special I have to do?

Thanks.[/QUOTE]

When you're in the directory make use of the TAB key to make sure the file name is exact.

---

