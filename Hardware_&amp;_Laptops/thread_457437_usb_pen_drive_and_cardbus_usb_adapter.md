---
title: "usb pen drive and cardbus usb adapter"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by maksei on 2007-05-28
Hi all -
I have a problem mounting a usb pen drive (Memorex 512MB Traveldrive, Kingston 2GB DataTraveler among others) on Ubuntu, Debian, Knoppix etc. 
I have a very old laptop (Dell Latitude XPi CD) without a built-in usb port. I bought a generic cardbus usb2.0 adapter and plugged it in my 32-bit cardbus type II slot. The adapter is detected, but when I plug in any usb pen drive, I get these errors (from dmesg output):

[I]
usb 3-2: new high speed USB device using address 4
usb 3-2: control timeout on ep0out
usb 3-2: control timeout on ep0out
usb 3-2: device not accepting address 4, error -110
usb 3-2: new high speed USB device using address 5
usb 3-2: control timeout on ep0out
usb 3-2: control timeout on ep0out
usb 3-2: device not accepting address 5, error -110
SCSI subsystem initialized
st: Version 20040403, fixed bufsize 32768, s/g segs 256
usb 3-1: new high speed USB device using address 6
usb 3-1: control timeout on ep0out
usb 3-1: control timeout on ep0out
usb 3-1: device not accepting address 6, error -110
usb 3-1: new high speed USB device using address 7
usb 3-1: control timeout on ep0out
usb 3-1: control timeout on ep0out
usb 3-1: device not accepting address 7, error -110
[/I]

Now I've seen posts on the same error that could be fixed by passing some cheatcodes at boot (acpi=off noapic nolapic irqpoll etc.). In my case these don't work. To repeat, this problem seems to be independent of distribution (DSL 3.3, Xubuntu 7.04, Knoppix 5.11, Ubuntu 6.10 & 6.06 LTS, Debian Sarge 3.1r5). I've also tried blacklisting ehci_hcd, ohci_hcd, uhci_hcd (separately and in combination) so they don't get loaded on boot - but to no avail. 

The adapter + pen drive work out of the box on WinXP and with supplied drivers on Win98 on this laptop.

Does anyone know if recompiling my kernel might help? I'm currently writing this from 2.6.8-3-386.

The BIOS on this laptop is very rudimentary - I can't set any IRQ's for instance. No updates to the BIOS are available as far as I could see.

In case this might be of any use, here are the message on boot-up:


[I]Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
Yenta: CardBus bridge found at 0000:00:09.0 [0000:0000]
Yenta: ISA IRQ mask 0x0c98, PCI irq 9
Socket status: 30000010
Yenta: CardBus bridge found at 0000:00:09.1 [0000:0000]
Yenta: ISA IRQ mask 0x0c98, PCI irq 9
Socket status: 30000020
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Feb 02 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ohci_hcd: block sizes: ed 64 td 64
PCI: Enabling device 0000:05:00.0 (0000 -> 0002)
ohci_hcd 0000:05:00.0: NEC Corporation USB
PCI: Setting latency timer of device 0000:05:00.0 to 64
ohci_hcd 0000:05:00.0: irq 9, pci mem c49d1000
ohci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
PCI: Enabling device 0000:05:00.1 (0000 -> 0002)
ohci_hcd 0000:05:00.1: NEC Corporation USB (#2)
PCI: Setting latency timer of device 0000:05:00.1 to 64
ohci_hcd 0000:05:00.1: irq 9, pci mem c49d3000
ohci_hcd 0000:05:00.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
PCI: Enabling device 0000:05:00.2 (0000 -> 0002)
ehci_hcd 0000:05:00.2: NEC Corporation USB 2.0
ehci_hcd 0000:05:00.2: irq 9, pci mem c49d5000
ehci_hcd 0000:05:00.2: new USB bus registered, assigned bus number 3
ehci_hcd 0000:05:00.2: USB 2.0 enabled, EHCI 1.00, driver 2004-May-10
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 5 ports detected
usb 3-2: new high speed USB device using address 2
usb 3-2: control timeout on ep0out
ehci_hcd 0000:05:00.2: Unlink after no-IRQ?  Different ACPI or APIC settings may help.
usb 3-2: control timeout on ep0out
usb 3-2: device not accepting address 2, error -110
usb 3-2: new high speed USB device using address 3
usb 3-2: control timeout on ep0out
usb 3-2: control timeout on ep0out
usb 3-2: device not accepting address 3, error -110
input: PC Speaker
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
inserting floppy driver for 2.6.8-3-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a National Semiconductor PC87306
cs: IO port probe 0x0100-0x04ff: excluding 0x230-0x23f 0x330-0x337 0x388-0x38f
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
cs: memory probe 0xa0000000-0xa0ffffff: clean.
ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A
cdrom: open failed.
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
usb 3-2: new high speed USB device using address 4
usb 3-2: control timeout on ep0out
usb 3-2: control timeout on ep0out
usb 3-2: device not accepting address 4, error -110
usb 3-2: new high speed USB device using address 5
usb 3-2: control timeout on ep0out
usb 3-2: control timeout on ep0out
usb 3-2: device not accepting address 5, error -110
SCSI subsystem initialized
st: Version 20040403, fixed bufsize 32768, s/g segs 256
usb 3-1: new high speed USB device using address 6
usb 3-1: control timeout on ep0out
usb 3-1: control timeout on ep0out
usb 3-1: device not accepting address 6, error -110
usb 3-1: new high speed USB device using address 7
usb 3-1: control timeout on ep0out
usb 3-1: control timeout on ep0out
usb 3-1: device not accepting address 7, error -110[/I]


Here's the output from lspci -vv:

[I]
0000:00:00.0 Host bridge: PicoPower Technology PT86C521 [Vesuvius v1] Host Bridge (rev 05)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort+ >SERR- <PERR+
	Latency: 0

0000:00:06.0 ISA bridge: PicoPower Technology PT86C523 [Vesuvius v3] PCI-ISA Bridge Slave
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

0000:00:07.0 VGA compatible controller: Neomagic Corporation NM2093 [MagicGraph 128ZV] (rev 02) (prog-if 00 [VGA])
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 0
	Region 0: Memory at 30000000 (32-bit, prefetchable) [size=4M]

0000:00:08.0 IDE interface: Silicon Image, Inc. (formerly CMD Technology Inc) PCI0643 (prog-if 80 [Master])
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 1000ns max)
	Interrupt: pin A routed to IRQ 14
	Region 4: I/O ports at fe00 [size=16]

0000:00:09.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 0x20 (128 bytes)
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at 10000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
	Memory window 0: 10400000-107ff000 (prefetchable)
	Memory window 1: 10800000-10bff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

0000:00:09.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 0x20 (128 bytes)
	Interrupt: pin B routed to IRQ 9
	Region 0: Memory at 10001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 10c00000-10fff000 (prefetchable)
	Memory window 1: 11000000-113ff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
	16-bit legacy interface ports at 0001

0000:05:00.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
	Subsystem: NEC Corporation: Unknown device 1735
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (250ns min, 10500ns max)
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at 11000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:05:00.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
	Subsystem: NEC Corporation: Unknown device 1033
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (250ns min, 10500ns max)
	Interrupt: pin B routed to IRQ 9
	Region 0: Memory at 11001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:05:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Unknown device 1735:00e0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 68 (4000ns min, 8500ns max), Cache Line Size: 0x08 (32 bytes)
	Interrupt: pin C routed to IRQ 9
	Region 0: Memory at 11002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-[/I]


Here's my /etc/mtab:
[I]
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
[/I]

any ideas?
thanks,
maxim

---

### Post by maksei on 2007-05-29
:( 
please someone help me out here
really frustrated
i tried removing and inserting yenta_socket, but still getting same problems

i also tried removing ehci-hcd, uhci-hcd and ohci-hcd (because they and yenta_socket are assigned to the same irq #9), but then the usb drive is not registered at all when inserted

also when I look at the boot-up messages, I see that usbcore uses a driver called [I]hub[/] to communicate with usb devices -- whereas I expected to see some scsi driver because usually usb drive is identified as /dev/sda1 or the like. Could that be the problem? how do I disable hub (it seems to be part of usbcore) and substitute some scsi storage driver?


can someone tell me what this line in my /etc/mtab file means:

*usbfs /proc/bus/usb usbfs rw 0 0*

any suggestions are really appreciated

---

