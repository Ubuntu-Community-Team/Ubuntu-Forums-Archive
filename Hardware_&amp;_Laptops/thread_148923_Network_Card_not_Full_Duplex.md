---
title: "Network Card not Full Duplex"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by Apreche on 2006-03-22
I have a very small home network. The most imporant part is this switch which most of the computers are connected to. It autonegotiates with the NICs to determine if it should be 10 or 100 and half or full duplex. If it is full duplex an orange light turns on for that port on the switch.

We have one PC in the living room hooked up to the TV. More the past many months this PC ran Gentoo and the orange light indicating full duplex was always on. I recently rebuilt this machine as an Ubuntu box. No hardware was changed. Now the full duplex light is no longer illuminated. I attempted to use ethtool to force full duplex, but it didn't work. No matter what command I give ethtool I get a message saying "Operation not supported".  

FYI lspci has this to say about the card

0000:00:0b.0 Ethernet controller: Lite-On Communications Inc LNE100TX [Linksys EtherFast 10/100] (rev 25)

And ethtool -i has this to say

driver: tulip
version: 1.1.13
firmware-version:
bus-info: 0000:00:0b.0

what to do?

---

### Post by ewoox on 2006-05-02
try mii-tool, it helped me. but maybe there is some drivers issue

---

