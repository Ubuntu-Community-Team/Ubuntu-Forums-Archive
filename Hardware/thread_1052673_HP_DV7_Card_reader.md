---
title: "HP DV7 Card reader"
date: 2009-01-28
forum: Hardware
---

### Post by maddix on 2009-01-28
I bought HP DV7 -1135nr laptop(few month ago), after playing with different Ubuntu systems, I've install Ubuntu 8.04 as most working out of box.
But I have card reader in my laptop, and card reader doesn't work.
Here is lspci:
> 
08:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
08:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
08:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
08:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384


Does anybody has success on that? I read a lot of threards about DV7 here and didn't found solution of my problem.

---

### Post by PenquinCoder on 2009-12-02
I have the the HP DV7 3060US, and I cannot get the MMC card reader working.
Also, when I plug in a USB thumb drive, it is registered in nautilus as 'SD/MMC reader' but will not mount, or allow me to open it.

Ubuntu Karmic (9.10) X86_64
HP DV7 3060us

lshw
> 
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f2407000-f2407fff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f2406000-f2406fff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f2408500-f24085ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f2405000-f2405fff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f2404000-f2404fff



lspci
> 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller


---

### Post by PenquinCoder on 2009-12-13
Is there seriously no answer for this??? 

I've been trying for the past week attempting to get a fix working for the SD reader for this laptop, and still no such luck. I cannot be the only user who has experienced this issue, as even the posts above mine state they are seeing it as well. 

Anyone recently found information on getting the device to work as properly intended?

---

### Post by IcarusR on 2009-12-14
Probably simpler to buy a usb card reader, they are cheap.

---

