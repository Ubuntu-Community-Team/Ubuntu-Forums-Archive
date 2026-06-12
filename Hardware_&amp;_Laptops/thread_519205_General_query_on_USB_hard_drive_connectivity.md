---
title: "General query on USB hard drive connectivity"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by muzhogg on 2007-08-06
Hi all,

First, a confession; I'm in the process of migrating to Linux from WinXP - so the following query actually relates to hardware operating under WinXP not Ubuntu. However, I'm posting here believing the issue is hardware rather than software related and with the expectation that very soon I will have to deal with it under Ubuntu rather than under WinXP. So with that said...

I have a Memorex Ultra Traveldrive USB2.0 80GB which every now and then "disconnects" from my HP Pavilion DV2024TX. These disconnects are pretty much random - sometimes I get several in succession, but can then go hours without it happening. These disconnects never last more than a second or two before the system finds the drive again. That XP hardware-found "ding" is enough to drive a man mad...

I'm wondering if this is a power supply problem, but I'm not actually aware of how USB drives behave when the power supplied by the USB port is inadequate.

So my question is simply this; does anybody know if these symptoms are likely to be caused by inadequate power from a single USB port? Or is it likely to be a hardware malfunction (the drive is only two weeks old)?

I should point out that the drive did come with a second USB power supply cable and the documentation warns that it might be needed - so if it's simply that I have to use this cable then so be it, but I'd rather use the USB port for other things!

Thanks and regards,
MH

---

### Post by kidders on 2007-08-09
Hi there,

I'd say the only difference between Linux & Windows will be that Linux's system logs might at least *try* to give you some indication of what your USB disk is really up to. It would surprise me if the issue mysteriously went away once you installed Ubuntu.

Some suggestions:
[LIST]
[*]Depending on your local consumer rights legislation, you might want to double-check with your retailer that your disk isn't broken, before your right to a replacement expires. Perhaps your USB cable is faulty.
[*]If the problem turns out to be power-related, as you suspect, you should bear in mind that drawing too much power from a USB port can damage your motherboard ... if your disk has an external power supply, you really should use it.
[*]Sudden disconnection & reconnection of storage devices can cause filesystem corruption. Invariably, your luck will run out at some point, and you'll start losing data, so you should try to minimise the frequency of these momentary disappearances.[/LIST]I hope that's of some help. By the way, I wonder what would happen if you deleted the "ding" you mentioned. Hehe.

---

