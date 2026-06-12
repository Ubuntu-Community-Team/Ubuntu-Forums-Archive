---
title: "About Net2280 PCI to USB 2.0 peripheral device controller"
date: 2008-10-28
forum: Hardware
---

### Post by anitemp on 2008-10-28
Hi,

I am planning to emulate a USB device on my PC and I came across PLX Net2280 PCI to USB 2.0 peripheral device controller which can be inserted into the PCI slot. On PLXTech's website the spec features of Net2280 include a PCI Bus and a USB device port along with other things. But the website also talks about Net2280EVB which is a PCI board on which the controller should be mounted on, in order to use it.

I have the following questions:

1. What are the hardware components that I need to order? Should I order just Net2280 controller or the PCI board as well?

Net2280REV1A-LF ([http://www.semiconductorstore.com/cart/pc/viewPrd.asp?idproduct=2073](http://www.semiconductorstore.com/cart/pc/viewPrd.asp?idproduct=2073))

and the PCI board - Net2280EVB ([http://www.plxtech.com/pdf/usb/2280EVB_Sales_Flyer.pdf](http://www.plxtech.com/pdf/usb/2280EVB_Sales_Flyer.pdf)).

2. Do I need to buy any additional software components apart from those supplied with Net2280 (for example the PLX-RDK mentioned on the website), if I am going to do the device emulation on Ubuntu? (ie. is the gadget API in <kernel_source>/drivers/usb/gadgets/ sufficient to do it?)

Thank you for looking into my post.

-anitemp

---

