---
title: "Usbserial changes address"
date: 2010-02-25
forum: Hardware
---

### Post by MemorX on 2010-02-25
Hi,

I am having a problem with a usbserial device, when i address it, it is typically:

/dev/ttyUSB0

This works fine, but when I restart the address usually changes to:

/dev/ttyUSB1

And then back again, on next reboot. This causes a problem because I have to change the address each time.

Does anyone know why this is happening? And how to fix it?
I am using the Ubuntu desktop version.

Thanks.

---

### Post by MemorX on 2010-03-01
Noone has any idea?

---

### Post by nh7o_hi on 2010-03-15
I have the same thing happening here, with both 9.10 and 9.04.

Gateway ML6720 laptop, and a single USB to serial port converter.

If the port gets renamed to ttyUSB1, unplugging for ~1 min and plugging back in causes a change back to ttyUSB0.

---

### Post by nh7o_hi on 2010-09-29
This seems to be fixed in 10.04.

---

