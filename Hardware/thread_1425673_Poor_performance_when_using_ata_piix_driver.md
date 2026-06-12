---
title: "Poor performance when using ata_piix driver"
date: 2010-03-09
forum: Hardware
---

### Post by mmaxx555 on 2010-03-09
Hello there, this is my first time posting as I always managed to find a solution to my problem on the forum. 

I experience poor performance on my main hd when running ubuntu, especially when moving big files or loading big files. 
This problem has been documented, but seems to be present in different configs and there is no solution for it yet.


After reading quite a bit around, I found out that some hd's perform better on ahci than in ata_piix. I checked lspci -v
 and my main is configured on ata_piix but the second one is on ahci.
As described on [http://ubuntuforums.org/showthread.php?t=1162132](http://ubuntuforums.org/showthread.php?t=1162132)  

I would like to get some help with changing the driver on the kernel to ahci. I can't follow the solution given on the previous post because I am running ubuntu on a vaio laptop and the bios is locked, I can't change the disk config. 
I tried creating a config file in modprobe.d, in local but that didn't work. 

If anyone could tell me how to do it or point me to some website I would be most grateful. I am a computer science student so I am happy to read and try stuff. 

The output of lspci is :

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fc304800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f6000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fc304c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=0c, sec-latency=56
	I/O behind bridge: 0000f000-0000ffff
	Memory behind bridge: fc000000-fc0fffff
	Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 18f0 [size=8]
	I/O ports at 18e8 [size=4]
	I/O ports at 18e0 [size=8]
	I/O ports at 18b4 [size=4]
	I/O ports at 18c0 [size=32]
	Memory at fc304000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Sony Corporation Device 9016
	Flags: medium devsel, IRQ 10
	Memory at 84000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GT] (rev a1)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 3000 [size=256]
	[virtual] Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1051
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at fa000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at fc004000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 80000000-83fff000 (prefetchable)
	Memory window 1: 88000000-8bfff000
	I/O window 0: 0000f000-0000f0ff
	I/O window 1: 0000f400-0000f4ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at fc006000 (32-bit, non-prefetchable) [size=2K]
	Memory at fc000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Sony Corporation Device 9016
	Flags: bus master, medium devsel, latency 57, IRQ 16
	Memory at fc005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

```

I am running kernel 2.6.31-10-generic, on a vaio AR51. 
If any more info is need please ask. 
M

---

### Post by mmaxx555 on 2010-03-10
*bump*

---

