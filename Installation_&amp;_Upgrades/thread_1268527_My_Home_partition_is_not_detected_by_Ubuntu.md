---
title: "My Home partition is not detected by Ubuntu"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by the8thstar on 2009-09-17
I resized and moved some partitions around the hard disk and now Ubuntu cannot find my home partition at boot.

My home partition is detected through gparted and blkid:

> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" (that's the live CD from which I'm trying to repair the system)
/dev/sda1: TYPE="swap" UUID="07f3a727-60f2-4c6e-b4ad-26acfe9e4ac3" 
/dev/sda2: UUID="5E4C837D4C834EA9" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sda3: UUID="5dda0098-ca52-4cdb-8d22-3787dee8cd30" TYPE="ext4" 
/dev/sda4: UUID="9ad998ca-a452-4d6c-b366-901360d9e3be" TYPE="ext4"

When I type sudo gedit /media/disk/etc/fstab from the liveCD, I can access my root partition:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=5dda0098-ca52-4cdb-8d22-3787dee8cd30 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=9ad998ca-a452-4d6c-b366-901360d9e3be /home           ext4    relatime        0       2
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

As you see, the UUID match between blkid and fstab. However the liveCD is incapable of "seeing" my home partition when I go to Places... so I'm wondering if something is wrong with the actual format of my home partition. I checked it for errors through gparted, but nothing changed. And I can't mount it through gparted or through sudo mount -t /dev/sda4 either.

I need your help. Thanks in advance!

---

### Post by the8thstar on 2009-09-17
Bump

---

### Post by sisco311 on 2009-09-17
try to mount the partition:
```
sudo mount -t ext4 /dev/sda4 /mnt
```
and post the output from:
```
dmesg | tail -n 20
```

---

### Post by the8thstar on 2009-09-17
OK, here goes:

> ubuntu@ubuntu:~$ dmesg | tail -n 20
[  391.320962] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  397.320967] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  403.321013] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  409.320986] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  415.320952] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  421.320951] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  427.320950] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  433.320950] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  439.320938] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  445.323049] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  451.320961] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  453.678921] EXT4-fs: barriers enabled
[  453.695258] kjournald2 starting.  Commit interval 5 seconds
[  453.695522] EXT4 FS on sda4, internal journal on sda4:8
[  453.695525] EXT4-fs: delayed allocation enabled
[  453.695527] EXT4-fs: file extents enabled
[  453.696253] EXT4-fs: mballoc enabled
[  453.696259] EXT4-fs: mounted filesystem with ordered data mode.
[  457.320958] ACPI: Unable to turn cooling device [f6c2df18] 'on'
[  463.320944] ACPI: Unable to turn cooling device [f6c2df18] 'on'

---

### Post by sisco311 on 2009-09-17
Everything looks fine. The partition should be mounted.

What's the output of:
```
mount
ls -al /mnt
```

---

### Post by the8thstar on 2009-09-17
> ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda3 on /media/disk type ext4 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/HP_PAVILION type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt type ext4 (rw)

> ubuntu@ubuntu:~$ ls -al /mnt
total 24
drwxr-xr-x  4 root root  4096 2009-04-22 19:48 .
drwxr-xr-x 24 root root   280 2009-09-17 15:15 ..
drwx------  2 root root 16384 2009-04-22 19:41 lost+found
drwxr-xr-x 76 1000 1000  4096 2009-09-16 15:33 the8thstar

I wish I knew what this meant!

---

### Post by sisco311 on 2009-09-17
> **the8thstar said:**
> I wish I knew what this meant!

> /dev/sda4 on /mnt type ext4 (rw)
the partition is mounted under /mnt

> ubuntu@ubuntu:~$ ls -al /mnt
total 24
drwxr-xr-x 4 root root 4096 2009-04-22 19:48 .
drwxr-xr-x 24 root root 280 2009-09-17 15:15 ..
drwx------ 2 root root 16384 2009-04-22 19:41 lost+found
drwxr-xr-x 76 1000 1000 4096 2009-09-16 15:33 **the8thstar**

and it contains your home directory. 

Try to reboot and see if it's mounted.

If not, then switch to a virtual terminal (Ctrl+Alt+F2) login and post the output of:
```
mount
```

EDIT: Do you get any error message during the boot up?

---

### Post by the8thstar on 2009-09-17
Yes, I got a fail message regarding the virtual something in regard to my home partition (the UUID was listed, so that's how I knew).

---

### Post by sisco311 on 2009-09-17
Boot the live cd, mount the root ("/") partition under /media/disk and post the content of /media/disk/var/log/dmesg file.

(Or upload it as an attachment.)

---

### Post by the8thstar on 2009-09-17
Here is the result:
> 
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 (Ubuntu 2.6.28-15.52-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  modified: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  modified: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378c2000 - 37fefa8c
[    0.000000] Allocated new RAMDISK: 0087d000 - 00faaa8c
[    0.000000] Move RAMDISK from 00000000378c2000 - 0000000037fefa8b to 0087d000 - 00faaa8b
[    0.000000] ACPI: RSDP 000F7C40, 0014 (r0 KM400 )
[    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 KM400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 KM400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FFF30C0, 518F (r1 KM400  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF8280, 005A (r1 KM400  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 139MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000faaa8c]      NEW RAMDISK ==> [000087d000 - 0000faaa8c]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f6130] 000f6130
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0003fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003fff0
[    0.000000] On node 0 totalpages: 262015
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 280 pages used for memmap
[    0.000000]   HighMem zone: 35546 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259967
[    0.000000] Kernel command line: root=UUID=5dda0098-ca52-4cdb-8d22-3787dee8cd30 ro quiet splash vga=791
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2075.276 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 5242240 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1018544k/1048512k available (4116k kernel code, 29216k reserved, 2199k data, 532k init, 143304k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05050ff - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05050ff   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004017] Calibrating delay loop (skipped), value calculated using timer frequency.. 4150.55 BogoMIPS (lpj=8301104)
[    0.004045] Security Framework initialized
[    0.004058] SELinux:  Disabled at boot.
[    0.004098] AppArmor: AppArmor initialized
[    0.004109] Mount-cache hash table entries: 512
[    0.004315] Initializing cgroup subsys ns
[    0.004320] Initializing cgroup subsys cpuacct
[    0.004323] Initializing cgroup subsys memory
[    0.004328] Initializing cgroup subsys freezer
[    0.004346] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004349] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004372] Checking 'hlt' instruction... OK.
[    0.020534] SMP alternatives: switching to UP code
[    0.172505] Freeing SMP alternatives: 18k freed
[    0.172511] ACPI: Core revision 20080926
[    0.175365] ACPI: Checking initramfs for custom DSDT
[    0.461305] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.503472] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
[    0.504002] Brought up 1 CPUs
[    0.504002] Total of 1 processors activated (4150.55 BogoMIPS).
[    0.504002] CPU0 attaching NULL sched-domain.
[    0.504002] net_namespace: 776 bytes
[    0.504002] Booting paravirtualized kernel on bare hardware
[    0.504002] Time: 15:10:51  Date: 09/17/09
[    0.504002] regulator: core version 0.5
[    0.504002] NET: Registered protocol family 16
[    0.504002] EISA bus registered
[    0.504002] ACPI: bus type pci registered
[    0.508942] PCI: PCI BIOS revision 2.10 entry at 0xfbda0, last bus=1
[    0.508946] PCI: Using configuration type 1 for base access
[    0.510436] ACPI: EC: Look up EC in DSDT
[    0.517896] ACPI: Interpreter enabled
[    0.517907] ACPI: (supports S0 S1 S3 S4 S5)
[    0.517935] ACPI: Using IOAPIC for interrupt routing
[    0.524140] ACPI: No dock devices found.
[    0.524156] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.524212] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.524270] pci 0000:00:01.0: supports D1
[    0.524302] pci 0000:00:09.0: reg 10 io port: [0xa000-0xa0ff]
[    0.524308] pci 0000:00:09.0: reg 14 32bit mmio: [0xe8010000-0xe80103ff]
[    0.524328] pci 0000:00:09.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.524336] pci 0000:00:09.0: supports D1 D2
[    0.524339] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524343] pci 0000:00:09.0: PME# disabled
[    0.524368] pci 0000:00:0a.0: reg 10 32bit mmio: [0xe8000000-0xe800ffff]
[    0.524374] pci 0000:00:0a.0: reg 14 io port: [0xa400-0xa407]
[    0.524398] pci 0000:00:0a.0: PME# supported from D3hot D3cold
[    0.524401] pci 0000:00:0a.0: PME# disabled
[    0.524427] pci 0000:00:0b.0: reg 10 32bit mmio: [0xe8011000-0xe80117ff]
[    0.524433] pci 0000:00:0b.0: reg 14 io port: [0xa800-0xa87f]
[    0.524459] pci 0000:00:0b.0: supports D2
[    0.524461] pci 0000:00:0b.0: PME# supported from D2 D3hot D3cold
[    0.524465] pci 0000:00:0b.0: PME# disabled
[    0.524494] pci 0000:00:0f.0: reg 10 io port: [0xac00-0xac07]
[    0.524500] pci 0000:00:0f.0: reg 14 io port: [0xb000-0xb003]
[    0.524506] pci 0000:00:0f.0: reg 18 io port: [0xb400-0xb407]
[    0.524512] pci 0000:00:0f.0: reg 1c io port: [0xb800-0xb803]
[    0.524518] pci 0000:00:0f.0: reg 20 io port: [0xbc00-0xbc0f]
[    0.524524] pci 0000:00:0f.0: reg 24 io port: [0xc000-0xc0ff]
[    0.524575] pci 0000:00:0f.1: reg 20 io port: [0xc400-0xc40f]
[    0.524634] pci 0000:00:10.0: reg 20 io port: [0xc800-0xc81f]
[    0.524648] pci 0000:00:10.0: supports D1 D2
[    0.524650] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524654] pci 0000:00:10.0: PME# disabled
[    0.524694] pci 0000:00:10.1: reg 20 io port: [0xcc00-0xcc1f]
[    0.524708] pci 0000:00:10.1: supports D1 D2
[    0.524710] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524714] pci 0000:00:10.1: PME# disabled
[    0.524752] pci 0000:00:10.2: reg 20 io port: [0xd000-0xd01f]
[    0.524767] pci 0000:00:10.2: supports D1 D2
[    0.524769] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524772] pci 0000:00:10.2: PME# disabled
[    0.524811] pci 0000:00:10.3: reg 20 io port: [0xd400-0xd41f]
[    0.524825] pci 0000:00:10.3: supports D1 D2
[    0.524827] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524831] pci 0000:00:10.3: PME# disabled
[    0.524856] pci 0000:00:10.4: reg 10 32bit mmio: [0xe8012000-0xe80120ff]
[    0.524884] pci 0000:00:10.4: supports D1 D2
[    0.524886] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524889] pci 0000:00:10.4: PME# disabled
[    0.524941] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.524947] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.524982] pci 0000:00:11.5: reg 10 io port: [0xd800-0xd8ff]
[    0.525012] pci 0000:00:11.5: supports D1 D2
[    0.525038] pci 0000:00:11.6: reg 10 io port: [0xdc00-0xdcff]
[    0.525093] pci 0000:00:12.0: reg 10 io port: [0xe000-0xe0ff]
[    0.525099] pci 0000:00:12.0: reg 14 32bit mmio: [0xe8013000-0xe80130ff]
[    0.525124] pci 0000:00:12.0: supports D1 D2
[    0.525126] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.525130] pci 0000:00:12.0: PME# disabled
[    0.525173] pci 0000:01:00.0: reg 10 32bit mmio: [0xe4000000-0xe4ffffff]
[    0.525178] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
[    0.525184] pci 0000:01:00.0: reg 18 32bit mmio: [0xe5000000-0xe5ffffff]
[    0.525197] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.525233] pci 0000:00:01.0: bridge 32bit mmio: [0xe4000000-0xe6ffffff]
[    0.525237] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.525244] bus 00 -> node 0
[    0.525252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.565477] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.565678] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.565881] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.566092] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 6 7 10 11 12)
[    0.566265] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.566430] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.566595] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.566759] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.566946] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.567139] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.567353] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.567544] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.567688] ACPI: WMI: Mapper loaded
[    0.567942] SCSI subsystem initialized
[    0.568006] libata version 3.00 loaded.
[    0.568067] usbcore: registered new interface driver usbfs
[    0.568088] usbcore: registered new interface driver hub
[    0.568122] usbcore: registered new device driver usb
[    0.568269] PCI: Using ACPI for IRQ routing
[    0.568365] Bluetooth: Core ver 2.13
[    0.568365] NET: Registered protocol family 31
[    0.568365] Bluetooth: HCI device and connection manager initialized
[    0.568365] Bluetooth: HCI socket layer initialized
[    0.568365] NET: Registered protocol family 8
[    0.568365] NET: Registered protocol family 20
[    0.568365] NetLabel: Initializing
[    0.568365] NetLabel:  domain hash size = 128
[    0.568365] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.568365] NetLabel:  unlabeled traffic allowed by default
[    0.568365] AppArmor: AppArmor Filesystem Enabled
[    0.568365] pnp: PnP ACPI init
[    0.568365] ACPI: bus type pnp registered
[    0.572702] pnp: PnP ACPI: found 13 devices
[    0.572704] ACPI: ACPI bus type pnp unregistered
[    0.572709] PnPBIOS: Disabled by ACPI PNP
[    0.572720] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[    0.572723] system 00:00: iomem range 0xd9800-0xdbfff has been reserved
[    0.572726] system 00:00: iomem range 0xf0000-0xfbfff could not be reserved
[    0.572729] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.572732] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.572735] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.572738] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.572741] system 00:00: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.572743] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.572746] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.572749] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.572766] system 00:02: ioport range 0x4000-0x407f has been reserved
[    0.572769] system 00:02: ioport range 0x5000-0x500f has been reserved
[    0.572775] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.572777] system 00:03: ioport range 0x294-0x297 has been reserved
[    0.572780] system 00:03: ioport range 0x290-0x297 could not be reserved
[    0.607467] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.607469] pci 0000:00:01.0:   IO window: disabled
[    0.607475] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe6ffffff
[    0.607479] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.607493] pci 0000:00:01.0: setting latency timer to 64
[    0.607498] bus: 00 index 0 io port: [0x00-0xffff]
[    0.607500] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.607502] bus: 01 index 0 mmio: [0x0-0x0]
[    0.607504] bus: 01 index 1 mmio: [0xe4000000-0xe6ffffff]
[    0.607506] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.607508] bus: 01 index 3 mmio: [0x0-0x0]
[    0.607519] NET: Registered protocol family 2
[    0.607639] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.608114] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.609984] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.610962] TCP: Hash tables configured (established 131072 bind 65536)
[    0.610966] TCP reno registered
[    0.611122] NET: Registered protocol family 1
[    0.611302] checking if image is initramfs... it is
[    1.107982] Switched to high resolution mode on CPU 0
[    1.227072] Freeing initrd memory: 7350k freed
[    1.227198] cpufreq: No nForce2 chipset.
[    1.227389] audit: initializing netlink socket (disabled)
[    1.227415] type=2000 audit(1253200252.224:1): initialized
[    1.235005] highmem bounce pool size: 64 pages
[    1.235013] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.236361] VFS: Disk quotas dquot_6.5.1
[    1.236421] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.237054] fuse init (API version 7.10)
[    1.237142] msgmni has been set to 1724
[    1.237358] alg: No test for stdrng (krng)
[    1.237373] io scheduler noop registered
[    1.237375] io scheduler anticipatory registered
[    1.237377] io scheduler deadline registered
[    1.237393] io scheduler cfq registered (default)
[    1.237407] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.237489] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    1.237509] pci 0000:01:00.0: Boot video device
[    1.242312] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.242322] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.242476] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.242480] ACPI: Power Button (FF) [PWRF]
[    1.242534] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.242537] ACPI: Power Button (CM) [PWRB]
[    1.242586] fan PNP0C0B:00: registered as cooling_device0
[    1.242592] ACPI: Fan [FAN] (on)
[    1.242847] processor ACPI_CPU:00: registered as cooling_device1
[    1.246875] thermal LNXTHERM:01: registered as thermal_zone0
[    1.248319] ACPI: Unable to turn cooling device [f6c2cf18] 'on'
[    1.248324] ACPI: Thermal Zone [THRM] (42 C)
[    1.248370] isapnp: Scanning for PnP cards...
[    1.601893] isapnp: No Plug & Play device found
[    1.603272] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.603365] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.603670] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.604483] brd: module loaded
[    1.604823] loop: module loaded
[    1.604908] Fixed MDIO Bus: probed
[    1.604916] PPP generic driver version 2.4.2
[    1.604986] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.605026] Driver 'sd' needs updating - please use bus_type methods
[    1.605036] Driver 'sr' needs updating - please use bus_type methods
[    1.605171] sata_via 0000:00:0f.0: version 2.4
[    1.605573] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    1.605576] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    1.605588] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.605662] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.605825] scsi0 : sata_via
[    1.605963] scsi1 : sata_via
[    1.607688] ata1: SATA max UDMA/133 cmd 0xac00 ctl 0xb000 bmdma 0xbc00 irq 20
[    1.607692] ata2: SATA max UDMA/133 cmd 0xb400 ctl 0xb800 bmdma 0xbc08 irq 20
[    1.808019] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.020011] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.030834] pata_via 0000:00:0f.1: version 0.3.3
[    2.030843] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    2.031065] scsi2 : pata_via
[    2.031136] scsi3 : pata_via
[    2.033106] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xc400 irq 14
[    2.033109] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xc408 irq 15
[    2.252515] ata3.00: ATA-6: ST380011A, 3.08, max UDMA/100
[    2.252518] ata3.00: 156301488 sectors, multi 16: LBA 
[    2.268377] ata3.00: configured for UDMA/100
[    2.440348] ata4.00: ATAPI: PIONEER DVD-RW  DVR-105, 1.20, max UDMA/33
[    2.440376] ata4.01: ATAPI: IDE-DVD ROM 16x, HD09, max UDMA/33
[    2.456231] ata4.00: configured for UDMA/33
[    2.472249] ata4.01: configured for UDMA/33
[    2.472982] scsi 2:0:0:0: Direct-Access     ATA      ST380011A        3.08 PQ: 0 ANSI: 5
[    2.473097] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.473120] sd 2:0:0:0: [sda] Write Protect is off
[    2.473123] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.473154] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.473251] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.473268] sd 2:0:0:0: [sda] Write Protect is off
[    2.473271] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.473298] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.473303]  sda: sda1 sda2 sda3 sda4
[    2.510329] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.510394] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.516901] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-105  1.20 PQ: 0 ANSI: 5
[    2.535212] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    2.535216] Uniform CD-ROM driver Revision: 3.20
[    2.535313] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.535352] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.535667] scsi 3:0:1:0: CD-ROM            IDE-DVD  ROM 16x          HD09 PQ: 0 ANSI: 5
[    2.538791] sr1: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    2.538852] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    2.538904] sr 3:0:1:0: Attached scsi generic sg2 type 5
[    2.539075] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.539458] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    2.539462] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    2.539472] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.539508] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    2.539581] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    2.539664] ehci_hcd 0000:00:10.4: irq 21, io mem 0xe8012000
[    2.548012] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    2.548106] usb usb1: configuration #1 chosen from 1 choice
[    2.548136] hub 1-0:1.0: USB hub found
[    2.548151] hub 1-0:1.0: 8 ports detected
[    2.548261] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.548276] uhci_hcd: USB Universal Host Controller Interface driver
[    2.548318] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.548326] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.548380] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.548399] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c800
[    2.548501] usb usb2: configuration #1 chosen from 1 choice
[    2.548531] hub 2-0:1.0: USB hub found
[    2.548543] hub 2-0:1.0: 2 ports detected
[    2.548623] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.548629] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.548673] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.548691] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000cc00
[    2.548780] usb usb3: configuration #1 chosen from 1 choice
[    2.548804] hub 3-0:1.0: USB hub found
[    2.548815] hub 3-0:1.0: 2 ports detected
[    2.548893] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.548899] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.548949] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.548968] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d000
[    2.549052] usb usb4: configuration #1 chosen from 1 choice
[    2.549077] hub 4-0:1.0: USB hub found
[    2.549087] hub 4-0:1.0: 2 ports detected
[    2.549185] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.549191] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    2.549239] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    2.549258] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
[    2.549343] usb usb5: configuration #1 chosen from 1 choice
[    2.549374] hub 5-0:1.0: USB hub found
[    2.549385] hub 5-0:1.0: 2 ports detected
[    2.549513] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.549944] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.549951] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.550078] mice: PS/2 mouse device common for all mice
[    2.550210] rtc_cmos 00:05: RTC can wake from S4
[    2.550258] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.550311] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    2.550377] device-mapper: uevent: version 1.0.3
[    2.550547] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.550615] device-mapper: multipath: version 1.0.5 loaded
[    2.550618] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.550711] EISA: Probing bus 0 at eisa.0
[    2.550730] Cannot allocate resource for EISA slot 4
[    2.550732] Cannot allocate resource for EISA slot 5
[    2.550745] EISA: Detected 0 cards.
[    2.550784] cpuidle: using governor ladder
[    2.550787] cpuidle: using governor menu
[    2.551327] TCP cubic registered
[    2.551433] NET: Registered protocol family 10
[    2.551883] lo: Disabled Privacy Extensions
[    2.552239] NET: Registered protocol family 17
[    2.552258] Bluetooth: L2CAP ver 2.11
[    2.552261] Bluetooth: L2CAP socket layer initialized
[    2.552264] Bluetooth: SCO (Voice Link) ver 0.6
[    2.552266] Bluetooth: SCO socket layer initialized
[    2.552299] Bluetooth: RFCOMM socket layer initialized
[    2.552311] Bluetooth: RFCOMM TTY layer initialized
[    2.552313] Bluetooth: RFCOMM ver 1.10
[    2.552335] powernow-k8: Processor cpuid 6a0 not supported
[    2.552364] Using IPI No-Shortcut mode
[    2.552454] registered taskstats version 1
[    2.552606]   Magic number: 9:502:184
[    2.552693] acpi LNXTHERM:00: hash matches
[    2.552758] rtc_cmos 00:05: setting system clock to 2009-09-17 15:10:53 UTC (1253200253)
[    2.552762] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.552764] EDD information not available.
[    2.553542] Freeing unused kernel memory: 532k freed
[    2.553664] Write protecting the kernel text: 4120k
[    2.553704] Write protecting the kernel read-only data: 1524k
[    2.591501] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.644096] vesafb: framebuffer at 0xd0000000, mapped to 0xf7c80000, using 3072k, total 262144k
[    2.644102] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[    2.644105] vesafb: protected mode interface info at c000:d3a0
[    2.644108] vesafb: pmi: set display start = c00cd3d6, set palette = c00cd440
[    2.644111] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    2.644123] vesafb: scrolling: redraw
[    2.644127] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    2.644265] Console: switching to colour frame buffer device 128x48
[    2.662612] fb0: VESA VGA frame buffer device
[    2.895663] Floppy drive(s): fd0 is 1.44M
[    2.917285] FDC 0 is a post-1991 82077
[    2.934019] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    2.934088] tulip 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.934461] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.
[    2.938912] eth0: ADMtek Comet rev 17 at Port 0xa000, 00:1a:70:13:00:27, IRQ 17.
[    2.962461] ohci1394 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.015345] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[e8011000-e80117ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.020898] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    3.084684] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.085107] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    3.085110] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    3.085122] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    3.085943] eth1: VIA Rhine II at 0xe8013000, 00:0e:a6:d1:79:30, IRQ 23.
[    3.086656] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    3.154951] usb 1-4: configuration #1 chosen from 1 choice
[    3.393957] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.610807] usb 2-1: configuration #1 chosen from 1 choice
[    3.619738] Initializing USB Mass Storage driver...
[    3.621826] scsi4 : SCSI emulation for USB Mass Storage devices
[    3.622167] usbcore: registered new interface driver usb-storage
[    3.622172] USB Mass Storage support registered.
[    3.622408] usb-storage: device found at 2
[    3.622410] usb-storage: waiting for device to settle before scanning
[    3.818548] EXT4-fs: INFO: recovery required on readonly filesystem.
[    3.818554] EXT4-fs: write access will be enabled during recovery.
[    3.824646] EXT4-fs: barriers enabled
[    3.999755] kjournald2 starting.  Commit interval 5 seconds
[    3.999779] EXT4-fs: delayed allocation enabled
[    3.999782] EXT4-fs: file extents enabled
[    4.000048] EXT4-fs: mballoc enabled
[    4.000051] EXT4-fs: recovery complete.
[    4.000661] EXT4-fs: mounted filesystem with ordered data mode.
[    4.296137] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000056d1d0]
[    7.248798] ACPI: Unable to turn cooling device [f6c2cf18] 'on'
[    8.621956] usb-storage: device scan complete
[    8.624894] scsi 4:0:0:0: Direct-Access              USB Card Reader  1.01 PQ: 0 ANSI: 0 CCS
[    8.627859] scsi 4:0:0:1: Direct-Access              USB Card Reader  1.01 PQ: 0 ANSI: 0 CCS
[    8.630848] scsi 4:0:0:2: Direct-Access              USB Card Reader  1.01 PQ: 0 ANSI: 0 CCS
[    8.633835] scsi 4:0:0:3: Direct-Access              USB Card Reader  1.01 PQ: 0 ANSI: 0 CCS
[    8.638929] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    8.639019] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    8.643850] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[    8.643909] sd 4:0:0:1: Attached scsi generic sg4 type 0
[    8.648851] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[    8.648895] sd 4:0:0:2: Attached scsi generic sg5 type 0
[    8.653810] sd 4:0:0:3: [sde] Attached SCSI removable disk
[    8.653849] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   13.248819] ACPI: Unable to turn cooling device [f6c2cf18] 'on'
[   19.249495] ACPI: Unable to turn cooling device [f6c2cf18] 'on'
[   19.602902] udev: starting version 141
[   19.749205] Linux agpgart interface v0.103
[   19.803046] agpgart: Detected VIA KM400/KM400A chipset
[   19.807612] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   19.958774] parport_pc 00:0a: reported by Plug and Play ACPI
[   19.958884] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   20.003220] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.060659] nvidia: module license 'NVIDIA' taints kernel.
[   21.324879] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.326893] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   21.415902] ppdev: user-space parallel port driver
[   21.520481] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   21.748660] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   21.749079] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   21.749082] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   21.749094] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   21.845488] 3:2:1: cannot get freq at ep 0x84
[   21.852450] usbcore: registered new interface driver snd-usb-audio
[   21.992130] psmouse serio1: ID: 10 00 64<7>VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   22.509628] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   23.004254] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   23.004276] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   23.004820] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   23.004975] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   23.642447] lp0: using parport0 (interrupt-driven).
[   23.855912] EXT4 FS on sda3, internal journal on sda3:8
[   24.505608] type=1505 audit(1253193075.451:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2048
[   24.567059] type=1505 audit(1253193075.511:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2052
[   24.567340] type=1505 audit(1253193075.511:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2052
[   24.567441] type=1505 audit(1253193075.511:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2052
[   24.567527] type=1505 audit(1253193075.511:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2052
[   24.754924] type=1505 audit(1253193075.699:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2057
[   24.755338] type=1505 audit(1253193075.699:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2057
[   24.792264] type=1505 audit(1253193075.739:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2061
[   24.925249] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.967612] nf_conntrack version 0.5.0 (16383 buckets, 65532 max)
[   24.967945] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   24.967948] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   24.967950] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   25.044562] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   25.248780] ACPI: Unable to turn cooling device [f6c2cf18] 'on'
[   27.294019] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   27.294025] vboxdrv: Successfully done.
[   27.294027] vboxdrv: Found 1 processor cores.
[   27.294199] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   27.294201] vboxdrv: Successfully loaded version 3.0.6 (interface 0x000e0000).

---

### Post by the8thstar on 2009-09-17
Bump

---

### Post by louieb on 2009-09-17
blkid has a bug sometime its cache doesn't get updated.
try 
```
sudo blkid -c /dev/null 
```and compare again 

an alternate is replace  the UUID in /etc/fstab
```

# /home was on /dev/sda4 during installation
/dev/sda4  /home           ext4    relatime        0       2

```from the mount output. 
> /dev/sda4 on /mnt type ext4 (rw)                      Sometimes this will break things. Best not to mount a partition directly on /mnt  - make a subdirectory like /mnt/zzz and mount the partition on the subdirectory.

---

### Post by the8thstar on 2009-09-19
Alright guys, I followed your directions and I was able to make Ubuntu work again! Thanks alot!

On a side note, I still need to solve my error 13 in Grub when I want to boot Windows XP. Yet another adventure!

---

