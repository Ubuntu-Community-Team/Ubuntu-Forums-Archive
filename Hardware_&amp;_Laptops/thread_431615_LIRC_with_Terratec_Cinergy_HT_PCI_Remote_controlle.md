---
title: "LIRC with Terratec Cinergy HT PCI Remote controller"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by the_mechanical on 2007-05-03
I tried several things but it was not possible for me to get my remote controller (RC) running with lirc wich was shipped  with the TV-Card.
It was included a USB-Infrared device (i don't know why because the card has a connector for IR).
lsusb says:
```
Bus 002 Device 002: ID 0419:0001 Samsung Info. Systems America, Inc. IrDA Remote Controller
```
In the remote controller is the following chip implemented: CY7C63001A-SC ([http://www.cypress.com](http://www.cypress.com))

I didn't find this RC or the chip in the LIRC database.

Can anybody help me?

---

### Post by the_mechanical on 2007-09-19
And now the same question for Gutsy.

---

### Post by rsched on 2007-12-11
> **the_mechanical said:**
> I tried several things but it was not possible for me to get my remote controller (RC) running with lirc wich was shipped  with the TV-Card.
It was included a USB-Infrared device (i don't know why because the card has a connector for IR).
lsusb says:
```
Bus 002 Device 002: ID 0419:0001 Samsung Info. Systems America, Inc. IrDA Remote Controller
```
In the remote controller is the following chip implemented: CY7C63001A-SC ([http://www.cypress.com](http://www.cypress.com))

I didn't find this RC or the chip in the LIRC database.

Can anybody help me?

The problem is that the USB device uses an array of 48 bits in one of the HID report descriptors. This should be compliant to the USB hid standard. But Linux as of now only supports fields up to 32 bit (you can see this when you enable HID debug messages).

In the end, I have got all keys of the remote working with LIRC. However, I needed to patch the Linux kernel to map the 48bit array into, for instance, two 24 bit arrays (hid-quirks.c). Additionally, the devinput module had to be extended to support 32 bits.

I have to check whether it is realistic to get the Linux kernel extended. Actually, it is not a device quirk, but only a workaround to the USB HID driver which supports fields up to 32 bit. The clean solution IMHO would be an extended USB HID driver. But short-term this seems unrealistic to me, due to a change of the userspace interface.

Regards,
Robert

---

