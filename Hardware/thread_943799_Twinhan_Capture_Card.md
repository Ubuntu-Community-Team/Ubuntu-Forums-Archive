---
title: "Twinhan Capture Card"
date: 2008-10-10
forum: Hardware
---

### Post by AgentX9 on 2008-10-10
I have now tried for several weeks to get my cature card to work, without sucess.

when I do dmesg, I get the following:
bttv: driver version 0.9.17 loaded
[   36.510137] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   36.510199] bttv: Bt8xx card found (0).
[   36.510233] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 21 (level, low) -> IRQ 21
[   36.510245] bttv0: Bt878 (rev 17) at 0000:03:06.0, irq: 21, latency: 64, mmio: 0xfddff000
[   36.510647] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[   36.510650] bttv0: using: Twinhan DST + clones [card=113,autodetected]
[   36.510670] bttv0: gpio: en=00000000, out=00000000 in=00f500fd [init]
[   36.510701] bttv0: tuner absent
[   36.510715] bttv0: add subdevice "dvb0"

When I set up the backend the card is not present.

I'm completely new to this. What to do?

anybody?

---

