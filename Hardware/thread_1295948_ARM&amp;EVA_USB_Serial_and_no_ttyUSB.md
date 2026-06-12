---
title: "ARM&amp;EVA USB Serial and no ttyUSB"
date: 2009-10-20
forum: Hardware
---

### Post by dentharg on 2009-10-20
Hi!

I'm trying to connect the Conitec ARM&EVA AT91 board, however plugging its usb does not create necessary /dev/ttyUSB0.

I've tried to load usbserial kernel module both without and with vendor=0x03eb product=0x6120 parameters.

If I load this module with parameters I get:
```
[ 1272.552321] usbserial_generic 7-2:1.0: Generic device with no bulk out, not allowed.                                    
[ 1272.552328] usbserial_generic: probe of 7-2:1.0 failed with error -5

```

Creating nodes by hand with
```
mknod /dev/ttyUSB0 c 188 0
```
does not help.

Riding latest beta of Karmic with kernel 2.6.31.4.

Thanks!

---

