---
title: "Ubuntu 12.10 Kernel 3.5 and MOSCHIP 9835 does not work, does not open"
date: 2013-02-08
forum: Hardware
---

### Post by FlavioRoman on 2013-02-08
I'm using Ubuntu 12.10, installed mcs9835 serial card, 2 serial ports is detected, when I try to open the door is frozen as if I was expecting.

Simple test: ls > /dev/ttyS?

When I do that the onboard port ttyS0 works
When I do this on port ttyS [4,5] freezes, the cursor does not return

setserial -g /dev/ttyS[0-7]:

/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS4, UART: 16550A, Port: 0xc000, IRQ: 19
/dev/ttyS5, UART: 16550A, Port: 0xbc00, IRQ: 19
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0

lspci -v:

00:0d.0 Serial controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01) (prog-if 02 [16550])
Subsystem: LSI Logic / Symbios Logic 2S (16C550 UART)
Flags: medium devsel, IRQ 19
I/O ports at c000 [size=8]
I/O ports at bc00 [size=8]
I/O ports at b800 [size=8]
I/O ports at b400 [size=8]
I/O ports at b000 [size=8]
I/O ports at ac00 [size=16]
Kernel driver in use: serial
Kernel modules: 8250_pci

---

### Post by QIII on 2013-02-08
Please do not start duplicate threads with the same subject.

Original post [here](http://ubuntuforums.org/showthread.php?t=2113968)

Thread closed.

---

