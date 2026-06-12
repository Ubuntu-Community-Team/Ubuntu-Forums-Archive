---
title: "Laptop DVD-RW won´t mount"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by binger on 2007-08-17
Hi,
I have using Ubuntu on my desktop for a few months now, and decided to install it on my laptop dual booting with XP.  The installation went smoothly, but now that its up and running I cant get my DVD/CD-RW drive working.  It is conncted through Serial ATA as is my one hard drive.  I have been searching the forums and google for answers and so far I havent been successful.  ANy help is much appreciated.  I will give as much info as I can below.  the laptop is a M-tech 570U.  Core Duo 1.8ghz with an intel chipset(945 I think). 
I am running Ubuntu Studio Feisty Fawn 7.04 with the 2..6.20-16 kernal

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6b4ae5d3-f2f3-47d7-9284-a2f1333e84da /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5106170f-b2a6-439e-814a-c9093fdc2554 none            swap    sw              0       0
/dev/sda3       /media/cdrom0   iso9660,udf user,noauto     0       0

brian@ubuntu:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-lowlatency/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
brian@ubuntu:~$ 


from some of the posts i have been reading, i have some questions, is there a piix bug in this kernal version?  I added ata_piix to my /etc/modules, i dont know if that helps or not.  I am still not sure if my dvd drive is /dev/sda or /dev/sda3

[    0.000000] Linux version 2.6.20-16-lowlatency (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP PREEMPT Thu Jun 7 20:23:03 UTC 2007 (Ubuntu Unofficial)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fd80000 end: 000000003fe80000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fe80000 size: 000000000000b000 end: 000000003fe8b000 type: 3
[    0.000000] copy_e820_map() start: 000000003fe8b000 size: 0000000000075000 end: 000000003ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000003ff00000 size: 0000000000100000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe80000 (usable)
[    0.000000]  BIOS-e820: 000000003fe80000 - 000000003fe8b000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fe8b000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7760
[    0.000000] Entering add_active_range(0, 0, 261760) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261760
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261760
[    0.000000] On node 0 totalpages: 261760
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32131 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f76b0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x3fe85766
[    0.000000] ACPI: FADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe8ae20
[    0.000000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe8ae94
[    0.000000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe8aefc
[    0.000000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x3fe8af34
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x3fe8af70
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3fe8afd8
[    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20050624) @ 0x3fe867d2
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20050624) @ 0x3fe86136
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x3fe857ae
[    0.000000] ACPI: DSDT (v001 INTEL  CALISTGA 0x06040000 INTL 0x20050624) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1828.864 MHz processor.
[   16.096026] Built 1 zonelists.  Total pages: 259715
[   16.096032] Kernel command line: root=UUID=6b4ae5d3-f2f3-47d7-9284-a2f1333e84da ro quiet splash
[   16.096293] mapped APIC to ffffd000 (fee00000)
[   16.096297] mapped IOAPIC to ffffc000 (fec00000)
[   16.096301] Enabling fast FPU save and restore... done.
[   16.096306] Enabling unmasked SIMD FPU exception support... done.
[   16.096316] Initializing CPU#0
[   16.096399] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   16.097720] Console: colour VGA+ 80x25
[   16.097998] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.098528] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.145717] Memory: 1026684k/1047040k available (2019k kernel code, 19668k reserved, 902k data, 328k init, 129536k highmem)
[   16.145733] virtual kernel memory layout:
[   16.145735]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   16.145737]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.145739]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.145741]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.145744]       .init : 0xc03e1000 - 0xc0433000   ( 328 kB)
[   16.145746]       .data : 0xc02f8c85 - 0xc03da6d4   ( 902 kB)
[   16.145748]       .text : 0xc0100000 - 0xc02f8c85   (2019 kB)
[   16.145754] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.145987] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.145997] hpet0: 3 64-bit timers, 14318180 Hz
[   16.147003] Using HPET for base-timer
[   16.206887] Calibrating delay using timer specific routine.. 3661.34 BogoMIPS (lpj=1830673)
[   16.206960] Security Framework v1.0.0 initialized
[   16.206968] SELinux:  Disabled at boot.
[   16.206997] Mount-cache hash table entries: 512
[   16.207194] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   16.207207] monitor/mwait feature present.
[   16.207211] using mwait in idle threads.
[   16.207217] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.207222] CPU: L2 cache: 2048K
[   16.207226] CPU: Physical Processor ID: 0
[   16.207229] CPU: Processor Core ID: 0
[   16.207233] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   16.207248] Compat vDSO mapped to ffffe000.
[   16.207253] Remapping vsyscall page to ffffe000
[   16.207271] Checking 'hlt' instruction... OK.
[   16.211032] SMP alternatives: switching to UP code
[   16.211461] Early unpacking initramfs... done
[   16.767365] ACPI: Core revision 20060707
[   16.767699] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.773514] CPU0: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[   16.773548] SMP alternatives: switching to SMP code
[   16.773674] Booting processor 1/1 eip 3000
[   16.784335] Initializing CPU#1
[   16.844797] Calibrating delay using timer specific routine.. 3657.61 BogoMIPS (lpj=1828808)
[   16.844808] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   16.844817] monitor/mwait feature present.
[   16.844822] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.844825] CPU: L2 cache: 2048K
[   16.844829] CPU: Physical Processor ID: 0
[   16.844831] CPU: Processor Core ID: 1
[   16.844834] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   16.845490] CPU1: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[   16.845526] Total of 2 processors activated (7318.96 BogoMIPS).
[   16.845730] ENABLING IO-APIC IRQs
[   16.845971] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.957604] checking TSC synchronization across 2 CPUs: passed.
[    0.001004] Brought up 2 CPUs
[    0.052473] migration_cost=30
[    0.052911] Booting paravirtualized kernel on bare hardware
[    0.053037] Time: 14:06:32  Date: 07/17/107
[    0.053085] NET: Registered protocol family 16
[    0.053243] EISA bus registered
[    0.053251] ACPI: bus type pci registered
[    0.053542] PCI: BIOS BUG #81[49435000] found
[    0.053603] PCI: Using configuration type 1
[    0.053606] Setting up standard PCI resources
[    0.059100] ACPI: Interpreter enabled
[    0.059105] ACPI: Using IOAPIC for interrupt routing
[    0.060377] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.060385] PCI: Probing PCI hardware (bus 00)
[    0.062509] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.062516] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.062803] Boot video device is 0000:01:00.0
[    0.064080] PCI: Transparent bridge - 0000:00:1e.0
[    0.064182] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[    0.064186] Please report the result to linux-kernel to fix this permanently
[    0.064283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.068647] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.069500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.069952] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.070402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.070850] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.071916] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.072307] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.072697] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.073102] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.073487] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.073882] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.074275] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.074663] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.077555] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.077570] pnp: PnP ACPI init
[    0.081773] pnp: PnP ACPI: found 13 devices
[    0.081780] PnPBIOS: Disabled by ACPI PNP
[    0.081865] PCI: Using ACPI for IRQ routing
[    0.081869] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.082047] NET: Registered protocol family 8
[    0.082051] NET: Registered protocol family 20
[    0.082493] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.082498] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.083015] PCI: Bridge: 0000:00:01.0
[    0.083019]   IO window: 2000-2fff
[    0.083025]   MEM window: d8000000-d80fffff
[    0.083031]   PREFETCH window: c0000000-cfffffff
[    0.083037] PCI: Bridge: 0000:00:1c.0
[    0.083042]   IO window: 3000-3fff
[    0.083051]   MEM window: d4000000-d5ffffff
[    0.083057]   PREFETCH window: d0000000-d1ffffff
[    0.083066] PCI: Bridge: 0000:00:1c.1
[    0.083070]   IO window: 4000-4fff
[    0.083079]   MEM window: d6000000-d7ffffff
[    0.083086]   PREFETCH window: d2000000-d3ffffff
[    0.083094] PCI: Bridge: 0000:00:1c.2
[    0.083096]   IO window: disabled.
[    0.083104]   MEM window: disabled.
[    0.083110]   PREFETCH window: disabled.
[    0.083123] PCI: Bus 7, cardbus bridge: 0000:06:07.0
[    0.083127]   IO window: 00005400-000054ff
[    0.083134]   IO window: 00005800-000058ff
[    0.083142]   PREFETCH window: 50000000-53ffffff
[    0.083150]   MEM window: 58000000-5bffffff
[    0.083157] PCI: Bridge: 0000:00:1e.0
[    0.083162]   IO window: 5000-5fff
[    0.083170]   MEM window: d8100000-d81fffff
[    0.083177]   PREFETCH window: 50000000-55ffffff
[    0.083201] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.083210] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.083240] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    0.083249] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.083278] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    0.083287] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.083317] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.083326] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.083344] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.083365] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.083422] NET: Registered protocol family 2
[    0.095901] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.096061] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.097552] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[    0.098344] TCP: Hash tables configured (established 131072 bind 65536)
[    0.098348] TCP reno registered
[    0.102032] checking if image is initramfs... it is
[    1.195831] Freeing initrd memory: 6897k freed
[    1.196080] Simple Boot Flag at 0x36 set to 0x1
[    1.196800] audit: initializing netlink socket (disabled)
[    1.196823] audit(1187359593.204:1): initialized
[    1.196994] highmem bounce pool size: 64 pages
[    1.197153] VFS: Disk quotas dquot_6.5.1
[    1.197184] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.197262] io scheduler noop registered
[    1.197266] io scheduler anticipatory registered
[    1.197270] io scheduler deadline registered
[    1.197295] io scheduler cfq registered (default)
[    1.197622] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    1.197676] assign_interrupt_mode Found MSI capability
[    1.197681] Allocate Port Service[0000:00:01.0:pcie00]
[    1.197823] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.197898] assign_interrupt_mode Found MSI capability
[    1.197903] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.197963] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.198126] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.198196] assign_interrupt_mode Found MSI capability
[    1.198200] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.198256] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.198417] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.198487] assign_interrupt_mode Found MSI capability
[    1.198491] Allocate Port Service[0000:00:1c.2:pcie00]
[    1.198552] Allocate Port Service[0000:00:1c.2:pcie02]
[    1.198813] isapnp: Scanning for PnP cards...
[    1.555197] isapnp: No Plug & Play device found
[    1.594324] Real Time Clock Driver v1.12ac
[    1.594414] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.594598] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.594753] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 8250
[    1.595546] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.595911] mice: PS/2 mouse device common for all mice
[    1.596851] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.597081] input: Macintosh mouse button emulation as /class/input/input0
[    1.597140] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.597146] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.597532] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.600145] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.601499] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.601535] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.601540] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.601544] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.601549] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.601687] EISA: Probing bus 0 at eisa.0
[    1.601698] Cannot allocate resource for EISA slot 1
[    1.601703] Cannot allocate resource for EISA slot 2
[    1.601707] Cannot allocate resource for EISA slot 3
[    1.601711] Cannot allocate resource for EISA slot 4
[    1.601715] Cannot allocate resource for EISA slot 5
[    1.601736] EISA: Detected 0 cards.
[    1.625184] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.631834] TCP cubic registered
[    1.631851] NET: Registered protocol family 1
[    1.631886] Starting balanced_irq
[    1.631899] Using IPI No-Shortcut mode
[    1.632033] ACPI: (supports S0 S3 S4 S5)
[    1.632105]   Magic number: 3:837:131
[    1.632215] Time: tsc clocksource has been installed.
[    1.632401] Freeing unused kernel memory: 328k freed
[    2.966472] Capability LSM initialized
[    3.031701] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.032040] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.032495] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    3.032503] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.033346] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.033655] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.034179] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    3.034187] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.753000] Time: hpet clocksource has been installed.
[    3.965000] ACPI: Invalid passive threshold
[    4.178000] ACPI: Thermal Zone [THM0] (35 C)
[    4.671000] usbcore: registered new interface driver usbfs
[    4.671000] usbcore: registered new interface driver hub
[    4.671000] usbcore: registered new device driver usb
[    4.673000] USB Universal Host Controller Interface driver v3.0
[    4.673000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    4.673000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.673000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.673000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.673000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001800
[    4.673000] usb usb1: configuration #1 chosen from 1 choice
[    4.673000] hub 1-0:1.0: USB hub found
[    4.673000] hub 1-0:1.0: 2 ports detected
[    4.775000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    4.775000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.775000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.775000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.775000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001820
[    4.775000] usb usb2: configuration #1 chosen from 1 choice
[    4.775000] hub 2-0:1.0: USB hub found
[    4.775000] hub 2-0:1.0: 2 ports detected
[    4.876000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    4.876000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.876000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.877000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.877000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    4.877000] usb usb3: configuration #1 chosen from 1 choice
[    4.877000] hub 3-0:1.0: USB hub found
[    4.877000] hub 3-0:1.0: 2 ports detected
[    4.885000] ieee1394: Initialized config rom entry `ip1394'
[    4.978000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    4.978000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.978000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.979000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.979000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    4.979000] usb usb4: configuration #1 chosen from 1 choice
[    4.979000] hub 4-0:1.0: USB hub found
[    4.979000] hub 4-0:1.0: 2 ports detected
[    4.980000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    5.081000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    5.081000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.081000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.081000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    5.081000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.081000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.081000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd8404000
[    5.085000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.085000] usb usb5: configuration #1 chosen from 1 choice
[    5.085000] hub 5-0:1.0: USB hub found
[    5.085000] hub 5-0:1.0: 8 ports detected
[    5.187000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    5.187000] ACPI: PCI Interrupt 0000:06:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
[    5.187000] eth0: RTL8169sb/8110sb at 0xf8832c00, 00:90:f5:4f:f9:24, IRQ 17
[    5.197000] SCSI subsystem initialized
[    5.206000] libata version 2.20 loaded.
[    5.209000] ata_piix 0000:00:1f.2: version 2.10ac1
[    5.209000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    5.360000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    5.360000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.360000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    5.360000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    5.360000] scsi0 : ata_piix
[    5.499000] usb 1-1: device not accepting address 2, error -71
[    5.518000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.518000] ata1.00: ATA-7: ST980825AS, 3.04, max UDMA/133
[    5.518000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.523000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.523000] ata1.00: configured for UDMA/133
[    5.523000] scsi1 : ata_piix
[    5.688000] ATA: abnormal status 0x7F on port 0x00010177
[    5.688000] scsi 0:0:0:0: Direct-Access     ATA      ST980825AS       3.04 PQ: 0 ANSI: 5
[    5.689000] ACPI: PCI Interrupt 0000:06:07.1[B] -> GSI 17 (level, low) -> IRQ 17
[    5.740000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d8102000-d81027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.748000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.748000] sda: Write Protect is off
[    5.748000] sda: Mode Sense: 00 3a 00 00
[    5.748000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.748000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.748000] sda: Write Protect is off
[    5.748000] sda: Mode Sense: 00 3a 00 00
[    5.749000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.749000]  sda: sda1 sda2 sda3 < sda5 >
[    5.846000] sd 0:0:0:0: Attached scsi disk sda
[    5.853000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.015000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[    6.100000] Attempting manual resume
[    6.100000] swsusp: Resume From Partition 8:5
[    6.100000] PM: Checking swsusp image.
[    6.100000] PM: Resume from disk failed.
[    6.138000] usb 5-6: configuration #1 chosen from 1 choice
[    6.153000] kjournald starting.  Commit interval 5 seconds
[    6.153000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.345000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[    6.511000] usb 1-1: configuration #1 chosen from 1 choice
[   18.337000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.340000] agpgart: Detected an Intel 945GM Chipset.
[   18.358000] agpgart: AGP aperture is 256M @ 0x0
[   18.374000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.377000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.845000] iTCO_vendor_support: vendor-support=0
[   19.016000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   19.016000] iTCO_wdt: Found a ICH7-M DH TCO device (Version=2, TCOBASE=0x1060)
[   19.016000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.048000] ACPI: PCI Interrupt 0000:06:07.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.073000] Yenta: CardBus bridge found at 0000:06:07.0 [1558:0571]
[   19.073000] Yenta: Enabling burst memory read transactions
[   19.074000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   19.074000] Yenta: Routing CardBus interrupts to PCI
[   19.074000] Yenta TI: socket 0000:06:07.0, mfunc 0x01aa1b22, devctl 0x64
[   19.297000] Yenta: ISA IRQ mask 0x0cf0, PCI irq 16
[   19.297000] Socket status: 30000006
[   19.297000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   19.297000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   19.297000] cs: IO port probe 0x5000-0x5fff: clean.
[   19.298000] pcmcia: parent PCI bridge Memory window: 0xd8100000 - 0xd81fffff
[   19.298000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x55ffffff
[   19.608000] intel_rng: FWH not detected
[   19.670000] sdhci: Secure Digital Host Controller Interface driver
[   19.670000] sdhci: Copyright(c) Pierre Ossman
[   19.670000] sdhci: SDHCI controller found at 0000:06:07.3 [104c:803c] (rev 0)
[   19.670000] ACPI: PCI Interrupt 0000:06:07.3[D] -> GSI 19 (level, low) -> IRQ 20
[   19.670000] mmc0: SDHCI at 0xd8102800 irq 20 PIO
[   19.817000] irda_init()
[   19.817000] NET: Registered protocol family 23
[   19.854000] ieee80211_crypt: registered algorithm 'NULL'
[   19.858000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.858000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.908000] usbcore: registered new interface driver hiddev
[   19.930000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   19.930000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.931000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.931000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   19.933000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.999000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   19.999000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[   19.999000] usbcore: registered new interface driver usbhid
[   19.999000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   20.020000] cs: IO port probe 0x100-0x3af: clean.
[   20.022000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.023000] cs: IO port probe 0x820-0x8ff: clean.
[   20.023000] cs: IO port probe 0xc00-0xcf7: clean.
[   20.024000] cs: IO port probe 0xa00-0xaff: clean.
[   20.277000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   20.277000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   20.325000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   20.441000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   20.444000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   20.444000] nsc-ircc, chip->init
[   20.444000] nsc-ircc, Found chip at base=0x02e
[   20.444000] nsc-ircc, driver loaded (Dag Brattli)
[   20.444000] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.444000] nsc-ircc, Found chip at base=0x02e
[   20.444000] nsc-ircc, driver loaded (Dag Brattli)
[   20.444000] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.444000] nsc-ircc, chip->init
[   20.444000] nsc-ircc, Found chip at base=0x02e
[   20.444000] nsc-ircc, driver loaded (Dag Brattli)
[   20.444000] pnp: Device 00:0a disabled.
[   20.747000] lp: driver loaded but no devices found
[   20.817000] fuse init (API version 7.8)
[   20.871000] Adding 1919728k swap on /dev/disk/by-uuid/5106170f-b2a6-439e-814a-c9093fdc2554.  Priority:-1 extents:1 across:1919728k
[   20.980000] EXT3 FS on sda2, internal journal
[   21.778000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   22.028000] No dock devices found.
[   22.048000] ibm_acpi: ec object not found
[   22.285000] ACPI: AC Adapter [ADP0] (on-line)
[   22.305000] Using specific hotkey driver
[   22.338000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.390000] input: Lid Switch as /class/input/input4
[   22.390000] ACPI: Lid Switch [LID0]
[   22.390000] input: Power Button (CM) as /class/input/input5
[   22.390000] ACPI: Power Button (CM) [PWRB]
[   22.390000] input: Sleep Button (CM) as /class/input/input6
[   22.390000] ACPI: Sleep Button (CM) [SLPB]
[   22.480000] ACPI: Battery Slot [BAT0] (battery present)
[   22.480000] ACPI: Battery Slot [BAT1] (battery absent)
[   22.534000] pcc_acpi: loading...
[   25.142000] ttyS1: LSR safety check engaged!
[   26.156000] r8169: eth0: link down
[   28.594000] ppdev: user-space parallel port driver
[   28.764000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   28.770000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[   28.770000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   28.788000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.492000] apm: BIOS not found.
[   29.676000] Bluetooth: Core ver 2.11
[   29.676000] NET: Registered protocol family 31
[   29.676000] Bluetooth: HCI device and connection manager initialized
[   29.676000] Bluetooth: HCI socket layer initialized
[   29.712000] Bluetooth: L2CAP ver 2.8
[   29.712000] Bluetooth: L2CAP socket layer initialized
[   29.796000] Bluetooth: RFCOMM socket layer initialized
[   29.796000] Bluetooth: RFCOMM TTY layer initialized
[   29.796000] Bluetooth: RFCOMM ver 1.8
[   30.769000] [fglrx] total      GART = 130023424
[   30.770000] [fglrx] free       GART = 114032640
[   30.770000] [fglrx] max single GART = 114032640
[   30.770000] [fglrx] total      LFB  = 134086656
[   30.770000] [fglrx] free       LFB  = 115871744
[   30.770000] [fglrx] max single LFB  = 115871744
[   30.770000] [fglrx] total      Inv  = 0
[   30.771000] [fglrx] free       Inv  = 0
[   30.771000] [fglrx] max single Inv  = 0
[   30.771000] [fglrx] total      TIM  = 0
[   41.853000] NET: Registered protocol family 10
[   41.853000] lo: Disabled Privacy Extensions
[   41.854000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   41.854000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   49.434000] NET: Registered protocol family 17
[   49.516000] ieee80211_crypt: registered algorithm 'WEP'
[   49.619000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   66.888000] eth1: no IPv6 routers present
[  107.622000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  107.623000] printk: 4 messages suppressed.
[  107.623000] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  107.691000] NTFS volume version 3.1.

---

### Post by binger on 2007-08-17
So I booted the 2.6.20.15 kernal, and no dvd/cd drive still. I booted up Windows XP and to my astonishment my DVD/CD dissappeared in windows as well!!!  The BIOS still detects the drive.  But neither of my OSes see it.  I can launch Boot Discs from the drive, but thats it.  
Would Grub rewriting the MBR have anything to do with this?
Why would installing Ubuntu effect my hardware in WinXP?
please help meeeeeeeeeeeeeeeeeeeeee

---

### Post by cancertoast on 2007-11-22
I have a Sager NP5760 and have the same exact problem.  This issue also occurs while using Vista64 too.  I have looked around and have found no information regarding a real work around,  Heck, I even asked on the SA forums and people  refuse to believe that something is wrong, it must be my drive or a worm. :rolleyes:.  So for the time being I am running Vista...  My Linux partition sits dormant and invisible until this bug is fixed.

---

### Post by Mike Armstrong on 2007-11-22
Does it appear if you type  [mount] in a terminal, without the brackets and without arguments? If so it could just be one of the problems I have come to regard as ubuntu misdirection errors. An ipod version of which has given me a prize headache., If it does show up here you may glean enough information to make it mount and work.

---

### Post by cancertoast on 2007-11-23
No.  I just tried out Mint Linux ( I like it) but now i have the same problem.  Both my linux and vista installs can not see my drive.

---

### Post by meierfra on 2007-11-27
I have seen a couple of  cases where grub makes the "DVD-Drive"  disappear. People usually  solve it by using a different boot loader. I would like to try to make it work with   Grub. But I'm not sure that my method works. I would  try it out myself but none of my computers have that problem. Are you willing to do an experiment? (Nothing dangerous)

If yes would you post the output of

```
sudo fdisk -l
```

to get started

---

### Post by cancertoast on 2007-11-27
I am willing to start this.  I will need to reinstall ubuntu, so I may not be able to get to this tonight.  I hope that this is not to much trouble for you?

---

### Post by meierfra on 2007-11-27
> I hope that this is not to much trouble for you?

Not  at all.

Do you have a Vista CD and  Ubuntu Live CD?

---

### Post by cancertoast on 2007-11-27
Yes I do.  I just made a small partition for ubuntu and have installed Gutsy on to it.  At the moment I am running patches.

edit:

Ok I ran that command and it spit this back.

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd787a40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7783    62513152    7  HPFS/NTFS
/dev/sda2            7784        9606    14643247+  83  Linux
/dev/sda3            9607        9729      987997+  82  Linux swap / Solaris


```

---

### Post by meierfra on 2007-11-28
I'm feeling really stupid right now: Do you have a working CD drive on your Laptop (in addition to the DVD drive which is not working?


More precisely are you able to boot from a CD?

---

### Post by cancertoast on 2007-11-28
> **meierfra said:**
> I'm feeling really stupid right now: Do you have a working CD drive on your Laptop (in addition to the DVD drive which is not working?

I am running on a Sager NP5760 laptop.  It has one CD/DVD r/rw-rom drive.

---

### Post by meierfra on 2007-11-28
Did you see my edit? Are able to boot from  a CD?

---

### Post by cancertoast on 2007-11-28
Yes I am able to read cds fine as I boot.  The drive only becomes invisible once either of my OSs load.

---

### Post by meierfra on 2007-11-28
Good

Step 1) Boot from the Vista CD/DVD and put Vista back in charge of the MBR:

 click on "Repair your Computer"
Select your Vista installation, and then click "Next >"
Click on command prompt
At the prompt type:

```
Bootrec /FixMBR

exit

```

Reboot. You will boot directly into Vista. Check whether you DVD drive is working.

If it's working, boot from the Ubuntu Live CD and report back.

---

### Post by cancertoast on 2007-11-28
This is all quite tricksy!  Unfortunately however I must cut this to an end for tonight.  I need to wake up early tomorrow for work and a few errands.  Let's resume this tomorrow evening.  :)

---

### Post by meierfra on 2007-11-28
That's fine. It's getting late for me too.

---

### Post by meierfra on 2007-11-28
In case that Step 1) was successful,  (that is, you can boot into Vista and the DVD drive is working) proceed as follows:

Step 2) Put Grub back in charge of the MBR, but without embedding the stage1.5 files: 

Open a terminal (Applications->Accessories->Terminal) and type

```
sudo grub
```
and then at the "grub>" prompt
```

root (hd0,1)

install /boot/grub/stage1 (hd0)  (hd0,1)/boot/grub/stage2 p /boot/grub/menu.lst

```

Reboot. You should  get to the  grub menu and  should be able to  boot into Vista and Ubuntu. 

And if you are really really lucky, the DVD drive   will be  working in both systems.

If the DVD drive is not working, you can repeat Step 1)  to get your DVD -drive back.  In this case I will help you  install a different boot loader.

---

### Post by cancertoast on 2007-11-28
I am going to go ahead and put vista back in charge of the MBR.  I will monitor this thread to see when you get back online.

---

### Post by meierfra on 2007-11-28
I just got home but will leave in 20 Minutes. Should be enough time for the first step.

---

### Post by cancertoast on 2007-11-28
It seems that I can not get to the recovery console via the vista disc.  I am guessing that this is happening because the disc is the Recovery DVD-ROM, not an actual Windows Vista Disc.  (I will purchase an actual disc at somepoint but not any time soon :/.)

---

### Post by meierfra on 2007-11-28
Got to leave. Will be back in two hour (and will be available for the next five hours after that))

---

### Post by meierfra on 2007-11-28
There are various other ways to restore the MBR. Try  the third method in this post
[URL="http://ubuntuforums.org/showthread.php?t=616540#2"]
http://ubuntuforums.org/showthread.php?t=616540#2[/URL]

(ignore the last sentence, your windows drive is /dev/sda. So you  don't need to modify any of the code)

Reboot and check whether you  DVD drive works.

---

### Post by cancertoast on 2007-11-28
Ok I installed it and ran
```

sudo ms-sys -m /dev/sda

```

An my Vista install picked right back up with a recognizable dvd-rom.

ed:  Don't worry, I debated on following it all word for word but just ran it from my install instead.

---

### Post by meierfra on 2007-11-28
Do make your life a little easier: You don't need to use the LIve CD. You can do the same thing from ubuntu.

Edit: Too late.

---

### Post by meierfra on 2007-11-28
Good news.   But it also means there is  virtually no chance Step 2 will  work. Well, Step 2 will put grub back in charge of the booting. But I'm almost certain that your DVD drive won't be working.  It won't hurt anything, so  you can give it a try it

In the mean time, I'll write up instruction how to use "lilo" instead "grub".

---

### Post by cancertoast on 2007-11-28
> **meierfra said:**
> Good news.   But it also means there is  virtually no chance Step 2 will  work. Well, Step 2 will put grub back in charge of the booting. But I'm almost certain that your DVD drive won't be working.  It won't hurt anything, so  you can give it a try it

In the mean time, I'll write up instruction how to use "lilo" instead "grub".


Please do!  I think I would rather use Lilo and save myself time.  Just a reminder, I am a complete linux novice, color pictures are a plus!  :lolflag:

---

### Post by meierfra on 2007-11-28
Actually installing lilo will be easier from ubuntu than from the LiveCD. So carry out Step 2)   and boot into  Ubuntu. (if you copy and paste my code from Step 2, it shouldn't take very long)


To install lilo open a terminal and type:

```
sudo apt-get install lilo
```

Create and open a new file "/etc/lilo.conf" via

```
gksudo gedit /etc/lilo.conf &
```

Copy and paste this into the file:


> 
lba32
boot=/dev/sda
root=/dev/sda2
prompt
timeout=50

image=/boot/vmlinuz-2.6.22-14-generic
	label="Ubuntu"
	initrd=/boot/initrd.img-2.6.22-14-generic
        append="ro quiet splash"
	read-only


image=/boot/vmlinuz-2.6.22-14-generic
	label="UbuntuRecovery"
	initrd=/boot/initrd.img-2.6.22-14-generic
        append="ro single"
	read-only

image=/boot/memtest86+.bin
	label="Memory Test+"
	read-only

other=/dev/sda1
label="Vista"


Type 

```
uname -a
```
in the terminal   and make sure "2.6.22-14-generic" appears in the output. If not use the numbers from "uname" in place of  "2.6.22-14-generic"

Save the file.

In the terminal

```
sudo lilo 
```

Reboot. You should now get a lilo menu in place of the grub menu. And hopefully you can boot  into ubuntu and windows and your DVD-drive is working.


Sorry,  this simple "lilo.conf"  won't give you a  fancy boot screen.  All I know about lilo I learned today. And I don't want to try anything which might not work.

---

### Post by cancertoast on 2007-11-29
Sorry to just disappear, I have grub back up and running.  I will install lilo tomorrow after work.  It is now time for bed!

---

### Post by cancertoast on 2007-11-29
I am going to go ahead and claim victory and success.  Ubuntu now picks up on the fact that my drive is a cdrom/dvd-rw drive.  I will assume that Vista works fine too.   
Thanks much friend!  I was making this out to be harder than I thought it was, all I needed was a guide.  :)

I do have a question though, when updates are released (specifically kernel upgrades) will I need to manually update lilo?

---

### Post by meierfra on 2007-11-29
> I was making this out to be harder than I thought it was,

And if I  would have told you to use lilo immediately instead of trying to make it work with grub, it would have been really easy. Step 1 and Step 2  turned out to be waste of our time. Sorry about that.

> I do have a question though, when updates are released (specifically kernel upgrades) will I need to manually update lilo?

Yes, that is  one of the disadvantages of lilo. You have to edit lilo.conf and then run "sudo lilo"

So I assume the DVD drive was not working after Step 2 and before lilo?

---

### Post by cancertoast on 2007-11-29
> **meierfra said:**
> And if I  would have told you to use lilo immediately instead of trying to make it work with grub, it would have been really easy. Step 1 and Step 2  turned out to be waste of our time. Sorry about that.



Yes, that is  one of the disadvantages of lilo. You have to edit lilo.conf and then run "sudo lilo"

So I assume the DVD drive was not working after Step 2 and before lilo?

The Drive was nonexistant before lilo was installed

---

### Post by vincencollins on 2007-12-12
I tried to install LILO last night and now I am unable to boot at all.  I can only get to the busybox console now.  I was searching for a solution and I found this [page]("http://users.bigpond.net.au/hermanzone/p4.html") that was very helpful.  I thought I would post it for others that might have some issues with getting LILO installed.

---

### Post by vonchiz on 2008-01-24
I had this same problem and couldn't get anyone to answer my posts.  It was a bear to fix, but here's how I did it.

From what I could tell, grub doesn't play nice with some removable laptop drives.  I tried several 3rd party boot loaders and either the problem replicated or Grub wouldn't boot linux.  

Step 1.  Replace Grub with Lilo as loutlined here
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)
I used the apt-get option to install Lilo, the directions are good.
MAKE SURE you install Lilo on your Ubuntu partition and not on your MBR.

Step 2.  Install GAG as my bootloader.  Very straightforward.  Linux won't boot if you have your bootloader installed on your MBR.

If you know how to install grub on your linux partition and not MBR, it would work also.  I got sick of #($(ing around with it and switched to Lilo.

Hope this helps.

---

