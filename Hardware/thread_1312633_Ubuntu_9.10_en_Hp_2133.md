---
title: "Ubuntu 9.10 en Hp 2133"
date: 2009-11-03
forum: Hardware
---

### Post by lean-mini on 2009-11-03
He actualizado mi Ubuntu 9.04 Jaunty a 9.10 Kármic Koala, la actualización corrió sola, y eso que en un momento se me desconectó el wifi, se guardaron los datos y al reconectar todo volvió a correr bien.
Si bien al principio el touchpad estaba como un poco trabado, al reiniciar se solucionó el problemita. SI bien en el inicio se escuchaban el sonido de los tambores, luego no se reproducía sonido. Bastó con actualizar con el gestor y reiniciar para que esto se solucionara (o por lo menos así me pasó, no se si esta relacionado). Todo está funcionando bien. TOdavía está un poco lento el inicio, inicia como ext3, veremos si esto se modifica en el futuro. 
EN términos generales estoy muy contento de que todo funcione, muestra una vez más el grado de avance y desarrollo de ubuntu.:D

:KS Les paso info que una vez me pidieron en [http://ubuntuforums.org/showthread.php?t=1139997](http://ubuntuforums.org/showthread.php?t=1139997)

 lspci

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
07:03.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
  
:KS lsusb
Bus 001 Device 004: ID 0951:160b Kingston Technology 
Bus 001 Device 002: ID 04f2:b107 Chicony Electronics Co., Ltd CNF7070 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

:KS lshw
PCI (sysfs)  
lean-hp2133               
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 887MiB
     *-cpu
          product: VIA C7-M Processor 1200MHz
          vendor: CentaurHauls
          physical id: 2
          bus info: cpu@0
          size: 1200MHz
          capacity: 1200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx up pni est tm2 xtpr rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en cpufreq
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: memory:fbf00000-fcffffff memory:d0000000-d7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:d0000000-d7ffffff(prefetchable) memory:fc000000-fcffffff memory:fbff0000-fbffffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:d000(size=4096) memory:fd000000-fdffffff ioport:de000000(size=33554432)
           *-network
                description: Wireless interface
                product: BCM4312 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 02
                serial: 00:21:00:35:16:a7
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:24 memory:fdffc000-fdffffff
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:31 ioport:e000(size=4096) memory:fe000000-fe9fffff ioport:f8000000(size=50331648)
        *-ide
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_via latency=64
             resources: irq:21 ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=16) ioport:c000(size=256)
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:20 ioport:b800(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:b880(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:23 ioport:bc00(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:21 memory:fbeffc00-fbeffcff
        *-isa
             description: ISA bridge
             product: VT8237S PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa cap_list
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:fea00000-feafffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5788 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:07:03.0
                logical name: eth0
                version: 03
                serial: 00:1f:29:98:c2:e2
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5788-v3.27 latency=64 mingnt=64 multicast=yes
                resources: irq:16 memory:feaf0000-feafffff
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=128
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:febfc000-febfffff
  *-scsi
       physical id: 1
       bus info: scsi@3
       logical name: scsi3
       capabilities: scsi-host
       configuration: driver=usb-storage

Abrazo a todos
LEan

---

