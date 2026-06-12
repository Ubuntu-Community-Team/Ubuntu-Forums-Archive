---
title: "serial port FIFO overruns"
date: 2008-08-10
forum: Hardware
---

### Post by davidgarcin on 2008-08-10
I've just added a PCI 2-port serial/1-port parallel card to my linux
box (Ubuntu 8.04 x64), and I'm having trouble getting the serial ports
to work correctly.  The serial chipset is the NetMos Nm 9835, and the
card is a Rosewill RC-303.

When receiving serial data, I will consistently get 16 bytes of data
before transmission is cut off.  Looking at dmesg with "dmesg | grep
ttyS2", I get a "ttyS2: 1 input overrun(s)" for every transmission
that I initiate from the sending device.  It would appear that the
16-byte UART FIFO is filling up and never being emptied....

So, I checked the IRQs:

```
dvg@chiron:~$ lspci -v
...
05:01.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O
Controller (rev 01)
       Subsystem: LSI Logic / Symbios Logic 1P2S
       Flags: medium devsel, IRQ 17
       I/O ports at ec00 [size=8]
       I/O ports at e880 [size=8]
       I/O ports at e800 [size=8]
       I/O ports at e480 [size=8]
       I/O ports at e400 [size=8]
       I/O ports at e080 [size=16]
```

However, looking at the IRQs assigned the serial port, I get IRQ 18, not 17:

```
dvg@chiron:~$ setserial -a /dev/ttyS2
/dev/ttyS2, Line 2, UART: 16550A, Port: 0xe880, IRQ: 18
       Baud_base: 115200, close_delay: 50, divisor: 0
       closing_wait: 3000
       Flags: spd_normal skip_test
```

This would explain why the FIFO is never emptied, the interrupt from
the UART never gets received.

I've tried reassigning the IRQ like so:
```
dvg@chiron:/etc/init.d$ sudo setserial /dev/ttyS2 port e880 UART
16550A irq 17 Baud_base 115200
Cannot set serial info: Device or resource busy
```

I guess that's not terribly surprising, given that the port is already
assigned... so I'm guessing this IRQ needs to be manually assigned
during startup at some point, but I'm sure exactly how that should be
done.  Any ideas?

Thanks!
-David

---

