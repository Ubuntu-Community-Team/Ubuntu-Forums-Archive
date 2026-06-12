---
title: "PCMCIA issues on archaic laptop"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by Rijnzael on 2007-07-10
I'm currently attempting to get a new wireless card working on my archaic laptop.  The card is a Ubiquiti SRC CardBus, which has an Atheros chipset.  Whenever I insert the card, the kernel returns the notice "cs: pcmcia_socket1: unable to apply power."  It says the same thing when I place the card into the other socket, except that pcmcia_socket1 becomes pcmcia_socket0.  Subsequently, the device will not show up in lspci.  The card does function, however.  I have verified that the card is functional on one other laptop, using both Windows and the same Ubuntu DVD I used to install Feisty to my old laptop.  The PCMCIA slots also function; they both support an old 16-bit 56k modem card, as well as a relatively new Belkin Pre-N wireless card.

I'm currently using the server package from a 32-bit Ubuntu Feisty DVD.  uname -a returns "Linux ubuntu 2.6.20-15-server #2 SMP".  lspci returns the following information on the PCMCIA slots:

"00:0a.0 CardBus bridge: Cirrus Logic PD 6832 PCMCIA/CardBus Ctrlr (rev c1)"
"00:0a.1 CardBus bridge: Cirrus Logic PD 6832 PCMCIA/CardBus Ctrlr (rev c1)"

---

