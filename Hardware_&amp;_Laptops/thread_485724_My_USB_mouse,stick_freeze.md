---
title: "My USB mouse,stick freeze"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by obavjestenja on 2007-06-27
My USB mouse,stick freeze all the time,please help :(

---

### Post by obavjestenja on 2007-06-27
guys help please:p

---

### Post by obavjestenja on 2007-06-27
please:(

---

### Post by elsaturnino on 2007-06-27
Could you give us a little more info on the problem? Does your computer hang? Do the mouse/stick stop working permanently or just for short periods of time?

---

### Post by obavjestenja on 2007-06-27
> **elsaturnino said:**
> Could you give us a little more info on the problem? Does your computer hang? Do the mouse/stick stop working permanently or just for short periods of time?

my computer continue to work(laptop LG) just  muuse usb and usb stick stop to work an i need to restart to get usb mouse and stick to work again.

---

### Post by elsaturnino on 2007-06-27
Run the following command after they freeze up and post the output here:

```
dmesg | tail
```

---

### Post by obavjestenja on 2007-06-28
> **elsaturnino said:**
> Run the following command after they freeze up and post the output here:

```
dmesg | tail
```



pika@pika-laptop:~$ dmesg | tail
[  883.820000] [fglrx] total      GART = 130023424
[  883.820000] [fglrx] free       GART = 114032640
[  883.820000] [fglrx] max single GART = 114032640
[  883.820000] [fglrx] total      LFB  = 134217728
[  883.820000] [fglrx] free       LFB  = 122679296
[  883.820000] [fglrx] max single LFB  = 122679296
[  883.820000] [fglrx] total      Inv  = 0
[  883.820000] [fglrx] free       Inv  = 0
[  883.820000] [fglrx] max single Inv  = 0
[  883.820000] [fglrx] total      TIM  = 0

---

### Post by obavjestenja on 2007-06-28
what now :D

---

### Post by elsaturnino on 2007-06-29
That didn't seem to net anything interesting. Just run the "dmesg" command (again, right after they freeze up) and post the output here (make sure to wrap it in CODE to increase the readability).

---

### Post by obavjestenja on 2007-06-29
> **elsaturnino said:**
> That didn't seem to net anything interesting. Just run the "dmesg" command (again, right after they freeze up) and post the output here (make sure to wrap it in CODE to increase the readability).


please help:D


pika@pika-laptop:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000004000 end: 00000000000d4000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000037da0000 end: 0000000037ea0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000037ea0000 size: 0000000000012000 end: 0000000037eb2000 type: 3
[    0.000000] copy_e820_map() start: 0000000037eb2000 size: 000000000004e000 end: 0000000037f00000 type: 4
[    0.000000] copy_e820_map() start: 0000000037f00000 size: 0000000000100000 end: 0000000038000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ea0000 - 0000000037eb2000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037eb2000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 894MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f70b0
[    0.000000] Entering add_active_range(0, 0, 229024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229024
[    0.000000]   HighMem    229024 ->   229024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229024
[    0.000000] On node 0 totalpages: 229024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1757 pages used for memmap
[    0.000000]   Normal zone: 223171 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7120
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x37eac0c9
[    0.000000] ACPI: FADT (v001 LGE    DEBORAH  0x06040000 LGE  0x000f4240) @ 0x37eb1ef6
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x37eb1f6a
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x37eb1fc4
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x37eac522
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x37eac307
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x37eac105
[    0.000000] ACPI: DSDT (v001    LGE DEBORAH  0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:a8000000)
[    0.000000] Detected 1733.273 MHz processor.
[   10.642534] Built 1 zonelists.  Total pages: 227235
[   10.642547] Kernel command line: root=UUID=3bea3f4d-b0fb-4279-9c18-44b5ee86037e ro quiet splash
[   10.642902] mapped APIC to ffffd000 (fee00000)
[   10.642904] mapped IOAPIC to ffffc000 (fec00000)
[   10.642908] Enabling fast FPU save and restore... done.
[   10.642919] Enabling unmasked SIMD FPU exception support... done.
[   10.642940] Initializing CPU#0
[   10.643105] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   10.645165] Console: colour VGA+ 80x25
[   10.646515] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.647888] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.699370] Memory: 897080k/916096k available (1992k kernel code, 18452k reserved, 900k data, 328k init, 0k highmem)
[   10.699389] virtual kernel memory layout:
[   10.699398]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   10.699400]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.699401]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.699402]     lowmem  : 0xc0000000 - 0xf7ea0000   ( 894 MB)
[   10.699403]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   10.699405]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   10.699415]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   10.699418] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.778960] Calibrating delay using timer specific routine.. 3478.94 BogoMIPS (lpj=6957884)
[   10.779043] Security Framework v1.0.0 initialized
[   10.779060] SELinux:  Disabled at boot.
[   10.779094] Mount-cache hash table entries: 512
[   10.779387] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[   10.779417] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.779420] CPU: L2 cache: 2048K
[   10.779432] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[   10.779450] Compat vDSO mapped to ffffe000.
[   10.779454] Remapping vsyscall page to ffffe000
[   10.779483] Checking 'hlt' instruction... OK.
[   10.795123] SMP alternatives: switching to UP code
[   10.795482] Freeing SMP alternatives: 11k freed
[   10.795841] Early unpacking initramfs... done
[   11.488659] ACPI: Core revision 20060707
[   11.501706] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   11.512311] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[   11.512362] Total of 1 processors activated (3478.94 BogoMIPS).
[   11.512722] ENABLING IO-APIC IRQs
[   11.513035] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.552920] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   11.553009] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   11.553020] ...trying to set up timer as Virtual Wire IRQ... works.
[   11.697934] Brought up 1 CPUs
[   11.698425] Booting paravirtualized kernel on bare hardware
[   11.698605] Time: 16:58:14  Date: 05/29/107
[   11.698658] NET: Registered protocol family 16
[   11.698833] EISA bus registered
[   11.698837] ACPI: bus type pci registered
[   11.699313] PCI: PCI BIOS revision 2.10 entry at 0xfd84d, last bus=14
[   11.699324] PCI: Using configuration type 1
[   11.699325] Setting up standard PCI resources
[   11.710528] ACPI: Interpreter enabled
[   11.710539] ACPI: Using IOAPIC for interrupt routing
[   11.712069] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.712084] PCI: Probing PCI hardware (bus 00)
[   11.714956] Boot video device is 0000:01:05.0
[   11.716416] PCI: Transparent bridge - 0000:00:14.4
[   11.716648] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.720111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   11.722958] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   11.723473] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   11.723966] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   11.724456] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   11.724946] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   11.725447] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   11.725984] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   11.726475] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   11.833937] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   11.834665] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   11.835774] ACPI: Power Resource [CTHT] (off)
[   11.835935] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.835951] pnp: PnP ACPI init
[   11.839794] pnp: PnP ACPI: found 10 devices
[   11.839799] PnPBIOS: Disabled by ACPI PNP
[   11.839880] PCI: Using ACPI for IRQ routing
[   11.839891] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.915704] NET: Registered protocol family 8
[   11.915715] NET: Registered protocol family 20
[   11.916090] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   11.916094] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   11.916105] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   11.916108] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   11.916110] pnp: 00:08: ioport range 0xc00-0xc01 has been reserved
[   11.916625] PCI: Bridge: 0000:00:01.0
[   11.916627]   IO window: 9000-9fff
[   11.916640]   MEM window: c0100000-c01fffff
[   11.916643]   PREFETCH window: d0000000-dfffffff
[   11.916647] PCI: Bridge: 0000:00:07.0
[   11.916658]   IO window: a000-afff
[   11.916661]   MEM window: c0200000-c02fffff
[   11.916673]   PREFETCH window: disabled.
[   11.916679] PCI: Bus 9, cardbus bridge: 0000:08:00.0
[   11.916689]   IO window: 00002000-000020ff
[   11.916695]   IO window: 00002400-000024ff
[   11.916710]   PREFETCH window: 40000000-43ffffff
[   11.916725]   MEM window: 44000000-47ffffff
[   11.916740] PCI: Bridge: 0000:00:14.4
[   11.916743]   IO window: 2000-2fff
[   11.916759]   MEM window: c0300000-c03fffff
[   11.916773]   PREFETCH window: 40000000-43ffffff
[   11.916812] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   11.916876] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 20 (level, low) -> IRQ 16
[   11.916925] NET: Registered protocol family 2
[   11.953664] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.953971] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.955658] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.956717] TCP: Hash tables configured (established 131072 bind 65536)
[   11.956720] TCP reno registered
[   11.965857] checking if image is initramfs... it is
[   13.336315] Freeing initrd memory: 6787k freed
[   13.337350] audit: initializing netlink socket (disabled)
[   13.337384] audit(1183136295.740:1): initialized
[   13.337678] VFS: Disk quotas dquot_6.5.1
[   13.337724] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.337841] io scheduler noop registered
[   13.337843] io scheduler anticipatory registered
[   13.337854] io scheduler deadline registered
[   13.337872] io scheduler cfq registered (default)
[   14.239187] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   14.239254] assign_interrupt_mode Found MSI capability
[   14.239258] Allocate Port Service[0000:00:07.0:pcie00]
[   14.239550] isapnp: Scanning for PnP cards...
[   14.601209] isapnp: No Plug & Play device found
[   14.651438] Real Time Clock Driver v1.12ac
[   14.651567] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.652955] mice: PS/2 mouse device common for all mice
[   14.654096] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.654604] input: Macintosh mouse button emulation as /class/input/input0
[   14.654685] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.654689] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.655258] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.657945] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.658883] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.658896] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.658899] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.658910] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.658912] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.659139] EISA: Probing bus 0 at eisa.0
[   14.659157] Cannot allocate resource for EISA slot 1
[   14.659160] Cannot allocate resource for EISA slot 2
[   14.659210] Cannot allocate resource for EISA slot 8
[   14.659212] EISA: Detected 0 cards.
[   14.689410] TCP cubic registered
[   14.689429] NET: Registered protocol family 1
[   14.689466] Using IPI No-Shortcut mode
[   14.689625] ACPI: (supports S0 S3 S4 S5)
[   14.689742]   Magic number: 11:319:996
[   14.689757]   hash matches device ttyd9
[   14.689774]   hash matches device ttyac
[   14.690217] Time: tsc clocksource has been installed.
[   14.690650] Freeing unused kernel memory: 328k freed
[   14.691421] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.053969] Capability LSM initialized
[   16.109905] ACPI: Transitioning device [FAN0] to D3
[   16.109908] ACPI: Transitioning device [FAN0] to D3
[   16.109911] ACPI: Fan [FAN0] (off)
[   16.118518] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.118532] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.118548] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   16.121694] ACPI: Thermal Zone [TZ1] (40 C)
[   16.746609] usbcore: registered new interface driver usbfs
[   16.746657] usbcore: registered new interface driver hub
[   16.746692] usbcore: registered new device driver usb
[   16.748124] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.748219] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[   16.748250] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   16.748584] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   16.748629] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0004000
[   16.816352] usb usb1: configuration #1 chosen from 1 choice
[   16.816419] hub 1-0:1.0: USB hub found
[   16.816440] hub 1-0:1.0: 4 ports detected
[   16.919828] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[   16.919875] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   16.919925] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   16.919961] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0005000
[   16.979851] usb usb2: configuration #1 chosen from 1 choice
[   16.979915] hub 2-0:1.0: USB hub found
[   16.979937] hub 2-0:1.0: 4 ports detected
[   17.083779] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[   17.083825] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   17.083864] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   17.083976] ehci_hcd 0000:00:13.2: irq 17, io mem 0xc0006000
[   17.084006] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.084222] usb usb3: configuration #1 chosen from 1 choice
[   17.084275] hub 3-0:1.0: USB hub found
[   17.084291] hub 3-0:1.0: 8 ports detected
[   17.130664] ieee1394: Initialized config rom entry `ip1394'
[   17.189513] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   17.189565] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[   17.189596] ATIIXP: chipset revision 128
[   17.189607] ATIIXP: not 100% native mode: will probe irqs later
[   17.189626]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   17.189660]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   17.189678] Probing IDE interface ide0...
[    5.752000] Time: acpi_pm clocksource has been installed.
[    5.840000] hda: FUJITSU MHV2060AT, ATA DISK drive
[    6.200000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    6.408000] usb 1-1: configuration #1 chosen from 1 choice
[    6.432000] usbcore: registered new interface driver hiddev
[    6.436000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[    6.440000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.0-1
[    6.440000] usbcore: registered new interface driver usbhid
[    6.440000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    6.512000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    6.588000] Probing IDE interface ide1...
[    7.328000] hdc: TSSTcorpCD/DVDW TS-L632B, ATAPI CD/DVD-ROM drive
[    7.664000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.680000] SCSI subsystem initialized
[    7.692000] libata version 2.20 loaded.
[    7.696000] ACPI: PCI Interrupt 0000:08:00.2[A] -> GSI 20 (level, low) -> IRQ 16
[    7.748000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[c0309000-c03097ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.760000] hda: max request size: 128KiB
[    7.776000] hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[    7.780000] hda: cache flushes supported
[    7.780000]  hda: hda1 hda2 < hda5 >
[    7.860000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.860000] Uniform CD-ROM driver Revision: 3.20
[    8.016000] Attempting manual resume
[    8.016000] swsusp: Resume From Partition 3:5
[    8.016000] PM: Checking swsusp image.
[    8.016000] PM: Resume from disk failed.
[    8.076000] kjournald starting.  Commit interval 5 seconds
[    8.076000] EXT3-fs: mounted filesystem with ordered data mode.
[    9.020000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e091040351230d]
[   21.980000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.984000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.436000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   22.948000] Linux agpgart interface v0.102 (c) Dave Jones
[   23.604000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   23.604000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   23.604000] sky2 0000:02:00.0: v1.13 addr 0xc0200000 irq 17 Yukon-FE (0xb7) rev 1
[   23.604000] sky2 eth0: addr 00:e0:91:13:49:a1
[   23.796000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   23.836000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   24.232000] sdhci: Secure Digital Host Controller Interface driver
[   24.232000] sdhci: Copyright(c) Pierre Ossman
[   24.232000] sdhci: SDHCI controller found at 0000:08:00.4 [104c:8034] (rev 0)
[   24.232000] ACPI: PCI Interrupt 0000:08:00.4[A] -> GSI 20 (level, low) -> IRQ 16
[   24.232000] mmc0: SDHCI at 0xc030a000 irq 16 DMA
[   24.236000] mmc1: SDHCI at 0xc0309c00 irq 16 DMA
[   24.236000] mmc2: SDHCI at 0xc0309800 irq 16 DMA
[   24.500000] ACPI: PCI Interrupt 0000:08:00.3[A] -> GSI 20 (level, low) -> IRQ 16
[   24.512000] input: PC Speaker as /class/input/input4
[   24.840000] sky2 eth0: enabling interface
[   24.840000] sky2 eth0: ram buffer 4K
[   24.868000] Yenta: CardBus bridge found at 0000:08:00.0 [1854:0023]
[   24.868000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   24.868000] Yenta: Routing CardBus interrupts to PCI
[   24.868000] Yenta TI: socket 0000:08:00.0, mfunc 0x01001002, devctl 0x64
[   25.152000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[   25.152000] Socket status: 30000006
[   25.152000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   25.152000] cs: IO port probe 0x2000-0x2fff: clean.
[   25.156000] pcmcia: parent PCI bridge Memory window: 0xc0300000 - 0xc03fffff
[   25.156000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   25.160000] ACPI: PCI Interrupt 0000:08:02.0[A] -> GSI 22 (level, low) -> IRQ 19
[   25.160000] rt2500 1.1.0 BETA4 2006/06/18 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[   25.416000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[   25.416000] rt2500 EEPROM:  7  7  7  7  7  8  8  8  8  8  8  8  7  7  dBm Maximum
[   25.508000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[   25.784000] cs: IO port probe 0x100-0x3af: clean.
[   25.788000] cs: IO port probe 0x3e0-0x4ff: clean.
[   25.792000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   25.792000] cs: IO port probe 0xc00-0xcf7: excluding 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   25.796000] cs: IO port probe 0xa00-0xaff: clean.
[   26.152000] NET: Registered protocol family 17
[   26.284000] fuse init (API version 7.8)
[   26.380000] lp: driver loaded but no devices found
[   26.460000] Adding 2441840k swap on /dev/disk/by-uuid/7bcdd308-5d95-4caa-bfde-e6139efb751b.  Priority:-1 extents:1 across:2441840k
[   26.636000] EXT3 FS on hda1, internal journal
[   26.984000] NET: Registered protocol family 10
[   26.984000] lo: Disabled Privacy Extensions
[   26.984000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.292000] ACPI: Battery Slot [CMB0] (battery present)
[   33.340000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   33.396000] ibm_acpi: ec object not found
[   33.432000] No dock devices found.
[   33.568000] input: Power Button (FF) as /class/input/input5
[   33.576000] ACPI: Power Button (FF) [PWRF]
[   33.640000] input: Lid Switch as /class/input/input6
[   33.640000] ACPI: Lid Switch [LID0]
[   33.672000] input: Sleep Button (CM) as /class/input/input7
[   33.672000] ACPI: Sleep Button (CM) [SLPB]
[   33.688000] input: Power Button (CM) as /class/input/input8
[   33.688000] ACPI: Power Button (CM) [PWRB]
[   33.844000] Using specific hotkey driver
[   33.896000] ACPI: AC Adapter [AC] (on-line)
[   33.932000] wmi_add device=f685c000
[   33.932000] calling WQBA
[   34.040000] pcc_acpi: loading...
[   37.112000] ra0: no IPv6 routers present
[   42.248000] ppdev: user-space parallel port driver
[   43.372000] apm: BIOS not found.
[   43.560000] Bluetooth: Core ver 2.11
[   43.560000] NET: Registered protocol family 31
[   43.560000] Bluetooth: HCI device and connection manager initialized
[   43.560000] Bluetooth: HCI socket layer initialized
[   43.628000] Bluetooth: L2CAP ver 2.8
[   43.628000] Bluetooth: L2CAP socket layer initialized
[   43.740000] Bluetooth: RFCOMM socket layer initialized
[   43.740000] Bluetooth: RFCOMM TTY layer initialized
[   43.740000] Bluetooth: RFCOMM ver 1.8
[   46.808000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  708.992000] usb 1-1: USB disconnect, address 3
[ 2141.264000] usb 1-1: new low speed USB device using ohci_hcd and address 4
[ 2141.472000] usb 1-1: configuration #1 chosen from 1 choice
[ 2141.476000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input9
[ 2141.476000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.0-1
pika@pika-laptop:~$

---

### Post by obavjestenja on 2007-06-29
what now :D

---

### Post by obavjestenja on 2007-06-29
help i need my  mouse back:(

---

### Post by samuraiCat on 2007-06-29
> **obavjestenja said:**
> help i need my  mouse back:(

Did you try to shut down and reboot with the mouse plugged in? If not, do.

---

### Post by obavjestenja on 2007-06-29
> **samuraiCat said:**
> Did you try to shut down and reboot with the mouse plugged in? If not, do.

yes i reboot,shut down,ctrl+alt+bakspace...... but no help after couple minuts my mouse stuck again and usb stick to.
im confuse:(

---

### Post by samuraiCat on 2007-06-29
> **obavjestenja said:**
> yes i reboot,shut down,ctrl+alt+bakspace...... but no help after couple minuts my mouse stuck again and usb stick to.
im confuse:(

Have you tried to boot up in "safe" mode? Try that, too. If that doesn't work, try a different USB port.

---

### Post by obavjestenja on 2007-06-29
> **samuraiCat said:**
> Have you tried to boot up in "safe" mode? Try that, too. If that doesn't work, try a different USB port.

already try that to:(
mouse its the basic thing ,why not working?

---

### Post by obavjestenja on 2007-06-29
any idea ?

---

### Post by obavjestenja on 2007-06-30
i don't want to back to xp,vista,please try to help:(

---

### Post by elsaturnino on 2007-06-30
I would suggest trying a different mouse and see if the same problem occurs. Let me know if you can do this.

---

### Post by mbittleston on 2007-07-07
Sounds similar to the problem at post:
[http://ubuntuforums.org/showthread.php?t=189572](http://ubuntuforums.org/showthread.php?t=189572)

the following solved it for me **when using the proprietary ati accelerated graphics driver**:
```
sudo gedit /boot/grub/menu.lst
```
change the line that reads
```
# defoptions=quiet splash
```
to add "noapic"
```
# defoptions=quiet splash **noapic**
```
save, close gedit, then run
```
sudo update-grub
```
to update the boot loader, then restart. I have not tested the ethernet connection, but wireless networking and mouse seem to be working fine for my Toshiba Satellite A105 w/ Logitech mouse (ubuntu release 7.04 - feisty) since that change.
The above makes wireless unreliable (keeps dropping connection) when using **unrestricted** driver. When using **unrestricted ati graphics driver**, add "noapic" and "irqpoll" works for me:
```
# defoptions=quiet splash **noapic irqpoll**
```

---

