---
title: "Incorrect memory clock - Thinkpad T500"
date: 2009-02-23
forum: Hardware
---

### Post by Squid Spectre on 2009-02-23
I've been driving myself mad trying to figure this one out. I recently ordered and received a Lenovo Thinkpad T500. Most everything works flawlessly, but for some reason the memory clock and wireless card is wrong. The computer is supposed to have DDR3 memory and an Intel 5300 AGN card. However, when I run lshw this is what I get back:

```

*-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        ...
        ...
        ...
   *-network
                description: Wireless interface
                product: Wireless WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 00
                serial: 00:21:6a:12:a5:a0
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=10.1.1.78 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn             

```

From what I can figure out the wireless could be due to one of two things.
     1.)Lenovo sent me the wrong card, its been know n to happen
     2.)The wireless card is so similar to the 5300 that it could be a generalization of the hardware by the hardware probe. The only concrete difference is the 3x3 antenna array versues the 1x2. 
Its not a significant difference but could mean a theoretical difference of 50 Mbps in wireless N and arguable some stability of the connection...that and about 20 bucks.

However the RAM clock speeds are outright mind boggling. I've done some research, and only found some people are claiming that its simply a bad return value and the RAM really DOES run at DDR3 speeds, but I'm not entirely inclined to believe that. I ran memtest86+ on them and it was reporting a transfer rate of roughly 3500 mbps about that of DDR2-400. I finally opened the thing up and looked and sure enough both sticks claim to be DDR3-8500. Maybe I'm just misunderstanding something or perhaps theres some tragic bottleneck on the motherboard that clocks everything down. But please, I would be thrilled to have any explanation at all, I'm at wits end.

The only feasible solution I have is to *ugh* reinstall Vista and run PCMark05 to validate my findings. But I'd rather not invest the time and effort if I can prove it has the correct hardware in Ubuntu and use Vista as a desperate last effort.

Any input from other people or owner's of thinkpads?

---

