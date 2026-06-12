---
title: "wireless card not detected on acer laptop"
date: 2008-06-20
forum: Hardware
---

### Post by Couchless on 2008-06-20
Hi Everybody. 

I am a newbee on using unbuntu. I like it but when something isn't working right away I get lost. 
I have a new laptop : Acer Aspire 5720Z-3A3G16Mi
with a wireless card: Broadcom Corporation 802.11g Giga bit.

It is not working when I have installed ubuntu 8.04 (Hardy). I tried all the Terminal commands described in the troubleshoot section but it seems that is doesn't recognize the wireless card at all. No output or anything.

Does somebody knows this problem?

---

### Post by ukripper on 2008-06-20
> **Couchless said:**
> Hi Everybody. 

I am a newbee on using unbuntu. I like it but when something isn't working right away I get lost. 
I have a new laptop : Acer Aspire 5720Z-3A3G16Mi
with a wireless card: Broadcom Corporation 802.11g Giga bit.

It is not working when I have installed ubuntu 8.04 (Hardy). I tried all the Terminal commands described in the troubleshoot section but it seems that is doesn't recognize the wireless card at all. No output or anything.

Does somebody knows this problem?

Can you post output of the following:
```
lspci
```

```
iwconfig
```

```
iwlist scan
```

---

### Post by DaddyUnit on 2008-06-20
I'm not the original poster but I have the same problem with a reconditioned Acer Aspire 4520 that I pulled out of the box and loaded Hardy on last night.

lspci = 07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

iwconfig = 
llo no wireless extensions.
eth0 no wireless extensions.

iwlist scan
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.

Any help would be appreciated...thanks.

---

### Post by ukripper on 2008-06-20
> **DaddyUnit said:**
> I'm not the original poster but I have the same problem with a reconditioned Acer Aspire 4520 that I pulled out of the box and loaded Hardy on last night.

lspci = 07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

iwconfig = 
llo no wireless extensions.
eth0 no wireless extensions.

iwlist scan
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.

Any help would be appreciated...thanks.

your card is detected but there are no drivers installed for it.
Use this howto- [http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)
it is same chipset AR242x as yours

here is simple guide - [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

---

### Post by DaddyUnit on 2008-06-21
Thanks very much for your reply. I took a look at the links and even started on the instructions found at one of them, but I'm concerned that because I'm on an AMD 64 and have the x86_64 installation, these may not work for me.

Here's everything I know about my laptop:
Acer Aspire 4520
AMD Athlon X2 Dual Core Processor 1K-53(1.7GHz, 2x 256KB L2 Cache)
There's a sticker on the case that says I've got nvidia GeForce 7000M

lspci
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by ukripper on 2008-06-23
this one should work for you on 64 bit..try this -
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

