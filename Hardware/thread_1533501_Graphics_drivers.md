---
title: "Graphics drivers"
date: 2010-07-18
forum: Hardware
---

### Post by shookees on 2010-07-18
Hello,

recently I've been dealing problems with my graphic card drivers.

I have integrated **Nvidia GeForce 8200M G** in my laptop.

lshw says:
> 
*-display
                description: VGA compatible controller
                product: C79 [GeForce 9200M G]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: b1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:20 memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:f6000000-f7ffffff(prefetchable) ioport:dc00(size=128) memory:fafe0000-faffffff(prefetchable)

which seems strange, because it reckons it as GF 9200M G

The thing is, that when I install any of the 2 suggested driver (either **version 173** or  **version current**, which is recommended) I deal with severe problems. Both times when logged in I get a message that the screen config file couldn't be found(yet on **v173** it doesn't make any complications except this).

The big thing is, when I activate **version current**, after reboot my screen divided into 4 small screens.

If you need any more information, just ask away

---

