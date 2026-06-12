---
title: "1024x768 is the highest resolution"
date: 2012-06-06
forum: Hardware
---

### Post by ckop64 on 2012-06-06
Hi. Just recently I have made a LiveUSB with Fedora 17 on it. When I booted it I experienced screen flickering and a highest resolution of 1024x768. When 
I rebooted into my main environment the problem still persisted (note, that on the Live USB fedora uses nouveau, whereas I use the binary blob on my Ubuntu 12.04 installation). It used to work fine for me. Any attempts of modifying xorg.conf didn't really help.

My lspci:
```
00:00.0 RAM memory: NVIDIA Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: NVIDIA Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: NVIDIA Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: NVIDIA Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB controller: NVIDIA Corporation MCP65 USB Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP65 USB Controller (rev a3)
00:07.0 Audio device: NVIDIA Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: NVIDIA Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: NVIDIA Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: NVIDIA Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: NVIDIA Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: NVIDIA Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: NVIDIA Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 VGA compatible controller: NVIDIA Corporation G94 [GeForce 9600 GT] (rev a1)

```My Xorg.0.log:
[http://pastebin.com/seL5KQSz](http://pastebin.com/seL5KQSz)

Thanks for any help in advance.

---

### Post by ckop64 on 2012-06-06
bump

---

### Post by aromo on 2012-06-06
> **ckop64 said:**
> Hi. Just recently I have made a LiveUSB with Fedora 17 on it. When I booted it I experienced screen flickering and a highest resolution of 1024x768. When 
I rebooted into my main environment the problem still persisted 

So, what's the problem?  My screen flickers a bit and gets 1024x768 (using 12.04).  Can you elaborate as to why it is a problem?

---

### Post by ckop64 on 2012-06-07
> **aromo said:**
> So, what's the problem?  My screen flickers a bit and gets 1024x768 (using 12.04).  Can you elaborate as to why it is a problem?

Yesterday I enjoyed flicker-free 1080p resolution, that's why.

---

