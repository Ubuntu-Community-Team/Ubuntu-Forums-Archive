---
title: "Hardy compatible PCMCIA Wifi card?"
date: 2008-07-26
forum: Hardware
---

### Post by lambdacore on 2008-07-26
Do you know any?

I have a Linksys WPC54G v5 and since I installed Hardy, I can't connect to any wireless network, even though I see them.
It is annoying. And it was not totally compatible in the first place, since I have to install the drivers with ndiswrapper (but at least it did work on Gutsy).

So do you know any PCMCIA wifi card that has no problem with Hardy? That works straight away, or at least works at all?

I need to use a PCMCIA because I have a crappy Acer Aspire 3050 and there is no way to make the wifi work with it.

Thanks :D

---

### Post by Dark_Stang on 2008-07-26
I'm just curious. Post the output of "lspci" so I can see what type of internal wireless card you've got. And for compatibility, this is the only list I could find.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by lambdacore on 2008-07-26
Here goes the lspci : 
root@lambda-core:/media/event/inf# lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
root@lambda-core:/media/event/inf# 


The internal is something like Atheros blablabla. It never worked on Ubuntu. I've seen many threads about it and it seem that well, it does not work.

And thanks a lot for the link!
That's pretty much exactly what I was looking for.
:D

---

### Post by Dark_Stang on 2008-07-26
Check out the 6th post in this thread.

[http://ubuntuforums.org/showthread.php?t=766529&highlight=ar5007](http://ubuntuforums.org/showthread.php?t=766529&highlight=ar5007)

---

### Post by lambdacore on 2008-07-26
Oh wow.
Bookmarked.
If only I had had this before ahah.
But I'm afraid that recently, my Atheros broke because it used to work on my Windows partition and now it's not working there either.

But thanks a lot, you're some kind of a god.

---

### Post by Dark_Stang on 2008-07-26
> **lambdacore said:**
> But thanks a lot, you're some kind of a **nerd**.
Fixed it for you...

---

