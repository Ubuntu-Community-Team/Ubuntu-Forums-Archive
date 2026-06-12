---
title: "PCMCIA card reader"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by hannaman on 2007-02-11
I bought a cheap pcmcia multimedia card reader for my laptop.  When I install an SD card into the reader, I get the following message in dmesg:
> 
[17180081.832000] pccard: PCMCIA card inserted into slot 1
[17180081.832000] pcmcia: registering new device pcmcia1.0
[17180081.920000] ata2: PATA max PIO0 cmd 0x4040 ctl 0x404E bmdma 0x0 irq 3
[17180082.100000] ata2: dev 0 failed to IDENTIFY (INIT_DEV_PARAMS failed)
[17180082.100000] scsi1 : pata_pcmcia

The output of lspci -v concerning the card looks like this:
> 
02:00.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 5
        Memory at e8108000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 34000000-35fff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at e8109000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 32000000-33fff000 (prefetchable)
        Memory window 1: 36000000-37fff000
        I/O window 0: 00004c00-00004cff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

I have tried using setpci -s and I have also tried using the modprobe for the TI card readers, even though I don't a TI card reader.  What is perplexing me is that when I insert and SD card in the reader, it looks as if a pcmcia card is inserted.  I know the chance of this card being supported is slim, but I thought I would see if anyone had any ideas.

Thanks

---

