---
title: "What does dual channel ultra DMA do?"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by oldcpu on 2007-06-06
Under chipset of the motherboard, it reads:

> Dual Channel Ultra DMA 33/66/100/133 master mode EIDE controller.

What does that do?

---

### Post by spd106 on 2007-06-07
I believe this means there are two UDMA ATA connectors on the motherboard.

Which allows you to have up to four ATA devices connected. Two on each channel, one master, one slave or both cable select if the devices support it. The devices on a channel share the bandwidth, so if you have only two devices it's usually better to give them a channel each.

As the industry moves to SATA, the older ATA connector will be phased out. So more and more motherboards will only have one ATA channel or like some of the new Intel boards, none at all.

If you want to know more about UDMA, try looking through wikipedia.

---

