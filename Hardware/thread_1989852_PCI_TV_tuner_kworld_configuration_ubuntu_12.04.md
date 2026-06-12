---
title: "PCI TV tuner kworld configuration ubuntu 12.04"
date: 2012-05-28
forum: Hardware
---

### Post by cuyo01 on 2012-05-28
Greetings. 

I have an old tv tuner, the problem is dont know what model is, is listed with lspci command as follow:

```
lspci
00:00.0 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: NVIDIA Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: NVIDIA Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: NVIDIA Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: NVIDIA Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:10.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
[B]01:04.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)[/B]
01:06.0 USB controller: OPTi Inc. 82C861 (rev 10)
02:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
02:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

Installed tvtime but i only can acces the s-video input, can only see signal conecting my ps2 to the tvcard s-video input but no channels.

running tvtime from terminal gives this:

```
tvtime
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /home/noe/.tvtime/tvtime.xml
videoinput: Can't get tuner info: Argumento inválido
videoinput: Can't get tuner info: Argumento inválido
mixer: find error: Conseguido
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.

```

i have the aerial antenna conected to the RF input of the tvcard.

---

