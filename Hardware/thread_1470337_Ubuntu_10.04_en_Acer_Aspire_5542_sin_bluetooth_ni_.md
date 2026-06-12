---
title: "Ubuntu 10.04 en Acer Aspire 5542 sin bluetooth ni wifi"
date: 2010-05-02
forum: Hardware
---

### Post by elgabi on 2010-05-02
Hola, el problema que tengo es el siguiente:

Instalé la versión de Ubuntu 10.04 LTS en mi notebook y todo funcionaba correctamente, detectó los dispositivos y tenía acceso correcto a la red wifi de mi casa y el bluetooth permanecía encendido.

El equipo durante su uso, descargó la batería completamente por lo que hibernó (estaba conectado a internet). Cuando inicié el sistema, esta vez conectado a la red eléctrica, no encendía ninguno de los indicadores de wifi ni el de bluetooth. Tampoco hubo forma de hacerlo manualmente con los "botoncitos" que tiene el equipo. Logicamente no tenía acceso a Internet ni a los dispositivos bluetooth. 

Con el WIFI:
Luego de pasar algunos comandos por la consola noté que el wifi estaba deshabilitado, mediante ifconfig wlan0 up logré activarlo, pero cada vez que reinicio el sistema, el dispositivo vuelve a apagarse. Entonces siempre que arranco el sistema tengo que (mediante consola) activarlo manualmente (y es un ***-pain).

Con el BLUETOOTH:
Cuando paso el comando lshw, el dispositivo bluetooth no veo que aparezca en el listado. Intenté con hciconfig hci0 up, como resultado obtengo "Can't get device info: No such device". Revisé al bootear si en el BIOS aparece como desactivado, pero nada por allí.

Algo extraño, si arranco el sistema con el LiveCD de Ubuntu, todo funciona perfectamente, tengo acceso WIFI y Bluetooth sin problemas...

IMPORTANTE: Mi notebook NO TIENE instalado Windows. Solamente instalé ubuntu y el problema surgió en una de las primeras ocasiones que lo usé. Lo tengo actualizado al corriente pero no se ha solucionado el problema. Con el LiveCD pude comprobar que los dispositivos FUNCIONAN, evidentemente hay algún problema de configuración que desconozco que pudo haberlo generado. Espero puedan ayudarme. Muchas gracias desde ya.

elgabi

---

### Post by crjweb on 2010-05-09
El problema Puede ser el nuevo Gestor de la red que viene con la versión 2.30 de GNOME, en la barra superior esta el icono de conexión con el botón derecho le haces click y le das a activar red.

---

### Post by guillermolisi on 2010-05-09
Que chip usa la placa de WiFi de esa maquina ?
Para hacerlo expeditivo y concreto, ejecutar en una consola/terminal los comandos "lspci", "lsusb" y "sudo lshw" (sin las comillas) asi veremos que es y como se la reconoce.

Copia y pega las salidas de cada uno aqui.

---

### Post by apteas on 2010-06-09
Parece que es un problema con Ubuntu 10.04 y no con Acer: [http://ubuntuforums.org/showthread.php?t=1471456](http://ubuntuforums.org/showthread.php?t=1471456)
Tal vez es necesario esperar para un "upgrade"? (Tenias el mismo problema con 9.10?)

---

### Post by elgabi on 2010-06-13
> **guillermolisi said:**
> Que chip usa la placa de WiFi de esa maquina ?
Para hacerlo expeditivo y concreto, ejecutar en una consola/terminal los comandos "lspci", "lsusb" y "sudo lshw" (sin las comillas) asi veremos que es y como se la reconoce.

Copia y pega las salidas de cada uno aqui.

Hola, gracias a todos por sus respuestas. Aquí abajo copio la salida de los comandos:


**Con sudo lshw:**

*-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 01
                serial: c4:17:fe:3b:31:e5
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.16.101 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:f0400000-f040ffff


**Con lspci:**
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
[COLOR="Red"]09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)[/COLOR]


**Con lsusb**

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Estas salidas ya las había obtenido, pero descarté que fuera un problema de drivers, porque inicialmente funcionaban muy bien, luego de algunos días de uso comenzó el problema de que se apagaron los dispositivos. El wifi puedo encenderlo pasando los comandos por la consola, pero el bluetooth nunca más encendió de nuevo.

Muchas gracias desde ya!


elgabi

---

### Post by rukiaEnix on 2010-06-13
no se si esto funcione pero prueba agregando wlan0 a /etc/modules
para ver si así ya te carga tu wifi en cuanto al bluetooth haz lo mismo a ver que pasa :p

---

### Post by guillermolisi on 2010-06-15
> **elgabi said:**
> Hola, gracias a todos por sus respuestas. Aquí abajo copio la salida de los comandos:


**Con sudo lshw:**

*-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 01
                serial: c4:17:fe:3b:31:e5
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.16.101 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:f0400000-f040ffff
Aqui claramente dice que esta funcionando y que tiene una IP asignada.
No estara en otro lado el problema ?


> **Con lsusb**

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Aqui y si no interpreto mal, lo que esta detectando es el chip de la webcam.
Bluetooth ni aparece. Esta encendido desde la maquina (generalmente una combinacion de teclas que incluyen Fn+F(algun_numero)) ?

---

### Post by guillegauna on 2010-06-27
disculpen, yoo tengoo mas o menos los mismos erroreees!!

despues de un determinado tiempo (puede qe tenga algo qe ver la hibernacion qe sucedio) pero mi pantalla qeda en negro (o apagada)

por otra parte, no me encuentra el bluetooth (por mas qe tenga el programa, ii qe tambien tenga el zblu)

como si fuese poco, tampoco me busca conecciones wifi!!!

Seria importante aclararles qe soi unusuarrio muuui nuevo de ubuntu.. (si bien utilice el 9.1)
de cualqier manera, QIERO aprender a utilizarlo, 
y por esta razon, es qe en la netbook nueva, lo instale..

Ahh!, algo mas!!.. nada de esto me pasa en win7 qe tambien esta instalado.. espero tengan solucion!!

les dejo algo de la netbook...

description: Desktop Computer
    product: P10
    vendor: EXO S.A.
    version: 1.0
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P10
       vendor: EXO S.A.
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080016 (04/14/2010)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          slot: CPU 1
          size: 1GHz
          capacity: 1750MHz
          width: 64 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm pse cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 24KiB
             capacity: 24KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
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
          physical id: d
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:25 memory:fe980000-fe9fffff ioport:dc00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fea00000-feafffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fe880000-fe8fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fe978000-fe97bfff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=8192) memory:feb00000-fecfffff memory:40000000-401fffff(prefetchable)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:febffc00-febffcff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:01:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:fecff800-fecff8ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:01:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:17 memory:fecff400-fecff4ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:01:00.4
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:fecff000-fecff0ff
           *-network DISABLED
                description: Ethernet interface
                product: JMC260 PCI Express Fast Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0.5
                bus info: pci@0000:01:00.5
                logical name: eth0
                version: 02
                serial: 00:24:25:0b:0e:6a
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=off broadcast=yes driver=jme driverversion=1.0.5 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:16 memory:fecf8000-fecfbfff ioport:f480(size=128) ioport:e800(size=256)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d880(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d800(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d480(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d400(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe977c00-fe977fff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1000(size=16) memory:40200000-402003ff
           *-disk
                description: ATA Disk
                product: WDC WD1600BEVT-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXA0AB9A7776
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=bf9d71d7
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: e858-e6b4
                   size: 498MiB
                   capacity: 500MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-12-30 14:48:51 filesystem=ntfs label=System state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 9c869ee7-7007-854d-8bb9-3d8019fd9463
                   size: 4978MiB
                   capacity: 5000MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-12-30 14:50:01 filesystem=ntfs label=Recovery state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /host
                   version: 3.1
                   serial: 70ef8fd6-adee-2047-b569-02dfe086e431
                   size: 143GiB
                   capacity: 143GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-12-30 14:51:25 filesystem=ntfs label=OS mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)

ultima observacion, me parece qe cuando conecto la netbook, ii la pongo a cargar.. este problema se enfatisa, o aparece..

Less ruego qe me ayuden!!, ii me enseñen, de poder.. =)

desde ya, gracias..!

SOLUCIONADO LO DEL VIDEO!!! =D

pero todavia no tengo wifi ni bluetooth.. :( (pero si tengo en win7)

sii alguien sabe, me avisa plzz? =D

---

### Post by elgabi on 2010-07-09
> **guillermolisi said:**
> Aqui claramente dice que esta funcionando y que tiene una IP asignada.
No estara en otro lado el problema ?



Aqui y si no interpreto mal, lo que esta detectando es el chip de la webcam.
Bluetooth ni aparece. Esta encendido desde la maquina (generalmente una combinacion de teclas que incluyen Fn+F(algun_numero)) ?

Hola, sí, la combinación de teclas (en este equipo es con la tecla Fn+ F3 para el dispositivo bluetooth) no lo enciende. Tampoco lo consigo presionando un botón especial dispuesto para tal fin. Intenté eso y puedo asegurar que muuuchas cosas más... Y sigo con los mismos problemas.

Aclaro que como el inconveniente continua y ya había tocado todo y pasado por la consola todos los comandos que se aconsejaba ante casos similares en los foros, opté finalmente por algo drástico: formatear la partición y volver a instalar Ubuntu.

¡Como era de imaginar, todo se solucionó mágicamente! (no era una sorpresa porque con el LiveCD las cosas funcionaban bien).

Hete aquí que una vez más marchaban los dispositivos de nuevo, pero con el transcurrir de los días y sospecho que luego de una hibernación involuntaria se volvió a arruinar tooodo otra vez: el dispositivo bluetooth apagado, el wifi solo consigo encenderlo pasando los comandos por consola (ifconfig wlan0 up) los depósitos de contraseñas pareciera que andan mal (por ej. me guarda la contraseña del wifi, y cuando reinicio tras encender el dispositivo pasando los comandos no consigue conectar).

Luego cierro manualmente la aplicación nm-applet, abro la consola y paso los comandos para volver a iniciar nm-applet, ahí me pide la clave (elijo no guardar la contraseña, porque no tiene sentido si cada vez que inicia no sirve para que arranque automáticamente conectado) y recién luego de todo ese lío, logro conectar... en fín, un gran gran inconveniente, es una incomodidad permanente.

Pero todavía no me rindo, a pesar de las bromitas que a estas alturas me hacen algunos "fans" del software propietario...

Seguiré investigando, mientras tanto cruzo los dedos para que alguna actualización logre fortuítamente resolver mi problema (si alguien me brinda algunos tips para reportar como bug, soy todo oidos).

Un saludo cordial para los amigos ubunteros, estaré merodeando por si hubiere novedades...

elgabi

---

### Post by guillegauna on 2010-07-17
> **elgabi said:**
> Hola, sí, la combinación de teclas (en este equipo es con la tecla Fn+ F3 para el dispositivo bluetooth) no lo enciende. Tampoco lo consigo presionando un botón especial dispuesto para tal fin. Intenté eso y puedo asegurar que muuuchas cosas más... Y sigo con los mismos problemas.

Aclaro que como el inconveniente continua y ya había tocado todo y pasado por la consola todos los comandos que se aconsejaba ante casos similares en los foros, opté finalmente por algo drástico: formatear la partición y volver a instalar Ubuntu.

¡Como era de imaginar, todo se solucionó mágicamente! (no era una sorpresa porque con el LiveCD las cosas funcionaban bien).

Hete aquí que una vez más marchaban los dispositivos de nuevo, pero con el transcurrir de los días y sospecho que luego de una hibernación involuntaria se volvió a arruinar tooodo otra vez: el dispositivo bluetooth apagado, el wifi solo consigo encenderlo pasando los comandos por consola (ifconfig wlan0 up) los depósitos de contraseñas pareciera que andan mal (por ej. me guarda la contraseña del wifi, y cuando reinicio tras encender el dispositivo pasando los comandos no consigue conectar).

Luego cierro manualmente la aplicación nm-applet, abro la consola y paso los comandos para volver a iniciar nm-applet, ahí me pide la clave (elijo no guardar la contraseña, porque no tiene sentido si cada vez que inicia no sirve para que arranque automáticamente conectado) y recién luego de todo ese lío, logro conectar... en fín, un gran gran inconveniente, es una incomodidad permanente.

Pero todavía no me rindo, a pesar de las bromitas que a estas alturas me hacen algunos "fans" del software propietario...

Seguiré investigando, mientras tanto cruzo los dedos para que alguna actualización logre fortuítamente resolver mi problema (si alguien me brinda algunos tips para reportar como bug, soy todo oidos).

Un saludo cordial para los amigos ubunteros, estaré merodeando por si hubiere novedades...

elgabi

eii amigo qee taal??!!

mira, sii es el mismo dispositivo qe el mio, vas hai solucioon!!
(pero a medias, diria)

laa cosa es asi.. la pag del hardware tiene el driver con sus 2programas para la activacion i el funcionamiento del wifi y bluetooth integrados en un solo dispositivo..

la diferencia es qe soporta ubuntu 10.04 pero hasta la version .21 y .22, la .23 no va.. asiqe, tendriasqeusar lsanteriores para hacerlo andar! 

yoo creo qee si es similar al problema qee yo tube, bastaria con bajarte el paqete especial de la pag, 

es un dato, qe me sirvio en la mia.. por ahi a vos tambien!

abraso!

---

