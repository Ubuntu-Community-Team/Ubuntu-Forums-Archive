---
title: "Satellite A100 lspci -v output"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by rich wagner on 2007-02-10
Hey everybody...

I am having an issue with 6.10 detecting my Texas Instruments internal card reader. An lspci -v shows that there are multiple devices on my laptop that are <access denied>. One of which is the card reader. I have looked on the forums as well as the internet and found some site but none of them are working for me. Here is part of the output from lspci -v. I do believe my device is the 07:06:2. Here is my output:

07:06.0 CardBus bridge: Texas Instruments Unknown device 8039
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at dc007000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=07, secondary=08, subordinate=0b, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 52000000-53fff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001

07:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 169
        Memory at dc006000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

07:06.2 Mass storage controller: Texas Instruments Unknown device 803b
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 185
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

07:06.3 Class 0805: Texas Instruments Unknown device 803c (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 185
        Memory at dc006800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

07:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 66, IRQ 50
        Memory at dc005000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 4000 [size=64]
        Capabilities: [dc] Power Management version 2



I found a site that list the output of another a100 laptop as 07:06.02 as an Texas Instruments all in one card reader.

[http://lkcl.net/reports/toshiba.satellitepro.a100.html](http://lkcl.net/reports/toshiba.satellitepro.a100.html)
[http://lkcl.net/reports/toshiba.satellitepro.a100/lspci-v](http://lkcl.net/reports/toshiba.satellitepro.a100/lspci-v) ( see output below )


[B]07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, medium devsel, latency 128, IRQ 10
	Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2[/B]


Does anyone know how I can enable this?

I tried sudo modprobe tifm_sd 

dmesg shows this

[17179654.660000] tifm_7xx1: ms card detected in socket 0
[17179674.480000] tifm_7xx1: demand removing card from socket 0
[17179680.252000] tifm_7xx1: ms card detected in socket 0

any ideas?

---

