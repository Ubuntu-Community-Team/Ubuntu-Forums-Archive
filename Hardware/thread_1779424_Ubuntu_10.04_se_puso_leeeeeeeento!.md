---
title: "Ubuntu 10.04 se puso leeeeeeeento!"
date: 2011-06-10
forum: Hardware
---

### Post by granjero on 2011-06-10
En mi pc de escritorio tengo Ubuntu 10.04. Hace 2 días se puso increíblemente lento. 

Hace unos días apareció un cartel que me quedaban 400 y pico de megas en / 
A raíz de eso desintalé un montón de cosas que había instalado para probar. Algunas las desintalé por el Centro de Softaware y otras con apt-get purge. Ahora le quedan 3,3gb a /

Ejemplos de lo leeeento:

Luego de poner mi clave en menos de 10 segundos tenía el escritorio listo y andando. Ahora tarda como 30 segundos.

Rhythmbox reproduce un rato después se calla, se pone gris, vuelve a arrancar. Mientras se puso gris la luz del HD esta roja a pleno. 

Abro chrome y pasa lo mismo que con el rhythmbox, al rato se pone gris. 

Idem con OpenOffice.


Booteando con el kernel anterior anda todo igual de mal.

Les dejo datos de la pc y el disco.

lshw
```
pc-jm                     
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: M3A
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0702 (03/14/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.11.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 35
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM_A1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM_B1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM SDRAM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM_A2
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM_B2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.11.2
          size: 2700MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:fa000000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G84 [GeForce 8600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:e800(size=128) memory:feae0000-feafffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port C)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:feb00000-febfffff
           *-network
                description: Ethernet interface
                product: L1 Gigabit Ethernet Adapter
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: b0
                serial: 00:1f:c6:bc:47:08
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.2.10 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:26 memory:febc0000-febfffff memory:feba0000-febbffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:d000(size=8) ioport:c000(size=4) ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=16) memory:f9fff800-f9fffbff
           *-disk:0
                description: ATA Disk
                product: WDC WD3200AAKS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAT11092701
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0004107b
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 866e497d-d467-b146-8808-9154f8077279
                   size: 19GiB
                   capacity: 20GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-10-11 00:08:28 filesystem=ntfs label=win7 modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 278GiB
                   capacity: 278GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 976MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 9765MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 190GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: HPFS/NTFS partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 19GiB
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-S223F
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: WDC WD10EARS-00Y
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sdb
                version: 80.0
                serial: WD-WCAV5E252190
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0007490a
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: 23a9a5ca-475f-42ef-a7c0-861fb22f1e97
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-09-03 11:56:54 filesystem=ext4 label=1TB lastmountpoint=/media/1TBA&#65533;&#65533;:&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;X&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;E&#65533; &#65533;&#1857;/&#65533;&#65533;~&#65533;>0!&#65533; "Q&#65533; "Q&#65533;:&#65533; modified=2011-06-10 12:20:49 mounted=2011-06-10 11:29:07 state=clean
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f9ffe000-f9ffefff
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f9ffd000-f9ffdfff
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f9ffc000-f9ffcfff
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f9ffb000-f9ffbfff
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f9ffa000-f9ffafff
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f9fff000-f9fff0ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f9ff4000-f9ff7fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

lspci
```
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
02:00.0 Ethernet controller: Atheros Communications L1 Gigabit Ethernet Adapter (rev b0)

```

fdisk -l
```
isco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x0004107b

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *       36303       38913    20972857+   7  HPFS/NTFS
/dev/sda2               1       36302   291594241    5  Extendida
/dev/sda5               1         125      999424   82  Linux swap / Solaris
/dev/sda6             125        1370     9999360   83  Linux
/dev/sda7            1370       26269   199999488   83  Linux
/dev/sda8           26270       28879    20964793+   7  HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x0007490a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1      121601   976760001   83  Linux

```

Alguna idea?

salud!

---

### Post by juancarlospaco on 2011-06-10
Pasale el Bleachbit completito, fijate el "top", mandale "sudo apt-get autoremove && apt-get clean"

---

### Post by granjero on 2011-06-10
hoy a la noche cuando llego a casa me fijo!

gracias JuanCarlos!  ;)

---

### Post by biale on 2011-06-10
Comando "top" para ver que procesos se llevan la cpu y la RAM. Errores del kernel?

---

### Post by granjero on 2011-06-10
pase el bleachbit instalado de repositorios como root. no me animé a agregarle el dir / en preferencias.

también hice apt-get autoremove && apt-get clean. 

sigue todo igual de mal.

top no muestra uso abusivo de CPU de ninguna app. nunca sube del 20%

no se que será. Mañana abro el gabinete y sopleteo todo. si sigue igual voy a mandar format c: ;)

salud!

---

### Post by guillermolisi on 2011-06-10
Y en los logs no figura nada ? Por ejemplo, en /var/log/dmesg no hay entradas que indiquen algun problema con el disco rigido, por ejemplo ?

Tenes activado SMART en el BIOS ?
Instala Smartmon tools y fijate que te dice (o usa alguna herramienta grafica para ello si tenes escritorio grafico).

La carga promedio del sistema en que valores anda ? (lo ves con Top en una terminal)

Ok, formateas, volves a instalar, bajas las actualizaciones, instalas programas, etc ..... y si el problema sigue ?

Es mas rapido pensar que hacer :)

---

### Post by granjero on 2011-06-11
ahi pego dmesg

no lo se leer :)

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-32-generic (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 (Ubuntu 2.6.32-32.62-generic 2.6.32.38+drm33.16)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
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
[    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  modified: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  modified: 000000007ffbe000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  modified: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 373f5000 - 37feffe3
[    0.000000] Allocated new RAMDISK: 008e3000 - 014ddfe3
[    0.000000] Move RAMDISK from 00000000373f5000 - 0000000037feffe2 to 008e3000 - 014ddfe2
[    0.000000] ACPI: RSDP 000faaf0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffb0000 00038 (v01 031408 OEMRSDT  20080314 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0200 00084 (v02 031408 OEMFACP  20080314 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffb0440 0650F (v01  P0004 P0004000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7ffbe000 00040
[    0.000000] ACPI: APIC 7ffb0390 0006C (v01 031408 OEMAPIC  20080314 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffb0400 0003C (v01 031408 OEMMCFG  20080314 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffbe040 00071 (v01 031408 AMI_OEM  20080314 MSFT 00000097)
[    0.000000] ACPI: HPET 7ffb6950 00038 (v01 031408 OEMHPET  20080314 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008deef8]    TEXT DATA BSS ==> [0000100000 - 00008deef8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008df000 - 00008e2179]              BRK ==> [00008df000 - 00008e2179]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e3000 - 00014ddfe3]      NEW RAMDISK ==> [00008e3000 - 00014ddfe3]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524095
[    0.000000] free_area_init_node: node 0, pgdat c07987c0, node_mem_map c14df200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294562 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2800000 s36312 r0 d21032 u1048576
[    0.000000] pcpu-alloc: s36312 r0 d21032 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-generic root=UUID=7271e4af-e609-4927-b8b9-da0e2e749a5f ro vga=771 quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffb0)
[    0.000000] Memory: 2047132k/2096832k available (4674k kernel code, 48052k reserved, 2120k data, 668k init, 1187528k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc084a000   ( 668 kB)
[    0.000000]       .data : 0xc0590ad7 - 0xc07a2d88   (2120 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590ad7   (4674 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2699.619 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5399.23 BogoMIPS (lpj=10798476)
[    0.004019] Security Framework initialized
[    0.004035] AppArmor: AppArmor initialized
[    0.004040] Mount-cache hash table entries: 512
[    0.004142] Initializing cgroup subsys ns
[    0.004145] Initializing cgroup subsys cpuacct
[    0.004149] Initializing cgroup subsys memory
[    0.004154] Initializing cgroup subsys devices
[    0.004156] Initializing cgroup subsys freezer
[    0.004158] Initializing cgroup subsys net_cls
[    0.004173] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004175] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004177] CPU: Physical Processor ID: 0
[    0.004179] CPU: Processor Core ID: 0
[    0.004182] mce: CPU supports 5 MCE banks
[    0.004189] using C1E aware idle routine
[    0.004195] Performance Events: AMD PMU driver.
[    0.004200] ... version:                0
[    0.004202] ... bit width:              48
[    0.004203] ... generic registers:      4
[    0.004205] ... value mask:             0000ffffffffffff
[    0.004206] ... max period:             00007fffffffffff
[    0.004208] ... fixed-purpose events:   0
[    0.004209] ... event mask:             000000000000000f
[    0.004213] Checking 'hlt' instruction... OK.
[    0.021747] ACPI: Core revision 20090903
[    0.028469] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028474] ftrace: allocating 21723 entries in 43 pages
[    0.032081] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032395] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073694] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.160107] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02
[    0.160124] Brought up 2 CPUs
[    0.160126] Total of 2 processors activated (10799.53 BogoMIPS).
[    0.160452] CPU0 attaching sched-domain:
[    0.160456]  domain 0: span 0-1 level MC
[    0.160459]   groups: 0 1
[    0.160464] CPU1 attaching sched-domain:
[    0.160465]  domain 0: span 0-1 level MC
[    0.160467]   groups: 1 0
[    0.160525] devtmpfs: initialized
[    0.160525] regulator: core version 0.5
[    0.160525] Time:  9:56:37  Date: 06/11/11
[    0.160525] NET: Registered protocol family 16
[    0.160525] EISA bus registered
[    0.160525] ACPI: bus type pci registered
[    0.160525] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.160525] PCI: Not using MMCONFIG.
[    0.160780] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.160782] PCI: Using configuration type 1 for base access
[    0.161469] Trying to unpack rootfs image as initramfs...
[    0.168162] bio: create slab <bio-0> at 0
[    0.168613] ACPI: EC: Look up EC in DSDT
[    0.170590] ACPI: Executed 3 blocks of module-level executable AML code
[    0.176115] ACPI: Interpreter enabled
[    0.176118] ACPI: (supports S0 S1 S3 S4 S5)
[    0.176140] ACPI: Using IOAPIC for interrupt routing
[    0.176239] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.179193] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.179195] PCI: Using MMCONFIG for extended config space
[    0.185147] ACPI Warning: Incorrect checksum in table [OEMB] - 3F, should be 3E (20090903/tbutils-314)
[    0.185248] ACPI: No dock devices found.
[    0.185381] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.185427] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.185492] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.185495] pci 0000:00:02.0: PME# disabled
[    0.185541] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.185544] pci 0000:00:06.0: PME# disabled
[    0.185598] pci 0000:00:12.0: reg 10 io port: [0xd000-0xd007]
[    0.185605] pci 0000:00:12.0: reg 14 io port: [0xc000-0xc003]
[    0.185613] pci 0000:00:12.0: reg 18 io port: [0xb000-0xb007]
[    0.185620] pci 0000:00:12.0: reg 1c io port: [0xa000-0xa003]
[    0.185627] pci 0000:00:12.0: reg 20 io port: [0x9000-0x900f]
[    0.185635] pci 0000:00:12.0: reg 24 32bit mmio: [0xf9fff800-0xf9fffbff]
[    0.185655] pci 0000:00:12.0: set SATA to AHCI mode
[    0.185696] pci 0000:00:13.0: reg 10 32bit mmio: [0xf9ffe000-0xf9ffefff]
[    0.185757] pci 0000:00:13.1: reg 10 32bit mmio: [0xf9ffd000-0xf9ffdfff]
[    0.185817] pci 0000:00:13.2: reg 10 32bit mmio: [0xf9ffc000-0xf9ffcfff]
[    0.185878] pci 0000:00:13.3: reg 10 32bit mmio: [0xf9ffb000-0xf9ffbfff]
[    0.185938] pci 0000:00:13.4: reg 10 32bit mmio: [0xf9ffa000-0xf9ffafff]
[    0.186026] pci 0000:00:13.5: reg 10 32bit mmio: [0xf9fff000-0xf9fff0ff]
[    0.186090] pci 0000:00:13.5: supports D1 D2
[    0.186091] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.186096] pci 0000:00:13.5: PME# disabled
[    0.186146] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]
[    0.186221] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.186228] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.186235] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.186242] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.186250] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.186307] pci 0000:00:14.2: reg 10 64bit mmio: [0xf9ff4000-0xf9ff7fff]
[    0.186355] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.186359] pci 0000:00:14.2: PME# disabled
[    0.186575] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.186585] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.186595] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.186601] pci 0000:01:00.0: reg 24 io port: [0xe800-0xe87f]
[    0.186607] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfeae0000-0xfeafffff]
[    0.186686] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.186689] pci 0000:00:02.0: bridge 32bit mmio: [0xfa000000-0xfeafffff]
[    0.186693] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.186740] pci 0000:02:00.0: reg 10 64bit mmio: [0xfebc0000-0xfebfffff]
[    0.186770] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfeba0000-0xfebbffff]
[    0.186803] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.186808] pci 0000:02:00.0: PME# disabled
[    0.186869] pci 0000:00:06.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.186933] pci 0000:00:14.4: transparent bridge
[    0.186954] pci_bus 0000:00: on NUMA node 0
[    0.186958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.187134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.187182] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.187247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.191190] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.191271] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.191350] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.191429] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.191508] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.191586] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.191662] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.191741] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.191830] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.191832] vgaarb: loaded
[    0.191925] SCSI subsystem initialized
[    0.192015] libata version 3.00 loaded.
[    0.192076] usbcore: registered new interface driver usbfs
[    0.192090] usbcore: registered new interface driver hub
[    0.192112] usbcore: registered new device driver usb
[    0.192219] ACPI: WMI: Mapper loaded
[    0.192221] PCI: Using ACPI for IRQ routing
[    0.192229] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.192231] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.192361] NetLabel: Initializing
[    0.192362] NetLabel:  domain hash size = 128
[    0.192364] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.192375] NetLabel:  unlabeled traffic allowed by default
[    0.192407] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.192412] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.194443] Switching to clocksource hpet
[    0.194729] AppArmor: AppArmor Filesystem Enabled
[    0.194729] pnp: PnP ACPI init
[    0.194729] ACPI: bus type pnp registered
[    0.196204] pnp 00:0c: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.196207] pnp 00:0c: mem resource (0xc0000-0xcffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.196210] pnp 00:0c: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.196213] pnp 00:0c: mem resource (0x100000-0x7fffffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.196443] pnp: PnP ACPI: found 13 devices
[    0.196444] ACPI: ACPI bus type pnp unregistered
[    0.196447] PnPBIOS: Disabled by ACPI PNP
[    0.196458] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.196461] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.196466] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.196468] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.196471] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.196473] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.196475] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.196478] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.196480] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.196482] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.196485] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.196487] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.196490] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.196492] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.196494] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.196497] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.196511] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.196514] system 00:08: ioport range 0xb10-0xb1f has been reserved
[    0.196516] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.196519] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.196521] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.196524] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.196527] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.196531] system 00:0a: ioport range 0xe00-0xe0f has been reserved
[    0.196534] system 00:0a: ioport range 0xe80-0xe8f has been reserved
[    0.196536] system 00:0a: ioport range 0xf40-0xf4f has been reserved
[    0.196539] system 00:0a: ioport range 0xa30-0xa3f has been reserved
[    0.196543] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.196547] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.231212] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.231215] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.231218] pci 0000:00:02.0:   MEM window: 0xfa000000-0xfeafffff
[    0.231222] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.231226] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.231228] pci 0000:00:06.0:   IO window: disabled
[    0.231231] pci 0000:00:06.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.231234] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.231238] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.231240] pci 0000:00:14.4:   IO window: disabled
[    0.231245] pci 0000:00:14.4:   MEM window: disabled
[    0.231249] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.231263] pci 0000:00:02.0: setting latency timer to 64
[    0.231269] pci 0000:00:06.0: setting latency timer to 64
[    0.231277] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.231279] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.231282] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.231284] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfeafffff]
[    0.231286] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.231289] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.231291] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.231293] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.231323] NET: Registered protocol family 2
[    0.231400] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.231675] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.232209] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.232456] TCP: Hash tables configured (established 131072 bind 65536)
[    0.232458] TCP reno registered
[    0.232563] NET: Registered protocol family 1
[    0.348545] pci 0000:01:00.0: Boot video device
[    0.348710] cpufreq-nforce2: No nForce2 chipset.
[    0.348731] Scanning for low memory corruption every 60 seconds
[    0.348810] audit: initializing netlink socket (disabled)
[    0.348819] type=2000 audit(1307786197.348:1): initialized
[    0.356435] highmem bounce pool size: 64 pages
[    0.356440] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.357612] VFS: Disk quotas dquot_6.5.2
[    0.357658] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.358106] fuse init (API version 7.13)
[    0.358172] msgmni has been set to 1681
[    0.358350] alg: No test for stdrng (krng)
[    0.358395] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.358398] io scheduler noop registered
[    0.358399] io scheduler anticipatory registered
[    0.358401] io scheduler deadline registered
[    0.358431] io scheduler cfq registered (default)
[    0.358546]   alloc irq_desc for 24 on node -1
[    0.358548]   alloc kstat_irqs on node -1
[    0.358557] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.358563] pcieport 0000:00:02.0: setting latency timer to 64
[    0.358642]   alloc irq_desc for 25 on node -1
[    0.358643]   alloc kstat_irqs on node -1
[    0.358648] pcieport 0000:00:06.0: irq 25 for MSI/MSI-X
[    0.358653] pcieport 0000:00:06.0: setting latency timer to 64
[    0.358708] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.358728] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.358813] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.358822] ACPI: Power Button [PWRB]
[    0.358856] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.358858] ACPI: Power Button [PWRF]
[    0.359109] ACPI: duty_cycle spans bit 4
[    0.359132] processor LNXCPU:00: registered as cooling_device0
[    0.359159] processor LNXCPU:01: registered as cooling_device1
[    0.362360] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.362476] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.362757] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.363649] brd: module loaded
[    0.364044] loop: module loaded
[    0.364119] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.364232]   alloc irq_desc for 16 on node -1
[    0.364234]   alloc kstat_irqs on node -1
[    0.364240] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.364276] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.364549] Fixed MDIO Bus: probed
[    0.364579] PPP generic driver version 2.4.2
[    0.364611] tun: Universal TUN/TAP device driver, 1.6
[    0.364613] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.364678] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.364694]   alloc irq_desc for 19 on node -1
[    0.364696]   alloc kstat_irqs on node -1
[    0.364699] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.364715] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.364740] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.364764] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.364782] ehci_hcd 0000:00:13.5: debug port 1
[    0.364805] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf9fff000
[    0.364860] isapnp: Scanning for PnP cards...
[    0.413931] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.414019] usb usb1: configuration #1 chosen from 1 choice
[    0.414042] hub 1-0:1.0: USB hub found
[    0.414050] hub 1-0:1.0: 10 ports detected
[    0.414118] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.414129] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.414138] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.414162] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.414181] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf9ffe000
[    0.475118] Freeing initrd memory: 12267k freed
[    0.505414] usb usb2: configuration #1 chosen from 1 choice
[    0.505434] hub 2-0:1.0: USB hub found
[    0.505443] hub 2-0:1.0: 2 ports detected
[    0.505483]   alloc irq_desc for 17 on node -1
[    0.505484]   alloc kstat_irqs on node -1
[    0.505488] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.505496] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.505526] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.505544] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf9ffd000
[    0.564623] usb usb3: configuration #1 chosen from 1 choice
[    0.564649] hub 3-0:1.0: USB hub found
[    0.564660] hub 3-0:1.0: 2 ports detected
[    0.564720]   alloc irq_desc for 18 on node -1
[    0.564722]   alloc kstat_irqs on node -1
[    0.564729] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.564745] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.564780] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.564806] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf9ffc000
[    0.628056] usb usb4: configuration #1 chosen from 1 choice
[    0.628075] hub 4-0:1.0: USB hub found
[    0.628083] hub 4-0:1.0: 2 ports detected
[    0.628125] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.628135] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.628160] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.628173] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf9ffb000
[    0.684071] usb usb5: configuration #1 chosen from 1 choice
[    0.684091] hub 5-0:1.0: USB hub found
[    0.684100] hub 5-0:1.0: 2 ports detected
[    0.684140] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.684150] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.684177] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.684189] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf9ffa000
[    0.723309] isapnp: No Plug & Play device found
[    0.744068] usb usb6: configuration #1 chosen from 1 choice
[    0.744088] hub 6-0:1.0: USB hub found
[    0.744098] hub 6-0:1.0: 2 ports detected
[    0.744141] uhci_hcd: USB Universal Host Controller Interface driver
[    0.744206] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[    0.744208] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.744581] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.744586] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.744666] mice: PS/2 mouse device common for all mice
[    0.744759] rtc_cmos 00:02: RTC can wake from S4
[    0.744792] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.744819] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.744901] device-mapper: uevent: version 1.0.3
[    0.745041] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.745164] device-mapper: multipath: version 1.1.0 loaded
[    0.745166] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.745292] EISA: Probing bus 0 at eisa.0
[    0.745328] EISA: Detected 0 cards.
[    0.745453] cpuidle: using governor ladder
[    0.745454] cpuidle: using governor menu
[    0.745781] TCP cubic registered
[    0.745904] NET: Registered protocol family 10
[    0.746298] lo: Disabled Privacy Extensions
[    0.746576] NET: Registered protocol family 17
[    0.746605] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (2 cpu cores) (version 2.20.00)
[    0.746614] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    0.746615] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    0.746635] Using IPI No-Shortcut mode
[    0.746701] PM: Resume from disk failed.
[    0.746717] registered taskstats version 1
[    0.746983]   Magic number: 15:668:929
[    0.747070] rtc_cmos 00:02: setting system clock to 2011-06-11 09:56:38 UTC (1307786198)
[    0.747072] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.747074] EDD information not available.
[    0.747116] Freeing unused kernel memory: 668k freed
[    0.747526] Write protecting the kernel text: 4676k
[    0.747555] Write protecting the kernel read-only data: 1844k
[    0.764882] udev: starting version 151
[    0.856673] Linux agpgart interface v0.103
[    0.858854] ahci 0000:00:12.0: version 3.0
[    0.858874]   alloc irq_desc for 22 on node -1
[    0.858876]   alloc kstat_irqs on node -1
[    0.858883] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.858912] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    0.859014] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.859018] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pmp pio ccc 
[    0.862352] atl1 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.862362] atl1 0000:02:00.0: setting latency timer to 64
[    0.862380] atl1 0000:02:00.0: version 2.1.3
[    0.876180] scsi0 : ahci
[    0.877292] scsi1 : ahci
[    0.877381] scsi2 : ahci
[    0.877462] scsi3 : ahci
[    0.877571] ata1: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fff900 irq 22
[    0.877574] ata2: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fff980 irq 22
[    0.877578] ata3: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fffa00 irq 22
[    0.877581] ata4: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fffa80 irq 22
[    0.877778] scsi4 : pata_atiixp
[    0.877852] scsi5 : pata_atiixp
[    0.878805] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    0.878807] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    0.976021] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    1.151622] usb 3-2: configuration #1 chosen from 1 choice
[    1.200095] ata4: SATA link down (SStatus 0 SControl 300)
[    1.288019] usb 6-2: new low speed USB device using ohci_hcd and address 2
[    1.360017] ata3: softreset failed (device not ready)
[    1.360020] ata3: applying SB600 PMP SRST workaround and retrying
[    1.360036] ata2: softreset failed (device not ready)
[    1.360039] ata2: applying SB600 PMP SRST workaround and retrying
[    1.360054] ata1: softreset failed (device not ready)
[    1.360057] ata1: applying SB600 PMP SRST workaround and retrying
[    1.458118] usb 6-2: configuration #1 chosen from 1 choice
[    1.465040] usbcore: registered new interface driver hiddev
[    1.473750] input: Genius Wireless Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input3
[    1.473834] generic-usb 0003:0458:0046.0001: input,hidraw0: USB HID v1.10 Mouse [Genius Wireless Mouse] on usb-0000:00:13.1-2/input0
[    1.483242] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:13.4/usb6/6-2/6-2:1.0/input/input4
[    1.483292] generic-usb 0003:04D9:1203.0002: input,hidraw1: USB HID v1.11 Keyboard [HID 04d9:1203] on usb-0000:00:13.4-2/input0
[    1.503120] input: HID 04d9:1203 as /devices/pci0000:00/0000:00:13.4/usb6/6-2/6-2:1.1/input/input5
[    1.503190] generic-usb 0003:04D9:1203.0003: input,hidraw2: USB HID v1.11 Device [HID 04d9:1203] on usb-0000:00:13.4-2/input1
[    1.503212] usbcore: registered new interface driver usbhid
[    1.503214] usbhid: v2.6:USB HID core driver
[    1.524032] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.524061] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.524081] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.524532] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100
[    1.524550] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.524916] ata1.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133
[    1.524919] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.524935] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.525269] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.525271] ata2.00: configured for UDMA/100
[    1.525865] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.525867] ata1.00: configured for UDMA/133
[    1.526019] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[    1.526168] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.526254] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.526290] sd 0:0:0:0: [sda] Write Protect is off
[    1.526292] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.526310] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.526419]  sda:
[    1.526766] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5
[    1.526936] ata3.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.526938] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.526955] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.529058] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.529061] ata3.00: configured for UDMA/133
[    1.530063] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.530066] Uniform CD-ROM driver Revision: 3.20
[    1.530144] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.530196] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.530312] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.530429] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.530508] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.530543] sd 2:0:0:0: [sdb] Write Protect is off
[    1.530546] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.530564] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.530733]  sdb: sda1 sda2 < sdb1
[    1.535208] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.540869]  sda5 sda6 sda7 sda8 >
[    1.580916] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.184564] uvesafb: NVIDIA Corporation, G84 Board - p402h01 , Chip Rev   , OEM: NVIDIA, VBE v3.0
[    2.203635] uvesafb: protected mode interface info at c000:b480
[    2.203639] uvesafb: pmi: set display start = c00cb4e3, set palette = c00cb53e
[    2.203641] uvesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    2.269967] uvesafb: VBIOS/hardware supports DDC2 transfers
[    2.365911] uvesafb: monitor limits: vf = 61 Hz, hf = 75 kHz, clk = 170 MHz
[    2.366194] uvesafb: scrolling: ywrap using protected mode interface, yres_virtual=3584
[    2.366670] uvesafb: framebuffer at 0xfb000000, mapped to 0xf8200000, using 14336k, total 14336k
[    2.366673] fb0: VESA VGA frame buffer device
[    2.597850] Console: switching to colour frame buffer device 128x48
[    2.910729] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   11.643186] Adding 999416k swap on /dev/sda5.  Priority:-1 extents:1 across:999416k 
[   11.652184] udev: starting version 151
[   11.713930] lp: driver loaded but no devices found
[   11.743404] udev: renamed network interface eth0 to eth1
[   11.762134] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   11.763610] vga16fb: initializing
[   11.763614] vga16fb: mapped to 0xc00a0000
[   11.763619] vga16fb: not registering due to another framebuffer present
[   11.909567] type=1505 audit(1307797009.661:2):  operation="profile_load" pid=688 name="/sbin/dhclient3"
[   11.909793] type=1505 audit(1307797009.661:3):  operation="profile_load" pid=688 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.909920] type=1505 audit(1307797009.661:4):  operation="profile_load" pid=688 name="/usr/lib/connman/scripts/dhclient-script"
[   11.914157] type=1505 audit(1307797009.665:5):  operation="profile_replace" pid=720 name="/sbin/dhclient3"
[   11.914401] type=1505 audit(1307797009.665:6):  operation="profile_replace" pid=720 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.914535] type=1505 audit(1307797009.665:7):  operation="profile_replace" pid=720 name="/usr/lib/connman/scripts/dhclient-script"
[   11.921042] nvidia: module license 'NVIDIA' taints kernel.
[   11.921046] Disabling lock debugging due to kernel taint
[   12.153891] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   12.746436] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.835204] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.905882] hda_codec: ALC883: BIOS auto-probing.
[   12.907285] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[   12.994265] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.994275] nvidia 0000:01:00.0: setting latency timer to 64
[   12.994280] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.994513] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   12.996078] psmouse serio1: ID: 10 00 64
[   13.544007] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   15.422094] type=1505 audit(1307797013.173:8):  operation="profile_replace" pid=937 name="/sbin/dhclient3"
[   15.422334] type=1505 audit(1307797013.173:9):  operation="profile_replace" pid=937 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.422468] type=1505 audit(1307797013.173:10):  operation="profile_replace" pid=937 name="/usr/lib/connman/scripts/dhclient-script"
[   15.423070] type=1505 audit(1307797013.173:11):  operation="profile_load" pid=936 name="/usr/share/gdm/guest-session/Xsession"
[   15.476604]   alloc irq_desc for 26 on node -1
[   15.476608]   alloc kstat_irqs on node -1
[   15.476624] atl1 0000:02:00.0: irq 26 for MSI/MSI-X
[   15.476711] atl1 0000:02:00.0: eth1 link is up 100 Mbps full duplex
```

gracias!

---

### Post by granjero on 2011-06-11
acá parece haber errores

```
jm@pc-jm:~$ tail -n 50 /var/log/kern.log 
Jun 11 11:32:45 pc-jm kernel: [ 5767.771346] ata1.00: cmd 60/08:00:30:c0:0f/00:00:11:00:00/40 tag 0 ncq 4096 in
Jun 11 11:32:45 pc-jm kernel: [ 5767.771347]          res 41/40:00:33:c0:0f/00:00:11:00:00/40 Emask 0x409 (media error) <F>
Jun 11 11:32:45 pc-jm kernel: [ 5767.771350] ata1.00: status: { DRDY ERR }
Jun 11 11:32:45 pc-jm kernel: [ 5767.771352] ata1.00: error: { UNC }
Jun 11 11:32:45 pc-jm kernel: [ 5767.772249] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:45 pc-jm kernel: [ 5767.773219] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:45 pc-jm kernel: [ 5767.773222] ata1.00: configured for UDMA/133
Jun 11 11:32:45 pc-jm kernel: [ 5767.773234] ata1: EH complete
Jun 11 11:32:48 pc-jm kernel: [ 5770.821198] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun 11 11:32:48 pc-jm kernel: [ 5770.821202] ata1.00: irq_stat 0x40000008
Jun 11 11:32:48 pc-jm kernel: [ 5770.821206] ata1.00: failed command: READ FPDMA QUEUED
Jun 11 11:32:48 pc-jm kernel: [ 5770.821212] ata1.00: cmd 60/08:00:30:c0:0f/00:00:11:00:00/40 tag 0 ncq 4096 in
Jun 11 11:32:48 pc-jm kernel: [ 5770.821213]          res 41/40:00:33:c0:0f/00:00:11:00:00/40 Emask 0x409 (media error) <F>
Jun 11 11:32:48 pc-jm kernel: [ 5770.821215] ata1.00: status: { DRDY ERR }
Jun 11 11:32:48 pc-jm kernel: [ 5770.821217] ata1.00: error: { UNC }
Jun 11 11:32:48 pc-jm kernel: [ 5770.822123] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:48 pc-jm kernel: [ 5770.823086] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:48 pc-jm kernel: [ 5770.823089] ata1.00: configured for UDMA/133
Jun 11 11:32:48 pc-jm kernel: [ 5770.823100] ata1: EH complete
Jun 11 11:32:51 pc-jm kernel: [ 5773.871194] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun 11 11:32:51 pc-jm kernel: [ 5773.871198] ata1.00: irq_stat 0x40000008
Jun 11 11:32:51 pc-jm kernel: [ 5773.871202] ata1.00: failed command: READ FPDMA QUEUED
Jun 11 11:32:51 pc-jm kernel: [ 5773.871208] ata1.00: cmd 60/08:00:30:c0:0f/00:00:11:00:00/40 tag 0 ncq 4096 in
Jun 11 11:32:51 pc-jm kernel: [ 5773.871209]          res 41/40:00:33:c0:0f/00:00:11:00:00/40 Emask 0x409 (media error) <F>
Jun 11 11:32:51 pc-jm kernel: [ 5773.871211] ata1.00: status: { DRDY ERR }
Jun 11 11:32:51 pc-jm kernel: [ 5773.871213] ata1.00: error: { UNC }
Jun 11 11:32:51 pc-jm kernel: [ 5773.872112] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:51 pc-jm kernel: [ 5773.873110] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:51 pc-jm kernel: [ 5773.873113] ata1.00: configured for UDMA/133
Jun 11 11:32:51 pc-jm kernel: [ 5773.873124] ata1: EH complete
Jun 11 11:32:54 pc-jm kernel: [ 5776.921122] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun 11 11:32:54 pc-jm kernel: [ 5776.921126] ata1.00: irq_stat 0x40000008
Jun 11 11:32:54 pc-jm kernel: [ 5776.921130] ata1.00: failed command: READ FPDMA QUEUED
Jun 11 11:32:54 pc-jm kernel: [ 5776.921136] ata1.00: cmd 60/08:00:30:c0:0f/00:00:11:00:00/40 tag 0 ncq 4096 in
Jun 11 11:32:54 pc-jm kernel: [ 5776.921137]          res 41/40:00:33:c0:0f/00:00:11:00:00/40 Emask 0x409 (media error) <F>
Jun 11 11:32:54 pc-jm kernel: [ 5776.921139] ata1.00: status: { DRDY ERR }
Jun 11 11:32:54 pc-jm kernel: [ 5776.921141] ata1.00: error: { UNC }
Jun 11 11:32:54 pc-jm kernel: [ 5776.922029] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:54 pc-jm kernel: [ 5776.923008] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:54 pc-jm kernel: [ 5776.923010] ata1.00: configured for UDMA/133
Jun 11 11:32:54 pc-jm kernel: [ 5776.923023] sd 0:0:0:0: [sda] Unhandled sense code
Jun 11 11:32:54 pc-jm kernel: [ 5776.923025] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 11 11:32:54 pc-jm kernel: [ 5776.923028] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 11:32:54 pc-jm kernel: [ 5776.923033] Descriptor sense data with sense descriptors (in hex):
Jun 11 11:32:54 pc-jm kernel: [ 5776.923034]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 11:32:54 pc-jm kernel: [ 5776.923042]         11 0f c0 33 
Jun 11 11:32:54 pc-jm kernel: [ 5776.923046] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 11:32:54 pc-jm kernel: [ 5776.923050] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 11 0f c0 30 00 00 08 00
Jun 11 11:32:54 pc-jm kernel: [ 5776.923058] end_request: I/O error, dev sda, sector 286244915
Jun 11 11:32:54 pc-jm kernel: [ 5776.923082] ata1: EH complete

```

---

### Post by granjero on 2011-06-11
y acá también

```
jm@pc-jm:~$ tail -n 50 /var/log/messages 
Jun 11 11:37:51 pc-jm kernel: [ 6074.191900] ata1.00: configured for UDMA/133
Jun 11 11:37:51 pc-jm kernel: [ 6074.191912] ata1: EH complete
Jun 11 11:37:55 pc-jm kernel: [ 6077.398591] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:55 pc-jm kernel: [ 6077.399555] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:55 pc-jm kernel: [ 6077.399558] ata1.00: configured for UDMA/133
Jun 11 11:37:55 pc-jm kernel: [ 6077.399576] sd 0:0:0:0: [sda] Unhandled sense code
Jun 11 11:37:55 pc-jm kernel: [ 6077.399578] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 11 11:37:55 pc-jm kernel: [ 6077.399581] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 11:37:55 pc-jm kernel: [ 6077.399585] Descriptor sense data with sense descriptors (in hex):
Jun 11 11:37:55 pc-jm kernel: [ 6077.399587]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 11:37:55 pc-jm kernel: [ 6077.399594]         11 0f c0 33 
Jun 11 11:37:55 pc-jm kernel: [ 6077.399598] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 11:37:55 pc-jm kernel: [ 6077.399602] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 11 0f c0 30 00 00 08 00
Jun 11 11:37:55 pc-jm kernel: [ 6077.399626] ata1: EH complete
Jun 11 11:37:55 pc-jm pulseaudio[1570]: ratelimit.c: 142 events suppressed
Jun 11 11:37:55 pc-jm pulseaudio[1570]: asyncq.c: q overrun, queuing locally
Jun 11 11:38:26 pc-jm pulseaudio[1570]: last message repeated 10 times
Jun 11 11:42:39 pc-jm kernel: [ 6361.675442] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:39 pc-jm kernel: [ 6361.676407] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:39 pc-jm kernel: [ 6361.676409] ata1.00: configured for UDMA/133
Jun 11 11:42:39 pc-jm kernel: [ 6361.676421] ata1: EH complete
Jun 11 11:42:42 pc-jm kernel: [ 6364.883763] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:42 pc-jm kernel: [ 6364.884747] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:42 pc-jm kernel: [ 6364.884750] ata1.00: configured for UDMA/133
Jun 11 11:42:42 pc-jm kernel: [ 6364.884762] ata1: EH complete
Jun 11 11:42:46 pc-jm kernel: [ 6368.258687] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:46 pc-jm kernel: [ 6368.259682] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:46 pc-jm kernel: [ 6368.259685] ata1.00: configured for UDMA/133
Jun 11 11:42:46 pc-jm kernel: [ 6368.259691] ata1: EH complete
Jun 11 11:42:49 pc-jm kernel: [ 6371.308627] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:49 pc-jm kernel: [ 6371.309618] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:49 pc-jm kernel: [ 6371.309621] ata1.00: configured for UDMA/133
Jun 11 11:42:49 pc-jm kernel: [ 6371.309627] ata1: EH complete
Jun 11 11:42:52 pc-jm kernel: [ 6374.516880] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:52 pc-jm kernel: [ 6374.517846] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:52 pc-jm kernel: [ 6374.517849] ata1.00: configured for UDMA/133
Jun 11 11:42:52 pc-jm kernel: [ 6374.517860] ata1: EH complete
Jun 11 11:42:55 pc-jm kernel: [ 6377.733447] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:55 pc-jm kernel: [ 6377.734408] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:55 pc-jm kernel: [ 6377.734411] ata1.00: configured for UDMA/133
Jun 11 11:42:55 pc-jm kernel: [ 6377.734423] sd 0:0:0:0: [sda] Unhandled sense code
Jun 11 11:42:55 pc-jm kernel: [ 6377.734425] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 11 11:42:55 pc-jm kernel: [ 6377.734428] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 11:42:55 pc-jm kernel: [ 6377.734432] Descriptor sense data with sense descriptors (in hex):
Jun 11 11:42:55 pc-jm kernel: [ 6377.734434]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 11:42:55 pc-jm kernel: [ 6377.734442]         11 0f c0 33 
Jun 11 11:42:55 pc-jm kernel: [ 6377.734445] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 11:42:55 pc-jm kernel: [ 6377.734449] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 11 0f c0 30 00 00 08 00
Jun 11 11:42:55 pc-jm kernel: [ 6377.734477] ata1: EH complete
Jun 11 11:42:56 pc-jm pulseaudio[1570]: ratelimit.c: 94 events suppressed
jm@pc-jm:~$ tail -n 150 /var/log/messages 
Jun 11 11:31:35 pc-jm kernel: [ 5697.591470] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:35 pc-jm kernel: [ 5697.591473] ata1.00: configured for UDMA/133
Jun 11 11:31:35 pc-jm kernel: [ 5697.591487] ata1: EH complete
Jun 11 11:31:38 pc-jm kernel: [ 5700.607105] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:38 pc-jm kernel: [ 5700.608071] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:38 pc-jm kernel: [ 5700.608073] ata1.00: configured for UDMA/133
Jun 11 11:31:38 pc-jm kernel: [ 5700.608094] sd 0:0:0:0: [sda] Unhandled sense code
Jun 11 11:31:38 pc-jm kernel: [ 5700.608096] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 11 11:31:38 pc-jm kernel: [ 5700.608099] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 11:31:38 pc-jm kernel: [ 5700.608103] Descriptor sense data with sense descriptors (in hex):
Jun 11 11:31:38 pc-jm kernel: [ 5700.608105]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 11:31:38 pc-jm kernel: [ 5700.608112]         01 1a d3 e4 
Jun 11 11:31:38 pc-jm kernel: [ 5700.608116] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 11:31:38 pc-jm kernel: [ 5700.608120] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 01 1a d3 e0 00 00 08 00
Jun 11 11:31:38 pc-jm kernel: [ 5700.608143] ata1: EH complete
Jun 11 11:31:38 pc-jm pulseaudio[1570]: asyncq.c: q overrun, queuing locally
Jun 11 11:31:41 pc-jm pulseaudio[1570]: last message repeated 10 times
Jun 11 11:31:41 pc-jm kernel: [ 5703.998849] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:41 pc-jm kernel: [ 5703.999829] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:41 pc-jm kernel: [ 5703.999832] ata1.00: configured for UDMA/133
Jun 11 11:31:41 pc-jm kernel: [ 5703.999845] ata1: EH complete
Jun 11 11:31:44 pc-jm kernel: [ 5707.173653] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:44 pc-jm kernel: [ 5707.174618] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:44 pc-jm kernel: [ 5707.174621] ata1.00: configured for UDMA/133
Jun 11 11:31:44 pc-jm kernel: [ 5707.174632] ata1: EH complete
Jun 11 11:31:47 pc-jm kernel: [ 5710.190221] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:47 pc-jm kernel: [ 5710.191186] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:47 pc-jm kernel: [ 5710.191189] ata1.00: configured for UDMA/133
Jun 11 11:31:47 pc-jm kernel: [ 5710.191202] ata1: EH complete
Jun 11 11:31:50 pc-jm kernel: [ 5713.206848] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:50 pc-jm kernel: [ 5713.207817] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:50 pc-jm kernel: [ 5713.207820] ata1.00: configured for UDMA/133
Jun 11 11:31:50 pc-jm kernel: [ 5713.207831] ata1: EH complete
Jun 11 11:31:53 pc-jm kernel: [ 5716.223423] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:53 pc-jm kernel: [ 5716.224384] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:53 pc-jm kernel: [ 5716.224387] ata1.00: configured for UDMA/133
Jun 11 11:31:53 pc-jm kernel: [ 5716.224399] ata1: EH complete
Jun 11 11:31:57 pc-jm kernel: [ 5719.556678] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:57 pc-jm kernel: [ 5719.557672] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:31:57 pc-jm kernel: [ 5719.557675] ata1.00: configured for UDMA/133
Jun 11 11:31:57 pc-jm kernel: [ 5719.557687] sd 0:0:0:0: [sda] Unhandled sense code
Jun 11 11:31:57 pc-jm kernel: [ 5719.557689] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 11 11:31:57 pc-jm kernel: [ 5719.557692] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 11:31:57 pc-jm kernel: [ 5719.557696] Descriptor sense data with sense descriptors (in hex):
Jun 11 11:31:57 pc-jm kernel: [ 5719.557698]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 11:31:57 pc-jm kernel: [ 5719.557706]         01 1a d3 e4 
Jun 11 11:31:57 pc-jm kernel: [ 5719.557709] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 11:31:57 pc-jm kernel: [ 5719.557713] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 01 1a d3 e0 00 00 08 00
Jun 11 11:31:57 pc-jm kernel: [ 5719.557737] ata1: EH complete
Jun 11 11:31:58 pc-jm pulseaudio[1570]: ratelimit.c: 386 events suppressed
Jun 11 11:32:39 pc-jm kernel: [ 5761.672404] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:39 pc-jm kernel: [ 5761.673384] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:39 pc-jm kernel: [ 5761.673387] ata1.00: configured for UDMA/133
Jun 11 11:32:39 pc-jm kernel: [ 5761.673398] ata1: EH complete
Jun 11 11:32:42 pc-jm kernel: [ 5764.722319] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:42 pc-jm kernel: [ 5764.723283] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:42 pc-jm kernel: [ 5764.723286] ata1.00: configured for UDMA/133
Jun 11 11:32:42 pc-jm kernel: [ 5764.723297] ata1: EH complete
Jun 11 11:32:45 pc-jm kernel: [ 5767.772249] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:45 pc-jm kernel: [ 5767.773219] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:45 pc-jm kernel: [ 5767.773222] ata1.00: configured for UDMA/133
Jun 11 11:32:45 pc-jm kernel: [ 5767.773234] ata1: EH complete
Jun 11 11:32:48 pc-jm kernel: [ 5770.822123] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:48 pc-jm kernel: [ 5770.823086] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:48 pc-jm kernel: [ 5770.823089] ata1.00: configured for UDMA/133
Jun 11 11:32:48 pc-jm kernel: [ 5770.823100] ata1: EH complete
Jun 11 11:32:51 pc-jm kernel: [ 5773.872112] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:51 pc-jm kernel: [ 5773.873110] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:51 pc-jm kernel: [ 5773.873113] ata1.00: configured for UDMA/133
Jun 11 11:32:51 pc-jm kernel: [ 5773.873124] ata1: EH complete
Jun 11 11:32:54 pc-jm kernel: [ 5776.922029] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:54 pc-jm kernel: [ 5776.923008] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:32:54 pc-jm kernel: [ 5776.923010] ata1.00: configured for UDMA/133
Jun 11 11:32:54 pc-jm kernel: [ 5776.923023] sd 0:0:0:0: [sda] Unhandled sense code
Jun 11 11:32:54 pc-jm kernel: [ 5776.923025] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 11 11:32:54 pc-jm kernel: [ 5776.923028] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 11:32:54 pc-jm kernel: [ 5776.923033] Descriptor sense data with sense descriptors (in hex):
Jun 11 11:32:54 pc-jm kernel: [ 5776.923034]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 11:32:54 pc-jm kernel: [ 5776.923042]         11 0f c0 33 
Jun 11 11:32:54 pc-jm kernel: [ 5776.923046] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 11:32:54 pc-jm kernel: [ 5776.923050] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 11 0f c0 30 00 00 08 00
Jun 11 11:32:54 pc-jm kernel: [ 5776.923082] ata1: EH complete
Jun 11 11:37:39 pc-jm kernel: [ 6061.665614] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:39 pc-jm kernel: [ 6061.666580] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:39 pc-jm kernel: [ 6061.666583] ata1.00: configured for UDMA/133
Jun 11 11:37:39 pc-jm kernel: [ 6061.666595] ata1: EH complete
Jun 11 11:37:42 pc-jm kernel: [ 6064.873874] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:42 pc-jm kernel: [ 6064.874839] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:42 pc-jm kernel: [ 6064.874842] ata1.00: configured for UDMA/133
Jun 11 11:37:42 pc-jm kernel: [ 6064.874854] ata1: EH complete
Jun 11 11:37:45 pc-jm kernel: [ 6067.923813] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:45 pc-jm kernel: [ 6067.924800] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:45 pc-jm kernel: [ 6067.924802] ata1.00: configured for UDMA/133
Jun 11 11:37:45 pc-jm kernel: [ 6067.924811] ata1: EH complete
Jun 11 11:37:48 pc-jm kernel: [ 6071.140402] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:48 pc-jm kernel: [ 6071.141365] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:48 pc-jm kernel: [ 6071.141368] ata1.00: configured for UDMA/133
Jun 11 11:37:48 pc-jm kernel: [ 6071.141379] ata1: EH complete
Jun 11 11:37:51 pc-jm kernel: [ 6074.190902] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:51 pc-jm kernel: [ 6074.191897] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:51 pc-jm kernel: [ 6074.191900] ata1.00: configured for UDMA/133
Jun 11 11:37:51 pc-jm kernel: [ 6074.191912] ata1: EH complete
Jun 11 11:37:55 pc-jm kernel: [ 6077.398591] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:55 pc-jm kernel: [ 6077.399555] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:37:55 pc-jm kernel: [ 6077.399558] ata1.00: configured for UDMA/133
Jun 11 11:37:55 pc-jm kernel: [ 6077.399576] sd 0:0:0:0: [sda] Unhandled sense code
Jun 11 11:37:55 pc-jm kernel: [ 6077.399578] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 11 11:37:55 pc-jm kernel: [ 6077.399581] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 11:37:55 pc-jm kernel: [ 6077.399585] Descriptor sense data with sense descriptors (in hex):
Jun 11 11:37:55 pc-jm kernel: [ 6077.399587]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 11:37:55 pc-jm kernel: [ 6077.399594]         11 0f c0 33 
Jun 11 11:37:55 pc-jm kernel: [ 6077.399598] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 11:37:55 pc-jm kernel: [ 6077.399602] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 11 0f c0 30 00 00 08 00
Jun 11 11:37:55 pc-jm kernel: [ 6077.399626] ata1: EH complete
Jun 11 11:37:55 pc-jm pulseaudio[1570]: ratelimit.c: 142 events suppressed
Jun 11 11:37:55 pc-jm pulseaudio[1570]: asyncq.c: q overrun, queuing locally
Jun 11 11:38:26 pc-jm pulseaudio[1570]: last message repeated 10 times
Jun 11 11:42:39 pc-jm kernel: [ 6361.675442] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:39 pc-jm kernel: [ 6361.676407] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:39 pc-jm kernel: [ 6361.676409] ata1.00: configured for UDMA/133
Jun 11 11:42:39 pc-jm kernel: [ 6361.676421] ata1: EH complete
Jun 11 11:42:42 pc-jm kernel: [ 6364.883763] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:42 pc-jm kernel: [ 6364.884747] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:42 pc-jm kernel: [ 6364.884750] ata1.00: configured for UDMA/133
Jun 11 11:42:42 pc-jm kernel: [ 6364.884762] ata1: EH complete
Jun 11 11:42:46 pc-jm kernel: [ 6368.258687] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:46 pc-jm kernel: [ 6368.259682] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:46 pc-jm kernel: [ 6368.259685] ata1.00: configured for UDMA/133
Jun 11 11:42:46 pc-jm kernel: [ 6368.259691] ata1: EH complete
Jun 11 11:42:49 pc-jm kernel: [ 6371.308627] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:49 pc-jm kernel: [ 6371.309618] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:49 pc-jm kernel: [ 6371.309621] ata1.00: configured for UDMA/133
Jun 11 11:42:49 pc-jm kernel: [ 6371.309627] ata1: EH complete
Jun 11 11:42:52 pc-jm kernel: [ 6374.516880] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:52 pc-jm kernel: [ 6374.517846] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:52 pc-jm kernel: [ 6374.517849] ata1.00: configured for UDMA/133
Jun 11 11:42:52 pc-jm kernel: [ 6374.517860] ata1: EH complete
Jun 11 11:42:55 pc-jm kernel: [ 6377.733447] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:55 pc-jm kernel: [ 6377.734408] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jun 11 11:42:55 pc-jm kernel: [ 6377.734411] ata1.00: configured for UDMA/133
Jun 11 11:42:55 pc-jm kernel: [ 6377.734423] sd 0:0:0:0: [sda] Unhandled sense code
Jun 11 11:42:55 pc-jm kernel: [ 6377.734425] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 11 11:42:55 pc-jm kernel: [ 6377.734428] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 11 11:42:55 pc-jm kernel: [ 6377.734432] Descriptor sense data with sense descriptors (in hex):
Jun 11 11:42:55 pc-jm kernel: [ 6377.734434]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun 11 11:42:55 pc-jm kernel: [ 6377.734442]         11 0f c0 33 
Jun 11 11:42:55 pc-jm kernel: [ 6377.734445] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 11 11:42:55 pc-jm kernel: [ 6377.734449] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 11 0f c0 30 00 00 08 00
Jun 11 11:42:55 pc-jm kernel: [ 6377.734477] ata1: EH complete
Jun 11 11:42:56 pc-jm pulseaudio[1570]: ratelimit.c: 94 events suppressed
jm@pc-jm:~$ 

```

Pareciera ser el disco rígido. no?

---

### Post by granjero on 2011-06-11
bootié desde un usb y corrí fsck por las dudas pero dice estar limpio.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x0004107b

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *       36303       38913    20972857+   7  HPFS/NTFS
/dev/sda2               1       36302   291594241    5  Extendida
/dev/sda5               1         125      999424   82  Linux swap / Solaris
/dev/sda6             125        1370     9999360   83  Linux
/dev/sda7            1370       26269   199999488   83  Linux
/dev/sda8           26270       28879    20964793+   7  HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x0007490a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1      121601   976760001   83  Linux

Disco /dev/sdc: 2031 MB, 2031091712 bytes
63 cabezas, 62 sectores/pista, 1015 cilindros
Unidades = cilindros de 3906 * 512 = 1999872 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00008371

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1        1015     1982264    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck desde util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda6: limpio, 334219/625856 ficheros, 1433943/2499840 bloques
ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck desde util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda6: limpio, 334219/625856 ficheros, 1433943/2499840 bloques
ubuntu@ubuntu:~$ 

```

salud!

---

### Post by guillermolisi on 2011-06-11
Segun interpreto de los ultimos dos logs, en /dev/sda tenes errores.

Como, con que opciones, corriste fsck ?

Si estuviera en tu lugar, inicio con un Live CD y corro en una consola/terminal ```
sudo badblocks -nsv /dev/sd<letra_que_identifique_disco_fisico>
```

Con esas opciones le decis que haga un test no destructivo de lectura-escritura, que te muestre la barra de avance y la informacion detallada de lo que hace y encuentra.

Opcionalmente podes agregarle la opcion -p <numero> para que vuelva a correr un <numero> de veces adicionales en forma continua (y no tener que hacerlo a mano si aun hay bloques defectuosos).

---

### Post by juancarlospaco on 2011-06-12
Veo un Disco nuevo en tu futuro...

---

### Post by granjero on 2011-06-12
en la utilidad de discos dice que hay errores. dejo una captura de pantalla.

salud!

---

### Post by biale on 2011-06-12
Y desde la misma utilidad de discos los parámetros 1 a 10 como andan?

---

### Post by granjero on 2011-06-13
biale, no encuentro donde están los parámetros que decís....

guillermo me había olvidado de responder una pregunta que me hiciste...

fsck lo corri así ```
sudo fsck /dev/sda6 y sudo fsck /dev/sda7
```

hoy a la noche me fijo lo de los badblocks.

gracias por todo!

---

### Post by guillermolisi on 2011-06-13
> **granjero said:**
> biale, no encuentro donde están los parámetros que decís....

guillermo me había olvidado de responder una pregunta que me hiciste...

fsck lo corri así ```
sudo fsck /dev/sda6 y sudo fsck /dev/sda7
```

hoy a la noche me fijo lo de los badblocks.

gracias por todo!
fsck usado de esa forma no verifica bloques malos, solo verifica que la estructura del sistema de archivos sea consistente. Es decir, no me parece determinante ni resuelve problemas de superficie de disco.

badblocks remapea los sectores dañados dejando habilitados solo los sectores que verificaron las pruebas y si la cantidad de bloques malos es alta, el disco queda con menos capacidad pero confiable (si es que no se esta degradando).

---

### Post by biale on 2011-06-13
Me refiero al mismo pantallazo que posteaste, pero mas arriba. Los primeros parámetros que muestra.

Además: Podemos descartar alguna vibración (ventilador) que este sufriendo el HDD o algún problema en cable/ conector, fuente de poder, etc?

Guillermo: hasta donde yo se badblocks tampoco los remapea. Lo que hace es forzar una detección de todos los problemas en una partición de disco.

---

### Post by guillermolisi on 2011-06-13
> **biale said:**
> 
Guillermo: hasta donde yo se badblocks tampoco los remapea. Lo que hace es forzar una detección de todos los problemas en una partición de disco.
Fijate que con los parametros que aconseje al final del proceso actualiza la lista de sectores defectuosos (se detiene y te pregunta si la queres actualizar). Esto sucede porque efectivamente remapea los sectores defectuosos hasta el limite del area reservada para este fin en el disco (si no fuera asi, para que te preguntaria si queres actualizar la lista de bloques defectuosos ?).

Ademas, en el man dice que la opcion de pasadas generalmente se utiliza para asegurarse de que no queden sectores dañados sin marcar (corriendo varias veces el utilitario).

Edit: Leyendo en la web en busca de confirmar mi parecer, creo que tengo que darle la razon a Biale. Hasta aqui, toda referencia al funcionamiento del comando solo habla de marcar el bloque defectuoso para que no se vuelva a usar, pero en ningun lado se menciona el remapeo, como si sucede en Unix (por lo menos en SCO).

---

### Post by granjero on 2011-06-14
biale, ahí cuelgo otra captura!
guillermo, si ejecuto ```
sudo badblocks -nsv /dev/sda
``` desde un live-usb me dice que sda está siendo usado. seguro es por la swap no?

si le doy ```
sudo badblocks -nsv /dev/sda6
``` empieza el proceso pero el cálculo que hice es que va a tardar 8,9 horas.

le di ctrl+c para salir. Es seguro dejarlo corriendo e ir a trabajar o dormir? o es interactivo?

salud!

---

### Post by guillermolisi on 2011-06-14
> **granjero said:**
> biale, ahí cuelgo otra captura!
guillermo, si ejecuto ```
sudo badblocks -nsv /dev/sda
``` desde un live-usb me dice que sda está siendo usado. seguro es por la swap no?

si le doy ```
sudo badblocks -nsv /dev/sda6
``` empieza el proceso pero el cálculo que hice es que va a tardar 8,9 horas.

le di ctrl+c para salir. Es seguro dejarlo corriendo e ir a trabajar o dormir? o es interactivo?

salud!
El analisis que se realiza es por particion (yo te indique mal oportunamente) asi que esta bien que sea del tipo /dev/sd<xy> donde "x" determina la unidad fisica e "y" la particion.

Ademas hiciste muy bien en hacer el comentario porque si el Live CD encuentra una particion con swap la utiliza, asi que tenes que entrar con Gparted (o equivalente) y desactivar el uso de swap (swap off) si queres verificar esa particion.

Hay un momento de interaccion con el usuario pero generalmente se da al final del proceso y queda esperando que se le ingrese una respuesta, asi que tranquilamente podes dejarlo por la noche y retomarlo a la mañana siguiente, por ejemplo, si te resulta mas practico.

Edit: El calculo de la demora es estimativo porque depende de dos factores: el tamaño del disco y la cantidad de sectores defectuosos que encuentre. La ultima vez lo corri sobre un disco de 60Gb y demoro 15 horas y algo mas.

---

### Post by biale on 2011-06-14
Con mucha RAM y usando el parametro "-c" avanzaba a razon de 30 Gbytes cada 45 minutos. Sobre partición no montada:
```

sudo badblocks -nvs -c 512 /dev/sda1 

```

Sobre si es o no es seguro, la realidad es que el disco "ya" esta fallando y no puede saberse hasta adonde es confiable. Yo hice un backup previo por las dudas. Y hasta pude ubicar un  archivo dañado.

Pero los problemas siguieron. Hasta que por casualidad decidí retirar el ventilador de disco (vibraciones!) y desde ese momento el disco funciona sin novedad. Parece que 1 Tera es un número mágico que genera discos mas sensibles; a partir de los 1,5 Tera la tecnología cambia y requiere alguna precaución con el formateo de los discos.

En su momento y para fijar todo bastante mas rápido (1 tera, aprox 3 hs) usé el utilitario de WD (bajo DOS) DLGDiagv519.exe  Lo corri ubicado en un pendrive USB bajo un arranque live de Freedos en un CD.

---

### Post by juancarlospaco on 2011-06-15
Parece una pavada pero... 
si el disco quedara fijo, se deben colocar siempre los 4 Tornillos (2 de cada lado),
muchos acostumbran poner solo 2 tornillos del lado opuesto al mother (mas facil de colocar),
pero la verdad es que puede producir vibraciones en el otro extremo del disco, 
que a la larga, pueden llegar a perjudicar la salud del mencionado.

---

### Post by granjero on 2011-06-18
Buenas, está corriendo badblocks. Ya van 3 horas y va por el 28%.
Al final no me quedó claro si con esto los sectores malos quedan bloqueados para usos futuros. Si esto es así ¿el bloqueo permanece luego de un formateo?

Juan Carlos: el HD tiene los 4 tornillos pertinentes desde que armé la máquina. 

Esta PC sufrió varios cortes de luz. ¿Puede ser esa la causa del problema?

Salud!

---

### Post by guillermolisi on 2011-06-18
> **granjero said:**
> Buenas, está corriendo badblocks. Ya van 3 horas y va por el 28%.
Al final no me quedó claro si con esto los sectores malos quedan bloqueados para usos futuros. Si esto es así ¿el bloqueo permanece luego de un formateo?

Juan Carlos: el HD tiene los 4 tornillos pertinentes desde que armé la máquina. 

Esta PC sufrió varios cortes de luz. ¿Puede ser esa la causa del problema?

Salud!
Los bloques quedan marcados. No se si formateando para NTFS, u otro FS =! ext* respeta las marcas.

Los cortes de energia afectan, sobre todo si son repetitivos en el corto lazo (por eso antes de levantar una maquina es preferible esperar unos minutos para verificar que el suministro se estabilizo).

La forma correcta para verificar un file system ext* es invocando e2fsck ya que con la opcion -c se invoca a badblocks y como despues se verifica la consistencia del FS, se intenta recuperar datos que esten en el sector dañado (o por lo menos sabras que estas teniendo perdida de datos).

---

### Post by granjero on 2011-06-18
casi 12 horas después


```
ubuntu@ubuntu:~$ sudo badblocks -nsv /dev/sda6
Revisando los bloques dañados en modo lectura-escritura no destructivo
Del bloque 0 al 226683903
Revisando los bloques dañados (prueba de lectura-escritura no destructiva)
Probando con un patrón aleatorio: 75118656done, 3:20:46 elapsed
75118688done, 3:21:23 elapsed
75118689done, 3:21:42 elapsed
75118690done, 3:22:00 elapsed
75118691done, 3:22:19 elapsed
75118692
75118693
75118694
75118695
75118696
75118697
75118698
75118699
75118700
75118701
75118702
75118703
75118704
75118705
75118706
75118707
75118708
75118709
75118710
75118711
75118712
75118713
75118714
75118715
75118716
75118717
75118718
75118719
75118720
75118721
75118722
75118723
75122556done, 3:22:38 elapsed
75122557done, 3:22:56 elapsed
75122558done, 3:23:15 elapsed
75122559done, 3:23:33 elapsed
78532276done, 3:34:34 elapsed
78532277done, 3:34:54 elapsed
78532278done, 3:35:14 elapsed
78532279done, 3:35:33 elapsed
78562536done, 3:35:58 elapsed
78562537done, 3:36:17 elapsed
78562538done, 3:36:36 elapsed
78562539done, 3:36:55 elapsed
78566744done, 3:37:15 elapsed
78566745done, 3:37:35 elapsed
78566746done, 3:37:54 elapsed
78566747done, 3:38:14 elapsed
141121560one, 6:56:27 elapsed
141121561one, 6:56:46 elapsed
141121562one, 6:57:05 elapsed
141121563one, 6:57:24 elapsed
145143080one, 7:10:36 elapsed
145143081one, 7:10:55 elapsed
145143082one, 7:11:14 elapsed
145143083one, 7:11:34 elapsed
225101368one, 11:40:58 elapsed
225101369
225101370
225101371
225101372
hecho                               
Paso terminado, se encontraron 66 bloques dañados.
ubuntu@ubuntu:~$ 

```

al final no me pidió ninguna confirmación de nada...

me falta pasarle a la swap y a la otra partición

ya quedaron desterrados esos bloques?

salud!

---

### Post by guillermolisi on 2011-06-19
Por lo que vi, ese disco aterrizo en por lo menos tres o cuatro lugares distintos. El contar con bloques malos consecutivos da idea de que el disco posee una raya en su superficie.

Mi recomendacion seria cambiarlo.

Si queres asegurarte de que todos los bloques esten correctamente marcados, que no se volveran a usar y que no hay mas que esos, volvelo a correr.

---

