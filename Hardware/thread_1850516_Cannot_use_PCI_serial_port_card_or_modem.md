---
title: "Cannot use PCI serial port card or modem"
date: 2011-09-26
forum: Hardware
---

### Post by brucester on 2011-09-26
When I install either a PCI serial or modem card I cannot get ubuntu to recognize it as an additional serial port like ttyS2. I have tried the setserial command and all the options, but I think its because the kernel does not have a module or driver for it. When I use the lspci -vvv command it shows kernel modules and drivers for the other PCI cards but nothing for the modem card. I even tried disabling the printer and second onboard serial port to see if the modem would be assigned one of those IRQs, instead other cards picked them up. The modem works in Windows, I have listed my lspci -vvv below. Any help would be appreciated.

Thanks

[CODE] ubuntu:~$ lspci -vvv
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8025
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 64
    Region 0: Memory at e4000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: df000000-dfdfffff
    Prefetchable memory behind bridge: dff00000-e3ffffff
    Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B+
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    Region 4: I/O ports at b800 [size=16]
    Kernel driver in use: ata_piix

00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin D routed to IRQ 3
    Region 4: I/O ports at b400 [size=32]
    Kernel driver in use: uhci_hcd

00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin ? routed to IRQ 9
    Kernel modules: i2c-piix4

00:07.0 RAID bus controller: Silicon Image, Inc. PCI0648 (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8025
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min, 1000ns max)
    Interrupt: pin A routed to IRQ 10
    Region 0: I/O ports at b000 [size=8]
    Region 1: I/O ports at a800 [size=4]
    Region 2: I/O ports at a400 [size=8]
    Region 3: I/O ports at a000 [size=4]
    Region 4: I/O ports at 9800 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_cmd64x
    Kernel modules: pata_cmd64x

00:09.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
    Subsystem: D-Link System Inc Device 1400
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (750ns min, 2000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 3
    Region 0: I/O ports at 9400 [size=256]
    Region 1: Memory at de800000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at 20000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:0b.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
    Subsystem: Conexant Systems, Inc. HCF 56k Data/Fax/Voice/Spkp Modem
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at de000000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Region 1: I/O ports at 9000 [disabled] [size=8]
    Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
    Subsystem: ATI Technologies Inc Device 002a
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at e0000000 (32-bit, prefetchable) [size=64M]
    Region 1: I/O ports at d800 [size=256]
    Region 2: Memory at df000000 (32-bit, non-prefetchable) [size=16K]
    Expansion ROM at dffe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: aty128fb

---

### Post by searchfgold6789 on 2011-09-26
Cute rage card, bro. :)
Anyway, what type of modem is it? Just a generic one? If so you may have to install Gnome PPP or KDE PPP.

---

### Post by brucester on 2011-09-26
Yes I think its a generic modem, says AOPEN FM-56.  I have tried other PCI modems including a USRobotics 56K which I thought might be supported but they don't work either. It could be that my bios is not assigning an Irq to the modem, it only shows the onboard serial ports. I disabled the second onboard serial port thinking the bios would assign the irq to the PCI modem, but when I do a lspci irq 3 is assigned to the USB serial. This is what I get when I try to use setserial to autoconfig the modem to use ttyS1
/dev/ttyS1, UART: 16550A, Port: 0x9000, IRQ: 0

# dmesg | grep ttyS
[    0.293179] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.294246] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.974899] ttyS1: LSR safety check engaged!
[   19.981965] ttyS1: LSR safety check engaged!
[   32.445402] ttyS1: LSR safety check engaged!
[  185.850977] ttyS1: LSR safety check engaged!
[  224.367455] ttyS1: LSR safety check engaged!
[  325.307776] ttyS1: LSR safety check engaged!
[  325.307931] ttyS1: LSR safety check engaged!
[  325.560179] ttyS1: LSR safety check engaged!
[  325.560228] ttyS1: LSR safety check engaged!
[  345.530707] ttyS1: LSR safety check engaged!

I guess I need to find a PCI modem that someone has got working in Ubuntu.

Thanks:)

---

