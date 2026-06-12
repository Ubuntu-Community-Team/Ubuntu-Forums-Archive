---
title: "Windows driver with Linux"
date: 2008-11-15
forum: Hardware
---

### Post by dlublink on 2008-11-15
Hey,

I am trying to get a memory card reader to work on my laptop. There is no linux driver for it at this time.

I tried installing the windows driver for it using ndiswrapper and it says invalid driver. I guess the doc is serious when it says it is only for network devices.

Is there any other alternative to get this working?

I had a look at the unified kernel project, anyone try it out yet?

Thanks,

David

02:06.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
02:06.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
02:06.2 System peripheral [0880]: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator [1217:7110]
02:06.3 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]

---

### Post by Yezinki on 2008-11-15
Read linux23dragon's posts on web cam driver uodates & hard ware specs.........OR ask for his help.....it shall be resolved!

Good luck!

---

### Post by dlublink on 2008-11-16
Here is lspci -vnn

```
02:06.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
        Subsystem: Hewlett-Packard Company NC6000 laptop [103c:0890]
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
        Memory at 90100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=04, sec-latency=176
        Memory window 0: 34000000-37fff000 (prefetchable)
        Memory window 1: 38000000-3bfff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        16-bit legacy interface ports at 0001

02:06.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
        Subsystem: Hewlett-Packard Company NC6000 laptop [103c:0890]
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
        Memory at 90180000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 3c000000-3ffff000 (prefetchable)
        Memory window 1: 40000000-43fff000
        I/O window 0: 00001c00-00001cff
        I/O window 1: 00004000-000040ff
        16-bit legacy interface ports at 0001

02:06.2 System peripheral [0880]: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator [1217:7110]
        Subsystem: Hewlett-Packard Company NC6000 laptop [103c:0890]
        Flags: slow devsel, IRQ 10
        Memory at 90200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [a0] Power Management version 2

02:06.3 CardBus bridge [0607]: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller [1217:7223]
        Subsystem: Hewlett-Packard Company NC6000 laptop [103c:0890]
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
        Memory at 90280000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=09, subordinate=0c, sec-latency=176
        Memory window 0: 44000000-47fff000 (prefetchable)
        Memory window 1: 48000000-4bfff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001

```

---

### Post by dlublink on 2008-11-16
I also forgot to mentioned I am using 8.04 LTS, but I have a second partition with 8.10. 

I will try and upgrade to 8.10 and see if it resolves my issue.

David

---

### Post by Yezinki on 2008-11-16
Fresh install would be better than up grading....

Just my thoughts,

Regards,

Yezinki.

---

### Post by Skripka on 2008-11-16
FWIW-I have a USB 20-in-one card reader, that is autodetected in the BIOS-and works automagically in Ibex (and also did in Hardy)...of course that is a USB device, but just sayin'.

---

### Post by Yezinki on 2008-11-16
Oh thats a USB not built in.....plus yr machine's BIOS reads it.

How do you view any card's files system??

---

### Post by thavox on 2008-12-31
Hi! I have the same problem with the same hw. i.e. my card reader isn't working.


lshw gives this:
*-pcmcia:0
                description: CardBus bridge
                product: OZ711M1/MC1 4-in-1 MemoryCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
           *-pcmcia:1
                description: CardBus bridge
                product: OZ711M1/MC1 4-in-1 MemoryCardBus Controller
                vendor: O2 Micro, Inc.
                physical id: b.1
                bus info: pci@0000:02:0b.1
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
           *-system **UNCLAIMED**
                description: System peripheral
                product: OZ711Mx 4-in-1 MemoryCardBus Accelerator
                vendor: O2 Micro, Inc.
                physical id: b.2
                bus info: pci@0000:02:0b.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=64

My conclusion of "lshw" info:
The "4-in-1" card reader is a pcmcia-device and there is no driver installed. :(


Found any solutions or drivers?

---

### Post by thavox on 2009-03-03
Look at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/211095](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/211095) for info about this hardware.

---

