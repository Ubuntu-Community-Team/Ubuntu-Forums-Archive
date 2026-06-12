---
title: "help me get my serial io card to work"
date: 2009-03-05
forum: Hardware
---

### Post by Ryan Castellucci on 2009-03-05
My Serial IO card is autodetected and the devices are created, but when i try to mess with them...

root@windy:~# stty -F /dev/ttyS1
stty: /dev/ttyS1: Input/output error
root@windy:~# stty -F /dev/ttyS2
stty: /dev/ttyS2: Input/output error

dmesg says....

[800858.222992] ttyS1: LSR safety check engaged!
[800861.041254] ttyS2: LSR safety check engaged!

lspci output:

```

05:00.0 0780: 9710:9835 (rev 01)
        Subsystem: 1000:0012
05:00.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)
        Subsystem: LSI Logic / Symbios Logic 1P2S
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at d410 [size=8]
        Region 1: I/O ports at d418 [size=8]
        Region 2: I/O ports at d420 [size=8]
        Region 3: I/O ports at d428 [size=8]
        Region 4: I/O ports at d430 [size=8]
        Region 5: I/O ports at d400 [size=16]

```

setserial says

# setserial -g /dev/ttyS{1,2}
/dev/ttyS1, UART: 16550A, Port: 0xd410, IRQ: 16
/dev/ttyS2, UART: 16550A, Port: 0xd418, IRQ: 16

---

