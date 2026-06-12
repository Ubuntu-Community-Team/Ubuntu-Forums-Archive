---
title: "Ubuntu kernel 2.6.27-7-server not detecting my ide partitions"
date: 2008-11-03
forum: General Help
---

### Post by amund on 2008-11-03
Hi!
I'm having some problems with ubuntu server. My ide disks are found, but my partitions are not. If I change kernel to kernel 2.6.27-7-generic, everything works ok. But I guess it's best to run the server kernel on a server, so was hoping to fix the problem :)
Anyone knows what's wrong? I've added some output that I was hoping could make some sense. Note the "fdisk -l" command give the same output... 

Ubuntu 8.10, kernel 2.6.27-7-server
```

ls /dev/sd
sda   sda1  sda2  sda3  sda4  sdb   sdc   sdc1  sdd   sdd1  sde 

```

```

lspci
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

```

```

lsmod
Module                  Size  Used by
appletalk              38880  0 
ipv6                  263460  12 
af_packet              25600  2 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
nls_utf8                9856  2 
hfsplus                81028  2 
lp                     17156  0 
loop                   23180  0 
evdev                  17696  0 
parport_pc             39460  1 
parport                42604  2 lp,parport_pc
pcspkr                 10624  0 
snd_via82xx            32408  0 
gameport               19468  1 snd_via82xx
snd_via82xx_modem      19464  0 
snd_mpu401_uart        15360  1 snd_via82xx
snd_ac97_codec        110372  2 snd_via82xx,snd_via82xx_modem
ac97_bus                9856  1 snd_ac97_codec
snd_rawmidi            29696  1 snd_mpu401_uart
snd_pcm                83332  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_timer              29832  1 snd_pcm
snd_seq_device         15116  1 snd_rawmidi
button                 14224  0 
snd_page_alloc         16264  3 snd_via82xx,snd_via82xx_modem,snd_pcm
snd                    63268  8 snd_via82xx,snd_via82xx_modem,snd_mpu401_uart,snd_ac97_codec,snd_rawmidi,snd_pcm,snd_timer,snd_seq_device
soundcore              15328  1 snd
i2c_viapro             15892  0 
i2c_core               31892  1 i2c_viapro
via_agp                16256  1 
shpchp                 38036  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  1 via_agp
ext3                  132872  3 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43040  1 sr_mod
sd_mod                 42264  9 
crc_t10dif              9984  1 sd_mod
sg                     39220  0 
sata_via               15492  1 
pata_via               15876  1 
ata_generic            12804  0 
sata_sil               15752  4 
pata_acpi              12160  0 
via_rhine              30728  0 
ehci_hcd               43916  0 
uhci_hcd               30864  0 
libata                176032  5 sata_via,pata_via,ata_generic,sata_sil,pata_acpi
usbcore               149360  3 ehci_hcd,uhci_hcd
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
winbond_840            28424  0 
mii                    13440  2 via_rhine,winbond_840
raid10                 30592  0 
raid456               134928  0 
async_xor              10496  1 raid456
async_memcpy            9728  1 raid456
async_tx               11008  3 raid456,async_xor,async_memcpy
xor                    23688  2 raid456,async_xor
raid1                  30080  0 
raid0                  15488  0 
multipath              15104  0 
linear                 13568  0 
md_mod                 93596  6 raid10,raid456,raid1,raid0,multipath,linear
dm_mirror              27008  0 
dm_log                 17924  1 dm_mirror
dm_snapshot            26276  0 
dm_mod                 63304  10 dm_mirror,dm_log,dm_snapshot
thermal                23708  0 
processor              42284  2 thermal
fan                    12420  0 
fbcon                  47392  0 
tileblit               10752  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60700  1 

```


```

fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11d13f40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   83  Linux
/dev/sda2              14       12170    97651102+  83  Linux
/dev/sda3           12171       12778     4883760   83  Linux
/dev/sda4           12779      121601   874120747+  8e  Linux LVM

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009411d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706   fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a19cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   83  Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f92b21a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001   83  Linux

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9c3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001   fd  Linux raid autodetect

```

Ubuntu 8.10, kernel 2.6.27-7-generic:

```

ls /dev/sd
sda   sda1  sda2  sda3  sda4  sdb   sdb1  sdc   sdc1  sdd   sdd1  sde   sde1 

```

```

lspci
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

```

```

lsmod 
Module                  Size  Used by
appletalk              39008  0 
ipv6                  263972  12 
af_packet              25728  2 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
nls_utf8                9856  2 
hfsplus                81028  2 
lp                     17156  0 
loop                   23180  0 
evdev                  17696  0 
pcspkr                 10624  0 
snd_via82xx            32536  0 
gameport               19468  1 snd_via82xx
snd_via82xx_modem      19464  0 
snd_ac97_codec        111652  2 snd_via82xx,snd_via82xx_modem
ac97_bus                9856  1 snd_ac97_codec
snd_mpu401_uart        15360  1 snd_via82xx
parport_pc             39204  1 
snd_pcm                83204  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_timer              29960  1 snd_pcm
snd_rawmidi            29824  1 snd_mpu401_uart
snd_seq_device         15116  1 snd_rawmidi
parport                42604  2 lp,parport_pc
snd                    63268  8 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
snd_page_alloc         16136  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              15328  1 snd
i2c_viapro             15764  0 
button                 14224  0 
i2c_core               31892  1 i2c_viapro
via_agp                16256  1 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  1 via_agp
ext3                  133256  3 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  11 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
sata_via               15492  2 
pata_via               16132  1 
ata_generic            12932  0 
via_rhine              30216  0 
uhci_hcd               30736  0 
ehci_hcd               43276  0 
usbcore               148848  3 uhci_hcd,ehci_hcd

pata_acpi              12160  0 
sata_sil               15752  4 
libata                177312  5 sata_via,pata_via,ata_generic,pata_acpi,sata_sil
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
winbond_840            28296  0 
mii                    13440  2 via_rhine,winbond_840
raid10                 30592  0 
raid456               135184  0 
async_xor              11392  1 raid456
async_memcpy           10112  1 raid456
async_tx               15312  3 raid456,async_xor,async_memcpy
xor                    23688  2 raid456,async_xor
raid1                  30080  0 
raid0                  15488  0 
multipath              15104  0 
linear                 13568  0 
md_mod                 93724  6 raid10,raid456,raid1,raid0,multipath,linear
dm_mirror              26880  0 
dm_log                 17924  1 dm_mirror
dm_snapshot            26276  0 
dm_mod                 63432  10 dm_mirror,dm_log,dm_snapshot
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 

```

```

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11d13f40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   83  Linux
/dev/sda2              14       12170    97651102+  83  Linux
/dev/sda3           12171       12778     4883760   83  Linux
/dev/sda4           12779      121601   874120747+  8e  Linux LVM

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f92b21a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9c3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009411d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30515   245111706   fd  Linux raid autodetect

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a19cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001   83  Linux

```

---

### Post by psusi on 2008-11-03
Can you post the output of sudo fdisk -lu and dmesg under both kernels?

---

### Post by amund on 2008-11-04
Hi, 
Thanks for answering! Now I'm having the same problem in the generic kernel :( The only thing I've done was to repartition the disk and assemble the array. The array is raid 5 with four partitions from four disks. Before I did this, I'm sure everything worked ok. I did a couple of reboots and the partitions was there. So the problem must have come after I started with the raid setup.

So, now I have the same problem in both kernels :(
I've tried removing mdadm from startup with no luck. 

I'm posting the information you wanted:

Server kernel:
```

fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11d13f40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   83  Linux
/dev/sda2          208845   195511049    97651102+  83  Linux
/dev/sda3       195511050   205278569     4883760   83  Linux
/dev/sda4       205278570  1953520064   874120747+  8e  Linux LVM

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009411d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a19cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488392064   244196001   fd  Linux raid autodetect

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f92b21a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   488392064   244196001   fd  Linux raid autodetect

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b9c3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   488392064   244196001   fd  Linux raid autodetect

```

```

dmesg 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-server (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Oct 30 05:04:11 UTC 2008 (Ubuntu 2.6.27-7.15-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003dff0000 (usable)
[    0.000000]  BIOS-e820: 000000003dff0000 - 000000003dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003dff3000 - 000000003e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3dff0 max_arch_pfn = 0x1000000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37786000 - 37fef922
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000F7690, 0014 (r0 KM400A)
[    0.000000] ACPI: RSDT 3DFF3040, 002C (r1 KM400A AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3DFF30C0, 0074 (r1 KM400A AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3DFF3180, 4E4D (r1 KM400A AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3DFF0000, 0040
[    0.000000] ACPI: APIC 3DFF8040, 005A (r1 KM400A AWRDACPI 42302E31 AWRD        0)
[    0.000000] 95MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00009000 - 00010000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
[    0.000000]   #4 [0037786000 - 0037fef922]          RAMDISK ==> [0037786000 - 0037fef922]
[    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00f5bb0] 000f5bb0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003dff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003dff0
[    0.000000] On node 0 totalpages: 253839
[    0.000000] free_area_init_node: node 0, pgdat c049eb00, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 24344 pages, LIFO batch:3
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3e000000:c0c00000)
[    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 251607
[    0.000000] Kernel command line: root=UUID=cc3e11ba-ea5f-4027-b5be-298b056ca171 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 1526.752 MHz processor.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.010000] Memory: 991628k/1015744k available (2628k kernel code, 23496k reserved, 1201k data, 436k init, 98240k highmem)
[    0.010000] virtual kernel memory layout:
[    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
[    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
[    0.010000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.010000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
[    0.010000]       .data : 0xc0391036 - 0xc04bd800   (1201 kB)
[    0.010000]       .text : 0xc0100000 - 0xc0391036   (2628 kB)
[    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.010000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.010019] Calibrating delay loop (skipped), value calculated using timer frequency.. 3053.50 BogoMIPS (lpj=15267520)
[    0.010055] Security Framework initialized
[    0.010069] SELinux:  Disabled at boot.
[    0.010206] AppArmor: AppArmor initialized
[    0.010220] Mount-cache hash table entries: 512
[    0.010511] Initializing cgroup subsys ns
[    0.010519] Initializing cgroup subsys cpuacct
[    0.010523] Initializing cgroup subsys memory
[    0.010548] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010553] CPU: L2 Cache: 256K (64 bytes/line)
[    0.010578] Checking 'hlt' instruction... OK.
[    0.050556] SMP alternatives: switching to UP code
[    0.060057] Freeing SMP alternatives: 11k freed
[    0.060064] ACPI: Core revision 20080609
[    0.064436] ACPI: Checking initramfs for custom DSDT
[    0.621069] ENABLING IO-APIC IRQs
[    0.621483] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.728126] CPU0: AMD Athlon(tm) XP 1800+ stepping 02
[    0.730000] Brought up 1 CPUs
[    0.730000] Total of 1 processors activated (3053.50 BogoMIPS).
[    0.730000] CPU0 attaching sched-domain:
[    0.730000]  domain 0: span 0 level CPU
[    0.730000]   groups: 0
[    0.730000] net_namespace: 840 bytes
[    0.730000] Booting paravirtualized kernel on bare hardware
[    0.730000] Time:  9:05:48  Date: 11/04/08
[    0.730000] NET: Registered protocol family 16
[    0.730000] EISA bus registered
[    0.730000] ACPI: bus type pci registered
[    0.731726] PCI: PCI BIOS revision 2.10 entry at 0xf1550, last bus=1
[    0.731730] PCI: Using configuration type 1 for base access
[    0.735027] ACPI: EC: Look up EC in DSDT
[    0.749461] ACPI: Interpreter enabled
[    0.749566] ACPI: (supports S0 S1 S3 S4 S5)
[    0.749598] ACPI: Using IOAPIC for interrupt routing
[    0.765025] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.765247] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e3ffffff]
[    0.765323] pci 0000:00:01.0: supports D1
[    0.765349] PCI: 0000:00:08.0 reg 10 io port: [a000, a07f]
[    0.765357] PCI: 0000:00:08.0 reg 14 32bit mmio: [eb001000, eb00107f]
[    0.765409] PCI: 0000:00:09.0 reg 10 io port: [a400, a407]
[    0.765417] PCI: 0000:00:09.0 reg 14 io port: [a800, a803]
[    0.765424] PCI: 0000:00:09.0 reg 18 io port: [ac00, ac07]
[    0.765431] PCI: 0000:00:09.0 reg 1c io port: [b000, b003]
[    0.765438] PCI: 0000:00:09.0 reg 20 io port: [b400, b40f]
[    0.765446] PCI: 0000:00:09.0 reg 24 32bit mmio: [eb000000, eb0001ff]
[    0.765453] PCI: 0000:00:09.0 reg 30 32bit mmio: [0, 7ffff]
[    0.765466] pci 0000:00:09.0: supports D1
[    0.765469] pci 0000:00:09.0: supports D2
[    0.765503] PCI: 0000:00:0f.0 reg 10 io port: [b800, b807]
[    0.765511] PCI: 0000:00:0f.0 reg 14 io port: [bc00, bc03]
[    0.765518] PCI: 0000:00:0f.0 reg 18 io port: [c000, c007]
[    0.765526] PCI: 0000:00:0f.0 reg 1c io port: [c400, c403]
[    0.765533] PCI: 0000:00:0f.0 reg 20 io port: [c800, c80f]
[    0.765541] PCI: 0000:00:0f.0 reg 24 io port: [cc00, ccff]
[    0.765695] PCI: 0000:00:0f.1 reg 20 io port: [d000, d00f]
[    0.765769] PCI: 0000:00:10.0 reg 20 io port: [d400, d41f]
[    0.765791] pci 0000:00:10.0: supports D1
[    0.765793] pci 0000:00:10.0: supports D2
[    0.765797] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.765802] pci 0000:00:10.0: PME# disabled
[    0.765846] PCI: 0000:00:10.1 reg 20 io port: [d800, d81f]
[    0.765867] pci 0000:00:10.1: supports D1
[    0.765869] pci 0000:00:10.1: supports D2
[    0.765872] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.765878] pci 0000:00:10.1: PME# disabled
[    0.765921] PCI: 0000:00:10.2 reg 20 io port: [dc00, dc1f]
[    0.765942] pci 0000:00:10.2: supports D1
[    0.765945] pci 0000:00:10.2: supports D2
[    0.765947] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.765953] pci 0000:00:10.2: PME# disabled
[    0.765996] PCI: 0000:00:10.3 reg 20 io port: [e000, e01f]
[    0.766017] pci 0000:00:10.3: supports D1
[    0.766020] pci 0000:00:10.3: supports D2
[    0.766022] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.766028] pci 0000:00:10.3: PME# disabled
[    0.766055] PCI: 0000:00:10.4 reg 10 32bit mmio: [eb002000, eb0020ff]
[    0.766184] pci 0000:00:10.4: supports D1
[    0.766187] pci 0000:00:10.4: supports D2
[    0.766190] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.766195] pci 0000:00:10.4: PME# disabled
[    0.766258] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.766266] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.766307] PCI: 0000:00:11.5 reg 10 io port: [e400, e4ff]
[    0.766346] pci 0000:00:11.5: supports D1
[    0.766348] pci 0000:00:11.5: supports D2
[    0.766377] PCI: 0000:00:11.6 reg 10 io port: [e800, e8ff]
[    0.766445] PCI: 0000:00:12.0 reg 10 io port: [ec00, ecff]
[    0.766453] PCI: 0000:00:12.0 reg 14 32bit mmio: [eb003000, eb0030ff]
[    0.766487] pci 0000:00:12.0: supports D1
[    0.766489] pci 0000:00:12.0: supports D2
[    0.766492] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.766498] pci 0000:00:12.0: PME# disabled
[    0.766547] PCI: 0000:01:00.0 reg 10 32bit mmio: [e4000000, e7ffffff]
[    0.766554] PCI: 0000:01:00.0 reg 14 32bit mmio: [e8000000, e8ffffff]
[    0.766666] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, ffff]
[    0.766680] pci 0000:01:00.0: supports D1
[    0.766682] pci 0000:01:00.0: supports D2
[    0.766716] PCI: bridge 0000:00:01.0 32bit mmio: [e8000000, e9ffffff]
[    0.766722] PCI: bridge 0000:00:01.0 32bit mmio pref: [e4000000, e7ffffff]
[    0.766731] bus 00 -> node 0
[    0.766742] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.845522] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.845966] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.846408] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.846807] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.847111] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.847493] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.847874] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.848255] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.848720] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[    0.849069] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.849511] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[    0.850040] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[    0.850412] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.850478] pnp: PnP ACPI init
[    0.850493] ACPI: bus type pnp registered
[    0.859672] pnp: PnP ACPI: found 12 devices
[    0.859678] ACPI: ACPI bus type pnp unregistered
[    0.859684] PnPBIOS: Disabled by ACPI PNP
[    0.860558] PCI: Using ACPI for IRQ routing
[    0.860757] NET: Registered protocol family 8
[    0.860757] NET: Registered protocol family 20
[    0.860757] NetLabel: Initializing
[    0.860757] NetLabel:  domain hash size = 128
[    0.860757] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.860757] NetLabel:  unlabeled traffic allowed by default
[    0.860757] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.860757]    actual entries 65620
[    0.861089] AppArmor: AppArmor Filesystem Enabled
[    0.861116] ACPI: RTC can wake from S4
[    0.861143] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    0.861143] system 00:00: iomem range 0xd4800-0xd7fff has been reserved
[    0.861143] system 00:00: iomem range 0xf0000-0xfbfff could not be reserved
[    0.861143] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.861143] system 00:00: iomem range 0x3dff0000-0x3dffffff could not be reserved
[    0.861143] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.861143] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.861143] system 00:00: iomem range 0x100000-0x3dfeffff could not be reserved
[    0.861143] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.861143] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.861143] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.861143] system 00:02: ioport range 0x400-0x47f has been reserved
[    0.861143] system 00:02: ioport range 0x5000-0x500f has been reserved
[    0.861143] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.861143] system 00:03: ioport range 0x294-0x297 has been reserved
[    0.898098] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.898103] pci 0000:00:01.0:   IO window: disabled
[    0.898111] pci 0000:00:01.0:   MEM window: 0xe8000000-0xe9ffffff
[    0.898117] pci 0000:00:01.0:   PREFETCH window: 0x000000e4000000-0x000000e7ffffff
[    0.898137] pci 0000:00:01.0: setting latency timer to 64
[    0.898143] bus: 00 index 0 io port: [0, ffff]
[    0.898146] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.898149] bus: 01 index 0 mmio: [0, 0]
[    0.898152] bus: 01 index 1 mmio: [e8000000, e9ffffff]
[    0.898155] bus: 01 index 2 mmio: [e4000000, e7ffffff]
[    0.898158] bus: 01 index 3 mmio: [0, 0]
[    0.898181] NET: Registered protocol family 2
[    0.898497] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.899141] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.902090] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.903580] TCP: Hash tables configured (established 131072 bind 65536)
[    0.903587] TCP reno registered
[    0.903884] NET: Registered protocol family 1
[    0.904093] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.446133]  it is
[    2.103161] Freeing initrd memory: 8614k freed
[    2.105051] audit: initializing netlink socket (disabled)
[    2.105083] type=2000 audit(1225789548.100:1): initialized
[    2.114973] highmem bounce pool size: 64 pages
[    2.114986] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.119989] VFS: Disk quotas dquot_6.5.1
[    2.120306] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.120508] msgmni has been set to 1762
[    2.120836] io scheduler noop registered
[    2.120840] io scheduler anticipatory registered
[    2.120844] io scheduler deadline registered (default)
[    2.120864] io scheduler cfq registered
[    2.120884] PCI: VIA PCI bridge detected.Disabling DAC.
[    2.120974] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    2.120988] pci 0000:01:00.0: Boot video device
[    2.121793] isapnp: Scanning for PnP cards...
[    2.486152] isapnp: No Plug & Play device found
[    2.577037] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.577307] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.578911] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.583021] brd: module loaded
[    2.583154] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.583494] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.583500] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.583728] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.585325] mice: PS/2 mouse device common for all mice
[    2.585698] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.585744] rtc0: alarms up to one year, y3k
[    2.586073] EISA: Probing bus 0 at eisa.0
[    2.586104] Cannot allocate resource for EISA slot 5
[    2.586120] EISA: Detected 0 cards.
[    2.586125] cpuidle: using governor ladder
[    2.586129] cpuidle: using governor menu
[    2.587136] TCP cubic registered
[    2.587187] Using IPI No-Shortcut mode
[    2.587735] registered taskstats version 1
[    2.588032]   Magic number: 0:795:69
[    2.588455] rtc_cmos 00:05: setting system clock to 2008-11-04 09:05:50 UTC (1225789550)
[    2.588461] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.588465] EDD information not available.
[    2.589464] Freeing unused kernel memory: 436k freed
[    2.589638] Write protecting the kernel text: 2632k
[    2.589703] Write protecting the kernel read-only data: 956k
[    2.609613] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.799360] fuse init (API version 7.9)
[    2.834662] fan PNP0C0B:00: registered as cooling_device0
[    2.834675] ACPI: Fan [FAN] (on)
[    2.851265] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.851362] processor ACPI0007:00: registered as cooling_device1
[    2.857614] thermal LNXTHERM:01: registered as thermal_zone0
[    2.859112] ACPI: Thermal Zone [THRM] (64 C)
[    2.894895] device-mapper: uevent: version 1.0.3
[    2.895487] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.941560] md: linear personality registered for level -1
[    2.951370] md: multipath personality registered for level -4
[    2.960467] md: raid0 personality registered for level 0
[    2.973216] md: raid1 personality registered for level 1
[    2.981647] xor: automatically using best checksumming function: pIII_sse
[    3.030006]    pIII_sse  :  1626.400 MB/sec
[    3.030011] xor: using function: pIII_sse (1626.400 MB/sec)
[    3.031710] async_tx: api initialized (sync-only)
[    3.210080] raid6: int32x1    525 MB/s
[    3.380050] raid6: int32x2    567 MB/s
[    3.550058] raid6: int32x4    426 MB/s
[    3.720211] raid6: int32x8    351 MB/s
[    3.890131] raid6: mmxx1      984 MB/s
[    4.060007] raid6: mmxx2     1726 MB/s
[    4.230015] raid6: sse1x1     960 MB/s
[    4.400018] raid6: sse1x2    1567 MB/s
[    4.400022] raid6: using algorithm sse1x2 (1567 MB/s)
[    4.400029] md: raid6 personality registered for level 6
[    4.400032] md: raid5 personality registered for level 5
[    4.400035] md: raid4 personality registered for level 4
[    4.454835] md: raid10 personality registered for level 10
[    5.460519] winbond-840.c:v1.01-e (2.4 port) Sep-11-2006  Donald Becker <becker@scyld.com>
[    5.460523]   http://www.scyld.com/network/drivers.html
[    5.460577] winbond-840 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.461357] eth0: Winbond W89c840 at 0001a000, 00:00:e8:21:d5:15, IRQ 16.
[    5.461985] eth0: MII PHY 0181b802h found at address 1, status 0x782d advertising 05e1.
[    5.496819] No dock devices found.
[    5.682016] SCSI subsystem initialized
[    5.724011] usbcore: registered new interface driver usbfs
[    5.724055] usbcore: registered new interface driver hub
[    5.724123] usbcore: registered new device driver usb
[    5.864767] libata version 3.00 loaded.
[    5.870661] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    5.871306] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    5.871321] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    5.871991] eth1: VIA Rhine II at 0xeb003000, 00:13:d4:55:5b:e7, IRQ 23.
[    5.872780] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    5.878831] USB Universal Host Controller Interface driver v3.0
[    5.879519] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    5.879535] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    5.879554] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    5.879742] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    5.879791] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[    5.880256] usb usb1: configuration #1 chosen from 1 choice
[    5.880301] hub 1-0:1.0: USB hub found
[    5.880319] hub 1-0:1.0: 2 ports detected
[    6.100668] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    6.100691] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    6.100733] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    6.100768] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[    6.101036] usb usb2: configuration #1 chosen from 1 choice
[    6.101081] hub 2-0:1.0: USB hub found
[    6.101099] hub 2-0:1.0: 2 ports detected
[    6.320908] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    6.320931] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    6.320973] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    6.321007] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[    6.321316] usb usb3: configuration #1 chosen from 1 choice
[    6.321361] hub 3-0:1.0: USB hub found
[    6.321378] hub 3-0:1.0: 2 ports detected
[    6.540636] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    6.540658] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    6.540701] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    6.540737] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e000
[    6.540997] usb usb4: configuration #1 chosen from 1 choice
[    6.541053] hub 4-0:1.0: USB hub found
[    6.541070] hub 4-0:1.0: 2 ports detected
[    6.760719] sata_sil 0000:00:09.0: version 2.3
[    6.760810] sata_sil 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.761095] scsi0 : sata_sil
[    6.761324] scsi1 : sata_sil
[    6.761379] ata1: SATA max UDMA/100 mmio m512@0xeb000000 tf 0xeb000080 irq 17
[    6.761384] ata2: SATA max UDMA/100 mmio m512@0xeb000000 tf 0xeb0000c0 irq 17
[    7.110192] ata1: SATA link down (SStatus 0 SControl 310)
[    7.291035] Marking TSC unstable due to TSC halts in idle
[    7.460059] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    7.848240] ata2.00: ATA-8: WDC WD10EACS-00ZJB0, 01.01B01, max UDMA/133
[    7.848248] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    7.880564] ata2.00: configured for UDMA/100
[    7.880783] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EACS-00Z 01.0 PQ: 0 ANSI: 5
[    7.881686] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    7.881701] pata_acpi 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    7.881805] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    7.881888] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    7.881922] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    7.885136] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    7.885171] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    7.885257] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    7.885325] ehci_hcd 0000:00:10.4: irq 21, io mem 0xeb002000
[    7.900082] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.900520] usb usb5: configuration #1 chosen from 1 choice
[    7.900568] hub 5-0:1.0: USB hub found
[    7.900680] hub 5-0:1.0: 8 ports detected
[    8.024267] sata_via 0000:00:0f.0: version 2.3
[    8.024301] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    8.024387] sata_via 0000:00:0f.0: routed to hard irq line 11
[    8.024518] scsi2 : sata_via
[    8.024757] scsi3 : sata_via
[    8.027915] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xbc00 bmdma 0xc800 irq 20
[    8.027920] ata4: SATA max UDMA/133 cmd 0xc000 ctl 0xc400 bmdma 0xc808 irq 20
[    8.057292] scsi 1:0:0:0: Attached scsi generic sg0 type 0
[    8.105927] Driver 'sd' needs updating - please use bus_type methods
[    8.106237] sd 1:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    8.106278] sd 1:0:0:0: [sda] Write Protect is off
[    8.106282] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.106346] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.106483] sd 1:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    8.106514] sd 1:0:0:0: [sda] Write Protect is off
[    8.106518] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.106574] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.106582]  sda: sda1 sda2 sda3 sda4
[    8.112789] sd 1:0:0:0: [sda] Attached SCSI disk
[    8.240056] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.421196] ata3.00: ATA-7: Maxtor 6L250S0, BACE1G10, max UDMA/133
[    8.421203] ata3.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    8.461168] ata3.00: configured for UDMA/133
[    8.670052] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.894817] ata4.00: ATA-7: ST3250820AS, 3.AAD, max UDMA/133
[    8.894824] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    8.978111] ata4.00: configured for UDMA/133
[    8.978320] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6L250S0   BACE PQ: 0 ANSI: 5
[    8.978771] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    8.980215] scsi 3:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
[    8.980514] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[    8.980798] pata_via 0000:00:0f.1: version 0.3.3
[    8.980829] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    8.981233] scsi4 : pata_via
[    8.981382] scsi5 : pata_via
[    8.985107] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[    8.985112] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[    8.987779] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[    8.987813] sd 2:0:0:0: [sdb] Write Protect is off
[    8.987818] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    8.987865] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.988117] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[    8.988143] sd 2:0:0:0: [sdb] Write Protect is off
[    8.988147] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    8.988191] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.988200]  sdb: sdb1
[    9.011240] sd 2:0:0:0: [sdb] Attached SCSI disk
[    9.011512] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    9.011554] sd 3:0:0:0: [sdc] Write Protect is off
[    9.011558] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    9.011627] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.011754] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    9.011791] sd 3:0:0:0: [sdc] Write Protect is off
[    9.011795] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    9.011951] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.011959]  sdc: sdc1
[    9.026424] sd 3:0:0:0: [sdc] Attached SCSI disk
[    9.191257] ata5.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
[    9.191265] ata5.00: 488397168 sectors, multi 16: LBA48 
[    9.191455] ata5.01: ATA-7: ST3250823A, 3.01, max UDMA/100
[    9.191460] ata5.01: 488397168 sectors, multi 16: LBA48 
[    9.210452] ata5.00: configured for UDMA/100
[    9.250356] ata5.01: configured for UDMA/100
[    9.430431] ata6.00: ATAPI: _NEC DVD_RW ND-3520A, 1.04, max UDMA/33
[    9.470282] ata6.00: configured for UDMA/33
[    9.470493] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
[    9.470938] scsi 4:0:0:0: Attached scsi generic sg3 type 0
[    9.472551] scsi 4:0:1:0: Direct-Access     ATA      ST3250823A       3.01 PQ: 0 ANSI: 5
[    9.472962] scsi 4:0:1:0: Attached scsi generic sg4 type 0
[    9.475326] scsi 5:0:0:0: CD-ROM            _NEC     DVD_RW ND-3520A  1.04 PQ: 0 ANSI: 5
[    9.475645] scsi 5:0:0:0: Attached scsi generic sg5 type 5
[    9.480229] sd 4:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
[    9.480324] sd 4:0:0:0: [sdd] Write Protect is off
[    9.480329] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    9.480395] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.480669] sd 4:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
[    9.480787] sd 4:0:0:0: [sdd] Write Protect is off
[    9.480791] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    9.480857] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.480866]  sdd: sdd1
[    9.482746] sd 4:0:0:0: [sdd] Attached SCSI disk
[    9.482917] sd 4:0:1:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    9.482956] sd 4:0:1:0: [sde] Write Protect is off
[    9.482960] sd 4:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    9.483113] sd 4:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.483240] sd 4:0:1:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    9.483273] sd 4:0:1:0: [sde] Write Protect is off
[    9.483277] sd 4:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    9.483334] sd 4:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.483342]  sde: sde1
[    9.504097] sd 4:0:1:0: [sde] Attached SCSI disk
[    9.815876] Driver 'sr' needs updating - please use bus_type methods
[    9.819749] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    9.819761] Uniform CD-ROM driver Revision: 3.20
[    9.820114] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   10.263513] md: md0 stopped.
[   10.582234] md: bind<sdd>
[   10.582446] md: bind<sdc>
[   10.582530] md: md0 stopped.
[   10.582543] md: unbind<sdc>
[   10.582680] md: export_rdev(sdc)
[   10.582688] md: unbind<sdd>
[   10.582728] md: export_rdev(sdd)
[   10.697044] md: md0 stopped.
[   10.706507] md: bind<sdd>
[   10.706724] md: bind<sdc>
[   10.706809] md: md0 stopped.
[   10.706823] md: unbind<sdc>
[   10.706865] md: export_rdev(sdc)
[   10.706874] md: unbind<sdd>
[   10.706914] md: export_rdev(sdd)
[   10.775638] md: md0 stopped.
[   10.803017] md: bind<sdd>
[   10.803449] md: bind<sdc>
[   10.803534] md: md0 stopped.
[   10.803548] md: unbind<sdc>
[   10.803588] md: export_rdev(sdc)
[   10.803597] md: unbind<sdd>
[   10.803638] md: export_rdev(sdd)
[   10.874452] md: md0 stopped.
[   10.886233] md: bind<sdd>
[   10.886451] md: bind<sdc>
[   10.886531] md: md0 stopped.
[   10.886545] md: unbind<sdc>
[   10.886587] md: export_rdev(sdc)
[   10.886596] md: unbind<sdd>
[   10.886635] md: export_rdev(sdd)
[   11.028487] kjournald starting.  Commit interval 5 seconds
[   11.028517] EXT3-fs: mounted filesystem with ordered data mode.
[   12.916623] udevd version 124 started
[   14.078163] Linux agpgart interface v0.103
[   14.085100] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.150403] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.168261] agpgart: Detected VIA KM400/KM400A chipset
[   14.174670] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   14.844053] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   14.871506] ACPI: Power Button (FF) [PWRF]
[   14.871673] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   14.910113] ACPI: Power Button (CM) [PWRB]
[   14.910288] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   14.950086] ACPI: Sleep Button (CM) [SLPB]
[   16.420494] parport_pc 00:09: reported by Plug and Play ACPI
[   16.420688] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   18.674791] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   18.675399] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   18.675414] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   18.798239] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   19.239014] md: md0 stopped.
[   19.420105] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   19.666041] md: bind<sdb1>
[   19.666266] md: bind<sde1>
[   19.727880] md: md0 stopped.
[   19.727911] md: unbind<sde1>
[   19.750299] md: export_rdev(sde1)
[   19.750339] md: unbind<sdb1>
[   19.770175] md: export_rdev(sdb1)
[   19.791716] md: bind<sdb1>
[   19.792196] md: bind<sde1>
[   19.930401] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   19.930431] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   19.931569] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   19.931823] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   19.980090] md: md0 stopped.
[   19.980123] md: unbind<sde1>
[   20.010350] md: export_rdev(sde1)
[   20.010472] md: unbind<sdb1>
[   20.030075] md: export_rdev(sdb1)
[   20.057833] md: bind<sdb1>
[   20.058148] md: bind<sde1>
[   20.452811] codec_read: codec 0 is not valid [0xfe0000]
[   20.460501] codec_read: codec 0 is not valid [0xfe0000]
[   20.468106] codec_read: codec 0 is not valid [0xfe0000]
[   20.475771] codec_read: codec 0 is not valid [0xfe0000]
[   23.630903] loop: module loaded
[   23.658788] lp0: using parport0 (interrupt-driven).
[   24.123915] Adding 5242872k swap on /dev/mapper/unsafeDisk-swap.  Priority:-1 extents:1 across:5242872k
[   24.629451] EXT3 FS on sda2, internal journal
[   25.666236] kjournald starting.  Commit interval 5 seconds
[   25.666752] EXT3 FS on sda1, internal journal
[   25.666762] EXT3-fs: mounted filesystem with ordered data mode.
[   25.677054] kjournald starting.  Commit interval 5 seconds
[   25.677325] EXT3 FS on sda3, internal journal
[   25.677334] EXT3-fs: mounted filesystem with ordered data mode.
[   26.562694] type=1505 audit(1225789574.097:2): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3904
[   26.785341] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.919748] eth0: Setting 100MBit-full-duplex based on MII#1
[   28.228625] NET: Registered protocol family 17
[   30.231584] NET: Registered protocol family 10
[   30.232497] lo: Disabled Privacy Extensions
[   36.841222] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   36.841539] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   36.841544] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   36.841548] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   38.239341] NET: Registered protocol family 5
[   41.130024] eth0: no IPv6 routers present

```

Generic kernel:

```

fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11d13f40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   83  Linux
/dev/sda2          208845   195511049    97651102+  83  Linux
/dev/sda3       195511050   205278569     4883760   83  Linux
/dev/sda4       205278570  1953520064   874120747+  8e  Linux LVM

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009411d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a19cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488392064   244196001   fd  Linux raid autodetect

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f92b21a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   488392064   244196001   fd  Linux raid autodetect

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b9c3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   488392064   244196001   fd  Linux raid autodetect

```

```

dmesg 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Oct 30 04:18:38 UTC 2008 (Ubuntu 2.6.27-7.15-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003dff0000 (usable)
[    0.000000]  BIOS-e820: 000000003dff0000 - 000000003dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003dff3000 - 000000003e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3dff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3778b000 - 37fef3aa
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000F7690, 0014 (r0 KM400A)
[    0.000000] ACPI: RSDT 3DFF3040, 002C (r1 KM400A AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3DFF30C0, 0074 (r1 KM400A AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3DFF3180, 4E4D (r1 KM400A AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3DFF0000, 0040
[    0.000000] ACPI: APIC 3DFF8040, 005A (r1 KM400A AWRDACPI 42302E31 AWRD        0)
[    0.000000] 95MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003778b000 - 0037fef3aa]          RAMDISK ==> [003778b000 - 0037fef3aa]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f5bb0] 000f5bb0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003dff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003dff0
[    0.000000] On node 0 totalpages: 253839
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 24344 pages, LIFO batch:3
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3e000000:c0c00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 251607
[    0.000000] Kernel command line: root=UUID=cc3e11ba-ea5f-4027-b5be-298b056ca171 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 1526.755 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 991812k/1015744k available (2572k kernel code, 23284k reserved, 1160k data, 424k init, 98240k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc03832aa - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03832aa   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004020] Calibrating delay loop (skipped), value calculated using timer frequency.. 3053.51 BogoMIPS (lpj=6107020)
[    0.004054] Security Framework initialized
[    0.004066] SELinux:  Disabled at boot.
[    0.004110] AppArmor: AppArmor initialized
[    0.004124] Mount-cache hash table entries: 512
[    0.004481] Initializing cgroup subsys ns
[    0.004489] Initializing cgroup subsys cpuacct
[    0.004493] Initializing cgroup subsys memory
[    0.004517] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004521] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004543] Checking 'hlt' instruction... OK.
[    0.020523] SMP alternatives: switching to UP code
[    0.028051] Freeing SMP alternatives: 11k freed
[    0.028057] ACPI: Core revision 20080609
[    0.033452] ACPI: Checking initramfs for custom DSDT
[    0.584265] ENABLING IO-APIC IRQs
[    0.584686] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.624561] CPU0: AMD Athlon(tm) XP 1800+ stepping 02
[    0.628031] Brought up 1 CPUs
[    0.628031] Total of 1 processors activated (3053.51 BogoMIPS).
[    0.628031] CPU0 attaching sched-domain:
[    0.628031]  domain 0: span 0 level CPU
[    0.628031]   groups: 0
[    0.628031] net_namespace: 840 bytes
[    0.628031] Booting paravirtualized kernel on bare hardware
[    0.628031] Time:  9:13:35  Date: 11/04/08
[    0.628031] NET: Registered protocol family 16
[    0.628031] EISA bus registered
[    0.628031] ACPI: bus type pci registered
[    0.635762] PCI: PCI BIOS revision 2.10 entry at 0xf1550, last bus=1
[    0.635767] PCI: Using configuration type 1 for base access
[    0.639092] ACPI: EC: Look up EC in DSDT
[    0.653166] ACPI: Interpreter enabled
[    0.653178] ACPI: (supports S0 S1 S3 S4 S5)
[    0.653302] ACPI: Using IOAPIC for interrupt routing
[    0.668823] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.668955] PCI: 0000:00:00.0 reg 10 32bit mmio: [e0000000, e3ffffff]
[    0.669033] pci 0000:00:01.0: supports D1
[    0.669058] PCI: 0000:00:08.0 reg 10 io port: [a000, a07f]
[    0.669066] PCI: 0000:00:08.0 reg 14 32bit mmio: [eb001000, eb00107f]
[    0.669208] PCI: 0000:00:09.0 reg 10 io port: [a400, a407]
[    0.669216] PCI: 0000:00:09.0 reg 14 io port: [a800, a803]
[    0.669223] PCI: 0000:00:09.0 reg 18 io port: [ac00, ac07]
[    0.669231] PCI: 0000:00:09.0 reg 1c io port: [b000, b003]
[    0.669238] PCI: 0000:00:09.0 reg 20 io port: [b400, b40f]
[    0.669245] PCI: 0000:00:09.0 reg 24 32bit mmio: [eb000000, eb0001ff]
[    0.669253] PCI: 0000:00:09.0 reg 30 32bit mmio: [0, 7ffff]
[    0.669267] pci 0000:00:09.0: supports D1
[    0.669269] pci 0000:00:09.0: supports D2
[    0.669302] PCI: 0000:00:0f.0 reg 10 io port: [b800, b807]
[    0.669309] PCI: 0000:00:0f.0 reg 14 io port: [bc00, bc03]
[    0.669317] PCI: 0000:00:0f.0 reg 18 io port: [c000, c007]
[    0.669324] PCI: 0000:00:0f.0 reg 1c io port: [c400, c403]
[    0.669332] PCI: 0000:00:0f.0 reg 20 io port: [c800, c80f]
[    0.669340] PCI: 0000:00:0f.0 reg 24 io port: [cc00, ccff]
[    0.669400] PCI: 0000:00:0f.1 reg 20 io port: [d000, d00f]
[    0.669468] PCI: 0000:00:10.0 reg 20 io port: [d400, d41f]
[    0.669489] pci 0000:00:10.0: supports D1
[    0.669491] pci 0000:00:10.0: supports D2
[    0.669495] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.669501] pci 0000:00:10.0: PME# disabled
[    0.669542] PCI: 0000:00:10.1 reg 20 io port: [d800, d81f]
[    0.669563] pci 0000:00:10.1: supports D1
[    0.669566] pci 0000:00:10.1: supports D2
[    0.669569] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.669574] pci 0000:00:10.1: PME# disabled
[    0.669707] PCI: 0000:00:10.2 reg 20 io port: [dc00, dc1f]
[    0.669729] pci 0000:00:10.2: supports D1
[    0.669731] pci 0000:00:10.2: supports D2
[    0.669734] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.669739] pci 0000:00:10.2: PME# disabled
[    0.669782] PCI: 0000:00:10.3 reg 20 io port: [e000, e01f]
[    0.669803] pci 0000:00:10.3: supports D1
[    0.669806] pci 0000:00:10.3: supports D2
[    0.669809] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.669814] pci 0000:00:10.3: PME# disabled
[    0.669840] PCI: 0000:00:10.4 reg 10 32bit mmio: [eb002000, eb0020ff]
[    0.669877] pci 0000:00:10.4: supports D1
[    0.669879] pci 0000:00:10.4: supports D2
[    0.669882] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.669887] pci 0000:00:10.4: PME# disabled
[    0.669947] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.669955] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices
[    0.669994] PCI: 0000:00:11.5 reg 10 io port: [e400, e4ff]
[    0.670033] pci 0000:00:11.5: supports D1
[    0.670035] pci 0000:00:11.5: supports D2
[    0.670062] PCI: 0000:00:11.6 reg 10 io port: [e800, e8ff]
[    0.670217] PCI: 0000:00:12.0 reg 10 io port: [ec00, ecff]
[    0.670225] PCI: 0000:00:12.0 reg 14 32bit mmio: [eb003000, eb0030ff]
[    0.670259] pci 0000:00:12.0: supports D1
[    0.670262] pci 0000:00:12.0: supports D2
[    0.670265] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.670270] pci 0000:00:12.0: PME# disabled
[    0.670319] PCI: 0000:01:00.0 reg 10 32bit mmio: [e4000000, e7ffffff]
[    0.670326] PCI: 0000:01:00.0 reg 14 32bit mmio: [e8000000, e8ffffff]
[    0.670346] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, ffff]
[    0.670360] pci 0000:01:00.0: supports D1
[    0.670362] pci 0000:01:00.0: supports D2
[    0.670396] PCI: bridge 0000:00:01.0 32bit mmio: [e8000000, e9ffffff]
[    0.670402] PCI: bridge 0000:00:01.0 32bit mmio pref: [e4000000, e7ffffff]
[    0.670410] bus 00 -> node 0
[    0.670422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.747895] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.748342] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.748687] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[    0.749083] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.749475] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.749856] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.750144] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.750522] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.750979] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[    0.751412] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.751844] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[    0.752358] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[    0.752722] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.752790] pnp: PnP ACPI init
[    0.752805] ACPI: bus type pnp registered
[    0.762011] pnp: PnP ACPI: found 12 devices
[    0.762017] ACPI: ACPI bus type pnp unregistered
[    0.762023] PnPBIOS: Disabled by ACPI PNP
[    0.762818] PCI: Using ACPI for IRQ routing
[    0.763114] NET: Registered protocol family 8
[    0.763114] NET: Registered protocol family 20
[    0.763114] NetLabel: Initializing
[    0.763114] NetLabel:  domain hash size = 128
[    0.763114] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.763114] NetLabel:  unlabeled traffic allowed by default
[    0.763114] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.763114]    actual entries 65620
[    0.764258] AppArmor: AppArmor Filesystem Enabled
[    0.764285] ACPI: RTC can wake from S4
[    0.764474] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    0.764480] system 00:00: iomem range 0xd4800-0xd7fff has been reserved
[    0.764485] system 00:00: iomem range 0xf0000-0xfbfff could not be reserved
[    0.764489] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.764494] system 00:00: iomem range 0x3dff0000-0x3dffffff could not be reserved
[    0.764499] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.764504] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.764508] system 00:00: iomem range 0x100000-0x3dfeffff could not be reserved
[    0.764513] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.764517] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.764522] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.764536] system 00:02: ioport range 0x400-0x47f has been reserved
[    0.764540] system 00:02: ioport range 0x5000-0x500f has been reserved
[    0.764560] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.764564] system 00:03: ioport range 0x294-0x297 has been reserved
[    0.800401] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.800406] pci 0000:00:01.0:   IO window: disabled
[    0.800413] pci 0000:00:01.0:   MEM window: 0xe8000000-0xe9ffffff
[    0.800419] pci 0000:00:01.0:   PREFETCH window: 0x000000e4000000-0x000000e7ffffff
[    0.800439] pci 0000:00:01.0: setting latency timer to 64
[    0.800445] bus: 00 index 0 io port: [0, ffff]
[    0.800448] bus: 00 index 1 mmio: [0, ffffffff]
[    0.800543] bus: 01 index 0 mmio: [0, 0]
[    0.800546] bus: 01 index 1 mmio: [e8000000, e9ffffff]
[    0.800549] bus: 01 index 2 mmio: [e4000000, e7ffffff]
[    0.800552] bus: 01 index 3 mmio: [0, 0]
[    0.800573] NET: Registered protocol family 2
[    0.800783] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.801529] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.804509] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.805990] TCP: Hash tables configured (established 131072 bind 65536)
[    0.805997] TCP reno registered
[    0.806199] NET: Registered protocol family 1
[    0.806516] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.344299]  it is
[    2.003275] Freeing initrd memory: 8592k freed
[    2.005171] audit: initializing netlink socket (disabled)
[    2.005202] type=2000 audit(1225790015.004:1): initialized
[    2.014731] highmem bounce pool size: 64 pages
[    2.014743] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.019866] VFS: Disk quotas dquot_6.5.1
[    2.020778] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.021011] msgmni has been set to 1762
[    2.021332] io scheduler noop registered
[    2.021336] io scheduler anticipatory registered
[    2.021340] io scheduler deadline registered
[    2.021360] io scheduler cfq registered (default)
[    2.021381] PCI: VIA PCI bridge detected.Disabling DAC.
[    2.021471] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    2.021487] pci 0000:01:00.0: Boot video device
[    2.022258] isapnp: Scanning for PnP cards...
[    2.382409] isapnp: No Plug & Play device found
[    2.467985] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.468193] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.469791] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.473824] brd: module loaded
[    2.473953] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.474171] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.474177] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.474493] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.475570] mice: PS/2 mouse device common for all mice
[    2.475929] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.475975] rtc0: alarms up to one year, y3k
[    2.476325] EISA: Probing bus 0 at eisa.0
[    2.476353] Cannot allocate resource for EISA slot 5
[    2.476368] EISA: Detected 0 cards.
[    2.476375] cpuidle: using governor ladder
[    2.476378] cpuidle: using governor menu
[    2.477371] TCP cubic registered
[    2.477418] Using IPI No-Shortcut mode
[    2.477944] registered taskstats version 1
[    2.478225]   Magic number: 0:451:221
[    2.478314] tty ttyu5: hash matches
[    2.478563] rtc_cmos 00:05: setting system clock to 2008-11-04 09:13:36 UTC (1225790016)
[    2.478593] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.478596] EDD information not available.
[    2.479560] Freeing unused kernel memory: 424k freed
[    2.479738] Write protecting the kernel text: 2576k
[    2.479789] Write protecting the kernel read-only data: 936k
[    2.497640] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.686743] fuse init (API version 7.9)
[    2.720945] fan PNP0C0B:00: registered as cooling_device0
[    2.720958] ACPI: Fan [FAN] (on)
[    2.737800] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.737988] processor ACPI0007:00: registered as cooling_device1
[    2.744548] thermal LNXTHERM:01: registered as thermal_zone0
[    2.746056] ACPI: Thermal Zone [THRM] (63 C)
[    2.780719] device-mapper: uevent: version 1.0.3
[    2.781222] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.825949] md: linear personality registered for level -1
[    2.835709] md: multipath personality registered for level -4
[    2.844637] md: raid0 personality registered for level 0
[    2.856893] md: raid1 personality registered for level 1
[    2.865169] xor: automatically using best checksumming function: pIII_sse
[    2.884006]    pIII_sse  :  1497.000 MB/sec
[    2.884010] xor: using function: pIII_sse (1497.000 MB/sec)
[    2.887185] async_tx: api initialized (async)
[    2.968074] raid6: int32x1    523 MB/s
[    3.036032] raid6: int32x2    569 MB/s
[    3.104059] raid6: int32x4    426 MB/s
[    3.172129] raid6: int32x8    350 MB/s
[    3.240022] raid6: mmxx1      984 MB/s
[    3.308031] raid6: mmxx2     1748 MB/s
[    3.376129] raid6: sse1x1     958 MB/s
[    3.444035] raid6: sse1x2    1564 MB/s
[    3.444039] raid6: using algorithm sse1x2 (1564 MB/s)
[    3.444046] md: raid6 personality registered for level 6
[    3.444049] md: raid5 personality registered for level 5
[    3.444052] md: raid4 personality registered for level 4
[    3.498075] md: raid10 personality registered for level 10
[    3.876818] winbond-840.c:v1.01-e (2.4 port) Sep-11-2006  Donald Becker <becker@scyld.com>
[    3.876822]   http://www.scyld.com/network/drivers.html
[    3.876875] winbond-840 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.877649] eth0: Winbond W89c840 at 0001a000, 00:00:e8:21:d5:15, IRQ 16.
[    3.878276] eth0: MII PHY 0181b802h found at address 1, status 0x782d advertising 05e1.
[    4.043206] No dock devices found.
[    4.210768] SCSI subsystem initialized
[    4.405510] libata version 3.00 loaded.
[    4.429024] sata_sil 0000:00:09.0: version 2.3
[    4.429113] sata_sil 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.450696] scsi0 : sata_sil
[    4.451623] scsi1 : sata_sil
[    4.451801] ata1: SATA max UDMA/100 mmio m512@0xeb000000 tf 0xeb000080 irq 17
[    4.451807] ata2: SATA max UDMA/100 mmio m512@0xeb000000 tf 0xeb0000c0 irq 17
[    4.780079] ata1: SATA link down (SStatus 0 SControl 310)
[    4.830554] usbcore: registered new interface driver usbfs
[    4.830694] usbcore: registered new interface driver hub
[    4.842657] usbcore: registered new device driver usb
[    4.861617] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    4.883882] USB Universal Host Controller Interface driver v3.0
[    5.100185] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    5.124895] ata2.00: ATA-8: WDC WD10EACS-00ZJB0, 01.01B01, max UDMA/133
[    5.124903] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.132714] ata2.00: configured for UDMA/100
[    5.133043] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EACS-00Z 01.0 PQ: 0 ANSI: 5
[    5.134016] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    5.134031] pata_acpi 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    5.134137] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    5.134197] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    5.134230] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    5.134847] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    5.134855] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    5.134865] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    5.134955] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    5.135005] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[    5.135416] usb usb1: configuration #1 chosen from 1 choice
[    5.135464] hub 1-0:1.0: USB hub found
[    5.135481] hub 1-0:1.0: 2 ports detected
[    5.340689] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    5.340710] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    5.340750] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    5.340784] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[    5.341059] usb usb2: configuration #1 chosen from 1 choice
[    5.341108] hub 2-0:1.0: USB hub found
[    5.341126] hub 2-0:1.0: 2 ports detected
[    5.548644] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    5.548665] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    5.548708] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    5.548742] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[    5.549010] usb usb3: configuration #1 chosen from 1 choice
[    5.549078] hub 3-0:1.0: USB hub found
[    5.549095] hub 3-0:1.0: 2 ports detected
[    5.756624] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    5.756645] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    5.756687] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    5.756722] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e000
[    5.757001] usb usb4: configuration #1 chosen from 1 choice
[    5.757045] hub 4-0:1.0: USB hub found
[    5.757062] hub 4-0:1.0: 2 ports detected
[    5.964635] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    5.964667] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    5.964711] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    5.964782] ehci_hcd 0000:00:10.4: irq 21, io mem 0xeb002000
[    5.976193] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.976618] usb usb5: configuration #1 chosen from 1 choice
[    5.976666] hub 5-0:1.0: USB hub found
[    5.976687] hub 5-0:1.0: 8 ports detected
[    6.087493] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    6.087511] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    6.088167] eth1: VIA Rhine II at 0xeb003000, 00:13:d4:55:5b:e7, IRQ 23.
[    6.088983] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    6.106679] sata_via 0000:00:0f.0: version 2.3
[    6.106713] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    6.106795] sata_via 0000:00:0f.0: routed to hard irq line 11
[    6.107751] scsi2 : sata_via
[    6.108036] scsi3 : sata_via
[    6.111241] ata3: SATA max UDMA/133 cmd 0xb800 ctl 0xbc00 bmdma 0xc800 irq 20
[    6.111247] ata4: SATA max UDMA/133 cmd 0xc000 ctl 0xc400 bmdma 0xc808 irq 20
[    6.283985] scsi 1:0:0:0: Attached scsi generic sg0 type 0
[    6.312139] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.340734] Driver 'sd' needs updating - please use bus_type methods
[    6.341039] sd 1:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    6.341077] sd 1:0:0:0: [sda] Write Protect is off
[    6.341082] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.341136] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.341367] sd 1:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[    6.341397] sd 1:0:0:0: [sda] Write Protect is off
[    6.341402] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.341455] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.341464]  sda: sda1 sda2 sda3 sda4
[    6.350747] sd 1:0:0:0: [sda] Attached SCSI disk
[    6.477362] ata3.00: ATA-7: Maxtor 6L250S0, BACE1G10, max UDMA/133
[    6.477370] ata3.00: 490234752 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.493356] ata3.00: configured for UDMA/133
[    6.536798] Marking TSC unstable due to TSC halts in idle
[    6.696047] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.900085] ata4.00: ATA-7: ST3250820AS, 3.AAD, max UDMA/133
[    6.900093] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.975054] ata4.00: configured for UDMA/133
[    6.975271] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6L250S0   BACE PQ: 0 ANSI: 5
[    6.975712] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    6.977152] scsi 3:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
[    6.977549] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[    6.977679] pata_via 0000:00:0f.1: version 0.3.3
[    6.977708] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    6.978177] scsi4 : pata_via
[    6.978365] scsi5 : pata_via
[    6.982077] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[    6.982082] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[    6.982102] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[    6.984091] sd 2:0:0:0: [sdb] Write Protect is off
[    6.984097] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.984746] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.984996] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
[    6.985026] sd 2:0:0:0: [sdb] Write Protect is off
[    6.985031] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.985078] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.985088]  sdb: sdb1
[    7.006744] sd 2:0:0:0: [sdb] Attached SCSI disk
[    7.006869] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    7.006904] sd 3:0:0:0: [sdc] Write Protect is off
[    7.006908] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.006966] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.007072] sd 3:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    7.007105] sd 3:0:0:0: [sdc] Write Protect is off
[    7.007110] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.007169] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.007176]  sdc: sdc1
[    7.023346] sd 3:0:0:0: [sdc] Attached SCSI disk
[    7.164909] ata5.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
[    7.164917] ata5.00: 488397168 sectors, multi 16: LBA48 
[    7.165121] ata5.01: ATA-7: ST3250823A, 3.01, max UDMA/100
[    7.165125] ata5.01: 488397168 sectors, multi 16: LBA48 
[    7.172399] ata5.00: configured for UDMA/100
[    7.180363] ata5.01: configured for UDMA/100
[    7.344439] ata6.00: ATAPI: _NEC DVD_RW ND-3520A, 1.04, max UDMA/33
[    7.360281] ata6.00: configured for UDMA/33
[    7.360492] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
[    7.360935] scsi 4:0:0:0: Attached scsi generic sg3 type 0
[    7.362509] scsi 4:0:1:0: Direct-Access     ATA      ST3250823A       3.01 PQ: 0 ANSI: 5
[    7.362893] scsi 4:0:1:0: Attached scsi generic sg4 type 0
[    7.365243] scsi 5:0:0:0: CD-ROM            _NEC     DVD_RW ND-3520A  1.04 PQ: 0 ANSI: 5
[    7.365575] scsi 5:0:0:0: Attached scsi generic sg5 type 5
[    7.368196] sd 4:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
[    7.371642] sd 4:0:0:0: [sdd] Write Protect is off
[    7.371652] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    7.371759] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.371938] sd 4:0:0:0: [sdd] 488397168 512-byte hardware sectors (250059 MB)
[    7.372091] sd 4:0:0:0: [sdd] Write Protect is off
[    7.372096] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    7.372159] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.372168]  sdd: sdd1
[    7.381634] sd 4:0:0:0: [sdd] Attached SCSI disk
[    7.381892] sd 4:0:1:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    7.381929] sd 4:0:1:0: [sde] Write Protect is off
[    7.381934] sd 4:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    7.381988] sd 4:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.382095] sd 4:0:1:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    7.382125] sd 4:0:1:0: [sde] Write Protect is off
[    7.382130] sd 4:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    7.382181] sd 4:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.382191]  sde: sde1
[    7.401556] sd 4:0:1:0: [sde] Attached SCSI disk
[    7.709671] Driver 'sr' needs updating - please use bus_type methods
[    7.713091] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    7.713102] Uniform CD-ROM driver Revision: 3.20
[    7.713452] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    8.117258] md: md0 stopped.
[    8.461193] md: bind<sdd>
[    8.461495] md: bind<sdc>
[    8.461579] md: md0 stopped.
[    8.461591] md: unbind<sdc>
[    8.461635] md: export_rdev(sdc)
[    8.461644] md: unbind<sdd>
[    8.461683] md: export_rdev(sdd)
[    8.506787] md: bind<sdb1>
[    8.507014] md: bind<sde1>
[    8.550999] md: md0 stopped.
[    8.551028] md: unbind<sde1>
[    8.551425] md: export_rdev(sde1)
[    8.551461] md: unbind<sdb1>
[    8.551496] md: export_rdev(sdb1)
[    8.566970] md: bind<sdd>
[    8.567212] md: bind<sdc>
[    8.567310] md: md0 stopped.
[    8.567323] md: unbind<sdc>
[    8.567367] md: export_rdev(sdc)
[    8.567387] md: unbind<sdd>
[    8.567419] md: export_rdev(sdd)
[    8.575847] md: bind<sdb1>
[    8.576073] md: bind<sde1>
[    8.646198] md: md0 stopped.
[    8.646228] md: unbind<sde1>
[    8.646515] md: export_rdev(sde1)
[    8.646550] md: unbind<sdb1>
[    8.646584] md: export_rdev(sdb1)
[    8.658587] md: bind<sdd>
[    8.658837] md: bind<sdc>
[    8.658930] md: md0 stopped.
[    8.658942] md: unbind<sdc>
[    8.658984] md: export_rdev(sdc)
[    8.659004] md: unbind<sdd>
[    8.659036] md: export_rdev(sdd)
[    8.667216] md: bind<sdb1>
[    8.667446] md: bind<sde1>
[    8.714825] md: md0 stopped.
[    8.714854] md: unbind<sde1>
[    8.714964] md: export_rdev(sde1)
[    8.714998] md: unbind<sdb1>
[    8.715032] md: export_rdev(sdb1)
[    8.733490] md: bind<sdd>
[    8.733736] md: bind<sdc>
[    8.733817] md: md0 stopped.
[    8.733829] md: unbind<sdc>
[    8.733872] md: export_rdev(sdc)
[    8.733892] md: unbind<sdd>
[    8.733924] md: export_rdev(sdd)
[    8.742231] md: bind<sdb1>
[    8.742457] md: bind<sde1>
[    8.870946] kjournald starting.  Commit interval 5 seconds
[    8.870977] EXT3-fs: mounted filesystem with ordered data mode.
[   10.952411] udevd version 124 started
[   12.047293] Linux agpgart interface v0.103
[   12.105399] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.124173] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.135839] agpgart: Detected VIA KM400/KM400A chipset
[   12.198856] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   12.898557] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.908770] ACPI: Power Button (FF) [PWRF]
[   12.908987] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.924054] ACPI: Power Button (CM) [PWRB]
[   12.924470] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   12.936159] ACPI: Sleep Button (CM) [SLPB]
[   14.435647] parport_pc 00:09: reported by Plug and Play ACPI
[   14.435748] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   16.813732] VIA 82xx Modem 0000:00:11.6: enabling device (0000 -> 0001)
[   16.814389] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   16.814403] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   16.837301] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   17.217421] md: md0 stopped.
[   17.217450] md: unbind<sde1>
[   17.228123] md: export_rdev(sde1)
[   17.228255] md: unbind<sdb1>
[   17.240182] md: export_rdev(sdb1)
[   17.564053] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   17.598324] md: bind<sdb1>
[   17.598653] md: bind<sde1>
[   17.664568] md: md0 stopped.
[   17.664599] md: unbind<sde1>
[   17.668339] md: export_rdev(sde1)
[   17.668371] md: unbind<sdb1>
[   17.676189] md: export_rdev(sdb1)
[   17.701039] md: bind<sdb1>
[   17.701253] md: bind<sde1>
[   17.873000] md: md0 stopped.
[   17.873029] md: unbind<sde1>
[   17.884313] md: export_rdev(sde1)
[   17.884420] md: unbind<sdb1>
[   17.892067] md: export_rdev(sdb1)
[   17.922255] md: bind<sdb1>
[   17.922483] md: bind<sde1>
[   18.068354] VIA 82xx Modem 0000:00:11.6: PCI INT C disabled
[   18.068385] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   18.068482] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   18.068715] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   18.584822] codec_read: codec 0 is not valid [0xfe0000]
[   18.592445] codec_read: codec 0 is not valid [0xfe0000]
[   18.601659] codec_read: codec 0 is not valid [0xfe0000]
[   18.615453] codec_read: codec 0 is not valid [0xfe0000]
[   21.702176] loop: module loaded
[   21.725557] lp0: using parport0 (interrupt-driven).
[   22.199450] Adding 5242872k swap on /dev/mapper/unsafeDisk-swap.  Priority:-1 extents:1 across:5242872k
[   22.737153] EXT3 FS on sda2, internal journal
[   23.819314] kjournald starting.  Commit interval 5 seconds
[   23.819830] EXT3 FS on sda1, internal journal
[   23.819839] EXT3-fs: mounted filesystem with ordered data mode.
[   23.852324] kjournald starting.  Commit interval 5 seconds
[   23.852593] EXT3 FS on sda3, internal journal
[   23.852602] EXT3-fs: mounted filesystem with ordered data mode.
[   24.671501] type=1505 audit(1225790039.159:2): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3896
[   24.891846] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.993115] eth0: Setting 100MBit-full-duplex based on MII#1
[   26.313126] NET: Registered protocol family 17
[   30.355219] NET: Registered protocol family 10
[   30.356151] lo: Disabled Privacy Extensions
[   36.628339] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   36.631324] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   36.631342] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   36.631347] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   38.005116] NET: Registered protocol family 5
[   41.032040] eth0: no IPv6 routers present

```

Thanks for any help!

---

### Post by amund on 2008-11-04
I've been doing some testing, and I think I've found the problem. 

It has something to do with the mdadm package. When I install the it, it will tell something like: "update-initramfs: Generating /boot/initrd.img-2.6.27-7-server". What I've found is that when using the server kernel, it will generate initrd for the generic kernel, and that is the wrong kernel.

What I did was removing the generic kernel. Remove and install the mdadm package. And now the mdadm package generated the initrd for the server kernel. For now, everything works ok. Hopefully, this was the problem. I will come back and update the post later if the problem persist. 

Anyone knows what the mdadm package is doing with the initrd image?

---

### Post by psusi on 2008-11-04
> **amund said:**
> 
Anyone knows what the mdadm package is doing with the initrd image?

It is installing itself into the initrd image.

I thought you said the problem was that /dev/sde1 wasn't showing up, not that mdadm wasn't recognizing the raid arrays?

---

### Post by amund on 2008-11-06
Both are my problems. I want to build the raid, but I can't because the partitions are missing. I didn't think mdadm could cause something like this. And the weird part is that it's only the ide disks that are affected.

I'm still not sure what the problem is, but now everything is working so I'm happy :)

---

