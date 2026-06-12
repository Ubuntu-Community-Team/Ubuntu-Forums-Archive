---
title: "Can this usb to serial rs-232 cable work?"
date: 2014-04-18
forum: Hardware
---

### Post by lindsayward on 2014-04-18
Hi there.
I bought this cable: [http://www.ebay.com/itm/351031410604?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1497.l2649](http://www.ebay.com/itm/351031410604?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1497.l2649) to connect my computer to a serial device, but I do not see anything with it. I had previously borrowed a USB to serial adapter and it worked as ttyUSB0, but this one does not show up like that. I am thinking I bought the wrong thing now. 
Could I get this to work, or do I need to buy something else? Thank you.

---

### Post by lindsayward on 2014-04-21
Does anyone know? Thanks.

---

### Post by tripp98 on 2014-04-21
that looks to be a propitiatory cable for programming a controller.  [http://www.vigorplc.com.tw/eng/product.htm](http://www.vigorplc.com.tw/eng/product.htm)

it is a female serial connector.

most usb to serial are female.  i have tried a few different ones and they all show up as ttyusb0.  they all seam to pick up under Ubuntu.  Guessing you are in AU so here is a link to a few different ones.  Never used any of these sites to order but you can probably pick one up at local office store or computer warehouse.  

[http://www.shopbot.com.au/usb-to-serial/price/australia/477516](http://www.shopbot.com.au/usb-to-serial/price/australia/477516)

---

### Post by lindsayward on 2014-04-23
Thanks for the reply! I really surprised I didn't see what the cable was called when I bought it - but the ends are correct! 
When you say "most usb to serial are female", I assume that's a typo, because I'm having a hard time finding female ends - only male... I ordered a male one and will use a f-f gender changer or cable.

---

### Post by tgalati4 on 2014-04-23
Most USB-to-serial adapters have a microchip that performs a data translation.  A common chip is the PL2303 and it shows up when you open a terminal:

```
lsusb
```

If you plug in an adapter and it doesn't show up in *lsusb* (which stands for "list USB devices") then it will not work.  If it does show up with the *lsusb* command, it still may not work because some serial devices will only communicate with a real serial port from an older computer.  Serial ports are synchronous devices and USB are asynchronous devices (they are hot-swap, or interruptible).  Some equipment can't handle the small interrupts that happen with a USB-to-serial adapter.

---

### Post by Rentacarss on 2014-04-23
harika bir sayfa

---

