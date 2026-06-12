---
title: "Display distortions"
date: 2012-12-12
forum: Hardware
---

### Post by sdarnok on 2012-12-12
I'm having a problem with screen distorting after a bit of use.  This involves pretty much all aspects, from unity toolbar, alt-tab application switcher, to the applications themselves.  For applications, I can change visual state and that seems to fix the problem, but for all others - reboot is the only option.

I'm running Ubuntu 12.10 on Acer1810tz laptop.  I'm attaching a screen shot of the alt-tab application switcher.


[ATTACH]228592[/ATTACH]


And here's some info that you might find useful (please ask for more):
k@a:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:029b]
	Kernel driver in use: atl1c
	Kernel modules: atl1c
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

---

