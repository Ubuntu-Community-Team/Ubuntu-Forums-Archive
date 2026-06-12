---
title: "[PCMCIA] Firewire Mobile card won't work"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by ranpha on 2007-03-06
[18037877.284000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[24004000-240047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[18037877.288000] eth1394: eth1: IEEE-1394 IPv4 over 1394 Ethernet (fw-host0)
[18037878.560000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009007010100000f]
[18037985.980000] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0000FFC0
[18038045.608000] ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0000FFC0

Above is my dmesg \ grep 1394 output. The card works fine but when i connect a HDD to it i get the two last errors. Can anybody help me with this?

Also if firewire doesn't work will this error also happen with a Sitecom USB 2.0 PCMCIA card? If so what other PCMCIA USB 2.0 card should i buy then.

My laptop is a THINKPAD R31 running Ubuntu 6.10 and the card is a FW-005 Sitecom Firewire Mobile Kit.

---

