---
title: "Network -Unclaimed"
date: 2010-02-18
forum: Hardware
---

### Post by AlarmTech on 2010-02-18
Help!
 I've been playing around Ubuntu since 6.10. Never really serious until I decided to go MS free last year. I got my 2wire PCMCIA card to work after switching to WICD instead of NetworkManager. 
Ever since I installed VirtualBox it hasn't worked. 

I was wondering if someone could look over my setup to make the Wifi work again.

Thanks,

Karl

Kubuntu 9.10

karl@Slave7:~$ sudo lshw
[sudo] password for karl: 
slave7                    
    description: Notebook 
    product: CF-50BBLNUDM 
    vendor: Matsushita Electric Industrial Co.,Ltd.
    version: 002                                   
    serial: 3CYUA02203                             
    width: 32 bits                                 
    capabilities: smbios-2.3 dmi-2.3               
    configuration: boot=normal chassis=notebook uuid=00000000-0000-1000-8000-00804529C619
  *-core                                                                                 
       description: Motherboard                                                          
       product: CF50-2                                                                   
       vendor: Matsushita Electric Industrial Co.,Ltd.                                   
       physical id: 0                                                                    
       version: 001                                                                      
       serial: None                                                                      
     *-firmware                                                                          
          description: BIOS                                                              
          vendor: Phoenix Technologies K.K.                                              
          physical id: 0                                                                 
          version: V2.00L10A (01/22/2003)                                                
          size: 114KiB                                                                   
          capacity: 448KiB                                                               
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi agp smartbattery biosbootspecification netboot                                                                                                
     *-cpu                                                                                                                                            
          description: CPU                                                                                                                            
          product: Mobile Intel(R) Pentium(R) 4 - M CPU 2.20GHz                                                                                       
          vendor: Intel Corp.                                                                                                                         
          physical id: 4                                                                                                                              
          bus info: cpu@0                                                                                                                             
          version: 15.2.7                                                                                                                             
          slot: IC1                                                                                                                                   
          size: 1200MHz                                                                                                                               
          capacity: 2200MHz                                                                                                                           
          width: 32 bits                                                                                                                              
          clock: 400MHz                                                                                                                               
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid cpufreq                                                                                                                             
          configuration: id=0                                                                                                                         
        *-cache:0                                                                                                                                     
             description: L1 cache                                                                                                                    
             physical id: 8                                                                                                                           
             slot: L1 Cache                                                                                                                           
             size: 8KiB                                                                                                                               
             capacity: 20KiB                                                                                                                          
             capabilities: internal write-back                                                                                                        
        *-cache:1                                                                                                                                     
             description: L2 cache                                                                                                                    
             physical id: 9                                                                                                                           
             slot: L2 Cache                                                                                                                           
             size: 512KiB                                                                                                                             
             capacity: 512KiB                                                                                                                         
             capabilities: burst internal write-back                                                                                                  
     *-memory:0                                                                                                                                       
          description: System Memory                                                                                                                  
          physical id: 1e                                                                                                                             
          slot: System board or motherboard                                                                                                           
          capacity: 2GiB                                                                                                                              
        *-bank:0                                                                                                                                      
             description: TSOP SDRAM Synchronous                                                                                                      
             physical id: 0                                                                                                                           
             slot: Onboard                                                                                                                            
             size: 256MiB                                                                                                                             
             width: 64 bits                                                                                                                           
        *-bank:1                                                                                                                                      
             description: DIMM SDRAM Synchronous                                                                                                      
             physical id: 1                                                                                                                           
             slot: DIMM                                                                                                                               
             size: 256MiB                                                                                                                             
             width: 64 bits                                                                                                                           
     *-memory:1 UNCLAIMED                                                                                                                             
          description: Flash Memory                                                                                                                   
          physical id: 1f                                                                                                                             
          slot: System board or motherboard                                                                                                           
          capacity: 512KiB                                                                                                                            
        *-bank UNCLAIMED                                                                                                                              
             description: TSOP FLASH Non-volatile                                                                                                     
             physical id: 0                                                                                                                           
             slot: Flash ROM                                                                                                                          
             size: 512KiB                                                                                                                             
             width: 8 bits                                                                                                                            
     *-memory:2 UNCLAIMED                                                                                                                             
          physical id: 1                                                                                                                              
     *-memory:3 UNCLAIMED                                                                                                                             
          physical id: 2                                                                                                                              
     *-pci                                                                                                                                            
          description: Host bridge                                                                                                                    
          product: 82845 845 [Brookdale] Chipset Host Bridge                                                                                          
          vendor: Intel Corporation                                                                                                                   
          physical id: 100                                                                                                                            
          bus info: pci@0000:00:00.0                                                                                                                  
          version: 04                                                                                                                                 
          width: 32 bits                                                                                                                              
          clock: 33MHz                                                                                                                                
          configuration: driver=agpgart-intel                                                                                                         
          resources: irq:0 memory:ec000000-efffffff(prefetchable)                                                                                     
        *-pci:0                                                                                                                                       
             description: PCI bridge                                                                                                                  
             product: 82845 845 [Brookdale] Chipset AGP Bridge                                                                                        
             vendor: Intel Corporation                                                                                                                
             physical id: 1                                                                                                                           
             bus info: pci@0000:00:01.0                                                                                                               
             version: 04                                                                                                                              
             width: 32 bits                                                                                                                           
             clock: 66MHz                                                                                                                             
             capabilities: pci bus_master                                                                                                             
             resources: ioport:3000(size=4096) memory:e8100000-e81fffff memory:f0000000-f7ffffff(prefetchable)                                        
           *-display UNCLAIMED                                                                                                                        
                description: VGA compatible controller                                                                                                
                product: Radeon Mobility M7 LW [Radeon Mobility 7500]                                                                                 
                vendor: ATI Technologies Inc                                                                                                          
                physical id: 0                                                                                                                        
                bus info: pci@0000:01:00.0                                                                                                            
                version: 00                                                                                                                           
                width: 32 bits                                                                                                                        
                clock: 66MHz                                                                                                                          
                capabilities: agp agp-2.0 pm bus_master cap_list                                                                                      
                configuration: latency=66 mingnt=8                                                                                                    
                resources: memory:f0000000-f7ffffff(prefetchable) ioport:3000(size=256) memory:e8100000-e810ffff memory:e8120000-e813ffff(prefetchable)                                                                                                                                                     
        *-usb                                                                                                                                         
             description: USB Controller                                                                                                              
             product: 82801CA/CAM USB Controller #1                                                                                                   
             vendor: Intel Corporation                                                                                                                
             physical id: 1d                                                                                                                          
             bus info: pci@0000:00:1d.0                                                                                                               
             version: 02                                                                                                                              
             width: 32 bits                                                                                                                           
             clock: 33MHz                                                                                                                             
             capabilities: bus_master                                                                                                                 
             configuration: driver=uhci_hcd latency=0                                                                                                 
             resources: irq:9 ioport:1800(size=32)                                                                                                    
        *-pci:1                                                                                                                                       
             description: PCI bridge                                                                                                                  
             product: 82801 Mobile PCI Bridge                                                                                                         
             vendor: Intel Corporation                                                                                                                
             physical id: 1e                                                                                                                          
             bus info: pci@0000:00:1e.0                                                                                                               
             version: 42                                                                                                                              
             width: 32 bits                                                                                                                           
             clock: 33MHz                                                                                                                             
             capabilities: pci bus_master                                                                                                             
             resources: ioport:4000(size=8192) memory:e8200000-e87fffff memory:20000000-27ffffff(prefetchable)                                        
           *-pcmcia:0                                                                                                                                 
                description: CardBus bridge                                                                                                           
                product: RL5c478                                                                                                                      
                vendor: Ricoh Co Ltd                                                                                                                  
                physical id: 0                                                                                                                        
                bus info: pci@0000:02:00.0                                                                                                            
                version: 80                                                                                                                           
                width: 64 bits                                                                                                                        
                clock: 33MHz                                                                                                                          
                capabilities: pcmcia bus_master cap_list                                                                                              
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128                                                               
                resources: iomemory:b00603020-b0060301f irq:9 memory:e8200000-e8200fff ioport:4000(size=256) ioport:4400(size=256) memory:20000000-23ffffff(prefetchable) memory:28000000-2bffffff                                                                                                          
           *-pcmcia:1                                                                                                                                 
                description: CardBus bridge                                                                                                           
                product: RL5c478                                                                                                                      
                vendor: Ricoh Co Ltd                                                                                                                  
                physical id: 0.1                                                                                                                      
                bus info: pci@0000:02:00.1                                                                                                            
                version: 80                                                                                                                           
                width: 64 bits                                                                                                                        
                clock: 33MHz                                                                                                                          
                capabilities: pcmcia bus_master cap_list                                                                                              
                configuration: driver=yenta_cardbus latency=176 maxlatency=5                                                                          
                resources: iomemory:b00a07020-b00a0701f irq:9 memory:e8201000-e8201fff ioport:4800(size=256) ioport:4c00(size=256) memory:24000000-27ffffff(prefetchable) memory:2c000000-2fffffff                                                                                                          
           *-network                                                                                                                                  
                description: Ethernet interface                                                                                                       
                product: RTL-8139/8139C/8139C+                                                                                                        
                vendor: Realtek Semiconductor Co., Ltd.                                                                                               
                physical id: 2                                                                                                                        
                bus info: pci@0000:02:02.0                                                                                                            
                logical name: eth0                                                                                                                    
                version: 10                                                                                                                           
                serial: 00:80:45:29:c6:19                                                                                                             
                size: 100MB/s                                                                                                                         
                capacity: 100MB/s                                                                                                                     
                width: 32 bits                                                                                                                        
                clock: 33MHz                                                                                                                          
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation                             
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.105 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s                                                                                           
                resources: irq:9 ioport:5000(size=256) memory:e8208800-e82088ff                                                                       
           *-usb:0                                                                                                                                    
                description: USB Controller                                                                                                           
                product: USB                                                                                                                          
                vendor: NEC Corporation                                                                                                               
                physical id: 4                                                                                                                        
                bus info: pci@0000:02:04.0                                                                                                            
                version: 43                                                                                                                           
                width: 32 bits                                                                                                                        
                clock: 33MHz                                                                                                                          
                capabilities: pm bus_master cap_list                                                                                                  
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1                                                                      
                resources: irq:9 memory:e8206000-e8206fff                                                                                             
           *-usb:1                                                                                                                                    
                description: USB Controller                                                                                                           
                product: USB                                                                                                                          
                vendor: NEC Corporation                                                                                                               
                physical id: 4.1                                                                                                                      
                bus info: pci@0000:02:04.1                                                                                                            
                version: 43                                                                                                                           
                width: 32 bits                                                                                                                        
                clock: 33MHz                                                                                                                          
                capabilities: pm bus_master cap_list                                                                                                  
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1                                                                      
                resources: irq:9 memory:e8207000-e8207fff                                                                                             
           *-usb:2                                                                                                                                    
                description: USB Controller                                                                                                           
                product: USB 2.0                                                                                                                      
                vendor: NEC Corporation                                                                                                               
                physical id: 4.2                                                                                                                      
                bus info: pci@0000:02:04.2                                                                                                            
                version: 04                                                                                                                           
                width: 32 bits                                                                                                                        
                clock: 33MHz                                                                                                                          
                capabilities: pm bus_master cap_list                                                                                                  
                configuration: driver=ehci_hcd latency=132 maxlatency=34 mingnt=16                                                                    
                resources: irq:9 memory:e8208c00-e8208cff                                                                                             
        *-isa                                                                                                                                         
             description: ISA bridge                                                                                                                  
             product: 82801CAM ISA Bridge (LPC)                                                                                                       
             vendor: Intel Corporation                                                                                                                
             physical id: 1f                                                                                                                          
             bus info: pci@0000:00:1f.0                                                                                                               
             version: 02                                                                                                                              
             width: 32 bits                                                                                                                           
             clock: 33MHz                                                                                                                             
             capabilities: isa bus_master                                                                                                             
             configuration: latency=0                                                                                                                 
        *-ide                                                                                                                                         
             description: IDE interface                                                                                                               
             product: 82801CAM IDE U100 Controller                                                                                                    
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
             resources: irq:9 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1820(size=16) memory:e8000000-e80003ff               
           *-disk                                                                                                                                     
                description: ATA Disk                                                                                                                 
                product: WDC WD1200UE-22K                                                                                                             
                vendor: Western Digital                                                                                                               
                physical id: 0                                                                                                                        
                bus info: scsi@0:0.0.0                                                                                                                
                logical name: /dev/sda                                                                                                                
                version: 01.0                                                                                                                         
                serial: WD-WXE806191072                                                                                                               
                size: 111GiB (120GB)                                                                                                                  
                capabilities: partitioned partitioned:dos                                                                                             
                configuration: ansiversion=5 signature=000a5bae                                                                                       
              *-volume:0                                                                                                                              
                   description: Windows FAT volume                                                                                                    
                   vendor: MSWIN4.1                                                                                                                   
                   physical id: 1                                                                                                                     
                   bus info: scsi@0:0.0.0,1                                                                                                           
                   logical name: /dev/sda1                                                                                                            
                   version: FAT32                                                                                                                     
                   serial: 4b1a-d727                                                                                                                  
                   size: 19GiB                                                                                                                        
                   capacity: 19GiB                                                                                                                    
                   capabilities: primary bootable fat initialized                                                                                     
                   configuration: FATs=2 filesystem=fat                                                                                               
              *-volume:1                                                                                                                              
                   description: Linux filesystem partition                                                                                            
                   vendor: Linux                                                                                                                      
                   physical id: 2                                                                                                                     
                   bus info: scsi@0:0.0.0,2                                                                                                           
                   logical name: /dev/sda2                                                                                                            
                   version: 1.0                                                                                                                       
                   serial: 1cf63bb5-98a8-42f2-8552-dc809aea000f                                                                                       
                   size: 20GiB                                                                                                                        
                   capacity: 20GiB                                                                                                                    
                   capabilities: primary extended_attributes large_files ext2 initialized                                                             
                   configuration: filesystem=ext2 modified=2010-02-12 15:07:44 mounted=2009-12-05 21:13:51 state=unknown                              
              *-volume:2                                                                                                                              
                   description: EXT3 volume                                                                                                           
                   vendor: Linux                                                                                                                      
                   physical id: 3                                                                                                                     
                   bus info: scsi@0:0.0.0,3                                                                                                           
                   logical name: /dev/sda3                                                                                                            
                   version: 1.0                                                                                                                       
                   serial: 91b163dc-4bc7-47ba-8dcc-b33001ea010f                                                                                       
                   size: 45GiB                                                                                                                        
                   capacity: 45GiB                                                                                                                    
                   capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized                                              
                   configuration: created=2009-12-05 19:33:22 filesystem=ext3 modified=2010-02-12 15:07:44 mounted=2010-02-12 10:24:16 state=clean    
              *-volume:3                                                                                                                              
                   description: Extended partition                                                                                                    
                   physical id: 4                                                                                                                     
                   bus info: scsi@0:0.0.0,4                                                                                                           
                   logical name: /dev/sda4                                                                                                            
                   size: 26GiB                                                                                                                        
                   capacity: 26GiB                                                                                                                    
                   capabilities: primary extended partitioned partitioned:extended                                                                    
                 *-logicalvolume:0                                                                                                                    
                      description: Linux filesystem partition                                                                                         
                      physical id: 5                                                                                                                  
                      logical name: /dev/sda5                                                                                                         
                      logical name: /                                                                                                                 
                      capacity: 25GiB                                                                                                                 
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted               
                 *-logicalvolume:1                                                                                                                    
                      description: Linux swap / Solaris partition                                                                                     
                      physical id: 6                                                                                                                  
                      logical name: /dev/sda6                                                                                                         
                      capacity: 1184MiB                                                                                                               
                      capabilities: nofs                                                                                                              
           *-cdrom                                                                                                                                    
                description: DVD reader                                                                                                               
                product: UJDA740 DVD/CDRW                                                                                                             
                vendor: MATSHITA                                                                                                                      
                physical id: 1                                                                                                                        
                bus info: scsi@1:0.0.0                                                                                                                
                logical name: /dev/cdrom                                                                                                              
                logical name: /dev/cdrw                                                                                                               
                logical name: /dev/dvd                                                                                                                
                logical name: /dev/scd0                                                                                                               
                logical name: /dev/sr0                                                                                                                
                version: 1.00                                                                                                                         
                capabilities: removable audio cd-r cd-rw dvd                                                                                          
                configuration: ansiversion=5 status=nodisc                                                                                            
        *-serial UNCLAIMED                                                                                                                            
             description: SMBus                                                                                                                       
             product: 82801CA/CAM SMBus Controller                                                                                                    
             vendor: Intel Corporation                                                                                                                
             physical id: 1f.3                                                                                                                        
             bus info: pci@0000:00:1f.3                                                                                                               
             version: 02                                                                                                                              
             width: 32 bits                                                                                                                           
             clock: 33MHz                                                                                                                             
             configuration: latency=0                                                                                                                 
             resources: ioport:1840(size=32)                                                                                                          
        *-multimedia                                                                                                                                  
             description: Multimedia audio controller                                                                                                 
             product: 82801CA/CAM AC'97 Audio Controller                                                                                              
             vendor: Intel Corporation                                                                                                                
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:9 ioport:1c00(size=256) ioport:1880(size=64)
     *-network UNCLAIMED
          description: Network controller
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 3
          bus info: pci@0000:07:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
          resources: memory:2c000000-2c001fff
  *-battery
       description: Lithium Ion Battery
       vendor: Panasonic
       physical id: 1
       slot: in the front,left-hand side
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
karl@Slave7:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:80:45:29:c6:19
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.105 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:9 ioport:5000(size=256) memory:e8208800-e82088ff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=0
       resources: memory:2c000000-2c001fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by AlarmTech on 2010-02-19
I went back and removed virtual box, WICD and reinstalled WICD. Removed the Windows driver from NDISWrapper and added it back. 
Rebooted and now my 2Wire PCMCIA card is working like a champ.

From what I've read this card can be a headache.

---

