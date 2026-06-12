---
title: "kubuntu Gusty and my SATA drive aren't working !!"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by cIIIz on 2007-12-22
hi all :guitar:

I'm new here and to the linux world so excuse me stupid question,
I just bought a new fresh SATA drive to install a fresh installation of kubuntu Gusty Gibbon on it. I don't want anyother OS on it just kubuntu. I plugged my old ATA drive which has windows XP on it and only connected the SATA drive.

everything went ok from the liveCD, the OS worked like a charm so decided to install kubuntu to my SATA drive BUT when I get to the 4th step in the installation ( where I should pick the partition ) there's nothing there ! just a blank list.

I looked in the forum and couldn't find a solution !
I tried the " pci=nomsi and acpi=force irqpoll " solution that I found [HERE]("http://ubuntuforums.org/showthread.php?t=336315&page=2") but no hope :(

I can see the drive in the file explorer labeled "Remote Share (unionfs)"
and I tried the QTparted program and I got this message " No device found. Maybe you're not using root user ? " 

here is my lspci, it may help !
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:05.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
00:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705 Gigabit Ethernet (rev 03)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R420 JI [Radeon X800PRO]
01:00.1 Display controller: ATI Technologies Inc R420 [Radeon X800 PRO/GTO] (Secondary)

```

so can I install a fresh installation of kubuntu/ubuntu on a fresh SATA drive ?
or do I have to install windows XP and then kubuntu :lolflag:

thanks in advance

---

### Post by calmfury on 2007-12-22
I have an extremely similar situation.  I have gutsy up and running.  I connected a 160gig sata drive (micro center $54.99) and It doesn't show up on my system.  I saw somewhere that there is problem with linux + via + sata.   It appears that the hardware for the controller is recognized according to

[I][I][B][COLOR="Blue"]
 :[I]/var/log$ dmesg | grep ata
[    0.000000]  BIOS-e820: 000000003bef3000 - 000000003bf00000 (ACPI data)
[   20.385242] Memory: 961928k/981952k available (2015k kernel code, 19408k reserved, 916k data, 364k init, 64448k highmem)
[   20.385285]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   26.686748] libata version 2.21 loaded.
[   26.692834] sata_via 0000:00:0f.0: version 2.2
[   26.693372] sata_via 0000:00:0f.0: routed to hard irq line 11
[   26.693534] scsi0 : sata_via
[   26.693629] scsi1 : sata_via
[   26.693676] ata1: SATA max UDMA/133 cmd 0x0001ff00 ctl 0x0001fe02 bmdma 0x0001fb00 irq 16
[   26.693684] ata2: SATA max UDMA/133 cmd 0x0001fd00 ctl 0x0001fc02 bmdma 0x0001fb08 irq 16
[   26.893812] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   27.105669] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   27.289919] ata2.00: ATA-6: ST3160828AS, 3.02, max UDMA/133
[   27.289928] ata2.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   27.305896] ata2.00: configured for UDMA/133
[   29.664627] EXT3-fs: mounted filesystem with ordered data mode.
[   48.332834] EXT3-fs: mounted filesystem with ordered data mode.
[/I][/COLOR][/B][/I][/I]

and lspci
[B][I][I][I][I][I]
[COLOR="Blue"]00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)[/COLOR][/I][/I][/I][/I][/I][/B]

I hope someone knows of a fix for this!

---

### Post by LuisC-SM on 2007-12-22
Hi

I also have a 120 GB sata drive and it's recongnized just fine.

An idea is to use the Ubuntu alternate CD or the normal Ubuntu CD, later you can install kubuntu.

The second idea that comes to my mind is to make a partition with a win 98 cd or MS DOS in case nothing works with gParted or any other partioning tool.

I'm almost sure the second way will work. I've read someplace that "libata" has had some issues readingSATA HD bigger than 120 GB.

Cheers

Luis

---

