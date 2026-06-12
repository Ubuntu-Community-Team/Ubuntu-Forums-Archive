---
title: "'lspci' returns nothing."
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by Ash-Fox on 2007-01-27
I've recently been asked to help someone setup Linux on their system -- I obliged and attempted to install Edgy on their system. Unfortunately, some weirdness occured where the system couldn't detect the network card.

Upon further investigation, I found that lspci couldn't find any devices at all.

I'm only particularly interested in getting the network card working and I would really appreciate it if someone could help me with this. Here is what little information I can get out of the system:

> ubuntu@ubuntu:~$ lspci
ubuntu@ubuntu:~$ lspci -vvx
ubuntu@ubuntu:~$ sudo lspci -H1
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
ubuntu@ubuntu:~$ sudo scanpci

pci bus 0x0000 cardnum 0x00 function 0x00: vendor 0x1106 device 0x3116
 VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge

pci bus 0x0000 cardnum 0x01 function 0x00: vendor 0x1106 device 0xb091
 VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]

pci bus 0x0000 cardnum 0x0e function 0x00: vendor 0x10ec device 0x8139
 Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+

pci bus 0x0000 cardnum 0x11 function 0x00: vendor 0x1106 device 0x3147
 VIA Technologies, Inc. VT8233A ISA Bridge

pci bus 0x0000 cardnum 0x11 function 0x01: vendor 0x1106 device 0x0571
 VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE

pci bus 0x0000 cardnum 0x11 function 0x02: vendor 0x1106 device 0x3038
 VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller

pci bus 0x0000 cardnum 0x11 function 0x03: vendor 0x1106 device 0x3038
 VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller

pci bus 0x0000 cardnum 0x11 function 0x05: vendor 0x1106 device 0x3059
 VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller

pci bus 0x0001 cardnum 0x00 function 0x00: vendor 0x5333 device 0x8d04
 S3 Inc. VT8375 [ProSavage8 KM266/KL266]
ubuntu@ubuntu:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000dff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000dff0000 - 000000000dff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000dff3000 - 000000000e000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 223MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6690
[17179569.184000] On node 0 totalpages: 57328
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 53232 pages, LIFO batch:15
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 VT8375                                ) @ 0x000f80e0
[17179569.184000] ACPI: RSDT (v001 VT8375 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x0dff3000
[17179569.184000] ACPI: FADT (v001 VT8375 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x0dff3040
[17179569.184000] ACPI: MADT (v001 VT8375 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x0dff6e80
[17179569.184000] ACPI: DSDT (v001 VT8375 MSI ACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 16
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 2, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 dfl dfl)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ11 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0e000000:f1ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 1612.143 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.968000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.968000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.980000] Memory: 217448k/229312k available (1910k kernel code, 11300k reserved, 1070k data, 308k init, 0k highmem)
[17179571.980000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.060000] Calibrating delay using timer specific routine.. 3227.51 BogoMIPS (lpj=6455037)
[17179572.060000] Security Framework v1.0.0 initialized
[17179572.060000] SELinux:  Disabled at boot.
[17179572.060000] Mount-cache hash table entries: 512
[17179572.060000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.060000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.060000] CPU: CLK_CTL MSR was 60031223. Reprogramming to 20031223
[17179572.060000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.060000] CPU: L2 Cache: 64K (64 bytes/line)
[17179572.060000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179572.060000] Checking 'hlt' instruction... OK.
[17179572.076000] SMP alternatives: switching to UP code
[17179572.076000] Freeing SMP alternatives: 16k freed
[17179572.076000] checking if image is initramfs... it is
[17179572.688000] Freeing initrd memory: 5524k freed
[17179572.688000] ACPI: Core revision 20060707
[17179572.696000] ACPI: Looking for DSDT ... not found!
[17179572.700000] CPU0: AMD Duron(tm) processor stepping 01
[17179572.700000] Total of 1 processors activated (3227.51 BogoMIPS).
[17179572.700000] ENABLING IO-APIC IRQs
[17179572.700000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.844000] Brought up 1 CPUs
[17179572.844000] migration_cost=0
[17179572.844000] NET: Registered protocol family 16
[17179572.844000] EISA bus registered
[17179572.844000] ACPI: bus type pci registered
[17179572.864000] PCI: PCI BIOS revision 2.10 entry at 0xfb990, last bus=1
[17179572.864000] PCI: Using configuration type 1
[17179572.864000] Setting up standard PCI resources
[17179572.884000] ACPI: Interpreter enabled
[17179572.884000] ACPI: Using IOAPIC for interrupt routing
[17179572.884000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.884000] PCI: Probing PCI hardware (bus 00)
[17179572.884000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.888000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179572.888000] Boot video device is 0000:01:00.0
[17179572.888000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.888000] ACPI Error (rscreate-0349): (PRT[1C].SourceIndex) Need Integer, found Reference [20060707]
[17179572.888000] ACPI Exception (pci_irq-0215): AE_BAD_DATA, Evaluating _PRT [AE_BAD_DATA] [20060707]
[17179572.892000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179572.892000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[17179572.892000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *9
[17179572.892000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179572.892000] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179572.892000] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[17179572.892000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[17179572.896000] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0, disabled.
[17179572.900000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.900000] pnp: PnP ACPI init
[17179572.904000] pnp: PnP ACPI: found 15 devices
[17179572.904000] PnPBIOS: Disabled by ACPI PNP
[17179572.904000] PCI: Using ACPI for IRQ routing
[17179572.904000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.904000] PCI: Bridge: 0000:00:01.0
[17179572.904000]   IO window: disabled.
[17179572.904000]   MEM window: e0000000-e1ffffff
[17179572.904000]   PREFETCH window: d8000000-dfffffff
[17179572.904000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.904000] NET: Registered protocol family 2
[17179572.932000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179572.932000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.932000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179572.932000] TCP: Hash tables configured (established 8192 bind 4096)
[17179572.932000] TCP reno registered
[17179572.932000] audit: initializing netlink socket (disabled)
[17179572.932000] audit(1169917928.932:1): initialized
[17179572.932000] VFS: Disk quotas dquot_6.5.1
[17179572.932000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.932000] Initializing Cryptographic API
[17179572.932000] io scheduler noop registered
[17179572.932000] io scheduler anticipatory registered
[17179572.932000] io scheduler deadline registered
[17179572.932000] io scheduler cfq registered (default)
[17179572.932000] isapnp: Scanning for PnP cards...
[17179573.288000] isapnp: No Plug & Play device found
[17179573.368000] Real Time Clock Driver v1.12ac
[17179573.368000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.368000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.368000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.372000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.372000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.372000] mice: PS/2 mouse device common for all mice
[17179573.372000] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[17179573.372000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.372000] ide: Assuming 50MHz system bus speed for PIO modes; override with idebus=xx
[17179573.376000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.376000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.376000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.376000] EISA: Probing bus 0 at eisa.0
[17179573.376000] Cannot allocate resource for EISA slot 1
[17179573.376000] Cannot allocate resource for EISA slot 4
[17179573.376000] EISA: Detected 0 cards.
[17179573.376000] TCP bic registered
[17179573.376000] NET: Registered protocol family 1
[17179573.376000] NET: Registered protocol family 8
[17179573.376000] NET: Registered protocol family 20
[17179573.376000] Using IPI No-Shortcut mode
[17179573.376000] ACPI: (supports S0 S1 S4 S5)
[17179573.376000] Freeing unused kernel memory: 308k freed
[17179573.408000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.616000] Capability LSM initialized
[17179574.680000] ACPI: Fan [FAN] (on)
[17179574.688000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179574.688000] ACPI: Thermal Zone [THRM] (22 C)
[17179575.648000] Probing IDE interface ide0...
[17179576.080000] hda: ST380011A, ATA DISK drive
[17179576.868000] hdb: HL-DT-ST CD-ROM GCR-8522B, ATAPI CD/DVD-ROM drive
[17179576.924000] Probing IDE interface ide1...
[17179577.496000] Probing IDE interface ide2...
[17179578.064000] Probing IDE interface ide3...
[17179578.632000] Probing IDE interface ide4...
[17179579.200000] Probing IDE interface ide5...
[17179579.768000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179579.784000] hda: max request size: 512KiB
[17179579.796000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63
[17179579.800000] hda: cache flushes supported
[17179579.800000]  hda: hda1 hda2 < hda5 >
[17179579.844000] hdb: ATAPI 52X CD-ROM drive, 128kB Cache
[17179579.844000] Uniform CD-ROM driver Revision: 3.20
[17179581.424000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179581.488000] ISO 9660 Extensions: RRIP_1991A
[17179581.548000] Registering unionfs 1.1.4
[17179581.560000] loop: loaded (max 8 devices)
[17179581.776000] squashfs: version 3.0 (2006/03/15) Phillip Lougher
[17179636.932000] input: PC Speaker as /class/input/input1
[17179637.036000] Floppy drive(s): fd0 is 1.44M
[17179637.060000] FDC 0 is a post-1991 82077
[17179637.720000] parport: PnPBIOS parport detected.
[17179637.720000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179638.452000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179638.992000] ts: Compaq touchscreen protocol output
[17179642.172000] NET: Registered protocol family 17
[17179651.484000] ACPI: Power Button (FF) [PWRF]
[17179651.484000] ACPI: Power Button (CM) [PWRB]
[17179651.484000] ACPI: Sleep Button (CM) [SLPB]
[17179651.716000] ibm_acpi: ec object not found
[17179651.784000] pcc_acpi: loading...
[17179656.180000] lp0: using parport0 (interrupt-driven).
[17179656.364000] ppdev: user-space parallel port driver
[17179669.432000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179669.432000] apm: overridden by ACPI.
[17179692.036000] Bluetooth: Core ver 2.8
[17179692.036000] NET: Registered protocol family 31
[17179692.036000] Bluetooth: HCI device and connection manager initialized
[17179692.036000] Bluetooth: HCI socket layer initialized
[17179692.336000] Bluetooth: L2CAP ver 2.8
[17179692.336000] Bluetooth: L2CAP socket layer initialized
[17179692.380000] Bluetooth: RFCOMM socket layer initialized
[17179692.380000] Bluetooth: RFCOMM TTY layer initialized
[17179692.380000] Bluetooth: RFCOMM ver 1.7
ubuntu@ubuntu:~$     



---

### Post by taurus on 2007-01-27
I see there is a build-in network card on the list, **_00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)_**.  Is that not the right one?

---

### Post by Ash-Fox on 2007-01-27
> **taurus said:**
> I see there is a build-in network card on the list, **_00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)_**.  Is that not the right one?

Yes, but that's with 'lspci -H1', that's a direct hardware lookup. The kernel doesn't detect it or anything else (which is what the vanilla 'lspci' command relies on).

---

### Post by Ash-Fox on 2007-01-27
So, would anyone happen to have any ideas on what todo?

---

