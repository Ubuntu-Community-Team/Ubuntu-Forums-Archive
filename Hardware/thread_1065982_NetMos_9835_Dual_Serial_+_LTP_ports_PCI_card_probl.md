---
title: "NetMos 9835 Dual Serial + LTP ports PCI card problem"
date: 2009-02-10
forum: Hardware
---

### Post by Ghotler on 2009-02-10
Here is the device:

[https://www.advanced2000.com/items.asp?Cc=CON-ENA&ItemMoveby](https://www.advanced2000.com/items.asp?Cc=CON-ENA&ItemMoveby)...

some information about the hardware

01:0a.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)
Subsystem: LSI Logic / Symbios Logic Device 0012
Flags: medium devsel, IRQ 5
I/O ports at 9c00 [size=8]
I/O ports at 9800 [size=8]
I/O ports at 9400 [size=8]
I/O ports at 9000 [size=8]
I/O ports at 8c00 [size=8]
I/O ports at 8800 [size=16]
Kernel driver in use: parport_serial
Kernel modules: parport_serial

setserial /dev/ttyS0 -a
/dev/ttyS0, Line 0, UART: unknown, Port: 0x9c00, IRQ: 5
Baud_base: 115200, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal

setserial /dev/ttyS1 -a
/dev/ttyS1, Line 1, UART: 16550A, Port: 0x9800, IRQ: 5
Baud_base: 115200, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal skip_test

setserial /dev/ttyS2 -a
/dev/ttyS2, Line 2, UART: unknown, Port: 0x03e8, IRQ: 4
Baud_base: 115200, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal skip_test

setserial /dev/ttyS3 -a
/dev/ttyS3, Line 3, UART: unknown, Port: 0x02e8, IRQ: 3
Baud_base: 115200, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal 

than my problem is that the card isnt working, i have an IR reciver that i built, and under windows it works fine, but in linux its not, so my IR reciver not gonna be the problem, than my PCI card is...i tring to catch a signal what i sending with my remote, for this i use xmode2 and mode2 but nothing happend , i cannot seeing any sign on my screen, pls help me...

---

