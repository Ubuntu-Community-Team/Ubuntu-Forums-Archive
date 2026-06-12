---
title: "problema ubuntu server"
date: 2010-08-29
forum: Hardware
---

### Post by granjero on 2010-08-29
hola 

quise actualizar un servidor y me pasa lo siguiente

```
administrador@ZETA:~$ sudo aptitude update
E: No se pudo abrir /root/.aptitude/config para escribir en él - apt_init (30: Sistema de solo lectura)
W: No se utiliza bloqueos para el fichero de bloqueo de sólo lectura /var/lib/dpkg/lock
E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 
Error en el bus
administrador@ZETA:~$ sudo dpkg --configure -a
dpkg: no se puede acceder al área de estado de dpkg: Sistema de solo lectura
administrador@ZETA:~$ 

```

```
administrador@ZETA:~$ sudo aptitude safe-upgrade 
E: No se pudo abrir /root/.aptitude/config para escribir en él - apt_init (30: Sistema de solo lectura)
W: No se utiliza bloqueos para el fichero de bloqueo de sólo lectura /var/lib/dpkg/lock
E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Error en el bus

```


que le pasa¿

salud!

---

### Post by guillermolisi on 2010-08-29
El inconveniente mas raro es ese mensaje de "Error en el bus" que esta afectando tanto a Aptitude como a apt-get, ambos no utilizan las mismas estructuras basicas, solo se conjugan cuando utilizan dpkg.

Al momento no se me ocurre por que se da, nunca hasta ahora me ha pasado, ni con servers ni con desktop (que basicamente para el caso seria lo mismo).

Que dice Aptitude cuando lo inicias interactivamente ? ("sudo aptitude" a secas)

---

### Post by granjero on 2010-08-30
dejo de bootear...

tira una vomitada de errores que no me da ni tiempo de leer....

cuando trato de bootear en recovery mode pareciera estar todo ok....

pero cuando le pongo que bootee normalmente vuelve la catarata de errores.

fsck desde un live cd dice que está todo ok.

ahora estoy bakupeando y luego reinstalaré....

doy el tema por solucionado...

---

### Post by guillermolisi on 2010-08-31
No es lo mismo cerrar el tema, finalizarlo, que solucionarlo.

La diferencia fundamental esta en que si luego de volver a instalar todo te encontras de nuevo con el problema estas peor que al principio, ya que trabajaste sin saber en realidad cual fue la causa que origino la cuestion.

Que dicen los logs (a los que podes acceder desde un liveCD) dmesg y xorg.0.log ?

---

### Post by granjero on 2010-08-31
cuando vuelvo al laburo copio los logs y los pego.... donde están esos logs¿? 

ojalá no vuelva a pasar....

ahora igual voy a instalar separando home del resto cosa de no tener que bakupear si todo se pudre de nuevo....

Guillermo si querés sacarle el solved y cerrar el tema hacelo...

lo que pasa es que tampoco tengo tiempo de andar probando que es lo que pasa....

prefiero instalar y dejarlo andando porque lo usan mucho ese server....


gracias igual por la buena onda!

salud!

---

### Post by guillermolisi on 2010-08-31
Me imagine que la cosa venia por el lado de un server en produccion (yo haria lo mismo en ese caso).

Los logs estan en /var/logs.

Buena idea esa de particion aparte para /home !

Suerte con la nueva instalacion.

---

### Post by granjero on 2010-08-31
antes de formatear compié los logs....

ahi van...  el xorg.0.log no lo encontré
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-22-generic-pae (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #63-Ubuntu SMP Wed Aug 18 23:57:18 UTC 2010 (Ubuntu 2.6.31-22.63-generic-pae)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bfb0000 (usable)
[    0.000000]  BIOS-e820: 000000001bfb0000 - 000000001bfbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bfbe000 - 000000001bfe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bfe0000 - 000000001c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1bfb0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
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
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001bfb0000 (usable)
[    0.000000]  modified: 000000001bfb0000 - 000000001bfbe000 (ACPI data)
[    0.000000]  modified: 000000001bfbe000 - 000000001bfe0000 (ACPI NVS)
[    0.000000]  modified: 000000001bfe0000 - 000000001c000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001bfb0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 001be00000 page 2M
[    0.000000]  001be00000 - 001bfb0000 page 4k
[    0.000000] kernel direct mapping tables up to 1bfb0000 @ 10000-16000
[    0.000000] RAMDISK: 14987000 - 1500348a
[    0.000000] ACPI: RSDP 000fa850 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 1bfb0000 00030 (v01 A M I  OEMRSDT  05000618 MSFT 00000097)
[    0.000000] ACPI: FACP 1bfb0200 00084 (v02 A M I  OEMFACP  05000618 MSFT 00000097)
[    0.000000] ACPI: DSDT 1bfb0430 04807 (v01  A0473 A0473000 00000000 INTL 02002026)
[    0.000000] ACPI: FACS 1bfbe000 00040
[    0.000000] ACPI: MCFG 1bfb03f0 0003C (v01 A M I  OEMMCFG  05000618 MSFT 00000097)
[    0.000000] ACPI: OEMB 1bfbe040 00046 (v01 A M I  AMI_OEM  05000618 MSFT 00000097)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1bfb0000
[    0.000000]   low ram: 0 - 1bfb0000
[    0.000000]   node 0 low ram: 00000000 - 1bfb0000
[    0.000000]   node 0 bootmap 00012000 - 000157f8
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001bfb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008eca80]    TEXT DATA BSS ==> [0000100000 - 00008eca80]
[    0.000000]   #4 [0014987000 - 001500348a]          RAMDISK ==> [0014987000 - 001500348a]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008ed000 - 00008f4230]              BRK ==> [00008ed000 - 00008f4230]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001bfb0
[    0.000000]   HighMem  0x0001bfb0 -> 0x0001bfb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001bfb0
[    0.000000] On node 0 totalpages: 114495
[    0.000000] free_area_init_node: node 0, pgdat c07ae640, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 864 pages used for memmap
[    0.000000]   Normal zone: 109648 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: No APIC-table, disabling MPS
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1c000000 (gap: 1c000000:e2c00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages at c1382000, static data 39036 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113599
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic-pae root=UUID=87c7d666-edba-4d93-b3fe-4199033890a6 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2291840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 436556k/458432k available (4660k kernel code, 21108k reserved, 2215k data, 560k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xdc7b0000 - 0xff9fe000   ( 562 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdbfb0000   ( 447 MB)
[    0.000000]       .init : 0xc07b8000 - 0xc0844000   ( 560 kB)
[    0.000000]       .data : 0xc058d2d0 - 0xc07b7288   (2215 kB)
[    0.000000]       .text : 0xc0100000 - 0xc058d2d0   (4660 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1396.776 MHz processor.
[    0.000010] spurious 8259A interrupt: IRQ7.
[    0.001793] Console: colour VGA+ 80x25
[    0.001797] console [tty0] enabled
[    0.001865] Calibrating delay loop (skipped), value calculated using timer frequency.. 2793.55 BogoMIPS (lpj=5587104)
[    0.001890] Security Framework initialized
[    0.001915] AppArmor: AppArmor initialized
[    0.001925] Mount-cache hash table entries: 512
[    0.002068] Initializing cgroup subsys ns
[    0.002074] Initializing cgroup subsys cpuacct
[    0.002079] Initializing cgroup subsys memory
[    0.002089] Initializing cgroup subsys devices
[    0.002092] Initializing cgroup subsys freezer
[    0.002096] Initializing cgroup subsys net_cls
[    0.002111] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.002115] CPU: L2 Cache: 256K (64 bytes/line)
[    0.002120] mce: CPU supports 5 MCE banks
[    0.002137] Performance Counters: AMD PMU driver.
[    0.002143] ... version:                 0
[    0.002145] ... bit width:               48
[    0.002148] ... generic counters:        4
[    0.002151] ... value mask:              0000ffffffffffff
[    0.002154] ... max period:              00007fffffffffff
[    0.002157] ... fixed-purpose counters:  0
[    0.002159] ... counter mask:            000000000000000f
[    0.002165] Checking 'hlt' instruction... OK.
[    0.016795] SMP alternatives: switching to UP code
[    0.024019] Freeing SMP alternatives: 20k freed
[    0.024049] ACPI: Core revision 20090521
[    0.033173] ACPI: setting ELCR to 0200 (from 0c70)
[    0.036090] weird, boot CPU (#0) not listed by the BIOS.
[    0.036092] SMP motherboard not detected.
[    0.040001] SMP disabled
[    0.040001] Brought up 1 CPUs
[    0.040001] Total of 1 processors activated (2793.55 BogoMIPS).
[    0.040001] CPU0 attaching NULL sched-domain.
[    0.040001] Booting paravirtualized kernel on bare hardware
[    0.040001] regulator: core version 0.5
[    0.040001] Time: 18:36:19  Date: 08/31/10
[    0.040001] NET: Registered protocol family 16
[    0.040001] EISA bus registered
[    0.040001] ACPI: bus type pci registered
[    0.040001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.040001] PCI: Not using MMCONFIG.
[    0.040001] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.040001] PCI: Using configuration type 1 for base access
[    0.040001] bio: create slab <bio-0> at 0
[    0.040001] ACPI: EC: Look up EC in DSDT
[    0.048092] ACPI: Interpreter enabled
[    0.048103] ACPI: (supports S0 S1 S3 S4 S5)
[    0.048133] ACPI: Using PIC for interrupt routing
[    0.048193] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.053015] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.053019] PCI: Using MMCONFIG for extended config space
[    0.060884] ACPI Warning: Incorrect checksum in table [OEMB] - 7B, should be 75 20090521 tbutils-246
[    0.061030] ACPI: No dock devices found.
[    0.061178] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.061244] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.061725] pci 0000:00:01.0: supports D1
[    0.061788] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.061794] pci 0000:00:02.0: PME# disabled
[    0.061868] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.061873] pci 0000:00:03.0: PME# disabled
[    0.061933] pci 0000:00:0f.0: reg 10 io port: [0xe800-0xe807]
[    0.061941] pci 0000:00:0f.0: reg 14 io port: [0xe400-0xe403]
[    0.061950] pci 0000:00:0f.0: reg 18 io port: [0xe000-0xe007]
[    0.061958] pci 0000:00:0f.0: reg 1c io port: [0xd800-0xd803]
[    0.061967] pci 0000:00:0f.0: reg 20 io port: [0xd400-0xd40f]
[    0.061975] pci 0000:00:0f.0: reg 24 io port: [0xd000-0xd0ff]
[    0.062052] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.062139] pci 0000:00:10.0: reg 20 io port: [0xc800-0xc81f]
[    0.062167] pci 0000:00:10.0: supports D1 D2
[    0.062171] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.062176] pci 0000:00:10.0: PME# disabled
[    0.062230] pci 0000:00:10.1: reg 20 io port: [0xc400-0xc41f]
[    0.062258] pci 0000:00:10.1: supports D1 D2
[    0.062261] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.062266] pci 0000:00:10.1: PME# disabled
[    0.062319] pci 0000:00:10.2: reg 20 io port: [0xc000-0xc01f]
[    0.062347] pci 0000:00:10.2: supports D1 D2
[    0.062350] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.062355] pci 0000:00:10.2: PME# disabled
[    0.062408] pci 0000:00:10.3: reg 20 io port: [0xb800-0xb81f]
[    0.062436] pci 0000:00:10.3: supports D1 D2
[    0.062439] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.062444] pci 0000:00:10.3: PME# disabled
[    0.062479] pci 0000:00:10.4: reg 10 32bit mmio: [0xf9fffc00-0xf9fffcff]
[    0.062525] pci 0000:00:10.4: supports D1 D2
[    0.062528] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.062533] pci 0000:00:10.4: PME# disabled
[    0.062713] pci 0000:00:12.0: reg 10 io port: [0xb400-0xb4ff]
[    0.062721] pci 0000:00:12.0: reg 14 32bit mmio: [0xf9fff800-0xf9fff8ff]
[    0.062764] pci 0000:00:12.0: supports D1 D2
[    0.062767] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.062773] pci 0000:00:12.0: PME# disabled
[    0.063048] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.063056] pci 0000:01:00.0: reg 14 32bit mmio: [0xfa000000-0xfaffffff]
[    0.063079] pci 0000:01:00.0: reg 30 32bit mmio: [0xfbef0000-0xfbefffff]
[    0.063100] pci 0000:01:00.0: supports D1 D2
[    0.063144] pci 0000:00:01.0: bridge 32bit mmio: [0xfa000000-0xfbefffff]
[    0.063150] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.063203] pci 0000:00:02.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.063260] pci 0000:00:03.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.063306] pci 0000:04:01.0: reg 10 64bit mmio: [0xfbffc000-0xfbffffff]
[    0.063349] pci 0000:04:01.0: PME# supported from D0 D3hot D3cold
[    0.063355] pci 0000:04:01.0: PME# disabled
[    0.063406] pci 0000:00:13.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.063458] pci 0000:00:13.1: transparent bridge
[    0.063491] pci_bus 0000:00: on NUMA node 0
[    0.063497] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.063757] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.063819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[    0.063969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.064032] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.064109] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[    0.083543] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.083675] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.083805] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.083933] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.084066] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.084196] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.084326] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.084457] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.084697] SCSI subsystem initialized
[    0.084790] libata version 3.00 loaded.
[    0.084886] usbcore: registered new interface driver usbfs
[    0.084904] usbcore: registered new interface driver hub
[    0.084934] usbcore: registered new device driver usb
[    0.085099] ACPI: WMI: Mapper loaded
[    0.085102] PCI: Using ACPI for IRQ routing
[    0.085114] pci 0000:00:02.0: BAR 14: can't allocate resource
[    0.085118] pci 0000:00:03.0: BAR 14: can't allocate resource
[    0.085337] Bluetooth: Core ver 2.15
[    0.085370] NET: Registered protocol family 31
[    0.085372] Bluetooth: HCI device and connection manager initialized
[    0.085377] Bluetooth: HCI socket layer initialized
[    0.085380] NetLabel: Initializing
[    0.085382] NetLabel:  domain hash size = 128
[    0.085384] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.085402] NetLabel:  unlabeled traffic allowed by default
[    0.087446] pnp: PnP ACPI init
[    0.087477] ACPI: bus type pnp registered
[    0.091651] pnp: PnP ACPI: found 14 devices
[    0.091655] ACPI: ACPI bus type pnp unregistered
[    0.091660] PnPBIOS: Disabled by ACPI PNP
[    0.091677] system 00:06: ioport range 0x290-0x297 has been reserved
[    0.091685] system 00:07: ioport range 0x3e0-0x3e7 has been reserved
[    0.091690] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.091694] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.091699] system 00:07: ioport range 0x400-0x41f has been reserved
[    0.091708] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.091713] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.091721] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.091729] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.091733] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.091738] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.091743] system 00:0d: iomem range 0x100000-0x1fffffff could not be reserved
[    0.091748] system 00:0d: iomem range 0xff780000-0xffffffff has been reserved
[    0.126459] AppArmor: AppArmor Filesystem Enabled
[    0.126522] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.126526] pci 0000:00:01.0:   IO window: disabled
[    0.126533] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfbefffff
[    0.126539] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.126546] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.126550] pci 0000:00:02.0:   IO window: disabled
[    0.126556] pci 0000:00:02.0:   MEM window: disabled
[    0.126562] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.126568] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.126571] pci 0000:00:03.0:   IO window: disabled
[    0.126578] pci 0000:00:03.0:   MEM window: disabled
[    0.126583] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.126590] pci 0000:00:13.0: PCI bridge, secondary bus 0000:04
[    0.126593] pci 0000:00:13.0:   IO window: disabled
[    0.126600] pci 0000:00:13.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.126605] pci 0000:00:13.0:   PREFETCH window: disabled
[    0.126611] pci 0000:00:13.1: PCI bridge, secondary bus 0000:05
[    0.126615] pci 0000:00:13.1:   IO window: disabled
[    0.126620] pci 0000:00:13.1:   MEM window: disabled
[    0.126625] pci 0000:00:13.1:   PREFETCH window: disabled
[    0.126642] pci 0000:00:01.0: setting latency timer to 64
[    0.126832] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    0.126836] PCI: setting IRQ 10 as level-triggered
[    0.126844] pci 0000:00:02.0: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    0.126852] pci 0000:00:02.0: setting latency timer to 64
[    0.126864] pci 0000:00:03.0: PCI INT A -> Link[LNKH] -> GSI 10 (level, low) -> IRQ 10
[    0.126872] pci 0000:00:03.0: setting latency timer to 64
[    0.126880] pci 0000:00:13.0: setting latency timer to 64
[    0.126888] pci 0000:00:13.1: setting latency timer to 64
[    0.126895] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.126899] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.126904] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfbefffff]
[    0.126908] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.126912] pci_bus 0000:02: resource 1 mem: [0x0-0xfffff]
[    0.126916] pci_bus 0000:03: resource 1 mem: [0x0-0xfffff]
[    0.126920] pci_bus 0000:04: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.126924] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.126928] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.126976] NET: Registered protocol family 2
[    0.127099] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.127466] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.127579] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.127694] TCP: Hash tables configured (established 16384 bind 16384)
[    0.127698] TCP reno registered
[    0.127807] NET: Registered protocol family 1
[    0.127895] Trying to unpack rootfs image as initramfs...
[    0.387140] Freeing initrd memory: 6641k freed
[    0.394667] cpufreq-nforce2: No nForce2 chipset.
[    0.394695] Scanning for low memory corruption every 60 seconds
[    0.394838] audit: initializing netlink socket (disabled)
[    0.394871] type=2000 audit(1283279779.391:1): initialized
[    0.408061] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.410000] VFS: Disk quotas dquot_6.5.2
[    0.410075] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.410798] fuse init (API version 7.12)
[    0.410913] msgmni has been set to 866
[    0.411175] alg: No test for stdrng (krng)
[    0.411190] io scheduler noop registered
[    0.411193] io scheduler anticipatory registered
[    0.411196] io scheduler deadline registered
[    0.411253] io scheduler cfq registered (default)
[    0.411265] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.411281] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.411380] pci 0000:01:00.0: Boot video device
[    0.411535] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.411675] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    0.411813] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
[    0.411822] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    0.411834] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.411918] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.412087] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.412092] ACPI: Power Button [PWRF]
[    0.412166] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.412173] ACPI: Power Button [PWRB]
[    0.412577] processor LNXCPU:00: registered as cooling_device0
[    0.412582] ACPI: Processor [CPU0] (supports 16 throttling states)
[    0.415778] isapnp: Scanning for PnP cards...
[    0.627988] Switched to high resolution mode on CPU 0
[    0.769728] isapnp: No Plug & Play device found
[    0.771237] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.771395] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.771762] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.773042] brd: module loaded
[    0.773615] loop: module loaded
[    0.773727] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.774495] pata_via 0000:00:0f.1: version 0.3.4
[    0.774714] scsi0 : pata_via
[    0.774833] scsi1 : pata_via
[    0.776590] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.776595] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.777029] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.777033] PCI: setting IRQ 11 as level-triggered
[    0.777042] pata_acpi 0000:00:0f.0: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.777102] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    0.777489] Fixed MDIO Bus: probed
[    0.777534] PPP generic driver version 2.4.2
[    0.777664] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.777875] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[    0.777878] PCI: setting IRQ 4 as level-triggered
[    0.777887] ehci_hcd 0000:00:10.4: PCI INT C -> Link[LNKC] -> GSI 4 (level, low) -> IRQ 4
[    0.777911] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.777962] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[    0.778010] ehci_hcd 0000:00:10.4: irq 4, io mem 0xf9fffc00
[    0.788009] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.788109] usb usb1: configuration #1 chosen from 1 choice
[    0.788148] hub 1-0:1.0: USB hub found
[    0.788159] hub 1-0:1.0: 8 ports detected
[    0.788240] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.788267] uhci_hcd: USB Universal Host Controller Interface driver
[    0.788529] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[    0.788532] PCI: setting IRQ 5 as level-triggered
[    0.788541] uhci_hcd 0000:00:10.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    0.788553] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.788605] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.788634] uhci_hcd 0000:00:10.0: irq 5, io base 0x0000c800
[    0.788734] usb usb2: configuration #1 chosen from 1 choice
[    0.788765] hub 2-0:1.0: USB hub found
[    0.788775] hub 2-0:1.0: 2 ports detected
[    0.788823] uhci_hcd 0000:00:10.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.788834] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.788870] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.788894] uhci_hcd 0000:00:10.1: irq 11, io base 0x0000c400
[    0.788987] usb usb3: configuration #1 chosen from 1 choice
[    0.789017] hub 3-0:1.0: USB hub found
[    0.789026] hub 3-0:1.0: 2 ports detected
[    0.789075] uhci_hcd 0000:00:10.2: PCI INT C -> Link[LNKC] -> GSI 4 (level, low) -> IRQ 4
[    0.789083] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.789117] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.789139] uhci_hcd 0000:00:10.2: irq 4, io base 0x0000c000
[    0.789236] usb usb4: configuration #1 chosen from 1 choice
[    0.789266] hub 4-0:1.0: USB hub found
[    0.789276] hub 4-0:1.0: 2 ports detected
[    0.789507] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    0.789511] PCI: setting IRQ 6 as level-triggered
[    0.789519] uhci_hcd 0000:00:10.3: PCI INT D -> Link[LNKD] -> GSI 6 (level, low) -> IRQ 6
[    0.789527] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.789569] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[    0.789593] uhci_hcd 0000:00:10.3: irq 6, io base 0x0000b800
[    0.789702] usb usb5: configuration #1 chosen from 1 choice
[    0.789734] hub 5-0:1.0: USB hub found
[    0.789744] hub 5-0:1.0: 2 ports detected
[    0.789858] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.790204] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.790214] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.790282] mice: PS/2 mouse device common for all mice
[    0.790393] rtc_cmos 00:02: RTC can wake from S4
[    0.790437] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.790468] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.790621] device-mapper: uevent: version 1.0.3
[    0.790755] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.790846] device-mapper: multipath: version 1.1.0 loaded
[    0.790850] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.791013] EISA: Probing bus 0 at eisa.0
[    0.791041] Cannot allocate resource for EISA slot 5
[    0.791058] EISA: Detected 0 cards.
[    0.791110] cpuidle: using governor ladder
[    0.791114] cpuidle: using governor menu
[    0.791789] TCP cubic registered
[    0.792026] NET: Registered protocol family 10
[    0.792586] lo: Disabled Privacy Extensions
[    0.793002] NET: Registered protocol family 17
[    0.793029] Bluetooth: L2CAP ver 2.13
[    0.793032] Bluetooth: L2CAP socket layer initialized
[    0.793036] Bluetooth: SCO (Voice Link) ver 0.6
[    0.793038] Bluetooth: SCO socket layer initialized
[    0.793089] Bluetooth: RFCOMM TTY layer initialized
[    0.793093] Bluetooth: RFCOMM socket layer initialized
[    0.793096] Bluetooth: RFCOMM ver 1.11
[    0.793112] powernow-k8: Power state transitions not supported
[    0.793139] Using IPI No-Shortcut mode
[    0.793234] PM: Resume from disk failed.
[    0.793250] registered taskstats version 1
[    0.793417]   Magic number: 6:832:646
[    0.793430] scsi_host host0: hash matches
[    0.793433] scsi host0: hash matches
[    0.793564] rtc_cmos 00:02: setting system clock to 2010-08-31 18:36:19 UTC (1283279779)
[    0.793569] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.793571] EDD information not available.
[    0.809528] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.940372] ata1.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB03, max UDMA/33
[    0.956259] ata1.00: configured for UDMA/33
[    0.957518] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB03 PQ: 0 ANSI: 5
[    0.964107] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.964111] Uniform CD-ROM driver Revision: 3.20
[    0.964226] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.964288] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.131242] Freeing unused kernel memory: 560k freed
[    1.131870] Write protecting the kernel text: 4664k
[    1.131950] Write protecting the kernel read-only data: 1860k
[    1.423428] sata_via 0000:00:0f.0: version 2.4
[    1.423447] sata_via 0000:00:0f.0: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.423500] sata_via 0000:00:0f.0: routed to hard irq line 11
[    1.477237] scsi2 : sata_via
[    1.477360] scsi3 : sata_via
[    1.479202] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd400 irq 11
[    1.479207] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xd800 bmdma 0xd408 irq 11
[    1.680015] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.892020] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.056341] ata4.00: ATA-7: SAMSUNG HD300LJ, ZT100-13, max UDMA7
[    2.056347] ata4.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.072346] ata4.00: configured for UDMA/133
[    2.072489] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD300LJ  ZT10 PQ: 0 ANSI: 5
[    2.072684] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.072734] sd 3:0:0:0: [sda] 586072368 512-byte logical blocks: (300 GB/279 GiB)
[    2.072790] sd 3:0:0:0: [sda] Write Protect is off
[    2.072794] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.072823] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.072977]  sda: sda1 sda2 < sda5 >
[    2.106954] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.110727] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.110784] via-rhine 0000:00:12.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    2.111630] eth0: VIA Rhine II at 0xf9fff800, 00:17:31:83:67:8b, IRQ 5.
[    2.112344] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[    2.530504] PM: Starting manual resume from disk
[    2.530511] PM: Resume from partition 8:5
[    2.530514] PM: Checking hibernation image.
[    2.530770] PM: Resume from disk failed.
[    2.563466] EXT4-fs (sda1): barriers enabled
[    2.588160] kjournald2 starting: pid 332, dev sda1:8, commit interval 5 seconds
[    2.588200] EXT4-fs (sda1): delayed allocation enabled
[    2.588205] EXT4-fs: file extents enabled
[    2.641792] EXT4-fs: mballoc enabled
[    2.641819] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.356199] type=1505 audit(1283279782.062:2): operation="profile_load" pid=354 name=/sbin/dhclient3
[    3.356623] type=1505 audit(1283279782.062:3): operation="profile_load" pid=354 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.356862] type=1505 audit(1283279782.062:4): operation="profile_load" pid=354 name=/usr/lib/connman/scripts/dhclient-script
[    3.375963] type=1505 audit(1283279782.078:5): operation="profile_load" pid=355 name=/usr/sbin/tcpdump
[    4.286944] Adding 1301224k swap on /dev/sda5.  Priority:-1 extents:1 across:1301224k 
[    4.498760] EXT4-fs (sda1): internal journal on sda1:8
[    4.707593] udev: starting version 147
[    5.461969] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.521258] parport_pc 00:05: reported by Plug and Play ACPI
[    5.521366] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    5.595371] lp: driver loaded but no devices found
[    5.616430] lp0: using parport0 (interrupt-driven).
[    5.774552] ppdev: user-space parallel port driver
[    5.792153] Linux agpgart interface v0.103
[    6.011929] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.018803] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0336]
[    6.026424] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    6.236309] psmouse serio1: ID: 10 00 64
[    6.298592] HDA Intel 0000:04:01.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    6.298627] HDA Intel 0000:04:01.0: setting latency timer to 64
[    6.298633] HDA Intel 0000:04:01.0: PCI: Disallowing DAC for device
[    6.400115] hda_codec: Unknown model for ALC660, trying auto-probe from BIOS...
[    6.400225] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:13.0/0000:04:01.0/input/input4
[    6.786090] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[    8.093486] eth0: link down
[    8.093547] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.177838] type=1505 audit(1283279786.882:6): operation="profile_replace" pid=720 name=/sbin/dhclient3
[    8.178264] type=1505 audit(1283279786.882:7): operation="profile_replace" pid=720 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.178502] type=1505 audit(1283279786.882:8): operation="profile_replace" pid=720 name=/usr/lib/connman/scripts/dhclient-script
[    8.180819] type=1505 audit(1283279786.886:9): operation="profile_replace" pid=721 name=/usr/sbin/tcpdump
```

tengo el resto de los logs también.

---

### Post by guillermolisi on 2010-08-31
En ese no vi nada raro relacionado con el problema.

---

### Post by granjero on 2010-09-04
le saque el solved al tread.

el server se me cae cada dos por tres...

anoche titilaban las luces de teclado de capslock y la de pausa creo.

la pantalla estaba como en la foto y el server muerto....

no se donde está el log completo de lo que le pasó!

un saludo!

---

### Post by guillermolisi on 2010-09-04
Revisa /var/log/dmesg, /var/log/syslog, /var/log/Xorg.0.log y tal vez alguno mas, dependiendo de lo que digan estos primeros.

Inicia bien y despues se cuelga o se cuelga de entrada ? (por IRC parecia que andaba bien)

Las actualizaciones estan al dia ?

---

### Post by granjero on 2010-09-04
Inicia bien y queda andando un par de horas.

después cuelga....

syslog
[http://paste.ubuntu.com/488385/](http://paste.ubuntu.com/488385/)

syslog.1 
[http://paste.ubuntu.com/488387/](http://paste.ubuntu.com/488387/)

en syslog.1 lo que me llama la atención es que corta el log y lo sigue como una hora despues

```
Sep  3 20:06:24 zeta kernel: [   16.990007] eth0: no IPv6 routers present
Sep  3 20:17:01 zeta CRON[1037]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  3 21:17:01 zeta CRON[1293]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  3 22:38:11 zeta kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
```

dsmeg
[http://paste.ubuntu.com/488388/](http://paste.ubuntu.com/488388/)

Xorg.0.log este no existe.

en esos logs no parece haber nada raro.

ahora está andando el server así que puedo entrar a ver cualquier archivo... si hace falta bajar otro log es posible.

puede ser el disco rígido?

salud y gracias!

---

### Post by juancarlospaco on 2010-09-04
sudo touch /forcefsck && sudo badblocks -s -v /dev/sdX && sudo reboot

sudo touch /forcefsck---> Chequea el disco en el proximo reboot
sudo badblocks -s -v /dev/sdX---> Chequea el disco por bloques dañados
sudo reboot--->Reinicia la PC

Parametros de Badblocks:
-s = Muestra el progreso
-v = Verbosidad
/dev/sdX = Donde X es la letra de tu particion/disco/etc

NO USAR SI TENES EL DISCO CIFRADO.

Pasar el MemTest86+ Completo.


*Veo una Ram nueva en tu futuro...*

---

### Post by granjero on 2010-09-04
no el disco no está cifrado....

/dev/sdX = Donde X es la letra de tu particion/disco/etc

/dev/sda si quiero que chequee todo el disco. es un sata. así que deberia ser /dev/sda no?

hacer esto en forma remota no tiene sentido no? (SSH mi nuevo amigo)

tengo que ir y hacerlo frente a la maquina??

sudo badblocks -s -v /dev/sdX---> Chequea el disco por bloques dañados 

y que hace si encuentra bloques dañados? anula su uso? o tengo que conseguir un HD nuevo?


salud!

---

### Post by guillermolisi on 2010-09-04
> **granjero said:**
> no el disco no está cifrado....

/dev/sdX = Donde X es la letra de tu particion/disco/etc

/dev/sda si quiero que chequee todo el disco. es un sata. así que deberia ser /dev/sda no?

hacer esto en forma remota no tiene sentido no? (SSH mi nuevo amigo)

tengo que ir y hacerlo frente a la maquina??

sudo badblocks -s -v /dev/sdX---> Chequea el disco por bloques dañados 

y que hace si encuentra bloques dañados? anula su uso? o tengo que conseguir un HD nuevo?


salud!
fsck revisa la consistencia de PARTICIONES, no de discos (cada particion es un filesystem y el disco puede contener varios de estos ultimos).

El disco/particion de inicio no se puede revisar via ssh porque tiene que estar desmontado (valido para todas las particiones que se quieran revisar).

Suponiendo que fsck informe de puntos defectuosos en el disco (y suponiendo tambien que no los mapee por alternativos) se podria llegar a usar alguna herramienta especifica como TestDsik o similar.

El reemplazo del disco lo diran las revisiones periodicas que hagas. Si por cada vez aparecen mas pistas malas, el disco va derecho a la jubilacion.

Tambien es una buena practica habilitar SMART en el BIOS e instalar SmartMon Tools para que te informe de problemas antes de que te quedes sin maniobra.

---

### Post by juancarlospaco on 2010-09-06
Lo que el dice :)

---

### Post by granjero on 2010-09-07
hoy a la noche dejé corriendo memtest para empezar...

mañana mis compañeros de la mañana me dirán que dijo el memtest.

con el tema del fsck:

es correcto bootear un live-session y desde ahí correr 

```
sudo badblocks -s -v /dev/sda
```

para que chequee todo el disco?

salud!

---

### Post by guillermolisi on 2010-09-08
Segun lo que interpreto del man de badblocks, se debe correr sobre una particion que no este montada. Por defecto hace un analisis no destructivo y podes pedirle que genere una lista de bloques malos que luego puede ser utilizada en posteriores corridas para no analizar sectores ya resueltos.

---

### Post by granjero on 2010-09-08
al final el memtest dijo que la memoria tenia errores, lamentablemente mis compañeros no fueron capaces de fotografiarme la pantalla para ver que errores decía.

cambié la memoria y hoy no se cayó en todo el día...   \\:D/   \\:D/   \\:D/    \\:D/    \\:D/    \\:D/

si no se cae hasta el viernes le vuelvo a poner solved al tema!

> **juancarlospaco said:**
> *Veo una Ram nueva en tu futuro...*

juancarlos entregá la bola de cristal!!!!

---

### Post by juancarlospaco on 2010-09-10
> **granjero said:**
> al final el memtest dijo que la memoria tenia errores

cambié la memoria y hoy no se cayó en todo el día...   

juancarlos entregá la bola de cristal!!!!

:D
Son años con Ubuntu...

---

### Post by granjero on 2010-09-23
thread solvd o 

listo el pollo; pelada la gallina!

luego de un examen visual minucioso me di cuenta que la fuente que tenía el server era una fuente que tenía un conector de 20 pines y el mother tiene un conector de 24 pines.

le compré una fuente acorde.

funciona de pelos!

salud!

---

