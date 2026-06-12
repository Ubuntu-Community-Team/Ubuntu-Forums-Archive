---
title: "Only one GPU detected"
date: 2016-04-09
forum: Hardware
---

### Post by alex527 on 2016-04-09
Hi everyone,

i have a 280X and a HD 7950 plugged into my Asrock H61 Pro BTC motherboard. One of them connected with a x1 to x16 extender (not extra powered). I'm using Lubuntu 15.10 64bit on a live USB-stick (persistant mode).
When running 'lspci' the one card connected via extender does't get listed, also when switching them. I'm using 'fglrx-updates' as driver. 
Any ideas?

thx, Alex

lubuntu@lubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 **VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]**
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

Edit: i also switched the extender cable.

---

