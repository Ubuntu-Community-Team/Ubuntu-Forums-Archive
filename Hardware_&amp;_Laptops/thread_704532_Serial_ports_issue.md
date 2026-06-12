---
title: "Serial ports issue"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by choffman on 2008-02-22
I'm having a issue with configuring and connecting devices to serial ports.  I have a total of 4 serial ports.

running setserial -g /dev/ttyS*

/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: 16550A, Port: 0x0a80, IRQ: 10
/dev/ttyS3, UART: 16550A, Port: 0x0a88, IRQ: 11

However when I try to connect any device to the serial port I don't get a response when I send something to it.

If I change the IRQ to 0 then I do get responses but not always what I expect.

I've tried all 4 ports and I have the same behavior on all 4.

I've successfully connected a USB to Serial port converter and connected the device to it and it appears to work

Anyone have any ideas to try?

---

