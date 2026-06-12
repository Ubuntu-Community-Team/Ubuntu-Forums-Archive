---
title: "Getting WiFi to work an MSI U160"
date: 2010-05-24
forum: Hardware
---

### Post by His Eminence on 2010-05-24
Just bought a shiny new MSI Wind U160. I've installed Ubuntu Netbook Edition 10.04 on it, the install was pretty smooth (after I finally managed to get the USB stick to be bootable and boot), however wireless networking doesn't work. Probably other stuff is not working too, but without the network it is hard to check. I can get to network using Ethernet cable, but it is not comfortable so in the end I use now mostly Windows 7 on my new netbook.

Question 1: how to get the damn WiFi on an MSI U160 to work?
Question 2: how to get the built-in 3G modem (from Huawei) to work?

---

### Post by dino99 on 2010-05-24
first question
As root:

mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

It is then possible to connect via network manager.

2d question:
[http://ubuntuforums.org/showthread.php?p=9237905](http://ubuntuforums.org/showthread.php?p=9237905)

---

### Post by His Eminence on 2010-05-24
> **dino99 said:**
> first question
As root:

mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

It is then possible to connect via network manager.


Thanks for your reply!

Did that (c&p-ed what you posted) but it didn't work. After restarting the network manager the dropdown in the upper-right corner of the screen was saying "Device not ready" in the "Wireless network" section. Did a reboot to be sure, after reboot it was like before - "Not connected" there. Interestingly, nothing touched the empty RT2860STA.dat file I created after I did. I checked after the reboot and last changed timestamp didn't change. 


> **dino99 said:**
> 
2d question:
[http://ubuntuforums.org/showthread.php?p=9237905](http://ubuntuforums.org/showthread.php?p=9237905)

Thanks will look into it, but WiFi is a priority of course.

---

### Post by His Eminence on 2010-05-27
*sigh* still stuck with Windows...

---

### Post by dino99 on 2010-05-27
maybe you are able to read the MSI manual:  ](*,)

***Switch to wireless networking at the click of a button

With the U160, you can connect to or disconnect from a wireless network just be pressing a button, making for relaxed, convenient Internet usage.

Easy, convenient upgrading

The U160’s user-friendly design makes upgrading device RAM or other modules incredibly simple.
	
 *****

[http://www.msi.com/index.php?func=proddesc&maincat_no=135&prod_no=1986](http://www.msi.com/index.php?func=proddesc&maincat_no=135&prod_no=1986)

---

### Post by His Eminence on 2010-05-31
> **dino99 said:**
> maybe you are able to read the MSI manual:  ](*,)


I don't understand why you are being rude. Your solution doesn't work - that doesn't imply I'm an idiot. 

In fact, your response makes me think you have never ever seen an MSI U160. If you did play with it you would know WiFi modem is switched on by a slider on the left side and its operation is signaled by a diode on the front. I'm not as stupid as to try to use a device that is switched off on the hardware level. 

OK - is there anyone here who:
- did get MSI U160's WiFi to work under Ubuntu,
- is willing to help?

---

### Post by ibuclaw on 2010-05-31
There seems to be a bug raised on this in Launchpad that may be related to your issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577147)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

Could you post the output of:
```
dmesg
```
In [NOPARSE]```
 
```[/NOPARSE] tags so can have a look to confirm this?

Regards

---

### Post by znuxor on 2010-05-31
I bought the msi u160. The reason why the wifi card doesn't work is because the driver for this card (Ralink rt3090)are not in the kernel (or not detected) and they are not available in the "normal" repositories. The solution is to do:
* You will need a working wired connection while you do that.

1) Add these line into the file /etc/apt/sources.list
```
### They are used with karmic instead of lucid because they are  unavailable for lucid.
deb http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu karmic main
deb-src http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu karmic main
```2) Update your sources with synaptic, apt-get or your your favorite package manager
```
sudo apt-get update
```3) Install the package rt3090-dkms with your package manager.
```
sudo apt-get install rt3090-dkms
```It should compile the driver without problem. It took about three minutes or less on mine.

edit: I actually forgot to add the GPG key, just do: sudo add-apt-repository ppa:markus-tisoft/ppa
and do an update with your favorite package manager. :)

---

### Post by pbf on 2010-06-01
Should this work on the standard version too?
Tried it on a standard 10.04 install on a Wind U160 and it doesnt seem to work.
'I get  a module license 'unspecified' taints kernel message' searching dmesg for rt3 and 'initialized fail' for rt2

Cheers,

Pete

---

### Post by ibuclaw on 2010-06-01
> **pbf said:**
> Should this work on the standard version too?
Tried it on a standard 10.04 install on a Wind U160 and it doesnt seem to work.
'I get  a module license 'unspecified' taints kernel message' searching dmesg for rt3 and 'initialized fail' for rt2

Cheers,

Pete

Could you post the entire dmesg log? Telling it in abstract says absolutely nothing about what is going on.

Regards

---

### Post by pbf on 2010-06-01
From a fresh install, no updates via update manager, just the steps above to install the 3090-dkms.
Netbook remix on its way down now, will see if that makes any difference?

Cheers,

Pete

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f3cf000 (usable)
[    0.000000]  BIOS-e820: 000000003f3cf000 - 000000003f3d1000 (reserved)
[    0.000000]  BIOS-e820: 000000003f3d1000 - 000000003f3d8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f3d8000 - 000000003f3e6000 (usable)
[    0.000000]  BIOS-e820: 000000003f3e6000 - 000000003f42c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f42c000 - 000000003f434000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f434000 - 000000003f437000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f437000 - 000000003f45e000 (reserved)
[    0.000000]  BIOS-e820: 000000003f45e000 - 000000003f45f000 (usable)
[    0.000000]  BIOS-e820: 000000003f45f000 - 000000003f469000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f469000 - 000000003f498000 (reserved)
[    0.000000]  BIOS-e820: 000000003f498000 - 000000003f600000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.6 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3f600 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F600000 mask 0FFF00000 write-through
[    0.000000]   2 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   3 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d800 (usable)
[    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f3cf000 (usable)
[    0.000000]  modified: 000000003f3cf000 - 000000003f3d1000 (reserved)
[    0.000000]  modified: 000000003f3d1000 - 000000003f3d8000 (ACPI NVS)
[    0.000000]  modified: 000000003f3d8000 - 000000003f3e6000 (usable)
[    0.000000]  modified: 000000003f3e6000 - 000000003f42c000 (ACPI NVS)
[    0.000000]  modified: 000000003f42c000 - 000000003f434000 (ACPI data)
[    0.000000]  modified: 000000003f434000 - 000000003f437000 (ACPI NVS)
[    0.000000]  modified: 000000003f437000 - 000000003f45e000 (reserved)
[    0.000000]  modified: 000000003f45e000 - 000000003f45f000 (usable)
[    0.000000]  modified: 000000003f45f000 - 000000003f469000 (ACPI NVS)
[    0.000000]  modified: 000000003f469000 - 000000003f498000 (reserved)
[    0.000000]  modified: 000000003f498000 - 000000003f600000 (usable)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed01000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2ef83000 - 2f71b2b0
[    0.000000] ACPI: RSDP 000f0410 00024 (v03 MSI_NB)
[    0.000000] ACPI: XSDT 3f42c080 00054 (v01 MSI_NB MEGABOOK 03022010 AMI  00010013)
[    0.000000] ACPI: FACP 3f433378 000F4 (v04 MSI_NB MEGABOOK 03022010 AMI  00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20090903/tbfadt-369)
[    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 3F465F40/000000003F465F80, using 32 (20090903/tbfadt-486)
[    0.000000] ACPI: DSDT 3f42c168 07210 (v02 MSI_NB MEGABOOK 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 3f465f40 00040
[    0.000000] ACPI: APIC 3f433470 00062 (v01 MSI_NB MEGABOOK 03022010 AMI  00010013)
[    0.000000] ACPI: MCFG 3f4334d8 0003C (v01 MSI_NB MEGABOOK 03022010 MSFT 00000097)
[    0.000000] ACPI: MCFG 3f433518 0003C (v01 MSI_NB MEGABOOK 03022010 MSFT 00000097)
[    0.000000] ACPI: SLIC 3f433558 00176 (v01 MSI_NB MEGABOOK 03022010 MSFT 00000097)
[    0.000000] ACPI: HPET 3f4336d0 00038 (v01 MSI_NB MEGABOOK 03022010 AMI. 00000003)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [002ef83000 - 002f71b2b0]          RAMDISK ==> [002ef83000 - 002f71b2b0]
[    0.000000]   #5 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd266]              BRK ==> [00008da000 - 00008dd266]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00fcb90] fcb90
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0003f3cf
[    0.000000]     0: 0x0003f3d8 -> 0x0003f3e6
[    0.000000]     0: 0x0003f45e -> 0x0003f45f
[    0.000000]     0: 0x0003f498 -> 0x0003f600
[    0.000000] On node 0 totalpages: 259283
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 31819 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f600000 (gap: 3f600000:bf600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u2097152
[    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257254
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=d70c67f8-6051-4a95-8406-5e97dd76d9ad ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5191360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f600)
[    0.000000] Memory: 1006632k/1038336k available (4673k kernel code, 29988k reserved, 2122k data, 656k init, 128288k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1712.560 MHz processor.
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3425.12 BogoMIPS (lpj=6850240)
[    0.004043] Security Framework initialized
[    0.004080] AppArmor: AppArmor initialized
[    0.004096] Mount-cache hash table entries: 512
[    0.004308] Initializing cgroup subsys ns
[    0.004318] Initializing cgroup subsys cpuacct
[    0.004327] Initializing cgroup subsys memory
[    0.004340] Initializing cgroup subsys devices
[    0.004346] Initializing cgroup subsys freezer
[    0.004351] Initializing cgroup subsys net_cls
[    0.004385] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004392] CPU: L2 cache: 512K
[    0.004397] CPU: Physical Processor ID: 0
[    0.004401] CPU: Processor Core ID: 0
[    0.004408] mce: CPU supports 5 MCE banks
[    0.004423] CPU0: Thermal monitoring enabled (TM2)
[    0.004431] using mwait in idle threads.
[    0.004441] Performance Events: Atom events, Intel PMU driver.
[    0.004456] ... version:                3
[    0.004460] ... bit width:              40
[    0.004465] ... generic registers:      2
[    0.004469] ... value mask:             000000ffffffffff
[    0.004474] ... max period:             000000007fffffff
[    0.004479] ... fixed-purpose events:   3
[    0.004483] ... event mask:             0000000700000003
[    0.004491] Checking 'hlt' instruction... OK.
[    0.020017] Disabling 4MB page tables to avoid TLB bug
[    0.024142] ACPI: Core revision 20090903
[    0.040026] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040037] ftrace: allocating 21771 entries in 43 pages
[    0.044105] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044423] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.084869] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.172099] CPU1: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.172124] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176031] Brought up 2 CPUs
[    0.176038] Total of 2 processors activated (6850.19 BogoMIPS).
[    0.176262] CPU0 attaching sched-domain:
[    0.176271]  domain 0: span 0-1 level SIBLING
[    0.176276]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.176288]   domain 1: span 0-1 level MC
[    0.176293]    groups: 0-1 (cpu_power = 1178)
[    0.176305] CPU1 attaching sched-domain:
[    0.176309]  domain 0: span 0-1 level SIBLING
[    0.176314]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.176325]   domain 1: span 0-1 level MC
[    0.176330]    groups: 0-1 (cpu_power = 1178)
[    0.176540] devtmpfs: initialized
[    0.176540] regulator: core version 0.5
[    0.176540] Time: 16:33:33  Date: 06/01/10
[    0.176540] NET: Registered protocol family 16
[    0.176540] Trying to unpack rootfs image as initramfs...
[    0.176540] EISA bus registered
[    0.176544] ACPI: bus type pci registered
[    0.176704] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.176713] PCI: Not using MMCONFIG.
[    0.199731] PCI: Using configuration type 1 for base access
[    0.202815] bio: create slab <bio-0> at 0
[    0.205454] ACPI: EC: Look up EC in DSDT
[    0.209692] ACPI: Executed 1 blocks of module-level executable AML code
[    0.216769] ACPI: BIOS _OSI(Linux) query ignored
[    0.220303] ACPI: Interpreter enabled
[    0.220330] ACPI: (supports S0 S1 S3 S4 S5)
[    0.220401] ACPI: Using IOAPIC for interrupt routing
[    0.220530] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.237322] PCI: BIOS Bug: MCFG area at f0000000 is not reserved in ACPI motherboard resources
[    0.237334] PCI: Not using MMCONFIG.
[    0.255368] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.255980] ACPI: No dock devices found.
[    0.256707] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.256882] pci 0000:00:02.0: reg 10 32bit mmio: [0xfea80000-0xfeafffff]
[    0.256895] pci 0000:00:02.0: reg 14 io port: [0xf100-0xf107]
[    0.256906] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.256917] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfc100000-0xfc1fffff]
[    0.256976] pci 0000:00:02.1: reg 10 32bit mmio: [0xfea00000-0xfea7ffff]
[    0.257140] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfeb00000-0xfeb03fff]
[    0.257231] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.257244] pci 0000:00:1b.0: PME# disabled
[    0.257377] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.257389] pci 0000:00:1c.0: PME# disabled
[    0.257527] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.257539] pci 0000:00:1c.1: PME# disabled
[    0.257670] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.257681] pci 0000:00:1c.2: PME# disabled
[    0.257808] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.257819] pci 0000:00:1c.3: PME# disabled
[    0.257911] pci 0000:00:1d.0: reg 20 io port: [0xf0a0-0xf0bf]
[    0.258007] pci 0000:00:1d.1: reg 20 io port: [0xf080-0xf09f]
[    0.258101] pci 0000:00:1d.2: reg 20 io port: [0xf060-0xf07f]
[    0.258196] pci 0000:00:1d.3: reg 20 io port: [0xf040-0xf05f]
[    0.258302] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfeb05000-0xfeb053ff]
[    0.258390] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.258400] pci 0000:00:1d.7: PME# disabled
[    0.258709] pci 0000:00:1f.2: reg 10 io port: [0xf0f0-0xf0f7]
[    0.258724] pci 0000:00:1f.2: reg 14 io port: [0xf0e0-0xf0e3]
[    0.258739] pci 0000:00:1f.2: reg 18 io port: [0xf0d0-0xf0d7]
[    0.258754] pci 0000:00:1f.2: reg 1c io port: [0xf0c0-0xf0c3]
[    0.258769] pci 0000:00:1f.2: reg 20 io port: [0xf020-0xf03f]
[    0.258784] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfeb04000-0xfeb043ff]
[    0.258843] pci 0000:00:1f.2: PME# supported from D3hot
[    0.258853] pci 0000:00:1f.2: PME# disabled
[    0.258939] pci 0000:00:1f.3: reg 20 io port: [0xf000-0xf01f]
[    0.259061] pci 0000:01:00.0: reg 10 io port: [0xe000-0xe0ff]
[    0.259096] pci 0000:01:00.0: reg 18 64bit mmio pref: [0xe2110000-0xe2110fff]
[    0.259122] pci 0000:01:00.0: reg 20 64bit mmio pref: [0xe2100000-0xe210ffff]
[    0.259139] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfe000000-0xfe01ffff]
[    0.259207] pci 0000:01:00.0: supports D1 D2
[    0.259214] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.259225] pci 0000:01:00.0: PME# disabled
[    0.259321] pci 0000:00:1c.0: bridge io port: [0xe000-0xefff]
[    0.259332] pci 0000:00:1c.0: bridge 32bit mmio: [0xfe000000-0xfe9fffff]
[    0.259348] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xe2100000-0xe2afffff]
[    0.259426] pci 0000:03:00.0: reg 10 32bit mmio: [0xfd600000-0xfd60ffff]
[    0.259615] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.259627] pci 0000:00:1c.1: bridge 32bit mmio: [0xfd600000-0xfdffffff]
[    0.259642] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xe1600000-0xe1ffffff]
[    0.259729] pci 0000:00:1c.2: bridge io port: [0xc000-0xcfff]
[    0.259740] pci 0000:00:1c.2: bridge 32bit mmio: [0xfcc00000-0xfd5fffff]
[    0.259755] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xe0b00000-0xe14fffff]
[    0.259840] pci 0000:00:1c.3: bridge io port: [0xb000-0xbfff]
[    0.259851] pci 0000:00:1c.3: bridge 32bit mmio: [0xfc200000-0xfcbfffff]
[    0.259866] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xe0000000-0xe09fffff]
[    0.259949] pci 0000:00:1e.0: transparent bridge
[    0.260040] pci_bus 0000:00: on NUMA node 0
[    0.260059] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.260361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.260683] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.260886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.261069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.261261] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.293993] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.294307] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.294622] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.294932] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.295240] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.295561] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.295870] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.296238] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.296558] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.296589] vgaarb: loaded
[    0.296902] SCSI subsystem initialized
[    0.297153] libata version 3.00 loaded.
[    0.297383] usbcore: registered new interface driver usbfs
[    0.297425] usbcore: registered new interface driver hub
[    0.297514] usbcore: registered new device driver usb
[    0.298139] ACPI: WMI: Mapper loaded
[    0.298147] PCI: Using ACPI for IRQ routing
[    0.298533] NetLabel: Initializing
[    0.298539] NetLabel:  domain hash size = 128
[    0.298544] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.298575] NetLabel:  unlabeled traffic allowed by default
[    0.298676] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.298691] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.304188] Switching to clocksource tsc
[    0.308546] AppArmor: AppArmor Filesystem Enabled
[    0.308585] pnp: PnP ACPI init
[    0.308620] ACPI: bus type pnp registered
[    0.313718] pnp: PnP ACPI: found 12 devices
[    0.313726] ACPI: ACPI bus type pnp unregistered
[    0.313736] PnPBIOS: Disabled by ACPI PNP
[    0.313772] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.313792] system 00:03: ioport range 0x800-0x87f has been reserved
[    0.313801] system 00:03: ioport range 0x480-0x4bf has been reserved
[    0.313812] system 00:03: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.313821] system 00:03: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.313831] system 00:03: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.313841] system 00:03: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.313850] system 00:03: iomem range 0xffe00000-0xffffffff has been reserved
[    0.313873] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.349021] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.349033] pci 0000:00:1c.0:   IO window: 0xe000-0xefff
[    0.349047] pci 0000:00:1c.0:   MEM window: 0xfe000000-0xfe9fffff
[    0.349059] pci 0000:00:1c.0:   PREFETCH window: 0x000000e2100000-0x000000e2afffff
[    0.349076] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.349086] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.349099] pci 0000:00:1c.1:   MEM window: 0xfd600000-0xfdffffff
[    0.349111] pci 0000:00:1c.1:   PREFETCH window: 0x000000e1600000-0x000000e1ffffff
[    0.349126] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    0.349136] pci 0000:00:1c.2:   IO window: 0xc000-0xcfff
[    0.349149] pci 0000:00:1c.2:   MEM window: 0xfcc00000-0xfd5fffff
[    0.349162] pci 0000:00:1c.2:   PREFETCH window: 0x000000e0b00000-0x000000e14fffff
[    0.349179] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:07
[    0.349189] pci 0000:00:1c.3:   IO window: 0xb000-0xbfff
[    0.349201] pci 0000:00:1c.3:   MEM window: 0xfc200000-0xfcbfffff
[    0.349213] pci 0000:00:1c.3:   PREFETCH window: 0x000000e0000000-0x000000e09fffff
[    0.349228] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.349234] pci 0000:00:1e.0:   IO window: disabled
[    0.349245] pci 0000:00:1e.0:   MEM window: disabled
[    0.349254] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.349290]   alloc irq_desc for 16 on node -1
[    0.349296]   alloc kstat_irqs on node -1
[    0.349313] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.349325] pci 0000:00:1c.0: setting latency timer to 64
[    0.349345]   alloc irq_desc for 17 on node -1
[    0.349351]   alloc kstat_irqs on node -1
[    0.349361] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.349373] pci 0000:00:1c.1: setting latency timer to 64
[    0.349391]   alloc irq_desc for 18 on node -1
[    0.349397]   alloc kstat_irqs on node -1
[    0.349407] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.349418] pci 0000:00:1c.2: setting latency timer to 64
[    0.349438]   alloc irq_desc for 19 on node -1
[    0.349443]   alloc kstat_irqs on node -1
[    0.349453] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.349464] pci 0000:00:1c.3: setting latency timer to 64
[    0.349480] pci 0000:00:1e.0: setting latency timer to 64
[    0.349493] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.349501] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.349509] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.349517] pci_bus 0000:01: resource 1 mem: [0xfe000000-0xfe9fffff]
[    0.349526] pci_bus 0000:01: resource 2 pref mem [0xe2100000-0xe2afffff]
[    0.349534] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.349542] pci_bus 0000:03: resource 1 mem: [0xfd600000-0xfdffffff]
[    0.349550] pci_bus 0000:03: resource 2 pref mem [0xe1600000-0xe1ffffff]
[    0.349558] pci_bus 0000:05: resource 0 io:  [0xc000-0xcfff]
[    0.349566] pci_bus 0000:05: resource 1 mem: [0xfcc00000-0xfd5fffff]
[    0.349575] pci_bus 0000:05: resource 2 pref mem [0xe0b00000-0xe14fffff]
[    0.349583] pci_bus 0000:07: resource 0 io:  [0xb000-0xbfff]
[    0.349591] pci_bus 0000:07: resource 1 mem: [0xfc200000-0xfcbfffff]
[    0.349599] pci_bus 0000:07: resource 2 pref mem [0xe0000000-0xe09fffff]
[    0.349608] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.349615] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]
[    0.349701] NET: Registered protocol family 2
[    0.349964] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.350819] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.351930] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.352449] TCP: Hash tables configured (established 131072 bind 65536)
[    0.352458] TCP reno registered
[    0.352713] NET: Registered protocol family 1
[    0.352774] pci 0000:00:02.0: Boot video device
[    0.771619] cpufreq-nforce2: No nForce2 chipset.
[    0.771705] Scanning for low memory corruption every 60 seconds
[    0.771987] audit: initializing netlink socket (disabled)
[    0.772013] type=2000 audit(1275410013.771:1): initialized
[    0.792034] highmem bounce pool size: 64 pages
[    0.792052] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.796929] VFS: Disk quotas dquot_6.5.2
[    0.797113] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.798946] fuse init (API version 7.13)
[    0.799245] msgmni has been set to 1716
[    0.799867] alg: No test for stdrng (krng)
[    0.800048] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.800057] io scheduler noop registered
[    0.800063] io scheduler anticipatory registered
[    0.800068] io scheduler deadline registered
[    0.800208] io scheduler cfq registered (default)
[    0.800549]   alloc irq_desc for 24 on node -1
[    0.800556]   alloc kstat_irqs on node -1
[    0.800578] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.800597] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.800834]   alloc irq_desc for 25 on node -1
[    0.800841]   alloc kstat_irqs on node -1
[    0.800859] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.800879] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.801112]   alloc irq_desc for 26 on node -1
[    0.801118]   alloc kstat_irqs on node -1
[    0.801136] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.801153] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.801377]   alloc irq_desc for 27 on node -1
[    0.801383]   alloc kstat_irqs on node -1
[    0.801400] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.801418] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.801619] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.801656] Firmware did not grant requested _OSC control
[    0.801704] Firmware did not grant requested _OSC control
[    0.801740] Firmware did not grant requested _OSC control
[    0.801773] Firmware did not grant requested _OSC control
[    0.801852] Firmware did not grant requested _OSC control
[    0.801886] Firmware did not grant requested _OSC control
[    0.801919] Firmware did not grant requested _OSC control
[    0.801951] Firmware did not grant requested _OSC control
[    0.801992] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.802589] ACPI: AC Adapter [ADP1] (off-line)
[    0.802854] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C09:00/PNP0C0D:00/input/input0
[    0.803324] ACPI: Lid Switch [LID0]
[    0.803497] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.803507] ACPI: Sleep Button [SLPB]
[    0.803642] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.803651] ACPI: Power Button [PWRB]
[    0.803786] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.803795] ACPI: Power Button [PWRF]
[    0.805307] ACPI: SSDT 3f460918 00444 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.807060] Monitor-Mwait will be used to enter C-1 state
[    0.807161] Monitor-Mwait will be used to enter C-2 state
[    0.807246] Monitor-Mwait will be used to enter C-3 state
[    0.807266] Marking TSC unstable due to TSC halts in idle
[    0.807409] processor LNXCPU:00: registered as cooling_device0
[    0.808284] Switching to clocksource hpet
[    0.809292] processor LNXCPU:01: registered as cooling_device1
[    0.817111] thermal LNXTHERM:01: registered as thermal_zone0
[    0.817135] ACPI: Thermal Zone [THRM] (41 C)
[    0.822246] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.826355] brd: module loaded
[    0.828147] loop: module loaded
[    0.828412] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.830003] Fixed MDIO Bus: probed
[    0.830137] PPP generic driver version 2.4.2
[    0.830346] tun: Universal TUN/TAP device driver, 1.6
[    0.830352] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.830658] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.830711]   alloc irq_desc for 23 on node -1
[    0.830718]   alloc kstat_irqs on node -1
[    0.830734] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.830767] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.830776] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.830866] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.830910] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.830931] ehci_hcd 0000:00:1d.7: debug port 1
[    0.834830] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.834899] isapnp: Scanning for PnP cards...
[    0.877385] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeb05000
[    0.893369] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.893647] usb usb1: configuration #1 chosen from 1 choice
[    0.893732] hub 1-0:1.0: USB hub found
[    0.893754] hub 1-0:1.0: 8 ports detected
[    0.893907] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.893950] uhci_hcd: USB Universal Host Controller Interface driver
[    0.894026] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.894043] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.894052] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.894149] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.894194] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000f0a0
[    0.894437] usb usb2: configuration #1 chosen from 1 choice
[    0.894511] hub 2-0:1.0: USB hub found
[    0.894530] hub 2-0:1.0: 2 ports detected
[    0.894635] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.894650] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.894658] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.894758] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.894816] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000f080
[    0.895048] usb usb3: configuration #1 chosen from 1 choice
[    0.895122] hub 3-0:1.0: USB hub found
[    0.895139] hub 3-0:1.0: 2 ports detected
[    0.895246] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.895261] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.895269] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.895353] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.895406] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f060
[    0.895638] usb usb4: configuration #1 chosen from 1 choice
[    0.895712] hub 4-0:1.0: USB hub found
[    0.895730] hub 4-0:1.0: 2 ports detected
[    0.895835] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.895849] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.895857] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.895940] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.895992] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000f040
[    0.896239] usb usb5: configuration #1 chosen from 1 choice
[    0.896314] hub 5-0:1.0: USB hub found
[    0.896332] hub 5-0:1.0: 2 ports detected
[    0.896562] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.940346] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.940372] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.940639] mice: PS/2 mouse device common for all mice
[    0.941055] rtc_cmos 00:05: RTC can wake from S4
[    0.941165] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.941208] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.941516] device-mapper: uevent: version 1.0.3
[    0.949758] ACPI: Battery Slot [BAT1] (battery present)
[    0.981879] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.020384] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.028365] device-mapper: multipath: version 1.1.0 loaded
[    1.028374] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.033688] EISA: Probing bus 0 at eisa.0
[    1.033734] EISA: Detected 0 cards.
[    1.053367] cpuidle: using governor ladder
[    1.053685] cpuidle: using governor menu
[    1.054885] TCP cubic registered
[    1.055341] NET: Registered protocol family 10
[    1.056515] lo: Disabled Privacy Extensions
[    1.057775] NET: Registered protocol family 17
[    1.058703] Using IPI No-Shortcut mode
[    1.058927] PM: Resume from disk failed.
[    1.058953] registered taskstats version 1
[    1.059598]   Magic number: 14:798:589
[    1.059732] rtc_cmos 00:05: setting system clock to 2010-06-01 16:33:34 UTC (1275410014)
[    1.059740] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.059745] EDD information not available.
[    1.084720] Freeing initrd memory: 7776k freed
[    1.190794] isapnp: No Plug & Play device found
[    1.190848] Freeing unused kernel memory: 656k freed
[    1.191557] Write protecting the kernel text: 4676k
[    1.191645] Write protecting the kernel read-only data: 1840k
[    1.226479] udev: starting version 151
[    1.301099] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    1.408184] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.408229] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.408307] r8169 0000:01:00.0: setting latency timer to 64
[    1.408380]   alloc irq_desc for 28 on node -1
[    1.408387]   alloc kstat_irqs on node -1
[    1.408412] r8169 0000:01:00.0: irq 28 for MSI/MSI-X
[    1.410244] eth0: RTL8102e at 0xf8080000, 40:61:86:ae:c0:8e, XID 04c00000 IRQ 28
[    1.460310] ahci 0000:00:1f.2: version 3.0
[    1.460345] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.460419]   alloc irq_desc for 29 on node -1
[    1.460427]   alloc kstat_irqs on node -1
[    1.460448] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    1.460603] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.460615] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.460628] ahci 0000:00:1f.2: setting latency timer to 64
[    1.484715] scsi0 : ahci
[    1.509933] usb 1-6: configuration #1 chosen from 1 choice
[    1.510017] scsi1 : ahci
[    1.524915] scsi2 : ahci
[    1.540673] scsi3 : ahci
[    1.541209] ata1: SATA max UDMA/133 abar m1024@0xfeb04000 port 0xfeb04100 irq 29
[    1.541222] ata2: SATA max UDMA/133 abar m1024@0xfeb04000 port 0xfeb04180 irq 29
[    1.541232] ata3: SATA max UDMA/133 abar m1024@0xfeb04000 port 0xfeb04200 irq 29
[    1.541243] ata4: SATA max UDMA/133 abar m1024@0xfeb04000 port 0xfeb04280 irq 29
[    1.860104] ata2: SATA link down (SStatus 0 SControl 300)
[    1.860141] ata4: SATA link down (SStatus 0 SControl 300)
[    1.860176] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.860210] ata3: SATA link down (SStatus 0 SControl 300)
[    1.913170] ata1.00: ATA-8: ST9250315AS, 0001SDM1, max UDMA/133
[    1.913186] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.915292] ata1.00: configured for UDMA/133
[    1.928277] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      0001 PQ: 0 ANSI: 5
[    1.928599] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.929205] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.929340] sd 0:0:0:0: [sda] Write Protect is off
[    1.929347] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.929417] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.929782]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.995039] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.725658] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   10.532886] Adding 2231288k swap on /dev/sda6.  Priority:-1 extents:1 across:2231288k 
[   10.582215] udev: starting version 151
[   10.696286] lp: driver loaded but no devices found
[   11.083541] udev: renamed network interface eth0 to eth1
[   11.123173] Linux agpgart interface v0.103
[   11.129644] rt3090sta: module license 'unspecified' taints kernel.
[   11.129654] Disabling lock debugging due to kernel taint
[   11.397764] rt2860 0000:03:00.0: enabling device (0000 -> 0002)
[   11.397785] rt2860 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.397843] rt2860 0000:03:00.0: setting latency timer to 64
[   11.398226] 
[   11.398229] 
[   11.398231] === pAd = f8412000, size = 523136 ===
[   11.398234] 
[   11.398519] <-- RTMPAllocAdapterBlock, Status=0
[   11.398529] pAd->CSRBaseAddress =0xf8400000, csr_addr=0xf8400000!
[   11.445055] [drm] Initialized drm 1.1.0 20060810
[   11.455965] agpgart-intel 0000:00:00.0: Intel IGD Chipset
[   11.456351] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[   11.499282] Linux video capture interface: v2.00
[   11.499729] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   11.566062] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (13d3:5070)
[   11.593397] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input6
[   11.593568] usbcore: registered new interface driver uvcvideo
[   11.593579] USB Video Class driver (v0.1.0)
[   11.640875] type=1505 audit(1275406425.077:2):  operation="profile_load" pid=585 name="/sbin/dhclient3"
[   11.641587] type=1505 audit(1275406425.081:3):  operation="profile_load" pid=585 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.642015] type=1505 audit(1275406425.081:4):  operation="profile_load" pid=585 name="/usr/lib/connman/scripts/dhclient-script"
[   11.657543] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.657557] i915 0000:00:02.0: setting latency timer to 64
[   11.704415]   alloc irq_desc for 30 on node -1
[   11.704424]   alloc kstat_irqs on node -1
[   11.704443] i915 0000:00:02.0: irq 30 for MSI/MSI-X
[   11.704458] [drm] set up 7M of stolen space
[   11.847486] [drm] initialized overlay support
[   11.895332] psmouse serio1: ID: 10 00 64
[   12.225554] type=1505 audit(1275406425.665:5):  operation="profile_load" pid=703 name="/usr/share/gdm/guest-session/Xsession"
[   12.229791] type=1505 audit(1275406425.669:6):  operation="profile_replace" pid=704 name="/sbin/dhclient3"
[   12.230518] type=1505 audit(1275406425.669:7):  operation="profile_replace" pid=704 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.230931] type=1505 audit(1275406425.669:8):  operation="profile_replace" pid=704 name="/usr/lib/connman/scripts/dhclient-script"
[   12.238793] type=1505 audit(1275406425.677:9):  operation="profile_load" pid=705 name="/usr/bin/evince"
[   12.248789] type=1505 audit(1275406425.685:10):  operation="profile_load" pid=705 name="/usr/bin/evince-previewer"
[   12.254737] type=1505 audit(1275406425.693:11):  operation="profile_load" pid=705 name="/usr/bin/evince-thumbnailer"
[   12.289830] fb0: inteldrmfb frame buffer device
[   12.289837] registered panic notifier
[   12.304454] acpi device:27: registered as cooling_device2
[   12.305636] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   12.305793] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.305857] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.310952] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.311013] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.324404] vga16fb: initializing
[   12.324415] vga16fb: mapped to 0xc00a0000
[   12.324426] vga16fb: not registering due to another framebuffer present
[   12.365794] [drm] Big FIFO is enabled
[   12.380512] Finger Sensing Pad, hw: 13.2.1, sw: 1.0.0-K, buttons: 2
[   12.436888] hda_codec: ALC888: BIOS auto-probing.
[   12.437907] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   12.440969] [drm] Big FIFO is enabled
[   12.440989] [drm] Big FIFO is enabled
[   12.591065] [drm] Big FIFO is enabled
[   12.616312] [drm] Big FIFO is enabled
[   12.632301] Console: switching to colour frame buffer device 128x37
[   12.638115] [drm] Big FIFO is enabled
[   12.655717] r8169: eth1: link down
[   12.656303] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   12.688129] RX DESC f42e0000  size = 2048
[   12.688641] <-- RTMPAllocTxRxRingMemory, Status=0
[   12.896609] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[   12.897983] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.898227] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.898469] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.898710] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.898951] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.899191] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.899434] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.899674] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.899910] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.900151] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.900391] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.900632] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.900872] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.901265] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.901508] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.901749] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.901991] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.902232] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.902472] ERROR!!! BBP(viaMCU=1) read R0 fail
[   12.902713] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.113949] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[   13.115178] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.115415] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.115650] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.115885] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.116124] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.116360] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.116594] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.116829] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.117217] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.117459] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.117698] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.117933] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.118168] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.118415] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.118659] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.118901] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.119145] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.119389] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.119632] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.119874] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.119887] ERROR!!! NICInitializeAdapter failed, Status[=0x00000001]
[   13.120368] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[   13.154342] !!! rt28xx Initialized fail !!!
[   13.210298] RX DESC f4b9f000  size = 2048
[   13.210810] <-- RTMPAllocTxRxRingMemory, Status=0
[   13.351307] [drm] Big FIFO is enabled
[   13.420007] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[   13.421395] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.421640] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.421883] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.422121] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.422359] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.422595] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.422830] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.423066] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.423338] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.423585] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.423824] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.424064] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.424302] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.424541] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.424778] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.425175] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.425413] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.425653] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.425899] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.426145] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.514236] input: FSPPS/2 Sentelic FingerSensingPad as /devices/platform/i8042/serio1/input/input9
[   13.552821] ppdev: user-space parallel port driver
[   13.637874] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[   13.639171] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.639410] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.639646] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.639884] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.640128] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.640375] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.640614] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.640856] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.641261] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.641500] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.641743] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.642036] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.642277] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.642515] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.642751] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.642987] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.643223] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.643460] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.643699] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.643943] ERROR!!! BBP(viaMCU=1) read R0 fail
[   13.643957] ERROR!!! NICInitializeAdapter failed, Status[=0x00000001]
[   13.644438] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
[   13.663145] !!! rt28xx Initialized fail !!!
[   13.995538] [drm] Big FIFO is enabled
[   14.165442] CPU0 attaching NULL sched-domain.
[   14.165454] CPU1 attaching NULL sched-domain.
[   14.188122] CPU0 attaching sched-domain:
[   14.188131]  domain 0: span 0-1 level SIBLING
[   14.188138]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   14.188154]   domain 1: span 0-1 level MC
[   14.188160]    groups: 0-1 (cpu_power = 1178)
[   14.188174] CPU1 attaching sched-domain:
[   14.188180]  domain 0: span 0-1 level SIBLING
[   14.188186]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   14.188200]   domain 1: span 0-1 level MC
[   14.188207]    groups: 0-1 (cpu_power = 1178)
[   17.070396] CPU0 attaching NULL sched-domain.
[   17.070410] CPU1 attaching NULL sched-domain.
[   17.092234] CPU0 attaching sched-domain:
[   17.092244]  domain 0: span 0-1 level SIBLING
[   17.092252]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   17.092268]   domain 1: span 0-1 level MC
[   17.092274]    groups: 0-1 (cpu_power = 1178)
[   17.092287] CPU1 attaching sched-domain:
[   17.092293]  domain 0: span 0-1 level SIBLING
[   17.092299]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   17.092313]   domain 1: span 0-1 level MC
[   17.092320]    groups: 0-1 (cpu_power = 1178)

```

---

### Post by ibuclaw on 2010-06-01
What happens when you put:
```
pciehp pciehp_force=1 pciehp_slot_with_bus=1
```
Inside the **/etc/modules** file

Run:
```
sudo update-initramfs -k all
```
after doing that and reboot.

Regards

---

### Post by pbf on 2010-06-01
Hi,

Had to have either a u or a c option rather than the u .
Choosing u for update didnt seem to do that much, did you need the dmesg again?

About to reinstall with netbook remix, for what its worth.

Cheers,

Pete

---

### Post by pbf on 2010-06-02
Hmm, no joy with that either, how odd if other people have this working on the same machine.

Mine is a UK model for reference.

Pete.

---

### Post by magpiefaerie on 2010-08-15
So I just installed Ubuntu Netbook on my MSI Wind and am having the same problem. Did anybody work out a way to fix this? The problem stems from there not being a way to search for wireless connections as the light indicating wireless is on is showing on the front, but I can't find a way to search for connections. Before installing Ubuntu Netbook (which I did using Wubi), I managed to connect without any problems with the same computer on Windows 7.

Any suggestions?

Thanks,
Magpie

---

### Post by Aearenda on 2010-09-20
I installed Lucid on a U160 for a friend, and then ran into this problem. Having tried all suggestions over several days with no success, I finally updated the U160's BIOS to version 108 and we're celebrating! The BIOS update was easy using a 2Gb USB drive (but it wouldn't recognise a 4Gb drive) formatted using BootFlashDos on a Windows XP system; we had to add the BIOS files from MSI's website. The workaround of adding the /etc/Wireless/RT2860STA/RT2860STA.dat file was still in place, and so was the updated RT3090STA driver referred to above. It now works, and I dare not change anything else!

---

### Post by yron87 on 2010-09-30
Worked for me

[http://ubuntuforums.org/showthread.php?p=9909732#post9909732](http://ubuntuforums.org/showthread.php?p=9909732#post9909732)

---

### Post by arvinluke on 2010-12-20
I have been using ubuntu in all my netbooks, computers. I am also using MSI netbooks, U210, U230, etc. In all my ubuntu installation what I did is I will "try ubuntu first" without installing it in my netbooks / computer and enable wireless and network connectivity and when it is already enabled then thats the time I will install ubuntu. Just make it sure you are connected to the internet while installing so that your repsositories can get the required packages. 

Hope this helps.:D

---

### Post by His Eminence on 2011-01-07
10.10 solves the WiFi problem. I've reinstalled and it works now on my U160. :p

---

