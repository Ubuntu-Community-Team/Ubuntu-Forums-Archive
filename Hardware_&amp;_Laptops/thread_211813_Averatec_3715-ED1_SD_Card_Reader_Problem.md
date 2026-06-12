---
title: "Averatec 3715-ED1 SD Card Reader Problem"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by muadib on 2006-07-08
I recently tested the SD card reader on my Averatec 3715-ed1 laptop and found that there are issues with it in Ubuntu. The relevant output from dmesg:

//snip//
[4294832.599000] mmc0: Timeout waiting for hardware interrupt. Please report this to .
[4294832.599000] sdhci: ============== REGISTER DUMP ==============
[4294832.599000] sdhci: Sys addr: 0x1fd58f7c | Version: 0x00002010
[4294832.599000] sdhci: Blk size: 0x00000008 | Blk cnt: 0x00000001
[4294832.599000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000012
[4294832.599000] sdhci: Present: 0x01f70a02 | Host ctl: 0x00000001
[4294832.599000] sdhci: Power: 0x0000000f | Blk gap: 0x00000000
[4294832.599000] sdhci: Walk up: 0x00000000 | Clock: 0x00008007
[4294832.599000] sdhci: Timeout: 0x0000000e | Int stat: 0x00000000
[4294832.599000] sdhci: Int enab: 0x01ff00cf | Sig enab: 0x01ff00cf
[4294832.599000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294832.599000] sdhci: Caps: 0x038021a1 | Max curr: 0x00ffffff
[4294832.599000] sdhci: ===========================================
//endsnip//
I also found that the keyboard stops responding for a few seconds after putting the card in. The kernel version that I was running that generated the output is the following :2.6.15-22-k7, the default Ubuntu Kernel. Other pertinent output would probably include lspci:
//snip// root@durnik:~# lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:09.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
0000:00:0a.2 0805: O2 Micro, Inc.: Unknown device 7120 (rev 01)
0000:00:0a.3 Bridge: O2 Micro, Inc.: Unknown device 7130 (rev 01)
0000:00:0a.4 FireWire (IEEE 1394): O2 Micro, Inc.: Unknown device 00f7 (rev 02)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01) //endsnip//
Not wanting to needlessly disturb the developers, I upgraded to the most recent version of the Linux Kernel which at the time of testing is 2.6.17.4 but found that with this kernel version, when I put in the card the computer crashed. I plan on mailing the mailing list as per the kernel messages now, though I can't at the moment because I am currently offline.
If anyone has had any luck with the card reader or has any suggestions, please let me know.

---

