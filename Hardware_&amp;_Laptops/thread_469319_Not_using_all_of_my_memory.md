---
title: "Not using all of my memory?"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by Opeth115 on 2007-06-09
Okay, well i have uninstalled Ubuntu and reinstalled numerous times (not for this specific problem but still have anyway), and whenever it get's past grub it gives me some sort of failed to allocate memory resources... everything still loads but im not sure if this means anything. i would jsut like to know why it does this and if there is anyway i could fix it.  After numerouse reinstalls it still appears....I have 2 gigs of corsair DDR2 XMS2 if that helps...

---

### Post by Opeth115 on 2007-06-09
anybody have any ideas?

---

### Post by 444 on 2007-06-09
I think it would have more to do with some device you have and not the ram.
So... use the dmesg command to hopefully get the exact error and give us the model of whatever it is we're talking about.

---

### Post by trippinnik on 2007-06-09
yeah dmesg or the exact error message at bootup would be helpful.

---

### Post by Opeth115 on 2007-06-09
ok well this is the out put of dmsg in the terminal the error at bootup goes by way to fast for me to write it down all ic an read is failed to allocate mem resources

```
[    0.000000]  BIOS-e820: 000000007eef3000 - 000000007eeff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eeff000 - 000000007ef00000 (usable)
[    0.000000]  BIOS-e820: 000000007ef00000 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 1135MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe200
[    0.000000] Entering add_active_range(0, 0, 519936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   519936
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   519936
[    0.000000] On node 0 totalpages: 519936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2270 pages used for memmap
[    0.000000]   HighMem zone: 288290 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 INTEL                                 ) @ 0x000fe020
[    0.000000] ACPI: RSDT (v001 INTEL  DP965LT  0x00000671      0x01000013) @ 0x7eefd038
[    0.000000] ACPI: FADT (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eefc000
[    0.000000] ACPI: MADT (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eef6000
[    0.000000] ACPI: WDDT (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eef5000
[    0.000000] ACPI: MCFG (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eef4000
[    0.000000] ACPI: ASF! (v032 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x7eef3000
[    0.000000] ACPI: SSDT (v001 INTEL     CpuPm 0x00000671 MSFT 0x01000013) @ 0x7eead000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu0Ist 0x00000671 MSFT 0x01000013) @ 0x7eeac000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu1Ist 0x00000671 MSFT 0x01000013) @ 0x7eeab000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu2Ist 0x00000671 MSFT 0x01000013) @ 0x7eeaa000
[    0.000000] ACPI: SSDT (v001 INTEL   Cpu3Ist 0x00000671 MSFT 0x01000013) @ 0x7eea9000
[    0.000000] ACPI: DSDT (v001 INTEL  DP965LT  0x00000671 MSFT 0x01000013) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f000000:80f00000)
[    0.000000] Detected 1864.892 MHz processor.
[   17.619503] Built 1 zonelists.  Total pages: 515874
[   17.619506] Kernel command line: root=UUID=d8450be9-62ea-426d-9913-bf4acc45384b ro quiet splash
[   17.619629] mapped APIC to ffffd000 (fee00000)
[   17.619631] mapped IOAPIC to ffffc000 (fec00000)
[   17.619633] Enabling fast FPU save and restore... done.
[   17.619635] Enabling unmasked SIMD FPU exception support... done.
[   17.619641] Initializing CPU#0
[   17.619683] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   17.620880] Console: colour VGA+ 80x25
[   17.621059] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.621288] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.686951] Memory: 2049972k/2079744k available (1992k kernel code, 27592k reserved, 900k data, 328k init, 1161500k highmem)
[   17.686960] virtual kernel memory layout:
[   17.686960]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.686961]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.686962]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.686964]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.686965]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   17.686966]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   17.686967]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   17.686969] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.763666] Calibrating delay using timer specific routine.. 3732.58 BogoMIPS (lpj=7465177)
[   17.763699] Security Framework v1.0.0 initialized
[   17.763704] SELinux:  Disabled at boot.
[   17.763717] Mount-cache hash table entries: 512
[   17.763829] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   17.763835] monitor/mwait feature present.
[   17.763837] using mwait in idle threads.
[   17.763840] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.763843] CPU: L2 cache: 2048K
[   17.763845] CPU: Physical Processor ID: 0
[   17.763846] CPU: Processor Core ID: 0
[   17.763848] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   17.763856] Compat vDSO mapped to ffffe000.
[   17.763859] Remapping vsyscall page to ffffe000
[   17.763869] Checking 'hlt' instruction... OK.
[   17.779751] SMP alternatives: switching to UP code
[   17.780058] Early unpacking initramfs... done
[   18.063028] ACPI: Core revision 20060707
[   18.063795] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.066611] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[   18.066627] SMP alternatives: switching to SMP code
[   18.066683] Booting processor 1/1 eip 3000
[   18.077051] Initializing CPU#1
[   18.155601] Calibrating delay using timer specific routine.. 3729.89 BogoMIPS (lpj=7459791)
[   18.155607] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   18.155611] monitor/mwait feature present.
[   18.155614] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.155615] CPU: L2 cache: 2048K
[   18.155617] CPU: Physical Processor ID: 0
[   18.155618] CPU: Processor Core ID: 1
[   18.155620] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   18.156001] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[   18.156017] Total of 2 processors activated (7462.48 BogoMIPS).
[   18.156157] ENABLING IO-APIC IRQs
[   18.156321] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.303586] checking TSC synchronization across 2 CPUs: passed.
[    0.003999] Brought up 2 CPUs
[    0.123374] migration_cost=91
[    0.123595] Booting paravirtualized kernel on bare hardware
[    0.123658] Time: 12:28:48  Date: 05/09/107
[    0.123680] NET: Registered protocol family 16
[    0.123748] EISA bus registered
[    0.123754] ACPI: bus type pci registered
[    0.125134] PCI: Using configuration type 1
[    0.125136] Setting up standard PCI resources
[    0.136087] ACPI: Interpreter enabled
[    0.136089] ACPI: Using IOAPIC for interrupt routing
[    0.136467] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.136475] PCI: Probing PCI hardware (bus 00)
[    0.136489] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.138036] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.138040] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[    0.138221] Boot video device is 0000:01:00.0
[    0.138757] PCI: Transparent bridge - 0000:00:1e.0
[    0.138830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.143357] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.143936] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.144145] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.144342] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.144542] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.144744] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
[    0.144942] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.145139] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.145335] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.146732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.146936] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.147135] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.147338] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.147540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.148793] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.148804] pnp: PnP ACPI init
[    0.151306] pnp: PnP ACPI: found 12 devices
[    0.151310] PnPBIOS: Disabled by ACPI PNP
[    0.151349] PCI: Using ACPI for IRQ routing
[    0.151351] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.151429] NET: Registered protocol family 8
[    0.151430] NET: Registered protocol family 20
[    0.151502] pnp: 00:06: ioport range 0x500-0x53f has been reserved
[    0.151505] pnp: 00:06: ioport range 0x400-0x47f could not be reserved
[    0.151507] pnp: 00:06: ioport range 0x680-0x6ff has been reserved
**[    0.151776] PCI: Failed to allocate mem resource #6:20000@90000000 for 0000:01:00.0**
[    0.151812] PCI: Bridge: 0000:00:01.0
[    0.151814]   IO window: 2000-2fff
[    0.151817]   MEM window: 90000000-91ffffff
[    0.151820]   PREFETCH window: 80000000-8fffffff
[    0.151823] PCI: Bridge: 0000:00:1c.0
[    0.151824]   IO window: disabled.
[    0.151828]   MEM window: 92300000-923fffff
[    0.151831]   PREFETCH window: disabled.
[    0.151835] PCI: Bridge: 0000:00:1c.1
[    0.151838]   IO window: 1000-1fff
[    0.151842]   MEM window: 92100000-921fffff
[    0.151845]   PREFETCH window: disabled.
[    0.151849] PCI: Bridge: 0000:00:1c.2
[    0.151850]   IO window: disabled.
[    0.151854]   MEM window: 92400000-924fffff
[    0.151857]   PREFETCH window: disabled.
[    0.151861] PCI: Bridge: 0000:00:1c.3
[    0.151862]   IO window: disabled.
[    0.151866]   MEM window: 92500000-925fffff
[    0.151869]   PREFETCH window: disabled.
[    0.151873] PCI: Bridge: 0000:00:1c.4
[    0.151874]   IO window: disabled.
[    0.151878]   MEM window: 92600000-926fffff
[    0.151881]   PREFETCH window: disabled.
[    0.151885] PCI: Bridge: 0000:00:1e.0
[    0.151886]   IO window: disabled.
[    0.151891]   MEM window: 92000000-920fffff
[    0.151894]   PREFETCH window: disabled.
[    0.151906] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.151910] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.151925] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    0.151930] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.151944] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    0.151949] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.151985] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.151989] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.152005] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[    0.152009] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.152024] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[    0.152028] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.152037] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.152059] NET: Registered protocol family 2
[    0.204276] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.204362] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.204791] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.204978] TCP: Hash tables configured (established 131072 bind 65536)
[    0.204980] TCP reno registered
[    0.220447] checking if image is initramfs... it is
[    0.777171] Freeing initrd memory: 6782k freed
[    0.777676] audit: initializing netlink socket (disabled)
[    0.777689] audit(1181392128.540:1): initialized
[    0.777768] highmem bounce pool size: 64 pages
[    0.777835] VFS: Disk quotas dquot_6.5.1
[    0.777850] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.777889] io scheduler noop registered
[    0.777891] io scheduler anticipatory registered
[    0.777893] io scheduler deadline registered
[    0.777902] io scheduler cfq registered (default)
[    0.778329] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.778359] assign_interrupt_mode Found MSI capability
[    0.778361] Allocate Port Service[0000:00:01.0:pcie00]
[    0.778436] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.778471] assign_interrupt_mode Found MSI capability
[    0.778473] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.778505] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.778588] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.778623] assign_interrupt_mode Found MSI capability
[    0.778625] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.778653] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.778735] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.778770] assign_interrupt_mode Found MSI capability
[    0.778772] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.778799] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.778883] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.778919] assign_interrupt_mode Found MSI capability
[    0.778921] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.778950] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.779033] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.779069] assign_interrupt_mode Found MSI capability
[    0.779071] Allocate Port Service[0000:00:1c.4:pcie00]
[    0.779098] Allocate Port Service[0000:00:1c.4:pcie02]
[    0.779233] isapnp: Scanning for PnP cards...
[    1.132080] isapnp: No Plug & Play device found
[    1.150083] Real Time Clock Driver v1.12ac
[    1.150127] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.150235] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.150770] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.150919] mice: PS/2 mouse device common for all mice
[    1.151383] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.151503] input: Macintosh mouse button emulation as /class/input/input0
[    1.151533] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.151536] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.151702] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.154586] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.154589] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.154693] EISA: Probing bus 0 at eisa.0
[    1.154699] Cannot allocate resource for EISA slot 1
[    1.154701] Cannot allocate resource for EISA slot 2
[    1.154703] Cannot allocate resource for EISA slot 3
[    1.154720] EISA: Detected 0 cards.
[    1.184228] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.184800] TCP cubic registered
[    1.184807] NET: Registered protocol family 1
[    1.184824] Starting balanced_irq
[    1.184829] Using IPI No-Shortcut mode
[    1.184907] ACPI: (supports S0 S3 S4 S5)
[    1.184943]   Magic number: 11:871:480
[    1.185113] Freeing unused kernel memory: 328k freed
[    1.187799] Time: tsc clocksource has been installed.
[    2.363585] Capability LSM initialized
[    2.397708] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.397787] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.397793] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.397800] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.698266] usbcore: registered new interface driver usbfs
[    2.698288] usbcore: registered new interface driver hub
[    2.698315] usbcore: registered new device driver usb
[    2.804743] USB Universal Host Controller Interface driver v3.0
[    2.805026] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.805036] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    2.805039] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.805234] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.805260] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000030a0
[    2.805640] usb usb1: configuration #1 chosen from 1 choice
[    2.805764] hub 1-0:1.0: USB hub found
[    2.805771] hub 1-0:1.0: 2 ports detected
[    2.805922] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    2.805924] Copyright (c) 1999-2006 Intel Corporation.
[    2.819049] ieee1394: Initialized config rom entry `ip1394'
[    2.827126] SCSI subsystem initialized
[    2.832540] libata version 2.20 loaded.
[    2.910846] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[    2.910855] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    2.910859] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.910880] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.910905] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00003080
[    2.910990] usb usb2: configuration #1 chosen from 1 choice
[    2.911022] hub 2-0:1.0: USB hub found
[    2.911027] hub 2-0:1.0: 2 ports detected
[    3.015464] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[    3.015472] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.015475] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.015494] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    3.015520] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00003060
[    3.015602] usb usb3: configuration #1 chosen from 1 choice
[    3.015637] hub 3-0:1.0: USB hub found
[    3.015641] hub 3-0:1.0: 2 ports detected
[    3.119999] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.120007] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.120010] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.120032] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.120056] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003040
[    3.120137] usb usb4: configuration #1 chosen from 1 choice
[    3.120159] hub 4-0:1.0: USB hub found
[    3.120164] hub 4-0:1.0: 2 ports detected
[    3.224995] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.225003] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.225006] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.225026] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.225050] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003020
[    3.225135] usb usb5: configuration #1 chosen from 1 choice
[    3.225158] hub 5-0:1.0: USB hub found
[    3.225163] hub 5-0:1.0: 2 ports detected
[    3.330058] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 22
[    3.330069] PCI: Setting latency timer of device 0000:00:19.0 to 64
[    3.358641] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:19:d1:0a:4d:63
[    3.452507] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.452603] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[    3.452615] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    3.452618] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.452642] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    3.452668] ehci_hcd 0000:00:1a.7: debug port 1
[    3.452674] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    3.452679] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x92225400
[    3.456557] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.456627] usb usb6: configuration #1 chosen from 1 choice
[    3.456648] hub 6-0:1.0: USB hub found
[    3.456653] hub 6-0:1.0: 4 ports detected
[    3.563366] ACPI: PCI Interrupt 0000:07:03.0[A] -> GSI 19 (level, low) -> IRQ 19
[    3.563372] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[    3.563383] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.563387] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.563409] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.563441] ehci_hcd 0000:00:1d.7: debug port 1
[    3.563447] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.563452] ehci_hcd 0000:00:1d.7: irq 21, io mem 0x92225000
[    3.567338] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.567400] usb usb7: configuration #1 chosen from 1 choice
[    3.567424] hub 7-0:1.0: USB hub found
[    3.567429] hub 7-0:1.0: 6 ports detected
[    3.613104] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[92004000-920047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.671688] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    3.671705] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    3.671723] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.671729] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.671745] ata1: PATA max UDMA/100 cmd 0x00011018 ctl 0x00011026 bmdma 0x00011000 irq 17
[    3.671748] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 19
[    3.671761] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.671763] scsi0 : pata_marvell
[    3.671785] ata2: SATA max UDMA/133 cmd 0x00013138 ctl 0x0001314e bmdma 0x00013110 irq 19
[    3.671809] ata3: SATA max UDMA/133 cmd 0x00013130 ctl 0x0001314a bmdma 0x00013118 irq 19
[    3.671816] scsi1 : ata_piix
[    3.671829] BAR5:00:00 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:01 0D:00 0E:00 0F:00 
[    3.839401] ATA: abnormal status 0x7F on port 0x0001313f
[    3.839420] scsi2 : ata_piix
[    4.024621] ata3.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[    4.024627] ata3.00: ATA-7: WDC WD4000KS-00MNB0, 07.02E07, max UDMA/133
[    4.024629] ata3.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.034939] ata3.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[    4.034943] ata3.00: configured for UDMA/133
[    4.035101] scsi 2:0:0:0: Direct-Access     ATA      WDC WD4000KS-00M 07.0 PQ: 0 ANSI: 5
[    4.035208] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[    4.035228] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 19
[    4.035243] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    4.035270] ata4: SATA max UDMA/133 cmd 0x00013128 ctl 0x00013146 bmdma 0x000130f0 irq 19
[    4.035320] ata5: SATA max UDMA/133 cmd 0x00013120 ctl 0x00013142 bmdma 0x000130f8 irq 19
[    4.035326] scsi3 : ata_piix
[    4.159700] ata1.00: ATAPI, max UDMA/66
[    4.159702] ata1.01: ATAPI, max UDMA/33
[    4.202116] ATA: abnormal status 0x7F on port 0x0001312f
[    4.202126] scsi4 : ata_piix
[    4.324827] ata1.00: configured for UDMA/66
[    4.367404] ATA: abnormal status 0x7F on port 0x00013127
[    4.490378] ata1.01: configured for UDMA/33
[    4.493657] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
[    4.497103] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
[    4.510567] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
[    4.510578] sda: Write Protect is off
[    4.510580] sda: Mode Sense: 00 3a 00 00
[    4.510593] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.510628] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
[    4.510636] sda: Write Protect is off
[    4.510637] sda: Mode Sense: 00 3a 00 00
[    4.510650] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.510653]  sda: sda1 sda2 <sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.526534] Uniform CD-ROM driver Revision: 3.20
[    4.526573] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.538541] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[    4.538578] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    4.540633]  sda5 > sda3
[    4.541121] sd 2:0:0:0: Attached scsi disk sda
[    4.541505] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    4.541523] sr 0:0:0:0: Attached scsi generic sg1 type 5
[    4.541540] sr 0:0:1:0: Attached scsi generic sg2 type 5
[    4.759699] Attempting manual resume
[    4.759701] swsusp: Resume From Partition 8:5
[    4.759703] PM: Checking swsusp image.
[    4.759885] PM: Resume from disk failed.
[    4.794079] kjournald starting.  Commit interval 5 seconds
[    4.794087] EXT3-fs: mounted filesystem with ordered data mode.
[    4.886974] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270001d98f6c]
[   11.804144] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[   11.807221] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   11.807225] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   12.695121] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.727317] shpchp: Unknown symbol acpi_run_oshp
[   12.727372] shpchp: Unknown symbol pci_hp_change_slot_info
[   12.727436] shpchp: Unknown symbol pci_hp_register
[   12.727599] shpchp: Unknown symbol pci_hp_deregister
[   12.727727] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   12.836513] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.852066] input: PC Speaker as /class/input/input2
[   12.984027] parport: PnPBIOS parport detected.
[   12.984078] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   13.013478] logips2pp: Detected unknown logitech mouse model 1
[   13.016207] Linux agpgart interface v0.102 (c) Dave Jones
[   13.018337] agpgart: Detected an Intel 965G Chipset.
[   13.030416] agpgart: AGP aperture is 256M @ 0x0
[   13.037139] iTCO_vendor_support: vendor-support=0
[   13.046639] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   13.107268] NET: Registered protocol family 17
[   13.180604] nvidia: module license 'NVIDIA' taints kernel.
[   13.184625] input: PS/2 Logitech Mouse as /class/input/input3
[   13.187530] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
[   13.187571] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.431507] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.431516] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   13.431589] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   13.558944] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   13.558959] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   14.143354] fuse init (API version 7.8)
[   14.168846] lp0: using parport0 (interrupt-driven).
[   14.275735] Adding 6024332k swap on /dev/disk/by-uuid/9e149e3b-abbe-432b-80d9-0894876c2d71.  Priority:-1 extents:1 across:6024332k
[   14.425758] EXT3 FS on sda1, internal journal
[   14.621901] kjournald starting.  Commit interval 5 seconds
[   14.622173] EXT3 FS on sda3, internal journal
[   14.622177] EXT3-fs: mounted filesystem with ordered data mode.
[   17.821889] NET: Registered protocol family 10
[   17.821964] lo: Disabled Privacy Extensions
[   19.923306] ibm_acpi: ec object not found
[   19.960781] No dock devices found.
[   19.991947] Using specific hotkey driver
[   20.057173] input: Power Button (FF) as /class/input/input4
[   20.057193] ACPI: Power Button (FF) [PWRF]
[   20.057225] input: Sleep Button (CM) as /class/input/input5
[   20.057242] ACPI: Sleep Button (CM) [SLPB]
[   20.130128] pcc_acpi: loading...
[   24.001327] ppdev: user-space parallel port driver
[   24.620050] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   24.620053] apm: disabled - APM is not SMP safe.
[   25.567570] Bluetooth: Core ver 2.11
[   25.567618] NET: Registered protocol family 31
[   25.567620] Bluetooth: HCI device and connection manager initialized
[   25.567623] Bluetooth: HCI socket layer initialized
[   25.598938] Bluetooth: L2CAP ver 2.8
[   25.598941] Bluetooth: L2CAP socket layer initialized
[   25.819764] Bluetooth: RFCOMM socket layer initialized
[   25.819773] Bluetooth: RFCOMM TTY layer initialized
[   25.819775] Bluetooth: RFCOMM ver 1.8
[   37.674345] eth0: no IPv6 routers present
[43248.445169] usb 4-2: new full speed USB device using uhci_hcd and address 2
[43248.651236] usb 4-2: configuration #1 chosen from 1 choice
[43248.819741] usbcore: registered new interface driver libusual
[43248.830398] Initializing USB Mass Storage driver...
[43248.830458] scsi5 : SCSI emulation for USB Mass Storage devices
[43248.830513] usbcore: registered new interface driver usb-storage
[43248.830516] USB Mass Storage support registered.
[43248.830603] usb-storage: device found at 2
[43248.830605] usb-storage: waiting for device to settle before scanning
[43252.237422] usb 4-2: USB disconnect, address 2
[43269.994517] usb 4-2: new full speed USB device using uhci_hcd and address 3
[43270.192501] usb 4-2: configuration #1 chosen from 1 choice
[43270.196539] scsi6 : SCSI emulation for USB Mass Storage devices
[43270.196950] usb-storage: device found at 3
[43270.196952] usb-storage: waiting for device to settle before scanning
[43275.198357] usb-storage: device scan complete
[43275.201364] scsi 6:0:0:0: Direct-Access     NIKON    NIKON DSC E4800  1.00 PQ: 0 ANSI: 2
[43275.206336] SCSI device sdb: 990976 512-byte hdwr sectors (507 MB)
[43275.209340] sdb: Write Protect is off
[43275.209343] sdb: Mode Sense: 18 00 00 08
[43275.209345] sdb: assuming drive cache: write through
[43275.218333] SCSI device sdb: 990976 512-byte hdwr sectors (507 MB)
[43275.221336] sdb: Write Protect is off
[43275.221339] sdb: Mode Sense: 18 00 00 08
[43275.221341] sdb: assuming drive cache: write through
[43275.221343]  sdb: sdb1
[43275.231366] sd 6:0:0:0: Attached scsi removable disk sdb
[43275.231410] sd 6:0:0:0: Attached scsi generic sg3 type 0
[45937.398689] usb 4-2: USB disconnect, address 3
[45937.453559] scsi 6:0:0:0: rejecting I/O to dead device
```

i don't really knwo what to look for in there but i highlight the only failed to allocate mem resource one

---

### Post by Opeth115 on 2007-06-10
This is my output for lspci also if that helps...

```

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by 444 on 2007-06-10
Well it seems to be refering to the video card. If you're not having any video problems don't worry about it.

---

### Post by Opeth115 on 2007-06-10
ok well would there be anyw ay i could get rid of it because im kidna nit picky about little things like that and it kinda annoys me lol

---

