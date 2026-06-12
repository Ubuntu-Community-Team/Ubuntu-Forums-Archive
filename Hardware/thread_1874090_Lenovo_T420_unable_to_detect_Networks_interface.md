---
title: "Lenovo T420 unable to detect Networks interface"
date: 2011-11-02
forum: Hardware
---

### Post by linux83 on 2011-11-02
Hello Freinds,

can some one help me to get my laptop lenovo T420 network interfaces to work.
i can't get Wired/Wiresles and display to work thus unable to update the system to latest driver.

my system is ubuntu 10.04.
this is the lshw and lspci -nn:
---------------------------------------------
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1c.4 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 5 [8086:1c18] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c4f] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 04)
03:00.0 Network controller [0280]: Intel Corporation Device [8086:0085] (rev 34)
0d:00.0 System peripheral [0880]: Ricoh Co Ltd Device [1180:e823] (rev 05)
---------------------------------------------------------------------------------
*-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f03fffff memory:e0000000-efffffff(prefetchable) ioport:5000(size=64)
        *-communication UNCLAIMED
             description: Communication controller
             product: Cougar Point HECI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f2525000-f252500f
        *-network UNCLAIMED
             description: Ethernet controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f2500000-f251ffff memory:f252b000-f252bfff ioport:5080(size=32)

thanks alot.

linux83

---

