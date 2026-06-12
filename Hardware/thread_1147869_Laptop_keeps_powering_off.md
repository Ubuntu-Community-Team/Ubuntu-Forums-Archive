---
title: "Laptop keeps powering off"
date: 2009-05-03
forum: Hardware
---

### Post by haykuro on 2009-05-03
Hello everyone!
I've been having a problem lately where my laptop decides to randomly shut off, completely.

It tends to happen during high CPU usage.

Running VMWare, while browsing the web locally, will force the laptop to shut off (it randomly just halts completely. it's pretty much just dying on the spot. no indication of it)

compiling a kernel, within a couple of minutes will cause the laptop to shut off.

at first i suspected overheating, but after monitoring the heat of the cpu while compiling a kernel (for the android platform) it just shuts off, and cpu usage was normal.

any help would be greatly appreciated.

Laptop
Vendor: Toshiba
Model: L305D-S5868
CPU: AMD Turion X2 (64)
GPU: ATI Radeon (Radeon HD 3100)
Distro: Ubuntu 9.04 (i386)

Some further info:
```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```
```
$ cat /etc/issue.net
Ubuntu 9.04
```
```
$ uname -a
Linux haykuro-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

---

### Post by Dark_Stang on 2009-05-03
Sounds like an overheating issue. Buy a can of air, pop off the access panels on the bottom of the laptop, and start cleaning it out. Also, make sure all your fans are spinning freely and not getting hung up on some dust/lint/pet hair.

---

### Post by shane2peru on 2009-10-14
> **haykuro said:**
> Hello everyone!
I've been having a problem lately where my laptop decides to randomly shut off, completely.

It tends to happen during high CPU usage.

Running VMWare, while browsing the web locally, will force the laptop to shut off (it randomly just halts completely. it's pretty much just dying on the spot. no indication of it)

compiling a kernel, within a couple of minutes will cause the laptop to shut off.

at first i suspected overheating, but after monitoring the heat of the cpu while compiling a kernel (for the android platform) it just shuts off, and cpu usage was normal.

any help would be greatly appreciated.

Laptop
Vendor: Toshiba
Model: L305D-S5868
CPU: AMD Turion X2 (64)
GPU: ATI Radeon (Radeon HD 3100)
Distro: Ubuntu 9.04 (i386)

Some further info:
```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```
```
$ cat /etc/issue.net
Ubuntu 9.04
```
```
$ uname -a
Linux haykuro-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

I have this same issue.  It is indeed an overheating issue, and all my cooling vents are clean and spinning.  This actually is a driver issue.  I found this thread still after many months looking for a solution.  I have installed ATI proprietary drivers and it doesn't seem to help.  I have tried about 6 different OS and none of them seemed to help.  Any cpu intense process kills the laptop.  If anyone knows of any solution (I'm into extreme solutions now) I'm willing to try it.  Nothing I have done has worked!  This is really annoying.

Shane

---

