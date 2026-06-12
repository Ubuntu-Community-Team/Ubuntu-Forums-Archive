---
title: "Acer Aspire 1353LC + LG 17&quot; problem"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by nirux on 2006-08-24
Installed Ubuntu on Acer Aspire 1353LC Laptop and everything works fine! max resolution for the laptop is 1024x768, correct.
But I use an external LG 17" LCD (max resolution 1280x1024) but I still get 1024x768 as maximum with Ubuntu.
I use this as main monitor, no dual screen, the laptop is "closed".

In winxp I get 1280x1024 no problem.

Solution on this problem, please? I need my 1280x1024!

---

### Post by olzon on 2006-08-24
I got the same problem...

---

### Post by Maylar on 2006-08-24
First, is the correct driver installed for the vid? It may just have the vesa driver installed. I know I had to set mine manually. As well as configure the display manually. Your best bet is to look in the xorg.conf file and see what driver is being used. It is located @ /etc/X11/xorg.conf If you are using Ubuntu, Kubuntu or Xubuntu would also be helpful, since if you are using Kubuntu, you will not have to edit it by hand. KDE has a nice GUI for changing the file (puts the cards and display in a nice drop down menu). What I ended up doing was booting a LiveCD of Kubuntu and saving the xorg.conf to the HDD. Made it alot easier. I looked your notebook up. Acer is not fourth coming on the graphics card used for that notebook. So, before changing anything. lspci will list all of the hardware on your system. Here is mine, so you have an idea of what your looking for from that command

```
maylar@victimized:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter**

```
After knowing what graphics card that has, we will be able to assist you further. You may want to post your xorg.conf file as well. It will also be helpful

---

### Post by nirux on 2006-08-26
the problem is not solved yet :confused: 

```
emma@nephilim:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host B ridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controlle r (rev 02)
0000:00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Contro ller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChr ome] Integrated Video (rev 01)
```

```
....
Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LG L1715S"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"LG L1715S"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
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
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by entangled on 2006-08-26
Having had this sort of problem in parallels desktop for mac recently my solution might work for you too.

In xorg.conf
in the Screens section
Make sure that each resolution subsection is modified as follows:

after the line listing modes
Modes "1024x768" "800x600" etc
add the line
Virtual   "1280x1024"

or whatever resolution you need.

and then also put that "1280x1024" into the modes line.

It may still not work because the vsync and hsync setting could be too low. I don't know how to calculate it, but try adding about 10% to the upper limit of vsync or hsync separately and restarting X. Eventually it should work.

---

### Post by nirux on 2006-08-26
> **entangled said:**
> Having had this sort of problem in parallels desktop for mac recently my solution might work for you too.

In xorg.conf
in the Screens section
Make sure that each resolution subsection is modified as follows:

after the line listing modes
Modes "1024x768" "800x600" etc
add the line
Virtual   "1280x1024"

or whatever resolution you need.

and then also put that "1280x1024" into the modes line.

It may still not work because the vsync and hsync setting could be too low. I don't know how to calculate it, but try adding about 10% to the upper limit of vsync or hsync separately and restarting X. Eventually it should work.

thanks, tried it, didn't work at all :| 
more help anyone please? I don't want to get back to virus xp...

---

