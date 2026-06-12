---
title: "Ejecting a PCMCIA card - How?"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by albeano2004 on 2007-01-23
Forgive me if this has already been asked, but I am trying to work out how to safely remove my USB PCMCIA card from my laptop - a IBM Thinkpad T30. Is there a terminal command to do this? I ask only because I notice in the manual for the card, it says about ejecting it in XP. Do I really need to do this, or can I remove it safely without risk of damaging the card?

Thanks,
albeano2004

---

### Post by IntuitiveNipple on 2007-01-23
If its controlled by the pccardctl interface, then:
```
$ pccardctl eject <socket#>
```
Usually, if it isn't a memory card, you can just physically eject it. PCMCIA and CardBus, USB, IEEE-1394 are all designed for *hot-plugging* but flash memory devices need more care to ensure all data has been written before ejecting them.

---

### Post by albeano2004 on 2007-01-23
Great, thanks for that! I will give it a try tonight when I get home from work.

Cheers,
albeano2004

---

