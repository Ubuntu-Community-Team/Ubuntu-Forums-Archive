---
title: "mount/recognize memory stick on vaio k115s"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by th0mas on 2006-07-01
Hello,

As I bought a Sony camera recently, i'd like to have my Memory Stick Pro slot working with Dapper. I have a vaio pcg-k115s.

First, i was wondering if the "card" (dunno if it's considered as pci/ide/scsi device) is recognized by my system. I don't see anything related with it in my lspci but i'm not sure at all. Someone can tell me more about it ?

```

$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:00:0a.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:00:0a.3 Mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)

```

Q: 
- Then if it's not detected, how do you think i could install it ? (recompiling kernel with scsi support i heard ?)
- If it's already recognized, are there any "modprobe" to type ?

T H A N K S !

(PS: under windows XP, it's recognized as MemoryStick or MemoryStickPro Device)

---

### Post by Max Luebbe on 2006-07-01
I've wanted to have this support on my fs series for a long time, but haven't had time to figure it out.

I'll start looking. If you find any information that could help, post it.

---

