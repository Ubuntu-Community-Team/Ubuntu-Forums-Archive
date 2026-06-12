---
title: "PCMCIA Ethernet Card on Thinkpad 770Z"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by xenonite on 2005-10-27
Hi, please help me installing the gigabit card on Ubuntu Breezy 5.10 on my Thinkpad 770Z.

This PCMCIA card has a RTL8169-Chip. In the dmesg output, it successfully loaded "r8169 Gigabit Ethernet driver 2.2LK"

In ifconfig -a, there it is identified with its correct hardware address. Status is "BROADCAST MULTICAST".

When I run "sudo ifup eth0" it tells me:
[INDENT]Ignoring unknown interface eth0=eth0[/INDENT]

regards,
xenonite

---

