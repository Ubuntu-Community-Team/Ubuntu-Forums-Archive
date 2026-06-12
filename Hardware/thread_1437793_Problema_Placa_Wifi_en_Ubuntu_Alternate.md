---
title: "Problema Placa Wifi en Ubuntu Alternate"
date: 2010-03-24
forum: Hardware
---

### Post by jawifi01 on 2010-03-24
Buen día, sigo molestando.
Resulta que un amigo se armó un media cententer con una maquina que tenia en desuso y me llamo a mi para que le ayude ¿?¡! (Cree que yo se mucho...pobre) y siguiendo algunos tutoriales de internet le pudimos dar forma a la cuestion. 

El problema que tenemos ahora es que le quiso poner una conexion wifi y para eso se compró (sin preguntar) una placa encore, modelo: ENLWI-G2

El sistema base es un Ubuntu Alternate 9.04, instalamos las wireless-tools y al darle iwconfig, aparece la placa como wlan0.

Entonces yo edité a mano el /etc/interfaces y agregué todos los datos de la placa:

auto wlan0
iface wlan0 inet static
address 192.168.0.55
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 192.168.0.1 4.4.4.4 8.8.8.8
wireless-essid redwifi
wireless-key 0123456789

El problema se presenta ya que no puedo levanar la placa de red wifi, le doy ifup wlan0 y se muere la maquina, no funciona el teclado, ni nada, no puedo cambiar de consola con alt+f1, nada de nada. Tengo que apagarla desde el boton reset y cuando reinicia...igual, se queda muerta durante el arranque y solo puedo solucionar reiniciando con el cd de ubuntu y entrando a recuperación, borro la parte de wifi del archivo interfaces y listo, sale andando, pero como es obvio sin wifi, llevo mas de 6 horas renegando y no se por donde revisar.
En lspci aparece:

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

Bueno, si alguien me puede orientar, agradecido.

PD: Donde dije que mi amigo (Pablo) cree que yo se es porque quizas manejo la consola un cachito más que el, pero yo, no se mucho que digamos ;)

Gracias

---

### Post by guillermolisi on 2010-03-24
Nos mostrarias la salida de "ifconfig" en una consola/terminal para tener algo mas de informacion ?
Y ya que estamos vendria muy bien la salida de "sudo lshw" (sin comillas, en todos los casos).

Veo que le das IP estatica a la placa, supongo que los valores utilizados estan de acuerdo con los que corresponden a la red que queres conectar, inclusive los del gateway (que deberia ser la IP interna del router/AP). Es asi ?

La red inalambrica, esta con o sin seguridad ? Si tiene seguridad/encripcion, cual se esta usando ?

---

### Post by totolinux on 2010-03-24
Hola no se si te sirve, pero tengo una placa igual a esa y es imposible que me funcione correctamente en ubuntu 9.04 y en xp. en algunos casos se cuelga y en otros se entrecorta o se bloquea a intervalos regulares. termine cambiando a una usb rtl8187 (encore).
aqui algunas sugerencias en ese momento y mi experiencia  [http://ubuntuforums.org/showthread.php?t=1322831&highlight=ad+hoc](http://ubuntuforums.org/showthread.php?t=1322831&highlight=ad+hoc)

---

### Post by jawifi01 on 2010-03-24
> **guillermolisi said:**
> Nos mostrarias la salida de "ifconfig" en una consola/terminal para tener algo mas de informacion ?
Y ya que estamos vendria muy bien la salida de "sudo lshw" (sin comillas, en todos los casos).

el ifconfig muestra la placa eth0:

eth0      Link encap:Ethernet  direcciónHW 00:50:bf:06:78:4e  
          inet dirección:192.168.0.50  Difusión:192.168.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::250:bfff:fe06:784e/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:445866 (445.8 KB)  TX bytes:34824 (34.8 KB)
          Interrupción:18 Dirección base: 0xb000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

y el otro dice: (es muuuy largo!!!)

mediac@mediac:~$ sudo lshw
[sudo] password for mediac: 
mediac                    
    description: Computer
    product: Springdale-G
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=4AB5E3BA-A58B-11D8-80AD-00E018A327D7
  *-core
       description: Motherboard
       product: D865PERL
       vendor: Intel Corporation
       physical id: 0
       version: AAC27648-210
       serial: BTRL42000138
       slot: Audio Mic In
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: RL86510A.86A.0089.P21.0502132202 (02/13/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: J2E1
          size: 2800MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 39
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 320 MHz (3.1 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: SerNum1
             slot: J5G1
             size: 512MiB
             width: 64 bits
             clock: 320MHz (3.1ns)
        *-bank:1
             description: DIMM DDR Synchronous 320 MHz (3.1 ns) [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: SerNum2
             slot: J5G2
             width: 64 bits
             clock: 320MHz (3.1ns)
        *-bank:2
             description: DIMM DDR Synchronous 320 MHz (3.1 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: SerNum3
             slot: J5H1
             size: 512MiB
             width: 64 bits
             clock: 320MHz (3.1ns)
        *-bank:3
             description: DIMM DDR Synchronous 320 MHz (3.1 ns) [empty]
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: SerNum4
             slot: J5H2
             width: 64 bits
             clock: 320MHz (3.1ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 440 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: c1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 2.1
                bus info: pci@0000:02:02.1
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
           *-network:0 DISABLED
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: wmaster0
                version: 20
                serial: 00:08:54:98:b1:a5
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 latency=32 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth0
                version: 10
                serial: 00:50:bf:06:78:4e
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.50 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: HDS728080PLAT20
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PF2O
                serial: PFD266S4T8LPHV
                size: 76GiB (82GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=04290428
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a0fc0baa-c133-43c7-b9eb-1fee7f3ed9d9
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-03-23 20:19:20 filesystem=ext4 modified=2010-03-24 09:12:56 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-03-24 09:07:00 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 6ecc2d05-b949-4129-9214-ebba5060f622
                   size: 1906MiB
                   capacity: 1906MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /mediac1
                   version: 1.0
                   serial: 139a45d4-8cbe-45a7-9348-b50dd1bce22f
                   size: 65GiB
                   capacity: 65GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-03-22 23:01:45 filesystem=ext4 modified=2010-03-24 16:46:46 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2010-03-24 16:46:46 state=mounted
           *-cdrom
                description: DVD writer
                product: DVD RW DW-Q30A
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: YYS4
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: Hitachi HDS72161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: P22O
                serial: PVC300Z20WVN3J
                size: 153GiB (164GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=85446ccb
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /mediac2
                   version: 1.0
                   serial: 28222879-c40f-4259-a056-bd7d20eb83fa
                   size: 153GiB
                   capacity: 153GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-12-16 14:34:35 filesystem=ext4 lastmountpoint=/home&#65533;*9&#65533;&#65533;&#65533;&#65533;XWC&#65533;&#65533;&#65533;&#65533;&#63294;&#65533;iW&#65533;&#65533;NE&#65533;&#65533;NE&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-03-24 16:46:46 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2010-03-24 16:46:46 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0


Esto es todo copy&paste de la máquina del problema.


> **guillermolisi said:**
> Veo que le das IP estatica a la placa, supongo que los valores utilizados estan de acuerdo con los que corresponden a la red que queres conectar, inclusive los del gateway (que deberia ser la IP interna del router/AP). Es asi ?

si, fijate que en la eth0 tambien tiene ip fija y es 192.168.0.50, por eso a la wifi le puse 192.168.0.55, el GW es 192.168.0.1, que es la del router, asi que eso es lo único que se seguro que está bien.

> **guillermolisi said:**
> La red inalambrica, esta con o sin seguridad ? Si tiene seguridad/encripcion, cual se esta usando ?

Esta con wep y la clave es 0123456789

Gracias

Juan

---

### Post by jawifi01 on 2010-03-24
> **totolinux said:**
> Hola no se si te sirve, pero tengo una placa igual a esa y es imposible que me funcione correctamente en ubuntu 9.04 y en xp. en algunos casos se cuelga y en otros se entrecorta o se bloquea a intervalos regulares. termine cambiando a una usb rtl8187 (encore).
aqui algunas sugerencias en ese momento y mi experiencia  [http://ubuntuforums.org/showthread.php?t=1322831&highlight=ad+hoc](http://ubuntuforums.org/showthread.php?t=1322831&highlight=ad+hoc)


Gracias por la info, aunque sea una mala noticia :(
Ahora voy  a revisar ese hilo de todas maneras.

gracias

---

### Post by guillermolisi on 2010-03-24
Esta deshabilitada. Fijate si hay algun switch que la encienda o apague.

> *-network:0 [COLOR=Blue]DISABLED[/COLOR]
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: wmaster0
                version: 20
                serial: 00:08:54:98:b1:a5
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rtl8180 latency=32 maxlatency=64 mingnt=32 module=[COLOR=DarkOrange]rtl8180[/COLOR] multicast=yes wireless=IEEE 802.11bgFijate que el modulo/driver que maneja la placa es el 8180 (indicado en color), o sea que hasta ahi esta bien solo que la maquina la ve apagada.

Proba primero sin cifrado, con la red abierta y si comprobas que funciona despues la cerras. WEP no es precisamente una encripcion segura.WPA2 personal es mi recomendacion.

Paradojicamente, la RTL8187 para mi tambien es un chip conflictivo.

---

### Post by jawifi01 on 2010-03-25
Acá sigo renegando, ya se está conviertiendo en una cruzada hacer funcar esta condenada placa wifi!!!

Quiero compilar un driver que baje de la página de realtek y cuando hago make dentro del directorio donde descomprimí el tar.gz me dice:

make: *** /lib/modules/2.6.28-18-generic/build: No existe el fichero ó directorio.  Alto.
make: *** [all] Error 2

Y no se que mas instalar para que pueda funcionar, revisé el directorio /lib/modules/2.6.28-18-generic y ese archivo build no está, pero no se con apt-get qué debería instalarlo.

Les aclaro además que no tengo entorno gráfico, es un linux alternate SIN entorno gráfico, ya que se va a usar solo como MediaCenter.

Gracias

Juan

---

### Post by totolinux on 2010-03-26
instalaste el metapaquete para compilar?
sudo aptitude install build-essential
yo no se mucho de este tema pero Build-essential es en realidad un metapaquete, o lo que es lo mismo: un paquete que contiene otros paquetes:


        * g++ 

        * g++-3.3 

        * gcc 

        * gcc-3.3 

        * libstdc++5-3.3-dev 


Por lo que instalamos las librerías y paquetes que necesitaremos para poder generar archivos binarios.


fuente: [http://doc.ubuntu-es.org/Compilar_programas](http://doc.ubuntu-es.org/Compilar_programas)

---

### Post by guillermolisi on 2010-03-26
> **jawifi01 said:**
> Acá sigo renegando, ya se está conviertiendo en una cruzada hacer funcar esta condenada placa wifi!!!

Quiero compilar un driver que baje de la página de realtek y cuando hago make dentro del directorio donde descomprimí el tar.gz me dice:

make: *** /lib/modules/2.6.28-18-generic/build: No existe el fichero ó directorio.  Alto.
make: *** [all] Error 2

Y no se que mas instalar para que pueda funcionar, revisé el directorio /lib/modules/2.6.28-18-generic y ese archivo build no está, pero no se con apt-get qué debería instalarlo.

Les aclaro además que no tengo entorno gráfico, es un linux alternate SIN entorno gráfico, ya que se va a usar solo como MediaCenter.

Gracias

Juan
Estas compilando el driver 8185 ? Segun lo que lei en el subforo de Networking & Wireless pareceria ser el unico que funciona pero la gran mayoria de casos positivos son sobre kernel de la 8.04. Los que tienen kernel mas moderno dicen experimentar problemas de calidad de señal y estabilidad en la conexion.

Tene en cuenta que si cambia la version del kernel (con una actualizacion) vas a tener que volver a compilar el driver.

Considerando que no es una notebook (o por lo menos me parecio interpretar eso) y que una placa de red inalambrica no es un componente caro, en tu lugar la cambiaria por otra marca que traiga chip Atheros o Intel (no Broadcom, no Realtek serie 818x).

Son unos pesos mas, pero cuanto vale tu tiempo tratando de hacer funcionar algo que muchos ya han probado sin exito concreto ?

---

### Post by jawifi01 on 2010-03-28
Lo solucioné instalandole ndiswrapper y el driver para Windows98, reinicié y salió andando perfecto.

Saludos

---

### Post by guillermolisi on 2010-03-28
> **jawifi01 said:**
> Lo solucioné instalandole ndiswrapper y el driver para Windows98, reinicié y salió andando perfecto.

Saludos
Perfecto, siempre esta esa alternativa que es mas economica que cambiar la placa (o la notebook). Comenta, por favor, como te funciona con ndiswrapper asi completamos el cuadro para algun otro que pase por la misma experiencia.

---

