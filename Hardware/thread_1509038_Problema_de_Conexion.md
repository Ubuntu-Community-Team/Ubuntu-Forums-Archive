---
title: "Problema de Conexion"
date: 2010-06-13
forum: Hardware
---

### Post by Torals on 2010-06-13
Bueno, este es un problema que se me presento ahora..... a decir verdad, el primero que tengo con Ubuntu despues de mas de un mes de uso sin ningun problema.

Cada un cierto tiempo aleatorio (en minutos, pueden ser 10 como pueden ser 45, etc) me quedo sin conexion a internet.

Cuando paso por primera vez, como siempre, culpe a la compañia proveedora y me puse a hacer otras cosas. Reinicie la PC, ingrese con windows y vi que tenia conexion nuevamente (el modem siempre acuso conexion normal)

Vuelvo a entrar con ubuntu y si, efectivamente tuve conexion en internet.... pero a los pocos minutos se desconecto nuevamente.

Resulta que ahora es comun desde el dia de ayer... y para solucionarlo tengo que desenchufar y volver a enchufar el modem, por lo que el problema es mio evidentemente.

Probe tanto con windows como con ubuntu, en ambos tengo el mismo problema.

Alguien tiene una idea de que se tratará?

Muchas gracias

---

### Post by guillermolisi on 2010-06-13
Podes darnos caracteristicas de tu hardware, principalmente del chip de la placa de red ?
Tambien seria util saber que version de Ubuntu y que tipo de conexion a Internet estas usando.

---

### Post by Torals on 2010-06-13
> **guillermolisi said:**
> Podes darnos caracteristicas de tu hardware, principalmente del chip de la placa de red ?
Tambien seria util saber que version de Ubuntu y que tipo de conexion a Internet estas usando.

El Chip de la placa te lo debo, no se como buscarlo :P

Es una core 2 duo E5500, con disco de 160 SATA, 2G_b de Ram y tengo Conexion de 2mb por cablemodam

Uso Ubuntu 10

Gracias!

---

### Post by leonardomdq on 2010-06-14
Para saber que chip tiene la placa de red ejecuta en una consola/terminal los comandos "lspci", "lsusb" y "sudo lshw" (sin las comillas) y luego lo que te arroja en la consola pegalo aca en el post.

---

### Post by lcamueira on 2010-07-02
Buenas, Estaba buscando solucion para un tema asi....

En mi caso solo tengo instalado ubuntu, lo tengo desde la version 9.10, donde instale sin problemas internet  por medio de una placa usb wireless. Ahi funciono sin problemas, ahora al actualizar a la version 10.04 LTS empezo a hacerme lo mismo... lo q pude notar es que si tengo mucha tasa de transferencia la conexion cae mas rapido y no revive hasta reiniciar la pc, a veces son 40mb a veces 10 mb a veces 150 y no pasa nada....

Dejo mis datos de lsusb y lshw

LSHW:

lucas-desktop             
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=2077961A-6E99-DB11-BB55-001A92913B2D
  *-core
       description: Motherboard
       product: M2N-E SLI
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.XX
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS M2N-E SLI ACPI BIOS Revision 0401 (10/04/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          slot: Socket AM2
          size: 2200MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: c
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: DIMM_A1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: DIMM_B1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: DIMM_A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: DIMM_B2
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:255 ioport:fc00(size=32) ioport:4c00(size=64) ioport:4c40(size=64)
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:feb00000-feb000ff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi2
          logical name: scsi3
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8 ) ioport:3f6 ioport:170(size=8 ) ioport:376 ioport:e800(size=16)
        *-cdrom
             description: CD-R/CD-RW writer
             product: CD-RW  RW8439E
             vendor: CREATIVE
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1R09
             serial: [CREATIVECD-RW  RW8439E  1R090
             capabilities: removable audio cd-r cd-rw
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: Maxtor 92041U4
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: FA52
             serial: G40WDW4C
             size: 19GiB (20GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=01c377c9
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: a04d-ef1d
                size: 19GiB
                capacity: 19GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-05-16 14:14:28 filesystem=ntfs state=clean
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8 ) ioport:bf0(size=4) ioport:970(size=8 ) ioport:b70(size=4) ioport:d400(size=16) memory:fe02c000-fe02cfff
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi4
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8 ) ioport:be0(size=4) ioport:960(size=8 ) ioport:b60(size=4) ioport:c000(size=16) memory:fe02b000-fe02bfff
        *-disk
             description: ATA Disk
             product: WDC WD1600JS-00N
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 10.0
             serial: WD-WCANMA466059
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=5c975c97
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: 02ca45bf-7969-4e5f-b7d3-980c7cedc8b5
                size: 143GiB
                capacity: 143GiB
                capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2010-04-09 14:15:20 filesystem=ext3 modified=2010-07-02 00:33:03 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-07-02 00:32:12 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdb2
                size: 5812MiB
                capacity: 5812MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 5812MiB
                   capabilities: nofs
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: pci bus_master
          resources: ioport:a000(size=4096) memory:fdf00000-fdffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:01:01.0
             version: c0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32
             resources: irq:17 memory:fdfff000-fdfff7ff ioport:ac00(size=128 )
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: f3
          serial: 00:1a:92:91:3b:2d
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:23 memory:fe02a000-fe02afff ioport:bc00(size=8 )
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: f3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:27 ioport:9000(size=4096) memory:f8000000-fbffffff ioport:d0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G94 [GeForce 9600 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:f8000000-f9ffffff ioport:9c00(size=128 ) memory:fbf80000-fbffffff(prefetchable)
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 08:10:74:07:3d:f9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw226 driverversion=1.55+Customer,12/21/2005,2.1.0.1 ip=192.168.1.103 link=yes multicast=yes wireless=IEEE 802.11g


LSUSB

Bus 002 Device 002: ID 0d8c:0201 C-Media Electronics, Inc. CM6501
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1286:1fab Marvell Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Por si sirve de ayuda, instale los drivers de la antena con ndiswrapper en la 9.10 y funciono barbaro, en la 10.04 lo deje como estaba y aparecio este problema, los reinstale y no cambio nada.


Saludos
:)

---

