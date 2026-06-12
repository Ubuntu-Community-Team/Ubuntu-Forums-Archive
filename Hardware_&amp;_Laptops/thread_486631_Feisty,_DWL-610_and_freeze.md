---
title: "Feisty, DWL-610 and freeze"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by Vitello on 2007-06-28
I have a D-Link DWL-610 pcmcia wireless card and I have a freeze problem with Feisty. With Dapper and Edgy I never had a problem....

I have configred my card with ndiswrapper and as you can see below is succesfully recognized but...when i try to connect my card with my wireless network my notebook completly freeze.

What can i do?

Thx
Vitello


[dmesg]

[19910.164000] pccard: CardBus card inserted into slot 0
[19910.392000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[19910.560000] ndiswrapper: driver netdlwl (D-Link,05/23/2003,5.140.0523.2003) loaded
[19910.560000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[19910.560000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[19910.564000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[19910.632000] ndiswrapper: using IRQ 11
[19911.196000] wlan0: ethernet device 00:05:5d:9e:36:15 using NDIS driver: netdlwl, version: 0x100, NDIS version: 0x500, vendor: 'D-Link Air Wireless LAN Adapter                                                 ', 1186:3300.5.conf
[19911.196000] wlan0: encryption modes supported: WEP
[19911.196000] usbcore: registered new interface driver ndiswrapper

---

### Post by Mr.Auer on 2007-12-23
Seems its a problem with DWL-610. Youre not alone, but we dont seem to know how to fix it :)
Look here:
[http://ubuntuforums.org/showthread.php?p=4002301#post4002301](http://ubuntuforums.org/showthread.php?p=4002301#post4002301)
[http://ubuntuforums.org/showthread.php?t=590258&highlight=dwl+610](http://ubuntuforums.org/showthread.php?t=590258&highlight=dwl+610)

---

