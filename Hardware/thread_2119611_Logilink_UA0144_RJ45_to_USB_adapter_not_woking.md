---
title: "Logilink UA0144 RJ45 to USB adapter not woking"
date: 2013-02-24
forum: Hardware
---

### Post by fernando98 on 2013-02-24
Hi everyone,
I've recently acquired a Dell XPS 12. Since I use Ethernet a lot I bought a Ethernet to USB adapter, the Logilink AU0144. In Windows 8 it works fine but in Ubuntu 12.10 it does not. When pluged in Ubuntu tries to connect to the Internet but after a while a message that reads: "Wired connection disconnected" pops-up.

I thought it could be a missing drivers issue but apparently there are no drivers for this product.

Here is the output of some commands:

lspci | grep Ethernet outpust nothing so here is the unfiltered lspci:

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Device 0153 (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QS77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)

```

lsusb:

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0b95:772b ASIX Electronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 03eb:8409 Atmel Corp. 
Bus 001 Device 004: ID 0c45:644e Microdia 
Bus 001 Device 005: ID 8087:0a05 Intel Corp. 
Bus 002 Device 003: ID 8087:07da Intel Corp. 

```

ifconfig:

Shows 2 interfaces the local loopback and a a Ethernet interface eth0 which has a MAC and IPv6 address

---

