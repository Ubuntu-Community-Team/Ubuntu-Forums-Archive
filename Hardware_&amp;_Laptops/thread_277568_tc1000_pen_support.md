---
title: "tc1000 pen support"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by nodows on 2006-10-14
I'm trying to get the stylus on my compaq tc1000 to work in ubuntu.  

I've downloaded the fpi2002 driver and compiled it, then busted a modprobe on it. As I understand it, its supposed to turn on the pen interface through a serial port, /dev/ttys0 specifically.  But I keep gettin an input/output error on the serial device.   Here's what I've done

> /$ sudo modprobe fpi2002
/$ sudo setserial /dev/ttys0 autoconfig

which produces this output:

> /dev/ttys0: Input/output error

I've tried a number of other paramenters such as "skip_test" in the setserial dialogue but nothing has been very fruitful.  Oddly once I recieved the

> /dev/ttyS0, UART: unknown, Port: 0×03f8, IRQ: 4 

which was a good start, all I needed is a UART of 16550A at that point, but I couldn't replicate it and I recived the input/output error ever since.  Any ideas anyone?

---

### Post by glennph93 on 2006-11-01
I had the same problem setting my serial port and it came down to a typo. Make sure you use a Capitol S in /dev/ttyS0.

---

