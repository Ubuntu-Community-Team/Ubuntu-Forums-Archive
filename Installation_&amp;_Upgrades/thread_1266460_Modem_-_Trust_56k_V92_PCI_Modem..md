---
title: "Modem - Trust 56k V92 PCI Modem."
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by Best04 on 2009-09-14
Hy to all!

Sorry, but my english not is very perfect!

I've the modem in subject.

This is the output of scanmodem software:

```


For candidate card in slot 01:0a.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:0a.0	1813:4000		Communication controller: Ambient Technologies Inc HaM controllerless modem 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 01:0a.0 ----
[    0.386829] pci 0000:01:0a.0: reg 10 32bit mmio: [0xfbfff000-0xfbffffff]
[    0.386833] pci 0000:01:0a.0: reg 14 io port: [0xe800-0xe8ff]
[    0.386854] pci 0000:01:0a.0: supports D2
[    0.386855] pci 0000:01:0a.0: PME# supported from D2 D3hot D3cold
[    0.386858] pci 0000:01:0a.0: PME# disabled


```

And this the lspci command:

```


root@best-desktop:/home/best# lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
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
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:0a.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)


```

	
Help me someone knows where to find drivers or how to install it?
	

On the site of linmodem there are more links righteous, but information that I could find is this:

```


http://xmodem.org/chipsets/intel/intel_563x_ham.html


```

While the modem is this:

```


http://www.trust.com/products/product.aspx?artnr=11709


```

Thanks!  :)

---

### Post by Best04 on 2009-09-17
Up! :)

---

