---
title: "Ubuntu 12.10 Kernel 3.5 and MOSCHIP 9865 does not work, does not open"
date: 2013-02-08
forum: Hardware
---

### Post by FlavioRoman on 2013-02-08
I'm using Ubuntu 12.10, installed mcs9865 serial card, 2 serial ports is detected, when I try to open the door is frozen as if I was expecting.

Simple test: ls > /dev/ttyD?
When I do that the onboard port ttyS0 works
When I do this on port ttyD[4,5] freezes, the cursor does not return

setserial -g /dev/tty[SD]*:

/dev/ttyD0, UART: 16550A, Port: 0xc000, IRQ: 19
/dev/ttyD1, UART: 16550A, Port: 0xbc00, IRQ: 16
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS4, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS5, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0

lspci -v:

00:0d.0 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02 [16550])
Subsystem: Device a000:1000
Flags: bus master, medium devsel, latency 64, IRQ 19
I/O ports at c000 [size=8]
Memory at feaf7000 (32-bit, non-prefetchable) [size=4K]
Memory at feaf6000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [48] Power Management version 2
Kernel driver in use: mcs9865-serial
Kernel modules: parport_pc, 8250_pci

00:0d.1 Serial controller: NetMos Technology PCI 9865 Multi-I/O Controller (prog-if 02 [16550])
Subsystem: Device a000:1000
Flags: bus master, medium devsel, latency 64, IRQ 16
I/O ports at bc00 [size=8]
Memory at feaf5000 (32-bit, non-prefetchable) [size=4K]
Memory at feaf4000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [48] Power Management version 2
Kernel driver in use: mcs9865-serial
Kernel modules: parport_pc, 8250_pci

As directed by the manufacturer of the snippet source commented:

drivers/tty/serial/8250/8250_pci.c

/ *
{PCI_VENDOR_ID_NETMOS, PCI_DEVICE_ID_NETMOS_9865,
0xA000, 0x1000,
0, 0, pbn_b0_1_115200},

{PCI_VENDOR_ID_NETMOS, PCI_DEVICE_ID_NETMOS_9865,
0xA000, 0x3002,
0, 0, pbn_b0_bt_2_115200},

{PCI_VENDOR_ID_NETMOS, PCI_DEVICE_ID_NETMOS_9865,
0xA000, 0x3004,
0, 0, pbn_b0_bt_4_115200},
* /

And recompile the kernel and installed the package MCS9865_Linux_Driver_v2.0.0_Source.tar.bz2

---

### Post by FlavioRoman on 2013-02-14
[COLOR="red"]Newer versions of the kernel, when you run:

  **open (device, O_RDWR or O_SYNC)**

Do not open the door, waiting process.
[/COLOR]

[COLOR="Navy"]I adjusted my code to:

  **open (device, O_RDWR or O_NONBLOCK or O_NOCTTY))**

Thus resolved.[/COLOR]

---

