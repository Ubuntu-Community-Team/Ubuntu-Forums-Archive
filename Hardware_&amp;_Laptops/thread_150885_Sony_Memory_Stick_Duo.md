---
title: "Sony Memory Stick Duo"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by zappa86 on 2006-03-26
Hi. I have a sony Vaio pcg-k23 and it has a memory stick duo reader build into it. When I stick in a memory stick nothing happens. I did a dmesg to see if anything happens and still nothing happens.  I looked in the dev directory and I dont see any extra hd or sd nodes when its in there. I did an LSPCI and here is my output:
```
ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device cbb2 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:00:0a.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:00:0a.3 Unknown mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 340M

```
If someone knows how to use a memory stick (perhaps I need to modprobe a module) please help me. Thanks

---

