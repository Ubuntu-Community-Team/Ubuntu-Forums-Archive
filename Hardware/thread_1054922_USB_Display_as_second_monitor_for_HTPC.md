---
title: "USB Display as second monitor for HTPC"
date: 2009-01-30
forum: Hardware
---

### Post by Bloemetjesgordijn on 2009-01-30
Hi guys,

I would like to buy a small USB display device as a second display. ([link]("http://www.slashgear.com/nanovision-mimo-um-710-um-730-usb-displays-review-2123771/"))

Does anyone know if this is supported by Ubuntu / Linux. 

According to the specs it has (some sort of OSx support / driver)

Thx in advance

Bloemetjesgordijn

---

### Post by jerhum on 2009-04-22
Hello

Up because i have the model um-710 but i don't found driver.
When i plugin i have this dmseg and the screen is on but black.
> usb 1-5: new high speed USB device using ehci_hcd and address 6
usb 1-5: configuration #1 chosen from 1 choice
generic-usb 0003:17E9:401A.0007: hiddev0,hidraw6: USB HID v1.10 Device [DisplayLink nanovision MiMo] on usb-0000:00:02.1-5/input1

---

### Post by number nine on 2009-05-15
DisplayLink just started an official Linux project today and there's some sourcecode available: [http://displaylink.org](http://displaylink.org). It's not a full driver yet but support for these devices should be coming soon!

The new DisplayLink library, libdlo, supports all USB 2.0 products based on DisplayLink. A complete list is here: [http://displaylink.com/shop](http://displaylink.com/shop).

---

