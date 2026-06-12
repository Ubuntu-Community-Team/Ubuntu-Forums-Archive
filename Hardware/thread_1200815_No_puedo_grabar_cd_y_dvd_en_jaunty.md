---
title: "No puedo grabar cd y dvd en jaunty"
date: 2009-06-30
forum: Hardware
---

### Post by jandry on 2009-06-30
Amigos del foro, he intentado grabar cd o dvd con k3b, brasero, etc y no me reconoce los cd o dvd virgenes. Tengo una grabadora de cd y dvd que lee perfectamente cd y dvd grabados. Intente con grabacion por consola y tampoco pude, tire los siguiente por consola y me da esto (no se porque dice not supported)
jandry@jandry-laptop:~$ wodim dev=help
Supported SCSI transports for this platform:

Transport name:         sg
Transport descr.:       Generic transport independent SCSI
Transp. layer ind.:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport
Transp. layer ind.:     ATAPI:
Target specifier:       bus,target,lun
Target example:         ATAPI:1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport using sg interface
Transp. layer ind.:     ATA:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         RSCSI
Transport descr.:       Remote SCSI
Transp. layer ind.:     REMOTE:
Target specifier:       rscsi@host:bus,target,lun
Target example:         REMOTE:rscsi@host:1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Si alguien tiene una idea le agradezco ya que en google no hay ninguna solucion.
Un abrazo ubuntero
Alejandro

---

### Post by andy_91 on 2009-06-30
probaste con el nero linux ???

---

### Post by guillermolisi on 2009-06-30
Es una unidad SATA ?
Pareceria que no la ve ni cuadrada ...

Que dice lshw ? y los logs ?

---

### Post by jandry on 2009-06-30
Esto devuelve lshw

WARNING: you should run this program as super-user.
jandry-laptop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 883MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU          550  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.6.1
          serial: 0001-0661-0000-0000-0000-0000
          size: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=32 module=via_agp
        *-system UNCLAIMED
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
                configuration: latency=32 mingnt=2
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
        *-ide:0
             description: IDE interface
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_via latency=32
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:90:f5:6d:8e:eb
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
        *-pci:3
             description: PCI bridge
             product: VT8237A Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-multimedia
                description: Audio device
                product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:05:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:4
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 00
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=4 mingnt=1
           *-system
                description: SD Host controller
                product: ENE PCI SmartMedia / xD Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=32 maxlatency=72 mingnt=32 module=sdhci_pci
           *-memory:1
                description: FLASH memory
                product: ENE PCI Secure Digital / MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 00
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32 module=sdhci_pci
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
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:a3:7e:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.5 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:41:26:a5:89:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

espero sirva de ayuda. Gracias

---

### Post by guillermolisi on 2009-06-30
Ale, correlo pero anteponiendo sudo.

Deberias ver algo asi:
```
*-cdrom                                                                     
                description: DVD-RAM writer                                            
                product: DVD-RAM GH22NS30                                              
                vendor: HL-DT-ST                                                       
                physical id: 1                                                         
                bus info: scsi@3:0.0.0                                                 
                logical name: /dev/scd0                                                
                logical name: /dev/sr0                                                 
                version: 1.02                                                          
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram             
                configuration: ansiversion=5 status=ready                              
              *-medium                                                                 
                   physical id: 0                                                      
                   logical name: /dev/scd0
```

---

### Post by jandry on 2009-06-30
Guille, esto me sale, solo me paso desde que actualice a jaunty, en otras grababa bien.

 *-cdrom                                                                                     
                description: DVD-RAM writer                                                            
                product: CDDVDW TS-L632H                                                               
                vendor: TSSTcorp                                                                       
                physical id: 0.0.0                                                                     
                bus info: scsi@2:0.0.0                                                                 
                logical name: /dev/cdrom                                                               
                logical name: /dev/cdrw                                                                
                logical name: /dev/dvd                                                                 
                logical name: /dev/dvdrw                                                               
                logical name: /dev/scd0                                                                
                logical name: /dev/sr0                                                                 
                version: TMC0                                                                          
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                             
                configuration: ansiversion=5 status=nodisc

---

