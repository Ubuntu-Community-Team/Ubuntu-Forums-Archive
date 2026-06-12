---
title: "Installing serial in Ubuntu Server issue"
date: 2012-01-07
forum: Hardware
---

### Post by Xeneth on 2012-01-07
I am trying to install a 4 port Serial PCI card.  Never installed in linux, so learning new.

Kernel version:  
3.0.0-14-generic-pae

My computer seed the device:
```

01:01.0 Communication controller: Device 5372:6873 (rev 01)
    Subsystem: LSI Logic / Symbios Logic Device 0004
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 5
    Region 0: I/O ports at de88 [size=8]
    Region 1: I/O ports at de90 [size=8]
    Region 2: I/O ports at de98 [size=8]
    Region 3: I/O ports at dea0 [size=8]
    Region 4: I/O ports at dea8 [size=8]
    Region 5: I/O ports at deb0 [size=16]

```


ttyS's in /dev:

```

ls -l /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 2012-01-07 18:56 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2012-01-07 18:56 /dev/ttyS1
crw-rw---- 1 root dialout 4, 74 2012-01-07 18:56 /dev/ttyS10
crw-rw---- 1 root dialout 4, 75 2012-01-07 18:56 /dev/ttyS11
crw-rw---- 1 root dialout 4, 76 2012-01-07 18:56 /dev/ttyS12
crw-rw---- 1 root dialout 4, 77 2012-01-07 18:56 /dev/ttyS13
crw-rw---- 1 root dialout 4, 78 2012-01-07 18:56 /dev/ttyS14
crw-rw---- 1 root dialout 4, 79 2012-01-07 18:56 /dev/ttyS15
crw-rw---- 1 root dialout 4, 80 2012-01-07 18:56 /dev/ttyS16
crw-rw---- 1 root dialout 4, 81 2012-01-07 18:56 /dev/ttyS17
crw-rw---- 1 root dialout 4, 82 2012-01-07 18:56 /dev/ttyS18
crw-rw---- 1 root dialout 4, 83 2012-01-07 18:56 /dev/ttyS19
crw-rw---- 1 root dialout 4, 66 2012-01-07 18:56 /dev/ttyS2
crw-rw---- 1 root dialout 4, 84 2012-01-07 18:56 /dev/ttyS20
crw-rw---- 1 root dialout 4, 85 2012-01-07 18:56 /dev/ttyS21
crw-rw---- 1 root dialout 4, 86 2012-01-07 18:56 /dev/ttyS22
crw-rw---- 1 root dialout 4, 87 2012-01-07 18:56 /dev/ttyS23
crw-rw---- 1 root dialout 4, 88 2012-01-07 18:56 /dev/ttyS24
crw-rw---- 1 root dialout 4, 89 2012-01-07 18:56 /dev/ttyS25
crw-rw---- 1 root dialout 4, 90 2012-01-07 18:56 /dev/ttyS26
crw-rw---- 1 root dialout 4, 91 2012-01-07 18:56 /dev/ttyS27
crw-rw---- 1 root dialout 4, 92 2012-01-07 18:56 /dev/ttyS28
crw-rw---- 1 root dialout 4, 93 2012-01-07 18:56 /dev/ttyS29
crw-rw---- 1 root dialout 4, 67 2012-01-07 18:56 /dev/ttyS3
crw-rw---- 1 root dialout 4, 94 2012-01-07 18:56 /dev/ttyS30
crw-rw---- 1 root dialout 4, 95 2012-01-07 18:56 /dev/ttyS31
crw-rw---- 1 root dialout 4, 68 2012-01-07 18:56 /dev/ttyS4
crw-rw---- 1 root dialout 4, 69 2012-01-07 18:56 /dev/ttyS5
crw-rw---- 1 root dialout 4, 70 2012-01-07 18:56 /dev/ttyS6
crw-rw---- 1 root dialout 4, 71 2012-01-07 18:56 /dev/ttyS7
crw-rw---- 1 root dialout 4, 72 2012-01-07 18:56 /dev/ttyS8
crw-rw---- 1 root dialout 4, 73 2012-01-07 18:56 /dev/ttyS9

```

Using stty, I tried getting a response from any of them, all gave an error but ttyS0 which is the built in port.

Using "sudo setserial -g /dev/ttyS*" got me:
```

/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS10, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS11, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS12, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS13, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS14, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS15, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS16, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS17, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS18, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS19, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS20, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS21, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS22, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS23, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS24, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS25, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS26, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS27, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS28, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS29, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS30, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS31, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS4, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS5, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS8, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS9, UART: unknown, Port: 0x0000, IRQ: 0

```

I admit that I was trying random things looking for a lead or to make a connection, but none are helping.  The drivers that came with it are on a vague disk, and has windows DLL's.

Any help would be greatly appreciated.


PS.  I got this off of ebay, so I am not 100% of it's brand, assuming lsi, but read evidence that other brands get labeled that in Linux.

---

### Post by Xeneth on 2012-01-07
This may not be very helpful, but what do I know?  :P

The windows drivers are names "MT68XDRV.inf" (could not find any info using this.)

The box it came in did have the name "Hexin" though it was a box for a cord originally, but had an added sticker of "XHH-1049" which did pull up one similar to mine, but not quite.  Maybe I got a knockoff.  Don't care if it works.


PS:  Looks like the brand is "[Elecity]("http://onbene.com/Manufacturer/7-elecity.aspx")", still having issues finding drivers.

---

