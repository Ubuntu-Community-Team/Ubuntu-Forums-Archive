---
title: "serial port not recognized"
date: 2012-09-06
forum: Hardware
---

### Post by barna on 2012-09-06
Hi,
I have installed an Applied Micro Circuits RS232 card after installing Ubuntu. The card is not recognized. It is reported like this by lshw

```

       *-generic UNCLAIMED
                description: Non-VGA unclassified device
                product: Applied Micro Circuits Corp.
                vendor: Applied Micro Circuits Corp.
                physical id: 1
                bus info: pci@0000:07:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: latency=32 maxlatency=1
                resources: ioport:1000(size=64) ioport:1060(size=32) ioport:1040(size=32)


```

lspci outputs this:
```

07:01.0 Non-VGA unclassified device: Applied Micro Circuits Corp. Device 801d

```

What should I check, what should I do so that Ubuntu recognized this card?
Thank you
Daniel

---

### Post by barna on 2012-09-06
The attached snapshot maybe helps, it is from KInfoCenter
Thanks

---

