---
title: "Aspire One Netbook Eth0"
date: 2012-02-13
forum: Hardware
---

### Post by Negam on 2012-02-13
Hey All,

I'm running Ubuntu 11.10 on an Aspire One Netbook 722.  I've been around Ubuntu for a little while, though not in any real technical capacity.

I've been working well with wireless.  I'm attempting to get wired up and running, and running into issues.  My Eth0 does not work automatically, and commands like ```
sudo dhclient eth0
``` return 'cannot find device "eth0"'.

The output of my /etc/network/interfaces is ```
auto lo
iface lo inet loopback

```The output of lspci -v
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, 66MHz, medium devsel, latency 0

00:01.0 VGA compatible controller: ATI Technologies Inc Device 9807 (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon
    Kernel modules: radeon

00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at f0444000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 4118 [size=8]
    I/O ports at 4124 [size=4]
    I/O ports at 4110 [size=8]
    I/O ports at 4120 [size=4]
    I/O ports at 4100 [size=16]
    Memory at f044c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f044b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f044a000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0449000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0448000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0300000-f03fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.2 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0200000-f02fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.3 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: f0100000-f01fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot-), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: ATI Technologies Inc Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
    Flags: fast devsel

06:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f0200000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-0c-a4-57-dc-0e-a1-ff
    Kernel modules: atl1c

07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Foxconn International, Inc. Device e042
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-19-ff-ff-70-60-d8
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: brcmsmac
    Kernel modules: wl, bcma, brcmsmac


```The output of 

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62004 (62.0 KB)  TX bytes:62004 (62.0 KB)

wlan0     Link encap:Ethernet  HWaddr 60:d8:19:70:87:60  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62d8:19ff:fe70:8760/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19926326 (19.9 MB)  TX bytes:2531559 (2.5 MB)
```I think it's a driver issue, but have no idea where to look.  Any pointers?

Thanks,

---

