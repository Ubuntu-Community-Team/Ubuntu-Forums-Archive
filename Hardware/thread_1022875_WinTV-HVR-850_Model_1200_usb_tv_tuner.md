---
title: "WinTV-HVR-850 Model 1200 usb tv tuner"
date: 2008-12-27
forum: Hardware
---

### Post by Brazman on 2008-12-27
Has anyone had any luck getting this device to work? I have tried many posts suggestions and to no luck. Here is a copy of dmesg and lspci -v:

_**dmesg:**_
> 11.526665] tveeprom 2-0050: Hauppauge model 72301, rev B3F0, serial# 5091597
[   11.526669] tveeprom 2-0050: MAC address is 00-0D-FE-4D-B1-0D
[   11.526673] tveeprom 2-0050: tuner model is Xceive XC5000 (idx 150, type 4)
[   11.526676] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   11.526679] tveeprom 2-0050: audio processor is AU8522 (idx 44)
[   11.526682] tveeprom 2-0050: decoder processor is AU8522 (idx 42)
[   11.526685] tveeprom 2-0050: has no radio, has IR receiver, has no IR transmitter
[   11.526688] hauppauge_eeprom: hauppauge eeprom: model=72301
[   11.814779] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   11.814784] nvidia 0000:03:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   11.814790] nvidia 0000:03:00.0: setting latency timer to 64
[   11.823950] nvidia 0000:05:00.0: enabling device (0000 -> 0003)
[   11.824330] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   11.824335] nvidia 0000:05:00.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   11.824347] nvidia 0000:05:00.0: setting latency timer to 64
[   11.824713] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
[   11.875104] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   11.875109] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   11.875124] HDA Intel 0000:00:10.1: setting latency timer to 64
[   11.903039] xc5000: Successfully identified at address 0x61
[   11.903043] xc5000: Firmware has not been loaded previously
[   11.903047] DVB: registering new adapter (au0828)
[   11.903050] DVB: registering frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[   11.903356] Registered device AU0828 [Hauppauge HVR850]
[   11.903521] usbcore: registered new interface driver au0828
[   11.910871] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   11.912544] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x6004
[   11.912571] usbcore: registered new interface driver usblp
[   12.908449] lp0: using parport0 (interrupt-driven).
[   13.001874] Adding 1992020k swap on /dev/sda5.  Priority:-1 extents:1 across:1992020k
[   13.543826] EXT3 FS on sda6, internal journal
[   14.274748] kjournald starting.  Commit interval 5 seconds
[   14.277580] EXT3 FS on sda7, internal journal
[   14.277587] EXT3-fs: mounted filesystem with ordered data mode.
[   14.445970] type=1505 audit(1230391771.624:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4811
[   14.566634] type=1505 audit(1230391771.745:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4816
[   14.566778] type=1505 audit(1230391771.745:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4816
[   14.695759] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.106828] ACPI: WMI: Mapper loaded
[   15.748863] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)


_**lspci -v:**_
> 00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [40] HyperTransport: Host or Secondary Interface

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
	I/O behind bridge: 00007000-0000afff
	Memory behind bridge: f2000000-fbffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000efffffff
	Capabilities: [40] Subsystem: nVidia Corporation Device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping Enable- Fixed-

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at 1c00 [size=64]
	I/O ports at 1c80 [size=64]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f043:81bc
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f400 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81bc
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=128
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: fde00000-fdefffff
	Capabilities: [b8] Subsystem: nVidia Corporation Device cb84
	Capabilities: [8c] HyperTransport: MSI Mapping Enable- Fixed-

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 829e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 8221
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

01:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=01, secondary=02, subordinate=06, sec-latency=0
	I/O behind bridge: 00007000-0000afff
	Memory behind bridge: f2000000-fbffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000efffffff
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Upstream Port, MSI 00
	Capabilities: [a0] Subsystem: Gammagraphx, Inc. Device 0000
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

02:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f2000000-f5ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Downstream Port (Slot-), MSI 00
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

02:01.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 00000000eff00000-00000000efffffff
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Downstream Port (Slot-), MSI 00
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

02:02.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: f6000000-f9ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Downstream Port (Slot-), MSI 00
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

02:03.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fbe00000-fbefffff
	Prefetchable memory behind bridge: 00000000efe00000-00000000efefffff
	Capabilities: [40] Power Management version 3
	Capabilities: [60] Express Downstream Port (Slot-), MSI 00
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
	Subsystem: eVga.com. Corp. Device c802
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at f2000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ac00 [size=128]
	[virtual] Expansion ROM at f5fe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

05:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
	Subsystem: eVga.com. Corp. Device c802
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 8c00 [size=128]
	[virtual] Expansion ROM at f9000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

07:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: D-Link System Inc Device 3a13
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ath_pci
	Kernel modules: ath_pci

07:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 81fe
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at bc00 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394


---

### Post by Brazman on 2009-05-09
Just wanted to state that I finally got this to work. I found the firmware online "dvb-fe-xfc5000-1.1.fw" and that solved this issue.

Here is the website: "http://www.gossamer-threads.com/lists/mythtv/users/361745"

You will find that the instructions work. Just download and copy it to this location: "cp dvb-fe-xc5000-1.1.fw /lib/firmware/" and then it should work.

I would like to say thank you to Mitchell for his post. 

The part that is working is ATSC. I did manage to get it to work in mythTV for broadcast but still trying to get cable to work. If anyone can help with that I would greatly appreciate it.

thanks,
Brazman

---

### Post by Victormd on 2009-06-07
I've been trying to get this same card (WinTV HVR-850) to work with no luck. Myth fails to open the card and TVTime can't seem to find it either. I followed so many guides that my lib/firmware has a bunch of different firmwares and I don't know what else to do. I followed the link you posted and downloaded that firmware as well but still no luck... Any suggestions??

---

### Post by MountainX on 2009-12-03
> **Brazman said:**
> Has anyone had any luck getting this device to work?

I got it to work in Mythbuntu 9.10. In the backend setup, set it up as a DVB card. Give it a separate video source from any PVR-X50 cards. And have it scan for channels (using EIT I think it's called).

I'm running 1 PVR-150 on Comcast cable which gets channel info from schedulesdirect.org. I'm running 1 HVR-850 also on Comcast cable with "over the air" program guide info.

---

### Post by markackerman8@gmail.com on 2010-03-31
Hello,

I would sure like to know if anyone has had any luck getting either the 850 or 950Q working with MythTV and NTSC analog cable?

I have been trying for a very long time to view cable tv with my computer! Arghhhh!

---

### Post by 510carl on 2011-02-20
Happauge WinTV-HVR 850 Working 100 percent in ubuntu 10.10 with Me TV 1.3.1

---

### Post by tunton on 2011-04-03
@510Carl, How did you get it to work?  Just plugging it in or did you have to install drivers? Also is it HVR850 Model 1200?

---

