---
title: "What kind of controller post is this?"
date: 2011-07-17
forum: Hardware
---

### Post by Arpeggiator on 2011-07-17
lspci

  	 	 	 	p { margin-bottom: 0.08in; }  00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)  
 00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)  
 00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)  
 00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)  
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)  
 00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)  
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)  
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)  
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)  
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)  
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)  
 00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)  
 00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)  
 00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)  
 00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)  
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)  
 02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01) 



lshw


   	 	 	 	p { margin-bottom: 0.08in; }  escription: Computer  
     width: 32 bits  
   *-core  
        description: Motherboard  
        physical id: 0  
      *-memory  
           description: System memory  
           physical id: 0  
           size: 2003MiB  
      *-cpu  
           product: Intel(R) Pentium(R) 4 CPU 2.80GHz  
           vendor: Intel Corp.  
           physical id: 1  
           bus info: cpu@0  
           version: 15.4.1  
           serial: 0000-0F41-0000-0000-0000-0000  
           size: 2800MHz  
           width: 64 bits  
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr  
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
         *-pci:0  
              description: PCI bridge  
              product: 82945G/GZ/P/PL PCI Express Root Port  
              vendor: Intel Corporation  
              physical id: 1  
              bus info: pci@0000:00:01.0 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci normal_decode bus_master cap_list  
              configuration: driver=pcieport  
              resources: irq:40 memory:fe900000-fe9fffff  
         *-display:0  
              description: VGA compatible controller  
              product: 82945G/GZ Integrated Graphics Controller  
              vendor: Intel Corporation  
              physical id: 2  
              bus info: pci@0000:00:02.0 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: vga_controller bus_master cap_list rom  
              configuration: driver=i915 latency=0  
              resources: irq:16 memory:feb00000-feb7ffff ioport:e898(size=8) memory:e0000000-efffffff memory:feac0000-feafffff  
         *-display:1 UNCLAIMED  
              description: Display controller  
              product: 82945G/GZ Integrated Graphics Controller  
              vendor: Intel Corporation  
              physical id: 2.1  
              bus info: pci@0000:00:02.1 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master cap_list  
              configuration: latency=0  
              resources: memory:feb80000-febfffff  
         *-pci:1  
              description: PCI bridge  
              product: N10/ICH 7 Family PCI Express Port 1  
              vendor: Intel Corporation  
              physical id: 1c  
              bus info: pci@0000:00:1c.0 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci normal_decode bus_master cap_list  
              configuration: driver=pcieport  
              resources: irq:41 ioport:1000(size=4096) memory:fe800000-fe8fffff ioport:80000000(size=2097152)  
            *-network  
                 description: Ethernet interface  
                 product: NetXtreme BCM5751 Gigabit Ethernet PCI Express  
                 vendor: Broadcom Corporation  
                 physical id: 0  
                 bus info: pci@0000:02:00.0  
                 logical name: eth0  
                 version: 01  
                 serial: 00:14:22:37:25:4a  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: bus_master cap_list ethernet physical  
                 configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=5751-v3.44a ip=192.168.1.111 latency=0 multicast=yes  
                 resources: irq:16 memory:fe8f0000-fe8fffff  
         *-pci:2  
              description: PCI bridge  
              product: N10/ICH 7 Family PCI Express Port 2  
              vendor: Intel Corporation  
              physical id: 1c.1  
              bus info: pci@0000:00:1c.1 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci normal_decode bus_master cap_list  
              configuration: driver=pcieport  
              resources: irq:42 ioport:3000(size=4096) memory:fe700000-fe7fffff ioport:80200000(size=2097152)  
         *-usb:0  
              description: USB Controller  
              product: N10/ICH 7 Family USB UHCI Controller #1  
              vendor: Intel Corporation  
              physical id: 1d  
              bus info: pci@0000:00:1d.0 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: uhci bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:21 ioport:ff80(size=32)  
         *-usb:1  
              description: USB Controller  
              product: N10/ICH 7 Family USB UHCI Controller #2  
              vendor: Intel Corporation  
              physical id: 1d.1  
              bus info: pci@0000:00:1d.1 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: uhci bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:22 ioport:ff60(size=32)  
         *-usb:2  
              description: USB Controller  
              product: N10/ICH 7 Family USB UHCI Controller #3  
              vendor: Intel Corporation  
              physical id: 1d.2  
              bus info: pci@0000:00:1d.2 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: uhci bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:18 ioport:ff40(size=32)  
         *-usb:3  
              description: USB Controller  
              product: N10/ICH 7 Family USB UHCI Controller #4  
              vendor: Intel Corporation  
              physical id: 1d.3  
              bus info: pci@0000:00:1d.3 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: uhci bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:23 ioport:ff20(size=32)  
         *-usb:4  
              description: USB Controller  
              product: N10/ICH 7 Family USB2 EHCI Controller  
              vendor: Intel Corporation  
              physical id: 1d.7  
              bus info: pci@0000:00:1d.7 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: ehci bus_master cap_list  
              configuration: driver=ehci_hcd latency=0  
              resources: irq:21 memory:ffa80800-ffa80bff  
         *-pci:3  
              description: PCI bridge  
              product: 82801 PCI Bridge  
              vendor: Intel Corporation  
              physical id: 1e  
              bus info: pci@0000:00:1e.0 
              version: e1  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci subtractive_decode bus_master cap_list  
         *-multimedia  
              description: Multimedia audio controller  
              product: 82801G (ICH7 Family) AC'97 Audio Controller  
              vendor: Intel Corporation  
              physical id: 1e.2  
              bus info: pci@0000:00:1e.2 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master cap_list  
              configuration: driver=Intel ICH latency=0  
              resources: irq:23 ioport:ec00(size=256) ioport:e8c0(size=64) memory:feabfa00-feabfbff memory:feabf900-feabf9ff  
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
              logical name: scsi0  
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              capabilities: ide bus_master emulated  
              configuration: driver=ata_piix latency=0  
              resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)  
            *-cdrom  
                 description: DVD reader 
                 product: CDRW/DVD GCC4482  
                 vendor: HL-DT-ST  
                 physical id: 0.0.0  
                 bus info: scsi@0:0.0.0  
                 logical name: /dev/cdrom  
                 logical name: /dev/cdrw 
                 logical name: /dev/dvd  
                 logical name: /dev/scd0 
                 logical name: /dev/sr0  
                 version: E107  
                 capabilities: removable audio cd-r cd-rw dvd  
                 configuration: ansiversion=5 status=nodisc  
         *-ide:1  
              description: IDE interface 
              product: N10/ICH7 Family SATA IDE Controller  
              vendor: Intel Corporation  
              physical id: 1f.2  
              bus info: pci@0000:00:1f.2 
              version: 01  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ide bus_master cap_list  
              configuration: driver=ata_piix latency=0  
              resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)  
         *-serial UNCLAIMED  
              description: SMBus  
              product: N10/ICH 7 Family SMBus Controller  
              vendor: Intel Corporation  
              physical id: 1f.3  
              bus info: pci@0000:00:1f.3 
              version: 01  
              width: 32 bits  
              clock: 33MHz  
              configuration: latency=0  
              resources: ioport:e8a0(size=32)  
 

 

 
Forgive me for my ignorance... Still kinda new at this computer thing. I had my computer only for one year.

---

