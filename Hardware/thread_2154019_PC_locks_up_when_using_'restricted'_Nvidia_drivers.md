---
title: "PC locks up when using 'restricted' Nvidia drivers | Geforce 8300gs"
date: 2013-06-13
forum: Hardware
---

### Post by luctor on 2013-06-13
Since a long time Nvidia drivers don't work with my computer anymore and I've sort of given up.
Whatever Nvidia driver I install my pc locks up, sometimes immediately, sometimes after a few minutes.
I tried to install drivers via the 'restricted drivers', from the Nvidia website and almost any version I could lay my hands on, with almost any kernel I could install. All fail.
Reviewing the logs doesn't help me.

Even in my Windows partition I can't install any 'latest' drivers. On my Windows partition I have the drivers installed from the Dell website : 163.71 Vista 32bit, A02. Rarely use Windows btw.

The Nouveau drivers work fine btw and I'm even able to play the odd game of Urban Terror :-) (although I'm no good at it)
Still, I want the proprietary to work.

Some specs :

```
lspci 
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**02:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8300 GS] (rev a1)**
```

If you need more , just let me know.

Rob

---

### Post by papibe on 2013-06-13
Hi luctor.

Have you tried to set it to nomodeset? If not, take a look at post #6 of this [thread]("http://ubuntuforums.org/showthread.php?t=2149499&highlight=nvidia+text+mode") to see how to do it.

Regards.

---

