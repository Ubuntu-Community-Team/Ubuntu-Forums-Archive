---
title: "increase the size of my trash?"
date: 2008-08-19
forum: General Help
---

### Post by jmate24 on 2008-08-19
hi, i am wondering how to increase the size of my trash?

---

### Post by finer recliner on 2008-08-19
as far as i know, there is no cap for how large your trash folder can be.

---

### Post by jerome1232 on 2008-08-19
Well other than the size of remaining free space on your drive, I agree, I've put 64 GB files in there.

---

### Post by jmate24 on 2008-08-19
for some odd reason in hardy it will only let me have about 1GB and i have a 250GB SATA hard drive.

---

### Post by jmate24 on 2008-08-22
now it is not letting me have any space for trash at all...

---

### Post by coffeecat on 2008-08-22
Have a look in System > Administration > System Monitor. Click on the File Systems tab. See what Total, Free, Available and Used is showing for your root (and /home if you have one) partitions. Do you have a separate /home partition?

---

### Post by FluffyElmo on 2008-08-22
In a terminal window, *Applications->Accessories->Terminal*, type the following command followed by Enter and post the result.
```
df
```

This will show the size and free disk space on all mounted filesystems. The trash should be limited only by free space and we may have a better idea of what's happing once we know your disk layout.

---

### Post by jmate24 on 2008-08-22
jm8241982@jm8241982-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            237155808 104102552 121101300  47% /
varrun                 1037332       116   1037216   1% /var/run
varlock                1037332         0   1037332   0% /var/lock
udev                   1037332        64   1037268   1% /dev
devshm                 1037332       136   1037196   1% /dev/shm
lrm                    1037332     39760    997572   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon     237155808 104102552 121101300  47% /home/jm8241982/.gvfs
/dev/sdb1            976760000  97925444 878834556  11% /media/disk
/dev/sdc1              1011792   1011280       512 100% /media/disk-1
/dev/sdd1               987696     70480    917216   8% /media/disk-2
jm8241982@jm8241982-desktop:~$

---

### Post by FluffyElmo on 2008-08-22
I think I know what the problem might be. Ubuntu doesn't have one global trash file, it stores the trash on the drive it's deleted from. So if you're deleting files from disk-1 (/dev/sdc1) which is 100% used then you are going to hit a limit on the size of your trash folder. 

I'm not sure how to change this, if it can be changed but one option would be to enable the delete command. Open your home folder, hit *Edit->Preferences* and under the behavior tab you can check "Include a delete command that bypasses trash". Now if you right click on a file or folder you will see a *Delete* item which will delete items directly bypassing the trash. Note that this means you can't recover these files if you make a mistake, but for a removable drive it sometimes makes sense.

---

### Post by jmate24 on 2008-08-22
here is my sys logs:

Aug 22 07:43:23 jm8241982-desktop syslogd 1.5.0#1ubuntu1: restart.
Aug 22 07:43:23 jm8241982-desktop anacron[16732]: Job `cron.daily' terminated
Aug 22 07:43:23 jm8241982-desktop anacron[16732]: Normal exit (1 job run)
Aug 22 07:49:39 jm8241982-desktop NetworkManager: <debug> [1219412979.350617] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_634933248'). 
Aug 22 07:50:08 jm8241982-desktop NetworkManager: <debug> [1219413008.497030] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_500637696'). 
Aug 22 08:02:47 jm8241982-desktop NetworkManager: <debug> [1219413767.490567] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_500637696'). 
Aug 22 08:03:28 jm8241982-desktop NetworkManager: <debug> [1219413808.681284] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_633204736'). 
Aug 22 08:15:06 jm8241982-desktop NetworkManager: <debug> [1219414506.046955] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_633204736'). 
Aug 22 08:16:04 jm8241982-desktop NetworkManager: <debug> [1219414564.543569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_514037760'). 
Aug 22 08:17:01 jm8241982-desktop /USR/SBIN/CRON[18049]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 08:28:24 jm8241982-desktop kernel: [51720.720173] xine_extractor[18555]: segfault at b2f3b8b1 eip b7770a17 esp b52d9690 error 4
Aug 22 08:40:22 jm8241982-desktop NetworkManager: <debug> [1219416022.963973] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_514037760'). 
Aug 22 08:40:49 jm8241982-desktop NetworkManager: <debug> [1219416049.712023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_572454912'). 
Aug 22 09:04:35 jm8241982-desktop -- MARK --
Aug 22 09:17:01 jm8241982-desktop /USR/SBIN/CRON[19499]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 09:20:02 jm8241982-desktop NetworkManager: <debug> [1219418402.469138] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_572454912'). 
Aug 22 09:21:46 jm8241982-desktop kernel: [54913.691643] xine_extractor[19831]: segfault at b2ec70e1 eip b7735a17 esp b529e690 error 4
Aug 22 09:21:48 jm8241982-desktop kernel: [54914.794467] xine_extractor[19839]: segfault at 5562e840 eip b76bb797 esp b5309c10 error 4
Aug 22 09:37:33 jm8241982-desktop NetworkManager: <debug> [1219419453.703918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_652646400'). 
Aug 22 09:50:22 jm8241982-desktop NetworkManager: <debug> [1219420222.108068] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_652646400'). 
Aug 22 09:51:46 jm8241982-desktop NetworkManager: <debug> [1219420306.483912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_511614976'). 
Aug 22 10:02:25 jm8241982-desktop NetworkManager: <debug> [1219420945.828479] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_511614976'). 
Aug 22 10:02:56 jm8241982-desktop NetworkManager: <debug> [1219420976.780903] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_711454720'). 
Aug 22 10:13:21 jm8241982-desktop NetworkManager: <debug> [1219421601.335666] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_711454720'). 
Aug 22 10:17:02 jm8241982-desktop /USR/SBIN/CRON[21743]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 10:44:35 jm8241982-desktop -- MARK --
Aug 22 11:04:35 jm8241982-desktop -- MARK --
Aug 22 11:17:01 jm8241982-desktop /USR/SBIN/CRON[23470]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 11:44:35 jm8241982-desktop -- MARK --
Aug 22 12:04:35 jm8241982-desktop -- MARK --
Aug 22 12:06:57 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 22 12:06:57 jm8241982-desktop kernel: [64793.851045] usblp0: removed
Aug 22 12:06:57 jm8241982-desktop kernel: [64794.147226] audit(1219428417.731:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=27265 profile="/usr/sbin/cupsd" namespace="default"
Aug 22 12:06:58 jm8241982-desktop hpijs: WARNING: color pen has low ink 
Aug 22 12:06:58 jm8241982-desktop hpijs: STATE: marker-supply-low-warning 
Aug 22 12:06:58 jm8241982-desktop hal_lpadmin: remove
Aug 22 12:06:58 jm8241982-desktop hal_lpadmin: Found configured printer: deskjet_3520
Aug 22 12:06:58 jm8241982-desktop NetworkManager: <debug> [1219428418.843483] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 22 12:08:25 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 22 12:17:01 jm8241982-desktop /USR/SBIN/CRON[28959]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 12:32:30 jm8241982-desktop NetworkManager: <debug> [1219429950.529257] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_442542080'). 
Aug 22 12:44:35 jm8241982-desktop -- MARK --
Aug 22 12:51:08 jm8241982-desktop NetworkManager: <debug> [1219431068.316792] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_442542080'). 

my kern.log

Aug 18 22:00:09 jm8241982-desktop kernel: [30031.033658] gdm[5341]: segfault at 6e61745f eip b774ee66 esp bfeccf88 error 4
Aug 18 22:00:09 jm8241982-desktop kernel: [30031.526659] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 18 22:01:09 jm8241982-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 18 22:01:09 jm8241982-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 18 22:01:09 jm8241982-desktop kernel: Symbols match kernel version 2.6.24.
Aug 18 22:01:09 jm8241982-desktop kernel: Loaded 14949 symbols from 82 modules.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] 896MB LOWMEM available.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] found SMP MP-table at 000f37a0
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Zone PFN ranges:
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   DMA             0 ->     4096
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   HighMem    229376 ->   524016
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]     0:        0 ->   524016
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] DMI 2.3 present.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 P4M80P)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: RSDT 7FEF3040, 002C (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: DSDT 7FEF3180, 4EA6 (r1 P4M80P AWRDACPI     1000 MSFT  100000E)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: FACS 7FEF0000, 0040
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: APIC 7FEF8080, 0084 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Processor #0 15:3 APIC version 20
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Processor #1 15:3 APIC version 20
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:7ed00000)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519923
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Kernel command line: root=UUID=0b1db72d-695f-4efc-b9c3-7ac6d48a3ea2 ro quiet splash
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Initializing CPU#0
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Detected 3200.468 MHz processor.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.390079] Console: colour VGA+ 80x25
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.390083] console [tty0] enabled
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.390820] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.391438] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502645] Memory: 2066072k/2096064k available (2177k kernel code, 28688k reserved, 1006k data, 368k init, 1178560k highmem)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502656] virtual kernel memory layout:
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502657]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502658]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502659]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502659]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502660]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502661]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502662]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502665] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.502724] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582514] Calibrating delay using timer specific routine.. 6408.35 BogoMIPS (lpj=12816719)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582548] Security Framework initialized
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582557] SELinux:  Disabled at boot.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582576] AppArmor: AppArmor initialized
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582580] Failure registering capabilities with primary security module.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582590] Mount-cache hash table entries: 512
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582745] Initializing cgroup subsys ns
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582750] Initializing cgroup subsys cpuacct
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582764] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582773] monitor/mwait feature present.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582775] using mwait in idle threads.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582781] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582783] CPU: L2 cache: 1024K
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582786] CPU: Physical Processor ID: 0
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582788] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582799] Compat vDSO mapped to ffffe000.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582818] Checking 'hlt' instruction... OK.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.598932] SMP alternatives: switching to UP code
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.600816] Early unpacking initramfs... done
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.877307] ACPI: Core revision 20070126
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.877369] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.881629] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.881651] SMP alternatives: switching to SMP code
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.882456] Booting processor 1/1 eip 3000
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.892640] Initializing CPU#1
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969335] Calibrating delay using timer specific routine.. 6400.72 BogoMIPS (lpj=12801444)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969349] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969356] monitor/mwait feature present.
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969363] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969366] CPU: L2 cache: 1024K
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969368] CPU: Physical Processor ID: 0
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969371] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969738] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969782] Total of 2 processors activated (12809.08 BogoMIPS).
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.970538] ENABLING IO-APIC IRQs
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.970860] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.117034] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.136990] Brought up 2 CPUs
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137052] CPU0 attaching sched-domain:
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137055]  domain 0: span 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137058]   groups: 01 02
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137061]   domain 1: span 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137063]    groups: 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137065] CPU1 attaching sched-domain:
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137067]  domain 0: span 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137069]   groups: 02 01
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137072]   domain 1: span 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137073]    groups: 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137338] net_namespace: 64 bytes
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137351] Booting paravirtualized kernel on bare hardware
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137896] Time:  4:00:41  Date: 08/19/08
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137922] NET: Registered protocol family 16
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.138176] EISA bus registered
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.138182] ACPI: bus type pci registered
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.146222] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.146225] PCI: Using configuration type 1
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.146250] Setting up standard PCI resources
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.153170] ACPI: EC: Look up EC in DSDT
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.158952] ACPI: Interpreter enabled
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.158959] ACPI: (supports S0 S1 S4 S5)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.158977] ACPI: Using IOAPIC for interrupt routing
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.164952] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.166214] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.206790] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.206956] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.207126] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.207275] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.207419] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.207557] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.207695] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.207833] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.208005] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.208160] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.208314] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.208492] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.208621] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.208667] pnp: PnP ACPI init
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.208675] ACPI: bus type pnp registered
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.211644] pnp: PnP ACPI: found 9 devices
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.211647] ACPI: ACPI bus type pnp unregistered
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.211651] PnPBIOS: Disabled by ACPI PNP
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.211968] PCI: Using ACPI for IRQ routing
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.211973] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.252640] NET: Registered protocol family 8
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.252642] NET: Registered protocol family 20
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.252717] AppArmor: AppArmor Filesystem Enabled
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.256478] Time: tsc clocksource has been installed.
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272616] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272620] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272622] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272625] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272628] system 00:00: iomem range 0x7fef0000-0x7fefffff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272631] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272633] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272636] system 00:00: iomem range 0x100000-0x7feeffff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272638] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272641] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272644] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272651] system 00:02: ioport range 0x400-0x47f has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272654] system 00:02: ioport range 0x500-0x50f has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272660] system 00:03: ioport range 0xb78-0xb7b has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272662] system 00:03: ioport range 0xf78-0xf7b has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272665] system 00:03: ioport range 0xa78-0xa7b has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272667] system 00:03: ioport range 0xe78-0xe7b has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272670] system 00:03: ioport range 0xbbc-0xbbf has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272672] system 00:03: ioport range 0xfbc-0xfbf has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272674] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272677] system 00:03: ioport range 0x800-0x87f has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272679] system 00:03: ioport range 0x880-0x8ff has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.272681] system 00:03: ioport range 0x290-0x297 has been reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.303119] PCI: Bridge: 0000:00:01.0
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.303123]   IO window: b000-bfff
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.303129]   MEM window: fb000000-fcffffff
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.303133]   PREFETCH window: e8000000-efffffff
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.303153] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.303164] NET: Registered protocol family 2
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.340439] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.340774] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.341474] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.342140] TCP: Hash tables configured (established 131072 bind 65536)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.342146] TCP reno registered
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.352539] checking if image is initramfs... it is
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.802824] Switched to high resolution mode on CPU 0
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.802954] Switched to high resolution mode on CPU 1
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.900441] Freeing initrd memory: 7305k freed
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.901376] audit: initializing netlink socket (disabled)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.901394] audit(1219118441.280:1): initialized
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.901653] highmem bounce pool size: 64 pages
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.903970] VFS: Disk quotas dquot_6.5.1
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.904066] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.904217] io scheduler noop registered
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.904219] io scheduler anticipatory registered
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.904221] io scheduler deadline registered
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.904232] io scheduler cfq registered (default)
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.904245] PCI: VIA PCI bridge detected. Disabling DAC.
Aug 18 22:01:09 jm8241982-desktop kernel: [   30.878222] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Aug 18 22:01:09 jm8241982-desktop kernel: [   30.878250] PCI: Bypassing VIA 8237 APIC De-Assert Message
Aug 18 22:01:09 jm8241982-desktop kernel: [   30.878273] Boot video device is 0000:01:00.0
Aug 18 22:01:09 jm8241982-desktop kernel: [   30.878653] isapnp: Scanning for PnP cards...
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.229789] isapnp: No Plug & Play device found
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.264155] Real Time Clock Driver v1.12ac
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.264274] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.266246] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.266326] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.266443] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.266445] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.266599] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286147] mice: PS/2 mouse device common for all mice
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286296] EISA: Probing bus 0 at eisa.0
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286338] EISA: Detected 0 cards.
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286341] cpuidle: using governor ladder
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286343] cpuidle: using governor menu
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286429] NET: Registered protocol family 1
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286459] Using IPI No-Shortcut mode
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286490] registered taskstats version 1
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286586]   Magic number: 4:821:9
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286726] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.286727] EDD information not available.
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.287080] Freeing unused kernel memory: 368k freed
Aug 18 22:01:09 jm8241982-desktop kernel: [   31.310250] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.524709] fuse init (API version 7.9)
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.546434] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.546449] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.856541] SCSI subsystem initialized
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.911268] libata version 3.00 loaded.
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.923908] usbcore: registered new interface driver usbfs
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.923945] usbcore: registered new interface driver hub
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.932089] sata_via 0000:00:0f.0: version 2.3
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.932411] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.932420] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.932474] sata_via 0000:00:0f.0: routed to hard irq line 11
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.932485] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.940014] usbcore: registered new device driver usb
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.942891] scsi0 : sata_via
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.967935] scsi1 : sata_via
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.968010] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf400 bmdma 0xe800 irq 16
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.968014] ata2: SATA max UDMA/133 cmd 0xf000 ctl 0xec00 bmdma 0xe808 irq 16
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.996554] USB Universal Host Controller Interface driver v3.0
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.171256] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.182842] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.182851] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.382619] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.546318] ata2.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.546323] ata2.00: 490234752 sectors, multi 1: LBA48 NCQ (depth 0/1)
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.554390] ata2.00: configured for UDMA/133
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.554540] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.554956] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.554964] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.554977] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.554981] uhci_hcd 0000:00:10.0: UHCI Host Controller
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.555258] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.555290] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000dc00
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.555433] usb usb1: configuration #1 chosen from 1 choice
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.555459] hub 1-0:1.0: USB hub found
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.555466] hub 1-0:1.0: 2 ports detected
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.657898] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.657914] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.657918] uhci_hcd 0000:00:10.1: UHCI Host Controller
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.657945] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.657968] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d800
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.658087] usb usb2: configuration #1 chosen from 1 choice
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.658114] hub 2-0:1.0: USB hub found
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.658120] hub 2-0:1.0: 2 ports detected
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.761593] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.761612] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.761618] uhci_hcd 0000:00:10.2: UHCI Host Controller
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.761657] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.761686] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000d400
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.761861] usb usb3: configuration #1 chosen from 1 choice
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.761903] hub 3-0:1.0: USB hub found
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.761911] hub 3-0:1.0: 2 ports detected
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.865255] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.865270] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.865275] uhci_hcd 0000:00:10.3: UHCI Host Controller
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.865309] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.865334] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000d000
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.865499] usb usb4: configuration #1 chosen from 1 choice
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.865536] hub 4-0:1.0: USB hub found
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.865546] hub 4-0:1.0: 2 ports detected
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.897033] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.970077] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.970087] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.970099] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.970477] eth0: VIA Rhine II at 0xfdffd000, 00:19:db:25:49:e1, IRQ 18.
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.971186] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.971244] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.971256] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.971261] ehci_hcd 0000:00:10.4: EHCI Host Controller
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.971300] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.971345] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfdffe000
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.020666] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.020833] usb usb5: configuration #1 chosen from 1 choice
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.020872] hub 5-0:1.0: USB hub found
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.020881] hub 5-0:1.0: 8 ports detected
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.124591] pata_via 0000:00:0f.1: version 0.3.3
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.124636] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.124698] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.124806] scsi2 : pata_via
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.124888] scsi3 : pata_via
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.127123] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.127130] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.419444] usb 1-1: device not accepting address 2, error -71
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.459685] ata3.00: ATAPI: Optiarc DVD RW AD-7191A, 1.04, max UDMA/66
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.650981] ata3.00: configured for UDMA/66
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.817616] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7191A  1.04 PQ: 0 ANSI: 5
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.817788] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 19
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.817799] 3c59x: Donald Becker and others.
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.817808] 0000:00:05.0: 3Com PCI 3c905B Cyclone 100baseTx at f8842000.
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.817817] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852670] Driver 'sd' needs updating - please use bus_type methods
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852790] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852813] sd 1:0:0:0: [sda] Write Protect is off
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852817] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852850] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852936] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852958] sd 1:0:0:0: [sda] Write Protect is off
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852961] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852998] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.853006]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.868798]  sda1 sda2 < sda5 >
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.887367] sd 1:0:0:0: [sda] Attached SCSI disk
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.893917] sd 1:0:0:0: Attached scsi generic sg0 type 0
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.893950] sr 2:0:0:0: Attached scsi generic sg1 type 5
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.898402] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.898409] Uniform CD-ROM driver Revision: 3.20
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.898489] sr 2:0:0:0: Attached scsi CD-ROM sr0
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.178691] Attempting manual resume
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.178695] swsusp: Resume From Partition 8:5
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.178697] PM: Checking swsusp image.
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.178872] PM: Resume from disk failed.
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.223036] kjournald starting.  Commit interval 5 seconds
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.223046] EXT3-fs: mounted filesystem with ordered data mode.
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.863054] usb 5-2: new high speed USB device using ehci_hcd and address 3
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.997071] usb 5-2: configuration #1 chosen from 1 choice
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.997300] hub 5-2:1.0: USB hub found
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.998199] hub 5-2:1.0: 4 ports detected
Aug 18 22:01:09 jm8241982-desktop kernel: [   36.285772] hub 5-0:1.0: over-current change on port 5
Aug 18 22:01:09 jm8241982-desktop kernel: [   36.389443] hub 5-0:1.0: over-current change on port 6
Aug 18 22:01:09 jm8241982-desktop kernel: [   36.493133] hub 5-0:1.0: over-current change on port 7
Aug 18 22:01:09 jm8241982-desktop kernel: [   36.596811] hub 5-0:1.0: over-current change on port 8
Aug 18 22:01:09 jm8241982-desktop kernel: [   36.939768] usb 2-2: new low speed USB device using uhci_hcd and address 2
Aug 18 22:01:09 jm8241982-desktop kernel: [   37.123146] usb 2-2: configuration #1 chosen from 1 choice
Aug 18 22:01:09 jm8241982-desktop kernel: [   37.363476] usb 1-1: new full speed USB device using uhci_hcd and address 4
Aug 18 22:01:09 jm8241982-desktop kernel: [   37.551372] usb 1-1: configuration #1 chosen from 1 choice
Aug 18 22:01:09 jm8241982-desktop kernel: [   37.754517] usb 5-2.1: new high speed USB device using ehci_hcd and address 5
Aug 18 22:01:09 jm8241982-desktop kernel: [   37.846839] usb 5-2.1: configuration #1 chosen from 1 choice
Aug 18 22:01:09 jm8241982-desktop kernel: [   42.083374] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 18 22:01:09 jm8241982-desktop kernel: [   42.145148] Linux agpgart interface v0.102
Aug 18 22:01:09 jm8241982-desktop kernel: [   42.200874] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 18 22:01:09 jm8241982-desktop kernel: [   42.263857] agpgart: Detected VIA VT3314 chipset
Aug 18 22:01:09 jm8241982-desktop kernel: [   42.270806] agpgart: AGP aperture is 128M @ 0xf0000000
Aug 18 22:01:09 jm8241982-desktop kernel: [   42.636165] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug 18 22:01:09 jm8241982-desktop kernel: [   43.091644] input: Power Button (FF) as /devices/virtual/input/input3
Aug 18 22:01:09 jm8241982-desktop kernel: [   43.125935] ACPI: Power Button (FF) [PWRF]
Aug 18 22:01:09 jm8241982-desktop kernel: [   43.126052] input: Power Button (CM) as /devices/virtual/input/input4
Aug 18 22:01:09 jm8241982-desktop kernel: [   43.145882] ACPI: Power Button (CM) [PWRB]
Aug 18 22:01:09 jm8241982-desktop kernel: [   43.145999] input: Sleep Button (CM) as /devices/virtual/input/input5
Aug 18 22:01:09 jm8241982-desktop kernel: [   43.177785] ACPI: Sleep Button (CM) [SLPB]
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.011871] udev: renamed network interface eth0 to eth1
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.049863] udev: renamed network interface eth1_rename to eth0
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.837273] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.837284] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.837433] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.914418] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.914453] usbcore: registered new interface driver usblp
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.961095] usbcore: registered new interface driver libusual
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.965130] usbcore: registered new interface driver hiddev
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.979859] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input6
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.988056] Initializing USB Mass Storage driver...
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.032202] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.032298] usbcore: registered new interface driver usbhid
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.032308] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.032916] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.033020] usbcore: registered new interface driver usb-storage
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.033025] USB Mass Storage support registered.
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.033196] usb-storage: device found at 5
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.033199] usb-storage: waiting for device to settle before scanning
Aug 18 22:01:09 jm8241982-desktop kernel: [   46.931892] lp: driver loaded but no devices found
Aug 18 22:01:09 jm8241982-desktop kernel: [   47.096571] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
Aug 18 22:01:09 jm8241982-desktop kernel: [   47.648863] EXT3 FS on sda1, internal journal
Aug 18 22:01:09 jm8241982-desktop kernel: [   49.059295] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 18 22:01:09 jm8241982-desktop kernel: [   49.504473] No dock devices found.
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.016147] usb-storage: device scan complete
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.017012] scsi 4:0:0:0: Direct-Access     ST310003 40NS                  PQ: 0 ANSI: 2 CCS
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.018871] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.025879] sd 4:0:0:0: [sdb] Write Protect is off
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.025886] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.025890] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.027451] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.028199] sd 4:0:0:0: [sdb] Write Protect is off
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.028204] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.028208] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.028213]  sdb: sdb1
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.042917] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.042984] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.671341] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.671349] apm: disabled - APM is not SMP safe.
Aug 18 22:01:10 jm8241982-desktop kernel: [   50.851831] ppdev: user-space parallel port driver
Aug 18 22:01:10 jm8241982-desktop kernel: [   51.008586] audit(1219118470.204:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4906 profile="/usr/sbin/cupsd" namespace="default"
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.281064] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.303011] eth0:  setting half-duplex.
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.394195] Bluetooth: Core ver 2.11
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.396413] NET: Registered protocol family 31
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.396420] Bluetooth: HCI device and connection manager initialized
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.396426] Bluetooth: HCI socket layer initialized
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.414224] Bluetooth: L2CAP ver 2.9
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.414232] Bluetooth: L2CAP socket layer initialized
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.458434] Bluetooth: RFCOMM socket layer initialized
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.458455] Bluetooth: RFCOMM TTY layer initialized
Aug 18 22:01:11 jm8241982-desktop kernel: [   52.458458] Bluetooth: RFCOMM ver 1.8
Aug 18 22:01:14 jm8241982-desktop kernel: [   55.622165] NET: Registered protocol family 17
Aug 18 22:01:17 jm8241982-desktop kernel: [   58.259082] NET: Registered protocol family 10
Aug 18 22:01:17 jm8241982-desktop kernel: [   58.259462] lo: Disabled Privacy Extensions
Aug 18 22:01:17 jm8241982-desktop kernel: [   58.260467] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 18 22:01:28 jm8241982-desktop kernel: [   68.272354] eth1: no IPv6 routers present
Aug 18 22:44:52 jm8241982-desktop kernel: [ 2664.224952] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 18 22:45:51 jm8241982-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 18 22:45:51 jm8241982-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 18 22:45:51 jm8241982-desktop kernel: Symbols match kernel version 2.6.24.
Aug 18 22:45:51 jm8241982-desktop kernel: Loaded 31287 symbols from 83 modules.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] 896MB LOWMEM available.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] found SMP MP-table at 000f37a0
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Zone PFN ranges:
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   DMA             0 ->     4096
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   HighMem    229376 ->   524016
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]     0:        0 ->   524016
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] DMI 2.3 present.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 P4M80P)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: RSDT 7FEF3040, 002C (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: DSDT 7FEF3180, 4EA6 (r1 P4M80P AWRDACPI     1000 MSFT  100000E)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: FACS 7FEF0000, 0040
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: APIC 7FEF8080, 0084 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Processor #0 15:3 APIC version 20
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Processor #1 15:3 APIC version 20
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:7ed00000)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519923
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Kernel command line: root=UUID=0b1db72d-695f-4efc-b9c3-7ac6d48a3ea2 ro quiet splash
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Initializing CPU#0
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Detected 3200.170 MHz processor.
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.669176] Console: colour VGA+ 80x25
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.669181] console [tty0] enabled
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.669922] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.670557] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780825] Memory: 2066072k/2096064k available (2177k kernel code, 28688k reserved, 1006k data, 368k init, 1178560k highmem)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780835] virtual kernel memory layout:
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780836]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780837]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780838]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780839]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780840]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780841]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780842]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780844] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.780903] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860694] Calibrating delay using timer specific routine.. 6408.37 BogoMIPS (lpj=12816745)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860727] Security Framework initialized
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860736] SELinux:  Disabled at boot.
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860754] AppArmor: AppArmor initialized
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860759] Failure registering capabilities with primary security module.
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860768] Mount-cache hash table entries: 512
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860920] Initializing cgroup subsys ns
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860926] Initializing cgroup subsys cpuacct
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860940] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860949] monitor/mwait feature present.
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860951] using mwait in idle threads.
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860958] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860960] CPU: L2 cache: 1024K
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860963] CPU: Physical Processor ID: 0
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860965] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860977] Compat vDSO mapped to ffffe000.
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860996] Checking 'hlt' instruction... OK.
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.877111] SMP alternatives: switching to UP code
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.878996] Early unpacking initramfs... done
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.155671] ACPI: Core revision 20070126
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.155733] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.160005] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.160026] SMP alternatives: switching to SMP code
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.160820] Booting processor 1/1 eip 3000
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.171004] Initializing CPU#1
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251502] Calibrating delay using timer specific routine.. 6400.75 BogoMIPS (lpj=12801500)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251513] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251520] monitor/mwait feature present.
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251526] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251529] CPU: L2 cache: 1024K
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251531] CPU: Physical Processor ID: 0
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251534] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251901] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251945] Total of 2 processors activated (12809.12 BogoMIPS).
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.252702] ENABLING IO-APIC IRQs
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.253024] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.399201] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419155] Brought up 2 CPUs
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419218] CPU0 attaching sched-domain:
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419221]  domain 0: span 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419224]   groups: 01 02
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419227]   domain 1: span 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419229]    groups: 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419231] CPU1 attaching sched-domain:
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419233]  domain 0: span 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419235]   groups: 02 01
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419238]   domain 1: span 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419240]    groups: 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419500] net_namespace: 64 bytes
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419513] Booting paravirtualized kernel on bare hardware
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.420058] Time:  4:45:23  Date: 08/19/08
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.420085] NET: Registered protocol family 16
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.420339] EISA bus registered
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.420345] ACPI: bus type pci registered
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.428383] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.428385] PCI: Using configuration type 1
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.428411] Setting up standard PCI resources
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.436120] ACPI: EC: Look up EC in DSDT
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.441876] ACPI: Interpreter enabled
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.441882] ACPI: (supports S0 S1 S4 S5)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.441901] ACPI: Using IOAPIC for interrupt routing
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.447897] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.449168] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.489734] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.489900] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.490066] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.490216] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.490360] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.490498] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.490636] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.490774] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.490958] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.491116] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.491272] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.491452] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.491581] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.491621] pnp: PnP ACPI init
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.491629] ACPI: bus type pnp registered
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.494598] pnp: PnP ACPI: found 9 devices
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.494601] ACPI: ACPI bus type pnp unregistered
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.494606] PnPBIOS: Disabled by ACPI PNP
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.494911] PCI: Using ACPI for IRQ routing
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.494915] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.534805] NET: Registered protocol family 8
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.534808] NET: Registered protocol family 20
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.534883] AppArmor: AppArmor Filesystem Enabled
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.538646] Time: tsc clocksource has been installed.
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554781] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554784] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554787] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554790] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554792] system 00:00: iomem range 0x7fef0000-0x7fefffff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554795] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554798] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554801] system 00:00: iomem range 0x100000-0x7feeffff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554803] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554806] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554808] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554816] system 00:02: ioport range 0x400-0x47f has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554818] system 00:02: ioport range 0x500-0x50f has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554824] system 00:03: ioport range 0xb78-0xb7b has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554827] system 00:03: ioport range 0xf78-0xf7b has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554829] system 00:03: ioport range 0xa78-0xa7b has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554831] system 00:03: ioport range 0xe78-0xe7b has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554834] system 00:03: ioport range 0xbbc-0xbbf has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554836] system 00:03: ioport range 0xfbc-0xfbf has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554839] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554841] system 00:03: ioport range 0x800-0x87f has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554843] system 00:03: ioport range 0x880-0x8ff has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.554846] system 00:03: ioport range 0x290-0x297 has been reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.585279] PCI: Bridge: 0000:00:01.0
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.585283]   IO window: b000-bfff
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.585288]   MEM window: fb000000-fcffffff
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.585293]   PREFETCH window: e8000000-efffffff
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.585312] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.585324] NET: Registered protocol family 2
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.622611] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.622953] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.623656] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.624326] TCP: Hash tables configured (established 131072 bind 65536)
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.624329] TCP reno registered
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.634688] checking if image is initramfs... it is
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.084991] Switched to high resolution mode on CPU 0
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.085119] Switched to high resolution mode on CPU 1
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.183629] Freeing initrd memory: 7305k freed
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.184578] audit: initializing netlink socket (disabled)
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.184595] audit(1219121123.284:1): initialized
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.184856] highmem bounce pool size: 64 pages
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.187169] VFS: Disk quotas dquot_6.5.1
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.187263] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.187412] io scheduler noop registered
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.187415] io scheduler anticipatory registered
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.187417] io scheduler deadline registered
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.187428] io scheduler cfq registered (default)
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.187441] PCI: VIA PCI bridge detected. Disabling DAC.
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.159588] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.159616] PCI: Bypassing VIA 8237 APIC De-Assert Message
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.159639] Boot video device is 0000:01:00.0
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.160026] isapnp: Scanning for PnP cards...
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.510815] isapnp: No Plug & Play device found
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.545019] Real Time Clock Driver v1.12ac
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.545137] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.546622] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.546699] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.546815] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.546818] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.546970] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574388] mice: PS/2 mouse device common for all mice
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574542] EISA: Probing bus 0 at eisa.0
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574584] EISA: Detected 0 cards.
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574587] cpuidle: using governor ladder
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574590] cpuidle: using governor menu
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574675] NET: Registered protocol family 1
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574705] Using IPI No-Shortcut mode
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574735] registered taskstats version 1
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574832]   Magic number: 4:98:768
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574937]   hash matches device ptyp4
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574969] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.574970] EDD information not available.
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.575322] Freeing unused kernel memory: 368k freed
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.598616] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 18 22:45:51 jm8241982-desktop kernel: [   31.812595] fuse init (API version 7.9)
Aug 18 22:45:51 jm8241982-desktop kernel: [   31.834171] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 18 22:45:51 jm8241982-desktop kernel: [   31.834186] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.064159] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.064173] 3c59x: Donald Becker and others.
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.064180] 0000:00:05.0: 3Com PCI 3c905B Cyclone 100baseTx at f883e000.
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.064187] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.160014] SCSI subsystem initialized
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.209621] libata version 3.00 loaded.
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.237169] usbcore: registered new interface driver usbfs
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.237206] usbcore: registered new interface driver hub
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.237341] sata_via 0000:00:0f.0: version 2.3
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.237664] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.237673] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.237726] sata_via 0000:00:0f.0: routed to hard irq line 11
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.237738] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.249317] usbcore: registered new device driver usb
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.250048] scsi0 : sata_via
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.263654] scsi1 : sata_via
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.263727] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf400 bmdma 0xe800 irq 17
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.263731] ata2: SATA max UDMA/133 cmd 0xf000 ctl 0xec00 bmdma 0xe808 irq 17
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.277042] USB Universal Host Controller Interface driver v3.0
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.420634] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.420647] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.468368] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.683680] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.847372] ata2.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.847377] ata2.00: 490234752 sectors, multi 1: LBA48 NCQ (depth 0/1)
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.855382] ata2.00: configured for UDMA/133
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.855534] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.856152] pata_via 0000:00:0f.1: version 0.3.3
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.856199] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.856253] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.856355] scsi2 : pata_via
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.856426] scsi3 : pata_via
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.858293] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.858297] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.191442] ata3.00: ATAPI: Optiarc DVD RW AD-7191A, 1.04, max UDMA/66
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.377734] ata3.00: configured for UDMA/66
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.544382] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7191A  1.04 PQ: 0 ANSI: 5
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545188] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545197] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545213] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545219] uhci_hcd 0000:00:10.0: UHCI Host Controller
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545508] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545547] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000dc00
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545763] usb usb1: configuration #1 chosen from 1 choice
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545802] hub 1-0:1.0: USB hub found
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545811] hub 1-0:1.0: 2 ports detected
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.648789] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.648807] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.648813] uhci_hcd 0000:00:10.1: UHCI Host Controller
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.648849] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.648876] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000d800
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.649039] usb usb2: configuration #1 chosen from 1 choice
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.649076] hub 2-0:1.0: USB hub found
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.649085] hub 2-0:1.0: 2 ports detected
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.752439] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.752455] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.752460] uhci_hcd 0000:00:10.2: UHCI Host Controller
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.752500] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.752526] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d400
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.752689] usb usb3: configuration #1 chosen from 1 choice
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.752726] hub 3-0:1.0: USB hub found
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.752736] hub 3-0:1.0: 2 ports detected
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.856140] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.856159] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.856165] uhci_hcd 0000:00:10.3: UHCI Host Controller
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.856209] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.856236] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000d000
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.856404] usb usb4: configuration #1 chosen from 1 choice
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.856442] hub 4-0:1.0: USB hub found
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.856450] hub 4-0:1.0: 2 ports detected
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.888891] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.959947] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.959965] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.959970] ehci_hcd 0000:00:10.4: EHCI Host Controller
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.960010] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.960062] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfdffe000
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.015490] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.015646] usb usb5: configuration #1 chosen from 1 choice
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.015686] hub 5-0:1.0: USB hub found
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.015696] hub 5-0:1.0: 8 ports detected
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.123821] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.123831] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.123843] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.124276] eth1: VIA Rhine II at 0xfdffd000, 00:19:db:25:49:e1, IRQ 19.
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.124987] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150464] Driver 'sd' needs updating - please use bus_type methods
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150594] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150622] sd 1:0:0:0: [sda] Write Protect is off
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150625] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150663] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150752] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150771] sd 1:0:0:0: [sda] Write Protect is off
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150776] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150814] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150821]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.169760]  sda1 sda2 < sda5 >
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.188331] sd 1:0:0:0: [sda] Attached SCSI disk
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.194974] sd 1:0:0:0: Attached scsi generic sg0 type 0
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.195007] sr 2:0:0:0: Attached scsi generic sg1 type 5
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.197597] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.197604] Uniform CD-ROM driver Revision: 3.20
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.197683] sr 2:0:0:0: Attached scsi CD-ROM sr0
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.414237] usb 1-1: device not accepting address 2, error -71
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.453233] Attempting manual resume
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.453237] swsusp: Resume From Partition 8:5
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.453239] PM: Checking swsusp image.
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.453413] PM: Resume from disk failed.
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.499087] kjournald starting.  Commit interval 5 seconds
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.499094] EXT3-fs: mounted filesystem with ordered data mode.
Aug 18 22:45:51 jm8241982-desktop kernel: [   35.853722] usb 5-2: new high speed USB device using ehci_hcd and address 3
Aug 18 22:45:51 jm8241982-desktop kernel: [   35.983603] usb 5-2: configuration #1 chosen from 1 choice
Aug 18 22:45:51 jm8241982-desktop kernel: [   35.983888] hub 5-2:1.0: USB hub found
Aug 18 22:45:51 jm8241982-desktop kernel: [   35.984113] hub 5-2:1.0: 4 ports detected
Aug 18 22:45:51 jm8241982-desktop kernel: [   36.268448] hub 5-0:1.0: over-current change on port 5
Aug 18 22:45:51 jm8241982-desktop kernel: [   36.372501] hub 5-0:1.0: over-current change on port 6
Aug 18 22:45:51 jm8241982-desktop kernel: [   36.475770] hub 5-0:1.0: over-current change on port 7
Aug 18 22:45:51 jm8241982-desktop kernel: [   36.579454] hub 5-0:1.0: over-current change on port 8
Aug 18 22:45:51 jm8241982-desktop kernel: [   36.922377] usb 2-2: new low speed USB device using uhci_hcd and address 2
Aug 18 22:45:51 jm8241982-desktop kernel: [   37.104876] usb 2-2: configuration #1 chosen from 1 choice
Aug 18 22:45:51 jm8241982-desktop kernel: [   37.345039] usb 1-1: new full speed USB device using uhci_hcd and address 4
Aug 18 22:45:51 jm8241982-desktop kernel: [   37.528685] usb 1-1: configuration #1 chosen from 1 choice
Aug 18 22:45:51 jm8241982-desktop kernel: [   37.728175] usb 5-2.1: new high speed USB device using ehci_hcd and address 5
Aug 18 22:45:51 jm8241982-desktop kernel: [   37.821351] usb 5-2.1: configuration #1 chosen from 1 choice
Aug 18 22:45:51 jm8241982-desktop kernel: [   40.954835] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.014735] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.341552] Linux agpgart interface v0.102
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.429346] agpgart: Detected VIA VT3314 chipset
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.436875] agpgart: AGP aperture is 128M @ 0xf0000000
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.617221] input: Power Button (FF) as /devices/virtual/input/input2
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.647541] ACPI: Power Button (FF) [PWRF]
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.647692] input: Power Button (CM) as /devices/virtual/input/input3
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.675460] ACPI: Power Button (CM) [PWRB]
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.675618] input: Sleep Button (CM) as /devices/virtual/input/input4
Aug 18 22:45:51 jm8241982-desktop kernel: [   41.711351] ACPI: Sleep Button (CM) [SLPB]
Aug 18 22:45:51 jm8241982-desktop kernel: [   42.502473] nvidia: module license 'NVIDIA' taints kernel.
Aug 18 22:45:51 jm8241982-desktop kernel: [   42.932704] usbcore: registered new interface driver hiddev
Aug 18 22:45:51 jm8241982-desktop kernel: [   42.948019] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input5
Aug 18 22:45:51 jm8241982-desktop kernel: [   42.960485] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2
Aug 18 22:45:51 jm8241982-desktop kernel: [   42.960516] usbcore: registered new interface driver usbhid
Aug 18 22:45:51 jm8241982-desktop kernel: [   42.960522] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.181267] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.181295] usbcore: registered new interface driver usblp
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.524046] usbcore: registered new interface driver libusual
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.596739] Initializing USB Mass Storage driver...
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.678177] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.696384] usbcore: registered new interface driver usb-storage
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.696393] USB Mass Storage support registered.
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.696520] usb-storage: device found at 5
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.696523] usb-storage: waiting for device to settle before scanning
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.995789] input: PC Speaker as /devices/platform/pcspkr/input/input6
Aug 18 22:45:51 jm8241982-desktop kernel: [   44.033101] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 18 22:45:51 jm8241982-desktop kernel: [   44.033114] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   44.033397] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Aug 18 22:45:51 jm8241982-desktop kernel: [   44.693098] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Aug 18 22:45:51 jm8241982-desktop kernel: [   44.693110] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
Aug 18 22:45:51 jm8241982-desktop kernel: [   44.693302] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   46.199665] lp: driver loaded but no devices found
Aug 18 22:45:51 jm8241982-desktop kernel: [   46.360175] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
Aug 18 22:45:51 jm8241982-desktop kernel: [   46.916706] EXT3 FS on sda1, internal journal
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.044759] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.488877] No dock devices found.
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.679619] usb-storage: device scan complete
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.680389] scsi 4:0:0:0: Direct-Access     ST310003 40NS                  PQ: 0 ANSI: 2 CCS
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.681867] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.682605] sd 4:0:0:0: [sdb] Write Protect is off
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.682613] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.682617] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.683719] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.684461] sd 4:0:0:0: [sdb] Write Protect is off
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.684466] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.684469] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.684474]  sdb: sdb1
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.708794] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.708862] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 18 22:45:51 jm8241982-desktop kernel: [   49.636588] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 18 22:45:51 jm8241982-desktop kernel: [   49.636596] apm: disabled - APM is not SMP safe.
Aug 18 22:45:51 jm8241982-desktop kernel: [   49.787541] ppdev: user-space parallel port driver
Aug 18 22:45:51 jm8241982-desktop kernel: [   49.935971] audit(1219121151.856:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4919 profile="/usr/sbin/cupsd" namespace="default"
Aug 18 22:45:52 jm8241982-desktop kernel: [   51.038896] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 18 22:45:52 jm8241982-desktop kernel: [   51.055586] eth0:  setting half-duplex.
Aug 18 22:45:53 jm8241982-desktop kernel: [   51.229643] Bluetooth: Core ver 2.11
Aug 18 22:45:53 jm8241982-desktop kernel: [   51.229953] NET: Registered protocol family 31
Aug 18 22:45:53 jm8241982-desktop kernel: [   51.229958] Bluetooth: HCI device and connection manager initialized
Aug 18 22:45:53 jm8241982-desktop kernel: [   51.229963] Bluetooth: HCI socket layer initialized
Aug 18 22:45:53 jm8241982-desktop kernel: [   51.246965] Bluetooth: L2CAP ver 2.9
Aug 18 22:45:53 jm8241982-desktop kernel: [   51.246973] Bluetooth: L2CAP socket layer initialized
Aug 18 22:45:53 jm8241982-desktop kernel: [   51.311209] Bluetooth: RFCOMM socket layer initialized
Aug 18 22:45:53 jm8241982-desktop kernel: [   51.311231] Bluetooth: RFCOMM TTY layer initialized
Aug 18 22:45:53 jm8241982-desktop kernel: [   51.311234] Bluetooth: RFCOMM ver 1.8
Aug 18 22:45:55 jm8241982-desktop kernel: [   53.498663] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 18 22:45:55 jm8241982-desktop kernel: [   53.498690] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 18 22:45:55 jm8241982-desktop kernel: [   53.498790] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 18 22:45:56 jm8241982-desktop kernel: [   54.781628] NET: Registered protocol family 17
Aug 18 22:46:01 jm8241982-desktop kernel: [   59.468017] NET: Registered protocol family 10
Aug 18 22:46:01 jm8241982-desktop kernel: [   59.468457] lo: Disabled Privacy Extensions
Aug 18 22:46:01 jm8241982-desktop kernel: [   59.469228] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 18 22:46:11 jm8241982-desktop kernel: [   69.519997] eth1: no IPv6 routers present
Aug 18 22:50:00 jm8241982-desktop kernel: [  297.742225] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 18 22:50:01 jm8241982-desktop kernel: [  298.813435] usb 1-1: USB disconnect, address 4
Aug 18 22:50:01 jm8241982-desktop kernel: [  298.813781] usblp0: removed
Aug 19 05:59:01 jm8241982-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 19 05:59:01 jm8241982-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 19 05:59:01 jm8241982-desktop kernel: Symbols match kernel version 2.6.24.
Aug 19 05:59:01 jm8241982-desktop kernel: Loaded 31287 symbols from 83 modules.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] 896MB LOWMEM available.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] found SMP MP-table at 000f37a0
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Zone PFN ranges:
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   DMA             0 ->     4096
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   HighMem    229376 ->   524016
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]     0:        0 ->   524016
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] DMI 2.3 present.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 P4M80P)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: RSDT 7FEF3040, 002C (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: DSDT 7FEF3180, 4EA6 (r1 P4M80P AWRDACPI     1000 MSFT  100000E)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: FACS 7FEF0000, 0040
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: APIC 7FEF8080, 0084 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Processor #0 15:3 APIC version 20
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Processor #1 15:3 APIC version 20
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:7ed00000)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519923
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Kernel command line: root=UUID=0b1db72d-695f-4efc-b9c3-7ac6d48a3ea2 ro quiet splash
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Initializing CPU#0
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Detected 3200.526 MHz processor.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.066512] Console: colour VGA+ 80x25
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.066516] console [tty0] enabled
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.067257] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.067884] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178103] Memory: 2066072k/2096064k available (2177k kernel code, 28688k reserved, 1006k data, 368k init, 1178560k highmem)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178113] virtual kernel memory layout:
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178114]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178115]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178116]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178117]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178118]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178119]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178120]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178123] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.178181] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.257972] Calibrating delay using timer specific routine.. 6408.36 BogoMIPS (lpj=12816728)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258005] Security Framework initialized
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258014] SELinux:  Disabled at boot.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258034] AppArmor: AppArmor initialized
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258038] Failure registering capabilities with primary security module.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258048] Mount-cache hash table entries: 512
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258201] Initializing cgroup subsys ns
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258207] Initializing cgroup subsys cpuacct
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258222] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258231] monitor/mwait feature present.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258233] using mwait in idle threads.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258238] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258241] CPU: L2 cache: 1024K
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258244] CPU: Physical Processor ID: 0
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258246] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258258] Compat vDSO mapped to ffffe000.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258276] Checking 'hlt' instruction... OK.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.274389] SMP alternatives: switching to UP code
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.276273] Early unpacking initramfs... done
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.552585] ACPI: Core revision 20070126
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.552647] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.556883] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.556905] SMP alternatives: switching to SMP code
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.557727] Booting processor 1/1 eip 3000
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.567911] Initializing CPU#1
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.644792] Calibrating delay using timer specific routine.. 6400.69 BogoMIPS (lpj=12801397)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.644803] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.644810] monitor/mwait feature present.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.644817] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.644820] CPU: L2 cache: 1024K
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.644822] CPU: Physical Processor ID: 0
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.644825] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.645192] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.645236] Total of 2 processors activated (12809.06 BogoMIPS).
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.645993] ENABLING IO-APIC IRQs
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.646315] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.792495] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812451] Brought up 2 CPUs
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812514] CPU0 attaching sched-domain:
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812518]  domain 0: span 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812520]   groups: 01 02
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812523]   domain 1: span 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812525]    groups: 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812528] CPU1 attaching sched-domain:
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812529]  domain 0: span 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812531]   groups: 02 01
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812534]   domain 1: span 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812536]    groups: 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812810] net_namespace: 64 bytes
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812822] Booting paravirtualized kernel on bare hardware
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.813368] Time: 11:58:33  Date: 08/19/08
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.813393] NET: Registered protocol family 16
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.813647] EISA bus registered
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.813653] ACPI: bus type pci registered
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.821694] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.821697] PCI: Using configuration type 1
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.821722] Setting up standard PCI resources
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.828640] ACPI: EC: Look up EC in DSDT
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.834445] ACPI: Interpreter enabled
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.834451] ACPI: (supports S0 S1 S4 S5)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.834470] ACPI: Using IOAPIC for interrupt routing
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.840449] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.841712] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.882251] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.882416] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.882585] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.882735] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.882879] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.883018] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.883157] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.883295] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.883466] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.883620] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.883774] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.883952] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.884087] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.884128] pnp: PnP ACPI init
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.884136] ACPI: bus type pnp registered
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.887103] pnp: PnP ACPI: found 9 devices
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.887105] ACPI: ACPI bus type pnp unregistered
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.887110] PnPBIOS: Disabled by ACPI PNP
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.887430] PCI: Using ACPI for IRQ routing
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.887434] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.928101] NET: Registered protocol family 8
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.928104] NET: Registered protocol family 20
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.928179] AppArmor: AppArmor Filesystem Enabled
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.931937] Time: tsc clocksource has been installed.
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948079] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948082] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948085] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948087] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948090] system 00:00: iomem range 0x7fef0000-0x7fefffff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948093] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948096] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948098] system 00:00: iomem range 0x100000-0x7feeffff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948101] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948104] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948106] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948113] system 00:02: ioport range 0x400-0x47f has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948116] system 00:02: ioport range 0x500-0x50f has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948122] system 00:03: ioport range 0xb78-0xb7b has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948124] system 00:03: ioport range 0xf78-0xf7b has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948127] system 00:03: ioport range 0xa78-0xa7b has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948129] system 00:03: ioport range 0xe78-0xe7b has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948132] system 00:03: ioport range 0xbbc-0xbbf has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948134] system 00:03: ioport range 0xfbc-0xfbf has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948136] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948139] system 00:03: ioport range 0x800-0x87f has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948141] system 00:03: ioport range 0x880-0x8ff has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.948144] system 00:03: ioport range 0x290-0x297 has been reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.978579] PCI: Bridge: 0000:00:01.0
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.978583]   IO window: b000-bfff
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.978589]   MEM window: fb000000-fcffffff
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.978593]   PREFETCH window: e8000000-efffffff
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.978613] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.978624] NET: Registered protocol family 2
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.015900] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.016236] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.016934] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.017597] TCP: Hash tables configured (established 131072 bind 65536)
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.017603] TCP reno registered
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.028001] checking if image is initramfs... it is
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.478282] Switched to high resolution mode on CPU 0
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.478415] Switched to high resolution mode on CPU 1
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.575887] Freeing initrd memory: 7305k freed
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.576831] audit: initializing netlink socket (disabled)
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.576849] audit(1219147113.280:1): initialized
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.577107] highmem bounce pool size: 64 pages
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.579432] VFS: Disk quotas dquot_6.5.1
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.579524] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.579675] io scheduler noop registered
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.579678] io scheduler anticipatory registered
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.579680] io scheduler deadline registered
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.579692] io scheduler cfq registered (default)
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.579706] PCI: VIA PCI bridge detected. Disabling DAC.
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.553851] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.553879] PCI: Bypassing VIA 8237 APIC De-Assert Message
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.553902] Boot video device is 0000:01:00.0
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.554282] isapnp: Scanning for PnP cards...
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.905345] isapnp: No Plug & Play device found
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.939213] Real Time Clock Driver v1.12ac
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.939332] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.941244] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.941323] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.941442] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.941445] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.941599] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.972666] mice: PS/2 mouse device common for all mice
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.972826] EISA: Probing bus 0 at eisa.0
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.972868] EISA: Detected 0 cards.
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.972871] cpuidle: using governor ladder
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.972873] cpuidle: using governor menu
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.972960] NET: Registered protocol family 1
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.972990] Using IPI No-Shortcut mode
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.973018] registered taskstats version 1
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.973115]   Magic number: 4:49:985
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.973250] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.973252] EDD information not available.
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.973611] Freeing unused kernel memory: 368k freed
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.996825] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.210874] fuse init (API version 7.9)
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.232550] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.232564] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.705536] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.705547] 3c59x: Donald Becker and others.
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.705554] 0000:00:05.0: 3Com PCI 3c905B Cyclone 100baseTx at f883e000.
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.705562] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.795356] usbcore: registered new interface driver usbfs
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.795389] usbcore: registered new interface driver hub
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.796388] usbcore: registered new device driver usb
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.864248] SCSI subsystem initialized
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.871339] USB Universal Host Controller Interface driver v3.0
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.871731] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.871740] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.871755] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.871760] uhci_hcd 0000:00:10.0: UHCI Host Controller
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.872056] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.872092] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000dc00
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.872279] usb usb1: configuration #1 chosen from 1 choice
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.872315] hub 1-0:1.0: USB hub found
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.872324] hub 1-0:1.0: 2 ports detected
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.929427] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.929439] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.973996] libata version 3.00 loaded.
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.978683] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.978705] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.978712] uhci_hcd 0000:00:10.1: UHCI Host Controller
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.978758] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.978791] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d800
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.978984] usb usb2: configuration #1 chosen from 1 choice
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.979023] hub 2-0:1.0: USB hub found
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.979032] hub 2-0:1.0: 2 ports detected
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.082308] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.082323] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.082327] uhci_hcd 0000:00:10.2: UHCI Host Controller
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.082358] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.082382] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000d400
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.082516] usb usb3: configuration #1 chosen from 1 choice
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.082543] hub 3-0:1.0: USB hub found
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.082550] hub 3-0:1.0: 2 ports detected
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.185993] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.186008] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.186012] uhci_hcd 0000:00:10.3: UHCI Host Controller
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.186047] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.186072] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000d000
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.186191] usb usb4: configuration #1 chosen from 1 choice
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.186217] hub 4-0:1.0: USB hub found
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.186224] hub 4-0:1.0: 2 ports detected
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.217797] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.290243] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.290254] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.290268] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.290703] eth1: VIA Rhine II at 0xfdffd000, 00:19:db:25:49:e1, IRQ 18.
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.291414] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.291474] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.291492] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.291499] ehci_hcd 0000:00:10.4: EHCI Host Controller
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.291551] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.291616] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfdffe000
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.342410] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.342605] usb usb5: configuration #1 chosen from 1 choice
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.342654] hub 5-0:1.0: USB hub found
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.342664] hub 5-0:1.0: 8 ports detected
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.446360] sata_via 0000:00:0f.0: version 2.3
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.446713] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.446721] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.446774] sata_via 0000:00:0f.0: routed to hard irq line 11
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.446786] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.471396] scsi0 : sata_via
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.471492] scsi1 : sata_via
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.471543] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf400 bmdma 0xe800 irq 19
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.471547] ata2: SATA max UDMA/133 cmd 0xf000 ctl 0xec00 bmdma 0xe808 irq 19
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.672411] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.736199] usb 1-1: device not accepting address 2, error -71
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.883753] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.047477] ata2.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.047481] ata2.00: 490234752 sectors, multi 1: LBA48 NCQ (depth 0/1)
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.067410] ata2.00: configured for UDMA/133
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.067554] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.070049] pata_via 0000:00:0f.1: version 0.3.3
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.070093] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.070145] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.070361] scsi2 : pata_via
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.070443] scsi3 : pata_via
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.072436] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.072440] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.406603] ata3.00: ATAPI: Optiarc DVD RW AD-7191A, 1.04, max UDMA/66
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.593858] ata3.00: configured for UDMA/66
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.760481] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7191A  1.04 PQ: 0 ANSI: 5
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776572] Driver 'sd' needs updating - please use bus_type methods
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776702] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776731] sd 1:0:0:0: [sda] Write Protect is off
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776738] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776782] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776875] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776891] sd 1:0:0:0: [sda] Write Protect is off
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776894] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776921] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776926]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.788523]  sda1 sda2 < sda5 >
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.807088] sd 1:0:0:0: [sda] Attached SCSI disk
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.814524] sd 1:0:0:0: Attached scsi generic sg0 type 0
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.814557] sr 2:0:0:0: Attached scsi generic sg1 type 5
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.816191] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.816197] Uniform CD-ROM driver Revision: 3.20
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.816253] sr 2:0:0:0: Attached scsi CD-ROM sr0
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.051735] Attempting manual resume
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.051740] swsusp: Resume From Partition 8:5
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.051742] PM: Checking swsusp image.
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.051916] PM: Resume from disk failed.
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.101238] kjournald starting.  Commit interval 5 seconds
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.101246] EXT3-fs: mounted filesystem with ordered data mode.
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.171864] usb 5-2: new high speed USB device using ehci_hcd and address 3
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.304813] usb 5-2: configuration #1 chosen from 1 choice
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.305101] hub 5-2:1.0: USB hub found
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.305327] hub 5-2:1.0: 4 ports detected
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.591600] hub 5-0:1.0: over-current change on port 5
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.695279] hub 5-0:1.0: over-current change on port 6
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.798965] hub 5-0:1.0: over-current change on port 7
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.901652] hub 5-0:1.0: over-current change on port 8
Aug 19 05:59:01 jm8241982-desktop kernel: [   32.244609] usb 1-1: new full speed USB device using uhci_hcd and address 4
Aug 19 05:59:01 jm8241982-desktop kernel: [   32.429618] usb 1-1: configuration #1 chosen from 1 choice
Aug 19 05:59:01 jm8241982-desktop kernel: [   32.632674] usb 5-2.1: new high speed USB device using ehci_hcd and address 5
Aug 19 05:59:01 jm8241982-desktop kernel: [   32.725987] usb 5-2.1: configuration #1 chosen from 1 choice
Aug 19 05:59:01 jm8241982-desktop kernel: [   32.962433] usb 2-2: new low speed USB device using uhci_hcd and address 2
Aug 19 05:59:01 jm8241982-desktop kernel: [   33.145631] usb 2-2: configuration #1 chosen from 1 choice
Aug 19 05:59:01 jm8241982-desktop kernel: [   37.709182] Linux agpgart interface v0.102
Aug 19 05:59:01 jm8241982-desktop kernel: [   37.748241] agpgart: Detected VIA VT3314 chipset
Aug 19 05:59:01 jm8241982-desktop kernel: [   37.756274] agpgart: AGP aperture is 128M @ 0xf0000000
Aug 19 05:59:01 jm8241982-desktop kernel: [   37.795861] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 19 05:59:01 jm8241982-desktop kernel: [   37.840864] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 19 05:59:01 jm8241982-desktop kernel: [   37.977501] input: Power Button (FF) as /devices/virtual/input/input2
Aug 19 05:59:01 jm8241982-desktop kernel: [   37.988239] ACPI: Power Button (FF) [PWRF]
Aug 19 05:59:01 jm8241982-desktop kernel: [   37.988376] input: Power Button (CM) as /devices/virtual/input/input3
Aug 19 05:59:01 jm8241982-desktop kernel: [   38.020208] ACPI: Power Button (CM) [PWRB]
Aug 19 05:59:01 jm8241982-desktop kernel: [   38.020360] input: Sleep Button (CM) as /devices/virtual/input/input4
Aug 19 05:59:01 jm8241982-desktop kernel: [   38.052046] ACPI: Sleep Button (CM) [SLPB]
Aug 19 05:59:01 jm8241982-desktop kernel: [   38.817853] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
Aug 19 05:59:01 jm8241982-desktop kernel: [   38.817881] usbcore: registered new interface driver usblp
Aug 19 05:59:01 jm8241982-desktop kernel: [   39.384144] usbcore: registered new interface driver hiddev
Aug 19 05:59:01 jm8241982-desktop kernel: [   39.407498] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input5
Aug 19 05:59:01 jm8241982-desktop kernel: [   39.427969] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2
Aug 19 05:59:01 jm8241982-desktop kernel: [   39.428002] usbcore: registered new interface driver usbhid
Aug 19 05:59:01 jm8241982-desktop kernel: [   39.428010] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 19 05:59:01 jm8241982-desktop kernel: [   39.858043] nvidia: module license 'NVIDIA' taints kernel.
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.281687] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.281700] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.281972] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.326748] input: PC Speaker as /devices/platform/pcspkr/input/input6
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.602167] usbcore: registered new interface driver libusual
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.640178] Initializing USB Mass Storage driver...
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.647997] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.660545] usbcore: registered new interface driver usb-storage
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.660553] USB Mass Storage support registered.
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.660559] usb-storage: device found at 5
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.660561] usb-storage: waiting for device to settle before scanning
Aug 19 05:59:01 jm8241982-desktop kernel: [   41.114912] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Aug 19 05:59:01 jm8241982-desktop kernel: [   41.114923] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
Aug 19 05:59:01 jm8241982-desktop kernel: [   41.115075] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   42.586134] lp: driver loaded but no devices found
Aug 19 05:59:01 jm8241982-desktop kernel: [   42.744872] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
Aug 19 05:59:01 jm8241982-desktop kernel: [   43.302485] EXT3 FS on sda1, internal journal
Aug 19 05:59:01 jm8241982-desktop kernel: [   44.439113] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 05:59:01 jm8241982-desktop kernel: [   44.901097] No dock devices found.
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.645314] usb-storage: device scan complete
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.646062] scsi 4:0:0:0: Direct-Access     ST310003 40NS                  PQ: 0 ANSI: 2 CCS
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.652162] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.652913] sd 4:0:0:0: [sdb] Write Protect is off
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.652918] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.652921] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.654007] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.654754] sd 4:0:0:0: [sdb] Write Protect is off
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.654758] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.654761] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.654765]  sdb: sdb1
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.683341] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.683411] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 19 05:59:01 jm8241982-desktop kernel: [   46.100921] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 19 05:59:01 jm8241982-desktop kernel: [   46.100929] apm: disabled - APM is not SMP safe.
Aug 19 05:59:01 jm8241982-desktop kernel: [   46.256509] ppdev: user-space parallel port driver
Aug 19 05:59:01 jm8241982-desktop kernel: [   46.421565] audit(1219147141.953:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4915 profile="/usr/sbin/cupsd" namespace="default"
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.640694] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.663046] eth0:  setting half-duplex.
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.773426] Bluetooth: Core ver 2.11
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.773735] NET: Registered protocol family 31
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.773740] Bluetooth: HCI device and connection manager initialized
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.773745] Bluetooth: HCI socket layer initialized
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.888527] Bluetooth: L2CAP ver 2.9
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.888535] Bluetooth: L2CAP socket layer initialized
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.957922] Bluetooth: RFCOMM socket layer initialized
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.957941] Bluetooth: RFCOMM TTY layer initialized
Aug 19 05:59:03 jm8241982-desktop kernel: [   47.957944] Bluetooth: RFCOMM ver 1.8
Aug 19 05:59:05 jm8241982-desktop kernel: [   50.274634] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 19 05:59:05 jm8241982-desktop kernel: [   50.274654] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 19 05:59:05 jm8241982-desktop kernel: [   50.274735] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 19 05:59:06 jm8241982-desktop kernel: [   51.051441] NET: Registered protocol family 17
Aug 19 05:59:10 jm8241982-desktop kernel: [   55.087910] NET: Registered protocol family 10
Aug 19 05:59:10 jm8241982-desktop kernel: [   55.088384] lo: Disabled Privacy Extensions
Aug 19 05:59:10 jm8241982-desktop kernel: [   55.089114] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 19 05:59:21 jm8241982-desktop kernel: [   65.635118] eth1: no IPv6 routers present
Aug 19 12:40:25 jm8241982-desktop kernel: [24057.172339] compiz.real[5710]: segfault at 000b2c20 eip 08055a80 esp bfd5a020 error 4
Aug 19 12:40:27 jm8241982-desktop kernel: [24058.945098] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 19 12:40:27 jm8241982-desktop kernel: [24058.945118] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 19 12:40:27 jm8241982-desktop kernel: [24058.945206] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 19 13:05:29 jm8241982-desktop kernel: [25556.478534] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:05:29 jm8241982-desktop kernel: [25556.478551] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:05:29 jm8241982-desktop kernel: [25556.478555]          cdb be 00 00 04 0e 47 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:05:29 jm8241982-desktop kernel: [25556.478559]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:05:29 jm8241982-desktop kernel: [25556.478565] ata3.00: status: { DRDY }
Aug 19 13:05:34 jm8241982-desktop kernel: [25561.503301] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:05:39 jm8241982-desktop kernel: [25566.472254] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:05:39 jm8241982-desktop kernel: [25566.472262] ata3: soft resetting link
Aug 19 13:05:39 jm8241982-desktop kernel: [25566.994936] ata3.00: configured for UDMA/66
Aug 19 13:05:39 jm8241982-desktop kernel: [25566.994977] ata3: EH complete
Aug 19 13:08:03 jm8241982-desktop kernel: [25710.428467] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:08:03 jm8241982-desktop kernel: [25710.428484] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:08:03 jm8241982-desktop kernel: [25710.428486]          cdb be 00 00 04 0f a1 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:08:03 jm8241982-desktop kernel: [25710.428488]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:08:03 jm8241982-desktop kernel: [25710.428493] ata3.00: status: { DRDY }
Aug 19 13:08:08 jm8241982-desktop kernel: [25715.453232] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:08:13 jm8241982-desktop kernel: [25720.422189] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:08:13 jm8241982-desktop kernel: [25720.422196] ata3: soft resetting link
Aug 19 13:08:14 jm8241982-desktop kernel: [25720.944858] ata3.00: configured for UDMA/66
Aug 19 13:08:14 jm8241982-desktop kernel: [25720.944899] ata3: EH complete
Aug 19 13:09:50 jm8241982-desktop kernel: [25817.194241] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:09:50 jm8241982-desktop kernel: [25817.194258] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:09:50 jm8241982-desktop kernel: [25817.194260]          cdb be 00 00 04 10 16 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:09:50 jm8241982-desktop kernel: [25817.194262]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:09:50 jm8241982-desktop kernel: [25817.194267] ata3.00: status: { DRDY }
Aug 19 13:09:55 jm8241982-desktop kernel: [25822.218012] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:10:00 jm8241982-desktop kernel: [25827.186968] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:10:00 jm8241982-desktop kernel: [25827.186976] ata3: soft resetting link
Aug 19 13:10:01 jm8241982-desktop kernel: [25827.709634] ata3.00: configured for UDMA/66
Aug 19 13:10:01 jm8241982-desktop kernel: [25827.709672] ata3: EH complete
Aug 19 13:10:51 jm8241982-desktop kernel: [25877.558504] ata3.00: limiting speed to UDMA/44:PIO4
Aug 19 13:10:51 jm8241982-desktop kernel: [25877.558514] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:10:51 jm8241982-desktop kernel: [25877.558529] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:10:51 jm8241982-desktop kernel: [25877.558531]          cdb be 00 00 04 10 23 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:10:51 jm8241982-desktop kernel: [25877.558532]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:10:51 jm8241982-desktop kernel: [25877.558537] ata3.00: status: { DRDY }
Aug 19 13:10:56 jm8241982-desktop kernel: [25882.583260] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:11:01 jm8241982-desktop kernel: [25887.552221] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:11:01 jm8241982-desktop kernel: [25887.552230] ata3: soft resetting link
Aug 19 13:11:02 jm8241982-desktop kernel: [25888.074890] ata3.00: configured for UDMA/44
Aug 19 13:11:02 jm8241982-desktop kernel: [25888.074928] ata3: EH complete
Aug 19 13:12:47 jm8241982-desktop kernel: [25992.821549] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:12:47 jm8241982-desktop kernel: [25992.821566] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:12:47 jm8241982-desktop kernel: [25992.821568]          cdb be 00 00 04 10 92 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:12:47 jm8241982-desktop kernel: [25992.821570]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:12:47 jm8241982-desktop kernel: [25992.821574] ata3.00: status: { DRDY }
Aug 19 13:12:52 jm8241982-desktop kernel: [25997.846312] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:12:57 jm8241982-desktop kernel: [26002.815274] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:12:57 jm8241982-desktop kernel: [26002.815282] ata3: soft resetting link
Aug 19 13:12:57 jm8241982-desktop kernel: [26003.337939] ata3.00: configured for UDMA/44
Aug 19 13:12:57 jm8241982-desktop kernel: [26003.337981] ata3: EH complete
Aug 19 13:16:57 jm8241982-desktop kernel: [26242.828670] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:16:57 jm8241982-desktop kernel: [26242.828687] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:16:57 jm8241982-desktop kernel: [26242.828689]          cdb be 00 00 04 24 30 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:16:57 jm8241982-desktop kernel: [26242.828690]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:16:57 jm8241982-desktop kernel: [26242.828695] ata3.00: status: { DRDY }
Aug 19 13:17:02 jm8241982-desktop kernel: [26247.854431] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:17:05 jm8241982-desktop kernel: [26250.477498] ata3: soft resetting link
Aug 19 13:17:06 jm8241982-desktop kernel: [26251.000159] ata3.00: configured for UDMA/44
Aug 19 13:17:06 jm8241982-desktop kernel: [26251.000197] ata3: EH complete
Aug 19 13:17:56 jm8241982-desktop kernel: [26300.849020] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:17:56 jm8241982-desktop kernel: [26300.849034] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:17:56 jm8241982-desktop kernel: [26300.849036]          cdb be 00 00 04 24 3d 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:17:56 jm8241982-desktop kernel: [26300.849037]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:17:56 jm8241982-desktop kernel: [26300.849040] ata3.00: status: { DRDY }
Aug 19 13:18:01 jm8241982-desktop kernel: [26305.874778] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:18:06 jm8241982-desktop kernel: [26310.842742] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:18:06 jm8241982-desktop kernel: [26310.842749] ata3: soft resetting link
Aug 19 13:18:06 jm8241982-desktop kernel: [26311.365410] ata3.00: configured for UDMA/44
Aug 19 13:18:06 jm8241982-desktop kernel: [26311.365449] ata3: EH complete
Aug 19 13:18:56 jm8241982-desktop kernel: [26361.214271] ata3.00: limiting speed to UDMA/33:PIO4
Aug 19 13:18:56 jm8241982-desktop kernel: [26361.214280] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:18:56 jm8241982-desktop kernel: [26361.214297] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:18:56 jm8241982-desktop kernel: [26361.214299]          cdb be 00 00 04 24 4a 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:18:56 jm8241982-desktop kernel: [26361.214301]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:18:56 jm8241982-desktop kernel: [26361.214305] ata3.00: status: { DRDY }
Aug 19 13:19:01 jm8241982-desktop kernel: [26366.239468] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:19:06 jm8241982-desktop kernel: [26371.207995] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:19:06 jm8241982-desktop kernel: [26371.208003] ata3: soft resetting link
Aug 19 13:19:07 jm8241982-desktop kernel: [26371.731656] ata3.00: configured for UDMA/33
Aug 19 13:19:07 jm8241982-desktop kernel: [26371.731694] ata3: EH complete
Aug 19 13:19:57 jm8241982-desktop kernel: [26421.580517] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:19:57 jm8241982-desktop kernel: [26421.580534] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:19:57 jm8241982-desktop kernel: [26421.580539]          cdb be 00 00 04 24 57 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:19:57 jm8241982-desktop kernel: [26421.580543]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:19:57 jm8241982-desktop kernel: [26421.580549] ata3.00: status: { DRDY }
Aug 19 13:20:02 jm8241982-desktop kernel: [26426.605281] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:20:07 jm8241982-desktop kernel: [26431.574237] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:20:07 jm8241982-desktop kernel: [26431.574245] ata3: soft resetting link
Aug 19 13:20:07 jm8241982-desktop kernel: [26432.096915] ata3.00: configured for UDMA/33
Aug 19 13:20:07 jm8241982-desktop kernel: [26432.096957] ata3: EH complete
Aug 19 13:21:24 jm8241982-desktop kernel: [26508.229194] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:21:24 jm8241982-desktop kernel: [26508.229211] ata3.00: cmd a0/01:00:00:50:40/00:00:00:00:00/a0 tag 0 dma 16464 in
Aug 19 13:21:24 jm8241982-desktop kernel: [26508.229215]          cdb be 00 00 04 24 b2 00 00  07 f8 00 00 00 00 00 00
Aug 19 13:21:24 jm8241982-desktop kernel: [26508.229219]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:21:24 jm8241982-desktop kernel: [26508.229226] ata3.00: status: { DRDY }
Aug 19 13:21:29 jm8241982-desktop kernel: [26513.254954] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:21:34 jm8241982-desktop kernel: [26518.223911] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:21:34 jm8241982-desktop kernel: [26518.223918] ata3: soft resetting link
Aug 19 13:21:34 jm8241982-desktop kernel: [26518.745588] ata3.00: configured for UDMA/33
Aug 19 13:21:34 jm8241982-desktop kernel: [26518.745631] ata3: EH complete
Aug 19 13:22:24 jm8241982-desktop kernel: [26568.594446] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:22:24 jm8241982-desktop kernel: [26568.594464] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:22:24 jm8241982-desktop kernel: [26568.594466]          cdb be 00 00 04 24 b9 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:22:24 jm8241982-desktop kernel: [26568.594468]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:22:24 jm8241982-desktop kernel: [26568.594473] ata3.00: status: { DRDY }
Aug 19 13:22:29 jm8241982-desktop kernel: [26573.620204] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:22:34 jm8241982-desktop kernel: [26578.588170] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:22:34 jm8241982-desktop kernel: [26578.588178] ata3: soft resetting link
Aug 19 13:22:35 jm8241982-desktop kernel: [26579.111825] ata3.00: configured for UDMA/33
Aug 19 13:22:35 jm8241982-desktop kernel: [26579.111863] ata3: EH complete
Aug 19 13:27:41 jm8241982-desktop kernel: [26884.238865] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:27:41 jm8241982-desktop kernel: [26884.238883] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:27:41 jm8241982-desktop kernel: [26884.238885]          cdb be 00 00 04 26 f0 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:27:41 jm8241982-desktop kernel: [26884.238887]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:27:41 jm8241982-desktop kernel: [26884.238892] ata3.00: status: { DRDY }
Aug 19 13:27:46 jm8241982-desktop kernel: [26889.263624] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:27:51 jm8241982-desktop kernel: [26894.233578] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:27:51 jm8241982-desktop kernel: [26894.233586] ata3: soft resetting link
Aug 19 13:27:51 jm8241982-desktop kernel: [26894.756248] ata3.00: configured for UDMA/33
Aug 19 13:27:51 jm8241982-desktop kernel: [26894.756277] ata3: EH complete
Aug 19 13:30:17 jm8241982-desktop kernel: [27039.596541] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:30:17 jm8241982-desktop kernel: [27039.596558] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:30:17 jm8241982-desktop kernel: [27039.596560]          cdb be 00 00 04 37 1a 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:30:17 jm8241982-desktop kernel: [27039.596562]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:30:17 jm8241982-desktop kernel: [27039.596567] ata3.00: status: { DRDY }
Aug 19 13:30:20 jm8241982-desktop kernel: [27042.946367] ata3: soft resetting link
Aug 19 13:30:20 jm8241982-desktop kernel: [27043.470030] ata3.00: configured for UDMA/33
Aug 19 13:30:20 jm8241982-desktop kernel: [27043.470071] ata3: EH complete
Aug 19 13:31:10 jm8241982-desktop kernel: [27093.317892] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:31:10 jm8241982-desktop kernel: [27093.317906] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:31:10 jm8241982-desktop kernel: [27093.317908]          cdb be 00 00 04 37 27 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:31:10 jm8241982-desktop kernel: [27093.317909]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:31:10 jm8241982-desktop kernel: [27093.317912] ata3.00: status: { DRDY }
Aug 19 13:31:15 jm8241982-desktop kernel: [27098.342658] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:31:20 jm8241982-desktop kernel: [27103.312610] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:31:20 jm8241982-desktop kernel: [27103.312617] ata3: soft resetting link
Aug 19 13:31:21 jm8241982-desktop kernel: [27103.834284] ata3.00: configured for UDMA/33
Aug 19 13:31:21 jm8241982-desktop kernel: [27103.834324] ata3: EH complete
Aug 19 13:32:11 jm8241982-desktop kernel: [27153.683148] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:32:11 jm8241982-desktop kernel: [27153.683165] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:32:11 jm8241982-desktop kernel: [27153.683167]          cdb be 00 00 04 37 34 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:32:11 jm8241982-desktop kernel: [27153.683169]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:32:11 jm8241982-desktop kernel: [27153.683174] ata3.00: status: { DRDY }
Aug 19 13:32:16 jm8241982-desktop kernel: [27158.708902] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:32:21 jm8241982-desktop kernel: [27163.677859] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:32:21 jm8241982-desktop kernel: [27163.677867] ata3: soft resetting link
Aug 19 13:32:22 jm8241982-desktop kernel: [27164.200528] ata3.00: configured for UDMA/33
Aug 19 13:32:22 jm8241982-desktop kernel: [27164.200568] ata3: EH complete
Aug 19 13:33:12 jm8241982-desktop kernel: [27214.048394] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:33:12 jm8241982-desktop kernel: [27214.048411] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:33:12 jm8241982-desktop kernel: [27214.048413]          cdb be 00 00 04 37 41 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:33:12 jm8241982-desktop kernel: [27214.048415]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:33:12 jm8241982-desktop kernel: [27214.048419] ata3.00: status: { DRDY }
Aug 19 13:33:17 jm8241982-desktop kernel: [27219.074150] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:33:22 jm8241982-desktop kernel: [27224.043111] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:33:22 jm8241982-desktop kernel: [27224.043120] ata3: soft resetting link
Aug 19 13:33:22 jm8241982-desktop kernel: [27224.565780] ata3.00: configured for UDMA/33
Aug 19 13:33:22 jm8241982-desktop kernel: [27224.565818] ata3: EH complete
Aug 19 13:34:30 jm8241982-desktop kernel: [27292.379255] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:34:30 jm8241982-desktop kernel: [27292.379272] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:34:30 jm8241982-desktop kernel: [27292.379276]          cdb be 00 00 04 38 dc 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:34:30 jm8241982-desktop kernel: [27292.379280]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:34:30 jm8241982-desktop kernel: [27292.379287] ata3.00: status: { DRDY }
Aug 19 13:34:35 jm8241982-desktop kernel: [27297.405010] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:34:40 jm8241982-desktop kernel: [27302.373970] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:34:40 jm8241982-desktop kernel: [27302.373977] ata3: soft resetting link
Aug 19 13:34:41 jm8241982-desktop kernel: [27302.896638] ata3.00: configured for UDMA/33
Aug 19 13:34:41 jm8241982-desktop kernel: [27302.896678] ata3: EH complete
Aug 19 13:36:57 jm8241982-desktop kernel: [27439.099074] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:36:57 jm8241982-desktop kernel: [27439.099091] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:36:57 jm8241982-desktop kernel: [27439.099095]          cdb be 00 00 04 4d 5e 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:36:57 jm8241982-desktop kernel: [27439.099099]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:36:57 jm8241982-desktop kernel: [27439.099106] ata3.00: status: { DRDY }
Aug 19 13:37:02 jm8241982-desktop kernel: [27444.123850] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:37:06 jm8241982-desktop kernel: [27447.920343] ata3: soft resetting link
Aug 19 13:37:07 jm8241982-desktop kernel: [27448.443014] ata3.00: configured for UDMA/33
Aug 19 13:37:07 jm8241982-desktop kernel: [27448.443055] ata3: EH complete
Aug 19 13:37:57 jm8241982-desktop kernel: [27498.291874] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:37:57 jm8241982-desktop kernel: [27498.291892] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:37:57 jm8241982-desktop kernel: [27498.291894]          cdb be 00 00 04 4d 6b 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:37:57 jm8241982-desktop kernel: [27498.291896]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:37:57 jm8241982-desktop kernel: [27498.291901] ata3.00: status: { DRDY }
Aug 19 13:38:02 jm8241982-desktop kernel: [27503.316640] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:38:07 jm8241982-desktop kernel: [27508.285593] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:38:07 jm8241982-desktop kernel: [27508.285602] ata3: soft resetting link
Aug 19 13:38:07 jm8241982-desktop kernel: [27508.808259] ata3.00: configured for UDMA/33
Aug 19 13:38:07 jm8241982-desktop kernel: [27508.808299] ata3: EH complete
Aug 19 13:38:57 jm8241982-desktop kernel: [27558.657124] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:38:57 jm8241982-desktop kernel: [27558.657141] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:38:57 jm8241982-desktop kernel: [27558.657143]          cdb be 00 00 04 4d 78 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:38:57 jm8241982-desktop kernel: [27558.657145]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:38:57 jm8241982-desktop kernel: [27558.657150] ata3.00: status: { DRDY }
Aug 19 13:39:02 jm8241982-desktop kernel: [27563.682880] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:39:07 jm8241982-desktop kernel: [27568.651838] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:39:07 jm8241982-desktop kernel: [27568.651846] ata3: soft resetting link
Aug 19 13:39:08 jm8241982-desktop kernel: [27569.173516] ata3.00: configured for UDMA/33
Aug 19 13:39:08 jm8241982-desktop kernel: [27569.173557] ata3: EH complete
Aug 19 13:42:33 jm8241982-desktop kernel: [27774.260403] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:42:33 jm8241982-desktop kernel: [27774.260420] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:42:33 jm8241982-desktop kernel: [27774.260424]          cdb be 00 00 04 76 b7 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:42:33 jm8241982-desktop kernel: [27774.260428]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:42:33 jm8241982-desktop kernel: [27774.260435] ata3.00: status: { DRDY }
Aug 19 13:42:38 jm8241982-desktop kernel: [27779.286160] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:42:43 jm8241982-desktop kernel: [27784.255119] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:42:43 jm8241982-desktop kernel: [27784.255127] ata3: soft resetting link
Aug 19 13:42:44 jm8241982-desktop kernel: [27784.777789] ata3.00: configured for UDMA/33
Aug 19 13:42:44 jm8241982-desktop kernel: [27784.777832] ata3: EH complete
Aug 19 13:46:19 jm8241982-desktop kernel: [27999.311082] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:46:19 jm8241982-desktop kernel: [27999.311099] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:46:19 jm8241982-desktop kernel: [27999.311101]          cdb be 00 00 04 78 0a 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:46:19 jm8241982-desktop kernel: [27999.311103]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:46:19 jm8241982-desktop kernel: [27999.311108] ata3.00: status: { DRDY }
Aug 19 13:46:24 jm8241982-desktop kernel: [28004.335845] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:46:29 jm8241982-desktop kernel: [28009.304803] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:46:29 jm8241982-desktop kernel: [28009.304811] ata3: soft resetting link
Aug 19 13:46:30 jm8241982-desktop kernel: [28009.827469] ata3.00: configured for UDMA/33
Aug 19 13:46:30 jm8241982-desktop kernel: [28009.827509] ata3: EH complete
Aug 19 13:51:34 jm8241982-desktop kernel: [28312.857849] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:51:34 jm8241982-desktop kernel: [28312.857866] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:51:34 jm8241982-desktop kernel: [28312.857868]          cdb be 00 00 04 b8 93 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:51:34 jm8241982-desktop kernel: [28312.857870]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:51:34 jm8241982-desktop kernel: [28312.857875] ata3.00: status: { DRDY }
Aug 19 13:51:39 jm8241982-desktop kernel: [28317.882609] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:51:40 jm8241982-desktop kernel: [28319.055066] ata3: soft resetting link
Aug 19 13:51:40 jm8241982-desktop kernel: [28319.577731] ata3.00: configured for UDMA/33
Aug 19 13:51:40 jm8241982-desktop kernel: [28319.577774] ata3: EH complete
Aug 19 13:52:30 jm8241982-desktop kernel: [28369.427586] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:52:30 jm8241982-desktop kernel: [28369.427603] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:52:30 jm8241982-desktop kernel: [28369.427607]          cdb be 00 00 04 b8 a0 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:52:30 jm8241982-desktop kernel: [28369.427610]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:52:30 jm8241982-desktop kernel: [28369.427617] ata3.00: status: { DRDY }
Aug 19 13:52:35 jm8241982-desktop kernel: [28374.452349] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:52:40 jm8241982-desktop kernel: [28379.421307] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:52:40 jm8241982-desktop kernel: [28379.421315] ata3: soft resetting link
Aug 19 13:52:41 jm8241982-desktop kernel: [28379.943971] ata3.00: configured for UDMA/33
Aug 19 13:52:41 jm8241982-desktop kernel: [28379.944009] ata3: EH complete
Aug 19 13:53:31 jm8241982-desktop kernel: [28429.792835] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:53:31 jm8241982-desktop kernel: [28429.792852] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:53:31 jm8241982-desktop kernel: [28429.792856]          cdb be 00 00 04 b8 ad 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:53:31 jm8241982-desktop kernel: [28429.792860]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:53:31 jm8241982-desktop kernel: [28429.792867] ata3.00: status: { DRDY }
Aug 19 13:53:36 jm8241982-desktop kernel: [28434.816603] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:53:41 jm8241982-desktop kernel: [28439.785561] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:53:41 jm8241982-desktop kernel: [28439.785570] ata3: soft resetting link
Aug 19 13:53:42 jm8241982-desktop kernel: [28440.308230] ata3.00: configured for UDMA/33
Aug 19 13:53:42 jm8241982-desktop kernel: [28440.308270] ata3: EH complete
Aug 19 13:54:32 jm8241982-desktop kernel: [28490.157092] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:54:32 jm8241982-desktop kernel: [28490.157109] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:54:32 jm8241982-desktop kernel: [28490.157111]          cdb be 00 00 04 b8 ba 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:54:32 jm8241982-desktop kernel: [28490.157113]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:54:32 jm8241982-desktop kernel: [28490.157117] ata3.00: status: { DRDY }
Aug 19 13:54:37 jm8241982-desktop kernel: [28495.181850] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:54:42 jm8241982-desktop kernel: [28500.150808] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:54:42 jm8241982-desktop kernel: [28500.150815] ata3: soft resetting link
Aug 19 13:54:42 jm8241982-desktop kernel: [28500.673482] ata3.00: configured for UDMA/33
Aug 19 13:54:42 jm8241982-desktop kernel: [28500.673524] ata3: EH complete
Aug 19 13:55:32 jm8241982-desktop kernel: [28550.522363] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:55:32 jm8241982-desktop kernel: [28550.522385] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:55:32 jm8241982-desktop kernel: [28550.522387]          cdb be 00 00 04 b8 c7 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:55:32 jm8241982-desktop kernel: [28550.522389]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:55:32 jm8241982-desktop kernel: [28550.522394] ata3.00: status: { DRDY }
Aug 19 13:55:37 jm8241982-desktop kernel: [28555.547105] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:55:42 jm8241982-desktop kernel: [28560.516058] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 13:55:42 jm8241982-desktop kernel: [28560.516067] ata3: soft resetting link
Aug 19 13:55:43 jm8241982-desktop kernel: [28561.039720] ata3.00: configured for UDMA/33
Aug 19 13:55:43 jm8241982-desktop kernel: [28561.039759] ata3: EH complete
Aug 19 13:58:08 jm8241982-desktop kernel: [28706.208014] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 13:58:08 jm8241982-desktop kernel: [28706.208032] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 13:58:08 jm8241982-desktop kernel: [28706.208034]          cdb be 00 00 04 cb 7a 00 00  0d f8 00 00 00 00 00 00
Aug 19 13:58:08 jm8241982-desktop kernel: [28706.208036]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 13:58:08 jm8241982-desktop kernel: [28706.208041] ata3.00: status: { DRDY }
Aug 19 13:58:13 jm8241982-desktop kernel: [28711.231783] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 13:58:14 jm8241982-desktop kernel: [28711.845933] ata3: soft resetting link
Aug 19 13:58:14 jm8241982-desktop kernel: [28712.368586] ata3.00: configured for UDMA/33
Aug 19 13:58:14 jm8241982-desktop kernel: [28712.368624] ata3: EH complete
Aug 19 14:05:51 jm8241982-desktop kernel: [29167.801581] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 14:05:51 jm8241982-desktop kernel: [29167.801598] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 14:05:51 jm8241982-desktop kernel: [29167.801602]          cdb be 00 00 04 e3 80 00 00  0d f8 00 00 00 00 00 00
Aug 19 14:05:51 jm8241982-desktop kernel: [29167.801606]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 14:05:51 jm8241982-desktop kernel: [29167.801612] ata3.00: status: { DRDY }
Aug 19 14:05:54 jm8241982-desktop kernel: [29170.983925] ata3: soft resetting link
Aug 19 14:05:55 jm8241982-desktop kernel: [29171.506594] ata3.00: configured for UDMA/33
Aug 19 14:05:55 jm8241982-desktop kernel: [29171.506636] ata3: EH complete
Aug 19 14:05:55 jm8241982-desktop kernel: [29171.548953] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
Aug 19 14:05:55 jm8241982-desktop kernel: [29171.548969] sr: Sense Key : Medium Error [deferred] 
Aug 19 14:05:55 jm8241982-desktop kernel: [29171.548975] sr: Add. Sense: No seek complete
Aug 19 14:06:45 jm8241982-desktop kernel: [29221.395330] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 14:06:45 jm8241982-desktop kernel: [29221.395348] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 14:06:45 jm8241982-desktop kernel: [29221.395350]          cdb be 00 00 04 e3 8d 00 00  0d f8 00 00 00 00 00 00
Aug 19 14:06:45 jm8241982-desktop kernel: [29221.395352]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 14:06:45 jm8241982-desktop kernel: [29221.395357] ata3.00: status: { DRDY }
Aug 19 14:06:50 jm8241982-desktop kernel: [29226.029278] ata3: soft resetting link
Aug 19 14:06:50 jm8241982-desktop kernel: [29226.551948] ata3.00: configured for UDMA/33
Aug 19 14:06:50 jm8241982-desktop kernel: [29226.551986] ata3: EH complete
Aug 19 14:07:40 jm8241982-desktop kernel: [29276.400807] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 14:07:40 jm8241982-desktop kernel: [29276.400824] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 14:07:40 jm8241982-desktop kernel: [29276.400828]          cdb be 00 00 04 e3 9a 00 00  0d f8 00 00 00 00 00 00
Aug 19 14:07:40 jm8241982-desktop kernel: [29276.400832]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 14:07:40 jm8241982-desktop kernel: [29276.400839] ata3.00: status: { DRDY }
Aug 19 14:07:45 jm8241982-desktop kernel: [29281.426566] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 14:07:49 jm8241982-desktop kernel: [29285.613889] ata3: soft resetting link
Aug 19 14:07:50 jm8241982-desktop kernel: [29286.136562] ata3.00: configured for UDMA/33
Aug 19 14:07:50 jm8241982-desktop kernel: [29286.136602] ata3: EH complete
Aug 19 14:08:40 jm8241982-desktop kernel: [29335.985419] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 14:08:40 jm8241982-desktop kernel: [29335.985436] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 14:08:40 jm8241982-desktop kernel: [29335.985441]          cdb be 00 00 04 e3 a7 00 00  0d f8 00 00 00 00 00 00
Aug 19 14:08:40 jm8241982-desktop kernel: [29335.985444]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 14:08:40 jm8241982-desktop kernel: [29335.985451] ata3.00: status: { DRDY }
Aug 19 14:08:45 jm8241982-desktop kernel: [29341.010182] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 14:08:50 jm8241982-desktop kernel: [29345.978143] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 14:08:50 jm8241982-desktop kernel: [29345.978151] ata3: soft resetting link
Aug 19 14:08:50 jm8241982-desktop kernel: [29346.500814] ata3.00: configured for UDMA/33
Aug 19 14:08:50 jm8241982-desktop kernel: [29346.500853] ata3: EH complete
Aug 19 14:12:59 jm8241982-desktop kernel: [29594.048157] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 14:12:59 jm8241982-desktop kernel: [29594.048175] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 14:12:59 jm8241982-desktop kernel: [29594.048179]          cdb be 00 00 04 e4 09 00 00  0d f8 00 00 00 00 00 00
Aug 19 14:12:59 jm8241982-desktop kernel: [29594.048182]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 14:12:59 jm8241982-desktop kernel: [29594.048188] ata3.00: status: { DRDY }
Aug 19 14:13:01 jm8241982-desktop kernel: [29596.448873] ata3: soft resetting link
Aug 19 14:13:02 jm8241982-desktop kernel: [29596.971535] ata3.00: configured for UDMA/33
Aug 19 14:13:02 jm8241982-desktop kernel: [29596.971575] ata3: EH complete
Aug 19 14:13:52 jm8241982-desktop kernel: [29646.820394] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 14:13:52 jm8241982-desktop kernel: [29646.820411] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 14:13:52 jm8241982-desktop kernel: [29646.820416]          cdb be 00 00 04 e4 16 00 00  0d f8 00 00 00 00 00 00
Aug 19 14:13:52 jm8241982-desktop kernel: [29646.820419]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 14:13:52 jm8241982-desktop kernel: [29646.820426] ata3.00: status: { DRDY }
Aug 19 14:13:57 jm8241982-desktop kernel: [29651.845158] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 14:13:58 jm8241982-desktop kernel: [29653.352593] ata3: soft resetting link
Aug 19 14:13:59 jm8241982-desktop kernel: [29653.874265] ata3.00: configured for UDMA/33
Aug 19 14:13:59 jm8241982-desktop kernel: [29653.874304] ata3: EH complete
Aug 19 14:14:49 jm8241982-desktop kernel: [29703.723132] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 14:14:49 jm8241982-desktop kernel: [29703.723149] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 14:14:49 jm8241982-desktop kernel: [29703.723151]          cdb be 00 00 04 e4 23 00 00  0d f8 00 00 00 00 00 00
Aug 19 14:14:49 jm8241982-desktop kernel: [29703.723153]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 14:14:49 jm8241982-desktop kernel: [29703.723157] ata3.00: status: { DRDY }
Aug 19 14:14:54 jm8241982-desktop kernel: [29708.747897] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 14:14:59 jm8241982-desktop kernel: [29713.716850] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 14:14:59 jm8241982-desktop kernel: [29713.716859] ata3: soft resetting link
Aug 19 14:14:59 jm8241982-desktop kernel: [29714.239516] ata3.00: configured for UDMA/33
Aug 19 14:14:59 jm8241982-desktop kernel: [29714.239543] ata3: EH complete
Aug 19 14:15:50 jm8241982-desktop kernel: [29765.037556] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 14:15:50 jm8241982-desktop kernel: [29765.037579] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 14:15:50 jm8241982-desktop kernel: [29765.037583]          cdb be 00 00 04 e4 3d 00 00  0d f8 00 00 00 00 00 00
Aug 19 14:15:50 jm8241982-desktop kernel: [29765.037586]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 14:15:50 jm8241982-desktop kernel: [29765.037593] ata3.00: status: { DRDY }
Aug 19 14:15:55 jm8241982-desktop kernel: [29770.062265] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 14:16:00 jm8241982-desktop kernel: [29775.031230] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 14:16:00 jm8241982-desktop kernel: [29775.031238] ata3: soft resetting link
Aug 19 14:16:01 jm8241982-desktop kernel: [29775.554891] ata3.00: configured for UDMA/33
Aug 19 14:16:01 jm8241982-desktop kernel: [29775.554932] ata3: EH complete
Aug 19 14:16:51 jm8241982-desktop kernel: [29825.402765] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 14:16:51 jm8241982-desktop kernel: [29825.402783] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 14:16:51 jm8241982-desktop kernel: [29825.402785]          cdb be 00 00 04 e4 4a 00 00  0d f8 00 00 00 00 00 00
Aug 19 14:16:51 jm8241982-desktop kernel: [29825.402787]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 14:16:51 jm8241982-desktop kernel: [29825.402792] ata3.00: status: { DRDY }
Aug 19 14:16:56 jm8241982-desktop kernel: [29830.427516] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 14:17:01 jm8241982-desktop kernel: [29835.396473] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 14:17:01 jm8241982-desktop kernel: [29835.396481] ata3: soft resetting link
Aug 19 14:17:01 jm8241982-desktop kernel: [29835.919143] ata3.00: configured for UDMA/33
Aug 19 14:17:01 jm8241982-desktop kernel: [29835.919181] ata3: EH complete
Aug 19 14:17:53 jm8241982-desktop kernel: [29886.995723] sound-juicer[15718]: segfault at 00000018 eip b77552be esp bf92c530 error 4
Aug 19 16:36:35 jm8241982-desktop kernel: [38183.882214] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 16:36:35 jm8241982-desktop kernel: [38183.882231] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 16:36:35 jm8241982-desktop kernel: [38183.882235]          cdb be 00 00 03 80 47 00 00  0d f8 00 00 00 00 00 00
Aug 19 16:36:35 jm8241982-desktop kernel: [38183.882238]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 16:36:35 jm8241982-desktop kernel: [38183.882245] ata3.00: status: { DRDY }
Aug 19 16:36:40 jm8241982-desktop kernel: [38188.906978] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 16:36:42 jm8241982-desktop kernel: [38191.698529] ata3: soft resetting link
Aug 19 16:36:43 jm8241982-desktop kernel: [38192.221197] ata3.00: configured for UDMA/33
Aug 19 16:36:43 jm8241982-desktop kernel: [38192.221237] ata3: EH complete
Aug 19 16:37:33 jm8241982-desktop kernel: [38242.070060] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 16:37:33 jm8241982-desktop kernel: [38242.070077] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 16:37:33 jm8241982-desktop kernel: [38242.070079]          cdb be 00 00 03 80 54 00 00  0d f8 00 00 00 00 00 00
Aug 19 16:37:33 jm8241982-desktop kernel: [38242.070081]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 16:37:33 jm8241982-desktop kernel: [38242.070085] ata3.00: status: { DRDY }
Aug 19 16:37:38 jm8241982-desktop kernel: [38247.095815] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 16:37:43 jm8241982-desktop kernel: [38252.064771] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 16:37:43 jm8241982-desktop kernel: [38252.064778] ata3: soft resetting link
Aug 19 16:37:43 jm8241982-desktop kernel: [38252.587437] ata3.00: configured for UDMA/33
Aug 19 16:37:43 jm8241982-desktop kernel: [38252.587467] ata3: EH complete
Aug 19 16:38:33 jm8241982-desktop kernel: [38302.435308] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 16:38:33 jm8241982-desktop kernel: [38302.435325] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 16:38:33 jm8241982-desktop kernel: [38302.435327]          cdb be 00 00 03 80 61 00 00  0d f8 00 00 00 00 00 00
Aug 19 16:38:33 jm8241982-desktop kernel: [38302.435328]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 16:38:33 jm8241982-desktop kernel: [38302.435333] ata3.00: status: { DRDY }
Aug 19 16:38:39 jm8241982-desktop kernel: [38307.461067] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 16:38:44 jm8241982-desktop kernel: [38312.429243] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 16:38:44 jm8241982-desktop kernel: [38312.429252] ata3: soft resetting link
Aug 19 16:38:44 jm8241982-desktop kernel: [38312.952687] ata3.00: configured for UDMA/33
Aug 19 16:38:44 jm8241982-desktop kernel: [38312.952726] ata3: EH complete
Aug 19 16:44:24 jm8241982-desktop kernel: [38651.754773] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Aug 19 16:44:24 jm8241982-desktop kernel: [38651.754788] ata3.00: cmd a0/01:00:00:70:77/00:00:00:00:00/a0 tag 0 dma 30576 in
Aug 19 16:44:24 jm8241982-desktop kernel: [38651.754789]          cdb be 00 00 02 f1 1b 00 00  0d f8 00 00 00 00 00 00
Aug 19 16:44:24 jm8241982-desktop kernel: [38651.754790]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 19 16:44:24 jm8241982-desktop kernel: [38651.754793] ata3.00: status: { DRDY }
Aug 19 16:44:29 jm8241982-desktop kernel: [38656.786521] ata3: port is slow to respond, please be patient (Status 0xd0)
Aug 19 16:44:34 jm8241982-desktop kernel: [38661.760459] ata3: device not ready (errno=-16), forcing hardreset
Aug 19 16:44:34 jm8241982-desktop kernel: [38661.760466] ata3: soft resetting link
Aug 19 16:44:34 jm8241982-desktop kernel: [38662.282395] ata3.00: configured for UDMA/33
Aug 19 16:44:34 jm8241982-desktop kernel: [38662.282431] ata3: EH complete
Aug 19 17:57:40 jm8241982-desktop kernel: [43034.223062] xine_extractor[19509]: segfault at 0d104730 eip b76abc27 esp b5300b70 error 4
Aug 19 18:43:50 jm8241982-desktop kernel: [45795.917069] /usr/bin/soundc[17105]: segfault at 00000004 eip 080e89d5 esp bf931950 error 4
Aug 19 18:43:55 jm8241982-desktop kernel: [45801.264957] nautilus[15442]: segfault at 00000004 eip b6019a56 esp bfaed8c0 error 4
Aug 19 18:43:58 jm8241982-desktop kernel: [45804.388820] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 20:48:51 jm8241982-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 19 20:48:51 jm8241982-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 19 20:48:51 jm8241982-desktop kernel: Symbols match kernel version 2.6.24.
Aug 19 20:48:51 jm8241982-desktop kernel: Loaded 31287 symbols from 83 modules.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] 896MB LOWMEM available.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] found SMP MP-table at 000f37a0
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Zone PFN ranges:
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   DMA             0 ->     4096
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   HighMem    229376 ->   524016
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]     0:        0 ->   524016
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] DMI 2.3 present.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 P4M80P)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: RSDT 7FEF3040, 002C (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: DSDT 7FEF3180, 4EA6 (r1 P4M80P AWRDACPI     1000 MSFT  100000E)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: FACS 7FEF0000, 0040
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: APIC 7FEF8080, 0084 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Processor #0 15:3 APIC version 20
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Processor #1 15:3 APIC version 20
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:7ed00000)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519923
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Kernel command line: root=UUID=0b1db72d-695f-4efc-b9c3-7ac6d48a3ea2 ro quiet splash
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Initializing CPU#0
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Detected 3200.516 MHz processor.
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.436278] Console: colour VGA+ 80x25
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.436283] console [tty0] enabled
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.437019] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.437652] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548129] Memory: 2066072k/2096064k available (2177k kernel code, 28688k reserved, 1006k data, 368k init, 1178560k highmem)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548139] virtual kernel memory layout:
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548140]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548141]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548142]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548143]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548143]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548144]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548145]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548148] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.548207] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.627997] Calibrating delay using timer specific routine.. 6408.32 BogoMIPS (lpj=12816646)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628031] Security Framework initialized
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628040] SELinux:  Disabled at boot.
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628058] AppArmor: AppArmor initialized
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628063] Failure registering capabilities with primary security module.
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628072] Mount-cache hash table entries: 512
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628226] Initializing cgroup subsys ns
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628232] Initializing cgroup subsys cpuacct
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628246] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628255] monitor/mwait feature present.
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628257] using mwait in idle threads.
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628263] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628265] CPU: L2 cache: 1024K
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628268] CPU: Physical Processor ID: 0
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628270] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628282] Compat vDSO mapped to ffffe000.
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628301] Checking 'hlt' instruction... OK.
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.644373] SMP alternatives: switching to UP code
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.646154] Early unpacking initramfs... done
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.921711] ACPI: Core revision 20070126
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.921774] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.925989] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.926010] SMP alternatives: switching to SMP code
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.926807] Booting processor 1/1 eip 3000
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.936992] Initializing CPU#1
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.014817] Calibrating delay using timer specific routine.. 6400.76 BogoMIPS (lpj=12801521)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.014829] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.014836] monitor/mwait feature present.
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.014842] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.014845] CPU: L2 cache: 1024K
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.014847] CPU: Physical Processor ID: 0
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.014849] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.015217] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.015261] Total of 2 processors activated (12809.08 BogoMIPS).
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.016017] ENABLING IO-APIC IRQs
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.016339] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.162516] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182472] Brought up 2 CPUs
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182534] CPU0 attaching sched-domain:
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182538]  domain 0: span 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182540]   groups: 01 02
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182543]   domain 1: span 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182545]    groups: 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182548] CPU1 attaching sched-domain:
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182549]  domain 0: span 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182551]   groups: 02 01
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182554]   domain 1: span 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182556]    groups: 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182821] net_namespace: 64 bytes
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182833] Booting paravirtualized kernel on bare hardware
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.183378] Time:  2:48:20  Date: 08/20/08
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.183404] NET: Registered protocol family 16
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.183658] EISA bus registered
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.183664] ACPI: bus type pci registered
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.191705] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.191707] PCI: Using configuration type 1
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.191732] Setting up standard PCI resources
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.199442] ACPI: EC: Look up EC in DSDT
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.205199] ACPI: Interpreter enabled
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.205205] ACPI: (supports S0 S1 S4 S5)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.205223] ACPI: Using IOAPIC for interrupt routing
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.211207] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.212476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.253040] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.253206] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.253373] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.253523] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.253667] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.253806] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.253945] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.254084] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.254269] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.254427] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.254584] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.254763] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.254890] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.254931] pnp: PnP ACPI init
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.254939] ACPI: bus type pnp registered
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.257922] pnp: PnP ACPI: found 9 devices
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.257925] ACPI: ACPI bus type pnp unregistered
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.257930] PnPBIOS: Disabled by ACPI PNP
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.258240] PCI: Using ACPI for IRQ routing
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.258243] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.298122] NET: Registered protocol family 8
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.298124] NET: Registered protocol family 20
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.298200] AppArmor: AppArmor Filesystem Enabled
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.301960] Time: tsc clocksource has been installed.
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318097] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318100] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318103] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318106] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318108] system 00:00: iomem range 0x7fef0000-0x7fefffff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318111] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318114] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318116] system 00:00: iomem range 0x100000-0x7feeffff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318119] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318122] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318125] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318131] system 00:02: ioport range 0x400-0x47f has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318134] system 00:02: ioport range 0x500-0x50f has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318140] system 00:03: ioport range 0xb78-0xb7b has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318143] system 00:03: ioport range 0xf78-0xf7b has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318145] system 00:03: ioport range 0xa78-0xa7b has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318148] system 00:03: ioport range 0xe78-0xe7b has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318150] system 00:03: ioport range 0xbbc-0xbbf has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318152] system 00:03: ioport range 0xfbc-0xfbf has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318155] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318157] system 00:03: ioport range 0x800-0x87f has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318160] system 00:03: ioport range 0x880-0x8ff has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.318162] system 00:03: ioport range 0x290-0x297 has been reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.348593] PCI: Bridge: 0000:00:01.0
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.348597]   IO window: b000-bfff
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.348602]   MEM window: fb000000-fcffffff
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.348606]   PREFETCH window: e8000000-efffffff
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.348626] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.348637] NET: Registered protocol family 2
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.385918] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.386278] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.386984] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.387654] TCP: Hash tables configured (established 131072 bind 65536)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.387657] TCP reno registered
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.398001] checking if image is initramfs... it is
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.848308] Switched to high resolution mode on CPU 0
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.848436] Switched to high resolution mode on CPU 1
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.947257] Freeing initrd memory: 7305k freed
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.948167] audit: initializing netlink socket (disabled)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.948182] audit(1219200500.284:1): initialized
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.948434] highmem bounce pool size: 64 pages
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.950746] VFS: Disk quotas dquot_6.5.1
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.950839] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.950984] io scheduler noop registered
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.950987] io scheduler anticipatory registered
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.950989] io scheduler deadline registered
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.951000] io scheduler cfq registered (default)
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.951014] PCI: VIA PCI bridge detected. Disabling DAC.
Aug 19 20:48:51 jm8241982-desktop kernel: [   24.923829] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Aug 19 20:48:51 jm8241982-desktop kernel: [   24.923855] PCI: Bypassing VIA 8237 APIC De-Assert Message
Aug 19 20:48:51 jm8241982-desktop kernel: [   24.923878] Boot video device is 0000:01:00.0
Aug 19 20:48:51 jm8241982-desktop kernel: [   24.924263] isapnp: Scanning for PnP cards...
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.275310] isapnp: No Plug & Play device found
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.310131] Real Time Clock Driver v1.12ac
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.310251] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.311854] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.311932] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.312049] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.312052] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.312206] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.343653] mice: PS/2 mouse device common for all mice
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.343814] EISA: Probing bus 0 at eisa.0
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.343856] EISA: Detected 0 cards.
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.343860] cpuidle: using governor ladder
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.343861] cpuidle: using governor menu
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.343950] NET: Registered protocol family 1
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.343979] Using IPI No-Shortcut mode
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.344009] registered taskstats version 1
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.344103]   Magic number: 4:511:814
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.344195]   hash matches device ptys8
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.344205]   hash matches device ptypb
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.344238] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.344239] EDD information not available.
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.344588] Freeing unused kernel memory: 368k freed
Aug 19 20:48:51 jm8241982-desktop kernel: [   25.367990] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 19 20:48:51 jm8241982-desktop kernel: [   26.582882] fuse init (API version 7.9)
Aug 19 20:48:51 jm8241982-desktop kernel: [   26.605335] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 19 20:48:51 jm8241982-desktop kernel: [   26.605350] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 19 20:48:51 jm8241982-desktop kernel: [   26.908857] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 20:48:51 jm8241982-desktop kernel: [   26.908870] 3c59x: Donald Becker and others.
Aug 19 20:48:51 jm8241982-desktop kernel: [   26.908879] 0000:00:05.0: 3Com PCI 3c905B Cyclone 100baseTx at f883e000.
Aug 19 20:48:51 jm8241982-desktop kernel: [   26.908891] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.192450] usbcore: registered new interface driver usbfs
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.192485] usbcore: registered new interface driver hub
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.210736] usbcore: registered new device driver usb
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.211014] SCSI subsystem initialized
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.223094] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.223104] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.223506] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.223515] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 17
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.223526] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.223930] eth1: VIA Rhine II at 0xfdffd000, 00:19:db:25:49:e1, IRQ 17.
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.225283] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.225442] libata version 3.00 loaded.
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.226307] USB Universal Host Controller Interface driver v3.0
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.226742] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.226751] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.226767] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.226772] uhci_hcd 0000:00:10.0: UHCI Host Controller
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.227061] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.227100] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000dc00
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.227297] usb usb1: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.227358] hub 1-0:1.0: USB hub found
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.227373] hub 1-0:1.0: 2 ports detected
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.329740] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.329764] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.329771] uhci_hcd 0000:00:10.1: UHCI Host Controller
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.329815] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.329848] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000d800
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.330039] usb usb2: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.330077] hub 2-0:1.0: USB hub found
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.330087] hub 2-0:1.0: 2 ports detected
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.433476] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.433499] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.433505] uhci_hcd 0000:00:10.2: UHCI Host Controller
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.433547] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.433575] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d400
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.433748] usb usb3: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.433792] hub 3-0:1.0: USB hub found
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.433802] hub 3-0:1.0: 2 ports detected
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.537119] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.537143] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.537149] uhci_hcd 0000:00:10.3: UHCI Host Controller
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.537189] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.537216] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000d000
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.537395] usb usb4: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.537433] hub 4-0:1.0: USB hub found
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.537443] hub 4-0:1.0: 2 ports detected
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.568882] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.640840] pata_via 0000:00:0f.1: version 0.3.3
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.641200] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.641212] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.641277] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.642001] scsi0 : pata_via
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.642957] scsi1 : pata_via
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.645210] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.645216] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.746559] usb 1-1: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.978944] ata1.00: ATAPI: Optiarc DVD RW AD-7191A, 1.04, max UDMA/66
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.987550] usb 1-2: new full speed USB device using uhci_hcd and address 3
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.148266] usb 1-2: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.152164] hub 1-2:1.0: USB hub found
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.154120] hub 1-2:1.0: 4 ports detected
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.166259] ata1.00: configured for UDMA/66
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.332862] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7191A  1.04 PQ: 0 ANSI: 5
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333303] sata_via 0000:00:0f.0: version 2.3
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333335] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 19
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333386] sata_via 0000:00:0f.0: routed to hard irq line 11
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333398] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333458] scsi2 : sata_via
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333702] scsi3 : sata_via
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333753] ata3: SATA max UDMA/133 cmd 0xf800 ctl 0xf400 bmdma 0xe800 irq 19
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333757] ata4: SATA max UDMA/133 cmd 0xf000 ctl 0xec00 bmdma 0xe808 irq 19
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.536882] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.628607] usb 2-2: new low speed USB device using uhci_hcd and address 2
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.748242] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.810190] usb 2-2: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.911954] ata4.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.911959] ata4.00: 490234752 sectors, multi 1: LBA48 NCQ (depth 0/1)
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.927913] ata4.00: configured for UDMA/133
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.928063] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.928573] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.928591] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.928596] ehci_hcd 0000:00:10.4: EHCI Host Controller
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.928638] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.928684] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfdffe000
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.940681] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.940837] usb usb5: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.940876] hub 5-0:1.0: USB hub found
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.940886] hub 5-0:1.0: 8 ports detected
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.064255] Driver 'sd' needs updating - please use bus_type methods
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.066947] sd 3:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.066969] sd 3:0:0:0: [sda] Write Protect is off
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.066973] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.067003] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.067083] sd 3:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.067100] sd 3:0:0:0: [sda] Write Protect is off
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.067104] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.067132] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.067138]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.071363]  sda1 sda2 <sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.075963] Uniform CD-ROM driver Revision: 3.20
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.076029] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.089791]  sda5 >
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.089916] sd 3:0:0:0: [sda] Attached SCSI disk
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.099586] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.099626] sd 3:0:0:0: Attached scsi generic sg1 type 0
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.324300] hub 1-2:1.0: hub_port_status failed (err = -71)
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.325287] hub 1-2:1.0: hub_port_status failed (err = -71)
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.326283] hub 1-2:1.0: hub_port_status failed (err = -71)
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.327280] hub 1-2:1.0: hub_port_status failed (err = -71)
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.327300] usb 2-2: USB disconnect, address 2
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.932653] usb 5-2: new high speed USB device using ehci_hcd and address 3
Aug 19 20:48:51 jm8241982-desktop kernel: [   30.065666] usb 5-2: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   30.065955] hub 5-2:1.0: USB hub found
Aug 19 20:48:51 jm8241982-desktop kernel: [   30.066276] hub 5-2:1.0: 4 ports detected
Aug 19 20:48:51 jm8241982-desktop kernel: [   30.351408] hub 5-0:1.0: over-current change on port 5
Aug 19 20:48:51 jm8241982-desktop kernel: [   30.455069] hub 5-0:1.0: over-current change on port 6
Aug 19 20:48:51 jm8241982-desktop kernel: [   30.558752] hub 5-0:1.0: over-current change on port 7
Aug 19 20:48:51 jm8241982-desktop kernel: [   30.662451] hub 5-0:1.0: over-current change on port 8
Aug 19 20:48:51 jm8241982-desktop kernel: [   30.766142] usb 1-1: USB disconnect, address 2
Aug 19 20:48:51 jm8241982-desktop kernel: [   30.766181] usbcore: registered new interface driver hiddev
Aug 19 20:48:51 jm8241982-desktop kernel: [   31.005408] usb 1-1: new full speed USB device using uhci_hcd and address 4
Aug 19 20:48:51 jm8241982-desktop kernel: [   31.189337] usb 1-1: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   31.192341] usb 1-2: USB disconnect, address 3
Aug 19 20:48:51 jm8241982-desktop kernel: [   31.520098] usb 5-2.1: new high speed USB device using ehci_hcd and address 5
Aug 19 20:48:51 jm8241982-desktop kernel: [   31.613445] usb 5-2.1: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   31.615093] usbcore: registered new interface driver usbhid
Aug 19 20:48:51 jm8241982-desktop kernel: [   31.615100] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 19 20:48:51 jm8241982-desktop kernel: [   31.850839] usb 2-2: new low speed USB device using uhci_hcd and address 3
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.032669] usb 2-2: configuration #1 chosen from 1 choice
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.050742] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input2
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.067256] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.067740] usbcore: registered new interface driver libusual
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.074619] Initializing USB Mass Storage driver...
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.074729] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.074836] usbcore: registered new interface driver usb-storage
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.074843] USB Mass Storage support registered.
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.075028] usb-storage: device found at 5
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.075032] usb-storage: waiting for device to settle before scanning
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.118464] Attempting manual resume
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.118469] swsusp: Resume From Partition 8:5
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.118471] PM: Checking swsusp image.
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.118646] PM: Resume from disk failed.
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.148807] kjournald starting.  Commit interval 5 seconds
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.148815] EXT3-fs: mounted filesystem with ordered data mode.
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.060288] usb-storage: device scan complete
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.061045] scsi 4:0:0:0: Direct-Access     ST310003 40NS                  PQ: 0 ANSI: 2 CCS
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.062747] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.063491] sd 4:0:0:0: [sdb] Write Protect is off
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.063498] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.063501] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.064612] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.065355] sd 4:0:0:0: [sdb] Write Protect is off
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.065359] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.065363] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.065370]  sdb: sdb1
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.070949] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.070996] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 19 20:48:51 jm8241982-desktop kernel: [   38.168902] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Aug 19 20:48:51 jm8241982-desktop kernel: [   38.168913] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.113898] Linux agpgart interface v0.102
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.201789] agpgart: Detected VIA VT3314 chipset
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.208830] agpgart: AGP aperture is 128M @ 0xf0000000
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.342947] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.396181] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.505088] input: Power Button (FF) as /devices/virtual/input/input3
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.532567] ACPI: Power Button (FF) [PWRF]
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.532718] input: Power Button (CM) as /devices/virtual/input/input4
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.544588] ACPI: Power Button (CM) [PWRB]
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.544739] input: Sleep Button (CM) as /devices/virtual/input/input5
Aug 19 20:48:51 jm8241982-desktop kernel: [   39.560489] ACPI: Sleep Button (CM) [SLPB]
Aug 19 20:48:51 jm8241982-desktop kernel: [   40.052445] input: PC Speaker as /devices/platform/pcspkr/input/input6
Aug 19 20:48:51 jm8241982-desktop kernel: [   41.078643] nvidia: module license 'NVIDIA' taints kernel.
Aug 19 20:48:51 jm8241982-desktop kernel: [   41.527512] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
Aug 19 20:48:51 jm8241982-desktop kernel: [   41.527540] usbcore: registered new interface driver usblp

Aug 19 20:48:51 jm8241982-desktop kernel: [   42.107635] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 20:48:51 jm8241982-desktop kernel: [   42.107651] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   42.107944] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Aug 19 20:48:51 jm8241982-desktop kernel: [   42.281253] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Aug 19 20:48:51 jm8241982-desktop kernel: [   42.281263] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
Aug 19 20:48:51 jm8241982-desktop kernel: [   42.281410] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   43.957596] lp: driver loaded but no devices found
Aug 19 20:48:51 jm8241982-desktop kernel: [   44.120573] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
Aug 19 20:48:51 jm8241982-desktop kernel: [   44.675043] EXT3 FS on sda1, internal journal
Aug 19 20:48:51 jm8241982-desktop kernel: [   45.910363] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 20:48:51 jm8241982-desktop kernel: [   46.389421] No dock devices found.
Aug 19 20:48:51 jm8241982-desktop kernel: [   47.514089] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 19 20:48:51 jm8241982-desktop kernel: [   47.514097] apm: disabled - APM is not SMP safe.
Aug 19 20:48:51 jm8241982-desktop kernel: [   47.661396] ppdev: user-space parallel port driver
Aug 19 20:48:51 jm8241982-desktop kernel: [   47.809870] audit(1219200531.981:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4990 profile="/usr/sbin/cupsd" namespace="default"
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.474957] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.495250] eth0:  setting half-duplex.
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.610527] Bluetooth: Core ver 2.11
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.612172] NET: Registered protocol family 31
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.612179] Bluetooth: HCI device and connection manager initialized
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.612186] Bluetooth: HCI socket layer initialized
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.667782] Bluetooth: L2CAP ver 2.9
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.667790] Bluetooth: L2CAP socket layer initialized
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.708031] Bluetooth: RFCOMM socket layer initialized
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.708049] Bluetooth: RFCOMM TTY layer initialized
Aug 19 20:48:53 jm8241982-desktop kernel: [   49.708052] Bluetooth: RFCOMM ver 1.8
Aug 19 20:48:56 jm8241982-desktop kernel: [   52.386244] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 19 20:48:56 jm8241982-desktop kernel: [   52.386266] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 19 20:48:56 jm8241982-desktop kernel: [   52.386348] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 19 20:48:57 jm8241982-desktop kernel: [   53.211759] NET: Registered protocol family 17
Aug 19 20:49:00 jm8241982-desktop kernel: [   56.753905] NET: Registered protocol family 10
Aug 19 20:49:00 jm8241982-desktop kernel: [   56.754296] lo: Disabled Privacy Extensions
Aug 19 20:49:00 jm8241982-desktop kernel: [   56.754911] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 19 20:49:15 jm8241982-desktop kernel: [   66.800921] eth1: no IPv6 routers present
Aug 19 20:52:22 jm8241982-desktop kernel: [  252.926179] usb 5-2.1: reset high speed USB device using ehci_hcd and address 5
Aug 19 20:52:32 jm8241982-desktop kernel: [  263.059429] usb 5-2.1: reset high speed USB device using ehci_hcd and address 5
Aug 19 20:52:43 jm8241982-desktop kernel: [  274.070739] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 19 20:52:43 jm8241982-desktop kernel: [  274.070763] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 19 20:52:43 jm8241982-desktop kernel: [  274.070851] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 19 20:53:08 jm8241982-desktop kernel: [  299.114224] usb 5-2.1: reset high speed USB device using ehci_hcd and address 5
Aug 19 20:53:08 jm8241982-desktop kernel: [  299.185988] usb 5-2.1: device descriptor read/64, error -71
Aug 19 20:53:08 jm8241982-desktop kernel: [  299.361442] usb 5-2.1: device descriptor read/64, error -71
Aug 19 20:53:09 jm8241982-desktop kernel: [  299.536894] usb 5-2.1: reset high speed USB device using ehci_hcd and address 5
Aug 19 20:53:09 jm8241982-desktop kernel: [  299.608672] usb 5-2.1: device descriptor read/64, error -71
Aug 19 20:53:09 jm8241982-desktop kernel: [  299.783125] usb 5-2.1: device descriptor read/64, error -71
Aug 19 20:53:09 jm8241982-desktop kernel: [  299.959565] usb 5-2.1: reset high speed USB device using ehci_hcd and address 5
Aug 19 20:53:09 jm8241982-desktop kernel: [  300.365118] usb 5-2.1: device not accepting address 5, error -71
Aug 19 20:53:09 jm8241982-desktop kernel: [  300.437199] usb 5-2.1: reset high speed USB device using ehci_hcd and address 5
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.844662] usb 5-2.1: device not accepting address 5, error -71
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845190] sd 4:0:0:0: Device offlined - not ready after error recovery
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845202] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845216] end_request: I/O error, dev sdb, sector 231
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845223] Buffer I/O error on device sdb1, logical block 21
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845268] sd 4:0:0:0: rejecting I/O to offline device
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845274] Buffer I/O error on device sdb1, logical block 21
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845769] sd 4:0:0:0: rejecting I/O to offline device
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845776] Buffer I/O error on device sdb1, logical block 184
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845790] sd 4:0:0:0: rejecting I/O to offline device
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.845796] Buffer I/O error on device sdb1, logical block 184
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.847174] usb 5-2.1: USB disconnect, address 5
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.854884] Buffer I/O error on device sdb1, logical block 5
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.854907] Buffer I/O error on device sdb1, logical block 5
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.855050] Buffer I/O error on device sdb1, logical block 5
Aug 19 20:53:10 jm8241982-desktop kernel: [  300.927958] usb 5-2.1: new high speed USB device using ehci_hcd and address 6
Aug 19 20:53:10 jm8241982-desktop kernel: [  301.003431] usb 5-2.1: device descriptor read/64, error -71
Aug 19 20:53:10 jm8241982-desktop kernel: [  301.183000] usb 5-2.1: device descriptor read/64, error -71
Aug 19 20:53:10 jm8241982-desktop kernel: [  301.358550] usb 5-2.1: new high speed USB device using ehci_hcd and address 7
Aug 19 20:53:10 jm8241982-desktop kernel: [  301.434202] usb 5-2.1: device descriptor read/64, error -71
Aug 19 20:53:11 jm8241982-desktop kernel: [  301.618532] usb 5-2.1: device descriptor read/64, error -71
Aug 19 20:53:11 jm8241982-desktop kernel: [  301.806174] usb 5-2.1: new high speed USB device using ehci_hcd and address 8
Aug 19 20:53:11 jm8241982-desktop kernel: [  302.212524] usb 5-2.1: device not accepting address 8, error -71
Aug 19 20:53:11 jm8241982-desktop kernel: [  302.284534] usb 5-2.1: new high speed USB device using ehci_hcd and address 9
Aug 19 20:53:12 jm8241982-desktop kernel: [  302.690079] usb 5-2.1: device not accepting address 9, error -71
Aug 19 20:53:35 jm8241982-desktop kernel: [  325.970443] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 20:54:55 jm8241982-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 19 20:54:55 jm8241982-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 19 20:54:55 jm8241982-desktop kernel: Symbols match kernel version 2.6.24.
Aug 19 20:54:55 jm8241982-desktop kernel: Loaded 31287 symbols from 83 modules.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] 896MB LOWMEM available.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] found SMP MP-table at 000f37a0
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Zone PFN ranges:
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   DMA             0 ->     4096
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   HighMem    229376 ->   524016
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]     0:        0 ->   524016
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] DMI 2.3 present.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 P4M80P)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: RSDT 7FEF3040, 002C (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: DSDT 7FEF3180, 4EA6 (r1 P4M80P AWRDACPI     1000 MSFT  100000E)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: FACS 7FEF0000, 0040
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: APIC 7FEF8080, 0084 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Processor #0 15:3 APIC version 20
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Processor #1 15:3 APIC version 20
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:7ed00000)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519923
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Kernel command line: root=UUID=0b1db72d-695f-4efc-b9c3-7ac6d48a3ea2 ro quiet splash
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Initializing CPU#0
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Detected 3200.148 MHz processor.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.218983] Console: colour VGA+ 80x25
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.218987] console [tty0] enabled
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.219721] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.220339] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331612] Memory: 2066072k/2096064k available (2177k kernel code, 28688k reserved, 1006k data, 368k init, 1178560k highmem)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331622] virtual kernel memory layout:
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331623]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331624]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331625]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331626]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331627]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331628]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331628]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331631] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.331690] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411480] Calibrating delay using timer specific routine.. 6408.35 BogoMIPS (lpj=12816715)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411514] Security Framework initialized
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411523] SELinux:  Disabled at boot.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411542] AppArmor: AppArmor initialized
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411546] Failure registering capabilities with primary security module.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411556] Mount-cache hash table entries: 512
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411710] Initializing cgroup subsys ns
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411715] Initializing cgroup subsys cpuacct
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411730] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411739] monitor/mwait feature present.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411740] using mwait in idle threads.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411747] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411749] CPU: L2 cache: 1024K
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411752] CPU: Physical Processor ID: 0
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411754] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411766] Compat vDSO mapped to ffffe000.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411786] Checking 'hlt' instruction... OK.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.427898] SMP alternatives: switching to UP code
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.429784] Early unpacking initramfs... done
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.707179] ACPI: Core revision 20070126
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.707240] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.711458] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.711479] SMP alternatives: switching to SMP code
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.712280] Booting processor 1/1 eip 3000
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.722464] Initializing CPU#1
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802288] Calibrating delay using timer specific routine.. 6400.67 BogoMIPS (lpj=12801344)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802299] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802306] monitor/mwait feature present.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802313] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802315] CPU: L2 cache: 1024K
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802318] CPU: Physical Processor ID: 0
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802320] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802688] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802732] Total of 2 processors activated (12809.02 BogoMIPS).
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.803489] ENABLING IO-APIC IRQs
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.803811] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.949988] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.969942] Brought up 2 CPUs
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970005] CPU0 attaching sched-domain:
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970008]  domain 0: span 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970010]   groups: 01 02
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970014]   domain 1: span 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970015]    groups: 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970018] CPU1 attaching sched-domain:
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970019]  domain 0: span 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970021]   groups: 02 01
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970024]   domain 1: span 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970026]    groups: 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970288] net_namespace: 64 bytes
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970300] Booting paravirtualized kernel on bare hardware
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970845] Time:  2:54:27  Date: 08/20/08
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970872] NET: Registered protocol family 16
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.971125] EISA bus registered
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.971131] ACPI: bus type pci registered
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.979175] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.979178] PCI: Using configuration type 1
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.979203] Setting up standard PCI resources
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.986123] ACPI: EC: Look up EC in DSDT
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.991918] ACPI: Interpreter enabled
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.991924] ACPI: (supports S0 S1 S4 S5)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.991943] ACPI: Using IOAPIC for interrupt routing
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.997927] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.999190] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.039773] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.039939] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.040104] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.040252] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.040396] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.040534] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.040674] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.040814] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.040985] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.041139] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.041293] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.041471] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.041606] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.041645] pnp: PnP ACPI init
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.041653] ACPI: bus type pnp registered
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.044643] pnp: PnP ACPI: found 9 devices
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.044646] ACPI: ACPI bus type pnp unregistered
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.044651] PnPBIOS: Disabled by ACPI PNP
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.044942] PCI: Using ACPI for IRQ routing
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.044946] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.069641] NET: Registered protocol family 8
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.069643] NET: Registered protocol family 20
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.069719] AppArmor: AppArmor Filesystem Enabled
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.073480] Time: tsc clocksource has been installed.
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085628] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085631] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085634] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085636] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085639] system 00:00: iomem range 0x7fef0000-0x7fefffff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085642] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085645] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085647] system 00:00: iomem range 0x100000-0x7feeffff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085650] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085652] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085655] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085662] system 00:02: ioport range 0x400-0x47f has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085665] system 00:02: ioport range 0x500-0x50f has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085670] system 00:03: ioport range 0xb78-0xb7b has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085673] system 00:03: ioport range 0xf78-0xf7b has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085675] system 00:03: ioport range 0xa78-0xa7b has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085677] system 00:03: ioport range 0xe78-0xe7b has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085680] system 00:03: ioport range 0xbbc-0xbbf has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085682] system 00:03: ioport range 0xfbc-0xfbf has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085684] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085687] system 00:03: ioport range 0x800-0x87f has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085689] system 00:03: ioport range 0x880-0x8ff has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.085691] system 00:03: ioport range 0x290-0x297 has been reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.116122] PCI: Bridge: 0000:00:01.0
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.116126]   IO window: b000-bfff
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.116132]   MEM window: fb000000-fcffffff
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.116136]   PREFETCH window: e8000000-efffffff
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.116156] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.116168] NET: Registered protocol family 2
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.153463] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.153813] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.154517] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.155182] TCP: Hash tables configured (established 131072 bind 65536)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.155185] TCP reno registered
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.165552] checking if image is initramfs... it is
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.615837] Switched to high resolution mode on CPU 0
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.615966] Switched to high resolution mode on CPU 1
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.715162] Freeing initrd memory: 7305k freed
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.716126] audit: initializing netlink socket (disabled)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.716144] audit(1219200867.268:1): initialized
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.716401] highmem bounce pool size: 64 pages
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.718720] VFS: Disk quotas dquot_6.5.1
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.718812] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.718961] io scheduler noop registered
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.718964] io scheduler anticipatory registered
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.718966] io scheduler deadline registered
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.718977] io scheduler cfq registered (default)
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.718991] PCI: VIA PCI bridge detected. Disabling DAC.
Aug 19 20:54:55 jm8241982-desktop kernel: [   24.690377] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Aug 19 20:54:55 jm8241982-desktop kernel: [   24.690404] PCI: Bypassing VIA 8237 APIC De-Assert Message
Aug 19 20:54:55 jm8241982-desktop kernel: [   24.690427] Boot video device is 0000:01:00.0
Aug 19 20:54:55 jm8241982-desktop kernel: [   24.690811] isapnp: Scanning for PnP cards...
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.041993] isapnp: No Plug & Play device found
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.076566] Real Time Clock Driver v1.12ac
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.076681] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.078245] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.078323] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.078438] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.078441] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.078595] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101181] mice: PS/2 mouse device common for all mice
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101337] EISA: Probing bus 0 at eisa.0
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101379] EISA: Detected 0 cards.
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101382] cpuidle: using governor ladder
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101384] cpuidle: using governor menu
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101470] NET: Registered protocol family 1
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101500] Using IPI No-Shortcut mode
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101531] registered taskstats version 1
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101626]   Magic number: 4:614:915
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101708]   hash matches device ptywe
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101763] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.101764] EDD information not available.
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.102120] Freeing unused kernel memory: 368k freed
Aug 19 20:54:55 jm8241982-desktop kernel: [   25.123895] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.340373] fuse init (API version 7.9)
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.362337] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.362352] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.869109] SCSI subsystem initialized
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.943389] usbcore: registered new interface driver usbfs
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.943423] usbcore: registered new interface driver hub
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.958552] libata version 3.00 loaded.
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.959506] usbcore: registered new device driver usb
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.961225] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.961240] 3c59x: Donald Becker and others.
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.961249] 0000:00:05.0: 3Com PCI 3c905B Cyclone 100baseTx at f8842000.
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.961259] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.987972] pata_via 0000:00:0f.1: version 0.3.3
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.988362] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.988372] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.988438] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.991441] scsi0 : pata_via
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.992332] USB Universal Host Controller Interface driver v3.0
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.995265] scsi1 : pata_via
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.997220] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.997226] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.998087] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.998097] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.330513] ata1.00: ATAPI: Optiarc DVD RW AD-7191A, 1.04, max UDMA/66
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.517808] ata1.00: configured for UDMA/66
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.684422] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7191A  1.04 PQ: 0 ANSI: 5
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685197] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685206] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685222] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685228] uhci_hcd 0000:00:10.0: UHCI Host Controller
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685519] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685558] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000dc00
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685753] usb usb1: configuration #1 chosen from 1 choice
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685793] hub 1-0:1.0: USB hub found
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685801] hub 1-0:1.0: 2 ports detected
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.788812] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.788831] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.788837] uhci_hcd 0000:00:10.1: UHCI Host Controller
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.788879] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.788911] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000d800
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.789086] usb usb2: configuration #1 chosen from 1 choice
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.789124] hub 2-0:1.0: USB hub found
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.789133] hub 2-0:1.0: 2 ports detected
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.896420] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.896436] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.896442] uhci_hcd 0000:00:10.2: UHCI Host Controller
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.896479] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.896506] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d400
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.896668] usb usb3: configuration #1 chosen from 1 choice
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.896710] hub 3-0:1.0: USB hub found
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.896718] hub 3-0:1.0: 2 ports detected
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.996098] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.996114] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.996120] uhci_hcd 0000:00:10.3: UHCI Host Controller
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.996155] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.996181] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000d000
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.996343] usb usb4: configuration #1 chosen from 1 choice
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.996383] hub 4-0:1.0: USB hub found
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.996391] hub 4-0:1.0: 2 ports detected
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.027884] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.101049] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.101060] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.101072] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.101560] eth1: VIA Rhine II at 0xfdffd000, 00:19:db:25:49:e1, IRQ 19.
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.102271] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.102721] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.102737] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.102743] ehci_hcd 0000:00:10.4: EHCI Host Controller
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.102785] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.102835] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfdffe000
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.151499] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.151670] usb usb5: configuration #1 chosen from 1 choice
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.151713] hub 5-0:1.0: USB hub found
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.151723] hub 5-0:1.0: 8 ports detected
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255318] sata_via 0000:00:0f.0: version 2.3
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255361] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255418] sata_via 0000:00:0f.0: routed to hard irq line 11
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255430] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255721] scsi2 : sata_via
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255797] scsi3 : sata_via
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255845] ata3: SATA max UDMA/133 cmd 0xf800 ctl 0xf400 bmdma 0xe800 irq 17
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255849] ata4: SATA max UDMA/133 cmd 0xf000 ctl 0xec00 bmdma 0xe808 irq 17
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.458557] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.550241] usb 1-1: device not accepting address 2, error -71
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.669867] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.833558] ata4.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.833563] ata4.00: 490234752 sectors, multi 1: LBA48 NCQ (depth 0/1)
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.841538] ata4.00: configured for UDMA/133
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.841686] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.855216] Driver 'sr' needs updating - please use bus_type methods
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.859802] Driver 'sd' needs updating - please use bus_type methods
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.863853] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.863858] Uniform CD-ROM driver Revision: 3.20
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.863919] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864205] sd 3:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864229] sd 3:0:0:0: [sda] Write Protect is off
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864234] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864273] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864355] sd 3:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864372] sd 3:0:0:0: [sda] Write Protect is off
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864376] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864405] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864411]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.869199] sd 3:0:0:0: Attached scsi generic sg1 type 0
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.875398]  sda1 sda2 < sda5 >
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.894040] sd 3:0:0:0: [sda] Attached SCSI disk
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.129033] Attempting manual resume
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.129037] swsusp: Resume From Partition 8:5
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.129039] PM: Checking swsusp image.
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.129214] PM: Resume from disk failed.
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.179819] kjournald starting.  Commit interval 5 seconds
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.179826] EXT3-fs: mounted filesystem with ordered data mode.
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.977765] usb 5-2: new high speed USB device using ehci_hcd and address 3
Aug 19 20:54:55 jm8241982-desktop kernel: [   30.110680] usb 5-2: configuration #1 chosen from 1 choice
Aug 19 20:54:55 jm8241982-desktop kernel: [   30.110962] hub 5-2:1.0: USB hub found
Aug 19 20:54:55 jm8241982-desktop kernel: [   30.111186] hub 5-2:1.0: 4 ports detected
Aug 19 20:54:55 jm8241982-desktop kernel: [   30.400435] hub 5-0:1.0: over-current change on port 5
Aug 19 20:54:55 jm8241982-desktop kernel: [   30.504093] hub 5-0:1.0: over-current change on port 6
Aug 19 20:54:55 jm8241982-desktop kernel: [   30.607778] hub 5-0:1.0: over-current change on port 7
Aug 19 20:54:55 jm8241982-desktop kernel: [   30.711443] hub 5-0:1.0: over-current change on port 8
Aug 19 20:54:55 jm8241982-desktop kernel: [   31.054363] usb 1-1: new full speed USB device using uhci_hcd and address 4
Aug 19 20:54:55 jm8241982-desktop kernel: [   31.238100] usb 1-1: configuration #1 chosen from 1 choice
Aug 19 20:54:55 jm8241982-desktop kernel: [   31.442392] usb 5-2.1: new high speed USB device using ehci_hcd and address 5
Aug 19 20:54:55 jm8241982-desktop kernel: [   31.535703] usb 5-2.1: configuration #1 chosen from 1 choice
Aug 19 20:54:55 jm8241982-desktop kernel: [   31.773099] usb 2-2: new low speed USB device using uhci_hcd and address 2
Aug 19 20:54:55 jm8241982-desktop kernel: [   31.954472] usb 2-2: configuration #1 chosen from 1 choice
Aug 19 20:54:55 jm8241982-desktop kernel: [   35.385102] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 19 20:54:55 jm8241982-desktop kernel: [   35.461715] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 19 20:54:55 jm8241982-desktop kernel: [   35.789675] Linux agpgart interface v0.102
Aug 19 20:54:55 jm8241982-desktop kernel: [   35.903329] agpgart: Detected VIA VT3314 chipset
Aug 19 20:54:55 jm8241982-desktop kernel: [   35.910363] agpgart: AGP aperture is 128M @ 0xf0000000
Aug 19 20:54:55 jm8241982-desktop kernel: [   36.154584] input: Power Button (FF) as /devices/virtual/input/input2
Aug 19 20:54:55 jm8241982-desktop kernel: [   36.174270] ACPI: Power Button (FF) [PWRF]
Aug 19 20:54:55 jm8241982-desktop kernel: [   36.174383] input: Power Button (CM) as /devices/virtual/input/input3
Aug 19 20:54:55 jm8241982-desktop kernel: [   36.198220] ACPI: Power Button (CM) [PWRB]
Aug 19 20:54:55 jm8241982-desktop kernel: [   36.198335] input: Sleep Button (CM) as /devices/virtual/input/input4
Aug 19 20:54:55 jm8241982-desktop kernel: [   36.230099] ACPI: Sleep Button (CM) [SLPB]
Aug 19 20:54:55 jm8241982-desktop kernel: [   36.769587] nvidia: module license 'NVIDIA' taints kernel.
Aug 19 20:54:55 jm8241982-desktop kernel: [   37.591021] usbcore: registered new interface driver hiddev
Aug 19 20:54:55 jm8241982-desktop kernel: [   37.606344] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input5
Aug 19 20:54:55 jm8241982-desktop kernel: [   37.630831] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2
Aug 19 20:54:55 jm8241982-desktop kernel: [   37.630859] usbcore: registered new interface driver usbhid
Aug 19 20:54:55 jm8241982-desktop kernel: [   37.630865] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 19 20:54:55 jm8241982-desktop kernel: [   37.868602] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
Aug 19 20:54:55 jm8241982-desktop kernel: [   37.868631] usbcore: registered new interface driver usblp
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.253276] input: PC Speaker as /devices/platform/pcspkr/input/input6
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.483100] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.483113] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.483391] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.659441] usbcore: registered new interface driver libusual
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.712449] Initializing USB Mass Storage driver...
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.713945] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.714081] usbcore: registered new interface driver usb-storage
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.714087] USB Mass Storage support registered.
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.714093] usb-storage: device found at 5
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.714097] usb-storage: waiting for device to settle before scanning
Aug 19 20:54:55 jm8241982-desktop kernel: [   39.116486] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Aug 19 20:54:55 jm8241982-desktop kernel: [   39.116495] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
Aug 19 20:54:55 jm8241982-desktop kernel: [   39.116640] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   40.747850] lp: driver loaded but no devices found
Aug 19 20:54:55 jm8241982-desktop kernel: [   40.906503] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
Aug 19 20:54:55 jm8241982-desktop kernel: [   41.464559] EXT3 FS on sda1, internal journal
Aug 19 20:54:55 jm8241982-desktop kernel: [   42.675601] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.147156] No dock devices found.
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.699614] usb-storage: device scan complete
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.700403] scsi 4:0:0:0: Direct-Access     ST310003 40NS                  PQ: 0 ANSI: 2 CCS
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.701759] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.714637] sd 4:0:0:0: [sdb] Write Protect is off
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.714646] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.714649] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.715712] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.716455] sd 4:0:0:0: [sdb] Write Protect is off
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.716461] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.716464] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.716472]  sdb: sdb1
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.720964] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.721028] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 19 20:54:55 jm8241982-desktop kernel: [   44.433696] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 19 20:54:55 jm8241982-desktop kernel: [   44.433704] apm: disabled - APM is not SMP safe.
Aug 19 20:54:55 jm8241982-desktop kernel: [   44.610135] ppdev: user-space parallel port driver
Aug 19 20:54:56 jm8241982-desktop kernel: [   44.774460] audit(1219200896.152:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4919 profile="/usr/sbin/cupsd" namespace="default"
Aug 19 20:54:57 jm8241982-desktop kernel: [   46.452613] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 19 20:54:57 jm8241982-desktop kernel: [   46.474080] eth0:  setting half-duplex.
Aug 19 20:54:57 jm8241982-desktop kernel: [   46.583482] Bluetooth: Core ver 2.11
Aug 19 20:54:57 jm8241982-desktop kernel: [   46.583975] NET: Registered protocol family 31
Aug 19 20:54:57 jm8241982-desktop kernel: [   46.583981] Bluetooth: HCI device and connection manager initialized
Aug 19 20:54:57 jm8241982-desktop kernel: [   46.583986] Bluetooth: HCI socket layer initialized
Aug 19 20:54:58 jm8241982-desktop kernel: [   46.638045] Bluetooth: L2CAP ver 2.9
Aug 19 20:54:58 jm8241982-desktop kernel: [   46.638053] Bluetooth: L2CAP socket layer initialized
Aug 19 20:54:58 jm8241982-desktop kernel: [   46.727851] Bluetooth: RFCOMM socket layer initialized
Aug 19 20:54:58 jm8241982-desktop kernel: [   46.727873] Bluetooth: RFCOMM TTY layer initialized
Aug 19 20:54:58 jm8241982-desktop kernel: [   46.727877] Bluetooth: RFCOMM ver 1.8
Aug 19 20:55:00 jm8241982-desktop kernel: [   49.174991] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 19 20:55:00 jm8241982-desktop kernel: [   49.175070] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 19 20:55:00 jm8241982-desktop kernel: [   49.175164] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 19 20:55:01 jm8241982-desktop kernel: [   50.028040] NET: Registered protocol family 17
Aug 19 20:55:05 jm8241982-desktop kernel: [   53.960402] NET: Registered protocol family 10
Aug 19 20:55:05 jm8241982-desktop kernel: [   53.960791] lo: Disabled Privacy Extensions
Aug 19 20:55:05 jm8241982-desktop kernel: [   53.961463] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 19 20:55:16 jm8241982-desktop kernel: [   64.600013] eth1: no IPv6 routers present
Aug 20 13:28:15 jm8241982-desktop kernel: [59457.590231] audit(1219260495.884:3): type=1503 operation="capable" name="dac_override" pid=14150 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:28:15 jm8241982-desktop kernel: [59457.590246] audit(1219260495.884:4): type=1503 operation="capable" name="dac_read_search" pid=14150 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:29:03 jm8241982-desktop kernel: [59505.533758] audit(1219260543.976:5): type=1503 operation="capable" name="dac_override" pid=14204 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:29:03 jm8241982-desktop kernel: [59505.533774] audit(1219260543.976:6): type=1503 operation="capable" name="dac_read_search" pid=14204 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:29:18 jm8241982-desktop kernel: [59519.803310] audit(1219260558.292:7): type=1503 operation="capable" name="dac_override" pid=14212 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:29:18 jm8241982-desktop kernel: [59519.803329] audit(1219260558.292:8): type=1503 operation="capable" name="dac_read_search" pid=14212 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:29:51 jm8241982-desktop kernel: [59552.506547] nautilus[5682]: segfault at 00000004 eip b5feaa56 esp bf8c3010 error 4
Aug 20 13:29:53 jm8241982-desktop kernel: [59554.736596] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 20 13:29:53 jm8241982-desktop kernel: [59554.736615] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 20 13:29:53 jm8241982-desktop kernel: [59554.736696] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 20 13:30:00 jm8241982-desktop kernel: [59561.807404] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 20 13:30:00 jm8241982-desktop kernel: [59561.807424] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 20 13:30:00 jm8241982-desktop kernel: [59561.807504] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 20 13:31:04 jm8241982-desktop kernel: [59625.430378] audit(1219260664.252:9): type=1503 operation="capable" name="dac_override" pid=14569 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:31:04 jm8241982-desktop kernel: [59625.430394] audit(1219260664.252:10): type=1503 operation="capable" name="dac_read_search" pid=14569 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:31:17 jm8241982-desktop kernel: [59638.479585] audit(1219260677.341:11): type=1503 operation="capable" name="dac_override" pid=14576 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:31:17 jm8241982-desktop kernel: [59638.479603] audit(1219260677.341:12): type=1503 operation="capable" name="dac_read_search" pid=14576 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:31:29 jm8241982-desktop kernel: [59650.759487] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 20 13:32:30 jm8241982-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 20 13:32:30 jm8241982-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 20 13:32:30 jm8241982-desktop kernel: Symbols match kernel version 2.6.24.
Aug 20 13:32:30 jm8241982-desktop kernel: Loaded 31287 symbols from 83 modules.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] 896MB LOWMEM available.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] found SMP MP-table at 000f37a0
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Zone PFN ranges:
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   DMA             0 ->     4096
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   HighMem    229376 ->   524016
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]     0:        0 ->   524016
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] DMI 2.3 present.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 P4M80P)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: RSDT 7FEF3040, 002C (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: DSDT 7FEF3180, 4EA6 (r1 P4M80P AWRDACPI     1000 MSFT  100000E)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: FACS 7FEF0000, 0040
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: APIC 7FEF8080, 0084 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Processor #0 15:3 APIC version 20
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Processor #1 15:3 APIC version 20
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:7ed00000)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519923
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Kernel command line: root=UUID=0b1db72d-695f-4efc-b9c3-7ac6d48a3ea2 ro quiet splash
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Initializing CPU#0
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Detected 3200.323 MHz processor.
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.424263] Console: colour VGA+ 80x25
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.424267] console [tty0] enabled
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.425002] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.425629] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.535987] Memory: 2066072k/2096064k available (2177k kernel code, 28688k reserved, 1006k data, 368k init, 1178560k highmem)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.535997] virtual kernel memory layout:
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.535998]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.535999]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.536000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.536001]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.536002]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.536003]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.536004]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.536007] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.536065] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.615856] Calibrating delay using timer specific routine.. 6408.36 BogoMIPS (lpj=12816725)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.615888] Security Framework initialized
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.615897] SELinux:  Disabled at boot.
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.615917] AppArmor: AppArmor initialized
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.615921] Failure registering capabilities with primary security module.
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.615931] Mount-cache hash table entries: 512
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616084] Initializing cgroup subsys ns
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616090] Initializing cgroup subsys cpuacct
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616104] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616113] monitor/mwait feature present.
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616115] using mwait in idle threads.
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616121] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616123] CPU: L2 cache: 1024K
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616126] CPU: Physical Processor ID: 0
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616128] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616139] Compat vDSO mapped to ffffe000.
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616158] Checking 'hlt' instruction... OK.
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.632275] SMP alternatives: switching to UP code
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.634162] Early unpacking initramfs... done
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.910633] ACPI: Core revision 20070126
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.910695] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.914968] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.914989] SMP alternatives: switching to SMP code
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.915793] Booting processor 1/1 eip 3000
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.925981] Initializing CPU#1
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.002677] Calibrating delay using timer specific routine.. 6400.71 BogoMIPS (lpj=12801433)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.002691] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.002698] monitor/mwait feature present.
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.002705] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.002707] CPU: L2 cache: 1024K
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.002710] CPU: Physical Processor ID: 0
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.002712] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.003080] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.003124] Total of 2 processors activated (12809.07 BogoMIPS).
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.003881] ENABLING IO-APIC IRQs
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.004203] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.150374] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170329] Brought up 2 CPUs
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170392] CPU0 attaching sched-domain:
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170395]  domain 0: span 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170397]   groups: 01 02
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170401]   domain 1: span 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170402]    groups: 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170405] CPU1 attaching sched-domain:
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170407]  domain 0: span 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170408]   groups: 02 01
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170411]   domain 1: span 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170413]    groups: 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170678] net_namespace: 64 bytes
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170690] Booting paravirtualized kernel on bare hardware
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.171236] Time: 19:32:02  Date: 08/20/08
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.171262] NET: Registered protocol family 16
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.171516] EISA bus registered
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.171522] ACPI: bus type pci registered
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.180248] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.180252] PCI: Using configuration type 1
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.180278] Setting up standard PCI resources
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.187294] ACPI: EC: Look up EC in DSDT
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.193068] ACPI: Interpreter enabled
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.193075] ACPI: (supports S0 S1 S4 S5)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.193093] ACPI: Using IOAPIC for interrupt routing
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.199086] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.200351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.240896] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.241062] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.241229] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.241379] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.241523] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.241663] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.241801] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.241940] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.242120] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.242277] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.242430] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.242608] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.242737] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.242776] pnp: PnP ACPI init
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.242784] ACPI: bus type pnp registered
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.245769] pnp: PnP ACPI: found 9 devices
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.245772] ACPI: ACPI bus type pnp unregistered
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.245777] PnPBIOS: Disabled by ACPI PNP
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.246080] PCI: Using ACPI for IRQ routing
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.246084] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.269890] NET: Registered protocol family 8
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.269893] NET: Registered protocol family 20
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.269972] AppArmor: AppArmor Filesystem Enabled
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.273868] Time: tsc clocksource has been installed.
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285879] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285882] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285884] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285887] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285890] system 00:00: iomem range 0x7fef0000-0x7fefffff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285892] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285895] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285898] system 00:00: iomem range 0x100000-0x7feeffff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285900] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285903] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285906] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285913] system 00:02: ioport range 0x400-0x47f has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285915] system 00:02: ioport range 0x500-0x50f has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285921] system 00:03: ioport range 0xb78-0xb7b has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285923] system 00:03: ioport range 0xf78-0xf7b has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285926] system 00:03: ioport range 0xa78-0xa7b has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285928] system 00:03: ioport range 0xe78-0xe7b has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285931] system 00:03: ioport range 0xbbc-0xbbf has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285933] system 00:03: ioport range 0xfbc-0xfbf has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285935] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285938] system 00:03: ioport range 0x800-0x87f has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285940] system 00:03: ioport range 0x880-0x8ff has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.285942] system 00:03: ioport range 0x290-0x297 has been reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.316380] PCI: Bridge: 0000:00:01.0
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.316384]   IO window: b000-bfff
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.316389]   MEM window: fb000000-fcffffff
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.316394]   PREFETCH window: e8000000-efffffff
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.316414] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.316425] NET: Registered protocol family 2
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.353715] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.354039] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.354737] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.355417] TCP: Hash tables configured (established 131072 bind 65536)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.355420] TCP reno registered
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.365802] checking if image is initramfs... it is
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.812375] Switched to high resolution mode on CPU 1
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.816216] Switched to high resolution mode on CPU 0
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.914324] Freeing initrd memory: 7305k freed
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.915281] audit: initializing netlink socket (disabled)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.915302] audit(1219260722.260:1): initialized
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.915560] highmem bounce pool size: 64 pages
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.917884] VFS: Disk quotas dquot_6.5.1
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.917977] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.918134] io scheduler noop registered
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.918137] io scheduler anticipatory registered
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.918139] io scheduler deadline registered
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.918150] io scheduler cfq registered (default)
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.918164] PCI: VIA PCI bridge detected. Disabling DAC.
Aug 20 13:32:30 jm8241982-desktop kernel: [   31.891231] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Aug 20 13:32:30 jm8241982-desktop kernel: [   31.891256] PCI: Bypassing VIA 8237 APIC De-Assert Message
Aug 20 13:32:30 jm8241982-desktop kernel: [   31.891279] Boot video device is 0000:01:00.0
Aug 20 13:32:30 jm8241982-desktop kernel: [   31.891665] isapnp: Scanning for PnP cards...
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.242670] isapnp: No Plug & Play device found
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.276620] Real Time Clock Driver v1.12ac
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.276736] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.278718] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.278798] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.278916] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.278919] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.279086] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302070] mice: PS/2 mouse device common for all mice
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302227] EISA: Probing bus 0 at eisa.0
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302269] EISA: Detected 0 cards.
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302273] cpuidle: using governor ladder
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302275] cpuidle: using governor menu
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302362] NET: Registered protocol family 1
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302392] Using IPI No-Shortcut mode
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302421] registered taskstats version 1
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302517]   Magic number: 4:10:547
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302647] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.302649] EDD information not available.
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.303010] Freeing unused kernel memory: 368k freed
Aug 20 13:32:30 jm8241982-desktop kernel: [   32.324764] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 20 13:32:30 jm8241982-desktop kernel: [   33.539931] fuse init (API version 7.9)
Aug 20 13:32:30 jm8241982-desktop kernel: [   33.561672] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 20 13:32:30 jm8241982-desktop kernel: [   33.561687] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 20 13:32:30 jm8241982-desktop kernel: [   33.989146] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 20 13:32:30 jm8241982-desktop kernel: [   33.989163] 3c59x: Donald Becker and others.
Aug 20 13:32:30 jm8241982-desktop kernel: [   33.989171] 0000:00:05.0: 3Com PCI 3c905B Cyclone 100baseTx at f883e000.
Aug 20 13:32:30 jm8241982-desktop kernel: [   33.989184] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.077142] SCSI subsystem initialized
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.124386] libata version 3.00 loaded.
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.150823] usbcore: registered new interface driver usbfs
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.150858] usbcore: registered new interface driver hub
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.164512] pata_via 0000:00:0f.1: version 0.3.3
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.164843] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.164851] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.164903] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.165068] usbcore: registered new device driver usb
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.186087] scsi0 : pata_via
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.188569] scsi1 : pata_via
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.190567] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.190572] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.192484] USB Universal Host Controller Interface driver v3.0
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.251825] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.251836] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.523475] ata1.00: ATAPI: Optiarc DVD RW AD-7191A, 1.04, max UDMA/66
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.710784] ata1.00: configured for UDMA/66
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.877335] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7191A  1.04 PQ: 0 ANSI: 5
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.877461] sata_via 0000:00:0f.0: version 2.3
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.877500] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.877561] sata_via 0000:00:0f.0: routed to hard irq line 11
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.877574] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.877965] scsi2 : sata_via
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.878187] scsi3 : sata_via
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.878237] ata3: SATA max UDMA/133 cmd 0xf800 ctl 0xf400 bmdma 0xe800 irq 17
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.878241] ata4: SATA max UDMA/133 cmd 0xf000 ctl 0xec00 bmdma 0xe808 irq 17
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.081376] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.292721] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.456425] ata4.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.456430] ata4.00: 490234752 sectors, multi 1: LBA48 NCQ (depth 0/1)
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.464403] ata4.00: configured for UDMA/133
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.464549] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465367] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465375] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465391] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465397] uhci_hcd 0000:00:10.0: UHCI Host Controller
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465677] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465717] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000dc00
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465917] usb usb1: configuration #1 chosen from 1 choice
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465946] hub 1-0:1.0: USB hub found
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465953] hub 1-0:1.0: 2 ports detected
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.568012] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.568033] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.568039] uhci_hcd 0000:00:10.1: UHCI Host Controller
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.568077] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.568104] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000d800
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.568267] usb usb2: configuration #1 chosen from 1 choice
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.568305] hub 2-0:1.0: USB hub found
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.568314] hub 2-0:1.0: 2 ports detected
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.671699] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.671718] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.671723] uhci_hcd 0000:00:10.2: UHCI Host Controller
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.671760] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.671789] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d400
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.671945] usb usb3: configuration #1 chosen from 1 choice
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.671983] hub 3-0:1.0: USB hub found
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.671991] hub 3-0:1.0: 2 ports detected
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.775348] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.775363] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.775369] uhci_hcd 0000:00:10.3: UHCI Host Controller
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.775402] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.775428] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000d000
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.775583] usb usb4: configuration #1 chosen from 1 choice
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.775622] hub 4-0:1.0: USB hub found
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.775631] hub 4-0:1.0: 2 ports detected
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.807131] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.879195] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.879211] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.879216] ehci_hcd 0000:00:10.4: EHCI Host Controller
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.879253] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.879308] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfdffe000
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.931752] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.931917] usb usb5: configuration #1 chosen from 1 choice
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.931957] hub 5-0:1.0: USB hub found
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.931967] hub 5-0:1.0: 8 ports detected
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.036044] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.036055] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.036068] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.036545] eth1: VIA Rhine II at 0xfdffd000, 00:19:db:25:49:e1, IRQ 19.
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.037256] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062056] Driver 'sd' needs updating - please use bus_type methods
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062199] sd 3:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062221] sd 3:0:0:0: [sda] Write Protect is off
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062227] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062275] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062395] sd 3:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062410] sd 3:0:0:0: [sda] Write Protect is off
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062414] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062440] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062446]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.069416]  sda1 sda2 <sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.072442] Uniform CD-ROM driver Revision: 3.20
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.072506] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.087872]  sda5 >
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.087991] sd 3:0:0:0: [sda] Attached SCSI disk
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.096616] sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.096650] sd 3:0:0:0: Attached scsi generic sg1 type 0
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.330509] usb 1-1: device not accepting address 2, error -71
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.363338] Attempting manual resume
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.363342] swsusp: Resume From Partition 8:5
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.363344] PM: Checking swsusp image.
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.363510] PM: Resume from disk failed.
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.407056] kjournald starting.  Commit interval 5 seconds
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.407065] EXT3-fs: mounted filesystem with ordered data mode.
Aug 20 13:32:30 jm8241982-desktop kernel: [   37.757105] usb 5-2: new high speed USB device using ehci_hcd and address 3
Aug 20 13:32:30 jm8241982-desktop kernel: [   37.891018] usb 5-2: configuration #1 chosen from 1 choice
Aug 20 13:32:30 jm8241982-desktop kernel: [   37.891296] hub 5-2:1.0: USB hub found
Aug 20 13:32:30 jm8241982-desktop kernel: [   37.891522] hub 5-2:1.0: 4 ports detected
Aug 20 13:32:30 jm8241982-desktop kernel: [   38.175827] hub 5-0:1.0: over-current change on port 5
Aug 20 13:32:30 jm8241982-desktop kernel: [   38.279489] hub 5-0:1.0: over-current change on port 6
Aug 20 13:32:30 jm8241982-desktop kernel: [   38.384161] hub 5-0:1.0: over-current change on port 7
Aug 20 13:32:30 jm8241982-desktop kernel: [   38.487848] hub 5-0:1.0: over-current change on port 8
Aug 20 13:32:30 jm8241982-desktop kernel: [   38.830786] usb 1-1: new full speed USB device using uhci_hcd and address 4
Aug 20 13:32:30 jm8241982-desktop kernel: [   39.011336] usb 1-1: configuration #1 chosen from 1 choice
Aug 20 13:32:30 jm8241982-desktop kernel: [   39.212888] usb 5-2.1: new high speed USB device using ehci_hcd and address 5
Aug 20 13:32:30 jm8241982-desktop kernel: [   39.306193] usb 5-2.1: configuration #1 chosen from 1 choice
Aug 20 13:32:30 jm8241982-desktop kernel: [   39.544578] usb 2-2: new low speed USB device using uhci_hcd and address 2
Aug 20 13:32:30 jm8241982-desktop kernel: [   39.726866] usb 2-2: configuration #1 chosen from 1 choice
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.096730] Linux agpgart interface v0.102
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.189507] agpgart: Detected VIA VT3314 chipset
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.196508] agpgart: AGP aperture is 128M @ 0xf0000000
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.248302] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.304718] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.446422] input: Power Button (FF) as /devices/virtual/input/input2
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.460134] ACPI: Power Button (FF) [PWRF]
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.460270] input: Power Button (CM) as /devices/virtual/input/input3
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.491402] ACPI: Power Button (CM) [PWRB]
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.491557] input: Sleep Button (CM) as /devices/virtual/input/input4
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.523305] ACPI: Sleep Button (CM) [SLPB]
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.754720] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
Aug 20 13:32:30 jm8241982-desktop kernel: [   43.754754] usbcore: registered new interface driver usblp
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.137566] nvidia: module license 'NVIDIA' taints kernel.
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.673574] input: PC Speaker as /devices/platform/pcspkr/input/input5
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.773374] usbcore: registered new interface driver libusual
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.853512] Initializing USB Mass Storage driver...
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.863616] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.863629] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.863920] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.867983] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.868156] usbcore: registered new interface driver usb-storage
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.868163] USB Mass Storage support registered.
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.868185] usbcore: registered new interface driver hiddev
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.868267] usb-storage: device found at 5
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.868270] usb-storage: waiting for device to settle before scanning
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.883080] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input6
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.909134] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.909164] usbcore: registered new interface driver usbhid
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.909171] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 20 13:32:30 jm8241982-desktop kernel: [   46.533092] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Aug 20 13:32:30 jm8241982-desktop kernel: [   46.533105] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
Aug 20 13:32:30 jm8241982-desktop kernel: [   46.533265] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   47.958539] lp: driver loaded but no devices found
Aug 20 13:32:30 jm8241982-desktop kernel: [   48.104508] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
Aug 20 13:32:30 jm8241982-desktop kernel: [   48.659266] EXT3 FS on sda1, internal journal
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.002553] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.467514] No dock devices found.
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.852825] usb-storage: device scan complete
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.853587] scsi 4:0:0:0: Direct-Access     ST310003 40NS                  PQ: 0 ANSI: 2 CCS
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.860804] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.861520] sd 4:0:0:0: [sdb] Write Protect is off
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.861525] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.861528] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.862642] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.863391] sd 4:0:0:0: [sdb] Write Protect is off
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.863395] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.863398] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.863404]  sdb: sdb1
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.887081] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.887146] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 20 13:32:30 jm8241982-desktop kernel: [   51.735556] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 20 13:32:30 jm8241982-desktop kernel: [   51.735563] apm: disabled - APM is not SMP safe.
Aug 20 13:32:31 jm8241982-desktop kernel: [   51.911332] ppdev: user-space parallel port driver
Aug 20 13:32:31 jm8241982-desktop kernel: [   52.103516] audit(1219260751.274:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4920 profile="/usr/sbin/cupsd" namespace="default"
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.073474] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.093737] eth0:  setting half-duplex.
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.134045] Bluetooth: Core ver 2.11
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.134459] NET: Registered protocol family 31
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.134466] Bluetooth: HCI device and connection manager initialized
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.134473] Bluetooth: HCI socket layer initialized
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.151878] Bluetooth: L2CAP ver 2.9
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.151885] Bluetooth: L2CAP socket layer initialized
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.215814] Bluetooth: RFCOMM socket layer initialized
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.215837] Bluetooth: RFCOMM TTY layer initialized
Aug 20 13:32:33 jm8241982-desktop kernel: [   54.215839] Bluetooth: RFCOMM ver 1.8
Aug 20 13:32:35 jm8241982-desktop kernel: [   56.509003] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 20 13:32:35 jm8241982-desktop kernel: [   56.509024] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 20 13:32:35 jm8241982-desktop kernel: [   56.509105] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 20 13:32:36 jm8241982-desktop kernel: [   57.438170] NET: Registered protocol family 17
Aug 20 13:32:38 jm8241982-desktop kernel: [   59.142226] NET: Registered protocol family 10
Aug 20 13:32:38 jm8241982-desktop kernel: [   59.142665] lo: Disabled Privacy Extensions
Aug 20 13:32:38 jm8241982-desktop kernel: [   59.143434] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 20 13:32:47 jm8241982-desktop kernel: [   69.184955] eth1: no IPv6 routers present
Aug 20 13:33:45 jm8241982-desktop kernel: [  126.919230] usblp0: removed
Aug 20 13:33:45 jm8241982-desktop kernel: [  127.221122] audit(1219260825.711:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=5837 profile="/usr/sbin/cupsd" namespace="default"
Aug 20 13:34:20 jm8241982-desktop kernel: [  162.164500] audit(1219260860.759:4): type=1503 operation="capable" name="dac_override" pid=6245 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:34:20 jm8241982-desktop kernel: [  162.164512] audit(1219260860.759:5): type=1503 operation="capable" name="dac_read_search" pid=6245 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:34:35 jm8241982-desktop kernel: [  176.583051] audit(1219260875.224:6): type=1503 operation="capable" name="dac_override" pid=6545 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:34:35 jm8241982-desktop kernel: [  176.583068] audit(1219260875.224:7): type=1503 operation="capable" name="dac_read_search" pid=6545 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:34:46 jm8241982-desktop kernel: [  187.720292] audit(1219260886.395:8): type=1503 operation="capable" name="dac_override" pid=6688 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:34:46 jm8241982-desktop kernel: [  187.720311] audit(1219260886.395:9): type=1503 operation="capable" name="dac_read_search" pid=6688 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:35:17 jm8241982-desktop kernel: [  218.650538] audit(1219260917.423:10): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6882 profile="/usr/sbin/cupsd" namespace="default"
Aug 20 13:35:34 jm8241982-desktop kernel: [  235.466787] audit(1219260934.288:11): type=1503 operation="capable" name="dac_override" pid=6959 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 13:35:34 jm8241982-desktop kernel: [  235.466805] audit(1219260934.288:12): type=1503 operation="capable" name="dac_read_search" pid=6959 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Aug 20 18:03:55 jm8241982-desktop kernel: [16287.293158] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 20 18:03:55 jm8241982-desktop kernel: [16287.293178] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 20 18:03:55 jm8241982-desktop kernel: [16287.293258] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 20 19:55:51 jm8241982-desktop kernel: [22982.164716] audit(1219283751.296:13): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=7672 profile="/usr/sbin/cupsd" namespace="default"
Aug 20 20:03:43 jm8241982-desktop kernel: [23453.255999] audit(1219284223.844:14): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=8000 profile="/usr/sbin/cupsd" namespace="default"
Aug 21 09:18:26 jm8241982-desktop kernel: [70989.365445] audit(1219331906.883:15): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=8933 profile="/usr/sbin/cupsd" namespace="default"
Aug 21 09:46:10 jm8241982-desktop kernel: [72647.614403] audit(1219333570.259:16): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=9333 profile="/usr/sbin/cupsd" namespace="default"
Aug 21 09:54:19 jm8241982-desktop kernel: [73135.648140] audit(1219334059.799:17): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=11140 profile="/usr/sbin/cupsd" namespace="default"
Aug 21 17:42:08 jm8241982-desktop kernel: [101117.399731] usb 5-2.2: new high speed USB device using ehci_hcd and address 6
Aug 21 17:42:08 jm8241982-desktop kernel: [101117.492839] usb 5-2.2: configuration #1 chosen from 1 choice
Aug 21 17:42:08 jm8241982-desktop kernel: [101117.493476] scsi5 : SCSI emulation for USB Mass Storage devices
Aug 21 17:42:08 jm8241982-desktop kernel: [101117.493818] usb-storage: device found at 6
Aug 21 17:42:08 jm8241982-desktop kernel: [101117.493826] usb-storage: waiting for device to settle before scanning
Aug 21 17:42:13 jm8241982-desktop kernel: [101122.476613] usb-storage: device scan complete
Aug 21 17:42:13 jm8241982-desktop kernel: [101122.956107] scsi 5:0:0:0: Direct-Access     GPX      Audio Player          PQ: 0 ANSI: 0 CCS
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.246448] scsi 5:0:0:1: Direct-Access     GPX      SD/MMC CARD           PQ: 0 ANSI: 0 CCS
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.248796] sd 5:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.249661] sd 5:0:0:0: [sdc] Write Protect is on
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.249669] sd 5:0:0:0: [sdc] Mode Sense: 3b 00 80 00
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.249673] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.252892] sd 5:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.253514] sd 5:0:0:0: [sdc] Write Protect is on
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.253521] sd 5:0:0:0: [sdc] Mode Sense: 3b 00 80 00
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.253524] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.253531]  sdc: sdc1
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.254628] sd 5:0:0:0: [sdc] Attached SCSI removable disk
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.254693] sd 5:0:0:0: Attached scsi generic sg3 type 0
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.256764] sd 5:0:0:1: [sdd] 977920 512-byte hardware sectors (501 MB)
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.261366] sd 5:0:0:1: [sdd] Write Protect is on
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.261376] sd 5:0:0:1: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.261380] sd 5:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.264505] sd 5:0:0:1: [sdd] 977920 512-byte hardware sectors (501 MB)
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.265124] sd 5:0:0:1: [sdd] Write Protect is on
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.265132] sd 5:0:0:1: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.265136] sd 5:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.265144]  sdd: sdd1
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.266372] sd 5:0:0:1: [sdd] Attached SCSI removable disk
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.266445] sd 5:0:0:1: Attached scsi generic sg4 type 0
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560574] sd 5:0:0:1: [sdd] READ CAPACITY failed
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560583] sd 5:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560590] sd 5:0:0:1: [sdd] Sense not available.
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560606] sd 5:0:0:0: [sdc] READ CAPACITY failed
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560610] sd 5:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560615] sd 5:0:0:0: [sdc] Sense not available.
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560761] sd 5:0:0:0: [sdc] Write Protect is off
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560768] sd 5:0:0:0: [sdc] Mode Sense: 00 00 00 00
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560773] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560839] sd 5:0:0:1: [sdd] Write Protect is off
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560844] sd 5:0:0:1: [sdd] Mode Sense: 00 00 00 00
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560848] sd 5:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561115] sd 5:0:0:0: [sdc] READ CAPACITY failed
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561120] sd 5:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561131] sd 5:0:0:0: [sdc] Sense not available.
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561295] sd 5:0:0:1: [sdd] READ CAPACITY failed
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561299] sd 5:0:0:1: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561304] sd 5:0:0:1: [sdd] Sense not available.
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561366] sd 5:0:0:0: [sdc] Write Protect is off
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561371] sd 5:0:0:0: [sdc] Mode Sense: 00 00 00 00
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561380] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561549] sd 5:0:0:1: [sdd] Write Protect is off
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561554] sd 5:0:0:1: [sdd] Mode Sense: 00 00 00 00
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561558] sd 5:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.564141] usb 5-2.2: USB disconnect, address 6
Aug 21 17:47:03 jm8241982-desktop kernel: [101412.410814] usb 5-2.2: new high speed USB device using ehci_hcd and address 7
Aug 21 17:47:04 jm8241982-desktop kernel: [101412.503931] usb 5-2.2: configuration #1 chosen from 1 choice
Aug 21 17:47:04 jm8241982-desktop kernel: [101412.504154] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 21 17:47:04 jm8241982-desktop kernel: [101412.504344] usb-storage: device found at 7
Aug 21 17:47:04 jm8241982-desktop kernel: [101412.504348] usb-storage: waiting for device to settle before scanning
Aug 21 17:47:09 jm8241982-desktop kernel: [101417.488067] usb-storage: device scan complete
Aug 21 17:47:09 jm8241982-desktop kernel: [101417.967447] scsi 6:0:0:0: Direct-Access     GPX      Audio Player          PQ: 0 ANSI: 0 CCS
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.256290] scsi 6:0:0:1: Direct-Access     GPX      SD/MMC CARD           PQ: 0 ANSI: 0 CCS
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.261525] sd 6:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.262137] sd 6:0:0:0: [sdc] Write Protect is on
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.262144] sd 6:0:0:0: [sdc] Mode Sense: 3b 00 80 00
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.262148] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.264856] sd 6:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.265479] sd 6:0:0:0: [sdc] Write Protect is on
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.265493] sd 6:0:0:0: [sdc] Mode Sense: 3b 00 80 00
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.265497] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.265503]  sdc: sdc1
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.266704] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.266768] sd 6:0:0:0: Attached scsi generic sg3 type 0
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.268854] sd 6:0:0:1: [sdd] 977920 512-byte hardware sectors (501 MB)
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.269863] sd 6:0:0:1: [sdd] Write Protect is off
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.269874] sd 6:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.269879] sd 6:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.272583] sd 6:0:0:1: [sdd] 977920 512-byte hardware sectors (501 MB)
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.273455] sd 6:0:0:1: [sdd] Write Protect is off
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.273474] sd 6:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.273478] sd 6:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.273484]  sdd: sdd1
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.274682] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.274748] sd 6:0:0:1: Attached scsi generic sg4 type 0
Aug 21 17:49:33 jm8241982-desktop kernel: [101561.505940] usb 5-2.2: USB disconnect, address 7
Aug 21 17:49:58 jm8241982-desktop kernel: [101586.202695] usb 5-2.2: new high speed USB device using ehci_hcd and address 8
Aug 21 17:49:58 jm8241982-desktop kernel: [101586.295796] usb 5-2.2: configuration #1 chosen from 1 choice
Aug 21 17:49:58 jm8241982-desktop kernel: [101586.296383] scsi7 : SCSI emulation for USB Mass Storage devices
Aug 21 17:49:58 jm8241982-desktop kernel: [101586.296779] usb-storage: device found at 8
Aug 21 17:49:58 jm8241982-desktop kernel: [101586.296785] usb-storage: waiting for device to settle before scanning
Aug 21 17:50:03 jm8241982-desktop kernel: [101591.278948] usb-storage: device scan complete
Aug 21 17:50:03 jm8241982-desktop kernel: [101591.758324] scsi 7:0:0:0: Direct-Access     GPX      Audio Player          PQ: 0 ANSI: 0 CCS
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.038324] scsi 7:0:0:1: Direct-Access     GPX      SD/MMC CARD           PQ: 0 ANSI: 0 CCS
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.040043] sd 7:0:0:0: [sdd] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.040913] sd 7:0:0:0: [sdd] Write Protect is on
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.040921] sd 7:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.040925] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.043915] sd 7:0:0:0: [sdd] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.044524] sd 7:0:0:0: [sdd] Write Protect is on
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.044529] sd 7:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.044531] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.044538]  sdd: sdd1
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.045494] sd 7:0:0:0: [sdd] Attached SCSI removable disk
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.045563] sd 7:0:0:0: Attached scsi generic sg3 type 0
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.047650] sd 7:0:0:1: [sde] 977920 512-byte hardware sectors (501 MB)
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.048274] sd 7:0:0:1: [sde] Write Protect is off
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.048282] sd 7:0:0:1: [sde] Mode Sense: 3b 00 00 00
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.048286] sd 7:0:0:1: [sde] Assuming drive cache: write through
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.051005] sd 7:0:0:1: [sde] 977920 512-byte hardware sectors (501 MB)
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.051639] sd 7:0:0:1: [sde] Write Protect is off
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.051649] sd 7:0:0:1: [sde] Mode Sense: 3b 00 00 00
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.051653] sd 7:0:0:1: [sde] Assuming drive cache: write through
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.051659]  sde: sde1
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.052860] sd 7:0:0:1: [sde] Attached SCSI removable disk
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.052926] sd 7:0:0:1: Attached scsi generic sg4 type 0
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.438894] sd 7:0:0:0: [sdd] READ CAPACITY failed
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.438903] sd 7:0:0:0: [sdd] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.438909] sd 7:0:0:0: [sdd] Sense not available.
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.438926] sd 7:0:0:1: [sde] READ CAPACITY failed
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.438929] sd 7:0:0:1: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.438933] sd 7:0:0:1: [sde] Sense not available.
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.439071] sd 7:0:0:0: [sdd] Write Protect is off
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.439078] sd 7:0:0:0: [sdd] Mode Sense: 00 00 00 00
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.439083] sd 7:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.439120] sd 7:0:0:1: [sde] Write Protect is off
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.439124] sd 7:0:0:1: [sde] Mode Sense: 00 00 00 00
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.439129] sd 7:0:0:1: [sde] Assuming drive cache: write through
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.440851] usb 5-2.2: USB disconnect, address 8
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.447318] sd 7:0:0:1: [sde] READ CAPACITY failed
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.447324] sd 7:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.447330] sd 7:0:0:1: [sde] Sense not available.
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.447347] sd 7:0:0:1: [sde] Write Protect is off
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.447350] sd 7:0:0:1: [sde] Mode Sense: 00 00 00 00
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.447353] sd 7:0:0:1: [sde] Assuming drive cache: write through
Aug 21 17:52:51 jm8241982-desktop kernel: [101759.230842] usb 5-2.2: new high speed USB device using ehci_hcd and address 9
Aug 21 17:52:51 jm8241982-desktop kernel: [101759.323942] usb 5-2.2: configuration #1 chosen from 1 choice
Aug 21 17:52:51 jm8241982-desktop kernel: [101759.324467] scsi8 : SCSI emulation for USB Mass Storage devices
Aug 21 17:52:51 jm8241982-desktop kernel: [101759.324971] usb-storage: device found at 9
Aug 21 17:52:51 jm8241982-desktop kernel: [101759.324978] usb-storage: waiting for device to settle before scanning
Aug 21 17:52:56 jm8241982-desktop kernel: [101764.308086] usb-storage: device scan complete
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.787467] scsi 8:0:0:0: Direct-Access     GPX      Audio Player          PQ: 0 ANSI: 0 CCS
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.788074] scsi 8:0:0:1: Direct-Access     GPX      SD/MMC CARD           PQ: 0 ANSI: 0 CCS
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.789691] sd 8:0:0:0: [sdd] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.790309] sd 8:0:0:0: [sdd] Write Protect is on
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.790315] sd 8:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.790317] sd 8:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.792915] sd 8:0:0:0: [sdd] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.793535] sd 8:0:0:0: [sdd] Write Protect is on
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.793541] sd 8:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.793545] sd 8:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.793551]  sdd: sdd1
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.794644] sd 8:0:0:0: [sdd] Attached SCSI removable disk
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.794708] sd 8:0:0:0: Attached scsi generic sg3 type 0
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.795850] sd 8:0:0:1: [sde] Attached SCSI removable disk
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.795909] sd 8:0:0:1: Attached scsi generic sg4 type 0
Aug 21 17:59:39 jm8241982-desktop kernel: [102165.820589] usb 5-2.2: USB disconnect, address 9
Aug 21 17:59:47 jm8241982-desktop kernel: [102173.929064] usb 5-2.2: new high speed USB device using ehci_hcd and address 10
Aug 21 17:59:47 jm8241982-desktop kernel: [102174.022169] usb 5-2.2: configuration #1 chosen from 1 choice
Aug 21 17:59:47 jm8241982-desktop kernel: [102174.022540] scsi9 : SCSI emulation for USB Mass Storage devices
Aug 21 17:59:47 jm8241982-desktop kernel: [102174.022743] usb-storage: device found at 10
Aug 21 17:59:47 jm8241982-desktop kernel: [102174.022749] usb-storage: waiting for device to settle before scanning
Aug 21 17:59:52 jm8241982-desktop kernel: [102179.006311] usb-storage: device scan complete
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.485819] scsi 9:0:0:0: Direct-Access     GPX      Audio Player          PQ: 0 ANSI: 0 CCS
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.764074] scsi 9:0:0:1: Direct-Access     GPX      SD/MMC CARD           PQ: 0 ANSI: 0 CCS
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.765791] sd 9:0:0:0: [sdd] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.766418] sd 9:0:0:0: [sdd] Write Protect is on
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.766426] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.766430] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.769027] sd 9:0:0:0: [sdd] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.769650] sd 9:0:0:0: [sdd] Write Protect is on
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.769655] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.769657] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.769661]  sdd: sdd1
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.770617] sd 9:0:0:0: [sdd] Attached SCSI removable disk
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.770685] sd 9:0:0:0: Attached scsi generic sg3 type 0
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.772776] sd 9:0:0:1: [sde] 977920 512-byte hardware sectors (501 MB)
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.773438] sd 9:0:0:1: [sde] Write Protect is off
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.773445] sd 9:0:0:1: [sde] Mode Sense: 3b 00 00 00
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.773449] sd 9:0:0:1: [sde] Assuming drive cache: write through
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.776007] sd 9:0:0:1: [sde] 977920 512-byte hardware sectors (501 MB)
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.776632] sd 9:0:0:1: [sde] Write Protect is off
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.776638] sd 9:0:0:1: [sde] Mode Sense: 3b 00 00 00
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.776642] sd 9:0:0:1: [sde] Assuming drive cache: write through
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.776649]  sde: sde1
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.777864] sd 9:0:0:1: [sde] Attached SCSI removable disk
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.777928] sd 9:0:0:1: Attached scsi generic sg4 type 0
Aug 21 18:00:04 jm8241982-desktop kernel: [102190.045463] sd 9:0:0:0: [sdd] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 18:00:04 jm8241982-desktop kernel: [102190.046077] sd 9:0:0:0: [sdd] Write Protect is off
Aug 21 18:00:04 jm8241982-desktop kernel: [102190.046083] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:00:04 jm8241982-desktop kernel: [102190.046088] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 18:00:06 jm8241982-desktop kernel: [102192.039205] sd 9:0:0:0: [sdd] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 18:00:06 jm8241982-desktop kernel: [102192.039952] sd 9:0:0:0: [sdd] Write Protect is off
Aug 21 18:00:06 jm8241982-desktop kernel: [102192.039958] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:00:06 jm8241982-desktop kernel: [102192.039964] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 18:00:32 jm8241982-desktop kernel: [102218.526610] sd 9:0:0:0: [sdd] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 18:00:32 jm8241982-desktop kernel: [102218.527237] sd 9:0:0:0: [sdd] Write Protect is off
Aug 21 18:00:32 jm8241982-desktop kernel: [102218.527245] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:00:32 jm8241982-desktop kernel: [102218.527248] sd 9:0:0:0: [sdd] Assuming drive cache: write through
Aug 21 18:00:32 jm8241982-desktop kernel: [102218.527258]  sdd: sdd1
Aug 21 18:01:54 jm8241982-desktop kernel: [102300.251206] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 21 18:04:31 jm8241982-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 21 18:04:31 jm8241982-desktop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 21 18:04:31 jm8241982-desktop kernel: Symbols match kernel version 2.6.24.
Aug 21 18:04:31 jm8241982-desktop kernel: Loaded 31672 symbols from 85 modules.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] 896MB LOWMEM available.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] found SMP MP-table at 000f37a0
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Zone PFN ranges:
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   DMA             0 ->     4096
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   HighMem    229376 ->   524016
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Movable zone start PFN for each node
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]     0:        0 ->   524016
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] DMI 2.3 present.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7930 checksum 0
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: RSDP 000F7930, 0014 (r0 P4M80P)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: RSDT 7FEF3040, 002C (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: DSDT 7FEF3180, 4EA6 (r1 P4M80P AWRDACPI     1000 MSFT  100000E)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: FACS 7FEF0000, 0040
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: APIC 7FEF8080, 0084 (r1 P4M80P AWRDACPI 42302E31 AWRD        0)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Processor #0 15:3 APIC version 20
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Processor #1 15:3 APIC version 20
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 3, address 0xfec00000, GSI 0-23
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:7ed00000)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519923
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Kernel command line: root=UUID=0b1db72d-695f-4efc-b9c3-7ac6d48a3ea2 ro quiet splash
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Initializing CPU#0
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Detected 3200.393 MHz processor.
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.696947] Console: colour VGA+ 80x25
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.696951] console [tty0] enabled
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.697417] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.697879] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810233] Memory: 2066072k/2096064k available (2177k kernel code, 28688k reserved, 1006k data, 368k init, 1178560k highmem)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810242] virtual kernel memory layout:
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810243]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810244]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810245]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810246]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810247]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810248]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810249]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810251] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.810311] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890103] Calibrating delay using timer specific routine.. 6408.50 BogoMIPS (lpj=12817011)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890136] Security Framework initialized
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890145] SELinux:  Disabled at boot.
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890164] AppArmor: AppArmor initialized
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890168] Failure registering capabilities with primary security module.
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890178] Mount-cache hash table entries: 512
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890333] Initializing cgroup subsys ns
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890339] Initializing cgroup subsys cpuacct
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890352] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890361] monitor/mwait feature present.
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890363] using mwait in idle threads.
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890369] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890372] CPU: L2 cache: 1024K
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890375] CPU: Physical Processor ID: 0
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890377] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890389] Compat vDSO mapped to ffffe000.
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890407] Checking 'hlt' instruction... OK.
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.906523] SMP alternatives: switching to UP code
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.908409] Early unpacking initramfs... done
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.185108] ACPI: Core revision 20070126
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.185163] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.189436] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.189457] SMP alternatives: switching to SMP code
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.190262] Booting processor 1/1 eip 3000
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.200448] Initializing CPU#1
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.280911] Calibrating delay using timer specific routine.. 6400.70 BogoMIPS (lpj=12801416)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.280923] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.280930] monitor/mwait feature present.
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.280936] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.280939] CPU: L2 cache: 1024K
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.280941] CPU: Physical Processor ID: 0
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.280944] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.281312] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.281356] Total of 2 processors activated (12809.21 BogoMIPS).
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.282112] ENABLING IO-APIC IRQs
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.282434] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.428610] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448565] Brought up 2 CPUs
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448627] CPU0 attaching sched-domain:
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448631]  domain 0: span 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448633]   groups: 01 02
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448636]   domain 1: span 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448638]    groups: 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448641] CPU1 attaching sched-domain:
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448642]  domain 0: span 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448644]   groups: 02 01
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448647]   domain 1: span 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448649]    groups: 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448908] net_namespace: 64 bytes
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448921] Booting paravirtualized kernel on bare hardware
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.449465] Time:  0:04:03  Date: 08/22/08
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.449491] NET: Registered protocol family 16
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.449744] EISA bus registered
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.449751] ACPI: bus type pci registered
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.457789] PCI: PCI BIOS revision 2.10 entry at 0xf9f30, last bus=1
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.457791] PCI: Using configuration type 1
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.457817] Setting up standard PCI resources
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.464738] ACPI: EC: Look up EC in DSDT
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.470532] ACPI: Interpreter enabled
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.470538] ACPI: (supports S0 S1 S4 S5)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.470557] ACPI: Using IOAPIC for interrupt routing
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.476549] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.477812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.518359] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.518525] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.518697] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.518847] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.518991] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.519130] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.519269] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.519407] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.519580] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.519735] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.519890] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.520068] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.520204] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.520244] pnp: PnP ACPI init
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.520252] ACPI: bus type pnp registered
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.523227] pnp: PnP ACPI: found 9 devices
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.523230] ACPI: ACPI bus type pnp unregistered
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.523234] PnPBIOS: Disabled by ACPI PNP
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.523552] PCI: Using ACPI for IRQ routing
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.523556] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.564215] NET: Registered protocol family 8
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.564217] NET: Registered protocol family 20
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.564294] AppArmor: AppArmor Filesystem Enabled
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.568055] Time: tsc clocksource has been installed.
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584191] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584195] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584197] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584200] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584203] system 00:00: iomem range 0x7fef0000-0x7fefffff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584206] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584208] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584211] system 00:00: iomem range 0x100000-0x7feeffff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584214] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584216] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584219] system 00:00: iomem range 0xfff80000-0xfffeffff could not be reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584226] system 00:02: ioport range 0x400-0x47f has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584229] system 00:02: ioport range 0x500-0x50f has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584235] system 00:03: ioport range 0xb78-0xb7b has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584238] system 00:03: ioport range 0xf78-0xf7b has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584240] system 00:03: ioport range 0xa78-0xa7b has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584242] system 00:03: ioport range 0xe78-0xe7b has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584245] system 00:03: ioport range 0xbbc-0xbbf has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584247] system 00:03: ioport range 0xfbc-0xfbf has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584250] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584252] system 00:03: ioport range 0x800-0x87f has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584254] system 00:03: ioport range 0x880-0x8ff has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.584257] system 00:03: ioport range 0x290-0x297 has been reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.614694] PCI: Bridge: 0000:00:01.0
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.614698]   IO window: b000-bfff
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.614704]   MEM window: fb000000-fcffffff
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.614708]   PREFETCH window: e8000000-efffffff
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.614728] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.614738] NET: Registered protocol family 2
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.652010] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.652347] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.653047] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.653717] TCP: Hash tables configured (established 131072 bind 65536)
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.653722] TCP reno registered
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.664116] checking if image is initramfs... it is
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.114400] Switched to high resolution mode on CPU 0
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.114529] Switched to high resolution mode on CPU 1
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.212336] Freeing initrd memory: 7305k freed
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.213270] audit: initializing netlink socket (disabled)
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.213288] audit(1219363443.284:1): initialized
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.213548] highmem bounce pool size: 64 pages
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.215870] VFS: Disk quotas dquot_6.5.1
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.215966] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.216115] io scheduler noop registered
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.216118] io scheduler anticipatory registered
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.216120] io scheduler deadline registered
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.216130] io scheduler cfq registered (default)
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.216144] PCI: VIA PCI bridge detected. Disabling DAC.
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.189594] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.189622] PCI: Bypassing VIA 8237 APIC De-Assert Message
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.189645] Boot video device is 0000:01:00.0
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.190024] isapnp: Scanning for PnP cards...
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.541076] isapnp: No Plug & Play device found
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.575730] Real Time Clock Driver v1.12ac
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.575847] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.577388] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.577469] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.577584] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.577587] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.577740] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.600433] mice: PS/2 mouse device common for all mice
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.600584] EISA: Probing bus 0 at eisa.0
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.600625] EISA: Detected 0 cards.
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.600629] cpuidle: using governor ladder
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.600631] cpuidle: using governor menu
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.600716] NET: Registered protocol family 1
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.600745] Using IPI No-Shortcut mode
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.600776] registered taskstats version 1
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.600870]   Magic number: 4:175:52
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.601011] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.601013] EDD information not available.
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.601368] Freeing unused kernel memory: 368k freed
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.625099] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 21 18:04:31 jm8241982-desktop kernel: [   32.838878] fuse init (API version 7.9)
Aug 21 18:04:31 jm8241982-desktop kernel: [   32.860682] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 21 18:04:31 jm8241982-desktop kernel: [   32.860697] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.058761] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.058775] 3c59x: Donald Becker and others.
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.058783] 0000:00:05.0: 3Com PCI 3c905B Cyclone 100baseTx at f883e000.
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.058793] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.187899] SCSI subsystem initialized
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.227354] libata version 3.00 loaded.
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.237524] sata_via 0000:00:0f.0: version 2.3
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.237910] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.237921] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.237978] sata_via 0000:00:0f.0: routed to hard irq line 11
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.237990] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.238848] scsi0 : sata_via
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.247322] scsi1 : sata_via
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.247409] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf400 bmdma 0xe800 irq 17
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.247414] ata2: SATA max UDMA/133 cmd 0xf000 ctl 0xec00 bmdma 0xe808 irq 17
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.399961] usbcore: registered new interface driver usbfs
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.399995] usbcore: registered new interface driver hub
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.400107] usbcore: registered new device driver usb
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.426834] USB Universal Host Controller Interface driver v3.0
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.450671] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.526578] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.526591] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.666016] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.829920] ata2.00: ATA-7: WDC WD2500YD-01NVB1, 10.02E01, max UDMA/133
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.829928] ata2.00: 490234752 sectors, multi 1: LBA48 NCQ (depth 0/1)
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.837699] ata2.00: configured for UDMA/133
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.837843] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500YD-01N 10.0 PQ: 0 ANSI: 5
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.838547] pata_via 0000:00:0f.1: version 0.3.3
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.838592] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.838643] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.838800] scsi2 : pata_via
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.838870] scsi3 : pata_via
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.840723] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.840727] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.172810] ata3.00: ATAPI: Optiarc DVD RW AD-7191A, 1.04, max UDMA/66
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.360112] ata3.00: configured for UDMA/66
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.526808] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7191A  1.04 PQ: 0 ANSI: 5
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.527972] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.527982] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.527998] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.528004] uhci_hcd 0000:00:10.0: UHCI Host Controller
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.528272] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.528310] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000dc00
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.528523] usb usb1: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.528561] hub 1-0:1.0: USB hub found
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.528571] hub 1-0:1.0: 2 ports detected
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.635165] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.635184] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.635189] uhci_hcd 0000:00:10.1: UHCI Host Controller
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.635225] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.635253] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000d800
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.635417] usb usb2: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.635456] hub 2-0:1.0: USB hub found
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.635465] hub 2-0:1.0: 2 ports detected
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.734833] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.734849] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.734854] uhci_hcd 0000:00:10.2: UHCI Host Controller
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.734888] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.734913] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000d400
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.735083] usb usb3: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.735121] hub 3-0:1.0: USB hub found
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.735129] hub 3-0:1.0: 2 ports detected
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.838546] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.838565] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.838570] uhci_hcd 0000:00:10.3: UHCI Host Controller
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.838617] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.838645] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000d000
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.838808] usb usb4: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.838846] hub 4-0:1.0: USB hub found
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.838854] hub 4-0:1.0: 2 ports detected
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.870304] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.943141] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.943155] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.943167] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.943645] eth1: VIA Rhine II at 0xfdffd000, 00:19:db:25:49:e1, IRQ 19.
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.944358] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.944592] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.944610] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.944617] ehci_hcd 0000:00:10.4: EHCI Host Controller
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.944667] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.944729] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfdffe000
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.994922] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.995086] usb usb5: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.995124] hub 5-0:1.0: USB hub found
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.995134] hub 5-0:1.0: 8 ports detected
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112228] Driver 'sd' needs updating - please use bus_type methods
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112350] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112369] sd 1:0:0:0: [sda] Write Protect is off
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112373] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112402] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112473] sd 1:0:0:0: [sda] 490234752 512-byte hardware sectors (251000 MB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112489] sd 1:0:0:0: [sda] Write Protect is off
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112493] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112521] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112526]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.127332]  sda1 sda2 < sda5 >
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.145931] sd 1:0:0:0: [sda] Attached SCSI disk
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.152501] sd 1:0:0:0: Attached scsi generic sg0 type 0
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.152536] sr 2:0:0:0: Attached scsi generic sg1 type 5
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.155810] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.155817] Uniform CD-ROM driver Revision: 3.20
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.155895] sr 2:0:0:0: Attached scsi CD-ROM sr0
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.367758] Attempting manual resume
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.367763] swsusp: Resume From Partition 8:5
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.367764] PM: Checking swsusp image.
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.367938] PM: Resume from disk failed.
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.396686] usb 1-1: device not accepting address 2, error -71
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.415152] kjournald starting.  Commit interval 5 seconds
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.415161] EXT3-fs: mounted filesystem with ordered data mode.
Aug 21 18:04:31 jm8241982-desktop kernel: [   36.825307] usb 5-2: new high speed USB device using ehci_hcd and address 3
Aug 21 18:04:31 jm8241982-desktop kernel: [   36.958174] usb 5-2: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   36.958462] hub 5-2:1.0: USB hub found
Aug 21 18:04:31 jm8241982-desktop kernel: [   36.958811] hub 5-2:1.0: 4 ports detected
Aug 21 18:04:31 jm8241982-desktop kernel: [   37.247021] hub 5-0:1.0: over-current change on port 5
Aug 21 18:04:31 jm8241982-desktop kernel: [   37.350696] hub 5-0:1.0: over-current change on port 6
Aug 21 18:04:31 jm8241982-desktop kernel: [   37.455368] hub 5-0:1.0: over-current change on port 7
Aug 21 18:04:31 jm8241982-desktop kernel: [   37.559048] hub 5-0:1.0: over-current change on port 8
Aug 21 18:04:31 jm8241982-desktop kernel: [   37.902004] usb 2-2: new low speed USB device using uhci_hcd and address 2
Aug 21 18:04:31 jm8241982-desktop kernel: [   38.083430] usb 2-2: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   38.323704] usb 1-1: new full speed USB device using uhci_hcd and address 4
Aug 21 18:04:31 jm8241982-desktop kernel: [   38.508479] usb 1-1: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   38.711840] usb 5-2.1: new high speed USB device using ehci_hcd and address 5
Aug 21 18:04:31 jm8241982-desktop kernel: [   38.808178] usb 5-2.1: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   39.006907] usb 5-2.2: new high speed USB device using ehci_hcd and address 6
Aug 21 18:04:31 jm8241982-desktop kernel: [   39.098852] usb 5-2.2: configuration #1 chosen from 1 choice
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.145121] Linux agpgart interface v0.102
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.272799] agpgart: Detected VIA VT3314 chipset
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.280117] agpgart: AGP aperture is 128M @ 0xf0000000
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.348546] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.428332] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.940603] input: Power Button (FF) as /devices/virtual/input/input2
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.966464] ACPI: Power Button (FF) [PWRF]
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.966617] input: Power Button (CM) as /devices/virtual/input/input3
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.998376] ACPI: Power Button (CM) [PWRB]
Aug 21 18:04:31 jm8241982-desktop kernel: [   42.998532] input: Sleep Button (CM) as /devices/virtual/input/input4
Aug 21 18:04:31 jm8241982-desktop kernel: [   43.030300] ACPI: Sleep Button (CM) [SLPB]
Aug 21 18:04:31 jm8241982-desktop kernel: [   43.619213] nvidia: module license 'NVIDIA' taints kernel.
Aug 21 18:04:31 jm8241982-desktop kernel: [   44.150010] input: PC Speaker as /devices/platform/pcspkr/input/input5
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.011310] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.011324] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.011604] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.040196] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.040230] usbcore: registered new interface driver usblp
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.260283] usbcore: registered new interface driver hiddev
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.275237] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2:1.0/input/input6
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.294416] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.294449] usbcore: registered new interface driver usbhid
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.294455] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.374499] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.374510] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.374658] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.551464] usbcore: registered new interface driver libusual
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.588484] Initializing USB Mass Storage driver...
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.616381] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.616599] usb-storage: device found at 5
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.616603] usb-storage: waiting for device to settle before scanning
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.620878] scsi5 : SCSI emulation for USB Mass Storage devices
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.621073] usbcore: registered new interface driver usb-storage
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.621080] USB Mass Storage support registered.
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.621245] usb-storage: device found at 6
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.621248] usb-storage: waiting for device to settle before scanning
Aug 21 18:04:31 jm8241982-desktop kernel: [   47.233085] lp: driver loaded but no devices found
Aug 21 18:04:31 jm8241982-desktop kernel: [   47.383741] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
Aug 21 18:04:31 jm8241982-desktop kernel: [   47.934356] EXT3 FS on sda1, internal journal
Aug 21 18:04:31 jm8241982-desktop kernel: [   49.351067] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 21 18:04:31 jm8241982-desktop kernel: [   49.830175] No dock devices found.
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.599243] usb-storage: device scan complete
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.599987] scsi 4:0:0:0: Direct-Access     ST310003 40NS                  PQ: 0 ANSI: 2 CCS
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.606090] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.606816] sd 4:0:0:0: [sdb] Write Protect is off
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.606821] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.606824] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.607933] sd 4:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.608695] sd 4:0:0:0: [sdb] Write Protect is off
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.608699] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.608703] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.608707]  sdb: sdb1
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.609535] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.609599] sd 4:0:0:0: Attached scsi generic sg2 type 0
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.615859] usb-storage: device scan complete
Aug 21 18:04:31 jm8241982-desktop kernel: [   51.095311] scsi 5:0:0:0: Direct-Access     GPX      Audio Player          PQ: 0 ANSI: 0 CCS
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.145734] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.145742] apm: disabled - APM is not SMP safe.
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.309694] ppdev: user-space parallel port driver
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.375317] scsi 5:0:0:1: Direct-Access     GPX      SD/MMC CARD           PQ: 0 ANSI: 0 CCS
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.378782] sd 5:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.379415] sd 5:0:0:0: [sdc] Write Protect is off
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.379424] sd 5:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.379428] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.382008] sd 5:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.382879] sd 5:0:0:0: [sdc] Write Protect is off
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.382885] sd 5:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.382888] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.382895]  sdc: sdc1
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.384113] sd 5:0:0:0: [sdc] Attached SCSI removable disk
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.384176] sd 5:0:0:0: Attached scsi generic sg3 type 0
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.386263] sd 5:0:0:1: [sdd] 977920 512-byte hardware sectors (501 MB)
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.386885] sd 5:0:0:1: [sdd] Write Protect is off
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.386892] sd 5:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.386896] sd 5:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.389486] sd 5:0:0:1: [sdd] 977920 512-byte hardware sectors (501 MB)
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.390113] sd 5:0:0:1: [sdd] Write Protect is off
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.390122] sd 5:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.390126] sd 5:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.390133]  sdd: sdd1
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.391355] sd 5:0:0:1: [sdd] Attached SCSI removable disk
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.391423] sd 5:0:0:1: Attached scsi generic sg4 type 0
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.507483] audit(1219363472.399:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4940 profile="/usr/sbin/cupsd" namespace="default"
Aug 21 18:04:34 jm8241982-desktop kernel: [   53.916611] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 21 18:04:34 jm8241982-desktop kernel: [   53.942494] eth0:  setting half-duplex.
Aug 21 18:04:34 jm8241982-desktop kernel: [   53.989306] Bluetooth: Core ver 2.11
Aug 21 18:04:34 jm8241982-desktop kernel: [   53.989731] NET: Registered protocol family 31
Aug 21 18:04:34 jm8241982-desktop kernel: [   53.989740] Bluetooth: HCI device and connection manager initialized
Aug 21 18:04:34 jm8241982-desktop kernel: [   53.989747] Bluetooth: HCI socket layer initialized
Aug 21 18:04:34 jm8241982-desktop kernel: [   54.003473] Bluetooth: L2CAP ver 2.9
Aug 21 18:04:34 jm8241982-desktop kernel: [   54.003481] Bluetooth: L2CAP socket layer initialized
Aug 21 18:04:34 jm8241982-desktop kernel: [   54.065830] Bluetooth: RFCOMM socket layer initialized
Aug 21 18:04:34 jm8241982-desktop kernel: [   54.065853] Bluetooth: RFCOMM TTY layer initialized
Aug 21 18:04:34 jm8241982-desktop kernel: [   54.065857] Bluetooth: RFCOMM ver 1.8
Aug 21 18:04:37 jm8241982-desktop kernel: [   56.173523] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 21 18:04:37 jm8241982-desktop kernel: [   56.173546] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 21 18:04:37 jm8241982-desktop kernel: [   56.173650] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 21 18:04:38 jm8241982-desktop kernel: [   57.723795] NET: Registered protocol family 17
Aug 21 18:04:41 jm8241982-desktop kernel: [   60.552704] NET: Registered protocol family 10
Aug 21 18:04:41 jm8241982-desktop kernel: [   60.553084] lo: Disabled Privacy Extensions
Aug 21 18:04:41 jm8241982-desktop kernel: [   60.553717] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 21 18:04:56 jm8241982-desktop kernel: [   71.469981] eth1: no IPv6 routers present
Aug 21 18:08:44 jm8241982-desktop kernel: [  299.332284] usb 5-2.2: USB disconnect, address 6
Aug 21 18:09:56 jm8241982-desktop kernel: [  370.476636] usb 5-2.2: new high speed USB device using ehci_hcd and address 7
Aug 21 18:09:56 jm8241982-desktop kernel: [  370.570614] usb 5-2.2: configuration #1 chosen from 1 choice
Aug 21 18:09:56 jm8241982-desktop kernel: [  370.571122] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 21 18:09:56 jm8241982-desktop kernel: [  370.571574] usb-storage: device found at 7
Aug 21 18:09:56 jm8241982-desktop kernel: [  370.571581] usb-storage: waiting for device to settle before scanning
Aug 21 18:10:01 jm8241982-desktop kernel: [  375.554020] usb-storage: device scan complete
Aug 21 18:10:01 jm8241982-desktop kernel: [  376.033395] scsi 6:0:0:0: Direct-Access     GPX      Audio Player          PQ: 0 ANSI: 0 CCS
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.130459] scsi 6:0:0:1: Direct-Access     GPX      SD/MMC CARD           PQ: 0 ANSI: 0 CCS
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.132183] sd 6:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.136060] sd 6:0:0:0: [sdc] Write Protect is off
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.136071] sd 6:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.136082] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.138656] sd 6:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.139280] sd 6:0:0:0: [sdc] Write Protect is off
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.139286] sd 6:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.139290] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.139295]  sdc: sdc1
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.140785] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.140857] sd 6:0:0:0: Attached scsi generic sg3 type 0
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.143037] sd 6:0:0:1: [sdd] 1984000 512-byte hardware sectors (1016 MB)
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.143913] sd 6:0:0:1: [sdd] Write Protect is off
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.143920] sd 6:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.143924] sd 6:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.146634] sd 6:0:0:1: [sdd] 1984000 512-byte hardware sectors (1016 MB)
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.147524] sd 6:0:0:1: [sdd] Write Protect is off
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.147535] sd 6:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.147539] sd 6:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.147546]  sdd: sdd1
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.148763] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.148831] sd 6:0:0:1: Attached scsi generic sg4 type 0
Aug 21 18:11:45 jm8241982-desktop kernel: [  479.248598] usb 5-2.2: USB disconnect, address 7
Aug 21 18:11:48 jm8241982-desktop kernel: [  482.764091] usb 5-2.2: new high speed USB device using ehci_hcd and address 8
Aug 21 18:11:49 jm8241982-desktop kernel: [  482.857071] usb 5-2.2: configuration #1 chosen from 1 choice
Aug 21 18:11:49 jm8241982-desktop kernel: [  482.857305] scsi7 : SCSI emulation for USB Mass Storage devices
Aug 21 18:11:49 jm8241982-desktop kernel: [  482.857495] usb-storage: device found at 8
Aug 21 18:11:49 jm8241982-desktop kernel: [  482.857499] usb-storage: waiting for device to settle before scanning
Aug 21 18:11:54 jm8241982-desktop kernel: [  487.841456] usb-storage: device scan complete
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.320840] scsi 7:0:0:0: Direct-Access     GPX      Audio Player          PQ: 0 ANSI: 0 CCS
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.421408] scsi 7:0:0:1: Direct-Access     GPX      SD/MMC CARD           PQ: 0 ANSI: 0 CCS
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.422891] sd 7:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.423767] sd 7:0:0:0: [sdc] Write Protect is off
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.423780] sd 7:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.423784] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.428062] sd 7:0:0:0: [sdc] 2032128 512-byte hardware sectors (1040 MB)
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.428724] sd 7:0:0:0: [sdc] Write Protect is off
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.428732] sd 7:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.428736] sd 7:0:0:0: [sdc] Assuming drive cache: write through
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.428743]  sdc: sdc1
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.429957] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.430023] sd 7:0:0:0: Attached scsi generic sg3 type 0
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.432096] sd 7:0:0:1: [sdd] 1984000 512-byte hardware sectors (1016 MB)
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.432718] sd 7:0:0:1: [sdd] Write Protect is off
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.432725] sd 7:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.432729] sd 7:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.435330] sd 7:0:0:1: [sdd] 1984000 512-byte hardware sectors (1016 MB)
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.436322] sd 7:0:0:1: [sdd] Write Protect is off
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.436329] sd 7:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.436333] sd 7:0:0:1: [sdd] Assuming drive cache: write through
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.436340]  sdd: sdd1
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.437683] sd 7:0:0:1: [sdd] Attached SCSI removable disk
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.437751] sd 7:0:0:1: Attached scsi generic sg4 type 0
Aug 22 08:28:24 jm8241982-desktop kernel: [51720.720173] xine_extractor[18555]: segfault at b2f3b8b1 eip b7770a17 esp b52d9690 error 4
Aug 22 09:21:46 jm8241982-desktop kernel: [54913.691643] xine_extractor[19831]: segfault at b2ec70e1 eip b7735a17 esp b529e690 error 4
Aug 22 09:21:48 jm8241982-desktop kernel: [54914.794467] xine_extractor[19839]: segfault at 5562e840 eip b76bb797 esp b5309c10 error 4
Aug 22 12:06:57 jm8241982-desktop kernel: [64793.851045] usblp0: removed
Aug 22 12:06:57 jm8241982-desktop kernel: [64794.147226] audit(1219428417.731:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=27265 profile="/usr/sbin/cupsd" namespace="default"

my user.log

Aug 18 21:04:29 jm8241982-desktop python: hp-makeuri[24048]: error: Device does not support fax.
Aug 18 21:04:29 jm8241982-desktop python: hp-makeuri[24053]: error: Device does not support fax.
Aug 18 22:01:10 jm8241982-desktop dhcdbd: Started up.
Aug 18 22:01:12 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 18 22:01:13 jm8241982-desktop python: hp-makeuri[5258]: error: Device does not support fax.
Aug 18 22:01:16 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Aug 18 22:01:16 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Aug 18 22:01:16 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Aug 18 22:01:16 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Aug 18 22:41:51 jm8241982-desktop pulseaudio[5614]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 18 22:45:51 jm8241982-desktop dhcdbd: Started up.
Aug 18 22:45:54 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 18 22:45:55 jm8241982-desktop python: hp-makeuri[5297]: error: Device does not support fax.
Aug 18 22:46:00 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Aug 18 22:46:00 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Aug 18 22:46:00 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Aug 18 22:46:00 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Aug 18 22:46:15 jm8241982-desktop pulseaudio[5596]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 19 05:59:02 jm8241982-desktop dhcdbd: Started up.
Aug 19 05:59:04 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 19 05:59:06 jm8241982-desktop python: hp-makeuri[5294]: error: Device does not support fax.
Aug 19 05:59:09 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Aug 19 05:59:09 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Aug 19 05:59:09 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Aug 19 05:59:09 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Aug 19 05:59:30 jm8241982-desktop pulseaudio[5623]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 19 12:41:03 jm8241982-desktop pulseaudio[15422]: pid.c: Stale PID file, overwriting.
Aug 19 12:41:03 jm8241982-desktop pulseaudio[15422]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 19 20:48:52 jm8241982-desktop dhcdbd: Started up.
Aug 19 20:48:54 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 19 20:48:56 jm8241982-desktop python: hp-makeuri[5410]: error: Device does not support fax.
Aug 19 20:48:59 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Aug 19 20:48:59 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Aug 19 20:48:59 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Aug 19 20:48:59 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Aug 19 20:51:37 jm8241982-desktop pulseaudio[5734]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 19 20:53:00 jm8241982-desktop pulseaudio[6121]: pid.c: Stale PID file, overwriting.
Aug 19 20:53:00 jm8241982-desktop pulseaudio[6121]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 19 20:54:56 jm8241982-desktop dhcdbd: Started up.
Aug 19 20:54:58 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 19 20:55:01 jm8241982-desktop python: hp-makeuri[5363]: error: Device does not support fax.
Aug 19 20:55:04 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Aug 19 20:55:04 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Aug 19 20:55:04 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Aug 19 20:55:04 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Aug 19 20:55:41 jm8241982-desktop pulseaudio[5666]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 20 13:30:20 jm8241982-desktop pulseaudio[14397]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 20 13:32:31 jm8241982-desktop dhcdbd: Started up.
Aug 20 13:32:34 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 20 13:32:35 jm8241982-desktop python: hp-makeuri[5312]: error: Device does not support fax.
Aug 20 13:32:37 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Aug 20 13:32:37 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Aug 20 13:32:37 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Aug 20 13:32:37 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Aug 20 13:32:58 jm8241982-desktop pulseaudio[5666]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 20 13:33:45 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 20 13:35:17 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 20 13:35:43 jm8241982-desktop last message repeated 2 times
Aug 20 18:06:49 jm8241982-desktop pulseaudio[7304]: pid.c: Stale PID file, overwriting.
Aug 20 18:06:49 jm8241982-desktop pulseaudio[7304]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 20 19:55:51 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 20 19:57:09 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 20 20:03:43 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 20 20:05:15 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 21 09:18:26 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 21 09:19:46 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 21 09:46:10 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 21 09:54:19 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 21 09:54:19 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 21 09:54:20 jm8241982-desktop hpijs: WARNING: color pen has low ink 
Aug 21 09:54:20 jm8241982-desktop hpijs: STATE: marker-supply-low-warning 
Aug 21 09:58:19 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 21 18:04:33 jm8241982-desktop dhcdbd: Started up.
Aug 21 18:04:35 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 21 18:04:37 jm8241982-desktop python: hp-makeuri[5440]: error: Device does not support fax.
Aug 21 18:04:39 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Aug 21 18:04:39 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Aug 21 18:04:39 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Aug 21 18:04:39 jm8241982-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Aug 21 18:05:02 jm8241982-desktop pulseaudio[5767]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 21 18:07:07 jm8241982-desktop pulseaudio[5767]: module-hal-detect.c: Error getting capability: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/volume_part1_size_1036353024
Aug 21 18:11:09 jm8241982-desktop pulseaudio[5767]: module-hal-detect.c: Error getting capability: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/volume_uuid_48AE_041D
Aug 22 12:06:57 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Aug 22 12:06:58 jm8241982-desktop hpijs: WARNING: color pen has low ink 
Aug 22 12:06:58 jm8241982-desktop hpijs: STATE: marker-supply-low-warning 
Aug 22 12:08:25 jm8241982-desktop deskjet_3500?serial=TH433140RV7O: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 

my debug

Aug 18 21:04:28 jm8241982-desktop hal_lpadmin: add
Aug 18 21:04:29 jm8241982-desktop hal_lpadmin: URIs: ['hp:/usb/deskjet_3500?serial=TH433140RV7O', 'usb://hp/deskjet%203500?serial=TH433140RV7O', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O']
Aug 18 21:04:29 jm8241982-desktop hal_lpadmin: HPLIP Fax URIs: None
Aug 18 21:04:29 jm8241982-desktop hal_lpadmin: Not adding printer: deskjet_3500 already exists
Aug 18 21:04:29 jm8241982-desktop NetworkManager: <debug> [1219115069.434601] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 18 22:01:09 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582764] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.582788] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969349] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 18 22:01:09 jm8241982-desktop kernel: [   21.969371] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137052] CPU0 attaching sched-domain:
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137055]  domain 0: span 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137058]   groups: 01 02
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137061]   domain 1: span 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137063]    groups: 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137065] CPU1 attaching sched-domain:
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137067]  domain 0: span 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137069]   groups: 02 01
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137072]   domain 1: span 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.137073]    groups: 03
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.153170] ACPI: EC: Look up EC in DSDT
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.166214] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.303153] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.802824] Switched to high resolution mode on CPU 0
Aug 18 22:01:09 jm8241982-desktop kernel: [   22.802954] Switched to high resolution mode on CPU 1
Aug 18 22:01:09 jm8241982-desktop kernel: [   30.878273] Boot video device is 0000:01:00.0
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.911268] libata version 3.00 loaded.
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.932089] sata_via 0000:00:0f.0: version 2.3
Aug 18 22:01:09 jm8241982-desktop kernel: [   32.932485] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.554977] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.657914] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.761612] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.865270] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.970099] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   33.971256] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.124591] pata_via 0000:00:0f.1: version 0.3.3
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.124698] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.817817] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852817] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.852961] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 18 22:01:09 jm8241982-desktop kernel: [   34.898489] sr 2:0:0:0: Attached scsi CD-ROM sr0
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.178695] swsusp: Resume From Partition 8:5
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.178697] PM: Checking swsusp image.
Aug 18 22:01:09 jm8241982-desktop kernel: [   35.178872] PM: Resume from disk failed.
Aug 18 22:01:09 jm8241982-desktop kernel: [   44.837433] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.033196] usb-storage: device found at 5
Aug 18 22:01:09 jm8241982-desktop kernel: [   45.033199] usb-storage: waiting for device to settle before scanning
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.016147] usb-storage: device scan complete
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.025886] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 18 22:01:09 jm8241982-desktop kernel: [   50.028204] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 18 22:01:11 jm8241982-desktop NetworkManager: <debug> [1219118471.585545] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7191A'). 
Aug 18 22:01:11 jm8241982-desktop audio[5156]: audio.conf: Key file does not have key 'Enable'
Aug 18 22:01:11 jm8241982-desktop audio[5156]: audio.conf: Key file does not have key 'Disable'
Aug 18 22:01:11 jm8241982-desktop audio[5156]: add_service_record: got record id 0x10000
Aug 18 22:01:11 jm8241982-desktop audio[5156]: audio.conf: Key file does not have key 'Disable'
Aug 18 22:01:11 jm8241982-desktop audio[5156]: audio.conf: Key file does not have group 'A2DP'
Aug 18 22:01:11 jm8241982-desktop last message repeated 3 times
Aug 18 22:01:11 jm8241982-desktop audio[5156]: SEP 0x806d5e0 registered: type:0 codec:0 seid:1
Aug 18 22:01:11 jm8241982-desktop audio[5156]: add_service_record: got record id 0x10001
Aug 18 22:01:11 jm8241982-desktop audio[5156]: add_service_record: got record id 0x10002
Aug 18 22:01:11 jm8241982-desktop audio[5156]: add_service_record: got record id 0x10003
Aug 18 22:01:12 jm8241982-desktop NetworkManager: <debug> [1219118472.584383] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 18 22:01:12 jm8241982-desktop hal_lpadmin: add
Aug 18 22:01:13 jm8241982-desktop hal_lpadmin: URIs: ['hp:/usb/deskjet_3500?serial=TH433140RV7O', 'usb://hp/deskjet%203500?serial=TH433140RV7O', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O']
Aug 18 22:01:13 jm8241982-desktop hal_lpadmin: HPLIP Fax URIs: None
Aug 18 22:01:13 jm8241982-desktop hal_lpadmin: Not adding printer: deskjet_3500 already exists
Aug 18 22:01:13 jm8241982-desktop NetworkManager: <debug> [1219118473.863819] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 18 22:01:28 jm8241982-desktop kernel: [   68.272354] eth1: no IPv6 routers present
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 18 22:45:51 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860940] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 18 22:45:51 jm8241982-desktop kernel: [   20.860965] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251513] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.251534] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419218] CPU0 attaching sched-domain:
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419221]  domain 0: span 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419224]   groups: 01 02
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419227]   domain 1: span 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419229]    groups: 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419231] CPU1 attaching sched-domain:
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419233]  domain 0: span 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419235]   groups: 02 01
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419238]   domain 1: span 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.419240]    groups: 03
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.436120] ACPI: EC: Look up EC in DSDT
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.449168] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 18 22:45:51 jm8241982-desktop kernel: [   21.585312] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.084991] Switched to high resolution mode on CPU 0
Aug 18 22:45:51 jm8241982-desktop kernel: [   22.085119] Switched to high resolution mode on CPU 1
Aug 18 22:45:51 jm8241982-desktop kernel: [   30.159639] Boot video device is 0000:01:00.0
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.064187] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.209621] libata version 3.00 loaded.
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.237341] sata_via 0000:00:0f.0: version 2.3
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.237738] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.856152] pata_via 0000:00:0f.1: version 0.3.3
Aug 18 22:45:51 jm8241982-desktop kernel: [   32.856253] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.545213] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.648807] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.752455] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.856159] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   33.959965] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.123843] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150625] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.150776] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.197683] sr 2:0:0:0: Attached scsi CD-ROM sr0
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.453237] swsusp: Resume From Partition 8:5
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.453239] PM: Checking swsusp image.
Aug 18 22:45:51 jm8241982-desktop kernel: [   34.453413] PM: Resume from disk failed.
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.696520] usb-storage: device found at 5
Aug 18 22:45:51 jm8241982-desktop kernel: [   43.696523] usb-storage: waiting for device to settle before scanning
Aug 18 22:45:51 jm8241982-desktop kernel: [   44.033114] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   44.693302] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.679619] usb-storage: device scan complete
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.682613] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 18 22:45:51 jm8241982-desktop kernel: [   48.684466] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 18 22:45:53 jm8241982-desktop NetworkManager: <debug> [1219121153.072368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7191A'). 
Aug 18 22:45:53 jm8241982-desktop audio[5167]: audio.conf: Key file does not have key 'Enable'
Aug 18 22:45:53 jm8241982-desktop audio[5167]: audio.conf: Key file does not have key 'Disable'
Aug 18 22:45:53 jm8241982-desktop audio[5167]: add_service_record: got record id 0x10000
Aug 18 22:45:53 jm8241982-desktop audio[5167]: audio.conf: Key file does not have key 'Disable'
Aug 18 22:45:53 jm8241982-desktop audio[5167]: audio.conf: Key file does not have group 'A2DP'
Aug 18 22:45:53 jm8241982-desktop last message repeated 3 times
Aug 18 22:45:53 jm8241982-desktop audio[5167]: SEP 0x806d5e0 registered: type:0 codec:0 seid:1
Aug 18 22:45:53 jm8241982-desktop audio[5167]: add_service_record: got record id 0x10001
Aug 18 22:45:53 jm8241982-desktop audio[5167]: add_service_record: got record id 0x10002
Aug 18 22:45:53 jm8241982-desktop audio[5167]: add_service_record: got record id 0x10003
Aug 18 22:45:54 jm8241982-desktop NetworkManager: <debug> [1219121154.071877] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 18 22:45:54 jm8241982-desktop hal_lpadmin: add
Aug 18 22:45:55 jm8241982-desktop hal_lpadmin: URIs: ['hp:/usb/deskjet_3500?serial=TH433140RV7O', 'usb://hp/deskjet%203500?serial=TH433140RV7O', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O']
Aug 18 22:45:55 jm8241982-desktop hal_lpadmin: HPLIP Fax URIs: None
Aug 18 22:45:55 jm8241982-desktop hal_lpadmin: Not adding printer: deskjet_3500 already exists
Aug 18 22:45:55 jm8241982-desktop NetworkManager: <debug> [1219121155.991962] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 18 22:46:11 jm8241982-desktop kernel: [   69.519997] eth1: no IPv6 routers present
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 19 05:59:01 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258222] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.258246] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.644803] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.644825] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812514] CPU0 attaching sched-domain:
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812518]  domain 0: span 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812520]   groups: 01 02
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812523]   domain 1: span 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812525]    groups: 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812528] CPU1 attaching sched-domain:
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812529]  domain 0: span 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812531]   groups: 02 01
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812534]   domain 1: span 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.812536]    groups: 03
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.828640] ACPI: EC: Look up EC in DSDT
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.841712] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 19 05:59:01 jm8241982-desktop kernel: [   17.978613] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.478282] Switched to high resolution mode on CPU 0
Aug 19 05:59:01 jm8241982-desktop kernel: [   18.478415] Switched to high resolution mode on CPU 1
Aug 19 05:59:01 jm8241982-desktop kernel: [   26.553902] Boot video device is 0000:01:00.0
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.705562] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.871755] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.973996] libata version 3.00 loaded.
Aug 19 05:59:01 jm8241982-desktop kernel: [   28.978705] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.082323] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.186008] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.290268] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.291492] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.446360] sata_via 0000:00:0f.0: version 2.3
Aug 19 05:59:01 jm8241982-desktop kernel: [   29.446786] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.070049] pata_via 0000:00:0f.1: version 0.3.3
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.070145] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776738] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.776894] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 05:59:01 jm8241982-desktop kernel: [   30.816253] sr 2:0:0:0: Attached scsi CD-ROM sr0
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.051740] swsusp: Resume From Partition 8:5
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.051742] PM: Checking swsusp image.
Aug 19 05:59:01 jm8241982-desktop kernel: [   31.051916] PM: Resume from disk failed.
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.281700] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.660559] usb-storage: device found at 5
Aug 19 05:59:01 jm8241982-desktop kernel: [   40.660561] usb-storage: waiting for device to settle before scanning
Aug 19 05:59:01 jm8241982-desktop kernel: [   41.115075] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.645314] usb-storage: device scan complete
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.652918] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 05:59:01 jm8241982-desktop kernel: [   45.654758] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 05:59:03 jm8241982-desktop NetworkManager: <debug> [1219147143.240505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7191A'). 
Aug 19 05:59:03 jm8241982-desktop audio[5181]: audio.conf: Key file does not have key 'Enable'
Aug 19 05:59:03 jm8241982-desktop audio[5181]: audio.conf: Key file does not have key 'Disable'
Aug 19 05:59:03 jm8241982-desktop audio[5181]: add_service_record: got record id 0x10000
Aug 19 05:59:03 jm8241982-desktop audio[5181]: audio.conf: Key file does not have key 'Disable'
Aug 19 05:59:03 jm8241982-desktop audio[5181]: audio.conf: Key file does not have group 'A2DP'
Aug 19 05:59:03 jm8241982-desktop last message repeated 3 times
Aug 19 05:59:03 jm8241982-desktop audio[5181]: SEP 0x806d5e0 registered: type:0 codec:0 seid:1
Aug 19 05:59:03 jm8241982-desktop audio[5181]: add_service_record: got record id 0x10001
Aug 19 05:59:03 jm8241982-desktop audio[5181]: add_service_record: got record id 0x10002
Aug 19 05:59:03 jm8241982-desktop audio[5181]: add_service_record: got record id 0x10003
Aug 19 05:59:04 jm8241982-desktop NetworkManager: <debug> [1219147144.241358] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 19 05:59:04 jm8241982-desktop hal_lpadmin: add
Aug 19 05:59:06 jm8241982-desktop hal_lpadmin: URIs: ['hp:/usb/deskjet_3500?serial=TH433140RV7O', 'usb://hp/deskjet%203500?serial=TH433140RV7O', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O']
Aug 19 05:59:06 jm8241982-desktop hal_lpadmin: HPLIP Fax URIs: None
Aug 19 05:59:06 jm8241982-desktop hal_lpadmin: Not adding printer: deskjet_3500 already exists
Aug 19 05:59:06 jm8241982-desktop NetworkManager: <debug> [1219147146.335551] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 19 05:59:21 jm8241982-desktop kernel: [   65.635118] eth1: no IPv6 routers present
Aug 19 12:50:02 jm8241982-desktop NetworkManager: <debug> [1219171802.682954] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_656666624'). 
Aug 19 14:06:15 jm8241982-desktop NetworkManager: <debug> [1219176375.485671] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_656666624'). 
Aug 19 16:35:09 jm8241982-desktop NetworkManager: <debug> [1219185309.571381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_501147648'). 
Aug 19 16:45:07 jm8241982-desktop NetworkManager: <debug> [1219185907.601598] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_501147648'). 
Aug 19 16:46:53 jm8241982-desktop NetworkManager: <debug> [1219186013.594918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_434728960'). 
Aug 19 16:52:15 jm8241982-desktop NetworkManager: <debug> [1219186335.444958] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_434728960'). 
Aug 19 16:52:32 jm8241982-desktop NetworkManager: <debug> [1219186352.536590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_434728960'). 
Aug 19 16:54:01 jm8241982-desktop NetworkManager: <debug> [1219186441.788135] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_434728960'). 
Aug 19 16:54:22 jm8241982-desktop NetworkManager: <debug> [1219186462.614686] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_434728960'). 
Aug 19 16:55:29 jm8241982-desktop NetworkManager: <debug> [1219186529.666527] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_434728960'). 
Aug 19 16:56:52 jm8241982-desktop NetworkManager: <debug> [1219186612.567282] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_522059776'). 
Aug 19 17:02:49 jm8241982-desktop NetworkManager: <debug> [1219186969.249917] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_522059776'). 
Aug 19 17:03:49 jm8241982-desktop NetworkManager: <debug> [1219187029.614121] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_535203840'). 
Aug 19 17:14:29 jm8241982-desktop NetworkManager: <debug> [1219187669.075016] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_535203840'). 
Aug 19 17:23:24 jm8241982-desktop NetworkManager: <debug> [1219188204.539494] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_547905536'). 
Aug 19 17:33:35 jm8241982-desktop NetworkManager: <debug> [1219188815.939681] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_547905536'). 
Aug 19 17:36:59 jm8241982-desktop NetworkManager: <debug> [1219189019.547114] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_520022016'). 
Aug 19 18:01:00 jm8241982-desktop NetworkManager: <debug> [1219190460.905319] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_520022016'). 
Aug 19 18:36:05 jm8241982-desktop NetworkManager: <debug> [1219192565.411314] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_342988800'). 
Aug 19 18:40:59 jm8241982-desktop NetworkManager: <debug> [1219192859.695829] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_342988800'). 
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 19 20:48:51 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628246] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 20:48:51 jm8241982-desktop kernel: [   15.628270] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.014829] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.014849] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182534] CPU0 attaching sched-domain:
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182538]  domain 0: span 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182540]   groups: 01 02
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182543]   domain 1: span 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182545]    groups: 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182548] CPU1 attaching sched-domain:
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182549]  domain 0: span 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182551]   groups: 02 01
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182554]   domain 1: span 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.182556]    groups: 03
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.199442] ACPI: EC: Look up EC in DSDT
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.212476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.348626] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.848308] Switched to high resolution mode on CPU 0
Aug 19 20:48:51 jm8241982-desktop kernel: [   16.848436] Switched to high resolution mode on CPU 1
Aug 19 20:48:51 jm8241982-desktop kernel: [   24.923878] Boot video device is 0000:01:00.0
Aug 19 20:48:51 jm8241982-desktop kernel: [   26.908891] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.223526] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.225442] libata version 3.00 loaded.
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.226767] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.329764] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.433499] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.537143] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.640840] pata_via 0000:00:0f.1: version 0.3.3
Aug 19 20:48:51 jm8241982-desktop kernel: [   27.641277] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333303] sata_via 0000:00:0f.0: version 2.3
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.333398] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   28.928591] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.066973] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.067104] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 20:48:51 jm8241982-desktop kernel: [   29.076029] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.075028] usb-storage: device found at 5
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.075032] usb-storage: waiting for device to settle before scanning
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.118469] swsusp: Resume From Partition 8:5
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.118471] PM: Checking swsusp image.
Aug 19 20:48:51 jm8241982-desktop kernel: [   32.118646] PM: Resume from disk failed.
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.060288] usb-storage: device scan complete
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.063498] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 20:48:51 jm8241982-desktop kernel: [   37.065359] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 20:48:51 jm8241982-desktop kernel: [   42.107651] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 19 20:48:51 jm8241982-desktop kernel: [   42.281410] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 19 20:48:53 jm8241982-desktop NetworkManager: <debug> [1219200533.755034] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7191A'). 
Aug 19 20:48:53 jm8241982-desktop audio[5301]: audio.conf: Key file does not have key 'Enable'
Aug 19 20:48:53 jm8241982-desktop audio[5301]: audio.conf: Key file does not have key 'Disable'
Aug 19 20:48:53 jm8241982-desktop audio[5301]: add_service_record: got record id 0x10000
Aug 19 20:48:53 jm8241982-desktop audio[5301]: audio.conf: Key file does not have key 'Disable'
Aug 19 20:48:53 jm8241982-desktop audio[5301]: audio.conf: Key file does not have group 'A2DP'
Aug 19 20:48:53 jm8241982-desktop last message repeated 3 times
Aug 19 20:48:53 jm8241982-desktop audio[5301]: SEP 0x806d5e0 registered: type:0 codec:0 seid:1
Aug 19 20:48:53 jm8241982-desktop audio[5301]: add_service_record: got record id 0x10001
Aug 19 20:48:53 jm8241982-desktop audio[5301]: add_service_record: got record id 0x10002
Aug 19 20:48:53 jm8241982-desktop audio[5301]: add_service_record: got record id 0x10003
Aug 19 20:48:54 jm8241982-desktop NetworkManager: <debug> [1219200534.757869] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 19 20:48:54 jm8241982-desktop hal_lpadmin: add
Aug 19 20:48:56 jm8241982-desktop hal_lpadmin: URIs: ['hp:/usb/deskjet_3500?serial=TH433140RV7O', 'usb://hp/deskjet%203500?serial=TH433140RV7O', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O']
Aug 19 20:48:56 jm8241982-desktop hal_lpadmin: HPLIP Fax URIs: None
Aug 19 20:48:56 jm8241982-desktop hal_lpadmin: Not adding printer: deskjet_3500 already exists
Aug 19 20:48:56 jm8241982-desktop NetworkManager: <debug> [1219200536.897681] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 19 20:49:15 jm8241982-desktop kernel: [   66.800921] eth1: no IPv6 routers present
Aug 19 20:53:10 jm8241982-desktop NetworkManager: <debug> [1219200790.385410] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_222251409655_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 19 20:53:10 jm8241982-desktop NetworkManager: <debug> [1219200790.479015] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48974553329CC95E'). 
Aug 19 20:53:10 jm8241982-desktop NetworkManager: <debug> [1219200790.483375] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_ST310003_40NS_222251409655_0_0'). 
Aug 19 20:53:10 jm8241982-desktop NetworkManager: <debug> [1219200790.486645] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_222251409655_if0_scsi_host_scsi_device_lun0'). 
Aug 19 20:53:10 jm8241982-desktop NetworkManager: <debug> [1219200790.489666] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_222251409655_if0_scsi_host'). 
Aug 19 20:53:10 jm8241982-desktop NetworkManager: <debug> [1219200790.493002] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_222251409655_if0'). 
Aug 19 20:53:10 jm8241982-desktop NetworkManager: <debug> [1219200790.496702] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_222251409655'). 
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 19 20:54:55 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411730] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.411754] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802299] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.802320] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970005] CPU0 attaching sched-domain:
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970008]  domain 0: span 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970010]   groups: 01 02
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970014]   domain 1: span 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970015]    groups: 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970018] CPU1 attaching sched-domain:
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970019]  domain 0: span 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970021]   groups: 02 01
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970024]   domain 1: span 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.970026]    groups: 03
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.986123] ACPI: EC: Look up EC in DSDT
Aug 19 20:54:55 jm8241982-desktop kernel: [   15.999190] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.116156] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.615837] Switched to high resolution mode on CPU 0
Aug 19 20:54:55 jm8241982-desktop kernel: [   16.615966] Switched to high resolution mode on CPU 1
Aug 19 20:54:55 jm8241982-desktop kernel: [   24.690427] Boot video device is 0000:01:00.0
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.958552] libata version 3.00 loaded.
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.961259] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.987972] pata_via 0000:00:0f.1: version 0.3.3
Aug 19 20:54:55 jm8241982-desktop kernel: [   26.988438] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.685222] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.788831] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.896436] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   27.996114] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.101072] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.102737] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255318] sata_via 0000:00:0f.0: version 2.3
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.255430] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.863919] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864234] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 20:54:55 jm8241982-desktop kernel: [   28.864376] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.129037] swsusp: Resume From Partition 8:5
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.129039] PM: Checking swsusp image.
Aug 19 20:54:55 jm8241982-desktop kernel: [   29.129214] PM: Resume from disk failed.
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.483113] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.714093] usb-storage: device found at 5
Aug 19 20:54:55 jm8241982-desktop kernel: [   38.714097] usb-storage: waiting for device to settle before scanning
Aug 19 20:54:55 jm8241982-desktop kernel: [   39.116640] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.699614] usb-storage: device scan complete
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.714646] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 20:54:55 jm8241982-desktop kernel: [   43.716461] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 19 20:54:57 jm8241982-desktop NetworkManager: <debug> [1219200897.949520] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7191A'). 
Aug 19 20:54:58 jm8241982-desktop audio[5214]: audio.conf: Key file does not have key 'Enable'
Aug 19 20:54:58 jm8241982-desktop audio[5214]: audio.conf: Key file does not have key 'Disable'
Aug 19 20:54:58 jm8241982-desktop audio[5214]: add_service_record: got record id 0x10000
Aug 19 20:54:58 jm8241982-desktop audio[5214]: audio.conf: Key file does not have key 'Disable'
Aug 19 20:54:58 jm8241982-desktop audio[5214]: audio.conf: Key file does not have group 'A2DP'
Aug 19 20:54:58 jm8241982-desktop last message repeated 3 times
Aug 19 20:54:58 jm8241982-desktop audio[5214]: SEP 0x806d5e0 registered: type:0 codec:0 seid:1
Aug 19 20:54:58 jm8241982-desktop audio[5214]: add_service_record: got record id 0x10001
Aug 19 20:54:58 jm8241982-desktop audio[5214]: add_service_record: got record id 0x10002
Aug 19 20:54:58 jm8241982-desktop audio[5214]: add_service_record: got record id 0x10003
Aug 19 20:54:58 jm8241982-desktop NetworkManager: <debug> [1219200898.950672] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 19 20:54:59 jm8241982-desktop hal_lpadmin: add
Aug 19 20:55:01 jm8241982-desktop hal_lpadmin: URIs: ['hp:/usb/deskjet_3500?serial=TH433140RV7O', 'usb://hp/deskjet%203500?serial=TH433140RV7O', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O']
Aug 19 20:55:01 jm8241982-desktop hal_lpadmin: HPLIP Fax URIs: None
Aug 19 20:55:01 jm8241982-desktop hal_lpadmin: Not adding printer: deskjet_3500 already exists
Aug 19 20:55:01 jm8241982-desktop NetworkManager: <debug> [1219200901.267689] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 19 20:55:16 jm8241982-desktop kernel: [   64.600013] eth1: no IPv6 routers present
Aug 20 08:03:21 jm8241982-desktop NetworkManager: <debug> [1219241001.373166] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_365725696'). 
Aug 20 08:07:55 jm8241982-desktop NetworkManager: <debug> [1219241275.479304] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_365725696'). 
Aug 20 08:09:22 jm8241982-desktop NetworkManager: <debug> [1219241362.783964] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_727564288'). 
Aug 20 08:17:25 jm8241982-desktop NetworkManager: <debug> [1219241845.350033] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_727564288'). 
Aug 20 08:19:48 jm8241982-desktop NetworkManager: <debug> [1219241988.447702] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_423397376'). 
Aug 20 08:25:05 jm8241982-desktop NetworkManager: <debug> [1219242305.947491] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_423397376'). 
Aug 20 08:29:38 jm8241982-desktop NetworkManager: <debug> [1219242578.503416] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_504215552'). 
Aug 20 08:35:38 jm8241982-desktop NetworkManager: <debug> [1219242938.548368] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_504215552'). 
Aug 20 08:36:19 jm8241982-desktop NetworkManager: <debug> [1219242979.500171] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_575887360'). 
Aug 20 13:25:17 jm8241982-desktop NetworkManager: <debug> [1219260317.240872] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_575887360'). 
Aug 20 13:26:23 jm8241982-desktop NetworkManager: <debug> [1219260383.517261] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_428763136'). 
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 20 13:32:30 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616104] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 20 13:32:30 jm8241982-desktop kernel: [   22.616128] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.002691] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.002712] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170392] CPU0 attaching sched-domain:
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170395]  domain 0: span 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170397]   groups: 01 02
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170401]   domain 1: span 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170402]    groups: 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170405] CPU1 attaching sched-domain:
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170407]  domain 0: span 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170408]   groups: 02 01
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170411]   domain 1: span 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.170413]    groups: 03
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.187294] ACPI: EC: Look up EC in DSDT
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.200351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.316414] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.812375] Switched to high resolution mode on CPU 1
Aug 20 13:32:30 jm8241982-desktop kernel: [   23.816216] Switched to high resolution mode on CPU 0
Aug 20 13:32:30 jm8241982-desktop kernel: [   31.891279] Boot video device is 0000:01:00.0
Aug 20 13:32:30 jm8241982-desktop kernel: [   33.989184] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.124386] libata version 3.00 loaded.
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.164512] pata_via 0000:00:0f.1: version 0.3.3
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.164903] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.877461] sata_via 0000:00:0f.0: version 2.3
Aug 20 13:32:30 jm8241982-desktop kernel: [   34.877574] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.465391] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.568033] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.671718] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.775363] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   35.879211] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.036068] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062227] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.062414] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.072506] sr 0:0:0:0: Attached scsi CD-ROM sr0
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.363342] swsusp: Resume From Partition 8:5
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.363344] PM: Checking swsusp image.
Aug 20 13:32:30 jm8241982-desktop kernel: [   36.363510] PM: Resume from disk failed.
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.863629] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.868267] usb-storage: device found at 5
Aug 20 13:32:30 jm8241982-desktop kernel: [   45.868270] usb-storage: waiting for device to settle before scanning
Aug 20 13:32:30 jm8241982-desktop kernel: [   46.533265] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.852825] usb-storage: device scan complete
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.861525] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 20 13:32:30 jm8241982-desktop kernel: [   50.863395] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 20 13:32:33 jm8241982-desktop audio[5213]: audio.conf: Key file does not have key 'Enable'
Aug 20 13:32:33 jm8241982-desktop audio[5213]: audio.conf: Key file does not have key 'Disable'
Aug 20 13:32:33 jm8241982-desktop audio[5213]: add_service_record: got record id 0x10000
Aug 20 13:32:33 jm8241982-desktop audio[5213]: audio.conf: Key file does not have key 'Disable'
Aug 20 13:32:33 jm8241982-desktop audio[5213]: audio.conf: Key file does not have group 'A2DP'
Aug 20 13:32:33 jm8241982-desktop last message repeated 3 times
Aug 20 13:32:33 jm8241982-desktop audio[5213]: SEP 0x806d5e0 registered: type:0 codec:0 seid:1
Aug 20 13:32:33 jm8241982-desktop audio[5213]: add_service_record: got record id 0x10001
Aug 20 13:32:33 jm8241982-desktop audio[5213]: add_service_record: got record id 0x10002
Aug 20 13:32:33 jm8241982-desktop audio[5213]: add_service_record: got record id 0x10003
Aug 20 13:32:34 jm8241982-desktop hal_lpadmin: add
Aug 20 13:32:34 jm8241982-desktop NetworkManager: <debug> [1219260754.355455] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 20 13:32:34 jm8241982-desktop hal_lpadmin: URIs: ['hp:/usb/deskjet_3500?serial=TH433140RV7O', 'usb://hp/deskjet%203500?serial=TH433140RV7O', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O']
Aug 20 13:32:35 jm8241982-desktop hal_lpadmin: HPLIP Fax URIs: None
Aug 20 13:32:35 jm8241982-desktop hal_lpadmin: Not adding printer: deskjet_3520 already exists
Aug 20 13:32:35 jm8241982-desktop NetworkManager: <debug> [1219260755.071963] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 20 13:32:47 jm8241982-desktop kernel: [   69.184955] eth1: no IPv6 routers present
Aug 20 13:33:46 jm8241982-desktop hal_lpadmin: remove
Aug 20 13:33:46 jm8241982-desktop hal_lpadmin: Found configured printer: deskjet_3520
Aug 20 13:33:46 jm8241982-desktop NetworkManager: <debug> [1219260826.510719] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 20 19:14:09 jm8241982-desktop NetworkManager: <debug> [1219281249.422486] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_428763136'). 
Aug 21 17:42:08 jm8241982-desktop kernel: [101117.493818] usb-storage: device found at 6
Aug 21 17:42:08 jm8241982-desktop kernel: [101117.493826] usb-storage: waiting for device to settle before scanning
Aug 21 17:42:08 jm8241982-desktop NetworkManager: <debug> [1219362128.148194] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 17:42:08 jm8241982-desktop NetworkManager: <debug> [1219362128.271038] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 17:42:13 jm8241982-desktop kernel: [101122.476613] usb-storage: device scan complete
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.249669] sd 5:0:0:0: [sdc] Mode Sense: 3b 00 80 00
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.253521] sd 5:0:0:0: [sdc] Mode Sense: 3b 00 80 00
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.261376] sd 5:0:0:1: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:42:13 jm8241982-desktop kernel: [101123.265132] sd 5:0:0:1: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:42:14 jm8241982-desktop NetworkManager: <debug> [1219362134.039790] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 17:42:14 jm8241982-desktop NetworkManager: <debug> [1219362134.046131] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 17:42:14 jm8241982-desktop NetworkManager: <debug> [1219362134.058108] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 17:42:14 jm8241982-desktop NetworkManager: <debug> [1219362134.091866] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 17:42:14 jm8241982-desktop NetworkManager: <debug> [1219362134.100842] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 17:42:14 jm8241982-desktop NetworkManager: <debug> [1219362134.283693] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 17:42:14 jm8241982-desktop NetworkManager: <debug> [1219362134.359763] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 17:42:14 jm8241982-desktop NetworkManager: <debug> [1219362134.418068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:42:14 jm8241982-desktop NetworkManager: <debug> [1219362134.485384] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 17:46:25 jm8241982-desktop NetworkManager: <debug> [1219362385.021361] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:46:29 jm8241982-desktop NetworkManager: <debug> [1219362389.021059] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560768] sd 5:0:0:0: [sdc] Mode Sense: 00 00 00 00
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.560844] sd 5:0:0:1: [sdd] Mode Sense: 00 00 00 00
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561371] sd 5:0:0:0: [sdc] Mode Sense: 00 00 00 00
Aug 21 17:46:33 jm8241982-desktop kernel: [101381.561554] sd 5:0:0:1: [sdd] Mode Sense: 00 00 00 00
Aug 21 17:46:33 jm8241982-desktop NetworkManager: <debug> [1219362393.058341] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 17:46:33 jm8241982-desktop NetworkManager: <debug> [1219362393.063995] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 17:46:33 jm8241982-desktop NetworkManager: <debug> [1219362393.071636] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 17:46:33 jm8241982-desktop NetworkManager: <debug> [1219362393.071765] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 17:46:33 jm8241982-desktop NetworkManager: <debug> [1219362393.071823] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 17:46:33 jm8241982-desktop NetworkManager: <debug> [1219362393.071877] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 17:46:33 jm8241982-desktop NetworkManager: <debug> [1219362393.083765] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 17:46:33 jm8241982-desktop NetworkManager: <debug> [1219362393.090592] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 17:46:33 jm8241982-desktop NetworkManager: <debug> [1219362393.094803] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 17:47:04 jm8241982-desktop kernel: [101412.504344] usb-storage: device found at 7
Aug 21 17:47:04 jm8241982-desktop kernel: [101412.504348] usb-storage: waiting for device to settle before scanning
Aug 21 17:47:04 jm8241982-desktop NetworkManager: <debug> [1219362424.070334] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 17:47:04 jm8241982-desktop NetworkManager: <debug> [1219362424.153044] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 17:47:09 jm8241982-desktop kernel: [101417.488067] usb-storage: device scan complete
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.262144] sd 6:0:0:0: [sdc] Mode Sense: 3b 00 80 00
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.265493] sd 6:0:0:0: [sdc] Mode Sense: 3b 00 80 00
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.269874] sd 6:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 17:47:09 jm8241982-desktop kernel: [101418.273474] sd 6:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 17:47:09 jm8241982-desktop NetworkManager: <debug> [1219362429.956234] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 17:47:09 jm8241982-desktop NetworkManager: <debug> [1219362429.960625] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 17:47:09 jm8241982-desktop NetworkManager: <debug> [1219362429.999872] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 17:47:10 jm8241982-desktop NetworkManager: <debug> [1219362430.017242] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 17:47:10 jm8241982-desktop NetworkManager: <debug> [1219362430.021575] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 17:47:10 jm8241982-desktop NetworkManager: <debug> [1219362430.200603] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 17:47:10 jm8241982-desktop NetworkManager: <debug> [1219362430.263369] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 17:47:10 jm8241982-desktop NetworkManager: <debug> [1219362430.339552] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 17:47:10 jm8241982-desktop NetworkManager: <debug> [1219362430.417651] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.544075] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.590973] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.591099] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.591154] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.591201] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.591253] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.591304] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.591351] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.591398] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.599663] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 17:49:33 jm8241982-desktop NetworkManager: <debug> [1219362573.599852] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 17:49:58 jm8241982-desktop kernel: [101586.296779] usb-storage: device found at 8
Aug 21 17:49:58 jm8241982-desktop kernel: [101586.296785] usb-storage: waiting for device to settle before scanning
Aug 21 17:49:58 jm8241982-desktop NetworkManager: <debug> [1219362598.402392] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 17:49:58 jm8241982-desktop NetworkManager: <debug> [1219362598.482786] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 17:50:03 jm8241982-desktop kernel: [101591.278948] usb-storage: device scan complete
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.040921] sd 7:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.044529] sd 7:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.048282] sd 7:0:0:1: [sde] Mode Sense: 3b 00 00 00
Aug 21 17:50:04 jm8241982-desktop kernel: [101592.051649] sd 7:0:0:1: [sde] Mode Sense: 3b 00 00 00
Aug 21 17:50:04 jm8241982-desktop NetworkManager: <debug> [1219362604.290206] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host'). 
Aug 21 17:50:04 jm8241982-desktop NetworkManager: <debug> [1219362604.306167] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host_scsi_device_lun1'). 
Aug 21 17:50:04 jm8241982-desktop NetworkManager: <debug> [1219362604.310389] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host_scsi_device_lun0'). 
Aug 21 17:50:04 jm8241982-desktop NetworkManager: <debug> [1219362604.319139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 17:50:04 jm8241982-desktop NetworkManager: <debug> [1219362604.326736] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 17:50:04 jm8241982-desktop NetworkManager: <debug> [1219362604.529404] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 17:50:04 jm8241982-desktop NetworkManager: <debug> [1219362604.594417] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 17:50:04 jm8241982-desktop NetworkManager: <debug> [1219362604.651183] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:50:04 jm8241982-desktop NetworkManager: <debug> [1219362604.715760] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 17:51:52 jm8241982-desktop NetworkManager: <debug> [1219362712.760046] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Aug 21 17:52:00 jm8241982-desktop NetworkManager: <debug> [1219362720.314152] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:52:23 jm8241982-desktop NetworkManager: <debug> [1219362743.827363] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.439078] sd 7:0:0:0: [sdd] Mode Sense: 00 00 00 00
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.439124] sd 7:0:0:1: [sde] Mode Sense: 00 00 00 00
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.041307] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 17:52:37 jm8241982-desktop kernel: [101744.447350] sd 7:0:0:1: [sde] Mode Sense: 00 00 00 00
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.056745] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.130441] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.131482] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.144554] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host_scsi_device_lun0'). 
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.144657] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.144727] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.144778] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host_scsi_device_lun1'). 
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.144830] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.144883] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_scsi_host'). 
Aug 21 17:52:37 jm8241982-desktop NetworkManager: <debug> [1219362757.144935] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 17:52:51 jm8241982-desktop kernel: [101759.324971] usb-storage: device found at 9
Aug 21 17:52:51 jm8241982-desktop kernel: [101759.324978] usb-storage: waiting for device to settle before scanning
Aug 21 17:52:52 jm8241982-desktop NetworkManager: <debug> [1219362772.366989] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 17:52:52 jm8241982-desktop NetworkManager: <debug> [1219362772.391960] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 17:52:56 jm8241982-desktop kernel: [101764.308086] usb-storage: device scan complete
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.790315] sd 8:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:52:57 jm8241982-desktop kernel: [101764.793541] sd 8:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:52:57 jm8241982-desktop NetworkManager: <debug> [1219362777.578933] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 17:52:57 jm8241982-desktop NetworkManager: <debug> [1219362777.596789] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 17:52:57 jm8241982-desktop NetworkManager: <debug> [1219362777.601552] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 17:52:57 jm8241982-desktop NetworkManager: <debug> [1219362777.605947] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 17:52:57 jm8241982-desktop NetworkManager: <debug> [1219362777.609640] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 17:52:57 jm8241982-desktop NetworkManager: <debug> [1219362777.694845] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 17:52:57 jm8241982-desktop NetworkManager: <debug> [1219362777.764495] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 17:52:57 jm8241982-desktop NetworkManager: <debug> [1219362777.808094] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:53:25 jm8241982-desktop NetworkManager: <debug> [1219362805.238354] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 17:59:39 jm8241982-desktop NetworkManager: <debug> [1219363179.713646] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 17:59:39 jm8241982-desktop NetworkManager: <debug> [1219363179.722356] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 17:59:39 jm8241982-desktop NetworkManager: <debug> [1219363179.725956] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 17:59:39 jm8241982-desktop NetworkManager: <debug> [1219363179.732253] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 17:59:39 jm8241982-desktop NetworkManager: <debug> [1219363179.732377] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 17:59:39 jm8241982-desktop NetworkManager: <debug> [1219363179.732432] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 17:59:39 jm8241982-desktop NetworkManager: <debug> [1219363179.746002] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 17:59:39 jm8241982-desktop NetworkManager: <debug> [1219363179.754907] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 17:59:39 jm8241982-desktop NetworkManager: <debug> [1219363179.761737] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 17:59:47 jm8241982-desktop kernel: [102174.022743] usb-storage: device found at 10
Aug 21 17:59:47 jm8241982-desktop kernel: [102174.022749] usb-storage: waiting for device to settle before scanning
Aug 21 17:59:48 jm8241982-desktop NetworkManager: <debug> [1219363188.349666] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 17:59:48 jm8241982-desktop NetworkManager: <debug> [1219363188.372456] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 17:59:52 jm8241982-desktop kernel: [102179.006311] usb-storage: device scan complete
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.766426] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.769655] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 80 00
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.773445] sd 9:0:0:1: [sde] Mode Sense: 3b 00 00 00
Aug 21 17:59:53 jm8241982-desktop kernel: [102179.776638] sd 9:0:0:1: [sde] Mode Sense: 3b 00 00 00
Aug 21 17:59:53 jm8241982-desktop NetworkManager: <debug> [1219363193.828517] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 17:59:53 jm8241982-desktop NetworkManager: <debug> [1219363193.848310] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 17:59:53 jm8241982-desktop NetworkManager: <debug> [1219363193.857497] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 17:59:53 jm8241982-desktop NetworkManager: <debug> [1219363193.864941] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 17:59:53 jm8241982-desktop NetworkManager: <debug> [1219363193.870969] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 17:59:54 jm8241982-desktop NetworkManager: <debug> [1219363194.048245] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 17:59:54 jm8241982-desktop NetworkManager: <debug> [1219363194.101546] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 17:59:54 jm8241982-desktop NetworkManager: <debug> [1219363194.158728] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 17:59:54 jm8241982-desktop NetworkManager: <debug> [1219363194.218344] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 18:00:04 jm8241982-desktop kernel: [102190.046083] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:00:06 jm8241982-desktop kernel: [102192.039958] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:00:32 jm8241982-desktop kernel: [102218.527245] sd 9:0:0:0: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:00:32 jm8241982-desktop NetworkManager: <debug> [1219363232.615492] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 18:00:33 jm8241982-desktop NetworkManager: <debug> [1219363233.137844] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524016) 0 entries of 256 used
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] On node 0 totalpages: 524016
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   HighMem zone: 292339 pages, LIFO batch:31
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 21 18:04:31 jm8241982-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890352] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 21 18:04:31 jm8241982-desktop kernel: [   21.890377] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.280923] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.280944] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448627] CPU0 attaching sched-domain:
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448631]  domain 0: span 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448633]   groups: 01 02
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448636]   domain 1: span 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448638]    groups: 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448641] CPU1 attaching sched-domain:
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448642]  domain 0: span 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448644]   groups: 02 01
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448647]   domain 1: span 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.448649]    groups: 03
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.464738] ACPI: EC: Look up EC in DSDT
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.477812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 21 18:04:31 jm8241982-desktop kernel: [   22.614728] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.114400] Switched to high resolution mode on CPU 0
Aug 21 18:04:31 jm8241982-desktop kernel: [   23.114529] Switched to high resolution mode on CPU 1
Aug 21 18:04:31 jm8241982-desktop kernel: [   31.189645] Boot video device is 0000:01:00.0
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.058793] PCI: Setting latency timer of device 0000:00:05.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.227354] libata version 3.00 loaded.
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.237524] sata_via 0000:00:0f.0: version 2.3
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.237990] PCI: Setting latency timer of device 0000:00:0f.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.838547] pata_via 0000:00:0f.1: version 0.3.3
Aug 21 18:04:31 jm8241982-desktop kernel: [   33.838643] PCI: Setting latency timer of device 0000:00:0f.1 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.527998] PCI: Setting latency timer of device 0000:00:10.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.635184] PCI: Setting latency timer of device 0000:00:10.1 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.734849] PCI: Setting latency timer of device 0000:00:10.2 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.838565] PCI: Setting latency timer of device 0000:00:10.3 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.943167] PCI: Setting latency timer of device 0000:00:12.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   34.944610] PCI: Setting latency timer of device 0000:00:10.4 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112373] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.112493] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.155895] sr 2:0:0:0: Attached scsi CD-ROM sr0
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.367763] swsusp: Resume From Partition 8:5
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.367764] PM: Checking swsusp image.
Aug 21 18:04:31 jm8241982-desktop kernel: [   35.367938] PM: Resume from disk failed.
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.011324] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.374658] PCI: Setting latency timer of device 0000:00:11.5 to 64
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.616599] usb-storage: device found at 5
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.616603] usb-storage: waiting for device to settle before scanning
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.621245] usb-storage: device found at 6
Aug 21 18:04:31 jm8241982-desktop kernel: [   45.621248] usb-storage: waiting for device to settle before scanning
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.599243] usb-storage: device scan complete
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.606821] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.608699] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
Aug 21 18:04:31 jm8241982-desktop kernel: [   50.615859] usb-storage: device scan complete
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.379424] sd 5:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.382885] sd 5:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.386892] sd 5:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:04:32 jm8241982-desktop kernel: [   51.390122] sd 5:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:04:34 jm8241982-desktop NetworkManager: <debug> [1219363474.934975] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7191A'). 
Aug 21 18:04:35 jm8241982-desktop audio[5282]: audio.conf: Key file does not have key 'Enable'
Aug 21 18:04:35 jm8241982-desktop audio[5282]: audio.conf: Key file does not have key 'Disable'
Aug 21 18:04:35 jm8241982-desktop audio[5282]: add_service_record: got record id 0x10000
Aug 21 18:04:35 jm8241982-desktop audio[5282]: audio.conf: Key file does not have key 'Disable'
Aug 21 18:04:35 jm8241982-desktop audio[5282]: audio.conf: Key file does not have group 'A2DP'
Aug 21 18:04:35 jm8241982-desktop last message repeated 3 times
Aug 21 18:04:35 jm8241982-desktop audio[5282]: SEP 0x806d5e0 registered: type:0 codec:0 seid:1
Aug 21 18:04:35 jm8241982-desktop audio[5282]: add_service_record: got record id 0x10001
Aug 21 18:04:35 jm8241982-desktop audio[5282]: add_service_record: got record id 0x10002
Aug 21 18:04:35 jm8241982-desktop audio[5282]: add_service_record: got record id 0x10003
Aug 21 18:04:35 jm8241982-desktop hal_lpadmin: add
Aug 21 18:04:35 jm8241982-desktop NetworkManager: <debug> [1219363475.937162] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 21 18:04:37 jm8241982-desktop hal_lpadmin: URIs: ['hp:/usb/deskjet_3500?serial=TH433140RV7O', 'usb://hp/deskjet%203500?serial=TH433140RV7O', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O']
Aug 21 18:04:37 jm8241982-desktop hal_lpadmin: HPLIP Fax URIs: None
Aug 21 18:04:37 jm8241982-desktop hal_lpadmin: Not adding printer: deskjet_3520 already exists
Aug 21 18:04:37 jm8241982-desktop NetworkManager: <debug> [1219363477.846693] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 21 18:04:56 jm8241982-desktop kernel: [   71.469981] eth1: no IPv6 routers present
Aug 21 18:06:08 jm8241982-desktop NetworkManager: <debug> [1219363568.852987] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Aug 21 18:06:38 jm8241982-desktop NetworkManager: <debug> [1219363598.722127] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 18:06:51 jm8241982-desktop NetworkManager: <debug> [1219363611.903298] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A421'). 
Aug 21 18:07:07 jm8241982-desktop NetworkManager: <debug> [1219363627.236538] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_1036353024'). 
Aug 21 18:07:07 jm8241982-desktop NetworkManager: <debug> [1219363627.244217] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_1036353024'). 
Aug 21 18:07:07 jm8241982-desktop NetworkManager: <debug> [1219363627.861402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_032B'). 
Aug 21 18:07:33 jm8241982-desktop NetworkManager: <debug> [1219363653.072242] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_032B'). 
Aug 21 18:07:33 jm8241982-desktop NetworkManager: <debug> [1219363653.407299] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_032B'). 
Aug 21 18:07:52 jm8241982-desktop NetworkManager: <debug> [1219363672.348765] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_032B'). 
Aug 21 18:08:05 jm8241982-desktop NetworkManager: <debug> [1219363685.565171] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_1036353024'). 
Aug 21 18:08:05 jm8241982-desktop NetworkManager: <debug> [1219363685.726042] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_1036353024'). 
Aug 21 18:08:06 jm8241982-desktop NetworkManager: <debug> [1219363686.028588] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_1036353024'). 
Aug 21 18:08:23 jm8241982-desktop NetworkManager: <debug> [1219363703.682952] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 18:08:23 jm8241982-desktop NetworkManager: <debug> [1219363703.780782] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48A0_A408'). 
Aug 21 18:08:24 jm8241982-desktop NetworkManager: <debug> [1219363704.170781] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_493484544'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.028227] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.028365] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_1036353024'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.028424] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.028482] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.028535] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.034765] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.036112] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.050445] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_493484544'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.050582] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.058808] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 18:08:45 jm8241982-desktop NetworkManager: <debug> [1219363725.064224] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 18:09:56 jm8241982-desktop kernel: [  370.571574] usb-storage: device found at 7
Aug 21 18:09:56 jm8241982-desktop kernel: [  370.571581] usb-storage: waiting for device to settle before scanning
Aug 21 18:09:56 jm8241982-desktop NetworkManager: <debug> [1219363796.872633] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 18:09:56 jm8241982-desktop NetworkManager: <debug> [1219363796.896193] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 18:10:01 jm8241982-desktop kernel: [  375.554020] usb-storage: device scan complete
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.136071] sd 6:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.139286] sd 6:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.143920] sd 6:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:10:02 jm8241982-desktop kernel: [  376.147535] sd 6:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:10:02 jm8241982-desktop NetworkManager: <debug> [1219363802.168599] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 18:10:02 jm8241982-desktop NetworkManager: <debug> [1219363802.170452] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 18:10:02 jm8241982-desktop NetworkManager: <debug> [1219363802.177689] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 18:10:02 jm8241982-desktop NetworkManager: <debug> [1219363802.205780] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 18:10:02 jm8241982-desktop NetworkManager: <debug> [1219363802.213875] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 18:10:02 jm8241982-desktop NetworkManager: <debug> [1219363802.293782] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 18:10:02 jm8241982-desktop NetworkManager: <debug> [1219363802.340392] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 18:10:02 jm8241982-desktop NetworkManager: <debug> [1219363802.390021] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_0365'). 
Aug 21 18:10:02 jm8241982-desktop NetworkManager: <debug> [1219363802.451916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3532_6536'). 
Aug 21 18:10:54 jm8241982-desktop NetworkManager: <debug> [1219363854.390090] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3532_6536'). 
Aug 21 18:11:09 jm8241982-desktop NetworkManager: <debug> [1219363869.724491] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_041D'). 
Aug 21 18:11:09 jm8241982-desktop NetworkManager: <debug> [1219363869.727629] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_041D'). 
Aug 21 18:11:09 jm8241982-desktop NetworkManager: <debug> [1219363869.758700] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_041D'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.476680] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.493361] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_0365'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.499872] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.500150] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.504965] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.505130] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.508014] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.508131] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_041D'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.511404] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.512057] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 18:11:45 jm8241982-desktop NetworkManager: <debug> [1219363905.522964] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 18:11:49 jm8241982-desktop kernel: [  482.857495] usb-storage: device found at 8
Aug 21 18:11:49 jm8241982-desktop kernel: [  482.857499] usb-storage: waiting for device to settle before scanning
Aug 21 18:11:49 jm8241982-desktop NetworkManager: <debug> [1219363909.499233] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058'). 
Aug 21 18:11:49 jm8241982-desktop NetworkManager: <debug> [1219363909.523353] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0'). 
Aug 21 18:11:54 jm8241982-desktop kernel: [  487.841456] usb-storage: device scan complete
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.423780] sd 7:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.428732] sd 7:0:0:0: [sdc] Mode Sense: 3b 00 00 00
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.432725] sd 7:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:11:54 jm8241982-desktop kernel: [  488.436329] sd 7:0:0:1: [sdd] Mode Sense: 3b 00 00 00
Aug 21 18:11:54 jm8241982-desktop NetworkManager: <debug> [1219363914.804285] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host'). 
Aug 21 18:11:54 jm8241982-desktop NetworkManager: <debug> [1219363914.806879] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0'). 
Aug 21 18:11:54 jm8241982-desktop NetworkManager: <debug> [1219363914.820733] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 21 18:11:54 jm8241982-desktop NetworkManager: <debug> [1219363914.834822] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1'). 
Aug 21 18:11:54 jm8241982-desktop NetworkManager: <debug> [1219363914.843331] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_402_5661_00101016300000000058_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Aug 21 18:11:54 jm8241982-desktop NetworkManager: <debug> [1219363914.979004] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_Audio_Player_00101016300000000058_0_0'). 
Aug 21 18:11:55 jm8241982-desktop NetworkManager: <debug> [1219363915.028435] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_GPX_SD_MMC_CARD_00101016300000000058_0_1'). 
Aug 21 18:11:55 jm8241982-desktop NetworkManager: <debug> [1219363915.074717] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_0365'). 
Aug 21 18:11:55 jm8241982-desktop NetworkManager: <debug> [1219363915.132343] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_48AE_041D'). 
Aug 21 18:13:32 jm8241982-desktop NetworkManager: <debug> [1219364012.159064] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_711383040'). 
Aug 21 18:22:25 jm8241982-desktop NetworkManager: <debug> [1219364545.559383] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_711383040'). 
Aug 21 22:23:40 jm8241982-desktop NetworkManager: <debug> [1219379020.694747] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_634933248'). 
Aug 22 07:49:39 jm8241982-desktop NetworkManager: <debug> [1219412979.350617] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_634933248'). 
Aug 22 07:50:08 jm8241982-desktop NetworkManager: <debug> [1219413008.497030] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_500637696'). 
Aug 22 08:02:47 jm8241982-desktop NetworkManager: <debug> [1219413767.490567] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_500637696'). 
Aug 22 08:03:28 jm8241982-desktop NetworkManager: <debug> [1219413808.681284] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_633204736'). 
Aug 22 08:15:06 jm8241982-desktop NetworkManager: <debug> [1219414506.046955] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_633204736'). 
Aug 22 08:16:04 jm8241982-desktop NetworkManager: <debug> [1219414564.543569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_514037760'). 
Aug 22 08:40:22 jm8241982-desktop NetworkManager: <debug> [1219416022.963973] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_514037760'). 
Aug 22 08:40:49 jm8241982-desktop NetworkManager: <debug> [1219416049.712023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_572454912'). 
Aug 22 09:20:02 jm8241982-desktop NetworkManager: <debug> [1219418402.469138] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_572454912'). 
Aug 22 09:37:33 jm8241982-desktop NetworkManager: <debug> [1219419453.703918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_652646400'). 
Aug 22 09:50:22 jm8241982-desktop NetworkManager: <debug> [1219420222.108068] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_652646400'). 
Aug 22 09:51:46 jm8241982-desktop NetworkManager: <debug> [1219420306.483912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_511614976'). 
Aug 22 10:02:25 jm8241982-desktop NetworkManager: <debug> [1219420945.828479] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_511614976'). 
Aug 22 10:02:56 jm8241982-desktop NetworkManager: <debug> [1219420976.780903] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_711454720'). 
Aug 22 10:13:21 jm8241982-desktop NetworkManager: <debug> [1219421601.335666] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_711454720'). 
Aug 22 12:06:58 jm8241982-desktop hal_lpadmin: remove
Aug 22 12:06:58 jm8241982-desktop hal_lpadmin: Found configured printer: deskjet_3520
Aug 22 12:06:58 jm8241982-desktop NetworkManager: <debug> [1219428418.843483] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_7304_TH433140RV7O_if0_printer_TH433140RV7O'). 
Aug 22 12:32:30 jm8241982-desktop NetworkManager: <debug> [1219429950.529257] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_442542080'). 
Aug 22 12:51:08 jm8241982-desktop NetworkManager: <debug> [1219431068.316792] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_442542080').

---

### Post by jmate24 on 2008-08-22
that is my media player and when ever i enable the delete command (right-click menu) i forget that when i use it, that i delete everything...
if i can shut off trash to certain drives then that would make things easier.

---

