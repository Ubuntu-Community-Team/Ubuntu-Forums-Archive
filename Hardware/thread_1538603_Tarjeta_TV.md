---
title: "Tarjeta TV"
date: 2010-07-25
forum: Hardware
---

### Post by Rick58 on 2010-07-25
Buenas tardes al foro. Hace un tiempo que intento buscar la solución al problema que tengo para utilizar una tarjeta de TV en Linux. 
La tarjeta es una Hauppage PCI 150 que viene instalada por defecto en una HP Slimline 3440la. Con Ubuntu directamente no la reconoce. He probado en opensuse, y allí la pude configurar, pero tampoco pude hacerla funcionar.  
Actualmente, tengo instalado ubuntu 10.04 funcionando perfecto, a no ser por el tema de la tarjeta.
Por favor, si hay alguien dispuesto a ver el tema y necesitan mayores datos, a vuestra disposición.
Muchas gracias.


Rick

---

### Post by guillermolisi on 2010-07-25
Ingresa ```
sudo lshw
``` en una consola/terminal y mostranos su salida.
Si podes aportar marca y modelo del chip que usa esa placa, mejor.

---

### Post by Rick58 on 2010-07-25
Gracias, Guillermo. Te paso la salida del comando, en cuanto al chip no pude ubicar dicha información, inclusoe en la pagina del fabricante. Según Windows es una WIN TV PVR PCI II (25xxx). Segun la página de HP, Win TV PVR 150.

rick@ubuntu:~$ sudo lshw
[sudo] password for rick: 
ubuntu                    
    description: Desktop Computer
    product: KN282AA-ABM s3440la
    vendor: HP-Pavilion
    version: Chassis Version
    serial: 3CR8180456
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=8057C2C9-E084-1310-BA46-8A15F88B5A8D
  *-core
       description: Motherboard
       product: Acacia
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.02
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 5.15 (04/01/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) Dual Core Processor 4050e
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.11.2
          slot: Socket AM2
          size: 2100MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 800 MHz (1.2 ns)
             product: HYMP112U64CP8-S6
             vendor: AD00000000000000
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 800 MHz (1.2 ns)
             product: HYMP112U64CP8-S6
             vendor: AD00000000000000
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.11.2
          size: 2100MHz
          capacity: 2100MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:7 ioport:fc00(size=64) ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02e000-fe02e0ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
          resources: ioport:c000(size=4096) memory:fde00000-fdefffff memory:f4000000-f7ffffff(prefetchable)
        *-firewire
             description: FireWire (IEEE 1394)
             product: FW322/323
             vendor: Agere Systems
             physical id: 5
             bus info: pci@0000:01:05.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=24 mingnt=12
             resources: irq:19 memory:fdeff000-fdefffff
        *-multimedia
             description: Multimedia video controller
             product: iTVC16 (CX23416) MPEG-2 Encoder
             vendor: Internext Compression Inc
             physical id: a
             bus info: pci@0000:01:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128
             resources: irq:18 memory:f4000000-f7ffffff(prefetchable)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe028000-fe02bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1f:c6:5f:2c:6c
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.101 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:25 memory:fe02d000-fe02dfff ioport:ec00(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi1
          logical name: scsi2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:fe02c000-fe02cfff
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-H653N
             vendor: TSSTcorp
             physical id: 0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0409
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: SAMSUNG HD501LJ
             physical id: 1
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: CR10
             serial: S10NJDWQ321600
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=1549f232
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 5c28-9574
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-06-05 05:21:55 filesystem=ntfs state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 6e5dfb6d-509c-f74a-aae5-1301d17d8c07
                size: 367GiB
                capacity: 368GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-06-05 05:22:00 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@2:0.0.0,3
                logical name: /dev/sda3
                logical name: /
                version: 1.0
                serial: 6a75241c-e9b5-4bec-8cb3-b32d3b3cf3e8
                size: 9766MiB
                capacity: 9766MiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-07-24 05:57:54 filesystem=ext4 lastmountpoint=/&#65533;rW&#65533;`&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p^&#65533;&#65533;g &#65533;&#65533;g/&#65533;d^&#65533;&#65533;!&#65533;&#65533;G&#65533;&#65533;G&#65533;`&#65533;&#65533;^&#65533;^&#65533;j modified=2010-07-24 06:20:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-07-25 15:10:18 state=mounted
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@2:0.0.0,4
                logical name: /dev/sda4
                size: 88GiB
                capacity: 88GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1954MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /home
                   capacity: 86GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:b000(size=4096) memory:f8000000-fbffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G98 [GeForce 8400]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff(prefetchable) memory:f8000000-f9ffffff ioport:bc00(size=128) memory:fbfe0000-fbffffff(prefetchable)
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
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
     *-scsi:0
          physical id: b
          bus info: usb@1:1
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart C3180
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdb
     *-scsi:1
          physical id: c
          bus info: usb@1:10
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@5:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@5:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@5:0.0.3
             logical name: /dev/sdf

Muchas gracias de nuevo.

Rick

---

### Post by guillermolisi on 2010-07-25
Linux la ve asi
> *-multimedia
             description: Multimedia video controller
             product: iTVC16 (CX23416) MPEG-2 Encoder
             vendor: Internext Compression Inc
             physical id: a
             bus info: pci@0000:01:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128
             resources: irq:18 memory:f4000000-f7ffffff(prefetchable)y tiene su driver asociado (ivtv), lo cual es bueno. Ahora, ni idea si el driver esta completamente funcional o no (nunca lo probe).

---

### Post by cromix on 2010-08-03
Hola Rick58! Recientemente instalé Ubuntu y ando buscando información y aprendiendo de a poco. Uno de los temas que estoy intentando resolver es la configuracion de mi tarjeta de TV FM. Pero bueno, al grano: para que puedas ver el chip de tu tarjeta abre la terminal que está en Aplicaciones- Accesorios y escribe: 

lspci

y casi al final del despliegue de comandos aparece tu tarjeta capturadora de tv y el semiconductor que utiliza. También para ver el subsistema de la capturadora escribe en la terminal:

dmesg | grep saa | grep subsystem

y obtendrás el dato.

Yo sigo buscando la mejor opción para hallar la configuración de la capturadora mía; hasta ahora ninguna es efectiva. Sigo buscando.

---

### Post by Rick58 on 2010-08-03
Muchas gracias por tu interés. Pasa que realmente, estoy un poco cansado de lidiar con estos problemas en linux (en varias distribuciones). Destaco el espíritu de colaboración en distintos foros y listas de correos, pero soluciones hasta ahora no he logrado, seguramente por mi falta de capacidad. 
De todas maneras, tengo un grueso manual de linux que me espera, así que pronto volveré "al ataque".
Gracias de nuevo!

---

### Post by saedelaere on 2010-08-16
I know this problem has been solved but if you need a software to watch and record TV with your ivtv device you may try [TV-Viewer]("http://tv-viewer.sourceforge.net/") If you are using 64bit Ubuntu 10.04 and receive segmentation faults you have to update Tcl/Tk as described [here]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Howto#Replacing_included_Tcl.2FTk_packages_with_ActiveTcl")

Best regards

---

### Post by guillermolisi on 2010-08-17
> **saedelaere said:**
> I know this problem has been solved but if you need a software to watch and record TV with your ivtv device you may try [TV-Viewer]("http://tv-viewer.sourceforge.net/") If you are using 64bit Ubuntu 10.04 and receive segmentation faults you have to update Tcl/Tk as described [here]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Howto#Replacing_included_Tcl.2FTk_packages_with_ActiveTcl")

Best regards
Traduccion
> Sé que este problema se ha solucionado, pero si necesitas un software para ver y grabar TV en tu dispositivo ivtv podes intentar TV-Viewer Si utilizas 64 bits de Ubuntu 10.04 y recibis fallos de segmentación tenes que actualizar Tcl / Tk como se describe aquí

Thanks a lot for your help saedelaere !

---

