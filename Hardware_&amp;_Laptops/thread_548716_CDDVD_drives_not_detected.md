---
title: "CD/DVD drives not detected"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by numeritos on 2007-09-11
I'm running Kubuntu Feisty Fawn with all the last updates. Both my DVD-RW and CD-RW IDE drivers are not detected. To install the OS I had to use the kernel boot option "generic.all_generic_ide". I quit using it now that I installed it because if I did my SATAII harddriver performed very poorly (hdparm -t returned 3,80MB/sec). The problem is that now I don't have any optical drive working because they are both IDE!

Is there a way to fix this without using that kernel boot option?

Here's my lspci:
```
# lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

My lsmod:
```
# lsmod
Module                  Size  Used by
vmnet                  44596  13
vmblock                16288  3
vmmon                 452012  0
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
vboxdrv                54664  0
ppdev                  10116  0
acpi_cpufreq           10056  0
cpufreq_stats           7360  0
cpufreq_powersave       2688  0
cpufreq_userspace       5408  0
cpufreq_conservative     8200  0
cpufreq_ondemand        9228  2
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
dev_acpi               12292  0
tc1100_wmi              8068  0
pcc_acpi               13184  0
sony_acpi               6284  0
battery                10756  0
asus_acpi              17308  0
ac                      6020  0
sbs                    15652  0
container               5248  0
button                  8720  0
dock                   10268  0
video                  16388  0
backlight               7040  1 asus_acpi
i2c_ec                  6016  1 sbs
nls_iso8859_1           5120  1
nls_cp437               6784  1
vfat                   14208  1
fat                    53916  1 vfat
ext2                   66824  1
ipv6                  268960  10
parport_pc             36388  0
lp                     12452  0
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  1
snd_hda_intel          21912  5
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               4713780  22
i2c_core               22656  2 i2c_ec,nvidia
af_packet              23816  2
snd                    54020  18 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
serio_raw               7940  0
pcspkr                  4224  0
psmouse                38920  0
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
intel_agp              26140  1
agpgart                35400  2 nvidia,intel_agp
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
tsdev                   8768  0
evdev                  11008  3
ext3                  133128  2
jbd                    59816  1 ext3
mbcache                 9604  2 ext2,ext3
sg                     36252  0
sd_mod                 23428  6
generic                 5124  0 [permanent]
floppy                 59524  0
r8169                  32392  0
ehci_hcd               34188  0
ata_generic             9092  0
ata_piix               15492  5
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  3 sg,sd_mod,libata
uhci_hcd               25360  0
usbcore               134280  3 ehci_hcd,uhci_hcd
thermal                14856  0
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

```

My dmesg:
```
# dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009cc00 end: 000000000009cc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009cc00 size: 0000000000003400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e3000 size: 000000000001d000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007feb0000 end: 000000007ffb0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007ffb0000 size: 000000000000e000 end: 000000007ffbe000 type: 3
[    0.000000] copy_e820_map() start: 000000007ffbe000 size: 0000000000032000 end: 000000007fff0000 type: 4
[    0.000000] copy_e820_map() start: 000000007fff0000 size: 0000000000010000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009cc00 (usable)
[    0.000000]  BIOS-e820: 000000000009cc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524208) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524208
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524208
[    0.000000] On node 0 totalpages: 524208
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292529 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9330
[    0.000000] ACPI: RSDT (v001 052107 RSDT1013 0x20070521 MSFT 0x00000097) @ 0x7ffb0000
[    0.000000] ACPI: FADT (v001 052107 FACP1013 0x20070521 MSFT 0x00000097) @ 0x7ffb0200
[    0.000000] ACPI: MADT (v001 052107 APIC1013 0x20070521 MSFT 0x00000097) @ 0x7ffb0390
[    0.000000] ACPI: MCFG (v001 052107 OEMMCFG  0x20070521 MSFT 0x00000097) @ 0x7ffb0400
[    0.000000] ACPI: OEMB (v001 052107 OEMB1013 0x20070521 MSFT 0x00000097) @ 0x7ffbe040
[    0.000000] ACPI: GSCI (v001 052107 GMCHSCI  0x20070521 MSFT 0x00000097) @ 0x7ffbe0c0
[    0.000000] ACPI: SSDT (v001 DpgPmm    CpuPm 0x00000012 INTL 0x20051117) @ 0x7ffc0a10
[    0.000000] ACPI: DSDT (v001  0AAAA 0AAAA000 0x00000000 INTL 0x20051117) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] Detected 2007.985 MHz processor.
[   24.179459] Built 1 zonelists.  Total pages: 520113
[   24.179462] Kernel command line: root=UUID=e4308fa0-6745-4ca2-ae6a-bece9aa105bd ro quiet splash
[   24.179580] mapped APIC to ffffd000 (fee00000)
[   24.179582] mapped IOAPIC to ffffc000 (fec00000)
[   24.179584] Enabling fast FPU save and restore... done.
[   24.179586] Enabling unmasked SIMD FPU exception support... done.
[   24.179592] Initializing CPU#0
[   24.179637] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   24.180788] Console: colour VGA+ 80x25
[   24.181010] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.181254] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.242986] Memory: 2067752k/2096832k available (1993k kernel code, 27716k reserved, 900k data, 328k init, 1179328k highmem)
[   24.242994] virtual kernel memory layout:
[   24.242994]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   24.242995]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.242996]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.242997]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.242998]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   24.242999]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   24.243000]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   24.243003] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.319378] Calibrating delay using timer specific routine.. 4018.96 BogoMIPS (lpj=8037935)
[   24.319411] Security Framework v1.0.0 initialized
[   24.319417] SELinux:  Disabled at boot.
[   24.319430] Mount-cache hash table entries: 512
[   24.319541] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   24.319547] monitor/mwait feature present.
[   24.319549] using mwait in idle threads.
[   24.319552] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.319554] CPU: L2 cache: 2048K
[   24.319556] CPU: Physical Processor ID: 0
[   24.319558] CPU: Processor Core ID: 0
[   24.319559] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   24.319567] Compat vDSO mapped to ffffe000.
[   24.319570] Remapping vsyscall page to ffffe000
[   24.319581] Checking 'hlt' instruction... OK.
[   24.335428] SMP alternatives: switching to UP code
[   24.335714] Early unpacking initramfs... done
[   24.598155] ACPI: Core revision 20060707
[   24.598363] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   24.600622] CPU0: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz stepping 02
[   24.600636] SMP alternatives: switching to SMP code
[   24.600695] Booting processor 1/1 eip 3000
[   24.611044] Initializing CPU#1
[   24.690674] Calibrating delay using timer specific routine.. 4016.05 BogoMIPS (lpj=8032110)
[   24.690679] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   24.690683] monitor/mwait feature present.
[   24.690686] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.690687] CPU: L2 cache: 2048K
[   24.690689] CPU: Physical Processor ID: 0
[   24.690690] CPU: Processor Core ID: 1
[   24.690691] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   24.691105] CPU1: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz stepping 02
[   24.691121] Total of 2 processors activated (8035.02 BogoMIPS).
[   24.691263] ENABLING IO-APIC IRQs
[   24.691427] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.838403] checking TSC synchronization across 2 CPUs: passed.
[    0.003990] Brought up 2 CPUs
[    0.181636] migration_cost=21
[    0.181854] Booting paravirtualized kernel on bare hardware
[    0.181914] Time: 21:15:02  Date: 08/11/107
[    0.181936] NET: Registered protocol family 16
[    0.182001] EISA bus registered
[    0.182005] ACPI: bus type pci registered
[    0.182127] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.182128] PCI: Using configuration type 1
[    0.182130] Setting up standard PCI resources
[    0.188352] ACPI: Interpreter enabled
[    0.188354] ACPI: Using IOAPIC for interrupt routing
[    0.188537] Error attaching device data
[    0.188567] Error attaching device data
[    0.188598] Error attaching device data
[    0.188628] Error attaching device data
[    0.188755] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.188763] PCI: Probing PCI hardware (bus 00)
[    0.189802] Boot video device is 0000:01:00.0
[    0.190232] PCI: Transparent bridge - 0000:00:1e.0
[    0.190289] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.193201] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.197852] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.198604] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.198857] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.199349] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.199576] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.199803] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.200026] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.200250] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.200473] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.200697] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.200923] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.201018] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.201028] pnp: PnP ACPI init
[    0.204618] pnp: PnP ACPI: found 17 devices
[    0.204622] PnPBIOS: Disabled by ACPI PNP
[    0.204653] PCI: Using ACPI for IRQ routing
[    0.204655] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.215025] NET: Registered protocol family 8
[    0.215027] NET: Registered protocol family 20
[    0.215855] pnp: 00:0a: ioport range 0xa00-0xadf has been reserved
[    0.215858] pnp: 00:0a: ioport range 0xae0-0xaef has been reserved
[    0.216094] PCI: Bridge: 0000:00:01.0
[    0.216096]   IO window: c000-cfff
[    0.216100]   MEM window: fc000000-fe9fffff
[    0.216103]   PREFETCH window: d0000000-dfffffff
[    0.216106] PCI: Bridge: 0000:00:1c.0
[    0.216107]   IO window: disabled.
[    0.216111]   MEM window: disabled.
[    0.216113]   PREFETCH window: disabled.
[    0.216117] PCI: Bridge: 0000:00:1c.4
[    0.216120]   IO window: d000-dfff
[    0.216124]   MEM window: fea00000-feafffff
[    0.216127]   PREFETCH window: disabled.
[    0.216131] PCI: Bridge: 0000:00:1c.5
[    0.216133]   IO window: e000-efff
[    0.216137]   MEM window: feb00000-febfffff
[    0.216140]   PREFETCH window: disabled.
[    0.216144] PCI: Bridge: 0000:00:1e.0
[    0.216145]   IO window: disabled.
[    0.216149]   MEM window: disabled.
[    0.216152]   PREFETCH window: disabled.
[    0.216164] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.216169] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.216184] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    0.216188] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.216203] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[    0.216207] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.216222] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[    0.216226] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.216235] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.216256] NET: Registered protocol family 2
[    0.251552] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.251635] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.251998] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.252184] TCP: Hash tables configured (established 131072 bind 65536)
[    0.252186] TCP reno registered
[    0.263591] checking if image is initramfs... it is
[    0.780787] Freeing initrd memory: 6778k freed
[    0.781291] audit: initializing netlink socket (disabled)
[    0.781303] audit(1189545302.520:1): initialized
[    0.781381] highmem bounce pool size: 64 pages
[    0.781447] VFS: Disk quotas dquot_6.5.1
[    0.781462] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.781502] io scheduler noop registered
[    0.781504] io scheduler anticipatory registered
[    0.781505] io scheduler deadline registered
[    0.781514] io scheduler cfq registered (default)
[    0.781742] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.781774] assign_interrupt_mode Found MSI capability
[    0.781776] Allocate Port Service[0000:00:01.0:pcie00]
[    0.781850] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.781886] assign_interrupt_mode Found MSI capability
[    0.781888] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.781917] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.782000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.782037] assign_interrupt_mode Found MSI capability
[    0.782038] Allocate Port Service[0000:00:1c.4:pcie00]
[    0.782065] Allocate Port Service[0000:00:1c.4:pcie02]
[    0.782146] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.782182] assign_interrupt_mode Found MSI capability
[    0.782184] Allocate Port Service[0000:00:1c.5:pcie00]
[    0.782210] Allocate Port Service[0000:00:1c.5:pcie02]
[    0.782344] isapnp: Scanning for PnP cards...
[    1.134656] isapnp: No Plug & Play device found
[    1.151775] Real Time Clock Driver v1.12ac
[    1.151819] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.151925] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.152384] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.152591] mice: PS/2 mouse device common for all mice
[    1.153053] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.153171] input: Macintosh mouse button emulation as /class/input/input0
[    1.153201] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.153204] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.153374] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.155499] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.155502] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.155578] EISA: Probing bus 0 at eisa.0
[    1.155604] EISA: Detected 0 cards.
[    1.177000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.185619] TCP cubic registered
[    1.185626] NET: Registered protocol family 1
[    1.185645] Starting balanced_irq
[    1.185653] Using IPI No-Shortcut mode
[    1.185728] ACPI: (supports S0 S1<6>Time: tsc clocksource has been installed.
[    1.185746]  S3 S4 S5)
[    1.185774]   Magic number: 7:791:297
[    1.185785]   hash matches device ttywe
[    1.185970] Freeing unused kernel memory: 328k freed
[    2.357433] Capability LSM initialized
[    2.388821] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [DpgPmm] OemTableId [ P001Ist] [20060707]
[    2.389268] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [DpgPmm] OemTableId [ P002Ist] [20060707]
[    2.389333] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.389338] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.698923] usbcore: registered new interface driver usbfs
[    2.698943] usbcore: registered new interface driver hub
[    2.698964] usbcore: registered new device driver usb
[    2.724238] USB Universal Host Controller Interface driver v3.0
[    2.724285] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    2.724295] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    2.724298] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.724386] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.724413] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000bc00
[    2.724499] usb usb1: configuration #1 chosen from 1 choice
[    2.724522] hub 1-0:1.0: USB hub found
[    2.724527] hub 1-0:1.0: 2 ports detected
[    2.728457] SCSI subsystem initialized
[    2.732320] libata version 2.20 loaded.
[    2.767645] Floppy drive(s): fd0 is 1.44M
[    2.790359] FDC 0 is a post-1991 82077
[    2.830706] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[    2.830716] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    2.830720] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.830738] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.830763] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000b880
[    2.830832] usb usb2: configuration #1 chosen from 1 choice
[    2.830854] hub 2-0:1.0: USB hub found
[    2.830859] hub 2-0:1.0: 2 ports detected
[    2.938477] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    2.938485] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    2.938488] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.938508] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    2.938530] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000b800
[    2.938596] usb usb3: configuration #1 chosen from 1 choice
[    2.938615] hub 3-0:1.0: USB hub found
[    2.938620] hub 3-0:1.0: 2 ports detected
[    3.046269] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.046276] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.046279] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.046295] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.046318] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000b480
[    3.046385] usb usb4: configuration #1 chosen from 1 choice
[    3.046405] hub 4-0:1.0: USB hub found
[    3.046410] hub 4-0:1.0: 2 ports detected
[    3.154061] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[    3.154068] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.154071] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.154088] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.154110] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000b400
[    3.154179] usb usb5: configuration #1 chosen from 1 choice
[    3.154198] hub 5-0:1.0: USB hub found
[    3.154202] hub 5-0:1.0: 2 ports detected
[    3.261855] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.261862] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.261865] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.261881] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 6
[    3.261901] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b080
[    3.261970] usb usb6: configuration #1 chosen from 1 choice
[    3.261990] hub 6-0:1.0: USB hub found
[    3.261994] hub 6-0:1.0: 2 ports detected
[    3.369720] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.369726] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.369744] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    3.369757] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.369794] ata1: SATA max UDMA/133 cmd 0x0001b000 ctl 0x0001ac02 bmdma 0x0001a480 irq 20
[    3.369816] ata2: SATA max UDMA/133 cmd 0x0001a880 ctl 0x0001a802 bmdma 0x0001a488 irq 20
[    3.369824] scsi0 : ata_piix
[    3.541524] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[    3.541529] ata1.00: ATA-8: SAMSUNG HD321KJ, CP100-10, max UDMA7
[    3.541532] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.553494] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[    3.553498] ata1.00: configured for UDMA/133
[    3.553505] scsi1 : ata_piix
[    3.725169] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    3.725172] ata2.00: ATA-7: WDC WD1600JS-00MHB1, 10.02E01, max UDMA/133
[    3.725174] ata2.00: 312581808 sectors, multi 16: LBA48
[    3.737132] ata2.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    3.737134] ata2.00: configured for UDMA/133
[    3.737216] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD321KJ  CP10 PQ: 0 ANSI: 5
[    3.737357] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600JS-00M 10.0 PQ: 0 ANSI: 5
[    3.737447] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[    3.737466] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 20
[    3.737479] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    3.737502] ata3: SATA max UDMA/133 cmd 0x0001a000 ctl 0x00019c02 bmdma 0x00019480 irq 20
[    3.737519] ata4: SATA max UDMA/133 cmd 0x00019880 ctl 0x00019802 bmdma 0x00019488 irq 20
[    3.737525] scsi2 : ata_piix
[    3.907179] ATA: abnormal status 0x7F on port 0x0001a007
[    3.907189] scsi3 : ata_piix
[    4.074875] ATA: abnormal status 0x7F on port 0x00019887
[    4.076420] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 21
[    4.076429] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    4.076432] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.076457] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[    4.076483] ehci_hcd 0000:00:1a.7: debug port 1
[    4.076488] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    4.076492] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xfbfffc00
[    4.080360] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.080432] usb usb7: configuration #1 chosen from 1 choice
[    4.080458] hub 7-0:1.0: USB hub found
[    4.080462] hub 7-0:1.0: 4 ports detected
[    4.086566] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[    4.086576] sda: Write Protect is off
[    4.086577] sda: Mode Sense: 00 3a 00 00
[    4.086589] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.086626] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[    4.086633] sda: Write Protect is off
[    4.086635] sda: Mode Sense: 00 3a 00 00
[    4.086646] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.086649]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    4.155739] sd 0:0:0:0: Attached scsi disk sda
[    4.155781] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[    4.155788] sdb: Write Protect is off
[    4.155790] sdb: Mode Sense: 00 3a 00 00
[    4.155801] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.155834] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[    4.155841] sdb: Write Protect is off
[    4.155843] sdb: Mode Sense: 00 3a 00 00
[    4.155854] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.155857]  sdb: sdb1 sdb2 < sdb5 sdb6<6>ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    4.188118] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.188122] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.188142] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    4.188167] ehci_hcd 0000:00:1d.7: debug port 1
[    4.188172] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.188178] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfbfff800
[    4.192053] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.192120] usb usb8: configuration #1 chosen from 1 choice
[    4.192141] hub 8-0:1.0: USB hub found
[    4.192145] hub 8-0:1.0: 8 ports detected
[    4.192169]  sdb7 > sdb3
[    4.192272] sd 1:0:0:0: Attached scsi disk sdb
[    4.195350] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.195367] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.300012] r8169 Gigabit Ethernet driver 2.2LK loaded
[    4.300036] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    4.300059] PCI: Setting latency timer of device 0000:04:00.0 to 64
[    4.300255] eth0: RTL8168b/8111b at 0xf885a000, 00:19:db:b5:5c:0e, IRQ 17
[    4.444952] Attempting manual resume
[    4.444955] swsusp: Resume From Partition 8:2
[    4.444956] PM: Checking swsusp image.
[    4.445098] PM: Resume from disk failed.
[    4.468328] kjournald starting.  Commit interval 5 seconds
[    4.468335] EXT3-fs: mounted filesystem with ordered data mode.
[   10.088727] r8169: eth0: link up
[   10.088733] r8169: eth0: link up
[   10.817558] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.818824] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.918904] Linux agpgart interface v0.102 (c) Dave Jones
[   10.944351] agpgart: Detected an Intel G33 Chipset.
[   10.957115] agpgart: AGP aperture is 256M @ 0x0
[   11.148939] input: PC Speaker as /class/input/input2
[   11.315697] NET: Registered protocol family 17
[   11.366688] nvidia: module license 'NVIDIA' taints kernel.
[   11.618220] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.618228] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   11.618307] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   11.763264] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   11.763279] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   11.771139] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   11.973175] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.269750] fuse init (API version 7.8)
[   12.329825] lp: driver loaded but no devices found
[   12.353616] Adding 2008116k swap on /dev/disk/by-uuid/8fe7c6f9-33da-45a7-f5e6-11fb661785d5.  Priority:-1 extents:1 across:2008116k
[   12.531519] EXT3 FS on sda5, internal journal
[   13.998708] NET: Registered protocol family 10
[   13.998805] lo: Disabled Privacy Extensions
[   16.946705] kjournald starting.  Commit interval 5 seconds
[   16.946970] EXT3 FS on sda6, internal journal
[   16.946973] EXT3-fs: mounted filesystem with ordered data mode.
[   22.169565] No dock devices found.
[   22.180251] Using specific hotkey driver
[   22.218162] input: Power Button (FF) as /class/input/input4
[   22.218276] ACPI: Power Button (FF) [PWRF]
[   22.218897] input: Power Button (CM) as /class/input/input5
[   22.219006] ACPI: Power Button (CM) [PWRB]
[   22.231489] ibm_acpi: ec object not found
[   22.335736] pcc_acpi: loading...
[   24.453379] eth0: no IPv6 routers present
[   25.593306] ppdev: user-space parallel port driver
[   26.231133] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   26.231137] apm: disabled - APM is not SMP safe.
[   26.676150] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   26.676156] vboxdrv: Successfully done.
[   27.032065] Bluetooth: Core ver 2.11
[   27.032462] NET: Registered protocol family 31
[   27.032465] Bluetooth: HCI device and connection manager initialized
[   27.032469] Bluetooth: HCI socket layer initialized
[   27.078408] Bluetooth: L2CAP ver 2.8
[   27.078413] Bluetooth: L2CAP socket layer initialized
[   27.335556] Bluetooth: RFCOMM socket layer initialized
[   27.335567] Bluetooth: RFCOMM TTY layer initialized
[   27.335569] Bluetooth: RFCOMM ver 1.8
[   28.177898] /dev/vmmon[5423]: VMCI: Driver initialized.
[   28.177932] /dev/vmmon[5423]: Module vmmon: registered with major=10 minor=165
[   28.177962] /dev/vmmon[5423]: Module vmmon: initialized
[   28.830035] /dev/vmnet: open called by PID 5476 (vmnet-bridge)
[   28.830243] /dev/vmnet: hub 0 does not exist, allocating memory.
[   28.830424] /dev/vmnet: port on hub 0 successfully opened
[   28.830577] bridge-eth0: enabling the bridge
[   28.830708] bridge-eth0: up
[   28.830814] bridge-eth0: already up
[   28.830933] bridge-eth0: attached
[   29.198975] /dev/vmnet: open called by PID 5514 (vmnet-netifup)
[   29.199163] /dev/vmnet: hub 1 does not exist, allocating memory.
[   29.199332] /dev/vmnet: port on hub 1 successfully opened
[   29.210730] /dev/vmnet: open called by PID 5513 (vmnet-dhcpd)
[   29.210918] /dev/vmnet: port on hub 1 successfully opened
[   29.225350] /dev/vmnet: open called by PID 5532 (vmnet-netifup)
[   29.225547] /dev/vmnet: hub 8 does not exist, allocating memory.
[   29.225727] /dev/vmnet: port on hub 8 successfully opened
[   29.254179] /dev/vmnet: open called by PID 5542 (vmnet-dhcpd)
[   29.254192] /dev/vmnet: port on hub 8 successfully opened
[   29.300904] /dev/vmnet: open called by PID 5551 (vmnet-natd)
[   29.301087] /dev/vmnet: port on hub 8 successfully opened
[   39.748446] vmnet1: no IPv6 routers present
[   40.187628] vmnet8: no IPv6 routers present
[   40.794471] eth0: no IPv6 routers present

```


Any ideas?

---

### Post by dabl on 2007-09-11
Are you sure the optical drive is set up appropriately in BIOS?  Ubuntu takes its hardware information from BIOS, so that's the first place to try some alternative settings, to see if that's the source of the problem. :)

---

### Post by numeritos on 2007-09-11
> **dabl said:**
> Are you sure the optical drive is set up appropriately in BIOS?  Ubuntu takes its hardware information from BIOS, so that's the first place to try some alternative settings, to see if that's the source of the problem. :)
Like I said in my post, if I put the kernel boot option "generic.all_generic_ide" all my  optical IDE drivers are detected, so it's set up correctly in BIOS :)

---

### Post by dabl on 2007-09-11
Can you post your /etc/fstab file?

EDIT:  This is probably significant:

> [    3.737525] scsi2 : ata_piix
[    3.907179] ATA: abnormal status 0x7F on port 0x0001a007
[    3.907189] scsi3 : ata_piix
[    4.074875] ATA: abnormal status 0x7F on port 0x00019887


Yep, a quick Google found this: [http://ubuntuforums.org/archive/index.php/t-504589.html](http://ubuntuforums.org/archive/index.php/t-504589.html)


You need to search for "ata piix" and see if there is a kernel boot option that you need to put in /boot/grub/menu.lst

;-)

---

### Post by numeritos on 2007-09-11
> **dabl said:**
> Can you post your /etc/fstab file?

EDIT:  This is probably significant:




Yep, a quick Google found this: [http://ubuntuforums.org/archive/index.php/t-504589.html](http://ubuntuforums.org/archive/index.php/t-504589.html)


You need to search for "ata piix" and see if there is a kernel boot option that you need to put in /boot/grub/menu.lst

;-)
Yeap, it must be significant but I really don't know how to fix it anyway. 

As you can see in my "lsmod" output the module "ata_piix" is loaded, but as stated in the link you posted, it must be buggy. Seems I'll need to choose between HD performance or my IDE drivers... Pretty upsetting

My /etc/fstab output (don't know how it'll help, but posting it as requested):
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e4308fa0-6745-4ca2-ae6a-bece9aa105bd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=567a84cc-dc84-43b2-9b66-242b13421a3d /boot           ext2    defaults        0       2
# /dev/sda6
UUID=b8de606f-e201-4ea6-9366-1edb4eada53b /home           ext3    defaults        0       2
# /dev/sda7
UUID=46E2-AAE2  /multimedia     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=8fe7c6f9-33da-45a7-f5e6-11fb661785d5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by rileyrg on 2007-09-13
I have same as the OP.

Put a SATA DVD rom in instead of the IDE one. Set the BIOS to compatible and you can then install the Ubuntu feisty 7.04 or even Debian Business Card NetInst. Sound and net will work with Ubuntu but not Debian.

---

### Post by numeritos on 2007-09-13
> **rileyrg said:**
> I have same as the OP.

Put a SATA DVD rom in instead of the IDE one. Set the BIOS to compatible and you can then install the Ubuntu feisty 7.04 or even Debian Business Card NetInst. Sound and net will work with Ubuntu but not Debian.
Feisty is already installed. I don't want to sound rude, but you say "put a SATA DVD rom" like they were cost free... Unfortunately, I can't afford to buy another DVD drive. I would very much like the IDE one to work :(

---

### Post by jmate24 on 2007-09-13
i have been having a simmilar problem ever since i installed lame. When i try to use sound juicer it says "No CD-ROM drives found: Sound Juicer could not find any CD-ROM drives to read."
But i have the correct configuration in my bios and nautilus(Places==>Computer). they both show up i have also installed nautilus-audio-convert and mpg123-alsa, mpg123-esd, lame, lame extras. all of gstreamer-0.10, a couple of gstreamer-0.8-0, gnome baker,devede, dvd95, audacity, beep mediaplayer, bmpx, dvd::rip, thoggen, gxine, xine, xmms, qdvdauthor, etc...
but i do remember installing a package to allow xmms to read the CD-RW/DVD-RAM drives(1 DVD-RAM, 1 CD-RW)
could that be the problem?

my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d132b058-3bbf-433b-a84a-f822e135bdb1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4c7f5aaa-02a1-4ea0-a596-84748741b65b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

lspci:
[CODE]/00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: f4000000-f7ffffff
        Capabilities: <access denied>

00:05.0 RAID bus controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
        Subsystem: Silicon Image, Inc. Winic W-680 (Silicon Image 680 based)
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at fc00 [size=8]
        I/O ports at f800 [size=4]
        I/O ports at f400 [size=8]
        I/O ports at f000 [size=4]
        I/O ports at ec00 [size=16]
        Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 20000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:06.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at e800 [size=32]
        Capabilities: <access denied>

00:06.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:06.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) Unknown device 1234
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at e000 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at d400 [size=4]
        I/O ports at d000 [size=16]
        I/O ports at cc00 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 0, IRQ 21
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at c800 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at c400 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at c000 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at bc00 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at b800 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at fdffd000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: VIA Technologies, Inc. DFI KT600-AL Motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Micro-Star International Co., Ltd. Unknown device b014
        Flags: medium devsel, IRQ 23
        I/O ports at b400 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 22
        I/O ports at b000 [size=256]
        Memory at fdffc000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7104
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 10
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fc000000 [disabled] [size=64K]
        Capabilities: <access denied>
/CODE]

If anyone can help that would be greatly appreciated
jmate24:)

---

### Post by Arjent on 2007-09-15
Try going into your boot sequence and altering the order so your cdrom boots after your hard drive.

This may not help your problem, but it is my standard solution for mounting errors. It has worked for me on several occasions.

---

### Post by arcanus on 2007-10-25
I had a similar problem in feisty. But when upgrading to Gutsy it fixed itself. I'm guessing a kernel issue.

---

### Post by numeritos on 2007-10-25
> **arcanus said:**
> I had a similar problem in feisty. But when upgrading to Gutsy it fixed itself. I'm guessing a kernel issue.
Yeah, luckily when I upgraded to Gutsy Gibbon it started working :)

---

