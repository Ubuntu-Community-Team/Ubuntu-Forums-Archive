---
title: "No consigo conectarme en modo router a internet con speedy"
date: 2010-03-16
forum: Hardware
---

### Post by roroland on 2010-03-16
Hola:

Tengo un modem/router ZTE ZXDSL 831 con Speedy. Tengo en mi pc un dual boot con ubuntu 9.10 y Win xp

Antes tenia este modem como conexion manual, pero lo pase a router como dice en la pagina de Speedy, sin problemas y se conecta bien en XP. En Ubuntu cuando no estaba en modo router podia conectarme bien en con sudo pppoeconf...

Pero desde que lo puse en modo router no logro que se conecte, en teoria es automatico, pero no hace nada...Probe agregandole los datos de IP en DSL...por las dudas tambien lo hice en Cableada (user y password tambien), sin suerte, le agregue el valor de MAC....tampoco...

No se que mas probar, por lo que lei deberia funcionar automaticamente..

Que puede ser ?
Gracias

---

### Post by atari130xe on 2010-03-16
Hola como estás? Tengo el mismo servicio con el mismo modem y funciona perfecto con 2 PC conectadas mediante un switch. Los pasos que seguí con similares a este poste de taringa, probá a ver si te funciona.

[http://www.taringa.net/posts/ebooks-tutoriales/2697873/Configurar-modem-ZTE-ZXDSL-831-II-como-router.html]("http://www.taringa.net/posts/ebooks-tutoriales/2697873/Configurar-modem-ZTE-ZXDSL-831-II-como-router.html")

suerte! :p

---

### Post by roroland on 2010-03-16
Hola, gracias por tu respuesta...

El tema es que ya funciona como router sin problemas bajo windows XP, pero cuando reinicio e ingreso a Ubuntu el sistema no lo toma, no me puedo conectar. Y por lo que tengo entendido una vez que el modem esta en modo router, éste le envia todos los datos necesarios al sistema (ubuntu) para conectarse sin tener que hacer nada mas.

Pero no funciona...

Gracias de todas maneras.

---

### Post by roroland on 2010-03-17
Nadie puede ayudarme ???? :cry:

---

### Post by guillermolisi on 2010-03-17
> **roroland said:**
> Nadie puede ayudarme ???? :cry:
Algun mensaje de error ? Alguna otra pista que permita entender mejor que esta pasando en esa maquina ?

En teoria es como bien vos decis: El modem configurado como router hace el discado y conecta la PC con IP dinamica y establece los demas parametros para DNSs y gateway. Siendo asi en la PC no hace falta nada mas que un buen cable y una placa Ehternet.

---

### Post by roroland on 2010-03-17
Hola, eso es lo extraño, el unico mensaje de error es el panel de estado de red (el doble monitorcito arriba aparece con una cruz roja ) ...

Si hago boton derecho y hago click en " estado de conexion" dice "error: no se puedo encontrar una conexion valida" o algo similar no recuerdo bien.

Borre todos los parametros de conexion y empece de cero, agregue una conexion nueva DSL y solo active el checkbox de "conectar automaticamente"  y mis datos de usuario y contraseña de speedy (sino no me deja crear la nueva conexion), lo demas lo deje todo automatico.

Insisto, al tener doble booteo con xp se que tanto el modem como speedy funcionan bien ya que no tengo problemas bajo windows.
En modo modem podia conectarme desde Ubuntu mediante pppoeconf...asi qu tiene q ser algo mal de configuracion.

Alguna sugerencia ?
Gracias

---

### Post by rojojuan on 2010-03-17
Para probar:

Si salís de XP apagá completamente la computadora y apaga también el modem. Recién entonces arrancás nuevamente y entrá a Ubuntu. Y viceversa.

---

### Post by guillermolisi on 2010-03-17
Sugiero que muestres la salida del comando en consola/terminal ```
sudo lshw
``` asi podremos saber a ciencia cierta como reconoce Ubuntu esa placa de red.

Tambien seria conveniente ver la salida en consola/terminal del comando ```
ifconfig -a
```

Si el hardware esta bien, tal como comprobas con Windows, puede ser que el problema sea con los drivers en Ubuntu, por eso la primera sugerencia.

---

### Post by roroland on 2010-03-17
Ya lo hice hoy eso...Una vez que configure nuevamente las conexiones, reinicie ubuntu apagando previamente el modem y nada...

En el campo "servicio" dentro de la configuracion de la conexion donde va el usuario y la contraseña de speedy debo poner algo ?

Debo agregar el MAC ?

Esos campos estan vacios ahora.
Gracias

PD: Ahora en cuanto los tenga les adjunto los datos que me piden

---

### Post by roroland on 2010-03-17
Ok, aqui les adjunto los resultados...


[SIZE=3]**sudo lshw**[/SIZE]

 description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: nVidia-nForce2
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: 1.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F5 (09/23/2003)
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 1920MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM 65535 MHz (0.0 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 256MiB
             clock: 1110MHz (0.9ns)
        *-bank:1
             description: DIMM 65535 MHz (0.0 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 256MiB
             clock: 1110MHz (0.9ns)
        *-bank:2
             description: DIMM 65535 MHz (0.0 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MiB
             clock: 1110MHz (0.9ns)
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia
          resources: irq:0 memory:e0000000-e3ffffff(prefetchable)
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 0
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:9 ioport:e800(size=32)
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:e7002000-e7002fff
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:e7003000-e7003fff
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:e7004000-e70040ff
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:e6000000-e6ffffff
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 7
                bus info: pci@0000:01:07.0
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
                resources: irq:19 ioport:c000(size=32)
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 7.1
                bus info: pci@0000:01:07.1
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: irq:0 ioport:c400(size=8)
           *-network DISABLED
                description: Ethernet interface
                product: VT6105/VT6106S [Rhine-III]
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 8b
                serial: 00:1b:11:11:19:b9
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
                resources: irq:16 ioport:c800(size=256) memory:e6000000-e60000ff
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: scsi0
             logical name: scsi1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-disk:0
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.06
                serial: 5JX0TNKF
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ac55ac55
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/B61871CA18718A5F
                   version: 3.1
                   serial: b886aef4-e4a8-ab4e-a886-6db9aae7c525
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-02-25 06:39:17 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 16GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 760MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: SAMSUNG SP0802N
                physical id: 0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: TK20
                serial: S00JJ1FL509464
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cb7c4ee4
              *-volume:0
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /media/743C3E9B3C3E5876
                      capacity: 39GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   version: 3.1
                   serial: 7820c0ed-4dc8-1d40-bafa-7724cd893ced
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2006-08-29 12:53:23 filesystem=ntfs label=Disco Local state=clean
           *-cdrom
                description: DVD writer
                product: DVDRW SHW-160P6S
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PS0A
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:e4000000-e5ffffff memory:c0000000-dfffffff(prefetchable)
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV350 AR [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: memory:c0000000-cfffffff(prefetchable) ioport:d000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff(prefetchable)
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AR [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: memory:d0000000-dfffffff(prefetchable) memory:e5010000-e501ffff


[SIZE=3]**ifconfig -a**[/SIZE]


eth0      Link encap:Ethernet  direcciónHW 00:1b:11:11:19:b9  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 Dirección base: 0x2000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by roroland on 2010-03-17
Alguna sugerencia ?

---

### Post by guillermolisi on 2010-03-17
Si, que no funciona porque por alguna razon que aun no logro dislumbrar, la placa de red esta deshabilitada:
> *-**[COLOR=Blue]network DISABLED[/COLOR]**
                description: Ethernet interface
                product: VT6105/VT6106S [Rhine-III]
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 8b
                serial: 00:1b:11:11:19:b9
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
                resources: irq:16 ioport:c800(size=256) memory:e6000000-e60000ffpor consiguiente la salida de ifconfig da como resultado una placa de red sin valores asignados (eth0). La buena noticia que la placa de red se ve con lo cual lo que habria que hacer es o habilitarla via Network Manager (que creo es lo que no resulta hasta el momento) o editar el archivo /etc/network/interfaces y configurar ahi la placa para que funcione con el router.

Si optas por esta ultima alternativa, deberias usar en una consola/terminal ```
sudo nano /etc/network/interfaces
``` (nano o tu editor de texto simple preferido) y cambiar/agregar, dependiendo si existe el bloque o no, lo siguiente:
```
iface eth0 inet dhcp
auto eth0
```guardas los cambios y ejecutas en consol/terminal ```
sudo /etc/init.d/networking restart
```para que reinicie el servicio de red.

Despues de esto la conexion deberia comenzar a funcionar sin mas tramite.

---

### Post by roroland on 2010-03-19
Hola, gracias por tu respuesta.

Hice la prueba pero me da un error, yo creo que el archivo debe estar mal. Te adjunto como tengo el archivo interfaces:

GNU nano 2.0.9        Fichero: /etc/network/interfaces                        

auto lo
iface lo inet loopback

[B]iface eth0 inet dhcp
auto eth0[/B]

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

Al ejecutar el refresh en la consola me dice lo siguiente:

rodrigo@rodrigo-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:7: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:7: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

Podrias darme todo el codigo completo de interfaces?

Gracias

---

### Post by guillermolisi on 2010-03-19
> **roroland said:**
> Hola, gracias por tu respuesta.

Hice la prueba pero me da un error, yo creo que el archivo debe estar mal. Te adjunto como tengo el archivo interfaces:

GNU nano 2.0.9        Fichero: /etc/network/interfaces                        

auto lo
iface lo inet loopback

[B]iface eth0 inet dhcp
auto eth0[/B]

pre-up /sbin/ifconfig eth0 up # **[COLOR=Blue]line maintained by pppoeconf[/COLOR]**
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

Al ejecutar el refresh en la consola me dice lo siguiente:

rodrigo@rodrigo-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:7: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:7: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

Podrias darme todo el codigo completo de interfaces?

Gracias
Estas teniendo ese problema, y el origen de todo esto, en que aun estas usando pppoe y por eso no te deja administrar manualmente la interface de red (que es lo que se logra cuando editas configurando la placa).

Remove completamente el paquete pppoe asi no interfiere, ademas con conexion a un router no deberia hacerte falta ya que es este ultimo el que se encarga de discar.

Si el /etc/network/interfaces esta tal como lo mostraste, esta bien asi. El problema es que esa interface esta tomada por pppoe para su gestion de conexion.

---

### Post by bichopro on 2010-03-19
> **guillermolisi said:**
> Estas teniendo ese problema, y el origen de todo esto, en que aun estas usando pppoe y por eso no te deja administrar manualmente la interface de red (que es lo que se logra cuando editas configurando la placa).

Remove completamente el paquete pppoe asi no interfiere, ademas con conexion a un router no deberia hacerte falta ya que es este ultimo el que se encarga de discar.

Si el /etc/network/interfaces esta tal como lo mostraste, esta bien asi. El problema es que esa interface esta tomada por pppoe para su gestion de conexion.

Exacto, el asunto es que antes tu marcabas login y pass y ahora eso lo hace el router por lo que están chocando ambas configuraciones. Tienes que borrar cualquier configuración anterior de adsl o en el pppoe para que así la próxima vez se conecte de manera automática, tal como imagino pasa en tu xp.

---

### Post by roroland on 2010-03-19
Entiendo, perdon la ignorancia pero de donde borro todo lo que es pppoe de paquetes synaptics ?

O simplemente borro cualquier conexion de red que este agregada al administrador de redes ?

GRacias

---

### Post by guillermolisi on 2010-03-19
> **roroland said:**
> Entiendo, perdon la ignorancia pero de donde borro todo lo que es pppoe de paquetes synaptics ?

O simplemente borro cualquier conexion de red que este agregada al administrador de redes ?

GRacias
Para remover completamente un paquete (y sus dependencias que este deje libres) te recomiendo usar el Gestor de Paquetes, Synaptic. Buscas el paquete en cuestion (con su buscador) y lo marcas con un click eligiendo Remover Completamente (incluye los archivos de configuracion del paquete) en el menu contextual que te aparecera. 

Revisa la lista de lo que se removera y si tenes alguna duda mostrala aqui antes de confirmarla, no vaya a ser que se borre algo que no se deba quitar.

Si en el futuro volves a necesitar pppoe con el mismo utilitario podes volverlo a instalar.

---

### Post by roroland on 2010-03-22
Buenas,

Hice todo, removi los paquetes de pppoe, reinicie pc y modem y nada...mismos problemas.

Les adjunto los informes que me da el sistema ahora que removi los paquetes de pppoe


```


rodrigo@rodrigo-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:7: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:7: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"


```


```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

```

```

rodrigo@rodrigo-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  direcciónHW 00:1b:11:11:19:b9  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 Dirección base: 0x2000 

```

```

rodrigo@rodrigo-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 00:1b:11:11:19:b9  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 Dirección base: 0x2000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)

```

```


rodrigo@rodrigo-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  direcciónHW 00:1b:11:11:19:b9  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 Dirección base: 0x2000 

```

```

rodrigo@rodrigo-desktop:~$ sudo lshw
rodrigo-desktop           
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: nVidia-nForce2
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: 1.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F5 (09/23/2003)
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 1920MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM 65535 MHz (0.0 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 256MiB
             clock: 1110MHz (0.9ns)
        *-bank:1
             description: DIMM 65535 MHz (0.0 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 256MiB
             clock: 1110MHz (0.9ns)
        *-bank:2
             description: DIMM 65535 MHz (0.0 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MiB
             clock: 1110MHz (0.9ns)
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia
          resources: irq:0 memory:e0000000-e3ffffff(prefetchable)
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 0
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:9 ioport:e800(size=32)
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:e7002000-e7002fff
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:e7003000-e7003fff
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:e7004000-e70040ff
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:e6000000-e6ffffff
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 7
                bus info: pci@0000:01:07.0
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
                resources: irq:19 ioport:c000(size=32)
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 7.1
                bus info: pci@0000:01:07.1
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: irq:0 ioport:c400(size=8)
           *-network DISABLED
                description: Ethernet interface
                product: VT6105/VT6106S [Rhine-III]
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 8b
                serial: 00:1b:11:11:19:b9
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
                resources: irq:16 ioport:c800(size=256) memory:e6000000-e60000ff
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: scsi0
             logical name: scsi1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-disk:0
                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.06
                serial: 5JX0TNKF
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ac55ac55
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/B61871CA18718A5F
                   version: 3.1
                   serial: b886aef4-e4a8-ab4e-a886-6db9aae7c525
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-02-25 06:39:17 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 16GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 760MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: SAMSUNG SP0802N
                physical id: 0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: TK20
                serial: S00JJ1FL509464
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cb7c4ee4
              *-volume:0
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   size: 39GiB
                   capacity: 39GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 39GiB
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   version: 3.1
                   serial: 7820c0ed-4dc8-1d40-bafa-7724cd893ced
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2006-08-29 12:53:23 filesystem=ntfs label=Disco Local state=clean
           *-cdrom
                description: DVD writer
                product: DVDRW SHW-160P6S
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PS0A
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:e4000000-e5ffffff memory:c0000000-dfffffff(prefetchable)
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV350 AR [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: memory:c0000000-cfffffff(prefetchable) ioport:d000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff(prefetchable)
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AR [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: memory:d0000000-dfffffff(prefetchable) memory:e5010000-e501ffff



```



GRACIAS OJALA PUEDAN DARME UNA MANO YA NO SE QUE MAS PROBAR

---

### Post by guillermolisi on 2010-03-22
> **roroland said:**
> Buenas,

Hice todo, removi los paquetes de pppoe, reinicie pc y modem y nada...mismos problemas.

Les adjunto los informes que me da el sistema ahora que removi los paquetes de pppoe


```


rodrigo@rodrigo-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:7: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:7: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"


```
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

[COLOR=Blue]pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider[/COLOR]

```

GRACIAS OJALA PUEDAN DARME UNA MANO YA NO SE QUE MAS PROBAR
Te falta remover las lineas marcadas en azul del archivo /etc/network/interfaces.

---

### Post by roroland on 2010-03-23
Hola Guillermo, gracias por tu respuesta....sigue sin funcionar

Borre las lineas e hice un network restart:

```
rodrigo@rodrigo-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for rodrigo: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1698
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:11:11:19:b9
Sending on   LPF/eth0/00:1b:11:11:19:b9
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:11:11:19:b9
Sending on   LPF/eth0/00:1b:11:11:19:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
```

Borre toda conexion configurada en DSL, reinicie y no funcionaba, por las dudas hice una coenxion nueva en DSL y tampoco...

Alguna idea o estoy frito ? #-o

Gracias

---

### Post by guillermolisi on 2010-03-23
Vamos bien, vamos bien porque la salida de consola exponiendo que buscaba un server DHCP es buena señal. Ahora hay que ver por que razon no logra una IP dinamica desde el Router. Tiene el servicio DHCP server habilitado ? Disca y conecta correctamente ?

---

### Post by roroland on 2010-03-29
Hola, perdon por la tardanza en mi respuesta. 

No tenia habilitado el DHCP, lo habilite y configure segun mi entender, le puse lo siguiente:

Start IP address: 192.168.1.1
End IP address: 192.168.1.30

Lease Time: 3 days 0 hours 0 minutes


Pese a esto sigue sin funcionar internet en Ubuntu, aunque el log de la Terminal muestra algo mas alentador aparentemente.

Listening on LPF/eth0/00:1b:11:11:19:b9
Sending on   LPF/eth0/00:1b:11:11:19:b9
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:11:11:19:b9
Sending on   LPF/eth0/00:1b:11:11:19:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.1 from 192.168.1.1
DHCPREQUEST of 192.168.1.1 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.1 from 192.168.1.1
bound to 192.168.1.1 -- renewal in 103004 seconds.
                                                                         [ OK ]


Que debo hacer ahora ? Recuerden que en XP funciona bien internet.

---

### Post by guillermolisi on 2010-03-29
Lo unico que necesitas de DHCP es el cliente porque el servidor te lo brinda tu ISP (Speedy) y le asigna una IP publica al router.

Luego, si en tu PC no usas IPs estatica, tu router deberia asignar IPs privadas a las PCs que se le conecten. Fijate si el router tiene habilitado el servicio DHCP para la LAN (tu red interna).

Si no lo queres habilitar tendras que darles IPs estaticas a las maquinas que conectes en esa red para que tengan salida a Internet a traves del router.

Agregar DHCP server a tu PC es complicar las cosas. Yo lo desinstalaria porque no es funcional a tu problema (el que hay que habilitar es el del router para la LAN).

---

### Post by roroland on 2010-03-29
Hola, es exactamente lo que hice creo...te adjunto captura a ver si hablamos de lo mismo...


[IMG]http://www.sonicbyte.com/dhcp.jpg[/IMG]

---

### Post by guillermolisi on 2010-03-29
Si, perfecto ! Disculpame pero entendi que habias instalado DHCP server en una PC !
Ahora fijate si las maquinas reciben asignacion de IP desde el router (por el rango asignado deberias confirmar que funciona).

Luego proba con ping para verificar que se vean entre si a ese nivel y despues vemos lo de la salida a Internet y la navegacion.

Edit: Para probar con ping solo tenes que ejecutar en consola/terminal ```
ping <ip_de_la_otra-maquina>
```Si no tenes otra maquina en la LAN, podes probar con
```
ping 72.14.209.104
```que es la IP publica de google.com

Deberias ver algo asi:
> 
PING google.com (72.14.209.104) 56(84) bytes of data.
64 bytes from bf-in-f104.1e100.net (72.14.209.104): icmp_seq=1 ttl=56 time=237 ms
64 bytes from bf-in-f104.1e100.net (72.14.209.104): icmp_seq=2 ttl=56 time=235 ms

---

### Post by roroland on 2010-03-29
Hola, gracias nuevamente por tu respuesta, pero creo que hay una confusion, la PC es 1 sola.
El tema es que tiene un doble booteo con XP en una particion y Ubuntu en la otra, disculpa si no fui lo suficientemente claro. No se si esto cambia en algo lo que viene siendo el hilo hasta ahora.

El punto es que entro en Windows xp con la configuracion actual del router y ingreso sin problemas a speedy, pero esta misma configuracion no la toma Ubuntu cuando reinicio e ingreso desde Ubuntu

Gracias !

---

### Post by roroland on 2010-03-30
Hice el ping pero me dice que no puede acceder al host, si le doy ping al localhost funciona bien pero no a otra cosa.

Hice la prueba de bootear con el live cd y pude conectarme a internet sin problemas, estoy pensando sino sera mejor reinstalar ubuntu y listo.

Una de las cosas q note con el live cd es que puedo editar la configuracion de la placa de red eth0, lo cual finalmente permitio q me conectara en el live cd pero en el ubuntu q tengo instalado no me permite hacerlo.

Que es mas sensato entonces ? Reinstalar ?

PD: Por cierto como reinstalo sin dañar el doble booteo que tengo ahora con windows xp ? No se como preparar las particiones para q siga booteando ambos sistemas y no me haga lio en el xp.

Gracias por la ayuda

---

### Post by guillermolisi on 2010-03-30
> **roroland said:**
> Hice el ping pero me dice que no puede acceder al host, si le doy ping al localhost funciona bien pero no a otra cosa.

Hice la prueba de bootear con el live cd y pude conectarme a internet sin problemas, estoy pensando sino sera mejor reinstalar ubuntu y listo.

Una de las cosas q note con el live cd es que puedo editar la configuracion de la placa de red eth0, lo cual finalmente permitio q me conectara en el live cd pero en el ubuntu q tengo instalado no me permite hacerlo.

Que es mas sensato entonces ? Reinstalar ?

PD: Por cierto como reinstalo sin dañar el doble booteo que tengo ahora con windows xp ? No se como preparar las particiones para q siga booteando ambos sistemas y no me haga lio en el xp.

Gracias por la ayuda
Si queres editar la configuracion de tu placa de red solo tenes que ingresar ```
sudo nano /etc/network/interfaces
```en una terminal/consola

Si el ping a una IP publica te dio negativo, entonces no se esta conectando con el router y de ahi a Internet.

Si configuras a mano la placa de red recorda que Network Manager te dira que no hay ninguna conexion ya que las placas administradas a mano no pueden ser gestionadas por NM.

Otra alternativa es que configures la placa y su conexion via Network Manager, ya probaste esta alternativa ?

---

### Post by roroland on 2010-03-30
Hola, no tengo idea de como hacerlo, no hay un codigo " default " para resetear el archivo interfaces ?

Digo esto porque con el live cd pude conectarme sin problemas una vez que configure los datos de speedy.

Gracias

---

### Post by guillermolisi on 2010-03-30
> **roroland said:**
> Hola, no tengo idea de como hacerlo, no hay un codigo " default " para resetear el archivo interfaces ?

Digo esto porque con el live cd pude conectarme sin problemas una vez que configure los datos de speedy.

Gracias
El modem de Speedy esta como router ? Si es asi, probaste de conectarte ahora con el LiveCD ?

Si probaste y conecta lo hace usando el Network Manager que es lo que te sugeria usar en mi ultimo mensaje pero iniciado la maquina desde el Ubuntu instalado.

Con Network Manager no deberias tocar nada y deberia conectar pero tambien podes configurar la placa de red a traves de su opcion Gestionar Conexiones.

---

### Post by Mauri233 on 2010-11-30
Te recomiendo que o llames a algun tecnico o pidas que los de [speedy]("http://www.telefonica.com.ar") envien uno para configurartelo si se te hace muy engorroso. Yo tambien quize configurarlo asi en su momento y tuve problemas hasta q me canse y decidi q un tecnico lo solucione.


saludos

---

### Post by gmunioz on 2010-12-01
Sugerencia:

Ejecuta en la consola de Windows, conectado a internet

ipconfig /all

Anota la salida

Reinicia con Ubuntu
Edita el archivo /etc/network/interfaces y
coloca en el los parámetros que informó windows

============================================
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.x
gateway 192.168.1.x
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
============================================

---

