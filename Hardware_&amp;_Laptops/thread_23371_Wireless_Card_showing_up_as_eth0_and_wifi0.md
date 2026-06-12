---
title: "Wireless Card showing up as eth0 and wifi0"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by pruett57 on 2005-04-01
Okay, so I have a IBM TP R40 with the cisco aironet 802.11b card. Ubuntu found the card and installed a driver for it without any issues but it is showing up as both the eth0 and wifi0 cards?

any ideas why and how to clean this up?

---

### Post by alastair on 2005-04-01
No idea really, but an odd situation. You are sure that they both are the same device? Same MAC?

ifconfig -a

What does "/etc/network/interfaces" say.

What relevant messages for eth0 and wifi0 are in the /var/log/syslog file (for bootup)?

---

### Post by tomchuk on 2005-04-04
Totally normal. The airo driver uses eth for normal mode and wifi for monitor mode. For all intents and purposes it is safe to completly ignore the wifi0 interface when configuring your network settings. The only time you'll need it is when using kismet, where you will configure your card with the source "cisco_wifix,eth0:wifi0,sourcename".

---

