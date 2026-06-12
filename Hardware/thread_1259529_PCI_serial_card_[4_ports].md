---
title: "PCI serial card [4 ports]"
date: 2009-09-06
forum: Hardware
---

### Post by MORA99 on 2009-09-06
Hi,

Does anyone have a few products that are known to work with ubuntu/linux ?
I need 4 RS232 ports in a PCI port (the old version).
I only have one PCI port, but plenty of room for 2 brackets if needed.


This is the one I have now "Serial controller: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART)"

Its detected and all ports added (and 4 too many), but I cant get it working, at one time I had it working but only about 10% of whats sent gets trough.
Tried changeing baud_base based on forum advice found on google (1152000), also tried 921563 920000 as thats about 1/16 of the freq mentioned in the manual.

I have changed boot to include 8250.nr_uarts=16 pci=nomsi,noacpi
(the msi one is for the network card)

The card is from "MANHATTAN".

But if I can find one card that is known to work I will just replace it.
Otherwise if you have an idea to get the card going, please let me know.


lspci
```

04:00.0 Serial controller: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 0 (Uart) (prog-if 06)
        Subsystem: Oxford Semiconductor Ltd Device 0000
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 21
        Region 0: I/O ports at 1060 [size=32]
        Region 1: Memory at 90103000 (32-bit, non-prefetchable) [size=4K]
        Region 2: I/O ports at 1040 [size=32]
        Region 3: Memory at 90102000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: serial

04:00.1 Bridge: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 1 (8bit bus)
        Subsystem: Oxford Semiconductor Ltd Device 0000
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 21
        Region 0: I/O ports at 1020 [size=32]
        Region 1: Memory at 90101000 (32-bit, non-prefetchable) [size=4K]
        Region 2: I/O ports at 1000 [size=32]
        Region 3: Memory at 90100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: serial

```

setserial -g /dev/ttyS*
```

/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS10, UART: 16450, Port: 0x1030, IRQ: 21
/dev/ttyS11, UART: 16450, Port: 0x1038, IRQ: 21
/dev/ttyS12, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS13, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS14, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS15, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS4, UART: 16950/954, Port: 0x1060, IRQ: 21
/dev/ttyS5, UART: 16950/954, Port: 0x1068, IRQ: 21
/dev/ttyS6, UART: 16950/954, Port: 0x1070, IRQ: 21
/dev/ttyS7, UART: 16950/954, Port: 0x1078, IRQ: 21
/dev/ttyS8, UART: 16450, Port: 0x1020, IRQ: 21
/dev/ttyS9, UART: 16450, Port: 0x1028, IRQ: 21

```
(0 is the one on the motherboard, 4-7 is the new ones, dont know about the rest)

lsb_release
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

```

dmesg
```

[    2.285765] Serial: 8250/16550 driver16 ports, IRQ sharing enabled
[    2.285884] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.286855] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.286997] serial 0000:04:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.287099] ttyS4: detected caps 00000700 should be 00000100
[    2.287111] 0000:04:00.0: ttyS4 at I/O 0x1060 (irq = 21) is a 16C950/954
[    2.287248] ttyS5: detected caps 00000700 should be 00000100
[    2.287259] 0000:04:00.0: ttyS5 at I/O 0x1068 (irq = 21) is a 16C950/954
[    2.287393] ttyS6: detected caps 00000700 should be 00000100
[    2.287404] 0000:04:00.0: ttyS6 at I/O 0x1070 (irq = 21) is a 16C950/954
[    2.287537] ttyS7: detected caps 00000700 should be 00000100
[    2.287548] 0000:04:00.0: ttyS7 at I/O 0x1078 (irq = 21) is a 16C950/954
[    2.287611] serial 0000:04:00.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.287685] 0000:04:00.1: ttyS8 at I/O 0x1020 (irq = 21) is a 16450
[    2.287796] 0000:04:00.1: ttyS9 at I/O 0x1028 (irq = 21) is a 16450
[    2.287905] 0000:04:00.1: ttyS10 at I/O 0x1030 (irq = 21) is a 16450
[    2.288015] 0000:04:00.1: ttyS11 at I/O 0x1038 (irq = 21) is a 16450

```

The system is a 1.6GHz atom 330 dual core with HT enabled with 2GB ram running 32bit ubuntu (installed last week from network).

Dont know what more to show to help in diagnoseing the problem :)

---

### Post by Vesperatus on 2010-04-01
Did you ever managed to get it to work ?

I stumbled on this post and I seem to have very similar hardware and I cant communicate with the devices. Works without issues under windows however.

---

### Post by MORA99 on 2010-04-01
Sadly no, I ended up using 4 USB-RS232 adapters, they work but have the added problem that the TTY is may change from time to time.

I returned the card for a refund after spending quite some time trying to get it working.

---

### Post by N9TA on 2010-04-17
I've got the same problem with a SIIG 4 port product. Can anyone help with this?

---

