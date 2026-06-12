---
title: "Ubuntu 12.04 Parallel Card Installation Problem"
date: 2013-12-11
forum: Hardware
---

### Post by BatuhanK on 2013-12-11
PC which has onboard parallel port and i am trying to put 2 more. Name of the cards is PCI EF232 2S1P. As i know its chipset is MCS98xx.

03:00.0 Communication controller: Device 5372:6872 (rev 01)
   Subsystem: LSI Logic / Symbios Logic Device 0012
   Flags: slow devsel, IRQ 21
   I/O ports at 3070 [size=8]
   I/O ports at 3068 [size=8]
   I/O ports at 3060 [size=8]
   I/O ports at 3058 [size=8]
   I/O ports at 3050 [size=8]
   I/O ports at 3040 [size=16]
   Kernel driver in use: serial

03:01.0 Communication controller: Apache Micro Peripherals Inc Device 1035 (rev 08)
   Subsystem: Apache Micro Peripherals Inc Device 1035
   Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 11
   Memory at e8100000 (32-bit, non-prefetchable) [size=64K]
   I/O ports at 3078 [size=8]
   Capabilities: [40] Power Management version 2

I think first one is the parallel port card second one is the onboard parallel port. 

#grep parport /proc/ioports
0378-037a : parport0

In the installation pdf of the MCS98xx chipset this is writter :

Installing MCS98XX Parallel Port on Linux Platform:
To install the parallel port use the following command.
/sbin/modprobe parport_pc io=0x3f8,a400 irq=4,18
(and press ENTER)
The above command indicates onboard parallel port at 0x3f8 with IRQ 4 and MCS9835
parallel port at a400 with IRQ18. (Refer to fig 2)
Incase if you require using more than 2 parallel ports (for example MCS9815) make use
of the following command:
/sbin/modprobe parport_pc io=0x3f8,8800,8c00,9c00 irq=4,18
(and press ENTER)
In the above command 9c00 is 16 bit I/O address and 8800 / 8c00 are 8 bit addresses.
Refer to the screen shot below for clarity.


I really don't know how can i make the other lpt ports works. Can someone help me?

---

### Post by BatuhanK on 2013-12-12
any suggestions?

---

### Post by BatuhanK on 2013-12-23
??

---

