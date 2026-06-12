---
title: "Lucid Lynx Beta 2 wont boot (Live CD)"
date: 2010-04-20
forum: Hardware
---

### Post by atari130xe on 2010-04-20
Hello Forum, I am trying to test Ubuntu Lucid Lynx beta 2 in a friend's machine and does not start with the live cd (The D integrity has been tested and its ok). It worls very well on my PC but not in his PC.

I have set the boot sequence in verbose mode and the last paragraphs I can see are:

```
Begin: Running /scripts/init-bottom ...
Done:
init: ureadahead-other main process (1089) terminated with status 4
init: ureadahead-other main process (1090) terminated with status 4
* setting sensors limits                                        (OK)
```

then the boot sequence freezes and nothing else happen. In "normal" mode it hangs in the "dot" part.

The computer specifications:
> Motherboard: Biostar PM890-M7 - 1.5MB RAM 160GB HD - Intel Celeron 420 1.6Mhz Processor
&#8226; Processor:
Supports Intel Pentium 4 processor ,Celeron D, Pentium D, and Core 2 Duo processor in LGA 775 package.
1066MHz system interface speed.
Supports Hyper-Threading Technology.
&#8226; Chipset:
VIA P4M890 VIA8237R+
&#8226; Memory:
Support 2 Single Channel DDR2
Support DDR2 533/400 Mhz
Maximum memory capacity is 4GB
RAM Support 256/512/1GB/2GB
&#8226; Slots:
2 x PCI Slot
1 x PCI-Express x 1 Slot
1 x PCI-Express x 16 Slot
&#8226; IDE:
2 x EIDE channels (up to 4 devices)
Ultra DMA 33/66/100/133 Bus Master Modes
&#8226; I/O:
1 x CD-In Connector
1 x VGA , 1 x Serial Port
2 x IDE Devices Connector
1 x RJ-45 LAN Jack
2 x Serial ATA Connectors
8 x USB 2.0 Ports (4 x Rear USB 2.0 , 4 x Front USB 2.0 )
1 x Floppy
1 x Lin-out/Lin-in/Mic-In
1 x PS/2 mouse, 1 x PS/2 keyboard
1 x S/PDIF Out Connector
&#8226; SATA:
Integrated in South Bridge VT8237R+
Support RAID 0 / 1 functions.
Data transfer rates up to 150MB/s
&#8226; Video:
VIA UniChrome Pro
&#8226; Audio:
Realtek ALC658-6Channel AC 97 2.3 CODEC
&#8226; LAN:
Realtek RTL8201CL PHY
--- Integrated 10/100 transceiver



Any help?:confused:

---

### Post by atari130xe on 2010-04-23
No one to help me? By the way I have downloaded the RC version and it happens the same, now Ubuntu ask me to enter user and password (when still its not installed) really wierd!

---

### Post by jbiggs12 on 2010-04-23
I'm not sure if I can help you on the whole not booting front, but I might be able to help you out on the RC version: Have you tried just using the user name "ubuntu" and having a blank password? Usually works for me.

Cheers, Jack

---

### Post by atari130xe on 2010-04-23
> **jbiggs12 said:**
> I'm not sure if I can help you on the whole not booting front, but I might be able to help you out on the RC version: Have you tried just using the user name "ubuntu" and having a blank password? Usually works for me.

Cheers, Jack

Hey Jack thanks for the sugestion, I Don't remember now, but Im not sure if I wrote user: ubuntu and then left it blank. I guess I did it. gee.

---

### Post by jbiggs12 on 2010-04-23
> **atari130xe said:**
> The computer specifications:
```

Motherboard: Biostar PM890-M7 - 1.5MB RAM 160GB HD - Intel Celeron 420 1.6Mhz Processor
&#8226; Processor:
Supports Intel Pentium 4 processor ,Celeron D, Pentium D, and Core 2 Duo processor in LGA 775 package.
1066MHz system interface speed.
Supports Hyper-Threading Technology.
&#8226; Chipset:
VIA P4M890 VIA8237R+
&#8226; Memory:
Support 2 Single Channel DDR2
Support DDR2 533/400 Mhz
Maximum memory capacity is 4GB
RAM Support 256/512/1GB/2GB
&#8226; Slots:
2 x PCI Slot
1 x PCI-Express x 1 Slot
1 x PCI-Express x 16 Slot
&#8226; IDE:
2 x EIDE channels (up to 4 devices)
Ultra DMA 33/66/100/133 Bus Master Modes
&#8226; I/O:
1 x CD-In Connector
1 x VGA , 1 x Serial Port
2 x IDE Devices Connector
1 x RJ-45 LAN Jack
2 x Serial ATA Connectors
8 x USB 2.0 Ports (4 x Rear USB 2.0 , 4 x Front USB 2.0 )
1 x Floppy
1 x Lin-out/Lin-in/Mic-In
1 x PS/2 mouse, 1 x PS/2 keyboard
1 x S/PDIF Out Connector
&#8226; SATA:
Integrated in South Bridge VT8237R+
Support RAID 0 / 1 functions.
Data transfer rates up to 150MB/s
&#8226; Video:
VIA UniChrome Pro
&#8226; Audio:
Realtek ALC658-6Channel AC 97 2.3 CODEC
&#8226; LAN:
Realtek RTL8201CL PHY
--- Integrated 10/100 transceiver
```


Also, I realized that your specifications say that you have 1.5 MB of RAM and a 1.5 MHz processor. Am I correct in assuming that you mean 1.5 GB and 1.5 GHz? If not, I think I know why Ubuntu isn't booting... :lolflag:

---

### Post by atari130xe on 2010-04-23
lol 1.5GB of RAM hehehe

---

### Post by mmalone21 on 2010-04-23
Have you updated the boot sequence in the BIOS to boot from the CD?

---

### Post by oldfred on 2010-04-24
On my machine both the beta & the RC turned the monitor off. I could still see my USB key flashing so the boot process continued but I could not see it. I had to add nomodeset to the boot line to get it to work for both the liveCD (it was a USB key so I could edit the boot) and after the install. Once I got the nvidia drivers installed I have had no problems. I have seen the nomodeset suggested for ATI also.

---

### Post by atari130xe on 2010-04-24
> **mmalone21 said:**
> Have you updated the boot sequence in the BIOS to boot from the CD?

Yes I did.

---

### Post by atari130xe on 2010-04-24
> **oldfred said:**
> On my machine both the beta & the RC turned the monitor off. I could still see my USB key flashing so the boot process continued but I could not see it. I had to add nomodeset to the boot line to get it to work for both the liveCD (it was a USB key so I could edit the boot) and after the install. Once I got the nvidia drivers installed I have had no problems. I have seen the nomodeset suggested for ATI also.

I got the RC now, it happens the same in the boot process, I will give it a try to "nomodeset", its really strange.
This computer has a integrated video chip VIA Chrome so I dont know if somebody else got the same problem. Thanks

---

### Post by Irihapeti on 2010-04-24
The CD versions up until about 14 April had viafb enabled, which blocked booting of the CD on machines with VIA Chrome graphics. I have a P4M900 chip, therefore I was affected.

"Nomodeset" didn't do anything. To get beta 2 to boot, I removed "quiet splash" and added "viafb.modeset=0" to the boot options. If you press F6 and then escape, you'll see the command line.

But if the RC isn't working, I wonder if it's something else.

---

### Post by atari130xe on 2010-04-24
> **Irihapeti said:**
> The CD versions up until about 14 April had viafb enabled, which blocked booting of the CD on machines with VIA Chrome graphics. I have a P4M900 chip, therefore I was affected.

"Nomodeset" didn't do anything. To get beta 2 to boot, I removed "quiet splash" and added "viafb.modeset=0" to the boot options. If you press F6 and then escape, you'll see the command line.

But if the RC isn't working, I wonder if it's something else.

Thanks I will give it a try too I hope It can be a solution

---

### Post by atari130xe on 2010-04-26
Well It didnt work adding your suggestions but I have reached the desktop and posting the syslog results after booting:

> Apr 26 14:35:33 ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr 26 14:35:33 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="960" x-info="http://www.rsyslog.com"] (re)start
Apr 26 14:35:33 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Apr 26 14:35:33 ubuntu rsyslogd: rsyslogd's userid changed to 101
Apr 26 14:35:33 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Apr 26 14:35:33 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005bee0000 (usable)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  BIOS-e820: 000000005bee0000 - 000000005bee3000 (ACPI NVS)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  BIOS-e820: 000000005bee3000 - 000000005bef0000 (ACPI data)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  BIOS-e820: 000000005bef0000 - 000000005bf00000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] DMI 2.4 present.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] last_pfn = 0x5bee0 max_arch_pfn = 0x100000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Apr 26 14:35:33 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   C0000-C8FFF write-protect
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   C9000-EFFFF uncachable
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   F0000-F7FFF write-through
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   F8000-F8FFF uncachable
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   F9000-FFFFF write-through
Apr 26 14:35:33 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   1 base 040000000 mask FE0000000 write-back
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   2 base 05C000000 mask FFC000000 uncachable
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   3 base 0D8000000 mask FF8000000 write-combining
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   4 base 05BF00000 mask FFFF00000 uncachable
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   5 disabled
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   6 disabled
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   7 disabled
Apr 26 14:35:33 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Scanning 0 areas for low memory corruption
Apr 26 14:35:33 ubuntu kernel: [    0.000000] modified physical RAM map:
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 000000005bee0000 (usable)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 000000005bee0000 - 000000005bee3000 (ACPI NVS)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 000000005bee3000 - 000000005bef0000 (ACPI data)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 000000005bef0000 - 000000005bf00000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Apr 26 14:35:33 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Apr 26 14:35:33 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] RAMDISK: 5b5dd000 - 5beaf5a0
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 008de000 - 011b05a0
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Move RAMDISK from 000000005b5dd000 - 000000005beaf59f to 008de000 - 011b059f
Apr 26 14:35:33 ubuntu kernel: [    0.000000] 582MB HIGHMEM available.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Apr 26 14:35:33 ubuntu kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   #5 [00008da000 - 00008dd0ea]              BRK ==> [00008da000 - 00008dd0ea]
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   #7 [00008de000 - 00011b05a0]      NEW RAMDISK ==> [00008de000 - 00011b05a0]
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Apr 26 14:35:33 ubuntu kernel: [    0.000000] found SMP MP-table at [c00f3fd0] f3fd0
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Zone PFN ranges:
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x0005bee0
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Apr 26 14:35:33 ubuntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Apr 26 14:35:33 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Apr 26 14:35:33 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x0005bee0
Apr 26 14:35:33 ubuntu kernel: [    0.000000] On node 0 totalpages: 376431
Apr 26 14:35:33 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c11b2200
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   HighMem zone: 1166 pages used for memmap
Apr 26 14:35:33 ubuntu kernel: [    0.000000]   HighMem zone: 148052 pages, LIFO batch:31
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Using APIC driver default
Apr 26 14:35:33 ubuntu kernel: [    0.000000] SFI: Simple Firmware Interface v0.7 [http://simplefirmware.org](http://simplefirmware.org)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Apr 26 14:35:33 ubuntu kernel: [    0.000000]     Virtual Wire compatibility mode.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] MPTABLE: OEM ID: OEM00000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] MPTABLE: Product ID: PROD00000000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] MPTABLE: APIC at: 0xFEE00000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Processor #0 (Bootup-CPU)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] I/O APIC #4 Version 17 at 0xFEC00000.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] I/O APIC #5 Version 17 at 0xFECC0000.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Processors: 1
Apr 26 14:35:33 ubuntu kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Apr 26 14:35:33 ubuntu kernel: [    0.000000] nr_irqs_gsi: 48
Apr 26 14:35:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Allocating PCI resources starting at 5bf00000 (gap: 5bf00000:84100000)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr 26 14:35:33 ubuntu kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Apr 26 14:35:33 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36024 r0 d21320 u4194304
Apr 26 14:35:33 ubuntu kernel: [    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
Apr 26 14:35:33 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 373489
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz acpi=off noapic nolapic edd=on nodmraid nomodeset debian-installer/language=es console-setup/layoutcode=latam
Apr 26 14:35:33 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Initializing CPU#0
Apr 26 14:35:33 ubuntu kernel: [    0.000000] allocated 7530560 bytes of page_cgroup
Apr 26 14:35:33 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0005bee0)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Memory: 1467784k/1506176k available (4673k kernel code, 37128k reserved, 2122k data, 656k init, 596872k highmem)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Apr 26 14:35:33 ubuntu kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
Apr 26 14:35:33 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Apr 26 14:35:33 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Apr 26 14:35:33 ubuntu kernel: [    0.000000] console [tty0] enabled
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Apr 26 14:35:33 ubuntu kernel: [    0.000000] Detected 1600.052 MHz processor.
Apr 26 14:35:33 ubuntu kernel: [    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.10 BogoMIPS (lpj=6400208)
Apr 26 14:35:33 ubuntu kernel: [    0.004142] Security Framework initialized
Apr 26 14:35:33 ubuntu kernel: [    0.004232] AppArmor: AppArmor initialized
Apr 26 14:35:33 ubuntu kernel: [    0.004295] Mount-cache hash table entries: 512
Apr 26 14:35:33 ubuntu kernel: [    0.004514] Initializing cgroup subsys ns
Apr 26 14:35:33 ubuntu kernel: [    0.004578] Initializing cgroup subsys cpuacct
Apr 26 14:35:33 ubuntu kernel: [    0.004638] Initializing cgroup subsys memory
Apr 26 14:35:33 ubuntu kernel: [    0.004703] Initializing cgroup subsys devices
Apr 26 14:35:33 ubuntu kernel: [    0.004761] Initializing cgroup subsys freezer
Apr 26 14:35:33 ubuntu kernel: [    0.004819] Initializing cgroup subsys net_cls
Apr 26 14:35:33 ubuntu kernel: [    0.004901] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 26 14:35:33 ubuntu kernel: [    0.005008] CPU: L2 cache: 512K
Apr 26 14:35:33 ubuntu kernel: [    0.005067] mce: CPU supports 6 MCE banks
Apr 26 14:35:33 ubuntu kernel: [    0.005136] using mwait in idle threads.
Apr 26 14:35:33 ubuntu kernel: [    0.005199] Performance Events: Core2 events, Intel PMU driver.
Apr 26 14:35:33 ubuntu kernel: [    0.005361] ... version:                2
Apr 26 14:35:33 ubuntu kernel: [    0.005417] ... bit width:              40
Apr 26 14:35:33 ubuntu kernel: [    0.005474] ... generic registers:      2
Apr 26 14:35:33 ubuntu kernel: [    0.005531] ... value mask:             000000ffffffffff
Apr 26 14:35:33 ubuntu kernel: [    0.005589] ... max period:             000000007fffffff
Apr 26 14:35:33 ubuntu kernel: [    0.005648] ... fixed-purpose events:   3
Apr 26 14:35:33 ubuntu kernel: [    0.005705] ... event mask:             0000000700000003
Apr 26 14:35:33 ubuntu kernel: [    0.005769] Checking 'hlt' instruction... OK.
Apr 26 14:35:33 ubuntu kernel: [    0.021085] SMP alternatives: switching to UP code
Apr 26 14:35:33 ubuntu kernel: [    0.030569] Freeing SMP alternatives: 19k freed
Apr 26 14:35:33 ubuntu kernel: [    0.030644] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr 26 14:35:33 ubuntu kernel: [    0.030708] ftrace: allocating 21771 entries in 43 pages
Apr 26 14:35:33 ubuntu kernel: [    0.032092] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Apr 26 14:35:33 ubuntu kernel: [    0.032157] SMP disabled
Apr 26 14:35:33 ubuntu kernel: [    0.032345] Brought up 1 CPUs
Apr 26 14:35:33 ubuntu kernel: [    0.032403] Total of 1 processors activated (3200.10 BogoMIPS).
Apr 26 14:35:33 ubuntu kernel: [    0.032852] CPU0 attaching NULL sched-domain.
Apr 26 14:35:33 ubuntu kernel: [    0.033015] devtmpfs: initialized
Apr 26 14:35:33 ubuntu kernel: [    0.033508] regulator: core version 0.5
Apr 26 14:35:33 ubuntu kernel: [    0.033609] Time: 14:33:54  Date: 04/26/10
Apr 26 14:35:33 ubuntu kernel: [    0.033717] NET: Registered protocol family 16
Apr 26 14:35:33 ubuntu kernel: [    0.036089] EISA bus registered
Apr 26 14:35:33 ubuntu kernel: [    0.043693] PCI: PCI BIOS revision 3.00 entry at 0xfaa30, last bus=128
Apr 26 14:35:33 ubuntu kernel: [    0.043753] PCI: Using configuration type 1 for base access
Apr 26 14:35:33 ubuntu kernel: [    0.044902] bio: create slab <bio-0> at 0
Apr 26 14:35:33 ubuntu kernel: [    0.045033] ACPI: Interpreter disabled.
Apr 26 14:35:33 ubuntu kernel: [    0.045156] vgaarb: loaded
Apr 26 14:35:33 ubuntu kernel: [    0.045344] SCSI subsystem initialized
Apr 26 14:35:33 ubuntu kernel: [    0.045458] libata version 3.00 loaded.
Apr 26 14:35:33 ubuntu kernel: [    0.045551] usbcore: registered new interface driver usbfs
Apr 26 14:35:33 ubuntu kernel: [    0.045621] usbcore: registered new interface driver hub
Apr 26 14:35:33 ubuntu kernel: [    0.045714] usbcore: registered new device driver usb
Apr 26 14:35:33 ubuntu kernel: [    0.045915] PCI: Probing PCI hardware
Apr 26 14:35:33 ubuntu kernel: [    0.045973] PCI: Probing PCI hardware (bus 00)
Apr 26 14:35:33 ubuntu kernel: [    0.046024] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xd8000000-0xdfffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.046614] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Apr 26 14:35:33 ubuntu kernel: [    0.046675] pci 0000:00:02.0: PME# disabled
Apr 26 14:35:33 ubuntu kernel: [    0.046817] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Apr 26 14:35:33 ubuntu kernel: [    0.046877] pci 0000:00:03.0: PME# disabled
Apr 26 14:35:33 ubuntu kernel: [    0.047008] pci 0000:00:0f.0: reg 10 io port: [0xfc00-0xfc07]
Apr 26 14:35:33 ubuntu kernel: [    0.047017] pci 0000:00:0f.0: reg 14 io port: [0xf800-0xf803]
Apr 26 14:35:33 ubuntu kernel: [    0.047025] pci 0000:00:0f.0: reg 18 io port: [0xf400-0xf407]
Apr 26 14:35:33 ubuntu kernel: [    0.047034] pci 0000:00:0f.0: reg 1c io port: [0xf000-0xf003]
Apr 26 14:35:33 ubuntu kernel: [    0.047042] pci 0000:00:0f.0: reg 20 io port: [0xec00-0xec0f]
Apr 26 14:35:33 ubuntu kernel: [    0.047050] pci 0000:00:0f.0: reg 24 io port: [0xe800-0xe8ff]
Apr 26 14:35:33 ubuntu kernel: [    0.047136] pci 0000:00:0f.1: reg 20 io port: [0xe400-0xe40f]
Apr 26 14:35:33 ubuntu kernel: [    0.047235] pci 0000:00:10.0: reg 20 io port: [0xe000-0xe01f]
Apr 26 14:35:33 ubuntu kernel: [    0.047268] pci 0000:00:10.0: supports D1 D2
Apr 26 14:35:33 ubuntu kernel: [    0.047271] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 26 14:35:33 ubuntu kernel: [    0.047332] pci 0000:00:10.0: PME# disabled
Apr 26 14:35:33 ubuntu kernel: [    0.047447] pci 0000:00:10.1: reg 20 io port: [0xdc00-0xdc1f]
Apr 26 14:35:33 ubuntu kernel: [    0.047479] pci 0000:00:10.1: supports D1 D2
Apr 26 14:35:33 ubuntu kernel: [    0.047482] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 26 14:35:33 ubuntu kernel: [    0.047542] pci 0000:00:10.1: PME# disabled
Apr 26 14:35:33 ubuntu kernel: [    0.047656] pci 0000:00:10.2: reg 20 io port: [0xd800-0xd81f]
Apr 26 14:35:33 ubuntu kernel: [    0.047689] pci 0000:00:10.2: supports D1 D2
Apr 26 14:35:33 ubuntu kernel: [    0.047692] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr 26 14:35:33 ubuntu kernel: [    0.047753] pci 0000:00:10.2: PME# disabled
Apr 26 14:35:33 ubuntu kernel: [    0.047867] pci 0000:00:10.3: reg 20 io port: [0xd400-0xd41f]
Apr 26 14:35:33 ubuntu kernel: [    0.047899] pci 0000:00:10.3: supports D1 D2
Apr 26 14:35:33 ubuntu kernel: [    0.047902] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Apr 26 14:35:33 ubuntu kernel: [    0.047963] pci 0000:00:10.3: PME# disabled
Apr 26 14:35:33 ubuntu kernel: [    0.048046] pci 0000:00:10.4: reg 10 32bit mmio: [0xfdfff000-0xfdfff0ff]
Apr 26 14:35:33 ubuntu kernel: [    0.048101] pci 0000:00:10.4: supports D1 D2
Apr 26 14:35:33 ubuntu kernel: [    0.048103] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
Apr 26 14:35:33 ubuntu kernel: [    0.048164] pci 0000:00:10.4: PME# disabled
Apr 26 14:35:33 ubuntu kernel: [    0.048428] pci 0000:00:12.0: reg 10 io port: [0xd000-0xd0ff]
Apr 26 14:35:33 ubuntu kernel: [    0.048436] pci 0000:00:12.0: reg 14 32bit mmio: [0xfdffe000-0xfdffe0ff]
Apr 26 14:35:33 ubuntu kernel: [    0.048485] pci 0000:00:12.0: supports D1 D2
Apr 26 14:35:33 ubuntu kernel: [    0.048487] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 26 14:35:33 ubuntu kernel: [    0.048548] pci 0000:00:12.0: PME# disabled
Apr 26 14:35:33 ubuntu kernel: [    0.048829] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xf4000000-0xf7ffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.048837] pci 0000:01:00.0: reg 14 32bit mmio: [0xfb000000-0xfbffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.048862] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
Apr 26 14:35:33 ubuntu kernel: [    0.048886] pci 0000:01:00.0: supports D1 D2
Apr 26 14:35:33 ubuntu kernel: [    0.048937] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
Apr 26 14:35:33 ubuntu kernel: [    0.048942] pci 0000:00:01.0: bridge 32bit mmio: [0xfb000000-0xfcffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.048948] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf4000000-0xf7ffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.049005] pci 0000:00:02.0: bridge io port: [0xb000-0xbfff]
Apr 26 14:35:33 ubuntu kernel: [    0.049011] pci 0000:00:02.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
Apr 26 14:35:33 ubuntu kernel: [    0.049018] pci 0000:00:02.0: bridge 64bit mmio pref: [0xfdb00000-0xfdbfffff]
Apr 26 14:35:33 ubuntu kernel: [    0.049076] pci 0000:00:03.0: bridge io port: [0xa000-0xafff]
Apr 26 14:35:33 ubuntu kernel: [    0.049081] pci 0000:00:03.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
Apr 26 14:35:33 ubuntu kernel: [    0.049090] pci 0000:00:03.0: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
Apr 26 14:35:33 ubuntu kernel: [    0.049144] pci 0000:00:13.1: transparent bridge
Apr 26 14:35:33 ubuntu kernel: [    0.049205] pci 0000:00:13.1: bridge io port: [0x9000-0x9fff]
Apr 26 14:35:33 ubuntu kernel: [    0.049210] pci 0000:00:13.1: bridge 32bit mmio: [0xfda00000-0xfdafffff]
Apr 26 14:35:33 ubuntu kernel: [    0.049217] pci 0000:00:13.1: bridge 64bit mmio pref: [0xfd900000-0xfd9fffff]
Apr 26 14:35:33 ubuntu kernel: [    0.049763] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr 26 14:35:33 ubuntu kernel: [    0.055659] PCI: Discovered peer bus 80
Apr 26 14:35:33 ubuntu kernel: [    0.055776] pci 0000:80:01.0: reg 10 64bit mmio: [0xd7ffc000-0xd7ffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.055829] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
Apr 26 14:35:33 ubuntu kernel: [    0.055890] pci 0000:80:01.0: PME# disabled
Apr 26 14:35:33 ubuntu kernel: [    0.056360] NetLabel: Initializing
Apr 26 14:35:33 ubuntu kernel: [    0.056417] NetLabel:  domain hash size = 128
Apr 26 14:35:33 ubuntu kernel: [    0.056474] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 26 14:35:33 ubuntu kernel: [    0.056543] NetLabel:  unlabeled traffic allowed by default
Apr 26 14:35:33 ubuntu kernel: [    0.056648] Switching to clocksource tsc
Apr 26 14:35:33 ubuntu kernel: [    0.059061] AppArmor: AppArmor Filesystem Enabled
Apr 26 14:35:33 ubuntu kernel: [    0.059133] pnp: PnP ACPI: disabled
Apr 26 14:35:33 ubuntu kernel: [    0.059193] PnPBIOS: Scanning system for PnP BIOS support...
Apr 26 14:35:33 ubuntu kernel: [    0.059329] PnPBIOS: Found PnP BIOS installation structure at 0xc00fb580
Apr 26 14:35:33 ubuntu kernel: [    0.059388] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb5b0, dseg 0xf0000
Apr 26 14:35:33 ubuntu kernel: [    0.060001] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
Apr 26 14:35:33 ubuntu kernel: [    0.060001] system 00:07: iomem range 0x0-0x9ffff could not be reserved
Apr 26 14:35:33 ubuntu kernel: [    0.060001] system 00:07: iomem range 0xfffe0000-0xffffffff has been reserved
Apr 26 14:35:33 ubuntu kernel: [    0.060001] system 00:07: iomem range 0xfec00000-0xfec0ffff has been reserved
Apr 26 14:35:33 ubuntu kernel: [    0.060001] system 00:07: iomem range 0xfee00000-0xfee0ffff has been reserved
Apr 26 14:35:33 ubuntu kernel: [    0.060001] system 00:07: iomem range 0x100000-0xffffff could not be reserved
Apr 26 14:35:33 ubuntu kernel: [    0.060001] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
Apr 26 14:35:33 ubuntu kernel: [    0.060001] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
Apr 26 14:35:33 ubuntu kernel: [    0.060001] system 00:08: iomem range 0xf8000-0xfffff could not be reserved
Apr 26 14:35:33 ubuntu kernel: [    0.060001] system 00:08: iomem range 0xc9200-0xcbfff has been reserved
Apr 26 14:35:33 ubuntu kernel: [    0.060168] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Apr 26 14:35:33 ubuntu kernel: [    0.060229] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Apr 26 14:35:33 ubuntu kernel: [    0.060291] pci 0000:00:01.0:   MEM window: 0xfb000000-0xfcffffff
Apr 26 14:35:33 ubuntu kernel: [    0.060352] pci 0000:00:01.0:   PREFETCH window: 0xf4000000-0xf7ffffff
Apr 26 14:35:33 ubuntu kernel: [    0.060415] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
Apr 26 14:35:33 ubuntu kernel: [    0.060474] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
Apr 26 14:35:33 ubuntu kernel: [    0.060535] pci 0000:00:02.0:   MEM window: 0xfdc00000-0xfdcfffff
Apr 26 14:35:33 ubuntu kernel: [    0.060596] pci 0000:00:02.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Apr 26 14:35:33 ubuntu kernel: [    0.060664] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
Apr 26 14:35:33 ubuntu kernel: [    0.060723] pci 0000:00:03.0:   IO window: 0xa000-0xafff
Apr 26 14:35:33 ubuntu kernel: [    0.060785] pci 0000:00:03.0:   MEM window: 0xfde00000-0xfdefffff
Apr 26 14:35:33 ubuntu kernel: [    0.060846] pci 0000:00:03.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Apr 26 14:35:33 ubuntu kernel: [    0.060915] pci 0000:00:13.1: PCI bridge, secondary bus 0000:04
Apr 26 14:35:33 ubuntu kernel: [    0.060974] pci 0000:00:13.1:   IO window: 0x9000-0x9fff
Apr 26 14:35:33 ubuntu kernel: [    0.061035] pci 0000:00:13.1:   MEM window: 0xfda00000-0xfdafffff
Apr 26 14:35:33 ubuntu kernel: [    0.061095] pci 0000:00:13.1:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Apr 26 14:35:33 ubuntu kernel: [    0.061177] pci 0000:00:01.0: setting latency timer to 64
Apr 26 14:35:33 ubuntu kernel: [    0.061191] pci 0000:00:02.0: setting latency timer to 64
Apr 26 14:35:33 ubuntu kernel: [    0.061207] pci 0000:00:03.0: setting latency timer to 64
Apr 26 14:35:33 ubuntu kernel: [    0.061216] pci 0000:00:13.1: setting latency timer to 64
Apr 26 14:35:33 ubuntu kernel: [    0.061221] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061224] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061228] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
Apr 26 14:35:33 ubuntu kernel: [    0.061231] pci_bus 0000:01: resource 1 mem: [0xfb000000-0xfcffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061234] pci_bus 0000:01: resource 2 pref mem [0xf4000000-0xf7ffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061237] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
Apr 26 14:35:33 ubuntu kernel: [    0.061240] pci_bus 0000:02: resource 1 mem: [0xfdc00000-0xfdcfffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061243] pci_bus 0000:02: resource 2 pref mem [0xfdb00000-0xfdbfffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061246] pci_bus 0000:03: resource 0 io:  [0xa000-0xafff]
Apr 26 14:35:33 ubuntu kernel: [    0.061249] pci_bus 0000:03: resource 1 mem: [0xfde00000-0xfdefffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061252] pci_bus 0000:03: resource 2 pref mem [0xfdd00000-0xfddfffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061255] pci_bus 0000:04: resource 0 io:  [0x9000-0x9fff]
Apr 26 14:35:33 ubuntu kernel: [    0.061257] pci_bus 0000:04: resource 1 mem: [0xfda00000-0xfdafffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061260] pci_bus 0000:04: resource 2 pref mem [0xfd900000-0xfd9fffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061263] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061266] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061269] pci_bus 0000:80: resource 0 io:  [0x00-0xffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061272] pci_bus 0000:80: resource 1 mem: [0x000000-0xffffffff]
Apr 26 14:35:33 ubuntu kernel: [    0.061320] NET: Registered protocol family 2
Apr 26 14:35:33 ubuntu kernel: [    0.061483] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 26 14:35:33 ubuntu kernel: [    0.061892] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 26 14:35:33 ubuntu kernel: [    0.062860] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 26 14:35:33 ubuntu kernel: [    0.063511] TCP: Hash tables configured (established 131072 bind 65536)
Apr 26 14:35:33 ubuntu kernel: [    0.063577] TCP reno registered
Apr 26 14:35:33 ubuntu kernel: [    0.063802] NET: Registered protocol family 1
Apr 26 14:35:33 ubuntu kernel: [    0.063899] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Apr 26 14:35:33 ubuntu kernel: [    0.079260] pci 0000:01:00.0: Boot video device
Apr 26 14:35:33 ubuntu kernel: [    0.079490] cpufreq-nforce2: No nForce2 chipset.
Apr 26 14:35:33 ubuntu kernel: [    0.079580] Scanning for low memory corruption every 60 seconds
Apr 26 14:35:33 ubuntu kernel: [    0.079766] audit: initializing netlink socket (disabled)
Apr 26 14:35:33 ubuntu kernel: [    0.079846] type=2000 audit(1272292434.079:1): initialized
Apr 26 14:35:33 ubuntu kernel: [    0.092317] Trying to unpack rootfs image as initramfs...
Apr 26 14:35:33 ubuntu kernel: [    2.589042] highmem bounce pool size: 64 pages
Apr 26 14:35:33 ubuntu kernel: [    2.589107] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 26 14:35:33 ubuntu kernel: [    2.590840] VFS: Disk quotas dquot_6.5.2
Apr 26 14:35:33 ubuntu kernel: [    2.590968] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 26 14:35:33 ubuntu kernel: [    2.591742] fuse init (API version 7.13)
Apr 26 14:35:33 ubuntu kernel: [    2.591909] msgmni has been set to 1702
Apr 26 14:35:33 ubuntu kernel: [    2.592247] alg: No test for stdrng (krng)
Apr 26 14:35:33 ubuntu kernel: [    2.592384] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr 26 14:35:33 ubuntu kernel: [    2.592449] io scheduler noop registered
Apr 26 14:35:33 ubuntu kernel: [    2.592504] io scheduler anticipatory registered
Apr 26 14:35:33 ubuntu kernel: [    2.592559] io scheduler deadline registered
Apr 26 14:35:33 ubuntu kernel: [    2.592662] io scheduler cfq registered (default)
Apr 26 14:35:33 ubuntu kernel: [    2.592900]   alloc irq_desc for 48 on node -1
Apr 26 14:35:33 ubuntu kernel: [    2.592903]   alloc kstat_irqs on node -1
Apr 26 14:35:33 ubuntu kernel: [    2.592914] pcieport 0000:00:02.0: setting latency timer to 64
Apr 26 14:35:33 ubuntu kernel: [    2.593060] pcieport 0000:00:03.0: setting latency timer to 64
Apr 26 14:35:33 ubuntu kernel: [    2.593155] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 26 14:35:33 ubuntu kernel: [    2.593255] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 26 14:35:33 ubuntu kernel: [    2.594940] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr 26 14:35:33 ubuntu kernel: [    2.595107] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 26 14:35:33 ubuntu kernel: [    2.595739] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 26 14:35:33 ubuntu kernel: [    2.596951] brd: module loaded
Apr 26 14:35:33 ubuntu kernel: [    2.597529] loop: module loaded
Apr 26 14:35:33 ubuntu kernel: [    2.597701] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 26 14:35:33 ubuntu kernel: [    2.598385] Fixed MDIO Bus: probed
Apr 26 14:35:33 ubuntu kernel: [    2.598481] PPP generic driver version 2.4.2
Apr 26 14:35:33 ubuntu kernel: [    2.598590] tun: Universal TUN/TAP device driver, 1.6
Apr 26 14:35:33 ubuntu kernel: [    2.598647] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr 26 14:35:33 ubuntu kernel: [    2.598817] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 26 14:35:33 ubuntu kernel: [    2.598916] ehci_hcd 0000:00:10.4: EHCI Host Controller
Apr 26 14:35:33 ubuntu kernel: [    2.599018] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
Apr 26 14:35:33 ubuntu kernel: [    2.599122] ehci_hcd 0000:00:10.4: irq 3, io mem 0xfdfff000
Apr 26 14:35:33 ubuntu kernel: [    2.599231] isapnp: Scanning for PnP cards...
Apr 26 14:35:33 ubuntu kernel: [    2.648450] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
Apr 26 14:35:33 ubuntu kernel: [    2.648610] usb usb1: configuration #1 chosen from 1 choice
Apr 26 14:35:33 ubuntu kernel: [    2.648702] hub 1-0:1.0: USB hub found
Apr 26 14:35:33 ubuntu kernel: [    2.648765] hub 1-0:1.0: 8 ports detected
Apr 26 14:35:33 ubuntu kernel: [    2.648883] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 26 14:35:33 ubuntu kernel: [    2.648956] uhci_hcd: USB Universal Host Controller Interface driver
Apr 26 14:35:33 ubuntu kernel: [    2.649066] uhci_hcd 0000:00:10.0: UHCI Host Controller
Apr 26 14:35:33 ubuntu kernel: [    2.649167] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Apr 26 14:35:33 ubuntu kernel: [    2.649256] uhci_hcd 0000:00:10.0: irq 10, io base 0x0000e000
Apr 26 14:35:33 ubuntu kernel: [    2.649424] usb usb2: configuration #1 chosen from 1 choice
Apr 26 14:35:33 ubuntu kernel: [    2.649509] hub 2-0:1.0: USB hub found
Apr 26 14:35:33 ubuntu kernel: [    2.649570] hub 2-0:1.0: 2 ports detected
Apr 26 14:35:33 ubuntu kernel: [    2.649682] uhci_hcd 0000:00:10.1: UHCI Host Controller
Apr 26 14:35:33 ubuntu kernel: [    2.649780] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Apr 26 14:35:33 ubuntu kernel: [    2.649866] uhci_hcd 0000:00:10.1: irq 11, io base 0x0000dc00
Apr 26 14:35:33 ubuntu kernel: [    2.650023] usb usb3: configuration #1 chosen from 1 choice
Apr 26 14:35:33 ubuntu kernel: [    2.650108] hub 3-0:1.0: USB hub found
Apr 26 14:35:33 ubuntu kernel: [    2.650168] hub 3-0:1.0: 2 ports detected
Apr 26 14:35:33 ubuntu kernel: [    2.650278] uhci_hcd 0000:00:10.2: UHCI Host Controller
Apr 26 14:35:33 ubuntu kernel: [    2.650376] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Apr 26 14:35:33 ubuntu kernel: [    2.650461] uhci_hcd 0000:00:10.2: irq 3, io base 0x0000d800
Apr 26 14:35:33 ubuntu kernel: [    2.650619] usb usb4: configuration #1 chosen from 1 choice
Apr 26 14:35:33 ubuntu kernel: [    2.650704] hub 4-0:1.0: USB hub found
Apr 26 14:35:33 ubuntu kernel: [    2.650765] hub 4-0:1.0: 2 ports detected
Apr 26 14:35:33 ubuntu kernel: [    2.650877] uhci_hcd 0000:00:10.3: UHCI Host Controller
Apr 26 14:35:33 ubuntu kernel: [    2.650984] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
Apr 26 14:35:33 ubuntu kernel: [    2.651070] uhci_hcd 0000:00:10.3: irq 11, io base 0x0000d400
Apr 26 14:35:33 ubuntu kernel: [    2.651226] usb usb5: configuration #1 chosen from 1 choice
Apr 26 14:35:33 ubuntu kernel: [    2.651355] hub 5-0:1.0: USB hub found
Apr 26 14:35:33 ubuntu kernel: [    2.651417] hub 5-0:1.0: 2 ports detected
Apr 26 14:35:33 ubuntu kernel: [    2.651589] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
Apr 26 14:35:33 ubuntu kernel: [    2.652049] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 26 14:35:33 ubuntu kernel: [    2.652114] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 26 14:35:33 ubuntu kernel: [    2.652315] mice: PS/2 mouse device common for all mice
Apr 26 14:35:33 ubuntu kernel: [    2.652501] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Apr 26 14:35:33 ubuntu kernel: [    2.652589] rtc0: alarms up to one day, 114 bytes nvram
Apr 26 14:35:33 ubuntu kernel: [    2.652778] device-mapper: uevent: version 1.0.3
Apr 26 14:35:33 ubuntu kernel: [    2.652980] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Apr 26 14:35:33 ubuntu kernel: [    2.653121] device-mapper: multipath: version 1.1.0 loaded
Apr 26 14:35:33 ubuntu kernel: [    2.653181] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 26 14:35:33 ubuntu kernel: [    2.653386] EISA: Probing bus 0 at eisa.0
Apr 26 14:35:33 ubuntu kernel: [    2.653479] EISA: Detected 0 cards.
Apr 26 14:35:33 ubuntu kernel: [    2.653599] cpuidle: using governor ladder
Apr 26 14:35:33 ubuntu kernel: [    2.653656] cpuidle: using governor menu
Apr 26 14:35:33 ubuntu kernel: [    2.654171] TCP cubic registered
Apr 26 14:35:33 ubuntu kernel: [    2.654406] NET: Registered protocol family 10
Apr 26 14:35:33 ubuntu kernel: [    2.654964] lo: Disabled Privacy Extensions
Apr 26 14:35:33 ubuntu kernel: [    2.655367] NET: Registered protocol family 17
Apr 26 14:35:33 ubuntu kernel: [    2.655470] Using IPI No-Shortcut mode
Apr 26 14:35:33 ubuntu kernel: [    2.655621] PM: Resume from disk failed.
Apr 26 14:35:33 ubuntu kernel: [    2.655636] registered taskstats version 1
Apr 26 14:35:33 ubuntu kernel: [    2.656104]   Magic number: 6:455:587
Apr 26 14:35:33 ubuntu kernel: [    2.656245] rtc_cmos 00:03: setting system clock to 2010-04-26 14:33:57 UTC (1272292437)
Apr 26 14:35:33 ubuntu kernel: [    2.656310] BIOS EDD facility v0.16 2004-Jun-25, 1 devices found
Apr 26 14:35:33 ubuntu kernel: [    2.917942] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 26 14:35:33 ubuntu kernel: [    2.961678] isapnp: No Plug & Play device found
Apr 26 14:35:33 ubuntu kernel: [    3.025106] Freeing initrd memory: 9033k freed
Apr 26 14:35:33 ubuntu kernel: [    3.031418] Freeing unused kernel memory: 656k freed
Apr 26 14:35:33 ubuntu kernel: [    3.031972] Write protecting the kernel text: 4676k
Apr 26 14:35:33 ubuntu kernel: [    3.032061] Write protecting the kernel read-only data: 1840k
Apr 26 14:35:33 ubuntu kernel: [    3.065300] udev: starting version 151
Apr 26 14:35:33 ubuntu kernel: [    3.233797] vga16fb: initializing
Apr 26 14:35:33 ubuntu kernel: [    3.233801] vga16fb: mapped to 0xc00a0000
Apr 26 14:35:33 ubuntu kernel: [    3.233933] fb0: VGA16 VGA frame buffer device
Apr 26 14:35:33 ubuntu kernel: [    3.239727] sata_via 0000:00:0f.0: version 2.4
Apr 26 14:35:33 ubuntu kernel: [    3.239776] sata_via 0000:00:0f.0: routed to hard irq line 11
Apr 26 14:35:33 ubuntu kernel: [    3.240355] Linux agpgart interface v0.103
Apr 26 14:35:33 ubuntu kernel: [    3.242855] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Apr 26 14:35:33 ubuntu kernel: [    3.242920] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Apr 26 14:35:33 ubuntu kernel: [    3.250648] scsi0 : sata_via
Apr 26 14:35:33 ubuntu kernel: [    3.257111] scsi1 : sata_via
Apr 26 14:35:33 ubuntu kernel: [    3.257234] ata1: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 11
Apr 26 14:35:33 ubuntu kernel: [    3.257293] ata2: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 11
Apr 26 14:35:33 ubuntu kernel: [    3.257421] pata_via 0000:00:0f.1: version 0.3.4
Apr 26 14:35:33 ubuntu kernel: [    3.263905] scsi2 : pata_via
Apr 26 14:35:33 ubuntu kernel: [    3.266938] scsi3 : pata_via
Apr 26 14:35:33 ubuntu kernel: [    3.267063] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
Apr 26 14:35:33 ubuntu kernel: [    3.267123] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
Apr 26 14:35:33 ubuntu kernel: [    3.272190] eth0: VIA Rhine II at 0xfdffe000, 00:e0:4d:4e:b6:18, IRQ 10.
Apr 26 14:35:33 ubuntu kernel: [    3.272958] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
Apr 26 14:35:33 ubuntu kernel: [    3.273050] agpgart: Detected VIA P4M890 chipset
Apr 26 14:35:33 ubuntu kernel: [    3.279565] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
Apr 26 14:35:33 ubuntu kernel: [    3.439710] ata3.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.01, max UDMA/66
Apr 26 14:35:33 ubuntu kernel: [    3.455794] ata3.00: configured for UDMA/66
Apr 26 14:35:33 ubuntu kernel: [    3.459286] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 26 14:35:33 ubuntu kernel: [    3.670749] ata1.00: ATA-7: MAXTOR STM380215AS, 4.AAB, max UDMA/133
Apr 26 14:35:33 ubuntu kernel: [    3.671561] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr 26 14:35:33 ubuntu kernel: [    3.737408] ata1.00: configured for UDMA/133
Apr 26 14:35:33 ubuntu kernel: [    3.737610] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM380215 4.AA PQ: 0 ANSI: 5
Apr 26 14:35:33 ubuntu kernel: [    3.737860] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 26 14:35:33 ubuntu kernel: [    3.738286] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
Apr 26 14:35:33 ubuntu kernel: [    3.738412] sd 0:0:0:0: [sda] Write Protect is off
Apr 26 14:35:33 ubuntu kernel: [    3.738470] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 26 14:35:33 ubuntu kernel: [    3.738502] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 26 14:35:33 ubuntu kernel: [    3.738754]  sda: sda1 sda2 sda3
Apr 26 14:35:33 ubuntu kernel: [    3.808153] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 26 14:35:33 ubuntu kernel: [    3.939290] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Apr 26 14:35:33 ubuntu kernel: [    3.951379] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.01 PQ: 0 ANSI: 5
Apr 26 14:35:33 ubuntu kernel: [    3.953827] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 26 14:35:33 ubuntu kernel: [    3.953896] Uniform CD-ROM driver Revision: 3.20
Apr 26 14:35:33 ubuntu kernel: [    3.954332] sr 2:0:0:0: Attached scsi CD-ROM sr0
Apr 26 14:35:33 ubuntu kernel: [    3.954547] sr 2:0:0:0: Attached scsi generic sg1 type 5
Apr 26 14:35:33 ubuntu kernel: [    4.257692] Console: switching to colour frame buffer device 80x30
Apr 26 14:35:33 ubuntu kernel: [   11.610275] xor: automatically using best checksumming function: pIII_sse
Apr 26 14:35:33 ubuntu kernel: [   11.627379]    pIII_sse  :  5534.000 MB/sec
Apr 26 14:35:33 ubuntu kernel: [   11.627470] xor: using function: pIII_sse (5534.000 MB/sec)
Apr 26 14:35:33 ubuntu kernel: [   11.631246] device-mapper: dm-raid45: initialized v0.2594b
Apr 26 14:35:33 ubuntu kernel: [   11.980266] EXT4-fs (sda1): mounted filesystem with ordered data mode
Apr 26 14:35:33 ubuntu kernel: [   12.164138] EXT4-fs (sda2): mounted filesystem with ordered data mode
Apr 26 14:35:33 ubuntu kernel: [   18.133984] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   18.134090] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   18.134261] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   18.134470] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   18.134630] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   18.135341] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   18.135450] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   18.772378] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   18.772476] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   18.772646] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   18.772854] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   18.773013] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   18.773723] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   18.773828] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   19.407914] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   19.408011] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   19.416981] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   19.425865] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   19.434531] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   19.443942] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   19.453054] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   20.146949] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   20.156222] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   20.165618] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   20.175015] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   20.184462] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   20.194543] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   20.204356] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   20.849297] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   20.859245] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   20.869162] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   20.879214] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   20.889208] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   20.900010] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   20.910220] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   21.620640] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   21.630843] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   21.641159] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   21.651513] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   21.661810] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   21.672961] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   21.683524] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   22.426386] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   22.436796] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   22.447218] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   22.457678] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   22.468077] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   22.479282] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   22.489894] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   23.335880] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   23.346437] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   23.356957] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   23.367562] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   23.378059] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   23.389213] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   23.399775] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   24.105459] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   24.115869] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   24.126340] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   24.136848] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   24.147297] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   24.158460] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   24.168976] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   24.909985] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:35:33 ubuntu kernel: [   24.920397] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:35:33 ubuntu kernel: [   24.930722] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:35:33 ubuntu kernel: [   24.941084] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:35:33 ubuntu kernel: [   24.951337] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:35:33 ubuntu kernel: [   24.962352] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:35:33 ubuntu kernel: [   24.972720] Buffer I/O error on device sr0, logical block 177718
Apr 26 14:35:33 ubuntu kernel: [   26.625477] ISO 9660 Extensions: Microsoft Joliet Level 3
Apr 26 14:35:33 ubuntu kernel: [   26.678943] ISO 9660 Extensions: RRIP_1991A
Apr 26 14:35:33 ubuntu kernel: [   27.768489] aufs 2-standalone.tree-20091207
Apr 26 14:35:33 ubuntu kernel: [   28.957595] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Apr 26 14:35:33 ubuntu kernel: [   97.672805] Adding 996020k swap on /dev/sda3.  Priority:-1 extents:1 across:996020k 
Apr 26 14:35:33 ubuntu kernel: [   99.068567] udev: starting version 151
Apr 26 14:35:36 ubuntu init: ubiquity main process (1156) terminated with status 1
Apr 26 14:35:36 ubuntu kernel: [  101.889641] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 26 14:35:37 ubuntu kernel: [  102.252906] psmouse serio1: ID: 10 00 64
Apr 26 14:35:37 ubuntu kernel: [  102.822160] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input2
Apr 26 14:35:40 ubuntu avahi-daemon[1238]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Apr 26 14:35:40 ubuntu avahi-daemon[1238]: Successfully dropped root privileges.
Apr 26 14:35:40 ubuntu avahi-daemon[1238]: avahi-daemon 0.6.25 starting up.
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Successfully called chroot().
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Successfully dropped remaining capabilities.
Apr 26 14:35:41 ubuntu avahi-daemon[1243]: chroot.c: open() failed: No such file or directory
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Failed to open /etc/resolv.conf: Invalid argument
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: No service file found in /etc/avahi/services.
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Network interface enumeration completed.
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Server startup complete. Host name is ubuntu.local. Local service cookie is 2957382472.
Apr 26 14:35:42 ubuntu NetworkManager: <info>  starting...
Apr 26 14:35:42 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Apr 26 14:35:43 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0)
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Apr 26 14:35:43 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 26 14:35:43 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 26 14:35:43 ubuntu NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Apr 26 14:35:43 ubuntu NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: (168123216) ... get_connections.
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: (168123216) ... get_connections (managed=false): return empty list.
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin AnyData
Apr 26 14:35:44 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'via-rhine')
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): now managed
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): bringing up device.
Apr 26 14:35:44 ubuntu kernel: [  109.492308] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): preparing device.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 26 14:35:44 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:12.0/net/eth0
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Generic
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Gobi
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Option High-Speed
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Huawei
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Longcheer
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 26 14:35:44 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 26 14:35:44 ubuntu NetworkManager: <info>  modem-manager is now available
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Ericsson MBM
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin MotoC
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin Nokia
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin Novatel
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin Option
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin Sierra
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin ZTE
Apr 26 14:35:45 ubuntu avahi-daemon[1238]: Registering new address record for fe80::2e0:4dff:fe4e:b618 on eth0.*.
Apr 26 14:35:46 ubuntu NetworkManager: <info>  dhclient started with pid 1290
Apr 26 14:35:46 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 26 14:35:46 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 26 14:35:46 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 26 14:35:46 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 26 14:35:46 ubuntu kernel: [  111.307623] HDA Intel 0000:80:01.0: setting latency timer to 64
Apr 26 14:35:46 ubuntu kernel: [  111.307630] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
Apr 26 14:35:46 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 26 14:35:46 ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 26 14:35:46 ubuntu dhclient: All rights reserved.
Apr 26 14:35:46 ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 26 14:35:46 ubuntu dhclient: 
Apr 26 14:35:46 ubuntu kernel: [  111.634952] input: HDA Digital PCBeep as /devices/pci0000:80/0000:80:01.0/input/input3
Apr 26 14:35:46 ubuntu gdm-binary[1174]: WARNING: Unable to find users: no seat-id found
Apr 26 14:35:46 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Apr 26 14:35:46 ubuntu dhclient: Listening on LPF/eth0/00:e0:4d:4e:b6:18
Apr 26 14:35:46 ubuntu dhclient: Sending on   LPF/eth0/00:e0:4d:4e:b6:18
Apr 26 14:35:46 ubuntu dhclient: Sending on   Socket/fallback
Apr 26 14:35:48 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 26 14:35:48 ubuntu dhclient: DHCPOFFER of 192.168.1.3 from 192.168.1.1
Apr 26 14:35:48 ubuntu dhclient: DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
Apr 26 14:35:48 ubuntu dhclient: DHCPACK of 192.168.1.3 from 192.168.1.1
Apr 26 14:35:48 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 26 14:35:48 ubuntu NetworkManager: <info>    address 192.168.1.3
Apr 26 14:35:48 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Apr 26 14:35:48 ubuntu NetworkManager: <info>    gateway 192.168.1.1
Apr 26 14:35:48 ubuntu NetworkManager: <info>    nameserver '192.168.1.1'
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 26 14:35:48 ubuntu avahi-daemon[1238]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.3.
Apr 26 14:35:48 ubuntu avahi-daemon[1238]: New relevant interface eth0.IPv4 for mDNS.
Apr 26 14:35:48 ubuntu avahi-daemon[1238]: Registering new address record for 192.168.1.3 on eth0.IPv4.
Apr 26 14:35:48 ubuntu dhclient: bound to 192.168.1.3 -- renewal in 42682 seconds.
Apr 26 14:35:50 ubuntu NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Apr 26 14:35:50 ubuntu NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 26 14:35:50 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr 26 14:35:50 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 26 14:35:54 ubuntu kernel: [  119.720750] eth0: no IPv6 routers present
Apr 26 14:35:55 ubuntu cron[1604]: (CRON) INFO (pidfile fd = 3)
Apr 26 14:35:55 ubuntu cron[1625]: (CRON) STARTUP (fork ok)
Apr 26 14:35:56 ubuntu acpid: starting up with netlink and the input layer
Apr 26 14:35:56 ubuntu cron[1625]: (CRON) INFO (Running @reboot jobs)
Apr 26 14:35:57 ubuntu acpid: 36 rules loaded
Apr 26 14:35:57 ubuntu acpid: waiting for events: event logging is off
Apr 26 14:35:57 ubuntu acpid: client connected from 1415[0:0]
Apr 26 14:35:57 ubuntu acpid: 1 client rule loaded
Apr 26 14:36:00 ubuntu kernel: [  125.851861] lp: driver loaded but no devices found
Apr 26 14:36:01 ubuntu kernel: [  126.514927] ppdev: user-space parallel port driver
Apr 26 14:36:03 ubuntu udev-configure-printer: add /module/lp
Apr 26 14:36:03 ubuntu udev-configure-printer: Failed to get parent
Apr 26 14:36:03 ubuntu kernel: [  128.904294] [drm] Initialized drm 1.1.0 20060810
Apr 26 14:36:04 ubuntu kernel: [  129.720989] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
Apr 26 14:36:04 ubuntu kernel: [  129.882324] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Apr 26 14:36:04 ubuntu kernel: [  129.882355] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 26 14:36:04 ubuntu kernel: [  129.882476] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 26 14:36:05 ubuntu kernel: [  130.684896] irq 10: nobody cared (try booting with the "irqpoll" option)
Apr 26 14:36:05 ubuntu kernel: [  130.684905] Pid: 1896, comm: update-motd-upd Not tainted 2.6.32-21-generic #32-Ubuntu
Apr 26 14:36:05 ubuntu kernel: [  130.684908] Call Trace:
Apr 26 14:36:05 ubuntu kernel: [  130.684919]  [<c0588f42>] ? printk+0x1d/0x23
Apr 26 14:36:05 ubuntu kernel: [  130.684925]  [<c01a14fc>] __report_bad_irq+0x2c/0x90
Apr 26 14:36:05 ubuntu kernel: [  130.684931]  [<c019fc34>] ? handle_IRQ_event+0x54/0x150
Apr 26 14:36:05 ubuntu kernel: [  130.684935]  [<c01a16b0>] note_interrupt+0x150/0x190
Apr 26 14:36:05 ubuntu kernel: [  130.684940]  [<c0106d77>] ? mask_and_ack_8259A+0x57/0xf0
Apr 26 14:36:05 ubuntu kernel: [  130.684944]  [<c01a225c>] handle_level_irq+0xcc/0x100
Apr 26 14:36:05 ubuntu kernel: [  130.684949]  [<c01412f6>] ? entity_tick+0xc6/0x120
Apr 26 14:36:05 ubuntu kernel: [  130.684953]  [<c01059ed>] handle_irq+0x1d/0x30
Apr 26 14:36:05 ubuntu kernel: [  130.684957]  [<c058fa1c>] do_IRQ+0x4c/0xc0
Apr 26 14:36:05 ubuntu kernel: [  130.684962]  [<c0103a30>] common_interrupt+0x30/0x40
Apr 26 14:36:05 ubuntu kernel: [  130.684966]  [<c015301d>] ? __do_softirq+0x4d/0x1b0
Apr 26 14:36:05 ubuntu kernel: [  130.684971]  [<c012a438>] ? default_spin_lock_flags+0x8/0x10
Apr 26 14:36:05 ubuntu kernel: [  130.684976]  [<c058b5af>] ? _spin_lock_irqsave+0x2f/0x50
Apr 26 14:36:05 ubuntu kernel: [  130.684980]  [<c0106c87>] ? enable_8259A_irq+0x47/0x70
Apr 26 14:36:05 ubuntu kernel: [  130.684984]  [<c01a2242>] ? handle_level_irq+0xb2/0x100
Apr 26 14:36:05 ubuntu kernel: [  130.684987]  [<c01531c5>] do_softirq+0x45/0x50
Apr 26 14:36:05 ubuntu kernel: [  130.684990]  [<c0153315>] irq_exit+0x65/0x70
Apr 26 14:36:05 ubuntu kernel: [  130.684994]  [<c058fa25>] do_IRQ+0x55/0xc0
Apr 26 14:36:05 ubuntu kernel: [  130.684998]  [<c0103a30>] common_interrupt+0x30/0x40
Apr 26 14:36:05 ubuntu kernel: [  130.685001] handlers:
Apr 26 14:36:05 ubuntu kernel: [  130.685003] [<c0444960>] (usb_hcd_irq+0x0/0x80)
Apr 26 14:36:05 ubuntu kernel: [  130.685009] [<f806c9d0>] (rhine_interrupt+0x0/0x2c0 [via_rhine])
Apr 26 14:36:05 ubuntu kernel: [  130.685025] Disabling IRQ #10
Apr 26 14:36:19 ubuntu ntpdate[1781]: step time server 91.189.94.4 offset 12.910752 sec
Apr 26 14:36:28 ubuntu gdm-session-worker[2186]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 26 14:36:28 ubuntu init: plymouth-stop pre-start process (2202) terminated with status 1
Apr 26 14:36:47 ubuntu gnome-session[2223]: WARNING: Application 'gnome-settings-daemon.desktop' failed to register before timeout
Apr 26 14:36:55 ubuntu polkitd[2363]: started daemon version 0.96 using authority implementation `local' version `0.96'
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Sucessfully called chroot.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Sucessfully dropped privileges.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Sucessfully limited resources.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Running.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Watchdog thread running.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Canary thread running.
Apr 26 14:37:01 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2373 of process 2373 (n/a) owned by '999' high priority at nice level -11.
Apr 26 14:37:01 ubuntu rtkit-daemon[2375]: Supervising 1 threads of 1 processes of 1 users.
Apr 26 14:37:08 ubuntu pulseaudio[2373]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Apr 26 14:37:09 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2428 of process 2373 (n/a) owned by '999' RT at priority 5.
Apr 26 14:37:09 ubuntu rtkit-daemon[2375]: Supervising 2 threads of 1 processes of 1 users.
Apr 26 14:37:09 ubuntu pulseaudio[2373]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Apr 26 14:37:09 ubuntu kernel: [  181.621040] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Apr 26 14:37:09 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2429 of process 2373 (n/a) owned by '999' RT at priority 5.
Apr 26 14:37:09 ubuntu rtkit-daemon[2375]: Supervising 3 threads of 1 processes of 1 users.
Apr 26 14:37:10 ubuntu pulseaudio[2373]: alsa-source.c: ALSA nos despertó para leer nuevos datos desde el dispositivo, ¡pero en realidad no hay nada para leer!
Apr 26 14:37:10 ubuntu pulseaudio[2373]: alsa-source.c: Lo más probable es que sea un error del controlador ALSA «snd_hda_intel». Por favor, informe esto a los desarrolladores de ALSA.
Apr 26 14:37:10 ubuntu pulseaudio[2373]: alsa-source.c: Nos despertaron con POLLIN puesto -- sin embargo, una llamada a snd_pcm_avail() devolvió 0 u otro valor < min_avail.
Apr 26 14:37:13 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2436 of process 2436 (n/a) owned by '999' high priority at nice level -11.
Apr 26 14:37:13 ubuntu rtkit-daemon[2375]: Supervising 4 threads of 2 processes of 1 users.
Apr 26 14:37:13 ubuntu pulseaudio[2436]: pid.c: Daemon already running.
Apr 26 14:37:15 ubuntu gnome-session[2223]: WARNING: Detected that screensaver has left the bus
Apr 26 14:37:17 ubuntu acpid: client 1415[0:0] has disconnected
Apr 26 14:37:17 ubuntu acpid: client connected from 2478[0:0]
Apr 26 14:37:17 ubuntu acpid: 1 client rule loaded
Apr 26 14:37:18 ubuntu kernel: [  191.213170] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Apr 26 14:37:18 ubuntu kernel: [  191.213200] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 26 14:37:18 ubuntu kernel: [  191.213320] pci 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 26 14:37:23 ubuntu kernel: [  196.179726] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:23 ubuntu kernel: [  196.179730] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:23 ubuntu kernel: [  196.179735] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:23 ubuntu kernel: [  196.179740] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:23 ubuntu kernel: [  196.179746] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6c 00 00 02 00
Apr 26 14:37:23 ubuntu kernel: [  196.179757] end_request: I/O error, dev sr0, sector 1421744
Apr 26 14:37:23 ubuntu kernel: [  196.179762] Buffer I/O error on device sr0, logical block 355436
Apr 26 14:37:23 ubuntu kernel: [  196.179767] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:24 ubuntu kernel: [  196.818327] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:24 ubuntu kernel: [  196.818330] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:24 ubuntu kernel: [  196.818335] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:24 ubuntu kernel: [  196.818340] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:24 ubuntu kernel: [  196.818346] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:24 ubuntu kernel: [  196.818356] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:24 ubuntu kernel: [  196.818361] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:26 ubuntu kernel: [  198.327444] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:26 ubuntu kernel: [  198.327448] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:26 ubuntu kernel: [  198.327453] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:26 ubuntu kernel: [  198.327458] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:26 ubuntu kernel: [  198.327464] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:26 ubuntu kernel: [  198.327475] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:26 ubuntu kernel: [  198.327480] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:27 ubuntu kernel: [  200.107726] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:27 ubuntu kernel: [  200.107731] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:27 ubuntu kernel: [  200.107736] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:27 ubuntu kernel: [  200.107741] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:27 ubuntu kernel: [  200.107747] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:27 ubuntu kernel: [  200.107757] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:27 ubuntu kernel: [  200.107763] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:28 ubuntu kernel: [  200.673404] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:28 ubuntu kernel: [  200.673408] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:28 ubuntu kernel: [  200.673413] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:28 ubuntu kernel: [  200.673418] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:28 ubuntu kernel: [  200.673424] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:28 ubuntu kernel: [  200.673434] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:28 ubuntu kernel: [  200.673439] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:30 ubuntu kernel: [  202.248036] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:30 ubuntu kernel: [  202.248040] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:30 ubuntu kernel: [  202.248045] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:30 ubuntu kernel: [  202.248050] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:30 ubuntu kernel: [  202.248055] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:30 ubuntu kernel: [  202.248066] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:30 ubuntu kernel: [  202.248070] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:30 ubuntu kernel: [  202.813832] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:30 ubuntu kernel: [  202.813836] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:30 ubuntu kernel: [  202.813841] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:30 ubuntu kernel: [  202.813846] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:30 ubuntu kernel: [  202.813851] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:30 ubuntu kernel: [  202.813861] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:30 ubuntu kernel: [  202.813866] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:33 ubuntu kernel: [  206.098273] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:33 ubuntu kernel: [  206.098278] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:33 ubuntu kernel: [  206.098282] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:33 ubuntu kernel: [  206.098287] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:33 ubuntu kernel: [  206.098293] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:33 ubuntu kernel: [  206.098303] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:33 ubuntu kernel: [  206.098308] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:35 ubuntu kernel: [  207.717345] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:35 ubuntu kernel: [  207.717349] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:35 ubuntu kernel: [  207.717354] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:35 ubuntu kernel: [  207.717359] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:35 ubuntu kernel: [  207.717364] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:35 ubuntu kernel: [  207.717374] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:35 ubuntu kernel: [  207.717379] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:37 ubuntu kernel: [  209.443548] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:37 ubuntu kernel: [  209.443552] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:37 ubuntu kernel: [  209.443557] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:37 ubuntu kernel: [  209.443563] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:37 ubuntu kernel: [  209.443569] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:37 ubuntu kernel: [  209.443579] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:37 ubuntu kernel: [  209.443585] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:40 ubuntu kernel: [  212.354665] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:40 ubuntu kernel: [  212.354669] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:40 ubuntu kernel: [  212.354674] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:40 ubuntu kernel: [  212.354679] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:40 ubuntu kernel: [  212.354685] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:40 ubuntu kernel: [  212.354695] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:40 ubuntu kernel: [  212.354702] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:40 ubuntu kernel: [  213.133640] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:40 ubuntu kernel: [  213.133643] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:40 ubuntu kernel: [  213.133648] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:40 ubuntu kernel: [  213.133653] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:40 ubuntu kernel: [  213.133658] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:40 ubuntu kernel: [  213.133668] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:40 ubuntu kernel: [  213.133673] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:42 ubuntu kernel: [  214.785736] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:42 ubuntu kernel: [  214.785741] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:42 ubuntu kernel: [  214.785745] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:42 ubuntu kernel: [  214.785751] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:42 ubuntu kernel: [  214.785756] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:42 ubuntu kernel: [  214.785767] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:42 ubuntu kernel: [  214.785772] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:43 ubuntu kernel: [  215.316135] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:43 ubuntu kernel: [  215.316139] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:43 ubuntu kernel: [  215.316143] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:43 ubuntu kernel: [  215.316148] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:43 ubuntu kernel: [  215.316154] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:43 ubuntu kernel: [  215.316164] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:43 ubuntu kernel: [  215.316168] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:44 ubuntu kernel: [  216.961603] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:44 ubuntu kernel: [  216.961609] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:44 ubuntu kernel: [  216.961614] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:44 ubuntu kernel: [  216.961619] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:44 ubuntu kernel: [  216.961624] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:44 ubuntu kernel: [  216.961634] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:44 ubuntu kernel: [  216.961642] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:46 ubuntu kernel: [  218.604841] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:46 ubuntu kernel: [  218.604845] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:46 ubuntu kernel: [  218.604850] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:46 ubuntu kernel: [  218.604855] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:46 ubuntu kernel: [  218.604861] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:46 ubuntu kernel: [  218.604871] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:46 ubuntu kernel: [  218.604877] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:46 ubuntu gnome-session[2521]: WARNING: Application 'gnome-settings-daemon.desktop' failed to register before timeout
Apr 26 14:37:46 ubuntu kernel: [  219.205709] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:46 ubuntu kernel: [  219.205714] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:46 ubuntu kernel: [  219.205719] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:46 ubuntu kernel: [  219.205724] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:46 ubuntu kernel: [  219.205729] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:46 ubuntu kernel: [  219.205739] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:46 ubuntu kernel: [  219.205745] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:48 ubuntu kernel: [  220.810799] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:48 ubuntu kernel: [  220.810804] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:48 ubuntu kernel: [  220.810809] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:48 ubuntu kernel: [  220.810814] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:48 ubuntu kernel: [  220.810820] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:48 ubuntu kernel: [  220.810830] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:48 ubuntu kernel: [  220.810835] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:49 ubuntu kernel: [  221.376516] sr 2:0:0:0: [sr0] Unhandled sense code
Apr 26 14:37:49 ubuntu kernel: [  221.376520] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 26 14:37:49 ubuntu kernel: [  221.376525] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Apr 26 14:37:49 ubuntu kernel: [  221.376530] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
Apr 26 14:37:49 ubuntu kernel: [  221.376535] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6c 6d 00 00 01 00
Apr 26 14:37:49 ubuntu kernel: [  221.376545] end_request: I/O error, dev sr0, sector 1421748
Apr 26 14:37:49 ubuntu kernel: [  221.376551] Buffer I/O error on device sr0, logical block 355437
Apr 26 14:37:53 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2540 of process 2540 (n/a) owned by '114' high priority at nice level -11.
Apr 26 14:37:53 ubuntu rtkit-daemon[2375]: Supervising 1 threads of 1 processes of 1 users.
Apr 26 14:37:54 ubuntu pulseaudio[2540]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Apr 26 14:37:54 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2541 of process 2540 (n/a) owned by '114' RT at priority 5.
Apr 26 14:37:54 ubuntu rtkit-daemon[2375]: Supervising 2 threads of 1 processes of 1 users.
Apr 26 14:37:54 ubuntu pulseaudio[2540]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Apr 26 14:37:54 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2542 of process 2540 (n/a) owned by '114' RT at priority 5.
Apr 26 14:37:54 ubuntu rtkit-daemon[2375]: Supervising 3 threads of 1 processes of 1 users.
Apr 26 14:38:02 ubuntu gdm-simple-greeter[2533]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Apr 26 14:38:14 ubuntu gdm-session-worker[2536]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 26 14:38:20 ubuntu gdm-session-worker[2536]: pam_sm_authenticate: Called
Apr 26 14:38:20 ubuntu gdm-session-worker[2536]: pam_sm_authenticate: username = [ubuntu]
Apr 26 14:38:21 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2651 of process 2651 (n/a) owned by '999' high priority at nice level -11.
Apr 26 14:38:21 ubuntu rtkit-daemon[2375]: Supervising 4 threads of 2 processes of 2 users.
Apr 26 14:38:21 ubuntu pulseaudio[2651]: pid.c: Stale PID file, overwriting.
Apr 26 14:38:22 ubuntu pulseaudio[2651]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2666 of process 2651 (n/a) owned by '999' RT at priority 5.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Supervising 5 threads of 2 processes of 2 users.
Apr 26 14:38:22 ubuntu pulseaudio[2651]: alsa-util.c: Disabling timer-based scheduling because high-resolution timers are not available from the kernel.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2668 of process 2651 (n/a) owned by '999' RT at priority 5.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Supervising 6 threads of 2 processes of 2 users.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2670 of process 2670 (n/a) owned by '999' high priority at nice level -11.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Supervising 7 threads of 3 processes of 2 users.
Apr 26 14:38:22 ubuntu pulseaudio[2670]: pid.c: Daemon already running.
Apr 26 14:39:41 ubuntu AptDaemon: INFO: Initializing daemon


and this one is the "daemon.log":
> Apr 26 14:35:36 ubuntu init: ubiquity main process (1156) terminated with status 1
Apr 26 14:35:40 ubuntu avahi-daemon[1238]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Apr 26 14:35:40 ubuntu avahi-daemon[1238]: Successfully dropped root privileges.
Apr 26 14:35:40 ubuntu avahi-daemon[1238]: avahi-daemon 0.6.25 starting up.
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Successfully called chroot().
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Successfully dropped remaining capabilities.
Apr 26 14:35:41 ubuntu avahi-daemon[1243]: chroot.c: open() failed: No such file or directory
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Failed to open /etc/resolv.conf: Invalid argument
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: No service file found in /etc/avahi/services.
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Network interface enumeration completed.
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 26 14:35:41 ubuntu avahi-daemon[1238]: Server startup complete. Host name is ubuntu.local. Local service cookie is 2957382472.
Apr 26 14:35:42 ubuntu NetworkManager: <info>  starting...
Apr 26 14:35:42 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Apr 26 14:35:43 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0)
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Apr 26 14:35:43 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 26 14:35:43 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 26 14:35:43 ubuntu NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Apr 26 14:35:43 ubuntu NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: (168123216) ... get_connections.
Apr 26 14:35:43 ubuntu NetworkManager:    SCPlugin-Ifupdown: (168123216) ... get_connections (managed=false): return empty list.
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin AnyData
Apr 26 14:35:44 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 0
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): carrier is OFF
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'via-rhine')
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): now managed
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): bringing up device.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): preparing device.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 26 14:35:44 ubuntu NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:12.0/net/eth0
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Generic
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Gobi
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Option High-Speed
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Huawei
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Longcheer
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 26 14:35:44 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 26 14:35:44 ubuntu NetworkManager: <info>  modem-manager is now available
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 26 14:35:44 ubuntu NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr 26 14:35:44 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr 26 14:35:44 ubuntu modem-manager: Loaded plugin Ericsson MBM
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin MotoC
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin Nokia
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin Novatel
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin Option
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin Sierra
Apr 26 14:35:45 ubuntu modem-manager: Loaded plugin ZTE
Apr 26 14:35:45 ubuntu avahi-daemon[1238]: Registering new address record for fe80::2e0:4dff:fe4e:b618 on eth0.*.
Apr 26 14:35:46 ubuntu NetworkManager: <info>  dhclient started with pid 1290
Apr 26 14:35:46 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 26 14:35:46 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 26 14:35:46 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 26 14:35:46 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 26 14:35:46 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 26 14:35:46 ubuntu dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 26 14:35:46 ubuntu dhclient: All rights reserved.
Apr 26 14:35:46 ubuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 26 14:35:46 ubuntu dhclient: 
Apr 26 14:35:46 ubuntu gdm-binary[1174]: WARNING: Unable to find users: no seat-id found
Apr 26 14:35:46 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Apr 26 14:35:46 ubuntu dhclient: Listening on LPF/eth0/00:e0:4d:4e:b6:18
Apr 26 14:35:46 ubuntu dhclient: Sending on   LPF/eth0/00:e0:4d:4e:b6:18
Apr 26 14:35:46 ubuntu dhclient: Sending on   Socket/fallback
Apr 26 14:35:48 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 26 14:35:48 ubuntu dhclient: DHCPOFFER of 192.168.1.3 from 192.168.1.1
Apr 26 14:35:48 ubuntu dhclient: DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
Apr 26 14:35:48 ubuntu dhclient: DHCPACK of 192.168.1.3 from 192.168.1.1
Apr 26 14:35:48 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 26 14:35:48 ubuntu NetworkManager: <info>    address 192.168.1.3
Apr 26 14:35:48 ubuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Apr 26 14:35:48 ubuntu NetworkManager: <info>    gateway 192.168.1.1
Apr 26 14:35:48 ubuntu NetworkManager: <info>    nameserver '192.168.1.1'
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 26 14:35:48 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 26 14:35:48 ubuntu avahi-daemon[1238]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.3.
Apr 26 14:35:48 ubuntu avahi-daemon[1238]: New relevant interface eth0.IPv4 for mDNS.
Apr 26 14:35:48 ubuntu avahi-daemon[1238]: Registering new address record for 192.168.1.3 on eth0.IPv4.
Apr 26 14:35:48 ubuntu dhclient: bound to 192.168.1.3 -- renewal in 42682 seconds.
Apr 26 14:35:50 ubuntu NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Apr 26 14:35:50 ubuntu NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 26 14:35:50 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr 26 14:35:50 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 26 14:35:56 ubuntu acpid: starting up with netlink and the input layer
Apr 26 14:35:57 ubuntu acpid: 36 rules loaded
Apr 26 14:35:57 ubuntu acpid: waiting for events: event logging is off
Apr 26 14:35:57 ubuntu acpid: client connected from 1415[0:0]
Apr 26 14:35:57 ubuntu acpid: 1 client rule loaded
Apr 26 14:36:19 ubuntu ntpdate[1781]: step time server 91.189.94.4 offset 12.910752 sec
Apr 26 14:36:28 ubuntu gdm-session-worker[2186]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 26 14:36:28 ubuntu init: plymouth-stop pre-start process (2202) terminated with status 1
Apr 26 14:36:47 ubuntu gnome-session[2223]: WARNING: Application 'gnome-settings-daemon.desktop' failed to register before timeout
Apr 26 14:36:55 ubuntu polkitd[2363]: started daemon version 0.96 using authority implementation `local' version `0.96'
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Sucessfully called chroot.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Sucessfully dropped privileges.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Sucessfully limited resources.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Running.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Watchdog thread running.
Apr 26 14:36:57 ubuntu rtkit-daemon[2375]: Canary thread running.
Apr 26 14:37:01 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2373 of process 2373 (n/a) owned by '999' high priority at nice level -11.
Apr 26 14:37:01 ubuntu rtkit-daemon[2375]: Supervising 1 threads of 1 processes of 1 users.
Apr 26 14:37:09 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2428 of process 2373 (n/a) owned by '999' RT at priority 5.
Apr 26 14:37:09 ubuntu rtkit-daemon[2375]: Supervising 2 threads of 1 processes of 1 users.
Apr 26 14:37:09 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2429 of process 2373 (n/a) owned by '999' RT at priority 5.
Apr 26 14:37:09 ubuntu rtkit-daemon[2375]: Supervising 3 threads of 1 processes of 1 users.
Apr 26 14:37:13 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2436 of process 2436 (n/a) owned by '999' high priority at nice level -11.
Apr 26 14:37:13 ubuntu rtkit-daemon[2375]: Supervising 4 threads of 2 processes of 1 users.
Apr 26 14:37:15 ubuntu gnome-session[2223]: WARNING: Detected that screensaver has left the bus
Apr 26 14:37:17 ubuntu acpid: client 1415[0:0] has disconnected
Apr 26 14:37:17 ubuntu acpid: client connected from 2478[0:0]
Apr 26 14:37:17 ubuntu acpid: 1 client rule loaded
Apr 26 14:37:46 ubuntu gnome-session[2521]: WARNING: Application 'gnome-settings-daemon.desktop' failed to register before timeout
Apr 26 14:37:53 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2540 of process 2540 (n/a) owned by '114' high priority at nice level -11.
Apr 26 14:37:53 ubuntu rtkit-daemon[2375]: Supervising 1 threads of 1 processes of 1 users.
Apr 26 14:37:54 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2541 of process 2540 (n/a) owned by '114' RT at priority 5.
Apr 26 14:37:54 ubuntu rtkit-daemon[2375]: Supervising 2 threads of 1 processes of 1 users.
Apr 26 14:37:54 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2542 of process 2540 (n/a) owned by '114' RT at priority 5.
Apr 26 14:37:54 ubuntu rtkit-daemon[2375]: Supervising 3 threads of 1 processes of 1 users.
Apr 26 14:38:02 ubuntu gdm-simple-greeter[2533]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Apr 26 14:38:14 ubuntu gdm-session-worker[2536]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Apr 26 14:38:20 ubuntu gdm-session-worker[2536]: pam_sm_authenticate: Called
Apr 26 14:38:20 ubuntu gdm-session-worker[2536]: pam_sm_authenticate: username = [ubuntu]
Apr 26 14:38:21 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2651 of process 2651 (n/a) owned by '999' high priority at nice level -11.
Apr 26 14:38:21 ubuntu rtkit-daemon[2375]: Supervising 4 threads of 2 processes of 2 users.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2666 of process 2651 (n/a) owned by '999' RT at priority 5.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Supervising 5 threads of 2 processes of 2 users.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2668 of process 2651 (n/a) owned by '999' RT at priority 5.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Supervising 6 threads of 2 processes of 2 users.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Sucessfully made thread 2670 of process 2670 (n/a) owned by '999' high priority at nice level -11.
Apr 26 14:38:22 ubuntu rtkit-daemon[2375]: Supervising 7 threads of 3 processes of 2 users.
Apr 26 14:39:41 ubuntu AptDaemon: INFO: Initializing daemon
Apr 26 14:44:42 ubuntu AptDaemon: INFO: Quiting due to inactivity
Apr 26 14:44:42 ubuntu AptDaemon: INFO: Shutdown was requested


Im trying to install Lucid from the desktop.

---

### Post by RBeaber on 2010-04-29
Atari130XE:
     You said you made it to the desktop.  What did you do to get there?  I'm having the same issue with the release version.  So far none of the suggestions have worked, either with the live boot or the install option.

Thanks,

-Rick

---

