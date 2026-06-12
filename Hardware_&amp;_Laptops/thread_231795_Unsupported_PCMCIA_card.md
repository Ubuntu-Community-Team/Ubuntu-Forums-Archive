---
title: "Unsupported PCMCIA card"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by jruschme on 2006-08-07
I have a slightly oddball wireless PC Card which I picked up from TigerDirect a few years ago. It is a variant of the Zcom XI-300, a PrismII-based 802.11b card which, when recognized, works nicely using the orinoco_cs driver.

The problem with this card is that it has a device-id different from the more normal XI-300 card and, as a result, is not normally in the list of supported devices.

Under hoary and breezy, I was able to get the card recognized by adding the following to /etc/pcmcia/config:

[INDENT]card "ZCOMAX XI-300 LAN/AP card"
  #version " ", "IEEE 802.11 Wireless LAN/AP Card"
  manfid 0xd601, 0x0003
  bind "orinoco_cs"[/INDENT]

Unfortunately, this does not work under dapper due, I assume, to the move to pcmciautils.

So, two questions:
[LIST=1]
[*]How can I make an equivalent configuration addition under dapper to have this card recognized?
[*]Does anyone know how I could submit this device to some upstream maintainer so that it will be supported OOTB by future releases?
[/LIST]

Thanks...
John

---

