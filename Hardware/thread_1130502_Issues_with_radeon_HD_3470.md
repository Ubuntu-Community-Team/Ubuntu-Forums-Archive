---
title: "Issues with radeon HD 3470"
date: 2009-04-19
forum: Hardware
---

### Post by 0xbaadf00d on 2009-04-19
(Hardware specs later, as I dont need immediate help)

Let me preface this post by saying that I realize this a well known bug. 
(for example, launchpad.net Bug #254908 and its duplicates)
The X server does not like the radeon hd 3470. Out of all my ubuntu install disks, one can bring up X with a gui, and I think it would be useful to figure out why.

Basically, my purpose for posting is to find someone more knowledgeable than myself to shed some light in this issue, and perhaps help the people that will inevitably google this problem in the future.

long story short:

I have a radeon hd 3470, and the ubuntu 8.04.1 LTS desktop disk 
(the one with the logo on it, not downloaded) is the only one that will get a gui up and running. (Livecd or full install)

I tried these others from ubuntu.com:
8.04.2 Desktop (x86 and amd64) regular and alternate install disks, 8.10 Desktop x86 and amd64, 9.04 beta x86,  all with the same result.
X wont start and Ive tried EVERY fix I could find on the web without success

Then, the handout cd (8.04.1, actual disk, not downloaded)
works without a hitch. I'll be pleasantly surprised if anyone can suggest an explanation for this behavior. On a side note, the checksum for this disk does not match 8.04.1 from old-releases.ubuntu.com.


Now, for the sake of completeness, hardware specs et al:

Toshiba A355D series:

AMD turion x2
ATI HD 3470
Atheros wireless
4 gigs ram

Xorg.conf and lspci:


xorg.conf:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```



Now my lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Unknown device 9602
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
02:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
08:00.1 System peripheral: JMicron Technologies, Inc. Unknown device 2382
08:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
08:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
08:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
0e:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
```

---

### Post by 0xbaadf00d on 2009-04-19
Also I am posting this from liveCD, if the xorg.conf or lspci change after full install I will repost them.

xorg.conf after enabling fglrx:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by zappa on 2009-05-10
Thanks a lot for your post. 
I did indeed find this page through a search engine, and this helpful for me as I'm in the market for a new laptop. 

As to your problem, it really beats me.

---

