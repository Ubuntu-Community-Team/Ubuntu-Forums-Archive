---
title: "Wireless not enabled, Presario"
date: 2010-05-23
forum: Hardware
---

### Post by NeroC on 2010-05-23
Hello!
I just installed Ubuntu 10.04 64bit version on wifes laptop, it's a Presario  CQ60-300EO.

And the little Network icon in the top panel says "Enable Wireless" but the button is grayed out so I can't click it.

In the package manager I've installed everything related to Broadcom, though I don't know if it's a broadcom card.

The card is activated as you can see because the is a blue button telling if it's on or off, however pressing the button makes no change, it stays on. Sometimes when restarting the wireless is enabled but the button is blinking in orange and blue (off and on) and when you try to change the wireless network the button turns blue. However under that short period you are not able to connect.

Can anyone help me?
It's a Presario  CQ60-300EO please look up some info if it's a Broadcom, Artheros or something else, I will look myself too

---

### Post by ajgreeny on 2010-05-23
See my response here [http://ubuntuforums.org/showthread.php?p=9348237#post9348237](http://ubuntuforums.org/showthread.php?p=9348237#post9348237)

You're not that same person using another name, are you?

---

### Post by NeroC on 2010-05-23
> **ajgreeny said:**
> 
You're not that same person using another name, are you?

Must be my wife, she's not home so I can't confront her :P

lspci gives me,
```

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```
The other command gives me,
```

  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:7a:40:b3
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2c:32:65:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff

```
I can see it says Atheros at vendor and in Ethernet Controller, so I'll go ahead and download the drivers for Atheros and see if it helps :)

---

### Post by NeroC on 2010-05-24
Installed the drivers, the button isn't grayed out but it doesn't connect to a network.
I click on the network name and just sits there "loading"

---

### Post by ed-rapley on 2010-05-25
Take a look at this thread, with posts 3 and four, i got my fujitsu amilo wifi working.

[http://ubuntuforums.org/showthread.php?p=9354354#post9354354](http://ubuntuforums.org/showthread.php?p=9354354#post9354354)

good luck.

---

