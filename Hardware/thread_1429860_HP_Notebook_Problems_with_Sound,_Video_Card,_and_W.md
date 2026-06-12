---
title: "HP Notebook Problems with Sound, Video Card, and Wireless Card  :("
date: 2010-03-14
forum: Hardware
---

### Post by cusinmex on 2010-03-14
Hello forum,

I have an HP Pavilion dv4-2012la laptop and like other dv4 models
I've come across some issues with the sound, video, and wireless.
[U]
[COLOR="Red"]Sound[/COLOR]
[/U]
I got the sound fixed today, but it seems like it's not adjusted well,
I mean that if I decrease the Master Volume for example to 50%, I get no sound as if it were lowered down all the way to 0% :S. In order for me to hear sound , I have to increase it to about 70% and it will be at normal sound, if I increase it to 100%  it will be sort of loud.
[U][COLOR="Red"]
Video[/COLOR][/U]so
As for the video, I have not been able to find any solutions, Ive tried
downloading driver for my ATI Mobility Radeon HD 4200, and well
when I activated it, the usual graphical corruption comes up after
restarting the system.
[U][COLOR="Red"]
Wireless[/COLOR][/U]

As for the wireless, I can't find anything.
I can only connect directly through the cable
but no wireless.  :(

Any ideas or solutions?


:frown:

---

### Post by teejayevans on 2010-03-14
You might want to post some more info, like:
lspci -v
dmesg

Tom

---

### Post by cusinmex on 2010-03-14
```
pepelalo@pepelalo-laptop:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: 92300000-924fffff
	Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00006fff
	Memory behind bridge: 91300000-922fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: 91200000-912fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: 91100000-911fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 70000000-700fffff
	Prefetchable memory behind bridge: 0000000091000000-00000000910fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 2298
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at 92508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at 92507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at 92506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at 92508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 92505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 92504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at 92508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at 92500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at 92400000 (32-bit, non-prefetchable) [size=64K]
	Memory at 92300000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:05.1 Audio device: ATI Technologies Inc Device 970f
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 92410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 3040
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at 91100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, fast devsel, latency 0, IRQ 2297
	I/O ports at 2000 [size=256]
	Memory at 91010000 (64-bit, prefetchable) [size=4K]
	Memory at 91000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 91020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8101, r8169

```

---

### Post by cusinmex on 2010-03-14
dmesg:


```
 disabled.
[    0.697010] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.697621] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.698230] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.698900] ACPI: WMI: Mapper loaded
[    0.700125] SCSI subsystem initialized
[    0.700174] libata version 3.00 loaded.
[    0.700174] usbcore: registered new interface driver usbfs
[    0.700174] usbcore: registered new interface driver hub
[    0.700174] usbcore: registered new device driver usb
[    0.700174] PCI: Using ACPI for IRQ routing
[    0.704040] Bluetooth: Core ver 2.13
[    0.708036] NET: Registered protocol family 31
[    0.708054] Bluetooth: HCI device and connection manager initialized
[    0.708089] Bluetooth: HCI socket layer initialized
[    0.708122] NET: Registered protocol family 8
[    0.708155] NET: Registered protocol family 20
[    0.708199] NetLabel: Initializing
[    0.708231] NetLabel:  domain hash size = 128
[    0.708264] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.708308] NetLabel:  unlabeled traffic allowed by default
[    0.708365] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 2303, 0
[    0.708541] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.712040] hpet: hpet2 irq 2303 for MSI
[    0.712093] AppArmor: AppArmor Filesystem Enabled
[    0.716034] Switched to high resolution mode on CPU 0
[    0.716046] Switched to high resolution mode on CPU 1
[    0.721089] pnp: PnP ACPI init
[    0.721179] ACPI: bus type pnp registered
[    0.773665] pnp: PnP ACPI: found 12 devices
[    0.773736] ACPI: ACPI bus type pnp unregistered
[    0.773772] PnPBIOS: Disabled by ACPI PNP
[    0.773815] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.773850] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.773891] system 00:08: ioport range 0x400-0x4cf has been reserved
[    0.773926] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.773960] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.773995] system 00:08: ioport range 0x680-0x6ff has been reserved
[    0.774029] system 00:08: ioport range 0x77a-0x77a has been reserved
[    0.774063] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.774098] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.774132] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.774167] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.774201] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.774235] system 00:08: ioport range 0xcd0-0xcdb has been reserved
[    0.774276] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.774311] system 00:09: iomem range 0xffe00000-0xffffffff has been reserved
[    0.809222] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.809257] pci 0000:00:01.0:   IO window: 0x7000-0x7fff
[    0.809292] pci 0000:00:01.0:   MEM window: 0x92300000-0x924fffff
[    0.809327] pci 0000:00:01.0:   PREFETCH window: 0x00000080000000-0x0000008fffffff
[    0.809366] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.809401] pci 0000:00:04.0:   IO window: 0x3000-0x6fff
[    0.809436] pci 0000:00:04.0:   MEM window: 0x91300000-0x922fffff
[    0.809470] pci 0000:00:04.0:   PREFETCH window: 0x00000090000000-0x00000090ffffff
[    0.809509] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08
[    0.809542] pci 0000:00:05.0:   IO window: disabled
[    0.809578] pci 0000:00:05.0:   MEM window: 0x91200000-0x912fffff
[    0.809612] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.809648] pci 0000:00:06.0: PCI bridge, secondary bus 0000:09
[    0.809682] pci 0000:00:06.0:   IO window: disabled
[    0.809716] pci 0000:00:06.0:   MEM window: 0x91100000-0x911fffff
[    0.809750] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.809786] pci 0000:00:07.0: PCI bridge, secondary bus 0000:0a
[    0.809822] pci 0000:00:07.0:   IO window: 0x2000-0x2fff
[    0.809856] pci 0000:00:07.0:   MEM window: 0x70000000-0x700fffff
[    0.809892] pci 0000:00:07.0:   PREFETCH window: 0x00000091000000-0x000000910fffff
[    0.809931] pci 0000:00:14.4: PCI bridge, secondary bus 0000:0b
[    0.809964] pci 0000:00:14.4:   IO window: disabled
[    0.810001] pci 0000:00:14.4:   MEM window: disabled
[    0.810036] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.810078] pci 0000:00:01.0: setting latency timer to 64
[    0.810086] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.810121] pci 0000:00:04.0: setting latency timer to 64
[    0.810126] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.810161] pci 0000:00:05.0: setting latency timer to 64
[    0.810166] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.810201] pci 0000:00:06.0: setting latency timer to 64
[    0.810206] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.810241] pci 0000:00:07.0: setting latency timer to 64
[    0.810248] bus: 00 index 0 io port: [0x00-0xffff]
[    0.810281] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.810315] bus: 01 index 0 io port: [0x7000-0x7fff]
[    0.810349] bus: 01 index 1 mmio: [0x92300000-0x924fffff]
[    0.810383] bus: 01 index 2 mmio: [0x80000000-0x8fffffff]
[    0.810416] bus: 01 index 3 mmio: [0x0-0x0]
[    0.810450] bus: 02 index 0 io port: [0x3000-0x6fff]
[    0.810483] bus: 02 index 1 mmio: [0x91300000-0x922fffff]
[    0.810517] bus: 02 index 2 mmio: [0x90000000-0x90ffffff]
[    0.810550] bus: 02 index 3 mmio: [0x0-0x0]
[    0.810583] bus: 08 index 0 mmio: [0x0-0x0]
[    0.810616] bus: 08 index 1 mmio: [0x91200000-0x912fffff]
[    0.810649] bus: 08 index 2 mmio: [0x0-0x0]
[    0.810682] bus: 08 index 3 mmio: [0x0-0x0]
[    0.810715] bus: 09 index 0 mmio: [0x0-0x0]
[    0.810748] bus: 09 index 1 mmio: [0x91100000-0x911fffff]
[    0.810782] bus: 09 index 2 mmio: [0x0-0x0]
[    0.810814] bus: 09 index 3 mmio: [0x0-0x0]
[    0.810847] bus: 0a index 0 io port: [0x2000-0x2fff]
[    0.810881] bus: 0a index 1 mmio: [0x70000000-0x700fffff]
[    0.810914] bus: 0a index 2 mmio: [0x91000000-0x910fffff]
[    0.810948] bus: 0a index 3 mmio: [0x0-0x0]
[    0.810980] bus: 0b index 0 mmio: [0x0-0x0]
[    0.811013] bus: 0b index 1 mmio: [0x0-0x0]
[    0.811046] bus: 0b index 2 mmio: [0x0-0x0]
[    0.811079] bus: 0b index 3 io port: [0x00-0xffff]
[    0.811112] bus: 0b index 4 mmio: [0x000000-0xffffffff]
[    0.811155] NET: Registered protocol family 2
[    0.821181] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.821444] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.821954] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.822263] TCP: Hash tables configured (established 131072 bind 65536)
[    0.822332] TCP reno registered
[    0.825159] NET: Registered protocol family 1
[    0.825304] checking if image is initramfs... it is
[    1.374453] Freeing initrd memory: 7385k freed
[    1.374519] Simple Boot Flag at 0x44 set to 0x1
[    1.374726] cpufreq: No nForce2 chipset.
[    1.374872] audit: initializing netlink socket (disabled)
[    1.374951] type=2000 audit(1268601421.373:1): initialized
[    1.382616] highmem bounce pool size: 64 pages
[    1.382656] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.383905] VFS: Disk quotas dquot_6.5.1
[    1.384017] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.385254] fuse init (API version 7.10)
[    1.385355] msgmni has been set to 1704
[    1.385577] alg: No test for stdrng (krng)
[    1.385623] io scheduler noop registered
[    1.385657] io scheduler anticipatory registered
[    1.385690] io scheduler deadline registered
[    1.385735] io scheduler cfq registered (default)
[    1.560105] pci 0000:01:05.0: Boot video device
[    1.560317] _OSC request fails
[    1.613806] _OSC request fails
[    1.665731] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.665756] pcieport-driver 0000:00:04.0: found MSI capability
[    1.665845] pcieport-driver 0000:00:04.0: irq 2302 for MSI/MSI-X
[    1.665852] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.665867] pci_express 0000:00:04.0:pcie02: allocate port service
[    1.665877] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.665910] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.665932] pcieport-driver 0000:00:05.0: found MSI capability
[    1.666013] pcieport-driver 0000:00:05.0: irq 2301 for MSI/MSI-X
[    1.666021] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.666033] pci_express 0000:00:05.0:pcie02: allocate port service
[    1.666042] pci_express 0000:00:05.0:pcie03: allocate port service
[    1.666075] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.666097] pcieport-driver 0000:00:06.0: found MSI capability
[    1.666178] pcieport-driver 0000:00:06.0: irq 2300 for MSI/MSI-X
[    1.666185] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.666195] pci_express 0000:00:06.0:pcie03: allocate port service
[    1.666228] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.666249] pcieport-driver 0000:00:07.0: found MSI capability
[    1.666330] pcieport-driver 0000:00:07.0: irq 2299 for MSI/MSI-X
[    1.666337] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.666346] pci_express 0000:00:07.0:pcie03: allocate port service
[    1.666389] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.666553] _OSC request fails
[    1.666665] _OSC request fails
[    1.666693] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.670655] ACPI: AC Adapter [ACAD] (on-line)
[    2.123671] ACPI: Battery Slot [BAT0] (battery present)
[    2.123869] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.123906] ACPI: Power Button (FF) [PWRF]
[    2.123974] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.124011] ACPI: Power Button (CM) [PWRB]
[    2.124077] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.124115] ACPI: Sleep Button (CM) [SLPB]
[    2.124195] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    2.124409] ACPI: Lid Switch [LID]
[    2.124791] ACPI: processor limited to max C-state 1
[    2.124883] processor ACPI_CPU:00: registered as cooling_device0
[    2.124945] ACPI: Processor [C000] (supports 8 throttling states)
[    2.125074] processor ACPI_CPU:01: registered as cooling_device1
[    2.231524] thermal LNXTHERM:01: registered as thermal_zone0
[    2.290450] ACPI: Thermal Zone [TZ01] (59 C)
[    2.290557] isapnp: Scanning for PnP cards...
[    2.673734] isapnp: No Plug & Play device found
[    2.685315] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.686174] brd: module loaded
[    2.686469] loop: module loaded
[    2.686588] Fixed MDIO Bus: probed
[    2.686658] PPP generic driver version 2.4.2
[    2.686738] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.686830] Driver 'sd' needs updating - please use bus_type methods
[    2.686870] Driver 'sr' needs updating - please use bus_type methods
[    2.686930] ahci 0000:00:11.0: version 3.0
[    2.686943] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.687034] ahci 0000:00:11.0: irq 2298 for MSI/MSI-X
[    2.687106] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    2.687146] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.687689] scsi0 : ahci
[    2.687863] scsi1 : ahci
[    2.687980] scsi2 : ahci
[    2.688109] ata1: SATA max UDMA/133 abar m1024@0x92508000 port 0x92508100 irq 2298
[    2.688147] ata2: SATA max UDMA/133 abar m1024@0x92508000 port 0x92508180 irq 2298
[    2.688185] ata3: SATA max UDMA/133 abar m1024@0x92508000 port 0x92508200 irq 2298
[    3.172098] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.172941] ata1.00: ATA-8: TOSHIBA MK3256GSY, LH013C, max UDMA/100
[    3.172981] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.173997] ata1.00: configured for UDMA/100
[    3.672095] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.677412] ata2.00: ATAPI: hp       DVDRAM GT20L, DC05, max UDMA/100, ATAPI AN
[    3.682905] ata2.00: configured for UDMA/100
[    4.020101] ata3: SATA link down (SStatus 0 SControl 300)
[    4.036174] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3256GS LH01 PQ: 0 ANSI: 5
[    4.036337] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.036419] sd 0:0:0:0: [sda] Write Protect is off
[    4.036453] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.036471] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.036563] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.036642] sd 0:0:0:0: [sda] Write Protect is off
[    4.036676] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.036692] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.036732]  sda: sda1 sda2 < sda5 >
[    4.095223] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.095298] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.098910] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT20L     DC05 PQ: 0 ANSI: 5
[    4.110316] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.110357] Uniform CD-ROM driver Revision: 3.20
[    4.110505] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.110549] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.111209] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.111296] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.111346] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    4.111350] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    4.111425] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    4.111530] ehci_hcd 0000:00:12.2: debug port 1
[    4.111578] ehci_hcd 0000:00:12.2: irq 17, io mem 0x92508500
[    4.120085] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    4.120209] usb usb1: configuration #1 chosen from 1 choice
[    4.120301] hub 1-0:1.0: USB hub found
[    4.120340] hub 1-0:1.0: 6 ports detected
[    4.120511] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.120561] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    4.120564] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.120636] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    4.120744] ehci_hcd 0000:00:13.2: debug port 1
[    4.120793] ehci_hcd 0000:00:13.2: irq 19, io mem 0x92508400
[    4.132084] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    4.132212] usb usb2: configuration #1 chosen from 1 choice
[    4.132300] hub 2-0:1.0: USB hub found
[    4.132339] hub 2-0:1.0: 6 ports detected
[    4.132469] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.132558] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.132610] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    4.132613] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    4.132683] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    4.132744] ohci_hcd 0000:00:12.0: irq 16, io mem 0x92507000
[    4.192148] usb usb3: configuration #1 chosen from 1 choice
[    4.192247] hub 3-0:1.0: USB hub found
[    4.192290] hub 3-0:1.0: 3 ports detected
[    4.192442] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.192493] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    4.192496] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    4.192565] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    4.192620] ohci_hcd 0000:00:12.1: irq 16, io mem 0x92506000
[    4.248154] usb usb4: configuration #1 chosen from 1 choice
[    4.248247] hub 4-0:1.0: USB hub found
[    4.248288] hub 4-0:1.0: 3 ports detected
[    4.248441] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.248493] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    4.248495] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.248568] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    4.248670] ohci_hcd 0000:00:13.0: irq 18, io mem 0x92505000
[    4.304152] usb usb5: configuration #1 chosen from 1 choice
[    4.304243] hub 5-0:1.0: USB hub found
[    4.304286] hub 5-0:1.0: 3 ports detected
[    4.304443] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.304494] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    4.304497] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.304567] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    4.304620] ohci_hcd 0000:00:13.1: irq 18, io mem 0x92504000
[    4.360148] usb usb6: configuration #1 chosen from 1 choice
[    4.360244] hub 6-0:1.0: USB hub found
[    4.360288] hub 6-0:1.0: 3 ports detected
[    4.360447] uhci_hcd: USB Universal Host Controller Interface driver
[    4.360554] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.406457] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.406500] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.409152] mice: PS/2 mouse device common for all mice
[    4.429222] rtc_cmos 00:04: RTC can wake from S4
[    4.429294] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.429354] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    4.429448] device-mapper: uevent: version 1.0.3
[    4.429627] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.429835] device-mapper: multipath: version 1.0.5 loaded
[    4.429870] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.430027] EISA: Probing bus 0 at eisa.0
[    4.430071] Cannot allocate resource for EISA slot 2
[    4.430105] Cannot allocate resource for EISA slot 3
[    4.430142] Cannot allocate resource for EISA slot 4
[    4.430176] Cannot allocate resource for EISA slot 5
[    4.430212] Cannot allocate resource for EISA slot 6
[    4.430246] Cannot allocate resource for EISA slot 7
[    4.430279] Cannot allocate resource for EISA slot 8
[    4.430314] EISA: Detected 0 cards.
[    4.430442] cpuidle: using governor ladder
[    4.430477] cpuidle: using governor menu
[    4.430948] TCP cubic registered
[    4.431095] NET: Registered protocol family 10
[    4.431487] lo: Disabled Privacy Extensions
[    4.431824] NET: Registered protocol family 17
[    4.431904] Bluetooth: L2CAP ver 2.11
[    4.431938] Bluetooth: L2CAP socket layer initialized
[    4.431972] Bluetooth: SCO (Voice Link) ver 0.6
[    4.432006] Bluetooth: SCO socket layer initialized
[    4.432111] Bluetooth: RFCOMM socket layer initialized
[    4.432148] Bluetooth: RFCOMM TTY layer initialized
[    4.432181] Bluetooth: RFCOMM ver 1.10
[    4.432273] powernow-k8: Found 1 AMD Athlon(tm) II Dual-Core M300 processors (2 cpu cores) (version 2.20.00)
[    4.432967] powernow-k8:    0 : pstate 0 (2000 MHz)
[    4.433042] powernow-k8:    1 : pstate 1 (1400 MHz)
[    4.433076] powernow-k8:    2 : pstate 2 (800 MHz)
[    4.433267] Using IPI No-Shortcut mode
[    4.433401] registered taskstats version 1
[    4.433576]   Magic number: 2:979:297
[    4.433770] rtc_cmos 00:04: setting system clock to 2010-03-14 21:17:05 UTC (1268601425)
[    4.433808] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.433842] EDD information not available.
[    4.434080] Freeing unused kernel memory: 532k freed
[    4.434288] Write protecting the kernel text: 4120k
[    4.434384] Write protecting the kernel read-only data: 1524k
[    4.455885] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.517363] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    4.651389] usb 1-6: configuration #1 chosen from 1 choice
[    4.785442] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.785554] r8169 0000:0a:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.785671] r8169 0000:0a:00.0: setting latency timer to 64
[    4.785794] r8169 0000:0a:00.0: irq 2297 for MSI/MSI-X
[    4.786365] eth0: RTL8102e at 0xf7cd6000, 00:26:22:ae:77:ca, XID 24c00000 IRQ 2297
[    4.992179] PM: Starting manual resume from disk
[    4.992214] PM: Resume from partition 8:5
[    4.992216] PM: Checking hibernation image.
[    4.992502] PM: Resume from disk failed.
[    5.001173] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.001212] EXT3-fs: write access will be enabled during recovery.
[    5.136093] usb 3-3: new low speed USB device using ohci_hcd and address 2
[    5.179183] kjournald starting.  Commit interval 5 seconds
[    5.179199] EXT3-fs: recovery complete.
[    5.179766] EXT3-fs: mounted filesystem with ordered data mode.
[    5.306193] usb 3-3: configuration #1 chosen from 1 choice
[    5.572093] usb 5-1: new full speed USB device using ohci_hcd and address 2
[    5.746165] usb 5-1: configuration #1 chosen from 1 choice
[    6.012080] usb 5-2: new full speed USB device using ohci_hcd and address 3
[    6.173149] usb 5-2: configuration #1 chosen from 1 choice
[   11.022914] udev: starting version 141
[   11.168582] acpi device:05: registered as cooling_device2
[   11.168961] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input6
[   11.178540] lis3lv02d: laptop model unknown, using default axes configuration
[   11.184189] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.187363] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
[   11.190239] lis3lv02d driver loaded.
[   11.226980] leds-hp-disk driver loaded.
[   11.256396] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.316316] usbcore: registered new interface driver hiddev
[   11.321096] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input8
[   11.349186] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:12.0-3/input0
[   11.349288] usbcore: registered new interface driver usbhid
[   11.349339] usbhid: v2.6:USB HID core driver
[   11.358060] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.401456] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   11.403326] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   11.403496] usbcore: registered new interface driver btusb
[   11.408734] Linux agpgart interface v0.103
[   11.577412] Linux video capture interface: v2.00
[   11.679767] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.768689] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.797416] [fglrx] Maximum main memory to use for locked dma buffers: 1642 MBytes.
[   11.797512] [fglrx]   vendor: 1002 device: 9712 count: 1
[   11.797861] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   11.797932] pci 0000:01:05.0: power state changed by ACPI to D0
[   11.797971] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.798007] pci 0000:01:05.0: setting latency timer to 64
[   11.798475] [fglrx] Driver built-in PAT support is enabled successfully
[   11.801201] uvcvideo: Found UVC 1.00 device HP Webcam (090c:137b)
[   11.801372] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
[   11.802769] input: HP Webcam as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6:1.0/input/input10
[   11.809223] usbcore: registered new interface driver uvcvideo
[   11.809281] USB Video Class driver (v0.1.0)
[   12.047454] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.047636] HDA Intel 0000:00:14.2: setting latency timer to 64
[   12.119273] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.119383] HDA Intel 0000:01:05.1: irq 2296 for MSI/MSI-X
[   12.119402] HDA Intel 0000:01:05.1: setting latency timer to 64
[   12.133131] APIC error on CPU1: 00(08)
[   12.133139] APIC error on CPU0: 00(08)
[   12.551863] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input11
[   12.676119] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12
[   13.137003] hda_intel: No response from codec, disabling MSI: last cmd=0x000f0000
[   14.141009] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   14.409375] lp: driver loaded but no devices found
[   14.475487] Adding 5269280k swap on /dev/sda5.  Priority:-1 extents:1 across:5269280k
[   14.982129] EXT3 FS on sda1, internal journal
[   15.384450] type=1505 audit(1268601436.447:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2100
[   15.430271] type=1505 audit(1268601436.495:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2104
[   15.430380] type=1505 audit(1268601436.495:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2104
[   15.430420] type=1505 audit(1268601436.495:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2104
[   15.430455] type=1505 audit(1268601436.495:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2104
[   15.563068] type=1505 audit(1268601436.627:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2109
[   15.563225] type=1505 audit(1268601436.627:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2109
[   15.589130] type=1505 audit(1268601436.655:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2113
[  132.893814] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  132.893817] Bluetooth: BNEP filters: protocol multicast
[  132.901895] Bridge firewalling registered
[  133.793301] ppdev: user-space parallel port driver
[  137.934949] r8169: eth0: link down
[  137.935160] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  146.804236] ACPI: EC: missing confirmations, switch off interrupt mode.
[  159.504859] usb 3-3: USB disconnect, address 2
[  166.156059] usb 3-3: new low speed USB device using ohci_hcd and address 3
[  166.324184] usb 3-3: configuration #1 chosen from 1 choice
[  166.331305] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input13
[  166.346005] generic-usb 0003:045E:0040.0002: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:12.0-3/input0
[  197.484693] r8169: eth0: link up
[  197.485398] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  208.389055] eth0: no IPv6 routers present
[ 1189.658392] r8169: eth0: link down
[ 1496.253637] r8169: eth0: link up
[11462.203752] Too big adjustment 32
[15613.992095] usb 1-2: new high speed USB device using ehci_hcd and address 5
[15614.131090] usb 1-2: configuration #1 chosen from 1 choice
[15614.166871] Initializing USB Mass Storage driver...
[15614.168850] scsi3 : SCSI emulation for USB Mass Storage devices
[15614.169371] usbcore: registered new interface driver usb-storage
[15614.169379] USB Mass Storage support registered.
[15614.169847] usb-storage: device found at 5
[15614.169852] usb-storage: waiting for device to settle before scanning
[15619.168378] usb-storage: device scan complete
[15619.223559] scsi 3:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[15620.555065] sd 3:0:0:0: [sdb] 7837696 512-byte hardware sectors: (4.01 GB/3.73 GiB)
[15620.555746] sd 3:0:0:0: [sdb] Write Protect is off
[15620.555755] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[15620.555761] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[15620.560290] sd 3:0:0:0: [sdb] 7837696 512-byte hardware sectors: (4.01 GB/3.73 GiB)
[15620.560947] sd 3:0:0:0: [sdb] Write Protect is off
[15620.560955] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[15620.560960] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[15620.560972]  sdb: sdb1
[15620.606645] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[15620.606766] sd 3:0:0:0: Attached scsi generic sg2 type 0
[16814.449482] r8169: eth0: link down
[17675.237288] r8169: eth0: link up
[17851.156424] usb 1-2: USB disconnect, address 5

```

---

### Post by leorolla on 2010-03-15
I suggest you open one thread at the appropriate forum for each issue.

If you are not in a rush, fix problems one by one, starting from the most critical :)

---

### Post by cusinmex on 2010-03-16
well right now, its more of the wireless than anything
else cause its urgent.

i can live without compiz and decent sound

but i need wireless internet :(

---

### Post by Greenwidth on 2010-03-16
Have you tried installing the backports to get the wireless working?
```
sudo apt-get install linux-backports-modules-karmic
```
and reboot.

NB if you're not using karmic, change the ending to your version.

---

### Post by cusinmex on 2010-03-16
Thanks This Solved It!!

Cheers from Mexico


Viva Linux!!!  :D

---

### Post by devildoc5 on 2010-03-16
I know this has been marked solved, but just in case anyone else is having these issues I would just like to point them to: [http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html)  

Should have just about everything you need...

---

