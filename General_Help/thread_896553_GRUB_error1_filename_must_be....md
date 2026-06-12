---
title: "GRUB error1: filename must be..."
date: 2008-08-21
forum: General Help
---

### Post by Elf Wizard on 2008-08-21
[COLOR=Navy]**Hi!** :D

After installing wubi (at xp sp3 pro Eng. x86, ntfs formated) and rebooting, I'm getting this GRUB error:

"[COLOR=Red]Error1: Filename must be either an absolu[COLOR=Red]te pathname or blocklist[/COLOR][/COLOR]"


A search for this error, indicates that is filesystem related, but without any further details.:confused:

Any hints maybe? :D[/COLOR]

---

### Post by schloss on 2008-09-14
I get the same error. Help please?

---

### Post by Elf Wizard on 2008-09-15
> **schloss said:**
> I get the same error. Help please?

[COLOR=Navy]If you have a secondary windows installation (as a temporary solution) you can install it there.

Eg. if you have a windows installation at c: and another one on d:, boot from d: and install it from there (even at c: ).

OK! I know this is not the ideal solution, just a temporary workaround. [/COLOR]

---

### Post by ago on 2008-09-15
Press insert rapidly at boot after selecting Ubuntu, this will provide more information. Post it here.

---

### Post by Elf Wizard on 2008-09-16
> **ago said:**
> Press insert rapidly at boot after selecting Ubuntu, this will provide more information. Post it here.

[COLOR=Navy]I tried installing it again, but although this time booted correctly, setup failed because of partman error.

I received a "partman crashed" message, with the exit code 10.
Just in case, i'm posting the var/log/syslog:[/COLOR] 

```
Sep 16 08:56:07 ubuntu syslogd 1.5.0#1ubuntu1: restart.
Sep 16 08:56:07 ubuntu kernel: Inspecting /boot/System.map-2.6.24-19-generic
Sep 16 08:56:07 ubuntu kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Sep 16 08:56:07 ubuntu kernel: Symbols match kernel version 2.6.24.
Sep 16 08:56:08 ubuntu kernel: Loaded 18393 symbols from 90 modules.
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Sep 16 08:56:08 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 16 08:56:08 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep 16 08:56:08 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 16 08:56:08 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 16 08:56:08 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
Sep 16 08:56:08 ubuntu kernel: [    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
Sep 16 08:56:08 ubuntu kernel: [    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
Sep 16 08:56:08 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Sep 16 08:56:08 ubuntu kernel: [    0.000000] 0MB HIGHMEM available.
Sep 16 08:56:08 ubuntu kernel: [    0.000000] 511MB LOWMEM available.
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Zone PFN ranges:
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   DMA             0 ->     4096
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   Normal       4096 ->   131056
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   HighMem    131056 ->   131056
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Sep 16 08:56:08 ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep 16 08:56:08 ubuntu kernel: [    0.000000]     0:        0 ->   131056
Sep 16 08:56:08 ubuntu kernel: [    0.000000] On node 0 totalpages: 131056
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   Normal zone: 991 pages used for memmap
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   Normal zone: 125969 pages, LIFO batch:31
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Sep 16 08:56:08 ubuntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Sep 16 08:56:08 ubuntu kernel: [    0.000000] DMI 2.3 present.
Sep 16 08:56:08 ubuntu kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7470 checksum 0
Sep 16 08:56:08 ubuntu kernel: [    0.000000] ACPI: RSDP 000F7470, 0014 (r0 AWARD )
Sep 16 08:56:08 ubuntu kernel: [    0.000000] ACPI: RSDT 1FFF3000, 0028 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
Sep 16 08:56:08 ubuntu kernel: [    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
Sep 16 08:56:08 ubuntu kernel: [    0.000000] ACPI: DSDT 1FFF30C0, 3B02 (r1 AWARD  AWRDACPI     1000 MSFT  100000C)
Sep 16 08:56:08 ubuntu kernel: [    0.000000] ACPI: FACS 1FFF0000, 0040
Sep 16 08:56:08 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
Sep 16 08:56:08 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Sep 16 08:56:08 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Sep 16 08:56:08 ubuntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130033
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Kernel command line: debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=el_GR.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Sep 16 08:56:08 ubuntu kernel: [    0.000000] mapped APIC to ffffb000 (0140d000)
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Initializing CPU#0
Sep 16 08:56:08 ubuntu kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Sep 16 08:56:08 ubuntu kernel: [    0.000000] Detected 1991.943 MHz processor.
Sep 16 08:56:08 ubuntu kernel: [   23.237112] Console: colour VGA+ 80x25
Sep 16 08:56:08 ubuntu kernel: [   23.237118] console [tty0] enabled
Sep 16 08:56:08 ubuntu kernel: [   23.237427] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 16 08:56:08 ubuntu kernel: [   23.237753] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 16 08:56:08 ubuntu kernel: [   23.255261] Memory: 507012k/524224k available (2177k kernel code, 16580k reserved, 1006k data, 368k init, 0k highmem)
Sep 16 08:56:08 ubuntu kernel: [   23.255274] virtual kernel memory layout:
Sep 16 08:56:08 ubuntu kernel: [   23.255275]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep 16 08:56:08 ubuntu kernel: [   23.255277]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 16 08:56:08 ubuntu kernel: [   23.255278]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Sep 16 08:56:08 ubuntu kernel: [   23.255280]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
Sep 16 08:56:08 ubuntu kernel: [   23.255281]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Sep 16 08:56:08 ubuntu kernel: [   23.255283]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
Sep 16 08:56:08 ubuntu kernel: [   23.255284]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
Sep 16 08:56:08 ubuntu kernel: [   23.255289] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep 16 08:56:08 ubuntu kernel: [   23.255338] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Sep 16 08:56:08 ubuntu kernel: [   23.335353] Calibrating delay using timer specific routine.. 3988.27 BogoMIPS (lpj=7976556)
Sep 16 08:56:08 ubuntu kernel: [   23.335386] Security Framework initialized
Sep 16 08:56:08 ubuntu kernel: [   23.335395] SELinux:  Disabled at boot.
Sep 16 08:56:08 ubuntu kernel: [   23.335413] AppArmor: AppArmor initialized
Sep 16 08:56:08 ubuntu kernel: [   23.335420] Failure registering capabilities with primary security module.
Sep 16 08:56:08 ubuntu kernel: [   23.335432] Mount-cache hash table entries: 512
Sep 16 08:56:08 ubuntu kernel: [   23.335608] Initializing cgroup subsys ns
Sep 16 08:56:08 ubuntu kernel: [   23.335613] Initializing cgroup subsys cpuacct
Sep 16 08:56:08 ubuntu kernel: [   23.335628] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
Sep 16 08:56:08 ubuntu kernel: [   23.335646] CPU: Trace cache: 12K uops, L1 D cache: 8K
Sep 16 08:56:08 ubuntu kernel: [   23.335650] CPU: L2 cache: 512K
Sep 16 08:56:08 ubuntu kernel: [   23.335654] CPU: Hyper-Threading is disabled
Sep 16 08:56:08 ubuntu kernel: [   23.335657] CPU: After all inits, caps: 3febf9ff 00000000 00000000 0000b080 00000000 00000000 00000000 00000000
Sep 16 08:56:08 ubuntu kernel: [   23.335674] Compat vDSO mapped to ffffe000.
Sep 16 08:56:08 ubuntu kernel: [   23.335692] Checking 'hlt' instruction... OK.
Sep 16 08:56:08 ubuntu kernel: [   23.351894] SMP alternatives: switching to UP code
Sep 16 08:56:08 ubuntu kernel: [   23.354070] Freeing SMP alternatives: 11k freed
Sep 16 08:56:08 ubuntu kernel: [   23.354244] Early unpacking initramfs... done
Sep 16 08:56:08 ubuntu kernel: [   23.836941] ACPI: Core revision 20070126
Sep 16 08:56:08 ubuntu kernel: [   23.837014] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Sep 16 08:56:08 ubuntu kernel: [   23.839107] ACPI: setting ELCR to 0200 (from 0ca0)
Sep 16 08:56:08 ubuntu kernel: [   23.925092] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
Sep 16 08:56:08 ubuntu kernel: [   23.925100] SMP motherboard not detected.
Sep 16 08:56:08 ubuntu kernel: [   23.925104] Local APIC not detected. Using dummy APIC emulation.
Sep 16 08:56:08 ubuntu kernel: [   23.925171] Brought up 1 CPUs
Sep 16 08:56:08 ubuntu kernel: [   23.925195] CPU0 attaching sched-domain:
Sep 16 08:56:08 ubuntu kernel: [   23.925200]  domain 0: span 01
Sep 16 08:56:08 ubuntu kernel: [   23.925203]   groups: 01
Sep 16 08:56:08 ubuntu kernel: [   23.925473] net_namespace: 64 bytes
Sep 16 08:56:08 ubuntu kernel: [   23.925482] Booting paravirtualized kernel on bare hardware
Sep 16 08:56:08 ubuntu kernel: [   23.926249] Time:  8:55:18  Date: 09/16/08
Sep 16 08:56:08 ubuntu kernel: [   23.926285] NET: Registered protocol family 16
Sep 16 08:56:08 ubuntu kernel: [   23.926595] EISA bus registered
Sep 16 08:56:08 ubuntu kernel: [   23.926613] ACPI: bus type pci registered
Sep 16 08:56:08 ubuntu kernel: [   23.939781] PCI: PCI BIOS revision 2.10 entry at 0xfb380, last bus=1
Sep 16 08:56:08 ubuntu kernel: [   23.939785] PCI: Using configuration type 1
Sep 16 08:56:08 ubuntu kernel: [   23.939791] Setting up standard PCI resources
Sep 16 08:56:08 ubuntu kernel: [   23.942929] ACPI: EC: Look up EC in DSDT
Sep 16 08:56:08 ubuntu kernel: [   23.947520] ACPI: Interpreter enabled
Sep 16 08:56:08 ubuntu kernel: [   23.947525] ACPI: (supports S0 S3 S4 S5)
Sep 16 08:56:08 ubuntu kernel: [   23.947547] ACPI: Using PIC for interrupt routing
Sep 16 08:56:08 ubuntu kernel: [   23.953248] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 16 08:56:08 ubuntu kernel: [   23.953516] Enabling SiS 96x SMBus.
Sep 16 08:56:08 ubuntu kernel: [   23.954641] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep 16 08:56:08 ubuntu kernel: [   23.985501] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Sep 16 08:56:08 ubuntu kernel: [   23.985642] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Sep 16 08:56:08 ubuntu kernel: [   23.985780] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Sep 16 08:56:08 ubuntu kernel: [   23.985918] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Sep 16 08:56:08 ubuntu kernel: [   23.986055] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Sep 16 08:56:08 ubuntu kernel: [   23.986194] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Sep 16 08:56:08 ubuntu kernel: [   23.986333] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Sep 16 08:56:08 ubuntu kernel: [   23.986471] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Sep 16 08:56:08 ubuntu kernel: [   23.986643] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep 16 08:56:08 ubuntu kernel: [   23.986690] pnp: PnP ACPI init
Sep 16 08:56:08 ubuntu kernel: [   23.986703] ACPI: bus type pnp registered
Sep 16 08:56:08 ubuntu kernel: [   23.989828] pnp: PnP ACPI: found 10 devices
Sep 16 08:56:08 ubuntu kernel: [   23.989832] ACPI: ACPI bus type pnp unregistered
Sep 16 08:56:08 ubuntu kernel: [   23.989838] PnPBIOS: Disabled by ACPI PNP
Sep 16 08:56:08 ubuntu kernel: [   23.990195] PCI: Using ACPI for IRQ routing
Sep 16 08:56:08 ubuntu kernel: [   23.990199] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Sep 16 08:56:08 ubuntu kernel: [   24.043261] NET: Registered protocol family 8
Sep 16 08:56:08 ubuntu kernel: [   24.043264] NET: Registered protocol family 20
Sep 16 08:56:08 ubuntu kernel: [   24.043368] AppArmor: AppArmor Filesystem Enabled
Sep 16 08:56:08 ubuntu kernel: [   24.047248] Time: tsc clocksource has been installed.
Sep 16 08:56:08 ubuntu kernel: [   24.055310] system 00:00: iomem range 0xcfc00-0xcffff has been reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055315] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055319] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055322] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055326] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055331] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055335] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055339] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055343] system 00:00: iomem range 0xffee0000-0xffefffff has been reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055347] system 00:00: iomem range 0xfffe0000-0xfffeffff has been reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055351] system 00:00: iomem range 0xfee00000-0xfeefffff has been reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055362] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Sep 16 08:56:08 ubuntu kernel: [   24.055365] system 00:02: ioport range 0x800-0x805 has been reserved
Sep 16 08:56:08 ubuntu kernel: [   24.086014] PCI: Bridge: 0000:00:01.0
Sep 16 08:56:08 ubuntu kernel: [   24.086017]   IO window: disabled.
Sep 16 08:56:08 ubuntu kernel: [   24.086026]   MEM window: e4000000-e5ffffff
Sep 16 08:56:08 ubuntu kernel: [   24.086032]   PREFETCH window: d0000000-dfffffff
Sep 16 08:56:08 ubuntu kernel: [   24.086062] NET: Registered protocol family 2
Sep 16 08:56:08 ubuntu kernel: [   24.123351] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Sep 16 08:56:08 ubuntu kernel: [   24.123689] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Sep 16 08:56:08 ubuntu kernel: [   24.123785] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Sep 16 08:56:08 ubuntu kernel: [   24.123882] TCP: Hash tables configured (established 16384 bind 16384)
Sep 16 08:56:08 ubuntu kernel: [   24.123885] TCP reno registered
Sep 16 08:56:08 ubuntu kernel: [   24.135426] checking if image is initramfs... it is
Sep 16 08:56:08 ubuntu kernel: [   24.587191] Switched to high resolution mode on CPU 0
Sep 16 08:56:08 ubuntu kernel: [   25.083483] Freeing initrd memory: 7939k freed
Sep 16 08:56:08 ubuntu kernel: [   25.084158] audit: initializing netlink socket (disabled)
Sep 16 08:56:08 ubuntu kernel: [   25.084177] audit(1221555318.748:1): initialized
Sep 16 08:56:08 ubuntu kernel: [   25.087270] VFS: Disk quotas dquot_6.5.1
Sep 16 08:56:08 ubuntu kernel: [   25.087391] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 16 08:56:08 ubuntu kernel: [   25.087598] io scheduler noop registered
Sep 16 08:56:08 ubuntu kernel: [   25.087602] io scheduler anticipatory registered
Sep 16 08:56:08 ubuntu kernel: [   25.087604] io scheduler deadline registered
Sep 16 08:56:08 ubuntu kernel: [   25.087623] io scheduler cfq registered (default)
Sep 16 08:56:08 ubuntu kernel: [   25.087674] pci 0000:00:0a.0: HCRESET not completed yet!
Sep 16 08:56:08 ubuntu kernel: [   25.087692] pci 0000:00:0a.1: HCRESET not completed yet!
Sep 16 08:56:08 ubuntu kernel: [   25.087729] Boot video device is 0000:01:00.0
Sep 16 08:56:08 ubuntu kernel: [   25.088116] isapnp: Scanning for PnP cards...
Sep 16 08:56:08 ubuntu kernel: [   25.442438] isapnp: No Plug & Play device found
Sep 16 08:56:08 ubuntu kernel: [   25.487551] Real Time Clock Driver v1.12ac
Sep 16 08:56:08 ubuntu kernel: [   25.487693] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep 16 08:56:08 ubuntu kernel: [   25.489519] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 16 08:56:08 ubuntu kernel: [   25.489626] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 16 08:56:08 ubuntu kernel: [   25.489780] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Sep 16 08:56:08 ubuntu kernel: [   25.490113] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 16 08:56:08 ubuntu kernel: [   25.490119] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 16 08:56:08 ubuntu kernel: [   25.495217] mice: PS/2 mouse device common for all mice
Sep 16 08:56:08 ubuntu kernel: [   25.495396] EISA: Probing bus 0 at eisa.0
Sep 16 08:56:08 ubuntu kernel: [   25.495405] Cannot allocate resource for EISA slot 1
Sep 16 08:56:08 ubuntu kernel: [   25.495417] Cannot allocate resource for EISA slot 4
Sep 16 08:56:08 ubuntu kernel: [   25.495435] EISA: Detected 0 cards.
Sep 16 08:56:08 ubuntu kernel: [   25.495440] cpuidle: using governor ladder
Sep 16 08:56:08 ubuntu kernel: [   25.495443] cpuidle: using governor menu
Sep 16 08:56:08 ubuntu kernel: [   25.495580] NET: Registered protocol family 1
Sep 16 08:56:08 ubuntu kernel: [   25.495623] Using IPI No-Shortcut mode
Sep 16 08:56:08 ubuntu kernel: [   25.495667] registered taskstats version 1
Sep 16 08:56:08 ubuntu kernel: [   25.495808]   Magic number: 8:956:927
Sep 16 08:56:08 ubuntu kernel: [   25.495898]   hash matches device ptyxc
Sep 16 08:56:08 ubuntu kernel: [   25.495967] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 16 08:56:08 ubuntu kernel: [   25.495970] EDD information not available.
Sep 16 08:56:08 ubuntu kernel: [   25.496391] Freeing unused kernel memory: 368k freed
Sep 16 08:56:08 ubuntu kernel: [   25.521035] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Sep 16 08:56:08 ubuntu kernel: [   26.826353] fuse init (API version 7.9)
Sep 16 08:56:08 ubuntu kernel: [   26.852857] ACPI: Fan [FAN] (on)
Sep 16 08:56:08 ubuntu kernel: [   26.865050] ACPI: Thermal Zone [THRM] (40 C)
Sep 16 08:56:08 ubuntu kernel: [   27.722656] usbcore: registered new interface driver usbfs
Sep 16 08:56:08 ubuntu kernel: [   27.722692] usbcore: registered new interface driver hub
Sep 16 08:56:08 ubuntu kernel: [   27.726164] SCSI subsystem initialized
Sep 16 08:56:08 ubuntu kernel: [   27.753613] usbcore: registered new device driver usb
Sep 16 08:56:08 ubuntu kernel: [   27.834611] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep 16 08:56:08 ubuntu kernel: [   27.834669] 8139cp 0000:00:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Sep 16 08:56:08 ubuntu kernel: [   27.834675] 8139cp 0000:00:09.0: Try the "8139too" driver instead.
Sep 16 08:56:08 ubuntu kernel: [   27.846451] libata version 3.00 loaded.
Sep 16 08:56:08 ubuntu kernel: [   27.863785] 8139too Fast Ethernet driver 0.9.28
Sep 16 08:56:08 ubuntu kernel: [   27.864115] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
Sep 16 08:56:08 ubuntu kernel: [   27.864119] PCI: setting IRQ 10 as level-triggered
Sep 16 08:56:08 ubuntu kernel: [   27.864124] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Sep 16 08:56:08 ubuntu kernel: [   27.864919] eth0: RealTek RTL8139 at 0xa400, 00:1d:0f:c0:79:1f, IRQ 10
Sep 16 08:56:08 ubuntu kernel: [   27.864923] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Sep 16 08:56:08 ubuntu kernel: [   27.880220] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 16 08:56:08 ubuntu kernel: [   27.880507] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
Sep 16 08:56:08 ubuntu kernel: [   27.880512] PCI: setting IRQ 7 as level-triggered
Sep 16 08:56:08 ubuntu kernel: [   27.880517] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Sep 16 08:56:08 ubuntu kernel: [   27.880538] ohci_hcd 0000:00:02.2: OHCI Host Controller
Sep 16 08:56:08 ubuntu kernel: [   27.880953] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
Sep 16 08:56:08 ubuntu kernel: [   27.880977] ohci_hcd 0000:00:02.2: irq 7, io mem 0xe7011000
Sep 16 08:56:08 ubuntu kernel: [   27.895390] USB Universal Host Controller Interface driver v3.0
Sep 16 08:56:08 ubuntu kernel: [   27.936704] usb usb1: configuration #1 chosen from 1 choice
Sep 16 08:56:08 ubuntu kernel: [   27.936743] hub 1-0:1.0: USB hub found
Sep 16 08:56:08 ubuntu kernel: [   27.936758] hub 1-0:1.0: 3 ports detected
Sep 16 08:56:08 ubuntu kernel: [   28.014881] Floppy drive(s): fd0 is 1.44M
Sep 16 08:56:08 ubuntu kernel: [   28.034353] FDC 0 is a post-1991 82077
Sep 16 08:56:08 ubuntu kernel: [   28.038659] ACPI: PCI Interrupt 0000:00:02.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Sep 16 08:56:08 ubuntu kernel: [   28.038683] ohci_hcd 0000:00:02.3: OHCI Host Controller
Sep 16 08:56:08 ubuntu kernel: [   28.038719] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
Sep 16 08:56:08 ubuntu kernel: [   28.038737] ohci_hcd 0000:00:02.3: irq 7, io mem 0xe7014000
Sep 16 08:56:08 ubuntu kernel: [   28.096659] usb usb2: configuration #1 chosen from 1 choice
Sep 16 08:56:08 ubuntu kernel: [   28.096698] hub 2-0:1.0: USB hub found
Sep 16 08:56:08 ubuntu kernel: [   28.096710] hub 2-0:1.0: 3 ports detected
Sep 16 08:56:08 ubuntu kernel: [   28.203144] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
Sep 16 08:56:08 ubuntu kernel: [   28.203151] PCI: setting IRQ 5 as level-triggered
Sep 16 08:56:08 ubuntu kernel: [   28.203156] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
Sep 16 08:56:08 ubuntu kernel: [   28.203173] uhci_hcd 0000:00:0a.0: UHCI Host Controller
Sep 16 08:56:08 ubuntu kernel: [   28.203229] uhci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 3
Sep 16 08:56:08 ubuntu kernel: [   28.203262] uhci_hcd 0000:00:0a.0: irq 5, io base 0x0000a800
Sep 16 08:56:08 ubuntu kernel: [   28.203454] usb usb3: configuration #1 chosen from 1 choice
Sep 16 08:56:08 ubuntu kernel: [   28.203490] hub 3-0:1.0: USB hub found
Sep 16 08:56:08 ubuntu kernel: [   28.203499] hub 3-0:1.0: 2 ports detected
Sep 16 08:56:08 ubuntu kernel: [   28.306614] ACPI: PCI Interrupt 0000:00:0a.1[b] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Sep 16 08:56:08 ubuntu kernel: [   28.306635] uhci_hcd 0000:00:0a.1: UHCI Host Controller
Sep 16 08:56:08 ubuntu kernel: [   28.306669] uhci_hcd 0000:00:0a.1: new USB bus registered, assigned bus number 4
Sep 16 08:56:08 ubuntu kernel: [   28.306700] uhci_hcd 0000:00:0a.1: irq 7, io base 0x0000ac00
Sep 16 08:56:08 ubuntu kernel: [   28.306864] usb usb4: configuration #1 chosen from 1 choice
Sep 16 08:56:08 ubuntu kernel: [   28.306904] hub 4-0:1.0: USB hub found
Sep 16 08:56:08 ubuntu kernel: [   28.306913] hub 4-0:1.0: 2 ports detected
Sep 16 08:56:08 ubuntu kernel: [   28.410778] sata_via 0000:00:0c.0: version 2.3
Sep 16 08:56:08 ubuntu kernel: [   28.411033] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Sep 16 08:56:08 ubuntu kernel: [   28.411039] PCI: setting IRQ 11 as level-triggered
Sep 16 08:56:08 ubuntu kernel: [   28.411044] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Sep 16 08:56:08 ubuntu kernel: [   28.411115] sata_via 0000:00:0c.0: routed to hard irq line 11
Sep 16 08:56:08 ubuntu kernel: [   28.413750] scsi0 : sata_via
Sep 16 08:56:08 ubuntu kernel: [   28.415012] scsi1 : sata_via
Sep 16 08:56:08 ubuntu kernel: [   28.416208] scsi2 : sata_via
Sep 16 08:56:08 ubuntu kernel: [   28.416281] ata1: SATA max UDMA/133 port i16@0xb000 bmdma 0xc000 irq 11
Sep 16 08:56:08 ubuntu kernel: [   28.416286] ata2: SATA max UDMA/133 port i16@0xb400 bmdma 0xc008 irq 11
Sep 16 08:56:08 ubuntu kernel: [   28.416289] ata3: PATA max UDMA/133 port i16@0xb800 bmdma 0xc010 irq 11
Sep 16 08:56:08 ubuntu kernel: [   28.674384] usb 3-2: new full speed USB device using uhci_hcd and address 2
Sep 16 08:56:08 ubuntu kernel: [   28.856380] usb 3-2: configuration #1 chosen from 1 choice
Sep 16 08:56:08 ubuntu kernel: [   28.882341] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 16 08:56:08 ubuntu kernel: [   28.890968] ata1.00: ATA-8: ST3500320AS, SD15, max UDMA/133
Sep 16 08:56:08 ubuntu kernel: [   28.890973] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Sep 16 08:56:08 ubuntu kernel: [   28.906941] ata1.00: configured for UDMA/133
Sep 16 08:56:08 ubuntu kernel: [   29.218256] ata2: SATA link down (SStatus 0 SControl 310)
Sep 16 08:56:08 ubuntu kernel: [   29.393899] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
Sep 16 08:56:08 ubuntu kernel: [   29.394186] ACPI: PCI Interrupt 0000:00:0a.2[C] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Sep 16 08:56:08 ubuntu kernel: [   29.394228] ehci_hcd 0000:00:0a.2: EHCI Host Controller
Sep 16 08:56:08 ubuntu kernel: [   29.394594] ehci_hcd 0000:00:0a.2: new USB bus registered, assigned bus number 5
Sep 16 08:56:08 ubuntu kernel: [   29.394651] ehci_hcd 0000:00:0a.2: irq 11, io mem 0xe7013000
Sep 16 08:56:08 ubuntu kernel: [   29.406142] Driver 'sd' needs updating - please use bus_type methods
Sep 16 08:56:08 ubuntu kernel: [   29.406239] ehci_hcd 0000:00:0a.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Sep 16 08:56:08 ubuntu kernel: [   29.406407] usb usb5: configuration #1 chosen from 1 choice
Sep 16 08:56:08 ubuntu kernel: [   29.406445] hub 5-0:1.0: USB hub found
Sep 16 08:56:08 ubuntu kernel: [   29.406455] hub 5-0:1.0: 4 ports detected
Sep 16 08:56:08 ubuntu kernel: [   29.406542] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Sep 16 08:56:08 ubuntu kernel: [   29.406562] sd 0:0:0:0: [sda] Write Protect is off
Sep 16 08:56:08 ubuntu kernel: [   29.406565] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 16 08:56:08 ubuntu kernel: [   29.406595] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 16 08:56:08 ubuntu kernel: [   29.406666] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Sep 16 08:56:08 ubuntu kernel: [   29.406682] sd 0:0:0:0: [sda] Write Protect is off
Sep 16 08:56:08 ubuntu kernel: [   29.406686] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 16 08:56:08 ubuntu kernel: [   29.406714] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 16 08:56:08 ubuntu kernel: [   29.406720]  sda: sda1 sda2
Sep 16 08:56:08 ubuntu kernel: [   29.428343] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 16 08:56:08 ubuntu kernel: [   29.436334] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 16 08:56:08 ubuntu kernel: [   29.438308] usb 3-2: USB disconnect, address 2
Sep 16 08:56:08 ubuntu kernel: [   29.517071] pata_sis 0000:00:02.5: version 0.5.2
Sep 16 08:56:08 ubuntu kernel: [   29.518127] scsi3 : pata_sis
Sep 16 08:56:08 ubuntu kernel: [   29.518890] scsi4 : pata_sis
Sep 16 08:56:08 ubuntu kernel: [   29.519637] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14
Sep 16 08:56:08 ubuntu kernel: [   29.519641] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15
Sep 16 08:56:08 ubuntu kernel: [   29.694061] ata4.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
Sep 16 08:56:08 ubuntu kernel: [   29.694067] ata4.00: 488397168 sectors, multi 16: LBA48 
Sep 16 08:56:08 ubuntu kernel: [   29.702562] ata4.00: configured for UDMA/100
Sep 16 08:56:08 ubuntu kernel: [   30.022507] ata5.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB05, max UDMA/33
Sep 16 08:56:08 ubuntu kernel: [   30.174067] usb 3-2: new full speed USB device using uhci_hcd and address 3
Sep 16 08:56:08 ubuntu kernel: [   30.194348] ata5.00: configured for UDMA/33
Sep 16 08:56:08 ubuntu kernel: [   30.194508] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
Sep 16 08:56:08 ubuntu kernel: [   30.194627] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Sep 16 08:56:08 ubuntu kernel: [   30.194647] sd 3:0:0:0: [sdb] Write Protect is off
Sep 16 08:56:08 ubuntu kernel: [   30.194651] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep 16 08:56:08 ubuntu kernel: [   30.194681] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 16 08:56:08 ubuntu kernel: [   30.194753] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Sep 16 08:56:08 ubuntu kernel: [   30.194770] sd 3:0:0:0: [sdb] Write Protect is off
Sep 16 08:56:08 ubuntu kernel: [   30.194774] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep 16 08:56:08 ubuntu kernel: [   30.194802] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 16 08:56:08 ubuntu kernel: [   30.194807]  sdb: sdb1 sdb2 < sdb5 sdb6 > sdb3 sdb4
Sep 16 08:56:08 ubuntu kernel: [   30.228351] sd 3:0:0:0: [sdb] Attached SCSI disk
Sep 16 08:56:08 ubuntu kernel: [   30.228409] sd 3:0:0:0: Attached scsi generic sg1 type 0
Sep 16 08:56:08 ubuntu kernel: [   30.229367] scsi 4:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB05 PQ: 0 ANSI: 5
Sep 16 08:56:08 ubuntu kernel: [   30.229476] scsi 4:0:0:0: Attached scsi generic sg2 type 5
Sep 16 08:56:08 ubuntu kernel: [   30.258102] Driver 'sr' needs updating - please use bus_type methods
Sep 16 08:56:08 ubuntu kernel: [   30.267042] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 16 08:56:08 ubuntu kernel: [   30.267050] Uniform CD-ROM driver Revision: 3.20
Sep 16 08:56:08 ubuntu kernel: [   30.267131] sr 4:0:0:0: Attached scsi CD-ROM sr0
Sep 16 08:56:08 ubuntu kernel: [   30.360170] usb 3-2: configuration #1 chosen from 1 choice
Sep 16 08:56:08 ubuntu kernel: [   30.833033] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
Sep 16 08:56:08 ubuntu kernel: [   30.835977] SGI XFS Quota Management subsystem
Sep 16 08:56:08 ubuntu kernel: [   30.850401] JFS: nTxBlock = 4027, nTxLock = 32223
Sep 16 08:56:08 ubuntu kernel: [   32.909496] loop: module loaded
Sep 16 08:56:08 ubuntu kernel: [   33.011504] ISO 9660 Extensions: Microsoft Joliet Level 3
Sep 16 08:56:08 ubuntu kernel: [   33.016539] ISO 9660 Extensions: RRIP_1991A
Sep 16 08:56:08 ubuntu kernel: [   33.031856] Registering unionfs 1.4
Sep 16 08:56:08 ubuntu kernel: [   33.031861] unionfs: debugging is not enabled
Sep 16 08:56:08 ubuntu kernel: [   33.075385] squashfs: version 3.3 (2007/10/31) Phillip Lougher
Sep 16 08:56:08 ubuntu kernel: [   61.412045] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 16 08:56:08 ubuntu kernel: [   61.488823] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 16 08:56:08 ubuntu kernel: [   61.551982] Linux agpgart interface v0.102
Sep 16 08:56:08 ubuntu kernel: [   61.818081] agpgart: Detected SiS chipset - id:1605
Sep 16 08:56:08 ubuntu kernel: [   61.823147] agpgart: AGP aperture is 64M @ 0xe0000000
Sep 16 08:56:08 ubuntu kernel: [   61.950814] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1080
Sep 16 08:56:08 ubuntu kernel: [   62.471998] input: Power Button (FF) as /devices/virtual/input/input2
Sep 16 08:56:08 ubuntu kernel: [   62.491571] ACPI: Power Button (FF) [PWRF]
Sep 16 08:56:08 ubuntu kernel: [   62.491762] input: Power Button (CM) as /devices/virtual/input/input3
Sep 16 08:56:08 ubuntu kernel: [   62.503787] ACPI: Power Button (CM) [PWRB]
Sep 16 08:56:08 ubuntu kernel: [   62.503958] input: Sleep Button (CM) as /devices/virtual/input/input4
Sep 16 08:56:08 ubuntu kernel: [   62.519766] ACPI: Sleep Button (CM) [FUTS]
Sep 16 08:56:08 ubuntu kernel: [   63.229911] input: PC Speaker as /devices/platform/pcspkr/input/input5
Sep 16 08:56:08 ubuntu kernel: [   64.099064] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Sep 16 08:56:08 ubuntu kernel: [   64.867111] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
Sep 16 08:56:08 ubuntu kernel: [   65.187238] intel8x0_measure_ac97_clock: measured 55119 usecs
Sep 16 08:56:08 ubuntu kernel: [   65.187244] intel8x0: clocking to 48000
Sep 16 08:56:08 ubuntu kernel: [   69.171951] device-mapper: uevent: version 1.0.3
Sep 16 08:56:08 ubuntu kernel: [   69.171995] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Sep 16 08:56:08 ubuntu kernel: [   70.110142] Adding 851404k swap on /dev/sdb6.  Priority:-1 extents:1 across:851404k
Sep 16 08:56:08 ubuntu kernel: [   70.304521] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 16 08:56:08 ubuntu kernel: [   72.713069] No dock devices found.
Sep 16 08:56:08 ubuntu NetworkManager: <info>  starting... 
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: Found user 'avahi' (UID 107) and group 'avahi' (GID 116).
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: Successfully dropped root privileges.
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: avahi-daemon 0.6.22 starting up.
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: Successfully called chroot().
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: Successfully dropped remaining capabilities.
Sep 16 08:56:08 ubuntu avahi-daemon[7893]: chroot.c: open() failed: No such file or directory
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: Failed to open /etc/resolv.conf: Invalid argument
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: No service file found in /etc/avahi/services.
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: Network interface enumeration completed.
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: Registering HINFO record with values 'I686'/'LINUX'.
Sep 16 08:56:08 ubuntu avahi-daemon[7892]: Server startup complete. Host name is ubuntu.local. Local service cookie is 1896117854.
Sep 16 08:56:08 ubuntu kernel: [   74.520718] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Sep 16 08:56:08 ubuntu kernel: [   74.520727] apm: overridden by ACPI.
Sep 16 08:56:08 ubuntu kernel: [   74.664506] lp: driver loaded but no devices found
Sep 16 08:56:08 ubuntu kernel: [   74.713921] ppdev: user-space parallel port driver
Sep 16 08:56:09 ubuntu python: Writing graphics card hardware list to /var/lib/guidance/guidance-gfxhardware-snapshot
Sep 16 08:56:09 ubuntu dhcdbd: Started up.
Sep 16 08:56:11 ubuntu kernel: [   77.185301] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep 16 08:56:11 ubuntu NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
Sep 16 08:56:11 ubuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep 16 08:56:11 ubuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep 16 08:56:11 ubuntu NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Sep 16 08:56:11 ubuntu NetworkManager: <info>  Deactivating device eth0. 
Sep 16 08:56:11 ubuntu NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Sep 16 08:56:11 ubuntu NetworkManager: <debug> [1221555371.357082] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'). 
Sep 16 08:56:11 ubuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Sep 16 08:56:11 ubuntu hcid[8199]: Bluetooth HCI daemon
Sep 16 08:56:11 ubuntu kernel: [   77.378049] Bluetooth: Core ver 2.11
Sep 16 08:56:11 ubuntu kernel: [   77.379013] NET: Registered protocol family 31
Sep 16 08:56:11 ubuntu kernel: [   77.379020] Bluetooth: HCI device and connection manager initialized
Sep 16 08:56:11 ubuntu kernel: [   77.379025] Bluetooth: HCI socket layer initialized
Sep 16 08:56:11 ubuntu hcid[8199]: Starting SDP server
Sep 16 08:56:11 ubuntu kernel: [   77.434510] Bluetooth: L2CAP ver 2.9
Sep 16 08:56:11 ubuntu kernel: [   77.434518] Bluetooth: L2CAP socket layer initialized
Sep 16 08:56:11 ubuntu hcid[8199]: Created local server at unix:abstract=/var/run/dbus-Kx33vLzco8,guid=c0a3e43280e800397ad809b848cf74ab
Sep 16 08:56:11 ubuntu audio[8215]: Bluetooth Audio daemon
Sep 16 08:56:11 ubuntu audio[8215]: Unix socket created: 5
Sep 16 08:56:11 ubuntu audio[8215]: audio.conf: Key file does not have key 'Enable'
Sep 16 08:56:11 ubuntu audio[8215]: audio.conf: Key file does not have key 'Disable'
Sep 16 08:56:11 ubuntu input[8218]: Bluetooth Input daemon
Sep 16 08:56:11 ubuntu input[8218]: Registered input manager path:/org/bluez/input
Sep 16 08:56:11 ubuntu kernel: [   77.505409] Bluetooth: RFCOMM socket layer initialized
Sep 16 08:56:11 ubuntu kernel: [   77.505731] Bluetooth: RFCOMM TTY layer initialized
Sep 16 08:56:11 ubuntu kernel: [   77.505737] Bluetooth: RFCOMM ver 1.8
Sep 16 08:56:11 ubuntu audio[8215]: add_service_record: got record id 0x10000
Sep 16 08:56:11 ubuntu audio[8215]: audio.conf: Key file does not have key 'Disable'
Sep 16 08:56:11 ubuntu audio[8215]: audio.conf: Key file does not have group 'A2DP'
Sep 16 08:56:11 ubuntu last message repeated 3 times
Sep 16 08:56:11 ubuntu audio[8215]: SEP 0x806d248 registered: type:0 codec:0 seid:1
Sep 16 08:56:11 ubuntu audio[8215]: add_service_record: got record id 0x10001
Sep 16 08:56:11 ubuntu audio[8215]: add_service_record: got record id 0x10002
Sep 16 08:56:11 ubuntu audio[8215]: add_service_record: got record id 0x10003
Sep 16 08:56:11 ubuntu audio[8215]: Registered manager path:/org/bluez/audio
Sep 16 08:56:12 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Will activate connection 'eth0'. 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Device eth0 activation scheduled... 
Sep 16 08:56:12 ubuntu NetworkManager: <debug> [1221555372.367126] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) started... 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Sep 16 08:56:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Sep 16 08:56:13 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Sep 16 08:56:13 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Sep 16 08:56:13 ubuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Sep 16 08:56:13 ubuntu kernel: [   79.414766] NET: Registered protocol family 10
Sep 16 08:56:13 ubuntu kernel: [   79.415440] lo: Disabled Privacy Extensions
Sep 16 08:56:14 ubuntu ubiquity[8324]: Ubiquity 1.8.12
Sep 16 08:56:14 ubuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Sep 16 08:56:14 ubuntu kernel: [   80.634902] NET: Registered protocol family 17
Sep 16 08:56:14 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Sep 16 08:56:14 ubuntu dhclient: DHCPOFFER of 192.168.1.2 from 192.168.1.1
Sep 16 08:56:14 ubuntu dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Sep 16 08:56:15 ubuntu avahi-daemon[7892]: Registering new address record for fe80::21d:fff:fec0:791f on eth0.*.
Sep 16 08:56:20 ubuntu dhclient: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
Sep 16 08:56:20 ubuntu dhclient: DHCPACK of 192.168.1.2 from 192.168.1.1
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: New relevant interface eth0.IPv4 for mDNS.
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Sep 16 08:56:20 ubuntu NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Sep 16 08:56:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Sep 16 08:56:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Sep 16 08:56:20 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Sep 16 08:56:20 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep 16 08:56:20 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep 16 08:56:20 ubuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Sep 16 08:56:20 ubuntu NetworkManager: <info>    address 192.168.1.2 
Sep 16 08:56:20 ubuntu NetworkManager: <info>    netmask 255.255.255.0 
Sep 16 08:56:20 ubuntu NetworkManager: <info>    broadcast 192.168.1.255 
Sep 16 08:56:20 ubuntu NetworkManager: <info>    gateway 192.168.1.1 
Sep 16 08:56:20 ubuntu NetworkManager: <info>    nameserver 192.168.1.1 
Sep 16 08:56:20 ubuntu NetworkManager: <info>    domain name 'siemens' 
Sep 16 08:56:20 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Sep 16 08:56:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Sep 16 08:56:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Sep 16 08:56:20 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Sep 16 08:56:20 ubuntu dhclient: bound to 192.168.1.2 -- renewal in 32477 seconds.
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: Withdrawing address record for 192.168.1.2 on eth0.
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: Withdrawing address record for fe80::21d:fff:fec0:791f on eth0.
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.2.
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: New relevant interface eth0.IPv4 for mDNS.
Sep 16 08:56:20 ubuntu avahi-daemon[7892]: Registering new address record for 192.168.1.2 on eth0.IPv4.
Sep 16 08:56:21 ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
Sep 16 08:56:21 ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Sep 16 08:56:21 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated. 
Sep 16 08:56:21 ubuntu NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Sep 16 08:56:21 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Sep 16 08:56:22 ubuntu ntpdate[8407]: step time server 91.189.94.4 offset -10799.092459 sec
Sep 16 05:56:23 ubuntu avahi-daemon[7892]: Registering new address record for fe80::21d:fff:fec0:791f on eth0.*.
Sep 16 05:56:23 ubuntu ubiquity[8324]: log-output -t ubiquity laptop-detect
Sep 16 05:56:24 ubuntu ubiquity[8324]: log-output -t ubiquity fontconfig-voodoo --auto --force --quiet
Sep 16 05:56:27 ubuntu ubiquity: object not accessible
Sep 16 05:56:27 ubuntu ubiquity[8324]: log-output -t ubiquity dcop kded kded unloadModule medianotifier
Sep 16 05:56:27 ubuntu ubiquity[8324]: switched to page stepLanguage
Sep 16 05:56:28 ubuntu localechooser: info: Locale has been preseeded to el_GR.UTF-8
Sep 16 05:56:28 ubuntu localechooser: info: Set languagechooser/language-name = 'Greek'
Sep 16 05:56:28 ubuntu localechooser: info: Set countrychooser/shortlist-el = 'GR'
Sep 16 05:56:28 ubuntu localechooser: info: Set debian-installer/locale = 'el_GR.UTF-8'
Sep 16 05:56:28 ubuntu localechooser: info: LANGNAME=Greek
Sep 16 05:56:28 ubuntu localechooser: info: line=Greek;2;el;GR;el_GR.UTF-8;UTF-8;;console-setup
Sep 16 05:56:28 ubuntu localechooser: info: Set debian-installer/language = 'el'
Sep 16 05:56:28 ubuntu localechooser: info: Set debian-installer/locale = 'el_GR.UTF-8'
Sep 16 05:56:28 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'el_GR.UTF-8'
Sep 16 05:56:28 ubuntu localechooser: info: Set debian-installer/country = 'GR'
Sep 16 05:56:28 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Sep 16 05:56:28 ubuntu localechooser: info: Set debconf/language = 'el'
Sep 16 05:56:28 ubuntu localechooser: info: Set debian-installer/country = 'GR'
Sep 16 05:56:28 ubuntu localechooser: info: Set debian-installer/locale = 'el_GR.UTF-8'
Sep 16 05:56:28 ubuntu ubiquity[8324]: debconffilter_done: Language (current: Language)
Sep 16 05:56:28 ubuntu ubiquity[8324]: Step_before = stepLanguage
Sep 16 05:56:31 ubuntu ubiquity[8324]: switched to page stepLocation
Sep 16 05:56:32 ubuntu kernel: [   97.244964] eth0: no IPv6 routers present
Sep 16 05:56:37 ubuntu localechooser: info: Locale has been preseeded to el_GR.UTF-8
Sep 16 05:56:37 ubuntu localechooser: info: Set languagechooser/language-name-fb = 'Greek'
Sep 16 05:56:37 ubuntu localechooser: info: Set countrychooser/shortlist-el = 'GR'
Sep 16 05:56:37 ubuntu localechooser: info: Set debian-installer/locale = 'el_GR.UTF-8'
Sep 16 05:56:37 ubuntu localechooser: info: Set debconf/language = ''
Sep 16 05:56:37 ubuntu localechooser: info: Set countrychooser/country-name = 'Greece'
Sep 16 05:56:37 ubuntu localechooser: info: Set debian-installer/country = 'GR'
Sep 16 05:56:37 ubuntu localechooser: info: Set debian-installer/locale = 'el_GR.UTF-8'
Sep 16 05:56:37 ubuntu ubiquity[8324]: debconffilter_done: Timezone (current: Timezone)
Sep 16 05:56:37 ubuntu ubiquity[8324]: Step_before = stepLocation
Sep 16 05:56:38 ubuntu ubiquity[8324]: log-output -t ubiquity setxkbmap -model pc105 -layout us
Sep 16 05:56:39 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Sep 16 05:56:39 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Sep 16 05:56:39 ubuntu ubiquity[8324]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Sep 16 05:56:39 ubuntu ubiquity[8324]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
Sep 16 05:56:39 ubuntu ubiquity[8324]: Step_before = stepLocation
Sep 16 05:56:41 ubuntu kernel: [  106.047265] end_request: I/O error, dev fd0, sector 0
Sep 16 05:56:41 ubuntu kernel: [  106.071258] end_request: I/O error, dev fd0, sector 0
Sep 16 05:56:52 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:56:52 ubuntu ntfsresize: Device name        : /dev/sda2
Sep 16 05:56:52 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:56:52 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:56:52 ubuntu ntfsresize: Current volume size: 499899613696 bytes (499900 MB)
Sep 16 05:56:52 ubuntu ntfsresize: Current device size: 499899617280 bytes (499900 MB)
Sep 16 05:56:52 ubuntu ntfsresize: ERROR: This software has detected that the disk has at least 3 bad sectors.
Sep 16 05:56:52 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:56:52 ubuntu ntfsresize: * WARNING: The disk has bad sector. This means physical damage on the disk *
Sep 16 05:56:52 ubuntu ntfsresize: * surface caused by deterioration, manufacturing faults or other reason.   *
Sep 16 05:56:52 ubuntu ntfsresize: * The reliability of the disk may stay stable or degrade fast. We suggest  *
Sep 16 05:56:52 ubuntu ntfsresize: * making a full backup urgently by running 'ntfsclone --rescue ...' then   *
Sep 16 05:56:52 ubuntu ntfsresize: * run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
Sep 16 05:56:52 ubuntu ntfsresize: * NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
Sep 16 05:56:52 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:56:52 ubuntu partman: Error running 'ntfsresize --info'
Sep 16 05:56:57 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:56:57 ubuntu ntfsresize: Device name        : /dev/sdb1
Sep 16 05:56:57 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:56:57 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:56:57 ubuntu ntfsresize: Current volume size: 145793053184 bytes (145794 MB)
Sep 16 05:56:57 ubuntu ntfsresize: Current device size: 145793055744 bytes (145794 MB)
Sep 16 05:56:57 ubuntu ntfsresize: Checking filesystem consistency ...
Sep 16 05:56:57 ubuntu ntfsresize: Accounting clusters ...
Sep 16 05:56:57 ubuntu ntfsresize: Space in use       : 101771 MB (69,8%)
Sep 16 05:56:57 ubuntu ntfsresize: Collecting resizing constraints ...
Sep 16 05:56:57 ubuntu ntfsresize: You might resize at 101770080256 bytes or 101771 MB (freeing 44023 MB).
Sep 16 05:56:57 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep 16 05:56:58 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:56:58 ubuntu ntfsresize: Device name        : /dev/sdb5
Sep 16 05:56:58 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:56:58 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:56:58 ubuntu ntfsresize: Current volume size: 20892176896 bytes (20893 MB)
Sep 16 05:56:58 ubuntu ntfsresize: Current device size: 20892178944 bytes (20893 MB)
Sep 16 05:56:58 ubuntu ntfsresize: Checking filesystem consistency ...
Sep 16 05:56:58 ubuntu ntfsresize: Accounting clusters ...
Sep 16 05:56:58 ubuntu ntfsresize: Space in use       : 6881 MB (32,9%)
Sep 16 05:56:58 ubuntu ntfsresize: Collecting resizing constraints ...
Sep 16 05:56:58 ubuntu ntfsresize: You might resize at 6880018432 bytes or 6881 MB (freeing 14012 MB).
Sep 16 05:56:58 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep 16 05:57:00 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:57:00 ubuntu ntfsresize: Device name        : /dev/sda2
Sep 16 05:57:00 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:57:00 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:57:00 ubuntu ntfsresize: Current volume size: 499899613696 bytes (499900 MB)
Sep 16 05:57:00 ubuntu ntfsresize: Current device size: 499899617280 bytes (499900 MB)
Sep 16 05:57:00 ubuntu ntfsresize: ERROR: This software has detected that the disk has at least 3 bad sectors.
Sep 16 05:57:00 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:57:00 ubuntu ntfsresize: * WARNING: The disk has bad sector. This means physical damage on the disk *
Sep 16 05:57:00 ubuntu ntfsresize: * surface caused by deterioration, manufacturing faults or other reason.   *
Sep 16 05:57:00 ubuntu ntfsresize: * The reliability of the disk may stay stable or degrade fast. We suggest  *
Sep 16 05:57:00 ubuntu ntfsresize: * making a full backup urgently by running 'ntfsclone --rescue ...' then   *
Sep 16 05:57:00 ubuntu ntfsresize: * run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
Sep 16 05:57:00 ubuntu ntfsresize: * NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
Sep 16 05:57:00 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:57:00 ubuntu partman: Error running 'ntfsresize --info'
Sep 16 05:57:01 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:57:01 ubuntu ntfsresize: Device name        : /dev/sda2
Sep 16 05:57:01 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:57:01 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:57:01 ubuntu ntfsresize: Current volume size: 499899613696 bytes (499900 MB)
Sep 16 05:57:01 ubuntu ntfsresize: Current device size: 499899617280 bytes (499900 MB)
Sep 16 05:57:01 ubuntu ntfsresize: ERROR: This software has detected that the disk has at least 3 bad sectors.
Sep 16 05:57:01 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:57:01 ubuntu ntfsresize: * WARNING: The disk has bad sector. This means physical damage on the disk *
Sep 16 05:57:01 ubuntu ntfsresize: * surface caused by deterioration, manufacturing faults or other reason.   *
Sep 16 05:57:01 ubuntu ntfsresize: * The reliability of the disk may stay stable or degrade fast. We suggest  *
Sep 16 05:57:01 ubuntu ntfsresize: * making a full backup urgently by running 'ntfsclone --rescue ...' then   *
Sep 16 05:57:01 ubuntu ntfsresize: * run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
Sep 16 05:57:01 ubuntu ntfsresize: * NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
Sep 16 05:57:01 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:57:01 ubuntu partman: Error running 'ntfsresize --info'
Sep 16 05:57:03 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:57:03 ubuntu ntfsresize: Device name        : /dev/sdb1
Sep 16 05:57:03 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:57:03 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:57:03 ubuntu ntfsresize: Current volume size: 145793053184 bytes (145794 MB)
Sep 16 05:57:03 ubuntu ntfsresize: Current device size: 145793055744 bytes (145794 MB)
Sep 16 05:57:03 ubuntu ntfsresize: Checking filesystem consistency ...
Sep 16 05:57:03 ubuntu ntfsresize: Accounting clusters ...
Sep 16 05:57:03 ubuntu ntfsresize: Space in use       : 101771 MB (69,8%)
Sep 16 05:57:03 ubuntu ntfsresize: Collecting resizing constraints ...
Sep 16 05:57:03 ubuntu ntfsresize: You might resize at 101770080256 bytes or 101771 MB (freeing 44023 MB).
Sep 16 05:57:03 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep 16 05:57:04 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:57:04 ubuntu ntfsresize: Device name        : /dev/sdb5
Sep 16 05:57:04 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:57:04 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:57:04 ubuntu ntfsresize: Current volume size: 20892176896 bytes (20893 MB)
Sep 16 05:57:04 ubuntu ntfsresize: Current device size: 20892178944 bytes (20893 MB)
Sep 16 05:57:04 ubuntu ntfsresize: Checking filesystem consistency ...
Sep 16 05:57:04 ubuntu ntfsresize: Accounting clusters ...
Sep 16 05:57:04 ubuntu ntfsresize: Space in use       : 6881 MB (32,9%)
Sep 16 05:57:04 ubuntu ntfsresize: Collecting resizing constraints ...
Sep 16 05:57:04 ubuntu ntfsresize: You might resize at 6880018432 bytes or 6881 MB (freeing 14012 MB).
Sep 16 05:57:04 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep 16 05:57:05 ubuntu ubiquity[8324]: debconffilter_done: Partman (current: Partman)
Sep 16 05:57:05 ubuntu ubiquity[8324]: dbfilter_handle_status: ('Partman', 10)
Sep 16 05:58:31 ubuntu ubiquity[8324]: dbfilter_handle_status: answer 524288
Sep 16 05:58:33 ubuntu kernel: [  217.949417] end_request: I/O error, dev fd0, sector 0
Sep 16 05:58:33 ubuntu kernel: [  217.973411] end_request: I/O error, dev fd0, sector 0
Sep 16 05:58:43 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:58:43 ubuntu ntfsresize: Device name        : /dev/sda2
Sep 16 05:58:43 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:58:43 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:58:43 ubuntu ntfsresize: Current volume size: 499899613696 bytes (499900 MB)
Sep 16 05:58:43 ubuntu ntfsresize: Current device size: 499899617280 bytes (499900 MB)
Sep 16 05:58:43 ubuntu ntfsresize: ERROR: This software has detected that the disk has at least 3 bad sectors.
Sep 16 05:58:43 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:58:43 ubuntu ntfsresize: * WARNING: The disk has bad sector. This means physical damage on the disk *
Sep 16 05:58:43 ubuntu ntfsresize: * surface caused by deterioration, manufacturing faults or other reason.   *
Sep 16 05:58:43 ubuntu ntfsresize: * The reliability of the disk may stay stable or degrade fast. We suggest  *
Sep 16 05:58:43 ubuntu ntfsresize: * making a full backup urgently by running 'ntfsclone --rescue ...' then   *
Sep 16 05:58:43 ubuntu ntfsresize: * run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
Sep 16 05:58:43 ubuntu ntfsresize: * NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
Sep 16 05:58:43 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:58:43 ubuntu partman: Error running 'ntfsresize --info'
Sep 16 05:58:46 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:58:46 ubuntu ntfsresize: Device name        : /dev/sdb1
Sep 16 05:58:46 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:58:46 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:58:46 ubuntu ntfsresize: Current volume size: 145793053184 bytes (145794 MB)
Sep 16 05:58:46 ubuntu ntfsresize: Current device size: 145793055744 bytes (145794 MB)
Sep 16 05:58:46 ubuntu ntfsresize: Checking filesystem consistency ...
Sep 16 05:58:46 ubuntu ntfsresize: Accounting clusters ...
Sep 16 05:58:46 ubuntu ntfsresize: Space in use       : 101771 MB (69,8%)
Sep 16 05:58:46 ubuntu ntfsresize: Collecting resizing constraints ...
Sep 16 05:58:46 ubuntu ntfsresize: You might resize at 101770080256 bytes or 101771 MB (freeing 44023 MB).
Sep 16 05:58:46 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep 16 05:58:47 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:58:47 ubuntu ntfsresize: Device name        : /dev/sdb5
Sep 16 05:58:47 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:58:47 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:58:47 ubuntu ntfsresize: Current volume size: 20892176896 bytes (20893 MB)
Sep 16 05:58:47 ubuntu ntfsresize: Current device size: 20892178944 bytes (20893 MB)
Sep 16 05:58:47 ubuntu ntfsresize: Checking filesystem consistency ...
Sep 16 05:58:47 ubuntu ntfsresize: Accounting clusters ...
Sep 16 05:58:47 ubuntu ntfsresize: Space in use       : 6881 MB (32,9%)
Sep 16 05:58:47 ubuntu ntfsresize: Collecting resizing constraints ...
Sep 16 05:58:47 ubuntu ntfsresize: You might resize at 6880018432 bytes or 6881 MB (freeing 14012 MB).
Sep 16 05:58:47 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep 16 05:58:48 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:58:48 ubuntu ntfsresize: Device name        : /dev/sda2
Sep 16 05:58:48 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:58:48 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:58:48 ubuntu ntfsresize: Current volume size: 499899613696 bytes (499900 MB)
Sep 16 05:58:48 ubuntu ntfsresize: Current device size: 499899617280 bytes (499900 MB)
Sep 16 05:58:48 ubuntu ntfsresize: ERROR: This software has detected that the disk has at least 3 bad sectors.
Sep 16 05:58:48 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:58:48 ubuntu ntfsresize: * WARNING: The disk has bad sector. This means physical damage on the disk *
Sep 16 05:58:48 ubuntu ntfsresize: * surface caused by deterioration, manufacturing faults or other reason.   *
Sep 16 05:58:48 ubuntu ntfsresize: * The reliability of the disk may stay stable or degrade fast. We suggest  *
Sep 16 05:58:48 ubuntu ntfsresize: * making a full backup urgently by running 'ntfsclone --rescue ...' then   *
Sep 16 05:58:48 ubuntu ntfsresize: * run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
Sep 16 05:58:48 ubuntu ntfsresize: * NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
Sep 16 05:58:48 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:58:48 ubuntu partman: Error running 'ntfsresize --info'
Sep 16 05:58:50 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:58:50 ubuntu ntfsresize: Device name        : /dev/sda2
Sep 16 05:58:50 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:58:50 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:58:50 ubuntu ntfsresize: Current volume size: 499899613696 bytes (499900 MB)
Sep 16 05:58:50 ubuntu ntfsresize: Current device size: 499899617280 bytes (499900 MB)
Sep 16 05:58:50 ubuntu ntfsresize: ERROR: This software has detected that the disk has at least 3 bad sectors.
Sep 16 05:58:50 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:58:50 ubuntu ntfsresize: * WARNING: The disk has bad sector. This means physical damage on the disk *
Sep 16 05:58:50 ubuntu ntfsresize: * surface caused by deterioration, manufacturing faults or other reason.   *
Sep 16 05:58:50 ubuntu ntfsresize: * The reliability of the disk may stay stable or degrade fast. We suggest  *
Sep 16 05:58:50 ubuntu ntfsresize: * making a full backup urgently by running 'ntfsclone --rescue ...' then   *
Sep 16 05:58:50 ubuntu ntfsresize: * run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
Sep 16 05:58:50 ubuntu ntfsresize: * NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
Sep 16 05:58:50 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:58:50 ubuntu partman: Error running 'ntfsresize --info'
Sep 16 05:58:52 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:58:52 ubuntu ntfsresize: Device name        : /dev/sdb1
Sep 16 05:58:52 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:58:52 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:58:52 ubuntu ntfsresize: Current volume size: 145793053184 bytes (145794 MB)
Sep 16 05:58:52 ubuntu ntfsresize: Current device size: 145793055744 bytes (145794 MB)
Sep 16 05:58:52 ubuntu ntfsresize: Checking filesystem consistency ...
Sep 16 05:58:52 ubuntu ntfsresize: Accounting clusters ...
Sep 16 05:58:52 ubuntu ntfsresize: Space in use       : 101771 MB (69,8%)
Sep 16 05:58:52 ubuntu ntfsresize: Collecting resizing constraints ...
Sep 16 05:58:52 ubuntu ntfsresize: You might resize at 101770080256 bytes or 101771 MB (freeing 44023 MB).
Sep 16 05:58:52 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep 16 05:58:53 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:58:53 ubuntu ntfsresize: Device name        : /dev/sdb5
Sep 16 05:58:53 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:58:53 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:58:53 ubuntu ntfsresize: Current volume size: 20892176896 bytes (20893 MB)
Sep 16 05:58:53 ubuntu ntfsresize: Current device size: 20892178944 bytes (20893 MB)
Sep 16 05:58:53 ubuntu ntfsresize: Checking filesystem consistency ...
Sep 16 05:58:53 ubuntu ntfsresize: Accounting clusters ...
Sep 16 05:58:53 ubuntu ntfsresize: Space in use       : 6881 MB (32,9%)
Sep 16 05:58:53 ubuntu ntfsresize: Collecting resizing constraints ...
Sep 16 05:58:53 ubuntu ntfsresize: You might resize at 6880018432 bytes or 6881 MB (freeing 14012 MB).
Sep 16 05:58:53 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Sep 16 05:58:53 ubuntu ubiquity[8324]: debconffilter_done: Partman (current: Partman)
Sep 16 05:58:53 ubuntu ubiquity[8324]: dbfilter_handle_status: ('Partman', 10)
Sep 16 05:58:58 ubuntu ubiquity[8324]: dbfilter_handle_status: answer 2097152
Sep 16 05:58:58 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep 16 05:58:58 ubuntu ubiquity[8324]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Sep 16 05:58:59 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep 16 05:58:59 ubuntu ubiquity[8324]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^xserver-xorg/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Sep 16 05:58:59 ubuntu ubiquity: object not accessible
Sep 16 05:58:59 ubuntu ubiquity[8324]: log-output -t ubiquity dcop kded kded loadModule medianotifier
Sep 16 05:58:59 ubuntu kdm[10661]: StartServerSucces
Sep 16 05:59:00 ubuntu /usr/sbin/cron[10702]: (CRON) INFO (pidfile fd = 3)
Sep 16 05:59:00 ubuntu /usr/sbin/cron[10703]: (CRON) STARTUP (fork ok)
Sep 16 05:59:00 ubuntu /usr/sbin/cron[10703]: (CRON) INFO (Running @reboot jobs)
Sep 16 05:59:27 ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
Sep 16 05:59:27 ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks. 
Sep 16 06:00:20 ubuntu hald: mounted /dev/sda1 on behalf of uid 999
```

---

### Post by ago on 2008-09-16
Sep 16 05:58:48 ubuntu partman: Error running 'ntfsresize --info'
Sep 16 05:58:50 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Sep 16 05:58:50 ubuntu ntfsresize: Device name        : /dev/sda2
Sep 16 05:58:50 ubuntu ntfsresize: NTFS volume version: 3.1
Sep 16 05:58:50 ubuntu ntfsresize: Cluster size       : 4096 bytes
Sep 16 05:58:50 ubuntu ntfsresize: Current volume size: 499899613696 bytes (499900 MB)
Sep 16 05:58:50 ubuntu ntfsresize: Current device size: 499899617280 bytes (499900 MB)
Sep 16 05:58:50 ubuntu ntfsresize: ERROR: This software has detected that the disk has at least 3 bad sectors.
Sep 16 05:58:50 ubuntu ntfsresize: ****************************************************************************
Sep 16 05:58:50 ubuntu ntfsresize: * WARNING: The disk has bad sector. This means physical damage on the disk *
Sep 16 05:58:50 ubuntu ntfsresize: * surface caused by deterioration, manufacturing faults or other reason.   *
Sep 16 05:58:50 ubuntu ntfsresize: * The reliability of the disk may stay stable or degrade fast. We suggest  *
Sep 16 05:58:50 ubuntu ntfsresize: * making a full backup urgently by running 'ntfsclone --rescue ...' then   *
Sep 16 05:58:50 ubuntu ntfsresize: * run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
Sep 16 05:58:50 ubuntu ntfsresize: * NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
Sep 16 05:58:50 ubuntu ntfsresize: ****************************************************************************

---

### Post by Elf Wizard on 2008-09-16
[COLOR=Navy]**THANKS **ago**!!! **:D

Seems like my main disk is ready to pass away. CHKDSK not found any errors or problematic sectors, but SMART monitoring programs are reporting that its in a prefailure state, with latency at read-write operations.[/COLOR]

[COLOR=Navy]I'll install Wubi again, at my new disk arrival.[/COLOR]

---

