---
title: "I think my PCMCIA slots are being ignored"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by mohapi on 2006-01-31
At first I thought I was having problems with my cardbus slots, but they work fine under Windows. For some reason Ubuntu won't acknowledge anything in there, even though they show up under the Device Manager and in an *lspci* command (as Texas Instruments PCI 1131 slots).

Any suggestions? I have two working wireless cards and neither of them gets even so much as a nod from Ubuntu. Is there some way to probe those ports and force Ubuntu to admit them?

---

### Post by davinci on 2006-01-31
maybe your wlan chipset is not supported? what is the output of lspci -v?

I have been wasting some days to get a realtek 8185l wlan card to work. no success ... 

the atheros card i bought thereafter was up and running in 15 mins ....

---

### Post by mohapi on 2006-02-01
Here's an *lspci -v*. ...

```
0000:00:00.0 Host bridge: Intel Corp. 430TX - 82439TX MTXC (rev 01)
	Flags: bus master, medium devsel, latency 32

0000:00:01.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
	Flags: bus master, medium devsel, latency 0

0000:00:01.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 32
	I/O ports at 3000 [size=16]

0000:00:01.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 1040 [size=32]

0000:00:01.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
	Flags: medium devsel, IRQ 9

0000:00:08.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01) (prog-if 00 [VGA])
	Flags: bus master, medium devsel, latency 0
	Memory at c0000000 (32-bit, prefetchable) [size=16M]
	Memory at c1000000 (32-bit, non-prefetchable) [size=2M]
	Memory at c1200000 (32-bit, non-prefetchable) [size=1M]

0000:00:0a.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Flags: bus master, medium devsel, latency 168, IRQ 9
	Memory at 08000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
	Memory window 0: 08400000-087ff000 (prefetchable)
	Memory window 1: 08800000-08bff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001

0000:00:0a.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
	Flags: bus master, medium devsel, latency 168, IRQ 9
	Memory at 08001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 08c00000-08fff000 (prefetchable)
	Memory window 1: 09000000-093ff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	16-bit legacy interface ports at 0001

```
That's with the card in there. As I understand it, I should be able to see some output from the card (it's a Belkin F5D7010 version 5, which I believe should work straight out of the box).

I should note that a plain CF card adapter does not show either, but does work perfectly on my M170.

Any suggestions?

(edited because I managed to confuse myself with what I had written, and thought it better not to confuse anyone else)

---

