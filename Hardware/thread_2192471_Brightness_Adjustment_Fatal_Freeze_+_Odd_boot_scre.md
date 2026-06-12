---
title: "Brightness Adjustment Fatal Freeze + Odd boot screen start up error"
date: 2013-12-08
forum: Hardware
---

### Post by shahanakhter on 2013-12-08
I have several problems I've tried googling now to fix and seen other users as well in hope maybe they could help me and they did and some minor problems were overcome, but overall I'm not happy with how my system is running, it is the little things that get to me, but sometimes it's major things like fatal freezes.

I'll tell you what has been happening in my lay men's noob terms and then post some stuff...

I have a Dell Inspiron N5010 laptop, 4GB ram and 500gb hdd, it is relatively old.  It originally came with Windows 7, one summer I started dual booting 12.04, then eventually I DBAN'd it and clean installed 13.10, then I wiped again and clean installed 12.04.3, which I've been using until this day.

[SIZE=4][I]**1)** First, I use several methods to adjust my brightness (now, i used to do it normally)
[/I][/SIZE]      
         When I used my brightness keys, and I adjust rapidly my computer freezes fatally, sometimes I can adjust it a little bit, but mostly it freezes.
          
                Sometimes I try the Magic ```
Alt + SysReq R-E-I-S-U-B
```  thing and that sometimes will work and I won't have to hard reboot.

I use  **xbacklight **and the System **Settings brightness bar   **BOTH just as often result in the same kind of crash.

This really sucks and sometimes even the dim screen thing will cause a crash, I've seen this a known bug and YES I have tried what it says on those sites to add various things to your grub and ```
[COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"[/FONT][/COLOR]
``` does not work, and yes there is that comment #71 which works for many people with my exact laptop but I've tried those and they do not work, I will re-try them soon.  My kernel version is 3.12, maybe that is the difference between me and those other inspiron users...

So inspiron n5010 running 12.04.3 kernel 3.12, if anyone knows a solution or could walk me through it, that'd be awesome.


[SIZE=4]**2) ***Odd broadcom wireless 'error' messages at start up and unusual boot screen.*

 [SIZE=2]   I remember a long time ago when Ubuntu used to give me the normal orange dots boot screen all the way through, at some point, I can't remember when, that stopped happening.

I have a broadcom wireless card which is :
[/SIZE][/SIZE]```
[SIZE=2]12:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)[/SIZE]
```

And so how my laptop boots is that I get the usual BIOS and then a blank purple screen, then a black screen, it turns off(the screen) then (it used to) it pops with a message like:

```
[FONT=Ubuntu Mono][    9.625943] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1[/FONT]
```

THEN I installed the proprietary driver via jockey-gtk, 

[I]which by the way runs really slow, everything started running really slow...  Hitting the launcher button has a good 2 second lag before the launcher pops up, it did not always used to be like this and a live USB it works fine.  Alt tab is also really slow...  I don't know if someone can help me with that, that'd be great.


[/I]jockey-gtk has been terrrrrrrible, it takes forever to do nothing but it still shows a moving 'downloading and installing' loading bar, which just goes on until crashing and some how miraculously after i hard reboot the driver was installed and then I get an info message at boot like:

```
[   13.781074] INFO @wl_cfg80211_attach : Registered CFG80211 phy
```

I will stress that my Ubuntu, outside of minor slowness and and these boot messages, works fine, the wireless card picks up wifi almost always and works continuously.  HOWEVER, lately it just gets stuck on boot and I have to hard reboot and that sucks, it happens to perfectly randomly...
I am sure it is related to the abnormal boot screen.

my lspci:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)



```


Anyway here is my dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.12.1-031201-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201311201654 SMP Wed Nov 20 21:54:49 UTC 2013
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.12.1-031201-generic root=UUID=c4a7ac62-7a32-464b-9ac2-64fba4070929 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bb5a5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb5a6000-0x00000000bb5edfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb5ee000-0x00000000bb5f8fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bb5f9000-0x00000000bb5fbfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb5fc000-0x00000000bb61ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb620000-0x00000000bb628fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb629000-0x00000000bb62bfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb62c000-0x00000000bb630fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb631000-0x00000000bb650fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bb651000-0x00000000bb693fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb694000-0x00000000bb7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bde00000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000137ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Dell Inc. Inspiron N5010/0WXY9J, BIOS A15 07/19/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   3 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   4 base 138000000 mask FF8000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 4GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3008MB, range: 64MB, type UC
[    0.000000] reg 3, base: 3GB, range: 1GB, type UC
[    0.000000] reg 4, base: 4992MB, range: 128MB, type UC
[    0.000000] total RAM covered: 3904M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 5      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3008MB, range: 64MB, type UC
[    0.000000] reg 3, base: 4GB, range: 1GB, type WB
[    0.000000] reg 4, base: 4992MB, range: 128MB, type UC
[    0.000000] e820: update [mem 0xbc000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbb800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcda0-0x000fcdaf] mapped at [ffff8800000fcda0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x137e00000-0x137ffffff]
[    0.000000]  [mem 0x137e00000-0x137ffffff] page 2M
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x134000000-0x137dfffff]
[    0.000000]  [mem 0x134000000-0x137dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x133ffffff]
[    0.000000]  [mem 0x100000000-0x133ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbb5a5fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbb3fffff] page 2M
[    0.000000]  [mem 0xbb400000-0xbb5a5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbb694000-0xbb7fffff]
[    0.000000]  [mem 0xbb694000-0xbb7fffff] page 4k
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x3609c000-0x37045fff]
[    0.000000] ACPI: RSDP 00000000000f0410 00024 (v03 DELL  )
[    0.000000] ACPI: XSDT 00000000bb5ee088 0005C (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000bb5f7a70 000F4 (v04 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20130725/tbfadt-395)
[    0.000000] ACPI BIOS Warning (bug): 32/64X FACS address mismatch in FADT - 0xBB62CF40/0x00000000BB62CF80, using 32 (20130725/tbfadt-522)
[    0.000000] ACPI: DSDT 00000000bb5ee170 09900 (v02 DELL    WN09    00005010 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bb62cf40 00040
[    0.000000] ACPI: APIC 00000000bb5f7b68 00072 (v01 DELL   WN09     01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000bb5f7be0 0014E (v01 AMICPU     PROC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000bb5f7d30 0003C (v01   DELL     WN09 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000bb5f7d70 00176 (v01 DELL    WN09    01072009 AMI  00010013)
[    0.000000] ACPI: HPET 00000000bb5f7ee8 00038 (v01   DELL     WN09 01072009 AMI. 00000003)
[    0.000000] ACPI: OSFR 00000000bb5f7f20 0008C (v01 DELL    M08     07DB0713 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000137ffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x137ffffff]
[    0.000000]   NODE_DATA [mem 0x137ff8000-0x137ffcfff]
[    0.000000]  [ffffea0000000000-ffffea0004dfffff] PMD -> [ffff880133800000-ffff8801375fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x137ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xbb5a5fff]
[    0.000000]   node   0: [mem 0xbb694000-0xbb7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x137ffffff]
[    0.000000] On node 0 totalpages: 997038
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11933 pages used for memmap
[    0.000000]   DMA32 zone: 763666 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 229376 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb5a6000-0xbb5edfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb5ee000-0xbb5f8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb5f9000-0xbb5fbfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb5fc000-0xbb61ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb620000-0xbb628fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb629000-0xbb62bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb62c000-0xbb630fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb631000-0xbb650fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb651000-0xbb693fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb800000-0xbddfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbde00000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff880137c00000 s86592 r8192 d24000 u524288
[    0.000000] pcpu-alloc: s86592 r8192 d24000 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 981436
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.12.1-031201-generic root=UUID=c4a7ac62-7a32-464b-9ac2-64fba4070929 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3825512K/3988152K available (7539K kernel code, 1118K rwdata, 3516K rodata, 1340K init, 1416K bss, 162640K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16252928 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2260.840 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4521.68 BogoMIPS (lpj=9043360)
[    0.000011] pid_max: default: 32768 minimum: 301
[    0.000040] Security Framework initialized
[    0.000066] AppArmor: AppArmor initialized
[    0.000069] Yama: becoming mindful.
[    0.000501] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001577] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.002015] Mount-cache hash table entries: 256
[    0.002249] Initializing cgroup subsys memory
[    0.002263] Initializing cgroup subsys devices
[    0.002268] Initializing cgroup subsys freezer
[    0.002272] Initializing cgroup subsys blkio
[    0.002276] Initializing cgroup subsys perf_event
[    0.002282] Initializing cgroup subsys hugetlb
[    0.002308] CPU: Physical Processor ID: 0
[    0.002311] CPU: Processor Core ID: 0
[    0.002319] mce: CPU supports 9 MCE banks
[    0.002335] CPU0: Thermal monitoring enabled (TM1)
[    0.002350] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.002350] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002350] tlb_flushall_shift: 6
[    0.002484] Freeing SMP alternatives memory: 28K (ffffffff81e68000 - ffffffff81e6f000)
[    0.004076] ACPI: Core revision 20130725
[    0.009108] ACPI: All ACPI Tables successfully acquired
[    0.018395] ftrace: allocating 31049 entries in 122 pages
[    0.037473] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.077171] smpboot: CPU0: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz (fam: 06, model: 25, stepping: 02)
[    0.185563] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.185575] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.185581] ... version:                3
[    0.185584] ... bit width:              48
[    0.185587] ... generic registers:      4
[    0.185590] ... value mask:             0000ffffffffffff
[    0.185594] ... max period:             000000007fffffff
[    0.185597] ... fixed-purpose events:   3
[    0.185600] ... event mask:             000000070000000f
[    0.200819] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.187552] smpboot: Booting Node   0, Processors  #   1 #   2 #   3 OK
[    0.227244] Brought up 4 CPUs
[    0.227254] smpboot: Total of 4 processors activated (18086.72 BogoMIPS)
[    0.230209] devtmpfs: initialized
[    0.236017] EVM: security.selinux
[    0.236020] EVM: security.SMACK64
[    0.236023] EVM: security.capability
[    0.236072] PM: Registering ACPI NVS region [mem 0xbb5a6000-0xbb5edfff] (294912 bytes)
[    0.236082] PM: Registering ACPI NVS region [mem 0xbb5f9000-0xbb5fbfff] (12288 bytes)
[    0.236086] PM: Registering ACPI NVS region [mem 0xbb620000-0xbb628fff] (36864 bytes)
[    0.236090] PM: Registering ACPI NVS region [mem 0xbb62c000-0xbb630fff] (20480 bytes)
[    0.236094] PM: Registering ACPI NVS region [mem 0xbb651000-0xbb693fff] (274432 bytes)
[    0.237166] pinctrl core: initialized pinctrl subsystem
[    0.237239] regulator-dummy: no parameters
[    0.237277] RTC time:  4:25:54, date: 12/08/13
[    0.237319] NET: Registered protocol family 16
[    0.237426] cpuidle: using governor ladder
[    0.237429] cpuidle: using governor menu
[    0.237462] ACPI: bus type PCI registered
[    0.237465] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.237525] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.237531] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.260574] PCI: Using configuration type 1 for base access
[    0.261564] bio: create slab <bio-0> at 0
[    0.261757] ACPI: Added _OSI(Module Device)
[    0.261762] ACPI: Added _OSI(Processor Device)
[    0.261764] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.261767] ACPI: Added _OSI(Processor Aggregator Device)
[    0.263184] ACPI: EC: Look up EC in DSDT
[    0.264638] ACPI: Executed 1 blocks of module-level executable AML code
[    0.269111] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.276049] ACPI: SSDT 00000000bb621c18 003A4 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.276438] ACPI: Dynamic OEM Table Load:
[    0.276442] ACPI: SSDT           (null) 003A4 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.276925] ACPI: Interpreter enabled
[    0.276934] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130725/hwxface-571)
[    0.276942] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130725/hwxface-571)
[    0.276960] ACPI: (supports S0 S3 S4 S5)
[    0.276963] ACPI: Using IOAPIC for interrupt routing
[    0.276999] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.277153] ACPI: No dock devices found.
[    0.297307] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.297458] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.297667] acpi PNP0A08:00: ACPI _OSC control (0x19) granted
[    0.297821] ACPI: \_SB_.PCI0.MCH_: can't evaluate _ADR (0x5)
[    0.297863] ACPI: \_SB_.PCI0.PCH_: can't evaluate _ADR (0x5)
[    0.297934] ACPI: \_SB_.PCI0.HPET: can't evaluate _ADR (0x5)
[    0.297956] PCI host bridge to bus 0000:00
[    0.297960] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.297964] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.297967] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.297971] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.297975] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xffffffff]
[    0.297986] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.298006] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.298093] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000
[    0.298106] pci 0000:00:02.0: reg 0x10: [mem 0xfa400000-0xfa7fffff 64bit]
[    0.298113] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.298118] pci 0000:00:02.0: reg 0x20: [io  0xf080-0xf087]
[    0.298241] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.298272] pci 0000:00:16.0: reg 0x10: [mem 0xfbd09000-0xfbd0900f 64bit]
[    0.298373] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.298473] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.298500] pci 0000:00:1a.0: reg 0x10: [mem 0xfbd08000-0xfbd083ff]
[    0.298613] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.301036] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.301090] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.301114] pci 0000:00:1b.0: reg 0x10: [mem 0xfbd00000-0xfbd03fff 64bit]
[    0.301216] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.301303] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.301408] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.301463] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.301504] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.301606] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.301661] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.301704] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.301806] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.301865] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.301905] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.302010] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.302071] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.302121] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.302148] pci 0000:00:1d.0: reg 0x10: [mem 0xfbd07000-0xfbd073ff]
[    0.302261] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.305285] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.305329] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.305445] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.305483] pci 0000:00:1f.0: [8086:3b0b] type 00 class 0x060100
[    0.305671] pci 0000:00:1f.2: [8086:3b2f] type 00 class 0x010601
[    0.305701] pci 0000:00:1f.2: reg 0x10: [io  0xf070-0xf077]
[    0.305713] pci 0000:00:1f.2: reg 0x14: [io  0xf060-0xf063]
[    0.305724] pci 0000:00:1f.2: reg 0x18: [io  0xf050-0xf057]
[    0.305736] pci 0000:00:1f.2: reg 0x1c: [io  0xf040-0xf043]
[    0.305747] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.305759] pci 0000:00:1f.2: reg 0x24: [mem 0xfbd06000-0xfbd067ff]
[    0.305828] pci 0000:00:1f.2: PME# supported from D3hot
[    0.305908] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.305931] pci 0000:00:1f.3: reg 0x10: [mem 0xfbd05000-0xfbd050ff 64bit]
[    0.305963] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.306072] pci 0000:00:1f.6: [8086:3b32] type 00 class 0x118000
[    0.306102] pci 0000:00:1f.6: reg 0x10: [mem 0xfbd04000-0xfbd04fff 64bit]
[    0.306332] pci 0000:00:1c.0: PCI bridge to [bus 11]
[    0.306452] pci 0000:12:00.0: [14e4:4727] type 00 class 0x028000
[    0.306485] pci 0000:12:00.0: reg 0x10: [mem 0xfbc00000-0xfbc03fff 64bit]
[    0.306650] pci 0000:12:00.0: supports D1 D2
[    0.306652] pci 0000:12:00.0: PME# supported from D0 D3hot D3cold
[    0.314075] pci 0000:00:1c.1: PCI bridge to [bus 12]
[    0.314095] pci 0000:00:1c.1:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.314267] pci 0000:13:00.0: [10ec:8136] type 00 class 0x020000
[    0.314328] pci 0000:13:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.314424] pci 0000:13:00.0: reg 0x18: [mem 0xd0b10000-0xd0b10fff 64bit pref]
[    0.314495] pci 0000:13:00.0: reg 0x20: [mem 0xd0b00000-0xd0b0ffff 64bit pref]
[    0.314542] pci 0000:13:00.0: reg 0x30: [mem 0xfb200000-0xfb21ffff pref]
[    0.314809] pci 0000:13:00.0: supports D1 D2
[    0.314811] pci 0000:13:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.315001] pci 0000:00:1c.2: PCI bridge to [bus 13]
[    0.315008] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.315013] pci 0000:00:1c.2:   bridge window [mem 0xfb200000-0xfbbfffff]
[    0.315021] pci 0000:00:1c.2:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.315099] pci 0000:00:1c.4: PCI bridge to [bus 15]
[    0.315106] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.315111] pci 0000:00:1c.4:   bridge window [mem 0xfa800000-0xfb1fffff]
[    0.315119] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.315209] pci 0000:00:1e.0: PCI bridge to [bus 20] (subtractive decode)
[    0.315226] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.315228] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.315230] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.315232] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.315694] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.315758] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.315821] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.315882] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.315943] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.316005] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.316068] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.316130] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.316374] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.316383] ACPI: \_SB_.PCI0: notify handler is installed
[    0.316462] Found 1 acpi root devices
[    0.316630] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.316637] vgaarb: loaded
[    0.316640] vgaarb: bridge control possible 0000:00:02.0
[    0.316823] SCSI subsystem initialized
[    0.316886] libata version 3.00 loaded.
[    0.316919] ACPI: bus type USB registered
[    0.316939] usbcore: registered new interface driver usbfs
[    0.316950] usbcore: registered new interface driver hub
[    0.316983] usbcore: registered new device driver usb
[    0.317103] PCI: Using ACPI for IRQ routing
[    0.326955] PCI: Discovered peer bus ff
[    0.326958] PCI: root bus ff: using default resources
[    0.326960] PCI: Probing PCI hardware (bus ff)
[    0.326985] PCI host bridge to bus 0000:ff
[    0.326990] pci_bus 0000:ff: root bus resource [io  0x0000-0xffff]
[    0.326994] pci_bus 0000:ff: root bus resource [mem 0x00000000-0xfffffffff]
[    0.326998] pci_bus 0000:ff: No busn resource found for root bus, will use [bus ff-ff]
[    0.327007] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    0.327051] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    0.327093] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    0.327133] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    0.327172] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    0.327215] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    0.327267] pci_bus 0000:ff: busn_res: [bus ff] end is updated to ff
[    0.327270] PCI: pci_cache_line_size set to 64 bytes
[    0.327342] e820: reserve RAM buffer [mem 0x0009d400-0x0009ffff]
[    0.327344] e820: reserve RAM buffer [mem 0xbb5a6000-0xbbffffff]
[    0.327347] e820: reserve RAM buffer [mem 0xbb800000-0xbbffffff]
[    0.327444] NetLabel: Initializing
[    0.327448] NetLabel:  domain hash size = 128
[    0.327450] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.327465] NetLabel:  unlabeled traffic allowed by default
[    0.327536] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.327545] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.329592] Switched to clocksource hpet
[    0.335071] AppArmor: AppArmor Filesystem Enabled
[    0.335110] pnp: PnP ACPI init
[    0.335129] ACPI: bus type PNP registered
[    0.335281] system 00:00: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.335287] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.335291] system 00:00: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.335295] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.335299] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.335305] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.335341] pnp 00:01: [dma 4]
[    0.335365] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.335402] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.335425] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.335451] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.335503] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.335509] system 00:05: [mem 0xfe800000-0xfe8001ff] has been reserved
[    0.335514] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.335553] pnp 00:06: Plug and Play ACPI device, IDs DLL0447 SYN0600 SYN0002 PNP0f13 (active)
[    0.335588] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.335748] system 00:08: [io  0x0400-0x047f] could not be reserved
[    0.335753] system 00:08: [io  0x1180-0x119f] has been reserved
[    0.335757] system 00:08: [io  0x0500-0x057f] has been reserved
[    0.335761] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.335766] system 00:08: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.335770] system 00:08: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.335774] system 00:08: [mem 0xff000000-0xffffffff] has been reserved
[    0.335779] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.335893] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.336110] pnp: PnP ACPI: found 10 devices
[    0.336113] ACPI: bus type PNP unregistered
[    0.343412] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 11] add_size 1000
[    0.343417] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 11] add_size 200000
[    0.343420] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 11] add_size 200000
[    0.343431] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 12] add_size 1000
[    0.343434] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 12] add_size 200000
[    0.343466] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.343468] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.343471] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.343473] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.343475] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.343480] pci 0000:00:1c.0: BAR 14: assigned [mem 0xd1500000-0xd16fffff]
[    0.343486] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd1700000-0xd18fffff 64bit pref]
[    0.343491] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd1900000-0xd1afffff 64bit pref]
[    0.343496] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.343500] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.343506] pci 0000:00:1c.0: PCI bridge to [bus 11]
[    0.343512] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.343520] pci 0000:00:1c.0:   bridge window [mem 0xd1500000-0xd16fffff]
[    0.343527] pci 0000:00:1c.0:   bridge window [mem 0xd1700000-0xd18fffff 64bit pref]
[    0.343536] pci 0000:00:1c.1: PCI bridge to [bus 12]
[    0.343541] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.343549] pci 0000:00:1c.1:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.343555] pci 0000:00:1c.1:   bridge window [mem 0xd1900000-0xd1afffff 64bit pref]
[    0.343566] pci 0000:00:1c.2: PCI bridge to [bus 13]
[    0.343571] pci 0000:00:1c.2:   bridge window [io  0xe000-0xefff]
[    0.343579] pci 0000:00:1c.2:   bridge window [mem 0xfb200000-0xfbbfffff]
[    0.343586] pci 0000:00:1c.2:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.343596] pci 0000:00:1c.4: PCI bridge to [bus 15]
[    0.343601] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.343609] pci 0000:00:1c.4:   bridge window [mem 0xfa800000-0xfb1fffff]
[    0.343616] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.343626] pci 0000:00:1e.0: PCI bridge to [bus 20]
[    0.343643] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.343645] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.343647] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.343649] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xffffffff]
[    0.343652] pci_bus 0000:11: resource 0 [io  0x2000-0x2fff]
[    0.343654] pci_bus 0000:11: resource 1 [mem 0xd1500000-0xd16fffff]
[    0.343656] pci_bus 0000:11: resource 2 [mem 0xd1700000-0xd18fffff 64bit pref]
[    0.343658] pci_bus 0000:12: resource 0 [io  0x3000-0x3fff]
[    0.343660] pci_bus 0000:12: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.343662] pci_bus 0000:12: resource 2 [mem 0xd1900000-0xd1afffff 64bit pref]
[    0.343664] pci_bus 0000:13: resource 0 [io  0xe000-0xefff]
[    0.343666] pci_bus 0000:13: resource 1 [mem 0xfb200000-0xfbbfffff]
[    0.343668] pci_bus 0000:13: resource 2 [mem 0xd0b00000-0xd14fffff 64bit pref]
[    0.343670] pci_bus 0000:15: resource 0 [io  0xd000-0xdfff]
[    0.343672] pci_bus 0000:15: resource 1 [mem 0xfa800000-0xfb1fffff]
[    0.343674] pci_bus 0000:15: resource 2 [mem 0xd0000000-0xd09fffff 64bit pref]
[    0.343677] pci_bus 0000:20: resource 4 [io  0x0000-0x0cf7]
[    0.343679] pci_bus 0000:20: resource 5 [io  0x0d00-0xffff]
[    0.343681] pci_bus 0000:20: resource 6 [mem 0x000a0000-0x000bffff]
[    0.343683] pci_bus 0000:20: resource 7 [mem 0xc0000000-0xffffffff]
[    0.343686] pci_bus 0000:ff: resource 4 [io  0x0000-0xffff]
[    0.343688] pci_bus 0000:ff: resource 5 [mem 0x00000000-0xfffffffff]
[    0.343724] NET: Registered protocol family 2
[    0.343919] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.344140] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.344309] TCP: Hash tables configured (established 32768 bind 32768)
[    0.344342] TCP: reno registered
[    0.344353] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.344390] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.344481] NET: Registered protocol family 1
[    0.344497] pci 0000:00:02.0: Boot video device
[    0.597845] PCI: CLS 64 bytes, default 64
[    0.597895] Trying to unpack rootfs image as initramfs...
[    0.918938] Freeing initrd memory: 16040K (ffff88003609c000 - ffff880037046000)
[    0.918952] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.918956] software IO TLB [mem 0xb75a6000-0xbb5a6000] (64MB) mapped at [ffff8800b75a6000-ffff8800bb5a5fff]
[    0.919227] Scanning for low memory corruption every 60 seconds
[    0.919571] Initialise module verification
[    0.919624] audit: initializing netlink socket (disabled)
[    0.919639] type=2000 audit(1386476754.804:1): initialized
[    0.951544] bounce pool size: 64 pages
[    0.951563] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.952833] zbud: loaded
[    0.953012] VFS: Disk quotas dquot_6.5.2
[    0.953055] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.953568] fuse init (API version 7.22)
[    0.953652] msgmni has been set to 7503
[    0.954340] Key type asymmetric registered
[    0.954345] Asymmetric key parser 'x509' registered
[    0.954380] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.954436] io scheduler noop registered
[    0.954440] io scheduler deadline registered (default)
[    0.954468] io scheduler cfq registered
[    0.954723] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.954909] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.955091] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.955268] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.955358] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.955452] pciehp: Using ACPI for slot detection.
[    0.955526] pciehp 0000:00:1c.4:pcie04: HPC vendor_id 8086 device_id 3b4a ss_vid 1028 ss_did 447
[    0.955587] pciehp 0000:00:1c.4:pcie04: service driver pciehp loaded
[    0.955592] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.082450] Console: switching to colour frame buffer device 128x48
[    1.210372] simple-framebuffer simple-framebuffer.0: fb0: simplefb registered!
[    1.212089] intel_idle: MWAIT substates: 0x1120
[    1.212090] intel_idle: v0.4 model 0x25
[    1.212092] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.212318] ACPI: AC Adapter [AC] (on-line)
[    1.213412] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.215363] ACPI: Power Button [PWRB]
[    1.216267] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.220128] ACPI: Lid Switch [LID0]
[    1.220995] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.222938] ACPI: Sleep Button [SBTN]
[    1.223839] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.225588] ACPI: Power Button [PWRF]
[    1.226508] ACPI: Requesting acpi_cpufreq
[    1.249028] thermal LNXTHERM:00: registered as thermal_zone0
[    1.250378] ACPI: Thermal Zone [THM] (53 C)
[    1.251392] GHES: HEST is not enabled!
[    1.251485] ACPI: Battery Slot [BAT0] (battery absent)
[    1.253727] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.258148] Linux agpgart interface v0.103
[    1.259201] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.260706] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.263382] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.265139] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.268392] brd: module loaded
[    1.269793] loop: module loaded
[    1.323187] libphy: Fixed MDIO Bus: probed
[    1.375938] tun: Universal TUN/TAP device driver, 1.6
[    1.428696] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.481994] PPP generic driver version 2.4.2
[    1.535100] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.588872] ehci-pci: EHCI PCI platform driver
[    1.642320] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    1.642334] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.695573] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.749594] ehci-pci 0000:00:1a.0: debug port 2
[    1.806754] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.806776] ehci-pci 0000:00:1a.0: irq 16, io mem 0xfbd08000
[    1.869962] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.918011] tsc: Refined TSC clocksource calibration: 2260.999 MHz
[    1.976490] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.030659] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.084652] usb usb1: Product: EHCI Host Controller
[    2.137893] usb usb1: Manufacturer: Linux 3.12.1-031201-generic ehci_hcd
[    2.191926] usb usb1: SerialNumber: 0000:00:1a.0
[    2.246016] hub 1-0:1.0: USB hub found
[    2.299898] hub 1-0:1.0: 2 ports detected
[    2.353580] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    2.353588] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.407353] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.461430] ehci-pci 0000:00:1d.0: debug port 2
[    2.518272] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.518288] ehci-pci 0000:00:1d.0: irq 23, io mem 0xfbd07000
[    2.582124] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.633815] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.685614] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.694247] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.781256] usb usb2: Product: EHCI Host Controller
[    2.828190] usb usb2: Manufacturer: Linux 3.12.1-031201-generic ehci_hcd
[    2.875739] usb usb2: SerialNumber: 0000:00:1d.0
[    2.876064] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    2.876066] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.876452] hub 1-1:1.0: USB hub found
[    3.056662] Switched to clocksource tsc
[    3.056664] hub 1-1:1.0: 6 ports detected
[    3.056778] hub 2-0:1.0: USB hub found
[    3.056786] hub 2-0:1.0: 2 ports detected
[    3.056882] ehci-platform: EHCI generic platform driver
[    3.056888] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.056889] ohci-platform: OHCI generic platform driver
[    3.056895] uhci_hcd: USB Universal Host Controller Interface driver
[    3.056956] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    3.082992] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.082997] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.083138] mousedev: PS/2 mouse device common for all mice
[    3.084019] rtc_cmos 00:02: RTC can wake from S4
[    3.084159] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    3.084192] rtc_cmos 00:02: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    3.084255] device-mapper: uevent: version 1.0.3
[    3.084319] device-mapper: ioctl: 4.26.0-ioctl (2013-08-15) initialised: dm-devel@redhat.com
[    3.084326] ledtrig-cpu: registered to indicate activity on CPUs
[    3.084418] TCP: cubic registered
[    3.084510] NET: Registered protocol family 10
[    3.084706] NET: Registered protocol family 17
[    3.084717] Key type dns_resolver registered
[    3.084953] Loading module verification certificates
[    3.085961] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: b1d410877cfeae5f9ffc8f10def18d7693a99d6c'
[    3.085973] registered taskstats version 1
[    3.088484] Key type trusted registered
[    3.090518] Key type encrypted registered
[    3.092571] AppArmor: AppArmor sha1 policy hashing enabled
[    3.093035]   Magic number: 9:433:413
[    4.309639] rtc_cmos 00:02: setting system clock to 2013-12-08 04:25:57 UTC (1386476757)
[    4.355692] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.400450] EDD information not available.
[    4.445105] PM: Hibernation image not present or could not be loaded.
[    4.446646] Freeing unused kernel memory: 1340K (ffffffff81d19000 - ffffffff81e68000)
[    4.493054] Write protecting the kernel read-only data: 12288k
[    4.503349] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input6
[    4.590179] Freeing unused kernel memory: 640K (ffff880001760000 - ffff880001800000)
[    4.640446] Freeing unused kernel memory: 580K (ffff880001b6f000 - ffff880001c00000)
[    4.698650] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    4.813822] udevd[118]: starting version 175
[    4.863199] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    4.863204] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.863494] hub 2-1:1.0: USB hub found
[    4.863564] hub 2-1:1.0: 8 ports detected
[    5.068640] ahci 0000:00:1f.2: version 3.0
[    5.068864] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    5.068955] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[    5.068959] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    5.068964] ahci 0000:00:1f.2: setting latency timer to 64
[    5.069254] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.069470] r8169 0000:13:00.0: irq 45 for MSI/MSI-X
[    5.069664] r8169 0000:13:00.0 eth0: RTL8102e at 0xffffc90000654000, f0:4d:a2:83:97:52, XID 04e00000 IRQ 45
[    5.083502] scsi0 : ahci
[    5.083606] scsi1 : ahci
[    5.083690] scsi2 : ahci
[    5.083783] scsi3 : ahci
[    5.083868] scsi4 : ahci
[    5.083952] scsi5 : ahci
[    5.084007] ata1: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06100 irq 44
[    5.084010] ata2: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06180 irq 44
[    5.084011] ata3: DUMMY
[    5.084012] ata4: DUMMY
[    5.084015] ata5: SATA max UDMA/133 abar m2048@0xfbd06000 port 0xfbd06300 irq 44
[    5.084015] ata6: DUMMY
[    5.238940] usb 1-1.6: new high-speed USB device number 3 using ehci-pci
[    5.402839] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.402868] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.402893] ata5: SATA link down (SStatus 0 SControl 300)
[    5.425555] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633C, DW50, max UDMA/100
[    5.425558] ata2.00: applying bridge limits
[    5.447403] ata2.00: configured for UDMA/100
[    5.480173] ata1.00: ATA-8: TOSHIBA MK5065GSX, GJ002D, max UDMA/100
[    5.480175] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.481107] ata1.00: configured for UDMA/100
[    5.481282] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK5065GS GJ00 PQ: 0 ANSI: 5
[    5.481486] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.481517] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.481545] sd 0:0:0:0: [sda] Write Protect is off
[    5.481547] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.481564] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.531436] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L633C DW50 PQ: 0 ANSI: 5
[    5.537272] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.537273] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.537458] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.537574] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.582053]  sda: sda1 sda2 < sda5 >
[    5.582734] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.584238] usb 1-1.6: New USB device found, idVendor=0c45, idProduct=6461
[    5.584240] usb 1-1.6: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    5.584244] usb 1-1.6: Product: Laptop_Integrated_Webcam_1.3M
[    5.584247] usb 1-1.6: Manufacturer: M091S-M01-0603-SA761
[    7.571706] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    9.058087] init: ureadahead main process (295) terminated with status 5
[   10.268312] Adding 3986428k swap on /dev/sda5.  Priority:-1 extents:1 across:3986428k FS
[   10.848335] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.560262] udevd[390]: starting version 175
[   13.193864] lp: driver loaded but no devices found
[   13.338421] lib80211: common routines for IEEE802.11 drivers
[   13.338427] lib80211_crypt: registered algorithm 'NULL'
[   13.477078] cfg80211: Calling CRDA to update world regulatory domain
[   13.745105] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.745114] Disabling lock debugging due to kernel taint
[   13.746798] wl: module verification failed: signature and/or required key missing - tainting kernel
[   13.781074] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.882888] lib80211_crypt: registered algorithm 'TKIP'
[   13.944511] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   14.246308] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.494827] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPI1 1 (20130725/utaddress-251)
[   14.494828] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.494834] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPI1 1 (20130725/utaddress-251)
[   14.494835] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.494840] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPI1 1 (20130725/utaddress-251)
[   14.494841] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.494841] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.534790] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   14.535002] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[   14.535321] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   14.537496] wmi: Mapper loaded
[   14.587361] [drm] Initialized drm 1.1.0 20060810
[   14.791181] [drm] Memory usable by graphics device = 2048M
[   14.791187] checking generic (c0000000 300000) vs hw (c0000000 10000000)
[   14.791189] fb: conflicting fb hw usage inteldrmfb vs simple - removing generic driver
[   14.791231] Console: switching to colour dummy device 80x25
[   14.791326] i915 0000:00:02.0: setting latency timer to 64
[   14.818987] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   14.818998] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.818999] [drm] Driver supports precise vblank timestamp query.
[   14.819068] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.848963] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   14.944243] fbcon: inteldrmfb (fb0) is primary device
[   15.554970] cfg80211: World regulatory domain updated:
[   15.554971] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.554973] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.554974] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.554975] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.554976] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.554977] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.845346] Console: switching to colour frame buffer device 170x48
[   15.846057] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000, board id: 3655, fw id: 581785
[   15.851213] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.904871] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   15.920174] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   16.030666] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   16.030669] i915 0000:00:02.0: registered panic notifier
[   16.041483] acpi device:2e: registered as cooling_device4
[   16.041622] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   16.041669] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input9
[   16.041783] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.041964] mei_me 0000:00:16.0: setting latency timer to 64
[   16.042036] mei_me 0000:00:16.0: irq 47 for MSI/MSI-X
[   16.047162] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   16.472054] type=1400 audit(1386476770.871:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=792 comm="apparmor_parser"
[   16.472061] type=1400 audit(1386476770.871:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=792 comm="apparmor_parser"
[   16.472065] type=1400 audit(1386476770.871:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=792 comm="apparmor_parser"
[   16.472461] type=1400 audit(1386476770.871:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=739 comm="apparmor_parser"
[   16.472470] type=1400 audit(1386476770.871:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=739 comm="apparmor_parser"
[   16.472476] type=1400 audit(1386476770.871:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=739 comm="apparmor_parser"
[   16.472485] type=1400 audit(1386476770.871:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=795 comm="apparmor_parser"
[   16.472493] type=1400 audit(1386476770.871:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=795 comm="apparmor_parser"
[   16.472499] type=1400 audit(1386476770.871:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=795 comm="apparmor_parser"
[   16.472598] type=1400 audit(1386476770.871:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=792 comm="apparmor_parser"
[   16.509197] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   16.509202]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.509204]    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   16.509206]    mono: mono_out=0x0
[   16.509207]    inputs:
[   16.509210]      Internal Mic=0xc
[   16.509212]      Mic=0xa
[   16.553367] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   16.553486] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.553587] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.736344] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   16.780005] Linux video capture interface: v2.00
[   16.873430] usb 2-1.2: new high-speed USB device number 3 using ehci-pci
[   16.972121] usb 2-1.2: New USB device found, idVendor=8564, idProduct=1000
[   16.972130] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   16.972136] usb 2-1.2: Product: Mass Storage Device
[   16.972141] usb 2-1.2: Manufacturer: JetFlash
[   16.972146] usb 2-1.2: SerialNumber: JLHGSX35VGGVOK1G
[   17.022160] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:6461)
[   17.060087] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input13
[   17.060241] usbcore: registered new interface driver uvcvideo
[   17.060244] USB Video Class driver (1.1.1)
[   17.310865] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[   17.310948] scsi6 : usb-storage 2-1.2:1.0
[   17.311193] usbcore: registered new interface driver usb-storage
[   18.657108] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 8GB    1100 PQ: 0 ANSI: 4
[   18.657550] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   18.658212] sd 6:0:0:0: [sdb] 15826944 512-byte logical blocks: (8.10 GB/7.54 GiB)
[   18.659086] sd 6:0:0:0: [sdb] Write Protect is off
[   18.659091] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   18.660079] sd 6:0:0:0: [sdb] No Caching mode page found
[   18.661265] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   18.666282] sd 6:0:0:0: [sdb] No Caching mode page found
[   18.667485] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   18.669878]  sdb: sdb1
[   18.672831] sd 6:0:0:0: [sdb] No Caching mode page found
[   18.674021] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   18.675363] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   18.788549] ppdev: user-space parallel port driver
[   19.188647] Bluetooth: Core ver 2.16
[   19.188674] NET: Registered protocol family 31
[   19.188676] Bluetooth: HCI device and connection manager initialized
[   19.188691] Bluetooth: HCI socket layer initialized
[   19.188695] Bluetooth: L2CAP socket layer initialized
[   19.188702] Bluetooth: SCO socket layer initialized
[   19.532396] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.532400] Bluetooth: BNEP filters: protocol multicast
[   19.532412] Bluetooth: BNEP socket layer initialized
[   19.533511] Bluetooth: RFCOMM TTY layer initialized
[   19.533523] Bluetooth: RFCOMM socket layer initialized
[   19.533525] Bluetooth: RFCOMM ver 1.11
[   19.734119] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   20.011551] init: failsafe main process (1021) killed by TERM signal
[   21.655492] audit_printk_skb: 33 callbacks suppressed
[   21.655496] type=1400 audit(1386476776.055:23): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1099 comm="apparmor_parser"
[   21.655503] type=1400 audit(1386476776.055:24): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1099 comm="apparmor_parser"
[   21.655507] type=1400 audit(1386476776.055:25): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1099 comm="apparmor_parser"
[   21.656042] type=1400 audit(1386476776.055:26): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1099 comm="apparmor_parser"
[   21.656047] type=1400 audit(1386476776.055:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1099 comm="apparmor_parser"
[   21.656326] type=1400 audit(1386476776.055:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1099 comm="apparmor_parser"
[   21.658570] type=1400 audit(1386476776.059:29): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1102 comm="apparmor_parser"
[   21.658579] type=1400 audit(1386476776.059:30): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1102 comm="apparmor_parser"
[   21.659205] type=1400 audit(1386476776.059:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1102 comm="apparmor_parser"
[   21.907301] type=1400 audit(1386476776.307:32): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1103 comm="apparmor_parser"
[   24.696326] r8169 0000:13:00.0 eth0: link down
[   24.696378] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.352649] cfg80211: Calling CRDA for country: US
[   27.357900] cfg80211: Regulatory domain changed to country: US
[   27.357904] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.357906] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   27.357908] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   27.357910] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.357912] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.357913] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.357915] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)

```

---

### Post by Toz on 2013-12-08
*I'm going to move this thread to **Hardware***

With respect to the brightness, can we dig a little deeper:

1. Your current kernel boot line (so we know what we're starting with):
```
cat /proc/cmdline
```

2. Your video card/driver (interestingly, it doesn't show up in your original lspci report):
```
lspci -k | grep -iA2 VGA
```

3. Your backlight interfaces and values:
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```

4. And finally, your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and paste back the link that is generated. You may need to install pastebinit if its not installed.

---

### Post by shahanakhter on 2013-12-08
[COLOR=#000000]1. 
      [/COLOR]```
BOOT_IMAGE=/boot/vmlinuz-3.12.1-031201-generic root=UUID=c4a7ac62-7a32-464b-9ac2-64fba4070929 ro
```[COLOR=#000000]

2.
      [/COLOR]```
grep: VGA: No such file or directory
```[COLOR=#000000]   I do have a VGA port in my laptop if that makes a difference...  I know ubuntu doesn't recognize my graphics... Maybe that's the issue?  How do install Intel (R) HD Graphics or is it "[/COLOR]00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)"
[COLOR=#000000]
3.   
      [/COLOR]```
/sys/class/backlight/acpi_video015
15
/sys/class/backlight/intel_backlight
4882

4882
```[COLOR=#000000]

4.
       [/COLOR] [http://paste.ubuntu.com/6543034/](http://paste.ubuntu.com/6543034/)


---

Let me know if there is anything else you need pasted, thank you so much for helping!  :)

---

### Post by Toz on 2013-12-08
> 2.
```

grep: VGA: No such file or directory[
```

I do have a VGA port in my laptop if that makes a difference... I know ubuntu doesn't recognize my graphics... Maybe that's the issue? How do install Intel (R) HD Graphics or is it "00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)"

You might have mistyped/pasted a part of the second command, hence the error. However, from the Xorg log file, it looks like you only have an intel video card (not a dual-video system). However, for completeness sake, can you re-run the command and post back the results:
```
lspci -k | grep -iA2 VGA
```

> 3.
```

/sys/class/backlight/acpi_video015
15
/sys/class/backlight/intel_backlight
4882
4882
```

You have 2 backlight interfaces, and his may be causing the problem. Since you are using a newer kernel, you can direct the system to use the intel backlight interface by creating the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"    "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...log out and back in again to test.

If it doesn't work, can you post back the contents of /usr/share/X11/xorg.conf.d/20-intel.conf (as you created it) and well as your Xorg log file again:
```
pastebinit /var/log/Xorg.0.log
```

---

### Post by shahanakhter on 2013-12-08
[IMG]http://i.imgur.com/RqYaOzT.png?1[/IMG]


This is what I'm getting for the lspci, I hope this helps, I'm not sure why it's not showing up here.  Or I'd feel really foolish if I'm still typing it in wrong...

Anywhooz, the 20-intel.conf WORKS!  right now, I logged out logged back in and it worked SO well, like... smoothly. and 'xbacklight -100' essentially turns off the monitor which is cool, it wasn't able to do that before at lowest brightness so I assume some better driver is at work here, thank you!

Right after that i rebooted, and quickly adjusted brightness and I exhibited the same freezing behavior...  so I hard rebooted, and now it is working smoothly again.  I guess I didn't give it enough time to register before?  I am going to reboot again and wait and see.  but right now... SOLVED as far as brightness goes.  I'd like to leave the thread unsolved ... UNLESS you think no one else can help me with that problem or I've been to vague and should make a separate thread, in which case I will.

THANK YOU, so much. This was such a debilitating issue, and I've asked so many people and no one has helped until now.  

In case that weird instance of that reboot happens again here is:  

[IMG]http://i.imgur.com/yCN8R7Y.png?1[/IMG]

and the pastebin: [http://paste.ubuntu.com/6543441/](http://paste.ubuntu.com/6543441/)
Thanks again, it's working great right now.

---

### Post by Toz on 2013-12-08
> **shahanakhter said:**
> This is what I'm getting for the lspci, I hope this helps, I'm not sure why it's not showing up here.  Or I'd feel really foolish if I'm still typing it in wrong...
Ahhhh, I have a typo in my command. My bad. But it doesn't matter. I'll fix it in my original post. The command should be:
```
lspci -k | grep -iA2 VGA
```
...I missed the dash.

> Anywhooz, the 20-intel.conf WORKS!  right now, I logged out logged back in and it worked SO well, like... smoothly. and 'xbacklight -100' essentially turns off the monitor which is cool, it wasn't able to do that before at lowest brightness so I assume some better driver is at work here, thank you!
Glad to hear that it worked for you. 

> I'd like to leave the thread unsolved ... UNLESS you think no one else can help me with that problem or I've been to vague and should make a separate thread, in which case I will.
Its difficult to troubleshoot two separate unrelated items in one thread. I think it would be best to create a new thread for your second item and put it in the Networking subforum so that one of the gurus there can have a look at it.

---

### Post by shahanakhter on 2013-12-08
Oh okay gotcha, it's this:

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)    Subsystem: Dell Device 0447
    Kernel driver in use: i915
```

Does that change anything?  

Just rebooted again and it's still working now, so I guess that's good to go now!  Hope the same thing works when I install Trusty Tahr but that's down the line.

> [COLOR=#000000]Its difficult to troubleshoot two separate unrelated items in one thread. I think it would be best to create a new thread for your second item and put it in the Networking subforum so that one of the gurus there can have a look at it.[/COLOR]

Yes that's what I thought, makes perfect sense.  Marking **solved**, you're awesome, thank you SO much for helping me out on a Sunday night, this was amazing!

*side note:  how did you know that?!  Would've taken me a million years...*

---

