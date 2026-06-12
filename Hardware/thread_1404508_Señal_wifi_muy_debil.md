---
title: "Señal wifi muy debil"
date: 2010-02-11
forum: Hardware
---

### Post by akiestudio on 2010-02-11
Hola buenas, tengo instalada una tarjeta de red y la señal es muy baja cuando he instalado los driver sale lo siguiente:

Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files 
development package or crate a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux


he intentado seguir algunos post para instalar los  header y hacer el enlace simbolico ,pero no he conseguido nada , la tarjeta de red es:


05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
    Subsystem: ASUSTeK Computer Inc. Device 811a
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (5750ns min, 7750ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at ff9f4000 (32-bit, non-prefetchable) [size=16K]
    Region 1: I/O ports at b800 [size=256]
    Expansion ROM at 88000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: skge
    Kernel modules: skge


Alguien puede decirme como puedo instalarla , para recebir una buena señal , uso el wicd. 

Gracias

---

### Post by alfplayer on 2010-02-11
> **akiestudio said:**
> 05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
    Subsystem: ASUSTeK Computer Inc. Device 811a
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (5750ns min, 7750ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at ff9f4000 (32-bit, non-prefetchable) [size=16K]
    Region 1: I/O ports at b800 [size=256]
    Expansion ROM at 88000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: skge
    Kernel modules: skge

Esta tarjeta de red es por cable (Gigabit), no es inalámbrica.

---

### Post by guillermolisi on 2010-02-11
> **akiestudio said:**
> Hola buenas, tengo instalada una tarjeta de red y la señal es muy baja cuando he instalado los driver sale lo siguiente:

Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files 
development package or crate a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux


he intentado seguir algunos post para instalar los  header y hacer el enlace simbolico ,pero no he conseguido nada 

Alguien puede decirme como puedo instalarla , para recebir una buena señal , uso el wicd. 

Gracias
Podes instalar los headers para la version de kernel que estas usando con Synaptic. Esto siempre que efectivamente NO los tengas instalados y el error lo de el script de instalacion del driver de la placa inalambrica porque los busca en un lugar donde no estan.

Contanos, por favor, como es el procedimiento que estas llevando a cabo con esa placa.

Tambien seria muy conveniente contar con las salidas de los comandos "lspci" y "lshw" (sin las comillas) ejecutados en una consola/terminal.

---

### Post by akiestudio on 2010-02-12
Ya he instalado todos los archivos de header de mi kernel ,pero cuando instalo sale lo siguiente:
```
Create tmp dir (/tmp/Sk98IiPXZGiJLFlnLnUhhDlgm)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.28-11-generic)                             [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (2)                                             [   OK   ]
Check architecture./install.sh: line 414: arch: orden no encontrada
 (found)                                                             [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (4.3.3) (Kernel:4.3.3 == gcc:4.3.3)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files 
development package or crate a symbolic link from the 
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of sk98lin driver module failed.
Delete temp directories (done)                
```
lscpi:```
fran@fran-desktop:~/Escritorio/Marvell_Lan$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900]
01:00.1 Display controller: ATI Technologies Inc R580 [Radeon X1900]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

```lshw :

```
 lshw
WARNING: you should run this program as super-user.
fran-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2013MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 2128MHz
          capacity: 2128MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
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
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: R580 [Radeon X1900]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
           *-display:1 UNCLAIMED
                description: Display controller
                product: R580 [Radeon X1900]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list
                configuration: driver=pata_jmicron latency=0
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8056 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 12
                serial: 00:18:f3:2a:9e:80
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:05:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-network DISABLED
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 4
                bus info: pci@0000:05:04.0
                logical name: eth1
                version: 14
                serial: 00:17:31:67:b3:a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 maxlatency=31 mingnt=23 module=skge multicast=yes
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:02:12:81
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.95 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:d8:13:bd:cd:82
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```Gracias por la ayuda, en windows la señal es bastante buena, pero aqui en ubuntu no tiene mas de una raya.

---

### Post by alfplayer on 2010-02-12
Lo que hay que saber es el chipset del adaptador de red. Si es USB se puede obtener ejecutando el comando lsusb.

---

### Post by guillermolisi on 2010-02-12
Debe ser USB porque no aparece en la lista de dispositivos PCI (salvo que esa placa posee dos adaptadores de red Ethernet).

---

### Post by alfplayer on 2010-02-12
Me imagino que el 88E8001 es integrado, el 88E8056 en una placa PCI-E y la que tiene señal baja una USB. La señal baja es un problema conocido en algunos adaptadores inalámbricos.

---

### Post by akiestudio on 2010-02-14
He formateado de nuevo el pc, porque tuve problemas con mi tarjeta grafica y no arrancaba el ubuntu,asi que esta sin instalarle nada.
Mi placa es una asus pb5-deluxe wifi , y haciendo lsubs. sale:```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Hay alguna manera de aumentarle la señal, con mi tarjeta , en windows la señal es bastante buena y en ubuntu casi ni tiene.

Saludos

---

### Post by guillermolisi on 2010-02-14
Por lo vengo leyendo sobre instalaciones que usan el chip RTL8187 tenes bastante suerte en que funcione, aunque sea con poca potencia. Me parece que los drivers que se estan usando les falta un poco mas de coccion para que esten a la altura de los demas (Atheros, Broadcom y chips anteriores de Realtek).

---

### Post by alfplayer on 2010-02-14
Es un problema conocido del RTL8187. Probaste o estás usando Ubuntu 9.10 ?

---

### Post by akiestudio on 2010-02-15
Estoy usando 9.04, con la 9.10 no pasa esto o sigue pasando igual...?

---

### Post by guillermolisi on 2010-02-15
> **akiestudio said:**
> Estoy usando 9.04, con la 9.10 no pasa esto o sigue pasando igual...?
Los casos reportados que he leido se refieren tanto a una como a otra version.
Igual con probar desde un LiveCD/USB con 9.10 y ver que resultados obtenes es solo cuestion de algunos minutos.

---

