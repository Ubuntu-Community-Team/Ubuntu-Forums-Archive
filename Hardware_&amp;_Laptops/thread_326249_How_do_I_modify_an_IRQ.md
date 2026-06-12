---
title: "How do I modify an IRQ?"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by Nonno Bassotto on 2006-12-27
It seems that I'm not able to use my infrared port because of an irq conflict. Is there a way to manually assign an irq to that port?

---

### Post by az on 2006-12-27
> **Nonno Bassotto said:**
> It seems that I'm not able to use my infrared port because of an irq conflict. Is there a way to manually assign an irq to that port?

Can you change that in your BIOS configuration?  Sometimes it's called Setup or Cmos when you boot...

---

### Post by patrickfromspain on 2006-12-27
maybe you could try booting using the irqpoll option and see if helps..

---

### Post by Nonno Bassotto on 2006-12-28
There's no option in the BIOS to assign IRQs. Actually I was thinking that it should be something Os-related. I once saw that you can modify the IRQ of your PCMCIA changing a line in I don't remember what file, and I thought something similar could be done for the infrared port.

@patrickfromspain: can you explain better what you mean? Should I add that option in the grub configuration file?

---

