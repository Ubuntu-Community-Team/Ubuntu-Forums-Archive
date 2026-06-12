---
title: "Network adapter driver for older laptop"
date: 2012-01-11
forum: Hardware
---

### Post by Senor Piquante on 2012-01-11
Hello everybody! I was hoping to pick your collective brain about something. I've got a fairly old laptop (from 2007 or earlier) which I've recently installed Ubuntu 10.04 onto. It connects to the Internet just fine with a wired connection, but it can't find the wireless driver on it's own, so I did some digging and turned up [this driver]("http://manpages.ubuntu.com/manpages/natty/man4/sis.4freebsd.html").

Here's the issue: The instructions say to add two lines to the kernel configuration file. I found instructions on this very forum on how to find the Grub files and how to add edits to 40_custom and use update-grub to apply them, but (being somewhat new to Ubuntu) I'm almost certain I've missed a step. For one thing, my connection options still tell me that the wireless is disabled.

I know the laptop can connect wirelessly when the drivers are working, having used the machine with another operating system before. Any suggestions? I bow to your collective expertise =)

---

### Post by TBABill on 2012-01-11
First step is to figure out what device the laptop uses. To do so you can open a terminal and type in ```
lspci -vvn
```Paste the output here and we can help guide you from there. Please don't edit grub or take other steps without knowing what you are doing. Grub is your bootloader and has no effect on your wireless.

---

### Post by Senor Piquante on 2012-01-11
Output from lspci -vvn

```

00:00.0 0600: 1039:0760 (rev 03)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 64
    Region 0: Memory at e0000000 (32-bit, non-prefetchable) [size=32M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64
    Kernel modules: amd64-agp

00:01.0 0604: 1039:0002
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: e2100000-e21fffff
    Prefetchable memory behind bridge: e8000000-efffffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:02.0 0601: 1039:0963 (rev 25)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:02.1 0c05: 1039:0016
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 0
    Region 4: I/O ports at 8100 [size=32]
    Kernel driver in use: sis96x_smbus
    Kernel modules: i2c-sis96x

00:02.5 0101: 1039:5513 (prog-if 80 [Master])
    Subsystem: 1025:0083
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 128
    Interrupt: pin ? routed to IRQ 16
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    Region 4: I/O ports at 2000 [size=16]
    Kernel driver in use: pata_sis

00:02.6 0703: 1039:7013 (rev a0)
    Subsystem: 1025:0083
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 18
    Region 0: I/O ports at 1000 [size=256]
    Region 1: I/O ports at 1c00 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

00:02.7 0401: 1039:7012 (rev a0)
    Subsystem: 1025:0083
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 173 (13000ns min, 2750ns max)
    Interrupt: pin C routed to IRQ 18
    Region 0: I/O ports at 1400 [size=256]
    Region 1: I/O ports at 1c80 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:03.0 0c03: 1039:7001 (rev 0f) (prog-if 10)
    Subsystem: 1025:0083
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (20000ns max)
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at e2002000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.1 0c03: 1039:7001 (rev 0f) (prog-if 10)
    Subsystem: 1025:0083
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (20000ns max)
    Interrupt: pin B routed to IRQ 21
    Region 0: Memory at e2003000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.2 0c03: 1039:7002 (prog-if 20)
    Subsystem: 1025:0083
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (20000ns max)
    Interrupt: pin D routed to IRQ 23
    Region 0: Memory at e2004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 0200: 1039:0900 (rev 91)
    Subsystem: 1025:0083
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 173 (13000ns min, 2750ns max)
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at 1800 [size=256]
    Region 1: Memory at e2005000 (32-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at 28000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sis900
    Kernel modules: sis900

00:06.0 0607: 104c:ac50 (rev 02)
    Subsystem: 1025:0083
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at 28020000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 24000000-27fff000
    I/O window 0: 00002400-000024ff
    I/O window 1: 00002800-000028ff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

00:0b.0 0280: 14e4:4318 (rev 02)
    Subsystem: 1468:0312
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at e2000000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

00:18.0 0600: 1022:1100
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>

00:18.1 0600: 1022:1101
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 0600: 1022:1102
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 0600: 1022:1103
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 0300: 1039:6330
    Subsystem: 1025:0083
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 7
    BIST result: 00
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at e2100000 (32-bit, non-prefetchable) [size=128K]
    Region 2: I/O ports at a000 [size=128]
    Capabilities: <access denied>
    Kernel modules: sisfb

```

---

### Post by TBABill on 2012-01-12
Sorry, can you just run ```
lspci -vv
```

---

### Post by Senor Piquante on 2012-01-12
Actually, it turned out to be less of a driver issue and more of a "I'm a blockhead" issue :P There's a button on the front of this thing that turns the wireless on and off; I must have hit it at some point since I last used it. Everything's good now. Thanks for your time anyway :)

---

