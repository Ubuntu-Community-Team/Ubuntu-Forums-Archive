---
title: "USB drive not found"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by SwordBoy on 2007-03-16
Hi,
I'm trying to get my external 400GB Freecom USB drive to work.  It doesn't seem to be seen at all on the USB interface, as the only entry is my USB microsoft mouse.  The dmesg output says somestuff about a possible USB cable being bad, but the drive works fine on other windows boxes.  I'm not sure what to try or look for to kick the USB into working.  I tried  modprobe usb-storage, but i don't really know what that's supposed to do!  In any case it didn't seem to have the desired effect.



lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


lsmod:
Module                  Size  Used by
usb_storage            73408  0 
libusual               15632  1 usb_storage
usbhid                 42464  0 
binfmt_misc            11784  1 
nfsd                  231844  13 
exportfs                6016  1 nfsd
lockd                  65800  2 nfsd
sunrpc                160188  8 nfsd,lockd
cpufreq_powersave       2048  0 
cpufreq_stats           5892  0 
cpufreq_userspace       4372  0 
cpufreq_ondemand        6944  0 
cpufreq_conservative     7200  0 
freq_table              4996  1 cpufreq_stats
tc1100_wmi              7428  0 
video                  16644  0 
battery                10756  0 
container               4736  0 
sbs                    15776  0 
button                  7056  0 
pcc_acpi               13184  0 
sony_acpi               5516  0 
i2c_ec                  5376  1 sbs
ac                      5892  0 
dev_acpi               11140  0 
asus_acpi              16792  0 
hotkey                 10660  0 
ipv6                  257632  20 
af_packet              21768  0 
nls_utf8                2304  1 
ntfs                  108148  1 
tun                    11648  1 
fuse                   41864  0 
sbp2                   23304  0 
lp                     11972  0 
snd_intel8x0           33436  1 
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
tsdev                   8256  0 
snd_pcm_oss            46080  0 
sg                     35356  0 
snd_mixer_oss          18560  1 snd_pcm_oss
evdev                  10496  1 
serio_raw               7300  0 
snd_pcm                80520  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
nvidia               4552052  36 
snd                    55428  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
rtc                    12596  0 
psmouse                40072  0 
forcedeth              30220  0 
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
floppy                 60676  0 
pcspkr                  3072  0 
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
nvidia_agp              8732  1 
i2c_nforce2             7296  0 
i2c_core               22288  3 i2c_ec,nvidia,i2c_nforce2
agpgart                33456  2 nvidia,nvidia_agp
reiserfs              258688  1 
ehci_hcd               32520  0 
ohci1394               35248  0 
ieee1394              302904  2 sbp2,ohci1394
ohci_hcd               20740  0 
usbcore               130304  6 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
ide_generic             1536  0 
sd_mod                 21648  4 
sata_promise           12292  2 
ide_cd                 32416  0 
cdrom                  37792  1 ide_cd
ide_disk               17664  2 
sata_nv                10116  0 
libata                 73228  2 sata_promise,sata_nv
scsi_mod              141320  5 usb_storage,sbp2,sg,sd_mod,libata
generic                 5252  0 
amd74xx                14364  0 [permanent]
thermal                14600  0 
processor              26028  1 thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability


dmesg:
[17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009cc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009cc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[17179569.184000] 1151MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 524272
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294896 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f73c0
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff3040
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff77c0
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:80000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1804.293 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.336000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.336000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.400000] Memory: 2069628k/2097088k available (1829k kernel code, 26096k reserved, 1038k data, 288k init, 1179584k highmem)
[17179572.400000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.480000] Calibrating delay using timer specific routine.. 3612.24 BogoMIPS (lpj=7224491)
[17179572.480000] Security Framework v1.0.0 initialized
[17179572.480000] SELinux:  Disabled at boot.
[17179572.480000] Mount-cache hash table entries: 512
[17179572.480000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.480000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.480000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.480000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.480000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179572.480000] CPU: AMD Athlon(tm) XP 2200+ stepping 00
[17179572.480000] Checking 'hlt' instruction... OK.
[17179572.496000] SMP alternatives: switching to UP code
[17179572.496000] Freeing SMP alternatives: 0k freed
[17179572.496000] checking if image is initramfs... it is
[17179572.972000] Freeing initrd memory: 5326k freed
[17179572.972000] ACPI: Core revision 20060707
[17179572.980000] ACPI: Looking for DSDT ... not found!
[17179572.984000] ENABLING IO-APIC IRQs
[17179572.984000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.124000] NET: Registered protocol family 16
[17179573.124000] EISA bus registered
[17179573.124000] ACPI: bus type pci registered
[17179573.140000] PCI: PCI BIOS revision 2.10 entry at 0xfbbb0, last bus=3
[17179573.140000] PCI: Using configuration type 1
[17179573.140000] Setting up standard PCI resources
[17179573.156000] ACPI: Interpreter enabled
[17179573.156000] ACPI: Using IOAPIC for interrupt routing
[17179573.156000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.156000] PCI: Probing PCI hardware (bus 00)
[17179573.160000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:09.0
[17179573.160000] Boot video device is 0000:03:00.0
[17179573.160000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.224000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179573.224000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179573.228000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.228000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.228000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.228000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.228000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.228000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.228000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.228000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.228000] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.232000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.232000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.232000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.232000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.232000] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179573.232000] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.232000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.232000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179573.232000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[17179573.232000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179573.232000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179573.232000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179573.236000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179573.240000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.240000] pnp: PnP ACPI init
[17179573.248000] pnp: PnP ACPI: found 15 devices
[17179573.248000] PnPBIOS: Disabled by ACPI PNP
[17179573.248000] PCI: Using ACPI for IRQ routing
[17179573.248000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.308000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[17179573.308000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[17179573.308000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[17179573.308000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[17179573.308000] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[17179573.308000] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[17179573.308000] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[17179573.308000] pnp: 00:01: ioport range 0x5040-0x507f has been reserved
[17179573.308000] PCI: Bridge: 0000:00:08.0
[17179573.308000]   IO window: 9000-9fff
[17179573.308000]   MEM window: ec000000-ecffffff
[17179573.308000]   PREFETCH window: disabled.
[17179573.308000] PCI: Bridge: 0000:00:1e.0
[17179573.308000]   IO window: disabled.
[17179573.308000]   MEM window: e9000000-ebffffff
[17179573.308000]   PREFETCH window: d0000000-dfffffff
[17179573.308000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179573.308000] NET: Registered protocol family 2
[17179573.348000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.348000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179573.348000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.348000] TCP: Hash tables configured (established 262144 bind 65536)
[17179573.348000] TCP reno registered
[17179573.348000] audit: initializing netlink socket (disabled)
[17179573.348000] audit(1174065433.348:1): initialized
[17179573.348000] highmem bounce pool size: 64 pages
[17179573.348000] VFS: Disk quotas dquot_6.5.1
[17179573.348000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.348000] Initializing Cryptographic API
[17179573.348000] io scheduler noop registered
[17179573.348000] io scheduler anticipatory registered
[17179573.348000] io scheduler deadline registered
[17179573.348000] io scheduler cfq registered (default)
[17179573.348000] isapnp: Scanning for PnP cards...
[17179573.704000] isapnp: No Plug & Play device found
[17179573.728000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.728000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.728000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.728000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.728000] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.728000] mice: PS/2 mouse device common for all mice
[17179573.728000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.728000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.728000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.728000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.732000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.732000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.732000] EISA: Probing bus 0 at eisa.0
[17179573.732000] Cannot allocate resource for EISA slot 4
[17179573.732000] Cannot allocate resource for EISA slot 5
[17179573.732000] EISA: Detected 0 cards.
[17179573.732000] TCP bic registered
[17179573.732000] NET: Registered protocol family 1
[17179573.732000] NET: Registered protocol family 8
[17179573.732000] NET: Registered protocol family 20
[17179573.732000] Using IPI Shortcut mode
[17179573.732000] ACPI: (supports S0 S1 S4 S5)
[17179573.732000] Freeing unused kernel memory: 288k freed
[17179573.756000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.860000] Capability LSM initialized
[17179574.892000] ACPI: Fan [FAN] (on)
[17179574.896000] ACPI: Thermal Zone [THRM] (31 C)
[17179575.320000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179575.320000] NFORCE2: chipset revision 162
[17179575.320000] NFORCE2: not 100% native mode: will probe irqs later
[17179575.320000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[17179575.320000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[17179575.320000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179575.320000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179575.320000] Probing IDE interface ide0...
[17179575.608000] hda: Maxtor 6Y060L0, ATA DISK drive
[17179576.280000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.280000] Probing IDE interface ide1...
[17179577.016000] hdc: HL-DT-ST DVDRAM GSA-4167B, ATAPI CD/DVD-ROM drive
[17179577.352000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.360000] SCSI subsystem initialized
[17179577.364000] libata version 1.20 loaded.
[17179577.372000] hda: max request size: 128KiB
[17179577.380000] hda: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179577.380000] hda: cache flushes supported
[17179577.380000]  hda: hda1
[17179577.404000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.404000] Uniform CD-ROM driver Revision: 3.20
[17179577.580000] sata_promise 0000:01:0b.0: version 1.04
[17179577.580000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179577.580000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 177
[17179577.580000] sata_promise PATA port found
[17179577.596000] ata1: SATA max UDMA/133 cmd 0xF885A200 ctl 0xF885A238 bmdma 0x0 irq 177
[17179577.596000] ata2: SATA max UDMA/133 cmd 0xF885A280 ctl 0xF885A2B8 bmdma 0x0 irq 177
[17179577.596000] ata3: PATA max UDMA/133 cmd 0xF885A300 ctl 0xF885A338 bmdma 0x0 irq 177
[17179577.800000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179577.964000] ata1: dev 0 cfg 49:2f00 82:346b 83:7f21 84:4003 85:3469 86:3c01 87:4003 88:207f
[17179577.964000] ata1: dev 0 ATA-6, max UDMA/133, 72303840 sectors: LBA48
[17179577.964000] ata1(0): applying bridge limits
[17179577.972000] ata1: dev 0 configured for UDMA/100
[17179577.972000] scsi0 : sata_promise
[17179578.176000] ata2: SATA link up 1.5 Gbps (SStatus 113)
[17179578.340000] ata2: dev 0 cfg 49:2f00 82:346b 83:7f21 84:4003 85:3469 86:3c01 87:4003 88:207f
[17179578.340000] ata2: dev 0 ATA-6, max UDMA/133, 72303840 sectors: LBA48
[17179578.340000] ata2(0): applying bridge limits
[17179578.348000] ata2: dev 0 configured for UDMA/100
[17179578.348000] scsi1 : sata_promise
[17179578.504000] ata3: disabling port
[17179578.504000] scsi2 : sata_promise
[17179578.504000]   Vendor: ATA       Model: WDC WD360GD-00FN  Rev: 35.0
[17179578.504000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179578.504000]   Vendor: ATA       Model: WDC WD360GD-00FN  Rev: 35.0
[17179578.504000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179578.512000] SCSI device sda: 72303840 512-byte hdwr sectors (37020 MB)
[17179578.512000] sda: Write Protect is off
[17179578.512000] sda: Mode Sense: 00 3a 00 00
[17179578.512000] SCSI device sda: drive cache: write back
[17179578.512000] SCSI device sda: 72303840 512-byte hdwr sectors (37020 MB)
[17179578.512000] sda: Write Protect is off
[17179578.512000] sda: Mode Sense: 00 3a 00 00
[17179578.512000] SCSI device sda: drive cache: write back
[17179578.512000]  sda: sda1 sda2
[17179578.524000] sd 0:0:0:0: Attached scsi disk sda
[17179578.528000] SCSI device sdb: 72303840 512-byte hdwr sectors (37020 MB)
[17179578.528000] sdb: Write Protect is off
[17179578.528000] sdb: Mode Sense: 00 3a 00 00
[17179578.532000] SCSI device sdb: drive cache: write back
[17179578.536000] SCSI device sdb: 72303840 512-byte hdwr sectors (37020 MB)
[17179578.536000] sdb: Write Protect is off
[17179578.536000] sdb: Mode Sense: 00 3a 00 00
[17179578.540000] SCSI device sdb: drive cache: write back
[17179578.540000]  sdb: sdb1 sdb2
[17179578.552000] sd 1:0:0:0: Attached scsi disk sdb
[17179578.776000] usbcore: registered new driver usbfs
[17179578.776000] usbcore: registered new driver hub
[17179578.776000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.776000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179578.776000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 185
[17179578.776000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179578.776000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179578.776000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179578.796000] ieee1394: Initialized config rom entry `ip1394'
[17179578.808000] ohci_hcd 0000:00:02.0: irq 185, io mem 0xed087000
[17179578.864000] usb usb1: configuration #1 chosen from 1 choice
[17179578.864000] hub 1-0:1.0: USB hub found
[17179578.864000] hub 1-0:1.0: 3 ports detected
[17179578.968000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179578.968000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 193
[17179578.968000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179578.968000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179578.968000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179578.996000] ohci_hcd 0000:00:02.1: irq 193, io mem 0xed082000
[17179579.052000] usb usb2: configuration #1 chosen from 1 choice
[17179579.052000] hub 2-0:1.0: USB hub found
[17179579.052000] hub 2-0:1.0: 3 ports detected
[17179579.156000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179579.156000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 201
[17179579.156000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179579.156000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179579.156000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179579.156000] ehci_hcd 0000:00:02.2: debug port 1
[17179579.156000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179579.156000] ehci_hcd 0000:00:02.2: irq 201, io mem 0xed083000
[17179579.156000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.156000] usb usb3: configuration #1 chosen from 1 choice
[17179579.156000] hub 3-0:1.0: USB hub found
[17179579.156000] hub 3-0:1.0: 6 ports detected
[17179579.260000] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 22
[17179579.260000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [APCM] -> GSI 22 (level, high) -> IRQ 185
[17179579.260000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179579.312000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[185]  MMIO=[ed084000-ed0847ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179579.372000] Attempting manual resume
[17179579.384000] Stopping tasks: =========<3>hub 3-0:1.0: over-current change on port 1
[17179580.428000] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[17179583.492000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[17179586.460000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[17179589.428000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[17179592.396000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[17179592.396000] hub 3-0:1.0: over-current change on port 2
[17179595.596000] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179598.564000] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179599.388000] 
[17179599.388000]  stopping tasks timed out after 20 seconds (1 tasks remaining):
[17179599.388000]   khubd
[17179599.388000] Restarting tasks...<6> Strange, khubd not stopped
[17179599.388000]  done
[17179599.392000] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[17179599.660000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00005c88b0]
[17179600.672000] ReiserFS: sda2: using ordered data mode
[17179600.688000] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[17179600.688000] ReiserFS: sda2: checking transaction log (sda2)
[17179601.312000] ReiserFS: sda2: replayed 31 transactions in 1 seconds
[17179601.340000] ReiserFS: sda2: Using r5 hash to sort names
[17179601.532000] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179604.500000] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17179604.500000] hub 3-0:1.0: over-current change on port 3
[17179604.788000] hub 3-0:1.0: over-current change on port 4
[17179607.988000] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[17179608.568000] Linux agpgart interface v0.101 (c) Dave Jones
[17179608.640000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[17179608.640000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5040
[17179608.868000] agpgart: Detected NVIDIA nForce2 chipset
[17179608.876000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179609.012000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179609.032000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179609.444000] input: PC Speaker as /class/input/input1
[17179609.452000] Floppy drive(s): fd0 is 1.44M
[17179609.468000] parport: PnPBIOS parport detected.
[17179609.468000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179609.468000] FDC 0 is a post-1991 82077
[17179609.508000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179609.508000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[17179609.508000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 21 (level, high) -> IRQ 193
[17179609.508000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179609.536000] Real Time Clock Driver v1.12ac
[17179609.648000] nvidia: module license 'NVIDIA' taints kernel.
[17179610.028000] eth0: forcedeth.c: subsystem: 01462:570c bound to 0000:00:04.0
[17179610.028000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179610.028000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 209
[17179610.028000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179610.380000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179610.512000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179610.512000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[17179610.572000] ts: Compaq touchscreen protocol output
[17179610.576000] eth0: no link during initialization.
[17179610.680000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[17179610.680000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 20 (level, high) -> IRQ 201
[17179610.680000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179611.000000] intel8x0_measure_ac97_clock: measured 54611 usecs
[17179611.000000] intel8x0: clocking to 48000
[17179611.092000] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[17179611.120000] lp0: using parport0 (interrupt-driven).
[17179611.132000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179611.132000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179611.156000] fuse init (API version 7.6)
[17179611.180000] tun: Universal TUN/TAP device driver, 1.6
[17179611.180000] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[17179611.212000] Adding 3068372k swap on /dev/disk/by-uuid/70ebbca4-148c-405a-a47a-94ed5249a984.  Priority:-1 extents:1 across:3068372k
[17179611.856000] eth0: link up.
[17179614.060000] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[17179617.028000] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[17179617.028000] hub 3-0:1.0: over-current change on port 5
[17179617.412000] ReiserFS: sda2: Removing [29 273765 0x0 SD]..done
[17179617.412000] ReiserFS: sda2: Removing [29 273764 0x0 SD]..done
[17179617.412000] ReiserFS: sda2: Removing [29 273763 0x0 SD]..done
[17179617.412000] ReiserFS: sda2: Removing [29 273749 0x0 SD]..done
[17179617.428000] ReiserFS: sda2: Removing [273371 273429 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [273150 273426 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [273150 273425 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [29 271680 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [271713 268936 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [271713 268935 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [271713 268931 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [271713 268886 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [271713 268813 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [271713 268742 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [35484 265820 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [271713 263787 0x0 SD]..done
[17179617.436000] ReiserFS: sda2: Removing [34552 259062 0x0 SD]..done
[17179617.448000] ReiserFS: sda2: Removing [203416 34552 0x0 SD]..done
[17179617.448000] ReiserFS: sda2: Removing [29 23230 0x0 SD]..done
[17179617.464000] ReiserFS: sda2: Removing [271713 443 0x0 SD]..done
[17179617.464000] ReiserFS: sda2: There were 20 uncompleted unlinks/truncates. Completed
[17179617.660000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179617.700000] NTFS volume version 3.1.
[17179619.276000] NET: Registered protocol family 17
[17179619.672000] NET: Registered protocol family 10
[17179619.672000] lo: Disabled Privacy Extensions
[17179619.672000] IPv6 over IPv4 tunneling driver
[17179620.228000] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179623.196000] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179624.772000] pcc_acpi: loading...
[17179624.784000] ACPI: Power Button (FF) [PWRF]
[17179624.784000] ACPI: Power Button (CM) [PWRB]
[17179624.824000] ibm_acpi: ec object not found
[17179625.092000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179626.164000] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179627.060000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179627.060000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179627.060000] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[17179627.432000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179627.432000] apm: overridden by ACPI.
[17179629.132000] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179629.132000] hub 3-0:1.0: over-current change on port 6
[17179630.576000] eth0: no IPv6 routers present
[17179632.332000] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[17179632.680000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[17179632.756000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179632.756000] NFSD: starting 90-second grace period
[17179635.300000] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[17179638.268000] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[17179641.236000] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[17179641.236000] ohci_hcd 0000:00:02.1: wakeup
[17179641.620000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[17179641.832000] usb 2-1: configuration #1 chosen from 1 choice
[17179641.988000] usbcore: registered new driver hiddev
[17179642.000000] input: Microsoft Basic Optical Mouse as /class/input/input3
[17179642.000000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:02.1-1
[17179642.000000] usbcore: registered new driver usbhid
[17179642.000000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17192121.100000] usbcore: registered new driver libusual
[17192121.124000] Initializing USB Mass Storage driver...
[17192121.124000] usbcore: registered new driver usb-storage
[17192121.124000] USB Mass Storage support registered.
[17192304.864000] usbcore: deregistering driver usb-storage
[17192304.864000] usbcore: deregistering driver libusual
[17192314.092000] usbcore: registered new driver libusual
[17192314.096000] Initializing USB Mass Storage driver...
[17192314.096000] usbcore: registered new driver usb-storage
[17192314.096000] USB Mass Storage support registered.

---

### Post by dkaddict on 2007-06-18
This may help?

I had to amend the /boot/grub/menu.lst in order to get USB working.

Here's how (I copied from a how2 I am waitng to get verified.

Open terminal and enter command>

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

to back up original file.

Next, to amend the /boot/..menu.lst file

Enter

sudo gedit /boot/grub/menu.lst 

(for Kubuntu I use>"kdesu kate /boot/grub/menu.lst"

Gedit or Kate will then open the file.

Next, scroll down to the line which begins with the word 'kernel'

Mine looks like this>

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro quiet splash

Next, after the word 'splash' I entered 'noapic'

So it looks like this>

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro quiet splash noapic

I saved the file quit Kate, quit my terminal, and rebooted (dunno if that's necessary).

When (K)Ubuntu was running again, I plugged in a flash drive and Bingo, it was recognised and mounted. I was well pleased. Now my (K)Ubuntu was as functional as the OS I was trying to escape. Or so I thought.

A couple of months later, I signed up to a new ISP who provided a wireless router with their broadband package.
My notebook has a built in wireless card. When, however, I turned it on, it wouldn't work without a reboot, and when I did that, the 'noapic' option was removed from my /boot/grub/menu.lst. USB and Wireless, it seemed, could not be utilised at the same time on my notebook. I had knowledge of the /boot...menu.lst file now, however, and a quick search with Google bore fruit. I came across a post (can't remember URL or which forum, sorry) which told of another option for /boot/grub/menu.lst called irqpoll.

I gave it a try.

I opened a terminal and followed the same instructions as those above.

On the line which I had amended, I erased 'noapic' and entered 'irqpoll' in its place.

It then looked like>

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro quiet splash irqpoll



Please make sure you have a good idea of what to do before attempting messing about with /boot/grub/menu.lst
I am the sole user of my comp, back my system up regularly, and have a seperate 'home' partition so a reinstall is not a great drama for me if I screw anything up.

It has been a while since I discovered the 'noapic' 'irqpoll' options and have forgotten the URLs of the posts/sites which helped me. I shall endeavour to find them.

Here are a couple of maybe useful links.

[http://www.acpi.info/](http://www.acpi.info/)

---

