---
title: "nou sound on new aspire 5530g"
date: 2008-08-17
forum: Hardware
---

### Post by sh1n1 on 2008-08-17
I've got a new acer aspire 5530G laptop and the first thing I did was install ubuntu 8.04 on it.  It is working good except for the fact that I have no sound or audio at all.  The volume control works fine and nothing is muted or anything but I don't have sound. :confused:  I've looke around on the forums here but can't find anything that works, also tried reinstalling ALSA. :(
Here is output from aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 and lspci -v:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, 66MHz, medium devsel, latency 64
	Capabilities: <access denied>

00:01.0 PCI bridge: Acer Incorporated [ALI] Unknown device 9602 (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: afd00000-afefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: afb00000-afbfffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=05, sec-latency=0
	Capabilities: <access denied>

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: f0200000-f02fffff
	Capabilities: <access denied>

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: f0300000-f03fffff
	Capabilities: <access denied>

00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: f0400000-f04fffff
	Capabilities: <access denied>

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 10a8 [size=8]
	I/O ports at 10a0 [size=4]
	I/O ports at 1088 [size=8]
	I/O ports at 1084 [size=4]
	I/O ports at 1090 [size=16]
	Memory at fe9ffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0504000 (32-bit, non-prefetchable) [size=4K]

00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0505000 (32-bit, non-prefetchable) [size=4K]

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f0508000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0506000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f0507000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f0508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=09, subordinate=0b, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
	I/O ports at 9000 [disabled] [size=256]
	Memory at afdf0000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Memory at afe00000 (32-bit, non-prefetchable) [disabled] [size=1M]
	Capabilities: <access denied>

02:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at afbf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at a000 [size=256]
	[virtual] Expansion ROM at afb00000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at afbec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: fast devsel, IRQ 18
	Memory at f0200000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

07:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
	Subsystem: Acer Incorporated [ALI] Unknown device 014b
	Flags: bus master, fast devsel, latency 0, IRQ 506
	Memory at f0300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

---

### Post by markbuntu on 2008-08-17
Type:

aplay -l

in a terminal. Tell us what it says.

---

### Post by sh1n1 on 2008-08-17
If you had read my post carefully you would have noticed that I already posted that info, but here it is again for your benefit:
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And to make absolutely clear I do not have any sound of any kind.  No login, no headphones, no nothing. :(

---

### Post by markbuntu on 2008-08-18
OK. Sorry, I did not see that. But anyway, since you have an ATI HD card, you can go here for a possible solution to your problem:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by sh1n1 on 2008-08-20
I tried all the options for my ATI HD card with ALC883 chipset and none of worked at all.  The only thing that changed was the soundmixer options but still no sound.

---

### Post by dustman on 2008-08-20
this thread helped me get going, maybe you'll find it useful:

[http://ubuntuforums.org/showthread.php?t=624002&page=3](http://ubuntuforums.org/showthread.php?t=624002&page=3)

---

### Post by lo-ma on 2008-10-16
Hi, sh1n1 did you find a solution to your problem?

Because I have the exact same computer with Hardy on it, and the exact same problem...

---

### Post by contadinoste on 2008-12-07
Try install
linux-backports-modules
for your kernels

---

