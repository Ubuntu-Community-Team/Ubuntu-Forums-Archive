---
title: "Feisty doesn't like ATI X700 in asus A6Va"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by arkangel on 2007-04-23
Hi 

In dapper I install the propietary driver tll 8.32  from that version  i always got the a black screen anyways i was happy until I updated to Feisty.

I follow  [this]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")  method one installs the driver but cannot use it

method two  i got the same blank screen as in dapper and whenever i try the versions below 8.33 i cannot build the deb (these version were working well in dapper)

with versions over 8.33  when I try to do aticonfig --initial either i got "no xorg.conf  file model found " or "segment fault".   

Any of you could do it ,  any of you have a hint  or need more info ,  btw i am using the kernel 2.20.15-i386  and this has smth to do ?

---

### Post by arkangel on 2007-04-23
I build again using the driver from ati web page 

whenever I used  aticonfig --initial  i got 
8048000-08067000 r-xp 00000000 08:02 3476680    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:02 3476680    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c6f000-b7c70000 rw-p b7c6f000 00:00 0 
b7c70000-b7c72000 r-xp 00000000 08:02 4146440    /lib/tls/i686/cmov/libdl-2.5.so
b7c72000-b7c74000 rw-p 00001000 08:02 4146440    /lib/tls/i686/cmov/libdl-2.5.so
b7c74000-b7c75000 rw-p b7c74000 00:00 0 
b7c75000-b7c79000 r-xp 00000000 08:02 3474693    /usr/lib/libXdmcp.so.6.0.0
b7c79000-b7c7a000 rw-p 00003000 08:02 3474693    /usr/lib/libXdmcp.so.6.0.0
b7c7a000-b7c7c000 r-xp 00000000 08:02 3474682    /usr/lib/libXau.so.6.0.0
b7c7c000-b7c7d000 rw-p 00001000 08:02 3474682    /usr/lib/libXau.so.6.0.0
b7c7d000-b7db8000 r-xp 00000000 08:02 4146434    /lib/tls/i686/cmov/libc-2.5.so
b7db8000-b7db9000 r--p 0013b000 08:02 4146434    /lib/tls/i686/cmov/libc-2.5.so
b7db9000-b7dbb000 rw-p 0013c000 08:02 4146434    /lib/tls/i686/cmov/libc-2.5.so
b7dbb000-b7dbe000 rw-p b7dbb000 00:00 0 
b7dbe000-b7de3000 r-xp 00000000 08:02 4146442    /lib/tls/i686/cmov/libm-2.5.so
b7de3000-b7de5000 rw-p 00024000 08:02 4146442    /lib/tls/i686/cmov/libm-2.5.so
b7de5000-b7ed2000 r-xp 00000000 08:02 3474676    /usr/lib/libX11.so.6.2.0
b7ed2000-b7ed6000 rw-p 000ed000 08:02 3474676    /usr/lib/libX11.so.6.2.0
b7ed6000-b7ee3000 r-xp 00000000 08:02 3474697    /usr/lib/libXext.so.6.4.0
b7ee3000-b7ee4000 rw-p 0000d000 08:02 3474697    /usr/lib/libXext.so.6.4.0
b7ee4000-b7ee5000 rw-p b7ee4000 00:00 0 
b7ee5000-b7eec000 r-xp 00000000 08:02 3474719    /usr/lib/libXrender.so.1.3.0
b7eec000-b7eed000 rw-p 00006000 08:02 3474719    /usr/lib/libXrender.so.1.3.0
b7eed000-b7ef2000 r-xp 00000000 08:02 3474717    /usr/lib/libXrandr.so.2.1.0
b7ef2000-b7ef3000 rw-p 00005000 08:02 3474717    /usr/lib/libXrandr.so.2.1.0
b7ef5000-b7f00000 r-xp 00000000 08:02 4112448    /lib/libgcc_s.so.1
b7f00000-b7f01000 rw-p 0000a000 08:02 4112448    /lib/libgcc_s.so.1
b7f01000-b7f04000 rw-p b7f01000 00:00 0 
b7f04000-b7f1d000 r-xp 00000000 08:02 4112405    /lib/ld-2.5.so
b7f1d000-b7f1f000 rw-p 00019000 08:02 4112405    /lib/ld-2.5.so
bff62000-bff78000 rw-p bff62000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

and an empty xorg.conf 
 when i force it with aticonfig --initial --force  it works  but  my xorg only contain the device name and the driver,  i cannot go further with aticonfig --overlay-type=Xv  again the info as above  if i restart without doing the overlay stuff i got a lines(see below). i suspect i need to configure manualy the part that overlay does  

when i type aticonfig --overlay=Xv, what does this command add or modify in the xorg.conf?   how can i check if the drivers is not build correctly or it is a configuration issue 

if U see  the xorg.conf seems to be incomplete there are no modes in the screen section , is that ok? , it will work anyway?  

 > 

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection




---

### Post by mrThefter on 2007-04-25
First off, you can't aticonfig anymore, when an X server is running. That means no GUI, and you need to be be in console mode, or you get coredumps/segfaults.

Secondly, Feisty doesn't seem to work very well with ATI Proprietary Drivers at the moment. I'm trying to get that fixed at the moment.

ddc is the offending module. After reading the modelines for a monitor, then attempting to set a modeline, it crashes. 
Disabling DDC might help, but since NoDDC doesn't work for the fglrx drivers, just comment it out up a bit in xorg.conf, then rename /usr/lib/xorg/modules/libddc.so to something recognizable (so you can restore it later)

---

### Post by arkangel on 2007-04-27
Hi  thanks

It didnt work,   I rebulit again and i disable the ddc module  

i am at office latter i will put the Xorg.0.log  result concerning fglrx  , i hope a new driver will be soon released ( one that works) :S

---

### Post by arkangel on 2007-04-27
i have tried  any recommendation i could found   no hope so far 

there is my Xorg.0.log  when using the fglrx

---

### Post by mrThefter on 2007-04-27
It doesn't look like the kernel module is loading. That might be why...
Install the module, then do a depmod -ae

---

### Post by arkangel on 2007-04-28
No hope, i forced the depmod  with -ae (the same lines as in the picture)  

there is something  weird though,   ln my .Xorg0.log



> 

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux greybox 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 28 23:21:55 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2590 card 1043,1977 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2591 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,2668 card 1043,1173 rev 04 class 04,03,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,2658 card 1043,1177 rev 04 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1043,1177 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1043,1177 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1043,1177 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1043,1177 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d4 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2641 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1043,1177 rev 04 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 0000,0000 rev 04 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4320 card 1043,173c rev 13 class 02,00,00 hdr 00
(II) PCI: 02:01:0: chip 1180,0476 card d000,0000 rev b3 class 06,07,00 hdr 82
(II) PCI: 02:01:1: chip 1180,0552 card 1043,1177 rev 08 class 0c,00,10 hdr 80
(II) PCI: 02:01:2: chip 1180,0822 card 1043,1177 rev 17 class 08,05,00 hdr 80
(II) PCI: 02:01:3: chip 1180,0592 card 1043,1177 rev 08 class 08,80,00 hdr 80
(II) PCI: 02:03:0: chip 8086,4220 card 8086,2701 rev 05 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000cfff (0x3000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcff00000 - 0xdfefffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,6), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x55ffffff (0x6000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:1:0), (2,3,6), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfeafa000 - 0xfeafafff (0x1000) MX[B]
	[1] -1	0	0xfeafbc00 - 0xfeafbcff (0x100) MX[B]
	[2] -1	0	0xfeafb800 - 0xfeafb8ff (0x100) MX[B]
	[3] -1	0	0xfeafb000 - 0xfeafb7ff (0x800) MX[B]
	[4] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[5] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[6] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[7] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[8] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[9] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[10] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[15] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[17] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafa000 - 0xfeafafff (0x1000) MX[B]
	[1] -1	0	0xfeafbc00 - 0xfeafbcff (0x100) MX[B]
	[2] -1	0	0xfeafb800 - 0xfeafb8ff (0x100) MX[B]
	[3] -1	0	0xfeafb000 - 0xfeafb7ff (0x800) MX[B]
	[4] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[5] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[6] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[7] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[8] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[9] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[10] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[15] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[17] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafa000 - 0xfeafafff (0x1000) MX[B]
	[5] -1	0	0xfeafbc00 - 0xfeafbcff (0x100) MX[B]
	[6] -1	0	0xfeafb800 - 0xfeafb8ff (0x100) MX[B]
	[7] -1	0	0xfeafb000 - 0xfeafb7ff (0x800) MX[B]
	[8] -1	0	0xfeafc000 - 0xfeafffff (0x4000) MX[B]
	[9] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[10] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[21] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[23] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[B](II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.36.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0[/B]
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) ATI Proprietary Linux Driver Version Identifier:8.36.5
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.36g1                           
(II) ATI Proprietary Linux Driver Build Date: Apr 17 2007 10:04:24
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.36.1.1.2.3-driver-lnx-x86-x86_64-338188
(EE) No devices detected.

Fatal server error:
no screens found




the fglrx part says build for  7.1  . Shouldnt be for 7.2   ?

---

### Post by mrThefter on 2007-05-01
yeah, fglrx is compiled for 7.1
There's no true 7.2 support yet. Bug ATi, maybe it'll get done in six months.

---

### Post by elmulo on 2007-05-01
I have the same notebook and from the live cd I get video from a second lcd attached to the rgb out port.

---

### Post by arkangel on 2007-05-02
> **elmulo said:**
> I have the same notebook and from the live cd I get video from a second lcd attached to the rgb out port.

But in general you have the same problem ?    with the live cd i have no problem cauze it is the ati driver installed , the problen it is that i have followed all tutorials and wiki i could find :S

---

### Post by tamagoji on 2007-05-02
i have the same problem with ati x300. 
it does not detect the device.
I have read, on the ati website, that also the latest version of the driver is compiled for Xorg7.1.
any workaround?

(if the problem is the version of xorg, i wonder how someone is able to let them work with feisty, considering that it installs by default 7.2 version)

---

### Post by Fulvio86 on 2007-05-02
i have an asus a6va with a x700 and i have the same problem with all distribution of linux!!
only with Dapper and driver ati 8.28 the grafic card work fine!! 
Can anyone tellme why there are this problem with this card in that model of notebook???
In edgy and feisty the screen are white and can't be built the proprietary driver!!! why??? 
excuse me for the terrible english
thanks 
bye

---

### Post by elmulo on 2007-05-02
Well, for me its black screen on the notebook but I can get the video to output to a second screen from the rgb port. This is when starting X. It has also happened to me with a lot of linux distributions. Linspire live Cd runs fine though (last time I tried). 

Good notebook overall, but the keyboard sucks.

---

### Post by arkangel on 2007-05-03
> **Fulvio86 said:**
> i have an asus a6va with a x700 and i have the same problem with all distribution of linux!!
only with Dapper and driver ati 8.28 the grafic card work fine!! 
Can anyone tellme why there are this problem with this card in that model of notebook???
In edgy and feisty the screen are white and can't be built the proprietary driver!!! why??? 
excuse me for the terrible english
thanks 
bye


Hi  I was able to install till 8.32 in dapper ,   from 8.33 no way ,  whenever i read the /var/log/Xorg.log  it is incomplete the system just hang up , the only difference is that the ddc module is not getting info from my screen i tried disabling  but the system just stops  and there is no more info availble in the logs

I read something about the mesa dri libraries and we are suppose to downgrade, if i am able to find the page again i will post it

---

### Post by Fulvio86 on 2007-05-04
ok thank you!!!! I'm really frustrated for this problem because i can use only dapper!!!

---

### Post by ratazana80 on 2007-05-10
Hi,

I also own a Asus A6VA, and I can't get the X700 to work on Fesity :(

---

### Post by tinolupin on 2007-05-10
i also have A6VA.. my X700 is not compatible with all new ati driver (es. Catalist 7.1 for winxp).. Flash bios of the video card, it's can be a solution?

---

### Post by arkangel on 2007-05-11
apparently not  until the new release of ati driver that support Xorg 7.2 i mean fully  ,  but still on my quest ...

---

### Post by Cylence on 2007-05-13
I'm having the same problem. Since I'm getting tired of having to spend lots of time for a video card I've paid, I won't buy Ati anymore until they show some respect to their Linux users.

---

