---
title: "Only one core detected on my Dual core laptop"
date: 2008-12-03
forum: Hardware
---

### Post by rdjse on 2008-12-03
Hi!

I've installed the latest Ubuntu 8.10 on my LG E500 laptop and I've only got one of my 2 cores up and running (It's an Intel Core 2 Duo)
To be able to boot I have to pass acpi=off or nolapic to the kernel, or else the system freeze. With acpi=off both my cores are detected and running, but I'm unable to take advantage of any power saving options and that's vital on a laptop. Using "nolapic" the system boots fine, I'm able to use power management features but only one core is detected, and that's a bit of a problem.

It feels like I'm so close on getting a nice Linux system running smooth on that laptop if I can solve this problem. Do you guys have any information or ideas of what I may change or do to get both my kernels up and running WITH acpi-support? 

Here's my lspci, tell me if you need some other outputs.
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
00:09.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
00:09.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
00:09.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
02:00.0 Network controller: RaLink Device 0781
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

---

### Post by rdjse on 2008-12-04
I think I solved it by using nolapic_timer that I found on another site. I have Quick Reply no idea what it does but hey... it works! :)

---

