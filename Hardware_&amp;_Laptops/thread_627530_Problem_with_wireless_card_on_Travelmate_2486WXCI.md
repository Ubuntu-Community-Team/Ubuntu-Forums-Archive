---
title: "Problem with wireless card on Travelmate 2486WXCI"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by w1z4rd on 2007-11-30
So I installed kubuntu 7.10 GG onto my Acer Travelmate 2486WXCI (2480 series), and I have just about got everything sorted except my wireless card. I searched this forum and was unable to find a solution that suited my needs.

Most of the tutorials and advice dealing with teh TM2480 series of laptop seemed to deal with issues with the broadcom wireless card... but my laptop does not have the broadcom card it appears to have a wireless card called Atheros.

Apparently my wireless card is just meant to "work:".. but it doesnt. It seems like kubuntu picks up the card as I can see the driver for it "in use"... but for some reason, I get not wireless options in my network manager or when i type ifconfig. Here is a screenshot about what I am talking about:

[[IMG]http://img523.imageshack.us/img523/6804/wirelessissueqn2.th.png[/IMG]](http://img523.imageshack.us/my.php?image=wirelessissueqn2.png)

When I type lspci tjhe card comes up as an atheros card

```
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller

```

I really do not know what could be going on here so any suggestions would be most appretiated.

---

### Post by w1z4rd on 2008-01-23
bump

---

