---
title: "Ubuntu 13.10 shutting down due to overheating"
date: 2014-01-26
forum: Hardware
---

### Post by okay19 on 2014-01-26
I run a dual boot of Ubuntu 13.10 and Windows 8.1 on my HP laptop. The installation works fine, but when I run any CPU-intensive games or programs on Ubuntu, the laptop will suddenly shut down. When I turn it back on, I am notified that my computer was automatically shut down to prevent hardware damage due to overheating. This problem does not occur on Windows at all.

Also, I just looked at my system info with Piriform Speccy and found out that my CPU's average temperature (on the Windows side) is about 90 degrees Celsius.

I have installed TLP on Ubuntu, and the problem has still happened twice since then. Any suggestions?

---

### Post by Yellow Pasque on 2014-01-26
What is the exact model you have? If it's overheating in Windows, your best bet is to resolve the issue there using HP's support resources. It's possible that you need a BIOS update to fix fan control or that you have a bum heatsink install.

Please show lspci output too:
```
lspci -q -k
```

---

### Post by okay19 on 2014-01-26
The laptop is an HP ENVY m6 notebook PC, and the CPU is listed as a quad-core AMD A10-4600M APU with Radeon graphics.

Here is the output of lspci:
```

dillon@dillon-pc:~$ lspci -q -k
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
    Subsystem: Hewlett-Packard Company Device 18a6
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7660G]
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: radeon
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: snd_hda_intel
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
    Kernel driver in use: pcieport
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Port
    Kernel driver in use: pcieport
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: xhci_hcd
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: xhci_hcd
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: ahci
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: ohci-pci
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: ehci-pci
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: ohci-pci
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: ehci-pci
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 14)
    Subsystem: Hewlett-Packard Company Device 18a6
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
    Subsystem: Hewlett-Packard Company Device 18a6
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
    Kernel driver in use: k10temp
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: rtsx_pci
01:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
    Subsystem: Hewlett-Packard Company Device 18a6
    Kernel driver in use: r8169
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
    Subsystem: Hewlett-Packard Company AR9485/HB125 802.11bgn 1×1 Wi-Fi Adapter
    Kernel driver in use: ath9k

```

---

### Post by Yellow Pasque on 2014-01-26
Try enabling dpm: [http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html](http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html)

---

### Post by okay19 on 2014-01-27
Solved, for now. I enabled dpm and changed the processor settings from 'performance' to 'ondemand.' No issues have come up since then.

---

