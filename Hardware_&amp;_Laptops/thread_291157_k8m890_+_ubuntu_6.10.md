---
title: "k8m890 + ubuntu 6.10"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by kapa on 2006-11-02
hello, I have a K8M890 based motherboard. Currently running Ubuntu 6.10 with package xserver-xorg-video-unichrome ([http://packages.ubuntu.com/edgy/x11/xserver-xorg-video-unichrome]("http://packages.ubuntu.com/edgy/x11/xserver-xorg-video-unichrome")).
I have never been able to get the unichrome driver in Xorg to load ](*,)

$ cat /var/log/Xorg.0.log.old | grep unichrome
(II) LoadModule: "unichrome"
(II) Loading /usr/lib/xorg/modules/drivers/unichrome_drv.so
(EE) LoadModule: Module unichrome does not have a unichromeModuleData data object.
(II) UnloadModule: "unichrome"
(II) Unloading /usr/lib/xorg/modules/drivers/unichrome_drv.so
(EE) Failed to load module "unichrome" (invalid module, 0)

someone can help me? tnk, kapa :cry:

---

### Post by CosminGC on 2006-11-05
I have the same problem ...

---

### Post by JanusDC on 2006-11-11
Me too, but with the K8M800

---

### Post by persicsb on 2006-11-11
> **kapa said:**
> hello, I have a K8M890 based motherboard. Currently running Ubuntu 6.10 with package xserver-xorg-video-unichrome ([http://packages.ubuntu.com/edgy/x11/xserver-xorg-video-unichrome]("http://packages.ubuntu.com/edgy/x11/xserver-xorg-video-unichrome")).
I have never been able to get the unichrome driver in Xorg to load ](*,)

$ cat /var/log/Xorg.0.log.old | grep unichrome
(II) LoadModule: "unichrome"
(II) Loading /usr/lib/xorg/modules/drivers/unichrome_drv.so
(EE) LoadModule: Module unichrome does not have a unichromeModuleData data object.
(II) UnloadModule: "unichrome"
(II) Unloading /usr/lib/xorg/modules/drivers/unichrome_drv.so
(EE) Failed to load module "unichrome" (invalid module, 0)

someone can help me? tnk, kapa :cry:

I have managed to resolve the problem.
Jump the next section, if you only need the solution.
Read the next section, to see why the problem occurs.

Why the problem occurs? Let's see in general!
Assume, that the xorg.conf file states, that the driver name XYZ.
Then, Xorg searches for the file XYZ_drv.so in the /usr/lib/xorg/modules/driver/ directory.
If it can't find it, generates an error, that the module can not be found.
If Xorg finds the module, it starts to load it. Xorg searches for a structure called XYZModuleData.

In this case, the module was renamed from via to unichrome, so the xserver-xorg-video-unichrome package does not conflict with the xserver-xorg-video-via package. Really, it is not the case: in fact, it conflicts, because the binary unichrome.sf.net driver contains a viaModuleData section.
So the filename MUST be via_drv.so for the unichrome.sf.net driver too. It won't work, if we just rename the driver. Xorg will find it, but it could not load it. So both the Xog driver and the unichrome.sf.net driver has the same name. 

Question:How can we make a difference on these drivers?
Answer: There is no way. 
The solution: 
1.Remove the xserver-xorg-video-via package. It conflicts with the unichrome.sf.net driver. The packages does not conflict, since they have separate filenames. The internals of the driver do conflict!
2.Install the xserver-xorg-video-unichrome driver.
3. Remove the file /usr/lib/xorg/modules/drivers/unichrome_drv.so to via_drv.so (that's why the two driver conflits, they MUST have the same name)
4. Edit the /etc/X11/xorg.conf driver, you MUST use "via" instead of "unichrome" in the Driver option.
5. Restart GDM.
 
It works for me, and gives better performance, than the Xorg via driver. But you cannot use Beryl, Compiz, etc with this driver: there is no hardware support :(

---

### Post by JanusDC on 2006-11-11
Thank you very much!!! It's works for me!

---

### Post by persicsb on 2006-11-12
> **JanusDC said:**
> Thank you very much!!! It's works for me!

Hm, I'm sorry. Really it does not work for me, since my chipset is not supported.
Interesting, that after the logout, Xorg loaded the driver from cache. After reboot, it does not worked. Never mind, it should work for the supported chipsets.

I will give a bugreport, or request, that the xserver-xorg-video-via and the xserver-xorg-video-unichrome packages should be marked as conflicting each other, so you can use the same filenames. Do you agree?
With it, Feisty Fawn would not have such problems.

---

### Post by JanusDC on 2006-11-12
> **persicsb said:**
> I will give a bugreport, or request, that the xserver-xorg-video-via and the xserver-xorg-video-unichrome packages should be marked as conflicting each other, so you can use the same filenames. Do you agree?
There is an open bug report about this issue: [68901](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-unichrome/+bug/68901), maybe you can confirm the bug too.

---

### Post by rsdavis9 on 2006-11-17
I have the following hardware:
via k8m890ce
averatec av4145-eh1
lshw reports:
product: 2200 Series
vendor: Averatec

Software:
ubuntu edgy 6.10
xorg 7.1.1
vesa 1.2.0

What I have already done:
1. I have been to openchrome.org and compiled and installed the branch vt3336_branch.
The driver comes up and is reasonably fast but it leaves missdraws all over the screen. (call them birdies?)
2. I have been to viaarena and thats where I found I had "via chrome 9 igp" by looking up the devid of 3230.
3. I downloaded the driver from via and got a makefile from a viaarena list but am having troubles with the compile. make fails with:
make: *** [via_driver.o] Error 1.
I am working on it.
4. With ubuntu 6.06 dapper and xorg 7.0.0 vesa 1.0.1 it was reasonably fast.
5. WIth knoppix 5.01 it was even faster. Same xorg and vesa
6. with the current edgy it is abysmally slow on scrolls and window drags. It probably takes 1/2 second per scroll line.
7. I added
Option "AIGLX" "off"
and
Option "Composite" "Disable"
to xorg.conf. No affect.
8. I dont want to go back to dapper because the new kernel(2.6.17) fixed a lockup(slow down) with the thermal module.

Questions:
1. I appear to be stuck with the vesa driver for now. How do I get it to perform as fast as dapper?
2. If I recompile xserver-xorg can I speed up the vesa driver by leaving things out?
3. Is there any other places other then what I have listed where I could find a working via driver? Or is there some simple way to fix the openchrome. I will probably cross post this to the xorg list.

---------------
bob@bobt64:~$ sudo lspci -vv -s 1:0
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 01) (prog-if 00 [VGA])
Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device a002
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- SERR-
Latency: 64 (500ns min)
Interrupt: pin A routed to IRQ 11
Region 0: Memory at a0000000 (32-bit, prefetchable) [size=256M]
Region 1: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
Expansion ROM at fe3f0000 [disabled] [size=64K]
Capabilities: [60] Power Management version 2
Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [70] AGP version 3.0
Status: RQ=256 Iso- ArqSz=0 Cal=7 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP- GART64- 64bit- FW- Rate=


---------------
Xorg.0.log

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux bobt64 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 07 July 2006
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 14 00:25:36 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "Generic Monitor"
(**) | |-->Device "via s3 deltachrome igp"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Touchpad"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
/usr/share/fonts/X11/misc/,
/usr/share/fonts/X11/TTF/,
/usr/share/fonts/X11/OTF,
/usr/share/fonts/X11/Type1/,
/usr/share/fonts/X11/CID/,
/usr/share/fonts/X11/100dpi/,
/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "off"
(**) Extension "Composite" is disabled
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0336 card 1106,0336 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1336 card 1106,1336 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2336 card 1106,2336 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3336 card 1106,3336 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4336 card 1106,4336 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:5: chip 1106,5336 card 1106,5336 rev 00 class 08,00,20 hdr 80
(II) PCI: 00:00:7: chip 1106,7336 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1106,a238 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 1106,c238 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0a:0: chip 1217,00f7 card 14ff,a002 rev 02 class 0c,00,10 hdr 80
(II) PCI: 00:0a:2: chip 1217,7120 card 14ff,a002 rev 01 class 08,05,00 hdr 00
(II) PCI: 00:0a:3: chip 1217,7130 card 14ff,a002 rev 01 class 01,80,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3349 card 1106,3349 rev 00 class 01,01,8f hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 14ff,a002 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 90 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 90 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 90 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1106,3038 rev 90 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 14ff,a002 rev 90 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3287 card 14ff,a002 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 14ff,a002 rev 70 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 14ff,a002 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:11:7: chip 1106,287e card 1106,287e rev 00 class 06,00,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 14ff,a002 rev 7c class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1106,287b card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1106,3230 card 14ff,a002 rev 01 class 03,00,00 hdr 00
(II) PCI: 05:00:0: chip 1106,287c card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 05:00:1: chip 1106,287d card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
[0] -1 0 0x00000000 - 0x0000ffff (0x10000) IX
(II) Bus 0 non-prefetchable memory range:
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX
(II) Bus 0 prefetchable memory range:
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
[0] -1 0 0xfb000000 - 0xfe3fffff (0x3400000) MX
(II) Bus 1 prefetchable memory range:
[0] -1 0 0xa0000000 - 0xafffffff (0x10000000) MX
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:19:0), (0,5,7), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 5 I/O range:
[0] -1 0 0x0000e000 - 0x0000efff (0x1000) IX
(II) Bus 5 non-prefetchable memory range:
[0] -1 0 0xfea00000 - 0xfebfffff (0x200000) MX
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (5:0:0), (5,6,6), BCTRL: 0x0003 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (5:0:1), (5,7,7), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 7 I/O range:
[0] -1 0 0x0000e000 - 0x0000efff (0x1000) IX
(II) Bus 7 non-prefetchable memory range:
[0] -1 0 0xfea00000 - 0xfebfffff (0x200000) MX
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3230) rev 1, Mem @ 0xa0000000/28, 0xfb000000/24, BIOS @ 0xfe3f0000/16
(II) Addressable bus resource ranges are
[0] -1 0 0x00000000 - 0xffffffff (0x0) MX
[1] -1 0 0x00000000 - 0x0000ffff (0x10000) IX
(II) OS-reported resource ranges:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MXE(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX
[5] -1 0 0x00000000 - 0x000000ff (0x100) IX
(II) Active PCI resource ranges:
[0] -1 0 0xfaffc800 - 0xfaffc8ff (0x100) MX
[1] -1 0 0xfaffcc00 - 0xfaffccff (0x100) MX
[2] -1 0 0xfaffe000 - 0xfaffe3ff (0x400) MX
[3] -1 0 0xfaffd000 - 0xfaffdfff (0x1000) MX
[4] -1 0 0xfaffe400 - 0xfaffe4ff (0x100) MX
[5] -1 0 0xfaffe800 - 0xfaffefff (0x800) MX
[6] -1 0 0x40000000 - 0x40000fff (0x1000) MX
[7] -1 0 0xfe3f0000 - 0xfe3fffff (0x10000) MX(B)
[8] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX(B)
[9] -1 0 0xa0000000 - 0xafffffff (0x10000000) MX(B)
[10] -1 0 0x0000a000 - 0x0000a0ff (0x100) IX
[11] -1 0 0x0000a400 - 0x0000a4ff (0x100) IX
[12] -1 0 0x0000a800 - 0x0000a8ff (0x100) IX
[13] -1 0 0x0000b000 - 0x0000b01f (0x20) IX
[14] -1 0 0x0000b400 - 0x0000b41f (0x20) IX
[15] -1 0 0x0000b800 - 0x0000b81f (0x20) IX
[16] -1 0 0x0000c000 - 0x0000c01f (0x20) IX
[17] -1 0 0x0000fc00 - 0x0000fc0f (0x10) IX
[18] -1 0 0x0000c400 - 0x0000c40f (0x10) IX
[19] -1 0 0x0000c800 - 0x0000c803 (0x4) IX
[20] -1 0 0x0000d000 - 0x0000d007 (0x8) IX
[21] -1 0 0x0000d400 - 0x0000d403 (0x4) IX
[22] -1 0 0x0000d800 - 0x0000d807 (0x8) IX
(II) Active PCI resource ranges after removing overlaps:
[0] -1 0 0xfaffc800 - 0xfaffc8ff (0x100) MX
[1] -1 0 0xfaffcc00 - 0xfaffccff (0x100) MX
[2] -1 0 0xfaffe000 - 0xfaffe3ff (0x400) MX
[3] -1 0 0xfaffd000 - 0xfaffdfff (0x1000) MX
[4] -1 0 0xfaffe400 - 0xfaffe4ff (0x100) MX
[5] -1 0 0xfaffe800 - 0xfaffefff (0x800) MX
[6] -1 0 0x40000000 - 0x40000fff (0x1000) MX
[7] -1 0 0xfe3f0000 - 0xfe3fffff (0x10000) MX(B)
[8] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX(B)
[9] -1 0 0xa0000000 - 0xafffffff (0x10000000) MX(B)
[10] -1 0 0x0000a000 - 0x0000a0ff (0x100) IX
[11] -1 0 0x0000a400 - 0x0000a4ff (0x100) IX
[12] -1 0 0x0000a800 - 0x0000a8ff (0x100) IX
[13] -1 0 0x0000b000 - 0x0000b01f (0x20) IX
[14] -1 0 0x0000b400 - 0x0000b41f (0x20) IX
[15] -1 0 0x0000b800 - 0x0000b81f (0x20) IX
[16] -1 0 0x0000c000 - 0x0000c01f (0x20) IX
[17] -1 0 0x0000fc00 - 0x0000fc0f (0x10) IX
[18] -1 0 0x0000c400 - 0x0000c40f (0x10) IX
[19] -1 0 0x0000c800 - 0x0000c803 (0x4) IX
[20] -1 0 0x0000d000 - 0x0000d007 (0x8) IX
[21] -1 0 0x0000d400 - 0x0000d403 (0x4) IX
[22] -1 0 0x0000d800 - 0x0000d807 (0x8) IX
(II) OS-reported resource ranges after removing overlaps with PCI:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MXE(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX
[5] -1 0 0x00000000 - 0x000000ff (0x100) IX
(II) All system resource ranges:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MXE(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX
[4] -1 0 0xfaffc800 - 0xfaffc8ff (0x100) MX
[5] -1 0 0xfaffcc00 - 0xfaffccff (0x100) MX
[6] -1 0 0xfaffe000 - 0xfaffe3ff (0x400) MX
[7] -1 0 0xfaffd000 - 0xfaffdfff (0x1000) MX
[8] -1 0 0xfaffe400 - 0xfaffe4ff (0x100) MX
[9] -1 0 0xfaffe800 - 0xfaffefff (0x800) MX
[10] -1 0 0x40000000 - 0x40000fff (0x1000) MX
[11] -1 0 0xfe3f0000 - 0xfe3fffff (0x10000) MX(B)
[12] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX(B)
[13] -1 0 0xa0000000 - 0xafffffff (0x10000000) MX(B)
[14] -1 0 0x0000ffff - 0x0000ffff (0x1) IX
[15] -1 0 0x00000000 - 0x000000ff (0x100) IX
[16] -1 0 0x0000a000 - 0x0000a0ff (0x100) IX
[17] -1 0 0x0000a400 - 0x0000a4ff (0x100) IX
[18] -1 0 0x0000a800 - 0x0000a8ff (0x100) IX
[19] -1 0 0x0000b000 - 0x0000b01f (0x20) IX
[20] -1 0 0x0000b400 - 0x0000b41f (0x20) IX
[21] -1 0 0x0000b800 - 0x0000b81f (0x20) IX
[22] -1 0 0x0000c000 - 0x0000c01f (0x20) IX
[23] -1 0 0x0000fc00 - 0x0000fc0f (0x10) IX
[24] -1 0 0x0000c400 - 0x0000c40f (0x10) IX
[25] -1 0 0x0000c800 - 0x0000c803 (0x4) IX
[26] -1 0 0x0000d000 - 0x0000d007 (0x8) IX
[27] -1 0 0x0000d400 - 0x0000d403 (0x4) IX
[28] -1 0 0x0000d800 - 0x0000d807 (0x8) IX
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.2.0
ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
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
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.0.0
ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.0.0
ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.0.2
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.1.0
ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
compiled for 4.2.0, module version = 1.0.0
Module class: XFree86 XInput Driver
ABI class: XFree86 XInput driver, version 0.3
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
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
(II) LoadModule: "synaptics"
(II) Reloading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
compiled for 4.3.99.902, module version = 1.0.0
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MXE(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX
[4] -1 0 0xfaffc800 - 0xfaffc8ff (0x100) MX
[5] -1 0 0xfaffcc00 - 0xfaffccff (0x100) MX
[6] -1 0 0xfaffe000 - 0xfaffe3ff (0x400) MX
[7] -1 0 0xfaffd000 - 0xfaffdfff (0x1000) MX
[8] -1 0 0xfaffe400 - 0xfaffe4ff (0x100) MX
[9] -1 0 0xfaffe800 - 0xfaffefff (0x800) MX
[10] -1 0 0x40000000 - 0x40000fff (0x1000) MX
[11] -1 0 0xfe3f0000 - 0xfe3fffff (0x10000) MX(B)
[12] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX(B)
[13] -1 0 0xa0000000 - 0xafffffff (0x10000000) MX(B)
[14] -1 0 0x0000ffff - 0x0000ffff (0x1) IX
[15] -1 0 0x00000000 - 0x000000ff (0x100) IX
[16] -1 0 0x0000a000 - 0x0000a0ff (0x100) IX
[17] -1 0 0x0000a400 - 0x0000a4ff (0x100) IX
[18] -1 0 0x0000a800 - 0x0000a8ff (0x100) IX
[19] -1 0 0x0000b000 - 0x0000b01f (0x20) IX
[20] -1 0 0x0000b400 - 0x0000b41f (0x20) IX
[21] -1 0 0x0000b800 - 0x0000b81f (0x20) IX
[22] -1 0 0x0000c000 - 0x0000c01f (0x20) IX
[23] -1 0 0x0000fc00 - 0x0000fc0f (0x10) IX
[24] -1 0 0x0000c400 - 0x0000c40f (0x10) IX
[25] -1 0 0x0000c800 - 0x0000c803 (0x4) IX
[26] -1 0 0x0000d000 - 0x0000d007 (0x8) IX
[27] -1 0 0x0000d400 - 0x0000d403 (0x4) IX
[28] -1 0 0x0000d800 - 0x0000d807 (0x8) IX
(II) resource ranges after probing:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MXE(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX
[4] -1 0 0xfaffc800 - 0xfaffc8ff (0x100) MX
[5] -1 0 0xfaffcc00 - 0xfaffccff (0x100) MX
[6] -1 0 0xfaffe000 - 0xfaffe3ff (0x400) MX
[7] -1 0 0xfaffd000 - 0xfaffdfff (0x1000) MX
[8] -1 0 0xfaffe400 - 0xfaffe4ff (0x100) MX
[9] -1 0 0xfaffe800 - 0xfaffefff (0x800) MX
[10] -1 0 0x40000000 - 0x40000fff (0x1000) MX
[11] -1 0 0xfe3f0000 - 0xfe3fffff (0x10000) MX(B)
[12] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX(B)
[13] -1 0 0xa0000000 - 0xafffffff (0x10000000) MX(B)
[14] 0 0 0x000a0000 - 0x000affff (0x10000) MS
[15] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS
[16] 0 0 0x000b8000 - 0x000bffff (0x8000) MS
[17] -1 0 0x0000ffff - 0x0000ffff (0x1) IX
[18] -1 0 0x00000000 - 0x000000ff (0x100) IX
[19] -1 0 0x0000a000 - 0x0000a0ff (0x100) IX
[20] -1 0 0x0000a400 - 0x0000a4ff (0x100) IX
[21] -1 0 0x0000a800 - 0x0000a8ff (0x100) IX
[22] -1 0 0x0000b000 - 0x0000b01f (0x20) IX
[23] -1 0 0x0000b400 - 0x0000b41f (0x20) IX
[24] -1 0 0x0000b800 - 0x0000b81f (0x20) IX
[25] -1 0 0x0000c000 - 0x0000c01f (0x20) IX
[26] -1 0 0x0000fc00 - 0x0000fc0f (0x10) IX
[27] -1 0 0x0000c400 - 0x0000c40f (0x10) IX
[28] -1 0 0x0000c800 - 0x0000c803 (0x4) IX
[29] -1 0 0x0000d000 - 0x0000d007 (0x8) IX
[30] -1 0 0x0000d400 - 0x0000d403 (0x4) IX
[31] -1 0 0x0000d800 - 0x0000d807 (0x8) IX
[32] 0 0 0x000003b0 - 0x000003bb (0xc) IS
[33] 0 0 0x000003c0 - 0x000003df (0x20) IS
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: VIA K8N890CE

(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor:
(II) VESA(0): VESA VBE OEM Product:
(II) VESA(0): VESA VBE OEM Product Rev:
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
.............. lines deleted
Mode: 1b6 (1280x800)
ModeAttributes: 0x9f
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0xa000
WinFuncPtr: 0xc0008a9e
BytesPerScanline: 1280
XResolution: 1280
YResolution: 800
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 8
NumberOfBanks: 1
MemoryModel: 4
BankSize: 0
NumberOfImages: 63
RedMaskSize: 0
RedFieldPosition: 0
GreenMaskSize: 0
GreenFieldPosition: 0
BlueMaskSize: 0
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 2
PhysBasePtr: 0xa0000000
LinBytesPerScanLine: 1280
BnkNumberOfImagePages: 63
LinNumberOfImagePages: 63
LinRedMaskSize: 0
LinRedFieldPosition: 0
LinGreenMaskSize: 0
LinGreenFieldPosition: 0
LinBlueMaskSize: 0
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
Mode: 1b7 (1280x800)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0xa000
WinFuncPtr: 0xc0008a9e
BytesPerScanline: 2560
XResolution: 1280
YResolution: 800
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 16
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 31
RedMaskSize: 5
RedFieldPosition: 11
GreenMaskSize: 6
GreenFieldPosition: 5
BlueMaskSize: 5
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 2
PhysBasePtr: 0xa0000000
LinBytesPerScanLine: 2560
BnkNumberOfImagePages: 31
LinNumberOfImagePages: 31
LinRedMaskSize: 5
LinRedFieldPosition: 11
LinGreenMaskSize: 6
LinGreenFieldPosition: 5
LinBlueMaskSize: 5
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
*Mode: 1b8 (1280x800)
ModeAttributes: 0x9b
WinAAttributes: 0x7
WinBAttributes: 0x0
WinGranularity: 64
WinSize: 64
WinASegment: 0xa000
WinBSegment: 0xa000
WinFuncPtr: 0xc0008a9e
BytesPerScanline: 5120
XResolution: 1280
YResolution: 800
XCharSize: 8
YCharSize: 16
NumberOfPlanes: 1
BitsPerPixel: 32
NumberOfBanks: 1
MemoryModel: 6
BankSize: 0
NumberOfImages: 15
RedMaskSize: 8
RedFieldPosition: 16
GreenMaskSize: 8
GreenFieldPosition: 8
BlueMaskSize: 8
BlueFieldPosition: 0
RsvdMaskSize: 0
RsvdFieldPosition: 0
DirectColorModeInfo: 2
PhysBasePtr: 0xa0000000
LinBytesPerScanLine: 5120
BnkNumberOfImagePages: 15
LinNumberOfImagePages: 15
LinRedMaskSize: 8
LinRedFieldPosition: 16
LinGreenMaskSize: 8
LinGreenFieldPosition: 8
LinBlueMaskSize: 8
LinBlueFieldPosition: 0
LinRsvdMaskSize: 0
LinRsvdFieldPosition: 0
MaxPixelClock: 0
.............. lines deleted

(II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
(II) VESA(0): Generic Monitor: Using hsync range of 28.00-51.00 kHz
(II) VESA(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(--) VESA(0): Virtual size is 1280x800 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x800"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Built-in mode "1280x768"
(++) VESA(0): DPI set to (100, 100)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x800" (1b8)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x768" (17b)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.1.0
ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC? No, I don't.
(II) resource ranges after preInit:
[0] -1 0 0x00100000 - 0x3fffffff (0x3ff00000) MXE(B)
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX
[4] -1 0 0xfaffc800 - 0xfaffc8ff (0x100) MX
[5] -1 0 0xfaffcc00 - 0xfaffccff (0x100) MX
[6] -1 0 0xfaffe000 - 0xfaffe3ff (0x400) MX
[7] -1 0 0xfaffd000 - 0xfaffdfff (0x1000) MX
[8] -1 0 0xfaffe400 - 0xfaffe4ff (0x100) MX
[9] -1 0 0xfaffe800 - 0xfaffefff (0x800) MX
[10] -1 0 0x40000000 - 0x40000fff (0x1000) MX
[11] -1 0 0xfe3f0000 - 0xfe3fffff (0x10000) MX(B)
[12] -1 0 0xfb000000 - 0xfbffffff (0x1000000) MX(B)
[13] -1 0 0xa0000000 - 0xafffffff (0x10000000) MX(B)
[14] 0 0 0x000a0000 - 0x000affff (0x10000) MS
[15] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS
[16] 0 0 0x000b8000 - 0x000bffff (0x8000) MS
[17] -1 0 0x0000ffff - 0x0000ffff (0x1) IX
[18] -1 0 0x00000000 - 0x000000ff (0x100) IX
[19] -1 0 0x0000a000 - 0x0000a0ff (0x100) IX
[20] -1 0 0x0000a400 - 0x0000a4ff (0x100) IX
[21] -1 0 0x0000a800 - 0x0000a8ff (0x100) IX
[22] -1 0 0x0000b000 - 0x0000b01f (0x20) IX
[23] -1 0 0x0000b400 - 0x0000b41f (0x20) IX
[24] -1 0 0x0000b800 - 0x0000b81f (0x20) IX
[25] -1 0 0x0000c000 - 0x0000c01f (0x20) IX
[26] -1 0 0x0000fc00 - 0x0000fc0f (0x10) IX
[27] -1 0 0x0000c400 - 0x0000c40f (0x10) IX
[28] -1 0 0x0000c800 - 0x0000c803 (0x4) IX
[29] -1 0 0x0000d000 - 0x0000d007 (0x8) IX
[30] -1 0 0x0000d400 - 0x0000d403 (0x4) IX
[31] -1 0 0x0000d800 - 0x0000d807 (0x8) IX
[32] 0 0 0x000003b0 - 0x000003bb (0xc) IS
[33] 0 0 0x000003c0 - 0x000003df (0x20) IS
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: VIA K8N890CE

(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor:
(II) VESA(0): VESA VBE OEM Product:
(II) VESA(0): VESA VBE OEM Product Rev:
(==) VESA(0): Write-combining range (0xa0000000,0x4000000)
(II) VESA(0): virtual address = 0xb3b4c000,
physical address = 0xa0000000, size = 67108864
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 1.0.0
ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "LeftEdge" "1700"
(**) Option "RightEdge" "5300"
(**) Option "TopEdge" "1700"
(**) Option "BottomEdge" "4200"
(**) Option "FingerLow" "25"
(**) Option "FingerHigh" "30"
(**) Option "MaxTapTime" "180"
(**) Option "MaxTapMove" "220"
(**) Option "VertScrollDelta" "100"
(--) Touchpad touchpad found
(**) Option "AlwaysCore"
(**) Touchpad: always reports core events
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
xkb_keycodes { include "xfree86+aliases(qwerty)" };
xkb_types { include "complete" };
xkb_compatibility { include "complete" };
xkb_symbols { include "pc(pc104)+us" };
xkb_geometry { include "pc(pc104)" };
Synaptics DeviceInit called
SynapticsCtrl called.
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Touchpad touchpad found
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
ProcXCloseDevice to close or not ?
SetGrabKeysState - disabled
SetGrabKeysState - enabled

---

### Post by rudykovanda on 2006-12-05
I have MB Asus K8V-VM witch K8M890CE (3230) graphics and in Kubuntu 6.10 I have this same problems, in "vesa" is very slow. I use Google :) and read this :

[http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/#more-188](http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/#more-188)

and make:


sudo apt-get remove xserver-xorg-video-via xserver-xorg-video-unichrome

sudo apt-get install build-essential libxinerama-dev x11proto-xinerama-dev libxvmc-dev sysutils tofrodos

sudo apt-get build-dep xserver-xorg-video-via

sudo apt-get build-dep xorg


(if question about install/remove say Y)

dovnload souce from 

[http://www.viaarena.com/Driver/CN_CX700-CN800XORG40071-kernel-src_20061107.tgz](http://www.viaarena.com/Driver/CN_CX700-CN800XORG40071-kernel-src_20061107.tgz)


and as root (or sudo)

# tar zxvf CN_CX700-CN800XORG40071-kernel-src_[fecha].tgz

# cd CN_CX700-CN800XORG40071-kernel-src_[fecha]/src

# ./makedriver

type your release and select procesor architecture


its make DIR CN_CX700-CN800XORG400xxx (xxx - release)


# ldconfig

# ./vinstall_2D

- this install via_drv.so and modify xorg.conf

and startx - in x86 via driver loaded, screen is very faster that "vesa", but screen is very unstable, has bug, broken pixels etc...

in 64bit driver not load, I not remember error, I test x86.... 

Any idea ?

---

### Post by caligula- on 2006-12-12
>...
>- this install via_drv.so and modify xorg.conf
>
>and startx - in x86 via driver loaded, screen is very faster that "vesa", >but screen is very unstable, has bug, broken pixels etc...
>
>in 64bit driver not load, I not remember error, I test x86....
>
>Any idea ?

same problem here.
i also followed the given steps and got the same result.
Any new ideas in the meantime?

caligula-

---

### Post by eeried on 2007-01-22
Have you tried OpenChrome (see Ubuntu doc)

Have you got the same problem with ubuntu Dapper?

I was thinking of buying this mothercard but I'm reconsidering...

---

### Post by CosminGC on 2007-01-22
I allready have windows on that pc. too bad.

---

### Post by turbocharger on 2008-01-14
Hi guys, there's a driver that enables 3D hardware acceleration, but it's originally for Debian.
But, as Ubuntu is a Debian-based OS, it could work :


Link : [http://www.viaarena.com/default.aspx?PageID=420&OSID=43&CatID=3190&SubCatID=164](http://www.viaarena.com/default.aspx?PageID=420&OSID=43&CatID=3190&SubCatID=164)

Maybe it's necessary to adapt it for Ubuntu.

---

