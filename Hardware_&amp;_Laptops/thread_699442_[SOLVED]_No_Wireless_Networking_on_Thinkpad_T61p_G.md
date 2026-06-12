---
title: "[SOLVED] No Wireless Networking on Thinkpad T61p Gutsy"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by MountainX on 2008-02-17
I do not have a wireless icon in the upper left area by the power button icon, etc. I do have a bluetooth icon (but I don't have a need for bluetooth at the moment). I would like to get wireless networking enabled. I have read a lot of posts, but couldn't find the help I need.

Here is some info:

:/proc/acpi/ibm$ sudo lspci
Password or swipe finger: 
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


/proc/acpi/ibm$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1572   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

The Fn+F5 key doesn't produce any change in the status of bluetooth. It remains enabled:
:/proc/acpi/ibm$ cat /proc/acpi/ibm/bluetooth
status:         enabled
commands:       enable, disable


I have a bunch of other issues too, such as suspend/resume not working. (I have been through all the tutorials and the steps at ThinkWiki, but no resolution yet.) Anyway, all I want to fix at the moment is the wireless ethernet. Thanks.

---

### Post by coaltown on 2008-02-18
two things:

what happens when you type:
```
sudo ifconfig eth1 up
```

also: Can you paste the output of the following command:
```
dmesg
```

---

### Post by MountainX on 2008-02-18
```
sudo ifconfig eth1 up
```
returns to command prompt with no message

dmesg gives the following output (this is after I plugged in two different flash drives):
```
[  
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099800 (usable)
[    0.000000]  BIOS-e820: 0000000000099800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d6000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfeb0000 - 00000000bfecc000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfecc000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a PAE enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6900
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 6400 pages used for memmap
[    0.000000]   HighMem zone: 812800 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F68D0 checksum 0
[    0.000000] ACPI: RSDP 000F68D0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT BFEBB74B, 0094 (r1 LENOVO TP-7L        2090  LTP        0)
[    0.000000] ACPI: FACP BFEBB800, 00F4 (r3 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
[    0.000000] ACPI: DSDT BFEBBC1D, FF05 (r1 LENOVO TP-7L        2090 MSFT  3000000)
[    0.000000] ACPI: FACS BFEE4000, 0040
[    0.000000] ACPI: SSDT BFEBB9B4, 0269 (r1 LENOVO TP-7L        2090 MSFT  3000000)
[    0.000000] ACPI: ECDT BFECBB22, 0052 (r1 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: TCPA BFECBB74, 0032 (r2 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: APIC BFECBBA6, 0068 (r1 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: MCFG BFECBC0E, 003C (r1 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: HPET BFECBC4A, 0038 (r1 LENOVO TP-7L        2090 LNVO        1)
[    0.000000] ACPI: SLIC BFECBDF0, 0176 (r1 LENOVO TP-7L        2090  LTP        0)
[    0.000000] ACPI: BOOT BFECBF66, 0028 (r1 LENOVO TP-7L        2090  LTP        1)
[    0.000000] ACPI: ASF! BFECBF8E, 0072 (r16 LENOVO TP-7L        2090 PTL         1)
[    0.000000] ACPI: SSDT BFEE26D9, 025F (r1 LENOVO TP-7L        2090 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE2938, 00A6 (r1 LENOVO TP-7L        2090 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE29DE, 04F7 (r1 LENOVO TP-7L        2090 INTL 20050513)
[    0.000000] ACPI: SSDT BFEE2ED5, 01D8 (r1 LENOVO TP-7L        2090 INTL 20050513)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:30000000)
[    0.000000] Built 1 zonelists.  Total pages: 1040384
[    0.000000] Kernel command line: root=/dev/mapper/ThinkUbuntu-root ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.018 MHz processor.
[   16.757533] Console: colour VGA+ 80x25
[   16.757829] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.758099] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.908316] Memory: 3097968k/4194304k available (2015k kernel code, 45132k reserved, 915k data, 364k init, 2226880k highmem)
[   16.908324] virtual kernel memory layout:
[   16.908325]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   16.908326]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.908327]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.908328]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.908328]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   16.908329]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   16.908330]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   16.908332] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.908364] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   16.908491] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.908495] hpet0: 3 64-bit timers, 14318180 Hz
[   16.989468] Calibrating delay using timer specific routine.. 3994.55 BogoMIPS (lpj=7989105)
[   16.989487] Security Framework v1.0.0 initialized
[   16.989493] SELinux:  Disabled at boot.
[   16.989502] Mount-cache hash table entries: 512
[   16.989605] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   16.989611] monitor/mwait feature present.
[   16.989612] using mwait in idle threads.
[   16.989616] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.989618] CPU: L2 cache: 4096K
[   16.989620] CPU: Physical Processor ID: 0
[   16.989621] CPU: Processor Core ID: 0
[   16.989623] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   16.989630] Compat vDSO mapped to ffffe000.
[   16.989641] Checking 'hlt' instruction... OK.
[   17.005551] SMP alternatives: switching to UP code
[   17.005898] Early unpacking initramfs... done
[   17.274109] ACPI: Core revision 20070126
[   17.274168] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.292085] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0b
[   17.292098] SMP alternatives: switching to SMP code
[   17.292163] Booting processor 1/1 eip 3000
[   17.302742] Initializing CPU#1
[   17.381429] Calibrating delay using timer specific routine.. 3990.01 BogoMIPS (lpj=7980032)
[   17.381434] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   17.381438] monitor/mwait feature present.
[   17.381441] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.381443] CPU: L2 cache: 4096K
[   17.381444] CPU: Physical Processor ID: 0
[   17.381446] CPU: Processor Core ID: 1
[   17.381447] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   17.381898] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0b
[   17.381921] Total of 2 processors activated (7984.56 BogoMIPS).
[   17.382101] ENABLING IO-APIC IRQs
[   17.382308] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.529240] checking TSC synchronization [CPU#0 -> CPU#1]:
[   17.549236] Measured 362720 cycles TSC warp between CPUs, turning off TSC clock.
[    0.504000] Marking TSC unstable due to: check_tsc_sync_source failed.
[    0.508000] Brought up 2 CPUs
[    0.644000] migration_cost=8000
[    0.644000] Booting paravirtualized kernel on bare hardware
[    0.644000] Time: 18:14:50  Date: 01/18/108
[    0.644000] NET: Registered protocol family 16
[    0.644000] EISA bus registered
[    0.644000] ACPI: bus type pci registered
[    0.644000] PCI: PCI BIOS revision 3.00 entry at 0xfdda7, last bus=24
[    0.644000] PCI: Using configuration type 1
[    0.644000] Setting up standard PCI resources
[    0.648000] ACPI: EC: Found ECDT
[    0.652000] ACPI: System BIOS is requesting _OSI(Linux)
[    0.652000] ACPI: Please test with "acpi_osi=!Linux"
[    0.652000] Please send dmidecode to linux-acpi@vger.kernel.org
[    0.664000] ACPI: Interpreter enabled
[    0.664000] ACPI: (supports S0 S3 S4 S5)
[    0.664000] ACPI: Using IOAPIC for interrupt routing
[    0.672000] ACPI: EC: GPE=0x12, ports=0x66, 0x62
[    0.672000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.672000] PCI: Probing PCI hardware (bus 00)
[    0.676000] PCI: Transparent bridge - 0000:00:1e.0
[    0.676000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.676000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.676000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.676000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.676000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.676000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.676000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.676000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.680000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[    0.680000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.680000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.680000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.680000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.680000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.680000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.680000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.680000] ACPI: Power Resource [PUBS] (on)
[    0.680000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.680000] pnp: PnP ACPI init
[    0.680000] ACPI: bus type pnp registered
[    0.688000] pnp: PnP ACPI: found 11 devices
[    0.688000] ACPI: ACPI bus type pnp unregistered
[    0.688000] PnPBIOS: Disabled by ACPI PNP
[    0.688000] PCI: Using ACPI for IRQ routing
[    0.688000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.848000] NET: Registered protocol family 8
[    0.848000] NET: Registered protocol family 20
[    0.848000] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.848000] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.848000] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.848000] pnp: 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.848000] pnp: 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.848000] pnp: 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.848000] pnp: 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.848000] pnp: 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.852000] Time: hpet clocksource has been installed.
[    0.852000] Switched to high resolution mode on CPU 0
[    0.852000] Switched to high resolution mode on CPU 1
[    0.880000] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
[    0.880000] PCI: Bridge: 0000:00:01.0
[    0.880000]   IO window: 2000-2fff
[    0.880000]   MEM window: d0000000-d2ffffff
[    0.880000]   PREFETCH window: e0000000-efffffff
[    0.880000] PCI: Bridge: 0000:00:1c.0
[    0.880000]   IO window: 3000-3fff
[    0.880000]   MEM window: dc100000-df2fffff
[    0.880000]   PREFETCH window: dfd00000-dfdfffff
[    0.880000] PCI: Bridge: 0000:00:1c.1
[    0.880000]   IO window: 4000-4fff
[    0.880000]   MEM window: d4000000-d7dfffff
[    0.880000]   PREFETCH window: dfa00000-dfafffff
[    0.880000] PCI: Bridge: 0000:00:1c.2
[    0.880000]   IO window: 5000-5fff
[    0.880000]   MEM window: fc000000-fdffffff
[    0.880000]   PREFETCH window: f8000000-f80fffff
[    0.880000] PCI: Bridge: 0000:00:1c.3
[    0.880000]   IO window: 6000-6fff
[    0.880000]   MEM window: d8000000-d9ffffff
[    0.880000]   PREFETCH window: df700000-df7fffff
[    0.880000] PCI: Bridge: 0000:00:1c.4
[    0.880000]   IO window: 7000-7fff
[    0.880000]   MEM window: cc000000-cdffffff
[    0.880000]   PREFETCH window: df400000-df4fffff
[    0.880000] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[    0.880000]   IO window: 00008000-000080ff
[    0.880000]   IO window: 00008400-000084ff
[    0.880000]   PREFETCH window: f4000000-f7ffffff
[    0.880000]   MEM window: c4000000-c7ffffff
[    0.880000] PCI: Bridge: 0000:00:1e.0
[    0.880000]   IO window: 8000-bfff
[    0.880000]   MEM window: f8100000-fbffffff
[    0.880000]   PREFETCH window: f4000000-f7ffffff
[    0.880000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.880000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.880000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 17
[    0.880000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.880000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 18
[    0.880000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.880000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 19
[    0.880000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.880000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 20
[    0.880000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.880000] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 20 (level, low) -> IRQ 17
[    0.880000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.880000] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[    0.880000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.880000] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.880000] PCI: Setting latency timer of device 0000:15:00.0 to 64
[    0.880000] NET: Registered protocol family 2
[    0.924000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.924000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.924000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.924000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.924000] TCP reno registered
[    0.936000] checking if image is initramfs... it is
[    1.516000] Freeing initrd memory: 7601k freed
[    1.516000] Simple Boot Flag at 0x35 set to 0x1
[    1.516000] audit: initializing netlink socket (disabled)
[    1.516000] audit(1203358490.352:1): initialized
[    1.516000] highmem bounce pool size: 64 pages
[    1.516000] VFS: Disk quotas dquot_6.5.1
[    1.516000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.516000] io scheduler noop registered
[    1.516000] io scheduler anticipatory registered
[    1.516000] io scheduler deadline registered
[    1.516000] io scheduler cfq registered (default)
[    1.516000] Boot video device is 0000:01:00.0
[    1.516000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    1.516000] assign_interrupt_mode Found MSI capability
[    1.516000] Allocate Port Service[0000:00:01.0:pcie00]
[    1.516000] Allocate Port Service[0000:00:01.0:pcie02]
[    1.516000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.516000] assign_interrupt_mode Found MSI capability
[    1.516000] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.516000] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.516000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.516000] assign_interrupt_mode Found MSI capability
[    1.516000] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.516000] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.520000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.520000] assign_interrupt_mode Found MSI capability
[    1.520000] Allocate Port Service[0000:00:1c.2:pcie00]
[    1.520000] Allocate Port Service[0000:00:1c.2:pcie02]
[    1.520000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    1.520000] assign_interrupt_mode Found MSI capability
[    1.520000] Allocate Port Service[0000:00:1c.3:pcie00]
[    1.520000] Allocate Port Service[0000:00:1c.3:pcie02]
[    1.520000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    1.520000] assign_interrupt_mode Found MSI capability
[    1.520000] Allocate Port Service[0000:00:1c.4:pcie00]
[    1.520000] Allocate Port Service[0000:00:1c.4:pcie02]
[    1.520000] isapnp: Scanning for PnP cards...
[    1.876000] isapnp: No Plug & Play device found
[    1.892000] Real Time Clock Driver v1.12ac
[    1.892000] hpet_resources: 0xfed00000 is busy
[    1.892000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.896000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.896000] input: Macintosh mouse button emulation as /class/input/input0
[    1.896000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.904000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.904000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.904000] mice: PS/2 mouse device common for all mice
[    1.904000] EISA: Probing bus 0 at eisa.0
[    1.904000] Cannot allocate resource for EISA slot 1
[    1.904000] Cannot allocate resource for EISA slot 2
[    1.904000] Cannot allocate resource for EISA slot 3
[    1.904000] Cannot allocate resource for EISA slot 4
[    1.904000] Cannot allocate resource for EISA slot 5
[    1.904000] Cannot allocate resource for EISA slot 6
[    1.904000] Cannot allocate resource for EISA slot 7
[    1.904000] Cannot allocate resource for EISA slot 8
[    1.904000] EISA: Detected 0 cards.
[    1.904000] TCP cubic registered
[    1.904000] NET: Registered protocol family 1
[    1.904000] Using IPI No-Shortcut mode
[    1.904000]   Magic number: 12:404:241
[    1.904000]   hash matches device ttyse
[    1.904000]   hash matches device thermal:02
[    1.904000] Freeing unused kernel memory: 364k freed
[    1.908000] input: AT Translated Set 2 keyboard as /class/input/input1
[    3.076000] AppArmor: AppArmor initialized<5>audit(1203358491.852:2):  type=1505 info="AppArmor initialized" pid=1256
[    3.088000] fuse init (API version 7.8)
[    3.092000] Failure registering capabilities with primary security module.
[    3.128000] ACPI: SSDT BFEE1B32, 02C4 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[    3.128000] ACPI: SSDT BFEE1E7B, 085E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[    3.128000] Monitor-Mwait will be used to enter C-1 state
[    3.128000] Monitor-Mwait will be used to enter C-2 state
[    3.128000] Monitor-Mwait will be used to enter C-3 state
[    3.128000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.128000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.128000] ACPI: SSDT BFEE1A6A, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[    3.128000] ACPI: SSDT BFEE1DF6, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[    3.132000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.132000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.132000] ACPI: Thermal Zone [THM0] (52 C)
[    3.136000] ACPI: Thermal Zone [THM1] (48 C)
[    3.144000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[    3.500000] usbcore: registered new interface driver usbfs
[    3.500000] usbcore: registered new interface driver hub
[    3.500000] usbcore: registered new device driver usb
[    3.500000] USB Universal Host Controller Interface driver v3.0
[    3.500000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 17
[    3.500000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    3.500000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.500000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.500000] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001860
[    3.500000] usb usb1: configuration #1 chosen from 1 choice
[    3.500000] hub 1-0:1.0: USB hub found
[    3.500000] hub 1-0:1.0: 2 ports detected
[    3.500000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    3.500000] Copyright (c) 1999-2006 Intel Corporation.
[    3.552000] SCSI subsystem initialized
[    3.604000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[    3.604000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    3.604000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.604000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.604000] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001880
[    3.604000] usb usb2: configuration #1 chosen from 1 choice
[    3.604000] hub 2-0:1.0: USB hub found
[    3.604000] hub 2-0:1.0: 2 ports detected
[    3.616000] libata version 2.21 loaded.
[    3.708000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.708000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.708000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.708000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    3.708000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    3.708000] usb usb3: configuration #1 chosen from 1 choice
[    3.708000] hub 3-0:1.0: USB hub found
[    3.708000] hub 3-0:1.0: 2 ports detected
[    3.812000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[    3.812000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.812000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.812000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.812000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x000018c0
[    3.812000] usb usb4: configuration #1 chosen from 1 choice
[    3.812000] hub 4-0:1.0: USB hub found
[    3.812000] hub 4-0:1.0: 2 ports detected
[    3.880000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.916000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[    3.916000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.916000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.916000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.916000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000018e0
[    3.916000] usb usb5: configuration #1 chosen from 1 choice
[    3.916000] hub 5-0:1.0: USB hub found
[    3.916000] hub 5-0:1.0: 2 ports detected
[    4.000000] Clocksource tsc unstable (delta = -320961505 ns)
[    4.020000] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 17
[    4.020000] PCI: Setting latency timer of device 0000:00:19.0 to 64
[    4.048000] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1e:37:86:99:22
[    4.056000] usb 1-2: configuration #1 chosen from 1 choice
[    4.148000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    4.148000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 19
[    4.148000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    4.148000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.148000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    4.148000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    4.148000] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfe226c00
[    4.152000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.152000] usb usb6: configuration #1 chosen from 1 choice
[    4.152000] hub 6-0:1.0: USB hub found
[    4.152000] hub 6-0:1.0: 4 ports detected
[    4.256000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[    4.256000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.256000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.256000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    4.256000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.256000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.256000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe227000
[    4.260000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.260000] usb usb7: configuration #1 chosen from 1 choice
[    4.260000] hub 7-0:1.0: USB hub found
[    4.260000] hub 7-0:1.0: 6 ports detected
[    4.368000] ata_piix 0000:00:1f.1: version 2.11
[    4.368000] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
[    4.368000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.368000] scsi0 : ata_piix
[    4.368000] scsi1 : ata_piix
[    4.368000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011830 irq 14
[    4.368000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011838 irq 15
[    4.496000] usb 1-2: USB disconnect, address 2
[    4.688000] ata1.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-M10N, 1.02, max UDMA/33
[    4.736000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    4.872000] ata1.00: configured for UDMA/33
[    4.872000] ata2: port disabled. ignoring.
[    4.876000] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-M10N  1.02 PQ: 0 ANSI: 5
[    4.876000] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 21
[    4.876000] PCI: Setting latency timer of device 0000:15:00.1 to 64
[    4.928000] usb 1-2: configuration #1 chosen from 1 choice
[    4.928000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.932000] ahci 0000:00:1f.2: version 2.2
[    4.932000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[    4.932000] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match
[    5.936000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x1 impl SATA mode
[    5.936000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    5.936000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.936000] scsi2 : ahci
[    5.936000] ata3: SATA max UDMA/133 cmd 0xf888a100 ctl 0x00000000 bmdma 0x00000000 irq 16
[    6.208000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00061b032a1cba19]
[    6.420000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.420000] ata3.00: ATA-8: Hitachi HTS722012K9SA00, DCCOC54P, max UDMA/133
[    6.420000] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.420000] ata3.00: configured for UDMA/133
[    6.420000] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS72201 DCCO PQ: 0 ANSI: 5
[    6.428000] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.428000] sd 2:0:0:0: [sda] Write Protect is off
[    6.428000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.428000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.428000] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.428000] sd 2:0:0:0: [sda] Write Protect is off
[    6.428000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.428000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.428000]  sda: sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    6.448000] Uniform CD-ROM driver Revision: 3.20
[    6.448000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.452000]  sda5 >
[    6.452000] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.456000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    6.456000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.740000] Attempting manual resume
[    6.740000] swsusp: Resume From Partition 254:1
[    6.740000] PM: Checking swsusp image.
[    6.740000] PM: Resume from disk failed.
[    6.768000] kjournald starting.  Commit interval 5 seconds
[    6.768000] EXT3-fs: mounted filesystem with ordered data mode.
[   12.636000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.644000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.684000] Linux agpgart interface v0.102 (c) Dave Jones
[   13.104000] ieee80211_crypt: registered algorithm 'NULL'
[   13.108000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   13.108000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.204000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   13.332000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   13.332000] Socket status: 30000006
[   13.332000] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
[   13.332000] cs: IO port probe 0x8000-0xbfff: clean.
[   13.332000] pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
[   13.332000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   13.352000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   13.352000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   13.352000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   13.352000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   13.352000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   13.396000] nvidia: module license 'NVIDIA' taints kernel.
[   13.648000] input: PC Speaker as /class/input/input2
[   13.684000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.684000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   13.684000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   13.740000] sdhci: Secure Digital Host Controller Interface driver
[   13.740000] sdhci: Copyright(c) Pierre Ossman
[   13.740000] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 21)
[   13.740000] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
[   13.744000] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   13.744000] mmc0: SDHCI at 0xf8101800 irq 22 DMA
[   13.912000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   13.912000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   14.020000] cs: IO port probe 0x100-0x3af: clean.
[   14.020000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   14.024000] cs: IO port probe 0x820-0x8ff: clean.
[   14.024000] cs: IO port probe 0xc00-0xcf7: clean.
[   14.024000] cs: IO port probe 0xa00-0xaff: clean.
[   14.136000] mmcblk0: mmc0:452d SD02G 2011136KiB 
[   14.136000]  mmcblk0: p1
[   14.172000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[   14.172000] serio: Synaptics pass-through port at isa0060/serio1/input0
[   14.208000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   14.380000] loop: module loaded
[   14.420000] lp: driver loaded but no devices found
[   14.516000] Adding 4796408k swap on /dev/mapper/ThinkUbuntu-swap_1.  Priority:-1 extents:1 across:4796408k
[   14.776000] EXT3 FS on dm-0, internal journal
[   15.116000] kjournald starting.  Commit interval 5 seconds
[   15.116000] EXT3 FS on sda1, internal journal
[   15.116000] EXT3-fs: mounted filesystem with ordered data mode.
[   15.484000] ipw3945: Radio Frequency Kill Switch is On:
[   15.484000] Kill switch must be turned off for wireless networking to work.
[   15.804000] NET: Registered protocol family 17
[   17.676000] ACPI: Battery Slot [BAT0] (battery present)
[   17.688000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   17.692000] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   17.712000] ACPI: ACPI Dock Station Driver 
[   17.780000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   17.780000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   17.780000] ACPI: Error installing bay notify handler
[   17.780000] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   17.796000] ACPI: AC Adapter [AC] (on-line)
[   17.836000] input: Power Button (FF) as /class/input/input4
[   17.836000] ACPI: Power Button (FF) [PWRF]
[   17.836000] input: Lid Switch as /class/input/input5
[   17.836000] ACPI: Lid Switch [LID]
[   17.836000] input: Sleep Button (CM) as /class/input/input6
[   17.836000] ACPI: Sleep Button (CM) [SLPB]
[   18.752000] ppdev: user-space parallel port driver
[   18.928000] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[   18.932000] audit(1203358508.545:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5166 profile="/usr/sbin/cupsd"
[   18.988000] apm: BIOS not found.
[   19.148000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   19.148000] thinkpad_acpi: http://ibm-acpi.sf.net/
[   19.148000] thinkpad_acpi: ThinkPad EC firmware 7KHT24WW-1.08
[   19.328000] Failure registering capabilities with primary security module.
[   19.364000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   19.576000] Bluetooth: Core ver 2.11
[   19.576000] NET: Registered protocol family 31
[   19.576000] Bluetooth: HCI device and connection manager initialized
[   19.576000] Bluetooth: HCI socket layer initialized
[   19.604000] Bluetooth: L2CAP ver 2.8
[   19.604000] Bluetooth: L2CAP socket layer initialized
[   19.640000] input: TPPS/2 IBM TrackPoint as /class/input/input7
[   19.692000] Bluetooth: RFCOMM socket layer initialized
[   19.692000] Bluetooth: RFCOMM TTY layer initialized
[   19.692000] Bluetooth: RFCOMM ver 1.8
[   24.220000] /dev/vmmon[5610]: VMCI: Driver initialized.
[   24.220000] /dev/vmmon[5610]: Module vmmon: registered with major=10 minor=165
[   24.220000] /dev/vmmon[5610]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   24.220000] /dev/vmmon[5610]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   24.220000] /dev/vmmon[5610]: Module vmmon: initialized
[   24.828000] /dev/vmnet: open called by PID 5662 (vmnet-bridge)
[   24.828000] /dev/vmnet: hub 0 does not exist, allocating memory.
[   24.828000] /dev/vmnet: port on hub 0 successfully opened
[   24.828000] bridge-eth0: enabling the bridge
[   24.828000] bridge-eth0: up
[   24.828000] bridge-eth0: already up
[   24.828000] bridge-eth0: attached
[   24.896000] /dev/vmnet: open called by PID 5679 (vmnet-netifup)
[   24.896000] /dev/vmnet: hub 1 does not exist, allocating memory.
[   24.896000] /dev/vmnet: port on hub 1 successfully opened
[   25.024000] /dev/vmnet: open called by PID 5678 (vmnet-dhcpd)
[   25.024000] /dev/vmnet: port on hub 1 successfully opened
[   25.028000] /dev/vmnet: open called by PID 5698 (vmnet-netifup)
[   25.028000] /dev/vmnet: hub 8 does not exist, allocating memory.
[   25.028000] /dev/vmnet: port on hub 8 successfully opened
[   25.124000] /dev/vmnet: open called by PID 5708 (vmnet-dhcpd)
[   25.124000] /dev/vmnet: port on hub 8 successfully opened
[   25.260000] /dev/vmnet: open called by PID 5716 (vmnet-natd)
[   25.260000] /dev/vmnet: port on hub 8 successfully opened
[   40.084000] input: Virtual ThinkFinger Keyboard as /class/input/input8
[  205.252000] input: Virtual ThinkFinger Keyboard as /class/input/input9
[  242.632000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[  242.956000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[  243.120000] usb 1-1: configuration #1 chosen from 1 choice
[  243.192000] Bluetooth: HCI USB driver ver 2.9
[  243.196000] usbcore: registered new interface driver hci_usb
[ 1162.248000] usb 7-1: new high speed USB device using ehci_hcd and address 2
[ 1162.380000] usb 7-1: configuration #1 chosen from 1 choice
[ 1162.812000] usbcore: registered new interface driver libusual
[ 1162.896000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1162.900000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1162.900000] Initializing USB Mass Storage driver...
[ 1162.900000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1162.900000] usb-storage: device found at 2
[ 1162.900000] usb-storage: waiting for device to settle before scanning
[ 1162.900000] usbcore: registered new interface driver usb-storage
[ 1162.900000] USB Mass Storage support registered.
[ 1167.900000] usb-storage: device scan complete
[ 1167.900000] scsi 3:0:0:0: Direct-Access     JetFlash TS2GJF220        0.00 PQ: 0 ANSI: 2
[ 1167.900000] scsi 3:0:0:1: CD-ROM            JetFlash TS2GJF220        0.00 PQ: 0 ANSI: 0 CCS
[ 1167.904000] sd 3:0:0:0: [sdb] 20479 512-byte hardware sectors (10 MB)
[ 1167.904000] sd 3:0:0:0: [sdb] Write Protect is off
[ 1167.904000] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1167.904000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1167.904000] sd 3:0:0:0: [sdb] 20479 512-byte hardware sectors (10 MB)
[ 1167.908000] sd 3:0:0:0: [sdb] Write Protect is off
[ 1167.908000] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1167.908000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1167.908000]  sdb: sdb1
[ 1168.084000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 1168.084000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 1168.272000] sr1: scsi3-mmc drive: 93x/93x cd/rw xa/form2 cdda tray
[ 1168.272000] sr 3:0:0:1: Attached scsi CD-ROM sr1
[ 1168.272000] sr 3:0:0:1: Attached scsi generic sg3 type 5
[ 1169.212000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1169.212000] ISOFS: changing to secondary root
[ 1780.808000] usb 7-1: USB disconnect, address 2
[ 1780.904000] scsi 3:0:0:1: rejecting I/O to dead device
[ 1780.904000] scsi 3:0:0:1: rejecting I/O to dead device
[ 1801.576000] usb 7-1: new high speed USB device using ehci_hcd and address 3
[ 1801.712000] usb 7-1: configuration #1 chosen from 1 choice
[ 1801.712000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1801.712000] usb-storage: device found at 3
[ 1801.712000] usb-storage: waiting for device to settle before scanning
[ 1806.712000] usb-storage: device scan complete
[ 1806.712000] scsi 4:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
[ 1806.716000] sd 4:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[ 1806.716000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1806.716000] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1806.716000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1806.720000] sd 4:0:0:0: [sdb] 3932160 512-byte hardware sectors (2013 MB)
[ 1806.720000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1806.720000] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1806.720000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1806.720000]  sdb: sdb1
[ 1806.772000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1806.772000] sd 4:0:0:0: Attached scsi generic sg2 type 0


```

BTW, the wireless networking has never worked since I did this (clean) install. I appreciate the help.

---

### Post by MountainX on 2008-02-20
stil haven't gotten wireless working... help is appreciated

---

### Post by Yellow Pasque on 2008-02-21
Well, let's make sure you have a driver loaded. Run this for me:
```
sudo lshw -C network
```

---

### Post by MountainX on 2008-02-21
The command 
```
sudo lshw -C network
```
shows the wireless interface with information that all looks correct. I cannot paste it ATM because I'm on my Windows box in order to get Internet access.

I did some experimenting and I might have a clue. The Wireless AP is set up to allow only WPA2 connections (highest security). When I use Ubuntu's "Network Settings" dialog to set the wireless connection properties, if I choose WPA2 Personal, and then run iwconfig, eth1 has no ESSID and no access point MAC. However, if I set the properties to WEP key (ascii) and run iwconfig, it shows the correct ESSID and the correct access point MAC address too. However, I cannot connect and I suspect it is because the wireless AP is rejecting due to the security level. How can I verify that is the issue? Thanks.

---

### Post by MountainX on 2008-02-21
I confirmed that my issue is related to a security setting. When I changed my router from WPA2 to WEP and changed the corresponding settings in Ubuntu, I was able to connect wirelessly for the first time.

So my challenge now is to figure out how to get WPA2 security working with Ubuntu. (The Windows machines on the network connect to the router using WPA2 already.)

---

### Post by MountainX on 2008-02-21
Now that I know my issue is related to WPA I started doing some research. Am I the only ThinkPad Ubuntu Gutsy user who can't get WPA wireless security working? At ThinkWiki for installing 7.10 on the TP T61p they don't even mention an issue with WPA.

I found the following site:
[http://www.linux.com/articles/56946](http://www.linux.com/articles/56946)

It says "Where previously you had to jump through hoops to do WPA or 802.1x authentication, network manager makes this completely transparent."

And this one: [http://blogs.reucon.com/srt/2007/10/24/ubuntu_7_10_on_the_ibm_thinkpad_t43p.html](http://blogs.reucon.com/srt/2007/10/24/ubuntu_7_10_on_the_ibm_thinkpad_t43p.html)
Is says, "Ubuntu recognized the internal WLAN adapter, provided a list of available wireless networks, asked for the WPA key and obtained the network config through DHCP"

What am I missing? Why does it work for others with ThinkPads but not me? BTW, I have a D-Link WBR-1310 router.

 Is the following bug applicable?
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/132473](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/132473)

Thanks

---

### Post by rakusson on 2008-02-21
hi, 

I had the same problem with me (I use T40 IPW 2100). I **resolved** it in the followinresolvedI g way.

Whenever you want to connect to WPA or WPA2, do the following.

1. Click the network icon on upper right hand corner and choose manual configuration.
2.  select Wireless and click properties.
3. The first thing you should do is UNCHECK 'enable roaming mode'.
4. Now put the necessary settings of your router in the given fields (I hope you know it).

Now you can fire your browser to check or type ifconfig in your terminal. 

I hope this will help you as I could not find other way around it.

---

### Post by MountainX on 2008-02-21
Here is all the info I can think of to provide:
```
~$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"my-essid"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:11:68:7C:6A   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-40 dBm  Noise level=-41 dBm
          Rx invalid nwid:0  Rx invalid crypt: 0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:225   Missed beacon:0

~$ ifconfig
[snip]
eth1      Link encap:Ethernet  HWaddr 00:1B:BF:85:FC:45  
          inet addr:192.168.1.102  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5168 errors:0 dropped:314 overruns:0 frame:0
          TX packets:3085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4553358 (4.3 MB)  TX bytes:535149 (522.6 KB)
          Interrupt:22 Base address:0xc000 Memory:d7dff000-d7dfffff 

~$ sudo lshw -C network
Password or swipe finger: 
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:86:99:22
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:bf:85:fc:45
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 link=no module=ipw3945 multicast=yes wireless=unassociated

~$ sudo ifconfig eth1 up
[returns no message]

~$ sudo lsmod | grep ipw3945
ipw3945               119840  1 
ieee80211              35656  1 ipw3945

I'm using DHCP

~$ /etc/init.d/wpasupplicant start
bash: /etc/init.d/wpasupplicant: No such file or directory


~$ sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -w
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.


I tried to create the following file given that it was not present:
/etc/wpa_supplicant.conf
However, I have not been able to understand all the details required to create the file.

Also I do not have /etc/default/wpasupplicant

Finally, I do not have a wireless icon in the upper left area of my screen.



```

---

### Post by MountainX on 2008-02-21
> **rakusson said:**
> hi, 

I had the same problem with me (I use T40 IPW 2100). I **resolved** it in the followinresolvedI g way.

Whenever you want to connect to WPA or WPA2, do the following.

1. Click the network icon on upper right hand corner and choose manual configuration.


I do not have that icon.

---

### Post by MountainX on 2008-02-21
**It is working now.**

Unfortunately, I cannot say exactly what I did to get it working. I tried a bunch of stuff and finally when I thought I had done all I could do, I rebooted my computer. When it came up, WPA wireless was working.

I think the thread that helped me the most was this one:
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

I had to create /etc/wpa_supplicant.conf as it said and I had to generate a wpa_passphrase. No other thread I have seen mentions using wpa_passphrase, but I think that was one key factor in getting this to work for me.

Other good links are:
[http://ph.ubuntuforums.com/showthread.php?t=571188](http://ph.ubuntuforums.com/showthread.php?t=571188)
[http://wiki.purduelug.org/PAL20Howto#head-13bbce7aae727998fff4a1847703554c7ab94a4c](http://wiki.purduelug.org/PAL20Howto#head-13bbce7aae727998fff4a1847703554c7ab94a4c)
[http://ubuntuforums.org/showpost.php?p=207693&postcount=2](http://ubuntuforums.org/showpost.php?p=207693&postcount=2)
[http://www.fmepnet.org/debian_wpa.html](http://www.fmepnet.org/debian_wpa.html)

[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4248112](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4248112) - good summary of networking commands

As a noob, I find all this extremely confusing. Why do most people have WPA working out of the box with Gutsy on the ThinkPads and I had to go through days of troubleshooting and manually create the config files, etc?

 I've been working for more than a month to get everything working on my laptop -- this has been damn hard!

Next I have to tackle suspend/hibernate and my TrackPoint mouse...

---

