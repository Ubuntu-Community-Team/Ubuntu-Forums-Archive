---
title: "CD-ROM idoes not work on Acer AX1700"
date: 2010-03-02
forum: Hardware
---

### Post by brent_weaver on 2010-03-02
Hello there. My cdrom drive either does not work, or if it does it is painfully slow. Here is my hw:

root@kebin:~# lshw                                                                         
kebin                                                                                      
    description: Desktop Computer                                                          
    product: Aspire X1700                                                                  
    vendor: Acer                                                                           
    serial: PTSBF0X019912022083000                                                         
    width: 64 bits                                                                         
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32                                 
    configuration: administrator_password=disabled boot=normal chassis=desktop frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=BC9A6780-C64D-11DD-B955-002197C767EA                             
  *-core                                                                                                            
       description: Motherboard                                                                                     
       product: Aspire X1700                                                                                        
       vendor: Acer                                                                                                 
       physical id: 0                                                                                               
       slot: To Be Filled By O.E.M.                                                                                 
     *-firmware                                                                                                     
          description: BIOS                                                                                         
          vendor: American Megatrends Inc.                                                                          
          physical id: 0                                                                                            
          version: R01-B4 (02/26/2009)                                                                              
          size: 128KiB                                                                                              
          capacity: 960KiB                                                                                          
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification                                                                                           
     *-cpu                                                                                                          
          description: CPU                                                                                          
          product: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz                                                  
          vendor: Intel Corp.                                                                                       
          physical id: 4                                                                                            
          bus info: cpu@0                                                                                           
          version: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz                                                  
          serial: To Be Filled By O.E.M.                                                                            
          slot: CPU 1                                                                                               
          size: 1203MHz                                                                                             
          capacity: 1203MHz                                                                                         
          width: 64 bits                                                                                            
          clock: 200MHz                                                                                             
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq                                                       
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
             size: 1MiB                                                                                             
             capacity: 1MiB                                                                                         
             capabilities: internal write-back unified                                                              
     *-memory                                                                                                       
          description: System Memory                                                                                
          physical id: 19                                                                                           
          slot: System board or motherboard                                                                         
          size: 4GiB                                                                                                
        *-bank:0                                                                                                    
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)                                                    
             product: NT2GT64U8HD0BY-AD                                                                             
             vendor: Nanya                                                                                          
             physical id: 0                                                                                         
             serial: 2110D02C                                                                                       
             slot: DIMM0                                                                                            
             size: 2GiB                                                                                             
             width: 64 bits                                                                                         
             clock: 800MHz (1.2ns)                                                                                  
        *-bank:1                                                                                                    
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)                                                    
             product: NT2GT64U8HD0BY-AD                                                                             
             vendor: Nanya                                                                                          
             physical id: 1                                                                                         
             serial: 131CD78C                                                                                       
             slot: DIMM1                                                                                            
             size: 2GiB                                                                                             
             width: 64 bits                                                                                         
             clock: 800MHz (1.2ns)                                                                                  
     *-pci                                                                                                          
          description: Host bridge                                                                                  
          product: MCP73 Host Bridge                                                                                
          vendor: nVidia Corporation                                                                                
          physical id: 100                                                                                          
          bus info: pci@0000:00:00.0                                                                                
          version: a2                                                                                               
          width: 32 bits                                                                                            
          clock: 66MHz                                                                                              
        *-memory:0 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: nForce 630i memory controller                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 0.1                                                                                       
             bus info: pci@0000:00:00.1                                                                             
             version: a2                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             capabilities: bus_master                                                                               
             configuration: latency=0                                                                               
        *-memory:1 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: nForce 630i memory controller                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 1                                                                                         
             bus info: pci@0000:00:01.0                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-memory:2 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: nForce 630i memory controller                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 1.1                                                                                       
             bus info: pci@0000:00:01.1                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-memory:3 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: nForce 630i memory controller                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 1.2                                                                                       
             bus info: pci@0000:00:01.2                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-memory:4 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: nForce 630i memory controller                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 1.3                                                                                       
             bus info: pci@0000:00:01.3                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-memory:5 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: nForce 630i memory controller                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 1.4                                                                                       
             bus info: pci@0000:00:01.4                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-memory:6 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: nForce 630i memory controller                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 1.5                                                                                       
             bus info: pci@0000:00:01.5                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-memory:7 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: nForce 630i memory controller                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 1.6                                                                                       
             bus info: pci@0000:00:01.6                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-memory:8 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: nForce 630i memory controller                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 2                                                                                         
             bus info: pci@0000:00:02.0                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-isa                                                                                                       
             description: ISA bridge                                                                                
             product: MCP73 LPC Bridge                                                                              
             vendor: nVidia Corporation                                                                             
             physical id: 3                                                                                         
             bus info: pci@0000:00:03.0                                                                             
             version: a2                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz                                                                                           
             capabilities: isa bus_master                                                                           
             configuration: latency=0                                                                               
             resources: ioport:4f00(size=256)                                                                       
        *-serial                                                                                                    
             description: SMBus                                                                                     
             product: MCP73 SMBus                                                                                   
             vendor: nVidia Corporation                                                                             
             physical id: 3.1                                                                                       
             bus info: pci@0000:00:03.1                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz                                                                                           
             capabilities: pm cap_list                                                                              
             configuration: driver=nForce2_smbus latency=0                                                          
             resources: irq:11 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)                       
        *-memory:9 UNCLAIMED                                                                                        
             description: RAM memory                                                                                
             product: MCP73 Memory Controller                                                                       
             vendor: nVidia Corporation                                                                             
             physical id: 3.2                                                                                       
             bus info: pci@0000:00:03.2                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-memory:10 UNCLAIMED                                                                                       
             description: RAM memory                                                                                
             product: MCP73 Memory Controller                                                                       
             vendor: nVidia Corporation                                                                             
             physical id: 3.4                                                                                       
             bus info: pci@0000:00:03.4                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz (15.2ns)                                                                                  
             configuration: latency=0                                                                               
        *-usb:0                                                                                                     
             description: USB Controller                                                                            
             product: GeForce 7100/nForce 630i USB                                                                  
             vendor: nVidia Corporation                                                                             
             physical id: 4                                                                                         
             bus info: pci@0000:00:04.0                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz                                                                                           
             capabilities: pm bus_master cap_list                                                                   
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3                                         
             resources: irq:21 memory:f9fff000-f9ffffff                                                             
        *-usb:1                                                                                                     
             description: USB Controller                                                                            
             product: MCP73 [nForce 630i] USB 2.0 Controller (EHCI)                                                 
             vendor: nVidia Corporation                                                                             
             physical id: 4.1                                                                                       
             bus info: pci@0000:00:04.1                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz                                                                                           
             capabilities: debug pm bus_master cap_list                                                             
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3                                         
             resources: irq:22 memory:f9ffec00-f9ffecff                                                             
        *-ide                                                                                                       
             description: IDE interface                                                                             
             product: MCP73 IDE                                                                                     
             vendor: nVidia Corporation                                                                             
             physical id: 8                                                                                         
             bus info: pci@0000:00:08.0                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz                                                                                           
             capabilities: ide pm bus_master cap_list                                                               
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3                                         
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)      
        *-multimedia                                                                                                
             description: Audio device                                                                              
             product: MCP73 High Definition Audio                                                                   
             vendor: nVidia Corporation                                                                             
             physical id: 9                                                                                         
             bus info: pci@0000:00:09.0                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz                                                                                           
             capabilities: pm msi bus_master cap_list                                                               
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2                                        
             resources: irq:23 memory:f9ff8000-f9ffbfff                                                             
        *-pci:0                                                                                                     
             description: PCI bridge                                                                                
             product: MCP73 PCI Express bridge                                                                      
             vendor: nVidia Corporation                                                                             
             physical id: a                                                                                         
             bus info: pci@0000:00:0a.0                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz                                                                                           
             capabilities: pci bus_master cap_list                                                                  
        *-pci:1                                                                                                     
             description: PCI bridge                                                                                
             product: MCP73 PCI Express bridge                                                                      
             vendor: nVidia Corporation                                                                             
             physical id: b                                                                                         
             bus info: pci@0000:00:0b.0                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 33MHz                                                                                           
             capabilities: pci pm msi pciexpress bus_master cap_list                                                
             configuration: driver=pcieport-driver                                                                  
             resources: irq:24 ioport:d000(size=4096) memory:fa000000-fe9fffff ioport:d0000000(size=268435456)      
           *-display                                                                                                
                description: VGA compatible controller                                                              
                product: G98 [GeForce G100]                                                                         
                vendor: nVidia Corporation                                                                          
                physical id: 0                                                                                      
                bus info: pci@0000:02:00.0                                                                          
                version: a1                                                                                         
                width: 64 bits                                                                                      
                clock: 33MHz                                                                                        
                capabilities: pm msi pciexpress bus_master cap_list rom                                             
                configuration: driver=nvidia latency=0                                                              
                resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:dc00(size=128) memory:fe9e0000-fe9fffff(prefetchable)                                                 
        *-pci:2                                                                                                     
             description: PCI bridge                                                                                
             product: MCP73 PCI Express bridge                                                                      
             vendor: nVidia Corporation                                                                             
             physical id: c                                                                                         
             bus info: pci@0000:00:0c.0                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 33MHz                                                                                           
             capabilities: pci pm msi pciexpress bus_master cap_list                                                
             configuration: driver=pcieport-driver                                                                  
             resources: irq:25 memory:fea00000-feafffff                                                             
           *-communication UNCLAIMED                                                                                
                description: Communication controller                                                               
                product: Agere Systems                                                                              
                vendor: Agere Systems                                                                               
                physical id: 0                                                                                      
                bus info: pci@0000:03:00.0                                                                          
                version: 01                                                                                         
                width: 64 bits                                                                                      
                clock: 33MHz                                                                                        
                capabilities: pm msi pciexpress bus_master cap_list                                                 
                configuration: latency=0                                                                            
                resources: memory:feaff000-feafffff                                                                 
        *-pci:3                                                                                                     
             description: PCI bridge                                                                                
             product: MCP73 PCI Express bridge                                                                      
             vendor: nVidia Corporation                                                                             
             physical id: d                                                                                         
             bus info: pci@0000:00:0d.0                                                                             
             version: a1                                                                                            
             width: 32 bits                                                                                         
             clock: 33MHz                                                                                           
             capabilities: pci pm msi pciexpress bus_master cap_list                                                
             configuration: driver=pcieport-driver                                                                  
             resources: irq:26 ioport:e000(size=4096) memory:feb00000-febfffff                                      
           *-firewire                                                                                               
                description: FireWire (IEEE 1394)                                                                   
                product: VIA Technologies, Inc.                                                                     
                vendor: VIA Technologies, Inc.                                                                      
                physical id: 0                                                                                      
                bus info: pci@0000:04:00.0                                                                          
                version: 00                                                                                         
                width: 64 bits                                                                                      
                clock: 33MHz                                                                                        
                capabilities: pm msi pciexpress bus_master cap_list                                                 
                configuration: driver=ohci1394 latency=0                                                            
                resources: irq:19 memory:febff800-febfffff ioport:e800(size=256)                                    
        *-storage                                                                                                   
             description: SATA controller                                                                           
             product: GeForce 7100/nForce 630i SATA                                                                 
             vendor: nVidia Corporation                                                                             
             physical id: e                                                                                         
             bus info: pci@0000:00:0e.0                                                                             
             logical name: scsi0                                                                                    
             logical name: scsi1                                                                                    
             version: a2                                                                                            
             width: 32 bits                                                                                         
             clock: 66MHz                                                                                           
             capabilities: storage pm msi bus_master cap_list emulated                                              
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3                                             
             resources: irq:27 ioport:c480(size=8) ioport:c400(size=4) ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=16) memory:f9ffc000-f9ffdfff                                                                            
           *-disk                                                                                                   
                description: ATA Disk                                                                               
                product: WDC WD6400AAKS-2                                                                           
                vendor: Western Digital                                                                             
                physical id: 0                                                                                      
                bus info: scsi@0:0.0.0                                                                              
                logical name: /dev/sda                                                                              
                version: 01.0                                                                                       
                serial: WD-WMASY7010359                                                                             
                size: 596GiB (640GB)                                                                                
                capabilities: partitioned partitioned:dos                                                           
                configuration: ansiversion=5 signature=328bacae                                                     
              *-volume:0                                                                                            
                   description: Windows NTFS volume                                                                 
                   physical id: 1                                                                                   
                   bus info: scsi@0:0.0.0,1                                                                         
                   logical name: /dev/sda1                                                                          
                   version: 3.1                                                                                     
                   serial: 607be859-25b0-6041-97d9-19127d0663bc                                                     
                   size: 97GiB                                                                                      
                   capacity: 97GiB                                                                                  
                   capabilities: primary bootable ntfs initialized                                                  
                   configuration: clustersize=4096 created=2008-11-29 04:30:33 filesystem=ntfs label=ACER state=clean                                                                                                                   
              *-volume:1                                                                                            
                   description: Linux swap volume                                                                   
                   physical id: 2                                                                                   
                   bus info: scsi@0:0.0.0,2                                                                         
                   logical name: /dev/sda2                                                                          
                   version: 1                                                                                       
                   serial: ba3f8fc7-9d7a-493d-a92a-71af270ab7ae                                                     
                   size: 1913MiB                                                                                    
                   capacity: 1913MiB                                                                                
                   capabilities: primary nofs swap initialized                                                      
                   configuration: filesystem=swap pagesize=4096                                                     
              *-volume:2                                                                                            
                   description: Linux filesystem partition                                                          
                   physical id: 3                                                                                   
                   bus info: scsi@0:0.0.0,3                                                                         
                   logical name: /dev/sda3                                                                          
                   logical name: /                                                                                  
                   version: 3.6                                                                                     
                   serial: 5522709c-f522-4ee1-9abe-380bdc3ba5aa                                                     
                   size: 93GiB                                                                                      
                   capacity: 93GiB                                                                                  
                   capabilities: primary journaled reiserfs initialized                                             
                   configuration: filesystem=reiserfs hash=r5 mount.fstype=reiserfs mount.options=rw,relatime,notail state=mounted                                                                                                      
              *-volume:3                                                                                            
                   description: Extended partition                                                                  
                   physical id: 4                                                                                   
                   bus info: scsi@0:0.0.0,4                                                                         
                   logical name: /dev/sda4                                                                          
                   size: 403GiB                                                                                     
                   capacity: 403GiB                                                                                 
                   capabilities: primary extended partitioned partitioned:extended                                  
                 *-logicalvolume:0                                                                                  
                      description: FAT16 partition                                                                  
                      physical id: 5                                                                                
                      logical name: /dev/sda5                                                                       
                      logical name: /common                                                                         
                      capacity: 390GiB                                                                              
                      configuration: mount.fstype=reiserfs mount.options=rw,relatime state=mounted                  
                 *-logicalvolume:1                                                                                  
                      description: Linux filesystem partition                                                       
                      physical id: 6                                                                                
                      logical name: /dev/sda6                                                                       
                      logical name: /home                                                                           
                      capacity: 12GiB                                                                               
                      configuration: mount.fstype=reiserfs mount.options=rw,relatime state=mounted                  
           *-cdrom                                                                                                  
                description: DVD-RAM writer                                                                         
                product: DVDRAM GH40F                                                                               
                vendor: HL-DT-ST                                                                                    
                physical id: 1                                                                                      
                bus info: scsi@1:0.0.0                                                                              
                logical name: /dev/cdrom                                                                            
                logical name: /dev/cdrw                                                                             
                logical name: /dev/dvd                                                                              
                logical name: /dev/dvdrw                                                                            
                logical name: /dev/scd0                                                                             
                logical name: /dev/sr0                                                                              
                version: MG01                                                                                       
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                                          
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-network
             description: Ethernet interface
             product: MCP73 Ethernet
             vendor: nVidia Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: eth0
             version: a2
             serial: 00:21:97:c7:67:ea
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=10.77.10.100 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
             resources: irq:28 memory:f9ff7000-f9ff7fff ioport:b880(size=8) memory:f9ffe800-f9ffe8ff memory:f9ffe400-f9ffe40f
     *-scsi
          physical id: 1
          bus info: usb@1:5
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc

Any help is GREATLY appreciated as I am lost w/o my cdrom! Let me know.

---

