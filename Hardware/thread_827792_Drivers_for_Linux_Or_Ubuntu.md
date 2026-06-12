---
title: "Drivers for Linux Or Ubuntu"
date: 2008-06-13
forum: Hardware
---

### Post by Uchiha_madara on 2008-06-13
I have Laptop Toshiba Satellite L30-115

I need Website or method to Configure the PCI Device ,Sound card, and the modem

i typed this command and





> 
nightmare@nightmare-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

Then What is The Next Step
Or Give me Link To Download The Previous Drivers

I hope that My Question is clear, I asked this Question Before 
But I did not got any answer:KS

---

### Post by davidryderuk on 2008-06-13
Try following the instructions here for sound.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by housam on 2008-06-13
for the modem, use the [[COLOR="Red"]_scanModem_[/COLOR]]("http://132.68.73.235/linmodems/first.html") tool to identify the required driver for your modem and install/configure it.

---

