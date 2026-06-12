---
title: "Xorg.conf en blanco en Lucid Lynx con ATI 2100"
date: 2010-05-04
forum: Hardware
---

### Post by leonardomdq on 2010-05-04
Necesito ayuda con el video en Ubuntu 10.04 Lucid Lynx.
Desde que instale el sistema vengo notando un muy bajo rendimiento y cuelgues que se producen ni bien enciendo la maquina o cuando estoy ejecutando alguna aplicacion.
Hice el test de memoria pensando que podia ser problema de hardware pero salio OK.

Despues de descartar el Hard me fijo el Xorg.conf y me encuentro que el mismo esta vacio (en blanco) :confused: .
Busque en Google el problema pero no encontre algo que funcionara. 
Por favor si me dan una mano les agradeceria.

Ejecute el comando siguiente para crear el xorg.conf y nada...sigue en blanco.
```

sudo touch /etc/X11/xorg.conf
```
lspci |grep VGA
```

leonardo@leonardo-desktop:~$ lspci |grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100
leonardo@leonardo-desktop:~$ 

```lshw

```

leonardo@leonardo-desktop:~$ sudo lshw
    description: Desktop Computer
    product: GA-MA74GM-S2
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=30303234-3144-3241-3430-3635FFFFFFFF
  *-core
       description: Motherboard
       product: GA-MA74GM-S2
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: FB (03/03/2009)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 7750 Dual-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.2.3
          slot: Socket M2
          size: 1350MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
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
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: 9
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 667 MHz (1.5 ns)
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             physical id: 1
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.2.3
          size: 1350MHz
          capacity: 1350MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:e000(size=4096) memory:fde00000-fdffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Radeon 2100
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=radeon latency=32
                resources: irq:27 memory:d0000000-dfffffff(prefetchable) memory:fdff0000-fdffffff ioport:ee00(size=256) memory:fde00000-fdefffff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:d000(size=4096) memory:fdd00000-fddfffff ioport:fda00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:24:1d:2a:40:65
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:26 ioport:de00(size=256) memory:fdaff000-fdafffff(prefetchable) memory:fdae0000-fdaeffff(prefetchable) memory:fda00000-fda0ffff(prefetchable)
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
             configuration: driver=ahci latency=32
             resources: irq:22 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f3ff
           *-disk
                description: ATA Disk
                product: WDC WD5000AAKS-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WMASY5422045
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00037c3b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 5cda01a4-de34-4df0-a786-8065def85a0b
                   size: 460GiB
                   capacity: 460GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-04-29 23:48:11 filesystem=ext4 lastmountpoint=/&#65533;^&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;-&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;u^ &#65533;U/&#65533;d&#65533;&#65533;~!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#806;&#65533;&#65533;&#65533;&#65533;a modified=2010-05-03 20:39:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-03 22:36:29 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   size: 5152MiB
                   capacity: 5152MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 5152MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH22NS50
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TN01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02e000-fe02efff
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
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02d000-fe02dfff
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
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fe02c000-fe02c0ff
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
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02b000-fe02bfff
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
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02a000-fe02afff
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
             configuration: driver=ehci_hcd latency=32
             resources: irq:19 memory:fe029000-fe0290ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=32
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
           *-disk
                description: ATA Disk
                product: Maxtor 2F040L0
                vendor: Maxtor
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sda
                version: VAM5
                serial: F1EDQ5WE
                size: 38GiB (41GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000161c4
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: c62fd5f0-9d57-47e3-be5b-34c0b6c14c7f
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-04-29 23:17:08 filesystem=ext4 label=DATOS lastmountpoint=/media/DATOS&#832;&#65533;&#65533;&#65533;&#65533;&#65533;&#1858;&#65533;&#65533;&#65533;&#65533;&#65533;^&#65533;&#65533;u^ &#65533;U/&#65533;&#65533;^&#65533;&#65533;~!&#65533;&#65533;&#65533;&#1888;&#65533;&#1856;&#65533; modified=2010-04-30 02:43:11 mounted=2010-04-30 02:43:04 state=clean
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
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:fe024000-fe027fff
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
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
             resources: ioport:c000(size=4096) memory:fdc00000-fdcfffff memory:fdb00000-fdbfffff(prefetchable)
           *-network
                description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 6
                bus info: pci@0000:03:06.0
                logical name: wlan0
                version: 01
                serial: 00:25:86:d3:98:3f
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k ip=192.168.1.33 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:20 memory:fdcf0000-fdcfffff
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
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe028000-fe028fff
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
leonardo@leonardo-desktop:~$ 

```lspci

```

leonardo@leonardo-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
leonardo@leonardo-desktop:~$ 

```Saludos
Leonardo

---

### Post by oktubrer on 2010-05-04
Desde hace varias versiones atrás que xorg soporta hotplugging, no es necesario disponer del archivo /etc/X11/xorg.conf para que funcione.

---

### Post by mama21mama on 2010-05-04
Hola,

yo tambien tuve problemas con el xorg y tengo nvidia.
luego del gdm a mi me dejaba de [responder el teclado y mouse]("http://ubuntuforums.org/showthread.php?t=1471314").
pero eso es historia mia.

Te paso [algunos xorg]("http://mamalibre.eshost.com.ar/?q=taxonomy/term/29")

luego en sistema/Administración/controladores de hardware te instalas el driver.

Saludos

---

### Post by leonardomdq on 2010-05-05
> **mama21mama said:**
> Hola,

yo tambien tuve problemas con el xorg y tengo nvidia.
luego del gdm a mi me dejaba de [responder el teclado y mouse]("http://ubuntuforums.org/showthread.php?t=1471314").
pero eso es historia mia.

Te paso [algunos xorg]("http://mamalibre.eshost.com.ar/?q=taxonomy/term/29")

luego en sistema/Administración/controladores de hardware te instalas el driver.

Saludos
Gracias por la respuesta.
Use los dos xorg.conf que me pasaste pero no me sale ningun driver para instalar desde **sistema/Administración/controladores de hardware **y si quiero arrancar si el driver no me arranca, se queda en modo ahorro de energia el LCD.

Alguna idea?

Muchas gracias.

---

### Post by guillermolisi on 2010-05-06
> **leonardomdq said:**
> Gracias por la respuesta.
Use los dos xorg.conf que me pasaste pero no me sale ningun driver para instalar desde **sistema/Administración/controladores de hardware **y si quiero arrancar si el driver no me arranca, se queda en modo ahorro de energia el LCD.

Alguna idea?

Muchas gracias.
Si el monitor se queda off line me suena a que hay problemas con las frecuencias de barrido vertical/horizontal. Los monitores se deconectan de la señal de video cuando las frecuencias de barrido estan fuera del rango de trabajo aceptado, protegiendo asi su electronica (sino se quemarian).

Esos valores se obtienen del manual del monitor y se defienen dentro del /etc/X11/xorg.conf para ajustarlas especificamente cuando el hot plugging falla.

---

