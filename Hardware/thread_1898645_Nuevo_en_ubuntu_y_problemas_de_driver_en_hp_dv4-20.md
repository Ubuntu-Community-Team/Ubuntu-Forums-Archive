---
title: "Nuevo en ubuntu y problemas de driver en hp dv4-2028la"
date: 2011-12-21
forum: Hardware
---

### Post by franquetooo on 2011-12-21
Hola gente, soy nuevo en esto del soft libre, y instale hoy ubuntu 11.10 x64 y todo perfecto pero tengo un par de problemas con la tarjeta grafica y el sonido. 

el sonido me pasa esto, si no tengo conectado auriculars funciona barbaro, conecto los auriculares y se queda mudo y tengo que ir a sonido y seleccionar auriculares para que anden, pero si los desconecto tengo que repetir todo para que ande.. espero que sea entendible osea si uso el altavoz despues no puedo usar los auriculares. 

y el tema de los graficos mi notebook tiene dos procesadores graficos, intel para ahorro de energia (cuando esta en bateria) y ATI para cuando esta en alto rendimiento. windows los gestionaba pero en ubuntu ni siquiera puedo hacer que me reconosca la placa. 

Si me pueden ayudar estaria muy agradecido ya que no quisiera tener que volver a window$ por estos problemas pequeños 

muchas gracias! :D

---

### Post by granjero on 2011-12-22
hola, bienvenido, para poder darte una mano es necesario que nos cuentes que laptop tenés y que copies aca la salida de los comandos ```
sudo lshw
sudo lsusb
```
eso lo hacés abriendo una terminal y tipeando esos comandos.

salud!

---

### Post by franquetooo on 2011-12-22
Aca te dejo los datos que pedis 

[HTML] *-memory
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1067 MHz (0,9 ns)
             product: 16JSF25664HZ-1G1F1
             vendor: Micron
             physical id: 0
             serial: E933A0CE
             slot: SLOT1
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1067 MHz (0,9 ns)
             product: 16JSF25664HZ-1G1F1
             vendor: Micron
             physical id: 1
             serial: E933A0CF
             slot: SLOT2
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
          vendor: Intel Corp.
          physical id: d
          bus info: cpu@0
          version: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
          slot: CPU
          size: 1199MHz
          capacity: 1199MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L3 cache
             physical id: e
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 10
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 11
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: f
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:6000(size=4096) memory:e8400000-e84fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M93 [Mobility Radeon HD 4300/4500 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:16 memory:c0000000-cfffffff ioport:6000(size=256) memory:e8400000-e840ffff memory:e8420000-e843ffff
           *-multimedia
                description: Audio device
                product: RV710/730
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:45 memory:e8410000-e8413fff
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:7050(size=8)
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:e8506100-e850610f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:e8505c00-e8505fff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:e8500000-e8503fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:5000(size=4096) memory:e7400000-e83fffff ioport:e0400000(size=16777216)
           *-multimedia UNCLAIMED
                description: Multimedia controller
                product: SAA7160
                vendor: Philips Semiconductors
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: msi pciexpress pm bus_master cap_list
                configuration: latency=0
                resources: memory:e7400000-e74fffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:e6400000-e73fffff ioport:e1400000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM43225 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: c4:17:fe:86:73:cf
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-14-generic firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:e6400000-e6403fff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096) memory:e5400000-e63fffff ioport:e2400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 03
                serial: 70:5a:b6:9e:c8:94
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:41 ioport:3000(size=256) memory:e2404000-e2404fff memory:e2400000-e2403fff memory:e2420000-e243ffff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) memory:e4400000-e53fffff ioport:e3400000(size=16777216)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:e8505800-e8505bff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:7048(size=8) ioport:705c(size=4) ioport:7040(size=8) ioport:7058(size=4) ioport:7020(size=32) memory:e8505000-e85057ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK5056GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LH00
                serial: 4037F389S
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000034dd
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: ba330817-086c-405f-8afa-862749d20ba5
                   size: 461GiB
                   capacity: 461GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-21 06:21:31 filesystem=ext4 lastmountpoint=/ modified=2011-12-21 06:31:31 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-12-22 00:12:35 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3893MiB
                   capacity: 3893MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3893MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT30L
                vendor: hp
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: mP04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e8506000-e85060ff ioport:7000(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel ips latency=0
             resources: irq:18 memory:e8504000-e8504fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:7f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:7f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:7f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:7f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:7f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:7f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          bus info: usb@1:1.3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
     *-scsi:1
          physical id: 2
          bus info: usb@2:1.3
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
             size: 7592MiB (7960MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/F0B4-7808
                version: FAT32
                serial: f0b4-7808
                size: 7588MiB
                capacity: 7591MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-battery
       description: Lithium Ion Battery
       product: EV06047
       vendor: LGC-LGC
       physical id: 1
       slot: Primary
       capacity: 47520mWh
       configuration: voltage=10,8V
[/HTML]


y el otro

[HTML]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 138a:0005 Validity Sensors, Inc. VFS301 Fingerprint Reader
Bus 001 Device 005: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 003: ID 22b8:41d9 Motorola PCS Droid/Milestone
[/HTML]


Muchas gracias a quien me pueda ayudar porque es desesperante que si te anda el altavoz se te desactive el auricular y que la placa predeterminada sea la de alto rendimiento porque levanta mucha temperatura.. 

Saludoss!

---

### Post by franquetooo on 2011-12-22
Actualizo, ahora tengo audio, no se como y funciona bien, conecto los auriculares y se desconecta el altavoz. pero no puedo ni subir ni bajar el volumen... y no me figura la placa de sonido en configuracion de sonido, pero si me funciona el sonido, es molesto no tener para regularlo.. alguien sabe algo sobre eso?

y lo de poder intercambiar las placas de video no encontre solucion aun. 

Muchas gracias!

---

### Post by franquetooo on 2011-12-28
Cierren, ya volvi a windows 7 de nuevo, lamentable pero no encontre solucion. 

=(

---

### Post by jeros1712 on 2011-12-30
> **franquetooo said:**
> Cierren, ya volvi a windows 7 de nuevo, lamentable pero no encontre solucion. 

=(

Una lastima, habias probado actualizar ubutnu ? para ver si solucionaba lo de subir y bajar el volumen ? aunque no entendi bien si es desde los paneles de ubuntu o desde los botones fisicos de la laptop.

saludos

---

