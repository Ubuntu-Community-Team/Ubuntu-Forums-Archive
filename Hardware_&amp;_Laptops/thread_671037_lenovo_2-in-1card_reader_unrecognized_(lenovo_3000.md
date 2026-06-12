---
title: "lenovo 2-in-1card reader unrecognized (lenovo 3000 N100)"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by boazarad on 2008-01-18
My Lenovo 3000 N100 came with a 2-in-1 card reader (Memory-Stick and xD card) and not the standard 5-in-1 card reader covered in the laptop testing page, and shipped with most models.

The card reader works fine in Vista (ugh!), but under Ubuntu (7.1) it doesn't seem to be recognized in any way - the status light doesn't even turn on when a card is inserted.

I've been googling around, and couldn't fine any proper references, not even here at the forums - at least not any that solved the problem...

Any ideas?

---

### Post by jerrykenny on 2008-01-18
Hi Boa,  its possible your card hasnt been integrated into the kernel yet . . . . . 

type dmesg in a terminal and see if theres any unrecognised hardware there.

Also type lshw in a terminal, this might give you more specific hardware information you can use to scour these forums with.

Also start the synaptic package manager, and try a few searches, eg for "lenovo" "thinkpad" "card reader" etc.

Quite possibly the next kernel update will take care of it for you.

---

### Post by boazarad on 2008-01-18
lshw gave me this:
>            *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:05:06.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:05:06.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:05:06.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.4
                bus info: pci@0000:05:06.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0

Looks like although there are only two card slots, some of the 5-in-1 card reader hardware is there. I don't quiet know what to make of the output though - any idea how to get these devices recognized?

---

