---
title: "Setting Up A Second Monitor"
date: 2010-10-02
forum: Hardware
---

### Post by Thommy.Morgan on 2010-10-02
I have an acer laptop running on Ubuntu and I have a monitor attached to it. Ubuntu recognizes the monitor, but it does not split the desktop between the two monitors, nor even display anything on that second monitor. I have tried using Xinerama but when I get to the step of configuring the xorg.conf file and rebooting, Ubuntu does not want to cooperate :(

Here is what my xorg.conf looks like:

```


Section "Screen"
	Identifier	"Configured Screen Device"
	Device		"Configured Video Device"
	Monitor		"Main Monitor"
	SubSection "Display"
		Virtual	2390 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Screen		0
	Option 		"DDCMode" "True"
	Option 		"MonitorLayout" "primary monitor,secondary monitor"
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"ATI Technologies, Inc Manhattan [Mobility Radeon HD 5000 Series]"
	Monitor        "Second Monitor"
	DefaultDepth    24
	SubSection "Display"
		Depth        1
		Modes        "1024x768"
	EndSubSection
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc Manhattan [Mobility Radeon HD 5000 Series]"
	Driver		"ati"
	BusID		"PCI:01:00.0"
	Screen		1
	Option 		"DDCMode" "True"
	Option 		"MonitorLayout" "primary monitor,secondary monitor"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0		"Configured Screen Device"
	Screen 1		"Second Screen" RightOf "Configured Screen Device"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"stylus" "SendCoreEvents"
	InputDevice	"cursor" "SendCoreEvents"
	InputDevice	"eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option 		"Xinerama" "true"
EndSection


```

And when I put this command into the Temrinal I get:

```


thommy@TheSavagewood:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
03:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

Can someone help me out? Or suggest a better alternative? I feel like I am so close to getting it to work, but I am just missing something. Thanks in advance for any help or advice!

~Thommy

---

