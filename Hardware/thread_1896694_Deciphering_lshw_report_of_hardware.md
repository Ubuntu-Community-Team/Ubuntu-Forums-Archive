---
title: "Deciphering lshw report of hardware"
date: 2011-12-17
forum: Hardware
---

### Post by Chizzleface on 2011-12-17
Hi!

I'm looking to get a new graphics card to upgrade my PC a little bit, but am slightly confused as to what slots I have available. A visual check doesn't help me out as it could be either standard PCI or PCIe x8 that I have available. And looking at the lshw report isn't helping me out in terms of identifying them! Can anyone give me a little hint as to what expansion slot I have available going off the lshw report?

```
*-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:8000(size=4096) memory:40d00000-40efffff ioport:40f00000(size=2097152)
*-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:7000(size=4096) memory:40900000-40afffff ioport:40b00000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:6000(size=4096) memory:40500000-406fffff ioport:40700000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:40100000-402fffff ioport:40300000(size=2097152)

```

Cheers!

---

### Post by MoreOrLess on 2011-12-17
You have PCI express (PCI-e). See this for the slot pics: [https://en.wikipedia.org/wiki/PCI_Express#Form_factors](https://en.wikipedia.org/wiki/PCI_Express#Form_factors)

Most likely, you can use any PCI-e x16 graphics card.

---

### Post by Chizzleface on 2011-12-17
> **MoreOrLess said:**
> You have PCI express (PCI-e). See this for the slot pics: [https://en.wikipedia.org/wiki/PCI_Express#Form_factors](https://en.wikipedia.org/wiki/PCI_Express#Form_factors)

Most likely, you can use any PCI-e x16 graphics card.

The thing is, I know I have one PCIe x1 slot on the mobo, but the other slots are puzzling me because they look like PCI, yet whenever I try to search for what a PCIe x8 looks like, I can only see ones that look just like PCI! It's dead annoying, because it means I can't find the right graphics card, or at least one with decent clock speed :(

I think I may have found my answer, the slots look like plain old PCI and from what I can see, they can't be express. The split on the slot is at the wrong end, it's at the far end, away from the edge of the mobo. 

Ah darnit, looks like I'll need to splooge out on a new mobo and all the assorted gubbins that goes with it :(

---

### Post by MoreOrLess on 2011-12-17
I guess you could have an AGP slot as well, if you have a slot that doesn't look like PCI or PCI-e.

---

### Post by Chizzleface on 2011-12-18
Nah, they're definitely conventional PCI. I took it down to PC World to confirm it. There's a PCI-e X1 slot on there but there's no decent graphics card for either slot any more so I'm going to be getting a new mobo. Shame really, the CPU is still quite powerful at 3gHz with hyper-threading - but I can probably get a good quad-core mobo and CPU for less than £100 these days.

---

### Post by MoreOrLess on 2011-12-18
Yeah, OEM's do that. Some bean counter cut production costs, but s/he screwed the customers' upgrade options.

---

