---
title: "Driver for RS 422"
date: 2010-01-22
forum: Hardware
---

### Post by rocoat82 on 2010-01-22
Hello

I want to know what is the driver for working with a serial port 422 (RS-422/485 2 port, PCI adapter made by Quatech). **dmesg** only report RS 232 serial port.

**lspci** return:

> 03:0a.0 Multiport serial controller: Quatech Inc Device 01b1 (rev 01)

For serial port RS 232, to test this, i use **cat /dev/ttyS0** for reading messages, but for RS 422 what is the device?

I use Kubuntu Karmic koala with kernel 2.6.31-17.

Thanks

---

