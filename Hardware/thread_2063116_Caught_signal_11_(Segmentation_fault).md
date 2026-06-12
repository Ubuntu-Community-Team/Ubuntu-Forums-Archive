---
title: "Caught signal 11 (Segmentation fault)"
date: 2012-09-26
forum: Hardware
---

### Post by oldnik on 2012-09-26
Hello,
My laptop sometimes unexpectedly goes logout without any possible assumption of the bug. I can't reproduce the error, but each time I have the 
```
Caught signal 11 (Segmentation fault)
```in the Xorg.0.log.old
Here are some logs:
Xorg.0.old
```
[ 17578.168] 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0x21d000+0x2448b) [0x24148b]
[ 17578.168] 9: /usr/lib/xorg/modules/drivers/intel_drv.so (0x21d000+0x9233) [0x226233]
[ 17578.168] 10: /usr/lib/i386-linux-gnu/libdrm.so.2 (drmHandleEvent+0xce) [0x35d9ee]
[ 17578.168] 11: /usr/lib/xorg/modules/drivers/intel_drv.so (0x21d000+0x9297) [0x226297]
[ 17578.168] 12: /usr/bin/X (WakeupHandler+0x53) [0x8076243]
[ 17578.168] 13: /usr/bin/X (WaitForSomething+0x1a5) [0x80a3fa5]
[ 17578.168] 14: /usr/bin/X (0x8048000+0x29ed2) [0x8071ed2]
[ 17578.168] 15: /usr/bin/X (0x8048000+0x1c70c) [0x806470c]
[ 17578.168] 16: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0x6b7113]
[ 17578.168] 17: /usr/bin/X (0x8048000+0x1ca21) [0x8064a21]
[ 17578.169] Segmentation fault at address 0xb83a8c8
[ 17578.191] 
Caught signal 11 (Segmentation fault). Server aborting
[ 17578.191] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[ 17578.191] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 17578.191] 
[ 17578.218] (II) Power Button: Close
[ 17578.239] (II) UnloadModule: "evdev"
[ 17578.240] (II) Unloading evdev
[ 17578.241] (II) Video Bus: Close
[ 17578.241] (II) UnloadModule: "evdev"
[ 17578.241] (II) Unloading evdev
[ 17578.243] (II) Power Button: Close
[ 17578.243] (II) UnloadModule: "evdev"
[ 17578.243] (II) Unloading evdev
[ 17578.247] (II) Sleep Button: Close
[ 17578.247] (II) UnloadModule: "evdev"
[ 17578.247] (II) Unloading evdev
[ 17578.248] (II) 1.3M WebCam: Close
[ 17578.249] (II) UnloadModule: "evdev"
[ 17578.249] (II) Unloading evdev
[ 17578.250] (II) AT Translated Set 2 keyboard: Close
[ 17578.251] (II) UnloadModule: "evdev"
[ 17578.251] (II) Unloading evdev
[ 17578.267] (II) UnloadModule: "synaptics"
[ 17578.267] (II) Unloading synaptics
[ 17578.269] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 17578.320]  ddxSigGiveUp: Closing log
```and $lspci -vvnn :
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at f0400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 21
    Region 4: I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 19
    Region 0: Memory at f0904000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 44
    Region 0: Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 80700000-808fffff
    Prefetchable memory behind bridge: 0000000080900000-0000000080afffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 80000000-800fffff
    Prefetchable memory behind bridge: 0000000080500000-00000000806fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 80100000-801fffff
    Prefetchable memory behind bridge: 0000000080300000-00000000804fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 4: I/O ports at 1860 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at 1880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 18a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 16
    Region 4: I/O ports at 18c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at f0904400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 0: I/O ports at 18f8 [size=8]
    Region 1: I/O ports at 180c [size=4]
    Region 2: I/O ports at 18f0 [size=8]
    Region 3: I/O ports at 1808 [size=4]
    Region 4: I/O ports at 18e0 [size=16]
    Region 5: I/O ports at 1810 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 10
    Region 0: Memory at 80200000 (64-bit, non-prefetchable) [size=256]
    Region 4: I/O ports at 1c00 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:292d] (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: Acer Incorporated [ALI] Device [1025:049b]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 0: I/O ports at 1c50 [size=8]
    Region 1: I/O ports at 1c44 [size=4]
    Region 2: I/O ports at 1c48 [size=8]
    Region 3: I/O ports at 1c40 [size=4]
    Region 4: I/O ports at 1c30 [size=16]
    Region 5: I/O ports at 1c20 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

07:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6603]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at 80000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

09:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:0253]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 45
    Region 0: Memory at 80100000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

```and from xsession-errors.log
```
(gnome-settings-daemon:6171): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed

(gnome-settings-daemon:6171): libappindicator-CRITICAL **: app_indicator_set_label: assertion `IS_APP_INDICATOR (self)' failed
```Those unexpected logouts are annoying! Can I do something with them?

---

