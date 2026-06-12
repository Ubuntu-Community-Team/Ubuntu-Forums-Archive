---
title: "Mygica X8507"
date: 2011-06-11
forum: Hardware
---

### Post by Fistandantilus on 2011-06-11
Hola!!!, Justo estaba leyendo el HOW-TO para TDA y me acorde de mi placa. Hace un tiempito me compre un Mygica X8507 que funciona perfectamente en win pero me estoy volviendo loco para hacerla funcionar en linux. 
Hasta el momento lo que hice fue esto: 

[LIST]
[*]me descarge los fuentes de linuxtv, compile e instale
[*]cree el archivo /etc/modprobe.d/cx23885.conf con la línea "options cx23885 card=22". El listado de opciones se puede ver [http://linuxtv.org/wiki/index.php/Geniatech/MyGica_X8507_PCI-Express_Hybrid_Card](http://linuxtv.org/wiki/index.php/Geniatech/MyGica_X8507_PCI-Express_Hybrid_Card)
[*]y me baje el firmware "dvb-fe-xc5000-1.6.114.fw" desde [http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)
[/LIST]
Mi idea es 1ero configurar tv analogica, pero ni eso pude conseguir. En tvtime se ve bien pero no se escucha y en mythtv se ve re mal, no se escucha y si cambio de canal o salgo se pincha el mythfrontend :(

Por el tema de tvtime ya me debo haber hecho como 3 how-to para arreglar el tema del audio que no parece muy raro que digamos. 
Y por el tema del mythtv en un principio al problema lo apunte como si estuviera tomando mal la norma PAL-N hasta que comprobe en las configuraciones que se guardan en mysql que efectivamente estaba tomando la norma PAL-N.

Ya no se para donde disparar...

No se si es problema de hardware, de software o de los dos....

denmen una mano por favor.

PD: Nunca está de mas:

lsmod
```
Module                  Size  Used by
usb_storage            50377  0 
lgs8gxx                12573  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
nfsd                  304374  11 
lockd                  75079  1 nfsd
nfs_acl                 2709  1 nfsd
auth_rpcgss            44452  1 nfsd
sunrpc                228003  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                4202  1 nfsd
joydev                 11104  0 
xc5000                 13475  2 
tuner                  20525  1 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_analog    78702  1 
ir_lirc_codec           4802  0 
lirc_dev               14330  1 ir_lirc_codec
ir_sony_decoder         2261  0 
ir_jvc_decoder          2386  0 
ir_rc6_decoder          2834  0 
ir_rc5_decoder          2290  0 
ir_nec_decoder          2706  0 
cx25840                43932  1 
cx23885               142313  0 
rc_core                19732  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx23885
snd_hda_intel          25805  4 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
cx2341x                20093  1 cx23885
videobuf_dma_sg         9941  1 cx23885
videobuf_dvb            6180  1 cx23885
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
dvb_core              102292  2 cx23885,videobuf_dvb
videobuf_core          20300  3 cx23885,videobuf_dma_sg,videobuf_dvb
fbcon                  39270  71 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tileblit                2487  1 fbcon
v4l2_common            11302  4 tuner,cx25840,cx23885,cx2341x
font                    8053  1 fbcon
videodev               85001  5 tuner,cx25840,cx23885,cx2341x,v4l2_common
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
media                  13792  1 videodev
asus_atk0110           10033  0 
hwmon_vid               3130  0 
snd                    71283  19 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
fglrx                2776051  242 
vga16fb                12757  1 
psmouse                64576  0 
vgastate                9857  1 vga16fb
serio_raw               4918  0 
i2c_piix4               9639  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32     8551  1 videodev
btcx_risc               4224  1 cx23885
tveeprom               14074  1 cx23885
edac_core              45423  0 
lp                      9336  0 
edac_mce_amd            9278  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83600  1 usbhid
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
pata_atiixp             4209  0 
r8169                  39714  0 
ahci                   38030  6 
mii                     5237  1 r8169

```dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-32-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 (Ubuntu 2.6.32-32.62-generic 2.6.32.38+drm33.16)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-generic root=UUID=7efe8783-fc3b-4103-abe6-be6e6f80ade9 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000c7f90000 (usable)
[    0.000000]  BIOS-e820: 00000000c7f90000 - 00000000c7fa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c7fa8000 - 00000000c7fd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c7fd0000 - 00000000c8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000238000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x238000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF8000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000238000000 aka 9088M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c8000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xc7f90 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000c7f90000 (usable)
[    0.000000]  modified: 00000000c7f90000 - 00000000c7fa8000 (ACPI data)
[    0.000000]  modified: 00000000c7fa8000 - 00000000c7fd0000 (ACPI NVS)
[    0.000000]  modified: 00000000c7fd0000 - 00000000c8000000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000238000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000c7f90000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00c7e00000 page 2M
[    0.000000]  00c7e00000 - 00c7f90000 page 4k
[    0.000000] kernel direct mapping tables up to c7f90000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-0000000238000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0200000000 page 1G
[    0.000000]  0200000000 - 0238000000 page 2M
[    0.000000] kernel direct mapping tables up to 238000000 @ 12000-14000
[    0.000000] RAMDISK: 3779c000 - 37fef7b4
[    0.000000] ACPI: RSDP 00000000000fbd80 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000c7f90000 0003C (v01 091109 RSDT1458 20090911 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000c7f90200 00084 (v01 091109 FACP1458 20090911 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 (20090903/tbfadt-557)
[    0.000000] ACPI: DSDT 00000000c7f90440 0F4BE (v01  A1303 A1303000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 00000000c7fa8000 00040
[    0.000000] ACPI: APIC 00000000c7f90390 0006C (v01 091109 APIC1458 20090911 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000c7f90400 0003C (v01 091109 OEMMCFG  20090911 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000c7fa8040 00072 (v01 091109 OEMB1458 20090911 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000c7f9f910 00038 (v01 091109 OEMHPET  20090911 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000c7f9f950 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000238000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000238000000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000005efff] pages 47
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0238000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a30a64]    TEXT DATA BSS ==> [0001000000 - 0001a30a64]
[    0.000000]   #3 [003779c000 - 0037fef7b4]          RAMDISK ==> [003779c000 - 0037fef7b4]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0001a31000 - 0001a312a4]              BRK ==> [0001a31000 - 0001a312a4]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] Reserving 128MB of memory at 32MB for crashkernel (System RAM: 9088MB)
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880028600000-ffff88002f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00238000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000c7f90
[    0.000000]     0: 0x00100000 -> 0x00238000
[    0.000000] On node 0 totalpages: 2096927
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3825 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 800712 pages, LIFO batch:31
[    0.000000]   Normal zone: 17472 pages used for memmap
[    0.000000]   Normal zone: 1260480 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000c7f90000 - 00000000c7fa8000
[    0.000000] PM: Registered nosave memory: 00000000c7fa8000 - 00000000c7fd0000
[    0.000000] PM: Registered nosave memory: 00000000c7fd0000 - 00000000c8000000
[    0.000000] PM: Registered nosave memory: 00000000c8000000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c8000000 (gap: c8000000:37e00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91864 r8192 d22824 u524288
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2065017
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-generic root=UUID=7efe8783-fc3b-4103-abe6-be6e6f80ade9 ro crashkernel=384M-2G:64M,2G-:128M quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 20000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 8054600k/9306112k available (5411k kernel code, 918404k absent, 333108k reserved, 2982k data, 888k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 83886080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3411.416 MHz processor.
[    0.030004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6822.82 BogoMIPS (lpj=34114110)
[    0.030019] Security Framework initialized
[    0.030031] AppArmor: AppArmor initialized
[    0.030458] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.032426] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.033306] Mount-cache hash table entries: 256
[    0.033387] Initializing cgroup subsys ns
[    0.033390] Initializing cgroup subsys cpuacct
[    0.033392] Initializing cgroup subsys memory
[    0.033397] Initializing cgroup subsys devices
[    0.033398] Initializing cgroup subsys freezer
[    0.033400] Initializing cgroup subsys net_cls
[    0.033412] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.033414] CPU: L2 Cache: 512K (64 bytes/line)
[    0.033416] CPU 0/0x0 -> Node 0
[    0.033418] tseg: 0000000000
[    0.033427] CPU: Physical Processor ID: 0
[    0.033428] CPU: Processor Core ID: 0
[    0.033430] mce: CPU supports 6 MCE banks
[    0.033437] Performance Events: AMD PMU driver.
[    0.033440] ... version:                0
[    0.033441] ... bit width:              48
[    0.033442] ... generic registers:      4
[    0.033444] ... value mask:             0000ffffffffffff
[    0.033445] ... max period:             00007fffffffffff
[    0.033446] ... fixed-purpose events:   0
[    0.033447] ... event mask:             000000000000000f
[    0.034543] ACPI: Core revision 20090903
[    0.050005] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.050008] ftrace: allocating 22476 entries in 89 pages
[    0.060053] Setting APIC routing to flat
[    0.060345] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.160391] CPU0: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.170000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.040000] Initializing CPU#1
[    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.040000] CPU 1/0x1 -> Node 0
[    0.040000] CPU: Physical Processor ID: 0
[    0.040000] CPU: Processor Core ID: 1
[    0.320028] CPU1: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.320033] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.330047] Booting processor 2 APIC 0x2 ip 0x6000
[    0.040000] Initializing CPU#2
[    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.040000] CPU 2/0x2 -> Node 0
[    0.040000] CPU: Physical Processor ID: 0
[    0.040000] CPU: Processor Core ID: 2
[    0.490080] CPU2: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.490085] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.500041] Booting processor 3 APIC 0x3 ip 0x6000
[    0.040000] Initializing CPU#3
[    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.040000] CPU 3/0x3 -> Node 0
[    0.040000] CPU: Physical Processor ID: 0
[    0.040000] CPU: Processor Core ID: 3
[    0.660035] CPU3: AMD Phenom(tm) II X4 965 Processor stepping 02
[    0.660040] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.670008] Brought up 4 CPUs
[    0.670009] Total of 4 processors activated (27292.61 BogoMIPS).
[    0.672267] CPU0 attaching sched-domain:
[    0.672271]  domain 0: span 0-3 level MC
[    0.672272]   groups: 0 1 2 3
[    0.672277] CPU1 attaching sched-domain:
[    0.672278]  domain 0: span 0-3 level MC
[    0.672279]   groups: 1 2 3 0
[    0.672282] CPU2 attaching sched-domain:
[    0.672283]  domain 0: span 0-3 level MC
[    0.672284]   groups: 2 3 0 1
[    0.672287] CPU3 attaching sched-domain:
[    0.672288]  domain 0: span 0-3 level MC
[    0.672289]   groups: 3 0 1 2
[    0.672354] devtmpfs: initialized
[    0.672354] regulator: core version 0.5
[    0.672354] Time: 19:17:03  Date: 06/10/11
[    0.672354] NET: Registered protocol family 16
[    0.672354] node 0 link 0: io port [1000, ffffff]
[    0.672354] TOM: 00000000c8000000 aka 3200M
[    0.672354] Fam 10h mmconf [e0000000, efffffff]
[    0.672354] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.672354] node 0 link 0: mmio [f0000000, ffffffff]
[    0.672354] node 0 link 0: mmio [a0000, bffff]
[    0.672354] node 0 link 0: mmio [c8000000, dfffffff]
[    0.672354] TOM2: 0000000238000000 aka 9088M
[    0.672354] Trying to unpack rootfs image as initramfs...
[    0.672354] bus: [00,07] on node 0 link 0
[    0.672354] bus: 00 index 0 io port: [0, ffff]
[    0.672354] bus: 00 index 1 mmio: [f0000000, ffffffff]
[    0.672354] bus: 00 index 2 mmio: [a0000, bffff]
[    0.672354] bus: 00 index 3 mmio: [c8000000, dfffffff]
[    0.672354] bus: 00 index 4 mmio: [238000000, fcffffffff]
[    0.672354] ACPI: bus type pci registered
[    0.672354] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.672354] PCI: Not using MMCONFIG.
[    0.672354] PCI: Using configuration type 1 for base access
[    0.672354] PCI: Using configuration type 1 for extended access
[    0.672354] bio: create slab <bio-0> at 0
[    0.672354] ACPI: EC: Look up EC in DSDT
[    0.672354] ACPI Error (psargs-0359): [ECEN] Namespace lookup failure, AE_NOT_FOUND
[    0.672354] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node ffffffff81a0f040), AE_NOT_FOUND
[    0.672354] ACPI Error (dswload-0781): [PRID] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.672354] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20090903/psloop-230)
[    0.672354] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node ffffffff81a0f040), AE_ALREADY_EXISTS
[    0.672354] ACPI: Marking method \___ as Serialized because of AE_ALREADY_EXISTS error
[    0.672354] ACPI: Executed 3 blocks of module-level executable AML code
[    0.793842] Freeing initrd memory: 8525k freed
[    0.912057] ACPI: Interpreter enabled
[    0.912062] ACPI: (supports S0 S1 S3 S4 S5)
[    0.912078] ACPI: Using IOAPIC for interrupt routing
[    0.912124] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.913575] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.917591] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.921214] ACPI: No dock devices found.
[    0.921325] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.921360] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.921410] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.921413] pci 0000:00:02.0: PME# disabled
[    0.921446] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.921448] pci 0000:00:04.0: PME# disabled
[    0.921481] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.921483] pci 0000:00:07.0: PME# disabled
[    0.921515] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.921517] pci 0000:00:09.0: PME# disabled
[    0.921564] pci 0000:00:11.0: reg 10 io port: [0xb000-0xb007]
[    0.921570] pci 0000:00:11.0: reg 14 io port: [0xa000-0xa003]
[    0.921576] pci 0000:00:11.0: reg 18 io port: [0x9000-0x9007]
[    0.921582] pci 0000:00:11.0: reg 1c io port: [0x8000-0x8003]
[    0.921588] pci 0000:00:11.0: reg 20 io port: [0x7000-0x700f]
[    0.921594] pci 0000:00:11.0: reg 24 32bit mmio: [0xfbafe400-0xfbafe7ff]
[    0.921611] pci 0000:00:11.0: set SATA to AHCI mode
[    0.921656] pci 0000:00:12.0: reg 10 32bit mmio: [0xfbaf6000-0xfbaf6fff]
[    0.921708] pci 0000:00:12.1: reg 10 32bit mmio: [0xfbaf7000-0xfbaf7fff]
[    0.921777] pci 0000:00:12.2: reg 10 32bit mmio: [0xfbafe800-0xfbafe8ff]
[    0.921827] pci 0000:00:12.2: supports D1 D2
[    0.921828] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.921831] pci 0000:00:12.2: PME# disabled
[    0.921862] pci 0000:00:13.0: reg 10 32bit mmio: [0xfbafc000-0xfbafcfff]
[    0.921914] pci 0000:00:13.1: reg 10 32bit mmio: [0xfbafd000-0xfbafdfff]
[    0.921982] pci 0000:00:13.2: reg 10 32bit mmio: [0xfbafec00-0xfbafecff]
[    0.922032] pci 0000:00:13.2: supports D1 D2
[    0.922033] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.922037] pci 0000:00:13.2: PME# disabled
[    0.922148] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.922154] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.922160] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.922165] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.922171] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.922234] pci 0000:00:14.2: reg 10 64bit mmio: [0xfbaf8000-0xfbafbfff]
[    0.922275] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.922278] pci 0000:00:14.2: PME# disabled
[    0.922379] pci 0000:00:14.5: reg 10 32bit mmio: [0xfbaff000-0xfbafffff]
[    0.922516] pci 0000:05:00.0: reg 10 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.922523] pci 0000:05:00.0: reg 18 64bit mmio: [0xfbfc0000-0xfbfdffff]
[    0.922528] pci 0000:05:00.0: reg 20 io port: [0xe000-0xe0ff]
[    0.922535] pci 0000:05:00.0: reg 30 32bit mmio pref: [0xfbfa0000-0xfbfbffff]
[    0.922551] pci 0000:05:00.0: supports D1 D2
[    0.922580] pci 0000:05:00.1: reg 10 64bit mmio: [0xfbffc000-0xfbffffff]
[    0.922610] pci 0000:05:00.1: supports D1 D2
[    0.922660] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.922662] pci 0000:00:02.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.922666] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.922698] pci 0000:04:00.0: reg 10 io port: [0xd800-0xd8ff]
[    0.922712] pci 0000:04:00.0: reg 18 64bit mmio: [0xfbeff000-0xfbefffff]
[    0.922722] pci 0000:04:00.0: reg 20 64bit mmio pref: [0xcfff0000-0xcfffffff]
[    0.922728] pci 0000:04:00.0: reg 30 32bit mmio pref: [0xfbec0000-0xfbedffff]
[    0.922755] pci 0000:04:00.0: supports D1 D2
[    0.922756] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.922759] pci 0000:04:00.0: PME# disabled
[    0.922815] pci 0000:00:04.0: bridge io port: [0xd000-0xdfff]
[    0.922818] pci 0000:00:04.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]
[    0.922821] pci 0000:00:04.0: bridge 64bit mmio pref: [0xcff00000-0xcfffffff]
[    0.922869] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbc00000-0xfbdfffff]
[    0.922954] pci 0000:03:00.0: supports D1 D2
[    0.922956] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    0.922961] pci 0000:03:00.0: PME# disabled
[    0.923022] pci 0000:00:07.0: bridge 32bit mmio: [0xfbc00000-0xfbdfffff]
[    0.923087] pci 0000:02:00.0: reg 10 64bit mmio: [0xfbbff800-0xfbbfffff]
[    0.923096] pci 0000:02:00.0: reg 18 io port: [0xc800-0xc8ff]
[    0.923171] pci 0000:02:00.0: supports D2
[    0.923173] pci 0000:02:00.0: PME# supported from D2 D3hot D3cold
[    0.923178] pci 0000:02:00.0: PME# disabled
[    0.923240] pci 0000:00:09.0: bridge io port: [0xc000-0xcfff]
[    0.923242] pci 0000:00:09.0: bridge 32bit mmio: [0xfbb00000-0xfbbfffff]
[    0.923298] pci 0000:00:14.4: transparent bridge
[    0.923320] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.923465] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.923507] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.923550] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.923589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    0.923644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.926855] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.926934] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.927012] ACPI: PCI Interrupt Link [LNKC] (IRQs *4 7 10 11 12 14 15)
[    0.927090] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.927168] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 *10 11 12 14 15)
[    0.927246] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 *11 12 14 15)
[    0.927324] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 *10 11 12 14 15)
[    0.927402] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 *10 11 12 14 15)
[    0.927474] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.927477] vgaarb: loaded
[    0.927540] SCSI subsystem initialized
[    0.927557] libata version 3.00 loaded.
[    0.927557] usbcore: registered new interface driver usbfs
[    0.927557] usbcore: registered new interface driver hub
[    0.927557] usbcore: registered new device driver usb
[    0.927557] ACPI: WMI: Mapper loaded
[    0.927557] PCI: Using ACPI for IRQ routing
[    0.927557] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.927557] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.927557] NetLabel: Initializing
[    0.927557] NetLabel:  domain hash size = 128
[    0.927557] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.927557] NetLabel:  unlabeled traffic allowed by default
[    0.927557] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.927557] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.927557] Switching to clocksource tsc
[    0.930916] AppArmor: AppArmor Filesystem Enabled
[    0.930924] pnp: PnP ACPI init
[    0.930931] ACPI: bus type pnp registered
[    0.932131] pnp 00:0a: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.932133] pnp 00:0a: mem resource (0xc0000-0xcffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.932135] pnp 00:0a: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.932137] pnp 00:0a: mem resource (0x100000-0xc7ffffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.932397] pnp: PnP ACPI: found 11 devices
[    0.932398] ACPI: ACPI bus type pnp unregistered
[    0.932405] system 00:06: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.932407] system 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.932410] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.932412] system 00:07: ioport range 0x40b-0x40b has been reserved
[    0.932414] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[    0.932415] system 00:07: ioport range 0xc00-0xc01 has been reserved
[    0.932417] system 00:07: ioport range 0xc14-0xc14 has been reserved
[    0.932419] system 00:07: ioport range 0xc50-0xc51 has been reserved
[    0.932420] system 00:07: ioport range 0xc52-0xc52 has been reserved
[    0.932422] system 00:07: ioport range 0xc6c-0xc6c has been reserved
[    0.932425] system 00:07: ioport range 0xc6f-0xc6f has been reserved
[    0.932426] system 00:07: ioport range 0xcd0-0xcd1 has been reserved
[    0.932428] system 00:07: ioport range 0xcd2-0xcd3 has been reserved
[    0.932430] system 00:07: ioport range 0xcd4-0xcd5 has been reserved
[    0.932431] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
[    0.932433] system 00:07: ioport range 0xcd8-0xcdf has been reserved
[    0.932434] system 00:07: ioport range 0xb00-0xb3f has been reserved
[    0.932436] system 00:07: ioport range 0x800-0x89f has been reserved
[    0.932438] system 00:07: ioport range 0xb00-0xb0f has been reserved
[    0.932439] system 00:07: ioport range 0xb20-0xb3f has been reserved
[    0.932441] system 00:07: ioport range 0x900-0x90f has been reserved
[    0.932443] system 00:07: ioport range 0x910-0x91f has been reserved
[    0.932445] system 00:07: ioport range 0xfe00-0xfefe has been reserved
[    0.932447] system 00:07: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.932448] system 00:07: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.932451] system 00:08: ioport range 0x230-0x23f has been reserved
[    0.932453] system 00:08: ioport range 0x290-0x29f has been reserved
[    0.932454] system 00:08: ioport range 0xf40-0xf4f has been reserved
[    0.932456] system 00:08: ioport range 0xa30-0xa3f has been reserved
[    0.932459] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.932465] system 00:0a: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.937091] pci 0000:00:02.0: PCI bridge, secondary bus 0000:05
[    0.937093] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.937096] pci 0000:00:02.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.937098] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.937102] pci 0000:00:04.0: PCI bridge, secondary bus 0000:04
[    0.937104] pci 0000:00:04.0:   IO window: 0xd000-0xdfff
[    0.937106] pci 0000:00:04.0:   MEM window: 0xfbe00000-0xfbefffff
[    0.937108] pci 0000:00:04.0:   PREFETCH window: 0x000000cff00000-0x000000cfffffff
[    0.937112] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.937113] pci 0000:00:07.0:   IO window: disabled
[    0.937115] pci 0000:00:07.0:   MEM window: 0xfbc00000-0xfbdfffff
[    0.937117] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.937120] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.937122] pci 0000:00:09.0:   IO window: 0xc000-0xcfff
[    0.937125] pci 0000:00:09.0:   MEM window: 0xfbb00000-0xfbbfffff
[    0.937126] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.937129] pci 0000:00:14.4: PCI bridge, secondary bus 0000:01
[    0.937131] pci 0000:00:14.4:   IO window: disabled
[    0.937135] pci 0000:00:14.4:   MEM window: disabled
[    0.937138] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.937148]   alloc irq_desc for 18 on node 0
[    0.937150]   alloc kstat_irqs on node 0
[    0.937153] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.937156] pci 0000:00:02.0: setting latency timer to 64
[    0.937160]   alloc irq_desc for 16 on node 0
[    0.937161]   alloc kstat_irqs on node 0
[    0.937163] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.937165] pci 0000:00:04.0: setting latency timer to 64
[    0.937169]   alloc irq_desc for 19 on node 0
[    0.937170]   alloc kstat_irqs on node 0
[    0.937172] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.937174] pci 0000:00:07.0: setting latency timer to 64
[    0.937178]   alloc irq_desc for 17 on node 0
[    0.937179]   alloc kstat_irqs on node 0
[    0.937180] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.937183] pci 0000:00:09.0: setting latency timer to 64
[    0.937189] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.937191] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.937192] pci_bus 0000:05: resource 0 io:  [0xe000-0xefff]
[    0.937194] pci_bus 0000:05: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.937196] pci_bus 0000:05: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.937197] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
[    0.937199] pci_bus 0000:04: resource 1 mem: [0xfbe00000-0xfbefffff]
[    0.937201] pci_bus 0000:04: resource 2 pref mem [0xcff00000-0xcfffffff]
[    0.937202] pci_bus 0000:03: resource 1 mem: [0xfbc00000-0xfbdfffff]
[    0.937204] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.937206] pci_bus 0000:02: resource 1 mem: [0xfbb00000-0xfbbfffff]
[    0.937207] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.937209] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.937228] NET: Registered protocol family 2
[    0.937368] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.938277] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.940187] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.940420] TCP: Hash tables configured (established 524288 bind 65536)
[    0.940422] TCP reno registered
[    0.940483] NET: Registered protocol family 1
[    1.100035] pci 0000:05:00.0: Boot video device
[    1.100796] PCI-DMA: Disabling AGP.
[    1.100878] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    1.100879] PCI-DMA: using GART IOMMU.
[    1.100881] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.102619] Scanning for low memory corruption every 60 seconds
[    1.102698] audit: initializing netlink socket (disabled)
[    1.102711] type=2000 audit(1307733423.100:1): initialized
[    1.108202] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.108997] VFS: Disk quotas dquot_6.5.2
[    1.109026] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.109356] fuse init (API version 7.13)
[    1.109397] msgmni has been set to 15748
[    1.109567] alg: No test for stdrng (krng)
[    1.109597] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.109599] io scheduler noop registered
[    1.109600] io scheduler anticipatory registered
[    1.109601] io scheduler deadline registered
[    1.109621] io scheduler cfq registered (default)
[    1.109718]   alloc irq_desc for 24 on node 0
[    1.109720]   alloc kstat_irqs on node 0
[    1.109725] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    1.109730] pcieport 0000:00:02.0: setting latency timer to 64
[    1.109817]   alloc irq_desc for 25 on node 0
[    1.109818]   alloc kstat_irqs on node 0
[    1.109822] pcieport 0000:00:04.0: irq 25 for MSI/MSI-X
[    1.109825] pcieport 0000:00:04.0: setting latency timer to 64
[    1.109905]   alloc irq_desc for 26 on node 0
[    1.109906]   alloc kstat_irqs on node 0
[    1.109909] pcieport 0000:00:07.0: irq 26 for MSI/MSI-X
[    1.109913] pcieport 0000:00:07.0: setting latency timer to 64
[    1.109990]   alloc irq_desc for 27 on node 0
[    1.109991]   alloc kstat_irqs on node 0
[    1.109994] pcieport 0000:00:09.0: irq 27 for MSI/MSI-X
[    1.109998] pcieport 0000:00:09.0: setting latency timer to 64
[    1.110059] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.110073] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.110130] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.110133] ACPI: Power Button [PWRB]
[    1.110163] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.110165] ACPI: Power Button [PWRF]
[    1.110413] processor LNXCPU:00: registered as cooling_device0
[    1.110445] processor LNXCPU:01: registered as cooling_device1
[    1.110466] processor LNXCPU:02: registered as cooling_device2
[    1.110483] processor LNXCPU:03: registered as cooling_device3
[    1.111881] Linux agpgart interface v0.103
[    1.111902] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.112521] brd: module loaded
[    1.112754] loop: module loaded
[    1.112797] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.112903] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.112923] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.113114] Fixed MDIO Bus: probed
[    1.113132] PPP generic driver version 2.4.2
[    1.113159] tun: Universal TUN/TAP device driver, 1.6
[    1.113161] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.113211] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.113239]   alloc irq_desc for 20 on node 0
[    1.113240]   alloc kstat_irqs on node 0
[    1.113244] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.113264] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.113287] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.113315] ehci_hcd 0000:00:12.2: debug port 1
[    1.113331] ehci_hcd 0000:00:12.2: irq 20, io mem 0xfbafe800
[    1.130018] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.130081] usb usb1: configuration #1 chosen from 1 choice
[    1.130098] hub 1-0:1.0: USB hub found
[    1.130102] hub 1-0:1.0: 6 ports detected
[    1.130178]   alloc irq_desc for 23 on node 0
[    1.130180]   alloc kstat_irqs on node 0
[    1.130183] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    1.130193] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.130215] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.130239] ehci_hcd 0000:00:13.2: debug port 1
[    1.130255] ehci_hcd 0000:00:13.2: irq 23, io mem 0xfbafec00
[    1.150017] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.150066] usb usb2: configuration #1 chosen from 1 choice
[    1.150080] hub 2-0:1.0: USB hub found
[    1.150084] hub 2-0:1.0: 6 ports detected
[    1.150140] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.150172] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.150183] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.150201] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.150221] ohci_hcd 0000:00:12.0: irq 19, io mem 0xfbaf6000
[    1.214081] usb usb3: configuration #1 chosen from 1 choice
[    1.214095] hub 3-0:1.0: USB hub found
[    1.214102] hub 3-0:1.0: 3 ports detected
[    1.214174] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.214183] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.214201] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.214215] ohci_hcd 0000:00:12.1: irq 19, io mem 0xfbaf7000
[    1.274075] usb usb4: configuration #1 chosen from 1 choice
[    1.274089] hub 4-0:1.0: USB hub found
[    1.274095] hub 4-0:1.0: 3 ports detected
[    1.274165]   alloc irq_desc for 21 on node 0
[    1.274166]   alloc kstat_irqs on node 0
[    1.274169] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.274180] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.274199] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.274218] ohci_hcd 0000:00:13.0: irq 21, io mem 0xfbafc000
[    1.334083] usb usb5: configuration #1 chosen from 1 choice
[    1.334098] hub 5-0:1.0: USB hub found
[    1.334104] hub 5-0:1.0: 3 ports detected
[    1.334173] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.334183] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.334205] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.334219] ohci_hcd 0000:00:13.1: irq 21, io mem 0xfbafd000
[    1.394076] usb usb6: configuration #1 chosen from 1 choice
[    1.394089] hub 6-0:1.0: USB hub found
[    1.394096] hub 6-0:1.0: 3 ports detected
[    1.394167] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.394178] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.394196] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.394215] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbaff000
[    1.454079] usb usb7: configuration #1 chosen from 1 choice
[    1.454093] hub 7-0:1.0: USB hub found
[    1.454099] hub 7-0:1.0: 2 ports detected
[    1.454148] uhci_hcd: USB Universal Host Controller Interface driver
[    1.454188] PNP: No PS/2 controller found. Probing ports directly.
[    1.455864] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.455871] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.455937] mice: PS/2 mouse device common for all mice
[    1.455998] rtc_cmos 00:02: RTC can wake from S4
[    1.456018] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.456039] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.456104] device-mapper: uevent: version 1.0.3
[    1.456176] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.456253] device-mapper: multipath: version 1.1.0 loaded
[    1.456255] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.456414] cpuidle: using governor ladder
[    1.456415] cpuidle: using governor menu
[    1.456613] TCP cubic registered
[    1.456690] NET: Registered protocol family 10
[    1.456937] lo: Disabled Privacy Extensions
[    1.457095] NET: Registered protocol family 17
[    1.457136] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor processors (4 cpu cores) (version 2.20.00)
[    1.457162] powernow-k8:    0 : pstate 0 (3400 MHz)
[    1.457164] powernow-k8:    1 : pstate 1 (2700 MHz)
[    1.457165] powernow-k8:    2 : pstate 2 (2200 MHz)
[    1.457166] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.457400] PM: Resume from disk failed.
[    1.457407] registered taskstats version 1
[    1.457730]   Magic number: 15:485:293
[    1.457738] tty tty26: hash matches
[    1.457787] rtc_cmos 00:02: setting system clock to 2011-06-10 19:17:03 UTC (1307733423)
[    1.457789] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.457790] EDD information not available.
[    1.457818] Freeing unused kernel memory: 888k freed
[    1.457971] Write protecting the kernel read-only data: 7688k
[    1.467173] udev: starting version 151
[    1.486175] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.486192] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.486233] r8169 0000:04:00.0: setting latency timer to 64
[    1.486265]   alloc irq_desc for 28 on node 0
[    1.486266]   alloc kstat_irqs on node 0
[    1.486276] r8169 0000:04:00.0: irq 28 for MSI/MSI-X
[    1.486622] eth0: RTL8168c/8111c at 0xffffc90000c72000, 90:e6:ba:88:1a:c7, XID 1c4000c0 IRQ 28
[    1.499238] ahci 0000:00:11.0: version 3.0
[    1.499248]   alloc irq_desc for 22 on node 0
[    1.499249]   alloc kstat_irqs on node 0
[    1.499254] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.499295]   alloc irq_desc for 29 on node 0
[    1.499296]   alloc kstat_irqs on node 0
[    1.499304] ahci 0000:00:11.0: irq 29 for MSI/MSI-X
[    1.499376] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.499379] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc sxs 
[    1.500441] ohci1394 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.500447] ohci1394 0000:02:00.0: setting latency timer to 64
[    1.502193] scsi0 : ahci
[    1.502807] scsi1 : ahci
[    1.502854] scsi2 : ahci
[    1.502897] scsi3 : ahci
[    1.502925] ata1: SATA max UDMA/133 abar m1024@0xfbafe400 port 0xfbafe500 irq 29
[    1.502928] ata2: SATA max UDMA/133 abar m1024@0xfbafe400 port 0xfbafe580 irq 29
[    1.502931] ata3: SATA max UDMA/133 abar m1024@0xfbafe400 port 0xfbafe600 irq 29
[    1.502933] ata4: SATA max UDMA/133 abar m1024@0xfbafe400 port 0xfbafe680 irq 29
[    1.503098] scsi4 : pata_atiixp
[    1.503135] scsi5 : pata_atiixp
[    1.504145] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.504147] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.562068] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fbbff800-fbbfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.640020] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    1.821149] usb 4-2: configuration #1 chosen from 1 choice
[    1.853783] ata4: SATA link down (SStatus 0 SControl 300)
[    1.853810] ata2: SATA link down (SStatus 0 SControl 300)
[    2.030044] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.030065] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.030818] ata1.00: ATA-8: WDC WD1001FALS-00E8B0, 05.00K05, max UDMA/133
[    2.030820] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.031683] ata1.00: configured for UDMA/133
[    2.033055] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN01, max UDMA/100
[    2.036890] ata3.00: configured for UDMA/100
[    2.050119] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 05.0 PQ: 0 ANSI: 5
[    2.050215] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.050248] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.050283] sd 0:0:0:0: [sda] Write Protect is off
[    2.050284] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.050295] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.050370]  sda:
[    2.057131] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN01 PQ: 0 ANSI: 5
[    2.059700]  sda1 sda2 < sda5 sda6 sda7 sda8sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.078135] Uniform CD-ROM driver Revision: 3.20
[    2.078199] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.078235] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.085085]  sda9 > sda4
[    2.085311] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.150019] usb 4-3: new low speed USB device using ohci_hcd and address 3
[    2.243333] usbcore: registered new interface driver hiddev
[    2.247232] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input3
[    2.247283] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:12.1-2/input0
[    2.247297] usbcore: registered new interface driver usbhid
[    2.247299] usbhid: v2.6:USB HID core driver
[    2.371171] usb 4-3: configuration #1 chosen from 1 choice
[    2.378245] input: USB USB Keykoard as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4
[    2.378287] generic-usb 0003:1C4F:0002.0002: input,hidraw1: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:12.1-3/input0
[    2.700836] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.883868] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000b85653]
[   10.431556] udev: starting version 151
[   10.463848] Adding 4883720k swap on /dev/sda6.  Priority:-1 extents:1 across:4883720k 
[   10.481870] EDAC MC: Ver: 2.1.0 Apr 20 2011
[   10.482785] lp: driver loaded but no devices found
[   10.488150] vga16fb: initializing
[   10.488153] vga16fb: mapped to 0xffff8800000a0000
[   10.488251] fb0: VGA16 VGA frame buffer device
[   10.492685] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   10.492688] Disabling lock debugging due to kernel taint
[   10.500310] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   10.500313] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.512996] type=1505 audit(1307744232.553:2):  operation="profile_load" pid=645 name="/sbin/dhclient3"
[   10.513169] type=1505 audit(1307744232.553:3):  operation="profile_load" pid=645 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.513267] type=1505 audit(1307744232.553:4):  operation="profile_load" pid=645 name="/usr/lib/connman/scripts/dhclient-script"
[   10.513958] type=1505 audit(1307744232.553:5):  operation="profile_replace" pid=705 name="/sbin/dhclient3"
[   10.514133] type=1505 audit(1307744232.553:6):  operation="profile_replace" pid=705 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.514232] type=1505 audit(1307744232.553:7):  operation="profile_replace" pid=705 name="/usr/lib/connman/scripts/dhclient-script"
[   10.514595] type=1505 audit(1307744232.553:8):  operation="profile_load" pid=724 name="/usr/sbin/ntpd"
[   10.515546] type=1505 audit(1307744232.553:9):  operation="profile_replace" pid=725 name="/usr/sbin/ntpd"
[   10.546103] [fglrx] Maximum main memory to use for locked dma buffers: 7644 MBytes.
[   10.546165] [fglrx]   vendor: 1002 device: 6898 count: 1
[   10.546468] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   10.546478] pci 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.546482] pci 0000:05:00.0: setting latency timer to 64
[   10.546746] [fglrx] Kernel PAT support is enabled
[   10.546759] [fglrx] module loaded - fglrx 8.85.6 [Apr 19 2011] with 1 minors
[   10.551883] it87: Found IT8720F chip at 0x290, revision 2
[   10.551894] it87: in3 is VCC (+5V)
[   10.551895] it87: in7 is VCCH (+5V Stand-By)
[   10.551914] ACPI: resource it87 [0x295-0x296] conflicts with ACPI region SIOE [0x000290-0x0002af]
[   10.551916] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.553644] EDAC amd64_edac:  Ver: 3.2.0 Apr 20 2011
[   10.554933] Linux media interface: v0.10
[   10.555219] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   10.555226] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   10.555227]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   10.555228]  (Note that use of the override may cause unknown side effects.)
[   10.555238] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   10.672232] Linux video capture interface: v2.00
[   10.796981] Console: switching to colour frame buffer device 80x30
[   10.848986] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.851095] cx23885 driver version 0.0.2 loaded
[   10.851166] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.851218] CORE cx23885[0]: subsystem: 14f1:8502, board: Mygica X8506 DMB-TH [card=22,insmod option]
[   11.209084] cx25840 2-0044: cx23885 A/V decoder found @ 0x88 (cx23885[0])
[   11.219018] cx25840 2-0044: firmware: requesting v4l-cx23885-avcore-01.fw
[   11.327360] IR NEC protocol handler initialized
[   11.353561] IR RC5(x) protocol handler initialized
[   11.375856] IR RC6 protocol handler initialized
[   11.405193] IR JVC protocol handler initialized
[   11.412458] IR Sony protocol handler initialized
[   11.425308] lirc_dev: IR Remote Control driver registered, major 248 
[   11.432982] IR LIRC bridge handler initialized
[   11.534159] EXT4-fs (sda8): mounted filesystem with ordered data mode
[   11.593867] hda_codec: AD1989B: BIOS auto-probing.
[   11.593918] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
[   11.601173] HDA Intel 0000:05:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   11.601209] HDA Intel 0000:05:00.1: setting latency timer to 64
[   11.936927] cx25840 2-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   11.983049] type=1505 audit(1307744234.024:10):  operation="profile_load" pid=1033 name="/usr/share/gdm/guest-session/Xsession"
[   11.983225] type=1505 audit(1307744234.024:11):  operation="profile_replace" pid=1034 name="/sbin/dhclient3"
[   11.990499] tuner 1-0061: Tuner -1 found with type(s) Radio TV.
[   12.010125] xc5000 1-0061: creating new instance
[   12.010822] xc5000: Successfully identified at address 0x61
[   12.010823] xc5000: Firmware has not been loaded previously
[   12.010876] cx23885[0]/0: registered device video0 [v4l2]
[   12.016308] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   12.016311] cx23885 0000:03:00.0: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[   12.022721] r8169: eth0: link up
[   12.022725] r8169: eth0: link up
[   12.059112] xc5000: firmware read 12401 bytes.
[   12.059114] xc5000: firmware uploading...
[   12.384734] /build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[   12.384745] generic-usb 0003:1C4F:0002.0003: timeout initializing reports
[   12.384815] input: USB USB Keykoard as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input6
[   12.384880] generic-usb 0003:1C4F:0002.0003: input,hidraw2: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:12.1-3/input1
[   12.384912] usb 4-2: USB disconnect, address 2
[   13.450026] xc5000: firmware upload complete...
[   13.651379] RPC: Registered udp transport module.
[   13.651381] RPC: Registered tcp transport module.
[   13.651382] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   13.663708] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   13.695454] svc: failed to register lockdv1 RPC service (errno 97).
[   13.696011] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   13.702382] NFSD: starting 90-second grace period
[   13.781273] usb 4-2: new low speed USB device using ohci_hcd and address 4
[   13.994913] usb 4-2: configuration #1 chosen from 1 choice
[   14.004971] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input7
[   14.005034] generic-usb 0003:0458:003A.0004: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:12.1-2/input0
[   14.062172] ppdev: user-space parallel port driver
[   14.154065] cx23885_dvb_register() allocating 1 frontend(s)
[   14.154069] cx23885[0]: cx23885 based dvb card
[   14.158663] xc5000 1-0061: attaching existing instance
[   14.159389] xc5000: Successfully identified at address 0x61
[   14.159391] xc5000: Firmware has been loaded previously
[   14.159394] DVB: registering new adapter (cx23885[0])
[   14.159396] DVB: registering adapter 0 frontend 0 (Legend Silicon LGS8913/LGS8GXX DMB-TH)...
[   14.159621] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   14.159629] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 19, latency: 0, mmio: 0xfbc00000
[   14.159635] cx23885 0000:03:00.0: setting latency timer to 64
[   14.159706]   alloc irq_desc for 30 on node 0
[   14.159708]   alloc kstat_irqs on node 0
[   14.159722] cx23885 0000:03:00.0: irq 30 for MSI/MSI-X
[   14.583304]   alloc irq_desc for 31 on node 0
[   14.583307]   alloc kstat_irqs on node 0
[   14.583315] fglrx_pci 0000:05:00.0: irq 31 for MSI/MSI-X
[   14.583763] [fglrx] Firegl kernel thread PID: 1736
[   14.583797] [fglrx] Firegl kernel thread PID: 1737
[   14.583830] [fglrx] Firegl kernel thread PID: 1738
[   14.584029] [fglrx] IRQ 31 Enabled
[   14.772654] [fglrx] Gart USWC size:1280 M.
[   14.772657] [fglrx] Gart cacheable size:508 M.
[   14.772660] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   14.772662] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
[   14.772663] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   14.788166] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input8
[   16.551134] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   18.077561] __ratelimit: 42 callbacks suppressed
[   18.077563] type=1503 audit(1307744240.115:26):  operation="mknod" pid=1201 parent=1 profile="/usr/sbin/named" requested_mask="c::" denied_mask="c::" fsuid=116 ouid=116 name="/var/log/bind9-resolv.log"
[   19.110611] type=1503 audit(1307744241.152:27):  operation="open" pid=1780 parent=1 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=117 ouid=0 name="/home/tmp/"
```

---

### Post by 53RG10 on 2011-08-07
Hola a todos
Tengo la misma placa y no la puedo hacer andar, ¿Alguien tiene idea cómo hacerlo?
Muchas gracias

Sergio

---

### Post by alfredo_ on 2011-10-31
Hola

Me he inscripto en ubuntu para ver si me pueden dar ayuda con esta placa, he modificado algo del código y almenos la TV analógica se puede ver y escuchar (SAP incluido). Necesito que alguien pruebe el código. En linuxtv.org he posteado el código. Y si alguien sabe algo de programación en C me puede ayudar con la parte digital, me reconoce todo pero el flujo no sale bien, por lo que no obtengo imagen.

Saludos

---

### Post by alfredo_ on 2011-10-31
Para incentivar un poco este es parte de dmesg

[   10.986023] cx23885 driver version 0.0.3 loaded
[   10.986105] cx23885 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.986292] CORE cx23885[0]: subsystem: 14f1:8502, board: Mygica X8507 [card=33,autodetected]
[   11.885536] cx25840 6-0044: cx23885 A/V decoder found @ 0x88 (cx23885[0])
[   12.635236] cx25840 6-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   12.644543] tuner 5-0061: Tuner -1 found with type(s) Radio TV.
[   12.686635] xc5000 5-0061: creating new instance
[   12.687332] xc5000: Successfully identified at address 0x61
[   12.687334] xc5000: Firmware has not been loaded previously
[   12.687408] cx23885[0]: registered device video1 [v4l2]
[   12.687440] cx23885[0]: registered device vbi1
[   12.687557] cx23885[0]: registered ALSA audio device
[   12.692984] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   12.712017] xc5000: firmware read 12401 bytes.
[   12.712019] xc5000: firmware uploading...
[   14.084010] xc5000: firmware upload complete...
[   14.708424] cx23885_dvb_register() allocating 1 frontend(s)
[   14.708429] cx23885[0]: cx23885 based dvb card
[   14.749897] mb86a20s: mb86a20s_attach: 
[   14.750355] Detected a Fujitsu mb86a20s frontend
[   14.750364] xc5000 5-0061: attaching existing instance
[   14.751094] xc5000: Successfully identified at address 0x61
[   14.751096] xc5000: Firmware has been loaded previously
[   14.751100] DVB: registering new adapter (cx23885[0])
[   14.751103] DVB: registering adapter 0 frontend 0 (Fujitsu mb86A20s)...
[   14.751439] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   14.751446] cx23885[0]/0: found at 0000:02:00.0, rev: 2, irq: 19, latency: 0, mmio: 0xfd400000
[   14.751454] cx23885 0000:02:00.0: setting latency timer to 64
[   14.893121] Adding 4192928k swap on /dev/sdb5.  Priority:-1 extents:1 across:4192928k

---

### Post by 53RG10 on 2011-11-09
> **alfredo_ said:**
> Para incentivar un poco este es parte de dmesg

[   10.986023] cx23885 driver version 0.0.3 loaded
[   10.986105] cx23885 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.986292] CORE cx23885[0]: subsystem: 14f1:8502, board: Mygica X8507 [card=33,autodetected]
[   11.885536] cx25840 6-0044: cx23885 A/V decoder found @ 0x88 (cx23885[0])
[   12.635236] cx25840 6-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   12.644543] tuner 5-0061: Tuner -1 found with type(s) Radio TV.
[   12.686635] xc5000 5-0061: creating new instance
[   12.687332] xc5000: Successfully identified at address 0x61
[   12.687334] xc5000: Firmware has not been loaded previously
[   12.687408] cx23885[0]: registered device video1 [v4l2]
[   12.687440] cx23885[0]: registered device vbi1
[   12.687557] cx23885[0]: registered ALSA audio device
[   12.692984] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   12.712017] xc5000: firmware read 12401 bytes.
[   12.712019] xc5000: firmware uploading...
[   14.084010] xc5000: firmware upload complete...
[   14.708424] cx23885_dvb_register() allocating 1 frontend(s)
[   14.708429] cx23885[0]: cx23885 based dvb card
[   14.749897] mb86a20s: mb86a20s_attach: 
[   14.750355] Detected a Fujitsu mb86a20s frontend
[   14.750364] xc5000 5-0061: attaching existing instance
[   14.751094] xc5000: Successfully identified at address 0x61
[   14.751096] xc5000: Firmware has been loaded previously
[   14.751100] DVB: registering new adapter (cx23885[0])
[   14.751103] DVB: registering adapter 0 frontend 0 (Fujitsu mb86A20s)...
[   14.751439] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   14.751446] cx23885[0]/0: found at 0000:02:00.0, rev: 2, irq: 19, latency: 0, mmio: 0xfd400000
[   14.751454] cx23885 0000:02:00.0: setting latency timer to 64
[   14.893121] Adding 4192928k swap on /dev/sdb5.  Priority:-1 extents:1 across:4192928k

Hola
¿Me podrías decir cómo hiciste para que te reconociera el firmware xc5000? Porque a mí lo único que me apareció siempre fue la placa en sí (cx23885) pero en tuner no. Nunca pude hacer que me la reconozca. Y probé con varios reproductores de video y varios consejos para instalarlo.
Saludos y gracias

---

### Post by alfredo_ on 2011-11-10
Hola  
 

 Para que te reconozca el sintonizador es necesario el controlador, sin este último solo interpreta que hay una placa y nada más, no hace nada.
 

 Si deseas que te funcione es necesario un controlador. En: 

[http://www.spinics.net/lists/linux-media/msg39915.html](http://www.spinics.net/lists/linux-media/msg39915.html)

tienes  el parche que hay que aplicar a kernel para que te funcione la parte analógica.
 La forma más fácil que encontré de hacerlo es bajarte el último kernel (>3.1) y compilarlo.
 Luego le aplicas el parche a los archivos:

/usr/src/linux/drivers/media/video/cx23885/cx23885-cards.c
/usr/src/linux/drivers/media/video/cx23885/cx23885.h 

/usr/src/linux/drivers/media/video/cx23885/cx23885-video.c 

y compilas el módulo con el siguiente comando: 
make SUBDIRS=drivers/media/video/cx23885 modules 
esto te generara un nuevo cx23886.ko (el driver) que deberás copiarlo a la dirección donde están los controladores de tu distribución. En mi caso estos están en: 
/lib/modules/3.1.0-3-desktop/kernel/drivers/media/video/cx23885/cx23885.ko Luego cargar el módulo (modprobe cx23885) o reiniciar la máquina para que lo cargue. Es necesario que el kernel tenga soporte para cx23885-alsa, sino te vas a tener que bajar los parches necesarios para el soporte de alsa que están en:

[http://git.linuxtv.org/liplianin/media_tree.git/shortlog/refs/heads/cx23885-alsa-clean-2](http://git.linuxtv.org/liplianin/media_tree.git/shortlog/refs/heads/cx23885-alsa-clean-2)

La explicación es algo corta y estoy suponiendo que tienes un poco de idea de lo que estoy escribiendo.  Si no quieres bajar el último kernel tendrás que emparchar además el controlador cx25840. Es posible que tengas que hacer alguna modificación a mano del kernel, en mi caso altera.h estaba en una dirección diferente por lo que al compilar me daba un error. Para poder ver la TV yo utilizo TVTime, para que se escuche tienes que lanzar desde una consola el siguiente comando:  
arecord -D hw:3,0 -r 48000 -c 2 -f S16_LE | aplay -

hw:3,0 es el dispositivo de sonido que me crea la placa sintonizadora, es posible que en tu caso sea hw:2.0 o utilizar mplayer de la siguiente manera, por ejemplo:

mplayer tv://$channel -tv driver=v4l2:device=/dev/video1:width=720:height=568:chanlist=us-bcast:alsa:adevice=hw.3,0:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:norm=PAL-Nc 
Donde /dev/video1 es la placa sintonizadora en tu caso puede ser /dev/video0 Si tienes buena señal de televisión verás que se ve mucho mejor que bajo Windows Espero que puedas hacerla funcionar, cualquier cosa escribí que voy ayudarte en la medida de mis posibilidades. Las cosas que no sepas como hacerla por favor busca en internet como se hacen y luego si no te salen con gusto te las explico. En cuanto a la parte digital estoy estudiando para ver si puedo hacer algo, me reconoce todo, pero no logro que TS salga bien, por lo que no tengo imagen. 
Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-10
Primero gracias.
Segundo, tu suposición es incorrecta :), empecé hace unos meses con Linux y no soy muy entendido. O sea, puedo manejarme por el Terminal y esas cosas, pero si tengo que editar archivos o compilar ya me pierdo.
Intenté actualizar al kernel 3.1 pero no me anda la placa ATI de video incorporada y me queda la pantalla negra.
Si hay posibilidades de que lo expliques mejor te lo voy a agradecer, y sino también, se qué lleva tiempo y no todos lo tienen, y ganas también :).
Saludos

---

### Post by guillermolisi on 2011-11-10
> **53RG10 said:**
> Primero gracias.
Segundo, tu suposición es incorrecta :), empecé hace unos meses con Linux y no soy muy entendido. O sea, puedo manejarme por el Terminal y esas cosas, pero si tengo que editar archivos o compilar ya me pierdo.
Intenté actualizar al kernel 3.1 pero no me anda la placa ATI de video incorporada y me queda la pantalla negra.
Si hay posibilidades de que lo expliques mejor te lo voy a agradecer, y sino también, se qué lleva tiempo y no todos lo tienen, y ganas también :).
Saludos

En la seccion Software de este Foro hay un sticky thread, ya de cierta antigüedad, que explica [como compilar un kernel]("http://ubuntuforums.org/showthread.php?t=1195325").

Creo que por lo menos te servira como lectura introductoria.

---

### Post by alfredo_ on 2011-11-10
Hola

Si no podes hacer funcionar con el nuevo kernel, regresa al kernel anterior e instala las fuentes de ese kernel.
Compilalo, _pero_no_instales_nada_ solo sirve para que las dependencias se cumplan.
Luego es seguro que te vas a tener que bajar los archivos de los direcorios cx23885 y cx25840 que se encuentran en la dirección: [http://git.linuxtv.org/liplianin/med...5-alsa-clean-2]("http://git.linuxtv.org/liplianin/media_tree.git/shortlog/refs/heads/cx23885-alsa-clean-2") (si esta no funciona, pulsa en la del mensaje anterior que puse)
Bueno cuando llegues aquí te sigo guiando. Si podes hacer funcionar el kernel 3.1 mejor, menos cosas tenemos que modificar.
Voy a tratar de una vez al día poder ingresar a internet, para poder leer tu respuestas y seguir con el instructivo.
Como herramienta de ayuda para editar y navegar por archivos, instala midnight commander (puede que lo haya escrito mal).

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-10
Muchísimas gracias por tu tiempo.
Mañana (ya hoy en Argentina) me fijo eso. El kernel 3.1 lo hice funcionar, sin los driver privativos de ATI.
Tampoco hace falta que revises a cada rato a ver que hice :D
Saludos

---

### Post by guillermolisi on 2011-11-11
> **alfredo_ said:**
> Hola

Si no podes hacer funcionar con el nuevo kernel, regresa al kernel anterior e instala las fuentes de ese kernel.
Compilalo, _pero_no_instales_nada_ solo sirve para que las dependencias se cumplan.
Luego es seguro que te vas a tener que bajar los archivos de los direcorios cx23885 y cx25840 que se encuentran en la dirección: [http://git.linuxtv.org/liplianin/med...5-alsa-clean-2]("http://git.linuxtv.org/liplianin/media_tree.git/shortlog/refs/heads/cx23885-alsa-clean-2") (si esta no funciona, pulsa en la del mensaje anterior que puse)
Bueno cuando llegues aquí te sigo guiando. Si podes hacer funcionar el kernel 3.1 mejor, menos cosas tenemos que modificar.
Voy a tratar de una vez al día poder ingresar a internet, para poder leer tu respuestas y seguir con el instructivo.
Como herramienta de ayuda para editar y navegar por archivos, instala midnight commander (puede que lo haya escrito mal).

Saludos,

Alfredo
Cuando cambie la version del kernel, tendra que compilarlo nuevamente con los modulos de la placa ?

Si es asi, habria que advertirlo. Si no es asi, habria que mencionar que se actualizaran via DKMS o algun otro metodo que evite la regeneracion manual.

---

### Post by alfredo_ on 2011-11-11
Hola

Gracias Guillermo por tus acotaciones, si podes mantenerte en el tema para ayudar en el proceso de compilación estaremos agradecido, dado que no lo hice nunca con Ubuntu y puede que haya algo distinto a la forma que yo estoy acostumbrado.
En respuesta a que si tiene que compilar el nuevo kernel, es sí. Solo compilar y crear los módulos. No hay que instalar nada. 

_OJO_ el kernel fuente y el que se está ejecutando en la máquina tiene que ser el mismo.

Luego de compilar o antes es conveniente hacer un respaldo del contenido de todos los archivos que hay en la carpeta cx23885 y cx25840 de los módulos del kernel en algún lugar, por ejemplo en tu directorio personal /home/sergio/x8507/respaldo/cx23885 y  /home/sergio/x8507/respaldo/cx25840/ si sergio es el nombre que estas usando.

Luego en otra carpeta bajar el contenido del enlace que indique y guardarlos en otro lugar. Por ejemplo /home/sergio/x8507/soporte_alsa/cx23885 con todo su contenido y /home/sergio/x8507/soporte_alsa/cx25840

Bueno sigo cuando ya tengas hecho esto.

Saludos,

Alfredo.

---

### Post by 53RG10 on 2011-11-11
Bueno, cada vez se me complica más :confused:. Y empiezo pidiendo disculpas porque a lo mejor los termine cansando...
Ahora, la primera pregunta es la siguiente: Como bien dijo guillermolisi, tengo el kernel 3.1 y varios anteriores 2.algo... Y varias cosas que hago en la terminal me hace los cambios en el kernel principal cuando instale el Sistema operativo. "_OJO_ el kernel fuente y el que se está ejecutando en la máquina tiene que ser el mismo". No sé como hacer para que todo lo haga en el kernel nuevo (3.1 en mi caso). ¿Tengo que eliminar (o desinstalar) los kernel anteriores? Si es así ¿Cómo? ¿Tengo que seguir los pasos que me dierno antes de cómo compilar un núcleo?
Pregunto esto porque no quiero empezar a probar. No entiendo cómo tengo que hacer las copias del contenido  de todos los archivos que hay en la carpeta cx23885 y cx25840 de los  módulos del kernel. ¿Dónde están?
No sé que más hacer, quiero empezar y hacer lo más que se pueda, pero sin copiar eso no quiero hacer mucho.
Y como dije antes, si se les hace muy pesado el asunto porque yo no entiendo demasiado me lo dicen, yo no me voy a enojar :).
Saludos

---

### Post by alfredo_ on 2011-11-11
Hola

Respondo entre lineas


*| Bueno, cada vez se me complica más :confused:. Y empiezo pidiendo disculpas porque a lo mejor los termine cansando...*


Todos hemos empezado con algún problema y hemos tenido que ser asistido por alguna otra persona o más de una. Esperemos que no nos canses y que lleguemos juntos a buen fin. Somos consientes que empiezas con algo difícil y que te va a costar un poco, pero después tendrá su fruto.


*| Ahora, la primera pregunta es la siguiente: Como bien dijo  guillermolisi, tengo el kernel 3.1 y varios anteriores 2.algo... Y  varias cosas que hago en la terminal me hace los cambios en el kernel  principal cuando instale el Sistema operativo. "_OJO_ el kernel fuente y  el que se está ejecutando en la máquina tiene que ser el mismo". No sé  como hacer para que todo lo haga en el kernel nuevo (3.1 en mi caso).  ¿Tengo que eliminar (o desinstalar) los kernel anteriores? Si es así  ¿Cómo? ¿Tengo que seguir los pasos que me dierno antes de cómo compilar  un núcleo?*


Espero que esto te lo conteste Guillermo. Pero en mi máquina si paso a una consola (Alt+Ctrl+F1 a F6) en la última línea me suele decir que kernel se esta usando o cuando aparece el menú de arranque de la PC (GRUB) me dice por ejemplo Ubuntu koala 2.6.30 y Ubuntu Koala 3.1.0. Si arranca con el que dice 3.1.0 quiere decir (puede fallar) que estas usando el kernel 3.1.0
En cuanto a las fuentes en /usr/src/linux aquí tienes las fuentes el kernel que estas compilando si tienes ademas de esto otros, por ejemplo /usr/src/linux-2.6.28 y/o /usr/src/linux-2.6.31 quiere decir que tienes mas de un kernel para compilar. El que tendrías que usar en un principio es el que esta en /usr/src/linx, pero mejor que te lo aclare Guillermo, por no estoy muy al tanto en compilación con Ubuntu y el que tengo instalado no lo quiero modificar porque lo uso para mover una máquina.

[I]
| Pregunto esto porque no quiero empezar a probar. No entiendo cómo tengo  que hacer las copias del contenido  de todos los archivos que hay en la  carpeta cx23885 y cx25840 de los  módulos del kernel. ¿Dónde están?[/I]


Dentro del directorio /usr/src/linux/drivers/media/video hay dos carpetas, cx23885 y cx25840, dentro de la cual están las fuentes del controlador. Estas carpetas tenes que copiarlas integramente a otro lugar. Podes hacerlo de la misma manera que lo haces en windows o en una consola utilizando midnight commander el cual se llama escribiendo mc en la consola.
El lugar donde podes hacer la copia puede ser tu directorio de trabajo, por ejemplo /home/sergio.
Aquí podes crear una nueva carpeta que se llame por ejemplo X8505 y dentro de ella otra que diga respaldo y dentro de esta última copias las carpetas cx23885 y cx25840 con todo su contenido.

 
*|No sé que más hacer, quiero empezar y hacer lo más que se pueda, pero sin copiar eso no quiero hacer mucho.*

Siempre es mejor hacer un respaldo y luego largarse a probar.

*| Y como dije antes, si se les hace muy pesado el asunto porque yo no entiendo demasiado me lo dicen, yo no me voy a enojar :smile:.*

Esperemos que todos tengamos buena paciencia y suerte para que lleguemos a buen fin.
Si tenes algún buen amigo que sepa algo de linux cerca de tu casa es un buen momento para pedir ayuda y sino con gusto te la daremos desde aquí.

Saludos,

Alfredo

---

### Post by guillermolisi on 2011-11-12
> **alfredo_ said:**
> Hola

Respondo entre lineas

......

*| Ahora, la primera pregunta es la siguiente: Como bien dijo  guillermolisi, tengo el kernel 3.1 y varios anteriores 2.algo... Y  varias cosas que hago en la terminal me hace los cambios en el kernel  principal cuando instale el Sistema operativo. "_OJO_ el kernel fuente y  el que se está ejecutando en la máquina tiene que ser el mismo". No sé  como hacer para que todo lo haga en el kernel nuevo (3.1 en mi caso).  ¿Tengo que eliminar (o desinstalar) los kernel anteriores? Si es así  ¿Cómo? ¿Tengo que seguir los pasos que me dierno antes de cómo compilar  un núcleo?*


Espero que esto te lo conteste Guillermo. Pero en mi máquina si paso a una consola (Alt+Ctrl+F1 a F6) en la última línea me suele decir que kernel se esta usando o cuando aparece el menú de arranque de la PC (GRUB) me dice por ejemplo Ubuntu koala 2.6.30 y Ubuntu Koala 3.1.0. Si arranca con el que dice 3.1.0 quiere decir (puede fallar) que estas usando el kernel 3.1.0
En cuanto a las fuentes en /usr/src/linux aquí tienes las fuentes el kernel que estas compilando si tienes ademas de esto otros, por ejemplo /usr/src/linux-2.6.28 y/o /usr/src/linux-2.6.31 quiere decir que tienes mas de un kernel para compilar. El que tendrías que usar en un principio es el que esta en /usr/src/linx, pero mejor que te lo aclare Guillermo, por no estoy muy al tanto en compilación con Ubuntu y el que tengo instalado no lo quiero modificar porque lo uso para mover una máquina.

.....

Saludos,

Alfredo

Si tenes mas de un kernel instalado y recibis una actualizacion, con repetir los pasos que recomienda Alfredo es suficiente. NO es necesario desinstalar/remover los kernels anteriores. Es mas, siempre es bueno tener el ultimo usado, que sabes funciona bien en tu maquina, para utilizarlo en caso de emergencia por algun problema que se presente con el nuevo.

No es obligatorio repetir la compilacion aconsejada sobre los kernels que tengas anteriores al ultimo a usar, ya sea porque no te interesan usarlos mas o porque ya los generaste, con el proceso que sugiere Alfredo, con los modulos de la placa.

En /usr/src/linux podes encontrar cosas como las del siguiente ejemplo, tomado de una de las maquinas que utilizo:

> guille@guillermo:~$ ls -al /usr/src
total 32
drwxr-xr-x  8 root root 4096 2011-10-24 22:00 .
drwxr-xr-x 12 root root 4096 2011-11-09 00:56 ..
drwxr-xr-x 24 root root 4096 2011-10-22 00:47 linux-headers-3.0.0-12
drwxr-xr-x  7 root root 4096 2011-10-22 00:47 linux-headers-3.0.0-12-generic
drwxr-xr-x  3 root root 4096 2011-10-24 22:00 nvidia-current-280.13
drwxr-xr-x  3 root root 4096 2011-10-24 22:00 nvidia-current-updates-280.13
drwxr-xr-x 12 root root 4096 2011-10-23 00:01 virtualbox-4.1.2
drwxr-xr-x  7 root root 4096 2011-10-23 00:01 virtualbox-guest-4.1.2

En el caso mostrado Ubuntu utiliza dos metodos, basados en [DKMS]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support"), que se instalan para evitar todo el proceso de compilacion manual para los drivers nVidia y VirtualBox cada vez que se recibe una actualizacion de version del kernel.

Lo mas importante de esto es que la version de linux-headers DEBE coincidir con la version del kernel a utilizar (a compilar).

---

### Post by 53RG10 on 2011-11-12
Bueno, empezamos.
Ya hice las copias por las dudas, e hice esto por si hay algo que esté mal que tenga que saber (los que entienden son ustedes):

ls -al /usr/src
```
total 60
drwxrwsr-x 15 root src  4096 2011-11-12 23:54 .
drwxr-xr-x 12 root root 4096 2011-11-10 01:08 ..
drwxr-sr-x  2 root src  4096 2011-11-10 01:08 ati
drwxr-sr-x  3 root src  4096 2011-11-10 01:08 fglrx-8.892
drwxr-xr-x 24 root root 4096 2011-08-12 13:09 linux-headers-2.6.38-10
drwxr-xr-x  7 root root 4096 2011-08-12 13:09 linux-headers-2.6.38-10-generic
drwxr-xr-x 24 root root 4096 2011-10-10 12:41 linux-headers-2.6.38-11
drwxr-xr-x  7 root root 4096 2011-10-10 12:41 linux-headers-2.6.38-11-generic
drwxr-xr-x 24 root root 4096 2011-11-01 11:15 linux-headers-2.6.38-12
drwxr-xr-x  7 root root 4096 2011-11-01 11:15 linux-headers-2.6.38-12-generic
drwxr-xr-x 24 root root 4096 2011-04-25 20:08 linux-headers-2.6.38-8
drwxr-xr-x  7 root root 4096 2011-11-10 19:42 linux-headers-2.6.38-8-generic
drwxr-xr-x 23 root root 4096 2011-11-10 11:39 linux-headers-3.1.0-030100
drwxr-xr-x  7 root root 4096 2011-11-10 11:40 linux-headers-3.1.0-030100-generic
drwxr-xr-x  4 root root 4096 2011-11-12 23:54 linux-source-2.6.38
lrwxrwxrwx  1 root root   47 2011-11-12 23:54 linux-source-2.6.38.tar.bz2 -> linux-source-2.6.38/linux-source-2.6.38.tar.bz2
```# uname -r
3.1.0-030100-generic

Aclaro también que esto es lo que ya tengo:
# lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4290]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:07.0 Communication controller: Intel Corporation 536EP Data Fax Modem
05:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
06:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)

```# dmesg | grep 23885
```
[   12.288521] cx23885 driver version 0.0.3 loaded
[   12.288590] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.288594] cx23885[0]: Your board isn't known (yet) to the driver.
[   12.288595] cx23885[0]: Try to pick one of the existing card configs via
[   12.288596] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   12.288596] cx23885[0]: version might help as well.
[   12.288598] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   12.288599] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   12.288600] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   12.288602] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   12.288603] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   12.288604] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   12.288605] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   12.288606] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   12.288608] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[   12.288609] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[   12.288610] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[   12.288611] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[   12.288613] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[   12.288614] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[   12.288615] cx23885[0]:    card=13 -> Compro VideoMate E650F
[   12.288616] cx23885[0]:    card=14 -> TurboSight TBS 6920
[   12.288617] cx23885[0]:    card=15 -> TeVii S470
[   12.288619] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[   12.288620] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[   12.288621] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[   12.288622] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[   12.288623] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[   12.288625] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[   12.288626] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[   12.288627] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[   12.288628] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[   12.288629] cx23885[0]:    card=25 -> Compro VideoMate E800
[   12.288631] cx23885[0]:    card=26 -> Hauppauge WinTV-HVR1290
[   12.288632] cx23885[0]:    card=27 -> Mygica X8558 PRO DMB-TH
[   12.288633] cx23885[0]:    card=28 -> LEADTEK WinFast PxTV1200
[   12.288634] cx23885[0]:    card=29 -> GoTView X5 3D Hybrid
[   12.288636] cx23885[0]:    card=30 -> NetUP Dual DVB-T/C-CI RF
[   12.288637] cx23885[0]:    card=31 -> Leadtek Winfast PxDVR3200 H XC4000
[   12.288791] CORE cx23885[0]: subsystem: 14f1:8502, board: UNKNOWN/GENERIC [card=0,autodetected]
[   12.415572] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   12.415576] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 19, latency: 0, mmio: 0xfd400000
[   12.415583] cx23885 0000:03:00.0: setting latency timer to 64
```Y si pongo: dmesg | grep xc5000 No aparece nada, o sea, el sintonizador no lo reconoce. Después de mostrar una idea de cómo está mi máquina, empiezo con las dudas:
> Para que te reconozca el sintonizador es necesario el controlador, sin este último solo interpreta que hay una placa y nada más, no hace nada.
Si deseas que te funcione es necesario un controlador. En:
[http://www.spinics.net/lists/linux-media/msg39915.html](http://www.spinics.net/lists/linux-media/msg39915.html)
tienes el parche que hay que aplicar a kernel para que te funcione la parte analógica.
La forma más fácil que encontré de hacerlo es bajarte el último kernel (>3.1) y compilarlo.
Luego le aplicas el parche a los archivos:
/usr/src/linux/drivers/media/video/cx23885/cx23885-cards.c
/usr/src/linux/drivers/media/video/cx23885/cx23885.h
/usr/src/linux/drivers/media/video/cx23885/cx23885-video.c
y compilas el módulo con el siguiente comando:
make SUBDIRS=drivers/media/video/cx23885 modules
esto te generara un nuevo cx23886.ko (el driver) que deberás copiarlo a la dirección donde están los controladores de tu distribución. En mi caso estos están en:
/lib/modules/3.1.0-3-desktop/kernel/drivers/media/video/cx23885/cx23885.ko Luego cargar el módulo (modprobe cx23885) o reiniciar la máquina para que lo cargue. Es necesario que el kernel tenga soporte para cx23885-alsa, sino te vas a tener que bajar los parches necesarios para el soporte de alsa que están en:

[http://git.linuxtv.org/liplianin/med...5-alsa-clean-2](http://git.linuxtv.org/liplianin/med...5-alsa-clean-2)Entré a las páginas y traté de entenderlo, pero no llego a hacer nada, perdón.

> Como herramienta de ayuda para editar y navegar por archivos, instala midnight commander (puede que lo haya escrito mal).Ya lo instalé y estaba escrito bien

> Lo mas importante de esto es que la version de linux-headers DEBE coincidir con la version del kernel a utilizar (a compilar).
¿Cómo sé eso o cómo lo hago?

Bueno, espero haber sido claro.
Saludos y seguiré agradeciendo

---

### Post by alfredo_ on 2011-11-13
Hola

Tienes que releer los mensajes anteriores de nuevo para recordar y verás que ya esta la respuesta a algunas de tus dudas. Cuando inicias la PC en el grub te da a elegir con que kernel quieres arrancar.
El sintonizador XC5000 no aparecerá hasta que el controlador este funcionando.

Ahora abre una consola como root y ve a /usr/src/linux-header-3.1.0-030100-generic o /usr/src/linux-header-3.1.0-030100 el que más cosa (carpetas y archivos) tenga y el que coincida con el que elijas para arrancar cuando inicia grub al encender la pc) ese será el que usaremos para compilar.

Tienes que tipear en la consola lo siguiente (van a tardar mucho en hacer estas instrucciones, en especial las últimas)

make clean

make oldconfig

make

make modules

Si tu pc tiene más de un núcleo agrega al final lo siguiente:

make clean -j3

make oldconfig -j3

make -j3

make modules -j3

Esto si tienes 4 núcleos tu pc, si tiene uno no se pone nada, si tiene 2 se pone j1, si son 3 se pone j2 si son 6 se pone j5

Bueno ya tienes para entretenerte un rato y vuelve a releer todos los mensajes.

Si hay alguna diferencia en como compilar espero que Guillermo me lo corrija por lo que he expuesto en mensajes anteriores

Saludos,

Alfredo

---

### Post by guillermolisi on 2011-11-13
> **alfredo_ said:**
> Hola

.....
Si tu pc tiene más de un núcleo agrega al final lo siguiente:

make clean -j3

make oldconfig -j3

make -j3

make modules -j3

Esto si tienes 4 núcleos tu pc, si tiene uno no se pone nada, si tiene 2 se pone j1, si son 3 se pone j2 si son 6 se pone j5

.....

Saludos,

Alfredo
Para saber a ciencia cierta cuantos nucleos tiene tu procesador, en una consola/terminal ingresa ```
sudo lshw
``` que te dara una larga salida con informacion detallada de tu hardware tal como es reconocido por el Linux que estas usando.

De toda esa salida, la parte referida a CPU es la mas importante para saber cuantos nucleos estan activos. A continuacion un ejemplo de mi maquina:
> *-core
       description: Motherboard
       product: P5VD2-MX
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.XX
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS P5VD2-MX ACPI BIOS Revision 1017
          date: 04/30/2007
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     [COLOR="RoyalBlue"]*-cpu:0[/COLOR]
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          slot: Socket 775
          size: 2996MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 214MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR2 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     [COLOR="RoyalBlue"]*-cpu:1[/COLOR]
          physical id: 2
          bus info: cpu@1
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          size: 3GHz
          capabilities: ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
Fijate que se mencionan CPU:0 y CPU:1, esto seria equivalente a contar con dos nucleos => que deberia usar -j1 en mi caso.

53rg10, no te desanimes que venis muy bien, posta. Por lo pronto estas mostrando actitud, que es lo primero que se necesita para poder incorporar conocimientos.

---

### Post by 53RG10 on 2011-11-13
Hola
Me apareció sólo esto, así que imagino que sólo me lo toma como 1 nucleo:
```
*-cpu
          description: CPU
          product: AMD Phenom(tm) II X4 955 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X4 955 Processor
          slot: Socket M2
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
```
Gracias por el incentivo de seguir, yo no tengo problemas de seguir y seguir, pero tampoco quiero tenerlos un mes tratando de que me ande una placa :).

Yo ya leí los mensajes anteriores, y si no me equivoco el próximo caso es aplicar el parche para la placa, cosa que no entendí mucho. Mi máquina arranca con el kernel 3.1, eso está correcto, y tengo los otros kernel como me dijeron.
Si pueden guiarme en el próximo paso, agradecido yo.
Saludos

---

### Post by alfredo_ on 2011-11-13
> **53RG10 said:**
> Hola
Me apareció sólo esto, así que imagino que sólo me lo toma como 1 nucleo:
```
*-cpu
          description: CPU
          product: AMD Phenom(tm) II X4 955 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X4 955 Processor
          slot: Socket M2
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
```Gracias por el incentivo de seguir, yo no tengo problemas de seguir y seguir, pero tampoco quiero tenerlos un mes tratando de que me ande una placa :).

Yo ya leí los mensajes anteriores, y si no me equivoco el próximo caso es aplicar el parche para la placa, cosa que no entendí mucho. Mi máquina arranca con el kernel 3.1, eso está correcto, y tengo los otros kernel como me dijeron.
Si pueden guiarme en el próximo paso, agradecido yo.
Saludos

Bueno ya sabemos que tenes 4 nucleos, por lo tanto tenes que utilizar:

make clean -j3

make oldconfig -j3

make -j3

make modules -j3

Este -j3 que se agrega es solo para que utilice todos los núcleos al compilar, lo cual hará que tarde menos en hacer el trabajo.

Hecho esto y esperamos que no se produzca ningún error, viene el paso de modificar (emparchar) el kernel.

Antes de compilar es mejor haber hecho un respaldo del contenido de las carpetas cx23885 y cx25840, si no lo habías hechos y compilastes, hace igual el respaldo, solo vas a tener algo de "basura" en el respaldo, pero sirve igual.

Una vez que hayas hecho esto hay que bajarse los controladores, voy a ver que es más fácil si que los busques o que yo los adjunte, creo que esto último va ha ser lo mejor.

Saludos,

Alfredo

---

### Post by guillermolisi on 2011-11-13
> **53RG10 said:**
> Hola
Me apareció sólo esto, así que imagino que sólo me lo toma como 1 nucleo:
```
*-cpu
          description: CPU
          product: AMD Phenom(tm) II X4 955 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X4 955 Processor
          slot: Socket M2
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
```
Gracias por el incentivo de seguir, yo no tengo problemas de seguir y seguir, pero tampoco quiero tenerlos un mes tratando de que me ande una placa :).

Yo ya leí los mensajes anteriores, y si no me equivoco el próximo caso es aplicar el parche para la placa, cosa que no entendí mucho. Mi máquina arranca con el kernel 3.1, eso está correcto, y tengo los otros kernel como me dijeron.
Si pueden guiarme en el próximo paso, agradecido yo.
Saludos
El [AMD Phenom II X4]("http://www.anandtech.com/show/2754") es un procesador de 4 nucleos.

Mas abajo de la salida del lshw que mostraste debe haber mas referencias en detalle a cada nucleo.

---

### Post by alfredo_ on 2011-11-13
Bueno veo que lo más fácil es que los adjunte, así que dentro de un rato si no me surge ningún problema te mando los míos propios.

Saludos,

Alfredo

---

### Post by alfredo_ on 2011-11-13
Bueno adjuntos están los archivos con los parches ya instalado, por lo que creo se te va a hacer más fácil.

En primer lugar reemplaza en usr/src/linux/drivers/media/video/cx23885 los archivos: 
cx23885-cards.c
cx23885-dvb.c
cx23885-video.c
cx23885.h
Kconfig
Makefile



y copia a esta carpeta también el archivo cx23885-alsa.c

---

### Post by alfredo_ on 2011-11-13
Una vez que hayas copiado los archivos es necesario que abras una consola como root.
Luego tienes que posicionarte en el directorio /usr/src/linux (en tu caso y también corregílo en la carta anterior en vez de linux el nombre que corresponde a tu kernel 3.1)
Ahora ejecuta el siguiente comando:

make SUBDIRS=drivers/media/video/cx23885 modules -j3

si tenemos mucha suerte habrás hecho tu controlador, y ya tendrías soporte. Lo más común es que surja algún error que tendremos que ver y corregir. Esto puede pasar si las fuentes de tu kernel son distintas al mio.

Si tuvimos suerte, ha que copiar el controlador que lleva el nombre cx23885.ko de /usr/src/linux/drivers/media/video/cx23885/ a /lib/modules/tu_kernel/kernel/drivers/media/video/cx23885/
Si utilizas midnight commander como root esto es bastante fácil.

Hecho esto hay que cargarlo, la manera en que yo lo hago es modprobe cx23885 (Guillermo quizás te de otra manera de cargar un módulo)
Bueno si llegas hasta este punto nos toca luego pelear para que puedas ver y escuchar.

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-13
Bueno, para empezar, me tiró algunos errores y no sé si puedo seguir:
```

sergio-usuario linux-headers-3.1.0-030100-generic # make clean -j3
  CLEAN   .
ls: no se puede acceder a /usr/src/linux-headers-3.1.0-030100-generic/Documentation/DocBook/media/*.b64: No existe el fichero o el directorio
  CLEAN   .tmp_versions
sergio-usuario linux-headers-3.1.0-030100-generic # make oldconfig -j3
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --oldconfig Kconfig
#
# configuration written to .config
#
sergio-usuario linux-headers-3.1.0-030100-generic # make -j3
scripts/kconfig/conf --silentoldconfig Kconfig
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
  HOSTCC  scripts/genksyms/genksyms.o
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  HOSTCC  scripts/genksyms/lex.lex.o
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/genksyms/parse.tab.o
  HOSTCC  scripts/mod/modpost.o
  HOSTLD  scripts/genksyms/genksyms
make[1]: *** No hay ninguna regla para construir el objetivo «kernel/bounds.c», necesario para «kernel/bounds.s».  Alto.
make[1]: *** Se espera a que terminen otras tareas....
make: *** [prepare0] Error 2
make: *** Se espera a que terminen otras tareas....
  HOSTCC  scripts/selinux/genheaders/genheaders
scripts/selinux/genheaders/genheaders.c:13:22: fatal error: classmap.h: No existe el fichero o el directorio
compilation terminated.
make[3]: *** [scripts/selinux/genheaders/genheaders] Error 1
make[2]: *** [scripts/selinux/genheaders] Error 2
make[1]: *** [scripts/selinux] Error 2
make[1]: *** Se espera a que terminen otras tareas....
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
make: *** [scripts] Error 2
sergio-usuario linux-headers-3.1.0-030100-generic # make modules -j3
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/conmakehash
  HOSTCC  scripts/selinux/genheaders/genheaders
scripts/selinux/genheaders/genheaders.c:13:22: fatal error: classmap.h: No existe el fichero o el directorio
compilation terminated.
make[3]: *** [scripts/selinux/genheaders/genheaders] Error 1
make[2]: *** [scripts/selinux/genheaders] Error 2
make[1]: *** [scripts/selinux] Error 2
make[1]: *** Se espera a que terminen otras tareas....
make[1]: *** No hay ninguna regla para construir el objetivo «kernel/bounds.c», necesario para «kernel/bounds.s».  Alto.
make[1]: *** Se espera a que terminen otras tareas....
make: *** [prepare0] Error 2
make: *** Se espera a que terminen otras tareas....
make: *** [scripts] Error 2

```El resto lo entendí (o eso creo), así que sabiendo si puedo seguir o si tengo que solucionarlo, no tendría problemas de continuar (ya me descargué los archivos y ya sé donde copiarlos).
Saludos

---

### Post by guillermolisi on 2011-11-13
> **alfredo_ said:**
> .... 
Hecho esto hay que cargarlo, la manera en que yo lo hago es modprobe cx23885 (Guillermo quizás te de otra manera de cargar un módulo)
Bueno si llegas hasta este punto nos toca luego pelear para que puedas ver y escuchar.

Saludos,

Alfredo
Me parece que estan faltando algunas indicaciones sobre cuando usar "sudo" porque hay acciones que requieren privilegios de superusuario para ser llevadas a cabo exitosamente y 53rg10 esta usando su cuenta de usuario regular.

Luego, si con ```
modprobe cx23885
``` no hubo errores y la cosa funciona, lo proximo que habria que hacer para no tener que cargarlo cada vez que se inicia el sistema es agregarlo al archivo /etc/modules, al final de todo, como ultima linea.

---

### Post by 53RG10 on 2011-11-13
> **guillermolisi said:**
> Me parece que estan faltando algunas indicaciones sobre cuando usar "sudo" porque hay acciones que requieren privilegios de superusuario para ser llevadas a cabo exitosamente y 53rg10 esta usando su cuenta de usuario regular.

Luego, si con ```
modprobe cx23885
``` no hubo errores y la cosa funciona, lo proximo que habria que hacer para no tener que cargarlo cada vez que se inicia el sistema es agregarlo al archivo /etc/modules, al final de todo, como ultima linea.

No se si será esto, pero cuando hago ese tipo de configuraciones pongo "sudo su" al principio y escribo la contraseña una vez. Esos errores me salieron como superusuario.
Saludos

P.D. No entendí, ¿puedo seguir o no con lo que sigue?

---

### Post by alfredo_ on 2011-11-13
Hola Sergio

Creo que el error esta en que no estas en una consola como **usuario root**. Concuerdo con lo que indica Guillermo.

Si estas como un usuario común tenes que anteponer la sentencia **sudo** los comandos que te indique, por ejemplo:

sudo make -j3

te va a pedir la contraseña de root, la escribis y te va a compilar. Proba haciendolo así.

Arranca de nuevo desde el principio. si da algún error no vale la pena seguir, hay que solucionarlo primero.

debajo te muestro como se ve en consola un usuario común primero y el root segundo:

alfredo@dhcppc1:~> mc

dhcppc1:/usr/src/linux # mc


Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-13
> **alfredo_ said:**
> Hola Sergio

Creo que el error esta en que no estas en una consola como **usuario root**. Concuerdo con lo que indica Guillermo.

Si estas como un usuario común tenes que anteponer la sentencia **sudo** los comandos que te indique, por ejemplo:

sudo make -j3

te va a pedir la contraseña de root, la escribis y te va a compilar. Proba haciendolo así.

Arranca de nuevo desde el principio. si da algún error no vale la pena seguir, hay que solucionarlo primero.

debajo te muestro como se ve en consola un usuario común primero y el root segundo:

alfredo@dhcppc1:~> mc

dhcppc1:/usr/src/linux # mc


Saludos,

Alfredo

No, fijate que en el texto anterior puse como lo hice, además de que se ve que está el símbolo #. Igual por las dudas probé y sigue pasando lo mismo.
¿En qué carpeta tengo que estar posicionado? Porque a lo mejor es ese el problema. En el mensaje anterior está que yo me paro en la carpeta del kernel 3.1.
Probé sin el -j3 por las dudas y tampoco. :confused:
Espero que no empecemos con problemas. Igual los solucionamos y listo :).
Saludos

EDITO para agregar algo: Siempre hay 2 carpetas de kernel, en mi caso, linux-headers-3.1.0-030100 y linux-headers-3.1.0-030100-generic. ¿Cuál es la diferencia? Yo uso la segunda. ¿Está bien?

---

### Post by alfredo_ on 2011-11-13
Hola

La verdad es que no se cual es la que hay que usar. Encima es un problema de quien te da el kernel, todavía no es un problema por el cual estamos trabajando.
Yo siempre te voy a poner linux y no linux-headers-3.1.0-030100 o linux-headers-3.1.0-030100-generic.
No se cual usar, por las dudas proba también con el otro.
Saludos,

Alfredo

---

### Post by guillermolisi on 2011-11-13
Tenes que usar el directorio que finaliza con -generic porque ese es el nucleo que estas utilizando.

Para que vean cual es la relacion entre ambos directorios, les paso un ls. Notesen los links simbolicos del segundo al primero.

> guille@guillermo:~$ ls -al /usr/src/linux-headers-3.0.0-12
total 160
drwxr-xr-x 24 root root  4096 2011-10-22 00:47 .
drwxr-xr-x  8 root root  4096 2011-10-24 22:00 ..
drwxr-xr-x 26 root root  4096 2011-10-22 00:47 arch
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 block
drwxr-xr-x  3 root root  4096 2011-10-22 00:47 crypto
drwxr-xr-x 23 root root  4096 2011-10-22 00:47 Documentation
drwxr-xr-x 93 root root  4096 2011-10-22 00:47 drivers
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 firmware
drwxr-xr-x 72 root root  4096 2011-10-22 00:47 fs
drwxr-xr-x 21 root root  4096 2011-10-22 00:47 include
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 init
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 ipc
-rw-r--r--  1 root root  2464 2011-07-21 23:17 Kbuild
-rw-r--r--  1 root root   252 2011-07-21 23:17 Kconfig
drwxr-xr-x  9 root root  4096 2011-10-22 00:47 kernel
drwxr-xr-x  8 root root  4096 2011-10-22 00:47 lib
-rw-r--r--  1 root root 53948 2011-10-07 11:50 Makefile                                                                             
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 mm                                                                                   
drwxr-xr-x 53 root root  4096 2011-10-22 00:47 net                                                                                  
drwxr-xr-x 10 root root  4096 2011-10-22 00:47 samples                                                                              
drwxr-xr-x 13 root root  4096 2011-10-22 00:47 scripts                                                                              
drwxr-xr-x  9 root root  4096 2011-10-22 00:47 security                                                                             
drwxr-xr-x 22 root root  4096 2011-10-22 00:47 sound                                                                                
drwxr-xr-x  8 root root  4096 2011-10-22 00:47 tools                                                                                
drwxr-xr-x  9 root root  4096 2011-10-22 00:47 ubuntu                                                                               
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 usr                                                                                  
drwxr-xr-x  3 root root  4096 2011-10-22 00:47 virt
guille@guillermo:~$ ls -al /usr/src/linux-headers-3.0.0-12-generic/
total 1032
drwxr-xr-x 7 root root   4096 2011-10-22 00:47 .
drwxr-xr-x 8 root root   4096 2011-10-24 22:00 ..
drwxr-xr-x 3 root root   4096 2011-10-22 00:47 arch
lrwxrwxrwx 1 root root     31 2011-10-07 17:44 block -> ../linux-headers-3.0.0-12/block
-rw-r--r-- 1 root root 141588 2011-10-07 17:43 .config
-rw-r--r-- 1 root root 141627 2011-10-07 17:43 .config.old
lrwxrwxrwx 1 root root     32 2011-10-07 17:44 crypto -> ../linux-headers-3.0.0-12/crypto
lrwxrwxrwx 1 root root     39 2011-10-07 17:44 Documentation -> ../linux-headers-3.0.0-12/Documentation
lrwxrwxrwx 1 root root     33 2011-10-07 17:44 drivers -> ../linux-headers-3.0.0-12/drivers
lrwxrwxrwx 1 root root     34 2011-10-07 17:44 firmware -> ../linux-headers-3.0.0-12/firmware
lrwxrwxrwx 1 root root     28 2011-10-07 17:44 fs -> ../linux-headers-3.0.0-12/fs
drwxr-xr-x 5 root root   4096 2011-10-22 00:47 include
lrwxrwxrwx 1 root root     30 2011-10-07 17:44 init -> ../linux-headers-3.0.0-12/init
lrwxrwxrwx 1 root root     29 2011-10-07 17:44 ipc -> ../linux-headers-3.0.0-12/ipc
lrwxrwxrwx 1 root root     32 2011-10-07 17:44 Kbuild -> ../linux-headers-3.0.0-12/Kbuild
lrwxrwxrwx 1 root root     33 2011-10-07 17:44 Kconfig -> ../linux-headers-3.0.0-12/Kconfig
drwxr-xr-x 2 root root   4096 2011-10-22 00:47 kernel
lrwxrwxrwx 1 root root     29 2011-10-07 17:44 lib -> ../linux-headers-3.0.0-12/lib
lrwxrwxrwx 1 root root     34 2011-10-07 17:44 Makefile -> ../linux-headers-3.0.0-12/Makefile
-rw-r--r-- 1 root root    456 2011-10-07 17:43 .missing-syscalls.d
lrwxrwxrwx 1 root root     28 2011-10-07 17:44 mm -> ../linux-headers-3.0.0-12/mm
-rw-r--r-- 1 root root 734707 2011-10-07 17:44 Module.symvers
lrwxrwxrwx 1 root root     29 2011-10-07 17:44 net -> ../linux-headers-3.0.0-12/net
lrwxrwxrwx 1 root root     33 2011-10-07 17:44 samples -> ../linux-headers-3.0.0-12/samples
drwxr-xr-x 7 root root   4096 2011-10-22 00:47 scripts
lrwxrwxrwx 1 root root     34 2011-10-07 17:44 security -> ../linux-headers-3.0.0-12/security
lrwxrwxrwx 1 root root     31 2011-10-07 17:44 sound -> ../linux-headers-3.0.0-12/sound
lrwxrwxrwx 1 root root     25 2011-10-07 17:43 source -> /build/buildd/linux-3.0.0
drwxr-xr-x 2 root root   4096 2011-10-07 17:43 .tmp_versions
lrwxrwxrwx 1 root root     31 2011-10-07 17:44 tools -> ../linux-headers-3.0.0-12/tools
lrwxrwxrwx 1 root root     32 2011-10-07 17:44 ubuntu -> ../linux-headers-3.0.0-12/ubuntu
lrwxrwxrwx 1 root root     29 2011-10-07 17:44 usr -> ../linux-headers-3.0.0-12/usr
lrwxrwxrwx 1 root root     30 2011-10-07 17:44 virt -> ../linux-headers-3.0.0-12/virt

Mi comentario sobro "sudo" fue porque de las transcripciones que mostraste no surgia claramente que estabas como root user (salvo por el # en el prompt al cual no mire).

---

### Post by 53RG10 on 2011-11-13
Algo raro hay entonces.
Ahí probé de hacerlo en usuario común con el comando "sudo make -j3" y lo hace, con el error como antes, pero no me pidió contraseña. ¿Por qué?
Perdón, pero no me quedó claro para que es que hay que hacer esas cuatro cosas.
Saludos.

---

### Post by alfredo_ on 2011-11-13
Hola

> **53RG10 said:**
> Algo raro hay entonces.
Ahí probé de hacerlo en usuario común con el comando "sudo make -j3" y lo hace, con el error como antes, pero no me pidió contraseña. ¿Por qué?
Perdón, pero no me quedó claro para que es que hay que hacer esas cuatro cosas.
Saludos.

Tendría que haberte pedido la contraseña. No sé la razón.
No se a cuales cuatro cosas te referís, si es a make oldconfig, make clean, make y make modules es para que se formen ciertas dependencias que hacen falta para luego si poder compilar el módulo que nos interesa.

Por lo visto hay un problema con las fuentes de tu kernel. Es probable que haya muy rápido otro kernel para actualizar. También podemos probar con un kernel más viejo, pero nos va a dar más guerra.
¿Probaste a compilar con las dos versiones a ver que pasaba?

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-13
Hola nuevamente
> **alfredo_ said:**
> 
No se a cuales cuatro cosas te referís, si es a make oldconfig, make clean, make y make modules es para que se formen ciertas dependencias que hacen falta para luego si poder compilar el módulo que nos interesa.
Sí, eran esas 4. Gracias.
> Por lo visto hay un problema con las fuentes de tu kernel. Es probable que haya muy rápido otro kernel para actualizar. También podemos probar con un kernel más viejo, pero nos va a dar más guerra.
¿Probaste a compilar con las dos versiones a ver que pasaba?

¿2 versiones? ¿Te referís a lo que pregunté antes: la que dice generic o la que no? Si es así te digo que me sale error porque también probé.

No sé que me conviene. La costumbre de que son prácticamente iguales, me olvidé de un detalle, no estoy usando Ubuntu en sí, sino el Mint, pero creo que es lo mismo. Si no es así pido perdón.
Estaba pensando también, que como salió el Mint 12 justo esta semana, instalarlo y ver si funciona mejor. O en todo caso probaremos con un kernel anterior.
Saludos y gracias

---

### Post by alfredo_ on 2011-11-13
> **53RG10 said:**
> Hola nuevamente

Sí, eran esas 4. Gracias.

¿2 versiones? ¿Te referís a lo que pregunté antes: la que dice generic o la que no? Si es así te digo que me sale error porque también probé.

No sé que me conviene. La costumbre de que son prácticamente iguales, me olvidé de un detalle, no estoy usando Ubuntu en sí, sino el Mint, pero creo que es lo mismo. Si no es así pido perdón.
Estaba pensando también, que como salió el Mint 12 justo esta semana, instalarlo y ver si funciona mejor. O en todo caso probaremos con un kernel anterior.
Saludos y gracias

Si me refería al la generic y a la otra.
En cuanto al tipo de distribución mayormente no hay diferencias, pero siempre hay un pero, cada distribución tiene sus particularidades.
En cuanto a la versión no es tan importante si son relativamente nuevas. El problema que se presenta es que las fuentes de tu kernel están mal. Proba compilar en uno de los kernels más viejos que tenes, para ver que pasa.

Saludos

Alfredo

---

### Post by 53RG10 on 2011-11-13
> **alfredo_ said:**
> 
En cuanto a la versión no es tan importante si son relativamente nuevas. El problema que se presenta es que las fuentes de tu kernel están mal. Proba compilar en uno de los kernels más viejos que tenes, para ver que pasa.
Antes de irme a dormir, lo hice con 2 versiones anteriores y también me tira error. ¿No estaré fallando en algo? ¿Revisaste los errores que me tira en detalle para ver si hay algo que se te pasó por alto?
Gracias

---

### Post by alfredo_ on 2011-11-13
Hola

> **53RG10 said:**
> Antes de irme a dormir, lo hice con 2 versiones anteriores y también me tira error. ¿No estaré fallando en algo? ¿Revisaste los errores que me tira en detalle para ver si hay algo que se te pasó por alto?
Gracias

No sé si me pasa algo por alto, así es como lo hago. Solo queda que te fijes que consejos dan para compila el kernel con tu distribución.

Buen descanso, yo voy a hacer lo mismo.

Alfredo

---

### Post by guillermolisi on 2011-11-14
> **alfredo_ said:**
> Bueno adjuntos están los archivos con los parches ya instalado, por lo que creo se te va a hacer más fácil.

En primer lugar reemplaza en usr/src/linux/drivers/media/video/cx23885 los archivos: 
cx23885-cards.c
cx23885-dvb.c
cx23885-video.c
cx23885.h
Kconfig
Makefile



y copia a esta carpeta también el archivo cx23885-alsa.c

El path correcto para el caso Ubuntu es ```
/usr/src/linux-headers-3.0.0-12/drivers/media/
```

El contenido de ese directorio en mi maquina tiene lo siguiente
> guille@guillermo:~$ ls -al /usr/src/linux-headers-3.0.0-12/drivers/media/
total 36
drwxr-xr-x  7 root root 4096 2011-10-22 00:47 .
drwxr-xr-x 93 root root 4096 2011-10-22 00:47 ..
drwxr-xr-x  3 root root 4096 2011-10-22 00:47 common
drwxr-xr-x 17 root root 4096 2011-10-22 00:47 dvb
-rw-r--r--  1 root root 2658 2011-07-21 23:17 Kconfig
-rw-r--r--  1 root root  298 2011-07-21 23:17 Makefile
drwxr-xr-x  4 root root 4096 2011-10-22 00:47 radio
drwxr-xr-x  3 root root 4096 2011-10-22 00:47 rc
drwxr-xr-x 29 root root 4096 2011-10-22 00:47 video

Luego en common veo que tengo > guille@guillermo:~$ ls -al /usr/src/linux-headers-3.0.0-12/drivers/media/common/tuners/
total 20
drwxr-xr-x 2 root root 4096 2011-10-22 00:47 .
drwxr-xr-x 3 root root 4096 2011-10-22 00:47 ..
-rw-r--r-- 1 root root 5956 2011-07-21 23:17 Kconfig
-rw-r--r-- 1 root root 1260 2011-07-21 23:17 Makefile

y en video tengo > guille@guillermo:~$ ls -al /usr/src/linux-headers-3.0.0-12/drivers/media/video/
total 368
drwxr-xr-x 29 root root  4096 2011-10-22 00:47 .
drwxr-xr-x  7 root root  4096 2011-10-22 00:47 ..
-rw-r--r--  1 root root  5629 2011-07-21 23:17 adv7343_regs.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 au0828
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 bt8xx
-rw-r--r--  1 root root   863 2011-07-21 23:17 btcx-risc.h
-rw-r--r--  1 root root  6845 2011-07-21 23:17 cafe_ccic-regs.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 cpia2
-rw-r--r--  1 root root  1681 2011-07-21 23:17 cs8420.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 cx18
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 cx231xx
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 cx23885
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 cx25840
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 cx88
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 davinci
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 em28xx
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 et61x251
drwxr-xr-x  5 root root  4096 2011-10-22 00:47 gspca
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 hdpvr
-rw-r--r--  1 root root  2800 2011-07-21 23:17 ibmmpeg2.h
-rw-r--r--  1 root root  3306 2011-07-21 23:17 indycam.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 ivtv
-rw-r--r--  1 root root 29597 2011-07-21 23:17 Kconfig
-rw-r--r--  1 root root  1650 2011-07-21 23:17 ks0127.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 m5mols
-rw-r--r--  1 root root  6405 2011-07-21 23:17 Makefile
-rw-r--r--  1 root root 12456 2011-07-21 23:17 meye.h
-rw-r--r--  1 root root  3432 2011-07-21 23:17 msp3400-driver.h
-rw-r--r--  1 root root   935 2011-07-21 23:17 mxb.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 omap
-rw-r--r--  1 root root 19075 2011-07-21 23:17 omap24xxcam.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 omap3isp
-rw-r--r--  1 root root   476 2011-07-21 23:17 ov7670.h
-rw-r--r--  1 root root  4914 2011-07-21 23:17 ov9640.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 pvrusb2
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 pwc
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 s5p-fimc
-rw-r--r--  1 root root 22819 2011-07-21 23:17 saa711x_regs.h
-rw-r--r--  1 root root  5006 2011-07-21 23:17 saa7121.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 saa7134
-rw-r--r--  1 root root  3304 2011-07-21 23:17 saa7146.h
-rw-r--r--  1 root root  9115 2011-07-21 23:17 saa7146reg.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 saa7164
-rw-r--r--  1 root root  8397 2011-07-21 23:17 saa7191.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 sn9c102
-rw-r--r--  1 root root  3711 2011-07-21 23:17 stk-webcam.h
-rw-r--r--  1 root root  6597 2011-07-21 23:17 tcm825x.h
-rw-r--r--  1 root root   723 2011-07-21 23:17 tea6415c.h
-rw-r--r--  1 root root   522 2011-07-21 23:17 tea6420.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 tlg2300
-rw-r--r--  1 root root  8034 2011-07-21 23:17 tvp514x_regs.h
-rw-r--r--  1 root root  5902 2011-07-21 23:17 tvp5150_reg.h
-rw-r--r--  1 root root  5274 2011-07-21 23:17 tvp7002_reg.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 usbvision
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 uvc
-rw-r--r--  1 root root  5139 2011-07-21 23:17 via-camera.h
-rw-r--r--  1 root root  4524 2011-07-21 23:17 vino.h
drwxr-xr-x  2 root root  4096 2011-10-22 00:47 zoran

Asi que tenemos que empezar por acomodar ubicaciones adecuadas en funcion de como esta estructurado Ubuntu para los fuentes del kernel.

Esta es la primera razon que encuentro para los errores reportados por 53rg10.

---

### Post by alfredo_ on 2011-11-14
> **guillermolisi said:**
> El path correcto para el caso Ubuntu es ```
/usr/src/linux-headers-3.0.0-12/drivers/media/
``` 

Tienes que seguir "más adentro" en los directorios. Tendría que llegar a algo así como:

/usr/src/linux-headers-3.0.0-12/drivers/media/video/cx23885



> **guillermolisi said:**
> 
Asi que tenemos que empezar por acomodar ubicaciones adecuadas en funcion de como esta estructurado Ubuntu para los fuentes del kernel.

Esta es la primera razon que encuentro para los errores reportados por 53rg10.

Creo que además tiene un problema en el mismo kernel, dado que dice el compilador:
> 
make[1]: *** No hay ninguna regla para construir el objetivo «kernel/bounds.c», necesario para «kernel/bounds.s».  Alto. 
Por lo que interpreto es que le falta algo, tal vez sea el archivo Kbuild que debería estar en:
/usr/src/linux-headers-3.0.0-12
Esto es lo que deduzco de mirar las fuentes de mi kernel.

Gracias Guillermo por ayudarnos,

Alfredo

---

### Post by guillermolisi on 2011-11-14
> **alfredo_ said:**
> Tienes que seguir "más adentro" en los directorios. Tendría que llegar a algo así como:

/usr/src/linux-headers-3.0.0-12/drivers/media/video/cx23885


Mostre hasta donde tiene que llegar, en detalle.

> 
Creo que además tiene un problema en el mismo kernel, dado que dice el compilador:

Por lo que interpreto es que le falta algo, tal vez sea el archivo Kbuild que debería estar en:
/usr/src/linux-headers-3.0.0-12
Esto es lo que deduzco de mirar las fuentes de mi kernel.

Gracias Guillermo por ayudarnos,

Alfredo
Si te fijas bien, [en un post mio anterior]("http://ubuntuforums.org/showpost.php?p=11454536&postcount=31") tambien muestro el contenido de /usr/src/linux-headers-3.0.0-12 y ahi figura kbuild.

---

### Post by 53RG10 on 2011-11-14
Hola, acá estoy de vuelta.
Tuve unos problemas con Linux y entonces aproveché e instalé Linux Mint 12. Así que ahora intentaré hacer lo mismo que antes a ver como me va. Les aviso primero así saben por qué es que no les traigo novedades.
Saludos

EDITO y comento que volví a tener el mismo error: > sergio-GA-890GPA-UD3H linux-headers-3.0.0-12-generic # make clean -j3
/usr/src/linux-headers-3.0.0-12-generic/ubuntu/aufs/Makefile:2: ubuntu/aufs/magic.mk: No existe el archivo o el directorio
make[2]: *** No hay ninguna regla para construir el objetivo «ubuntu/aufs/magic.mk».  Alto.
make[1]: *** [ubuntu/aufs] Error 2
make: *** [_clean_ubuntu] Error 2
make: *** Se espera a que terminen otras tareas....
sergio-GA-890GPA-UD3H linux-headers-3.0.0-12-generic # make oldconfig -j3
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --oldconfig Kconfig
#
# configuration written to .config
#
sergio-GA-890GPA-UD3H linux-headers-3.0.0-12-generic # make -j3
scripts/kconfig/conf --silentoldconfig Kconfig
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
  HOSTCC  scripts/genksyms/genksyms.o
  HOSTCC  scripts/genksyms/lex.o
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  HOSTCC  scripts/selinux/genheaders/genheaders
scripts/selinux/genheaders/genheaders.c:13:22: error fatal: classmap.h: No existe el archivo o el directorio
compilación terminada.
  HOSTCC  scripts/mod/modpost.o
make[3]: *** [scripts/selinux/genheaders/genheaders] Error 1
make[2]: *** [scripts/selinux/genheaders] Error 2
make[1]: *** [scripts/selinux] Error 2
make[1]: *** Se espera a que terminen otras tareas....
  HOSTCC  scripts/mod/sumversion.o
make[1]: *** No hay ninguna regla para construir el objetivo «kernel/bounds.c», necesario para «kernel/bounds.s».  Alto.
make[1]: *** Se espera a que terminen otras tareas....
make: *** [prepare0] Error 2
make: *** Se espera a que terminen otras tareas....
  HOSTLD  scripts/mod/modpost
make: *** [scripts] Error 2
sergio-GA-890GPA-UD3H linux-headers-3.0.0-12-generic # make modules -j3
  CHK     include/linux/version.h
  HOSTCC  scripts/selinux/genheaders/genheaders
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/selinux/mdp/mdp
scripts/selinux/genheaders/genheaders.c:13:22: error fatal: classmap.h: No existe el archivo o el directorio
compilación terminada.
scripts/selinux/mdp/mdp.c:44:22: error fatal: classmap.h: No existe el archivo o el directorio
compilación terminada.
make[3]: *** [scripts/selinux/genheaders/genheaders] Error 1
make[2]: *** [scripts/selinux/genheaders] Error 2
make[2]: *** Se espera a que terminen otras tareas....
  HOSTCC  scripts/conmakehash
make[3]: *** [scripts/selinux/mdp/mdp] Error 1
make[2]: *** [scripts/selinux/mdp] Error 2
make[1]: *** [scripts/selinux] Error 2
make[1]: *** Se espera a que terminen otras tareas....
make: *** [scripts] Error 2

¿Y ahora?

---

### Post by guillermolisi on 2011-11-14
> **53RG10 said:**
> Hola, acá estoy de vuelta.
Tuve unos problemas con Linux y entonces aproveché e instalé Linux Mint 12. Así que ahora intentaré hacer lo mismo que antes a ver como me va. Les aviso primero así saben por qué es que no les traigo novedades.
Saludos

EDITO y comento que volví a tener el mismo error: 
¿Y ahora?

Ahora cambio la cosa. El error se esta dando en otro archivo distinto de la corrida anterior.

Se que esto lo deberia haber preguntado antes, pero .... tenes habilitado el repositorio src y bajado el kernel en version fuente ?

---

### Post by 53RG10 on 2011-11-14
> **guillermolisi said:**
> Ahora cambio la cosa. El error se esta dando en otro archivo distinto de la corrida anterior.
Se que esto lo deberia haber preguntado antes, pero .... tenes habilitado el repositorio src y bajado el kernel en version fuente ?
En realidad, no entiendo lo que estás preguntando, para variar :confused:.
Decime que es y como hacerlo que lo hago... Si no es mucho pedir.
Gracias

P.D. ¿Será mejor que instale otro tipo de distro, como por ejemplo debian?  ¿O estaría en lo msimo?

---

### Post by alfredo_ on 2011-11-14
Hola

¿Instalaste Linux Mint o Ubuntu?

Hay un lugar donde vos podes agregar y quitar software como lugares de donde descargalos en todas las distribuciones. Lo que te pregunta Guillermo es si has puesto, entre las cosas que hay para descargar, es el repositorio (el lugar de  donde descargar) las fuentes del kernel (son, por decirlo de alguna manera, los archivos con los que se hacen los controladores) y si las haz instalado. Normalmente se las busca como fuente o source (src) del kernel. 

Te repito si te sale un error no sigas, hay que solucionarlo. Todo lo demás que haga solo nos hará confundir y no sirve para nada

Bueno ya tenes algo para buscar.

Saludos,

Alfredo

---

### Post by alfredo_ on 2011-11-14
Hola

Como dato mira esta página:

[http://www.ubuntu-es.org/node/431](http://www.ubuntu-es.org/node/431)

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-15
Hola
Por primera vez les traigo buenas noticias, creo que ya está (o casi), primero hice esto:
```
 # apt-get install build-essential kernel-package
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias      
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  dpkg-dev g++ g++-4.6 intltool-debian libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libmail-sendmail-perl libstdc++6-4.6-dev libsys-hostname-long-perl
  po-debconf
Paquetes sugeridos:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  linux-source kernel-source libncurses-dev docbook-utils xmlto grub grub2
  jfsutils mcelog oprofile reiserfsprogs squashfs-tools xfsprogs quota
  btrfs-tools libstdc++6-4.6-doc libmail-box-perl
Se instalarán los siguientes paquetes NUEVOS:
  build-essential dpkg-dev g++ g++-4.6 intltool-debian kernel-package
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libdpkg-perl libmail-sendmail-perl libstdc++6-4.6-dev
  libsys-hostname-long-perl po-debconf
0 actualizados, 14 se instalarán, 0 para eliminar y 1 no actualizados.
Necesito descargar 10,0 MB de archivos.
Se utilizarán 33,4 MB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Des:1 http://archive.ubuntu.com/ubuntu/ oneiric/main libstdc++6-4.6-dev amd64 4.6.1-9ubuntu3 [1.644 kB]
Des:2 http://archive.ubuntu.com/ubuntu/ oneiric/main g++-4.6 amd64 4.6.1-9ubuntu3 [6.970 kB]
Des:3 http://archive.ubuntu.com/ubuntu/ oneiric/main g++ amd64 4:4.6.1-2ubuntu5 [1.444 B]
Des:4 http://archive.ubuntu.com/ubuntu/ oneiric/main libdpkg-perl all 1.16.0.3ubuntu5 [171 kB]
Des:5 http://archive.ubuntu.com/ubuntu/ oneiric/main dpkg-dev all 1.16.0.3ubuntu5 [473 kB]
Des:6 http://archive.ubuntu.com/ubuntu/ oneiric/main build-essential amd64 11.5ubuntu1 [5.928 B]
Des:7 http://archive.ubuntu.com/ubuntu/ oneiric/main intltool-debian all 0.35.0+20060710.1 [31,6 kB]
Des:8 http://archive.ubuntu.com/ubuntu/ oneiric/main po-debconf all 1.0.16+nmu1 [212 kB]
Des:9 http://archive.ubuntu.com/ubuntu/ oneiric/universe kernel-package all 12.036+nmu1 [404 kB]
Des:10 http://archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-perl all 1.19.02-2 [50,7 kB]
Des:11 http://archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-xs-perl amd64 0.04-1build1 [13,4 kB]
Des:12 http://archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-merge-perl all 0.08-2 [12,7 kB]
Des:13 http://archive.ubuntu.com/ubuntu/ oneiric/main libsys-hostname-long-perl all 1.4-2 [11,4 kB]
Des:14 http://archive.ubuntu.com/ubuntu/ oneiric/main libmail-sendmail-perl all 0.79.16-1 [26,5 kB]
Descargados 10,0 MB en 1min. 24seg. (119 kB/s)                                
Seleccionando el paquete libstdc++6-4.6-dev previamente no seleccionado.
(Leyendo la base de datos ... 171447 ficheros o directorios instalados actualmente.)
Desempaquetando libstdc++6-4.6-dev (de .../libstdc++6-4.6-dev_4.6.1-9ubuntu3_amd64.deb) ...
Seleccionando el paquete g++-4.6 previamente no seleccionado.
Desempaquetando g++-4.6 (de .../g++-4.6_4.6.1-9ubuntu3_amd64.deb) ...
Seleccionando el paquete g++ previamente no seleccionado.
Desempaquetando g++ (de .../g++_4%3a4.6.1-2ubuntu5_amd64.deb) ...
Seleccionando el paquete libdpkg-perl previamente no seleccionado.
Desempaquetando libdpkg-perl (de .../libdpkg-perl_1.16.0.3ubuntu5_all.deb) ...
Seleccionando el paquete dpkg-dev previamente no seleccionado.
Desempaquetando dpkg-dev (de .../dpkg-dev_1.16.0.3ubuntu5_all.deb) ...
Seleccionando el paquete build-essential previamente no seleccionado.
Desempaquetando build-essential (de .../build-essential_11.5ubuntu1_amd64.deb) ...
Seleccionando el paquete intltool-debian previamente no seleccionado.
Desempaquetando intltool-debian (de .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Seleccionando el paquete po-debconf previamente no seleccionado.
Desempaquetando po-debconf (de .../po-debconf_1.0.16+nmu1_all.deb) ...
Seleccionando el paquete kernel-package previamente no seleccionado.
Desempaquetando kernel-package (de .../kernel-package_12.036+nmu1_all.deb) ...
Seleccionando el paquete libalgorithm-diff-perl previamente no seleccionado.
Desempaquetando libalgorithm-diff-perl (de .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Seleccionando el paquete libalgorithm-diff-xs-perl previamente no seleccionado.
Desempaquetando libalgorithm-diff-xs-perl (de .../libalgorithm-diff-xs-perl_0.04-1build1_amd64.deb) ...
Seleccionando el paquete libalgorithm-merge-perl previamente no seleccionado.
Desempaquetando libalgorithm-merge-perl (de .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Seleccionando el paquete libsys-hostname-long-perl previamente no seleccionado.
Desempaquetando libsys-hostname-long-perl (de .../libsys-hostname-long-perl_1.4-2_all.deb) ...
Seleccionando el paquete libmail-sendmail-perl previamente no seleccionado.
Desempaquetando libmail-sendmail-perl (de .../libmail-sendmail-perl_0.79.16-1_all.deb) ...
Procesando disparadores para man-db ...
Procesando disparadores para doc-base ...
Procesando 1 archivo doc-base añadido...
Registrando documentos con scrollkeeper...
Configurando libdpkg-perl (1.16.0.3ubuntu5) ...
Configurando dpkg-dev (1.16.0.3ubuntu5) ...
Configurando intltool-debian (0.35.0+20060710.1) ...
Configurando po-debconf (1.0.16+nmu1) ...
Configurando libalgorithm-diff-perl (1.19.02-2) ...
Configurando libalgorithm-diff-xs-perl (0.04-1build1) ...
Configurando libalgorithm-merge-perl (0.08-2) ...
Configurando libsys-hostname-long-perl (1.4-2) ...
Configurando libmail-sendmail-perl (0.79.16-1) ...
Configurando g++-4.6 (4.6.1-9ubuntu3) ...
Configurando libstdc++6-4.6-dev (4.6.1-9ubuntu3) ...
Configurando g++ (4:4.6.1-2ubuntu5) ...
update-alternatives: utilizando /usr/bin/g++ para proveer /usr/bin/c++ (c++) en modo automático.
Configurando build-essential (11.5ubuntu1) ...
Configurando kernel-package (12.036+nmu1) ...
sergio-GA-890GPA-UD3H sergio # apt-get update
Ign http://packages.linuxmint.com lisa InRelease
Obj http://packages.medibuntu.org oneiric InRelease                           
Ign http://security.ubuntu.com oneiric-security InRelease                     
Ign http://archive.canonical.com oneiric InRelease                            
Des:1 http://packages.linuxmint.com lisa Release.gpg [198 B]                  
Ign http://archive.ubuntu.com oneiric InRelease                               
Ign http://archive.ubuntu.com oneiric-updates InRelease                       
Obj http://security.ubuntu.com oneiric-security Release.gpg                   
Obj http://archive.canonical.com oneiric Release.gpg                          
Des:2 http://packages.linuxmint.com lisa Release [16,5 kB]                    
Obj http://packages.medibuntu.org oneiric/free amd64 Packages                 
Obj http://archive.ubuntu.com oneiric Release.gpg                             
Obj http://security.ubuntu.com oneiric-security Release                       
Obj http://archive.canonical.com oneiric Release                              
Obj http://archive.ubuntu.com oneiric-updates Release.gpg                     
Obj http://security.ubuntu.com oneiric-security/main amd64 Packages           
Obj http://archive.canonical.com oneiric/partner amd64 Packages               
Obj http://packages.medibuntu.org oneiric/non-free amd64 Packages             
Des:3 http://packages.linuxmint.com lisa/main amd64 Packages [12,0 kB]        
Obj http://archive.ubuntu.com oneiric Release                                 
Obj http://security.ubuntu.com oneiric-security/restricted amd64 Packages     
Obj http://security.ubuntu.com oneiric-security/universe amd64 Packages       
Obj http://security.ubuntu.com oneiric-security/multiverse amd64 Packages     
Obj http://security.ubuntu.com oneiric-security/main i386 Packages            
Obj http://security.ubuntu.com oneiric-security/restricted i386 Packages      
Obj http://archive.canonical.com oneiric/partner i386 Packages                
Ign http://archive.canonical.com oneiric/partner TranslationIndex             
Obj http://security.ubuntu.com oneiric-security/universe i386 Packages        
Obj http://security.ubuntu.com oneiric-security/multiverse i386 Packages      
Obj http://security.ubuntu.com oneiric-security/main TranslationIndex         
Obj http://security.ubuntu.com oneiric-security/multiverse TranslationIndex   
Obj http://security.ubuntu.com oneiric-security/restricted TranslationIndex   
Obj http://archive.ubuntu.com oneiric-updates Release                         
Obj http://security.ubuntu.com oneiric-security/universe TranslationIndex     
Obj http://packages.medibuntu.org oneiric/free i386 Packages                  
Obj http://archive.ubuntu.com oneiric/main amd64 Packages                     
Obj http://archive.ubuntu.com oneiric/restricted amd64 Packages               
Obj http://archive.ubuntu.com oneiric/universe amd64 Packages                 
Obj http://archive.ubuntu.com oneiric/multiverse amd64 Packages               
Obj http://archive.ubuntu.com oneiric/main i386 Packages                      
Obj http://security.ubuntu.com oneiric-security/main Translation-en           
Obj http://security.ubuntu.com oneiric-security/multiverse Translation-en     
Des:4 http://packages.linuxmint.com lisa/upstream amd64 Packages [25,4 kB]    
Obj http://archive.ubuntu.com oneiric/restricted i386 Packages                
Obj http://archive.ubuntu.com oneiric/universe i386 Packages                  
Obj http://archive.ubuntu.com oneiric/multiverse i386 Packages                
Obj http://archive.ubuntu.com oneiric/main TranslationIndex                   
Obj http://archive.ubuntu.com oneiric/multiverse TranslationIndex             
Obj http://security.ubuntu.com oneiric-security/restricted Translation-en     
Obj http://packages.medibuntu.org oneiric/non-free i386 Packages              
Obj http://archive.ubuntu.com oneiric/restricted TranslationIndex             
Obj http://archive.ubuntu.com oneiric/universe TranslationIndex               
Obj http://archive.ubuntu.com oneiric-updates/main amd64 Packages             
Obj http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages       
Obj http://archive.ubuntu.com oneiric-updates/universe amd64 Packages         
Des:5 http://packages.linuxmint.com lisa/import amd64 Packages [19,3 kB]      
Obj http://security.ubuntu.com oneiric-security/universe Translation-en       
Obj http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages       
Ign http://packages.medibuntu.org oneiric/free TranslationIndex               
Des:6 http://packages.linuxmint.com lisa/main i386 Packages [12,0 kB]         
Obj http://archive.ubuntu.com oneiric-updates/main i386 Packages              
Obj http://archive.ubuntu.com oneiric-updates/restricted i386 Packages        
Obj http://archive.ubuntu.com oneiric-updates/universe i386 Packages          
Obj http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages        
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex           
Des:7 http://packages.linuxmint.com lisa/upstream i386 Packages [24,9 kB]     
Obj http://archive.ubuntu.com oneiric-updates/main TranslationIndex           
Obj http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex     
Obj http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex     
Obj http://archive.ubuntu.com oneiric-updates/universe TranslationIndex       
Obj http://archive.ubuntu.com oneiric/main Translation-es                     
Obj http://archive.ubuntu.com oneiric/main Translation-en                     
Obj http://archive.ubuntu.com oneiric/multiverse Translation-es               
Ign http://archive.canonical.com oneiric/partner Translation-es_AR            
Obj http://archive.ubuntu.com oneiric/multiverse Translation-en               
Obj http://archive.ubuntu.com oneiric/restricted Translation-es               
Obj http://archive.ubuntu.com oneiric/restricted Translation-en               
Ign http://archive.canonical.com oneiric/partner Translation-es               
Obj http://archive.ubuntu.com oneiric/universe Translation-es                 
Obj http://archive.ubuntu.com oneiric/universe Translation-en                 
Obj http://archive.ubuntu.com oneiric-updates/main Translation-en             
Obj http://archive.ubuntu.com oneiric-updates/multiverse Translation-en       
Obj http://archive.ubuntu.com oneiric-updates/restricted Translation-en       
Des:8 http://packages.linuxmint.com lisa/import i386 Packages [19,3 kB]       
Ign http://archive.canonical.com oneiric/partner Translation-es_ES            
Ign http://archive.canonical.com oneiric/partner Translation-en               
Obj http://archive.ubuntu.com oneiric-updates/universe Translation-en         
Ign http://packages.linuxmint.com lisa/import TranslationIndex                
Ign http://packages.linuxmint.com lisa/main TranslationIndex                  
Ign http://packages.linuxmint.com lisa/upstream TranslationIndex              
Ign http://packages.linuxmint.com lisa/import Translation-es_AR               
Ign http://packages.linuxmint.com lisa/import Translation-es                  
Ign http://packages.linuxmint.com lisa/import Translation-es_ES               
Ign http://packages.linuxmint.com lisa/import Translation-en                  
Ign http://packages.linuxmint.com lisa/main Translation-es_AR                 
Ign http://packages.linuxmint.com lisa/main Translation-es                    
Ign http://packages.linuxmint.com lisa/main Translation-es_ES                 
Ign http://packages.linuxmint.com lisa/main Translation-en                    
Ign http://packages.linuxmint.com lisa/upstream Translation-es_AR             
Ign http://packages.linuxmint.com lisa/upstream Translation-es                
Ign http://packages.linuxmint.com lisa/upstream Translation-es_ES             
Ign http://packages.linuxmint.com lisa/upstream Translation-en                
Ign http://packages.medibuntu.org oneiric/free Translation-es_AR              
Ign http://packages.medibuntu.org oneiric/free Translation-es
Ign http://packages.medibuntu.org oneiric/free Translation-es_ES
Ign http://packages.medibuntu.org oneiric/free Translation-en
Ign http://packages.medibuntu.org oneiric/non-free Translation-es_AR
Ign http://packages.medibuntu.org oneiric/non-free Translation-es
Ign http://packages.medibuntu.org oneiric/non-free Translation-es_ES
Ign http://packages.medibuntu.org oneiric/non-free Translation-en
Descargados 130 kB en 20seg. (6.212 B/s)
Leyendo listas de paquetes... Hecho
# apt-get install linux-source
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias      
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  linux-source-3.0.0
Paquetes sugeridos:
  libncurses-dev ncurses-dev libqt3-dev
Se instalarán los siguientes paquetes NUEVOS:
  linux-source linux-source-3.0.0
0 actualizados, 2 se instalarán, 0 para eliminar y 1 no actualizados.
Necesito descargar 79,2 MB de archivos.
Se utilizarán 86,6 MB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Des:1 http://archive.ubuntu.com/ubuntu/ oneiric/main linux-source-3.0.0 all 3.0.0-12.20 [79,2 MB]
Des:2 http://archive.ubuntu.com/ubuntu/ oneiric/main linux-source all 3.0.0.12.14 [2.342 B]
Descargados 79,2 MB en 12min. 13seg. (108 kB/s)                                  
Seleccionando el paquete linux-source-3.0.0 previamente no seleccionado.
(Leyendo la base de datos ... 172886 ficheros o directorios instalados actualmente.)
Desempaquetando linux-source-3.0.0 (de .../linux-source-3.0.0_3.0.0-12.20_all.deb) ...
Seleccionando el paquete linux-source previamente no seleccionado.
Desempaquetando linux-source (de .../linux-source_3.0.0.12.14_all.deb) ...
Configurando linux-source-3.0.0 (3.0.0-12.20) ...
Configurando linux-source (3.0.0.12.14) ...
```Y después hice esto sin ningún error (alguna vez me tenía que pasar ):
cd /usr/src
sudo tar jxvf linux-source-3.0.0.tar.bz2
ln -s linux-source-3.0.0 linux

Y como para culminar pude hacer lo que me habían pedido varios mensajes atrás y que no podía hacerlo por errores (lo ejecuté dentro de la carpeta cd /usr/src/linux-source-3.0.0 (inexistente hasta el paso anterior):

make clean -j3
make oldconfig -j3
make -j3

Hasta acá todo perfecto y después hice este:
make modules -j3
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CALL    scripts/checksyscalls.sh
  Building modules, stage 2.
  MODPOST 3201 modules
WARNING: modpost: Found 9 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'

Como me puso eso, ejecuté por las dudas en la terminal 'make CONFIG_DEBUG_SECTION_MISMATCH=y' y tardó bastante pero no sé que hizo al final. Pensé que me iba a crear un archivo o mostrar algo, pero si lo hizo no sé donde está

Como me anticiparon llevó su tiempo, pero valió la pena.
Muchas gracias por la paciencia.
Habiendo hecho esto, ¿ahora por donde seguimos (o sigo)?
Saludos

P.D. En cuanto al Linux, aclaro que era el Mint 12 el que instalé.

---

### Post by alfredo_ on 2011-11-15
Hola

Bueno ahora estamos mejor, has podido compilar.
Los Warning te están avisando de que algo puede fallar, pero no es de la parte que nos interesa, por lo que no le hacemos caso.

Lo que te toca hacer ahora es lo que pido en el mensaje              #[**12**]("http://ubuntuforums.org/showpost.php?p=11446893&postcount=12") y luego el del               #[**23**]("http://ubuntuforums.org/showpost.php?p=11454076&postcount=23") y              #[**24**]("http://ubuntuforums.org/showpost.php?p=11454107&postcount=24") en ese orden.

Si tenemos mucha suerte tendrías soporte, pero es probable que haya que corregir algo.
Por si las moscas, los archivos que puse tienen parte de pruebas que estoy haciendo para ver si puedo ver la parte digital, por lo que vas a ver que reconoce todo, pero no funcionan. (Si te llega a salir andando juro que insultare a ti y toda tu familia por un largo tiempo y a mí y la mía también, el tano Pasman será un poroto al lado mio :smile:).

También hace respaldo de lo que hay en:

/lib/modules/tu_kernel/kernel/drivers/media/video/cx23885/

Con TVTime, XawTV es necesario en una consola a parte lanzar este comando para que haya sonido:

arecord -D hw:3,0 -r 48000 -c 2 -f S16_LE | aplay -

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-15
Hola
> **alfredo_ said:**
> Hola
Lo que te toca hacer ahora es lo que pido en el mensaje              #[**12**]("http://ubuntuforums.org/showpost.php?p=11446893&postcount=12") y luego el del               #[**23**]("http://ubuntuforums.org/showpost.php?p=11454076&postcount=23") y              #[**24**]("http://ubuntuforums.org/showpost.php?p=11454107&postcount=24") en ese orden.
Si tenemos mucha suerte tendrías soporte, pero es probable que haya que corregir algo.

Obviamente no tuvimos suerte:
```
# make SUBDIRS=drivers/media/video/cx23885 modules -j3
  CC [M]  drivers/media/video/cx23885/cx23885-cards.o
  CC [M]  drivers/media/video/cx23885/cx23885-video.o
make[1]: *** No hay ninguna regla para construir el objetivo «drivers/media/video/cx23885/cx23885-vbi.o», necesario para «drivers/media/video/cx23885/cx23885.o».  Alto.
make[1]: *** Se espera a que terminen otras tareas....
drivers/media/video/cx23885/cx23885-cards.c:28:50: error fatal: ../../../staging/altera-stapl/altera.h: No existe el archivo o el directorio
compilación terminada.
In file included from drivers/media/video/cx23885/cx23885-video.c:34:0:
drivers/media/video/cx23885/cx23885.h:36:25: error fatal: cx23885-reg.h: No existe el archivo o el directorio
compilación terminada.
make[1]: *** [drivers/media/video/cx23885/cx23885-cards.o] Error 1
make[1]: *** [drivers/media/video/cx23885/cx23885-video.o] Error 1
make: *** [_module_drivers/media/video/cx23885] Error 2

```
¿Cómo sigo?
Saludos

---

### Post by alfredo_ on 2011-11-15
Hola Sergio

Ya estamos cerca.


Reemplaza también los archivos cx23885-core.c y cx23885-vbi.c en /usr/src/linux....etc. (no hace falta a esta altura poner todo el directorio.

y compila de nuevo el kernel.

make SUBDIRS=drivers/media/video/cx23885 modules -j3

Te va a dar errores, pero espero que sean distintos.

Espero que hayas hecho respaldo de los originales, pues ellos me van a servir luego para corregir algún error de dependencia o anular algún controlador que por ahora no necesitemos y tenga algún problema de dependencia.

Saludos.

Alfredo

---

### Post by alfredo_ on 2011-11-15
Hola 

Revisando veo que hay algo que no tendría por que estar faltando

> 
drivers/media/video/cx23885/cx23885-cards.c:28:50: error fatal: ../../../staging/altera-stapl/altera.h: No existe el archivo o el directorio

drivers/media/video/cx23885/cx23885.h:36:25: error fatal: cx23885-reg.h: No existe el archivo o el directorio
compilación terminada.


Por favor decime que archivos tenias en la carpeta: 
/usr/src/linux-source-3.0.0/drivers/media/video/cx23885/

tendrían que ser unos 31 archivos:

file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/Kconfig
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/Makefile
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/altera-ci.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/altera-ci.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cimax2.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cimax2.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-417.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-av.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-av.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-cards.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-core.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-dvb.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-f300.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-f300.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-i2c.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-input.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-input.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-ioctl.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-ioctl.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-ir.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-ir.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-reg.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-vbi.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885-video.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23885.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23888-ir.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/cx23888-ir.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/netup-eeprom.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/netup-eeprom.h
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/netup-init.c
file:///home/alfredo/ISDB/linux-media-2011-11-04/drivers/media/video/cx23885/netup-init.h

Estos son los que yo tengo

Revisa por favor.

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-15
Hola
Yo acabo de darme cuenta que había sólo 2 archivos (recién ahora los miré porque copié la carpeta directamente), igual no sabía cuántos tenía que haber: 
Kconfig
Makefile
Por lo que veo eso es raro por lo menos, ¿no?
Saludos

---

### Post by alfredo_ on 2011-11-15
Hola

Esto quiere decir que no estamos donde están las fuentes del kernel.
Vas a tener que investigar un poco dentro de las carpetas /usr/src/ tendría que estar una con las fuentes, en ellas te vas a dar cuenta porque la carpeta en cuestión va a tener todos esos archivos.
Lo raro es que si compilo tendría que estar estos datos.
Con un buscador de archivos, el de tu preferencia, busca dentro de /usr/src/ a ver si hay alguna que los contenga. Por ejemplo en KDE dolphin tiene esta capacidad, o suele haber en el lanzador de programas alguno que permite buscar.

Saludos,

Alfredo

---

### Post by alfredo_ on 2011-11-15
Me quedo algo en el tintero, supongo que leíste el enlace de como compilar e instalar las fuentes, que puse en una carta anterior.

Saludos,

Alfredo

---

### Post by alfredo_ on 2011-11-15
[FONT=Arial]No veo de de tus cartas anteriores que hayas hecho:[/FONT]

sudo apt-get install linux-source

[FONT=Arial]Que es lo que recomiendan en el enlace que te pase.

Aunque en alguna de tus cartas da a entender que lo has hecho por otro lado. Quizás Guillermo nos pueda ayudar en este punto.

Saludos,

Alfredo[/FONT]

---

### Post by alfredo_ on 2011-11-15
Hola 

_[COLOR=Red]**Por favor lee bien lo que te estoy sugiriendo**[/COLOR]_. Esto es porque cuando te indique que reemplazaras los archivos cx23885-video.c tendrías que haberte dado cuenta que no estaban, más si es que los estas haciendo con midnight commander.
Como ayuda relee todos los mensajes que hemos escrito e interpretalos lo mejor que puedas, así evitaremos errores como los últimos. Que la ansiedad no te domine.

Vamos sigamos para adelante,

Alfredo

---

### Post by 53RG10 on 2011-11-15
Hola
No hay problema, parece que vamos llegando a buen puerto:
¿Esto: > Me quedo algo en el tintero, supongo que leíste el enlace de como  compilar e instalar las fuentes, que puse en una carta anterior. y esto:
> [FONT=Arial]No veo de de tus cartas anteriores que hayas hecho:[/FONT]
sudo apt-get install linux-source
[FONT=Arial]Que es lo que recomiendan en el enlace que te pase.[/FONT] es lo mismo?
Porque el apt-get install linux-source ya lo hice y ahí me equivoqué, yo estaba reemplazando archivos del kernel que termina en -generic y era en la carpeta linux-source. Ahí si están los archivos.
Entonces ahora te pregunto, ¿la carpeta que reemplacé la vuelvo a como estaba y entonces hago lo que debía hacer antes en la carpeta correcta? Ahora también hice copias de seguridad de las que corresponden.
Perdón por la confusión, pero no estoy muy familiarizado con el Commander y lo hice a ojo. Y gracias nuevamente.
Saludos

---

### Post by alfredo_ on 2011-11-15
Hola

> Hola
No hay problema, parece que vamos llegando a buen puerto:
¿Esto: 
Me quedo algo en el tintero, supongo que leíste el enlace de como   compilar e instalar las fuentes, que puse en una carta anterior.
 y esto:
[FONT=Arial]No veo de de tus cartas anteriores que hayas hecho:[/FONT]
sudo apt-get install linux-source
[FONT=Arial]Que es lo que recomiendan en el enlace que te pase.[/FONT]
 es lo mismo?

Si es lo mismo, corregí lo que había escrito, pero ya lo habías leído. Mis disculpas.

> 
Porque el apt-get install linux-source ya lo hice y ahí me equivoqué, yo estaba reemplazando archivos del kernel que termina en -generic y era en la carpeta linux-source. Ahí si están los archivos.
Entonces ahora te pregunto, ¿la carpeta que reemplacé la vuelvo a como estaba y entonces hago lo que debía hacer antes en la carpeta correcta? Ahora también hice copias de seguridad de las que corresponden.
Perdón por la confusión, pero no estoy muy familiarizado con el Commander y lo hice a ojo. Y gracias nuevamente.
Saludos

Siempre es mejor dejar las cosas como están, más si se comete un error.

Todo lo vamos ha realizar en linux-source. Primero le hacemos los respaldos, luego los make, luego reemplazamos los archivos que te he enviado, después el "make SUBDIRS=drivers/media/video/cx23885 modules -j3", seguimos con el reemplazo de cx23885.ko y por último el modprobe. **¡Si hay un error no sigas!.**

Es probable que haya errores.

Bueno adelante.

Alfredo

---

### Post by 53RG10 on 2011-11-15
Hola
> Si es lo mismo, corregí lo que había escrito, pero ya lo habías leído. Mis disculpas. Lo único que falta es que vos me pidas perdón a mí :D. Si te estoy volviendo loco para instalar una placa.
> Siempre es mejor dejar las cosas como están, más si se comete un error. Así será entonces.
> 
Todo lo vamos ha realizar en linux-source. Primero le hacemos los respaldos, luego los make, luego reemplazamos los archivos que te he enviado, después el "make SUBDIRS=drivers/media/video/cx23885 modules -j3", seguimos con el reemplazo de cx23885.ko y por último el modprobe. **¡Si hay un error no sigas!.**

Bueno, ahí vamos, a ver que pasa. Empiezo y cuando aparece el primer error te aviso ;).

---

### Post by 53RG10 on 2011-11-15
No me queda claro si es un error, ante la duda:
> linux-source-3.0.0 # make SUBDIRS=drivers/media/video/cx23885 modules -j3
  CC [M]  drivers/media/video/cx23885/cx23885-alsa.o
  LD [M]  drivers/media/video/cx23885/cx23885.o
  Building modules, stage 2.
  MODPOST 2 modules
WARNING: "cx23885_risc_databuffer" [drivers/media/video/cx23885/cx23885.ko] undefined!
  CC      drivers/media/video/cx23885/altera-ci.mod.o
  CC      drivers/media/video/cx23885/cx23885.mod.o
  LD [M]  drivers/media/video/cx23885/altera-ci.ko
  LD [M]  drivers/media/video/cx23885/cx23885.ko

Saludos

---

### Post by alfredo_ on 2011-11-15
Hola

Es una advertencia, pero ami también me paso y no recuerdo como lo solucione.
Dejame pensar y mañana te respondo.
No sigas, porque si mi memoria no me falla te va a colgar la pc al cargar el controlador.

Aguantame que  lo recuerde.

Proba a reemplazar cx23885-core.c también y ejecuta:
make SUBDIRS=drivers/media/video/cx23885 modules -j3

de nuevo, creo que con eso se soluciona.


Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-15
> **alfredo_ said:**
> Hola
Es una advertencia, pero ami también me paso y no recuerdo como lo solucione.
Dejame pensar y mañana te respondo.
No sigas, porque si mi memoria no me falla te va a colgar la pc al cargar el controlador.
Aguantame que  lo recuerde.

OK. Por las dudas te aclaro que el archivo al que hace mención (cx23885.ko) todavía no lo copié de los archivos que me diste vos a esa carpeta.
Saludos

EDICIÓN: Perdón, me equivoqué, no lo copié de la otra carpeta a esa. No de los archivos que me diste vos, ahí no está.

---

### Post by 53RG10 on 2011-11-15
Casi se soluciona:
> linux-source-3.0.0 # make SUBDIRS=drivers/media/video/cx23885 modules -j3
  Building modules, stage 2.
  MODPOST 2 modules
WARNING: "cx23885_risc_databuffer" [drivers/media/video/cx23885/cx23885.ko] undefined!
  CC      drivers/media/video/cx23885/cx23885.mod.o
  LD [M]  drivers/media/video/cx23885/cx23885.ko 			 		

Saludos

---

### Post by alfredo_ on 2011-11-15
Hola



> **53RG10 said:**
> OK. Por las dudas te aclaro que el archivo al que hace mención (cx23885.ko) todavía no lo copié de los archivos que me diste vos a esa carpeta.
Saludos

EDICIÓN: Perdón, me equivoqué, no lo copié de la otra carpeta a esa. No de los archivos que me diste vos, así no está.

Mira el mensaje anterior que lo corregí.

El archivo cx23885.ko hay que pasarlo (copiarlo) a /lib/modules/3.0-xxxx/kernel/drivers/media/video/cx23885/

Lo que estamos haciendo con esto es reemplazar el antiguo controlado por uno nuevo que soporta nuestra placa de TV. Por las mosca hace respaldo del controlador original.

Creo que estamos muy cerca.

Saludos y lo seguimos mañana.

Alfredo

---

### Post by 53RG10 on 2011-11-15
> **alfredo_ said:**
> 
El archivo cx23885.ko hay que pasarlo (copiarlo) a /lib/modules/3.0-xxxx/kernel/drivers/media/video/cx23885/

Hecho eso quedó así:
```
linux-source-3.0.0 # make SUBDIRS=drivers/media/video/cx23885 modules -j3
  Building modules, stage 2.
  MODPOST 2 modules
WARNING: "cx23885_risc_databuffer" [drivers/media/video/cx23885/cx23885.ko] undefined!
```
Siento que de ayer a hoy avanzamos bastante, así que más que conforme, sobretodo por el tiempo que me dedicás. No me voy a cansar de agradecerte, aunque a lo mejor a vos te cansa que te agradezca, por eso voy a parar un poco.;)
Saludos y hasta mañana

---

### Post by alfredo_ on 2011-11-16
Hola

Creo que no fui claro o no me entendiste.

Primero hay que reemplazar el archivo cx23885-core.c que vos tenes por el que te envíe. Luego volver a ejecutar el comando make SUBDIRS=drivers/media/video/cx23885 modules -j3. Si el Warning persiste no lo copias a /lib/...  porque puede que se te cuelgue la máquina al reiniciar. Si el Warning desaparece, si lo copias y ejecutas como root modprobe ... o reinicias la pc, esto último es para que se cargue el controlador.

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-16
Hola> **alfredo_ said:**
> Hola
Primero hay que reemplazar el archivo cx23885-core.c que vos tenes por el que te envíe. Luego volver a ejecutar el comando make SUBDIRS=drivers/media/video/cx23885 modules -j3. Si el Warning persiste no lo copias a /lib/...  porque puede que se te cuelgue la máquina al reiniciar. 
Lo hice y así me dio nuevamente:
```
make SUBDIRS=drivers/media/video/cx23885 modules -j3
  Building modules, stage 2.
  MODPOST 2 modules
WARNING: "cx23885_risc_databuffer" [drivers/media/video/cx23885/cx23885.ko] undefined!
```Saludos

---

### Post by alfredo_ on 2011-11-16
Hola

No se porque te da ese error. Pero vamos a probar que no sea algo de basura vieja que haya quedado.

Como usuario root utiliza midnight commander (mc) y dirigite a /usr/src/.../cx23885/ (te das cuenta que estoy abreviando, la dirección, para no tener que escribir todo) y en esta carpeta con las teclas de cursor posicionate primero en cx23885-alsa.c y presiona la tecla F4 te va a abrir el editor, luego F2 para guardar y por último F10 para salir. Hace lo mismo con cx23885-core.c y cx23885.h. Con esto le estamos cambiando la fecha de modificación, lo cual obliga al compilador a reveer todo de nuevo.

Hecho esto ejecuta de nuevo la compilación del controlador:

make SUBDIRS=drivers/media/video/cx23885 modules -j3

Espero que no salga de nuevo este error.
En mi caso cuando me dio este error fue por un problema de que había mal unos espacios, pero como yo te mande los archivos no tendría que pasar, salvo que en el camino se hayan estropeado. Si falla de nuevo, adjunta estos 3 archivos que los voy a comparar con los mios para ver si se corrompierón.

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-16
Hola
Ya guardé los archivos de nuevo y ahora me sale este error:```
# make SUBDIRS=drivers/media/video/cx23885 modules -j3
  CC [M]  drivers/media/video/cx23885/cx23885-cards.o
  CC [M]  drivers/media/video/cx23885/cx23885-video.o
  CC [M]  drivers/media/video/cx23885/cx23885-vbi.o
drivers/media/video/cx23885/cx23885-vbi.c:88:12: error: declaración static de ‘cx23885_restart_vbi_queue’ después de una declaración que no es static
drivers/media/video/cx23885/cx23885.h:585:12: nota: la declaración previa de ‘cx23885_restart_vbi_queue’ estaba aquí
drivers/media/video/cx23885/cx23885-video.c: En la función ‘cx23885_flatiron_mux’:
drivers/media/video/cx23885/cx23885-video.c:466:53: error: ‘FLD_CH_SEL’ no se declaró aquí (primer uso en esta función)
drivers/media/video/cx23885/cx23885-video.c:466:53: nota: cada identificador sin declarar se reporta sólo una vez para cada función en el que aparece
drivers/media/video/cx23885/cx23885-cards.c:35:20: error fatal: xc4000.h: No existe el archivo o el directorio
compilación terminada.
make[1]: *** [drivers/media/video/cx23885/cx23885-vbi.o] Error 1
make[1]: *** Se espera a que terminen otras tareas....
make[1]: *** [drivers/media/video/cx23885/cx23885-video.o] Error 1
make[1]: *** [drivers/media/video/cx23885/cx23885-cards.o] Error 1
make: *** [_module_drivers/media/video/cx23885] Error 2

```

¿Te envío los archivos o era lo que esperabas?
Saludos

---

### Post by alfredo_ on 2011-11-16
Hola Sergio

> 

drivers/media/video/cx23885/cx23885-cards.c:35:20: error fatal: xc4000.h: No existe el archivo o el directorio


Esta es la única que esperaba. 
¿El archivo cx23885-vbi.c es el que vos tenías o es el que yo envíe?. Si es el que vos tenías reemplazalo por el que yo envíe.

Mientras tanto miro el código para ver si me doy cuenta de algo.

Tema aparte el editor de ubuntu, donde ahora estoy escribiendo se puso en ortografía en inglés, ¿sabes donde se vuelve a castellano? no veo en la página donde regresarlo al castellano 

Saludos,

Alfredo

---

### Post by alfredo_ on 2011-11-16
Hola 

Reemplaza también el archivo que te envío adjunto.

---

### Post by alfredo_ on 2011-11-16
> **alfredo_ said:**
> Hola 

Reemplaza también el archivo que te envío adjunto.


Grrr... no se adjunto.

---

### Post by 53RG10 on 2011-11-16
> **alfredo_ said:**
> Hola Sergio
Tema aparte el editor de ubuntu, donde ahora estoy escribiendo se puso en ortografía en inglés, ¿sabes donde se vuelve a castellano? no veo en la página donde regresarlo al castellano

Todo lo que sea idioma de Ubuntu, creo que está en "Configuración del sistema, Soporte de idiomas", y ahí pones el orden de idiomas que querés y aplicás a todo el sistema. Si no hay traducción para el primero, usa el segundo, y así sigue. No sé si será eso, tampoco soy muy experto.

> ¿El archivo cx23885-vbi.c es el que vos tenías o es el que yo envíe?. Si es el que vos tenías reemplazalo por el que yo envíe.Lo copié (no lo había copiado) y copié este también
> **alfredo_ said:**
> 
Reemplaza también el archivo que te envío adjunto.
El resultado ahora es el siguiente:
> # make SUBDIRS=drivers/media/video/cx23885 modules -j3
  CC [M]  drivers/media/video/cx23885/cx23885-cards.o
  CC [M]  drivers/media/video/cx23885/cx23885-video.o
  CC [M]  drivers/media/video/cx23885/cx23885-vbi.o
drivers/media/video/cx23885/cx23885-cards.c:35:20: error fatal: xc4000.h: No existe el archivo o el directorio
compilación terminada.
  CC [M]  drivers/media/video/cx23885/cx23885-core.o
  CC [M]  drivers/media/video/cx23885/cx23885-i2c.o
make[1]: *** [drivers/media/video/cx23885/cx23885-cards.o] Error 1
make[1]: *** Se espera a que terminen otras tareas....
make: *** [_module_drivers/media/video/cx23885] Error 2

---

### Post by alfredo_ on 2011-11-16
Bueno, creo que esta contra las cuerdas, dejame mirar ahora un poco que es lo que hay que anular y te lo paso en unos 15 min. + o -.

Si ubiesemos tenido el kernel 3.1 estarías ya con soporte. Pero bueno un poco más.

Aguardame.

---

### Post by alfredo_ on 2011-11-16
Utilizando midnight commander vas a tener que anular un controlador para otra tarjeta.

Solo tenes que agregar estos dos símbolos: **/*** donde te lo indique y este otro: ***/ . **Si son los símbolos de dividir y el de multiplicar.

En el archivo cx23885-card.c es necesario que encuentres lo que pongo en color y lo reemplaces por lo que pongo de bajo:

[COLOR=Red]#include "xc4000.h"[/COLOR]
/*#include "xc4000.h"*/



[COLOR=Red]    [CX23885_BOARD_LEADTEK_WINFAST_PXDVR3200_H_XC4000] = {
        .name        = "Leadtek Winfast PxDVR3200 H XC4000",
        .porta        = CX23885_ANALOG_VIDEO,
        .portc        = CX23885_MPEG_DVB,
        .tuner_type    = TUNER_XC4000,
        .tuner_addr    = 0x61,
        .radio_type    = TUNER_XC4000,
        .radio_addr    = 0x61,
        .input        = {{
            .type    = CX23885_VMUX_TELEVISION,
            .vmux    = CX25840_VIN2_CH1 |
                  CX25840_VIN5_CH2 |
                  CX25840_NONE0_CH3,
        }, {
            .type    = CX23885_VMUX_COMPOSITE1,
            .vmux    = CX25840_COMPOSITE1,
        }, {
            .type    = CX23885_VMUX_SVIDEO,
            .vmux    = CX25840_SVIDEO_LUMA3 |
                  CX25840_SVIDEO_CHROMA4,
        }, {
            .type    = CX23885_VMUX_COMPONENT,
            .vmux    = CX25840_VIN7_CH1 |
                  CX25840_VIN6_CH2 |
                  CX25840_VIN8_CH3 |
                  CX25840_COMPONENT_ON,
        } },
    },[/COLOR]

/*    [CX23885_BOARD_LEADTEK_WINFAST_PXDVR3200_H_XC4000] = {
        .name        = "Leadtek Winfast PxDVR3200 H XC4000",
        .porta        = CX23885_ANALOG_VIDEO,
        .portc        = CX23885_MPEG_DVB,
        .tuner_type    = TUNER_XC4000,
        .tuner_addr    = 0x61,
        .radio_type    = TUNER_XC4000,
        .radio_addr    = 0x61,
        .input        = {{
            .type    = CX23885_VMUX_TELEVISION,
            .vmux    = CX25840_VIN2_CH1 |
                  CX25840_VIN5_CH2 |
                  CX25840_NONE0_CH3,
        }, {
            .type    = CX23885_VMUX_COMPOSITE1,
            .vmux    = CX25840_COMPOSITE1,
        }, {
            .type    = CX23885_VMUX_SVIDEO,
            .vmux    = CX25840_SVIDEO_LUMA3 |
                  CX25840_SVIDEO_CHROMA4,
        }, {
            .type    = CX23885_VMUX_COMPONENT,
            .vmux    = CX25840_VIN7_CH1 |
                  CX25840_VIN6_CH2 |
                  CX25840_VIN8_CH3 |
                  CX25840_COMPONENT_ON,
        } },
    },*/




[COLOR=Red]        .subvendor = 0x107d,
        .subdevice = 0x6f39,
        .card       = CX23885_BOARD_LEADTEK_WINFAST_PXDVR3200_H_XC4000,
    }, {[/COLOR]


/*        .subvendor = 0x107d,
        .subdevice = 0x6f39,
        .card       = CX23885_BOARD_LEADTEK_WINFAST_PXDVR3200_H_XC4000,
    }, {*/



[COLOR=Red]case CX23885_BOARD_LEADTEK_WINFAST_PXDVR3200_H_XC4000:[/COLOR]
/*case CX23885_BOARD_LEADTEK_WINFAST_PXDVR3200_H_XC4000:*/
Todas las veces que aparece. 

Acordate, con F4 inicias edición, con las flechas te moves, con F2 guardas y con F10 salis.

Sigo mirando si hay que sacar algo, pero ya tenes para entretenerte. Si te resulta muy difícil me decis que lo edito yo y te lo envío.

Saludos

---

### Post by alfredo_ on 2011-11-16
Hola si se te complica acá van los archivos modificados, si no le erré tendría que salir todo funcionando.

Reemplazalos y volve a compilar.

---

### Post by 53RG10 on 2011-11-16
Me resultaba difícil así que los copié. Ahora por eso me salió error. Eso me pasa por no animarme, :D.
> # make SUBDIRS=drivers/media/video/cx23885 modules -j3
  CC [M]  drivers/media/video/cx23885/cx23885-cards.o
  CC [M]  drivers/media/video/cx23885/cx23885-dvb.o
  CC [M]  drivers/media/video/cx23885/cx23885-417.o
drivers/media/video/cx23885/cx23885-417.c: En la función ‘vidioc_querycap’:
drivers/media/video/cx23885/cx23885-417.c:1362:17: error: ‘CX23885_VERSION_CODE’ no se declaró aquí (primer uso en esta función)
drivers/media/video/cx23885/cx23885-417.c:1362:17: nota: cada identificador sin declarar se reporta sólo una vez para cada función en el que aparece
make[1]: *** [drivers/media/video/cx23885/cx23885-417.o] Error 1
make[1]: *** Se espera a que terminen otras tareas....
make: *** [_module_drivers/media/video/cx23885] Error 2


---

### Post by alfredo_ on 2011-11-16
Hola Este error no lo tenía, pero en mi configuración este dato no esta, por lo que te mando adjunto el archivo donde sale el error para que lo cambies por el tuyo.

---

### Post by 53RG10 on 2011-11-16
Por primera vez puedo decir... Ningún error :p:
> # make SUBDIRS=drivers/media/video/cx23885 modules -j3
  CC [M]  drivers/media/video/cx23885/cx23885-417.o
  CC [M]  drivers/media/video/cx23885/cx23885-ioctl.o
  CC [M]  drivers/media/video/cx23885/cx23885-ir.o
  CC [M]  drivers/media/video/cx23885/cx23885-av.o
  CC [M]  drivers/media/video/cx23885/cx23885-input.o
  CC [M]  drivers/media/video/cx23885/cx23888-ir.o
  CC [M]  drivers/media/video/cx23885/netup-init.o
  CC [M]  drivers/media/video/cx23885/cimax2.o
  CC [M]  drivers/media/video/cx23885/netup-eeprom.o
  CC [M]  drivers/media/video/cx23885/cx23885-f300.o
  CC [M]  drivers/media/video/cx23885/cx23885-alsa.o
  LD [M]  drivers/media/video/cx23885/cx23885.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      drivers/media/video/cx23885/cx23885.mod.o
  LD [M]  drivers/media/video/cx23885/cx23885.ko
Gracias.
¿Que me falta? ¿O ya puedo pasar al reemplazo del .ko que me faltaba y después al modprobe?

---

### Post by alfredo_ on 2011-11-16
> **53RG10 said:**
> Por primera vez puedo decir... Ningún error :p:
Gracias.
¿Que me falta? ¿O ya puedo pasar al reemplazo del .ko que me faltaba y después al modprobe?


¡¡¡¡¡¡¡ Chi, si ,sip,  !!!!!!!!!


Luego que se cargue hace en una consola el siguiente comando:

dmesg

Si tenemos suerte, tenes la placa funcionando.

MERDA

---

### Post by 53RG10 on 2011-11-16
> **alfredo_ said:**
> ¡¡¡¡¡¡¡ Chi, si ,sip,  !!!!!!!!!
Luego que se cargue hace en una consola el siguiente comando:
dmesg
Si tenemos suerte, tenes la placa funcionando.
MERDA

Bueno, por poco...
```
# modprobe cx23885
FATAL: Error inserting cx23885 (/lib/modules/3.0.0-12-generic/kernel/drivers/media/video/cx23885/cx23885.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```# dmesg | grep 23885
[   10.531321] cx23885: Unknown symbol snd_pcm_new (err 0)
[   10.531356] cx23885: Unknown symbol snd_pcm_format_physical_width (err 0)
[   10.531386] cx23885: Unknown symbol cx23885_risc_databuffer (err 0)
[   10.531417] cx23885: Unknown symbol snd_pcm_lib_ioctl (err 0)
[   10.531447] cx23885: Unknown symbol snd_pcm_hw_constraint_pow2 (err 0)
[   10.531454] cx23885: Unknown symbol snd_pcm_set_ops (err 0)
[   10.531524] cx23885: Unknown symbol snd_pcm_period_elapsed (err 0)
[ 1185.632705] cx23885: Unknown symbol cx23885_risc_databuffer (err 0)

---

### Post by alfredo_ on 2011-11-16
Aca ya no tengo ciencia.

Tirendome a la pileta, reinicia la pc a ver que pasa. La otra que se me ocurre es hacer lo que hicimos hoy con mc de entrar con F4 y guardar con F2 en todos los archivos y ver si da algún error.

Grrrrr...

---

### Post by 53RG10 on 2011-11-16
> **alfredo_ said:**
> Aca ya no tengo ciencia.
Tirendome a la pileta, reinicia la pc a ver que pasa. La otra que se me ocurre es hacer lo que hicimos hoy con mc de entrar con F4 y guardar con F2 en todos los archivos y ver si da algún error.
Grrrrr...

Mirá, hice eso sin errores. Pero me dí cuenta de algo, haciendo las compilaciones siempre fueron en la carpeta "linux-source-3.0.0", pero si mirás dónde salta el error, es la carpeta "linux-headers-3.0.0-12-generic", que es la única que aparece en el lib/...
¿Ahora te das cuenta por qué el error?
Saludos

EDITO: No sé si te acordás que esa carpeta estaba prácticamente vacía y era ahí donde yo copiaba los archivos que me diste al principio. Ahora están estos archivos en "linux-headers-3.0.0-12-generic":
cx23885 # dir
cx23885-alsa.c     cx23885-dvb.c    cx23885-video.c  Makefile
cx23885-cards.c  cx23885.h    Kconfig

---

### Post by alfredo_ on 2011-11-16
> **53RG10 said:**
> Mirá, hice eso sin errores. Pero me dí cuenta de algo, haciendo las compilaciones siempre fueron en la carpeta "linux-source-3.0.0", pero si mirás dónde salta el error, es la carpeta "linux-headers-3.0.0-12-generic", que es la única que aparece en el lib/...
¿Ahora te das cuenta por qué el error?
Saludos


Creo que lo que esta pasando es que las fuentes y kernel que se esta utilizando son distintos. Creo que es lo que me estás diciendo. Si es así hay que buscar la manera que sean iguales, sino no va a funcionar.
Para tener en cuenta:

linux-source-3.0.0
linux-headers-3.0.0-12-generic

los números tienen que ser iguales, en ambas partes. Acá Guillermo nos podría dar una mejor orientación.
Fijate si esta disponible algo que coincidan fuentes y kernel instalado o a instalar. 


Saludos

---

### Post by 53RG10 on 2011-11-16
Bueno, empecemos, no sé si te sirve a vos, pero a Guillermo me imagino que sí:

# ls -al /usr/src
```
total 24
drwxr-xr-x  6 root root 4096 2011-11-16 20:16 .
drwxr-xr-x 13 root root 4096 2011-11-14 18:59 ..
lrwxrwxrwx  1 root root   18 2011-11-15 11:47 linux -> linux-source-3.0.0
drwxr-xr-x 24 root root 4096 2011-11-15 11:57 linux-headers-3.0.0-12
drwxr-xr-x  7 root root 4096 2011-11-15 11:57 linux-headers-3.0.0-12-generic
drwxrwxr-x 27 root root 4096 2011-11-17 00:19 linux-source-3.0.0
lrwxrwxrwx  1 root root   45 2011-10-07 17:33 linux-source-3.0.0.tar.bz2 -> linux-source-3.0.0/linux-source-3.0.0.tar.bz2
drwxr-xr-x  7 root root 4096 2011-10-18 13:24 virtualbox-guest-4.1.2
```

# uname -r
3.0.0-12-generic

# lspci >lspci.txt
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4290]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:07.0 Communication controller: Intel Corporation 536EP Data Fax Modem
05:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
06:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
```

# dmesg | grep 23885
```
[    9.787942] cx23885: Unknown symbol snd_pcm_new (err 0)
[    9.787983] cx23885: Unknown symbol snd_pcm_format_physical_width (err 0)
[    9.797279] cx23885: Unknown symbol cx23885_risc_databuffer (err 0)
[    9.797323] cx23885: Unknown symbol snd_pcm_lib_ioctl (err 0)
[    9.797363] cx23885: Unknown symbol snd_pcm_hw_constraint_pow2 (err 0)
[    9.797372] cx23885: Unknown symbol snd_pcm_set_ops (err 0)
[    9.797456] cx23885: Unknown symbol snd_pcm_period_elapsed (err 0)
[  416.193901] cx23885: Unknown symbol cx23885_risc_databuffer (err 0)
[  594.071223] cx23885: Unknown symbol cx23885_risc_databuffer (err 0)
```
Saludos

---

### Post by alfredo_ on 2011-11-16
Ahora nos falta ver que en: /lib/modules/ tendría que haber algo así como lo que hay en /usr/src/

Ejemplo, si compilas en: 

/usr/src/linux-headers-3.0.0-12-generic

en /lib/modules/ tendrías que tener algo como esto:

/lib/modules/3.0.0-12-generic

¡Fijate que los números 3.0.0-12 tienen que estar en los dos!

Si esto no pasa el controlador no funcionará.

Hasta acá llego yo hoy, ponete en campaña para ver si conseguis lo que te estoy indicando, sino el esfuerzo es en vano. Si salvamos este punto tenemos el problema ganado, almenos eso creo.
Bueno espero que mañana cuando me vuelva a conectar tenga la sorpresa de que te esta funcionando.

Saludos,

Alfredo

---

### Post by alfredo_ on 2011-11-16
Por último para que veas y ejemplificar una vez más te paso lo que yo tengo

> dhcppc1:/usr/src # ls -al
total 28
drwxr-xr-x  7 root root 4096 nov  9 14:28 .
drwxr-xr-x 13 root root 4096 mar  2  2011 ..
lrwxrwxrwx  1 root root   13 nov  8 19:22 linux -> linux-3.1.0-3
drwxr-xr-x 24 root root 4096 nov 13 22:10 linux-3.1.0-3
drwxr-xr-x  3 root root 4096 nov  8 19:25 linux-3.1.0-3-obj
drwxr-xr-x  3 root root 4096 nov  9 14:29 linux-media
drwxr-xr-x  3 root root 4096 nov  4 04:50 linux-obj
drwxr-xr-x  8 root root 4096 mar  2  2011 packages


En linux-3.1.0-3 es donde estan mis fuentes para compilar.
Ahora lo que tengo en donde están los módulos que carga el kernel:

> dhcppc1:/lib/modules # ls -al
total 16
drwxr-xr-x  4 root root 4096 nov  8 23:15 .
drwxr-xr-x 13 root root 4096 nov 16 12:29 ..
drwxr-xr-x  4 root root 4096 nov  8 19:23 2.6.37.6-0.9-desktop
drwxr-xr-x  5 root root 4096 nov  8 19:25 3.1.0-3-desktop


Se ve que en ambos esta 3.1.0.-3

Bueno hasta mañana.

Alfredo

---

### Post by 53RG10 on 2011-11-17
Hola
La verdad es que intenté de todas las maneras, pero no puedo. Ahora instalé el kernel 3.1.1 para ver si podía, pero siempre me tira error cuando intento hacer los make. En el único que no me tira error es en el "linux-source-3.0.0", que es en el que yo lo había hecho todo, pero no aparece en el /lib/modules (Puse el código más abajo)
```
src # ls -al
total 36
drwxr-xr-x  9 root root 4096 2011-11-17 14:49 .
drwxr-xr-x 13 root root 4096 2011-11-14 18:59 ..
drwxr-xr-x 24 root root 4096 2011-11-17 14:17 linux-headers-3.0.0-12
drwxr-xr-x  7 root root 4096 2011-11-17 14:17 linux-headers-3.0.0-12-generic
drwxr-xr-x 23 root root 4096 2011-11-17 14:20 linux-headers-3.1.1-030101
drwxr-xr-x  7 root root 4096 2011-11-17 14:43 linux-headers-3.1.1-030101-generic
drwxrwxr-x 27 root root 4096 2011-11-17 00:25 linux-source-3.0.0
lrwxrwxrwx  1 root root   45 2011-10-07 17:33 linux-source-3.0.0.tar.bz2 -> linux-source-3.0.0/linux-source-3.0.0.tar.bz2
drwxr-xr-x 12 root root 4096 2011-11-17 00:45 virtualbox-4.1.2
drwxr-xr-x  7 root root 4096 2011-10-18 13:24 virtualbox-guest-4.1.2

```

```
modules # ls -al
total 16
drwxr-xr-x  4 root root 4096 2011-11-17 14:21 .
drwxr-xr-x 19 root root 4096 2011-11-15 16:02 ..
drwxr-xr-x  5 root root 4096 2011-11-17 00:46 3.0.0-12-generic
drwxr-xr-x  5 root root 4096 2011-11-17 14:22 3.1.1-030101-generic

```
Doy permiso de que me digan que ya está y que no moleste más :P. No me voy a enojar. Demasiada paciencia y horas me dedicaron.
Saludos

---

### Post by alfredo_ on 2011-11-17
Hola

**[COLOR=black]¡Yo no me desanimo, vos no te desanimás![/COLOR]**


¿Que error da con el kernel 3.1.1?

Fijate si en algún lado se puede descargar: linux-source-3.0.0-12 

Hay otra posibilidad pero tenes que estudiar un poco que es compliar el kernel que se deja e instalarlo. Esto es un poco distinto a lo que estamos haciendo, y tenes que asegurarte que almenos con algún kernel puedas bootear. Nos difícil, pero tampoco tan fácil.

Hasta el martes creo que no voy a poder asistirte por no diponer de tiempo, pero luego sigo en carrera con gusto, si vos lo deseas.

Estamos muy cerca de que funcione, el problema que estamos teniendo es que la distribución te estadando algo sin probar (fuentes del kernel) o estas cometiendo un error que no vemos.
Tabién podrías consultar en algún lado sobre compilación del kernel, quizás allí te den una solución fácil, para luego si poder hacer nuestra parte.

Saludos y ánimo, 

Alfredo

---

### Post by 53RG10 on 2011-11-17
Hola
Jaja. No hay problema, yo no me desanimo, pero tampoco quiero volverlos locos por una placa. ;)
En cuanto a los errores es que quise empezar a hacer lo mismo de antes:
```
# make clean -j3
ls: no se puede acceder a /usr/src/linux-headers-3.1.1-030101-generic/Documentation/DocBook/media/*.b64: No existe el archivo o el directorio
  CLEAN   .tmp_versions

```
Y quise bajarme el mismo kernel que ya tenía pero no lo encontré en ningún lado. Por eso me bajé el 3.1
Saludos

---

### Post by alfredo_ on 2011-11-17
Hola

No estoy seguro, pero creo que lo que vas a tener que baja es algo así como: 

linux-source-3.1.1.0030101

---

### Post by alfredo_ on 2011-11-19
Hola

Guillermo, acordate que en el lugar donde tengas las fuentes del kernel hay muchos archvos, fijate en la carpeta /.../cx23886 que tienen que estar los que ya conoces. Si no los ves no te molestes en compilar, porque va a fallar.

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-20
Hola
Tanto querer compilar, se ve que toqué algo que no debería haber tocado y nunca más lo pude hacer arrancar. :(
Igual no importa, ahora estoy con poco tiempo porque tengo una semana de exámenes, pero después voy a empezar todo de cero y tratar de compilar como corresponde informándome mejor, ya que me interesa el tema.
Agradezco la ayuda de ambos y espero que estén dentro de unos días cuando vuelva a la carga. No voy a parar hasta que el tema del post esté solucionado. :D
Saludos

---

### Post by alfredo_ on 2011-11-23
Hola Sergio

He instalado Kubuntu, y he podido compilar e instalar el controlador sin mayores problemas, cuando estés de nuevo te paso como lo hice. La placa funciona bien y con el kernel 3.0.0-13.
El archivo cx23885.ko que se genera es muy grande, aún comprimido, para poder ponerlo aquí. Por lo que te toca seguir compilando.

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-23
Hola
Gracias, lo único que estuve haciendo estos días es probar diferentes distros. La de linux mint 12 que había probado no me había dado cuenta que era RC, y por lo tanto tenía varios problemas aún. Después probé Debian directamente, pero no me toma el módem USB ADSL que tengo, y no tengo ganas de andar probando algo que me volví loco para entender como andaba en Mint :).
Así que voy a hacer lo siguiente creo, tengo exámen mañana jueves, por eso a partir de mañana empezaré por instalar Linux Mint 11, e instalar un kernel a partir de los 3.0, según cuál me digas vos.
Si querés, cuando veas este mensaje, decíme por donde empiezo, haciendo de cuenta que ya instalé Llinux Mint 11 (que si no me equivoco tiene kernel anterior a 3). Así cuando vuelva a entrar al foro ya te digo cómo me fue.
Saludos

Sergio

P.D. Como dije en uno de los mensajes anteriores, hasta que no la saque andando no paro. :)

---

### Post by 53RG10 on 2011-11-23
Hola de nuevo
Todavía no es seguro que instale el Mint, porque estuve probando un KDE  (que no sabía cuál era la diferencia) y la verdad es que me gustó mucho  más que el Gnome (también estuve viendo fotos en internet).
Yo pensé que  el Kubuntu era una versión más liviana o algo así, pero no.
Me la estoy  bajando para probarla y me parece que con esta me quedo.
Igualmente creo que no te cambia nada, ¿no?, porque sigue siendo basada en Ubuntu.
¡¡¡Cada día que pasa me gusta más Linux!!! :P
Y ni te cuento el día que haga andar la placa gracias a vos :P
Saludos

---

### Post by alfredo_ on 2011-11-23
Hola voy a resumir lo que hice para que te sirva de guía.
 

 
[LIST=1]
[*]Instalé el gestor de descargas     Synaptic.
[*]Ejecuté este programa y busqué     los kernel disponibles.
[*]Había disponibles 3.0.0-13.15, yo     tenía el 3.0.0-12
[*]Actualicé de la versión 3.0.0-12     a 3.0.0-13 e instalé linux-source y linux-source-3.0.0
[*]Se instalaron algunos otros     programas como por ejemplo gcc.
[*]Las fuentes del kernel se     instalaron en /usr/src/linux-source-3.0.0/linux-source-3.0.0 luego     de descomprimir /usr/src/linux-source-3.0.0.tar.bz2
[*]Abrí Konsole y me identifiqué     como root (sudo su) y me posicione en     /usr/src/linux-source-3.0.0/linux-source-3.0.0
[*]Ejecuté los siguientes comandos:     make clean, make oldconfig y make (no te olvides de poner -j3 al     final de cada comando para que utilicé la PC todos sus núcleos)
[*]Reemplace los archivos que he     puesto en la página y ejecuté: make     SUBDIRS=drivers/media/video/cx23885 modules -j3
[*]Luego reemplace el archivo     /usr/src/linux-source-3.0.0/linux-source-3.0.0/     drivers/media/video/cx23885/cx23885.ko en     /lib/modules/3.0.0-13-generic/kernel/drivers/media/video/cx23885/cx23885.ko
[*]Reinicié el sistema operativo y     listo
[/LIST]
 

 Si te llega a dar algún error no hay que seguir, hay que preguntar.
 Te recuerdo que he instalado Kubuntu 11.10.
 
Mer... con los exámenes. ¿De que materia son, si no es mucha indiscreción?

 Suerte,
 

 Alfredo

---

### Post by 53RG10 on 2011-11-24
> **alfredo_ said:**
> 
 Mer... con los exámenes. ¿De que materia son, si no es mucha indiscreción?
Suerte,
 
Hola, gracias.
Si te cuento de que materia son, te voy a tener que matar después... :).
No, en serio, empecé Tecnicatura en Programación Informática. Tengo 30 años, pero nunca es tarde si se tienen ganas de aprender ;).
El de hoy era de Química y parece que me fue bien, si es así, descanso hasta el año que viene. Ya había aprobado Matemática y Lengua.
Volviendo al tema, ya instalé Kubuntu, más adelante trataré de hacer lo de la lista, a ver que pasa esta vez.
Saludos

Sergio

---

### Post by 53RG10 on 2011-11-24
Hola
Hice todo esto:
> Instalé el gestor de descargas Synaptic.
Ejecuté este programa y busqué los kernel disponibles.
Instalé linux-source y linux-source-3.0.0
Acá donde no estoy seguro, porque a mí la carpeta linux-source-3.0.0 dentro de linux-source-3.0.0 que necesito para ejecutar los make adentro no está. A mí me aparece esto:

```
root@kubuntu:/usr/src# ls
linux-headers-3.0.0-12  linux-headers-3.0.0-12-generic  linux-source-3.0.0  linux-source-3.0.0.tar.bz2
root@kubuntu:/usr/src# cd linux-source-3.0.0
root@kubuntu:/usr/src/linux-source-3.0.0# ls
debian  debian.master  linux-source-3.0.0.tar.bz2
```¿Me falta algo o tengo que realizar los make dentro de la única carpeta linux-source-3.0.0 que yo tengo?

Saludos

---

### Post by alfredo_ on 2011-11-25
Hola

> **53RG10 said:**
> Hola
Hice todo esto:

Acá donde no estoy seguro, porque a mí la carpeta linux-source-3.0.0 dentro de linux-source-3.0.0 que necesito para ejecutar los make adentro no está. A mí me aparece esto:

```
root@kubuntu:/usr/src# ls
linux-headers-3.0.0-12  linux-headers-3.0.0-12-generic  linux-source-3.0.0  **linux-source-3.0.0.tar.bz2**
root@kubuntu:/usr/src# cd linux-source-3.0.0
root@kubuntu:/usr/src/linux-source-3.0.0# ls
debian  debian.master  linux-source-3.0.0.tar.bz2
```¿Me falta algo o tengo que realizar los make dentro de la única carpeta linux-source-3.0.0 que yo tengo?

Saludos

No me doy cuenta donde se descomprimierón las fuentes del kernel. Pero no hay problema, podemos rastrear donde están.

En muy factible que estén donde descomprimiste [B]linux-source-3.0.0.tar.bz2

[/B]Supongamos que no sabes donde están, no hay problema, busca dentro del direcotorio /usr/src donde están los archivos que tenemos que modificar (cx23885-dvd.c; cx23885-cards.c; etc.) y ese será el direcorio donde hay que compilar.

No estoy muy seguro, pero me parece que te falta descomprimir **linux-source-3.0.0.tar.bz2 **que lo tenes en **/usr/src/linux-source-3.0.0/** y luego de descomprimir te va a aparecer un nuevo directorio que sería algo así como: **/usr/src/linux-source-3.0.0/****linux-source-3.0.0/** y es quí donde hay que compilar.

Supongo que si haces un listado de lo que hay ahora en  **/usr/src/linux-source-3.0.0/** te quedaría algo así como esto:

root@kubuntu:/usr/src/linux-source-3.0.0# ls
debian  debian.master  linux-source-3.0.0  linux-source-3.0.0.tar.bz2


Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-25
Hola.
Hoy tengo un día ocupado.
Voy a ver si puedo hacer eso el fin de semana.
Saludos

---

### Post by 53RG10 on 2011-11-27
Holas y ¡¡¡buenísimas!!! :P.
Aunque no lo creas te vengo a mostrar lo siguiente:
```
# dmesg | grep 23885
[    9.004595] cx23885 driver version 0.0.3 loaded
[    9.008029] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.008192] CORE cx23885[0]: subsystem: 14f1:8502, board: Mygica X8507 [card=33,autodetected]
[    9.616963] cx25840 8-0044: cx23885 A/V decoder found @ 0x88 (cx23885[0])
[   10.250784] cx25840 8-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   10.387268] cx23885[0]: registered device video1 [v4l2]
[   10.387287] cx23885[0]: registered device vbi0
[   10.387366] cx23885[0]: registered ALSA audio device
[   12.436886] cx23885_dvb_register() allocating 1 frontend(s)
[   12.436889] cx23885[0]: cx23885 based dvb card
[   12.453055] DVB: registering new adapter (cx23885[0])
[   12.453279] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   12.453283] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 19, latency: 0, mmio: 0xfd400000
[   12.453290] cx23885 0000:03:00.0: setting latency timer to 64
# dmesg | grep xc5000
[   10.386519] xc5000 7-0061: creating new instance
[   10.387205] xc5000: Successfully identified at address 0x61
[   10.387206] xc5000: Firmware has not been loaded previously
[   10.392712] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   10.396406] xc5000: firmware read 12401 bytes.
[   10.396408] xc5000: firmware uploading...
[   11.764050] xc5000: firmware upload complete...
[   12.452334] xc5000 7-0061: attaching existing instance
[   12.453051] xc5000: Successfully identified at address 0x61
[   12.453052] xc5000: Firmware has been loaded previously
```Sabía que tenía que pasar. Y ya con esto estoy muy satisfecho, porque me costó bastante llegar a eso.
Ahora si no me equivoco, y revisando los mensajes de este tema, falta hacer algo.
Acá estoy cuando quieras y tengas tiempo.
Saludos y muchas gracias.

Sergio

P.D. Te mando el Dmesg completo por las dudas: ```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-13-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 (Ubuntu 3.0.0-13.22-generic 3.0.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=279eaa22-1f20-497d-9f55-056e86d03c14 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfdf0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfdf0000 - 00000000cfdf1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfdf1000 - 00000000cfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000110000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-890GPA-UD3H/GA-890GPA-UD3H, BIOS FF 11/24/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x110000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 base 000100000000 mask FFFFF0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] reg 4, base: 4GB, range: 256MB, type WB
[    0.000000] total RAM covered: 3326M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000cfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfdf0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f44e0] f44e0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfdf0000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfc00000 page 2M
[    0.000000]  00cfc00000 - 00cfdf0000 page 4k
[    0.000000] kernel direct mapping tables up to cfdf0000 @ cfded000-cfdf0000
[    0.000000] init_memory_mapping: 0000000100000000-0000000110000000
[    0.000000]  0100000000 - 0110000000 page 2M
[    0.000000] kernel direct mapping tables up to 110000000 @ 10fffe000-110000000
[    0.000000] RAMDISK: 359e8000 - 36cec000
[    0.000000] ACPI: RSDP 00000000000f5e80 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfdf1000 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000cfdf1080 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfdf1100 076BC (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfdf0000 00040
[    0.000000] ACPI: SSDT 00000000cfdf8880 0088C (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfdf9140 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfdf9180 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: MATS 00000000cfdf91c0 00034 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 00000000cfdf9230 00202 (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000cfdf87c0 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000110000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000110000000
[    0.000000]   NODE_DATA [000000010fff9000 - 000000010fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0003bfffff] PMD -> [ffff88010be00000-ffff88010effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00110000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfdf0
[    0.000000]     0: 0x00100000 -> 0x00110000
[    0.000000] On node 0 totalpages: 916863
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833064 pages, LIFO batch:31
[    0.000000]   Normal zone: 896 pages used for memmap
[    0.000000]   Normal zone: 64640 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfdf0000 - 00000000cfdf1000
[    0.000000] PM: Registered nosave memory: 00000000cfdf1000 - 00000000cfe00000
[    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88010fc00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 901626
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=279eaa22-1f20-497d-9f55-056e86d03c14 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 3450848k/4456448k available (6105k kernel code, 788996k absent, 216604k reserved, 4879k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 29360128 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3213.593 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6427.18 BogoMIPS (lpj=12854372)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004028] Security Framework initialized
[    0.004039] AppArmor: AppArmor initialized
[    0.004040] Yama: becoming mindful.
[    0.004352] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.005449] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.005933] Mount-cache hash table entries: 256
[    0.006032] Initializing cgroup subsys cpuacct
[    0.006036] Initializing cgroup subsys memory
[    0.006044] Initializing cgroup subsys devices
[    0.006045] Initializing cgroup subsys freezer
[    0.006047] Initializing cgroup subsys net_cls
[    0.006048] Initializing cgroup subsys blkio
[    0.006053] Initializing cgroup subsys perf_event
[    0.006074] tseg: 00cff00000
[    0.006075] CPU: Physical Processor ID: 0
[    0.006076] CPU: Processor Core ID: 0
[    0.006078] mce: CPU supports 6 MCE banks
[    0.006086] using AMD E400 aware idle routine
[    0.007172] ACPI: Core revision 20110413
[    0.012030] ftrace: allocating 25656 entries in 101 pages
[    0.020259] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059940] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 03
[    0.060003] Performance Events: AMD PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              48
[    0.060003] ... generic registers:      4
[    0.060003] ... value mask:             0000ffffffffffff
[    0.060003] ... max period:             00007fffffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000000000f
[    0.060003] Booting Node   0, Processors  #1
[    0.060003] smpboot cpu 1: start_ip = 9a000
[    0.148020] System has AMD C1E enabled
[    0.148032] Switch to broadcast mode on CPU1
[    0.148060]  #2
[    0.148061] smpboot cpu 2: start_ip = 9a000
[    0.240027] Switch to broadcast mode on CPU2
[    0.240067]  #3
[    0.240068] smpboot cpu 3: start_ip = 9a000
[    0.332034] Brought up 4 CPUs
[    0.332036] Total of 4 processors activated (25711.78 BogoMIPS).
[    0.332033] Switch to broadcast mode on CPU3
[    0.334416] Switch to broadcast mode on CPU0
[    0.334416] devtmpfs: initialized
[    0.334416] PM: Registering ACPI NVS region at cfdf0000 (4096 bytes)
[    0.334416] print_constraints: dummy: 
[    0.334416] Time: 13:54:50  Date: 11/27/11
[    0.334416] NET: Registered protocol family 16
[    0.334416] node 0 link 0: io port [9000, ffff]
[    0.334416] TOM: 00000000d0000000 aka 3328M
[    0.334416] Fam 10h mmconf [e0000000, e00fffff]
[    0.334416] node 0 link 0: mmio [a0000, bffff]
[    0.334416] node 0 link 0: mmio [d0000000, dfffffff]
[    0.334416] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.334416] node 0 link 0: mmio [e0000000, e06fffff] ==> [e0100000, e06fffff]
[    0.334416] TOM2: 0000000130000000 aka 4864M
[    0.334416] bus: [00, 06] on node 0 link 0
[    0.334416] bus: 00 index 0 [io  0x0000-0xffff]
[    0.334416] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.334416] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.334416] bus: 00 index 3 [mem 0xe0700000-0xffffffff]
[    0.334416] bus: 00 index 4 [mem 0xe0100000-0xe06fffff]
[    0.334416] bus: 00 index 5 [mem 0x130000000-0xfcffffffff]
[    0.334416] Extended Config Space enabled on 1 nodes
[    0.334416] ACPI: bus type pci registered
[    0.334416] Trying to unpack rootfs image as initramfs...
[    0.334416] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.334416] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.352265] PCI: Using configuration type 1 for base access
[    0.352699] bio: create slab <bio-0> at 0
[    0.352699] ACPI: EC: Look up EC in DSDT
[    0.357438] ACPI Warning: Incorrect checksum in table [TAMG] - 0x45, should be 0x44 (20110413/tbutils-314)
[    0.357530] ACPI: Interpreter enabled
[    0.357533] ACPI: (supports S0 S3 S4 S5)
[    0.357546] ACPI: Using IOAPIC for interrupt routing
[    0.505541] ACPI: No dock devices found.
[    0.505544] HEST: Table not found.
[    0.505546] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.505590] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.505666] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.505668] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.505669] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.505671] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.505673] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xfebfffff]
[    0.505684] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.505694] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.505721] pci 0000:00:01.0: [1022:9602] type 1 class 0x000604
[    0.505747] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
[    0.505768] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.505770] pci 0000:00:05.0: PME# disabled
[    0.505782] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
[    0.505802] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.505804] pci 0000:00:07.0: PME# disabled
[    0.505815] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    0.505836] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.505838] pci 0000:00:0a.0: PME# disabled
[    0.505861] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.505877] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    0.505884] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    0.505890] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    0.505897] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    0.505904] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    0.505911] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
[    0.505926] pci 0000:00:11.0: set SATA to AHCI mode
[    0.505958] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.505967] pci 0000:00:12.0: reg 10: [mem 0xfe02e000-0xfe02efff]
[    0.506017] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.506030] pci 0000:00:12.2: reg 10: [mem 0xfe02d000-0xfe02d0ff]
[    0.506080] pci 0000:00:12.2: supports D1 D2
[    0.506081] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.506084] pci 0000:00:12.2: PME# disabled
[    0.506099] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.506109] pci 0000:00:13.0: reg 10: [mem 0xfe02c000-0xfe02cfff]
[    0.506158] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.506172] pci 0000:00:13.2: reg 10: [mem 0xfe02b000-0xfe02b0ff]
[    0.506221] pci 0000:00:13.2: supports D1 D2
[    0.506222] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.506225] pci 0000:00:13.2: PME# disabled
[    0.506240] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.506290] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.506300] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.506307] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.506314] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.506321] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.506327] pci 0000:00:14.1: reg 20: [io  0xfa00-0xfa0f]
[    0.506353] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.506368] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
[    0.506409] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.506412] pci 0000:00:14.2: PME# disabled
[    0.506423] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.506476] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.506504] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.506514] pci 0000:00:14.5: reg 10: [mem 0xfe02a000-0xfe02afff]
[    0.506562] pci 0000:00:15.0: [1002:43a0] type 1 class 0x000604
[    0.506601] pci 0000:00:15.0: supports D1 D2
[    0.506621] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.506631] pci 0000:00:16.0: reg 10: [mem 0xfe029000-0xfe029fff]
[    0.506680] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.506694] pci 0000:00:16.2: reg 10: [mem 0xfe028000-0xfe0280ff]
[    0.506743] pci 0000:00:16.2: supports D1 D2
[    0.506744] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.506747] pci 0000:00:16.2: PME# disabled
[    0.506761] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.506772] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.506783] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.506793] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.506804] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.506837] pci 0000:01:05.0: [1002:9714] type 0 class 0x000300
[    0.506844] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.506848] pci 0000:01:05.0: reg 14: [io  0xce00-0xceff]
[    0.506851] pci 0000:01:05.0: reg 18: [mem 0xfdbe0000-0xfdbeffff]
[    0.506859] pci 0000:01:05.0: reg 24: [mem 0xfda00000-0xfdafffff]
[    0.506869] pci 0000:01:05.0: supports D1 D2
[    0.506877] pci 0000:01:05.1: [1002:970f] type 0 class 0x000403
[    0.506883] pci 0000:01:05.1: reg 10: [mem 0xfdbfc000-0xfdbfffff]
[    0.506903] pci 0000:01:05.1: supports D1 D2
[    0.506930] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.506933] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.506935] pci 0000:00:01.0:   bridge window [mem 0xfda00000-0xfdbfffff]
[    0.506938] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.506967] pci 0000:02:00.0: [1033:0194] type 0 class 0x000c03
[    0.506981] pci 0000:02:00.0: reg 10: [mem 0xfd7fe000-0xfd7fffff 64bit]
[    0.507033] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.507036] pci 0000:02:00.0: PME# disabled
[    0.512049] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.512053] pci 0000:00:05.0:   bridge window [io  0xb000-0xbfff]
[    0.512056] pci 0000:00:05.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.512059] pci 0000:00:05.0:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
[    0.512095] pci 0000:03:00.0: [14f1:8852] type 0 class 0x000400
[    0.512124] pci 0000:03:00.0: reg 10: [mem 0xfd400000-0xfd5fffff 64bit]
[    0.512234] pci 0000:03:00.0: supports D1 D2
[    0.512235] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    0.512241] pci 0000:03:00.0: PME# disabled
[    0.512269] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.512278] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.512281] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.512283] pci 0000:00:07.0:   bridge window [mem 0xfd400000-0xfd5fffff]
[    0.512286] pci 0000:00:07.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.512316] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
[    0.512327] pci 0000:04:00.0: reg 10: [io  0xde00-0xdeff]
[    0.512346] pci 0000:04:00.0: reg 18: [mem 0xfddff000-0xfddfffff 64bit pref]
[    0.512358] pci 0000:04:00.0: reg 20: [mem 0xfddf8000-0xfddfbfff 64bit pref]
[    0.512367] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.512393] pci 0000:04:00.0: supports D1 D2
[    0.512394] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.512397] pci 0000:04:00.0: PME# disabled
[    0.520051] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
[    0.520056] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.520058] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.520061] pci 0000:00:0a.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.520096] pci 0000:05:07.0: [8086:1040] type 0 class 0x000780
[    0.520114] pci 0000:05:07.0: reg 10: [mem 0xfcc00000-0xfcffffff]
[    0.520185] pci 0000:05:07.0: supports D2
[    0.520186] pci 0000:05:07.0: PME# supported from D2 D3hot D3cold
[    0.520190] pci 0000:05:07.0: PME# disabled
[    0.520214] pci 0000:05:0e.0: [104c:8024] type 0 class 0x000c00
[    0.520232] pci 0000:05:0e.0: reg 10: [mem 0xfd3ff000-0xfd3ff7ff]
[    0.520242] pci 0000:05:0e.0: reg 14: [mem 0xfd3f8000-0xfd3fbfff]
[    0.520305] pci 0000:05:0e.0: supports D1 D2
[    0.520306] pci 0000:05:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.520310] pci 0000:05:0e.0: PME# disabled
[    0.520336] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
[    0.520339] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.520342] pci 0000:00:14.4:   bridge window [mem 0xfcc00000-0xfd3fffff]
[    0.520345] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.520347] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.520349] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.520351] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.520352] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.520354] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xfebfffff] (subtractive decode)
[    0.520402] pci 0000:06:00.0: [197b:2363] type 0 class 0x000101
[    0.520481] pci 0000:06:00.0: reg 24: [mem 0xfd9fe000-0xfd9fffff]
[    0.520519] pci 0000:06:00.0: PME# supported from D3hot
[    0.520523] pci 0000:06:00.0: PME# disabled
[    0.520549] pci 0000:06:00.1: [197b:2363] type 0 class 0x000101
[    0.520570] pci 0000:06:00.1: reg 10: [io  0x9f00-0x9f07]
[    0.520582] pci 0000:06:00.1: reg 14: [io  0x9e00-0x9e03]
[    0.520594] pci 0000:06:00.1: reg 18: [io  0x9d00-0x9d07]
[    0.520605] pci 0000:06:00.1: reg 1c: [io  0x9c00-0x9c03]
[    0.520617] pci 0000:06:00.1: reg 20: [io  0x9b00-0x9b0f]
[    0.520679] pci 0000:06:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.520691] pci 0000:00:15.0: PCI bridge to [bus 06-06]
[    0.520694] pci 0000:00:15.0:   bridge window [io  0x9000-0x9fff]
[    0.520697] pci 0000:00:15.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.520701] pci 0000:00:15.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.520717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.520888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.520914] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.520955] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.520973] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.520991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.521010] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.521030]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.521032]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.521034] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.528350] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0
[    0.528377] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0
[    0.528401] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0
[    0.528425] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0
[    0.528448] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0
[    0.528472] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0
[    0.528495] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0
[    0.528518] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0
[    0.528590] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.528593] vgaarb: loaded
[    0.528594] vgaarb: bridge control possible 0000:01:05.0
[    0.528720] SCSI subsystem initialized
[    0.528739] libata version 3.00 loaded.
[    0.528739] usbcore: registered new interface driver usbfs
[    0.528739] usbcore: registered new interface driver hub
[    0.528739] usbcore: registered new device driver usb
[    0.528739] PCI: Using ACPI for IRQ routing
[    0.534976] PCI: pci_cache_line_size set to 64 bytes
[    0.534982] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    0.535058] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.535060] reserve RAM buffer: 00000000cfdf0000 - 00000000cfffffff 
[    0.535128] NetLabel: Initializing
[    0.535129] NetLabel:  domain hash size = 128
[    0.535130] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.535138] NetLabel:  unlabeled traffic allowed by default
[    0.535163] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.535166] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.537059] Switching to clocksource hpet
[    0.538782] Switched to NOHz mode on CPU #2
[    0.538787] Switched to NOHz mode on CPU #1
[    0.538792] Switched to NOHz mode on CPU #3
[    0.538795] Switched to NOHz mode on CPU #0
[    0.539876] AppArmor: AppArmor Filesystem Enabled
[    0.539892] pnp: PnP ACPI init
[    0.539902] ACPI: bus type pnp registered
[    0.539969] pnp 00:00: [bus 00-ff]
[    0.539971] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.539973] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.539974] pnp 00:00: [io  0x0d00-0xffff window]
[    0.539976] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.539977] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.539979] pnp 00:00: [mem 0xd0000000-0xfebfffff window]
[    0.540037] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.540044] pnp 00:01: [io  0x0010-0x001f]
[    0.540045] pnp 00:01: [io  0x0022-0x003f]
[    0.540047] pnp 00:01: [io  0x0044-0x005f]
[    0.540048] pnp 00:01: [io  0x0062-0x0063]
[    0.540049] pnp 00:01: [io  0x0065-0x006f]
[    0.540050] pnp 00:01: [io  0x0074-0x007f]
[    0.540051] pnp 00:01: [io  0x0091-0x0093]
[    0.540053] pnp 00:01: [io  0x00a2-0x00bf]
[    0.540054] pnp 00:01: [io  0x00e0-0x00ef]
[    0.540055] pnp 00:01: [io  0x04d0-0x04d1]
[    0.540056] pnp 00:01: [io  0x0220-0x0225]
[    0.540057] pnp 00:01: [io  0x0290-0x0294]
[    0.540098] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.540100] system 00:01: [io  0x0220-0x0225] has been reserved
[    0.540102] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.540104] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.602259] Freeing initrd memory: 19472k freed
[    0.644364] pnp 00:02: [io  0x4100-0x411f]
[    0.644367] pnp 00:02: [io  0x0228-0x022f]
[    0.644369] pnp 00:02: [io  0x040b]
[    0.644370] pnp 00:02: [io  0x04d6]
[    0.644371] pnp 00:02: [io  0x0c00-0x0c01]
[    0.644372] pnp 00:02: [io  0x0c14]
[    0.644373] pnp 00:02: [io  0x0c50-0x0c52]
[    0.644374] pnp 00:02: [io  0x0c6c-0x0c6d]
[    0.644375] pnp 00:02: [io  0x0c6f]
[    0.644377] pnp 00:02: [io  0x0cd0-0x0cd1]
[    0.644378] pnp 00:02: [io  0x0cd2-0x0cd3]
[    0.644379] pnp 00:02: [io  0x0cd4-0x0cdf]
[    0.644380] pnp 00:02: [io  0x4000-0x40fe]
[    0.644381] pnp 00:02: [io  0x4210-0x4217]
[    0.644382] pnp 00:02: [io  0x0b00-0x0b0f]
[    0.644383] pnp 00:02: [io  0x0b10-0x0b1f]
[    0.644385] pnp 00:02: [io  0x0b20-0x0b3f]
[    0.644386] pnp 00:02: [mem 0x00000000-0x00000fff window]
[    0.644388] pnp 00:02: [mem 0xfee00400-0xfee00fff window]
[    0.644394] pnp 00:02: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.644426] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:04:00.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.644473] system 00:02: [io  0x4100-0x411f] has been reserved
[    0.644476] system 00:02: [io  0x0228-0x022f] has been reserved
[    0.644477] system 00:02: [io  0x040b] has been reserved
[    0.644479] system 00:02: [io  0x04d6] has been reserved
[    0.644481] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.644483] system 00:02: [io  0x0c14] has been reserved
[    0.644484] system 00:02: [io  0x0c50-0x0c52] has been reserved
[    0.644486] system 00:02: [io  0x0c6c-0x0c6d] has been reserved
[    0.644487] system 00:02: [io  0x0c6f] has been reserved
[    0.644489] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.644490] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.644492] system 00:02: [io  0x0cd4-0x0cdf] has been reserved
[    0.644494] system 00:02: [io  0x4000-0x40fe] has been reserved
[    0.644495] system 00:02: [io  0x4210-0x4217] has been reserved
[    0.644497] system 00:02: [io  0x0b00-0x0b0f] has been reserved
[    0.644499] system 00:02: [io  0x0b10-0x0b1f] has been reserved
[    0.644500] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.644502] system 00:02: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.644505] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.644568] pnp 00:03: [dma 4]
[    0.644569] pnp 00:03: [io  0x0000-0x000f]
[    0.644570] pnp 00:03: [io  0x0080-0x0090]
[    0.644571] pnp 00:03: [io  0x0094-0x009f]
[    0.644573] pnp 00:03: [io  0x00c0-0x00df]
[    0.644591] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.644621] pnp 00:04: [io  0x0070-0x0073]
[    0.644631] pnp 00:04: [irq 8]
[    0.644651] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.644656] pnp 00:05: [io  0x0061]
[    0.644672] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.644677] pnp 00:06: [io  0x00f0-0x00ff]
[    0.644682] pnp 00:06: [irq 13]
[    0.644699] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.644873] pnp 00:07: [io  0x03f8-0x03ff]
[    0.644879] pnp 00:07: [irq 4]
[    0.644916] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.644936] pnp 00:08: [io  0x0060]
[    0.644937] pnp 00:08: [io  0x0064]
[    0.644943] pnp 00:08: [irq 1]
[    0.644965] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.644984] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    0.645019] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.645021] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.645114] pnp 00:0a: [mem 0x000cee00-0x000cffff]
[    0.645115] pnp 00:0a: [mem 0x000f0000-0x000f7fff]
[    0.645116] pnp 00:0a: [mem 0x000f8000-0x000fbfff]
[    0.645118] pnp 00:0a: [mem 0x000fc000-0x000fffff]
[    0.645119] pnp 00:0a: [mem 0xcfdf0000-0xcfdfffff]
[    0.645120] pnp 00:0a: [mem 0xffff0000-0xffffffff]
[    0.645121] pnp 00:0a: [mem 0x00000000-0x0009ffff]
[    0.645123] pnp 00:0a: [mem 0x00100000-0xcfdeffff]
[    0.645124] pnp 00:0a: [mem 0xcfe00000-0xcfefffff]
[    0.645125] pnp 00:0a: [mem 0xcff00000-0xcfffffff]
[    0.645127] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.645128] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.645129] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.645131] pnp 00:0a: [mem 0xfff80000-0xfffeffff]
[    0.645133] pnp 00:0a: disabling [mem 0x000cee00-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.645136] pnp 00:0a: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.645138] pnp 00:0a: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.645141] pnp 00:0a: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.645143] pnp 00:0a: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.645146] pnp 00:0a: disabling [mem 0x00100000-0xcfdeffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.645190] system 00:0a: [mem 0xcfdf0000-0xcfdfffff] could not be reserved
[    0.645192] system 00:0a: [mem 0xffff0000-0xffffffff] has been reserved
[    0.645194] system 00:0a: [mem 0xcfe00000-0xcfefffff] has been reserved
[    0.645196] system 00:0a: [mem 0xcff00000-0xcfffffff] could not be reserved
[    0.645198] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.645199] system 00:0a: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.645201] system 00:0a: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.645203] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.645216] pnp: PnP ACPI: found 11 devices
[    0.645217] ACPI: ACPI bus type pnp unregistered
[    0.650617] PCI: max bus depth: 1 pci_try_num: 2
[    0.650639] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.650642] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.650644] pci 0000:00:01.0:   bridge window [mem 0xfda00000-0xfdbfffff]
[    0.650646] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.650649] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.650651] pci 0000:00:05.0:   bridge window [io  0xb000-0xbfff]
[    0.650653] pci 0000:00:05.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.650656] pci 0000:00:05.0:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
[    0.650659] pci 0000:00:07.0: PCI bridge to [bus 03-03]
[    0.650660] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.650663] pci 0000:00:07.0:   bridge window [mem 0xfd400000-0xfd5fffff]
[    0.650665] pci 0000:00:07.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.650670] pci 0000:04:00.0: BAR 6: assigned [mem 0xfdd00000-0xfdd1ffff pref]
[    0.650672] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
[    0.650673] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.650676] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.650678] pci 0000:00:0a.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.650681] pci 0000:00:14.4: PCI bridge to [bus 05-05]
[    0.650683] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.650687] pci 0000:00:14.4:   bridge window [mem 0xfcc00000-0xfd3fffff]
[    0.650690] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.650695] pci 0000:00:15.0: PCI bridge to [bus 06-06]
[    0.650697] pci 0000:00:15.0:   bridge window [io  0x9000-0x9fff]
[    0.650700] pci 0000:00:15.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.650703] pci 0000:00:15.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.650721] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.650723] pci 0000:00:05.0: setting latency timer to 64
[    0.650732] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.650734] pci 0000:00:07.0: setting latency timer to 64
[    0.650743] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.650745] pci 0000:00:0a.0: setting latency timer to 64
[    0.650752] pci 0000:00:15.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.650755] pci 0000:00:15.0: setting latency timer to 64
[    0.650758] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.650760] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.650761] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.650763] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.650764] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.650766] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.650767] pci_bus 0000:01: resource 1 [mem 0xfda00000-0xfdbfffff]
[    0.650769] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.650771] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.650772] pci_bus 0000:02: resource 1 [mem 0xfd700000-0xfd7fffff]
[    0.650774] pci_bus 0000:02: resource 2 [mem 0xfd600000-0xfd6fffff 64bit pref]
[    0.650776] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.650777] pci_bus 0000:03: resource 1 [mem 0xfd400000-0xfd5fffff]
[    0.650779] pci_bus 0000:03: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.650780] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.650782] pci_bus 0000:04: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.650784] pci_bus 0000:04: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.650785] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    0.650787] pci_bus 0000:05: resource 1 [mem 0xfcc00000-0xfd3fffff]
[    0.650788] pci_bus 0000:05: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
[    0.650790] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.650791] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.650793] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.650794] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff]
[    0.650796] pci_bus 0000:05: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.650797] pci_bus 0000:06: resource 0 [io  0x9000-0x9fff]
[    0.650799] pci_bus 0000:06: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.650800] pci_bus 0000:06: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.650832] NET: Registered protocol family 2
[    0.650942] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.651775] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.653796] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.654044] TCP: Hash tables configured (established 524288 bind 65536)
[    0.654046] TCP reno registered
[    0.654053] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.654077] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.654185] NET: Registered protocol family 1
[    0.654194] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.720122] pci 0000:01:05.0: Boot video device
[    0.720159] PCI: CLS 4 bytes, default 64
[    0.721600] PCI-DMA: Disabling AGP.
[    0.721671] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.721672] PCI-DMA: using GART IOMMU.
[    0.721674] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.724795] audit: initializing netlink socket (disabled)
[    0.724804] type=2000 audit(1322402089.720:1): initialized
[    0.745456] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.759916] VFS: Disk quotas dquot_6.5.2
[    0.759957] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.760385] fuse init (API version 7.16)
[    0.760438] msgmni has been set to 6906
[    0.760799] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.760829] io scheduler noop registered
[    0.760830] io scheduler deadline registered
[    0.760856] io scheduler cfq registered (default)
[    0.761031] pcieport 0000:00:05.0: setting latency timer to 64
[    0.761059] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    0.761138] pcieport 0000:00:07.0: setting latency timer to 64
[    0.761157] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    0.761227] pcieport 0000:00:0a.0: setting latency timer to 64
[    0.761245] pcieport 0000:00:0a.0: irq 42 for MSI/MSI-X
[    0.761357] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.761373] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.761454] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.761458] ACPI: Power Button [PWRB]
[    0.761486] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.761489] ACPI: Power Button [PWRF]
[    0.761504] ACPI: acpi_idle registered with cpuidle
[    0.761523] ACPI: processor limited to max C-state 1
[    0.952612] ERST: Table is not found!
[    0.952658] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.973002] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.032621] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.032795] Linux agpgart interface v0.103
[    1.033426] brd: module loaded
[    1.033725] loop: module loaded
[    1.033895] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.033986] pata_acpi 0000:06:00.1: enabling device (0000 -> 0001)
[    1.033991] pata_acpi 0000:06:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.034008] pata_acpi 0000:06:00.1: setting latency timer to 64
[    1.034016] pata_acpi 0000:06:00.1: PCI INT B disabled
[    1.034285] Fixed MDIO Bus: probed
[    1.034301] PPP generic driver version 2.4.2
[    1.034327] tun: Universal TUN/TAP device driver, 1.6
[    1.034328] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.034379] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.034418] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.034438] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.034467] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.034474] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.034488] QUIRK: Enable AMD PLL fix
[    1.034496] ehci_hcd 0000:00:12.2: debug port 1
[    1.034519] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02d000
[    1.044067] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.044149] hub 1-0:1.0: USB hub found
[    1.044152] hub 1-0:1.0: 5 ports detected
[    1.044270] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.044280] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.044303] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.044309] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.044326] ehci_hcd 0000:00:13.2: debug port 1
[    1.044336] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe02b000
[    1.056066] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.056137] hub 2-0:1.0: USB hub found
[    1.056140] hub 2-0:1.0: 5 ports detected
[    1.056252] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.056262] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.056285] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.056292] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.056307] ehci_hcd 0000:00:16.2: debug port 1
[    1.056317] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe028000
[    1.068066] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.068136] hub 3-0:1.0: USB hub found
[    1.068139] hub 3-0:1.0: 4 ports detected
[    1.068199] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.068265] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.068276] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.068299] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.068322] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe02e000
[    1.128111] hub 4-0:1.0: USB hub found
[    1.128116] hub 4-0:1.0: 5 ports detected
[    1.128249] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.128259] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.128284] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.128297] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02c000
[    1.188119] hub 5-0:1.0: USB hub found
[    1.188124] hub 5-0:1.0: 5 ports detected
[    1.188256] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.188267] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.188290] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.188302] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe02a000
[    1.248113] hub 6-0:1.0: USB hub found
[    1.248118] hub 6-0:1.0: 2 ports detected
[    1.248236] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.248247] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.248268] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.248281] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe029000
[    1.308107] hub 7-0:1.0: USB hub found
[    1.308112] hub 7-0:1.0: 4 ports detected
[    1.308184] uhci_hcd: USB Universal Host Controller Interface driver
[    1.308228] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.308230] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.308343] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.308404] mousedev: PS/2 mouse device common for all mice
[    1.308471] rtc_cmos 00:04: RTC can wake from S4
[    1.308533] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.308555] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.308615] device-mapper: uevent: version 1.0.3
[    1.308657] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.308662] cpuidle: using governor ladder
[    1.308663] cpuidle: using governor menu
[    1.308664] EFI Variables Facility v0.08 2004-May-17
[    1.308806] TCP cubic registered
[    1.308881] NET: Registered protocol family 10
[    1.309196] NET: Registered protocol family 17
[    1.309206] Registering the dns_resolver key type
[    1.309267] PM: Hibernation image not present or could not be loaded.
[    1.309273] registered taskstats version 1
[    1.320636]   Magic number: 3:330:939
[    1.320717] rtc_cmos 00:04: setting system clock to 2011-11-27 13:54:51 UTC (1322402091)
[    1.320730] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
[    1.320756] powernow-k8:    0 : pstate 0 (3200 MHz)
[    1.320757] powernow-k8:    1 : pstate 1 (2500 MHz)
[    1.320758] powernow-k8:    2 : pstate 2 (2100 MHz)
[    1.320760] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.320980] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.320982] EDD information not available.
[    1.322133] Freeing unused kernel memory: 984k freed
[    1.322313] Write protecting the kernel read-only data: 10240k
[    1.322485] Freeing unused kernel memory: 20k freed
[    1.325897] Freeing unused kernel memory: 1396k freed
[    1.328919] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.338580] udevd[137]: starting version 173
[    1.355339] [drm] Initialized drm 1.1.0 20060810
[    1.355939] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.355958] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.356020] r8169 0000:04:00.0: setting latency timer to 64
[    1.356060] usb 1-2: new high speed USB device number 2 using ehci_hcd
[    1.356063] r8169 0000:04:00.0: irq 43 for MSI/MSI-X
[    1.356387] r8169 0000:04:00.0: eth0: RTL8168d/8111d at 0xffffc90000672000, 6c:f0:49:ec:94:5d, XID 083000c0 IRQ 43
[    1.362703] pata_jmicron 0000:06:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.362731] pata_jmicron 0000:06:00.1: setting latency timer to 64
[    1.362914] ahci 0000:00:11.0: version 3.0
[    1.362921] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.362970] ahci 0000:00:11.0: irq 44 for MSI/MSI-X
[    1.363038] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.363040] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.365011] scsi0 : pata_jmicron
[    1.365741] scsi1 : ahci
[    1.366881] scsi2 : pata_jmicron
[    1.366936] ata1: PATA max UDMA/100 cmd 0x9f00 ctl 0x9e00 bmdma 0x9b00 irq 17
[    1.366938] ata2: PATA max UDMA/100 cmd 0x9d00 ctl 0x9c00 bmdma 0x9b08 irq 17
[    1.367512] [drm] radeon defaulting to kernel modesetting.
[    1.367514] [drm] radeon kernel modesetting enabled.
[    1.367613] scsi3 : ahci
[    1.367668] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.367672] radeon 0000:01:05.0: setting latency timer to 64
[    1.367788] [drm] initializing kernel modesetting (RS880 0x1002:0x9714 0x1458:0xD000).
[    1.367808] [drm] register mmio base: 0xFDBE0000
[    1.367809] [drm] register mmio size: 65536
[    1.368206] ATOM BIOS: B43106_DVI
[    1.368223] radeon 0000:01:05.0: VRAM: 624M 0x00000000C0000000 - 0x00000000E6FFFFFF (624M used)
[    1.368225] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    1.370376] [drm] Detected VRAM RAM=624M, BAR=256M
[    1.370380] [drm] RAM width 32bits DDR
[    1.371008] scsi4 : ahci
[    1.371265] [TTM] Zone  kernel: Available graphics memory: 1769336 kiB.
[    1.371266] [TTM] Initializing pool allocator.
[    1.371294] [drm] radeon: 624M of VRAM memory ready
[    1.371296] [drm] radeon: 512M of GTT memory ready.
[    1.371313] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.371314] [drm] Driver supports precise vblank timestamp query.
[    1.371329] [drm] radeon: irq initialized.
[    1.371333] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.371961] [drm] Loading RS780 Microcode
[    1.371991] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.372079] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    1.372082] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.372130] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    1.372139] scsi5 : ahci
[    1.372215] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 44
[    1.372218] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 44
[    1.372220] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 44
[    1.372223] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 44
[    1.372351] xhci_hcd 0000:02:00.0: irq 17, io mem 0xfd7fe000
[    1.372397] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.372400] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
[    1.372404] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    1.372407] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[    1.372410] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
[    1.372526] xHCI xhci_add_endpoint called for root hub
[    1.372527] xHCI xhci_check_bandwidth called for root hub
[    1.372549] hub 8-0:1.0: USB hub found
[    1.372555] hub 8-0:1.0: 2 ports detected
[    1.372611] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.372633] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.373458] wmi: Mapper loaded
[    1.375789] xHCI xhci_add_endpoint called for root hub
[    1.375790] xHCI xhci_check_bandwidth called for root hub
[    1.375804] hub 9-0:1.0: USB hub found
[    1.375812] hub 9-0:1.0: 2 ports detected
[    1.375868] ahci 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.376245] scsi6 : pata_atiixp
[    1.376387] scsi7 : pata_atiixp
[    1.376752] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.376754] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    1.388057] ahci 0000:06:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.388061] ahci 0000:06:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.388066] ahci 0000:06:00.0: setting latency timer to 64
[    1.388304] scsi8 : ahci
[    1.388360] scsi9 : ahci
[    1.388389] ata9: SATA max UDMA/133 abar m8192@0xfd9fe000 port 0xfd9fe100 irq 17
[    1.388393] ata10: SATA max UDMA/133 abar m8192@0xfd9fe000 port 0xfd9fe180 irq 17
[    1.390764] radeon 0000:01:05.0: WB enabled
[    1.421704] [drm] ring test succeeded in 1 usecs
[    1.421778] [drm] radeon: ib pool ready.
[    1.421825] [drm] ib test succeeded in 0 usecs
[    1.421831] failed to evaluate ATIF got AE_BAD_PARAMETER
[    1.421967] [drm] Radeon Display Connectors
[    1.421968] [drm] Connector 0:
[    1.421969] [drm]   VGA
[    1.421970] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    1.421972] [drm]   Encoders:
[    1.421973] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    1.421974] [drm] Connector 1:
[    1.421974] [drm]   DVI-D
[    1.421975] [drm]   HPD1
[    1.421976] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    1.421977] [drm]   Encoders:
[    1.421979] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[    1.473596] [drm] Radeon display connector VGA-1: Found valid EDID
[    1.483042] [drm] Radeon display connector DVI-D-1: No monitor connected or invalid EDID
[    1.483057] [drm] radeon: power management initialized
[    1.555672] [drm] fb mappable at 0xD0141000
[    1.555673] [drm] vram apper at 0xD0000000
[    1.555674] [drm] size 5242880
[    1.555675] [drm] fb depth is 24
[    1.555676] [drm]    pitch is 5120
[    1.555714] fbcon: radeondrmfb (fb0) is primary device
[    1.555757] Console: switching to colour frame buffer device 160x64
[    1.555776] fb0: radeondrmfb frame buffer device
[    1.555777] drm: registered panic notifier
[    1.555782] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[    1.692095] ata5: SATA link down (SStatus 0 SControl 300)
[    1.696094] ata3: SATA link down (SStatus 0 SControl 300)
[    1.708119] ata9: SATA link down (SStatus 0 SControl 300)
[    1.724075] Refined TSC clocksource calibration: 3214.108 MHz.
[    1.724084] Switching to clocksource tsc
[    1.864067] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.864085] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.866092] ata4.00: ATA-8: WDC WD1002FAEX-007BA0, 05.01D05, max UDMA/133
[    1.866095] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.867550] ata4.00: configured for UDMA/133
[    1.867681] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1002FAEX-0 05.0 PQ: 0 ANSI: 5
[    1.867782] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    1.867811] sd 3:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.867843] sd 3:0:0:0: [sda] Write Protect is off
[    1.867845] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.867862] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.884081] ata10: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.887107] ata10.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN03, max UDMA/100
[    1.890928] ata10.00: configured for UDMA/100
[    1.902469] ata6.00: ATA-7: WDC WD1600AABS-61PRA0, 05.06H05, max UDMA/133
[    1.902472] ata6.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.903167] ata6.00: configured for UDMA/133
[    1.903266] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1600AABS-6 05.0 PQ: 0 ANSI: 5
[    1.903357] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    1.903368] sd 5:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.903414] sd 5:0:0:0: [sdb] Write Protect is off
[    1.903416] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.903434] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.906767] scsi 9:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN03 PQ: 0 ANSI: 5
[    1.908405]  sda: sda1 sda2 sda4 < sda5 sda6 sda7 sda8 >
[    1.908721] sd 3:0:0:0: [sda] Attached SCSI disk
[    1.914157]  sdb: sdb1
[    1.914363] sd 5:0:0:0: [sdb] Attached SCSI disk
[    1.915185] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.915187] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.915264] sr 9:0:0:0: Attached scsi CD-ROM sr0
[    1.915301] sr 9:0:0:0: Attached scsi generic sg2 type 5
[    1.916343] firewire_ohci 0000:05:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.972113] firewire_ohci: Added fw-ohci device 0000:05:0e.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.056020] usb 4-5: new full speed USB device number 2 using ohci_hcd
[    2.472117] firewire_core: created device fw0: GUID 00eb806d006cf049, S400
[    2.696406] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    2.736060] usb 5-1: new low speed USB device number 2 using ohci_hcd
[    3.192026] usb 5-2: new full speed USB device number 3 using ohci_hcd
[    3.332020] usb 5-2: device descriptor read/64, error -62
[    3.576058] usb 5-2: device descriptor read/64, error -62
[    3.816052] usb 5-2: new full speed USB device number 4 using ohci_hcd
[    3.956049] usb 5-2: device descriptor read/64, error -62
[    4.200046] usb 5-2: device descriptor read/64, error -62
[    4.440018] usb 5-2: new full speed USB device number 5 using ohci_hcd
[    4.848043] usb 5-2: device not accepting address 5, error -62
[    4.984044] usb 5-2: new full speed USB device number 6 using ohci_hcd
[    5.392042] usb 5-2: device not accepting address 6, error -62
[    5.392072] hub 5-0:1.0: unable to enumerate USB device on port 2
[    5.504065] usb 8-2: new low speed USB device number 2 using xhci_hcd
[    5.557961] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    5.570946] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    5.577971] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    5.579043] usb 8-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    8.874987] udevd[471]: starting version 173
[    8.893771] lp: driver loaded but no devices found
[    8.894866] Adding 999420k swap on /dev/sda6.  Priority:-1 extents:1 across:999420k 
[    8.895956] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[    8.895960] shpchp 0000:00:01.0: Cannot reserve MMIO region
[    8.896059] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.899231] Linux video capture interface: v2.00
[    8.902860] altera_stapl: module is from the staging directory, the quality is unknown, you have been warned.
[    8.907038] IR NEC protocol handler initialized
[    8.908061] IR RC5(x) protocol handler initialized
[    8.911497] IR RC6 protocol handler initialized
[    8.917004] IR JVC protocol handler initialized
[    8.920504] IR Sony protocol handler initialized
[    8.926016] lirc_dev: IR Remote Control driver registered, major 250 
[    8.926149] IR LIRC bridge handler initialized
[    8.930400] type=1400 audit(1322412899.104:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=611 comm="apparmor_parser"
[    8.930734] type=1400 audit(1322412899.104:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=611 comm="apparmor_parser"
[    8.930945] type=1400 audit(1322412899.104:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=611 comm="apparmor_parser"
[    8.944199] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    8.944631] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    8.944690] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[    8.953558] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.967481] MCE: In-kernel MCE decoding enabled.
[    8.968101] EDAC MC: Ver: 2.1.0
[    8.969774] AMD64 EDAC driver v3.4.0
[    8.998885] hda_codec: ALC892: BIOS auto-probing.
[    9.004595] cx23885 driver version 0.0.3 loaded
[    9.008029] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.008192] CORE cx23885[0]: subsystem: 14f1:8502, board: Mygica X8507 [card=33,autodetected]
[    9.172357] uvcvideo: Found UVC 1.00 device Vimicro USB Camera (Altair) (0ac8:3450)
[    9.174491] NET: Registered protocol family 8
[    9.174493] NET: Registered protocol family 20
[    9.174811] input: Vimicro USB Camera (Altair) as /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.0/input/input3
[    9.175039] usbcore: registered new interface driver uvcvideo
[    9.175040] USB Video Class driver (v1.1.0)
[    9.175310] [ueagle-atm] driver ueagle 1.4 loaded
[    9.175327] usb 4-5: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9021) Rev (0X500B): Eagle II
[    9.182235] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input4
[    9.182311] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:13.0-1/input0
[    9.221083] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[    9.222132] input: Sanmos TWIN SHOCK gamepad as /devices/pci0000:00/0000:00:05.0/0000:02:00.0/usb8/8-2/8-2:1.0/input/input5
[    9.222201] generic-usb 0003:11C0:5400.0002: input,hidraw1: USB HID v1.00 Joystick [Sanmos TWIN SHOCK gamepad] on usb-0000:02:00.0-2/input0
[    9.222215] usbcore: registered new interface driver usbhid
[    9.222217] usbhid: USB HID core driver
[    9.306242] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[    9.306510] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.306548] HDA Intel 0000:01:05.1: setting latency timer to 64
[    9.308047] usb 4-5: reset full speed USB device number 2 using ohci_hcd
[    9.333974] EDAC amd64: DRAM ECC disabled.
[    9.333985] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    9.333986]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    9.333987]  (Note that use of the override may cause unknown side effects.)
[    9.616963] cx25840 8-0044: cx23885 A/V decoder found @ 0x88 (cx23885[0])
[    9.721130] usb 4-5: [ueagle-atm] using iso mode
[    9.723145] usb 4-5: [ueagle-atm] (re)booting started
[    9.723161] usbcore: registered new interface driver ueagle-atm
[    9.871979] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   10.005159] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   10.250784] cx25840 8-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   10.359428] r8169 0000:04:00.0: eth0: link down
[   10.359812] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.365241] i2c-core: driver [tuner] using legacy suspend method
[   10.365243] i2c-core: driver [tuner] using legacy resume method
[   10.365413] tuner 7-0061: Tuner -1 found with type(s) Radio TV.
[   10.386519] xc5000 7-0061: creating new instance
[   10.387205] xc5000: Successfully identified at address 0x61
[   10.387206] xc5000: Firmware has not been loaded previously
[   10.387268] cx23885[0]: registered device video1 [v4l2]
[   10.387287] cx23885[0]: registered device vbi0
[   10.387366] cx23885[0]: registered ALSA audio device
[   10.392712] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   10.396406] xc5000: firmware read 12401 bytes.
[   10.396408] xc5000: firmware uploading...
[   11.421106] usb 4-5: [ueagle-atm] ATU-R firmware version : 44e2ea17
[   11.422096] usb 4-5: [Ueagle-atm] requesting firmware ueagle-atm/CMVep.bin.v2 failed, try to get older cmvs
[   11.423310] usb 4-5: [Ueagle-atm] use deprecated cmvs version, please update your firmware
[   11.458105] usb 4-5: [ueagle-atm] modem started, waiting synchronization...
[   11.764050] xc5000: firmware upload complete...
[   12.436886] cx23885_dvb_register() allocating 1 frontend(s)
[   12.436889] cx23885[0]: cx23885 based dvb card
[   12.451852] mb86a20s: mb86a20s_attach: 
[   12.452330] Detected a Fujitsu mb86a20s frontend
[   12.452334] xc5000 7-0061: attaching existing instance
[   12.453051] xc5000: Successfully identified at address 0x61
[   12.453052] xc5000: Firmware has been loaded previously
[   12.453055] DVB: registering new adapter (cx23885[0])
[   12.453057] DVB: registering adapter 0 frontend 0 (Fujitsu mb86A20s)...
[   12.453279] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   12.453283] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 19, latency: 0, mmio: 0xfd400000
[   12.453290] cx23885 0000:03:00.0: setting latency timer to 64
[   12.587588] ppdev: user-space parallel port driver
[   12.592975] type=1400 audit(1322412902.768:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1116 comm="apparmor_parser"
[   12.593346] type=1400 audit(1322412902.768:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1116 comm="apparmor_parser"
[   22.563135] usb 4-5: [ueagle-atm] modem operational
[   69.182195] usb 5-1: USB disconnect, device number 2
[   70.736049] usb 5-1: new low speed USB device number 7 using ohci_hcd
[   70.912296] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input7
[   70.912367] generic-usb 0003:093A:2510.0003: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:13.0-1/input0
[  130.239095] type=1400 audit(1322413020.412:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1166 comm="apparmor_parser"
[  130.239141] type=1400 audit(1322413020.412:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1169 comm="apparmor_parser"
[  130.239344] type=1400 audit(1322413020.412:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=1169 comm="apparmor_parser"
[  130.239411] type=1400 audit(1322413020.412:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1166 comm="apparmor_parser"
[  130.239553] type=1400 audit(1322413020.412:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1168 comm="apparmor_parser"
[  130.239609] type=1400 audit(1322413020.412:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1166 comm="apparmor_parser"
[  130.239650] type=1400 audit(1322413020.412:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1170 comm="apparmor_parser"
[  130.240300] type=1400 audit(1322413020.416:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1168 comm="apparmor_parser"
[  130.292899] init: apport pre-start process (1201) terminated with status 1
[  130.293004] init: alsa-restore main process (1210) terminated with status 99
[  130.302130] init: apport post-stop process (1233) terminated with status 1
[  130.342814] Bluetooth: Core ver 2.16
[  130.342833] NET: Registered protocol family 31
[  130.342835] Bluetooth: HCI device and connection manager initialized
[  130.342837] Bluetooth: HCI socket layer initialized
[  130.342838] Bluetooth: L2CAP socket layer initialized
[  130.342875] Bluetooth: SCO socket layer initialized
[  130.344369] Bluetooth: RFCOMM TTY layer initialized
[  130.344373] Bluetooth: RFCOMM socket layer initialized
[  130.344375] Bluetooth: RFCOMM ver 1.11
[  130.344448] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  130.344450] Bluetooth: BNEP filters: protocol multicast
[  130.732463] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[  131.001055] EXT4-fs (sda8): re-mounted. Opts: commit=0
[  131.173666] init: plymouth-stop pre-start process (1530) terminated with status 1
[  132.391281] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[  132.520553] EXT4-fs (sda8): re-mounted. Opts: commit=0

```

---

### Post by alfredo_ on 2011-11-27
Hola

Muy bien, ya tienes soporte para tu placa de video.
En cuanto a un mensaje tuyo anterior, te comento que nunca es tarde para estudiar. Puede llegar a parecer difícil y agotador, pero cuando uno lo mira con el conocimiento aprendido se da cuenta de que no era tanto.
Espero que te recibas, que hayas aprobados tus exámenes y que empieces a estudiar C++ para que me ayudes a entender el código y así darle soporte a lo que falta de esta placa.

No hace falta nada más ya esta funcionando tu placa. Eso sí ¿como hago para poder ver y escuchar?

Por ejemplo, en tu caso tendrás que hacer lo siguiente:

En una consola (Konsole) lanzar:

**tvtime -d /dev/video1**

Pero seguro que no escucharas nada, por lo que tendrás que lanzar en otro terminal el siguiente comando:

**arecord -D hw:3,0 -r 48000 -c 2 -f S16_LE | aplay -**

Es posible que tengas que cambiar hw:3,0 por hw:2,0
Este hw:3,0 es el nuevo dispositivo de sonido que crea la placa de TV

Si te lees el man de TVTime vas a poder controlar el sonido por ejemplo modificando el volumen general.

Ahora viene mi "cacho de maldad", cada vez que cambies de kernel, vas a tener que compilar de nuevo con las fuentes de ese kernel. Y para se un poco más malo, no te va a hacer falta esto a partir del kernel 3.3 :P. Ayer me avisaron que a partir de ese kernel ya vendrá de serie el soporte.

Gran saludo,

Alfredo

---

### Post by alfredo_ on 2011-11-27
Hola 

Hoy te puse que tenias que saber cual es el dispositivo de sonido

> 

Pero seguro que no escucharas nada, por lo que tendrás que lanzar en otro terminal el siguiente comando:

**arecord -D hw:3,0 -r 48000 -c 2 -f S16_LE | aplay -**

Es posible que tengas que cambiar hw:3,0 por hw:2,0
Este hw:3,0 es el nuevo dispositivo de sonido que crea la placa de TV



Bueno, es simple tenes que ejecutar en un terminal el siguiente comando y te lo va a decir.

**arecord -l**

Esto es lo que yo obtengo en mi PC:

alfredo@dhcppc3:~> arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC889A Analog [ALC889A Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[B]card 3: CX23885 [Conexant CX23885], device 0: CX23885 Digital [CX23885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]
alfredo@dhcppc3:~> 

Es por eso que yo pongo hw:3,0. Lo he puesto en negrita para que resalte y te des cuenta facilmente.
Cuando inicies la TV si no escuchas sonido, anda levantando de apoco los controles de volumen del mezcaldor de sonido (por ejemplo Kmix, alsamixer o lo que utilices).

Bueno espero más buenas noticias de parte tuya.

Alfredo

---

### Post by alfredo_ on 2011-11-27
Para que vayas practicando puedes grabar tu programa favorito de tv con por ejemplo el siguiente comando:

mencoder -noodml -tv driver=v4l2:device=/dev/video1:input=0:normid=8:[COLOR=Blue]freq=199,25[/COLOR]:amode=1:width=720:height=568:fps=25.0:[COLOR=Blue]alsa:adevice=hw.3,0[/COLOR]:amode=1:audiorate=48000:forceaudio:volume=100 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf harddup,pp=lb -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:acodec=mp2:abitrate=256:aspect=4/3 -ofps 25 [COLOR=Blue]-endpos 01:30:00[/COLOR] -o /home/alfredo/miprograma.mpeg


donde [COLOR=Blue]freq=199,25[/COLOR] es la frecuencia del canal que quieres que sintonice la placa y [COLOR=Blue]-endpos 01:30:00[/COLOR] es la cantidad de tiempo que quieres que grabe, en este caso una hora y media. He coloreado la sentencia para que lo encuentres fácilmente, no va en colores en la instrucción normal.
Ojo que si haces copy y paste que no se te corte la sentencia.

Es más si deseas que se grabe algo cuando no estás simplemente configuras el bios para que prenda la pc a la hora que quieras y luego configuras cron para que ejecute el comando anterior a la hora que lo desees y luego apage la pc. 

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-27
Hola
Sonaba demasiado fácil
Así estamos:
```
tvtime -d /dev/video1
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /root/.tvtime/tvtime.xml
No protocol specified
xcommon: Cannot open display ':0'.
```
¿¿¿???

En cuanto a lo del estudio, es más probable que primero aparezca el driver correspondiente a que yo aprenda a programar :)
Saludos

---

### Post by alfredo_ on 2011-11-27
Hola

¿Provaste la otra manera que indique en uno de los primeros mensajes?

mplayer tv://$channel -tv  driver=v4l2:device=/dev/video1:width=720:height=568:chanlist=us-bcast:alsa:adevice=hw.3,0:amode=1:audiorate=48000:   forceaudio:volume=100:immediatemode=0:norm=PAL-Nc 

¿Y con VLC probaste?

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-27
Me toma la cámara web y se me queda haciendo el famoso ruido de radio no sintonizada....

---

### Post by alfredo_ on 2011-11-27
Hola

> **53RG10 said:**
> Hola
Sonaba demasiado fácil
Así estamos:
```
tvtime -d /dev/video1
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /root/.tvtime/tvtime.xml
No protocol specified
xcommon: Cannot open display ':0'.
```¿¿¿???


Este es un problema con Xorg o el controlador de pantalla, no tiene nada que ver con la placa de tv, almenos eso creo.

Proba con xawtv, se te va a ver feo, pero es un principio, en general si amplias la ventana tirando de un extremo se mejora. 

Proba tambien el sonido.

Alfredo

---

### Post by alfredo_ on 2011-11-27
> **53RG10 said:**
> Me toma la cámara web y se me queda haciendo el famoso ruido de radio no sintonizada....

Se más claro, porque no entiendo lo que me indicas.
Poneme que comando estás utilizando, porque si usas xawtv -c /dev/video1 tendría que ver la tele, la otra es sacar la webcam, reiniciar y hacer las pruebas, luego que funcione mas o menos seguis con los problemas que aparezcan.

Saludos,

Alfredo

---

### Post by alfredo_ on 2011-11-28
Hola

> 
```
tvtime -d /dev/video1
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /root/.tvtime/tvtime.xml
No protocol specified
xcommon: Cannot open display ':0'.
```¿¿¿???
s

Creo que el problema es que puedes estar ejecutando TVTime como root, si es así da este error. ejecuta TVTime como el usuario que eres en una "konsola".

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-28
Hola
Justo entré para ver, e hice eso, entré como usuario común y ningún problema.
Ahora estoy haciendo un escaneo personalizado de canales (de la misma maner que como se abre el tvtime, tvtime-scanner -d /dev/video1). Mi pregunta es, ¿para que aparezca la placa en tvtime tengo que abrirlo siempre de esa manera?.
Ahora me queda ver lo del audio, después te cuento.
Saludos

---

### Post by alfredo_ on 2011-11-28
Hola

> **53RG10 said:**
> Hola
Justo entré para ver, e hice eso, entré como usuario común y ningún problema.
Ahora estoy haciendo un escaneo personalizado de canales (de la misma maner que como se abre el tvtime, tvtime-scanner -d /dev/video1). Mi pregunta es, ¿para que aparezca la placa en tvtime tengo que abrirlo siempre de esa manera?.
Ahora me queda ver lo del audio, después te cuento.
Saludos

Bueno ya puedes ver, es importante.
No estoy seguro de interpretar tu pregunta, pero si la idea es la de presionar en un ícono y que salga de una funcionando se hace de la siguiente manera:

Supongo que el escritorio es KDE.
Al igual que bajo windows, si presionas con el botón derecho del ratón sobre el menú lanzador de aplicaciones (el que esta abajo a la izquierda), una de las opciones que se abre en la ventanita emergene es "editar aplicaciones..." buscas la de TVTime y pones lo siguiente:

tvtime -d /dev/video1 -x /dev/mixer:pcm | arecord -D hw:3,0 -r 48000 -c 2 -f S16_LE | aplay -

donde: video1 es la placa de tv, si sacas la webcam pasa a ser video0. mixer:pcm le estas indicando que utilice la salida pcm para controlar el nivel de volumen, hw:3,0 la capturadora de sonido que crea la placa de tv.

También puedes ejecutar esto desde la linea de comandos (por ejemplo: Konsole)

Una vez que ya veas la tele, estudiate las opciones de TVTime y ajusta a tu gusto, por lo general solo hay que configurar la resolución (720) la entrada, el canal de sonido (esta disponible el SAP), la norma de televisión (pal-nc) y además yo le pongo que no ponga la pantalla en azul cuando no encuentra un canal.

Donde aparece la carita :p reemplazado por dos puntos ":" seguidos de la letra pe "p". Esto es porque lo reconoce como emoticon y no como texto plano.

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-28
Hola
Perdón, pero específicamente en qué parte del editor de aplicaciones escribo eso, ¿en algún lugar de la ficha general, o de la avanzado?
Gracias y perdón por seguir demostrando mi "ignorancia linuxera" :)
Me olvidé de aclararte lo del tema de que en los nuevos kernel ya va a venir incluído. No importa, si no lo hacía así, peleando, no lo disfrutaba. :P
Saludos

---

### Post by alfredo_ on 2011-11-28
Hola

> **53RG10 said:**
> Hola
Perdón, pero específicamente en qué parte del editor de aplicaciones escribo eso, ¿en algún lugar de la ficha general, o de la avanzado?
Gracias y perdón por seguir demostrando mi "ignorancia linuxera" :)
Me olvidé de aclararte lo del tema de que en los nuevos kernel ya va a venir incluído. No importa, si no lo hacía así, peleando, no lo disfrutaba. :P
Saludos

Supongo que ya te funciona bien, todo, sino es perder tiempo hacer esto.

> 
Supongo que el escritorio es KDE.
Al igual que bajo windows, si presionas con el botón derecho del ratón  sobre el menú lanzador de aplicaciones (el que esta abajo a la  izquierda), una de las opciones que se abre en la ventanita emergene es  "editar aplicaciones..." buscas la de TVTime y pones lo siguiente:

TVTime esta dentro de Multimedia --> TV --> Programa para ver la television TVTime y en el casillero que dice Orden pones lo que te indique. 
*Aclaración* con este comando te evitas tener que abrir una consola para ejecutar, pero el sonido no deja de sonar cuando se cierra la aplicación. Si queres no tener que hacer esto tendrás que ingeniartelas para agregar en este lanzador mplayer como lo explique en una carta anterior, ya en esto te toca a vos buscar.

**¡POR FAVOR DECIME SI YA VES Y ESCUCHAS CON LA PLACA!**

Saludos,

Alfredo

---

### Post by 53RG10 on 2011-11-28
Jajaja...  No te comenté lo más importante. A eso venía.
Me sintonizó los canales el TVTime sin ningún problema, pero no me aparece el audio.
Probé con lo siguiente y tampoco:
```
[sergio@sergio-GA-890GPA-UD3H:~$ mplayer tv://$channel -tv driver=v4l2:device=/dev/video1:width=720:height=568:chanlist=us-bcast:alsa:adevice=hw.3,0:amode=1:audiorate=48000: forceaudio:volume=100:immediatemode=0:norm=PAL-Nc 
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Mygica X8507
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilities:  video capture  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = NTSC-M; 1 = NTSC-M-JP; 2 = NTSC-443; 3 = PAL-BG; 4 = PAL-I; 5 = PAL-DK; 6 = PAL-M; 7 = PAL-N; 8 = PAL-Nc; 9 = PAL-60; 10 = SECAM-DK; 11 = SECAM-L;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video; 3 = Component;
 Current input: 0
 Current format: YUYV
v4l2: current audio mode is : STEREO
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0  57/ 57 ??% ??% ??,?% 0 0 
TV input is not seekable! (Seeking will probably be for changing channels ;)
V:   0.0  68/ 68 ??% ??% ??,?% 0 0 
TV input is not seekable! (Seeking will probably be for changing channels ;)
V:   0.0  88/ 88 ??% ??% ??,?% 0 0 
TV input is not seekable! (Seeking will probably be for changing channels ;)
V:   0.0 6578/6578 ??% ??% ??,?% 0 0 
No bind found for key 'MOUSE_BTN2'.
V:   0.0 6592/6592 ??% ??% ??,?% 0 0 
No bind found for key 'MOUSE_BTN0-MOUSE_BTN0_DBL'.
V:   0.0 6594/6594 ??% ??% ??,?% 0 0 
No bind found for key 'MOUSE_BTN0_DBL'.
V:   0.0 6690/6690 ??% ??% ??,?% 0 0 
v4l2: 6692 frames successfully processed, 7722 frames dropped.

Exiting... (Quit)
sergio@sergio-GA-890GPA-UD3H:~$ mplayer tv://$channel -tv driver=v4l2:device=/dev/video1:width=720:height=568:chanlist=us-bcast:alsa:adevice=hw.2,0:amode=1:audiorate=48000: forceaudio:volume=100:immediatemode=0:norm=PAL-Nc 
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Mygica X8507
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilities:  video capture  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = NTSC-M; 1 = NTSC-M-JP; 2 = NTSC-443; 3 = PAL-BG; 4 = PAL-I; 5 = PAL-DK; 6 = PAL-M; 7 = PAL-N; 8 = PAL-Nc; 9 = PAL-60; 10 = SECAM-DK; 11 = SECAM-L;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video; 3 = Component;
 Current input: 0
 Current format: YUYV
v4l2: current audio mode is : STEREO
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0 473/473 ??% ??% ??,?% 0 0 
v4l2: 475 frames successfully processed, 547 frames dropped.
Exiting... (Quit)

```

Por las dudas aclaro que mi placa está acá (por si me equivoco en algo, aunque creo que no):
```
arecord -l
**** Lista de CAPTURE dispositivos hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC892 Analog [ALC892 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: ALC892 Digital [ALC892 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: CX23885 [Conexant CX23885], dispositivo 0: CX23885 Digital [CX23885 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```Saludos

---

### Post by 53RG10 on 2011-11-28
No me preguntes por qué, pero probé de nuevo con el tvtime y ahora escucho... :D

tvtime -d /dev/video1
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /home/sergio/.tvtime/tvtime.xml
mixer: find error: Conseguido
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.

arecord -D hw:2,0 -r 48000 -c 2 -f S16_LE | aplay -
Grabación WAVE 'stdin' : Signed 16 bit Little Endian, Ratio 48000 Hz, Estéreo
Sonando WAVE 'stdin' : Signed 16 bit Little Endian, Ratio 48000 Hz, Estéreo

---

### Post by alfredo_ on 2011-11-28
**¡Bien, nos damos por hecho!.**

Ahora te toca a vos acomodar para que puedas lanzar todo desde un ícono. Ami eso no me molesta, por lo que siempre tengo abierto un terminal donde escribir alguna línea de comando.

En mi caso tiene un pequeño retardo entre el sonido y la imágen, usando mplayer esto no pasa, pero me gusta TVTime, por lo cual lo utlizo.

Igual voy a seguir mirando este tema, aunque no tan seguido. Voy a ver si puede seguir estudiando la placa y los controladores para poder mejorar, aunque lo mio es nada, la mayor parte la han hecho otros, yo solo hice pruebas sobre el trabajo de los de más y los acomode a esta placa. Ellos son los que tienen el conocimiento, yo solo puse un poco de paciencia y mucho de prueba y error.
Si llegas a saber de alguien que sepa de programación y quiera ayudar sería buenisimo, la parte de electrónica la puedo superar más facilmente, pero la de programación con todo el código no, dado que hay muchisimo y me resulta menos comprensible.

Saludos,

Alfredo

---

### Post by guillermolisi on 2011-11-28
Felicitaciones a ambos !!! Excelente thread !!

---

### Post by 53RG10 on 2011-11-28
> **guillermolisi said:**
> Felicitaciones a ambos !!! Excelente thread !!
:D
No te hagas el humilde que aportaste lo tuyo :).
Y yo fui el que más aportó... (confusión) :P
Saludos y estaré atento a ver si puedo encontrar a alguien con ganas (y conocimiento) de hacer andar la parte de sintonización digital.

---

### Post by alfredo_ on 2011-11-28
=D>

> **guillermolisi said:**
> Felicitaciones a ambos !!! Excelente thread !!

A ti también.

Saludos,

Alfredo

---

### Post by 53RG10 on 2012-02-13
Hola a todos
Revivo este tema porque quisiera saber si esta placa va a ser reconocida en el kernel 3.3.
Y si es así, ¿será completamente reconocida? ¿O sólo la parte analógica?
Pregunto, porque ví que está cercana la fecha de salida de este kernel, y quiero saber si vale la pena arriesgarme a instalarlo o no.
Saludos

---

### Post by alfredo_ on 2012-02-13
Hola Sergio

Solo va a soportar la parte analógica y solo lo correspondiente a la TV, no funka lo demás (TDA, radio, entradas de video y audio).
En el kernel 3.3 hay muchos cambios, por lo que voy a volver a la carga con la parte digital y hay unas personas que están trabajando en la parte de dar soporte a la radio para el chip cx23885. Si esto pasa y tengo un poco de suerte, tal vez funcione también la radio. Pero será con kernel más nuevos.
¿por qué esta como resuelto si aún falta mucho por hacer?
Saludos,
Alfredo

---

### Post by guillermolisi on 2012-02-13
> **alfredo_ said:**
> Hola Sergio

Solo va a soportar la parte analógica y solo lo correspondiente a la TV, no funka lo demás (TDA, radio, entradas de video y audio).
En el kernel 3.3 hay muchos cambios, por lo que voy a volver a la carga con la parte digital y hay unas personas que están trabajando en la parte de dar soporte a la radio para el chip cx23885. Si esto pasa y tengo un poco de suerte, tal vez funcione también la radio. Pero será con kernel más nuevos.
¿por qué esta como resuelto si aún falta mucho por hacer?
Saludos,
Alfredo

Tal vez esta con esa etiqueta por lo que se dice [en este post]("http://ubuntuforums.org/showpost.php?p=11496969&postcount=117")

---

### Post by 53RG10 on 2012-02-13
> **alfredo_ said:**
> Hola Sergio

Solo va a soportar la parte analógica y solo lo correspondiente a la TV, no funka lo demás (TDA, radio, entradas de video y audio).
En el kernel 3.3 hay muchos cambios, por lo que voy a volver a la carga con la parte digital y hay unas personas que están trabajando en la parte de dar soporte a la radio para el chip cx23885. Si esto pasa y tengo un poco de suerte, tal vez funcione también la radio. Pero será con kernel más nuevos.
¿por qué esta como resuelto si aún falta mucho por hacer?
Saludos,
Alfredo
Hola Alfredo, gracias por la respuesta.
¿Por qué cuesta tanto hacer andar la parte digital? La Kworld ub430 funciona desde Ubuntu 11.10, lo reconoce como "Fujitsu mb86A20s (DVB-T)"). Como yo no conozco, pregunto: ¿no se puede hacer nada al respecto? ¿o no tienen nada que ver una con la otra?
Saludos y perdón si mis preguntas no tienen mucho sentido :P

---

### Post by alfredo_ on 2012-02-15
Hola

> **53RG10 said:**
> Hola Alfredo, gracias por la respuesta.
¿Por qué cuesta tanto hacer andar la parte digital? La Kworld ub430 funciona desde Ubuntu 11.10, lo reconoce como "Fujitsu mb86A20s (DVB-T)"). Como yo no conozco, pregunto: ¿no se puede hacer nada al respecto? ¿o no tienen nada que ver una con la otra?
Saludos y perdón si mis preguntas no tienen mucho sentido :P

Te recuerdo que soy un metido más que un experto. En lo que es usb hay programas que permiten "usmear" lo que esta haciendo el dispositivo bajo Windows. En equipos con otro tipo de interface no esta tan desarrollado y lo que se puede ver es poco. Se requiere muchisimos conocimientos, talvez unas 50 personas en el planeta, como máximo, están capacitadas para hacer funcionar estos aparatos. Otros utilizamos sus trabajos para hacer lo que podemos. Los fabricantes no dan especificaciones, no solo el que hace la placa sino los que hacen los chips, con lo que podrás imaginar lo complicado que se pone la cosa. Y nuestra placa cumple con todos estos obstáculos. En esta nueva versión que esta por salir del kernel (3.3) hay hecho muchos cambios, talvez se pueda ver ya digital, pero no lo puedo asegurar, dado que no estoy al tanto de todos los cambios. Para que te des una idea las hojas de datos de los componentes que tiene nuestra placa no están disponibles (cx23885, xc5000 y mb86a20s), con prueba y error y comparando con otros chips es que han hecho los desarrolladores que algo funcione.
Lo que se puede hacer es insistir constantemente al fabricante para que ponga a disposición el controlador o las especificaciones (esto es casi imposible).
La forma en que se comunica el mb86a20s con el resto es lo que hace que no funcione por ahora en linux nuestra tarjeta, cambia de una placa de tv a otra y mas si el bus y el fabricante son distintos.
Espero haberte respondido a tu pregunta.
Saludos,

Alfredo

---

### Post by alfredo_ on 2012-02-15
Hola

> **guillermolisi said:**
> Tal vez esta con esa etiqueta por lo que se dice [en este post]("http://ubuntuforums.org/showpost.php?p=11496969&postcount=117")

Si, si se lee solo esa parte se puede entender como resuelto, pero si se comienza a leer desde el principio (primeros mensajes) se verá que la pregunta original es sobre la parte digital de la placa, la cual aún no funciona. Espero que pronto esto suceda. A parte de que faltan hacer funcionar otras partes analógicas como ser la radio.

Gracias por tu respuesta y si sabes o podes retirar la parte [solved] estaría bueno, dado que falta mucho por hacer y es probable que lleve mucho tiempo hasta que este realmente resuelto.

Saludos,

Alfredo

---

### Post by 53RG10 on 2012-02-15
> **alfredo_ said:**
> Hola

Te recuerdo que soy un metido más que un experto. En lo que es usb hay programas que permiten "usmear" lo que esta haciendo el dispositivo bajo Windows. En equipos con otro tipo de interface no esta tan desarrollado y lo que se puede ver es poco. Se requiere muchisimos conocimientos, talvez unas 50 personas en el planeta, como máximo, están capacitadas para hacer funcionar estos aparatos. Otros utilizamos sus trabajos para hacer lo que podemos. Los fabricantes no dan especificaciones, no solo el que hace la placa sino los que hacen los chips, con lo que podrás imaginar lo complicado que se pone la cosa. Y nuestra placa cumple con todos estos obstáculos. En esta nueva versión que esta por salir del kernel (3.3) hay hecho muchos cambios, talvez se pueda ver ya digital, pero no lo puedo asegurar, dado que no estoy al tanto de todos los cambios. Para que te des una idea las hojas de datos de los componentes que tiene nuestra placa no están disponibles (cx23885, xc5000 y mb86a20s), con prueba y error y comparando con otros chips es que han hecho los desarrolladores que algo funcione.
Lo que se puede hacer es insistir constantemente al fabricante para que ponga a disposición el controlador o las especificaciones (esto es casi imposible).
La forma en que se comunica el mb86a20s con el resto es lo que hace que no funcione por ahora en linux nuestra tarjeta, cambia de una placa de tv a otra y mas si el bus y el fabricante son distintos.
Espero haberte respondido a tu pregunta.
Saludos,

Alfredo
Hola Alfredo,
Gracias por tu respuesta, está mucho más claro el asunto para mí.
Lo que si sabía es que los fabricantes (o al menos la mayoría) se las hacen difícil a los programadores de Linux. Aunque tengo fe que de a poco vaya cambiando.
Yo cada tanto les mando un e-mail a los de Mygica para que liberen el driver que prometen hace más de una año. No creo que me presten atención (la única vez que me respondieron fue la primera), pero peor es no hacer nada.
Saludos

---

### Post by 53RG10 on 2012-05-14
Hola a todos nuevamente.
Sé que estas cosas llevan tiempo, pero escribo para saber si hay alguna novedad con respecto a esta placa y su funcionamiento en Linux. La parte analógica ningún problema, porque probé el kernel 3.3 y funciona, pero quería saber cómo estaba el tema de la parte digital, ¿se avanzó algo?
Gracias y perdón por se impaciente :)

Saludos

---

### Post by alfredo_ on 2012-06-06
Hola  No he podido avanzar porque hay cambios en la API que tengo que resolver con los kernel nuevos. ¿Te funciono bien con el kernel 3.3? Te pregunto porque a mi no, tengo que hacer un pequeño cambio para que se escuche y la imagén tiene el costado izquierdo con una franja verde y la imágen se achica u poco deformandoce. Esto por cambios que se hicierón para soportar VBI. Hay quente trabajando en esto dado que no es la única placa afectada.  Cuando logre saltar el primer inconveninte continuo.  Saludos.

---

### Post by 53RG10 on 2012-06-08
> **alfredo_ said:**
> Hola  No he podido avanzar porque hay cambios en la API que tengo que resolver con los kernel nuevos. ¿Te funciono bien con el kernel 3.3? Te pregunto porque a mi no, tengo que hacer un pequeño cambio para que se escuche y la imagén tiene el costado izquierdo con una franja verde y la imágen se achica u poco deformandoce. Esto por cambios que se hicierón para soportar VBI. Hay quente trabajando en esto dado que no es la única placa afectada.  Cuando logre saltar el primer inconveninte continuo.  Saludos.
Hola
Esta semana vendí la placa, así que ya no voy a poder ayudarte (o mejor dicho, no vas a poder ayudarme ;) ). Igualmente, le pasé el link al que se la vendí (también usa Linux, aunque no Ubuntu creo), en una de esas si le parece a él se comunicará.
Gracias por tu ayuda, fue muy útil en su momento.
Saludos y suerte con el reconocimiento de la placa

P.D. Igualmente, me voy a mantener informado, porque me gustaría que le encuentren la vuelta rápido a este asunto.

---

### Post by alfredo_ on 2012-06-13
Hola  > **53RG10 said:**
>  Esta semana vendí la placa, 

 Que mal...  Ahora en serio, ¿que paso que la vendistes?  Bueno espero que el nuevo adquiriente o como se escriba, se sume a esto de linux y ayude en su desarrollo. ¿Vas a comprar otra placa?  Saludos

---

### Post by 53RG10 on 2012-06-15
> **alfredo_ said:**
> Hola  
Que mal...  Ahora en serio, ¿que paso que la vendistes?  Bueno espero que el nuevo adquiriente o como se escriba, se sume a esto de linux y ayude en su desarrollo. ¿Vas a comprar otra placa?  Saludos
Sí, me costó venderla, pero me compré una PixelView USB y me anda perfecto. Pero era mucha plata para mí tener las 2, necesitaba venderla.
Se la vendí a un linuxero, así que espero que pueda ayudarte.
Saludos

---

### Post by alfredo_ on 2012-12-18
Hola

Por si alguien esta interesado, con el kernel 3.7 hay soporte completo para la parte de televisión analógica.
También esta disponible para su descarga los parches para que funcione el control remoto.
[[PATCH 1/2] Add RC support for MyGica X8507 - remote keytable definition -- Linux media]("http://www.spinics.net/lists/linux-media/msg56153.html") 
[[PATCH 2/2] Add RC support for MyGica X8507 - add support card -- Linux media]("http://www.spinics.net/lists/linux-media/msg56152.html") 
Y por si alguno esta interesado la radio también ya la he logrado hacer anda, aunque aún no lo he publicado porque hay parte del código que no es apto para un kernel definitivo, pero se puede escuchar la FM perfectamente.

Saludos

---

### Post by nrmmota on 2013-03-13
> **alfredo_ said:**
> Hola

Por si alguien esta interesado, con el kernel 3.7 hay soporte completo para la parte de televisión analógica.
También esta disponible para su descarga los parches para que funcione el control remoto.
[[PATCH 1/2] Add RC support for MyGica X8507 - remote keytable definition -- Linux media]("http://www.spinics.net/lists/linux-media/msg56153.html") 
[[PATCH 2/2] Add RC support for MyGica X8507 - add support card -- Linux media]("http://www.spinics.net/lists/linux-media/msg56152.html") 
Y por si alguno esta interesado la radio también ya la he logrado hacer anda, aunque aún no lo he publicado porque hay parte del código que no es apto para un kernel definitivo, pero se puede escuchar la FM perfectamente.

Saludos

Tienes la certeza de esto?

---

### Post by guillermolisi on 2013-03-13
Si Alfredo_ lo dice no me caben dudas de que asi es.

---

### Post by alfredo_ on 2013-03-16
> **nrmmota said:**
> Tienes la certeza de esto?

Hola nrmmota

Que gusto saber de que hay gente interesada en este controlador, lograr hacer andar algo cuando no tenes los conocimientos y hay que adquirirlos es tedioso y muy lento, pero si hay más de uno, te da un pogo de ganas extra.

No se a que parte te refieres si tengo certeza, pero todo lo que he puesto ha sido desarrollado por mi (en realidad copiado de otros controladores).
Si te refieres a la parte del control remoto, con instalar kernel 9 lo podrás usar, ojo viene desactivado, tendrás que activarlo, dado que en algunas tarjetas con el controlador cx23885 han encontrado que da fallo al kernel, por lo que los desarrolladores de V4L han optado por dejarlo desactivado al módulo de ir.
También puedes acceder a él bajando los últimos controladores utilizando git, si deseas utilizar este método sigue el siguiente enlace:
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

Si lo que deseas es hacer funcionar la radio, dime y pondré lo que hace falta. Te va tocar "emparchar" el kernel.

_Gracias_Guillermo_por_tus_palabras_._

Saludos,

Alfredo

---

### Post by alfredo_ on 2013-07-14
Hola

En el día de hoy he podido hacer funcionar por primera vez la parte digital con un kernel 3.2. :D

Por desgracia no funciona con kernel superiores, por lo que tengo que estudiar el problema. :(

Si alguno tiene ganas de jugar con esto avise que pongo los parches aquí para que puedan probar.

Adjunto una toma de pantalla donse se ve el escritorio KDE y VLC con la imágen de TV en HD (reduci el tamaño de la imágen para que suba rápido).

Saludos

---

### Post by alfredo_ on 2013-08-10
Hola

Gracias al trabajo de Mauro ahora es posible ver con cualquier kernel. En los enlaces de abajo están los parches a aplicar. Sino tendrán que esperar hasta la aparición de los kernels 3.12 o 3.13 en los cuales tendría que venir ya con ellos.

[https://linuxtv.org/patch/19653/](https://linuxtv.org/patch/19653/) 
[https://linuxtv.org/patch/19652/](https://linuxtv.org/patch/19652/) 
[https://linuxtv.org/patch/19654/](https://linuxtv.org/patch/19654/)

Como dato extra, estos controladores son más robustos que en windos, dado que no se cuelga el sintonizador cuando hay baja señal.

Espero poder poner pronto el parche para la radio así este tema queda cerrado.

Saludos

---

