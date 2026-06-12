---
title: "Targus ACP60 Volari Z7/Z9/Z9s"
date: 2009-06-16
forum: Hardware
---

### Post by Circa Lucid on 2009-06-16
I've got Ubuntu 904 on my Inspiron 6400 running beautifully. Then I've got a Targus ACP60 which works perfectly (to my glee and amazement) except for the video. I'm a newb to desktop linux but I searched and tested alot before posting this. Basically, I'm trying to get a 2 montior setup going.

Using the vesa driver on PCI:13:2:0, my main screen displays 'Sorry, this VBios does only support Z9s' and completely locks my machine up. Using xgiz (2.70.09 that I DLed from XGITech.com and installed after having to tweak the install_ubuntu.sh), I get an error that the driver was compiled for xorg 1.4.0 and not 1.6.0. I've seen alot of documentation to use sisfb but when I do, I get (WW) Warning, couldn't open module sisfb even after removing the entry from blacklist-framebuffer.conf. With sis, I get completely unusable video.

From a Mac forum, I found out that the specific processor in this ACP60 is a Volari Z9 and I found the open_source drivers on XGI's website. So I'm going to look at compiling it myself and I'll post my results. Anyone have a workaround before I go off on the trail of learning how to build kernel modules from source??

(II) LoadModule: "xgiz"
(II) Loading /usr/lib/xorg/modules/drivers//xgiz_drv.so
(II) Module xgiz: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 2.70.9
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(EE) module ABI major version (2) doesn't match the server's version (5)
(II) UnloadModule: "xgiz"
(II) Unloading /usr/lib/xorg/modules/drivers//xgiz_drv.so
(EE) Failed to load module "xgiz" (module requirement mismatch, 0)
(EE) No drivers available.


xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)


lspci -vvvnn
0d:02.0 VGA compatible controller [0300]: XGI Technology Inc. (eXtreme Graphics Innovation) Volari Z7/Z9/Z9s [18ca:0020]
	Subsystem: XGI Technology Inc. (eXtreme Graphics Innovation) Volari Z7/Z9/Z9s [18ca:0020]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	BIST result: 00
	Region 0: Memory at <unassigned> (32-bit, prefetchable)
	Region 1: Memory at efa00000 (32-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at d400 [size=128]
	Expansion ROM at efa60000 [disabled] [size=32K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel modules: sisfb

/etc/X11/xorg.conf
Section "Device"
	Identifier	"Videocard0"
	Driver		"sisfb"
	BusID		"PCI:13:2:0"
	VendorName	"Videocard vendor"
	BoardName	"XGI Volari Z7/Z9/Z9s"
EndSection


(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xeff00000/524288, 0xd0000000/268435456, 0xefec0000/262144, I/O @ 0x0000eff8/8
(--) PCI: (0@13:2:0) XGI Technology Inc. (eXtreme Graphics Innovation) Volari Z7/Z9/Z9s rev 0, Mem @ 0xe0000000/33554432, 0xefbc0000/262144, I/O @ 0x0000dd80/128, BIOS @ 0x????????/32768

---

