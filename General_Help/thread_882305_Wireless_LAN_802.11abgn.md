---
title: "Wireless LAN 802.11a/b/g/n"
date: 2008-08-06
forum: General Help
---

### Post by zachoeser on 2008-08-06
My Laptop has 's wireless specs are a 	Wireless LAN 802.11a/b/g/n . I am dual booting with vista 64X.I can not find any way to get my wireless to work. i tried the ndiswrapper but that does not support vista drivers. and i tried a .inf file i found on google and that does not work either. does anyone have any ideas on how to get my wireless up.. It is imperative i get this working before monday when school starts. Please and thank you in advance,

---

### Post by tamoneya on 2008-08-06
can we get some info on the manufacturer of the card.  Run this in terminal:```
lspci
```

---

### Post by zachoeser on 2008-08-06
> **tamoneya said:**
> can we get some info on the manufacturer of the card.  Run this in terminal:```
lspci
```

Its Broadcom

---

### Post by zachoeser on 2008-08-06
Broadcom

---

### Post by tamoneya on 2008-08-07
> **zachoeser said:**
> Broadcom

I was looking for the specific chipset so can you post the output of lspci.

Thanks

---

### Post by zachoeser on 2008-08-07
zach@Zach-Ubuntu:~$ lspci
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
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by tamoneya on 2008-08-07
have you seen this thread.  It seems to apply directly to you.  They even attached the drivers they used.

[http://ubuntuforums.org/showthread.php?t=616801](http://ubuntuforums.org/showthread.php?t=616801)

---

### Post by zachoeser on 2008-08-07
yea thanks for that. i looked and tried forever but i cant get the driver to install
i got the fwcutter working but it says i neeed a newer version but i have the newest version.... it says it extracts the driver but idk how to install it

---

### Post by zachoeser on 2008-08-08
THANK YOU SO MUCH! I finally got it working after like 4 hours but i did it THANkS Again!

---

