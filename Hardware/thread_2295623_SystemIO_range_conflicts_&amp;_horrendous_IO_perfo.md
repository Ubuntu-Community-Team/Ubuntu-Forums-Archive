---
title: "SystemIO range conflicts &amp; horrendous IO performance"
date: 2015-09-20
forum: Hardware
---

### Post by Amon_Re on 2015-09-20
I've been hunting down an issue on my computer that's been there for a while now. At first I thought it was an issue with Darktable, but recently I managed to exclude that one. The issue is related to disk I/O and I'm at a loss to actually fix this one.

This is the output of lspci:
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
	Subsystem: Intel Corporation Device 2032
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: ivb_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f6000000-f70fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
	Capabilities: [88] Subsystem: Intel Corporation Device 2032
	Capabilities: [80] Power Management version 3
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [140] Root Complex Link
	Capabilities: [d94] #19
	Kernel driver in use: pcieport

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Intel Corporation Device 2032
	Flags: bus master, medium devsel, latency 0, IRQ 26
	Memory at f7220000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [70] Power Management version 2
	Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Intel Corporation Device 2032
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f723b000 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: mei_me

00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
	Subsystem: Intel Corporation Device 2032
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f7200000 (32-bit, non-prefetchable) [size=128K]
	Memory at f7239000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at f040 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] PCI Advanced Features
	Kernel driver in use: e1000e

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Device 2032
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f7238000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Intel Corporation Device 2032
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at f7230000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Intel Corporation Device 2032
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7100000-f71fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Intel Corporation Device 2032
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Device 2032
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7237000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation H77 Express Chipset LPC Controller (rev 04)
	Subsystem: Intel Corporation Device 2032
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Intel Corporation Device 2032
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at f090 [size=8]
	I/O ports at f080 [size=4]
	I/O ports at f070 [size=8]
	I/O ports at f060 [size=4]
	I/O ports at f020 [size=32]
	Memory at f7236000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Intel Corporation Device 2032
	Flags: medium devsel, IRQ 11
	Memory at f7235000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f000 [size=32]

01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Gigabyte Technology Co., Ltd Device 3555
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	[virtual] Expansion ROM at f7000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Capabilities: [900] #19
	Kernel driver in use: nvidia

01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device 3555
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: snd_hda_intel

03:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
	Subsystem: Silicon Image, Inc. Device 7132
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f7184000 (64-bit, non-prefetchable) [size=128]
	Memory at f7180000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at d000 [size=128]
	Expansion ROM at f7100000 [disabled] [size=512K]
	Capabilities: [54] Power Management version 2
	Capabilities: [5c] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: sata_sil24

```

I noticed the following error in syslog:
```
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220446] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20141107/utaddress-258)
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220453] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220471] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220475] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220476] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220479] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220480] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220497] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x000000000000050f-0x000000000000050f (\_SB_.PCI0.RLED.DBG0) (20141107/utaddress-258)
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220501] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep 19 15:15:04 Intel-DH77EB kernel: [   12.220502] lpc_ich: Resource conflict(s) found affecting gpio_ich

```

I'm assuming that issue's with gpio_ich might be related to my IO issues but how does one troubleshoot this?

---

### Post by tgalati4 on 2015-09-20
What is the SMART status of your disk drive?

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

ACPI errors are common.  I don't think they are relevant to disk IO issues.

---

### Post by Amon_Re on 2015-09-21
All 3 disks pass (unsurprisingly, they're all pretty new), I suspect it's when multiple applications are writing/reading the btrfs system on /home (I have defrag & compress on).

Not really sure how to debug this kinda thing though, file fragmentation doesn't look to bad (assuming filefrag is reliable with btrfs).

---

### Post by tgalati4 on 2015-09-21
Boot a LiveUSB (which uses ext4), install *darktable* and run some tests.  This will be an entirely RAM session, no disks involved, so you can determine how long it takes to perform typical operations.  

I don't run [btrfs]("http://https://help.ubuntu.com/community/btrfs"), so I can't help troubleshoot.  I'm sure you had a good reason for choosing btrfs--one that did not include slow disk IO.

You could file a bug against it if it is repeatable behavior.  Some think it's ready for prime time:  [http://askubuntu.com/questions/572911/does-ubuntu-plan-to-move-to-btrfs-as-default-filesystem](http://askubuntu.com/questions/572911/does-ubuntu-plan-to-move-to-btrfs-as-default-filesystem)

---

### Post by Amon_Re on 2015-10-10
After some time today I've managed to pinpoint the problem, it was indeed related to btrfs but more precisely to file fragmentation in .cache, after deleting it I've noticed a gigantic increase in performance on my system, I've set .cache to nodatacow & compression on and I'll see if the problem returns but for now everything is a-ok. 

No idea why autodefrag didn't pick up on it though...

---

