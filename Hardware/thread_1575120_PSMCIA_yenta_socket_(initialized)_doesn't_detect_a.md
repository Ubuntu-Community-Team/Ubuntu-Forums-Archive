---
title: "PSMCIA yenta socket (initialized) doesn't detect any of PCMCIA cards in Xubuntu"
date: 2010-09-15
forum: Hardware
---

### Post by Joseph K on 2010-09-15
Hello,
I have a problem, I have old Toshiba laptop Satellite 2100 CDS and tried to put there Xubuntu (9.10). I've tried alternate installation, it didn't recognize my PCMCIA network card, which has Realtek Semiconductor RTL 8139 chipset, I know that, 'cause I have also second compaq laptop with Kubuntu, and this card works there fine - lspci show me this type of used driver (I mean now in Kubuntu).

I browsed a lot of forums and found kind of messages, that could be useful to install xubuntu from desktop cd, where network works fine, but I had same result - nothing, nothing with live CD, nothing after installation. 

It seems, that even if PCMCIA is installed - lspcmcia show me yenta_cardbus socket recognized - there's some bug, which causes, that PCMCIA slots in Xubuntu do not detect any of PCMCIA cards. I have also other PCMCIA wireless card - same result.

Do you have any idea, how to solve this?
Thank you

I've also tried Debian Lenny and networking worked fine, but there were other problems, so I've decided to try to solve this xubuntu problem.

---

### Post by Joseph K on 2010-09-15
Additional information: CardBus bridge: Toshiba American Info Systems ToPIC97 (rev 07)

---

