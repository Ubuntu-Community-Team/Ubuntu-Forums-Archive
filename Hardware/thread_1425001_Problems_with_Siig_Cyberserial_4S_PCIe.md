---
title: "Problems with Siig Cyberserial 4S PCIe"
date: 2010-03-08
forum: Hardware
---

### Post by jlamanna on 2010-03-08
Hi,
I'm running Hardy and just installed a Siig Cyberserial 4S PCIe 4-port serial card.
However, it doesn't seem as though the kernel is able to see it.
Here's the output of lspci -v:

01:00.0 Serial controller: Oxford Semiconductor Ltd Unknown device c208 (prog-if 06 [16950])
        Subsystem: Siig Inc Unknown device 2250
        Flags: fast devsel, IRQ 16
        Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
        Memory at fe600000 (32-bit, non-prefetchable) [size=2M]
        Memory at fe400000 (32-bit, non-prefetchable) [size=2M]
        Capabilities: [40] Power Management version 3
        Capabilities: [70] Express Endpoint IRQ 0
        Capabilities: [b0] MSI-X: Enable- Mask- TabSize=16

There's no mention in dmesg of the card at all either.
Does this PCIe card work with Linux at all?

Thanks.

-- James

---

