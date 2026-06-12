---
title: "Unwanted serial port I/O during boot"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by krix on 2007-10-01
When my PC boots it seems to send the character ```
0x7f
```  on the serial port. Unfortunately I have a serial device attached that is quite sensible to commands it does not understand, so this device will go into an error state, when my PC boots.

Does anyone know how I can avoid Ubuntu sending anything on the serial port during boot?
Does Ubuntu do any hardware probing, that  I should disable?

The output to the serial device is sent right after I see this message on the screen:
> Uncompressing linux .. OK, booting kernel

I run Ubuntu 6.04 server editiion.

Thanks.
Kristian

---

