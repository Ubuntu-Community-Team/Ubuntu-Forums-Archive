---
title: "Atheros Wireless Broke (HP G60)"
date: 2010-05-25
forum: Hardware
---

### Post by mustangzach on 2010-05-25
Yeah. it was working fine, I've ran Ubuntu since 9.04, and this problem has only happened once before.. then it went away with a few reboots.

My wireless card doesn't detect my networks, and if I try to manually connect, it won't connect.

The wireless card is an Atheros 5007 mini PCI, the laptop is an HP G60-445DX.

I can try to modprobe ath5k, but it doesn't do anything..

Help guys? lspci shows the card is connected.

---

### Post by mustangzach on 2010-05-28
> **mustangzach said:**
> Yeah. it was working fine, I've ran Ubuntu since 9.04, and this problem has only happened once before.. then it went away with a few reboots.

My wireless card doesn't detect my networks, and if I try to manually connect, it won't connect.

The wireless card is an Atheros 5007 mini PCI, the laptop is an HP G60-445DX.

I can try to modprobe ath5k, but it doesn't do anything..

Help guys? lspci shows the card is connected.

Bumping with the lspci output.


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

It sseems to work perfectly, the light is even blue, but it won't detect or manually connect to a network.

---

### Post by mustangzach on 2010-05-29
Hmm.. well, when it first did it after a reboot, I hit the wireless button, I guess disabling it, when I was trying to fix it. I hit it today, it started working again. So.. PEBKAC, but not really PEBKAC.. there's still a bug, but my stupidity made it seem much worse than it really is. No thanks to you guys, I resolved it.

---

