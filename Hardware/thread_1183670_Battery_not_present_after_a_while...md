---
title: "Battery not present after a while.."
date: 2009-06-10
forum: Hardware
---

### Post by flaerpen on 2009-06-10
When I've just started my laptop the battery monitor finds my battery and works great when I unplug and plug in the cable. But after a while it states that the battery is not present. I think it is charging (the battery does'nt die anyway)

Some info:
```
victor@staropramen:~$ cat /proc/acpi/battery/BAT1/info
present:                 yes                          
design capacity:         4800 mAh                     
last full capacity:      3968 mAh                     
battery technology:      rechargeable                 
design voltage:          10800 mV                     
design capacity warning: 0 mAh                        
design capacity low:     0 mAh                        
capacity granularity 1:  1 mAh                        
capacity granularity 2:  1 mAh                        
model number:            MS-1221                      

serial number:           

battery type:            LION

OEM info:                MSI Corp.

victor@staropramen:~$ cat /proc/acpi/battery/BAT1/state 
present:                 yes                            
capacity state:          ok                             
charging state:          charged                        
present rate:            0 mA                           
remaining capacity:      3968 mAh                       
present voltage:         12521 mV
```

When I unplug the cable:
```
victor@staropramen:~$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            2037 mA
remaining capacity:      3963 mAh
present voltage:         12214 mV
```

The computer I have is a LG E500 S.APNNV. sudo lshw:
```
victor@staropramen:~$ sudo lshw                                                                                                                
[sudo] password for victor:                                                                                                                    
staropramen                                                                                                                                    
    description: Notebook                                                                                                                      
    product: E500-S.APNNV                                                                                                                      
    vendor: LG Electronics                                                                                                                     
    version: LG-1636                                                                                                                           
    serial: 709MSKV014053                                                                                                                      
    width: 32 bits                                                                                                                             
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp                                                                                               
    configuration: chassis=notebook cpus=2 uuid=E83360A4-20C6-DD11-8000-504350524F44                                                           
  *-core                                                                                                                                       
       description: Motherboard                                                                                                                
       product: MS-16361                                                                                                                       
       vendor: MICRO-STAR INT'L CO.,LTD                                                                                                        
       physical id: 0                                                                                                                          
       version: Ver 1.000                                                                                                                      
       serial: BSS-0123456789                                                                                                                  
       slot: To Be Filled By O.E.M.                                                                                                            
     *-firmware                                                                                                                                
          description: BIOS                                                                                                                    
          vendor: American Megatrends Inc.                                                                                                     
          physical id: 0                                                                                                                       
          version: A1636IL1 V1.1G (02/01/2008)                                                                                                 
          size: 64KiB                                                                                                                          
          capacity: 448KiB                                                                                                                     
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int17printer acpi usb agp smartbattery biosbootspecification                                                                                                         
     *-cpu:0                                                                                                                                   
          description: CPU                                                                                                                     
          product: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz                                                                             
          vendor: Intel Corp.                                                                                                                  
          physical id: 4                                                                                                                       
          bus info: cpu@0                                                                                                                      
          version: 6.15.13                                                                                                                     
          serial: 0000-06FD-0000-0000-0000-0000                                                                                                
          slot: CPU 1                                                                                                                          
          size: 1GHz                                                                                                                           
          capacity: 1500MHz                                                                                                                    
          width: 64 bits                                                                                                                       
          clock: 167MHz                                                                                                                        
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq     
          configuration: id=1                                                                                                                  
        *-cache:0                                                                                                                              
             description: L1 cache                                                                                                             
             physical id: 5                                                                                                                    
             slot: L1-Cache                                                                                                                    
             size: 64KiB                                                                                                                       
             capacity: 64KiB                                                                                                                   
             capabilities: internal write-back data                                                                                            
        *-cache:1                                                                                                                              
             description: L2 cache                                                                                                             
             physical id: 6                                                                                                                    
             slot: L2-Cache                                                                                                                    
             size: 2MiB                                                                                                                        
             capacity: 2MiB                                                                                                                    
             capabilities: internal write-back unified                                                                                         
        *-cache:2 DISABLED                                                                                                                     
             description: L3 cache                                                                                                             
             physical id: 7                                                                                                                    
             slot: L3-Cache                                                                                                                    
             capabilities: internal                                                                                                            
        *-logicalcpu:0                                                                                                                         
             description: Logical CPU                                                                                                          
             physical id: 1.1                                                                                                                  
             width: 64 bits                                                                                                                    
             capabilities: logical                                                                                                             
        *-logicalcpu:1                                                                                                                         
             description: Logical CPU                                                                                                          
             physical id: 1.2                                                                                                                  
             width: 64 bits                                                                                                                    
             capabilities: logical                                                                                                             
     *-memory                                                                                                                                  
          description: System Memory                                                                                                           
          physical id: 10                                                                                                                      
          slot: System board or motherboard                                                                                                    
          size: 2GiB                                                                                                                           
        *-bank:0                                                                                                                               
             description: SODIMM Synchronous                                                                                                   
             product: PartNum0                                                                                                                 
             vendor: Manufacturer0                                                                                                             
             physical id: 0                                                                                                                    
             serial: SerNum0                                                                                                                   
             slot: DIMM0                                                                                                                       
             size: 1GiB                                                                                                                        
             width: 64 bits                                                                                                                    
        *-bank:1                                                                                                                               
             description: SODIMM [empty]                                                                                                       
             product: PartNum1                                                                                                                 
             vendor: Manufacturer1                                                                                                             
             physical id: 1                                                                                                                    
             serial: SerNum1                                                                                                                   
             slot: DIMM1                                                                                                                       
        *-bank:2                                                                                                                               
             description: SODIMM Synchronous                                                                                                   
             product: PartNum2                                                                                                                 
             vendor: Manufacturer2                                                                                                             
             physical id: 2                                                                                                                    
             serial: SerNum2                                                                                                                   
             slot: DIMM2                                                                                                                       
             size: 1GiB                                                                                                                        
             width: 64 bits                                                                                                                    
     *-cpu:1                                                                                                                                   
          physical id: 1                                                                                                                       
          bus info: cpu@1                                                                                                                      
          version: 6.15.13                                                                                                                     
          serial: 0000-06FD-0000-0000-0000-0000                                                                                                
          size: 1GHz                                                                                                                           
          capacity: 1GHz                                                                                                                       
          capabilities: ht cpufreq                                                                                                             
          configuration: id=1                                                                                                                  
        *-logicalcpu:0                                                                                                                         
             description: Logical CPU                                                                                                          
             physical id: 1.1                                                                                                                  
             capabilities: logical                                                                                                             
        *-logicalcpu:1                                                                                                                         
             description: Logical CPU                                                                                                          
             physical id: 1.2                                                                                                                  
             capabilities: logical                                                                                                             
     *-pci                                                                                                                                     
          description: Host bridge                                                                                                             
          product: Mobile PM965/GM965/GL960 Memory Controller Hub                                                                              
          vendor: Intel Corporation                                                                                                            
          physical id: 100                                                                                                                     
          bus info: pci@0000:00:00.0                                                                                                           
          version: 03                                                                                                                          
          width: 32 bits                                                                                                                       
          clock: 33MHz                                                                                                                         
        *-pci:0                                                                                                                                
             description: PCI bridge                                                                                                           
             product: Mobile PM965/GM965/GL960 PCI Express Root Port                                                                           
             vendor: Intel Corporation                                                                                                         
             physical id: 1                                                                                                                    
             bus info: pci@0000:00:01.0                                                                                                        
             version: 03                                                                                                                       
             width: 32 bits                                                                                                                    
             clock: 33MHz                                                                                                                      
             capabilities: pci pm msi pciexpress bus_master cap_list                                                                           
             configuration: driver=pcieport-driver                                                                                             
           *-display                                                                                                                           
                description: VGA compatible controller                                                                                         
                product: GeForce 8400M G                                                                                                       
                vendor: nVidia Corporation                                                                                                     
                physical id: 0                                                                                                                 
                bus info: pci@0000:01:00.0                                                                                                     
                version: a1                                                                                                                    
                width: 64 bits                                                                                                                 
                clock: 33MHz                                                                                                                   
                capabilities: pm msi pciexpress bus_master cap_list                                                                            
                configuration: driver=nvidia latency=0 module=nvidia                                                                           
        *-usb:0                                                                                                                                
             description: USB Controller                                                                                                       
             product: 82801H (ICH8 Family) USB UHCI Controller #4                                                                              
             vendor: Intel Corporation                                                                                                         
             physical id: 1a                                                                                                                   
             bus info: pci@0000:00:1a.0                                                                                                        
             version: 03                                                                                                                       
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
             version: 03                                                                                                                       
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
             version: 03                                                                                                                       
             width: 32 bits                                                                                                                    
             clock: 33MHz                                                                                                                      
             capabilities: pm debug bus_master cap_list                                                                                        
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd                                                                          
        *-multimedia                                                                                                                           
             description: Audio device                                                                                                         
             product: 82801H (ICH8 Family) HD Audio Controller                                                                                 
             vendor: Intel Corporation                                                                                                         
             physical id: 1b                                                                                                                   
             bus info: pci@0000:00:1b.0                                                                                                        
             version: 03                                                                                                                       
             width: 64 bits                                                                                                                    
             clock: 33MHz                                                                                                                      
             capabilities: pm msi pciexpress bus_master cap_list                                                                               
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel                                                                    
        *-pci:1                                                                                                                                
             description: PCI bridge                                                                                                           
             product: 82801H (ICH8 Family) PCI Express Port 1                                                                                  
             vendor: Intel Corporation                                                                                                         
             physical id: 1c                                                                                                                   
             bus info: pci@0000:00:1c.0                                                                                                        
             version: 03                                                                                                                       
             width: 32 bits                                                                                                                    
             clock: 33MHz                                                                                                                      
             capabilities: pci pciexpress msi pm bus_master cap_list                                                                           
             configuration: driver=pcieport-driver                                                                                             
        *-pci:2                                                                                                                                
             description: PCI bridge                                                                                                           
             product: 82801H (ICH8 Family) PCI Express Port 4                                                                                  
             vendor: Intel Corporation                                                                                                         
             physical id: 1c.3                                                                                                                 
             bus info: pci@0000:00:1c.3                                                                                                        
             version: 03                                                                                                                       
             width: 32 bits                                                                                                                    
             clock: 33MHz                                                                                                                      
             capabilities: pci pciexpress msi pm bus_master cap_list                                                                           
             configuration: driver=pcieport-driver                                                                                             
           *-network                                                                                                                           
                description: Wireless interface                                                                                                
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection                                                               
                vendor: Intel Corporation                                                                                                      
                physical id: 0                                                                                                                 
                bus info: pci@0000:03:00.0                                                                                                     
                logical name: wmaster0                                                                                                         
                version: 61                                                                                                                    
                serial: 00:13:e8:9a:f4:ff                                                                                                      
                width: 64 bits                                                                                                                 
                clock: 33MHz                                                                                                                   
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless                                         
                configuration: broadcast=yes driver=iwlagn ip=192.168.0.6 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn       
        *-pci:3                                                                                                                                
             description: PCI bridge                                                                                                           
             product: 82801H (ICH8 Family) PCI Express Port 5                                                                                  
             vendor: Intel Corporation                                                                                                         
             physical id: 1c.4                                                                                                                 
             bus info: pci@0000:00:1c.4                                                                                                        
             version: 03                                                                                                                       
             width: 32 bits                                                                                                                    
             clock: 33MHz                                                                                                                      
             capabilities: pci pciexpress msi pm bus_master cap_list                                                                           
             configuration: driver=pcieport-driver                                                                                             
           *-network                                                                                                                           
                description: Ethernet interface                                                                                                
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller                                                                
                vendor: Realtek Semiconductor Co., Ltd.                                                                                        
                physical id: 0                                                                                                                 
                bus info: pci@0000:04:00.0                                                                                                     
                logical name: eth0                                                                                                             
                version: 01                                                                                                                    
                serial: 00:19:db:ed:4a:c3                                                                                                      
                size: 10MB/s                                                                                                                   
                capacity: 100MB/s                                                                                                              
                width: 64 bits                                                                                                                 
                clock: 33MHz                                                                                                                   
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation   
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s                                                                                                          
        *-usb:3                                                                                                                                
             description: USB Controller                                                                                                       
             product: 82801H (ICH8 Family) USB UHCI Controller #1                                                                              
             vendor: Intel Corporation                                                                                                         
             physical id: 1d                                                                                                                   
             bus info: pci@0000:00:1d.0                                                                                                        
             version: 03                                                                                                                       
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
             version: 03                                                                                                                       
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
             version: 03                                                                                                                       
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
             version: 03                                                                                                                       
             width: 32 bits                                                                                                                    
             clock: 33MHz                                                                                                                      
             capabilities: pm debug bus_master cap_list                                                                                        
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd                                                                          
        *-pci:4                                                                                                                                
             description: PCI bridge                                                                                                           
             product: 82801 Mobile PCI Bridge                                                                                                  
             vendor: Intel Corporation                                                                                                         
             physical id: 1e                                                                                                                   
             bus info: pci@0000:00:1e.0                                                                                                        
             version: f3                                                                                                                       
             width: 32 bits                                                                                                                    
             clock: 33MHz                                                                                                                      
             capabilities: pci bus_master cap_list                                                                                             
           *-pcmcia                                                                                                                            
                description: CardBus bridge                                                                                                    
                product: OZ711SP1 Memory CardBus Controller                                                                                    
                vendor: O2 Micro, Inc.                                                                                                         
                physical id: 4                                                                                                                 
                bus info: pci@0000:05:04.0                                                                                                     
                version: 01                                                                                                                    
                width: 32 bits                                                                                                                 
                clock: 33MHz                                                                                                                   
                capabilities: pcmcia bus_master cap_list                                                                                       
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=195 module=yenta_socket                                    
           *-system                                                                                                                            
                description: SD Host controller                                                                                                
                product: Integrated MMC/SD Controller                                                                                          
                vendor: O2 Micro, Inc.                                                                                                         
                physical id: 4.2                                                                                                               
                bus info: pci@0000:05:04.2                                                                                                     
                version: 02                                                                                                                    
                width: 32 bits                                                                                                                 
                clock: 33MHz                                                                                                                   
                capabilities: pm bus_master cap_list                                                                                           
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci                                                                    
           *-storage UNCLAIMED                                                                                                                 
                description: Mass storage controller                                                                                           
                product: Integrated MS/xD Controller                                                                                           
                vendor: O2 Micro, Inc.                                                                                                         
                physical id: 4.3                                                                                                               
                bus info: pci@0000:05:04.3                                                                                                     
                version: 01                                                                                                                    
                width: 32 bits                                                                                                                 
                clock: 33MHz                                                                                                                   
                capabilities: storage pm cap_list                                                                                              
                configuration: latency=64                                                                                                      
           *-firewire                                                                                                                          
                description: FireWire (IEEE 1394)                                                                                              
                product: Firewire (IEEE 1394)                                                                                                  
                vendor: O2 Micro, Inc.                                                                                                         
                physical id: 4.4                                                                                                               
                bus info: pci@0000:05:04.4                                                                                                     
                version: 02                                                                                                                    
                width: 32 bits                                                                                                                 
                clock: 33MHz                                                                                                                   
                capabilities: pm bus_master cap_list                                                                                           
                configuration: driver=ohci1394 latency=64 module=ohci1394                                                                      
        *-isa                                                                                                                                  
             description: ISA bridge                                                                                                           
             product: 82801HEM (ICH8M) LPC Interface Controller                                                                                
             vendor: Intel Corporation                                                                                                         
             physical id: 1f                                                                                                                   
             bus info: pci@0000:00:1f.0                                                                                                        
             version: 03                                                                                                                       
             width: 32 bits                                                                                                                    
             clock: 33MHz                                                                                                                      
             capabilities: isa bus_master cap_list                                                                                             
             configuration: latency=0                                                                                                          
        *-ide                                                                                                                                  
             description: IDE interface                                                                                                        
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller                                                                         
             vendor: Intel Corporation                                                                                                         
             physical id: 1f.2                                                                                                                 
             bus info: pci@0000:00:1f.2                                                                                                        
             logical name: scsi0                                                                                                               
             logical name: scsi1                                                                                                               
             version: 03                                                                                                                       
             width: 32 bits                                                                                                                    
             clock: 66MHz                                                                                                                      
             capabilities: ide pm bus_master cap_list emulated                                                                                 
             configuration: driver=ata_piix latency=0                                                                                          
           *-disk                                                                                                                              
                description: ATA Disk                                                                                                          
                product: ST9160821AS                                                                                                           
                vendor: Seagate                                                                                                                
                physical id: 0.0.0                                                                                                             
                bus info: scsi@0:0.0.0                                                                                                         
                logical name: /dev/sda                                                                                                         
                version: 3.AL                                                                                                                  
                serial: 5MA56AEY                                                                                                               
                size: 149GiB (160GB)                                                                                                           
                capabilities: partitioned partitioned:dos                                                                                      
                configuration: ansiversion=5 signature=000c2481                                                                                
              *-volume:0                                                                                                                       
                   description: Windows NTFS volume                                                                                            
                   physical id: 1                                                                                                              
                   bus info: scsi@0:0.0.0,1                                                                                                    
                   logical name: /dev/sda1                                                                                                     
                   version: 3.1                                                                                                                
                   serial: 0efdb872-8e45-bb47-b1d0-8fd121fd520c                                                                                
                   size: 22GiB                                                                                                                 
                   capacity: 22GiB                                                                                                             
                   capabilities: primary bootable ntfs initialized                                                                             
                   configuration: clustersize=4096 created=2009-01-08 00:16:54 filesystem=ntfs state=clean                                     
              *-volume:1                                                                                                                       
                   description: Extended partition                                                                                             
                   physical id: 2                                                                                                              
                   bus info: scsi@0:0.0.0,2                                                                                                    
                   logical name: /dev/sda2                                                                                                     
                   size: 126GiB                                                                                                                
                   capacity: 126GiB                                                                                                            
                   capabilities: primary extended partitioned partitioned:extended                                                             
                 *-logicalvolume:0                                                                                                             
                      description: Linux filesystem partition                                                                                  
                      physical id: 5                                                                                                           
                      logical name: /dev/sda5                                                                                                  
                      capacity: 88GiB                                                                                                          
                 *-logicalvolume:1                                                                                                             
                      description: Linux filesystem partition                                                                                  
                      physical id: 6                                                                                                           
                      logical name: /dev/sda6                                                                                                  
                      logical name: /home                                                                                                      
                      capacity: 18GiB                                                                                                          
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted                          
                 *-logicalvolume:2                                                                                                             
                      description: Linux filesystem partition                                                                                  
                      physical id: 7                                                                                                           
                      logical name: /dev/sda7                                                                                                  
                      logical name: /                                                                                                          
                      capacity: 18GiB                                                                                                          
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted        
                 *-logicalvolume:3                                                                                                             
                      description: Linux swap / Solaris partition                                                                              
                      physical id: 8                                                                                                           
                      logical name: /dev/sda8                                                                                                  
                      capacity: 1247MiB                                                                                                        
                      capabilities: nofs                                                                                                       
           *-cdrom                                                                                                                             
                description: DVD-RAM writer                                                                                                    
                product: DVDRAM GSA-T20N                                                                                                       
                vendor: HL-DT-ST                                                                                                               
                physical id: 0.1.0                                                                                                             
                bus info: scsi@1:0.1.0                                                                                                         
                logical name: /dev/cdrom                                                                                                       
                logical name: /dev/cdrw                                                                                                        
                logical name: /dev/dvd                                                                                                         
                logical name: /dev/dvdrw                                                                                                       
                logical name: /dev/scd0                                                                                                        
                logical name: /dev/sr0                                                                                                         
                version: WA03                                                                                                                  
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                                                                     
                configuration: ansiversion=5 status=nodisc                                                                                     
     *-scsi                                                                                                                                    
          physical id: 2                                                                                                                       
          bus info: usb@2:4                                                                                                                    
          logical name: scsi2                                                                                                                  
          capabilities: emulated scsi-host                                                                                                     
          configuration: driver=usb-storage                                                                                                    
        *-disk                                                                                                                                 
             description: SCSI Disk                                                                                                            
             physical id: 0.0.0                                                                                                                
             bus info: scsi@2:0.0.0                                                                                                            
             logical name: /dev/sdb
             size: 279GiB (300GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=31902177
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/disk
                version: 3.1
                serial: 9c72c127-815c-f247-81b7-571b7cc52d82
                size: 279GiB
                capacity: 279GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2006-04-14 02:13:50 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:68:27:c3:9e:82
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I don't know what to do. Please help?

---

### Post by flaerpen on 2009-06-12
I found some more info about this problem. When I start the computer it says the batter level is 99%. After a minuter (or so) it says 100% and after that "Battery: 0% (fully charged) AC Adapter: Plugged in". If I unplug the adapter it recognize it and change power profile. But if I plug it in again it doesn't recognize it! Nothing happens. It still say "Battery: 0% (fully charged) AC Adapter: Not plugged in" as it does when I unplugged it.

Maybe this could help anyone helping me?

---

### Post by flaerpen on 2009-06-20
*Bump*

---

### Post by krls_ on 2009-12-01
I have exactly the same problem (with the same laptop: LG E500) since I upgraded to Kubuntu 9.10 (I remember it worked better with the latest versions). Did you find any solution?
Thank you!

---

