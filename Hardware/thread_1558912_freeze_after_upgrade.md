---
title: "freeze after upgrade"
date: 2010-08-22
forum: Hardware
---

### Post by libertyblues on 2010-08-22
Hey how's it going? I have an IBM Thinkpad T43. I installed 10.04 just fine and ran it for a while, and then when I got an internet connection I went to synaptic and marked all upgrades. I don't know if it's the new kernel or what, but after the upgrade, occasionally my screen will go blank, the mouse cursor is still visible, but everything's frozen. I reboot, it happens again. I reinstalled 10.04 and everything works fine again until I mark all upgrades. Here's a /var/log/messages if that helps:

Aug 22 19:46:23 linksys404 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="693" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug 22 19:49:17 linksys404 kernel: [  505.434261] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Aug 22 19:49:17 linksys404 kernel: [  505.435172] SGI XFS Quota Management subsystem
Aug 22 19:49:17 linksys404 kernel: [  505.530895] JFS: nTxBlock = 3970, nTxLock = 31761
Aug 22 19:49:17 linksys404 kernel: [  505.628965] NTFS driver 2.1.29 [Flags: R/O MODULE].
Aug 22 19:49:17 linksys404 kernel: [  505.663559] QNX4 filesystem 0.2.3 registered.
Aug 22 19:49:17 linksys404 kernel: [  505.745887] Btrfs loaded
Aug 22 19:49:17 linksys404 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Aug 22 19:49:18 linksys404 50mounted-tests: debug: mounted as ntfs-3g filesystem
Aug 22 19:49:18 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 22 19:49:18 linksys404 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Aug 22 19:49:18 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 22 19:49:18 linksys404 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Aug 22 19:49:18 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 22 19:49:18 linksys404 macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Aug 22 19:49:18 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 22 19:49:18 linksys404 20microsoft: debug: /dev/sda1 is a NTFS partition
Aug 22 19:49:19 linksys404 20microsoft: result: /dev/sda1:Microsoft Windows XP Professional:Windows:chain
Aug 22 19:49:19 linksys404 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Aug 22 19:49:19 linksys404 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 22 19:49:19 linksys404 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug 22 19:49:19 linksys404 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Aug 22 19:49:19 linksys404 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 22 19:49:19 linksys404 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Aug 22 19:49:19 linksys404 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Aug 22 19:49:19 linksys404 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 22 19:49:19 linksys404 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Aug 22 19:49:19 linksys404 kernel: [  508.025025] kjournald starting.  Commit interval 5 seconds
Aug 22 19:49:19 linksys404 kernel: [  508.025044] EXT3-fs: mounted filesystem with ordered data mode.
Aug 22 19:49:19 linksys404 50mounted-tests: debug: mounted as ext3 filesystem
Aug 22 19:49:19 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 22 19:49:20 linksys404 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Aug 22 19:49:20 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 22 19:49:20 linksys404 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Aug 22 19:49:20 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 22 19:49:20 linksys404 macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Aug 22 19:49:20 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 22 19:49:20 linksys404 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Aug 22 19:49:20 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 22 19:49:20 linksys404 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Aug 22 19:49:20 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 22 19:49:20 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Aug 22 19:49:20 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Aug 22 19:49:20 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Aug 22 19:49:20 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Aug 22 19:50:31 linksys404 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Aug 22 19:50:31 linksys404 50mounted-tests: debug: mounted as ntfs-3g filesystem
Aug 22 19:50:31 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 22 19:50:31 linksys404 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Aug 22 19:50:31 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 22 19:50:31 linksys404 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Aug 22 19:50:31 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 22 19:50:31 linksys404 macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Aug 22 19:50:31 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 22 19:50:31 linksys404 20microsoft: debug: /dev/sda1 is a NTFS partition
Aug 22 19:50:31 linksys404 20microsoft: result: /dev/sda1:Microsoft Windows XP Professional:Windows:chain
Aug 22 19:50:31 linksys404 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Aug 22 19:50:32 linksys404 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 22 19:50:32 linksys404 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug 22 19:50:32 linksys404 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Aug 22 19:50:32 linksys404 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 22 19:50:32 linksys404 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Aug 22 19:50:32 linksys404 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Aug 22 19:50:32 linksys404 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Aug 22 19:50:32 linksys404 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda6
Aug 22 19:50:32 linksys404 kernel: [  580.282968] kjournald starting.  Commit interval 5 seconds
Aug 22 19:50:32 linksys404 kernel: [  580.282994] EXT3-fs: mounted filesystem with ordered data mode.
Aug 22 19:50:32 linksys404 50mounted-tests: debug: mounted as ext3 filesystem
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Aug 22 19:50:32 linksys404 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Aug 22 19:50:32 linksys404 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Aug 22 19:50:32 linksys404 macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Aug 22 19:50:32 linksys404 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Aug 22 19:50:32 linksys404 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Aug 22 19:50:32 linksys404 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Aug 22 05:38:32 linksys404 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug 22 05:38:32 linksys404 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="794" x-info="http://www.rsyslog.com"] (re)start
Aug 22 05:38:32 linksys404 rsyslogd: rsyslogd's groupid changed to 103
Aug 22 05:38:32 linksys404 rsyslogd: rsyslogd's userid changed to 101
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 (Ubuntu 2.6.32-24.41-generic 2.6.32.15+drm33.5)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] KERNEL supported cpus:
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   Intel GenuineIntel
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   AMD AuthenticAMD
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   NSC Geode by NSC
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   Cyrix CyrixInstead
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   Centaur CentaurHauls
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   Transmeta GenuineTMx86
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   Transmeta TransmetaCPU
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   UMC UMC UMC UMC
Aug 22 05:38:32 linksys404 kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fee0000 (usable)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 000000001fee0000 - 000000001fef5000 (ACPI data)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 000000001fef5000 - 000000001ff00000 (ACPI NVS)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] DMI present.
Aug 22 05:38:32 linksys404 kernel: [    0.000000] last_pfn = 0x1fee0 max_arch_pfn = 0x100000
Aug 22 05:38:32 linksys404 kernel: [    0.000000] PAT not supported by CPU.
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Scanning 1 areas for low memory corruption
Aug 22 05:38:32 linksys404 kernel: [    0.000000] modified physical RAM map:
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 0000000000100000 - 000000001fee0000 (usable)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 000000001fee0000 - 000000001fef5000 (ACPI data)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 000000001fef5000 - 000000001ff00000 (ACPI NVS)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 000000001ff00000 - 0000000020000000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001fee0000
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Aug 22 05:38:32 linksys404 kernel: [    0.000000] RAMDISK: 177cf000 - 17f67ba6
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: RSDP 000f6c10 00024 (v02 IBM   )
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: XSDT 1fee6ff2 0005C (v01 IBM    TP-1Y    00001220  LTP 00000000)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: FACP 1fee7100 000F4 (v03 IBM    TP-1Y    00001220 IBM  00000001)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20090903/tbfadt-526)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 000000000000102C/0 (20090903/tbfadt-557)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: DSDT 1fee72e7 0DB08 (v01 IBM    TP-1Y    00001220 MSFT 0100000E)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: FACS 1fef6000 00040
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: SSDT 1fee72b4 00033 (v01 IBM    TP-1Y    00001220 MSFT 0100000E)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: ECDT 1fef4def 00052 (v01 IBM    TP-1Y    00001220 IBM  00000001)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: TCPA 1fef4e41 00032 (v01 IBM    TP-1Y    00001220 PTL  00000001)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: APIC 1fef4e73 0005A (v01 IBM    TP-1Y    00001220 IBM  00000001)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: MCFG 1fef4ecd 0003E (v01 IBM    TP-1Y    00001220 IBM  00000001)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: BOOT 1fef4fd8 00028 (v01 IBM    TP-1Y    00001220  LTP 00000001)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] 0MB HIGHMEM available.
Aug 22 05:38:32 linksys404 kernel: [    0.000000] 510MB LOWMEM available.
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   mapped low ram: 0 - 1fee0000
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   low ram: 0 - 1fee0000
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   node 0 low ram: 00000000 - 1fee0000
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   node 0 bootmap 00008000 - 0000bfdc
Aug 22 05:38:32 linksys404 kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fee0000]
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   #4 [00177cf000 - 0017f67ba6]          RAMDISK ==> [00177cf000 - 0017f67ba6]
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   #6 [00008de000 - 00008e1128]              BRK ==> [00008de000 - 00008e1128]
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Zone PFN ranges:
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   Normal   0x00001000 -> 0x0001fee0
Aug 22 05:38:32 linksys404 kernel: [    0.000000]   HighMem  0x0001fee0 -> 0x0001fee0
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Movable zone start PFN for each node
Aug 22 05:38:32 linksys404 kernel: [    0.000000] early_node_map[3] active PFN ranges
Aug 22 05:38:32 linksys404 kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Aug 22 05:38:32 linksys404 kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Aug 22 05:38:32 linksys404 kernel: [    0.000000]     0: 0x00000100 -> 0x0001fee0
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Using APIC driver default
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug 22 05:38:32 linksys404 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 22 05:38:32 linksys404 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Aug 22 05:38:32 linksys404 kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Aug 22 05:38:32 linksys404 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug 22 05:38:32 linksys404 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Aug 22 05:38:32 linksys404 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Aug 22 05:38:32 linksys404 kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Aug 22 05:38:32 linksys404 kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug 22 05:38:32 linksys404 kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Aug 22 05:38:32 linksys404 kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u4194304
Aug 22 05:38:32 linksys404 kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
Aug 22 05:38:32 linksys404 kernel: [    0.000000] pcpu-alloc: [0] 0 
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129661
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=b106bc79-78a4-4448-b886-64a0b04e8d95 ro quiet splash
Aug 22 05:38:32 linksys404 kernel: [    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Initializing CPU#0
Aug 22 05:38:32 linksys404 kernel: [    0.000000] allocated 2615680 bytes of page_cgroup
Aug 22 05:38:32 linksys404 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Memory: 499268k/523136k available (4679k kernel code, 23008k reserved, 2124k data, 660k init, 0k highmem)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] virtual kernel memory layout:
Aug 22 05:38:32 linksys404 kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]     vmalloc : 0xe06e0000 - 0xff7fe000   ( 497 MB)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdfee0000   ( 510 MB)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
Aug 22 05:38:32 linksys404 kernel: [    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Aug 22 05:38:32 linksys404 kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Hierarchical RCU implementation.
Aug 22 05:38:32 linksys404 kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Extended CMOS year: 2000
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Console: colour VGA+ 80x25
Aug 22 05:38:32 linksys404 kernel: [    0.000000] console [tty0] enabled
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Fast TSC calibration using PIT
Aug 22 05:38:32 linksys404 kernel: [    0.000000] Detected 1861.896 MHz processor.
Aug 22 05:38:32 linksys404 kernel: [    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3723.79 BogoMIPS (lpj=7447584)
Aug 22 05:38:32 linksys404 kernel: [    0.008023] Security Framework initialized
Aug 22 05:38:32 linksys404 kernel: [    0.008049] AppArmor: AppArmor initialized
Aug 22 05:38:32 linksys404 kernel: [    0.008057] Mount-cache hash table entries: 512
Aug 22 05:38:32 linksys404 kernel: [    0.008184] Initializing cgroup subsys ns
Aug 22 05:38:32 linksys404 kernel: [    0.008189] Initializing cgroup subsys cpuacct
Aug 22 05:38:32 linksys404 kernel: [    0.008193] Initializing cgroup subsys memory
Aug 22 05:38:32 linksys404 kernel: [    0.008203] Initializing cgroup subsys devices
Aug 22 05:38:32 linksys404 kernel: [    0.008206] Initializing cgroup subsys freezer
Aug 22 05:38:32 linksys404 kernel: [    0.008208] Initializing cgroup subsys net_cls
Aug 22 05:38:32 linksys404 kernel: [    0.008231] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 22 05:38:32 linksys404 kernel: [    0.008235] CPU: L2 cache: 2048K
Aug 22 05:38:32 linksys404 kernel: [    0.008239] mce: CPU supports 5 MCE banks
Aug 22 05:38:32 linksys404 kernel: [    0.008249] CPU0: Thermal monitoring enabled (TM2)
Aug 22 05:38:32 linksys404 kernel: [    0.008258] Performance Events: p6 PMU driver.
Aug 22 05:38:32 linksys404 kernel: [    0.008275] ... version:                0
Aug 22 05:38:32 linksys404 kernel: [    0.008277] ... bit width:              32
Aug 22 05:38:32 linksys404 kernel: [    0.008280] ... generic registers:      2
Aug 22 05:38:32 linksys404 kernel: [    0.008282] ... value mask:             00000000ffffffff
Aug 22 05:38:32 linksys404 kernel: [    0.008284] ... max period:             000000007fffffff
Aug 22 05:38:32 linksys404 kernel: [    0.008286] ... fixed-purpose events:   0
Aug 22 05:38:32 linksys404 kernel: [    0.008289] ... event mask:             0000000000000003
Aug 22 05:38:32 linksys404 kernel: [    0.008293] Checking 'hlt' instruction... OK.
Aug 22 05:38:32 linksys404 kernel: [    0.024853] SMP alternatives: switching to UP code
Aug 22 05:38:32 linksys404 kernel: [    0.032080] Freeing SMP alternatives: 19k freed
Aug 22 05:38:32 linksys404 kernel: [    0.032088] ACPI: Core revision 20090903
Aug 22 05:38:32 linksys404 kernel: [    0.056009] ftrace: converting mcount calls to 0f 1f 44 00 00
Aug 22 05:38:32 linksys404 kernel: [    0.056015] ftrace: allocating 21780 entries in 43 pages
Aug 22 05:38:32 linksys404 kernel: [    0.060072] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 22 05:38:32 linksys404 kernel: [    0.060444] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 22 05:38:32 linksys404 kernel: [    0.103227] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
Aug 22 05:38:32 linksys404 kernel: [    0.104001] Brought up 1 CPUs
Aug 22 05:38:32 linksys404 kernel: [    0.104001] Total of 1 processors activated (3723.79 BogoMIPS).
Aug 22 05:38:32 linksys404 kernel: [    0.104001] devtmpfs: initialized
Aug 22 05:38:32 linksys404 kernel: [    0.104001] regulator: core version 0.5
Aug 22 05:38:32 linksys404 kernel: [    0.104001] Time:  5:38:09  Date: 08/22/10
Aug 22 05:38:32 linksys404 kernel: [    0.104001] NET: Registered protocol family 16
Aug 22 05:38:32 linksys404 kernel: [    0.104001] EISA bus registered
Aug 22 05:38:32 linksys404 kernel: [    0.104001] ACPI: bus type pci registered
Aug 22 05:38:32 linksys404 kernel: [    0.104001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Aug 22 05:38:32 linksys404 kernel: [    0.104001] PCI: MCFG area at e0000000 reserved in E820
Aug 22 05:38:32 linksys404 kernel: [    0.104001] PCI: Using MMCONFIG for extended config space
Aug 22 05:38:32 linksys404 kernel: [    0.104001] PCI: Using configuration type 1 for base access
Aug 22 05:38:32 linksys404 kernel: [    0.104001] bio: create slab <bio-0> at 0
Aug 22 05:38:32 linksys404 kernel: [    0.104001] ACPI: EC: EC description table is found, configuring boot EC
Aug 22 05:38:32 linksys404 kernel: [    0.113302] ACPI: Interpreter enabled
Aug 22 05:38:32 linksys404 kernel: [    0.113311] ACPI: (supports S0 S3 S4 S5)
Aug 22 05:38:32 linksys404 kernel: [    0.113335] ACPI: Using IOAPIC for interrupt routing
Aug 22 05:38:32 linksys404 kernel: [    0.121934] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Aug 22 05:38:32 linksys404 kernel: [    0.121934] ACPI: Power Resource [PUBS] (on)
Aug 22 05:38:32 linksys404 kernel: [    0.125132] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Aug 22 05:38:32 linksys404 kernel: [    0.125159] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 22 05:38:32 linksys404 kernel: [    0.125262] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Aug 22 05:38:32 linksys404 kernel: [    0.125266] pci 0000:00:01.0: PME# disabled
Aug 22 05:38:32 linksys404 kernel: [    0.125380] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug 22 05:38:32 linksys404 kernel: [    0.125385] pci 0000:00:1c.0: PME# disabled
Aug 22 05:38:32 linksys404 kernel: [    0.125476] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Aug 22 05:38:32 linksys404 kernel: [    0.125481] pci 0000:00:1c.2: PME# disabled
Aug 22 05:38:32 linksys404 kernel: [    0.125850] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Aug 22 05:38:32 linksys404 kernel: [    0.125856] pci 0000:00:1d.7: PME# disabled
Aug 22 05:38:32 linksys404 kernel: [    0.126024] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
Aug 22 05:38:32 linksys404 kernel: [    0.126029] pci 0000:00:1e.2: PME# disabled
Aug 22 05:38:32 linksys404 kernel: [    0.126122] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
Aug 22 05:38:32 linksys404 kernel: [    0.126127] pci 0000:00:1e.3: PME# disabled
Aug 22 05:38:32 linksys404 kernel: [    0.126223] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Aug 22 05:38:32 linksys404 kernel: [    0.126228] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Aug 22 05:38:32 linksys404 kernel: [    0.126232] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 1600-167f
Aug 22 05:38:32 linksys404 kernel: [    0.126237] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 15e0-15ef
Aug 22 05:38:32 linksys404 kernel: [    0.126342] pci 0000:00:1f.2: PME# supported from D3hot
Aug 22 05:38:32 linksys404 kernel: [    0.126346] pci 0000:00:1f.2: PME# disabled
Aug 22 05:38:32 linksys404 kernel: [    0.126744] pci 0000:02:00.0: PME# supported from D3hot D3cold
Aug 22 05:38:32 linksys404 kernel: [    0.126750] pci 0000:02:00.0: PME# disabled
Aug 22 05:38:32 linksys404 kernel: [    0.126970] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug 22 05:38:32 linksys404 kernel: [    0.126976] pci 0000:04:00.0: PME# disabled
Aug 22 05:38:32 linksys404 kernel: [    0.128177] pci 0000:00:1e.0: transparent bridge
Aug 22 05:38:32 linksys404 kernel: [    0.133201] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 05:38:32 linksys404 kernel: [    0.133397] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 05:38:32 linksys404 kernel: [    0.133591] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 05:38:32 linksys404 kernel: [    0.133785] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 05:38:32 linksys404 kernel: [    0.133978] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 05:38:32 linksys404 kernel: [    0.134171] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 05:38:32 linksys404 kernel: [    0.134365] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 05:38:32 linksys404 kernel: [    0.134562] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Aug 22 05:38:32 linksys404 kernel: [    0.134709] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Aug 22 05:38:32 linksys404 kernel: [    0.134713] vgaarb: loaded
Aug 22 05:38:32 linksys404 kernel: [    0.134836] SCSI subsystem initialized
Aug 22 05:38:32 linksys404 kernel: [    0.134959] usbcore: registered new interface driver usbfs
Aug 22 05:38:32 linksys404 kernel: [    0.134972] usbcore: registered new interface driver hub
Aug 22 05:38:32 linksys404 kernel: [    0.134998] usbcore: registered new device driver usb
Aug 22 05:38:32 linksys404 kernel: [    0.135125] ACPI: WMI: Mapper loaded
Aug 22 05:38:32 linksys404 kernel: [    0.135127] PCI: Using ACPI for IRQ routing
Aug 22 05:38:32 linksys404 kernel: [    0.135207] Expanded resource reserved due to conflict with Adapter ROM
Aug 22 05:38:32 linksys404 kernel: [    0.135296] NetLabel: Initializing
Aug 22 05:38:32 linksys404 kernel: [    0.135299] NetLabel:  domain hash size = 128
Aug 22 05:38:32 linksys404 kernel: [    0.135300] NetLabel:  protocols = UNLABELED CIPSOv4
Aug 22 05:38:32 linksys404 kernel: [    0.135315] NetLabel:  unlabeled traffic allowed by default
Aug 22 05:38:32 linksys404 kernel: [    0.135468] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Aug 22 05:38:32 linksys404 kernel: [    0.135475] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug 22 05:38:32 linksys404 kernel: [    0.135481] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Aug 22 05:38:32 linksys404 kernel: [    0.140019] Switching to clocksource tsc
Aug 22 05:38:32 linksys404 kernel: [    0.142113] AppArmor: AppArmor Filesystem Enabled
Aug 22 05:38:32 linksys404 kernel: [    0.142127] pnp: PnP ACPI init
Aug 22 05:38:32 linksys404 kernel: [    0.142140] ACPI: bus type pnp registered
Aug 22 05:38:32 linksys404 kernel: [    0.145485] pnp: PnP ACPI: found 13 devices
Aug 22 05:38:32 linksys404 kernel: [    0.145488] ACPI: ACPI bus type pnp unregistered
Aug 22 05:38:32 linksys404 kernel: [    0.145491] PnPBIOS: Disabled by ACPI PNP
Aug 22 05:38:32 linksys404 kernel: [    0.145506] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145510] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145513] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145517] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145520] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145523] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145527] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145530] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145534] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145537] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145540] system 00:00: iomem range 0xec000-0xeffff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145544] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145547] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145551] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145559] system 00:02: ioport range 0x1000-0x107f has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145562] system 00:02: ioport range 0x1180-0x11bf has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145565] system 00:02: ioport range 0x15e0-0x15ef has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145569] system 00:02: ioport range 0x1600-0x1641 has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145572] system 00:02: ioport range 0x1644-0x167f has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145576] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145579] system 00:02: iomem range 0xf0008000-0xf000bfff has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145582] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145586] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.145589] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
Aug 22 05:38:32 linksys404 kernel: [    0.180323] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Aug 22 05:38:32 linksys404 kernel: [    0.180327] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
Aug 22 05:38:32 linksys404 kernel: [    0.180332] pci 0000:00:01.0:   MEM window: 0xa8100000-0xa81fffff
Aug 22 05:38:32 linksys404 kernel: [    0.180336] pci 0000:00:01.0:   PREFETCH window: 0xc0000000-0xc7ffffff
Aug 22 05:38:32 linksys404 kernel: [    0.180341] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Aug 22 05:38:32 linksys404 kernel: [    0.180345] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff
Aug 22 05:38:32 linksys404 kernel: [    0.180351] pci 0000:00:1c.0:   MEM window: 0xa8200000-0xa82fffff
Aug 22 05:38:32 linksys404 kernel: [    0.180357] pci 0000:00:1c.0:   PREFETCH window: 0x00000020000000-0x000000201fffff
Aug 22 05:38:32 linksys404 kernel: [    0.180365] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
Aug 22 05:38:32 linksys404 kernel: [    0.180369] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
Aug 22 05:38:32 linksys404 kernel: [    0.180376] pci 0000:00:1c.2:   MEM window: 0xa8300000-0xa83fffff
Aug 22 05:38:32 linksys404 kernel: [    0.180381] pci 0000:00:1c.2:   PREFETCH window: 0x000000c8000000-0x000000c80fffff
Aug 22 05:38:32 linksys404 kernel: [    0.180391] pci 0000:04:00.0: CardBus bridge, secondary bus 0000:05
Aug 22 05:38:32 linksys404 kernel: [    0.180394] pci 0000:04:00.0:   IO window: 0x005000-0x0050ff
Aug 22 05:38:32 linksys404 kernel: [    0.180400] pci 0000:04:00.0:   IO window: 0x005400-0x0054ff
Aug 22 05:38:32 linksys404 kernel: [    0.180406] pci 0000:04:00.0:   PREFETCH window: 0xd0000000-0xd3ffffff
Aug 22 05:38:32 linksys404 kernel: [    0.180413] pci 0000:04:00.0:   MEM window: 0xac000000-0xafffffff
Aug 22 05:38:32 linksys404 kernel: [    0.180419] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
Aug 22 05:38:32 linksys404 kernel: [    0.180423] pci 0000:00:1e.0:   IO window: 0x5000-0x8fff
Aug 22 05:38:32 linksys404 kernel: [    0.180429] pci 0000:00:1e.0:   MEM window: 0xa8400000-0xb7ffffff
Aug 22 05:38:32 linksys404 kernel: [    0.180435] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000d7ffffff
Aug 22 05:38:32 linksys404 kernel: [    0.180458] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 22 05:38:32 linksys404 kernel: [    0.180477] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Aug 22 05:38:32 linksys404 kernel: [    0.180498] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Aug 22 05:38:32 linksys404 kernel: [    0.180524] pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 22 05:38:32 linksys404 kernel: [    0.180622] NET: Registered protocol family 2
Aug 22 05:38:32 linksys404 kernel: [    0.180714] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Aug 22 05:38:32 linksys404 kernel: [    0.180989] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Aug 22 05:38:32 linksys404 kernel: [    0.181095] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Aug 22 05:38:32 linksys404 kernel: [    0.181191] TCP: Hash tables configured (established 16384 bind 16384)
Aug 22 05:38:32 linksys404 kernel: [    0.181194] TCP reno registered
Aug 22 05:38:32 linksys404 kernel: [    0.181258] NET: Registered protocol family 1
Aug 22 05:38:32 linksys404 kernel: [    0.181433] Simple Boot Flag at 0x35 set to 0x1
Aug 22 05:38:32 linksys404 kernel: [    0.181502] cpufreq-nforce2: No nForce2 chipset.
Aug 22 05:38:32 linksys404 kernel: [    0.181531] Scanning for low memory corruption every 60 seconds
Aug 22 05:38:32 linksys404 kernel: [    0.181651] audit: initializing netlink socket (disabled)
Aug 22 05:38:32 linksys404 kernel: [    0.181664] type=2000 audit(1282455489.179:1): initialized
Aug 22 05:38:32 linksys404 kernel: [    0.192831] Trying to unpack rootfs image as initramfs...
Aug 22 05:38:32 linksys404 kernel: [    0.204356] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 22 05:38:32 linksys404 kernel: [    0.209811] VFS: Disk quotas dquot_6.5.2
Aug 22 05:38:32 linksys404 kernel: [    0.209880] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 22 05:38:32 linksys404 kernel: [    0.210522] fuse init (API version 7.13)
Aug 22 05:38:32 linksys404 kernel: [    0.210613] msgmni has been set to 976
Aug 22 05:38:32 linksys404 kernel: [    0.216173] alg: No test for stdrng (krng)
Aug 22 05:38:32 linksys404 kernel: [    0.216249] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Aug 22 05:38:32 linksys404 kernel: [    0.216253] io scheduler noop registered
Aug 22 05:38:32 linksys404 kernel: [    0.216255] io scheduler anticipatory registered
Aug 22 05:38:32 linksys404 kernel: [    0.216258] io scheduler deadline registered
Aug 22 05:38:32 linksys404 kernel: [    0.216301] io scheduler cfq registered (default)
Aug 22 05:38:32 linksys404 kernel: [    0.216870] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 22 05:38:32 linksys404 kernel: [    0.216964] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 22 05:38:32 linksys404 kernel: [    0.217221] ACPI: AC Adapter [AC] (on-line)
Aug 22 05:38:32 linksys404 kernel: [    0.217298] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Aug 22 05:38:32 linksys404 kernel: [    0.217852] ACPI: Lid Switch [LID]
Aug 22 05:38:32 linksys404 kernel: [    0.217901] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Aug 22 05:38:32 linksys404 kernel: [    0.217908] ACPI: Sleep Button [SLPB]
Aug 22 05:38:32 linksys404 kernel: [    0.217963] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Aug 22 05:38:32 linksys404 kernel: [    0.217966] ACPI: Power Button [PWRF]
Aug 22 05:38:32 linksys404 kernel: [    0.219616] Marking TSC unstable due to TSC halts in idle
Aug 22 05:38:32 linksys404 kernel: [    0.219688] processor LNXCPU:00: registered as cooling_device0
Aug 22 05:38:32 linksys404 kernel: [    0.223850] Switching to clocksource hpet
Aug 22 05:38:32 linksys404 kernel: [    0.229691] thermal LNXTHERM:01: registered as thermal_zone0
Aug 22 05:38:32 linksys404 kernel: [    0.229700] ACPI: Thermal Zone [THM0] (62 C)
Aug 22 05:38:32 linksys404 kernel: [    0.231205] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Aug 22 05:38:32 linksys404 kernel: [    0.232162] serial 00:09: activated
Aug 22 05:38:32 linksys404 kernel: [    0.232288] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Aug 22 05:38:32 linksys404 kernel: [    0.232419] serial 0000:00:1e.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
Aug 22 05:38:32 linksys404 kernel: [    0.232426] serial 0000:00:1e.3: PCI INT B disabled
Aug 22 05:38:32 linksys404 kernel: [    0.233463] brd: module loaded
Aug 22 05:38:32 linksys404 kernel: [    0.233949] loop: module loaded
Aug 22 05:38:32 linksys404 kernel: [    0.234033] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Aug 22 05:38:32 linksys404 kernel: [    0.234150] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Aug 22 05:38:32 linksys404 kernel: [    0.240327] isapnp: Scanning for PnP cards...
Aug 22 05:38:32 linksys404 kernel: [    0.320028] ACPI: Battery Slot [BAT0] (battery present)
Aug 22 05:38:32 linksys404 kernel: [    0.392394] scsi0 : ata_piix
Aug 22 05:38:32 linksys404 kernel: [    0.392552] scsi1 : ata_piix
Aug 22 05:38:32 linksys404 kernel: [    0.393604] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
Aug 22 05:38:32 linksys404 kernel: [    0.393608] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
Aug 22 05:38:32 linksys404 kernel: [    0.394030] Fixed MDIO Bus: probed
Aug 22 05:38:32 linksys404 kernel: [    0.394074] PPP generic driver version 2.4.2
Aug 22 05:38:32 linksys404 kernel: [    0.394156] tun: Universal TUN/TAP device driver, 1.6
Aug 22 05:38:32 linksys404 kernel: [    0.394158] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug 22 05:38:32 linksys404 kernel: [    0.394262] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 22 05:38:32 linksys404 kernel: [    0.394513] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Aug 22 05:38:32 linksys404 kernel: [    0.394744] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Aug 22 05:38:32 linksys404 kernel: [    0.394767] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug 22 05:38:32 linksys404 kernel: [    0.394794] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 22 05:38:32 linksys404 kernel: [    0.394835] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Aug 22 05:38:32 linksys404 kernel: [    0.394873] ehci_hcd 0000:00:1d.7: debug port 1
Aug 22 05:38:32 linksys404 kernel: [    0.398797] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xa8000000
Aug 22 05:38:32 linksys404 kernel: [    0.420370] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug 22 05:38:32 linksys404 kernel: [    0.420524] usb usb1: configuration #1 chosen from 1 choice
Aug 22 05:38:32 linksys404 kernel: [    0.420560] hub 1-0:1.0: USB hub found
Aug 22 05:38:32 linksys404 kernel: [    0.420572] hub 1-0:1.0: 8 ports detected
Aug 22 05:38:32 linksys404 kernel: [    0.420655] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 22 05:38:32 linksys404 kernel: [    0.420676] uhci_hcd: USB Universal Host Controller Interface driver
Aug 22 05:38:32 linksys404 kernel: [    0.421307] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Aug 22 05:38:32 linksys404 kernel: [    0.421496] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Aug 22 05:38:32 linksys404 kernel: [    0.421508] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 22 05:38:32 linksys404 kernel: [    0.421523] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 22 05:38:32 linksys404 kernel: [    0.421576] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Aug 22 05:38:32 linksys404 kernel: [    0.421621] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
Aug 22 05:38:32 linksys404 kernel: [    0.421723] usb usb2: configuration #1 chosen from 1 choice
Aug 22 05:38:32 linksys404 kernel: [    0.421753] hub 2-0:1.0: USB hub found
Aug 22 05:38:32 linksys404 kernel: [    0.421761] hub 2-0:1.0: 2 ports detected
Aug 22 05:38:32 linksys404 kernel: [    0.422361] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Aug 22 05:38:32 linksys404 kernel: [    0.422826] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
Aug 22 05:38:32 linksys404 kernel: [    0.422843] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 22 05:38:32 linksys404 kernel: [    0.422854] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 22 05:38:32 linksys404 kernel: [    0.422894] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Aug 22 05:38:32 linksys404 kernel: [    0.422928] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
Aug 22 05:38:32 linksys404 kernel: [    0.423026] usb usb3: configuration #1 chosen from 1 choice
Aug 22 05:38:32 linksys404 kernel: [    0.423054] hub 3-0:1.0: USB hub found
Aug 22 05:38:32 linksys404 kernel: [    0.423061] hub 3-0:1.0: 2 ports detected
Aug 22 05:38:32 linksys404 kernel: [    0.423110] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 22 05:38:32 linksys404 kernel: [    0.423121] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 22 05:38:32 linksys404 kernel: [    0.423160] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Aug 22 05:38:32 linksys404 kernel: [    0.423192] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Aug 22 05:38:32 linksys404 kernel: [    0.423287] usb usb4: configuration #1 chosen from 1 choice
Aug 22 05:38:32 linksys404 kernel: [    0.423313] hub 4-0:1.0: USB hub found
Aug 22 05:38:32 linksys404 kernel: [    0.423320] hub 4-0:1.0: 2 ports detected
Aug 22 05:38:32 linksys404 kernel: [    0.423367] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Aug 22 05:38:32 linksys404 kernel: [    0.423377] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug 22 05:38:32 linksys404 kernel: [    0.423407] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Aug 22 05:38:32 linksys404 kernel: [    0.423432] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
Aug 22 05:38:32 linksys404 kernel: [    0.423524] usb usb5: configuration #1 chosen from 1 choice
Aug 22 05:38:32 linksys404 kernel: [    0.423550] hub 5-0:1.0: USB hub found
Aug 22 05:38:32 linksys404 kernel: [    0.423558] hub 5-0:1.0: 2 ports detected
Aug 22 05:38:32 linksys404 kernel: [    0.423666] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Aug 22 05:38:32 linksys404 kernel: [    0.436800] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 22 05:38:32 linksys404 kernel: [    0.436814] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 22 05:38:32 linksys404 kernel: [    0.440305] mice: PS/2 mouse device common for all mice
Aug 22 05:38:32 linksys404 kernel: [    0.440458] rtc_cmos 00:06: RTC can wake from S4
Aug 22 05:38:32 linksys404 kernel: [    0.440507] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Aug 22 05:38:32 linksys404 kernel: [    0.440541] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Aug 22 05:38:32 linksys404 kernel: [    0.440685] device-mapper: uevent: version 1.0.3
Aug 22 05:38:32 linksys404 kernel: [    0.440816] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Aug 22 05:38:32 linksys404 kernel: [    0.441642] device-mapper: multipath: version 1.1.0 loaded
Aug 22 05:38:32 linksys404 kernel: [    0.441646] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 22 05:38:32 linksys404 kernel: [    0.442587] EISA: Probing bus 0 at eisa.0
Aug 22 05:38:32 linksys404 kernel: [    0.442595] Cannot allocate resource for EISA slot 1
Aug 22 05:38:32 linksys404 kernel: [    0.442599] Cannot allocate resource for EISA slot 2
Aug 22 05:38:32 linksys404 kernel: [    0.442602] Cannot allocate resource for EISA slot 3
Aug 22 05:38:32 linksys404 kernel: [    0.442604] Cannot allocate resource for EISA slot 4
Aug 22 05:38:32 linksys404 kernel: [    0.442606] Cannot allocate resource for EISA slot 5
Aug 22 05:38:32 linksys404 kernel: [    0.442609] Cannot allocate resource for EISA slot 6
Aug 22 05:38:32 linksys404 kernel: [    0.442611] Cannot allocate resource for EISA slot 7
Aug 22 05:38:32 linksys404 kernel: [    0.442613] Cannot allocate resource for EISA slot 8
Aug 22 05:38:32 linksys404 kernel: [    0.442615] EISA: Detected 0 cards.
Aug 22 05:38:32 linksys404 kernel: [    0.445323] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Aug 22 05:38:32 linksys404 kernel: [    0.445651] cpuidle: using governor ladder
Aug 22 05:38:32 linksys404 kernel: [    0.445717] cpuidle: using governor menu
Aug 22 05:38:32 linksys404 kernel: [    0.446186] TCP cubic registered
Aug 22 05:38:32 linksys404 kernel: [    0.446365] NET: Registered protocol family 10
Aug 22 05:38:32 linksys404 kernel: [    0.446828] lo: Disabled Privacy Extensions
Aug 22 05:38:32 linksys404 kernel: [    0.447144] NET: Registered protocol family 17
Aug 22 05:38:32 linksys404 kernel: [    0.447341] P-state transition latency capped at 20 uS
Aug 22 05:38:32 linksys404 kernel: [    0.447659] Using IPI No-Shortcut mode
Aug 22 05:38:32 linksys404 kernel: [    0.447772] registered taskstats version 1
Aug 22 05:38:32 linksys404 kernel: [    0.448151]   Magic number: 6:773:618
Aug 22 05:38:32 linksys404 kernel: [    0.448262] rtc_cmos 00:06: setting system clock to 2010-08-22 05:38:09 UTC (1282455489)
Aug 22 05:38:32 linksys404 kernel: [    0.448265] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 22 05:38:32 linksys404 kernel: [    0.448267] EDD information not available.
Aug 22 05:38:32 linksys404 kernel: [    0.592981] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0J04, max UDMA/33
Aug 22 05:38:32 linksys404 kernel: [    0.593192] ata1.00: ATA-6: HTS541040G9AT00, MB2IA60A, max UDMA/100
Aug 22 05:38:32 linksys404 kernel: [    0.593195] ata1.00: 78140160 sectors, multi 16: LBA 
Aug 22 05:38:32 linksys404 kernel: [    0.593209] ata1.00: applying bridge limits
Aug 22 05:38:32 linksys404 kernel: [    0.608560] ata2.00: configured for UDMA/33
Aug 22 05:38:32 linksys404 kernel: [    0.609138] ata1.00: configured for UDMA/100
Aug 22 05:38:32 linksys404 kernel: [    0.697941] Freeing initrd memory: 7778k freed
Aug 22 05:38:32 linksys404 kernel: [    0.835488] isapnp: No Plug & Play device found
Aug 22 05:38:32 linksys404 kernel: [    0.835696] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2I PQ: 0 ANSI: 5
Aug 22 05:38:32 linksys404 kernel: [    0.835919] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 22 05:38:32 linksys404 kernel: [    0.836176] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
Aug 22 05:38:32 linksys404 kernel: [    0.836229] sd 0:0:0:0: [sda] Write Protect is off
Aug 22 05:38:32 linksys404 kernel: [    0.836259] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 05:38:32 linksys404 kernel: [    0.836419]  sda:
Aug 22 05:38:32 linksys404 kernel: [    0.840379] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4242N 0J04 PQ: 0 ANSI: 5
Aug 22 05:38:32 linksys404 kernel: [    0.851374] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Aug 22 05:38:32 linksys404 kernel: [    0.851378] Uniform CD-ROM driver Revision: 3.20
Aug 22 05:38:32 linksys404 kernel: [    0.851535] sr 1:0:0:0: Attached scsi generic sg1 type 5
Aug 22 05:38:32 linksys404 kernel: [    0.859218]  sda1 sda2 < sda5 sda6 > sda3
Aug 22 05:38:32 linksys404 kernel: [    0.884308] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 22 05:38:32 linksys404 kernel: [    0.884326] Freeing unused kernel memory: 660k freed
Aug 22 05:38:32 linksys404 kernel: [    0.884767] Write protecting the kernel text: 4680k
Aug 22 05:38:32 linksys404 kernel: [    0.884805] Write protecting the kernel read-only data: 1844k
Aug 22 05:38:32 linksys404 kernel: [    0.900355] udev: starting version 151
Aug 22 05:38:32 linksys404 kernel: [    1.105056] tg3.c:v3.102 (September 1, 2009)
Aug 22 05:38:32 linksys404 kernel: [    1.105079] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 22 05:38:32 linksys404 kernel: [    1.147711] eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:10:c6:cd:0f:e5
Aug 22 05:38:32 linksys404 kernel: [    1.147716] eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Aug 22 05:38:32 linksys404 kernel: [    1.147719] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Aug 22 05:38:32 linksys404 kernel: [    1.147722] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Aug 22 05:38:32 linksys404 kernel: [    1.481465] EXT3-fs: INFO: recovery required on readonly filesystem.
Aug 22 05:38:32 linksys404 kernel: [    1.481469] EXT3-fs: write access will be enabled during recovery.
Aug 22 05:38:32 linksys404 kernel: [    4.028559] kjournald starting.  Commit interval 5 seconds
Aug 22 05:38:32 linksys404 kernel: [    4.028576] EXT3-fs: sda3: orphan cleanup on readonly fs
Aug 22 05:38:32 linksys404 kernel: [    4.420311] EXT3-fs: sda3: 6 orphan inodes deleted
Aug 22 05:38:32 linksys404 kernel: [    4.420313] EXT3-fs: recovery complete.
Aug 22 05:38:32 linksys404 kernel: [    4.467331] EXT3-fs: mounted filesystem with ordered data mode.
Aug 22 05:38:32 linksys404 kernel: [   21.621161] udev: starting version 151
Aug 22 05:38:32 linksys404 kernel: [   21.779606] Adding 497972k swap on /dev/sda5.  Priority:-1 extents:1 across:497972k 
Aug 22 05:38:32 linksys404 kernel: [   21.809306] intel_rng: FWH not detected
Aug 22 05:38:32 linksys404 kernel: [   21.945332] Linux agpgart interface v0.103
Aug 22 05:38:32 linksys404 kernel: [   21.998214] lp: driver loaded but no devices found
Aug 22 05:38:32 linksys404 kernel: [   22.038869] Non-volatile memory driver v1.3
Aug 22 05:38:32 linksys404 kernel: [   22.045819] parport_pc 00:0a: reported by Plug and Play ACPI
Aug 22 05:38:32 linksys404 kernel: [   22.045875] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
Aug 22 05:38:32 linksys404 kernel: [   22.110252] NET: Registered protocol family 23
Aug 22 05:38:32 linksys404 kernel: [   22.126500] lp0: using parport0 (interrupt-driven).
Aug 22 05:38:32 linksys404 kernel: [   22.168344] EXT3 FS on sda3, internal journal
Aug 22 05:38:32 linksys404 kernel: [   22.169396] cfg80211: Calling CRDA to update world regulatory domain
Aug 22 05:38:32 linksys404 kernel: [   22.227515] cfg80211: World regulatory domain updated:
Aug 22 05:38:32 linksys404 kernel: [   22.227519] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 22 05:38:32 linksys404 kernel: [   22.227523] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 22 05:38:32 linksys404 kernel: [   22.227526] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 22 05:38:32 linksys404 kernel: [   22.227529] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 22 05:38:32 linksys404 kernel: [   22.227532] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 22 05:38:32 linksys404 kernel: [   22.227535] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 22 05:38:32 linksys404 kernel: [   22.238386] type=1505 audit(1282473511.287:2):  operation="profile_load" pid=553 name="/sbin/dhclient3"
Aug 22 05:38:32 linksys404 kernel: [   22.239031] type=1505 audit(1282473511.287:3):  operation="profile_load" pid=553 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 22 05:38:32 linksys404 kernel: [   22.239377] type=1505 audit(1282473511.287:4):  operation="profile_load" pid=553 name="/usr/lib/connman/scripts/dhclient-script"
Aug 22 05:38:32 linksys404 kernel: [   22.271545] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5
Aug 22 05:38:32 linksys404 kernel: [   22.271608] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Aug 22 05:38:32 linksys404 kernel: [   22.294556] ppdev: user-space parallel port driver
Aug 22 05:38:32 linksys404 kernel: [   22.295576] nsc-ircc 00:0b: activated
Aug 22 05:38:32 linksys404 kernel: [   22.295664] nsc-ircc, chip->init
Aug 22 05:38:32 linksys404 kernel: [   22.295677] nsc-ircc, Found chip at base=0x02e
Aug 22 05:38:32 linksys404 kernel: [   22.295714] nsc-ircc, driver loaded (Dag Brattli)
Aug 22 05:38:32 linksys404 kernel: [   22.296997] IrDA: Registered device irda0
Aug 22 05:38:32 linksys404 kernel: [   22.297000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
Aug 22 05:38:32 linksys404 kernel: [   22.298011] [drm] Initialized drm 1.1.0 20060810
Aug 22 05:38:32 linksys404 kernel: [   22.348564] yenta_cardbus 0000:04:00.0: CardBus bridge found [1014:056c]
Aug 22 05:38:32 linksys404 kernel: [   22.373018] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Aug 22 05:38:32 linksys404 kernel: [   22.373022] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
Aug 22 05:38:32 linksys404 kernel: [   22.373024] thinkpad_acpi: ThinkPad BIOS 1YET57WW (1.22 ), EC 1YHT26WW-1.03
Aug 22 05:38:32 linksys404 kernel: [   22.373027] thinkpad_acpi: IBM ThinkPad T43, model 2668Y3R
Aug 22 05:38:32 linksys404 kernel: [   22.373030] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
Aug 22 05:38:32 linksys404 kernel: [   22.373032] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
Aug 22 05:38:32 linksys404 kernel: [   22.390870] Registered led device: tpacpi::thinklight
Aug 22 05:38:32 linksys404 kernel: [   22.391444] Registered led device: tpacpi::power
Aug 22 05:38:32 linksys404 kernel: [   22.391948] Registered led device: tpacpi::standby
Aug 22 05:38:32 linksys404 kernel: [   22.404675] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
Aug 22 05:38:32 linksys404 kernel: [   22.426605] thinkpad_acpi: fan_init: initial fan status is unknown, assuming it is in auto mode
Aug 22 05:38:32 linksys404 kernel: [   22.428337] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
Aug 22 05:38:32 linksys404 kernel: [   22.478193] yenta_cardbus 0000:04:00.0: ISA IRQ mask 0x0c30, PCI irq 16
Aug 22 05:38:32 linksys404 kernel: [   22.478199] yenta_cardbus 0000:04:00.0: Socket status: 30000006
Aug 22 05:38:32 linksys404 kernel: [   22.478208] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x8fff
Aug 22 05:38:32 linksys404 kernel: [   22.478212] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x8fff: clean.
Aug 22 05:38:32 linksys404 kernel: [   22.479207] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0xa8400000 - 0xb7ffffff
Aug 22 05:38:32 linksys404 kernel: [   22.479211] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd7ffffff
Aug 22 05:38:32 linksys404 kernel: [   22.484510] [drm] radeon defaulting to kernel modesetting.
Aug 22 05:38:32 linksys404 kernel: [   22.484513] [drm] radeon kernel modesetting enabled.
Aug 22 05:38:32 linksys404 kernel: [   22.484639] radeon 0000:01:00.0: power state changed by ACPI to D0
Aug 22 05:38:32 linksys404 kernel: [   22.484681] radeon 0000:01:00.0: power state changed by ACPI to D0
Aug 22 05:38:32 linksys404 kernel: [   22.484691] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 22 05:38:32 linksys404 kernel: [   22.490016] ath5k 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Aug 22 05:38:32 linksys404 kernel: [   22.490064] ath5k 0000:04:02.0: registered as 'phy0'
Aug 22 05:38:32 linksys404 kernel: [   22.902242] [drm] radeon: Initializing kernel modesetting.
Aug 22 05:38:32 linksys404 kernel: [   22.904765] [drm] register mmio base: 0xA8100000
Aug 22 05:38:32 linksys404 kernel: [   22.904768] [drm] register mmio size: 65536
Aug 22 05:38:32 linksys404 kernel: [   22.905106] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
Aug 22 05:38:32 linksys404 kernel: [   22.905124] [drm] Generation 2 PCI interface, using max accessible memory
Aug 22 05:38:32 linksys404 kernel: [   22.905127] [drm] radeon: VRAM 64M
Aug 22 05:38:32 linksys404 kernel: [   22.905130] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
Aug 22 05:38:32 linksys404 kernel: [   22.905132] [drm] radeon: GTT 512M
Aug 22 05:38:32 linksys404 kernel: [   22.905134] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
Aug 22 05:38:32 linksys404 kernel: [   22.905186] [drm] radeon: using MSI.
Aug 22 05:38:32 linksys404 kernel: [   22.905215] [drm] radeon: irq initialized.
Aug 22 05:38:32 linksys404 kernel: [   22.905759] [drm] Detected VRAM RAM=64M, BAR=128M
Aug 22 05:38:32 linksys404 kernel: [   22.905763] [drm] RAM width 64bits DDR
Aug 22 05:38:32 linksys404 kernel: [   22.915582] [TTM] Zone  kernel: Available graphics memory: 254090 kiB.
Aug 22 05:38:32 linksys404 kernel: [   22.915603] [drm] radeon: 64M of VRAM memory ready
Aug 22 05:38:32 linksys404 kernel: [   22.915606] [drm] radeon: 512M of GTT memory ready.
Aug 22 05:38:32 linksys404 kernel: [   22.915626] [drm] GART: num cpu pages 131072, num gpu pages 131072
Aug 22 05:38:32 linksys404 kernel: [   22.916167] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Aug 22 05:38:32 linksys404 kernel: [   22.916208] [drm] PCIE GART of 512M enabled (table at 0x00040000).
Aug 22 05:38:32 linksys404 kernel: [   22.916219] [drm] radeon: cp idle (0x10000C03)
Aug 22 05:38:32 linksys404 kernel: [   22.916314] [drm] Loading R300 Microcode
Aug 22 05:38:32 linksys404 kernel: [   22.916591] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
Aug 22 05:38:32 linksys404 kernel: [   22.922724] [drm] radeon: ring at 0x0000000020000000
Aug 22 05:38:32 linksys404 kernel: [   22.922748] [drm] ring test succeeded in 1 usecs
Aug 22 05:38:32 linksys404 kernel: [   22.922902] [drm] radeon: ib pool ready.
Aug 22 05:38:32 linksys404 kernel: [   22.922990] [drm] ib test succeeded in 0 usecs
Aug 22 05:38:32 linksys404 kernel: [   22.923097] [drm] DFP table revision: 4
Aug 22 05:38:32 linksys404 kernel: [   22.923144] [drm] Panel ID String: SXGA+ Single (85MHz)    
Aug 22 05:38:32 linksys404 kernel: [   22.923147] [drm] Panel Size 1400x1050
Aug 22 05:38:32 linksys404 kernel: [   22.923178] [drm] Default TV standard: NTSC
Aug 22 05:38:32 linksys404 kernel: [   22.923180] [drm] 27.000000000 MHz TV ref clk
Aug 22 05:38:32 linksys404 kernel: [   22.923184] [drm] Default TV standard: NTSC
Aug 22 05:38:32 linksys404 kernel: [   22.923185] [drm] 27.000000000 MHz TV ref clk
Aug 22 05:38:32 linksys404 kernel: [   22.923213] [drm] Radeon Display Connectors
Aug 22 05:38:32 linksys404 kernel: [   22.923215] [drm] Connector 0:
Aug 22 05:38:32 linksys404 kernel: [   22.923217] [drm]   VGA
Aug 22 05:38:32 linksys404 kernel: [   22.923220] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
Aug 22 05:38:32 linksys404 kernel: [   22.923222] [drm]   Encoders:
Aug 22 05:38:32 linksys404 kernel: [   22.923223] [drm]     CRT1: INTERNAL_DAC1
Aug 22 05:38:32 linksys404 kernel: [   22.923225] [drm] Connector 1:
Aug 22 05:38:32 linksys404 kernel: [   22.923227] [drm]   DVI-D
Aug 22 05:38:32 linksys404 kernel: [   22.923228] [drm]   HPD1
Aug 22 05:38:32 linksys404 kernel: [   22.923231] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
Aug 22 05:38:32 linksys404 kernel: [   22.923233] [drm]   Encoders:
Aug 22 05:38:32 linksys404 kernel: [   22.923235] [drm]     DFP1: INTERNAL_TMDS1
Aug 22 05:38:32 linksys404 kernel: [   22.923237] [drm] Connector 2:
Aug 22 05:38:32 linksys404 kernel: [   22.923238] [drm]   LVDS
Aug 22 05:38:32 linksys404 kernel: [   22.923240] [drm]   Encoders:
Aug 22 05:38:32 linksys404 kernel: [   22.923241] [drm]     LCD1: INTERNAL_LVDS
Aug 22 05:38:32 linksys404 kernel: [   22.923243] [drm] Connector 3:
Aug 22 05:38:32 linksys404 kernel: [   22.923245] [drm]   S-video
Aug 22 05:38:32 linksys404 kernel: [   22.923246] [drm]   Encoders:
Aug 22 05:38:32 linksys404 kernel: [   22.923248] [drm]     TV1: INTERNAL_DAC2
Aug 22 05:38:32 linksys404 kernel: [   22.989729] [drm] fb mappable at 0xC00C0000
Aug 22 05:38:32 linksys404 kernel: [   22.989732] [drm] vram apper at 0xC0000000
Aug 22 05:38:32 linksys404 kernel: [   22.989734] [drm] size 5913600
Aug 22 05:38:32 linksys404 kernel: [   22.989736] [drm] fb depth is 24
Aug 22 05:38:32 linksys404 kernel: [   22.989738] [drm]    pitch is 5632
Aug 22 05:38:32 linksys404 kernel: [   22.993551] fb0: radeondrmfb frame buffer device
Aug 22 05:38:32 linksys404 kernel: [   22.993554] registered panic notifier
Aug 22 05:38:32 linksys404 kernel: [   22.993561] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
Aug 22 05:38:32 linksys404 kernel: [   22.998083] vga16fb: mapped to 0xc00a0000
Aug 22 05:38:32 linksys404 kernel: [   22.998087] vga16fb: not registering due to another framebuffer present
Aug 22 05:38:32 linksys404 kernel: [   23.108281] Console: switching to colour frame buffer device 175x65
Aug 22 05:38:32 linksys404 kernel: [   23.117286] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 22 05:38:32 linksys404 kernel: [   23.204112] Registered led device: ath5k-phy0::rx
Aug 22 05:38:32 linksys404 kernel: [   23.204130] Registered led device: ath5k-phy0::tx
Aug 22 05:38:32 linksys404 kernel: [   23.204134] ath5k phy0: Atheros AR5213A chip found (MAC: 0x59, PHY: 0x43)
Aug 22 05:38:32 linksys404 kernel: [   23.204137] ath5k phy0: RF5112B multiband radio found (0x36)
Aug 22 05:38:32 linksys404 kernel: [   23.224782] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
Aug 22 05:38:32 linksys404 kernel: [   23.224788] serio: Synaptics pass-through port at isa0060/serio1/input0
Aug 22 05:38:32 linksys404 kernel: [   23.267846] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
Aug 22 05:38:32 linksys404 kernel: [   23.408700] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Aug 22 05:38:32 linksys404 kernel: [   23.410389] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Aug 22 05:38:32 linksys404 kernel: [   23.411329] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Aug 22 05:38:32 linksys404 kernel: [   23.411930] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Aug 22 05:38:32 linksys404 kernel: [   23.412771] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Aug 22 05:38:32 linksys404 kernel: [   23.621296] AC'97 0 analog subsections not ready
Aug 22 05:38:32 linksys404 kernel: [   23.709832] type=1505 audit(1282473512.759:5):  operation="profile_load" pid=813 name="/usr/share/gdm/guest-session/Xsession"
Aug 22 05:38:32 linksys404 kernel: [   23.714720] type=1505 audit(1282473512.763:6):  operation="profile_replace" pid=814 name="/sbin/dhclient3"
Aug 22 05:38:32 linksys404 kernel: [   23.715369] type=1505 audit(1282473512.763:7):  operation="profile_replace" pid=814 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 22 05:38:32 linksys404 kernel: [   23.720546] type=1505 audit(1282473512.771:8):  operation="profile_replace" pid=814 name="/usr/lib/connman/scripts/dhclient-script"
Aug 22 05:38:32 linksys404 kernel: [   23.726477] type=1505 audit(1282473512.775:9):  operation="profile_load" pid=816 name="/usr/bin/evince"
Aug 22 05:38:32 linksys404 kernel: [   23.757282] type=1505 audit(1282473512.807:10):  operation="profile_load" pid=816 name="/usr/bin/evince-previewer"
Aug 22 05:38:32 linksys404 kernel: [   23.773857] type=1505 audit(1282473512.823:11):  operation="profile_load" pid=816 name="/usr/bin/evince-thumbnailer"
Aug 22 05:38:32 linksys404 kernel: [   23.846694] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 22 05:38:32 linksys404 kernel: [   23.909517] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 22 05:38:33 linksys404 kernel: [   24.211506] intel8x0_measure_ac97_clock: measured 62772 usecs (3023 samples)
Aug 22 05:38:33 linksys404 kernel: [   24.211510] intel8x0: clocking to 48000
Aug 22 05:38:39 linksys404 kernel: [   30.427823] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Aug 22 05:38:39 linksys404 kernel: [   30.659726] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
Aug 22 05:38:49 linksys404 kernel: [   40.634914] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 22 05:38:49 linksys404 kernel: [   40.634965] cfg80211: Calling CRDA for country: TW
Aug 22 05:38:49 linksys404 kernel: [   40.638177] cfg80211: Regulatory domain: TW
Aug 22 05:38:49 linksys404 kernel: [   40.638179] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 22 05:38:49 linksys404 kernel: [   40.638182] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
Aug 22 05:38:49 linksys404 kernel: [   40.638187] cfg80211: Regulatory domain: TW
Aug 22 05:38:49 linksys404 kernel: [   40.638188] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 22 05:38:49 linksys404 kernel: [   40.638192] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Aug 22 05:38:49 linksys404 kernel: [   40.638195] 	(5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Aug 22 05:38:49 linksys404 kernel: [   40.638198] 	(5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Aug 22 05:38:49 linksys404 kernel: [   40.638202] cfg80211: Regulatory domain: 98
Aug 22 05:38:49 linksys404 kernel: [   40.638204] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 22 05:38:49 linksys404 kernel: [   40.638207] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Aug 22 05:38:49 linksys404 kernel: [   40.638295] cfg80211: Current regulatory domain updated by AP to: TW
Aug 22 05:38:49 linksys404 kernel: [   40.638298] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 22 05:38:49 linksys404 kernel: [   40.638301] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Aug 22 05:38:50 linksys404 kernel: [   40.977898] padlock: VIA PadLock not detected.


If it matters I installed unrestricted extras and all the codecs and stuff. For now I'll just roll back to 10.04 without the upgrade to the kernel, I suppose, or maybe 9.10. :lolflag:

If we need more data I can do another "mark all upgrades" and get it to crash again, if this isn't the right log file. peace out.):P

---

