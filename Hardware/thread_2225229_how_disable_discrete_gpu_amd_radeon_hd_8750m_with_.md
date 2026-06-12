---
title: "how disable discrete gpu amd radeon hd 8750m with open driver?"
date: 2014-05-20
forum: Hardware
---

### Post by fab2 on 2014-05-20
Hello everyone, 
I post on the forum because I have a small question about the switch between my hybrid gpu intel and AMD Radeon HD 8750m with ubuntu 14.04 (kernel 3.13?). 
I would like to know how to turn my graphics discrete cards hd8750m to use only the intel integrated card, and _only with __free driver radeon_ (for gain energy)? 
I can turn off the gpu with the proprietary driver but it works very badly and amdcccle disappears after a few restarts, so I can not enable or disable. More it disables my radeon hd also on windows 8 (which I use for games), so it is a bad solution. But the little that it works gives me a big gain of battery.  
There is no file / sys / kernel / debug / vgaswitcheroo / switch or other vga_switcheroo to use (even as root). Is not supported?
More, my radeon hd is "display controller" and not "VGA compatible controller", is it normal?
Thank you and sorry for my bad english .
lspci | grep "VGA compatible controller"00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
fabien@fabien-Aspire-E1-572PG:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
00:1c.4 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 5 [8086:9c18] (rev e4)
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57786 Gigabit Ethernet PCIe [14e4:16b3] (rev 01)
01:00.1 SD Host controller [0805]: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 01)
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] [1002:6600]
 					 
 				 			 		 		 			 				 			
 		
 	    	[h=2]#4 [Le 10/05/2014, à 05:13]("http://forum.ubuntu-fr.org/viewtopic.php?pid=16871381#p16871381")[/h] 	 		 			 				 					**vebveb** 				
 				 					 					 						/

---

### Post by fab2 on 2014-05-21
nobody have ideas? acpi-call can it resolve my problem?

---

### Post by fab2 on 2014-05-23
up :)
 I have not managed to install acpi-call but I DPM enabled by adding radeon.dpm = 1 to grub (it was not ebable by default on 14.04). but I do not understand how to use it?

---

