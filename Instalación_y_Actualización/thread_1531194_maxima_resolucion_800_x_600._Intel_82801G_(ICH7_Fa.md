---
title: "maxima resolucion 800 x 600. Intel 82801G (ICH7 Family). Ubuntu 9.10"
date: 2010-07-14
forum: Instalación y Actualización
---

### Post by zhottaz on 2010-07-14
ola soy alejandro hace poco publique que me ayudaran a instalar ubuntu y lo logreeEEEEEEEEEEEE!!!!!!!!!!!!!!! estoy escribiendo este post desde el!!! bueno pero sabria que me vendrian problemas y bueno aparecio el primero.
Aplique en GEstor de actualizacion el cual me actualizo y despues actualize abuntu de 9.04(la que descarque para instalar) a la version 9.10 ya que el gestor me dio la opcion, bueno pero ahora la resolucion maxima es de 800 x 600 muy grande para mi por mi monitor y no me deja 1024; antes si podia con la version 9.04.

Andube investigando y habian varios problemas similares pero no entendia mucho porque llevo 2 dias con linux (entenderas q es poco) y algunas respuestas daban a que tenia que modificar codigos en archivos de texto pero no se donde estan ni como llegar a ellos, y mi tarjeta de video es integrada de una placa foxconn.

Porque antes podia hacerlo y ahora con esta version no puedo me parce raro. ayuda
recuerden q hasta ahora solo e navegado en internet y nada mas gracias

---

### Post by asterix77 on 2010-07-15
¿Cuales son las carateristicas de tu pc?

Escribe lo que arrojan los siguientes comandos para partir con algo.

#sudo lspci

#lshw


Saludos

---

### Post by zhottaz on 2010-07-16
CON EL PRIMER COMANDO ME APARECE ESTO  "spci" 



00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:03.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
01:04.0 Mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 13)





CON EL SEFGUNDO COMANDO ESTO "lshw"



WARNING: you should run this program as super-user.
zhottazenlinux-desktop    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 502MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          size: 3050MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: id=0
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
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fdf80000-fdfbffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fdff8000-fdffbfff
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fe00(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fd00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fc00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fb00(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdfff000-fdfff3ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:fdd00000-fddfffff ioport:fde00000(size=1048576)
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=15 mingnt=15
                resources: irq:21 memory:fddff000-fddff7ff memory:fddf8000-fddfbfff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5788 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:01:03.0
                logical name: eth0
                version: 03
                serial: 00:01:6c:cd:59:2d
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5788-v3.04 ip=192.168.0.101 latency=32 mingnt=64 multicast=yes
                resources: irq:23 memory:fdde0000-fddeffff
           *-storage
                description: Mass storage controller
                product: IT/ITE8212 Dual channel ATA RAID controller
                vendor: Integrated Technology Express, Inc.
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 13
                width: 32 bits
                clock: 66MHz
                capabilities: storage bus_master cap_list rom
                configuration: driver=pata_it821x latency=64 maxlatency=8 mingnt=8
                resources: irq:20 ioport:ef00(size=8) ioport:ee00(size=4) ioport:ed00(size=8) ioport:ec00(size=4) ioport:eb00(size=16) memory:fde00000-fde1ffff(prefetchable)
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
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f900(size=8) ioport:f800(size=4) ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=16) memory:fdffe000-fdffe3ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)

---

### Post by themasterdark on 2010-07-16
Es una tarjeta intel sería bueno actualices sus controladores de video:

ve a menu -> accesorios -> terminal (y escribe lo siguiente)

```
sudo apt-add-repository ppa:xorg-edgers/ppa
```

(eso añadira el repositorio ppa de xorg donde esta la actualizacion de los drivers de intel)

sudo apt-get update

(actualizara la lista de software disponible)

sudo aptitude full-upgrade

(actualizara los paquetes disponibles en tu sistema)

luego solo reinicia, saludos, cuentanos como te fue

---

### Post by Patriciologico on 2010-07-17
Esa tarjeta integrada da problemas en 9.04 y 9.10 incluso con el repositorio añadido que te recomienda. Esa fue mi experiencia al menos, por eso use 8.04 hasta que salio 10.04 donde el problema esta resuelto y no veo afectado el rendimiento.

Mi recomendación es que uses la versión actual (10.04)

Saludos

---

### Post by themasterdark on 2010-07-17
Pero debiese probar si su problema se arregla, en caso de que siga igual debiese pensar en actualizar su sistema a la ultima version de ubuntu.

Saludos

---

### Post by Carlos C on 2010-07-19
> **themasterdark said:**
> 

sudo apt-add-repository ppa:xorg-edgers/ppa (sale una carita ahi es :X pero en minusculas)



Una manera de evitar los emoticones es seleccionando el texto y haciendo click en el botón "#" de manera que sea insertado como código:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
```Perdón por desviar la discusión, pero puede servir.

Edité el título para que fuera más descriptivo del problema.

Saludos.

---

### Post by themasterdark on 2010-07-19
> **carlos c said:**
> una manera de evitar los emoticones es seleccionando el texto y haciendo click en el botón "#" de manera que sea insertado como código:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
```perdón por desviar la discusión, pero puede servir.

Edité el título para que fuera más descriptivo del problema.

Saludos.

gracias =)

---

