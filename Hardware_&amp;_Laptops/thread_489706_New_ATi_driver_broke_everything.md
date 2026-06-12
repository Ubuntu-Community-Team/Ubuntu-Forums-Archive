---
title: "New ATi driver broke everything"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by weblordpepe on 2007-07-01
Hi there I've installed the very latest ATi drivers from the ATi website. The 25th of June drivers.

They were OK but I wanted to remove them because they made Doom3 go funny.

Anyway I am wondering how do you uninstall them? For some reason no games function correctly & doom3 wont even start. The open-source drivers are great.
But whenever I switch to the restricted ATI driver, this crap happens. Help! Is there any way I can re-install the restricted ATi drivers from a repository or something?

This downloaded driver really screwed up my Ubuntu.

When I load up a quake3 engine game or doom3 i get this:
> ...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

typing **lsmod | grep fgl** gives:
> fglrx                 682988  0 
agpgart                35400  2 fglrx,intel_agp

And attempting to run the ati control panel gives me this:
```

pepe@davobug:~$ amdcccle 
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    145 (Uknown extension)
  Minor opcode: 33 (Unknown request)
  Resource id:  0x3d
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    145 (Uknown extension)
  Minor opcode: 48 (Unknown request)
  Resource id:  0x3d
*** glibc detected *** amdcccle: munmap_chunk(): invalid pointer: 0xbf8bda8c ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0x4e3def5b]
amdcccle[0x81b0cb7]
amdcccle(AtiXUPcs_GetVal+0x68)[0x81b0b18]
amdcccle[0x81ad4db]
amdcccle(AtiXUDisp_InitContext+0x32)[0x81ac932]
amdcccle(AtiXUPriv_InitContext+0x51)[0x81abd01]
amdcccle(__AtiXUtil_Open+0xbb)[0x81aa5bb]
amdcccle(main+0x186)[0x814cfb6]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0x4e389ebc]
amdcccle[0x814ac31]
======= Memory map: ========
08048000-086d2000 r-xp 00000000 08:03 772903     /usr/bin/amdcccle
086d2000-0878f000 rwxp 0068a000 08:03 772903     /usr/bin/amdcccle
0878f000-087f6000 rwxp 0878f000 00:00 0          [heap]
4d9a5000-4d9be000 r-xp 00000000 08:03 606262     /lib/ld-2.5.so
4d9be000-4d9c0000 rwxp 00019000 08:03 606262     /lib/ld-2.5.so
4d9da000-4da8c000 r-xp 00000000 08:03 772505     /usr/lib/libstdc++.so.5.0.7
4da8c000-4da91000 rwxp 000b1000 08:03 772505     /usr/lib/libstdc++.so.5.0.7
4da91000-4da97000 rwxp 4da91000 00:00 0 
4e374000-4e4af000 r-xp 00000000 08:03 640204     /lib/tls/i686/cmov/libc-2.5.so
4e4af000-4e4b0000 r-xp 0013b000 08:03 640204     /lib/tls/i686/cmov/libc-2.5.so
4e4b0000-4e4b2000 rwxp 0013c000 08:03 640204     /lib/tls/i686/cmov/libc-2.5.so
4e4b2000-4e4b5000 rwxp 4e4b2000 00:00 0 
4e4b7000-4e4b9000 r-xp 00000000 08:03 5292034    /lib/tls/i686/cmov/libdl-2.5.so
4e4b9000-4e4bb000 rwxp 00001000 08:03 5292034    /lib/tls/i686/cmov/libdl-2.5.so
4e4bd000-4e4e2000 r-xp 00000000 08:03 5292033    /lib/tls/i686/cmov/libm-2.5.so
4e4e2000-4e4e4000 rwxp 00024000 08:03 5292033    /lib/tls/i686/cmov/libm-2.5.so
4e4e6000-4e4f9000 r-xp 00000000 08:03 5292035    /lib/tls/i686/cmov/libpthread-2.5.so
4e4f9000-4e4fb000 rwxp 00013000 08:03 5292035    /lib/tls/i686/cmov/libpthread-2.5.so
4e4fb000-4e4fd000 rwxp 4e4fb000 00:00 0 
4e4ff000-4e512000 r-xp 00000000 08:03 772114     /usr/lib/libz.so.1.2.3
4e512000-4e513000 rwxp 00012000 08:03 772114     /usr/lib/libz.so.1.2.3
4e515000-4e517000 r-xp 00000000 08:03 784242     /usr/lib/libXau.so.6.0.0
4e517000-4e518000 rwxp 00001000 08:03 784242     /usr/lib/libXau.so.6.0.0
4e51a000-4e51e000 r-xp 00000000 08:03 784243     /usr/lib/libXdmcp.so.6.0.0
4e51e000-4e51f000 rwxp 00003000 08:03 784243     /usr/lib/libXdmcp.so.6.0.0
4e521000-4e60e000 r-xp 00000000 08:03 784244     /usr/lib/libX11.so.6.2.0
4e60e000-4e612000 rwxp 000ed000 08:03 784244     /usr/lib/libX11.so.6.2.0
4e614000-4e621000 r-xp 00000000 08:03 784250     /usr/lib/libXext.so.6.4.0
4e621000-4e622000 rwxp 0000d000 08:03 784250     /usr/lib/libXext.so.6.4.0
4e6f7000-4e715000 r-xp 00000000 08:03 772866     /usr/lib/libexpat.so.1.0.0
4e715000-4e717000 rwxp 0001d000 08:03 772866     /usr/lib/libexpat.so.1.0.0
4e73e000-4e745000 r-xp 00000000 08:03 784245     /usr/lib/libXrender.so.1.3.0
4e745000-4e746000 rwxp 00006000 08:03 784245     /usr/lib/libXrender.so.1.3.0
4e748000-4e7b0000 r-xp 00000000 08:03 772547     /usr/lib/libfreetype.so.6.3.10
4e7b0000-4e7b3000 rwxp 00068000 08:03 772547     /usr/lib/libfreetype.so.6.3.10
4e7ba000-4e7be000 r-xp 00000000 08:03 784254     /usr/lib/libXfixes.so.3.1.0
4e7be000-4e7bf000 rwxp 00003000 08:03 784254     /usr/lib/libXfixes.so.3.1.0
4e7c1000-4e7c8000 r-xp 00000000 08:03 784252     /usr/lib/libXi.so.6.0.0
4e7c8000-4e7c9000 rwxp 00006000 08:03 784252     /usr/lib/libXi.so.6.0.0
4e7cb000-4e7ee000 r-xp 00000000 08:03 772869     /usr/lib/libfontconfig.so.1.2.0
4e7ee000-4e7f6000 rwxp 00023000 08:03 772869     /usr/lib/libfontconfig.so.1.2.0
4e7f8000-4e800000 r-xp 00000000 08:03 784255     /usr/lib/libXcursor.so.1.0.2
4e800000-4e801000 rwxp 00007000 08:03 784255     /usr/lib/libXcursor.so.1.0.2
4e808000-4e80d000 r-xp 00000000 08:03 784253     /usr/lib/libXrandr.so.2.1.0
4e80d000-4e80e000 rwxp 00005000 08:03 784253     /usr/lib/libXrandr.so.2.1.0
4e99a000-4e9a2000 r-xp 00000000 08:03 784302     /usr/lib/libSM.so.6.0.0
4e9a2000-4e9a3000 rwxp 00007000 08:03 784302     /usr/lib/libSM.so.6.0.0
4e9a5000-4e9ba000 r-xp 00000000 08:03 784301     /usr/lib/libICE.so.6.3.0
4e9ba000-4e9bc000 rwxp 00014000 08:03 784301     /usr/lib/libICE.so.6.3.0
4e9bc000-4e9bd000 rwxp 4e9bc000 00:00 0 
4e9bf000-4e9ca000 r-xp 00000000 08:03 607379     /lib/libgcc_s.so.1
4e9ca000-4e9cb000 rwxp 0000a000 08:03 607379     /lib/libgcc_s.so.1
b7cc2000-b7cc8000 r-xs 00000000 08:03 245937     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b7cc8000-b7cc9000 r-xs 00000000 08:03 245965     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b7cc9000-b7ccc000 r-xs 00000000 08:03 245953     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b7ccc000-b7ccd000 r-xs 00000000 08:03 245959     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b7ccd000-b7cce000 r-xs 00000000 08:03 245940     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b7cce000-b7cd2000 r-xs 00000000 08:03 245934     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b7cd2000-b7cd3000 r-xs 00000000 08:03 245922     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b7cd3000-b7cd5000 r-xs 00000000 08:03 245927     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b7cd5000-b7cd7000 r-xs 00000000 08:03 245915     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b7cd7000-b7cd8000 r-xs 00000000 08:03 245930     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b7cd8000-b7cda000 r-xs 00000000 08:03 245938     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b7cda000-b7ce0000 r-xs 00000000 08:03 245928     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b7ce0000-b7ce2000 r-xs 00000000 08:03 245954     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b7ce2000-b7ce4000 r-xs 00000000 08:03 245951     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b7ce4000-b7cec000 r-xs 00000000 08:03 245957     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b7cec000-b7cf2000 r-xs 00000000 08:03 245911     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b7cf2000-b7cf3000 r-xs 00000000 08:03 245920     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b7cf3000-b7d0a000 r-xs 00000000 08:03 248521     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b7d0a000-b7d0c000 r-xs 00000000 08:03 245955     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b7d0c000-b7d12000 r-xs 00000000 08:03 245949     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b7d12000-b7d15000 r-xs 00000000 08:03 245926     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b7d15000-b7d19000 r-xs 00000000 08:03 245909     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b7d19000-b7d1b000 r-xs 00000000 08:03 248100     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b7d1b000-b7d1c000 r-xs 00000000 08:03 245963     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b7d1c000-b7d1d000 r-xs 00000000 08:03 245960     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b7d1d000-b7d1e000 r-xs 00000000 08:03 245945     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b7d1e000-b7d1f000 r-xs 00000000 08:03 245916     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b7d1f000-b7d20000 r-xs 00000000 08:03 251740     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b7d20000-b7d23000 r-xs 00000000 08:03 245942     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b7d23000-b7d28000 r-xs 00000000 08:03 251739     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b7d28000-b7d2a000 r-xs 00000000 08:03 245908     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b7d2a000-b7d2b000 r-xs 00000000 08:03 245961     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b7d2b000-b7d2d000 r-xs 00000000 08:03 245913     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b7d2d000-b7d2e000 r-xs 00000000 08:03 245939     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b7d2e000-b7d33000 r-xs 00000000 08:03 245933     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b7d33000-b7d37000 r-xs 00000000 08:03 245910     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b7d37000-b7d39000 r-xs 00000000 08:03 245931     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b7d39000-b7d3c000 r-xs 00000000 08:03 245923     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b7d3c000-b7d3d000 r-xs 00000000 08:03 245956     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b7d3d000-b7d3f000 r-xs 00000000 08:03 245918     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b7d3f000-b7d43000 r-xs 00000000 08:03 251735     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b7d43000-b7d49000 r-xs 00000000 08:03 245912     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b7d49000-b7d4a000 r-xs 00000000 08:03 245935     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7d4a000-b7d52000 r-xs 00000000 08:03 245941     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b7d52000-b7d54000 r-xs 00000000 08:03 251733     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b7d54000-b7d57000 r-xs 00000000 08:03 245943     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b7d57000-b7d59000 r-xs 00000000 08:03 251731     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b7d59000-b7d5b000 r-xs 00000000 08:03 248096     /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b7d5b000-b7d96000 r-xp 00000000 08:03 820546     /usr/lib/locale/en_NZ.utf8/LC_CTYPE
b7d96000-b7e6d000 r-xp 00000000 08:03 820545     /usr/lib/locale/en_NZ.utf8/LC_COLLATE
b7e6d000-b7e71000 rwxp b7e6d000 00:00 0 
b7e71000-b7f09000 r-xp 00000000 08:03 771556     /usr/lib/libGL.so.1.2
b7f09000-b7f0e000 rwxp 00098000 08:03 771556     /usr/lib/libGL.so.1.2
b7f0e000-b7f13000 rwxp b7f0e000 00:00 0 
b7f15000-b7f16000 r-xp 00000000 08:03 820551     /usr/lib/locale/en_NZ.utf8/LC_NUMERIC
b7f16000-b7f17000 r-xp 00000000 08:03 820554     /usr/lib/locale/en_NZ.utf8/LC_TIME
b7f17000-b7f18000 r-xp 00000000 08:03 820549     /usr/lib/locale/en_NZ.utf8/LC_MONETARY
b7f18000-b7f19000 r-xp 00000000 08:03 835623     /usr/lib/locale/en_NZ.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f19000-b7f1a000 r-xp 00000000 08:03 820552     /usr/lib/locale/en_NZ.utf8/LC_PAPER
b7f1a000-b7f1b000 r-xp 00000000 08:03 820550     /usr/lib/locale/en_NZ.utf8/LC_NAME
b7f1b000-b7f1c000 r-xp 00000000 08:03 820544     /usr/lib/locale/en_NZ.utf8/LC_ADDRESS
b7f1c000-b7f1d000 r-xp 00000000 08:03 820553     /usr/lib/locale/en_NZ.utf8/LC_TELEPHONE
b7f1d000-b7f1e000 r-xp 00000000 08:03 820548     /usr/lib/locale/en_NZ.utf8/LC_MEASUREMENT
b7f1e000-b7f25000 r-xs 00000000 08:03 607043     /usr/lib/gconv/gconv-modules.cache
b7f25000-b7f26000 r-xp 00000000 08:03 820547     /usr/lib/locale/en_NZ.utf8/LC_IDENTIFICATION
b7f26000-b7f28000 rwxp b7f26000 00:00 0 
bf8a9000-bf8be000 rwxp bf8a9000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

My xorg.conf is here:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
	
EndSection

Section "DRI"
	Mode	0666
EndSection








Section "Extensions"
	Option		"Composite"	"0"
EndSection
```

---

### Post by weblordpepe on 2007-07-01
OK nevermind. I just reinstalled the ATI driver from the ati site. Turns out it was the antialiasing settings which gave input lag.

I cant remember what I did to break it initially though.

Anyway - anyone who has installed the ATI driver right from the ATI website (ati-driver-installer-8.38.6-x86.x86_64.run) please let me know if there is a way to uninstall it and return to the normal ATi restricted driver that Ubuntu provides.

---

### Post by newbie2 on 2007-07-03
[http://ubuntuforums.org/showthread.php?t=490937](http://ubuntuforums.org/showthread.php?t=490937)

---

### Post by weblordpepe on 2007-07-03
Cheers, nube.

---

