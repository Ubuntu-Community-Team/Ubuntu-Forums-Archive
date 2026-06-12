---
title: "modem driver"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by m.v.ramesh on 2007-08-16
Hi Guys !!

I've recently installed Ubuntu 7.02 Feisty Fawn on my Toshiba Laptop.
The Modem hasnt been recognised during the installation process.

As mentioned on ur website, i've run the Scanmodem tool n attached the details.

Please guide me as to how i can install the modem.

Thanks in advance.

Ramesh


ModemData.txt:-

Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
          SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_August_04


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot       PCI ID          SubsystemID     Name
 ----------     ---------       ---------       --------------
 00:1e.3        8086:266d       1179:0001       Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW

 Modem interrupt assignment and sharing:

 --- Bootup diagnostics for card in PCI slot 00:1e.3 ----
[   20.270584] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[   20.270593] ACPI: PCI interrupt for device 0000:00:1e.3 disabled

 The PCI slot 00:1e.3 of the modem card may be disabled early in
 a bootup process,  but then enabled later. If modem drivers load
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.


 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

CodecModemFile not found


dmesg.txt:-

          CPU0
 0:     829595   IO-APIC-edge      timer
 1:        255   IO-APIC-edge      i8042
 8:          3   IO-APIC-edge      rtc
 9:        848   IO-APIC-fasteoi   acpi
 12:     222950   IO-APIC-edge      i8042
 14:      36143   IO-APIC-edge      libata
 15:          0   IO-APIC-edge      libata
 16:       5571   IO-APIC-fasteoi   tifm_7xx1, Intel ICH6
 17:     362222   IO-APIC-fasteoi   uhci_hcd:usb4, yenta, i915@pci:0000:00:02.0
 19:       1418   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 20:      17666   IO-APIC-fasteoi   uhci_hcd:usb2, libata, sdhci:slot0, sdhci:slot1, sdhci:slot2
 21:          1   IO-APIC-fasteoi   uhci_hcd:usb3, ohci1394
 22:          0   IO-APIC-fasteoi   eth0
 23:          1   IO-APIC-fasteoi   ipw2200
NMI:          0
LOC:     829470
ERR:          0
MIS:          0

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f5e0000 end: 000000001f6e0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f6e0000 size: 000000000000a000 end: 000000001f6ea000 type: 3
[    0.000000] copy_e820_map() start: 000000001f6ea000 size: 0000000000016000 end: 000000001f700000 type: 4
[    0.000000] copy_e820_map() start: 000000001f700000 size: 0000000000900000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010006000 end: 00000000f0006000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0008000 size: 0000000000004000 end: 00000000f000c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f6ea000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f6ea000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128736) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128736
[    0.000000]   HighMem    128736 ->   128736
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128736
[    0.000000] On node 0 totalpages: 128736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123667 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f6980
[    0.000000] ACPI: RSDT (v001 TOSCPL   RSDT   0x06040000  LTP 0x00000000) @ 0x1f6e276f
[    0.000000] ACPI: MADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1f6e9e88
[    0.000000] ACPI: FADT (v001 TOSCPL ALVISO   0x06040000 LOHR 0x00000032) @ 0x1f6e9ef0
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f6e9fd8
[    0.000000] ACPI: MCFG (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x1f6e9f9c
[    0.000000] ACPI: SSDT (v001 SataRe SataAhci 0x00001000 INTL 0x20030224) @ 0x1f6e2fe5
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x1f6e2baa
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x1f6e29cc
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x1f6e27b3
[    0.000000] ACPI: DSDT (v001 TOSCPL ALVISO   0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Detected 1695.835 MHz processor.
[   18.424423] Built 1 zonelists.  Total pages: 127731
[   18.424428] Kernel command line: root=UUID=3e0b2062-0bc0-424d-a858-0a430d7dc8b9 ro quiet splash
[   18.424594] mapped APIC to ffffd000 (fee00000)
[   18.424596] mapped IOAPIC to ffffc000 (fec00000)
[   18.424600] Enabling fast FPU save and restore... done.
[   18.424603] Enabling unmasked SIMD FPU exception support... done.
[   18.424614] Initializing CPU#0
[   18.424693] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   18.426665] Console: colour VGA+ 80x25
[   18.426891] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.427136] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.442067] Memory: 499264k/514944k available (1992k kernel code, 15120k reserved, 893k data, 328k init, 0k highmem)
[   18.442078] virtual kernel memory layout:
[   18.442079]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.442080]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.442082]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   18.442083]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[   18.442084]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   18.442086]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   18.442087]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   18.442090] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.520568] Calibrating delay using timer specific routine.. 3395.34 BogoMIPS (lpj=6790696)
[   18.520611] Security Framework v1.0.0 initialized
[   18.520620] SELinux:  Disabled at boot.
[   18.520638] Mount-cache hash table entries: 512
[   18.520783] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000180 00000000 00000000
[   18.520796] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.520799] CPU: L2 cache: 2048K
[   18.520802] CPU: After all inits, caps: afe9fbff 00000000 00000000 00002040 00000180 00000000 00000000
[   18.520812] Compat vDSO mapped to ffffe000.
[   18.520816] Remapping vsyscall page to ffffe000
[   18.520827] Checking 'hlt' instruction... OK.
[   18.536646] SMP alternatives: switching to UP code
[   18.536851] Freeing SMP alternatives: 11k freed
[   18.537032] Early unpacking initramfs... done
[   18.875452] ACPI: Core revision 20060707
[   18.875856] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.917875] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 08
[   18.917901] Total of 1 processors activated (3395.34 BogoMIPS).
[   18.918094] ENABLING IO-APIC IRQs
[   18.918295] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.063862] Brought up 1 CPUs
[   19.064107] Booting paravirtualized kernel on bare hardware
[   19.064184] Time: 19:32:38  Date: 07/09/107
[   19.064213] NET: Registered protocol family 16
[   19.064298] EISA bus registered
[   19.064303] ACPI: bus type pci registered
[   19.064683] PCI: PCI BIOS revision 2.10 entry at 0xfd924, last bus=7
[   19.064686] PCI: Using configuration type 1
[   19.064687] Setting up standard PCI resources
[   19.070926] ACPI: Interpreter enabled
[   19.070928] ACPI: Using IOAPIC for interrupt routing
[   19.071374] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.071379] PCI: Probing PCI hardware (bus 00)
[   19.072024] Boot video device is 0000:00:02.0
[   19.072677] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   19.072681] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   19.073570] PCI: Transparent bridge - 0000:00:1e.0
[   19.073638] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[   19.073641] Please report the result to linux-kernel to fix this permanently
[   19.073692] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.081966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   19.082223] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   19.082935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   19.083854] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   19.084097] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   19.084337] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   19.084582] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   19.084821] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   19.085061] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   19.085300] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   19.085541] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   19.124233] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.124243] pnp: PnP ACPI init
[   19.143890] pnp: PnP ACPI: found 9 devices
[   19.143894] PnPBIOS: Disabled by ACPI PNP
[   19.143928] PCI: Using ACPI for IRQ routing
[   19.143930] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.167630] NET: Registered protocol family 8
[   19.167633] NET: Registered protocol family 20
[   19.167760] pnp: 00:01: ioport range 0xfe00-0xfe7f has been reserved
[   19.167763] pnp: 00:01: ioport range 0xfe80-0xfeff has been reserved
[   19.167765] pnp: 00:01: ioport range 0xff00-0xff7f has been reserved
[   19.168012] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   19.168020] PCI: Bridge: 0000:00:1c.0
[   19.168023]   IO window: 3000-3fff
[   19.168029]   MEM window: b4000000-b7ffffff
[   19.168034]   PREFETCH window: d0000000-d3ffffff
[   19.168040] PCI: Bridge: 0000:00:1c.1
[   19.168043]   IO window: 4000-4fff
[   19.168049]   MEM window: b8000000-bbffffff
[   19.168054]   PREFETCH window: d4000000-d7ffffff
[   19.168063] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[   19.168065]   IO window: 00005400-000054ff
[   19.168070]   IO window: 00005800-000058ff
[   19.168076]   PREFETCH window: 30000000-33ffffff
[   19.168082]   MEM window: 38000000-3bffffff
[   19.168087] PCI: Bridge: 0000:00:1e.0
[   19.168090]   IO window: 5000-5fff
[   19.168096]   MEM window: bc000000-bc0fffff
[   19.168101]   PREFETCH window: 30000000-33ffffff
[   19.168130] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   19.168137] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.168160] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   19.168166] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.168179] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.168196] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 16 (level, low) -> IRQ 17
[   19.168223] NET: Registered protocol family 2
[   19.207685] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   19.207758] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   19.207864] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   19.207917] TCP: Hash tables configured (established 16384 bind 8192)
[   19.207919] TCP reno registered
[   19.219722] checking if image is initramfs... it is
[   19.888905] Freeing initrd memory: 6997k freed
[   19.889176] Simple Boot Flag at 0x36 set to 0x1
[   19.889426] audit: initializing netlink socket (disabled)
[   19.889445] audit(1186687958.508:1): initialized
[   19.889584] VFS: Disk quotas dquot_6.5.1
[   19.889606] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.889664] io scheduler noop registered
[   19.889667] io scheduler anticipatory registered
[   19.889669] io scheduler deadline registered
[   19.889681] io scheduler cfq registered (default)
[   19.889992] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.890047] assign_interrupt_mode Found MSI capability
[   19.890050] Allocate Port Service[0000:00:1c.0:pcie00]
[   19.890082] Allocate Port Service[0000:00:1c.0:pcie02]
[   19.890196] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.890250] assign_interrupt_mode Found MSI capability
[   19.890253] Allocate Port Service[0000:00:1c.1:pcie00]
[   19.890283] Allocate Port Service[0000:00:1c.1:pcie02]
[   19.890454] isapnp: Scanning for PnP cards...
[   20.244243] isapnp: No Plug & Play device found
[   20.269788] Real Time Clock Driver v1.12ac
[   20.269853] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.270584] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[   20.270593] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   20.270670] mice: PS/2 mouse device common for all mice
[   20.271205] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.271450] input: Macintosh mouse button emulation as /class/input/input0
[   20.271483] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.271487] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.271725] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.271949] i8042.c: Detected active multiplexing controller, rev 1.1.
[   20.272019] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.272023] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.272026] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.272028] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.272030] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.272142] EISA: Probing bus 0 at eisa.0
[   20.272150] Cannot allocate resource for EISA slot 1
[   20.272153] Cannot allocate resource for EISA slot 2
[   20.272155] Cannot allocate resource for EISA slot 3
[   20.272158] Cannot allocate resource for EISA slot 4
[   20.272160] Cannot allocate resource for EISA slot 5
[   20.272174] EISA: Detected 0 cards.
[   20.302346] TCP cubic registered
[   20.302360] NET: Registered protocol family 1
[   20.302382] Using IPI No-Shortcut mode
[   20.302459] ACPI: (supports S0 S3 S4 S5)
[   20.302511]   Magic number: 3:182:546
[   20.302641]   hash matches device null
[   20.302895] Freeing unused kernel memory: 328k freed
[   20.304350] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.306116] Time: tsc clocksource has been installed.
[   21.513706] Capability LSM initialized
[   21.543582] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   21.543596] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   21.853314] usbcore: registered new interface driver usbfs
[   21.853336] usbcore: registered new interface driver hub
[   21.853355] usbcore: registered new device driver usb
[   21.854149] USB Universal Host Controller Interface driver v3.0
[   21.854205] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   21.854216] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   21.854220] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.854391] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   21.854423] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   21.854518] usb usb1: configuration #1 chosen from 1 choice
[   21.854539] hub 1-0:1.0: USB hub found
[   21.854544] hub 1-0:1.0: 2 ports detected
[   21.944455] 8139too Fast Ethernet driver 0.9.28
[   21.956003] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   21.956016] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   21.956021] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.956044] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   21.956078] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   21.956168] usb usb2: configuration #1 chosen from 1 choice
[   21.956190] hub 2-0:1.0: USB hub found
[   21.956196] hub 2-0:1.0: 2 ports detected
[   21.971379] ieee1394: Initialized config rom entry `ip1394'
[   22.059862] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   22.059876] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.059881] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.059902] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.059938] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001860
[   22.060031] usb usb3: configuration #1 chosen from 1 choice
[   22.060059] hub 3-0:1.0: USB hub found
[   22.060064] hub 3-0:1.0: 2 ports detected
[    3.604000] Time: acpi_pm clocksource has been installed.
[    3.604000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    3.604000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.604000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.604000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.604000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    3.604000] usb usb4: configuration #1 chosen from 1 choice
[    3.604000] hub 4-0:1.0: USB hub found
[    3.604000] hub 4-0:1.0: 2 ports detected
[    3.708000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.708000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.708000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.708000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.708000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.708000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.708000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xb0040000
[    3.712000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.712000] usb usb5: configuration #1 chosen from 1 choice
[    3.712000] hub 5-0:1.0: USB hub found
[    3.712000] hub 5-0:1.0: 8 ports detected
[    3.820000] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 21 (level, low) -> IRQ 22
[    3.820000] eth0: RealTek RTL8139 at 0xe0064000, 00:16:d4:1f:14:b0, IRQ 22
[    3.820000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.820000] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 18 (level, low) -> IRQ 21
[    3.872000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[bc006800-bc006fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.872000] SCSI subsystem initialized
[    3.876000] libata version 2.20 loaded.
[    3.880000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.880000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[    3.880000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.880000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    3.880000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    3.880000] scsi0 : ata_piix
[    3.884000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.200000] ata1.00: ATAPI, max UDMA/33
[    4.364000] ata1.00: configured for UDMA/33
[    4.364000] scsi1 : ata_piix
[    4.364000] ata2: port disabled. ignoring.
[    4.364000] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.50 PQ: 0 ANSI: 5
[    4.364000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    4.364000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    4.364000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.364000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.364000] ata3: SATA max UDMA/133 cmd 0x00012090 ctl 0x00012086 bmdma 0x000118b0 irq 20
[    4.364000] ata4: SATA max UDMA/133 cmd 0x00012088 ctl 0x00012082 bmdma 0x000118b8 irq 20
[    4.364000] scsi2 : ata_piix
[    4.528000] ata3.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    4.528000] ata3.00: ATA-7: FUJITSU MHV2060BH, 00000028, max UDMA/100
[    4.528000] ata3.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.536000] ata3.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    4.536000] ata3.00: configured for UDMA/100
[    4.536000] scsi3 : ata_piix
[    4.692000] ATA: abnormal status 0x7F on port 0x0001208f
[    4.696000] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHV2060B 0000 PQ: 0 ANSI: 5
[    4.716000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.716000] sda: Write Protect is off
[    4.716000] sda: Mode Sense: 00 3a 00 00
[    4.716000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.716000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.716000] sda: Write Protect is off
[    4.716000] sda: Mode Sense: 00 3a 00 00
[    4.716000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.716000]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.720000] Uniform CD-ROM driver Revision: 3.20
[    4.720000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.788000]  sda1 sda2 < sda5 sda6 > sda3
[    4.828000] sd 2:0:0:0: Attached scsi disk sda
[    4.832000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.832000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    5.120000] Attempting manual resume
[    5.120000] swsusp: Resume From Partition 8:6
[    5.120000] PM: Checking swsusp image.
[    5.120000] PM: Resume from disk failed.
[    5.148000] kjournald starting.  Commit interval 5 seconds
[    5.148000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.428000] eth0: link down
[   17.548000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.552000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.940000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.948000] agpgart: Detected an Intel 915GM Chipset.
[   17.948000] agpgart: Detected 7932K stolen memory.
[   17.968000] agpgart: AGP aperture is 256M @ 0xc0000000
[   17.984000] intel_rng: FWH not detected
[   18.012000] NET: Registered protocol family 17
[   18.036000] iTCO_vendor_support: vendor-support=0
[   18.440000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.440000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   18.440000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.504000] Yenta: CardBus bridge found at 0000:06:04.0 [1179:ff00]
[   18.504000] Yenta: Enabling burst memory read transactions
[   18.504000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.504000] Yenta: Routing CardBus interrupts to PCI
[   18.504000] Yenta TI: socket 0000:06:04.0, mfunc 0x10aa1b22, devctl 0x66
[   18.736000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   18.736000] Socket status: 30000006
[   18.736000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   18.736000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   18.736000] cs: IO port probe 0x5000-0x5fff: clean.
[   18.736000] pcmcia: parent PCI bridge Memory window: 0xbc000000 - 0xbc0fffff
[   18.736000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   18.740000] ieee80211_crypt: registered algorithm 'NULL'
[   18.740000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.740000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.812000] ACPI: PCI Interrupt 0000:06:04.3[B] -> GSI 17 (level, low) -> IRQ 16
[   18.828000] sdhci: Secure Digital Host Controller Interface driver
[   18.828000] sdhci: Copyright(c) Pierre Ossman
[   18.828000] sdhci: SDHCI controller found at 0000:06:04.4 [104c:8034] (rev 0)
[   18.828000] ACPI: PCI Interrupt 0000:06:04.4[D] -> GSI 19 (level, low) -> IRQ 20
[   18.828000] mmc0: SDHCI at 0xbc009400 irq 20 DMA
[   18.832000] mmc1: SDHCI at 0xbc009000 irq 20 DMA
[   18.832000] mmc2: SDHCI at 0xbc006400 irq 20 DMA
[   18.932000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   18.932000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.932000] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 22 (level, low) -> IRQ 23
[   18.932000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.152000] ipw2200: Radio Frequency Kill Switch is On:
[   19.152000] Kill switch must be turned off for wireless networking to work.
[   19.152000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   19.356000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 16
[   19.356000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   19.416000] input: PS/2 Mouse as /class/input/input2
[   19.436000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   19.608000] cs: IO port probe 0x100-0x3af: clean.
[   19.644000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.644000] cs: IO port probe 0x820-0x8ff: clean.
[   19.644000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.644000] cs: IO port probe 0xa00-0xaff: clean.
[   20.180000] intel8x0_measure_ac97_clock: measured 55314 usecs
[   20.180000] intel8x0: clocking to 48000
[   20.316000] fuse init (API version 7.8)
[   20.368000] lp: driver loaded but no devices found
[   20.412000] Adding 257000k swap on /dev/disk/by-uuid/af416e1f-4558-40e1-92aa-c866299dbe74.  Priority:-1 extents:1 across:257000k
[   20.548000] EXT3 FS on sda3, internal journal
[   20.780000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   20.848000] NTFS volume version 3.1.
[   20.884000] NTFS volume version 3.1.
[   25.028000] Using specific hotkey driver
[   25.076000] ACPI: Battery Slot [BAT1] (battery present)
[   25.148000] ACPI: AC Adapter [ACAD] (on-line)
[   25.220000] No dock devices found.
[   25.240000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.240000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   25.256000] ibm_acpi: ec object not found
[   25.328000] input: Power Button (FF) as /class/input/input4
[   25.332000] ACPI: Power Button (FF) [PWRF]
[   25.376000] input: Lid Switch as /class/input/input5
[   25.376000] ACPI: Lid Switch [LID0]
[   25.420000] input: Power Button (CM) as /class/input/input6
[   25.420000] ACPI: Power Button (CM) [PWRB]
[   25.528000] pcc_acpi: loading...
[   29.824000] [drm] Initialized drm 1.1.0 20060810
[   29.828000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   29.828000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.572000] ppdev: user-space parallel port driver
[   31.444000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   31.444000] apm: overridden by ACPI.
[   31.576000] Bluetooth: Core ver 2.11
[   31.576000] NET: Registered protocol family 31
[   31.576000] Bluetooth: HCI device and connection manager initialized
[   31.576000] Bluetooth: HCI socket layer initialized
[   31.612000] Bluetooth: L2CAP ver 2.8
[   31.612000] Bluetooth: L2CAP socket layer initialized
[   31.768000] Bluetooth: RFCOMM socket layer initialized
[   31.768000] Bluetooth: RFCOMM TTY layer initialized
[   31.768000] Bluetooth: RFCOMM ver 1.8
[   51.348000] NET: Registered protocol family 10
[   51.352000] lo: Disabled Privacy Extensions
[   51.352000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   51.352000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  679.280000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  679.356000] eth0: link down
[  679.356000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  690.644000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  690.716000] eth0: link down
[  690.716000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3258.016000] usb 5-5: new high speed USB device using ehci_hcd and address 2
[ 3258.148000] usb 5-5: configuration #1 chosen from 1 choice
[ 3258.900000] usbcore: registered new interface driver libusual
[ 3258.980000] Initializing USB Mass Storage driver...
[ 3258.980000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3258.984000] usbcore: registered new interface driver usb-storage
[ 3258.984000] USB Mass Storage support registered.
[ 3258.984000] usb-storage: device found at 2
[ 3258.984000] usb-storage: waiting for device to settle before scanning
[ 3263.984000] usb-storage: device scan complete
[ 3263.984000] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 3264.780000] SCSI device sdb: 4014080 512-byte hdwr sectors (2055 MB)
[ 3264.784000] sdb: Write Protect is off
[ 3264.784000] sdb: Mode Sense: 23 00 00 00
[ 3264.784000] sdb: assuming drive cache: write through
[ 3264.784000] SCSI device sdb: 4014080 512-byte hdwr sectors (2055 MB)
[ 3264.784000] sdb: Write Protect is off
[ 3264.784000] sdb: Mode Sense: 23 00 00 00
[ 3264.784000] sdb: assuming drive cache: write through
[ 3264.784000]  sdb: sdb1
[ 3264.788000] sd 4:0:0:0: Attached scsi removable disk sdb
[ 3264.788000] sd 4:0:0:0: Attached scsi generic sg2 type 0

---

