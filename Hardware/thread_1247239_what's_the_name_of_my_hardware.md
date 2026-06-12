---
title: "what's the name of my hardware?"
date: 2009-08-22
forum: Hardware
---

### Post by PowerSource on 2009-08-22
my brother's resolution in ubuntu is much lower than in vista, and in the settings i can only lower it more, not raise it.
i read somewhere that i should check the proprietary drivers, but there was only drivers for the network card. now i thought that i could google the name of the graphics card, but i can't find the name of it. i don't want to go into vista to check it.
i tried lspci and hwcheck that i downloaded, but the results didn't say anything about a graphics card.
help?

---

### Post by oldfred on 2009-08-22
This gives the entire system:

```
sudo lshw
```

from my system( somewhere in the middle of entire list):

           *-display
                description: VGA compatible controller
                product: G94 [GeForce 9600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia

---

### Post by PowerSource on 2009-08-22
thanks!
i found the name of the card:
*-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
then i found this thread:
[http://ubuntuforums.org/showthread.php?t=615094](http://ubuntuforums.org/showthread.php?t=615094)
but that solves it only if i would be using 7.04 i think, it didn't work opening it in 9.04.
what am i gonna do :(

---

