---
title: "PCMCIA Firewire card?"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by cgbier on 2007-03-26
Does anyone know a Firewire card working with LINUX?

Should be OHCI compatible for DV.

TIA

---

### Post by 23meg on 2007-03-26
My Billionton CB1394T card works without a problem. It has a Texas Instruments chipset; there's a similar product with a VIA chipset which may not be OHCI compatible and may not work with Linux; make sure you look for the exact model.

---

### Post by doyen on 2007-04-05
Hi,
I was wondering how did you get the pcmcia card mounted.
I have an st lab 1394A pcmcia adaptor card.. it has 2 usb 2.0 and two firewires.
I have attached a usb stick at the end but I do not know what I meant to do to
mount them.

If I do lspci 
07:00.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
07:00.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
07:00.4 FireWire (IEEE 1394): ALi Corporation M5253 P1394 OHCI 1.1 Controller

but I can't find the usb stick.. if I attach the stick on the usb ports of the IBM T42, (Kubuntu 6.10) they are automatically mounted under /media

Any ideas?

Cheers,
Aldo

---

