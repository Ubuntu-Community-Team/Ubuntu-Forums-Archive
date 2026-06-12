---
title: "Placa de Tv PCI Encore ENLTV-FM3"
date: 2010-05-12
forum: Hardware
---

### Post by Don King on 2010-05-12
Bunenas a todos, vengo a esta comunidad pidiendo ayuda, porque la verdad que estoy mas que desorientado. 
Recientemente obtuve esta placa de TV, y la verdad que no tengo idea de como hacerla funcionar en Ubuntu 10.04. No me la detecto de una. Lo primero que se me ocurrio fue instalar meter el disco e instalar el driver y el programa con Wine, lo cual anduvo joya, pero a la hora de correr el programa éste no andaba. Googleando encontre varias paginas donde se recomendaba el programa Mythtv, asi que lo instale con los repositorios. El tema es que no se cómo confirgurarlo, principalmente instalar los drivers para que el programa la note, porque desgraciadamente no lo hace. 

Soy bastante nuevo en esto, asi que pediré que todo sea explicado lo mas sencillamente posible. 

Gracias de antemano.

---

### Post by Don King on 2010-05-30
En serio?  Nadie?

---

### Post by guillermolisi on 2010-05-30
Siempre, sea el hardware que sea, pasa por saber que chip utiliza y como es reconocido por Linux.

Para ello hay dos herramientas fundamentales basicas: ```
sudo lshw
``` y ```
lspci
``` ejecutados en una consola/terminal.

Con esa informacion podras saber si la placa es "vista" por Ubuntu y de que forma.

Mostranos las salidas aqui para ver si alguien te puede dar una mano con este tema.

---

### Post by Don King on 2010-05-31
Gracias Guillermo por responderme. Bueno, aca estan:
LSHW:
```

nahuel-desktop            
    description: Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=69B170EE-5E4E-11DC-8B9F-004095005280
  *-core
       description: Motherboard
       product: D945GCNL
       vendor: Intel Corporation
       physical id: 0
       version: AAD97184-104
       serial: BTNL73600CUE
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: LGA 775
          size: 1200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Unknown
             size: 2MiB
             capacity: 2MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 2
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 4
          version: NL94510J.86A.0010.2007.0523.1650 (05/23/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 0x393930353331362D3030352E4130344C4600
             vendor: 0x7F98000000000000
             physical id: 0
             serial: 0x670CE68E
             slot: J6H1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: J6J1
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:50200000-5027ffff ioport:20e0(size=8) memory:40000000-4fffffff(prefetchable) memory:50280000-502bffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:502c0000-502c3fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:50300000-504fffff memory:50500000-506fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:50100000-501fffff memory:50700000-508fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:19:d1:8f:45:a0
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=190.55.234.189 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:28 ioport:1000(size=256) memory:50100000-50100fff memory:50700000-5071ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:50900000-50afffff memory:50b00000-50cfffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:5000(size=4096) memory:50d00000-50efffff memory:50f00000-510fffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:2080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:2060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:2040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:2020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:502c4000-502c43ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:50000000-500fffff
           *-multimedia
                description: Multimedia controller
                product: SAA7134/SAA7135HL Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84
                resources: irq:18 memory:50000000-500003ff
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:20b0(size=16)
           *-disk
                description: ATA Disk
                product: ST320413A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sda
                version: 3.32
                serial: 5ED0LTJ2
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=065b065b
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 30786936-baec-d54d-9018-eb74c44f4d0a
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-02-07 19:01:02 filesystem=ntfs state=clean
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:20c8(size=8) ioport:20ec(size=4) ioport:20c0(size=8) ioport:20e8(size=4) ioport:20a0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD1600AAJS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 03.0
                serial: WD-WCAV35117744
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000bfc6c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: b727702f-a3f5-495c-9936-1270246054a6
                   size: 146GiB
                   capacity: 146GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-01-24 12:34:24 filesystem=ext4 lastmountpoint=/&#65533;Lg&#1058;&#65533;&#65533;J&#65533;&#65533;&#65533;&#65533;&#65533;p^&#65533;&#65533;u^ &#65533;U/&#65533;d^&#65533;&#65533;~!&#65533;H-&#65533;&#65533;H-&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^&#65533;&#65533;^&#65533;&#65533;a modified=2010-05-25 23:32:58 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-31 02:06:08 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   size: 2902MiB
                   capacity: 2902MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 2902MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:2000(size=32)

```LSPCI:
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:04.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

```

---

### Post by UbunArg on 2010-06-01
Tengo el mismo problema. Hace unos dias compré la misma placa y no puedo hacerla andar en Ubuntu 10.04 (Actualizado delde 9.10) y ya probé algunas soluciones y nada...

Hay dos soluciones segun leí: Una implica instalar un paquete llamado "mercurial" y otros pasos que la verdad no se qué es lo que hacen pero no me funcionó y me modificó varios archivos.

Otra forma de hacerla funcionar según leí es cargando este modulo de esta forma:
> $ sudo modprobe -r saa7134_alsa
$ sudo modprobe -r saa7134
$ sudo modprobe saa7134 card=63 tuner=47Pero aquí varían los valores de card y tuner para cada placa así que no se como conseguir el valor correcto (esos valores que puse son para una placa TV Kworld pero que es detectada de la misma forma que esta, así que podrías probar).
Ademas no puedo probar mucho porque mi sistema está muy tocado y al probar hacer esto me salen algunos errores...tengo que esperar para hacer una instalación limpia y después probar :(


Suerte

---

### Post by guillermolisi on 2010-06-01
En el historico de la lista de Ubuntu-ar hay [varios threads sobre este chip]("http://old.nabble.com/forum/Search.jtp?forum=17402&local=y&query=saa7134").

---

### Post by Johann-1.0 on 2011-05-14
Buenas noches muchachos. ¿Cómo podemos hacer para reunir suficientes personas para hacer una queja formal contra Encore Electronics? Yo compré esta tarjeta porque decía en la caja que era compatible con Linux...pero resulta que busco y busco maneras y no encuentro la solución correcta. Me parece que lo más lógico es que Encore Electronics nos provea de los controladores respectivos y no que tengamos que estar dando saltos de foro en foro para resolver este problema. Insisto, la única razón por la que lo compré es porque decía que era compatible con Linux.

---

### Post by Johann-1.0 on 2011-08-24
Ya conseguí que se viera la imagen. Lamentablemente, sólo tengo sonido de estática. ¿Alguien sabe cómo solucionarlo? De paso, mi tarjeta es Encore y la computadora la ve como KWorld. Gracias de antemano.

---

