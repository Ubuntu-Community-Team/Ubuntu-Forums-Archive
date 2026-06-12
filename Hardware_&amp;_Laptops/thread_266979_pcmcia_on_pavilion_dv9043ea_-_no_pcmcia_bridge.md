---
title: "pcmcia on pavilion dv9043ea - no pcmcia bridge"
date: 2006-09-28
forum: Hardware &amp; Laptops
---

### Post by drunken-wallaby on 2006-09-28
Hi.

I have the following problem. I want to use a pcmcia card with my notebook. However, it seems that there is no "pcmcia bridge" installed, since this is the error message I get, when I try to manually start pcmcia via ```
sudo /etc/init.d/pcmciautils restart
```. Question, what can I do to install such a **pcmcia bridge**?

Bernhard

Ps: This is my output of lspci ```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

---

### Post by jcaveman on 2006-11-05
I have this chipset in a DV6119us and it doesn't have PCMCIA capability.  It has ExpressCard/54.  I don't think the PCMCIA drivers with this card slot.  I'm not sure but I believe its an extension to PCIe.  Its also the reason, the bcm43xx drivers don't work with the Broadcom 4311 wireless, a new bus that isn't implemented in the open source drivers yet.

---

### Post by niC666 on 2007-10-15
Anything happen with this?

I have the same problem on a HP Pavilion dv9521ei. 
PCMCIAutils fails with No PCMCIA bridge module specified

---

### Post by niC666 on 2007-10-15
New laptops generally have expresscard slots instead of PCMCIA slots. the expresscard technology is not backwards compatible with PCMCIA.

---

