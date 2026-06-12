---
title: "Fail to resume from sleep"
date: 2008-05-04
forum: Hardware
---

### Post by svk on 2008-05-04
Hello,

I recently upgraded from 7.10 to 8.04 and discovered a problem that previously didn't exist.  If my laptop sleeps for a long time (about an hour), nothing shows up on the display when I resume from sleep.  This is a problem if I leave my laptop on for a long time because it will go to sleep automatically.

Interestingly enough, Ubuntu remains fully functional: it's just that nothing shows up on the display.  As an experiment, I once left the music player on pause and walked away; two hours later, I came back and moved the mouse; nothing showed up, as expected, but when I hit the shortcut key to play, the music resumed playing.  So nothing crashes: the only problem is that the screen is blank.

I checked all the logs: there appears to be no evidence of anything wrong.  I'll post them anyway.

Here are the relevant specs for my laptop (as shown by **lshw**):
```

bijou
    product: HP Pavilion dv6000 (GA456UA#ABA)
    version: Rev 1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2

     *-display
          description: VGA compatible controller
          product: C51 [Geforce 6150 Go]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

```

My video card is nVidia GeForce 6150, as shown by **lspci**:
[FONT="Fixedsys"]00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)[/FONT]

The driver for this video card is a restricted driver from nVidia that Ubuntu installed automatically.  I don't know how to get any more information about it -- all it tells me in System -> Administration -> Hardware Drivers is that the "NVIDIA accelerated graphics driver (latest cards)" driver is in use.

Here are some of the log files that were generated in /var/log the last time this happened to me.  Note that **I left the laptop at about 14:00**, so the laptop went to sleep several minutes after that; **I came back at 15:45**, moved the mouse, and the display showed nothing.  I blindly ran a couple commands to copy these log files: [FONT="Fixedsys"]Alt+F2, gnome-terminal, ENTER, mkdir logs, sudo cp -R /var/log/* logs, *my_password*, ENTER[/FONT].  I restarted the x server (CTRL+ALT+BACKSPACE) and was delighted to find out that my commands did exactly what I wanted them to do, so I preserved all the logs when the incident happened.  Unfortunately, the logs don't show anything interesting.  Here they are anyway.

**syslog:**
```

May  4 14:06:30 bijou kernel: [  139.616492] irq 7: nobody cared (try booting with the "irqpoll" option)
May  4 14:06:30 bijou kernel: [  139.616501] Pid: 0, comm: swapper Tainted: P        2.6.24-16-generic #1
May  4 14:06:30 bijou kernel: [  139.616518]  [__report_bad_irq+0x24/0x80] __report_bad_irq+0x24/0x80
May  4 14:06:30 bijou kernel: [  139.616528]  [note_interrupt+0x27b/0x2c0] note_interrupt+0x27b/0x2c0
May  4 14:06:30 bijou kernel: [  139.616536]  [<f88aabab>] usb_hcd_irq+0x2b/0x60 [usbcore]
May  4 14:06:30 bijou kernel: [  139.616560]  [handle_IRQ_event+0x30/0x60] handle_IRQ_event+0x30/0x60
May  4 14:06:30 bijou kernel: [  139.616568]  [handle_level_irq+0x91/0xf0] handle_level_irq+0x91/0xf0
May  4 14:06:30 bijou kernel: [  139.616575]  [do_IRQ+0x3b/0x70] do_IRQ+0x3b/0x70
May  4 14:06:30 bijou kernel: [  139.616578]  [__switch_to+0x9e/0x150] __switch_to+0x9e/0x150
May  4 14:06:30 bijou kernel: [  139.616586]  [common_interrupt+0x23/0x30] common_interrupt+0x23/0x30
May  4 14:06:30 bijou kernel: [  139.616598]  [native_safe_halt+0x2/0x10] native_safe_halt+0x2/0x10
May  4 14:06:30 bijou kernel: [  139.616606]  [<f88710c0>] acpi_safe_halt+0x1c/0x29 [processor]
May  4 14:06:30 bijou kernel: [  139.616616]  [<f8871129>] acpi_idle_enter_c1+0x5c/0x64 [processor]
May  4 14:06:30 bijou kernel: [  139.616626]  [cpuidle_idle_call+0x7c/0xb0] cpuidle_idle_call+0x7c/0xb0
May  4 14:06:30 bijou kernel: [  139.616633]  [cpu_idle+0x45/0xd0] cpu_idle+0x45/0xd0
May  4 14:06:30 bijou kernel: [  139.616650]  =======================
May  4 14:06:30 bijou kernel: [  139.616652] handlers:
May  4 14:06:30 bijou kernel: [  139.616653] [<f88aab80>] (usb_hcd_irq+0x0/0x60 [usbcore])
May  4 14:06:30 bijou kernel: [  139.616671] Disabling IRQ #7
May  4 14:17:02 bijou /USR/SBIN/CRON[6331]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  4 14:43:19 bijou -- MARK --
May  4 15:03:19 bijou -- MARK --
May  4 15:17:01 bijou /USR/SBIN/CRON[6394]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  4 15:43:19 bijou -- MARK --

```

**messages:**
```

May  4 14:06:30 bijou kernel: [  139.616501] Pid: 0, comm: swapper Tainted: P        2.6.24-16-generic #1
May  4 14:06:30 bijou kernel: [  139.616518]  [__report_bad_irq+0x24/0x80] __report_bad_irq+0x24/0x80
May  4 14:06:30 bijou kernel: [  139.616528]  [note_interrupt+0x27b/0x2c0] note_interrupt+0x27b/0x2c0
May  4 14:06:30 bijou kernel: [  139.616536]  [<f88aabab>] usb_hcd_irq+0x2b/0x60 [usbcore]
May  4 14:06:30 bijou kernel: [  139.616560]  [handle_IRQ_event+0x30/0x60] handle_IRQ_event+0x30/0x60
May  4 14:06:30 bijou kernel: [  139.616568]  [handle_level_irq+0x91/0xf0] handle_level_irq+0x91/0xf0
May  4 14:06:30 bijou kernel: [  139.616575]  [do_IRQ+0x3b/0x70] do_IRQ+0x3b/0x70
May  4 14:06:30 bijou kernel: [  139.616578]  [__switch_to+0x9e/0x150] __switch_to+0x9e/0x150
May  4 14:06:30 bijou kernel: [  139.616586]  [common_interrupt+0x23/0x30] common_interrupt+0x23/0x30
May  4 14:06:30 bijou kernel: [  139.616598]  [native_safe_halt+0x2/0x10] native_safe_halt+0x2/0x10
May  4 14:06:30 bijou kernel: [  139.616606]  [<f88710c0>] acpi_safe_halt+0x1c/0x29 [processor]
May  4 14:06:30 bijou kernel: [  139.616616]  [<f8871129>] acpi_idle_enter_c1+0x5c/0x64 [processor]
May  4 14:06:30 bijou kernel: [  139.616626]  [cpuidle_idle_call+0x7c/0xb0] cpuidle_idle_call+0x7c/0xb0
May  4 14:06:30 bijou kernel: [  139.616633]  [cpu_idle+0x45/0xd0] cpu_idle+0x45/0xd0
May  4 14:06:30 bijou kernel: [  139.616650]  =======================
May  4 14:23:19 bijou -- MARK --
May  4 14:43:19 bijou -- MARK --
May  4 15:03:19 bijou -- MARK --
May  4 15:23:19 bijou -- MARK --
May  4 15:43:19 bijou -- MARK --

```

**dmesg:**
(I'm not sure how much of this is relevant, so I'm posting all of it).
```

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf00000 (usable)
[    0.000000]  BIOS-e820: 000000007bf00000 - 000000007bf15000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bf15000 - 000000007bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1087MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8920
[    0.000000] Entering add_active_range(0, 0, 507648) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   507648
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   507648
[    0.000000] On node 0 totalpages: 507648
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2174 pages used for memmap
[    0.000000]   HighMem zone: 276098 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F88F0 checksum 0
[    0.000000] ACPI: RSDP 000F88F0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 7BF0BB67, 0040 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 7BF14B58, 0074 (r1 HP     MCP51M    6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 7BF0BBA7, 8FB1 (r1 HP       MCP51M  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 7BF15FC0, 0040
[    0.000000] ACPI: SSDT 7BF14BCC, 01C4 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 7BF14D90, 003C (r1 HP       MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 7BF14DCC, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 7BF14E04, 005E (r1 HP     	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7BF14E62, 0028 (r1     HP $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 7BF14E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: nVIDIA   Product ID: C51-MCP51    APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503682
[    0.000000] Kernel command line: root=UUID=e790272e-2b61-4902-a770-09055aa76e95 ro noapic noirqpoll
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1808.250 MHz processor.
[   23.266804] spurious 8259A interrupt: IRQ7.
[   23.269940] Console: colour VGA+ 80x25
[   23.269944] console [tty0] enabled
[   23.273549] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.273998] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.365229] Memory: 2000752k/2030592k available (2157k kernel code, 28528k reserved, 998k data, 364k init, 1113088k highmem)
[   23.365302] virtual kernel memory layout:
[   23.365303]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   23.365305]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.365306]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.365307]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.365308]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   23.365309]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   23.365311]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   23.365711] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.365845] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   23.366055] hpet clockevent registered
[   23.446014] Calibrating delay using timer specific routine.. 3619.65 BogoMIPS (lpj=7239305)
[   23.446134] Security Framework initialized
[   23.446188] SELinux:  Disabled at boot.
[   23.446250] AppArmor: AppArmor initialized
[   23.446302] Failure registering capabilities with primary security module.
[   23.446362] Mount-cache hash table entries: 512
[   23.446536] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   23.446546] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.446600] CPU: L2 Cache: 512K (64 bytes/line)
[   23.446650] CPU 0(2) -> Core 0
[   23.446699] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   23.446709] Compat vDSO mapped to ffffe000.
[   23.446768] Checking 'hlt' instruction... OK.
[   23.462343] SMP alternatives: switching to UP code
[   23.463661] Early unpacking initramfs... done
[   23.815992] ACPI: Core revision 20070126
[   23.816117] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.818404] ACPI: setting ELCR to 0200 (from 0ca0)
[   24.026240] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   24.026378] SMP alternatives: switching to SMP code
[   24.026895] Booting processor 1/1 eip 3000
[   24.037144] Initializing CPU#1
[   24.117865] Calibrating delay using timer specific routine.. 3616.49 BogoMIPS (lpj=7232984)
[   24.117872] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   24.117879] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.117881] CPU: L2 Cache: 512K (64 bytes/line)
[   24.117884] CPU 1(2) -> Core 1
[   24.117885] AMD C1E detected late. 	Force timer broadcast.
[   24.117887] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   24.117805] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   24.118243] Total of 2 processors activated (7236.14 BogoMIPS).
[   24.118408] Brought up 2 CPUs
[   24.118482] CPU0 attaching sched-domain:
[   24.118484]  domain 0: span 03
[   24.118486]   groups: 01 02
[   24.118489] CPU1 attaching sched-domain:
[   24.118491]  domain 0: span 03
[   24.118493]   groups: 02 01
[   24.118697] net_namespace: 64 bytes
[   24.118753] Booting paravirtualized kernel on bare hardware
[   24.119284] Time: 14:03:00  Date: 05/04/08
[   24.119359] NET: Registered protocol family 16
[   24.119581] EISA bus registered
[   24.119632] ACPI: bus type pci registered
[   24.135297] PCI: BIOS BUG #81[49435000] found
[   24.135348] PCI: Using configuration type 1
[   24.135399] Setting up standard PCI resources
[   24.137119] ACPI: EC: Look up EC in DSDT
[   24.138984] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   24.139269] ACPI: Interpreter enabled
[   24.139319] ACPI: (supports S0 S3 S4 S5)
[   24.139520] ACPI: Using PIC for interrupt routing
[   24.140433] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   24.146511] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   24.146569] ACPI: EC: driver started in interrupt mode
[   24.146675] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.147981] PCI: Transparent bridge - 0000:00:10.0
[   24.148046] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.148137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   24.148163] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   24.148194] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   24.181564] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.182180] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   24.182733] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   24.183260] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.183869] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.184476] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.185085] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 *11 14 15)
[   24.185613] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.186224] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   24.186782] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   24.187311] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   24.187840] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   24.188368] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   24.188895] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.189505] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.190113] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.190741] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.191357] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   24.191888] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15)
[   24.192390] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.192467] pnp: PnP ACPI init
[   24.192522] ACPI: bus type pnp registered
[   24.195684] pnp: PnP ACPI: found 13 devices
[   24.195736] ACPI: ACPI bus type pnp unregistered
[   24.195788] PnPBIOS: Disabled by ACPI PNP
[   24.196075] PCI: Using ACPI for IRQ routing
[   24.196127] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.214508] NET: Registered protocol family 8
[   24.214559] NET: Registered protocol family 20
[   24.214644] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   24.214840] hpet0: 3 32-bit timers, 25000000 Hz
[   24.215933] AppArmor: AppArmor Filesystem Enabled
[   24.218277] Time: hpet clocksource has been installed.
[   24.218550] Clockevents: could not switch to one-shot mode:<6>Clockevents: could not switch to one-shot mode: lapic is not functional.
[   24.218342] Could not switch to high resolution mode on CPU 0
[   24.218707]  lapic is not functional.
[   24.218756] Could not switch to high resolution mode on CPU 1
[   24.234529] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[   24.234596] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[   24.237985] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   24.238048] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[   24.238111] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[   24.238168] system 00:03: iomem range 0xe0000000-0xefffffff could not be reserved
[   24.238233] system 00:04: ioport range 0x1000-0x107f has been reserved
[   24.238286] system 00:04: ioport range 0x1080-0x10ff has been reserved
[   24.238339] system 00:04: ioport range 0x1400-0x147f has been reserved
[   24.238393] system 00:04: ioport range 0x1480-0x14ff has been reserved
[   24.238446] system 00:04: ioport range 0x1800-0x187f has been reserved
[   24.238517] system 00:04: ioport range 0x1880-0x18ff has been reserved
[   24.238570] system 00:04: ioport range 0x2000-0x203f has been reserved
[   24.238626] system 00:05: ioport range 0x360-0x361 has been reserved
[   24.238679] system 00:05: ioport range 0x380-0x383 has been reserved
[   24.238732] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[   24.269206] PCI: Bridge: 0000:00:02.0
[   24.269256]   IO window: 4000-4fff
[   24.269307]   MEM window: b4000000-b5ffffff
[   24.269357]   PREFETCH window: d0000000-d01fffff
[   24.269408] PCI: Bridge: 0000:00:03.0
[   24.269457]   IO window: disabled.
[   24.269507]   MEM window: b6000000-b7ffffff
[   24.269557]   PREFETCH window: d0200000-d03fffff
[   24.269609] PCI: Bridge: 0000:00:10.0
[   24.269657]   IO window: disabled.
[   24.269708]   MEM window: b8000000-b80fffff
[   24.269758]   PREFETCH window: disabled.
[   24.269819] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.269826] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   24.269833] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   24.269844] NET: Registered protocol family 2
[   24.314518] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.314843] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.315727] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.316205] TCP: Hash tables configured (established 131072 bind 65536)
[   24.316258] TCP reno registered
[   24.330598] checking if image is initramfs... it is
[   25.015893] Freeing initrd memory: 7688k freed
[   25.016055] Simple Boot Flag at 0x36 set to 0x1
[   25.016772] audit: initializing netlink socket (disabled)
[   25.016836] audit(1209909780.444:1): initialized
[   25.017076] highmem bounce pool size: 64 pages
[   25.019030] VFS: Disk quotas dquot_6.5.1
[   25.019151] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.019328] io scheduler noop registered
[   25.019378] io scheduler anticipatory registered
[   25.019429] io scheduler deadline registered
[   25.019487] io scheduler cfq registered (default)
[   25.019552] Boot video device is 0000:00:05.0
[   25.230096] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.230120] assign_interrupt_mode Found MSI capability
[   25.230191] Allocate Port Service[0000:00:02.0:pcie00]
[   25.230256] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   25.230277] assign_interrupt_mode Found MSI capability
[   25.230342] Allocate Port Service[0000:00:03.0:pcie00]
[   25.230568] isapnp: Scanning for PnP cards...
[   25.583401] isapnp: No Plug & Play device found
[   25.611706] Real Time Clock Driver v1.12ac
[   25.611955] hpet_resources: 0xfed00000 is busy
[   25.612008] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.613222] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.613349] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.613505] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   25.630455] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.630516] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.649583] mice: PS/2 mouse device common for all mice
[   25.649770] EISA: Probing bus 0 at eisa.0
[   25.649825] Cannot allocate resource for EISA slot 1
[   25.649876] Cannot allocate resource for EISA slot 2
[   25.649927] Cannot allocate resource for EISA slot 3
[   25.649979] Cannot allocate resource for EISA slot 4
[   25.650043] EISA: Detected 0 cards.
[   25.650093] cpuidle: using governor ladder
[   25.650143] cpuidle: using governor menu
[   25.650282] NET: Registered protocol family 1
[   25.650362] Using IPI No-Shortcut mode
[   25.650442] registered taskstats version 1
[   25.650623]   Magic number: 8:290:80
[   25.650862] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.650914] EDD information not available.
[   25.651203] Freeing unused kernel memory: 364k freed
[   25.662608] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   25.891555] fuse init (API version 7.9)
[   25.915637] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   25.915915] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   25.917821] ACPI: Thermal Zone [THRM] (55 C)
[   26.474788] usbcore: registered new interface driver usbfs
[   26.474863] usbcore: registered new interface driver hub
[   26.474959] usbcore: registered new device driver usb
[   26.475984] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.476304] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   26.476358] PCI: setting IRQ 11 as level-triggered
[   26.476362] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   26.476508] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   26.476511] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   26.476852] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   26.476930] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
[   26.531211] usb usb1: configuration #1 chosen from 1 choice
[   26.531288] hub 1-0:1.0: USB hub found
[   26.531346] hub 1-0:1.0: 8 ports detected
[   26.545290] SCSI subsystem initialized
[   26.584833] libata version 3.00 loaded.
[   26.633570] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   26.633626] PCI: setting IRQ 7 as level-triggered
[   26.633631] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   26.633773] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   26.633776] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   26.633851] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   26.633942] ehci_hcd 0000:00:0b.1: debug port 1
[   26.633994] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   26.634002] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
[   26.645015] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.645193] usb usb2: configuration #1 chosen from 1 choice
[   26.645268] hub 2-0:1.0: USB hub found
[   26.645322] hub 2-0:1.0: 8 ports detected
[   26.749115] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   26.749460] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   26.749513] PCI: setting IRQ 10 as level-triggered
[   26.749517] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   26.749656] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   27.160948] usb 2-4: new high speed USB device using ehci_hcd and address 2
[   27.269094] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1b:24:7c:9b:64
[   27.269162] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   27.269391] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   27.269416] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   27.269730] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   27.269783] PCI: setting IRQ 5 as level-triggered
[   27.269787] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   27.269938] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.269946] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[   27.272394] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   27.272450] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   27.302274] usb 2-4: configuration #1 chosen from 1 choice
[   27.324343] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   27.328704] pata_amd 0000:00:0d.0: version 0.3.10
[   27.328753] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   27.332830] scsi0 : pata_amd
[   27.334361] scsi1 : pata_amd
[   27.334982] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[   27.335037] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[   27.668921] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-L632M, 0A17, max MWDMA2
[   27.788554] usb 1-6: new low speed USB device using ohci_hcd and address 2
[   27.856755] ata1.00: configured for MWDMA2
[   27.856836] ata2: port disabled. ignoring.
[   27.865246] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632M 0A17 PQ: 0 ANSI: 5
[   27.865849] sata_nv 0000:00:0e.0: version 3.5
[   27.865863] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   27.866036] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.866096] scsi2 : sata_nv
[   27.866294] scsi3 : sata_nv
[   27.866511] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 5
[   27.866565] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 5
[   28.000401] usb 1-6: configuration #1 chosen from 1 choice
[   28.018633] usbcore: registered new interface driver hiddev
[   28.024444] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.0/input/input2
[   28.044255] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-6
[   28.044471] usbcore: registered new interface driver usbhid
[   28.044523] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.332271] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.340443] ata3.00: ATA-7: FUJITSU MHW2160BH PL, 891F, max UDMA/100
[   28.340497] ata3.00: 312581808 sectors, multi 16: LBA48 
[   28.356434] ata3.00: configured for UDMA/100
[   28.604014] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00e7a34100]
[   28.668073] ata4: SATA link down (SStatus 0 SControl 300)
[   28.678780] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2160B 891F PQ: 0 ANSI: 5
[   28.687478] Driver 'sr' needs updating - please use bus_type methods
[   28.694259] Driver 'sd' needs updating - please use bus_type methods
[   28.780556] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   28.780626] Uniform CD-ROM driver Revision: 3.20
[   28.780728] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   28.780850] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   28.780918] sd 2:0:0:0: [sda] Write Protect is off
[   28.780970] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.780987] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.784461] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   28.784525] sd 2:0:0:0: [sda] Write Protect is off
[   28.784576] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.784617] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.784682]  sda: sda1 sda2 sda3 sda4 <<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   28.787424] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   28.849686]  sda5 sda6 sda7 >
[   28.881015] sd 2:0:0:0: [sda] Attached SCSI disk
[   29.319677] Attempting manual resume
[   29.319729] swsusp: Resume From Partition 8:7
[   29.319731] PM: Checking swsusp image.
[   29.320018] PM: Resume from disk failed.
[   29.348424] kjournald starting.  Commit interval 5 seconds
[   29.348486] EXT3-fs: mounted filesystem with ordered data mode.
[   36.135708] input: Power Button (FF) as /devices/virtual/input/input3
[   36.159618] ACPI: Power Button (FF) [PWRF]
[   36.159774] input: Power Button (CM) as /devices/virtual/input/input4
[   36.187599] ACPI: Power Button (CM) [PWRB]
[   36.187743] input: Sleep Button (CM) as /devices/virtual/input/input5
[   36.219588] ACPI: Sleep Button (CM) [SLPB]
[   36.219720] input: Lid Switch as /devices/virtual/input/input6
[   36.226822] ACPI: Lid Switch [LID]
[   36.231844] ACPI: AC Adapter [ACAD] (on-line)
[   36.338199] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.367797] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.439533] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   36.439614] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   36.479712] Linux agpgart interface v0.102
[   36.575171] nvidia: module license 'NVIDIA' taints kernel.
[   37.191603] ACPI: Battery Slot [BAT0] (battery present)
[   37.191743] ACPI: WMI-Acer: Mapper loaded
[   37.194301] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
[   37.223266] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   37.224837] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:26/LNXVIDEO:01/input/input8
[   37.255248] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   37.493445] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 11
[   37.493502] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 11 (level, low) -> IRQ 11
[   37.493641] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   37.493860] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   37.998841] Linux video capture interface: v2.00
[   38.203542] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   38.205159] usbcore: registered new interface driver uvcvideo
[   38.205213] USB Video Class driver (v0.1.0)
[   38.358627] ricoh-mmc: Ricoh MMC Controller disabling driver
[   38.358684] ricoh-mmc: Copyright(c) Philip Langdale
[   38.358770] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   38.358839] ricoh-mmc: Controller is now disabled.
[   38.395710] sdhci: Secure Digital Host Controller Interface driver
[   38.395768] sdhci: Copyright(c) Pierre Ossman
[   38.395866] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   38.396203] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   38.396255] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   38.396405] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   38.396512] mmc0: SDHCI at 0xb8000800 irq 11 DMA
[   38.797607] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   38.797665] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   38.797815] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   39.258729] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   39.321807] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   40.169394] lp: driver loaded but no devices found
[   40.267540] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   40.380716] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   40.381460] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 9
[   40.381517] PCI: setting IRQ 9 as level-triggered
[   40.381520] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 9 (level, low) -> IRQ 9
[   40.381704] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   40.396671] ndiswrapper: using IRQ 9
[   40.629691] wlan0: ethernet device 00:1a:73:77:81:cc using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[   40.629797] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   40.635009] usbcore: registered new interface driver ndiswrapper
[   40.704606] Adding 2000052k swap on /dev/sda7.  Priority:-1 extents:1 across:2000052k
[   41.040499] EXT3 FS on sda3, internal journal
[   41.474964] kjournald starting.  Commit interval 5 seconds
[   41.475490] EXT3 FS on sda6, internal journal
[   41.475494] EXT3-fs: mounted filesystem with ordered data mode.
[   42.225096] ip_tables: (C) 2000-2006 Netfilter Core Team

```

**acpid:**
```

[Sun May  4 03:26:23 2008] logfile reopened
[Sun May  4 13:36:13 2008] client connected from 23493[0:0]
[Sun May  4 13:36:13 2008] 1 client rule loaded
[Sun May  4 13:36:14 2008] client connected from 23493[0:0]
[Sun May  4 13:36:14 2008] 1 client rule loaded
[Sun May  4 14:00:48 2008] client connected from 24005[0:0]
[Sun May  4 14:00:48 2008] 1 client rule loaded
[Sun May  4 14:00:49 2008] client connected from 24005[0:0]
[Sun May  4 14:00:49 2008] 1 client rule loaded
[Sun May  4 14:02:23 2008] exiting
[Sun May  4 14:03:19 2008] starting up
[Sun May  4 14:03:19 2008] 74 rules loaded
[Sun May  4 14:03:21 2008] client connected from 5709[111:123]
[Sun May  4 14:03:21 2008] 1 client rule loaded
[Sun May  4 14:03:22 2008] client connected from 5866[0:0]
[Sun May  4 14:03:22 2008] 1 client rule loaded
[Sun May  4 14:03:24 2008] client connected from 5866[0:0]
[Sun May  4 14:03:24 2008] 1 client rule loaded
[Sun May  4 15:45:28 2008] client connected from 5866[0:0]
[Sun May  4 15:45:28 2008] 1 client rule loaded

```

**Xorg.0.log:**
```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux bijou 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May  4 14:03:22 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f0 card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 103c,30b7 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 103c,30b7 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 0000,0000 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0244 card 103c,30b7 rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 103c,30b7 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 103c,30b7 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 103c,30b7 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:3: chip 10de,0271 card 103c,30b7 rev a3 class 0b,40,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 103c,30b7 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 103c,30b7 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card f03c,30b7 rev f1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 103c,30b7 rev f1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 103c,30b7 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 103c,30b7 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 03:00:0: chip 14e4,4328 card 103c,1366 rev 03 class 02,80,00 hdr 00
(II) PCI: 07:05:0: chip 1180,0832 card 103c,30b7 rev 00 class 0c,00,10 hdr 80
(II) PCI: 07:05:1: chip 1180,0822 card 103c,30b7 rev 19 class 08,05,00 hdr 80
(II) PCI: 07:05:2: chip 1180,0592 card 103c,30b7 rev 0a class 08,80,00 hdr 80
(II) PCI: 07:05:3: chip 1180,0852 card 103c,30b7 rev 05 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xb4000000 - 0xb5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd01fffff (0x200000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:3:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xb6000000 - 0xb7ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xd03fffff (0x200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:16:0), (0,7,7), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xb8000000 - 0xb80fffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51 [Geforce 6150 Go] rev 162, Mem @ 0xb2000000/24, 0xc0000000/28, 0xb1000000/24
(--) PCI: (0:10:3) nVidia Corporation MCP51 PMU rev 163, Mem @ 0xb0040000/18
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[1] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[2] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[3] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[4] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
	[5] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[6] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[7] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[8] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[9] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[10] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[11] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[12] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[16] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[17] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[18] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[19] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[20] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[21] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[22] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[23] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[24] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[1] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[2] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[3] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[4] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
	[5] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[6] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[7] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[8] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[9] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[10] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[11] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[12] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[16] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[17] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[18] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[19] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[20] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[21] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[22] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[23] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[24] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[5] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[6] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[7] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[8] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
	[9] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[10] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[11] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[12] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[13] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[14] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[15] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[16] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[22] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[23] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[24] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[25] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[26] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[27] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[28] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[29] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[30] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
(--) Assigning device section with no busID to primary device
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:10:3) found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[5] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[6] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[7] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[8] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
	[9] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[10] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[11] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[12] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[13] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[14] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[15] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[16] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[22] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[23] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[24] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[25] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[26] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[27] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[28] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[29] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[30] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[5] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[6] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[7] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[8] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
	[9] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[10] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[11] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[12] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[13] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[14] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[15] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[16] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[25] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[26] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[27] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[28] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[29] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[30] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[31] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[32] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[33] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 6150 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.28.53.15
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 6150 at PCI:0:5:0:
(--) NVIDIA(0):     LPL (DFP-0)
(--) NVIDIA(0): LPL (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb8001000 - 0xb80010ff (0x100) MX[B]
	[5] -1	0	0xb8000c00 - 0xb8000cff (0x100) MX[B]
	[6] -1	0	0xb8000800 - 0xb80008ff (0x100) MX[B]
	[7] -1	0	0xb8000000 - 0xb80007ff (0x800) MX[B]
	[8] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
	[9] -1	0	0xb6000000 - 0xb6003fff (0x4000) MX[B]
	[10] -1	0	0xb0008000 - 0xb0008fff (0x1000) MX[B]
	[11] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[12] -1	0	0xb0006000 - 0xb0006fff (0x1000) MX[B]
	[13] -1	0	0xb0005000 - 0xb00050ff (0x100) MX[B]
	[14] -1	0	0xb0004000 - 0xb0004fff (0x1000) MX[B]
	[15] -1	0	0xb0040000 - 0xb007ffff (0x40000) MX[B]
	[16] -1	0	0xb1000000 - 0xb1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xb2000000 - 0xb2ffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x000030e0 - 0x000030e7 (0x8) IX[B]
	[25] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[26] -1	0	0x000030b0 - 0x000030b3 (0x4) IX[B]
	[27] -1	0	0x000030b8 - 0x000030bf (0x8) IX[B]
	[28] -1	0	0x000030b4 - 0x000030b7 (0x4) IX[B]
	[29] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[30] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[31] -1	0	0x00003000 - 0x0000303f (0x40) IX[B]
	[32] -1	0	0x00003040 - 0x0000307f (0x40) IX[B]
	[33] -1	0	0x00001d00 - 0x00001d7f (0x80) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

Please help me with this problem!  It's really annoying to have to kill the x server every time I leave my laptop for longer than an hour.  

All thanks in advance!

---

### Post by crobinson55331 on 2008-05-04
If it makes you feel any better, I have exactly the same issue.  The screen looks like it wants to resume - goes from completely blank to a light grey - the only solution is a ctl-alt-bksp to kill x and resume.  If you find solution, please share.

---

### Post by svk on 2008-05-04
Well, I did find a cheap workaround.  Instead of rebooting or doing ctrl+alt+backspace, you can switch to the terminal by pressing ctrl+alt+f1, and then switching back to the graphical display by pressing ctrl+alt+f7.  That way, you won't lose everything you had open.

Of course, I'd love to hear about an actual fix.

---

### Post by NiklasV on 2008-05-06
The above workaround can be automated by uncommenting the line
```

DOUBLE_CONSOLE_SWITCH=true

```
in /etc/default/acpi-support.

---

### Post by tamias on 2008-05-06
I have reported this issue at [http://ubuntuforums.org/showthread.php?p=4788709](http://ubuntuforums.org/showthread.php?p=4788709) and am still waiting for a solution.

In the meantime, as the laptop is fully usable albeit with the monitor switched off, you can force the DPMS mode of the monitor to 'on' by issuing the command

```
sudo vbetool dpms on
```

at one of the TTYs (Ctrl+Alt+F1 etc). After entering your password the monitor will wake up.

As for getting this to happen automatically, no such luck as of yet!

---

### Post by suzypeppercorn on 2008-05-06
I have the same exact laptop and i'm experiencing the same problem. I hope a fix comes soon.

---

### Post by kikapu on 2008-05-06
Mine is the same but a little different problem. I also have problems with suspend and i do some things i read here:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61)

I can resume but only this way:
- i put my thinkpad to suspend (sleep)
- i press Fn to wake it up. It tries to wake but it cannot resume and goes to sleep again (!)
- i press Fn again. Now it wakes up and display a white screen. Although i cannot see anythin, i type my password and computer is back on again! The wifi now is off and i have to run Wicd again, but until a fix is provided this is the only way for me here...

---

### Post by spoolboyy on 2008-05-07
I have this exact same problem with my Dell C800 laptop (512mb ram, 1.0ghz cpu and nVidia Geforce 2 Go graphics card) running Ubuntu 8.04.

Interestingly enough I had the same issue when I ran xUbuntu 7.10 on it previous to updating to 8.04.  I just never let it go to sleep.

I have noticed the same things that the others have mentioned and will make the additional comment that this only seems to happen when the machine goes into hibernate mode or sleep.  If the monitor just shuts off due to inactivity, the screen comes back on (at least for me).

any word on this?

-Adam

---

### Post by tamias on 2008-05-07
Yes, I can confirm that it's only an issue with hibernate/suspend. If the monitor is DPMS-blanked after a timeout, it always wakes up fine for me.

Incidentally, as reported elsewhere ([http://ubuntuforums.org/showthread.php?p=4788709](http://ubuntuforums.org/showthread.php?p=4788709)) I sometimes receive a chorus of fast, high-pitched beeps when this problem occurs. I'm still wondering if there's a bug in gnome-power-manager or something that is causing it to crash.

Can anyone help me to debug this issue? There are several of us now reporting problems and I'd love to file a bug report, but still have no idea what package is at fault.

---

### Post by suzypeppercorn on 2008-05-09
i wish i could be of more help but i am new to linux.

If you needed to confirm anything on my laptop just tell me what steps to follow.

---

### Post by Merdril on 2008-05-10
I have an HP Pavilion dv6353us and I had the same problem for a while but I found a workaround with KDE. I enabled power management (can't remember how to do it and I'm writing this post on Windows XP atm) and set the monitor sleeping times how I wanted. Ever since, i never had that black screen problem. Hope this helps.

---

### Post by tamias on 2008-05-13
Thanks for your reply, Merdril.

I don't understand what you mean by "enabled power management" -- this should always be running on a laptop anyway. I can certainly already set monitor sleep times etc. on my laptop, but it makes no difference to the broken DPMS control in Hardy.

---

### Post by barzam on 2008-05-14
I have the same problem, and I solve it by just entering my password then enter, I figure I just can't see the field. 

Try it out, it works for my on my dell laptop.

---

### Post by djails on 2008-05-14
Hi everyone,
I also had a "fail to resume" problem, although mine has probably a different cause from yours, but I managed to get resume to work by using
```
sudo /etc/acpi/sleep.sh force
``` to get the laptop to sleep. By doing so, it does resume fine, although I still get the high pitch noise.
Let me know if it helps.

---

### Post by tamias on 2008-05-27
I seem to have been able to fix this problem by executing

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The replacement /etc/X11/xorg.conf is very much shorter than the previous version which the dpkg reconfigure replaced: in particular, it contains no information about available screen modes. Yet, it seems to work. I assume something in my older xorg.conf was breaking the DPMS resume.

---

### Post by svk on 2008-05-29
I was able to "fix" this issue by downgrading my video card driver.  I have an nVidia GO 6150 and it was running on the restricted driver that Hardy Heron automatically found.  To downgrade the driver, I installed the envy-ng package, ran the EnvyNG application (in Applications -> System Tools -> EnvyNG), and selected to install the NVIDIA driver version 96.43.05.  This also fixed another (possibly related) issue where I [could only see a blank screen instead of a tty terminal]("https://bugs.launchpad.net/ubuntu/+bug/155100") when I hit any of ctrl+alt+F1 through ctrl+alt+F6.  However, I am still experiencing frequent system-wide video freezes, but they may be related instead to compiz-fusion.  

I should note that I had none of these problems in Gutsy.

---

