---
title: "3rd and 4th serial port not configured on startup"
date: 2013-04-10
forum: Hardware
---

### Post by MrRadiotron on 2013-04-10
Ubuntu 12.04.2 LTS 3.2.0-39-generic-pae

Hi there, the PC I'm working on has 4 serial ports.

ttyS0 and ttyS1 function properly straight from startup,

ttyS2 and ttyS3 do not.

here is the relevant dmesg messages:

```

Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.050346] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.100595] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.144567] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    1.188577] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[    1.383941] isapnp: No Plug & Play device found
[    1.449179] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.477192] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.498296] 00:08: ttyS2 at I/O 0x3e8 (irq = 7) is a 16550A
[    1.524994] 00:09: ttyS3 at I/O 0x2e8 (irq = 7) is a 16550A

```

to get them to function I have to re-configure them by invoking:

```
setserial /dev/ttyS3 baud_base 115200 auto_irq skip_test autoconfig
```

which I found here

Before re-configuring the serial port, setserial reports the following for the serial ports:

```
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: 16550A, Port: 0x03e8, IRQ: 7
/dev/ttyS3, UART: 16550A, Port: 0x02e8, IRQ: 7
```

After re-configuring the fllowing is reported:

```
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: 16550A, Port: 0x03e8, IRQ: 0
/dev/ttyS3, UART: 16550A, Port: 0x02e8, IRQ: 0
```

The serial ports are provided by a fintek f81866 chip which supports IRQ shareing so having the initial IRQs set to 7 should not be a problem. while having the IRQs set to 0 is a problem from what I understand as according to the setserial man page IRQ 0 is reserved for Timer channel 0.

The fintek f81866 chip supports up to 6 serial ports.

So I tried adding 8250.nr_uarts=8 to the bootline but, this did nothing (as far as I know, I don't know of a way to confirm what boot parameters have been passed).

Whats is going wrong?
Why isn't ttyS2 and ttyS3 being configured correctly at startup?

How can I fix this?
What would I need to do so that they are configured correctly at startup (short of making my own init script)?

Thanks in advance!

---

