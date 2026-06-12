---
title: "¿Qué Hardware para Server DHCP + Firewall + VPN?"
date: 2011-07-15
forum: Hardware
---

### Post by granjero on 2011-07-15
buenas... Estoy planeando armar un server que haga todo lo del título!

Tengo un par de dudas sobre el hard que necesito..

También saber si es correcto como estoy encarando el asunto.

Mi idea es poner una máquina que se encargue de asignar las ip de las redes.

Quiero tener 3 redes. al estilo 192.168.10.0/24 + 192.168.20.0/24 + 192.168.30.0/24

Como todo lo voy aprendiendo mientras lo implemento me surgen unas dudas.

Para tener las 3 redes la maquina tendría que tener 4 placas de red.

Por Ej eth0, eth1, eth2, eth3. A 0 la conecto al módem que me da una ip fija de 10Mb que hay contratada. 1, 2, y 3 configurando el server DHCP hago que cada una administre una red.

Placas comunes o hay algo mejor. Cuanto RAM. Qué chip?

Alguno tiene una buena guía para configurar DHCP?

Luego la VPN. Para conectar otras máquinas que están fuera de la red y puedan acceder al servidor samba y otros recursos como si estuvieran en la red. Mi idea es OPenVPN.

y al final configuraré un firewall para filtrar contenidos y demás.


Esto es lo que tengo. Sirve?


```
              
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=A0E3001E-8C00-00C2-69EB-E0CB4E26E2F8
  *-core
       description: Motherboard
       product: M4A785TD-M EVO
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: 102848430000511
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0904 (10/14/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) II X2 245 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.6.2
          serial: To Be Filled By O.E.M.
          slot: AM3
          size: 2900MHz
          capacity: 2900MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpufreq
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
             size: 1MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.2
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge Alternate
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS880 PCI to PCI bridge (int gfx)
             vendor: ASUSTeK Computer Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:d000(size=4096) memory:fe800000-fe9fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS880 [Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff(prefetchable) ioport:d000(size=256) memory:fe9f0000-fe9fffff memory:fe800000-fe8fffff
           *-multimedia
                description: Audio device
                product: RS880 Audio Device [Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fe9e8000-fe9ebfff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:fea00000-feafffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:19 memory:feaff800-feafffff memory:feaff400-feaff47f memory:feaff000-feaff07f memory:feafec00-feafec7f
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 5)
             vendor: Advanced Micro Devices [AMD]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:feb00000-febfffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: e0:cb:4e:26:e2:f8
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.30 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:27 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febf0000-febfffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:fe7ffc00-fe7fffff
           *-disk:0
                description: ATA Disk
                product: WDC WD1600AAJS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAV2J800849
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=064d51fc
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: ff85331e-0e36-4ec6-9e40-27a22d1604ae
                   size: 953MiB
                   capacity: 953MiB
                   capabilities: primary bootable nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 148GiB
                   capacity: 148GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 18GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 129GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
           *-disk:1
                description: ATA Disk
                product: SAMSUNG HD502HJ
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/sdb
                version: 1AJ1
                serial: S20BJ90ZB43254
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=554bdd72
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/500Gb
                   version: 1.0
                   serial: 1748304c-7d45-4e47-a4df-5bfe02474ea1
                   size: 465GiB
                   capacity: 465GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-27 21:09:17 filesystem=ext4 lastmountpoint=/media/500Gb&#65533;&#65533;&#65533;&#65533;8`&#65533;H2&#65533;&#65533;&#65533;&#65533;u!&#65533;-0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#26634; modified=2011-07-02 12:00:21 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-07-02 12:00:21 state=mounted
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe7fe000-fe7fefff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe7fd000-fe7fdfff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe7ff800-fe7ff8ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe7fc000-fe7fcfff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe7fb000-fe7fbfff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe7ff400-fe7ff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
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
             resources: irq:16 memory:fe7f4000-fe7f7fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe7fa000-fe7fafff
     *-pci:1
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

```


;)

---

### Post by guillermolisi on 2011-07-15
En principio y considerando que sera un server, con lo cual el uso de un escritorio grafico podria ser eventual (no permanente), no veo mayores problemas en usar ese hardware para los servicios que mencionas.

Respecto de las placas de red vas a tener que usar una para cada enlace publico a Internet que tengas. Para las subredes, porque los bloques que mencionas estan en la misma red, la cantidad de placas dependera de la cantidad de PCs que esten en cada subred. Podes usar una placa para cada subred o utilizar asignacion de IP secundaria (modo promiscuo).

Respecto de que placas de red usar, el criterio de mejor practica aconseja placas para servidores, que son sustancialmente mas caras que las que se utilizan en desktops (integradas o discretas) porque poseen caracteristicas superiores. Si cada cliente trabajara con un ancho de banda < 1Gb, cada placa del servidor (y la boca del switch donde se la conecte) deberia ser de por lo menos 1Gb. De esta forma evitas cuello de botella en el acceso al servidor desde cada PC por accesos concurrentes y simultaneos.

Las placas que he usado y nunca me dieron problemas son 3Com e Intel (Intel tiene una linea para servers con dos o cuatro bocas de 1Gb que te permite inclusive hacer bonding y asi aumentar el ancho de banda de acceso al server).

Me parece buena opcion openVPN.

Una aclaracion, si queres controlar accesos a sitios/contenidos en Internet mi consejo es usar Squid. Te va a resultar mas facil de mantener que haciendolo solamente con iptables.

---

### Post by granjero on 2011-07-15
Gracias Guillermo por las respuestas. Entorno gráfico no voy a usar. ¿Con 1Gb de RAM que tiene esa máquina va bien?

> Respecto de las placas de red vas a tener que usar una para cada enlace publico a Internet que tengas. Para las subredes, porque los bloques que mencionas estan en la misma red, la cantidad de placas dependera de la cantidad de PCs que esten en cada subred. Podes usar una placa para cada subred o utilizar asignacion de IP secundaria (modo promiscuo).


¿Me recomendarías lectura para entender esto que me comentás? ¿A qué te referís con "...cada enlace publico a Internet que tengas."?

Quiero Separar las redes para que los recursos de una y otra red nos sean vistos por los usuarios de una y otra red.

Mi idea es en la primer red (oficina) a las PCs y dispositivos existentes (telefonos IP) asignar IPs por dirección de hardware y dejar un pool de 70 IPS para conecciones WiFi y conecciones VPN. 

La segunda red parecido. Es un Laboratorio de iMacs, asignar por direccion de hardware más un pool para WiFi.

La tercera red sería Exclusivamente para los invitados.

Qué lectura me recomiendan?

Muchas Gracias.

Salud!

---

### Post by guillermolisi on 2011-07-15
1 Gb RAM deberia alcanzar para lograr un funcionamiento aceptable. Siempre tenes la posibilidad de agregarle mas memoria, si hace falta.

Las placas de red configuradas en modo promiscuo poseen mas de una direccion IP y el sistema las "ve" como pseudo interfaces (eth0a o eth01, no recuerdo bien en este preciso momento, si posee dos direcciones). Podes probar de esta forma siempre que la estimacion de relacion "trafico de red/ancho de banda de la placa" de para que sea operativo (sino te vas a enterar cuando te llamen preguntando si hay Internet o se cayo la red).

Las subredes tal como las pasaste no se veran entre si porque las estas enmascarando con /24 que es equivalente a la mascara 255.255.255.0 (solamente podran ver maquinas a nivel de host, dentro de la misma subred). Es decir, asi como planteas la red, ya estan separadas. Si no queres marearte con la notacion canonica, tenes este site para ayudarte [http://jodies.de/ipcalc](http://jodies.de/ipcalc)

Suponiendo que tenes un solo server que asistira a tres subredes distintas, tenes por lo menos dos alternativas para que este server sea alcanzable por cada subred:

Que el server tenga una placa de red por subred y una IP dentro de cada bloque para que sea alcanzable por las PCs.
Que tenga una sola placa con IPs en cada bloque de subred (modo promiscuo).

Ademas de eso, cuando implementes OpenVPN deberias considerar una red diferente (sino, no se podra conectar), ponele 172.16.xxx.xxx.

Cada enlace publico significa una IP publica. Si tenes mas de un enlace tenes que instalar una placa de red para cada uno ya que cada placa tendra una IP publica diferente.

Para todo esto, siempre he buscado informacion via Google asi que no puedo recomendarte una lectura en particular.

---

### Post by hictio on 2011-07-16
No se si ya seleccionaste distribución para esto, pero te recomiendo algunas:

[Zentyal](http://www.zentyal.org/) Basado en Ubuntu Server 10.04, todavía no lo pude probar, le tengo muchas ganas
[Endian Firewall](http://www.endian.com/en/community/overview/) Muy fácil de configurar
[PF Sense](http://www.pfsense.org/) Muy, muy bueno para hacer balance de carga, un más complejo para hacer el setup

De hardware estás más que bien en lo requerimientos para cualquiera de estas distribuciones.

---

