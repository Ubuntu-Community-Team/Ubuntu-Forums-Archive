---
title: "HP250G3 shutdown/reboot/suspend issue"
date: 2015-10-08
forum: Hardware
---

### Post by kerya on 2015-10-08
HP250G3 does not power off (shutdown), does not reboot(either button or keyboard or menu), suspend does not working.

Tried with Xubuntu 14.04, 14.10, 15.04; kernels 3.16, 3.13.

No answer on launchpad(for a month): [https://answers.launchpad.net/ubuntu/+question/271094](https://answers.launchpad.net/ubuntu/+question/271094)

$ uname -a
Linux kerya-hp250 3.19.0-27-generic #29~14.04.1-Ubuntu SMP Sun Aug 16 01:51:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
 
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
 
$ sudo dmidecode -t 1
# dmidecode 2.12
# SMBIOS entry point at 0x79029000
SMBIOS 2.7 present.
 Handle 0x0001, DMI type 1, 27 bytes
System Information
 Manufacturer: Hewlett-Packard
 Product Name: HP 250 G3 Notebook PC
 Version: 0991100000000000000600087
 Serial Number: CND4450N5K
 UUID: E02F0F1B-D142-E411-932B-3464A9CA0F50
 Wake-up Type: Power Switch
 SKU Number: K3X00EA#ACB
 Family: 103C_5336AN G=N L=CON B=HP S=PAV
 
$ lspci -v
00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, fast devsel, latency 0
 Kernel driver in use: iosf_mbi_pci
 00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e) (prog-if 00 [VGA controller])
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, fast devsel, latency 0, IRQ 91
 Memory at 90000000 (32-bit, non-prefetchable) [size=4M]
 Memory at 80000000 (32-bit, prefetchable) [size=256M]
 I/O ports at 2050 [size=8]
 Expansion ROM at <unassigned> [disabled]
 Capabilities: <access denied>
 Kernel driver in use: i915
 00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e) (prog-if 01 [AHCI 1.0])
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 88
 I/O ports at 2048 [size=8]
 I/O ports at 205c [size=4]
 I/O ports at 2040 [size=8]
 I/O ports at 2058 [size=4]
 I/O ports at 2020 [size=32]
 Memory at 90a1f000 (32-bit, non-prefetchable) [size=2K]
 Capabilities: <access denied>
 Kernel driver in use: ahci
 00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0e) (prog-if 30 [XHCI])
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, medium devsel, latency 0, IRQ 87
 Memory at 90a00000 (64-bit, non-prefetchable) [size=64K]
 Capabilities: <access denied>
 Kernel driver in use: xhci_hcd
 00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, fast devsel, latency 0, IRQ 92
 Memory at 90900000 (32-bit, non-prefetchable) [size=1M]
 Memory at 90800000 (32-bit, non-prefetchable) [size=1M]
 Capabilities: <access denied>
 Kernel driver in use: mei_txe
 00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, fast devsel, latency 0, IRQ 93
 Memory at 90a10000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: snd_hda_intel
 00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
 Flags: fast devsel
 Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
 I/O behind bridge: 00003000-00003fff
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
 I/O behind bridge: 00004000-00004fff
 Memory behind bridge: 90700000-907fffff
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 00:1c.2 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
 I/O behind bridge: 00005000-00005fff
 Memory behind bridge: 90600000-906fffff
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 00:1c.3 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
 I/O behind bridge: 00001000-00001fff
 Memory behind bridge: 90500000-905fffff
 Prefetchable memory behind bridge: 0000000090400000-00000000904fffff
 Capabilities: <access denied>
 Kernel driver in use: pcieport
 00:1d.0 USB controller: Intel Corporation ValleyView USB Enhanced Host Controller (rev 0e) (prog-if 20 [EHCI])
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, medium devsel, latency 0, IRQ 23
 Memory at 90a18000 (32-bit, non-prefetchable) [size=1K]
 Capabilities: <access denied>
 Kernel driver in use: ehci-pci
 00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, medium devsel, latency 0
 Capabilities: <access denied>
 Kernel driver in use: lpc_ich
 00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: medium devsel, IRQ 7
 Memory at 90a19000 (32-bit, non-prefetchable) [size=32]
 I/O ports at 2000 [size=32]
 Capabilities: <access denied>
 02:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
 Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter
 Flags: bus master, fast devsel, latency 0, IRQ 17
 Memory at 90710000 (32-bit, non-prefetchable) [size=64K]
 Capabilities: <access denied>
 Kernel driver in use: rt2800pci
 02:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
 Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter
 Flags: fast devsel, IRQ 11
 Memory at 90700000 (32-bit, non-prefetchable) [size=64K]
 Capabilities: <access denied>
 03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, fast devsel, latency 0, IRQ 89
 Memory at 90600000 (32-bit, non-prefetchable) [size=4K]
 Capabilities: <access denied>
 Kernel driver in use: rtsx_pci
 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
 Subsystem: Hewlett-Packard Company Device 2213
 Flags: bus master, fast devsel, latency 0, IRQ 90
 I/O ports at 1000 [size=256]
 Memory at 90500000 (64-bit, non-prefetchable) [size=4K]
 Memory at 90400000 (64-bit, prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: r8169

---

### Post by niksuldim on 2015-12-22
i do not understand,you press the power button or soft shutdown or restart through menu,its very simple enable usb 3.0 via bios setup(start your computer press esc button then when prompts f10)....

---

