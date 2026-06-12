---
title: "USB 3.0 card"
date: 2010-09-30
forum: Hardware
---

### Post by giddyup306 on 2010-09-30
Does anyone know of a USB 3.0 card that supports Linux?  I can't find one anywhere.  I tried to do a search, but it said...

```
Sorry - no matches. Please try some different terms.
```

---

### Post by cascade9 on 2010-09-30
I've got a USB30 controller chip on my motherboard, and it seems to run without a problem. I havent given it much in the way of testing (I dont own a single USB3.0 device to test with), but it hasnt had a problem with the USB2.0 sticks and media players I tried. 

Bit of the lshw readout- 

> *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation


I would guess that any PCIe NEC 720200 USB3./0 cad should work, though a quite search did help me find at least 1 that had a big 'NOT LINUX OR MAC COMPATIBLE" warning. But that could have more to do with not wantign to give support than any issues with the card under linux or mac :(

BTW, heres a link to a brand I've never heard of, but its the same baisc USB 3.0 controller chip, and does state that it will work with linux- 

[http://cgi.ebay.com/USB3-0-Card-PCI-Express-PCI-e-new-NEC-720200F1-chipset-/230531205703](http://cgi.ebay.com/USB3-0-Card-PCI-Express-PCI-e-new-NEC-720200F1-chipset-/230531205703)

---

### Post by hop5uk on 2010-09-30
I have this chipset on a card made by sabrent and i cannot get it to work either and lshw reveils
 *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:fdffe000-fdffffff

 Can anybody tell me if this is correct and if so how to proceed?

The link sent for ebay has the same chipset.I am assuming that it is this factor that dictates whether it is compatible or not

---

### Post by Virus666 on 2010-10-30
Which interface are you asking for?

If it is expresscard; **Vantec 2-Port SuperSpeed USB 3.0 ExpressCard 34** does the job...

[http://www.vantecusa.com/en/product/view_detail/407](http://www.vantecusa.com/en/product/view_detail/407)

---

