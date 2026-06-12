---
title: "Asus vivobook not recognized keyboard with ubuntu 24.04"
date: 2024-05-03
forum: Hardware
---

### Post by abrumyx on 2024-05-03
[COLOR=#0C0D0E][FONT=-apple-system]I bought an Asus Vivobook ASUSTeK COMPUTER INC. ASUS Vivobook 17 X1704VAP_X1704VA - Intel® Core&#8482; 5 120U × 12 I'm running Ubuntu 23.04[/FONT][/COLOR]
[HTML]uname -a 
Linux 6.8.0-31-generic #31-Ubuntu SMP PREEMPT_DYNAMIC Sat Apr 20 00:40:06 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
[/HTML]

[HTML]lspci
0000:00:00.0 Host bridge: Intel Corporation Raptor Lake-P/U 2p+8e cores Host Bridge/DRAM Controller (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation Raptor Lake-U [Intel Graphics] (rev 04)
0000:00:04.0 Signal processing controller: Intel Corporation Raptor Lake Dynamic Platform and Thermal Framework Processor Participant (rev 01)
0000:00:06.0 System peripheral: Intel Corporation RST VMD Managed Controller
0000:00:08.0 System peripheral: Intel Corporation GNA Scoring Accelerator module (rev 01)
0000:00:0a.0 Signal processing controller: Intel Corporation Raptor Lake Crashlog and Telemetry (rev 01)
0000:00:0e.0 RAID bus controller: Intel Corporation Volume Management Device NVMe RAID Controller Intel Corporation
0000:00:14.0 USB controller: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller (rev 01)
0000:00:14.2 RAM memory: Intel Corporation Alder Lake PCH Shared SRAM (rev 01)
0000:00:14.3 Network controller: Intel Corporation Raptor Lake PCH CNVi WiFi (rev 01)
0000:00:15.0 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #0 (rev 01)
0000:00:15.1 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #1 (rev 01)
0000:00:15.2 Serial bus controller: Intel Corporation Alder Lake PCH Serial IO I2C Controller #2 (rev 01)
0000:00:16.0 Communication controller: Intel Corporation Alder Lake PCH HECI Controller (rev 01)
0000:00:19.0 Serial bus controller: Intel Corporation Alder Lake-P Serial IO I2C Controller #0 (rev 01)
0000:00:1f.0 ISA bridge: Intel Corporation Raptor Lake LPC/eSPI Controller (rev 01)
0000:00:1f.3 Audio device: Intel Corporation Raptor Lake-P/U/H cAVS (rev 01)
0000:00:1f.4 SMBus: Intel Corporation Alder Lake PCH-P SMBus Host Controller (rev 01)
0000:00:1f.5 Serial bus controller: Intel Corporation Alder Lake-P PCH SPI Controller (rev 01)
10000:e0:06.0 PCI bridge: Intel Corporation Raptor Lake PCIe 4.0 Graphics Port (rev 01)
10000:e1:00.0 Non-Volatile memory controller: Sandisk Corp WD Black SN770 / PC SN740 256GB / PC SN560 (DRAM-less) NVMe SSD (rev 01)
[COLOR=#0C0D0E][FONT=-apple-system][/FONT][/COLOR][/HTML][COLOR=#0C0D0E][FONT=-apple-system]

The laptop is up to date, so, I believe I don't have anything to do until Ubuntu releases new drivers, right? Can someone explain to me how this works? I mean drivers, should be released by the Linux kernel or Ubuntu? Is Asus related here?[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]In the beginning, I tried Debian 12 and the laptop just didn't recognize anything, then by mistake tried Ubuntu 22.04 (By mistake because I wante to check 24.04) and the network card didn't work (in addition to the keyboard), with Ubuntu 24.04 I think only the keyboard doesn't work.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Thanks a lot![/FONT][/COLOR]

---

