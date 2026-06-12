---
title: "USB problems"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by thumpa007 on 2006-06-24
I've read all I can find and I now need to ask for help.

I have installed Dapper on my JVC MP-7230 laptop (also known as an ASUS S200B) via the net - not the live CD. However I am having problems with USB devices. Every thing works fine under windows so I do not think there are hardware problems.

USB devices I've that work:
external IBM DVD drive
ipod nano

USB devices that don't work are and are not shown in lsusb:
mouse
WiFi

The mouse works fine on my desktop PC Dapper install from the Live CD.

The WiFi is built into the laptop and is connected to USB. The WiFi device is made by actiontec and uses the Prism2 chip.

lsmod shows only the ehci_hcd and ohci_hcd modules are loaded (which explains why the DVD drive and ipod works). I've used modprobe to load usbhid, prism2_usb, ndiswrapper* modules - I've not used the prism and ndis modules at the same time. Both the WiFi and mouse have power but do not work.

*I believe I have installed the appropriate driver with ndiswrapper.

What should I try next?

---

### Post by thumpa007 on 2006-06-26
Here is some more info that may help someone help me.

lsusb
```
Bus 001 Device 001: ID 0000:0000
```

lsmod | grep usb
```
usbcore               139076  3 ehci_hcd,ohci_hcd
```

lspci
```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 31)
0000:00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
0000:00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
0000:00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 88)
0000:00:09.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 88)
0000:00:09.2 System peripheral: Ricoh Co Ltd R5C576 SD Bus Host Adapter
0000:00:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:00:0f.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0f.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0f.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)
```

dmesg
```
[17179569.184000] Linux version 2.6.15-25-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000effb000 (usable)
[17179569.184000]  BIOS-e820: 000000000effb000 - 000000000efff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000efff000 - 000000000f000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 239MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 61435
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 57339 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f6330
[17179569.184000] ACPI: RSDT (v001 J2     J2       0x30303031 MSFT 0x31313031) @ 0x0effb000
[17179569.184000] ACPI: FADT (v001 J2     J2       0x30303031 MSFT 0x31313031) @ 0x0effb080
[17179569.184000] ACPI: BOOT (v001 J2     J2       0x30303031 MSFT 0x31313031) @ 0x0effb040
[17179569.184000] ACPI: DSDT (v001   JVC  J2       0x00001000 INTL 0x02002015) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xe408
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0f000000:f0ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0125e000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 930.479 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.432000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.432000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179569.456000] Memory: 232312k/245740k available (2101k kernel code, 12912k reserved, 592k data, 332k init, 0k highmem)
[17179569.456000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.536000] Calibrating delay using timer specific routine.. 1862.10 BogoMIPS (lpj=3724201)
[17179569.536000] Security Framework v1.0.0 initialized
[17179569.536000] SELinux:  Disabled at boot.
[17179569.536000] Mount-cache hash table entries: 512
[17179569.536000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.536000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.536000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.536000] CPU: L2 cache: 512K
[17179569.536000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.536000] mtrr: v2.0 (20020519)
[17179569.536000] Enabling fast FPU save and restore... done.
[17179569.536000] Enabling unmasked SIMD FPU exception support... done.
[17179569.536000] Checking 'hlt' instruction... OK.
[17179569.552000] SMP alternatives: switching to UP code
[17179569.552000] checking if image is initramfs... it is
[17179570.688000] Freeing initrd memory: 6804k freed
[17179570.740000] ACPI: Looking for DSDT ... not found!
[17179570.744000] ACPI: setting ELCR to 0200 (from 08b0)
[17179570.752000] CPU0: Intel Mobile Intel(R) Pentium(R) III CPU - M   933MHz stepping 04
[17179570.752000] SMP motherboard not detected.
[17179570.752000] Local APIC not detected. Using dummy APIC emulation.
[17179570.752000] Brought up 1 CPUs
[17179570.752000] NET: Registered protocol family 16
[17179570.752000] EISA bus registered
[17179570.752000] ACPI: bus type pci registered
[17179570.752000] PCI: PCI BIOS revision 2.10 entry at 0xf10c0, last bus=1
[17179570.752000] PCI: Using configuration type 1
[17179570.752000] ACPI: Subsystem revision 20051216
[17179570.760000] ACPI: Interpreter enabled
[17179570.760000] ACPI: Using PIC for interrupt routing
[17179570.760000] ACPI: Device [SLPB] status [0000000a]: functional but not present; setting present
[17179570.760000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.760000] PCI: Probing PCI hardware (bus 00)
[17179570.764000] Uncovering SIS18 that hid as a SIS503 (compatible=0)
[17179570.764000] Enabling SiS 96x SMBus.
[17179570.764000] Boot video device is 0000:01:00.0
[17179570.764000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.772000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 *11 14 15)
[17179570.772000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 14 15)
[17179570.772000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 14 15)
[17179570.776000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 14 15)
[17179570.776000] ACPI: Embedded Controller [EC0] (gpe 29) interrupt mode.
[17179570.780000] ACPI: Power Resource [PFAN] (off)
[17179570.780000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.780000] pnp: PnP ACPI init
[17179570.788000] pnp: PnP ACPI: found 9 devices
[17179570.788000] PnPBIOS: Disabled by ACPI PNP
[17179570.788000] PCI: Using ACPI for IRQ routing
[17179570.788000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.788000] PCI: BIOS reporting unknown device 00:48
[17179570.788000] PCI: Device 0000:00:09.1 not found by BIOS
[17179570.788000] PCI: BIOS reporting unknown device 00:78
[17179570.788000] PCI: Device 0000:00:0f.1 not found by BIOS
[17179570.792000] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[17179570.792000] pnp: 00:02: ioport range 0xe480-0xe4ff has been reserved
[17179570.792000] pnp: 00:02: ioport range 0x480-0x48f has been reserved
[17179570.792000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[17179570.792000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[17179570.792000] PCI: Bridge: 0000:00:02.0
[17179570.792000]   IO window: a000-afff
[17179570.792000]   MEM window: d2800000-d2ffffff
[17179570.792000]   PREFETCH window: d8000000-e7efffff
[17179570.792000] PCI: Bus 2, cardbus bridge: 0000:00:09.0
[17179570.792000]   IO window: 00001000-000010ff
[17179570.792000]   IO window: 00001400-000014ff
[17179570.792000]   PREFETCH window: 10000000-11ffffff
[17179570.792000]   MEM window: 12000000-13ffffff
[17179570.792000] PCI: Bus 6, cardbus bridge: 0000:00:09.1
[17179570.792000]   IO window: 00001800-000018ff
[17179570.792000]   IO window: 00001c00-00001cff
[17179570.792000]   PREFETCH window: 14000000-15ffffff
[17179570.792000]   MEM window: 16000000-17ffffff
[17179570.792000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179570.792000] **** SET: Misaligned resource pointer: cdab6da2 Type 07 Len 0
[17179570.792000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179570.792000] PCI: setting IRQ 11 as level-triggered
[17179570.792000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179570.792000] ACPI: PCI Interrupt 0000:00:09.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179570.792000] Simple Boot Flag at 0x3a set to 0x1
[17179570.792000] audit: initializing netlink socket (disabled)
[17179570.792000] audit(1151344809.788:1): initialized
[17179570.792000] VFS: Disk quotas dquot_6.5.1
[17179570.792000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.792000] Initializing Cryptographic API
[17179570.792000] io scheduler noop registered
[17179570.792000] io scheduler anticipatory registered
[17179570.792000] io scheduler deadline registered
[17179570.796000] io scheduler cfq registered
[17179570.796000] isapnp: Scanning for PnP cards...
[17179571.148000] isapnp: No Plug & Play device found
[17179571.184000] Real Time Clock Driver v1.12
[17179571.184000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.188000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.188000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.188000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.188000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.188000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.188000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.188000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.196000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.196000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.196000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.196000] mice: PS/2 mouse device common for all mice
[17179571.196000] EISA: Probing bus 0 at eisa.0
[17179571.196000] Cannot allocate resource for EISA slot 1
[17179571.196000] EISA: Detected 0 cards.
[17179571.196000] NET: Registered protocol family 2
[17179571.232000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179571.232000] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[17179571.232000] TCP bind hash table entries: 8192 (order: 4, 98304 bytes)
[17179571.232000] TCP: Hash tables configured (established 8192 bind 8192)
[17179571.232000] TCP reno registered
[17179571.232000] TCP bic registered
[17179571.232000] NET: Registered protocol family 1
[17179571.232000] NET: Registered protocol family 8
[17179571.232000] NET: Registered protocol family 20
[17179571.232000] Using IPI No-Shortcut mode
[17179571.232000] ACPI wakeup devices: 
[17179571.232000] SLPB MAC0 USB0 USB1 USB2 AUDO MODM CRD0 CRD1 
[17179571.232000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.232000] Freeing unused kernel memory: 332k freed
[17179571.340000] vga16fb: initializing
[17179571.340000] vga16fb: mapped to 0xc00a0000
[17179571.360000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.416000] Console: switching to colour frame buffer device 80x25
[17179571.416000] fb0: VGA16 VGA frame buffer device
[17179572.484000] Capability LSM initialized
[17179572.540000] ACPI: Fan [FAN] (off)
[17179572.548000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.556000] ACPI: Thermal Zone [THRM] (30 C)
[17179573.372000] SIS5513: IDE controller at PCI slot 0000:00:00.1
[17179573.372000] SIS5513: chipset revision 208
[17179573.372000] SIS5513: not 100% native mode: will probe irqs later
[17179573.372000] SIS5513: SiS630 ATA 100 (1st gen) controller
[17179573.372000]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:pio
[17179573.372000] Probing IDE interface ide0...
[17179573.664000] hda: IC25N030ATCS04-0, ATA DISK drive
[17179574.336000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.368000] hda: max request size: 128KiB
[17179574.368000] hda: 58605120 sectors (30005 MB) w/1768KiB Cache, CHS=58140/16/63, UDMA(33)
[17179574.368000] hda: cache flushes not supported
[17179574.368000]  hda: hda1 hda2 hda3 hda4 < hda5 >
[17179574.932000] ieee1394: Initialized config rom entry `ip1394'
[17179574.936000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179574.936000] **** SET: Misaligned resource pointer: ceee8b62 Type 07 Len 0
[17179574.936000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 4
[17179574.936000] PCI: setting IRQ 4 as level-triggered
[17179574.936000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKD] -> GSI 4 (level, low) -> IRQ 4
[17179574.988000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[4]  MMIO=[d2000000-d20007ff]  Max Packet=[2048]
[17179575.016000] usbcore: registered new driver usbfs
[17179575.016000] usbcore: registered new driver hub
[17179575.024000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179575.024000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179575.024000] ohci_hcd 0000:00:0f.0: OHCI Host Controller
[17179576.260000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800030a2716]
[17179583.024000] ohci_hcd 0000:00:0f.0: USB HC takeover failed!  (BIOS/SMM bug)
[17179583.024000] ohci_hcd 0000:00:0f.0: can't reset
[17179583.024000] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[17179583.024000] ohci_hcd 0000:00:0f.0: init 0000:00:0f.0 fail, -16
[17179583.024000] ohci_hcd: probe of 0000:00:0f.0 failed with error -16
[17179583.024000] **** SET: Misaligned resource pointer: ceee87a2 Type 07 Len 0
[17179583.024000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[17179583.024000] PCI: setting IRQ 7 as level-triggered
[17179583.024000] ACPI: PCI Interrupt 0000:00:0f.1[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[17179583.024000] ohci_hcd 0000:00:0f.1: OHCI Host Controller
[17179591.024000] ohci_hcd 0000:00:0f.1: USB HC takeover failed!  (BIOS/SMM bug)
[17179591.024000] ohci_hcd 0000:00:0f.1: can't reset
[17179591.024000] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[17179591.024000] ohci_hcd 0000:00:0f.1: init 0000:00:0f.1 fail, -16
[17179591.024000] ohci_hcd: probe of 0000:00:0f.1 failed with error -16
[17179591.024000] **** SET: Misaligned resource pointer: ceee80e2 Type 07 Len 0
[17179591.024000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[17179591.024000] PCI: setting IRQ 5 as level-triggered
[17179591.024000] ACPI: PCI Interrupt 0000:00:0f.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179591.024000] ehci_hcd 0000:00:0f.2: EHCI Host Controller
[17179591.048000] ehci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
[17179591.048000] ehci_hcd 0000:00:0f.2: irq 5, io mem 0xd0000000
[17179591.048000] ehci_hcd 0000:00:0f.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179591.048000] hub 1-0:1.0: USB hub found
[17179591.048000] hub 1-0:1.0: 3 ports detected
[17179591.184000] Probing IDE interface ide1...
[17179592.060000] Attempting manual resume
[17179592.084000] kjournald starting.  Commit interval 5 seconds
[17179592.084000] EXT3-fs: mounted filesystem with ordered data mode.
[17179609.852000] Linux agpgart interface v0.101 (c) Dave Jones
[17179609.864000] agpgart: Detected SiS 630 chipset
[17179609.872000] agpgart: AGP aperture is 64M @ 0xd4000000
[17179610.072000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179610.072000] Yenta: CardBus bridge found at 0000:00:09.0 [1043:1674]
[17179610.204000] Yenta: ISA IRQ mask 0x0408, PCI irq 11
[17179610.204000] Socket status: 30000006
[17179610.204000] ACPI: PCI Interrupt 0000:00:09.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179610.204000] Yenta: CardBus bridge found at 0000:00:09.1 [1043:1674]
[17179610.332000] Yenta: ISA IRQ mask 0x0408, PCI irq 11
[17179610.332000] Socket status: 30000006
[17179610.644000] sis900.c: v1.08.09 Sep. 19 2005
[17179610.644000] ACPI: PCI Interrupt 0000:00:01.1[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179610.644000] 0000:00:01.1: ICS LAN PHY transceiver found at address 1.
[17179610.664000] 0000:00:01.1: Using transceiver found at address 1 as default
[17179610.664000] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 5, 00:80:88:03:9e:77.
[17179610.792000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179610.804000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179611.084000] ACPI: PCI Interrupt 0000:00:01.4[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[17179611.476000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[17179611.492000] input: TPPS/2 IBM TrackPoint as /class/input/input1
[17179612.760000] MC'97 1 converters and GPIO not ready (0x1)
[17179612.776000] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2485kHz
[17179613.168000] ts: Compaq touchscreen protocol output
[17179613.364000] input: PC Speaker as /class/input/input2
[17179613.440000] cs: IO port probe 0x100-0x3af: clean.
[17179613.440000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179613.440000] cs: IO port probe 0x820-0x8ff: clean.
[17179613.444000] cs: IO port probe 0xc00-0xcf7: clean.
[17179613.444000] cs: IO port probe 0xa00-0xaff: clean.
[17179613.464000] cs: IO port probe 0x100-0x3af: clean.
[17179613.464000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179613.468000] cs: IO port probe 0x820-0x8ff: clean.
[17179613.468000] cs: IO port probe 0xc00-0xcf7: clean.
[17179613.468000] cs: IO port probe 0xa00-0xaff: clean.
[17179613.472000] ac97 codec read TIMEOUT [0x72/0x1c072]!!!
[17179613.496000] ac97 codec read TIMEOUT [0x54/0x1c0d4]!!!
[17179614.068000] lp: driver loaded but no devices found
[17179614.156000] SCSI subsystem initialized
[17179614.184000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179614.184000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179614.184000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179614.344000] Adding 248968k swap on /dev/hda5.  Priority:-1 extents:1 across:248968k
[17179614.476000] EXT3 FS on hda3, internal journal
[17179614.804000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179614.804000] md: bitmap version 4.39
[17179615.132000] NET: Registered protocol family 17
[17179615.984000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179616.984000] eth0: Media Link On 100mbps full-duplex 
[17179618.184000] NET: Registered protocol family 10
[17179618.184000] lo: Disabled Privacy Extensions
[17179618.184000] IPv6 over IPv4 tunneling driver
```

---

### Post by thumpa007 on 2006-06-27
I've just complied Kernel v2.6.17.1 and the mouse works and many more items showing under lsusb. I'll play with the WiFi this evening.

The SD card reader does not appear to be working. I'll play with this once I've sorted the WiFi.

Finally a step forward. :D

---

### Post by thumpa007 on 2006-06-27
Still no sign of life from WiFi.

this I what get from lsusb now


```

Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 002: ID 04f1:3009 Victor Company of Japan, Ltd
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
```

I've no idea what device 2 is on bus 1 is.

From the laptop user manual the wireless device I understand the wireless device is on bus 3.

I could really do with some help now!

---

### Post by thumpa007 on 2006-06-27
OK I tell a lie. I've just run UVCView.x86.exe in windows and this device on BUS 1 is my wireless card.

Question now is how to make it work?

---

### Post by thumpa007 on 2006-06-27
can any one make sense of this: [http://tagoh.jp/w/wiliki.cgi?InterLinkXP7230&l=en]("http://tagoh.jp/w/wiliki.cgi?InterLinkXP7230&l=en")

I tried modprobe prism2_usb but it was not found. I'm guessing I need to compile it. So I've tried compiling linux_wlan_ng but it fails. ](*,)

---

### Post by thumpa007 on 2006-07-09
It seems that linux-wlan-ng-0.2.3 will not compile with kernel version 2.6.17 due to some changes to do with Modules.symvers

I've also tried compiling the ubuntu package linux-wlan-ng-source, I can't work our why this fails.

I'm going to try Kernel 2.6.16.24

---

