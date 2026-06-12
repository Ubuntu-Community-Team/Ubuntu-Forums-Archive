---
title: "Problemas de rendimiento Notebook Eurocase E3"
date: 2012-07-04
forum: Hardware
---

### Post by anguntu on 2012-07-04
Hola a todos,

Esto que me esta pasando es bastante particular y la verdad todavía no encuentro explicación lógica, resulta que esta notebook tiene un procesador core i3 y 4 G de RAM, pero tengo problemas de "rendimiento", por ejemplo estoy escuchando música y navegando, y la música empieza a dar saltos, es como si el sistema se sobrecargara (me recuerda a mi viejo amd k6-2)pero no existe tal sobrecarga de procesos (apenas tengo firefox con 2 pestañas abiertas y rhythmbox), otra cosa es que tengo como pequeños micro cuelgues (no se como explicar esto técnicamente) o sea estoy moviendo el mouse y este como que se traba y luego sigue.

Ya no se si puede ser la RAM, el Diso duro, Video...
SO: Ubuntu 12.04 64 bit
Este es mi hard:

eurocase
    descripción: Notebook
    producto: TWH (HuronRiver_CRB)
    fabricante: Quanta
    versión: TBD
    serie: 123456789
    anchura: 64 bits
    capacidades: smbios-2.7 dmi-2.7 vsyscall32
    configuración: boot=normal chassis=notebook family=Intel_Mobile sku=HuronRiver_CRB uuid=88888888-8887-8888-8888-878888888888
  *-core
       descripción: Placa base
       producto: TWH
       fabricante: Quanta
       id físico: 0
       versión: TBD
       serie: QCQB6BX146010D
       ranura: Base Board Chassis Location
     *-firmware
          descripción: BIOS
          fabricante: INSYDE
          id físico: 0
          versión: QU221
          date: 10/14/2011
          tamaño: 1MiB
          capacidad: 2496KiB
          capacidades: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          descripción: Memoria de sistema
          id físico: 19
          ranura: Placa de sistema o placa base
          tamaño: 4GiB
        *-bank:0
             descripción: SODIMM DDR3 Síncrono 1333 MHz (0,8 ns)
             producto: BKH400SO25608-1333
             id físico: 0
             serie: FFFFFFFF
             ranura: ChannelA-DIMM0
             tamaño: 4GiB
             anchura: 64 bits
             reloj: 1333MHz (0.8ns)
        *-bank:1
             descripción: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-05-08 10:38+0000X-Generator: Launchpad (build 15204) [vacío]
             id físico: 1
             ranura: ChannelA-DIMM1
        *-bank:2
             descripción: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-05-08 10:38+0000X-Generator: Launchpad (build 15204) [vacío]
             id físico: 2
             ranura: ChannelB-DIMM0
        *-bank:3
             descripción: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-03-14 06:38+0000Last-Translator: Paco Molinero <paco@byasl.com>Language-Team: Spanish <es@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2012-05-08 10:38+0000X-Generator: Launchpad (build 15204) [vacío]
             id físico: 3
             ranura: ChannelB-DIMM1
     *-cpu
          descripción: CPU
          producto: Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
          fabricante: Intel Corp.
          id físico: 27
          información del bus: cpu@0
          versión: Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
          ranura: CPU1
          tamaño: 800MHz
          capacidad: 4GHz
          anchura: 64 bits
          reloj: 1333MHz
          capacidades: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuración: cores=2 enabledcores=2 threads=4
        *-cache:0
             descripción: L1 caché
             id físico: 29
             ranura: L1 Cache
             tamaño: 32KiB
             capacidad: 32KiB
             capacidades: synchronous internal write-through instruction
        *-cache:1
             descripción: L2 caché
             id físico: 2a
             ranura: L2 Cache
             tamaño: 256KiB
             capacidad: 256KiB
             capacidades: synchronous internal write-through unified
        *-cache:2
             descripción: L3 caché
             id físico: 2b
             ranura: L3 Cache
             tamaño: 3MiB
             capacidad: 3MiB
             capacidades: synchronous internal write-through unified
     *-cache
          descripción: L1 caché
          id físico: 28
          ranura: L1 Cache
          tamaño: 32KiB
          capacidad: 32KiB
          capacidades: synchronous internal write-through data
     *-pci
          descripción: Host bridge
          producto: 2nd Generation Core Processor Family DRAM Controller
          fabricante: Intel Corporation
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 09
          anchura: 32 bits
          reloj: 33MHz
          configuración: driver=agpgart-intel
          recursos: irq:0
        *-display
             descripción: VGA compatible controller
             producto: 2nd Generation Core Processor Family Integrated Graphics Controller
             fabricante: Intel Corporation
             id físico: 2
             información del bus: pci@0000:00:02.0
             versión: 09
             anchura: 64 bits
             reloj: 33MHz
             capacidades: msi pm vga_controller bus_master cap_list rom
             configuración: driver=i915 latency=0
             recursos: irq:42 memoria:d8000000-d83fffff memoria:d0000000-d7ffffff ioport:5000(size=64)
        *-communication
             descripción: Communication controller
             producto: 6 Series/C200 Series Chipset Family MEI Controller #1
             fabricante: Intel Corporation
             id físico: 16
             información del bus: pci@0000:00:16.0
             versión: 04
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi bus_master cap_list
             configuración: driver=mei latency=0
             recursos: irq:41 memoria:da604000-da60400f
        *-usb:0
             descripción: USB controller
             producto: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             fabricante: Intel Corporation
             id físico: 1a
             información del bus: pci@0000:00:1a.0
             versión: 04
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci_hcd latency=0
             recursos: irq:16 memoria:da609000-da6093ff
        *-multimedia
             descripción: Audio device
             producto: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             fabricante: Intel Corporation
             id físico: 1b
             información del bus: pci@0000:00:1b.0
             versión: 04
             anchura: 64 bits
             reloj: 33MHz
             capacidades: pm msi pciexpress bus_master cap_list
             configuración: driver=snd_hda_intel latency=0
             recursos: irq:43 memoria:da600000-da603fff
        *-pci:0
             descripción: PCI bridge
             producto: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             fabricante: Intel Corporation
             id físico: 1c
             información del bus: pci@0000:00:1c.0
             versión: b4
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:17 ioport:4000(size=4096) memoria:da500000-da5fffff
           *-network
                descripción: Interfaz inalámbrica
                producto: RTL8188CE 802.11b/g/n WiFi Adapter
                fabricante: Realtek Semiconductor Co., Ltd.
                id físico: 0
                información del bus: pci@0000:07:00.0
                nombre lógico: wlan0
                versión: 01
                serie: 74:de:2b:c2:ea:99
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuración: broadcast=yes driver=rtl8192ce driverversion=3.2.0-25-generic firmware=N/A ip=10.0.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                recursos: irq:16 ioport:4000(size=256) memoria:da500000-da503fff
        *-pci:1
             descripción: PCI bridge
             producto: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             fabricante: Intel Corporation
             id físico: 1c.1
             información del bus: pci@0000:00:1c.1
             versión: b4
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:16 ioport:3000(size=4096) memoria:da400000-da4fffff
           *-network
                descripción: Ethernet interface
                producto: AR8151 v2.0 Gigabit Ethernet
                fabricante: Atheros Communications Inc.
                id físico: 0
                información del bus: pci@0000:08:00.0
                nombre lógico: eth0
                versión: c0
                serie: e8:9a:8f:c7:97:58
                capacidad: 1Gbit/s
                anchura: 64 bits
                reloj: 33MHz
                capacidades: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuración: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                recursos: irq:44 memoria:da400000-da43ffff ioport:3000(size=128)
        *-pci:2
             descripción: PCI bridge
             producto: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             fabricante: Intel Corporation
             id físico: 1c.3
             información del bus: pci@0000:00:1c.3
             versión: b4
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci pciexpress msi pm normal_decode bus_master cap_list
             configuración: driver=pcieport
             recursos: irq:19 ioport:2000(size=4096) memoria:d9400000-da3fffff ioport:d8400000(size=16777216)
        *-usb:1
             descripción: USB controller
             producto: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             fabricante: Intel Corporation
             id físico: 1d
             información del bus: pci@0000:00:1d.0
             versión: 04
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci_hcd latency=0
             recursos: irq:23 memoria:da608000-da6083ff
        *-isa
             descripción: ISA bridge
             producto: HM65 Express Chipset Family LPC Controller
             fabricante: Intel Corporation
             id físico: 1f
             información del bus: pci@0000:00:1f.0
             versión: 04
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa bus_master cap_list
             configuración: latency=0
        *-storage
             descripción: SATA controller
             producto: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             fabricante: Intel Corporation
             id físico: 1f.2
             información del bus: pci@0000:00:1f.2
             nombre lógico: scsi0
             nombre lógico: scsi1
             versión: 04
             anchura: 32 bits
             reloj: 66MHz
             capacidades: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuración: driver=ahci latency=0
             recursos: irq:40 ioport:5088(size=8) ioport:5094(size=4) ioport:5080(size=8) ioport:5090(size=4) ioport:5060(size=32) memoria:da607000-da6077ff
           *-disk
                descripción: ATA Disk
                producto: TOSHIBA MK5075GS
                fabricante: Toshiba
                id físico: 0
                información del bus: scsi@0:0.0.0
                nombre lógico: /dev/sda
                versión: GT00
                serie: 816ZT1OTT
                tamaño: 465GiB (500GB)
                capacidades: partitioned partitioned:dos
                configuración: ansiversion=5 signature=137083a4
              *-volume:0
                   descripción: Windows NTFS volumen
                   id físico: 1
                   información del bus: scsi@0:0.0.0,1
                   nombre lógico: /dev/sda1
                   versión: 3.1
                   serie: 2820-82bc
                   tamaño: 98MiB
                   capacidad: 100MiB
                   capacidades: primary bootable ntfs initialized
                   configuración: clustersize=4096 created=2012-05-02 01:57:51 filesystem=ntfs label=System state=clean
              *-volume:1
                   descripción: Windows NTFS volumen
                   id físico: 2
                   información del bus: scsi@0:0.0.0,2
                   nombre lógico: /dev/sda2
                   versión: 3.1
                   serie: 6a011f79-aece-1f4c-896a-01b63e131b11
                   tamaño: 6494MiB
                   capacidad: 6500MiB
                   capacidades: primary ntfs initialized
                   configuración: clustersize=4096 created=2012-05-02 03:24:18 filesystem=ntfs label=Recovery state=clean
              *-volume:2
                   descripción: Windows NTFS volumen
                   id físico: 3
                   información del bus: scsi@0:0.0.0,3
                   nombre lógico: /dev/sda3
                   versión: 3.1
                   serie: 50d9235e-778f-2e44-b562-848b6e88feeb
                   tamaño: 53GiB
                   capacidad: 53GiB
                   capacidades: primary ntfs initialized
                   configuración: clustersize=4096 created=2012-05-02 01:57:58 filesystem=ntfs label=OS_7 modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:3
                   descripción: Extended partition
                   id físico: 4
                   información del bus: scsi@0:0.0.0,4
                   nombre lógico: /dev/sda4
                   tamaño: 406GiB
                   capacidad: 406GiB
                   capacidades: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      descripción: Linux filesystem partition
                      id físico: 5
                      nombre lógico: /dev/sda5
                      nombre lógico: /
                      capacidad: 46GiB
                      configuración: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      descripción: Linux swap / Solaris partition
                      id físico: 6
                      nombre lógico: /dev/sda6
                      capacidad: 18GiB
                      capacidades: nofs
                 *-logicalvolume:2
                      descripción: Linux filesystem partition
                      id físico: 7
                      nombre lógico: /dev/sda7
                      nombre lógico: /home
                      capacidad: 340GiB
                      configuración: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
           *-cdrom
                descripción: DVD-RAM writer
                producto: DVD-RW DVRTD11RS
                fabricante: PIONEER
                id físico: 1
                información del bus: scsi@1:0.0.0
                nombre lógico: /dev/cdrom
                nombre lógico: /dev/cdrw
                nombre lógico: /dev/dvd
                nombre lógico: /dev/dvdrw
                nombre lógico: /dev/sr0
                versión: 1.01
                capacidades: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuración: ansiversion=5 status=nodisc
        *-serial NO RECLAMADO
             descripción: SMBus
             producto: 6 Series/C200 Series Chipset Family SMBus Controller
             fabricante: Intel Corporation
             id físico: 1f.3
             información del bus: pci@0000:00:1f.3
             versión: 04
             anchura: 64 bits
             reloj: 33MHz
             configuración: latency=0
             recursos: memoria:da605000-da6050ff ioport:5040(size=32)
  *-power NO RECLAMADO
       descripción: OEM_Define1
       producto: OEM_Define5
       fabricante: OEM_Define2
       id físico: 1
       versión: OEM_Define6
       serie: OEM_Define3
       capacidad: 75mWh
  *-battery
       descripción: Ion litio Battery
       producto: CRB Battery 0
       fabricante: -Virtual Battery 0-
       id físico: 2
       versión: 10/12/2007
       serie: Battery 0
       ranura: Fake

Espero sus comentarios, graciasEMAIL@ADDRESS

---

### Post by fernestocba on 2013-05-07
Hola amigos, soy de cordoba capital, tengo el mismo Hardware y el mismo problema. Mi laptop aún esta en garantia, igual hice la denuncia en defensa del consumidor. 
La lleve 3 veces al servicio tecnico.
La ultima vez que la lleve, la enviaron a Bs As, me dijeron q le cambiaron la placa madre, son impresentables, me dieron un nuevo cargador, el cual tiene el conector a la notebook muy flojo, ahora estoy probando el equipo, anda mas rapido, pero cuando ejecuto programas de musica o video, tiene cuelgues aleatorios.
Asi que la llevare de nuevo al service, y por otro lado este jueves, asistiré a la audiencia para decirles que el equipo no funciona correctamente.
Instale Ubuntu 12.10.

---

### Post by fernestocba on 2013-05-09
Estimados, en el día de ayer lleve por 4ta vez la notebook al servicio oficial de EUROCASE en Cordoba, Neyra Hnos.
Por otro lado, asisti a la Audiencia en Defensa del consumidor. Fue breve, dado que intentamos comunicarnos con Neyra hnos y no obtuvimos respuestas, por lo que el personal de def del consumidor, emitira notificacion para nueva audiencia, con las partes involucradas, en mi caso seria, Eurocase, Neyra Hnos y Musimundo. 
La verdad que hay que armarse de paciencia con Def del consumidor, por los plazos, en última instancia me queda por hacer una denuncia mediante abogado particular.

Saludos

---

### Post by dirty fingers on 2013-05-09
ojala consigas lo que es justo !

---

### Post by fernestocba on 2013-05-22
Hola gente, tengo fecha para 2 audiencia en Junio.
Por otro lado les explique a la gente de Eurocase el problema con un ejemplo
la note lee una peli desde la lectora de dvd y todo ok, pero cuando lee la misma pelicula desde el disco rigido, se ve entrecortada.
O sea q en la comunicacion entre el CPU y el DISCO, algo esta funcionando mal.
Actualmente la note esta en BsAs.


Saludos

---

### Post by MeduZa on 2013-05-24
parece un problema de BIOS en el controlador de sistema vital o de este a nivel mobo. obvio no estoy seguro pero asi a simple vista parece eso :( suerte con eso

---

### Post by fernestocba on 2013-05-27
En cuanto pueda comunicarme con el servicio tecnico de Eurocase, les informare de la solucion.

SaludoS!

---

### Post by fernestocba on 2013-06-05
Al fin, retire hace unos minutos la notebook. Le cambiaron el Disco y el microprocesador. Ahora a probarla, en principio todo va bien

---

### Post by fernestocba on 2013-06-06
Gente, al fin la notebook anda como se debe. De todas maneras asistire a la audiencia para dejar constancia de que me extiendan la garantia por todo el tiempo que estuvo en el servicio tecnico. Son casi 6 meses.

Saludos

---

### Post by fernestocba on 2013-06-10
Buenas Gente, le cuento que ahora si la notebook funciona como corresponde. Un alivio grande para mi. 
Saludos.

---

