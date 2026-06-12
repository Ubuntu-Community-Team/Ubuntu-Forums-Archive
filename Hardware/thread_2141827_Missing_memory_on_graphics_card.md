---
title: "Missing memory on graphics card"
date: 2013-05-03
forum: Hardware
---

### Post by Sworddragon on 2013-05-03
My graphics card is a GeForce 8600 GT and I'm using nvidia-313-updates 313.30-0ubuntu1. On the POST screen my graphics card is showing that it is owning 512 MiB of memory. lspci is only showing 256 MiB:

```
sworddragon@ubuntu:~$ lspci -v -s 01:00.0
01:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Device 7377:0000
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at b800 [size=128]
	[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia

```

Has somebody an idea about this?

---

### Post by matt_symes on 2013-05-03
Hi

> **Sworddragon said:**
> My graphics card is a GeForce 8600 GT and I'm using nvidia-313-updates 313.30-0ubuntu1. On the POST screen my graphics card is showing that it is owning 512 MiB of memory. lspci is only showing 256 MiB:

```
sworddragon@ubuntu:~$ lspci -v -s 01:00.0
01:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Device 7377:0000
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at b800 [size=128]
    [virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

```

Has somebody an idea about this?

According this this...

[http://www.nvidia.com/object/geforce_8600.html](http://www.nvidia.com/object/geforce_8600.html)

...the card has 256MB of onboard video ram. 

Is it possible that the other 256MB memory is system memory that it has grabbed ?

If you look in the file

```
/var/log/dmesg
```

it should tell you.

I would do something like this to narrow it down.

```
grep -C5 "00:01.0" /var/log/dmesg
```

Kind regards

---

### Post by Sworddragon on 2013-05-04
> **matt_symes said:**
> According this this...

[http://www.nvidia.com/object/geforce_8600.html](http://www.nvidia.com/object/geforce_8600.html)

...the card has 256MB of onboard video ram. 

Is it possible that the other 256MB memory is system memory that it has grabbed ?

Often the vendors are modifying the grahics cards so 512 MiB wouldn't be unlikely. From my 16384 MiB there are 335 MiB reserved by the kernel. Maybe it does already contain such shared memory but I have made a look on the NVIDIA control panel and found this: "Total Dedicated Memory: 512 MB". I even doubt that the POST screen is showing 256 MiB of dedicated memory and 256 MiB of shared memory as 512 MiB.


> **matt_symes said:**
> If you look in the file

```
/var/log/dmesg
```

it should tell you.

I would do something like this to narrow it down.

```
grep -C5 "00:01.0" /var/log/dmesg
```

Here is the output:

```
sworddragon@ubuntu:~$ dmesg | grep -C5 '00:01.0'
[    0.284181] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.284225] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.284268] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.284311] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.284357] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.284443] pci 0000:01:00.0: [10de:0402] type 00 class 0x030000
[    0.284452] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.284461] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.284470] pci 0000:01:00.0: reg 1c: [mem 0xfa000000-0xfbffffff 64bit]
[    0.284477] pci 0000:01:00.0: reg 24: [io  0xb800-0xb87f]
[    0.284483] pci 0000:01:00.0: reg 30: [mem 0xfe9e0000-0xfe9fffff pref]
[    0.291399] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.291405] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    0.291407] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfe9fffff]
[    0.291410] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.291455] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
--
[    0.317056] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.317187] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.317194] acpi root: \_SB_.PCI0 notify handler is installed
[    0.317220] Found 1 acpi root devices
[    0.317293] ACPI: No dock devices found.
[    0.317374] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.317378] vgaarb: loaded
[    0.317379] vgaarb: bridge control possible 0000:01:00.0
[    0.317507] SCSI subsystem initialized
[    0.317510] ACPI: bus type ATA registered
[    0.317615] libata version 3.00 loaded.
[    0.317628] ACPI: bus type USB registered
[    0.317643] usbcore: registered new interface driver usbfs
--
[    0.342052] TCP: Hash tables configured (established 131072 bind 65536)
[    0.342090] TCP: reno registered
[    0.342106] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.342199] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.342339] NET: Registered protocol family 1
[    0.763706] pci 0000:01:00.0: Boot video device
[    0.763805] PCI: CLS 64 bytes, default 64
[    0.763846] Trying to unpack rootfs image as initramfs...
[    1.014338] Freeing initrd memory: 18940k freed
[    1.020097] PCI-DMA: Disabling AGP.
[    1.020231] PCI-DMA: aperture base @ c4000000 size 65536 KB
--
[   20.474599] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   20.853663] r8169 0000:02:00.0 eth0: link up
[   20.853681] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.494169] nvidia: module license 'NVIDIA' taints kernel.
[   22.494178] Disabling lock debugging due to kernel taint
[   22.510790] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.511069] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  313.30  Wed Mar 27 16:56:45 PDT 2013
[   23.493894] init: failsafe main process (967) killed by TERM signal
[   25.740584] ISO 9660 Extensions: Microsoft Joliet Level 3
[   25.884522] vboxdrv: Found 6 processor cores.
[   25.884887] vboxdrv: fAsync=0 offMin=0x6ff offMax=0x5767

```

---

### Post by matt_symes on 2013-05-04
Hi

This is not an SLI setup is it ?

Not much in the logs there. You may want to post the entire output of dmesg.

Kind regards

---

### Post by robert shearer on 2013-05-04
See 'lshw and lspci lie' in this thread...;)
[http://ubuntuforums.org/showthread.php?t=2106641&highlight=](http://ubuntuforums.org/showthread.php?t=2106641&highlight=)

---

### Post by matt_symes on 2013-05-04
Hi

> **robert shearer said:**
> See 'lshw and lspci lie' in this thread...;)
[http://ubuntuforums.org/showthread.php?t=2106641&highlight=](http://ubuntuforums.org/showthread.php?t=2106641&highlight=)

LOL. :lolflag:

Thanks for posting that robert shearer.

@OP. What does dmesg say ?

Kind regards

---

### Post by Sworddragon on 2013-05-04
> **matt_symes said:**
> This is not an SLI setup is it ?

It is a single graphics card.


> **matt_symes said:**
> Not much in the logs there. You may want to post the entire output of dmesg.

```
sworddragon@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.9.0-0-generic (buildd@akateko) (gcc version 4.8.0 (Ubuntu 4.8.0-4ubuntu3) ) #4-Ubuntu SMP Thu May 2 21:43:59 UTC 2013 (Ubuntu 3.9.0-0.4-generic 3.9.0)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.9.0-0-generic root=UUID=05338ff8-a226-421b-90a4-1dd45199f783 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e6000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cff9ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cffa0000-0x00000000cffaffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cffb0000-0x00000000cffdffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cffe0000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000042fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./960GM/U3S3 FX, BIOS P1.20 05/21/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x430000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000430000000 aka 17152M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcffa0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01f95000, 0x01f95fff] PGTABLE
[    0.000000] BRK [0x01f96000, 0x01f96fff] PGTABLE
[    0.000000] BRK [0x01f97000, 0x01f97fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42fe00000-0x42fffffff]
[    0.000000]  [mem 0x42fe00000-0x42fffffff] page 2M
[    0.000000] BRK [0x01f98000, 0x01f98fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42c000000-0x42fdfffff]
[    0.000000]  [mem 0x42c000000-0x42fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x42bffffff]
[    0.000000]  [mem 0x400000000-0x42bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcff9ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcff9ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35af2000-0x36d70fff]
[    0.000000] ACPI: RSDP 00000000000fa700 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cffa0000 00040 (v01 052112 RSDT1357 20120521 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cffa0200 00084 (v01 A_M_I  OEMFACP  12000601 MSFT 00000097)
[    0.000000] ACPI BIOS Bug: Warning: Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20130117/tbfadt-599)
[    0.000000] ACPI: DSDT 00000000cffa0460 08AFD (v01  AS618 AS618112 00000112 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cffb0000 00040
[    0.000000] ACPI: APIC 00000000cffa0390 0008C (v01 052112 APIC1357 20120521 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cffa0420 0003C (v01 052112 OEMMCFG  20120521 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cffb0040 00072 (v01 052112 OEMB1357 20120521 MSFT 00000097)
[    0.000000] ACPI: AAFT 00000000cffaa460 0002E (v01 052112 OEMAAFT  20120521 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cffaa490 00038 (v01 052112 OEMHPET  20120521 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cffaa4d0 00E10 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000042fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x42fffffff]
[    0.000000]   NODE_DATA [mem 0x42fff9000-0x42fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0010bfffff] PMD -> [ffff88041f600000-ffff88042f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x42fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xcff9ffff]
[    0.000000]   node   0: [mem 0x100000000-0x42fffffff]
[    0.000000] On node 0 totalpages: 4194110
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13247 pages used for memmap
[    0.000000]   DMA32 zone: 847776 pages, LIFO batch:31
[    0.000000]   Normal zone: 52224 pages used for memmap
[    0.000000]   Normal zone: 3342336 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x06] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 6, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cffa0000 - 00000000cffb0000
[    0.000000] PM: Registered nosave memory: 00000000cffb0000 - 00000000cffe0000
[    0.000000] PM: Registered nosave memory: 00000000cffe0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] e820: [mem 0xd0000000-0xffefffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88042fc00000 s85824 r8192 d20672 u262144
[    0.000000] pcpu-alloc: s85824 r8192 d20672 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4128554
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.9.0-0-generic root=UUID=05338ff8-a226-421b-90a4-1dd45199f783 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 16346532k/17563648k available (7033k kernel code, 787208k absent, 429908k reserved, 6234k data, 1268k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.004000] tsc: Fast TSC calibration using PIT
[    0.008000] tsc: Detected 2705.365 MHz processor
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5410.73 BogoMIPS (lpj=10821460)
[    0.000008] pid_max: default: 32768 minimum: 301
[    0.000033] Security Framework initialized
[    0.000046] AppArmor: AppArmor initialized
[    0.000048] Yama: becoming mindful.
[    0.000920] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.005477] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.007602] Mount-cache hash table entries: 256
[    0.007782] Initializing cgroup subsys cpuacct
[    0.007784] Initializing cgroup subsys memory
[    0.007795] Initializing cgroup subsys devices
[    0.007797] Initializing cgroup subsys freezer
[    0.007800] Initializing cgroup subsys blkio
[    0.007802] Initializing cgroup subsys perf_event
[    0.007805] Initializing cgroup subsys hugetlb
[    0.007828] tseg: 0000000000
[    0.007834] CPU: Physical Processor ID: 0
[    0.007836] CPU: Processor Core ID: 0
[    0.007838] mce: CPU supports 6 MCE banks
[    0.007844] LVT offset 0 assigned for vector 0xf9
[    0.007850] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.007850] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
[    0.007850] tlb_flushall_shift: 4
[    0.007919] Freeing SMP alternatives: 24k freed
[    0.009188] ACPI: Core revision 20130117
[    0.011133] ACPI: All ACPI Tables successfully acquired
[    0.018130] ftrace: allocating 26861 entries in 105 pages
[    0.027969] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067709] smpboot: CPU0: AMD Phenom(tm) II X6 1045T Processor (fam: 10, model: 0a, stepping: 00)
[    0.175814] Performance Events: AMD PMU driver.
[    0.175819] ... version:                0
[    0.175820] ... bit width:              48
[    0.175822] ... generic registers:      4
[    0.175823] ... value mask:             0000ffffffffffff
[    0.175825] ... max period:             00007fffffffffff
[    0.175827] ... fixed-purpose events:   0
[    0.175828] ... event mask:             000000000000000f
[    0.176681] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.176754] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5
[    0.242261] Brought up 6 CPUs
[    0.242265] smpboot: Total of 6 processors activated (32464.38 BogoMIPS)
[    0.249489] devtmpfs: initialized
[    0.251381] EVM: security.selinux
[    0.251384] EVM: security.SMACK64
[    0.251385] EVM: security.capability
[    0.251472] PM: Registering ACPI NVS region [mem 0xcffb0000-0xcffdffff] (196608 bytes)
[    0.252234] regulator-dummy: no parameters
[    0.252284] NET: Registered protocol family 16
[    0.252358] node 0 link 0: io port [1000, ffffff]
[    0.252360] TOM: 00000000d0000000 aka 3328M
[    0.252363] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.252365] node 0 link 0: mmio [a0000, bffff]
[    0.252366] node 0 link 0: mmio [d0000000, dfffffff]
[    0.252368] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.252370] node 0 link 0: mmio [f0000000, ffafffff]
[    0.252371] TOM2: 0000000430000000 aka 17152M
[    0.252373] bus: [bus 00-1f] on node 0 link 0
[    0.252374] bus: 00 [io  0x0000-0xffff]
[    0.252375] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.252376] bus: 00 [mem 0xd0000000-0xdfffffff]
[    0.252377] bus: 00 [mem 0xf0000000-0xffffffff]
[    0.252378] bus: 00 [mem 0x430000000-0xfcffffffff]
[    0.252468] ACPI: bus type PCI registered
[    0.252524] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.252528] PCI: not using MMCONFIG
[    0.252530] PCI: Using configuration type 1 for base access
[    0.252532] PCI: Using configuration type 1 for extended access
[    0.252831] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.252833] mtrr: probably your BIOS does not setup all CPUs.
[    0.252835] mtrr: corrected configuration.
[    0.253503] bio: create slab <bio-0> at 0
[    0.253587] ACPI: Added _OSI(Module Device)
[    0.253589] ACPI: Added _OSI(Processor Device)
[    0.253591] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.253593] ACPI: Added _OSI(Processor Aggregator Device)
[    0.254205] ACPI: EC: Look up EC in DSDT
[    0.255156] ACPI: Executed 3 blocks of module-level executable AML code
[    0.257388] ACPI: Interpreter enabled
[    0.257396] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130117/hwxface-568)
[    0.257406] ACPI: (supports S0 S1 S3 S4 S5)
[    0.257408] ACPI: Using IOAPIC for interrupt routing
[    0.257423] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.257980] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.265448] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.282776] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.282960] PCI host bridge to bus 0000:00
[    0.282964] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.282967] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.282969] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.282972] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.282974] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.282976] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xdfffffff]
[    0.282979] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.282989] pci 0000:00:00.0: [1022:9600] type 00 class 0x060000
[    0.283060] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
[    0.283090] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.283104] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.283130] pci 0000:00:05.0: [1022:9605] type 01 class 0x060400
[    0.283158] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.283173] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.283195] pci 0000:00:06.0: [1022:9606] type 01 class 0x060400
[    0.283223] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.283238] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.283260] pci 0000:00:07.0: [1022:9607] type 01 class 0x060400
[    0.283288] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.283304] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.283341] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
[    0.283359] pci 0000:00:11.0: reg 10: [io  0xa000-0xa007]
[    0.283367] pci 0000:00:11.0: reg 14: [io  0x9000-0x9003]
[    0.283376] pci 0000:00:11.0: reg 18: [io  0x8000-0x8007]
[    0.283384] pci 0000:00:11.0: reg 1c: [io  0x7000-0x7003]
[    0.283393] pci 0000:00:11.0: reg 20: [io  0x6000-0x600f]
[    0.283401] pci 0000:00:11.0: reg 24: [mem 0xf9fffc00-0xf9ffffff]
[    0.283420] pci 0000:00:11.0: set SATA to AHCI mode
[    0.283498] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.283511] pci 0000:00:12.0: reg 10: [mem 0xf9ffe000-0xf9ffefff]
[    0.283583] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.283606] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.283618] pci 0000:00:12.1: reg 10: [mem 0xf9ffd000-0xf9ffdfff]
[    0.283694] pci 0000:00:12.1: System wakeup disabled by ACPI
[    0.283723] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.283740] pci 0000:00:12.2: reg 10: [mem 0xf9fff800-0xf9fff8ff]
[    0.283817] pci 0000:00:12.2: supports D1 D2
[    0.283818] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.283848] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.283876] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.283888] pci 0000:00:13.0: reg 10: [mem 0xf9ffc000-0xf9ffcfff]
[    0.283963] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.283986] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.283998] pci 0000:00:13.1: reg 10: [mem 0xf9ffb000-0xf9ffbfff]
[    0.284074] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.284102] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.284119] pci 0000:00:13.2: reg 10: [mem 0xf9fff400-0xf9fff4ff]
[    0.284200] pci 0000:00:13.2: supports D1 D2
[    0.284202] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.284233] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.284264] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.284381] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.284396] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.284404] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.284413] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.284421] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.284429] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.284506] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.284526] pci 0000:00:14.2: reg 10: [mem 0xf9ff4000-0xf9ff7fff 64bit]
[    0.284587] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.284609] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.284632] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.284729] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.284779] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.284801] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.284813] pci 0000:00:14.5: reg 10: [mem 0xf9ffa000-0xf9ffafff]
[    0.284891] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.284916] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.284961] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.285004] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.285048] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.285094] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.285182] pci 0000:01:00.0: [10de:0402] type 00 class 0x030000
[    0.285191] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.285200] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.285209] pci 0000:01:00.0: reg 1c: [mem 0xfa000000-0xfbffffff 64bit]
[    0.285215] pci 0000:01:00.0: reg 24: [io  0xb800-0xb87f]
[    0.285222] pci 0000:01:00.0: reg 30: [mem 0xfe9e0000-0xfe9fffff pref]
[    0.292164] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.292171] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    0.292174] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfe9fffff]
[    0.292177] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.292221] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.292234] pci 0000:02:00.0: reg 10: [io  0xc800-0xc8ff]
[    0.292253] pci 0000:02:00.0: reg 18: [mem 0xf8fff000-0xf8ffffff 64bit pref]
[    0.292265] pci 0000:02:00.0: reg 20: [mem 0xf8ff8000-0xf8ffbfff 64bit pref]
[    0.292318] pci 0000:02:00.0: supports D1 D2
[    0.292319] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.300177] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.300183] pci 0000:00:05.0:   bridge window [io  0xc000-0xcfff]
[    0.300187] pci 0000:00:05.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.300233] pci 0000:03:00.0: [1b21:0611] type 00 class 0x010185
[    0.300244] pci 0000:03:00.0: reg 10: [io  0xe800-0xe807]
[    0.300251] pci 0000:03:00.0: reg 14: [io  0xe400-0xe403]
[    0.300258] pci 0000:03:00.0: reg 18: [io  0xe000-0xe007]
[    0.300265] pci 0000:03:00.0: reg 1c: [io  0xd800-0xd803]
[    0.300272] pci 0000:03:00.0: reg 20: [io  0xd400-0xd40f]
[    0.300279] pci 0000:03:00.0: reg 24: [mem 0xfeaffc00-0xfeaffdff]
[    0.308185] pci 0000:00:06.0: PCI bridge to [bus 03]
[    0.308191] pci 0000:00:06.0:   bridge window [io  0xd000-0xefff]
[    0.308193] pci 0000:00:06.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.308238] pci 0000:04:00.0: [1b6f:7023] type 00 class 0x0c0330
[    0.308253] pci 0000:04:00.0: reg 10: [mem 0xfebf8000-0xfebfffff 64bit]
[    0.308317] pci 0000:04:00.0: supports D1 D2
[    0.308318] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.316195] pci 0000:00:07.0: PCI bridge to [bus 04]
[    0.316203] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.316273] pci 0000:00:14.4: PCI bridge to [bus 05] (subtractive decode)
[    0.316282] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.316284] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.316285] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.316287] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.316288] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.316290] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.316381] acpi PNP0A03:00: Requesting ACPI _OSC control (0x1d)
[    0.316552] acpi PNP0A03:00: ACPI _OSC control (0x18) granted
[    0.317627] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[    0.317669] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.317705] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 12 14 15)
[    0.317741] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.317776] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 10 11 12 14 15) *0, disabled.
[    0.317812] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 10 11 12 14 15) *0, disabled.
[    0.317848] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 *11 12 14 15)
[    0.317888] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.318019] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.318026] acpi root: \_SB_.PCI0 notify handler is installed
[    0.318052] Found 1 acpi root devices
[    0.318126] ACPI: No dock devices found.
[    0.318208] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.318211] vgaarb: loaded
[    0.318212] vgaarb: bridge control possible 0000:01:00.0
[    0.318339] SCSI subsystem initialized
[    0.318342] ACPI: bus type ATA registered
[    0.318446] libata version 3.00 loaded.
[    0.318459] ACPI: bus type USB registered
[    0.318475] usbcore: registered new interface driver usbfs
[    0.318483] usbcore: registered new interface driver hub
[    0.318512] usbcore: registered new device driver usb
[    0.318610] PCI: Using ACPI for IRQ routing
[    0.326599] PCI: pci_cache_line_size set to 64 bytes
[    0.326650] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.326652] e820: reserve RAM buffer [mem 0xcffa0000-0xcfffffff]
[    0.326713] NetLabel: Initializing
[    0.326715] NetLabel:  domain hash size = 128
[    0.326717] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.326725] NetLabel:  unlabeled traffic allowed by default
[    0.326780] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.326784] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.328810] Switching to clocksource hpet
[    0.333118] AppArmor: AppArmor Filesystem Enabled
[    0.333139] pnp: PnP ACPI init
[    0.333147] ACPI: bus type PNP registered
[    0.333253] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.333283] pnp 00:01: [dma 4]
[    0.333296] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.333320] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.333337] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.333354] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.333592] pnp 00:05: [dma 3]
[    0.333662] pnp 00:05: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.333727] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.333796] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.333800] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.333803] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.333941] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.333944] system 00:08: [io  0x040b] has been reserved
[    0.333946] system 00:08: [io  0x04d6] has been reserved
[    0.333949] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.333954] system 00:08: [io  0x0c14] has been reserved
[    0.333956] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.333959] system 00:08: [io  0x0c52] has been reserved
[    0.333961] system 00:08: [io  0x0c6c] has been reserved
[    0.333963] system 00:08: [io  0x0c6f] has been reserved
[    0.333966] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.333968] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.333970] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.333973] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.333975] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.333977] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.333980] system 00:08: [io  0x0b00-0x0b0f] has been reserved
[    0.333982] system 00:08: [io  0x0b20-0x0b3f] has been reserved
[    0.333985] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.333987] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.333989] system 00:08: [io  0xfe00-0xfefe] has been reserved
[    0.333992] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.333995] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.333998] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.334136] pnp 00:09: [dma 0 disabled]
[    0.334176] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.334229] system 00:0a: [io  0x0290-0x029f] has been reserved
[    0.334232] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.334271] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.334274] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.335188] pnp 00:0c: [Firmware Bug]: [mem 0x00000000-0xffffffffffffffff disabled] covers only part of AMD MMCONFIG area [mem 0xe0000000-0xefffffff]; adding more reservations
[    0.335224] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.335228] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.335231] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.335234] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.335238] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.335334] pnp: PnP ACPI: found 13 devices
[    0.335336] ACPI: bus type PNP unregistered
[    0.341449] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.341453] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    0.341457] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfe9fffff]
[    0.341460] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.341464] pci 0000:00:05.0: PCI bridge to [bus 02]
[    0.341467] pci 0000:00:05.0:   bridge window [io  0xc000-0xcfff]
[    0.341471] pci 0000:00:05.0:   bridge window [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.341475] pci 0000:00:06.0: PCI bridge to [bus 03]
[    0.341477] pci 0000:00:06.0:   bridge window [io  0xd000-0xefff]
[    0.341480] pci 0000:00:06.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.341485] pci 0000:00:07.0: PCI bridge to [bus 04]
[    0.341488] pci 0000:00:07.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.341492] pci 0000:00:14.4: PCI bridge to [bus 05]
[    0.341697] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.341699] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.341701] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.341702] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.341704] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.341705] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.341707] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.341708] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfe9fffff]
[    0.341710] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.341711] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.341713] pci_bus 0000:02: resource 2 [mem 0xf8f00000-0xf8ffffff 64bit pref]
[    0.341714] pci_bus 0000:03: resource 0 [io  0xd000-0xefff]
[    0.341716] pci_bus 0000:03: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.341718] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.341719] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.341721] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.341722] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.341724] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.341725] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.341727] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.341756] NET: Registered protocol family 2
[    0.341988] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.342582] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.342857] TCP: Hash tables configured (established 131072 bind 65536)
[    0.342895] TCP: reno registered
[    0.342911] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.343005] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.343144] NET: Registered protocol family 1
[    0.765650] pci 0000:01:00.0: Boot video device
[    0.765749] PCI: CLS 64 bytes, default 64
[    0.765791] Trying to unpack rootfs image as initramfs...
[    1.016997] Freeing initrd memory: 18940k freed
[    1.022682] PCI-DMA: Disabling AGP.
[    1.022818] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.022821] PCI-DMA: using GART IOMMU.
[    1.022824] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.026492] LVT offset 1 assigned for vector 0x400
[    1.026509] IBS: LVT offset 1 assigned
[    1.026560] perf: AMD IBS detected (0x0000001f)
[    1.026584] Scanning for low memory corruption every 60 seconds
[    1.026788] Initialise module verification
[    1.026842] audit: initializing netlink socket (disabled)
[    1.026868] type=2000 audit(1367686398.916:1): initialized
[    1.048656] bounce pool size: 64 pages
[    1.048667] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.050490] VFS: Disk quotas dquot_6.5.2
[    1.050530] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.050973] fuse init (API version 7.21)
[    1.051035] msgmni has been set to 32092
[    1.051544] Key type asymmetric registered
[    1.051548] Asymmetric key parser 'x509' registered
[    1.051576] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.051609] io scheduler noop registered
[    1.051611] io scheduler deadline registered (default)
[    1.051616] io scheduler cfq registered
[    1.051739] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.051789] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    1.051837] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    1.051883] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
[    1.051922] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.051934] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.052012] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.052018] ACPI: Power Button [PWRB]
[    1.052043] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.052046] ACPI: Power Button [PWRF]
[    1.052089] ACPI: acpi_idle registered with cpuidle
[    1.054333] GHES: HEST is not enabled!
[    1.054439] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.074932] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.076053] Linux agpgart interface v0.103
[    1.077118] brd: module loaded
[    1.077679] loop: module loaded
[    1.077985] libphy: Fixed MDIO Bus: probed
[    1.078044] tun: Universal TUN/TAP device driver, 1.6
[    1.078045] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.078103] PPP generic driver version 2.4.2
[    1.078163] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.078165] ehci-pci: EHCI PCI platform driver
[    1.078250] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.078261] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.078269] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.078281] ehci-pci 0000:00:12.2: debug port 1
[    1.078318] ehci-pci 0000:00:12.2: irq 17, io mem 0xf9fff800
[    1.089941] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.090000] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.090011] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.090021] usb usb1: Product: EHCI Host Controller
[    1.090039] usb usb1: Manufacturer: Linux 3.9.0-0-generic ehci_hcd
[    1.090041] usb usb1: SerialNumber: 0000:00:12.2
[    1.090213] hub 1-0:1.0: USB hub found
[    1.090218] hub 1-0:1.0: 6 ports detected
[    1.090410] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.090417] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.090421] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.090435] ehci-pci 0000:00:13.2: debug port 1
[    1.090469] ehci-pci 0000:00:13.2: irq 19, io mem 0xf9fff400
[    1.101963] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.102017] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.102027] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.102038] usb usb2: Product: EHCI Host Controller
[    1.102046] usb usb2: Manufacturer: Linux 3.9.0-0-generic ehci_hcd
[    1.102054] usb usb2: SerialNumber: 0000:00:13.2
[    1.102238] hub 2-0:1.0: USB hub found
[    1.102242] hub 2-0:1.0: 6 ports detected
[    1.102351] ehci-platform: EHCI generic platform driver
[    1.102368] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.102456] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.102464] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.102488] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf9ffe000
[    1.162015] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.162019] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.162022] usb usb3: Product: OHCI Host Controller
[    1.162024] usb usb3: Manufacturer: Linux 3.9.0-0-generic ohci_hcd
[    1.162026] usb usb3: SerialNumber: 0000:00:12.0
[    1.162121] hub 3-0:1.0: USB hub found
[    1.162128] hub 3-0:1.0: 3 ports detected
[    1.162304] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.162310] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.162325] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf9ffd000
[    1.222084] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.222088] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.222091] usb usb4: Product: OHCI Host Controller
[    1.222092] usb usb4: Manufacturer: Linux 3.9.0-0-generic ohci_hcd
[    1.222095] usb usb4: SerialNumber: 0000:00:12.1
[    1.222193] hub 4-0:1.0: USB hub found
[    1.222200] hub 4-0:1.0: 3 ports detected
[    1.222383] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.222389] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.222412] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf9ffc000
[    1.282163] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.282167] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.282169] usb usb5: Product: OHCI Host Controller
[    1.282171] usb usb5: Manufacturer: Linux 3.9.0-0-generic ohci_hcd
[    1.282173] usb usb5: SerialNumber: 0000:00:13.0
[    1.282265] hub 5-0:1.0: USB hub found
[    1.282272] hub 5-0:1.0: 3 ports detected
[    1.282447] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.282455] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.282471] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf9ffb000
[    1.342240] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.342244] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.342247] usb usb6: Product: OHCI Host Controller
[    1.342248] usb usb6: Manufacturer: Linux 3.9.0-0-generic ohci_hcd
[    1.342251] usb usb6: SerialNumber: 0000:00:13.1
[    1.342357] hub 6-0:1.0: USB hub found
[    1.342363] hub 6-0:1.0: 3 ports detected
[    1.342543] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.342550] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.342565] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf9ffa000
[    1.402318] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.402322] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.402325] usb usb7: Product: OHCI Host Controller
[    1.402327] usb usb7: Manufacturer: Linux 3.9.0-0-generic ohci_hcd
[    1.402329] usb usb7: SerialNumber: 0000:00:14.5
[    1.402436] hub 7-0:1.0: USB hub found
[    1.402443] hub 7-0:1.0: 2 ports detected
[    1.402550] uhci_hcd: USB Universal Host Controller Interface driver
[    1.402673] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.402681] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 8
[    1.402798] xhci_hcd 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.402839] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.402842] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.402845] usb usb8: Product: xHCI Host Controller
[    1.402848] usb usb8: Manufacturer: Linux 3.9.0-0-generic xhci_hcd
[    1.402850] usb usb8: SerialNumber: 0000:04:00.0
[    1.402960] xHCI xhci_add_endpoint called for root hub
[    1.402961] xHCI xhci_check_bandwidth called for root hub
[    1.402977] hub 8-0:1.0: USB hub found
[    1.402983] hub 8-0:1.0: 2 ports detected
[    1.403034] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.403038] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 9
[    1.403058] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.403062] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.403065] usb usb9: Product: xHCI Host Controller
[    1.403067] usb usb9: Manufacturer: Linux 3.9.0-0-generic xhci_hcd
[    1.403070] usb usb9: SerialNumber: 0000:04:00.0
[    1.403117] xHCI xhci_add_endpoint called for root hub
[    1.403118] xHCI xhci_check_bandwidth called for root hub
[    1.403131] hub 9-0:1.0: USB hub found
[    1.403137] hub 9-0:1.0: 2 ports detected
[    1.403288] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.406085] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.406090] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.406190] mousedev: PS/2 mouse device common for all mice
[    1.406315] rtc_cmos 00:02: RTC can wake from S4
[    1.406418] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.406444] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.406499] device-mapper: uevent: version 1.0.3
[    1.406558] device-mapper: ioctl: 4.24.0-ioctl (2013-01-15) initialised: dm-devel@redhat.com
[    1.406615] cpuidle: using governor ladder
[    1.406738] cpuidle: using governor menu
[    1.406747] ledtrig-cpu: registered to indicate activity on CPUs
[    1.406750] EFI Variables Facility v0.08 2004-May-17
[    1.406936] ashmem: initialized
[    1.407050] TCP: cubic registered
[    1.407131] NET: Registered protocol family 10
[    1.407292] NET: Registered protocol family 17
[    1.407301] Key type dns_resolver registered
[    1.407651] Loading module verification certificates
[    1.408530] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: a613b88bb096e930ea59a01dc9480bd1d49d0787'
[    1.408539] registered taskstats version 1
[    1.411343] Key type trusted registered
[    1.413117] Key type encrypted registered
[    1.415462] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.415726] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.415729] EDD information not available.
[    1.416816] Freeing unused kernel memory: 1268k freed
[    1.417133] Write protecting the kernel read-only data: 12288k
[    1.419775] Freeing unused kernel memory: 1148k freed
[    1.422244] Freeing unused kernel memory: 1064k freed
[    1.434791] udevd[118]: starting version 175
[    1.447742] libahci: module verification failed: signature and/or required key missing - tainting kernel
[    1.448491] ahci 0000:00:11.0: version 3.0
[    1.448697] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.448705] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.449644] scsi0 : ahci
[    1.450050] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.450305] r8169 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.450555] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000181c000, bc:5f:f4:73:9c:55, XID 0c900800 IRQ 45
[    1.450559] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.450576] scsi1 : ahci
[    1.451287] scsi2 : ahci
[    1.451830] scsi3 : ahci
[    1.451881] ata1: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd00 irq 22
[    1.451886] ata2: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffd80 irq 22
[    1.451890] ata3: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe00 irq 22
[    1.451894] ata4: SATA max UDMA/133 abar m1024@0xf9fffc00 port 0xf9fffe80 irq 22
[    1.452040] ahci 0000:03:00.0: irq 46 for MSI/MSI-X
[    1.452070] ahci: SSS flag set, parallel bus scan disabled
[    1.452096] ahci 0000:03:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl IDE mode
[    1.452101] ahci 0000:03:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    1.453270] scsi4 : ahci
[    1.453696] scsi5 : ahci
[    1.453764] ata5: SATA max UDMA/133 abar m512@0xfeaffc00 port 0xfeaffd00 irq 46
[    1.453768] ata6: SATA max UDMA/133 abar m512@0xfeaffc00 port 0xfeaffd80 irq 46
[    1.455336] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.456268] scsi6 : pata_acpi
[    1.456746] scsi7 : pata_acpi
[    1.456959] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.456962] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.770910] ata4: SATA link down (SStatus 0 SControl 300)
[    1.770924] ata5: SATA link down (SStatus 0 SControl 300)
[    1.770990] ata3: SATA link down (SStatus 0 SControl 300)
[    1.943102] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.943158] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.943976] ata1.00: ATA-7: ST3200827AS, 3.AHH, max UDMA/100
[    1.943995] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.945006] ata1.00: configured for UDMA/100
[    1.945271] scsi 0:0:0:0: Direct-Access     ATA      ST3200827AS      3.AH PQ: 0 ANSI: 5
[    1.945606] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.945631] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.945842] sd 0:0:0:0: [sda] Write Protect is off
[    1.945848] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.945902] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.945973] ata2.00: ATAPI: HL-DT-ST DVDRAM GH24LS50, YP02, max UDMA/100
[    1.949953] ata2.00: configured for UDMA/100
[    1.955807] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24LS50  YP02 PQ: 0 ANSI: 5
[    1.959797] sr0: scsi3-mmc drive: 102x/102x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.959813] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.959993] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.960066] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.977381]  sda: sda1 sda2 < sda5 >
[    1.978003] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.027176] tsc: Refined TSC clocksource calibration: 2705.370 MHz
[    2.027196] Switching to clocksource tsc
[    2.183396] usb 4-1: new low-speed USB device number 2 using ohci_hcd
[    2.279514] ata6: SATA link down (SStatus 0 SControl 300)
[    2.350678] usb 4-1: New USB device found, idVendor=093a, idProduct=2510
[    2.350696] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.350707] usb 4-1: Product: USB OPTICAL MOUSE
[    2.350715] usb 4-1: Manufacturer: PIXART
[    2.358581] hidraw: raw HID events driver (C) Jiri Kosina
[    2.364819] usbcore: registered new interface driver usbhid
[    2.364823] usbhid: USB HID core driver
[    2.367307] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input2
[    2.367408] hid-generic 0003:093A:2510.0001: input,hidraw0: USB HID v1.10 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:12.1-1/input0
[    2.615949] usb 5-3: new full-speed USB device number 2 using ohci_hcd
[    2.662867] vesafb: mode is 1680x1050x32, linelength=6720, pages=0
[    2.662873] vesafb: scrolling: redraw
[    2.662877] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.670615] vesafb: framebuffer at 0xfb000000, mapped to 0xffffc90011c80000, using 6912k, total 6912k
[    2.670749] Console: switching to colour frame buffer device 210x65
[    2.675508] fb0: VESA VGA frame buffer device
[    2.785261] usb 5-3: New USB device found, idVendor=058f, idProduct=9360
[    2.785359] usb 5-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.785389] usb 5-3: Product: USB Reader
[    2.785405] usb 5-3: Manufacturer:  
[    2.785420] usb 5-3: SerialNumber: 2004888
[    2.789348] Initializing USB Mass Storage driver...
[    2.789516] scsi8 : usb-storage 5-3:1.0
[    2.789613] usbcore: registered new interface driver usb-storage
[    2.789643] USB Mass Storage support registered.
[    2.920350] usb 3-3: new low-speed USB device number 2 using ohci_hcd
[    3.090651] usb 3-3: New USB device found, idVendor=046a, idProduct=0023
[    3.090748] usb 3-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.106145] input: HID 046a:0023 as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input3
[    3.106323] cherry 0003:046A:0023.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 046a:0023] on usb-0000:00:12.0-3/input0
[    3.116873] input: HID 046a:0023 as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input4
[    3.116995] cherry 0003:046A:0023.0003: input,hidraw2: USB HID v1.11 Device [HID 046a:0023] on usb-0000:00:12.0-3/input1
[    3.796675] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    3.802685] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    3.808689] scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    3.814698] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    3.814963] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    3.815212] sd 8:0:0:1: Attached scsi generic sg3 type 0
[    3.815396] sd 8:0:0:2: Attached scsi generic sg4 type 0
[    3.816006] sd 8:0:0:3: Attached scsi generic sg5 type 0
[    4.105067] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[    4.115079] sd 8:0:0:1: [sdc] Attached SCSI removable disk
[    4.125092] sd 8:0:0:2: [sdd] Attached SCSI removable disk
[    4.135110] sd 8:0:0:3: [sde] Attached SCSI removable disk
[    7.803755] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    7.803787] EXT4-fs (sda1): write access will be enabled during recovery
[   12.382673] EXT4-fs (sda1): orphan cleanup on readonly fs
[   12.382706] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 7340147
[   12.382750] EXT4-fs (sda1): 1 orphan inode deleted
[   12.382771] EXT4-fs (sda1): recovery complete
[   13.368700] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   17.539598] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.014989] udevd[448]: starting version 175
[   18.888902] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.751513] lp: driver loaded but no devices found
[   22.252759] parport_pc 00:05: reported by Plug and Play ACPI
[   22.252826] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   22.286013] ppdev: user-space parallel port driver
[   22.349868] lp0: using parport0 (interrupt-driven).
[   22.717794] wmi: Mapper loaded
[   22.722832] MCE: In-kernel MCE decoding enabled.
[   22.738961] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20130117/utaddress-251)
[   22.738979] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.818875] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[   22.818957] sp5100_tco: PCI Revision ID: 0x3c
[   22.818975] sp5100_tco: failed to find MMIO address, giving up.
[   23.044377] EDAC MC: Ver: 3.0.0
[   23.047132] microcode: CPU0: patch_level=0x010000bf
[   23.121280] AMD64 EDAC driver v3.4.0
[   23.121329] EDAC amd64: DRAM ECC disabled.
[   23.121371] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   23.121371]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   23.121371]  (Note that use of the override may cause unknown side effects.)
[   23.525248] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[   23.525391] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   23.525448] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   23.612714] microcode: CPU0: new patch_level=0x010000dc
[   23.612757] microcode: CPU1: patch_level=0x010000bf
[   23.612765] microcode: CPU1: new patch_level=0x010000dc
[   23.612797] microcode: CPU2: patch_level=0x010000bf
[   23.612821] microcode: CPU2: new patch_level=0x010000dc
[   23.612851] microcode: CPU3: patch_level=0x010000bf
[   23.612877] microcode: CPU3: new patch_level=0x010000dc
[   23.612906] microcode: CPU4: patch_level=0x010000bf
[   23.612932] microcode: CPU4: new patch_level=0x010000dc
[   23.612942] microcode: CPU5: patch_level=0x010000bf
[   23.612949] microcode: CPU5: new patch_level=0x010000dc
[   23.613034] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   24.010681] kvm: Nested Virtualization enabled
[   24.010686] kvm: Nested Paging enabled
[   27.307903] nvidia: module license 'NVIDIA' taints kernel.
[   27.307908] Disabling lock debugging due to kernel taint
[   27.324309] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   27.324432] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  313.30  Wed Mar 27 16:56:45 PDT 2013
[   29.332775] r8169 0000:02:00.0 eth0: link down
[   29.332817] r8169 0000:02:00.0 eth0: link down
[   29.332904] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.766326] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.004845] ISO 9660 Extensions: Microsoft Joliet Level 3
[   30.010257] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   30.141950] ISO 9660 Extensions: RRIP_1991A
[   30.953250] r8169 0000:02:00.0 eth0: link up
[   30.953259] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.670408] init: failsafe main process (912) killed by TERM signal
[   34.142229] bio: create slab <bio-1> at 1
[   34.354280] vboxdrv: Found 6 processor cores.
[   34.354645] vboxdrv: fAsync=0 offMin=0x906 offMax=0x3b76
[   34.354847] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   34.354852] vboxdrv: Successfully loaded version 4.2.10_Ubuntu (interface 0x001a0004).
[   34.737288] vboxpci: IOMMU not found (not registered)
[   47.145785] NVRM: Your system is not currently configured to drive a VGA console
[   47.145789] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   47.145790] NVRM: requires the use of a text-mode VGA console. Use of other console
[   47.145792] NVRM: drivers including, but not limited to, vesafb, may result in
[   47.145793] NVRM: corruption and stability problems, and is not supported.
[   52.615346] Adding 16776188k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:16776188k 

```


> **robert shearer said:**
> See 'lshw and lspci lie' in this thread...;)
[http://ubuntuforums.org/showthread.php?t=2106641&highlight=](http://ubuntuforums.org/showthread.php?t=2106641&highlight=)

Now we need just to know if this is really an output issue or if something on initializing fails. Which component is responsible for this? The NVIDIA driver seems to know the correct value. Could this be a kernel issue?

---

### Post by Sworddragon on 2013-05-12
I have now opened a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/pciutils/+bug/1179126](https://bugs.launchpad.net/ubuntu/+source/pciutils/+bug/1179126)

---

### Post by robert shearer on 2013-05-12
re your bug report...(nota bene  )> Capabilities: <access denied>
what do you get when you run...
```
**sudo** lspci -v -s 01:00.0
```
and..
```
dmesg | grep VRAM
```

---

### Post by Yellow Pasque on 2013-05-12
I wouldn't stress about it. Some AMD cards do the same, and IIRC, the explanation boils down to, "It's not displaying available RAM the way you would expect."

---

### Post by Sworddragon on 2013-05-14
The bug report has given the solution: The size that lspci is showing is the amount of memory which the CPU can use for read/write operations. The GPU will still be able to use all the memory. But now I'm wondering why at default the CPU can't select the full amount of memory. And are there any noticeable disadvantages of such a limitation?

---

