---
title: "CDROM won't mount on VAIO laptop"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by Sha-baz on 2006-12-31
When I try to open my 'CD-ROM 1' I get the error: 'unable to mount the selected volume'. Details are 'mount: special device /dev/hdb does not exist
. My CD-ROM is however attached as primary slave... The CD-ROM is still recognized by my BIOS at startup, so no worries there. Here's what I did so far:
 
I checked if the right modules were loaded using *lsmod*,
They were not loaded, so I loaded them using '*sudo modprob cdrom*' and '*sudo modprob ide_cd*', then I check *lsmod* again, to find that they are now loaded:
 
```

Module                  Size  Used by
[COLOR="Red"]ide_cd                 33696  0 
cdrom                  38944  1 ide_cd[/COLOR]
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
etc...

```
 
Good, now something should show up in my *dmesg* output:
 
```

[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[17179569.184000]  BIOS-e820: 000000001f6e0000 - 000000001f6ea000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001f6ea000 - 000000001f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 502MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 128736
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124640 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7520
[17179569.184000] ACPI: RSDT (v001   Sony       J1 0x20050311 PTL  0x00000000) @ 0x1f6e58d2
[17179569.184000] ACPI: MADT (v001   Sony       J1 0x20050311 PTL  0x0000005f) @ 0x1f6e9e78
[17179569.184000] ACPI: FADT (v002   Sony       J1 0x20050311 PTL  0x0000005f) @ 0x1f6e9ee0
[17179569.184000] ACPI: BOOT (v001   Sony       J1 0x20050311 PTL  0x00000001) @ 0x1f6e9fd8
[17179569.184000] ACPI: MCFG (v001   Sony       J1 0x20050311 PTL  0x0000005f) @ 0x1f6e9f9c
[17179569.184000] ACPI: SSDT (v001   Sony       J1 0x20050311 PTL  0x20030224) @ 0x1f6e618f
[17179569.184000] ACPI: SSDT (v001   Sony       J1 0x20050311 PTL  0x20030224) @ 0x1f6e5d4a
[17179569.184000] ACPI: SSDT (v001   Sony       J1 0x20050311 PTL  0x20030224) @ 0x1f6e5b2f
[17179569.184000] ACPI: SSDT (v001   Sony       J1 0x20050311 PTL  0x20030224) @ 0x1f6e5916
[17179569.184000] ACPI: DSDT (v001   Sony       J1 0x20050311 PTL  0x20030224) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1729.355 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.056000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.056000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.068000] Memory: 499304k/514944k available (1910k kernel code, 15084k reserved, 1069k data, 308k init, 0k highmem)
[17179570.068000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.148000] Calibrating delay using timer specific routine.. 3463.77 BogoMIPS (lpj=6927546)
[17179570.148000] Security Framework v1.0.0 initialized
[17179570.148000] SELinux:  Disabled at boot.
[17179570.148000] Mount-cache hash table entries: 512
[17179570.148000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179570.148000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179570.148000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.148000] CPU: L2 cache: 2048K
[17179570.148000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000180 00000000 00000000
[17179570.148000] Checking 'hlt' instruction... OK.
[17179570.164000] SMP alternatives: switching to UP code
[17179570.164000] Freeing SMP alternatives: 16k freed
[17179570.164000] checking if image is initramfs... it is
[17179570.748000] Freeing initrd memory: 6870k freed
[17179570.748000] ACPI: Core revision 20060707
[17179570.748000] ACPI: Looking for DSDT ... not found!
[17179570.784000] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[17179570.784000] Total of 1 processors activated (3463.77 BogoMIPS).
[17179570.784000] ENABLING IO-APIC IRQs
[17179570.784000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.928000] Brought up 1 CPUs
[17179570.928000] migration_cost=0
[17179570.928000] NET: Registered protocol family 16
[17179570.928000] EISA bus registered
[17179570.928000] ACPI: bus type pci registered
[17179570.928000] PCI: Using MMCONFIG
[17179570.928000] Setting up standard PCI resources
[17179570.936000] ACPI: Interpreter enabled
[17179570.936000] ACPI: Using IOAPIC for interrupt routing
[17179570.948000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.948000] PCI: Probing PCI hardware (bus 00)
[17179570.952000] Boot video device is 0000:00:02.0
[17179570.952000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179570.952000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[17179570.952000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.952000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.952000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[17179570.952000] Please report the result to linux-kernel to fix this permanently
[17179570.952000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.956000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.956000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[17179570.960000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[17179570.960000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[17179570.960000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[17179570.960000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[17179570.960000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179570.960000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[17179570.960000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[17179570.960000] ACPI: Embedded Controller [EC] (gpe 23) interrupt mode.
[17179571.060000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.060000] pnp: PnP ACPI init
[17179571.060000] pnp: PnP ACPI: found 8 devices
[17179571.060000] PnPBIOS: Disabled by ACPI PNP
[17179571.060000] PCI: Using ACPI for IRQ routing
[17179571.060000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.060000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.060000] PCI: Bus 7, cardbus bridge: 0000:06:03.0
[17179571.060000]   IO window: 00002400-000024ff
[17179571.060000]   IO window: 00002800-000028ff
[17179571.060000]   PREFETCH window: 30000000-31ffffff
[17179571.060000]   MEM window: 34000000-35ffffff
[17179571.060000] PCI: Bridge: 0000:00:1e.0
[17179571.060000]   IO window: 2000-2fff
[17179571.060000]   MEM window: b0100000-b01fffff
[17179571.060000]   PREFETCH window: 30000000-31ffffff
[17179571.060000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.060000] PCI: Enabling device 0000:06:03.0 (0000 -> 0003)
[17179571.060000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179571.060000] NET: Registered protocol family 2
[17179571.096000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.096000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179571.096000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.096000] TCP: Hash tables configured (established 16384 bind 8192)
[17179571.096000] TCP reno registered
[17179571.096000] Simple Boot Flag at 0x36 set to 0x1
[17179571.096000] audit: initializing netlink socket (disabled)
[17179571.096000] audit(1167508047.096:1): initialized
[17179571.096000] VFS: Disk quotas dquot_6.5.1
[17179571.096000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.096000] Initializing Cryptographic API
[17179571.096000] io scheduler noop registered
[17179571.096000] io scheduler anticipatory registered
[17179571.096000] io scheduler deadline registered
[17179571.096000] io scheduler cfq registered (default)
[17179571.096000] isapnp: Scanning for PnP cards...
[17179571.452000] isapnp: No Plug & Play device found
[17179571.468000] Real Time Clock Driver v1.12ac
[17179571.468000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.472000] mice: PS/2 mouse device common for all mice
[17179571.472000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.472000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.472000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.472000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.472000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.476000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.480000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.480000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.480000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.480000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.480000] EISA: Probing bus 0 at eisa.0
[17179571.480000] Cannot allocate resource for EISA slot 1
[17179571.480000] Cannot allocate resource for EISA slot 2
[17179571.480000] EISA: Detected 0 cards.
[17179571.480000] TCP bic registered
[17179571.480000] NET: Registered protocol family 1
[17179571.480000] NET: Registered protocol family 8
[17179571.480000] NET: Registered protocol family 20
[17179571.480000] Using IPI No-Shortcut mode
[17179571.480000] ACPI: (supports S0 S3 S4 S5)
[17179571.484000] Freeing unused kernel memory: 308k freed
[17179572.088000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.552000] Capability LSM initialized
[17179573.576000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179573.576000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.576000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179573.576000] ACPI: Getting cpuindex for acpiid 0x1
[17179573.576000] ACPI: Thermal Zone [THRM] (74 C)
[17179573.824000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179573.824000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[17179573.824000] ICH6: chipset revision 3
[17179573.824000] ICH6: not 100% native mode: will probe irqs later
[17179573.824000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[17179573.824000] Probing IDE interface ide0...
[17179580.180000] hda: HTS721010G9AT00, ATA DISK drive
[17179602.920000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179603.244000] hda: max request size: 512KiB
[17179603.248000] hda: 195371568 sectors (100030 MB) w/7539KiB Cache, CHS=16383/255/63, UDMA(100)
[17179603.248000] hda: cache flushes supported
[17179603.248000]  hda: hda1 hda2 < hda5 hda6 > hda3
[17179604.304000] Probing IDE interface ide1...
[17179604.324000] usbcore: registered new driver usbfs
[17179604.324000] usbcore: registered new driver hub
[17179604.324000] USB Universal Host Controller Interface driver v3.0
[17179604.324000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179604.324000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179604.324000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179604.324000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179604.324000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x00001820
[17179604.324000] usb usb1: configuration #1 chosen from 1 choice
[17179604.328000] hub 1-0:1.0: USB hub found
[17179604.328000] hub 1-0:1.0: 2 ports detected
[17179604.388000] ieee1394: Initialized config rom entry `ip1394'
[17179604.548000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179604.548000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179604.548000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179604.548000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179604.548000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x00001840
[17179604.548000] usb usb2: configuration #1 chosen from 1 choice
[17179604.548000] hub 2-0:1.0: USB hub found
[17179604.548000] hub 2-0:1.0: 2 ports detected
[17179604.816000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179604.816000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179604.816000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179604.816000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179604.816000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x00001860
[17179604.816000] usb usb3: configuration #1 chosen from 1 choice
[17179604.816000] hub 3-0:1.0: USB hub found
[17179604.816000] hub 3-0:1.0: 2 ports detected
[17179605.020000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179605.020000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179605.020000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179605.020000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179605.020000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x00001880
[17179605.020000] usb usb4: configuration #1 chosen from 1 choice
[17179605.020000] hub 4-0:1.0: USB hub found
[17179605.020000] hub 4-0:1.0: 2 ports detected
[17179605.184000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 185
[17179605.184000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179605.184000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179605.184000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179605.184000] ehci_hcd 0000:00:1d.7: debug port 1
[17179605.184000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179605.184000] ehci_hcd 0000:00:1d.7: irq 185, io mem 0xb0004000
[17179605.188000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179605.188000] usb usb5: configuration #1 chosen from 1 choice
[17179605.188000] hub 5-0:1.0: USB hub found
[17179605.188000] hub 5-0:1.0: 8 ports detected
[17179605.368000] ACPI: PCI Interrupt 0000:06:03.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179605.416000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[b0104000-b01047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179606.720000] Attempting manual resume
[17179606.756000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179606.756000] EXT3-fs: write access will be enabled during recovery.
[17179606.940000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301e547dc]
[17179607.024000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179607.220000] usb 1-1: configuration #1 chosen from 1 choice
[17179607.228000] usbcore: registered new driver hiddev
[17179607.244000] input: Logitech Optical USB Mouse as /class/input/input1
[17179607.244000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
[17179607.244000] usbcore: registered new driver usbhid
[17179607.244000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179608.724000] kjournald starting.  Commit interval 5 seconds
[17179608.724000] EXT3-fs: hda3: orphan cleanup on readonly fs
[17179609.008000] ext3_orphan_cleanup: deleting unreferenced inode 424435
[17179609.012000] EXT3-fs: hda3: 1 orphan inode deleted
[17179609.012000] EXT3-fs: recovery complete.
[17179609.264000] EXT3-fs: mounted filesystem with ordered data mode.
[17179621.612000] Linux agpgart interface v0.101 (c) Dave Jones
[17179621.656000] hw_random: RNG not detected
[17179621.852000] agpgart: Detected an Intel 915GM Chipset.
[17179621.856000] agpgart: Detected 7932K stolen memory.
[17179621.872000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179622.076000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179622.076000] Yenta: CardBus bridge found at 0000:06:03.0 [104d:818f]
[17179622.076000] Yenta: Enabling burst memory read transactions
[17179622.076000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179622.076000] Yenta: Routing CardBus interrupts to PCI
[17179622.076000] Yenta TI: socket 0000:06:03.0, mfunc 0x01001b22, devctl 0x64
[17179622.312000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 169
[17179622.312000] Socket status: 30000006
[17179622.312000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[17179622.312000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179622.312000] cs: IO port probe 0x2000-0x2fff: clean.
[17179622.312000] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[17179622.312000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179622.604000] input: PS/2 Mouse as /class/input/input2
[17179622.624000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179622.728000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179622.728000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179622.728000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179622.760000] e100: eth0: e100_probe: addr 0xb0107000, irq 201, MAC addr 00:01:4A:60:D4:EE
[17179623.304000] ieee80211_crypt: registered algorithm 'NULL'
[17179623.308000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[17179623.308000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179623.308000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179623.576000] ts: Compaq touchscreen protocol output
[17179623.668000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179623.668000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179623.796000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179623.796000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179623.796000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179623.964000] cs: IO port probe 0x100-0x3af: clean.
[17179624.048000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179624.052000] cs: IO port probe 0x820-0x8ff: clean.
[17179624.052000] cs: IO port probe 0xc00-0xcf7: clean.
[17179624.052000] cs: IO port probe 0xa00-0xaff: clean.
[17179624.612000] NET: Registered protocol family 17
[17179628.708000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179628.708000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179628.752000] NET: Registered protocol family 10
[17179629.144000] lo: Disabled Privacy Extensions
[17179629.144000] IPv6 over IPv4 tunneling driver
[17179629.144000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[17179630.036000] ieee80211_crypt: registered algorithm 'WEP'
[17179630.576000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179630.980000] lp: driver loaded but no devices found
[17179631.020000] SCSI subsystem initialized
[17179631.036000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179631.036000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179631.052000] Adding 1092348k swap on /dev/disk/by-uuid/97a9a5be-5d25-445f-8e95-e00d31b020ab.  Priority:-1 extents:1 across:1092348k
[17179631.624000] EXT3 FS on hda3, internal journal
[17179631.924000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179631.968000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17179631.968000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179631.968000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179631.968000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
[17179635.080000] ACPI: AC Adapter [ADP1] (on-line)
[17179635.116000] ACPI: Battery Slot [BAT0] (battery present)
[17179635.132000] ACPI: Power Button (FF) [PWRF]
[17179635.132000] ACPI: Lid Switch [LID0]
[17179635.132000] ACPI: Power Button (CM) [PWRB]
[17179636.172000] ibm_acpi: ec object not found
[17179636.904000] pcc_acpi: loading...
[17179636.924000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[17179637.912000] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[17179637.912000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179640.240000] eth1: no IPv6 routers present
[17179641.244000] [drm] Initialized drm 1.0.1 20051102
[17179641.244000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179641.244000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179642.200000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179642.200000] apm: overridden by ACPI.
[17179647.560000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[17179647.564000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[17179647.564000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[17179647.564000] sonypi: device allocated minor is 62
[17179647.632000] input: Sony Vaio Jogdial as /class/input/input4
[17179647.748000] input: Sony Vaio Keys as /class/input/input5
[17179647.860000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 647)
[17179647.908000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 658)
[17179647.952000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 660)
[17179648.000000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 647)
[17179648.124000] Bluetooth: Core ver 2.8
[17179648.124000] NET: Registered protocol family 31
[17179648.124000] Bluetooth: HCI device and connection manager initialized
[17179648.124000] Bluetooth: HCI socket layer initialized
[17179648.136000] Bluetooth: L2CAP ver 2.8
[17179648.136000] Bluetooth: L2CAP socket layer initialized
[17179648.156000] Bluetooth: RFCOMM socket layer initialized
[17179648.156000] Bluetooth: RFCOMM TTY layer initialized
[17179648.156000] Bluetooth: RFCOMM ver 1.7

```
 
Maybe I just don't see it, but is the device in here somewhere?
It should be, right? Anyway, it still doesn't mount...
 
Does anyone know what I might try to resolve this problem?

---

### Post by thegom on 2007-03-04
I am having the exact same problem on my vaio laptop. Anyone?

---

### Post by ed.granada on 2007-03-13
There are LOTS of forum threads on the net, with lots of people, with the same problem... and I can´t still find a solution!!! I have a HP COMPAQ laptop, and my problem is the same. My post (entire error log and different tries) is:

[http://www.ubuntuforums.org/showthread.php?t=382538](http://www.ubuntuforums.org/showthread.php?t=382538)

I´m gettin desperated!!!

---

