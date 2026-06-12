---
title: "AMD Integrated &amp; Dedicated? Battery life."
date: 2017-02-13
forum: Hardware
---

### Post by izznogooood on 2017-02-13
I recently bought a Lenovo Yoga 500. This has an AMD cpu with integrated graphics "and i think it also has a dedicated graphics card"?

```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 45)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330] (rev ff)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter (rev 20)



```

Now I know the radeon module is loaded

```
anders@yoga:~$ cat /var/log/Xorg.0.log |grep radeon[     8.344] (II) LoadModule: "radeon"
[     8.344] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     8.345] (II) Module radeon: vendor="X.Org Foundation"
[     8.596] (II) RADEON(G0): [DRI2]   DRI driver: radeonsi
[     8.596] (II) RADEON(G0): [DRI2]   VDPAU driver: radeonsi
[     8.805] (II) RADEON(0): [DRI2]   DRI driver: radeonsi
[     8.805] (II) RADEON(0): [DRI2]   VDPAU driver: radeonsi
[     9.015] (II) AIGLX: Loaded and initialized radeonsi



```

But which graphics card does it use? And any power saving tips in regards to AMD and Radeon would be much appreciated as 2 hours does not pass as a laptop in my eyes....

---

