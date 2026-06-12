---
title: "ISA Creative sound blaster (16F) CT2940 on intrepid"
date: 2009-03-05
forum: Hardware
---

### Post by anystupidname on 2009-03-05
Hi, I'm running intrepid with LXDE and gnome on a relatively old box. (533mhz/384MB RAM) The problem is the ISA sound card my friend has to work with. It is a Creative CT2940 and I've tried using the following modules/drivers:
sb
snd-sb16
snd-sbawe
a couple others

I don't have any success. Further, the card doesn't even show up in lspci and lshw as far as I can tell. Am I missing something? There is an ISA NIC too, which is less important to get working but I'm curious as well. Any assistance would be much appreciated.

---

### Post by cariboo on 2009-03-05
Check the irq's they may be conflicting with something else:

```
cat /proc/interrupts
```

If there are any conflicts you may have to set the irq via jumpers on the card.

Jim

---

### Post by anystupidname on 2009-03-06
Thanks for the idea. I'd completely forgotten about IRQs.
On the downside, it doesn't look like there is a conflict as "soundblaster" is on 5 and nothing else is on 5. On the upside, I now have confirmation the card is actually "present" :) Any other ideas?

---

