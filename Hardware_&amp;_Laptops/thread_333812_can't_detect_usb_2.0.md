---
title: "can't detect usb 2.0"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by Mba7eth on 2007-01-08
hi all , 
I have just install ubuntu .
yesterday i tried to copy a file of size 500 MB to my flash desk but it took around 10 minutes to finish !!!!!! although i'm using usb 2.0 ????????????? 
why ??? please help guys !!!!
this is the description of the hardware used from the kernal 
 *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:c0000000-c00003ff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s




Mba7eth

---

