---
title: "USB and CD/DVD mounting problems"
date: 2010-09-13
forum: Hardware
---

### Post by lbmounse on 2010-09-13
I just upgraded (via fresh install) both my laptop and desktop to Kubuntu 10.04.

Now, both of these devices are refusing to mount USB flash devices.
It will, however, mount my USB external HD, and the laptop will mount a SD card in it's card reader.

Also, the desktop is being finicky about mounting CDs and DVDS.
If I insert the disk within 5 minutes or so of booting, it works fine.  However, after a period, the CD unmounts and disappears.  If i try to open/close the cd tray, or even insert a different disk, it does not detect/mount it.

Any suggestions?

---

### Post by rickyjohn12 on 2010-09-13
This page explains how to create and use Live USB media. A Live USB system stored on flash memory, sometimes called a stick, lets you boot any USB-bootable computer into a Fedora operating system environment without writing to that computer's hard disk. The Live USB stick can feature an area to store changes to the system, called a persistent overlay. It can also have a separate area to store user account information and data such as documents and downloaded files, with optional encryption for security and peace of mind. Finally, with a non-destructive installation, pre-existing files and excess storage space on the stick are accessible from the system. Essentially, you can carry your computer with you in your pocket, booting it on nearly any system you find yourself using.

---

### Post by lbmounse on 2010-09-13
I'm not using a USB live system.  I boot from the internal HD.
The problem is getting non-bootable devices to mount.

---

### Post by flyingsliverfin on 2010-09-13
ive messed around with usb sticks more than cd's... so
go to the terminal and type exactly ```
sudo fdisk -l
``` and post the output please

---

### Post by lbmounse on 2010-09-14
It appears to be only detecting my HD

```
Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00280028

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3890    31246393+   c  W95 FAT32 (LBA)
/dev/sda2   *        3891       19657   126648427+  83  Linux
/dev/sda3           19658       20023     2939864+   5  Extended
/dev/sda5           19658       20023     2939863+  82  Linux swap / Solaris
```

I'm trying to connect my phone by usb cable.  It worked in 8.04.
It works with my pen drive and external HD.  But not with my phone or camera.  And my desktop is failing to id and mount cds.

---

### Post by flyingsliverfin on 2010-09-14
oh so ur flash drive works... sorry i have no idea what to do with cd's and phones etc manually

---

### Post by lbmounse on 2010-09-15
I found this solution to the DVD/CD problem in this thread: [http://ca.ubuntuforums.org/showthread.php?t=1235151&page=4](http://ca.ubuntuforums.org/showthread.php?t=1235151&page=4)

>  Re: CD/DVD drive won't mount
Well the latest kernel (2.6.35) was released for Ubuntu a couple of days back. After a couple of days testing this has DEFINITELY solved my CD/DVD mounting problems.

Add ppa:kernel-ppa/ppa to your software source list

Reload - then search for "2.6.35" in Synaptic.

Install the following 3 packages (make sure you choose the correct 3 for either 32 or 64 bit. 14 is the latest in the repository so this may change)

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic
linux-image-2.6.35-14-generic

This kernel will now be the default. Everything now works for me and I have had no problems with it.

I am now running the 2.6.35-14 and the 2.6.35-21 kernels.  The CD/DVD drive seems to have no problems now.

However, the problem remains with certain USB devices.  I installed digikam, and it allowed me to access my camera.  

However, I still can't mount the camera and cell phone as a USB device.

---

### Post by flyingsliverfin on 2010-09-15
if you have a sd card reader you could try taking the memory card out of the camera and doing it that way... 
how about transferring pics or whatever via bluetooth? im not sure that works very well though. if it works though its nice. 1 less cable to lug around everywhere on trips

---

### Post by efflandt on 2010-09-16
See if you get any errors in dmesg or /var/log/messages about trying to read a non-existing drive (especially floppy).  That seems to interfere with auto mounting USB and CD/DVD, but was not an issue until 10.04.  I think that may have also caused a suspend/hybernate issue (kept waking after 20 seconds).

Some people were able to fix that by disabling the non-existing floppy in BIOS.  But for one old laptop with hot swap drive bay, Linux kept throwing errors trying to read a floppy anyway (in case one was attached later).  In that case I had to blacklist floppy and **sudo update-initramfs -u** to make sure that the floppy module did not load at all.

---

### Post by lbmounse on 2010-09-18
This machine does have a floppy, but it dees not appear to be working, either.  This isn't a real concern, because I don't use it.

Here is the output to dmesg.  (My usb devices were NOT plugged in at the time.)  It is giving multiple errors.

```
luke@preservedword:/usr/lib/sysinfo$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-21-generic-pae (buildd@lychee) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #30~lucid1-Ubuntu SMP Sat Sep 11 15:43:06 UTC 2010 (Ubuntu 2.6.35-21.30~lucid1-generic-pae 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bfc0000 (usable)
[    0.000000]  BIOS-e820: 000000003bfc0000 - 000000003bfce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bfce000 - 000000003bff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bff0000 - 000000003c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3bfc0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003bfc0000 (usable)
[    0.000000]  modified: 000000003bfc0000 - 000000003bfce000 (ACPI data)
[    0.000000]  modified: 000000003bfce000 - 000000003bff0000 (ACPI NVS)
[    0.000000]  modified: 000000003bff0000 - 000000003c000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
[    0.000000] RAMDISK: 2c7fc000 - 2d010000
[    0.000000] ACPI: RSDP 000f84e0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3bfc0000 00030 (v01 A M I  OEMRSDT  04000627 MSFT 00000097)
[    0.000000] ACPI: FACP 3bfc0200 00084 (v02 A M I  OEMFACP  04000627 MSFT 00000097)
[    0.000000] ACPI: DSDT 3bfc0400 0409D (v01  12345 12345123 00000123 INTL 02002026)
[    0.000000] ACPI: FACS 3bfce000 00040
[    0.000000] ACPI: APIC 3bfc0390 0006C (v01 A M I  OEMAPIC  04000627 MSFT 00000097)
[    0.000000] ACPI: OEMB 3bfce040 0004B (v01 A M I  AMI_OEM  04000627 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 67MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0003bfc0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bfc0
[    0.000000] On node 0 totalpages: 245583
[    0.000000] free_area_init_node: node 0, pgdat c0840bc0, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 136 pages used for memmap
[    0.000000]   HighMem zone: 17210 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3c000000 (gap: 3c000000:c2c00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1800000 s39872 r0 d21568 u524288
[    0.000000] pcpu-alloc: s39872 r0 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243663
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-21-generic-pae root=UUID=a2e5ba5e-ea0b-49c1-af9b-d57a82cf01a6 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4913600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (49 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009fb3dc]   TEXT DATA BSS
[    0.000000]   #3 [002c7fc000 - 002d010000]         RAMDISK
[    0.000000]   #4 [00009fc000 - 0000a03101]             BRK
[    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #7 [000009fc00 - 00000fd380]   BIOS reserved
[    0.000000]   #8 [00000fd498 - 00000ff780]   BIOS reserved
[    0.000000]   #9 [00000fd380 - 00000fd498]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001781000]         BOOTMEM
[    0.000000]   #15 [0001781000 - 0001781004]         BOOTMEM
[    0.000000]   #16 [0001781040 - 0001781100]         BOOTMEM
[    0.000000]   #17 [0001781100 - 00017811a8]         BOOTMEM
[    0.000000]   #18 [00017811c0 - 00017841c0]         BOOTMEM
[    0.000000]   #19 [00017841c0 - 00017841d0]         BOOTMEM
[    0.000000]   #20 [0001784200 - 0001784800]         BOOTMEM
[    0.000000]   #21 [0001784800 - 000178482f]         BOOTMEM
[    0.000000]   #22 [0001784840 - 00017849a8]         BOOTMEM
[    0.000000]   #23 [00017849c0 - 0001784a00]         BOOTMEM
[    0.000000]   #24 [0001784a00 - 0001784a40]         BOOTMEM
[    0.000000]   #25 [0001784a40 - 0001784a80]         BOOTMEM
[    0.000000]   #26 [0001784a80 - 0001784ac0]         BOOTMEM
[    0.000000]   #27 [0001784ac0 - 0001784b00]         BOOTMEM
[    0.000000]   #28 [0001784b00 - 0001784b40]         BOOTMEM
[    0.000000]   #29 [0001784b40 - 0001784b80]         BOOTMEM
[    0.000000]   #30 [0001784b80 - 0001784bc0]         BOOTMEM
[    0.000000]   #31 [0001784bc0 - 0001784c00]         BOOTMEM
[    0.000000]   #32 [0001784c00 - 0001784c10]         BOOTMEM
[    0.000000]   #33 [0001784c40 - 0001784cae]         BOOTMEM
[    0.000000]   #34 [0001784cc0 - 0001784d2e]         BOOTMEM
[    0.000000]   #35 [0001800000 - 000180f000]         BOOTMEM
[    0.000000]   #36 [0001880000 - 000188f000]         BOOTMEM
[    0.000000]   #37 [0001900000 - 000190f000]         BOOTMEM
[    0.000000]   #38 [0001980000 - 000198f000]         BOOTMEM
[    0.000000]   #39 [0001786d40 - 0001786d44]         BOOTMEM
[    0.000000]   #40 [0001786d80 - 0001786d84]         BOOTMEM
[    0.000000]   #41 [0001786dc0 - 0001786dd0]         BOOTMEM
[    0.000000]   #42 [0001786e00 - 0001786e10]         BOOTMEM
[    0.000000]   #43 [0001786e40 - 0001786ed8]         BOOTMEM
[    0.000000]   #44 [0001786f00 - 0001786f38]         BOOTMEM
[    0.000000]   #45 [0001786f40 - 000178af40]         BOOTMEM
[    0.000000]   #46 [000198f000 - 0001a0f000]         BOOTMEM
[    0.000000]   #47 [000178af40 - 00017caf40]         BOOTMEM
[    0.000000]   #48 [0001a0f000 - 0001ebe9c0]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003bfc0)
[    0.000000] Memory: 951276k/982784k available (5084k kernel code, 31056k reserved, 2441k data, 704k init, 69384k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc085a000 - 0xc090a000   ( 704 kB)
[    0.000000]       .data : 0xc05f71ba - 0xc08598e8   (2441 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05f71ba   (5084 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU-based detection of stalled CPUs is disabled.
[    0.000000]  Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 3199.964 MHz processor.
[    0.016005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6399.92 BogoMIPS (lpj=12799856)
[    0.016012] pid_max: default: 32768 minimum: 301
[    0.016036] Security Framework initialized
[    0.016060] AppArmor: AppArmor initialized
[    0.016063] Yama: becoming mindful.
[    0.016139] Mount-cache hash table entries: 512
[    0.016303] Initializing cgroup subsys ns
[    0.016309] Initializing cgroup subsys cpuacct
[    0.016315] Initializing cgroup subsys memory
[    0.016328] Initializing cgroup subsys devices
[    0.016331] Initializing cgroup subsys freezer
[    0.016334] Initializing cgroup subsys net_cls
[    0.016375] CPU: Physical Processor ID: 0
[    0.016378] CPU: Processor Core ID: 0
[    0.016381] mce: CPU supports 4 MCE banks
[    0.016396] CPU0: Thermal monitoring enabled (TM1)
[    0.016401] using mwait in idle threads.
[    0.016409] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.016416] ... version:                0
[    0.016418] ... bit width:              40
[    0.016420] ... generic registers:      18
[    0.016423] ... value mask:             000000ffffffffff
[    0.016425] ... max period:             0000007fffffffff
[    0.016428] ... fixed-purpose events:   0
[    0.016430] ... event mask:             000000000003ffff
[    0.023660] ACPI: Core revision 20100428
[    0.031762] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.031770] ftrace: allocating 22390 entries in 44 pages
[    0.036090] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040259] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.079952] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 05
[    0.080000] Booting Node   0, Processors  #1
[    0.020000] Initializing CPU#1
[    0.168000] TSC synchronization [CPU#0 -> CPU#1]:
[    0.168000] Measured 7991635984 cycles TSC warp between CPUs, turning off TSC clock.
[    0.168000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.168023] Brought up 2 CPUs
[    0.168028] Total of 2 processors activated (12800.29 BogoMIPS).
[    0.168819] devtmpfs: initialized
[    0.169334] regulator: core version 0.5
[    0.169378] Time: 22:43:38  Date: 09/18/10
[    0.169430] NET: Registered protocol family 16
[    0.169444] Trying to unpack rootfs image as initramfs...
[    0.169651] EISA bus registered
[    0.169667] ACPI: bus type pci registered
[    0.169897] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[    0.169901] PCI: Using configuration type 1 for base access
[    0.173306] bio: create slab <bio-0> at 0
[    0.174278] ACPI: EC: Look up EC in DSDT
[    0.179441] ACPI: Executed 1 blocks of module-level executable AML code
[    0.189202] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node f741a150), AE_INVALID_TABLE_LENGTH
[    0.189362] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node f741a1e0), AE_INVALID_TABLE_LENGTH
[    0.189438] ACPI: Interpreter enabled
[    0.189444] ACPI: (supports S0 S1 S4 S5)
[    0.189500] ACPI: Using IOAPIC for interrupt routing
[    0.211498] ACPI Warning: Incorrect checksum in table [OEMB] - 0x4C, should be 0x3F (20100428/tbutils-314)
[    0.211758] ACPI: No dock devices found.
[    0.211765] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.212040] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.212508] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.212514] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.212520] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.212526] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.212535] pci_root PNP0A03:00: host bridge window [mem 0x3c000000-0xff37ffff] (ignored)
[    0.212574] pci 0000:00:00.0: reg 10: [mem 0xf8000000-0xfbffffff pref]
[    0.213002] pci 0000:00:01.0: supports D1
[    0.213074] pci 0000:00:08.0: reg 10: [io  0xe800-0xe8ff]
[    0.213086] pci 0000:00:08.0: reg 14: [mem 0xfebffc00-0xfebfffff]
[    0.213120] pci 0000:00:08.0: reg 30: [mem 0xfebc0000-0xfebdffff pref]
[    0.213147] pci 0000:00:08.0: supports D1 D2
[    0.213152] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot
[    0.213159] pci 0000:00:08.0: PME# disabled
[    0.213211] pci 0000:00:0f.0: reg 10: [io  0xec00-0xec07]
[    0.213222] pci 0000:00:0f.0: reg 14: [io  0xe480-0xe483]
[    0.213232] pci 0000:00:0f.0: reg 18: [io  0xe400-0xe407]
[    0.213242] pci 0000:00:0f.0: reg 1c: [io  0xe080-0xe083]
[    0.213253] pci 0000:00:0f.0: reg 20: [io  0xe000-0xe00f]
[    0.213263] pci 0000:00:0f.0: reg 24: [io  0xd800-0xd8ff]
[    0.213358] pci 0000:00:0f.1: reg 20: [io  0xfc00-0xfc0f]
[    0.213468] pci 0000:00:10.0: reg 20: [io  0xdc00-0xdc1f]
[    0.213506] pci 0000:00:10.0: supports D1 D2
[    0.213510] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213518] pci 0000:00:10.0: PME# disabled
[    0.213582] pci 0000:00:10.1: reg 20: [io  0xd480-0xd49f]
[    0.213619] pci 0000:00:10.1: supports D1 D2
[    0.213624] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213631] pci 0000:00:10.1: PME# disabled
[    0.213694] pci 0000:00:10.2: reg 20: [io  0xd400-0xd41f]
[    0.213736] pci 0000:00:10.2: supports D1 D2
[    0.213741] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213753] pci 0000:00:10.2: PME# disabled
[    0.213826] pci 0000:00:10.3: reg 20: [io  0xd080-0xd09f]
[    0.213863] pci 0000:00:10.3: supports D1 D2
[    0.213867] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213875] pci 0000:00:10.3: PME# disabled
[    0.213920] pci 0000:00:10.4: reg 10: [mem 0xfebff800-0xfebff8ff]
[    0.213981] pci 0000:00:10.4: supports D1 D2
[    0.213985] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.213992] pci 0000:00:10.4: PME# disabled
[    0.214076] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.214148] pci 0000:00:11.5: reg 10: [io  0xee00-0xeeff]
[    0.214211] pci 0000:00:11.5: supports D1 D2
[    0.214312] pci 0000:01:00.0: reg 10: [mem 0xf0000000-0xf3ffffff pref]
[    0.214323] pci 0000:01:00.0: reg 14: [mem 0xfd000000-0xfdffffff]
[    0.214351] pci 0000:01:00.0: reg 30: [mem 0xfeaf0000-0xfeafffff pref]
[    0.214378] pci 0000:01:00.0: supports D1 D2
[    0.214453] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.214464] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.214472] pci 0000:00:01.0:   bridge window [mem 0xfca00000-0xfeafffff]
[    0.214479] pci 0000:00:01.0:   bridge window [mem 0xeff00000-0xf7efffff pref]
[    0.214492] pci_bus 0000:00: on NUMA node 0
[    0.214500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.214872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.235486] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.235704] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.235893] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.236110] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.236330] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.236520] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.236740] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.236937] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.237014] HEST: Table is not found!
[    0.237184] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.237191] vgaarb: loaded
[    0.237539] SCSI subsystem initialized
[    0.237711] libata version 3.00 loaded.
[    0.237835] usbcore: registered new interface driver usbfs
[    0.237862] usbcore: registered new interface driver hub
[    0.237909] usbcore: registered new device driver usb
[    0.238152] ACPI: WMI: Mapper loaded
[    0.238156] PCI: Using ACPI for IRQ routing
[    0.238162] PCI: pci_cache_line_size set to 64 bytes
[    0.238310] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.238316] reserve RAM buffer: 000000003bfc0000 - 000000003bffffff 
[    0.238505] NetLabel: Initializing
[    0.238509] NetLabel:  domain hash size = 128
[    0.238512] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.238534] NetLabel:  unlabeled traffic allowed by default
[    0.260673] AppArmor: AppArmor Filesystem Enabled
[    0.260702] pnp: PnP ACPI init
[    0.260732] ACPI: bus type pnp registered
[    0.275815] pnp: PnP ACPI: found 14 devices
[    0.275820] ACPI: ACPI bus type pnp unregistered
[    0.275826] PnPBIOS: Disabled by ACPI PNP
[    0.275853] system 00:09: [io  0x0a00-0x0a0f] has been reserved
[    0.275860] system 00:09: [io  0x0290-0x029f] has been reserved
[    0.275865] system 00:09: [io  0x0a20-0x0a2f] has been reserved
[    0.275870] system 00:09: [io  0x0a30-0x0a3f] has been reserved
[    0.275876] system 00:09: [io  0x0a40-0x0a4f] has been reserved
[    0.275888] system 00:0a: [io  0x03e0-0x03e7] has been reserved
[    0.275894] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.275899] system 00:0a: [io  0x0800-0x087f] has been reserved
[    0.275905] system 00:0a: [io  0x0400-0x041f] has been reserved
[    0.275917] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.275923] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.275936] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.275942] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.275948] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.275954] system 00:0d: [mem 0x00100000-0x3bffffff] could not be reserved
[    0.275959] system 00:0d: [mem 0xff380000-0xffffffff] has been reserved
[    0.313427] Switching to clocksource acpi_pm
[    0.313645] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.313651] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.313669] pci 0000:00:01.0:   bridge window [mem 0xfca00000-0xfeafffff]
[    0.313682] pci 0000:00:01.0:   bridge window [mem 0xeff00000-0xf7efffff pref]
[    0.313708] pci 0000:00:01.0: setting latency timer to 64
[    0.313716] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.313721] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    0.313727] pci_bus 0000:01: resource 1 [mem 0xfca00000-0xfeafffff]
[    0.313732] pci_bus 0000:01: resource 2 [mem 0xeff00000-0xf7efffff pref]
[    0.313808] NET: Registered protocol family 2
[    0.313941] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.314498] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.315624] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.316000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.316000] TCP reno registered
[    0.316000] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.316000] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.316000] NET: Registered protocol family 1
[    0.316000] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.316000] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    0.316000] pci 0000:01:00.0: Boot video device
[    0.316000] PCI: CLS 32 bytes, default 64
[    0.316000] cpufreq-nforce2: No nForce2 chipset.
[    0.316000] Scanning for low memory corruption every 60 seconds
[    0.316000] audit: initializing netlink socket (disabled)
[    0.316000] type=2000 audit(1284849818.312:1): initialized
[    0.329224] highmem bounce pool size: 64 pages
[    0.329235] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.332118] VFS: Disk quotas dquot_6.5.2
[    0.332241] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.333487] fuse init (API version 7.14)
[    0.333674] msgmni has been set to 1722
[    0.335851] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.335857] io scheduler noop registered
[    0.335861] io scheduler deadline registered
[    0.335888] io scheduler cfq registered (default)
[    0.336129] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.336172] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.336594] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.336612] ACPI: Sleep Button [SLPB]
[    0.336699] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.336710] ACPI: Power Button [PWRB]
[    0.336800] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.336808] ACPI: Power Button [PWRF]
[    0.337289] ACPI: acpi_idle registered with cpuidle
[    0.348484] ERST: Table is not found!
[    0.348781] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.348917] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.349640] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.351933] brd: module loaded
[    0.353138] loop: module loaded
[    0.353624]   alloc irq_desc for 20 on node -1
[    0.353629]   alloc kstat_irqs on node -1
[    0.353643] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.353740] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.353766] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.353808] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    0.354457] Fixed MDIO Bus: probed
[    0.354524] PPP generic driver version 2.4.2
[    0.354592] tun: Universal TUN/TAP device driver, 1.6
[    0.354596] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.354791] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.354822]   alloc irq_desc for 21 on node -1
[    0.354826]   alloc kstat_irqs on node -1
[    0.354835] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.354861] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.354930] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.355015] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfebff800
[    0.355070] isapnp: Scanning for PnP cards...
[    0.444193] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.444453] hub 1-0:1.0: USB hub found
[    0.444463] hub 1-0:1.0: 8 ports detected
[    0.444606] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.444636] uhci_hcd: USB Universal Host Controller Interface driver
[    0.444717] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.444733] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.444792] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.444826] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000dc00
[    0.445029] hub 2-0:1.0: USB hub found
[    0.445037] hub 2-0:1.0: 2 ports detected
[    0.445128] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.445139] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.445190] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.445217] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d480
[    0.445417] hub 3-0:1.0: USB hub found
[    0.445424] hub 3-0:1.0: 2 ports detected
[    0.445515] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.445524] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.445586] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.445612] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d400
[    0.445814] hub 4-0:1.0: USB hub found
[    0.445826] hub 4-0:1.0: 2 ports detected
[    0.445918] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.445928] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.445984] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.446010] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d080
[    0.446213] hub 5-0:1.0: USB hub found
[    0.446221] hub 5-0:1.0: 2 ports detected
[    0.446425] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.446948] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.446963] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.447065] mice: PS/2 mouse device common for all mice
[    0.447267] rtc_cmos 00:02: RTC can wake from S4
[    0.447332] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.447393] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.447581] device-mapper: uevent: version 1.0.3
[    0.456611] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.512838] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.523831] Freeing initrd memory: 8272k freed
[    0.535936] device-mapper: multipath: version 1.1.1 loaded
[    0.535944] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.536261] EISA: Probing bus 0 at eisa.0
[    0.536314] EISA: Detected 0 cards.
[    0.536456] cpuidle: using governor ladder
[    0.536460] cpuidle: using governor menu
[    0.537059] TCP cubic registered
[    0.537301] NET: Registered protocol family 10
[    0.538024] lo: Disabled Privacy Extensions
[    0.538448] NET: Registered protocol family 17
[    0.538542] Using IPI No-Shortcut mode
[    0.538724] PM: Resume from disk failed.
[    0.538752] registered taskstats version 1
[    0.539070]   Magic number: 10:390:755
[    0.539242] rtc_cmos 00:02: setting system clock to 2010-09-18 22:43:38 UTC (1284849818)
[    0.539247] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.539250] EDD information not available.
[    0.709642] isapnp: No Plug & Play device found
[    0.709667] Freeing unused kernel memory: 704k freed
[    0.710562] Write protecting the kernel text: 5088k
[    0.710669] Write protecting the kernel read-only data: 2020k
[    0.734155] udev: starting version 151
[    0.828124] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    0.828198]   alloc irq_desc for 16 on node -1
[    0.828204]   alloc kstat_irqs on node -1
[    0.828218] tulip 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.828822] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1
[    0.879029] net eth0: ADMtek Comet rev 17 at Port 0xe800, 00:14:bf:5e:72:dc, IRQ 16
[    0.879770] sata_via 0000:00:0f.0: version 2.6
[    0.879794] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.879885] sata_via 0000:00:0f.0: routed to hard irq line 11
[    0.886360] scsi0 : sata_via
[    0.890240] scsi1 : sata_via
[    0.894116] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe480 bmdma 0xe000 irq 20
[    0.894123] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xe008 irq 20
[    0.894390] pata_via 0000:00:0f.1: version 0.3.4
[    0.894415] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.911005] scsi2 : pata_via
[    0.930546] Floppy drive(s): fd0 is 1.44M
[    0.943075] scsi3 : pata_via
[    0.949718] FDC 0 is a post-1991 82077
[    0.949934] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.949941] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    1.096030] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.260417] ata1.00: ATA-7: Hitachi HDS721616PLA380, P22OAB3A, max UDMA/133
[    1.260422] ata1.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.276446] ata1.00: configured for UDMA/133
[    1.276632] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[    1.276944] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.277045] sd 0:0:0:0: [sda] 321672960 512-byte logical blocks: (164 GB/153 GiB)
[    1.277210] sd 0:0:0:0: [sda] Write Protect is off
[    1.277215] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.277250] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.277466]  sda: sda1 sda2 sda3 < sda5 >
[    1.320159] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.480025] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.844400] ata4.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB04, max UDMA/33
[    1.844445] ata4.01: ATAPI: LITE-ON DVD D LH-16D1P, TL13, max UDMA/33
[    1.860284] ata4.00: configured for UDMA/33
[    1.892281] ata4.01: configured for UDMA/33
[    1.893760] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB04 PQ: 0 ANSI: 5
[    1.900457] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.900463] Uniform CD-ROM driver Revision: 3.20
[    1.900619] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.900796] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.901365] scsi 3:0:1:0: CD-ROM            LITE-ON  DVD D LH-16D1P   TL13 PQ: 0 ANSI: 5
[    1.903250] sr1: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[    1.903396] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    1.903486] sr 3:0:1:0: Attached scsi generic sg2 type 5
[    2.374216] EXT3-fs: barriers not enabled
[    2.379630] kjournald starting.  Commit interval 5 seconds
[    2.379743] EXT3-fs (sda2): mounted filesystem with ordered data mode
[   12.311976] Adding 2939856k swap on /dev/sda5.  Priority:-1 extents:1 across:2939856k 
[   13.277912] udev: starting version 151
[   13.656623] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.738804] Linux agpgart interface v0.103
[   13.744469] agpgart: Detected VIA VT3314 chipset
[   13.749672] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   14.002141] parport_pc 00:08: reported by Plug and Play ACPI
[   14.002249] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   14.003580] lp: driver loaded but no devices found
[   14.100332] lp0: using parport0 (interrupt-driven).
[   14.116492] ppdev: user-space parallel port driver
[   14.139382] psmouse serio1: ID: 10 00 64
[   14.741692] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   14.741743] type=1400 audit(1284864232.700:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=538 comm="apparmor_parser"
[   14.742476] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   14.742501] type=1400 audit(1284864232.700:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=538 comm="apparmor_parser"
[   14.742853] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   14.742877] type=1400 audit(1284864232.700:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=538 comm="apparmor_parser"
[   14.848301] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   15.085134]   alloc irq_desc for 22 on node -1
[   15.085140]   alloc kstat_irqs on node -1
[   15.085155] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   15.085623] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   15.181429] EXT3-fs (sda2): using internal journal
[  103.340494] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[  103.340549] type=1400 audit(1284864321.296:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=743 comm="apparmor_parser"
[  103.341213] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[  103.341238] type=1400 audit(1284864321.296:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=743 comm="apparmor_parser"
[  103.341593] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[  103.341618] type=1400 audit(1284864321.296:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=743 comm="apparmor_parser"
[  103.420770] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[  103.420820] type=1400 audit(1284864321.380:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=748 comm="apparmor_parser"
[  103.421594] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[  103.421652] type=1400 audit(1284864321.380:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=748 comm="apparmor_parser"
[  103.679696] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[  103.679745] type=1400 audit(1284864321.632:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=749 comm="apparmor_parser"
[  103.725752] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[  103.725796] type=1400 audit(1284864321.680:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=753 comm="apparmor_parser"
[  103.986468] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[  103.986512] type=1400 audit(1284864321.944:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=754 comm="apparmor_parser"
[  104.696598] [drm] Initialized drm 1.1.0 20060810
[  104.701544] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  104.702606] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[  104.898995] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[  104.899024] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[  104.899116] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[  105.869683] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[  105.869730] type=1400 audit(1284864323.824:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=862 comm="apparmor_parser"
[  106.913734] 0000:00:08.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[  106.913749] net eth0: Setting full-duplex based on MII#1 link partner capability of 45e1
[  114.028015] eth0: no IPv6 routers present
[  315.274210] sr 3:0:0:0: [sr0] Unhandled sense code
[  315.274216] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  315.274221] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[  315.274228] sr 3:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[  315.274237] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 02 f5 46 00 00 02 00
[  315.274250] end_request: I/O error, dev sr0, sector 775448
[  315.274257] Buffer I/O error on device sr0, logical block 96931
[  321.731887] sr 3:0:0:0: [sr0] Unhandled sense code
[  321.731895] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  321.731903] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[  321.731912] sr 3:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[  321.731924] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 02 f5 46 00 00 02 00
[  321.731944] end_request: I/O error, dev sr0, sector 775448
[  321.731954] Buffer I/O error on device sr0, logical block 96931
[  328.188366] sr 3:0:0:0: [sr0] Unhandled sense code
[  328.188372] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  328.188378] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[  328.188385] sr 3:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[  328.188393] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 02 f5 46 00 00 02 00
[  328.188407] end_request: I/O error, dev sr0, sector 775448
[  328.188413] Buffer I/O error on device sr0, logical block 96931

```

---

### Post by lbmounse on 2010-09-19
lsusb - phone connected: 

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 009: ID 05c6:1000 Qualcomm, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 05dc:a731 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsusb - phone disconnected

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 05dc:a731 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

