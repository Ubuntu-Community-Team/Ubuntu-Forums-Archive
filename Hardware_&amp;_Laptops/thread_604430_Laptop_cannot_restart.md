---
title: "Laptop cannot restart"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by guttdude on 2007-11-06
I use ubuntu 7.10 gusty on my laptop twinhead d212a.
CPU is AMD XP-M (LV) 1600+ on VIA P/KN266 VT8633.
I can shut down my laptop but I cannot restart.
When I try to restart my laptop, I stall at the blank screen with lcd backlight opened and cannot do any keyboard.

Help me please.

---

### Post by guttdude on 2007-11-10
No one :( ... Can any log file help?

---

### Post by SpiritIsReality on 2007-11-10
howdy
You can shut down. Then you can start, and all ok?
I mean if you click on shutdown button, the computer shuts off. Then can you power it on and it starts,? or no.
But you can not restart?
I mean if you click the restart button on the screen, it will not restart?
trails

---

### Post by SpiritIsReality on 2007-11-10
howdy
There is also a /var/log/messages that might help.
[http://www.google.ca/search?hl=en&q=...G=Search&meta=](http://www.google.ca/search?hl=en&q=...G=Search&meta=)
[http://www.ibm.com/developerworks/li...ry/l-roadmap5/](http://www.ibm.com/developerworks/li...ry/l-roadmap5/)
trails

---

### Post by SpiritIsReality on 2007-11-10
howdy
You could try a knoppix live cd and if your laptop will run, you could check your error messages in /var/log/messages of your ubuntu partition.
hope it helps
you could search your video card and your model of laptop to see if it could be a video problem after install.?
[http://www.google.ca/](http://www.google.ca/)
[http://www.google.ca/advanced_search?hl=en](http://www.google.ca/advanced_search?hl=en)
[http://www.google.ca/language_tools?hl=en](http://www.google.ca/language_tools?hl=en)
all the best
trails

---

### Post by biggyfred on 2007-11-10
What is on the screen? Is the splash screen up? Does anything ever come up? Does GRUB come up?

---

### Post by guttdude on 2007-11-11
I can Shut Down my laptop using the Shut Down button in quit menu. It ends all the process and then turns off my computer without problem. 

But when I press Restart button, it also ends all the process and then turn into blank screen without restart my machine. I have to press the power button for 5 sec and then press it again to turn on the computer.

Here is my /var/log/message for today
```

Nov 11 19:47:46 xp1600-term syslogd 1.4.1#21ubuntu3: restart.
Nov 11 19:47:46 xp1600-term kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov 11 19:47:46 xp1600-term kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov 11 19:47:46 xp1600-term kernel: Symbols match kernel version 2.6.22.
Nov 11 19:47:46 xp1600-term kernel: No module symbols loaded - kernel modules not enabled. 
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000025ff0000 (usable)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]  BIOS-e820: 0000000025ff0000 - 0000000025ff8000 (ACPI data)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]  BIOS-e820: 0000000025ff8000 - 0000000026000000 (ACPI NVS)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] 0MB HIGHMEM available.
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] 607MB LOWMEM available.
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] Zone PFN ranges:
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]   DMA             0 ->     4096
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]   Normal       4096 ->   155632
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]   HighMem    155632 ->   155632
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov 11 19:47:46 xp1600-term kernel: [    0.000000]     0:        0 ->   155632
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] DMI 2.3 present.
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FB600 checksum 0
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] ACPI: RSDP 000FB600, 0014 (r0 AMI   )
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] ACPI: RSDT 25FF0000, 0028 (r1 AMIINT VIA_K7         10 MSFT       97)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] ACPI: FACP 25FF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] ACPI: DSDT 25FF00C0, 418F (r1    VIA   VIA_K7     1000 MSFT  100000D)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] ACPI: FACS 25FF8000, 0040
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 26000000:d9f80000)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] Built 1 zonelists.  Total pages: 154417
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] Kernel command line: root=UUID=06c3148e-4578-4546-80a6-3c7a880638af ro quiet splash nolapic noacpi noapm pci=routeirq
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] Initializing CPU#0
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 11 19:47:46 xp1600-term kernel: [    0.000000] Detected 1393.209 MHz processor.
Nov 11 19:47:46 xp1600-term kernel: [   12.933062] Console: colour VGA+ 80x25
Nov 11 19:47:46 xp1600-term kernel: [   12.934719] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 11 19:47:46 xp1600-term kernel: [   12.937262] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 11 19:47:46 xp1600-term kernel: [   12.968453] Memory: 605196k/622528k available (2015k kernel code, 16756k reserved, 916k data, 364k init, 0k highmem)
Nov 11 19:47:46 xp1600-term kernel: [   12.968469] virtual kernel memory layout:
Nov 11 19:47:46 xp1600-term kernel: [   12.968471]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Nov 11 19:47:46 xp1600-term kernel: [   12.968473]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 11 19:47:46 xp1600-term kernel: [   12.968475]     vmalloc : 0xe6800000 - 0xff7fe000   ( 399 MB)
Nov 11 19:47:46 xp1600-term kernel: [   12.968476]     lowmem  : 0xc0000000 - 0xe5ff0000   ( 607 MB)
Nov 11 19:47:46 xp1600-term kernel: [   12.968478]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Nov 11 19:47:46 xp1600-term kernel: [   12.968480]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
Nov 11 19:47:46 xp1600-term kernel: [   12.968482]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
Nov 11 19:47:46 xp1600-term kernel: [   12.968487] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 11 19:47:46 xp1600-term kernel: [   12.968560] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Nov 11 19:47:46 xp1600-term kernel: [   13.048491] Calibrating delay using timer specific routine.. 2789.97 BogoMIPS (lpj=5579946)
Nov 11 19:47:46 xp1600-term kernel: [   13.048546] Security Framework v1.0.0 initialized
Nov 11 19:47:46 xp1600-term kernel: [   13.048559] SELinux:  Disabled at boot.
Nov 11 19:47:46 xp1600-term kernel: [   13.048585] Mount-cache hash table entries: 512
Nov 11 19:47:46 xp1600-term kernel: [   13.048849] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 11 19:47:46 xp1600-term kernel: [   13.048853] CPU: L2 Cache: 256K (64 bytes/line)
Nov 11 19:47:46 xp1600-term kernel: [   13.048875] Compat vDSO mapped to ffffe000.
Nov 11 19:47:46 xp1600-term kernel: [   13.048895] Checking 'hlt' instruction... OK.
Nov 11 19:47:46 xp1600-term kernel: [   13.064709] SMP alternatives: switching to UP code
Nov 11 19:47:46 xp1600-term kernel: [   13.065197] Freeing SMP alternatives: 11k freed
Nov 11 19:47:46 xp1600-term kernel: [   13.065854] Early unpacking initramfs... done
Nov 11 19:47:46 xp1600-term kernel: [   13.538883] ACPI: Core revision 20070126
Nov 11 19:47:46 xp1600-term kernel: [   13.539037] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 11 19:47:46 xp1600-term kernel: [   13.541162] ACPI: setting ELCR to 0200 (from 0c00)
Nov 11 19:47:46 xp1600-term kernel: [   13.556544] CPU0: AMD mobile AMD Athlon(tm) XP-M (LV) 1600+ stepping 01
Nov 11 19:47:46 xp1600-term kernel: [   13.556554] SMP motherboard not detected.
Nov 11 19:47:46 xp1600-term kernel: [   13.556559] Local APIC not detected. Using dummy APIC emulation.
Nov 11 19:47:46 xp1600-term kernel: [   13.556635] Brought up 1 CPUs
Nov 11 19:47:46 xp1600-term kernel: [   13.556873] Booting paravirtualized kernel on bare hardware
Nov 11 19:47:46 xp1600-term kernel: [   13.557005] Time: 19:47:15  Date: 10/11/107
Nov 11 19:47:46 xp1600-term kernel: [   13.557066] NET: Registered protocol family 16
Nov 11 19:47:46 xp1600-term kernel: [   13.557269] EISA bus registered
Nov 11 19:47:46 xp1600-term kernel: [   13.557294] ACPI: bus type pci registered
Nov 11 19:47:46 xp1600-term kernel: [   13.559177] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
Nov 11 19:47:46 xp1600-term kernel: [   13.559181] PCI: Using configuration type 1
Nov 11 19:47:46 xp1600-term kernel: [   13.559184] Setting up standard PCI resources
Nov 11 19:47:46 xp1600-term kernel: [   13.579582] ACPI: EC: GPE=0x04, ports=0x66, 0x62
Nov 11 19:47:46 xp1600-term kernel: [   13.582654] ACPI: Interpreter enabled
Nov 11 19:47:46 xp1600-term kernel: [   13.582659] ACPI: (supports S0 S3 S4 S5)
Nov 11 19:47:46 xp1600-term kernel: [   13.582681] ACPI: Using PIC for interrupt routing
Nov 11 19:47:46 xp1600-term kernel: [   13.587943] ACPI: EC: GPE=0x04, ports=0x66, 0x62
Nov 11 19:47:46 xp1600-term kernel: [   13.588017] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 11 19:47:46 xp1600-term kernel: [   13.588497] PCI quirk: region 0800-087f claimed by vt8235 PM
Nov 11 19:47:46 xp1600-term kernel: [   13.588502] PCI quirk: region 0400-040f claimed by vt8235 SMB
Nov 11 19:47:46 xp1600-term kernel: [   13.592135] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *11 14 15)
Nov 11 19:47:46 xp1600-term kernel: [   13.592260] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 5 9 14 15) *0, disabled.
Nov 11 19:47:46 xp1600-term kernel: [   13.592381] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 12)
Nov 11 19:47:46 xp1600-term kernel: [   13.592499] ACPI: PCI Interrupt Link [LNKD] (IRQs 6 7) *0, disabled.
Nov 11 19:47:46 xp1600-term kernel: [   13.592609] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 11 19:47:46 xp1600-term kernel: [   13.592646] pnp: PnP ACPI init
Nov 11 19:47:46 xp1600-term kernel: [   13.592662] ACPI: bus type pnp registered
Nov 11 19:47:46 xp1600-term kernel: [   13.594479] pnp: PnP ACPI: found 9 devices
Nov 11 19:47:46 xp1600-term kernel: [   13.594484] ACPI: ACPI bus type pnp unregistered
Nov 11 19:47:46 xp1600-term kernel: [   13.594492] PnPBIOS: Disabled by ACPI PNP
Nov 11 19:47:46 xp1600-term kernel: [   13.594598] PCI: Using ACPI for IRQ routing
Nov 11 19:47:46 xp1600-term kernel: [   13.594602] PCI: Routing PCI interrupts for all devices because "pci=routeirq" specified
Nov 11 19:47:46 xp1600-term kernel: [   13.594783] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
Nov 11 19:47:46 xp1600-term kernel: [   13.594796] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Nov 11 19:47:46 xp1600-term kernel: [   13.594948] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
Nov 11 19:47:46 xp1600-term kernel: [   13.594959] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Nov 11 19:47:46 xp1600-term kernel: [   13.594965] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Nov 11 19:47:46 xp1600-term kernel: [   13.594972] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Nov 11 19:47:46 xp1600-term kernel: [   13.594978] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Nov 11 19:47:46 xp1600-term kernel: [   13.594984] ACPI: Unable to derive IRQ for device 0000:00:11.1
Nov 11 19:47:46 xp1600-term kernel: [   13.594987] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
Nov 11 19:47:46 xp1600-term kernel: [   13.594991] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Nov 11 19:47:46 xp1600-term kernel: [   13.594997] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Nov 11 19:47:46 xp1600-term kernel: [   13.595143] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Nov 11 19:47:46 xp1600-term kernel: [   13.595153] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Nov 11 19:47:46 xp1600-term kernel: [   13.595297] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
Nov 11 19:47:46 xp1600-term kernel: [   13.595305] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
Nov 11 19:47:46 xp1600-term kernel: [   13.598095] NET: Registered protocol family 8
Nov 11 19:47:46 xp1600-term kernel: [   13.598099] NET: Registered protocol family 20
Nov 11 19:47:46 xp1600-term kernel: [   13.598253] pnp: 00:08: iomem range 0x0-0x9ffff could not be reserved
Nov 11 19:47:46 xp1600-term kernel: [   13.598258] pnp: 00:08: iomem range 0x0-0x0 could not be reserved
Nov 11 19:47:46 xp1600-term kernel: [   13.598262] pnp: 00:08: iomem range 0xf0000-0xfffff could not be reserved
Nov 11 19:47:46 xp1600-term kernel: [   13.598267] pnp: 00:08: iomem range 0x100000-0x27ffffff could not be reserved
Nov 11 19:47:46 xp1600-term kernel: [   13.599757] Time: tsc clocksource has been installed.
Nov 11 19:47:46 xp1600-term kernel: [   13.628751] PCI: Bridge: 0000:00:01.0
Nov 11 19:47:46 xp1600-term kernel: [   13.628753]   IO window: disabled.
Nov 11 19:47:46 xp1600-term kernel: [   13.628760]   MEM window: dfd00000-dfefffff
Nov 11 19:47:46 xp1600-term kernel: [   13.628765]   PREFETCH window: cfc00000-dfbfffff
Nov 11 19:47:46 xp1600-term kernel: [   13.628772] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
Nov 11 19:47:46 xp1600-term kernel: [   13.628775]   IO window: 00001000-000010ff
Nov 11 19:47:46 xp1600-term kernel: [   13.628780]   IO window: 00001400-000014ff
Nov 11 19:47:46 xp1600-term kernel: [   13.628786]   PREFETCH window: 30000000-33ffffff
Nov 11 19:47:46 xp1600-term kernel: [   13.628791]   MEM window: 34000000-37ffffff
Nov 11 19:47:46 xp1600-term kernel: [   13.628836] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Nov 11 19:47:46 xp1600-term kernel: [   13.628858] NET: Registered protocol family 2
Nov 11 19:47:46 xp1600-term kernel: [   13.667787] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 11 19:47:46 xp1600-term kernel: [   13.668204] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Nov 11 19:47:46 xp1600-term kernel: [   13.672887] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 11 19:47:46 xp1600-term kernel: [   13.674697] TCP: Hash tables configured (established 131072 bind 65536)
Nov 11 19:47:46 xp1600-term kernel: [   13.674706] TCP reno registered
Nov 11 19:47:46 xp1600-term kernel: [   13.683971] checking if image is initramfs... it is
Nov 11 19:47:47 xp1600-term kernel: [   14.131100] Switched to high resolution mode on CPU 0
Nov 11 19:47:47 xp1600-term kernel: [   14.576447] Freeing initrd memory: 7215k freed
Nov 11 19:47:47 xp1600-term kernel: [   14.577221] audit: initializing netlink socket (disabled)
Nov 11 19:47:47 xp1600-term kernel: [   14.577251] audit(1194810435.124:1): initialized
Nov 11 19:47:47 xp1600-term kernel: [   14.580385] VFS: Disk quotas dquot_6.5.1
Nov 11 19:47:47 xp1600-term kernel: [   14.580494] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 11 19:47:47 xp1600-term kernel: [   14.580679] io scheduler noop registered
Nov 11 19:47:47 xp1600-term kernel: [   14.580683] io scheduler anticipatory registered
Nov 11 19:47:47 xp1600-term kernel: [   14.580686] io scheduler deadline registered
Nov 11 19:47:47 xp1600-term kernel: [   14.580707] io scheduler cfq registered (default)
Nov 11 19:47:47 xp1600-term kernel: [   14.580733] PCI: VIA PCI bridge detected. Disabling DAC.
Nov 11 19:47:47 xp1600-term kernel: [   14.581130] isapnp: Scanning for PnP cards...
Nov 11 19:47:47 xp1600-term kernel: [   14.934955] isapnp: No Plug & Play device found
Nov 11 19:47:47 xp1600-term kernel: [   14.983899] Real Time Clock Driver v1.12ac
Nov 11 19:47:47 xp1600-term kernel: [   14.984068] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 11 19:47:47 xp1600-term kernel: [   14.986491] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 11 19:47:47 xp1600-term kernel: [   14.986858] input: Macintosh mouse button emulation as /class/input/input0
Nov 11 19:47:47 xp1600-term kernel: [   14.986978] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov 11 19:47:47 xp1600-term kernel: [   14.990622] i8042.c: Detected active multiplexing controller, rev 1.1.
Nov 11 19:47:47 xp1600-term kernel: [   14.991754] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 11 19:47:47 xp1600-term kernel: [   14.991766] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Nov 11 19:47:47 xp1600-term kernel: [   14.991771] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Nov 11 19:47:47 xp1600-term kernel: [   14.991775] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Nov 11 19:47:47 xp1600-term kernel: [   14.991779] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Nov 11 19:47:47 xp1600-term kernel: [   14.992198] mice: PS/2 mouse device common for all mice
Nov 11 19:47:47 xp1600-term kernel: [   14.992536] EISA: Probing bus 0 at eisa.0
Nov 11 19:47:47 xp1600-term kernel: [   14.992555] Cannot allocate resource for EISA slot 1
Nov 11 19:47:47 xp1600-term kernel: [   14.992588] EISA: Detected 0 cards.
Nov 11 19:47:47 xp1600-term kernel: [   14.992778] TCP cubic registered
Nov 11 19:47:47 xp1600-term kernel: [   14.992792] NET: Registered protocol family 1
Nov 11 19:47:47 xp1600-term kernel: [   14.992828] Using IPI No-Shortcut mode
Nov 11 19:47:47 xp1600-term kernel: [   14.993110]   Magic number: 15:109:799
Nov 11 19:47:47 xp1600-term kernel: [   14.993351]   hash matches device ptyr7
Nov 11 19:47:47 xp1600-term kernel: [   14.993433]   hash matches device PNP0C09:00
Nov 11 19:47:47 xp1600-term kernel: [   14.994425] Freeing unused kernel memory: 364k freed
Nov 11 19:47:47 xp1600-term kernel: [   15.137345] input: AT Translated Set 2 keyboard as /class/input/input1
Nov 11 19:47:47 xp1600-term kernel: [   16.365303] AppArmor: AppArmor initialized<5>audit(1194810437.124:2):  type=1505 info="AppArmor initialized" pid=1177
Nov 11 19:47:47 xp1600-term kernel: [   16.375519] fuse init (API version 7.8)
Nov 11 19:47:47 xp1600-term kernel: [   16.383506] Failure registering capabilities with primary security module.
Nov 11 19:47:47 xp1600-term kernel: [   16.402570] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Nov 11 19:47:47 xp1600-term kernel: [    3.432000] Marking TSC unstable due to: possible TSC halt in C2.
Nov 11 19:47:47 xp1600-term kernel: [    3.436000] Time: acpi_pm clocksource has been installed.
Nov 11 19:47:47 xp1600-term kernel: [    3.456000] ACPI: Thermal Zone [THRM] (0 C)
Nov 11 19:47:47 xp1600-term kernel: [    4.396000] usbcore: registered new interface driver usbfs
Nov 11 19:47:47 xp1600-term kernel: [    4.396000] usbcore: registered new interface driver hub
Nov 11 19:47:47 xp1600-term kernel: [    4.396000] usbcore: registered new device driver usb
Nov 11 19:47:47 xp1600-term kernel: [    4.400000] USB Universal Host Controller Interface driver v3.0
Nov 11 19:47:47 xp1600-term kernel: [    4.400000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Nov 11 19:47:47 xp1600-term kernel: [    4.400000] PCI: VIA VLink IRQ fixup for 0000:00:10.0, from 0 to 7
Nov 11 19:47:47 xp1600-term kernel: [    4.400000] uhci_hcd 0000:00:10.0: UHCI Host Controller
Nov 11 19:47:47 xp1600-term kernel: [    4.400000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Nov 11 19:47:47 xp1600-term kernel: [    4.400000] uhci_hcd 0000:00:10.0: irq 7, io base 0x0000e400
Nov 11 19:47:47 xp1600-term kernel: [    4.400000] usb usb1: configuration #1 chosen from 1 choice
Nov 11 19:47:47 xp1600-term kernel: [    4.400000] hub 1-0:1.0: USB hub found
Nov 11 19:47:47 xp1600-term kernel: [    4.400000] hub 1-0:1.0: 2 ports detected
Nov 11 19:47:47 xp1600-term kernel: [    4.500000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 11 19:47:47 xp1600-term kernel: [    4.500000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 11 19:47:47 xp1600-term kernel: [    4.504000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Nov 11 19:47:47 xp1600-term kernel: [    4.504000] PCI: VIA VLink IRQ fixup for 0000:00:10.1, from 0 to 7
Nov 11 19:47:47 xp1600-term kernel: [    4.504000] uhci_hcd 0000:00:10.1: UHCI Host Controller
Nov 11 19:47:47 xp1600-term kernel: [    4.504000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Nov 11 19:47:47 xp1600-term kernel: [    4.504000] uhci_hcd 0000:00:10.1: irq 7, io base 0x0000e800
Nov 11 19:47:47 xp1600-term kernel: [    4.504000] usb usb2: configuration #1 chosen from 1 choice
Nov 11 19:47:47 xp1600-term kernel: [    4.504000] hub 2-0:1.0: USB hub found
Nov 11 19:47:47 xp1600-term kernel: [    4.504000] hub 2-0:1.0: 2 ports detected
Nov 11 19:47:47 xp1600-term kernel: [    4.568000] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Nov 11 19:47:47 xp1600-term kernel: [    4.608000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Nov 11 19:47:47 xp1600-term kernel: [    4.608000] PCI: VIA VLink IRQ fixup for 0000:00:10.2, from 0 to 7
Nov 11 19:47:47 xp1600-term kernel: [    4.608000] uhci_hcd 0000:00:10.2: UHCI Host Controller
Nov 11 19:47:47 xp1600-term kernel: [    4.608000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Nov 11 19:47:47 xp1600-term kernel: [    4.608000] uhci_hcd 0000:00:10.2: irq 7, io base 0x0000ec00
Nov 11 19:47:47 xp1600-term kernel: [    4.608000] usb usb3: configuration #1 chosen from 1 choice
Nov 11 19:47:47 xp1600-term kernel: [    4.608000] hub 3-0:1.0: USB hub found
Nov 11 19:47:47 xp1600-term kernel: [    4.608000] hub 3-0:1.0: 2 ports detected
Nov 11 19:47:47 xp1600-term kernel: [    4.712000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
Nov 11 19:47:47 xp1600-term kernel: [    4.712000] PCI: VIA VLink IRQ fixup for 0000:00:10.3, from 0 to 7
Nov 11 19:47:47 xp1600-term kernel: [    4.712000] ehci_hcd 0000:00:10.3: EHCI Host Controller
Nov 11 19:47:47 xp1600-term kernel: [    4.712000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Nov 11 19:47:47 xp1600-term kernel: [    4.712000] ehci_hcd 0000:00:10.3: irq 7, io mem 0xdfffff00
Nov 11 19:47:47 xp1600-term kernel: [    4.712000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 11 19:47:47 xp1600-term kernel: [    4.712000] usb usb4: configuration #1 chosen from 1 choice
Nov 11 19:47:47 xp1600-term kernel: [    4.712000] hub 4-0:1.0: USB hub found
Nov 11 19:47:47 xp1600-term kernel: [    4.712000] hub 4-0:1.0: 6 ports detected
Nov 11 19:47:47 xp1600-term kernel: [    4.816000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
Nov 11 19:47:47 xp1600-term kernel: [    4.816000] ACPI: Unable to derive IRQ for device 0000:00:11.1
Nov 11 19:47:47 xp1600-term kernel: [    4.816000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
Nov 11 19:47:47 xp1600-term kernel: [    4.816000] VP_IDE: chipset revision 6
Nov 11 19:47:47 xp1600-term kernel: [    4.816000] VP_IDE: not 100%% native mode: will probe irqs later
Nov 11 19:47:47 xp1600-term kernel: [    4.816000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Nov 11 19:47:47 xp1600-term kernel: [    4.816000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
Nov 11 19:47:47 xp1600-term kernel: [    4.816000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
Nov 11 19:47:47 xp1600-term kernel: [    5.232000] hda: ST98823A, ATA DISK drive
Nov 11 19:47:47 xp1600-term kernel: [    5.904000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Nov 11 19:47:47 xp1600-term kernel: [    6.828000] hdc: ASUS SDRW-0806T-D, ATAPI CD/DVD-ROM drive
Nov 11 19:47:47 xp1600-term kernel: [    7.520000] ide1 at 0x170-0x177,0x376 on irq 15
Nov 11 19:47:47 xp1600-term kernel: [    7.540000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Nov 11 19:47:47 xp1600-term kernel: [    7.544000] eth0: VIA Rhine II at 0x1d800, 00:40:45:1b:a5:db, IRQ 11.
Nov 11 19:47:47 xp1600-term kernel: [    7.544000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
Nov 11 19:47:47 xp1600-term kernel: [    7.556000] SCSI subsystem initialized
Nov 11 19:47:47 xp1600-term kernel: [    7.580000] hda: max request size: 512KiB
Nov 11 19:47:47 xp1600-term kernel: [    7.596000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
Nov 11 19:47:47 xp1600-term kernel: [    7.596000] hda: cache flushes supported
Nov 11 19:47:47 xp1600-term kernel: [    7.596000]  hda: hda1 hda2 hda3 hda4 < hda5 hda6 hda7 >
Nov 11 19:47:47 xp1600-term kernel: [    7.708000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Nov 11 19:47:47 xp1600-term kernel: [    7.708000] Uniform CD-ROM driver Revision: 3.20
Nov 11 19:47:47 xp1600-term kernel: [    8.116000] kjournald starting.  Commit interval 5 seconds
Nov 11 19:47:47 xp1600-term kernel: [    8.116000] EXT3-fs: mounted filesystem with ordered data mode.
Nov 11 19:47:47 xp1600-term kernel: [   20.580000] Linux agpgart interface v0.102 (c) Dave Jones
Nov 11 19:47:47 xp1600-term kernel: [   20.620000] Yenta: CardBus bridge found at 0000:00:0a.0 [0001:0000]
Nov 11 19:47:47 xp1600-term kernel: [   20.620000] Yenta O2: res at 0x94/0xD4: 00/ea
Nov 11 19:47:47 xp1600-term kernel: [   20.620000] Yenta O2: enabling read prefetch/write burst
Nov 11 19:47:47 xp1600-term kernel: [   20.668000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 11 19:47:47 xp1600-term kernel: [   20.748000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
Nov 11 19:47:47 xp1600-term kernel: [   20.748000] Socket status: 30000820
Nov 11 19:47:47 xp1600-term kernel: [   20.756000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 11 19:47:47 xp1600-term kernel: [   21.004000] agpgart: Detected VIA Apollo Pro266 chipset
Nov 11 19:47:47 xp1600-term kernel: [   21.008000] agpgart: AGP aperture is 64M @ 0xe0000000
Nov 11 19:47:47 xp1600-term kernel: [   21.384000] pccard: CardBus card inserted into slot 0
Nov 11 19:47:47 xp1600-term kernel: [   22.040000] NET: Registered protocol family 23
Nov 11 19:47:47 xp1600-term kernel: [   22.116000] input: PC Speaker as /class/input/input2
Nov 11 19:47:47 xp1600-term kernel: [   22.120000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
Nov 11 19:47:47 xp1600-term kernel: [   22.156000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
Nov 11 19:47:47 xp1600-term kernel: [   22.556000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Nov 11 19:47:47 xp1600-term kernel: [   22.568000] ath_hal: module license 'Proprietary' taints kernel.
Nov 11 19:47:47 xp1600-term kernel: [   22.568000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Nov 11 19:47:47 xp1600-term kernel: [   22.896000] wlan: 0.8.4.2 (0.9.3.2)
Nov 11 19:47:47 xp1600-term kernel: [   22.948000] cs: IO port probe 0x100-0x3af: clean.
Nov 11 19:47:47 xp1600-term kernel: [   22.948000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Nov 11 19:47:47 xp1600-term kernel: [   22.948000] cs: IO port probe 0x820-0x8ff: clean.
Nov 11 19:47:47 xp1600-term kernel: [   22.952000] cs: IO port probe 0xc00-0xcf7: clean.
Nov 11 19:47:47 xp1600-term kernel: [   22.952000] cs: IO port probe 0xa00-0xaff: clean.
Nov 11 19:47:47 xp1600-term kernel: [   23.008000] ath_pci: 0.9.4.5 (0.9.3.2)
Nov 11 19:47:47 xp1600-term kernel: [   23.080000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Nov 11 19:47:47 xp1600-term kernel: [   23.592000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Nov 11 19:47:47 xp1600-term kernel: [   23.592000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] ath_rate_sample: 1.2 (0.9.3.2)
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: mac 5.9 phy 4.3 radio 4.6
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: Use hw queue 1 for WME_AC_BE traffic
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: Use hw queue 0 for WME_AC_BK traffic
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: Use hw queue 2 for WME_AC_VI traffic
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: Use hw queue 3 for WME_AC_VO traffic
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: Use hw queue 8 for CAB traffic
Nov 11 19:47:47 xp1600-term kernel: [   24.088000] wifi0: Use hw queue 9 for beacons
Nov 11 19:47:47 xp1600-term kernel: [   24.124000] wifi0: Atheros 5212: mem=0x34000000, irq=10
Nov 11 19:47:47 xp1600-term kernel: [   25.268000] lp: driver loaded but no devices found
Nov 11 19:47:47 xp1600-term kernel: [   25.792000] EXT3 FS on hda5, internal journal
Nov 11 19:47:47 xp1600-term kernel: [   26.776000] kjournald starting.  Commit interval 5 seconds
Nov 11 19:47:47 xp1600-term kernel: [   26.776000] EXT3 FS on hda2, internal journal
Nov 11 19:47:47 xp1600-term kernel: [   26.776000] EXT3-fs: mounted filesystem with ordered data mode.
Nov 11 19:47:47 xp1600-term kernel: [   26.812000] kjournald starting.  Commit interval 5 seconds
Nov 11 19:47:47 xp1600-term kernel: [   26.812000] EXT3 FS on hda6, internal journal
Nov 11 19:47:47 xp1600-term kernel: [   26.812000] EXT3-fs: mounted filesystem with ordered data mode.
Nov 11 19:47:47 xp1600-term kernel: [   29.880000] ACPI: Battery Slot [BAT0] (battery present)
Nov 11 19:47:47 xp1600-term kernel: [   30.616000] ACPI: AC Adapter [AC] (off-line)
Nov 11 19:47:47 xp1600-term kernel: [   30.740000] input: Power Button (FF) as /class/input/input4
Nov 11 19:47:47 xp1600-term kernel: [   30.740000] ACPI: Power Button (FF) [PWRF]
Nov 11 19:47:47 xp1600-term kernel: [   30.768000] input: Power Button (CM) as /class/input/input5
Nov 11 19:47:47 xp1600-term kernel: [   30.768000] ACPI: Power Button (CM) [PWRB]
Nov 11 19:47:47 xp1600-term kernel: [   30.780000] input: Sleep Button (CM) as /class/input/input6
Nov 11 19:47:47 xp1600-term kernel: [   30.780000] ACPI: Sleep Button (CM) [SLPB]
Nov 11 19:47:47 xp1600-term kernel: [   30.788000] input: Lid Switch as /class/input/input7
Nov 11 19:47:47 xp1600-term kernel: [   30.788000] ACPI: Lid Switch [LIDD]
Nov 11 19:47:47 xp1600-term kernel: [   30.940000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Nov 11 19:47:47 xp1600-term kernel: [   30.996000] No dock devices found.
Nov 11 19:47:47 xp1600-term kernel: [   31.360000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
Nov 11 19:47:47 xp1600-term kernel: [   31.364000] powernow: SGTC: 13333
Nov 11 19:47:47 xp1600-term kernel: [   31.364000] powernow: Minimum speed 398 MHz. Maximum speed 1393 MHz.
Nov 11 19:47:48 xp1600-term kernel: [   33.468000] eth0: link down
Nov 11 19:47:50 xp1600-term kernel: [   35.808000] ppdev: user-space parallel port driver
Nov 11 19:47:51 xp1600-term kernel: [   36.440000] [drm] Initialized drm 1.1.0 20060810
Nov 11 19:47:51 xp1600-term kernel: [   36.456000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
Nov 11 19:47:51 xp1600-term kernel: [   36.464000] [drm] Initialized savage 2.4.1 20050313 on minor 0
Nov 11 19:47:51 xp1600-term kernel: [   36.464000] mtrr: base(0xd2000000) is not aligned on a size(0x5000000) boundary
Nov 11 19:47:51 xp1600-term kernel: [   36.464000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Nov 11 19:47:51 xp1600-term kernel: [   36.464000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
Nov 11 19:47:51 xp1600-term kernel: [   36.464000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
Nov 11 19:47:51 xp1600-term kernel: [   36.884000] NET: Registered protocol family 10
Nov 11 19:47:51 xp1600-term kernel: [   36.884000] lo: Disabled Privacy Extensions
Nov 11 19:47:51 xp1600-term kernel: [   36.884000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 11 19:47:52 xp1600-term kernel: [   37.328000] audit(1194785271.878:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4772 profile="/usr/sbin/cupsd"
Nov 11 19:47:52 xp1600-term kernel: [   37.596000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov 11 19:47:52 xp1600-term kernel: [   37.596000] apm: overridden by ACPI.
Nov 11 19:47:53 xp1600-term kernel: [   38.712000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Nov 11 19:47:53 xp1600-term kernel: [   38.832000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Nov 11 19:47:53 xp1600-term kernel: [   38.844000] NFSD: starting 90-second grace period
Nov 11 19:47:56 xp1600-term kernel: [   41.152000] Clocksource tsc unstable (delta = -163797483 ns)
Nov 11 19:47:59 xp1600-term kernel: [   44.524000] Failure registering capabilities with primary security module.
Nov 11 19:48:00 xp1600-term dhcdbd: Started up.
Nov 11 19:48:27 xp1600-term dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Nov 11 19:48:29 xp1600-term kernel: [   74.844000] NET: Registered protocol family 17
Nov 11 19:48:39 xp1600-term dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Nov 11 19:48:39 xp1600-term dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Nov 11 19:48:39 xp1600-term dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers

```

Or I have to restart it and then capture /var/log/messages ?

---

### Post by oilchangeguy on 2007-11-11
i've got a toshiba satellite 1805-s177 that does the same thing. and i've used 6.06, and 7.04. both will not restart. if a restart is needed, i just shut it down, and start it again. it takes a little longer, but it's no big deal.

---

### Post by guttdude on 2007-11-11
This is /var/log/messages in the margin of the period of restart.

```

Nov 11 19:48:39 xp1600-term dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Nov 11 20:03:11 xp1600-term kernel: [  955.112000] nfsd: last server has exited
Nov 11 20:03:11 xp1600-term kernel: [  955.112000] nfsd: unexporting all filesystems
Nov 11 20:03:11 xp1600-term kernel: [  955.124000] RPC: failed to contact local rpcbind server (errno 5).
Nov 11 20:03:11 xp1600-term exiting on signal 15
Nov 11 20:33:11 xp1600-term syslogd 1.4.1#21ubuntu3: restart.
Nov 11 20:33:11 xp1600-term kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov 11 20:33:12 xp1600-term kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov 11 20:33:12 xp1600-term kernel: Symbols match kernel version 2.6.22.
Nov 11 20:33:12 xp1600-term kernel: No module symbols loaded - kernel modules not enabled. 

```

I don't think it helps?

---

### Post by SpiritIsReality on 2007-11-11
howdy
Please try running  
dmesg
Sometimes in that the messages recommend trying things like add acpi=force to the end of your kernel line in /boot/grub/menu.lst .
running a dmesg | grep = 
might work to weed out anything with a = in it. yep. I just tried it and one of the lines is:
[   39.875553] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
So what I could try to do is:
make a backup of /boot/grub/menu.lst if I feel like it
sudo cp /boot/grub/men.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
add the pci=routeirq onto the kernel line like so
kernel /boot/vmlinuz-2.6.22-14-genericroot=UUID=a10146c1-ff01-426e-91b1-1b14f186e17f ro pci=routeirq
save and close.If you're wondering why there's no quiet splash, have a look at 
zless /usr/share/doc/upstart/README.Debian.gz
use the pag or arrow keys to up or down. type q to quit.
trails

---

