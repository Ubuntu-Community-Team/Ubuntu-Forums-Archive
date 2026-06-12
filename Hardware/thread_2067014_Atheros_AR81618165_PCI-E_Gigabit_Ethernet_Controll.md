---
title: "Atheros AR8161/8165 PCI-E Gigabit Ethernet Controller Driver"
date: 2012-10-05
forum: Hardware
---

### Post by hesam18 on 2012-10-05
Hello everyone;
I am looking for "Atheros AR8161/8165 PCI-E Gigabit Ethernet Controller" **_LAN Driver_** for UBUNTU 12.10 64bit
Who can help me to find? (I google it but nothing useful)

also this is the result of lspci -vk:

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
	Subsystem: Lenovo Device 3977
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d2000000-d30fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 3977
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d3400000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Lenovo Device 3977
	Flags: bus master, medium devsel, latency 0, IRQ 42
	Memory at d3b00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Lenovo Device 3977
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d3b14000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 3977
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at d3b19000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Lenovo Device 3977
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d3b10000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d3a00000-d3afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: d3900000-d39fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: d3800000-d38fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 3977
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d3b18000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
	Subsystem: Lenovo Device 3977
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo Device 3977
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at 4088 [size=8]
	I/O ports at 4094 [size=4]
	I/O ports at 4080 [size=8]
	I/O ports at 4090 [size=4]
	I/O ports at 4060 [size=32]
	Memory at d3b17000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Lenovo Device 3977
	Flags: medium devsel, IRQ 10
	Memory at d3b15000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 4040 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation GeForce GT 630M (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 3977
	Flags: fast devsel, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 3000 [size=128]
	Expansion ROM at d3000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel modules: nouveau, nvidiafb

02:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)
	Subsystem: Lenovo Device 3979
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d3a00000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Lenovo Device 31a1
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d3900000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
	Subsystem: Lenovo Device 3976
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d3803000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30) (prog-if 01)
	Subsystem: Lenovo Device 3976
	Flags: fast devsel, IRQ 19
	Memory at d3802000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
	Subsystem: Lenovo Device 3976
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d3801000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms

04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)
	Subsystem: Lenovo Device 3976
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d3800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
[SIZE="4"]My Wireless is working clearly, I need LAN adapter driver[/SIZE]

thanks guys ;)

---

### Post by varunendra on 2012-10-06
> **hesam18 said:**
> ```
02:00.0 Ethernet controller: Atheros Communications Inc. [COLOR=Red]**AR8161**[/COLOR] Gigabit Ethernet (rev 08)
```
That^ chip is a newcomer to the market and its driver for linux is still under development. Try either of these solutions (both are same, just using different versions of the alx driver):
[http://ubuntuforums.org/showthread.php?p=12206393](http://ubuntuforums.org/showthread.php?p=12206393) (originally suggested & tested by *chili555*, using a newer version)

Or,

[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller) (by *izx*, using an older version of the driver, apparently working for many)

Hope it'll work for you too.

---

### Post by Bachi on 2013-04-07
> **varunendra said:**
> That^ chip is a newcomer to the market and its driver for linux is still under development. 

I use the by now delivered alx driver, wireless works, but wired ethernet does not. Haven't had such issues in a long time. I think it is time that we start to rumble on manufacturer's social websites if they still release new hardware without proper linux drivers - this really should be ended now. Place your comments on their social media sites mentioned in the footer of atheros.com .. I certainly did..

---

### Post by clark22 on 2013-06-20
The ALX driver will be officially added in newer kernels, but in the meantime you can find it here: The ALX driver.

---

