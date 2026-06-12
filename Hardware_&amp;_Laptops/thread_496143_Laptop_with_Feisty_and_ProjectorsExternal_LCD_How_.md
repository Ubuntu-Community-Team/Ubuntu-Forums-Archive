---
title: "Laptop with Feisty and Projectors/External LCD: How to set up xorg.conf?"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by effenberg0x0 on 2007-07-08
Hi everyone, after 11 years of windows, I have finally made the change to Linux through Ubuntu this year, and I am using it to work on my Laptop for the last 6 months with no real problems until this week. I guess I was so used to hot-plugging a projector to this same Laptop when I was a windows user, that I didn't even stop to think  about Ubuntu and Linux compatibility issues. Well, it was an imposrtant meeting at a client and yes, it did not work.

Back home, after playing a fool, I connected a Samsung SyncMaster 740N (17'' LCD) to the VGA port of my Laptop for the first time ever, I was really expecting it to work immediately, however life ain't that easy. Resolution looks ugly, most of the screen is lost ("out of the monitor area"), letters are crispy, almost unreadable.

Ok, so I read everything I could find on the net for the last day and tried a number of solutions. I don't want nothing complicated. All I want is for Ubuntu to reproduce the exact same image I am seeing in the Laptop screen in the VGA port, so that any LCD or projector I plug there will addapt itself in terms of frequencies, etc.

Here's how my xorg.conf looks like right now (only the relevant parts of it):

 Section "Device"
	Identifier	"Via"
#	Driver		"fbdev"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	VideoRam	65536
        Option          "MonitorLayout" "LCD,LCD+LFP"
	Option          "Clone" "true"
	Option		"DevicePresence" "true"
#	Option 		"FixedPipe" "A" 
#	Option         "UseEdidFreqs" "false"
EndSection

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Internal"
	Device		"Via"
	Monitor		"Laptop Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"External"
	Device		"Via"
	Monitor		"External Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Internal"
	Screen 1	"External"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Any ideas what I am doing wrong here? Help would be very appreciated, I gotta be at a client again on tuesday, it would kill me to have to get XP back to my life...

Thanks!
Effenberg

---

### Post by effenberg0x0 on 2007-07-10
As a differente approach, has anyone succeeded on using the LAPTOP port for presentations (projector) on any machine based on any VIA video chipset? 

I have tried all possible xorg configurations: the resolution, refresh rate and etc on the VGA port seem to not respect the settings at xorg.conf, ever, no matter what you do.

I have tried VIA driver, UniChrome and Openchrome with the same results. 

Thanks,
Effenberg

---

### Post by effenberg0x0 on 2007-07-13
I still can't find a solution, so I am posting some additional information about my hardware, in hopes others with a similar problem will get to this thread while searching for the same answers...

In Brazil, this Laptop is a ITAUTEC W7630 ([http://www.itautec.com.br/iPortal/pt-BR/81d09001-dfc3-44de-a566-14c79ad432f9.htm](http://www.itautec.com.br/iPortal/pt-BR/81d09001-dfc3-44de-a566-14c79ad432f9.htm))
Out of Brazil, this Laptop is sold under many brands, but essentially it is a FIC ([http://www.fic.com.tw/product/notebooks.htm](http://www.fic.com.tw/product/notebooks.htm)).

I have managed to make everything work, except the external LCD, LFP, DFP, CRT, etc. My problem is: I can get image on the connected display, but resolution is weird as ell as refresh rate. Messing around in xorg.conf seems to solve the problem for all LapTop hardware, except this one. It simply makes no difference at all to play with xorg.conf settings, which makes me wonder if VIA VGA drivers for Linux  (VIA, OpenChrome, UniChrome) can actually handle an external display. 

This is the output of lspci:
```

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```

Any help would be deeply appreciated.

Regards,
Effenberg

---

### Post by pytheas22 on 2007-10-09
I don't know if you ever solved this problem, but I just wanted to suggest that maybe there's an internal switch in your laptop that you have to press to enable the video-out on the VGA port.  On my Dell Inspiron 1150, there's a function key that says "CRT/LCD," and pressing it when an external monitor is connected will make it clone to the monitor.  Otherwise the monitor won't be detected, even if xorg.conf says to force it.

On the other hand, this worked for me out of the box with Ubuntu 7.04; I didn't have to do any editing of xorg.conf, it just works.  If I wanted to get Xinerema set up I'd probably have to edit some stuff, but I don't care aboutc that.  I also have Intel video, which tends to work well since Intel releases open-source drivers, though; I don't know if VIA has good open-source support or not.

---

