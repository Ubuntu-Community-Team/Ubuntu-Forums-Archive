---
title: "GPS702e3 eSATA ExpressCard doesn't work"
date: 2009-07-12
forum: Hardware
---

### Post by xaprb on 2009-07-12
I'm trying to get this eSATA ExpressCard adapter to work.  It is an IOGEAR 2-port ExpressCard/34 and my laptop is a Dell Inspiron 1501.  My kernel and release:

```
baron@kanga:~$ uname -a
Linux kanga 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux
baron@kanga:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

```

When I plug the device in, there is no indication in dmesg that anything happened, and the lights on the device don't come on.  (It doesn't help that I'm plugging a 34mm card into a 54mm slot and can't be really sure it's actually plugged in; ExpressCard is such a lame design.)

From what I've found in Googling, it used to be necessary only to "modprobe pceihp", but that module is now built into the kernel.

I also found a kernel bug that said the following options would need to be posted to the kernel during boot:

```
pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1
```

I've added that, but I'm not sure it did anything.

During boot, dmesg shows this:

```
[    1.176396] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    1.176518] pci 0000:01:05.0: Boot video device
[    1.176610] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.176633] pcieport-driver 0000:00:05.0: found MSI capability
[    1.176636] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.176650] pci_express 0000:00:05.0:pcie02: allocate port service
[    1.176686] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.176707] pcieport-driver 0000:00:06.0: found MSI capability
[    1.176709] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.176724] pci_express 0000:00:06.0:pcie02: allocate port service
[    1.176775] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.176782] pciehp 0000:00:05.0:pcie02: Bypassing BIOS check for pciehp use on 0000:00:05.0
[    1.176825] pciehp 0000:00:05.0:pcie02: HPC vendor_id 1002 device_id 5a37 ss_vid 0 ss_did 0
[    1.176847] pciehp 0000:00:05.0:pcie02: service driver pciehp loaded
[    1.176851] pciehp 0000:00:06.0:pcie02: Bypassing BIOS check for pciehp use on 0000:00:06.0
[    1.176860] pciehp 0000:00:06.0:pcie02: HPC vendor_id 1002 device_id 5a38 ss_vid 0 ss_did 0
[    2.180048] pciehp 0000:00:06.0:pcie02: Device 0000:05:00.0 already exists at 0000:05:00, cannot hot-add
[    2.180089] pciehp 0000:00:06.0:pcie02: Cannot add device at 0000:05:00
[    3.184048] pciehp 0000:00:06.0:pcie02: service driver pciehp loaded
[    3.184057] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

```

lspci shows

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

```

Any advice?

---

