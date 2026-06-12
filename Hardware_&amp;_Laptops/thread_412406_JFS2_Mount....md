---
title: "JFS2 Mount..."
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by benzies on 2007-04-18
Hi guys

Ive been attempting to mount my scsi devices.  They are currently being recognised through a scsi controller on a crappyish PC. 

So far i dont think i can see the scsi devices in dev at all.  I assume that the device is recognised under /dev/ as somthing like sca or somthing, not sure but i do know its not sda (or is it :S god help me).  

After getting past that problem (if you can help please) im trying to mount, what i think is a, jfs2 file system that used to run in a IBM server running AIX 4.3

Any help would be great.

Cheers
Benzies

---

### Post by kidders on 2007-04-18
Hi there,

Could you post your dmesg ... or if you prefer, anything else that might give an idea of what your system is/isn't doing?

---

### Post by benzies on 2007-04-18
Welll.... It salong. But whatever helps :)

You can see it there :)


#
#[17179610.188000] SCSI device sda: drive cache: write through
#[17179610.216000] SCSI device sda: 35548320 512-byte hdwr sectors (18201 MB)
#[17179610.256000] sda: Write Protect is off
#[17179610.256000] sda: Mode Sense: c3 00 00 08
#[17179610.288000] SCSI device sda: drive cache: write through
#[17179610.288000]  sda: sda2 sda3 sda4
#[17179610.304000] sd 1:0:4:0: Attached scsi disk sda
#[17179610.308000] SCSI device sdb: 35548320 512-byte hdwr sectors (18201 MB)
#

```
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Mar 13 23:32:38 UTC 2007 (Ubuntu 2.6.17-11.37-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ffd0000 (usable)
[17179569.184000]  BIOS-e820: 000000000ffd0000 - 000000000fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 0000000010000000 (usable)
[17179569.184000]  BIOS-e820: 00000000feea0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 256MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7d80
[17179569.184000] On node 0 totalpages: 65536
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61440 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000e0010
[17179569.184000] ACPI: RSDT (v001 COMPAQ CPQ0005  0x20010405  0x00000000) @ 0x000e0080
[17179569.184000] ACPI: FADT (v001 COMPAQ SOLANO   0x00000001  0x00000000) @ 0x000e0130
[17179569.184000] ACPI: SSDT (v001 COMPAQ CORE_UTL 0x00000001 MSFT 0x0100000d) @ 0x000e136c
[17179569.184000] ACPI: SSDT (v001 COMPAQ VILLTBL1 0x00000001 MSFT 0x0100000d) @ 0x000e14e0
[17179569.184000] ACPI: MADT (v001 COMPAQ SOLANO   0x00000001  0x00000000) @ 0x000e01a4
[17179569.184000] ACPI: SSDT (v001 COMPAQ     APIC 0x00000001 MSFT 0x0100000d) @ 0x000e3277
[17179569.184000] ACPI: SSDT (v001 COMPAQ PNP_PRSS 0x00000001 MSFT 0x0100000d) @ 0x000e2380
[17179569.184000] ACPI: SSDT (v001 COMPAQ       S3 0x00000001 MSFT 0x0100000d) @ 0x000e2a8b
[17179569.184000] ACPI: SSDT (v001 COMPAQ   PIDETM 0x00000001 MSFT 0x0100000d) @ 0x000e2c1f
[17179569.184000] ACPI: SSDT (v001 COMPAQ     GTF0 0x00000001 MSFT 0x0100000d) @ 0x000e2e83
[17179569.184000] ACPI: SSDT (v001 COMPAQ   SIDETM 0x00000001 MSFT 0x0100000d) @ 0x000e2d51
[17179569.184000] ACPI: SSDT (v001 COMPAQ     GTF2 0x00000001 MSFT 0x0100000d) @ 0x000e307d
[17179569.184000] ACPI: SSDT (v001 COMPAQ WN98SCSI 0x00000001 MSFT 0x0100000d) @ 0x000e334a
[17179569.184000] ACPI: DSDT (v001 COMPAQ     DSDT 0x00000001 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xf808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 17
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eeea0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdc1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 996.940 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.152000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.152000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179570.172000] Memory: 250080k/262144k available (1911k kernel code, 11368k reserved, 1073k data, 308k init, 0k highmem)
[17179570.172000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.252000] Calibrating delay using timer specific routine.. 1995.59 BogoMIPS (lpj=3991183)
[17179570.252000] Security Framework v1.0.0 initialized
[17179570.252000] SELinux:  Disabled at boot.
[17179570.252000] Mount-cache hash table entries: 512
[17179570.252000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.252000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.252000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179570.252000] CPU: L2 cache: 256K
[17179570.252000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179570.252000] Checking 'hlt' instruction... OK.
[17179570.268000] SMP alternatives: switching to UP code
[17179570.268000] Freeing SMP alternatives: 16k freed
[17179570.268000] checking if image is initramfs... it is
[17179571.240000] Freeing initrd memory: 5326k freed
[17179571.240000] ACPI: Core revision 20060707
[17179571.240000] ACPI: Looking for DSDT ... not found!
[17179571.244000] CPU0: Intel Pentium III (Coppermine) stepping 0a
[17179571.244000] Total of 1 processors activated (1995.59 BogoMIPS).
[17179571.244000] ENABLING IO-APIC IRQs
[17179571.244000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.388000] Brought up 1 CPUs
[17179571.388000] migration_cost=0
[17179571.388000] NET: Registered protocol family 16
[17179571.388000] EISA bus registered
[17179571.388000] ACPI: bus type pci registered
[17179571.388000] PCI: PCI BIOS revision 2.10 entry at 0xe838d, last bus=2
[17179571.388000] PCI: Using configuration type 1
[17179571.388000] Setting up standard PCI resources
[17179571.392000] ACPI: Interpreter enabled
[17179571.392000] ACPI: Using IOAPIC for interrupt routing
[17179571.396000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[17179571.396000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11)
[17179571.396000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11)
[17179571.396000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[17179571.396000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11)
[17179571.396000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11)
[17179571.396000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[17179571.396000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11)
[17179571.400000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.400000] PCI: Probing PCI hardware (bus 00)
[17179571.400000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.400000] PCI quirk: region f800-f87f claimed by ICH4 ACPI/GPIO/TCO
[17179571.400000] PCI quirk: region fa00-fa3f claimed by ICH4 GPIO
[17179571.400000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.400000] Boot video device is 0000:01:00.0
[17179571.400000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.400000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.404000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[17179571.408000] ACPI: Power Resource [X1PR] (on)
[17179571.412000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.412000] pnp: PnP ACPI init
[17179571.416000] pnp: PnP ACPI: found 15 devices
[17179571.416000] PnPBIOS: Disabled by ACPI PNP
[17179571.420000] PCI: Using ACPI for IRQ routing
[17179571.420000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.616000] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[17179571.616000] pnp: 00:0d: ioport range 0x400-0x41f has been reserved
[17179571.616000] pnp: 00:0d: ioport range 0x420-0x43f has been reserved
[17179571.616000] pnp: 00:0d: ioport range 0x440-0x45f has been reserved
[17179571.616000] pnp: 00:0d: ioport range 0x460-0x47f could not be reserved
[17179571.616000] pnp: 00:0d: ioport range 0xf800-0xf81f could not be reserved
[17179571.616000] pnp: 00:0d: ioport range 0xf820-0xf83f could not be reserved
[17179571.616000] pnp: 00:0d: ioport range 0xf840-0xf85f has been reserved
[17179571.616000] pnp: 00:0d: ioport range 0xf860-0xf87f has been reserved
[17179571.616000] PCI: Bridge: 0000:00:01.0
[17179571.616000]   IO window: disabled.
[17179571.616000]   MEM window: 41000000-421fffff
[17179571.616000]   PREFETCH window: 48000000-4fffffff
[17179571.616000] PCI: Bridge: 0000:00:1e.0
[17179571.616000]   IO window: 1000-1fff
[17179571.616000]   MEM window: 40000000-404fffff
[17179571.616000]   PREFETCH window: 20000000-200fffff
[17179571.616000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.616000] NET: Registered protocol family 2
[17179571.652000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179571.652000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.652000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179571.652000] TCP: Hash tables configured (established 8192 bind 4096)
[17179571.652000] TCP reno registered
[17179571.652000] audit: initializing netlink socket (disabled)
[17179571.652000] audit(1176935792.652:1): initialized
[17179571.652000] VFS: Disk quotas dquot_6.5.1
[17179571.652000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.652000] Initializing Cryptographic API
[17179571.652000] io scheduler noop registered
[17179571.652000] io scheduler anticipatory registered
[17179571.652000] io scheduler deadline registered
[17179571.652000] io scheduler cfq registered (default)
[17179571.652000] isapnp: Scanning for PnP cards...
[17179572.008000] isapnp: No Plug & Play device found
[17179572.060000] Real Time Clock Driver v1.12ac
[17179572.060000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.060000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.060000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.060000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.060000] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.064000] mice: PS/2 mouse device common for all mice
[17179572.064000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.064000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.064000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.064000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[17179572.068000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.068000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.068000] EISA: Probing bus 0 at eisa.0
[17179572.068000] Cannot allocate resource for EISA slot 1
[17179572.068000] Cannot allocate resource for EISA slot 2
[17179572.068000] EISA: Detected 0 cards.
[17179572.068000] TCP bic registered
[17179572.068000] NET: Registered protocol family 1
[17179572.068000] NET: Registered protocol family 8
[17179572.068000] NET: Registered protocol family 20
[17179572.068000] Using IPI No-Shortcut mode
[17179572.068000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.068000] Freeing unused kernel memory: 308k freed
[17179572.096000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.296000] Capability LSM initialized
[17179573.372000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179574.272000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[17179574.272000] ICH2: chipset revision 2
[17179574.272000] ICH2: not 100% native mode: will probe irqs later
[17179574.272000]     ide0: BM-DMA at 0x2460-0x2467, BIOS settings: hda:DMA, hdb:pio
[17179574.272000]     ide1: BM-DMA at 0x2468-0x246f, BIOS settings: hdc:DMA, hdd:pio
[17179574.272000] Probing IDE interface ide0...
[17179575.016000] hda: HL-DT-ST RW/DVD GCC-4520B, ATAPI CD/DVD-ROM drive
[17179575.688000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.688000] Probing IDE interface ide1...
[17179575.976000] hdc: Maxtor 98196H8, ATA DISK drive
[17179576.648000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.684000] hda: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.684000] Uniform CD-ROM driver Revision: 3.20
[17179576.700000] hdc: max request size: 128KiB
[17179576.708000] hdc: Host Protected Area detected.
[17179576.708000]       current capacity is 160075441 sectors (81958 MB)
[17179576.708000]       native  capacity is 160086528 sectors (81964 MB)
[17179576.708000] hdc: Host Protected Area disabled.
[17179576.708000] hdc: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.708000] hdc: cache flushes not supported
[17179576.708000]  hdc: hdc1 hdc2 < hdc5 > hdc3
[17179577.016000] SCSI subsystem initialized
[17179577.024000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 21 (level, low) -> IRQ 169
[17179577.036000] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[17179577.036000]         <Adaptec 2940 Ultra SCSI adapter>
[17179577.036000]         aic7880: Ultra Wide Channel A, SCSI Id=7, 16/253 SCBs
[17179577.036000] 
[17179577.036000] ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 18 (level, low) -> IRQ 177
[17179592.256000] scsi1 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[17179592.256000]         <Adaptec 29160 Ultra160 SCSI adapter>
[17179592.256000]         aic7892: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
[17179592.256000] 
[17179592.476000] usbcore: registered new driver usbfs
[17179592.476000] usbcore: registered new driver hub
[17179592.480000] USB Universal Host Controller Interface driver v3.0
[17179592.480000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 185
[17179592.480000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[17179592.480000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[17179592.480000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 1
[17179592.480000] uhci_hcd 0000:00:1f.4: irq 185, io base 0x00002440
[17179592.480000] usb usb1: configuration #1 chosen from 1 choice
[17179592.480000] hub 1-0:1.0: USB hub found
[17179592.480000] hub 1-0:1.0: 2 ports detected
[17179592.628000] Attempting manual resume
[17179592.668000] kjournald starting.  Commit interval 5 seconds
[17179592.668000] EXT3-fs: mounted filesystem with ordered data mode.
[17179593.292000]   Vendor: IBM       Model: DNES-318350W      Rev: SAGU
[17179593.292000]   Type:   Direct-Access                      ANSI SCSI revision: 03
[17179593.292000] scsi1:A:4:0: Tagged Queuing enabled.  Depth 8
[17179593.292000]  target1:0:4: Beginning Domain Validation
[17179593.328000]  target1:0:4: wide asynchronous
[17179593.340000]  target1:0:4: FAST-20 WIDE SCSI 40.0 MB/s ST (50 ns, offset 31)
[17179593.356000]  target1:0:4: Domain Validation skipping write tests
[17179593.356000]  target1:0:4: Ending Domain Validation
[17179593.904000]   Vendor: IBM       Model: DNES-318350W      Rev: SAGU
[17179593.904000]   Type:   Direct-Access                      ANSI SCSI revision: 03
[17179593.904000] scsi1:A:8:0: Tagged Queuing enabled.  Depth 8
[17179593.904000]  target1:0:8: Beginning Domain Validation
[17179593.940000]  target1:0:8: wide asynchronous
[17179593.952000]  target1:0:8: FAST-20 WIDE SCSI 40.0 MB/s ST (50 ns, offset 31)
[17179593.964000]  target1:0:8: Domain Validation skipping write tests
[17179593.964000]  target1:0:8: Ending Domain Validation
[17179607.044000] FDC 0 is a post-1991 82077
[17179607.200000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179607.212000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179607.256000] hw_random: RNG not detected
[17179607.892000] input: ImPS/2 Generic Wheel Mouse as /class/input/input1
[17179608.260000] Linux agpgart interface v0.101 (c) Dave Jones
[17179608.264000] agpgart: Detected an Intel i815 Chipset.
[17179608.268000] agpgart: AGP aperture is 64M @ 0x50000000
[17179608.632000] parport: PnPBIOS parport detected.
[17179608.632000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179608.728000] input: PC Speaker as /class/input/input2
[17179609.040000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179609.040000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179609.040000] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 193
[17179609.128000] e100: eth0: e100_probe: addr 0x40100000, irq 193, MAC addr 00:02:A5:84:B8:CC
[17179609.368000] nvidia: module license 'NVIDIA' taints kernel.
[17179609.376000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 177
[17179609.380000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7184  Tue Aug  1 18:38:58 PDT 2006
[17179609.708000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[17179609.708000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179609.756000] SCSI device sda: 35548320 512-byte hdwr sectors (18201 MB)
[17179609.760000] ts: Compaq touchscreen protocol output
[17179609.860000] sda: Write Protect is off
[17179609.860000] sda: Mode Sense: c3 00 00 08
[17179610.024000] intel8x0_measure_ac97_clock: measured 56169 usecs
[17179610.024000] intel8x0: clocking to 41162
[17179610.188000] SCSI device sda: drive cache: write through
[17179610.216000] SCSI device sda: 35548320 512-byte hdwr sectors (18201 MB)
[17179610.256000] sda: Write Protect is off
[17179610.256000] sda: Mode Sense: c3 00 00 08
[17179610.288000] SCSI device sda: drive cache: write through
[17179610.288000]  sda: sda2 sda3 sda4
[17179610.304000] sd 1:0:4:0: Attached scsi disk sda
[17179610.308000] SCSI device sdb: 35548320 512-byte hdwr sectors (18201 MB)
[17179610.352000] sdb: Write Protect is off
[17179610.352000] sdb: Mode Sense: c3 00 00 08
[17179610.384000] SCSI device sdb: drive cache: write through
[17179610.420000] SCSI device sdb: 35548320 512-byte hdwr sectors (18201 MB)
[17179610.468000] sdb: Write Protect is off
[17179610.468000] sdb: Mode Sense: c3 00 00 08
[17179610.500000] SCSI device sdb: drive cache: write through
[17179610.500000]  sdb: sdb2 sdb3 sdb4
[17179610.504000] sd 1:0:8:0: Attached scsi disk sdb
[17179610.536000] sd 1:0:4:0: Attached scsi generic sg0 type 0
[17179610.536000] sd 1:0:8:0: Attached scsi generic sg1 type 0
[17179610.920000] lp0: using parport0 (interrupt-driven).
[17179610.996000] fuse init (API version 7.6)
[17179611.068000] Adding 2048248k swap on /dev/disk/by-uuid/7c2d147b-114b-4f45-9065-b7babcfd0e29.  Priority:-1 extents:1 across:2048248k
[17179611.164000] EXT3 FS on hdc1, internal journal
[17179611.352000] NET: Registered protocol family 17
[17179611.504000] kjournald starting.  Commit interval 5 seconds
[17179611.512000] EXT3 FS on hdc3, internal journal
[17179611.512000] EXT3-fs: mounted filesystem with ordered data mode.
[17179618.724000] ACPI: Power Button (FF) [PWRF]
[17179618.724000] ACPI: Power Button (CM) [PBTN]
[17179618.936000] ibm_acpi: ec object not found
[17179618.988000] pcc_acpi: loading...
[17179621.928000] NET: Registered protocol family 10
[17179621.928000] lo: Disabled Privacy Extensions
[17179621.928000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179621.928000] IPv6 over IPv4 tunneling driver
[17179624.172000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179624.172000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179624.172000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179624.636000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179624.636000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179624.636000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179626.796000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179626.796000] apm: overridden by ACPI.
[17179666.228000] /dev/vmmon[4679]: Module vmmon: registered with major=10 minor=165
[17179666.228000] /dev/vmmon[4679]: Module vmmon: initialized
[17179667.848000] /dev/vmnet: open called by PID 4708 (vmnet-bridge)
[17179667.848000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179667.848000] /dev/vmnet: port on hub 0 successfully opened
[17179667.848000] bridge-eth0: enabling the bridge
[17179667.848000] bridge-eth0: up
[17179667.848000] bridge-eth0: already up
[17179667.848000] bridge-eth0: attached
[17179667.908000] /dev/vmnet: open called by PID 4714 (vmnet-netifup)
[17179667.908000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179667.908000] /dev/vmnet: port on hub 1 successfully opened
[17179667.924000] /dev/vmnet: open called by PID 4720 (vmnet-netifup)
[17179667.924000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179667.924000] /dev/vmnet: port on hub 8 successfully opened
[17179667.952000] /dev/vmnet: open called by PID 4724 (vmnet-natd)
[17179667.952000] /dev/vmnet: port on hub 8 successfully opened
[17179668.264000] /dev/vmnet: open called by PID 4756 (vmnet-dhcpd)
[17179668.264000] /dev/vmnet: port on hub 1 successfully opened
[17179668.556000] /dev/vmnet: open called by PID 4757 (vmnet-dhcpd)
[17179668.556000] /dev/vmnet: port on hub 8 successfully opened
[17179668.620000] Bluetooth: Core ver 2.8
[17179668.620000] NET: Registered protocol family 31
[17179668.620000] Bluetooth: HCI device and connection manager initialized
[17179668.620000] Bluetooth: HCI socket layer initialized
[17179668.680000] Bluetooth: L2CAP ver 2.8
[17179668.680000] Bluetooth: L2CAP socket layer initialized
[17179668.812000] Bluetooth: RFCOMM socket layer initialized
[17179668.812000] Bluetooth: RFCOMM TTY layer initialized
[17179668.812000] Bluetooth: RFCOMM ver 1.7
[17179678.608000] vmnet1: no IPv6 routers present
[17179678.660000] vmnet8: no IPv6 routers present
[17179736.236000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179736.236000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17179751.164000] eth0: no IPv6 routers present
```

---

### Post by kidders on 2007-04-19
Thanks for that. :-) It looks as though you've got...

[LIST]
[*]Primary IDE interface: Optical drive @ /dev/hda
[*]Secondary IDE interface: 80GB Maxtor HDD @ /dev/hdc
[*]SCSI interface: 20GB HDD @ /dev/sda
[*]SCSI interface: 20GB HDD @ /dev/sdb
[/LIST]

Your SCSI devices each seem to have 3 partitions, so why Ubuntu won't mount them for you is a bit of a mystery. I wonder what kind of partition table is on them. :-k

What's the output of **sudo fdisk -l /dev/sda** ?

Assuming **fdisk** recognises the partition table, you could try manually mounting each of the partitions. Presumably it won't work, but what your Ubuntu complains about would be useful.

---

### Post by benzies on 2007-04-19
LOL, i see there is a little humour in Ubuntu.


fdisk -l /dev/sda

        There is a valid AIX label on this disk.
        Unfortunately Linux cannot handle these
        disks at the moment.  Nevertheless some
        advice:
        1. fdisk will destroy its contents on write.
        2. Be sure that this disk is NOT a still vital
           part of a volume group. (Otherwise you may
           erase the other disks as well, if unmirrored.)
        3. Before deleting this physical volume be sure
           to remove the disk logically from your AIX
           machine.  (Otherwise you become an AIXpert).

Disk /dev/sda: 18.2 GB, 18200739840 bytes
256 heads, 63 sectors/track, 2204 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by kidders on 2007-04-19
Oh dear. I suspected there might be reason to worry about the partition tables. Unfortunately, afaik there's nothing more you can do. :-(

---

### Post by benzies on 2007-04-20
Damn. Thanks for trying though.  Ill just format them and go on with my next project.

Speaking of which, you wouldnt know how to install ubuntu on a IBM Rs/6000 h80 7014 enterprise server would you?

---

### Post by kidders on 2007-04-20
I'm afraid my IBM knowledge is very limited. Is the installer failing?

---

### Post by benzies on 2007-04-21
Wait, change that to a 7026-h80 server.  Its not that its failing, its more of like wtf do i do?  I have almost tried every ubuntu CD available. I would have thought it would have worked with the PPC veriosn but it didnt, tried the normal (x86) but that didnt work.  

I checked the sms menu (or bios for most pc user) and it does say that it boots to scsi cdrom as a second boot.  Floppy being the first.

I just cant understand why it wouldnt even bother to tell me anything really.  It's kinda confusing in many ways... :S

---

### Post by benzies on 2007-04-21
This is the best info i can find about it. :)


    *
      Product Information

IBM RS/6000 7026-H80 - PPC RS64 III 450 MHz
General

Type: Server

Recommended Use: Corporate business

Product Form Factor: Tower - 5U

Built-in Devices: Led panel

Server Scalability: 6-way

Internal Bays Qty: 2

Front Accessible Bays Qty: 3

Width: 44.5 cm

Depth: 82 cm

Height: 21.8 cm

Weight: 52 kg

Colour: Black
Processor

Type: IBM PowerPC RS64 III 450 MHz

64-bit Computing: Yes

Installed Qty: 1

Max Supported Qty: 6

Upgradability: Upgradeable
Cache memory

Type: L2 Cache

Installed Size: 2 MB
Ram

Installed Size: 256 MB / 8 GB (max)

Technology: SDRAM - ECC

Access Time: 10 ns

Form Factor: DIMM 200-PIN

Upgrade Rule: 2 modules at a time
Storage controller

Type: 1 x SCSI - integrated - PCI

Controller Interface Type: Fast Wide SCSI
Storage

Floppy Drive: 3.5" 1.44 MB floppy

Hard Drive: 1 x 9.1 GB - hot-swap - Fast Wide SCSI

Hard Drive (2nd): None
	
Optical storage

Type: CD-ROM - SCSI

Read Speed: 32x

Media Load Type: Tray
Monitor

Monitor Type: None
Input device

Type: Mouse, keyboard
Networking

Networking: Network adapter - PCI - integrated

Data Link Protocol: Ethernet

Network / Transport Protocol: TCP/IP, IPX/SPX

Compliant Standards: IEEE 802.3, IEEE 802.5
Expansion / connectivity

Expansion Bays Total (Free):

    * 2 ( 1 ) x internal - 3.5" x 1/3H
    * 2 ( 1 ) x front accessible - 5.25" x 1/2H
    * 1 ( 0 ) x front accessible - 3.5" x 1/3H

Expansion Slots Total (Free):

    * 10 ( 10 ) x PCI 64 hot-plug 66 MHz
    * 1 ( 1 ) x memory board
    * 6 ( 5 ) x processor
    * 8 ( 6 ) x memory - DIMM 200-PIN
    * 4 ( 4 ) x PCI 64 hot-plug 33 MHz

Interfaces:
Miscellaneous

Compliant Standards: Plug and Play
Power

Device Type: Power supply

Voltage Required: AC 220 V ± 10% ( 50/60 Hz )

Compliant Standards: EPA Energy Star
Operating system / software

OS Provided: IBM AIX 4.3.3

---

### Post by kidders on 2007-04-21
I've been learning more about your hardware, and it seems that you were on the right track when you tried a PPC installation. Unfortunately, most PPC Linux installers are aimed at Macs, not IBMs, so they will tend not to work without some tweaks. I've seen suggestions that Debian can be made to install on IBM PPC64s. Since Ubuntu is Debian-based, it seems sensible to suggest that getting it to install *should* be possible ... although I would probably try an old release first.

To be honest, if I had your box, I wouldn't bother with Ubuntu at all though. I'd opt for a Linux distro that is *designed* to be highly architecture-specific in the first place ... Gentoo, for example.

How much Linux experience do you have?

---

### Post by benzies on 2007-04-22
Hrm. I have been using the ubuntu OS for about 6 or so months.  

I have a couple of guides to remind me how to use advanced commands in linux.  Being as, once i have the system running there is no real need to try and configure anything else.

So i guess my real experience isnt great, but the forum's should answer any questions i have :)

I did however find this website

[http://www.debian.org/ports/powerpc/inst/prep](http://www.debian.org/ports/powerpc/inst/prep)

Tell us what you think.

---

### Post by kidders on 2007-04-22
> **benzies said:**
> I have a couple of guides to remind me how to use advanced commands in linux.  Being as, once i have the system running there is no real need to try and configure anything else.Hmm... Perhaps something as involved as Gentoo wouldn't be appropriate for you. The main reason I asked that experience question is that the more "hardcore" Linux distros might give you better control over the performance of your box ... but if you don't think of yourself as a guru (hehe) they might just be more trouble than they're worth.

> **benzies said:**
>  [http://www.debian.org/ports/powerpc/inst/prep](http://www.debian.org/ports/powerpc/inst/prep)

Tell us what you think.Seems promising. There's certainly nothing lost in trying! One thing worth factoring into your choice of distro is the ready availability of applications that will run (and run *well*) on your platform, once the OS is installed. Not having checked, I'm not sure there aren't big differences from one distribution to the next.

---

