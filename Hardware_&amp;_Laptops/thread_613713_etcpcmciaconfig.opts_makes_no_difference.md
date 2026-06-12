---
title: "/etc/pcmcia/config.opts makes no difference"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by dlublink on 2007-11-15
Hello,

I did this :

echo exclude irq 3 >> /etc/pcmcia/config.opts

I restarted my computer.

I did 

cat /proc/interrupt and saw:

3: 282 XT-PIC-XT pcmcia1.0 

If I remove the PCMCIA card, that line disappears.

Why is it using interrupt number 3 when I specifically said not to?

( the card is a 16 bit card). I believe that this behaviour may be causing my computer to have kernel panics , #95817 )

Thanks,

David

---

