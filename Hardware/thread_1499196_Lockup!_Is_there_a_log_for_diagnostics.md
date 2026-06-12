---
title: "Lockup! Is there a log for diagnostics?"
date: 2010-06-01
forum: Hardware
---

### Post by Moozillaaa on 2010-06-01
My machine just locked up with GIMP image editing in motion...

I had to pull the plug, with NO response from the machine. Is there a log that gives any info here?


edit:
I just noticed that ALL browsing history, from the last 'session', is gone. This alone must mean something also...

2nd edit:
My browsing history library just got wiped of the last 16 days' history. This is a real mystery.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=159061&d=1275427277[/IMG]

---

### Post by Moozillaaa on 2010-06-01
It's looking like my system just did a 'System Restore', to how it was 2 weeks ago.
 
Earlier this morning, for example, I moved 1,700 pictures from one file, into another file, for X-screensaver GLSlideshow. I installed X-screensaver too. 
 
Both changes are UNDONE, and I wonder what else I'll find here... [IMG]http://www.linuxforums.org/forum/images/smilies/confused.gif[/IMG]

---

### Post by kevinatkins on 2010-06-01
Hi,

This looks mighty strange... never seen anything like this before! To get you started, you'll find various log files in the /var/log directory. First file to examine would probably be /var/log/messages. A convenient way of looking at the logs is with the log file viewer, which you can find in System -> Administration. 

Good luck!

---

### Post by uOpt on 2010-06-01
A corrupted Mozilla history file happens every now and then on crashes.

One diagnostic item is whether the keyboard LEDs blink. If yes, it is a kernel panic.

Generally, since Linux does lack the bluescreen feature of Windows, the best you can do is switch to a text console when you expect the crash to happen so that error messages are not hidden from you by X11.

Did you do the usual testing circus (mprime, superpi, memtest86)?

---

### Post by Moozillaaa on 2010-06-01
> **uOpt said:**
> A corrupted Mozilla history file happens every now and then on crashes.

One diagnostic item is whether the keyboard LEDs blink. If yes, it is a kernel panic.

Generally, since Linux does lack the bluescreen feature of Windows, the best you can do is switch to a text console when you expect the crash to happen so that error messages are not hidden from you by X11.

Did you do the usual testing circus (mprime, superpi, memtest86)?

No tests done yet, but I guess I need to run them...




 
No, no freezes before. New build, 1 month ago, all compatible components...
Foxconn A7DA-S
AMD Athlon II X3 440
2 x 1G KVR667D2K2 memsticks.
 
This is getting VERY mysterious - it's like my clock just went back.
 
Last week, I changed the Unix root password, and added root user log in to X-server. Those settings just UN-did also. [IMG]http://www.linuxforums.org/forum/images/smilies/confused.gif[/IMG] [IMG]http://www.linuxforums.org/forum/images/smilies/confused.gif[/IMG] [IMG]http://www.linuxforums.org/forum/images/smilies/confused.gif[/IMG]
 
I flashed BIOS early last week; it is still written in place. CPU was not recognized new, until after flash.
 
XP is also on this disk. I have not booted it up, to see how that looks, since the clock seems to have backed up. [IMG]http://www.linuxforums.org/forum/images/smilies/icon_eek.gif[/IMG]

---

### Post by Moozillaaa on 2010-06-01
Anything of note here in this log/message file?

```
Jun  1 17:20:50 chucknb-desktop syslogd 1.5.0#1ubuntu1: restart.
Jun  1 17:36:32 chucknb-desktop kernel: [ 1631.973181] usb 2-3: reset high speed USB device using ehci_hcd and address 2
Jun  1 17:37:07 chucknb-desktop kernel: [ 1666.943889] usb 2-3: reset high speed USB device using ehci_hcd and address 2
Jun  1 17:37:48 chucknb-desktop kernel: [ 1707.665022] usb 2-3: reset high speed USB device using ehci_hcd and address 2
Jun  1 17:50:33 chucknb-desktop -- MARK --
Jun  1 18:06:07 chucknb-desktop kernel: [ 3405.122585] Not cloning cgroup for unused subsystem ns
Jun  1 18:06:07 chucknb-desktop kernel: [ 3405.400282] [fglrx] interrupt source ff00002f successfully disabled!
Jun  1 18:06:07 chucknb-desktop kernel: [ 3405.400286] [fglrx] enable ID = 0x00000000
Jun  1 18:06:07 chucknb-desktop kernel: [ 3405.400289] [fglrx] Receive disable interrupt message with irqEnableMask: ff00002f; dwIRQEnableId: 00000006
Jun  1 18:06:13 chucknb-desktop kernel: [ 3411.446207] nfsd: last server has exited
Jun  1 18:06:13 chucknb-desktop kernel: [ 3411.446245] nfsd: unexporting all filesystems
Jun  1 18:06:13 chucknb-desktop exiting on signal 15
Jun  1 18:21:02 chucknb-desktop syslogd 1.5.0#1ubuntu1: restart.
Jun  1 18:21:02 chucknb-desktop kernel: Inspecting /boot/System.map-2.6.24-27-generic
Jun  1 18:21:02 chucknb-desktop kernel: Loaded 28554 symbols from /boot/System.map-2.6.24-27-generic.
Jun  1 18:21:02 chucknb-desktop kernel: Symbols match kernel version 2.6.24.
Jun  1 18:21:03 chucknb-desktop kernel: Loaded 26204 symbols from 107 modules.
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Linux version 2.6.24-27-generic (buildd@yellow) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Mar 24 11:03:26 UTC 2010 (Ubuntu 2.6.24-27.69-generic)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Command line: root=UUID=32a7f436-76a6-4cca-966f-2d24d2e2702a ro quiet splash
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000006ffb0000 (usable)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]  BIOS-e820: 000000006ffb0000 - 000000006ffbe000 (ACPI data)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]  BIOS-e820: 000000006ffbe000 - 000000006ffe0000 (ACPI NVS)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]  BIOS-e820: 000000006ffe0000 - 0000000070000000 (reserved)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] end_pfn_map = 1048576
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] DMI present.
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FA1F0 checksum 0
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: RSDP 000FA1F0, 0014 (r0 ACPIAM)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: RSDT 6FFB0000, 003C (r1 080409 RSDT0751 20090804 MSFT       97)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: FACP 6FFB0200, 0084 (r1 080409 FACP0751 20090804 MSFT       97)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20070126]
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: DSDT 6FFB0450, 9420 (r1  81BF1 81BF1P09        0 INTL 20051117)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: FACS 6FFBE000, 0040
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: APIC 6FFB0390, 007C (r1 080409 APIC0751 20090804 MSFT       97)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: MCFG 6FFB0410, 003C (r1 080409 OEMMCFG  20090804 MSFT       97)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: OEMB 6FFBE040, 0072 (r1 080409 OEMB0751 20090804 MSFT       97)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: HPET 6FFB9870, 0038 (r1 080409 OEMHPET  20090804 MSFT       97)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: SSDT 6FFB98B0, 0672 (r1 A M I  POWERNOW        1 AMD         1)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] No NUMA configuration found
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Faking a node at 0000000000000000-000000006ffb0000
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000006ffb0000
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Zone PFN ranges:
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]   DMA             0 ->     4096
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]   DMA32        4096 ->  1048576
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]   Normal    1048576 ->  1048576
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Movable zone start PFN for each node
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]     0:        0 ->      159
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000]     0:      256 ->   458672
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Processor #1
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Processor #2
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 3, address 0xfec00000, GSI 0-23
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Setting APIC routing to flat
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 70000000:8f700000)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] SMP: Allowing 6 CPUs, 3 hotplug CPUs
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 451083
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Policy zone: DMA32
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Kernel command line: root=UUID=32a7f436-76a6-4cca-966f-2d24d2e2702a ro quiet splash
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] Initializing CPU#0
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jun  1 18:21:03 chucknb-desktop kernel: [    0.000000] TSC calibrated against HPET
Jun  1 18:21:03 chucknb-desktop kernel: [   30.556689] Marking TSC unstable due to TSCs unsynchronized
Jun  1 18:21:03 chucknb-desktop kernel: [   30.556691] time.c: Detected 3000.103 MHz processor.
Jun  1 18:21:03 chucknb-desktop kernel: [   30.557264] Console: colour VGA+ 80x25
Jun  1 18:21:03 chucknb-desktop kernel: [   30.557266] console [tty0] enabled
Jun  1 18:21:03 chucknb-desktop kernel: [   30.557278] Checking aperture...
Jun  1 18:21:03 chucknb-desktop kernel: [   30.557280] CPU 0: aperture @ 5022000000 size 32 MB
Jun  1 18:21:03 chucknb-desktop kernel: [   30.557281] Aperture too small (32 MB)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.565527] No AGP bridge found
Jun  1 18:21:03 chucknb-desktop kernel: [   30.574442] Memory: 1796432k/1834688k available (2494k kernel code, 37868k reserved, 1322k data, 320k init)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.574464] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=6, Nodes=1
Jun  1 18:21:03 chucknb-desktop kernel: [   30.574474] Calibrating delay loop (skipped), using tsc calculated value.. 6000.20 BogoMIPS (lpj=12000412)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.574494] Security Framework initialized
Jun  1 18:21:03 chucknb-desktop kernel: [   30.574498] SELinux:  Disabled at boot.
Jun  1 18:21:03 chucknb-desktop kernel: [   30.574507] AppArmor: AppArmor initialized
Jun  1 18:21:03 chucknb-desktop kernel: [   30.574509] Failure registering capabilities with primary security module.
Jun  1 18:21:03 chucknb-desktop kernel: [   30.574602] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575262] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575570] Mount-cache hash table entries: 256
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575653] Initializing cgroup subsys ns
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575656] Initializing cgroup subsys cpuacct
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575667] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575668] CPU: L2 Cache: 512K (64 bytes/line)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575670] CPU 0/0 -> Node 0
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575671] CPU: Physical Processor ID: 0
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575672] CPU: Processor Core ID: 0
Jun  1 18:21:03 chucknb-desktop kernel: [   30.575689] SMP alternatives: switching to UP code
Jun  1 18:21:03 chucknb-desktop kernel: [   30.576103] Early unpacking initramfs... done
Jun  1 18:21:03 chucknb-desktop kernel: [   30.761198] ACPI: Core revision 20070126
Jun  1 18:21:03 chucknb-desktop kernel: [   30.761250] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun  1 18:21:03 chucknb-desktop kernel: [   30.809706] Using local APIC timer interrupts.
Jun  1 18:21:03 chucknb-desktop kernel: [   30.843010] Detected 12.500 MHz APIC timer.
Jun  1 18:21:03 chucknb-desktop kernel: [   30.843075] SMP alternatives: switching to SMP code
Jun  1 18:21:03 chucknb-desktop kernel: [   30.843429] Booting processor 1/3 APIC 0x1
Jun  1 18:21:03 chucknb-desktop kernel: [   30.853465] Initializing CPU#1
Jun  1 18:21:03 chucknb-desktop kernel: [   30.930932] Calibrating delay using timer specific routine.. 6000.22 BogoMIPS (lpj=12000458)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.930936] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.930937] CPU: L2 Cache: 512K (64 bytes/line)
Jun  1 18:21:03 chucknb-desktop kernel: [   30.930939] CPU 1/1 -> Node 0
Jun  1 18:21:03 chucknb-desktop kernel: [   30.930940] CPU: Physical Processor ID: 0
Jun  1 18:21:03 chucknb-desktop kernel: [   30.930941] CPU: Processor Core ID: 1
Jun  1 18:21:03 chucknb-desktop kernel: [   30.930998] AMD Athlon(tm) II X3 440 Processor stepping 02
Jun  1 18:21:03 chucknb-desktop kernel: [   30.931007] AMD C1E detected late. Force timer broadcast.
Jun  1 18:21:03 chucknb-desktop kernel: [   30.931135] SMP alternatives: switching to SMP code
Jun  1 18:21:03 chucknb-desktop kernel: [   30.931370] Booting processor 2/3 APIC 0x2
Jun  1 18:21:03 chucknb-desktop kernel: [   30.941400] Initializing CPU#2
Jun  1 18:21:03 chucknb-desktop kernel: [   31.018935] Calibrating delay using timer specific routine.. 6000.18 BogoMIPS (lpj=12000364)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.018940] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.018941] CPU: L2 Cache: 512K (64 bytes/line)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.018943] CPU 2/2 -> Node 0
Jun  1 18:21:03 chucknb-desktop kernel: [   31.018944] CPU: Physical Processor ID: 0
Jun  1 18:21:03 chucknb-desktop kernel: [   31.018945] CPU: Processor Core ID: 2
Jun  1 18:21:03 chucknb-desktop kernel: [   31.019001] AMD Athlon(tm) II X3 440 Processor stepping 02
Jun  1 18:21:03 chucknb-desktop kernel: [   31.019038] Brought up 3 CPUs
Jun  1 18:21:03 chucknb-desktop kernel: [   31.019287] net_namespace: 120 bytes
Jun  1 18:21:03 chucknb-desktop kernel: [   31.019541] Time: 18:20:29  Date: 06/01/10
Jun  1 18:21:03 chucknb-desktop kernel: [   31.019563] NET: Registered protocol family 16
Jun  1 18:21:03 chucknb-desktop kernel: [   31.019669] ACPI: bus type pci registered
Jun  1 18:21:03 chucknb-desktop kernel: [   31.019713] PCI: Using configuration type 1
Jun  1 18:21:03 chucknb-desktop kernel: [   31.026406] ACPI: Interpreter enabled
Jun  1 18:21:03 chucknb-desktop kernel: [   31.026408] ACPI: (supports S0 S1 S3 S4 S5)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.026419] ACPI: Using IOAPIC for interrupt routing
Jun  1 18:21:03 chucknb-desktop kernel: [   31.026652] Error attaching device data
Jun  1 18:21:03 chucknb-desktop kernel: [   31.026654] Error attaching device data
Jun  1 18:21:03 chucknb-desktop kernel: [   31.026657] Error attaching device data
Jun  1 18:21:03 chucknb-desktop kernel: [   31.026659] Error attaching device data
Jun  1 18:21:03 chucknb-desktop kernel: [   31.026662] Error attaching device data
Jun  1 18:21:03 chucknb-desktop kernel: [   31.026664] Error attaching device data
Jun  1 18:21:03 chucknb-desktop kernel: [   31.032864] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.033018] pci 0000:00:11.0: set SATA to AHCI mode
Jun  1 18:21:03 chucknb-desktop kernel: [   31.034054] PCI: Transparent bridge - 0000:00:14.4
Jun  1 18:21:03 chucknb-desktop kernel: [   31.036868] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.036957] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037044] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 12 14 15)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037130] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037216] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 *10 11 12 14 15)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037302] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 *10 11 12 14 15)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037387] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *7 10 11 12 14 15)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037473] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037550] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  7C, should be 79 [20070126]
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037555] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037572] pnp: PnP ACPI init
Jun  1 18:21:03 chucknb-desktop kernel: [   31.037577] ACPI: bus type pnp registered
Jun  1 18:21:03 chucknb-desktop kernel: [   31.041281] pnp: PnP ACPI: found 17 devices
Jun  1 18:21:03 chucknb-desktop kernel: [   31.041283] ACPI: ACPI bus type pnp unregistered
Jun  1 18:21:03 chucknb-desktop kernel: [   31.041414] PCI: Using ACPI for IRQ routing
Jun  1 18:21:03 chucknb-desktop kernel: [   31.041416] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun  1 18:21:03 chucknb-desktop kernel: [   31.059187] NET: Registered protocol family 8
Jun  1 18:21:03 chucknb-desktop kernel: [   31.059188] NET: Registered protocol family 20
Jun  1 18:21:03 chucknb-desktop kernel: [   31.059246] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jun  1 18:21:03 chucknb-desktop kernel: [   31.059249] hpet0: 4 32-bit timers, 14318180 Hz
Jun  1 18:21:03 chucknb-desktop kernel: [   31.060284] AppArmor: AppArmor Filesystem Enabled
Jun  1 18:21:03 chucknb-desktop kernel: [   31.063129] Time: hpet clocksource has been installed.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.063132] Clockevents: could not switch to one-shot mode: lapic is not functional.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.063134] Could not switch to high resolution mode on CPU 0
Jun  1 18:21:03 chucknb-desktop kernel: [   31.063137] Clockevents: could not switch to one-shot mode: lapic is not functional.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.063142] Could not switch to high resolution mode on CPU 1
Jun  1 18:21:03 chucknb-desktop kernel: [   31.067121] Clockevents: could not switch to one-shot mode: lapic is not functional.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.067125] Could not switch to high resolution mode on CPU 2
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075135] system 00:01: iomem range 0x0-0x0 could not be reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075138] system 00:01: iomem range 0x70000000-0x7fffffff has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075146] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075147] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075152] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075154] system 00:0b: ioport range 0x40b-0x40b has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075155] system 00:0b: ioport range 0x4d6-0x4d6 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075157] system 00:0b: ioport range 0xc00-0xc01 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075158] system 00:0b: ioport range 0xc14-0xc14 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075160] system 00:0b: ioport range 0xc50-0xc51 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075162] system 00:0b: ioport range 0xc52-0xc52 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075163] system 00:0b: ioport range 0xc6c-0xc6c has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075165] system 00:0b: ioport range 0xc6f-0xc6f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075166] system 00:0b: ioport range 0xcd0-0xcd1 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075168] system 00:0b: ioport range 0xcd2-0xcd3 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075169] system 00:0b: ioport range 0xcd4-0xcd5 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075171] system 00:0b: ioport range 0xcd6-0xcd7 has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075172] system 00:0b: ioport range 0xcd8-0xcdf has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075174] system 00:0b: ioport range 0x800-0x89f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075175] system 00:0b: ioport range 0xb00-0xb0f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075177] system 00:0b: ioport range 0xb20-0xb3f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075178] system 00:0b: ioport range 0x900-0x90f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075179] system 00:0b: ioport range 0x910-0x91f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075181] system 00:0b: ioport range 0xfe00-0xfefe has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075183] system 00:0b: iomem range 0xffb80000-0xffbfffff could not be reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075185] system 00:0b: iomem range 0xfec10000-0xfec1001f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075189] system 00:0e: ioport range 0xe00-0xe0f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075191] system 00:0e: ioport range 0xe80-0xe8f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075192] system 00:0e: ioport range 0xf40-0xf4f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075193] system 00:0e: ioport range 0xa30-0xa3f has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075198] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075202] system 00:10: iomem range 0x0-0x9ffff could not be reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075204] system 00:10: iomem range 0xc0000-0xcffff has been reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075205] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075207] system 00:10: iomem range 0x100000-0x6fffffff could not be reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075209] system 00:10: iomem range 0xfec00000-0xffffffff could not be reserved
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075441] PCI: Bridge: 0000:00:01.0
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075442]   IO window: c000-cfff
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075445]   MEM window: fe800000-fe9fffff
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075446]   PREFETCH window: d0000000-dfffffff
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075448] PCI: Bridge: 0000:00:09.0
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075449]   IO window: disabled.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075450]   MEM window: fea00000-feafffff
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075452]   PREFETCH window: disabled.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075455] PCI: Bridge: 0000:03:05.0
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075456]   IO window: disabled.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075461]   MEM window: disabled.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075464]   PREFETCH window: f4000000-fbffffff
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075469] PCI: Bridge: 0000:00:14.4
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075471]   IO window: d000-efff
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075475]   MEM window: feb00000-febfffff
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075478]   PREFETCH window: f4000000-fbffffff
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075497] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun  1 18:21:03 chucknb-desktop kernel: [   31.075524] NET: Registered protocol family 2
Jun  1 18:21:03 chucknb-desktop kernel: [   31.087093] Clockevents: could not switch to one-shot mode:<6>Clockevents: could not switch to one-shot mode: lapic is not functional.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.087099] Could not switch to high resolution mode on CPU 0
Jun  1 18:21:03 chucknb-desktop kernel: [   31.087100] Clockevents: could not switch to one-shot mode: lapic is not functional.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.087105] Could not switch to high resolution mode on CPU 1
Jun  1 18:21:03 chucknb-desktop kernel: [   31.087107]  lapic is not functional.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.087109] Could not switch to high resolution mode on CPU 2
Jun  1 18:21:03 chucknb-desktop kernel: [   31.123129] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.123551] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.124792] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.125104] TCP: Hash tables configured (established 262144 bind 65536)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.125107] TCP reno registered
Jun  1 18:21:03 chucknb-desktop kernel: [   31.135181] checking if image is initramfs... it is
Jun  1 18:21:03 chucknb-desktop kernel: [   31.496622] Freeing initrd memory: 7545k freed
Jun  1 18:21:03 chucknb-desktop kernel: [   31.499846] audit: initializing netlink socket (disabled)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.499855] audit(1275416429.915:1): initialized
Jun  1 18:21:03 chucknb-desktop kernel: [   31.501013] VFS: Disk quotas dquot_6.5.1
Jun  1 18:21:03 chucknb-desktop kernel: [   31.501055] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.501133] io scheduler noop registered
Jun  1 18:21:03 chucknb-desktop kernel: [   31.501135] io scheduler anticipatory registered
Jun  1 18:21:03 chucknb-desktop kernel: [   31.501136] io scheduler deadline registered
Jun  1 18:21:03 chucknb-desktop kernel: [   31.501190] io scheduler cfq registered (default)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.666769] assign_interrupt_mode Found MSI capability
Jun  1 18:21:03 chucknb-desktop kernel: [   31.680032] Real Time Clock Driver v1.12ac
Jun  1 18:21:03 chucknb-desktop kernel: [   31.680178] Linux agpgart interface v0.102
Jun  1 18:21:03 chucknb-desktop kernel: [   31.680180] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun  1 18:21:03 chucknb-desktop kernel: [   31.680292] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  1 18:21:03 chucknb-desktop kernel: [   31.680413] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jun  1 18:21:03 chucknb-desktop kernel: [   31.680760] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun  1 18:21:03 chucknb-desktop kernel: [   31.681180] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun  1 18:21:03 chucknb-desktop kernel: [   31.681218] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun  1 18:21:03 chucknb-desktop kernel: [   31.681273] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PSMS] at 0x60,0x64 irq 1,12
Jun  1 18:21:03 chucknb-desktop kernel: [   31.681579] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun  1 18:21:03 chucknb-desktop kernel: [   31.681585] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690576] mice: PS/2 mouse device common for all mice
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690604] cpuidle: using governor ladder
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690605] cpuidle: using governor menu
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690696] NET: Registered protocol family 1
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690767] registered taskstats version 1
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690854]   Magic number: 14:254:341
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690954]   hash matches device ACPI0007:03
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690958] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690960] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690961] EDD information not available.
Jun  1 18:21:03 chucknb-desktop kernel: [   31.690969] Freeing unused kernel memory: 320k freed
Jun  1 18:21:03 chucknb-desktop kernel: [   31.691204] Write protecting the kernel read-only data: 1040k
Jun  1 18:21:03 chucknb-desktop kernel: [   31.722468] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun  1 18:21:03 chucknb-desktop kernel: [   32.819351] fuse init (API version 7.9)
Jun  1 18:21:03 chucknb-desktop kernel: [   32.830501] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun  1 18:21:03 chucknb-desktop kernel: [   32.830509] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun  1 18:21:03 chucknb-desktop kernel: [   32.830515] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun  1 18:21:03 chucknb-desktop kernel: [   32.831348] ACPI: Thermal Zone [THRM] (40 C)
Jun  1 18:21:03 chucknb-desktop kernel: [   32.950654] usbcore: registered new interface driver usbfs
Jun  1 18:21:03 chucknb-desktop kernel: [   32.950670] usbcore: registered new interface driver hub
Jun  1 18:21:03 chucknb-desktop kernel: [   32.950732] tg3.c:v3.86 (November 9, 2007)
Jun  1 18:21:03 chucknb-desktop kernel: [   32.950751] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun  1 18:21:03 chucknb-desktop kernel: [   32.950980] usbcore: registered new device driver usb
Jun  1 18:21:03 chucknb-desktop kernel: [   32.995613] SCSI subsystem initialized
Jun  1 18:21:03 chucknb-desktop kernel: [   33.477295] eth0: Tigon3 [partno(BCM95784M) rev 5784100 PHY(5784)] (PCI Express) 10/100/1000Base-T Ethernet 00:1f:e2:0e:22:78
Jun  1 18:21:03 chucknb-desktop kernel: [   33.477300] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Jun  1 18:21:03 chucknb-desktop kernel: [   33.477302] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jun  1 18:21:03 chucknb-desktop kernel: [   33.477420] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun  1 18:21:03 chucknb-desktop kernel: [   33.477515] ohci_hcd 0000:00:12.0: OHCI Host Controller
Jun  1 18:21:03 chucknb-desktop kernel: [   33.477707] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
Jun  1 18:21:03 chucknb-desktop kernel: [   33.477731] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe7fe000
Jun  1 18:21:03 chucknb-desktop kernel: [   33.536869] usb usb1: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   33.536885] hub 1-0:1.0: USB hub found
Jun  1 18:21:03 chucknb-desktop kernel: [   33.536892] hub 1-0:1.0: 3 ports detected
Jun  1 18:21:03 chucknb-desktop kernel: [   33.640741] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 16
Jun  1 18:21:03 chucknb-desktop kernel: [   33.640847] ohci_hcd 0000:00:12.1: OHCI Host Controller
Jun  1 18:21:03 chucknb-desktop kernel: [   33.640894] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
Jun  1 18:21:03 chucknb-desktop kernel: [   33.640909] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe7fd000
Jun  1 18:21:03 chucknb-desktop kernel: [   33.700707] usb usb2: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   33.700721] hub 2-0:1.0: USB hub found
Jun  1 18:21:03 chucknb-desktop kernel: [   33.700728] hub 2-0:1.0: 3 ports detected
Jun  1 18:21:03 chucknb-desktop kernel: [   33.804617] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
Jun  1 18:21:03 chucknb-desktop kernel: [   33.804717] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun  1 18:21:03 chucknb-desktop kernel: [   33.804760] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
Jun  1 18:21:03 chucknb-desktop kernel: [   33.804781] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe7fc000
Jun  1 18:21:03 chucknb-desktop kernel: [   33.864539] usb usb3: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   33.864555] hub 3-0:1.0: USB hub found
Jun  1 18:21:03 chucknb-desktop kernel: [   33.864561] hub 3-0:1.0: 3 ports detected
Jun  1 18:21:03 chucknb-desktop kernel: [   33.968445] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 18
Jun  1 18:21:03 chucknb-desktop kernel: [   33.968530] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jun  1 18:21:03 chucknb-desktop kernel: [   33.968576] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
Jun  1 18:21:03 chucknb-desktop kernel: [   33.968591] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe7fb000
Jun  1 18:21:03 chucknb-desktop kernel: [   34.028367] usb usb4: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   34.028381] hub 4-0:1.0: USB hub found
Jun  1 18:21:03 chucknb-desktop kernel: [   34.028387] hub 4-0:1.0: 3 ports detected
Jun  1 18:21:03 chucknb-desktop kernel: [   34.120221] usb 2-1: new low speed USB device using ohci_hcd and address 2
Jun  1 18:21:03 chucknb-desktop kernel: [   34.132286] ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 18
Jun  1 18:21:03 chucknb-desktop kernel: [   34.132385] ohci_hcd 0000:00:14.5: OHCI Host Controller
Jun  1 18:21:03 chucknb-desktop kernel: [   34.132432] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
Jun  1 18:21:03 chucknb-desktop kernel: [   34.132446] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe7fa000
Jun  1 18:21:03 chucknb-desktop kernel: [   34.192242] usb usb5: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   34.192258] hub 5-0:1.0: USB hub found
Jun  1 18:21:03 chucknb-desktop kernel: [   34.192265] hub 5-0:1.0: 2 ports detected
Jun  1 18:21:03 chucknb-desktop kernel: [   34.296167] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 17
Jun  1 18:21:03 chucknb-desktop kernel: [   34.296268] ehci_hcd 0000:00:12.2: EHCI Host Controller
Jun  1 18:21:03 chucknb-desktop kernel: [   34.296314] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 6
Jun  1 18:21:03 chucknb-desktop kernel: [   34.296345] ehci_hcd 0000:00:12.2: debug port 1
Jun  1 18:21:03 chucknb-desktop kernel: [   34.296356] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe7ff800
Jun  1 18:21:03 chucknb-desktop kernel: [   34.332007] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun  1 18:21:03 chucknb-desktop kernel: [   34.332078] usb usb6: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   34.332094] hub 6-0:1.0: USB hub found
Jun  1 18:21:03 chucknb-desktop kernel: [   34.332098] hub 6-0:1.0: 6 ports detected
Jun  1 18:21:03 chucknb-desktop kernel: [   34.439985] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 19
Jun  1 18:21:03 chucknb-desktop kernel: [   34.440081] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun  1 18:21:03 chucknb-desktop kernel: [   34.440136] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 7
Jun  1 18:21:03 chucknb-desktop kernel: [   34.440166] ehci_hcd 0000:00:13.2: debug port 1
Jun  1 18:21:03 chucknb-desktop kernel: [   34.440177] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe7ff400
Jun  1 18:21:03 chucknb-desktop kernel: [   34.451891] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun  1 18:21:03 chucknb-desktop kernel: [   34.451956] usb usb7: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   34.451970] hub 7-0:1.0: USB hub found
Jun  1 18:21:03 chucknb-desktop kernel: [   34.451973] hub 7-0:1.0: 6 ports detected
Jun  1 18:21:03 chucknb-desktop kernel: [   34.555904] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 22
Jun  1 18:21:03 chucknb-desktop kernel: [   34.556014] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
Jun  1 18:21:03 chucknb-desktop kernel: [   35.558878] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Jun  1 18:21:03 chucknb-desktop kernel: [   35.558882] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
Jun  1 18:21:03 chucknb-desktop kernel: [   35.559623] scsi0 : ahci
Jun  1 18:21:03 chucknb-desktop kernel: [   35.559969] scsi1 : ahci
Jun  1 18:21:03 chucknb-desktop kernel: [   35.560117] scsi2 : ahci
Jun  1 18:21:03 chucknb-desktop kernel: [   35.560263] scsi3 : ahci
Jun  1 18:21:03 chucknb-desktop kernel: [   35.560307] ata1: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd00 irq 22
Jun  1 18:21:03 chucknb-desktop kernel: [   35.560310] ata2: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd80 irq 22
Jun  1 18:21:03 chucknb-desktop kernel: [   35.560312] ata3: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe00 irq 22
Jun  1 18:21:03 chucknb-desktop kernel: [   35.560314] ata4: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe80 irq 22
Jun  1 18:21:03 chucknb-desktop kernel: [   35.690726] usb 7-3: new high speed USB device using ehci_hcd and address 2
Jun  1 18:21:03 chucknb-desktop kernel: [   35.838981] usb 7-3: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   36.046379] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun  1 18:21:03 chucknb-desktop kernel: [   36.054213] ata1.00: ATA-7: WDC WD5000ABYS-01TNA0, 12.01C01, max UDMA/133
Jun  1 18:21:03 chucknb-desktop kernel: [   36.054215] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun  1 18:21:03 chucknb-desktop kernel: [   36.055747] ata1.00: configured for UDMA/133
Jun  1 18:21:03 chucknb-desktop kernel: [   36.098340] usb 7-4: new high speed USB device using ehci_hcd and address 3
Jun  1 18:21:03 chucknb-desktop kernel: [   36.249731] usb 7-4: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   36.533918] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun  1 18:21:03 chucknb-desktop kernel: [   36.547906] ata2.00: ATA-7: WDC WD5000ABYS-01TNA0, 12.01C01, max UDMA/133
Jun  1 18:21:03 chucknb-desktop kernel: [   36.547909] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun  1 18:21:03 chucknb-desktop kernel: [   36.549443] ata2.00: configured for UDMA/133
Jun  1 18:21:03 chucknb-desktop kernel: [   36.585857] usb 2-1: new low speed USB device using ohci_hcd and address 4
Jun  1 18:21:03 chucknb-desktop kernel: [   36.825109] usb 2-1: configuration #1 chosen from 1 choice
Jun  1 18:21:03 chucknb-desktop kernel: [   37.029451] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun  1 18:21:03 chucknb-desktop kernel: [   37.039900] ata3.00: ATA-7: WDC WD5000ABYS-01TNA0, 12.01C01, max UDMA/133
Jun  1 18:21:03 chucknb-desktop kernel: [   37.039902] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun  1 18:21:03 chucknb-desktop kernel: [   37.041425] ata3.00: configured for UDMA/133
Jun  1 18:21:03 chucknb-desktop kernel: [   37.357120] ata4: SATA link down (SStatus 0 SControl 300)
Jun  1 18:21:03 chucknb-desktop kernel: [   37.357219] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000ABYS-0 12.0 PQ: 0 ANSI: 5
Jun  1 18:21:03 chucknb-desktop kernel: [   37.357286] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000ABYS-0 12.0 PQ: 0 ANSI: 5
Jun  1 18:21:03 chucknb-desktop kernel: [   37.357332] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000ABYS-0 12.0 PQ: 0 ANSI: 5
Jun  1 18:21:03 chucknb-desktop kernel: [   37.358338] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jun  1 18:21:03 chucknb-desktop kernel: [   37.359340] scsi4 : pata_atiixp
Jun  1 18:21:03 chucknb-desktop kernel: [   37.359671] scsi5 : pata_atiixp
Jun  1 18:21:03 chucknb-desktop kernel: [   37.360373] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Jun  1 18:21:03 chucknb-desktop kernel: [   37.360375] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Jun  1 18:21:03 chucknb-desktop kernel: [   37.365043] Driver 'sd' needs updating - please use bus_type methods
Jun  1 18:21:03 chucknb-desktop kernel: [   37.377023] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Jun  1 18:21:03 chucknb-desktop kernel: [   37.377036] sd 0:0:0:0: [sda] Write Protect is off
Jun  1 18:21:03 chucknb-desktop kernel: [   37.377047] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  1 18:21:03 chucknb-desktop kernel: [   37.377091] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Jun  1 18:21:03 chucknb-desktop kernel: [   37.377095] sd 0:0:0:0: [sda] Write Protect is off
Jun  1 18:21:03 chucknb-desktop kernel: [   37.377103] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  1 18:21:03 chucknb-desktop kernel: [   37.377107]  sda:<6>usbcore: registered new interface driver hiddev
Jun  1 18:21:03 chucknb-desktop kernel: [   37.381067]  sda1 sda2 sda3
Jun  1 18:21:03 chucknb-desktop kernel: [   37.390716] input: Microsoft Microsoft Notebook Receiver v2.0 as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.0/input/input2
Jun  1 18:21:03 chucknb-desktop kernel: [   37.395253] sd 0:0:0:0: [sda] Attached SCSI disk
Jun  1 18:21:03 chucknb-desktop kernel: [   37.395296] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jun  1 18:21:03 chucknb-desktop kernel: [   37.395303] sd 1:0:0:0: [sdb] Write Protect is off
Jun  1 18:21:03 chucknb-desktop kernel: [   37.395312] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  1 18:21:03 chucknb-desktop kernel: [   37.395340] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jun  1 18:21:03 chucknb-desktop kernel: [   37.395345] sd 1:0:0:0: [sdb] Write Protect is off
Jun  1 18:21:03 chucknb-desktop kernel: [   37.395353] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  1 18:21:03 chucknb-desktop kernel: [   37.395355]  sdb: sdb1 sdb2 sdb3
Jun  1 18:21:03 chucknb-desktop kernel: [   37.400462] sd 1:0:0:0: [sdb] Attached SCSI disk
Jun  1 18:21:03 chucknb-desktop kernel: [   37.400487] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
Jun  1 18:21:03 chucknb-desktop kernel: [   37.400493] sd 2:0:0:0: [sdc] Write Protect is off
Jun  1 18:21:03 chucknb-desktop kernel: [   37.400501] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  1 18:21:03 chucknb-desktop kernel: [   37.400519] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
Jun  1 18:21:03 chucknb-desktop kernel: [   37.400523] sd 2:0:0:0: [sdc] Write Protect is off
Jun  1 18:21:03 chucknb-desktop kernel: [   37.400531] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun  1 18:21:03 chucknb-desktop kernel: [   37.400533]  sdc: sdc1 sdc2 sdc3
Jun  1 18:21:03 chucknb-desktop kernel: [   37.409607] sd 2:0:0:0: [sdc] Attached SCSI disk
Jun  1 18:21:03 chucknb-desktop kernel: [   37.412898] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Notebook Receiver v2.0] on usb-0000:00:12.1-1
Jun  1 18:21:03 chucknb-desktop kernel: [   37.412911] usbcore: registered new interface driver usbhid
Jun  1 18:21:03 chucknb-desktop kernel: [   37.412914] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jun  1 18:21:03 chucknb-desktop kernel: [   37.413130] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun  1 18:21:03 chucknb-desktop kernel: [   37.413143] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jun  1 18:21:03 chucknb-desktop kernel: [   37.413157] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun  1 18:21:03 chucknb-desktop kernel: [   38.164757] ata6.00: ATAPI: ATAPI   DVD D  DH16D2P, HP55, max UDMA/33
Jun  1 18:21:03 chucknb-desktop kernel: [   38.164770] ata6.01: ATAPI: CR-4804TE, 2.6C, max MWDMA1
Jun  1 18:21:03 chucknb-desktop kernel: [   38.368539] ata6.00: configured for UDMA/33
Jun  1 18:21:03 chucknb-desktop kernel: [   38.552451] ata6.01: configured for MWDMA1
Jun  1 18:21:03 chucknb-desktop kernel: [   38.554260] scsi 5:0:0:0: CD-ROM            ATAPI    DVD D  DH16D2P   HP55 PQ: 0 ANSI: 5
Jun  1 18:21:03 chucknb-desktop kernel: [   38.554312] scsi 5:0:0:0: Attached scsi generic sg3 type 5
Jun  1 18:21:03 chucknb-desktop kernel: [   38.556716] scsi 5:0:1:0: CD-ROM            MITSUMI  CR-4804TE        2.6C PQ: 0 ANSI: 5
Jun  1 18:21:03 chucknb-desktop kernel: [   38.556748] scsi 5:0:1:0: Attached scsi generic sg4 type 5
Jun  1 18:21:03 chucknb-desktop kernel: [   38.557038] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 22 (level, low) -> IRQ 22
Jun  1 18:21:03 chucknb-desktop kernel: [   38.610101] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun  1 18:21:03 chucknb-desktop kernel: [   38.616004] sil680: 133MHz clock.
Jun  1 18:21:03 chucknb-desktop kernel: [   38.616027] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun  1 18:21:03 chucknb-desktop kernel: [   38.616233] scsi6 : pata_sil680
Jun  1 18:21:03 chucknb-desktop kernel: [   38.616278] scsi7 : pata_sil680
Jun  1 18:21:03 chucknb-desktop kernel: [   38.616293] ata7: PATA max UDMA/133 irq 21
Jun  1 18:21:03 chucknb-desktop kernel: [   38.616294] ata8: PATA max UDMA/133 irq 21
Jun  1 18:21:03 chucknb-desktop kernel: [   38.630960] usbcore: registered new interface driver libusual
Jun  1 18:21:03 chucknb-desktop kernel: [   38.633235] Initializing USB Mass Storage driver...
Jun  1 18:21:03 chucknb-desktop kernel: [   38.633290] scsi8 : SCSI emulation for USB Mass Storage devices
Jun  1 18:21:03 chucknb-desktop kernel: [   38.633348] scsi9 : SCSI emulation for USB Mass Storage devices
Jun  1 18:21:03 chucknb-desktop kernel: [   38.633375] usbcore: registered new interface driver usb-storage
Jun  1 18:21:03 chucknb-desktop kernel: [   38.633376] USB Mass Storage support registered.
Jun  1 18:21:03 chucknb-desktop kernel: [   38.963793] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun  1 18:21:03 chucknb-desktop kernel: [   38.963798] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun  1 18:21:03 chucknb-desktop kernel: [   38.968385] Driver 'sr' needs updating - please use bus_type methods
Jun  1 18:21:03 chucknb-desktop kernel: [   38.976021] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Jun  1 18:21:03 chucknb-desktop kernel: [   38.976026] Uniform CD-ROM driver Revision: 3.20
Jun  1 18:21:03 chucknb-desktop kernel: [   38.984112] sr1: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Jun  1 18:21:03 chucknb-desktop kernel: [   43.648347] scsi 9:0:0:0: Direct-Access     Kingston SNA-DC/U         1.08 PQ: 0 ANSI: 4
Jun  1 18:21:03 chucknb-desktop kernel: [   43.648513] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Jun  1 18:21:03 chucknb-desktop kernel: [   43.648987] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Jun  1 18:21:03 chucknb-desktop kernel: [   43.649232] sd 9:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Jun  1 18:21:03 chucknb-desktop kernel: [   43.649485] scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Jun  1 18:21:03 chucknb-desktop kernel: [   43.649857] sd 9:0:0:0: [sdd] Write Protect is off
Jun  1 18:21:03 chucknb-desktop kernel: [   43.649986] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Jun  1 18:21:03 chucknb-desktop kernel: [   43.650865] sd 9:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
Jun  1 18:21:03 chucknb-desktop kernel: [   43.651485] sd 9:0:0:0: [sdd] Write Protect is off
Jun  1 18:21:03 chucknb-desktop kernel: [   43.651493]  sdd: sdd1
Jun  1 18:21:03 chucknb-desktop kernel: [   43.789002] sd 9:0:0:0: [sdd] Attached SCSI disk
Jun  1 18:21:03 chucknb-desktop kernel: [   43.789033] sd 9:0:0:0: Attached scsi generic sg5 type 0
Jun  1 18:21:03 chucknb-desktop kernel: [   43.790779] sd 8:0:0:0: [sde] Attached SCSI removable disk
Jun  1 18:21:03 chucknb-desktop kernel: [   43.790813] sd 8:0:0:0: Attached scsi generic sg6 type 0
Jun  1 18:21:03 chucknb-desktop kernel: [   43.791853] sd 8:0:0:1: [sdf] Attached SCSI removable disk
Jun  1 18:21:03 chucknb-desktop kernel: [   43.791867] sd 8:0:0:1: Attached scsi generic sg7 type 0
Jun  1 18:21:03 chucknb-desktop kernel: [   43.792843] sd 8:0:0:2: [sdg] Attached SCSI removable disk
Jun  1 18:21:03 chucknb-desktop kernel: [   43.792858] sd 8:0:0:2: Attached scsi generic sg8 type 0
Jun  1 18:21:03 chucknb-desktop kernel: [   43.793842] sd 8:0:0:3: [sdh] Attached SCSI removable disk
Jun  1 18:21:03 chucknb-desktop kernel: [   43.793859] sd 8:0:0:3: Attached scsi generic sg9 type 0
Jun  1 18:21:03 chucknb-desktop kernel: [   44.390257] kjournald starting.  Commit interval 5 seconds
Jun  1 18:21:03 chucknb-desktop kernel: [   44.390269] EXT3-fs: mounted filesystem with ordered data mode.
Jun  1 18:21:03 chucknb-desktop kernel: [   56.994270] input: PC Speaker as /devices/platform/pcspkr/input/input3
Jun  1 18:21:03 chucknb-desktop kernel: [   57.111794] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun  1 18:21:03 chucknb-desktop kernel: [   57.162508] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun  1 18:21:03 chucknb-desktop kernel: [   57.193571] ACPI: WMI-Acer: Mapper loaded
Jun  1 18:21:03 chucknb-desktop kernel: [   57.213721] input: Power Button (FF) as /devices/virtual/input/input4
Jun  1 18:21:03 chucknb-desktop kernel: [   57.241924] ACPI: Power Button (FF) [PWRF]
Jun  1 18:21:03 chucknb-desktop kernel: [   57.242012] input: Power Button (CM) as /devices/virtual/input/input5
Jun  1 18:21:03 chucknb-desktop kernel: [   57.273883] ACPI: Power Button (CM) [PWRB]
Jun  1 18:21:03 chucknb-desktop kernel: [   57.286023] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Jun  1 18:21:03 chucknb-desktop kernel: [   57.482939] Linux video capture interface: v2.00
Jun  1 18:21:03 chucknb-desktop kernel: [   57.515357] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jun  1 18:21:03 chucknb-desktop kernel: [   57.527234] [fglrx] Maximum main memory to use for locked dma buffers: 1646 MBytes.
Jun  1 18:21:03 chucknb-desktop kernel: [   57.527261] [fglrx] ASYNCIO init succeed!
Jun  1 18:21:03 chucknb-desktop kernel: [   57.527406] [fglrx] PAT is enabled successfully!
Jun  1 18:21:03 chucknb-desktop kernel: [   57.527428] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Jun  1 18:21:03 chucknb-desktop kernel: [   57.605141] NET: Registered protocol family 23
Jun  1 18:21:03 chucknb-desktop kernel: [   57.708838] ivtv:  Start initialization, version 1.1.0
Jun  1 18:21:03 chucknb-desktop kernel: [   57.708906] ivtv0: Initializing card #0
Jun  1 18:21:03 chucknb-desktop kernel: [   57.708909] ivtv0: Autodetected Hauppauge card (cx23416 based)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.712015] ACPI: PCI Interrupt 0000:04:08.0[A] -> GSI 20 (level, low) -> IRQ 20
Jun  1 18:21:03 chucknb-desktop kernel: [   57.834766] tveeprom 1-0050: Hauppauge model 23552, rev D492, serial# 7967011
Jun  1 18:21:03 chucknb-desktop kernel: [   57.834770] tveeprom 1-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.834772] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.834774] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.834775] tveeprom 1-0050: audio processor is CX25843 (idx 37)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.834776] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.834777] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
Jun  1 18:21:03 chucknb-desktop kernel: [   57.834779] ivtv0: Autodetected WinTV PVR 500 (unit #1)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.893650] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.893671] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.893672] tuner 1-0043: type set to tda9887
Jun  1 18:21:03 chucknb-desktop kernel: [   57.898076] TEA5767 detected.
Jun  1 18:21:03 chucknb-desktop kernel: [   57.898077] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.898087] tea5767 1-0060: type set to Philips TEA5767HN FM Radio
Jun  1 18:21:03 chucknb-desktop kernel: [   57.898089] tuner 1-0060: type set to tea5767
Jun  1 18:21:03 chucknb-desktop kernel: [   57.898356] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Jun  1 18:21:03 chucknb-desktop kernel: [   57.964279] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.009976] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019297] tuner-simple 1-0061: type set to 57 (Philips FQ1236A MK4)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019301] tuner 1-0061: type set to Philips FQ1236A MK4
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019571] ivtv0: Registered device video0 for encoder MPG (4096 kB)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019582] ivtv0: Registered device video32 for encoder YUV (2048 kB)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019592] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019601] ivtv0: Registered device video24 for encoder PCM (320 kB)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019611] ivtv0: Registered device radio0 for encoder radio
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019613] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019660] ivtv1: Initializing card #1
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019662] ivtv1: Autodetected Hauppauge card (cx23416 based)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.019978] ACPI: PCI Interrupt 0000:04:09.0[A] -> GSI 21 (level, low) -> IRQ 21
Jun  1 18:21:03 chucknb-desktop kernel: [   58.026281] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.026292] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.026293] tuner 2-0043: type set to tda9887
Jun  1 18:21:03 chucknb-desktop kernel: [   58.029639] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.046677] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.046943] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.071773] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Jun  1 18:21:03 chucknb-desktop kernel: [   58.094975] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Jun  1 18:21:03 chucknb-desktop kernel: [   58.126937] ACPI: PCI Interrupt 0000:01:05.1[B] -> GSI 19 (level, low) -> IRQ 19
Jun  1 18:21:03 chucknb-desktop kernel: [   58.129964] tveeprom 2-0050: Hauppauge model 23552, rev D492, serial# 7967011
Jun  1 18:21:03 chucknb-desktop kernel: [   58.129968] tveeprom 2-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.129969] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.129971] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.129973] tveeprom 2-0050: audio processor is CX25843 (idx 37)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.129974] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.129975] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
Jun  1 18:21:03 chucknb-desktop kernel: [   58.129977] ivtv1: Correcting tveeprom data: no radio present on second unit
Jun  1 18:21:03 chucknb-desktop kernel: [   58.129978] ivtv1: Autodetected WinTV PVR 500 (unit #2)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.142221] tuner-simple 2-0061: type set to 57 (Philips FQ1236A MK4)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.142225] tuner 2-0061: type set to Philips FQ1236A MK4
Jun  1 18:21:03 chucknb-desktop kernel: [   58.142425] ivtv1: Registered device video1 for encoder MPG (4096 kB)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.142435] ivtv1: Registered device video33 for encoder YUV (2048 kB)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.142446] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.142457] ivtv1: Registered device video25 for encoder PCM (320 kB)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.142459] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
Jun  1 18:21:03 chucknb-desktop kernel: [   58.142472] ivtv:  End initialization
Jun  1 18:21:03 chucknb-desktop kernel: [   58.360750] lp: driver loaded but no devices found
Jun  1 18:21:03 chucknb-desktop kernel: [   58.964734] EXT3 FS on sdd1, internal journal
Jun  1 18:21:03 chucknb-desktop kernel: [   59.806969] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun  1 18:21:03 chucknb-desktop kernel: [   60.187762] NET: Registered protocol family 17
Jun  1 18:21:03 chucknb-desktop kernel: [   63.423816] No dock devices found.
Jun  1 18:21:03 chucknb-desktop kernel: [   64.730217] ppdev: user-space parallel port driver
Jun  1 18:21:03 chucknb-desktop kernel: [   64.954260] audit(1275430863.701:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6275 profile="/usr/sbin/cupsd" namespace="default"
Jun  1 18:21:03 chucknb-desktop kernel: [   65.087594] RPC: Registered udp transport module.
Jun  1 18:21:03 chucknb-desktop kernel: [   65.087597] RPC: Registered tcp transport module.
Jun  1 18:21:03 chucknb-desktop kernel: [   65.170930] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Jun  1 18:21:04 chucknb-desktop kernel: [   65.252285] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jun  1 18:21:04 chucknb-desktop kernel: [   65.263585] NFSD: starting 90-second grace period
Jun  1 18:21:05 chucknb-desktop dhcdbd: Started up.
Jun  1 18:21:06 chucknb-desktop kernel: [   67.610621] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Jun  1 18:21:06 chucknb-desktop kernel: [   67.808235] ivtv0: Encoder revision: 0x02060039
Jun  1 18:21:10 chucknb-desktop kernel: [   71.678486] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Jun  1 18:21:11 chucknb-desktop kernel: [   72.746806] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Jun  1 18:21:11 chucknb-desktop kernel: [   72.943332] ivtv1: Encoder revision: 0x02060039
Jun  1 18:21:15 chucknb-desktop kernel: [   76.529270] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Jun  1 18:21:16 chucknb-desktop kernel: [   77.473222] Bluetooth: Core ver 2.11
Jun  1 18:21:16 chucknb-desktop kernel: [   77.473300] NET: Registered protocol family 31
Jun  1 18:21:16 chucknb-desktop kernel: [   77.473301] Bluetooth: HCI device and connection manager initialized
Jun  1 18:21:16 chucknb-desktop kernel: [   77.473304] Bluetooth: HCI socket layer initialized
Jun  1 18:21:16 chucknb-desktop kernel: [   77.494112] Bluetooth: L2CAP ver 2.9
Jun  1 18:21:16 chucknb-desktop kernel: [   77.494117] Bluetooth: L2CAP socket layer initialized
Jun  1 18:21:16 chucknb-desktop kernel: [   77.633769] Bluetooth: RFCOMM socket layer initialized
Jun  1 18:21:16 chucknb-desktop kernel: [   77.633782] Bluetooth: RFCOMM TTY layer initialized
Jun  1 18:21:16 chucknb-desktop kernel: [   77.633783] Bluetooth: RFCOMM ver 1.8
Jun  1 18:21:17 chucknb-desktop kernel: [   78.893793] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 18
Jun  1 18:21:17 chucknb-desktop kernel: [   79.059247] tg3: eth0: Link is up at 100 Mbps, full duplex.
Jun  1 18:21:17 chucknb-desktop kernel: [   79.059256] tg3: eth0: Flow control is off for TX and off for RX.
Jun  1 18:21:17 chucknb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun  1 18:21:18 chucknb-desktop kernel: [   79.779132] [fglrx] GART Table is not in FRAME_BUFFER range 
Jun  1 18:21:18 chucknb-desktop kernel: [   79.779145] [fglrx] Reserve Block - 0 offset =  0X17ffc000 length = 0X4000
Jun  1 18:21:18 chucknb-desktop kernel: [   79.779147] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Jun  1 18:21:18 chucknb-desktop kernel: [   80.135744] [fglrx] interrupt source ff00002f successfully enabled
Jun  1 18:21:18 chucknb-desktop kernel: [   80.135754] [fglrx] enable ID = 0x00000006
Jun  1 18:21:18 chucknb-desktop kernel: [   80.135761] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002f
Jun  1 18:21:19 chucknb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun  1 18:21:19 chucknb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun  1 18:21:19 chucknb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  1 18:21:19 chucknb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  1 18:21:19 chucknb-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun  1 18:21:21 chucknb-desktop kernel: [   82.488878] NET: Registered protocol family 10
Jun  1 18:21:21 chucknb-desktop kernel: [   82.489069] lo: Disabled Privacy Extensions
Jun  1 18:21:25 chucknb-desktop kernel: [   87.078155] hda-intel: Invalid position buffer, using LPIB read method instead.
Jun  1 18:41:02 chucknb-desktop -- MARK --
```

---

### Post by uOpt on 2010-06-01
Oh, you are using the ATI drivers?

Good luck :)

---

### Post by Moozillaaa on 2010-06-01
I booted XP, and XP partition was OK.

I rebooted Ubuntu, and it's back to how it is supposed to be. I am bewildered. If I did not take the screenshot post #1, I would not believe it.

Even deleted 'trashed' files, from last week, were BACK on the desktop. :confused:

But everything is back, including the FF browse library.

The browse history tho', for the last hour, including this thread, are not in this computer.

I do not know where to look in log files for this answer...

???

---

### Post by Moozillaaa on 2010-06-01
Should the ATI accelerated graphics driver be disabled?

---

