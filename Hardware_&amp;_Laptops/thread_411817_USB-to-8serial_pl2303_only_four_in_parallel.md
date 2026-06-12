---
title: "USB-to-8serial pl2303 only four in parallel"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by mschw on 2007-04-17
Hi!

I have a 8-port USB-to-serial box with pl2303 chips.

It seems my 6.06LTS and 6.10 can only operate four of the eight serial ports concurrently.

All eight ports (/dev/ttyUSB0 thru ttyUSB7) work individually, but I need at least six ports in parallel (at 9600bps) for my application. I can grab any combination of four ports, then any next port I "int fd = open(...,O_RDWR|O_NOCTTY|O_NDELAY)" returns -1.

After open() I use tcgetattr()/tcsetattr() to set up the port (no xon/xoff, 9600-8N1, raw IO) for simple 9600bps tx/rx/gnd communication.

Is that (four ports at a time) a general limitation or need I change something?

---

### Post by mschw on 2007-04-17
I found out, that the limitation is the USB2.0 port mode or the ehci driver, which (in combination) has not enough resources to allocate an "urb" (found this out on linuxforen.de) - this has something to do with "transporting"an interrupt for each serial port, and the USB2.0 hubs.

I went to the BIOS setup and reduced the port setting to USB1.1 and now all six ports that I need can be allocated together (the ohci driver transports the urbs, in combination with the hubs being in 1.1 mode).

So, no more USB2.0 but only USB1.1 - but I have enough ports now

---

