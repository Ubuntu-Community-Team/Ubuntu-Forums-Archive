---
title: "Zonet PCMCIA Modem Locks System (Hangs)"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by trtech on 2007-09-12
Hello,

I've just bought a Zonet 56K V.92 PCMCIA Modem Card (ZFM5600CF). I used the same type of card with no trouble on my old laptop, which ran SuSE. This is a 100% hardware modem, not a winmodem, so it should work fine.

When I try to boot Ubuntu with the card inserted, the system hangs here

```
ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 16
pccard: PCMCIA card inserted into slot 0
cs: memory probe 0xff400000-0xffcfffff: excluding 0xff400000-0xff48fffff_
```

I noticed that about 17 lines up, there is the text:
```
Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
```

Also, if I boot without the card inserted, and then insert the card, the system completely locks up.

Is it possible that this is due to an IRQ conflict? What can be done about it?

Thanks,
Chris

---

