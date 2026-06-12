---
title: "Ubuntu Sound Problem"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by Squallio on 2007-05-22
I'm running a toshiba laptop, and my sound doesn't work..

I did a lpsci, here's the results..

I get an error when I try to open my volume control..

I did a lpsci and this is what I got:
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

I really don't want to be stuck with windows.. :(

---

### Post by Squallio on 2007-05-22
Anyone have any idea? :(

---

### Post by Najand on 2007-05-25
Right Click on Sound Icon, then, select "open volume control". 
Then Select "edit" -> "Preferences"
Check "External Amplifier" and close preferences window.
Then select "Switches" tab and uncheck "External Amplifier" and then close everything. 
You would have sound afterwards.

---

