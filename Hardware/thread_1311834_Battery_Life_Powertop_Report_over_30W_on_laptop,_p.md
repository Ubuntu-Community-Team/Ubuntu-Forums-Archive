---
title: "Battery Life Powertop Report over 30W on laptop, please help"
date: 2009-11-02
forum: Hardware
---

### Post by aaronfc on 2009-11-02
Hi,
I'm new to ubuntu and I just installed 9.10, I always thought that my laptop had very bad battery support. On vista I could only use it fo100,0%  Dispositivo USB  1-8 : USB2.0-CRW (Generic)r a periode of 1:30h more or less.

Now when I installed PowerTop i found that it reports that my latpot is using about 30W what seems to be a vert high value for it, so its not battery problem, is consumition problem, no?

Here I paste my proccessor info:
```
cat /proc/cpuinfo
processor       : 0                           
vendor_id       : GenuineIntel                
cpu family      : 6                           
model           : 15                          
model name      : Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping        : 13                                             
cpu MHz         : 996.000                                        
cache size      : 2048 KB                                        
physical id     : 0                                              
siblings        : 2                                              
core id         : 0                                              
cpu cores       : 2                                              
apicid          : 0                                              
initial apicid  : 0                                              
fdiv_bug        : no                                             
hlt_bug         : no                                             
f00f_bug        : no                                             
coma_bug        : no                                             
fpu             : yes                                            
fpu_exception   : yes                                            
cpuid level     : 10                                             
wp              : yes                                            
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm                                                                                                                     
bogomips        : 3666.71                                                                                             
clflush size    : 64                                                                                                  
power management:                                                                                                     

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6           
model           : 15          
model name      : Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
stepping        : 13                                             
cpu MHz         : 996.000                                        
cache size      : 2048 KB                                        
physical id     : 0                                              
siblings        : 2                                              
core id         : 1                                              
cpu cores       : 2                                              
apicid          : 1                                              
initial apicid  : 1                                              
fdiv_bug        : no                                             
hlt_bug         : no                                             
f00f_bug        : no                                             
coma_bug        : no                                             
fpu             : yes                                            
fpu_exception   : yes                                            
cpuid level     : 10                                             
wp              : yes                                            
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm                                                                                                                     
bogomips        : 3667.00                                                                                             
clflush size    : 64                                                                                                  
power management:                            
```And here I paste my powertop report.
```
powertop --dump
PowerTOP 1.11   (C) 2007, 2008 Intel Corporation                                                                                                                                    
                                                                                                                                                                                    
Recolectando datos durante 15 segundos                                                                                                                                              
                                                                                                                                                                                    
                                                                                                                                                                                    
Cn                Residencia media                                                                                                                                                  
C0 (cpu ejecutando)        ( 9,9%)                                                                                                                                                  
C0                0,0ms ( 0,0%)                                                                                                                                                     
C1 halt           0,0ms ( 0,0%)                                                                                                                                                     
C2                2,0ms (11,4%)                                                                                                                                                     
C3                2,0ms (78,7%)                                                                                                                                                     
P-estados (frecuencias)                                                                                                                                                             
  1,83 GHz     9,4%                                                                                                                                                                 
  1328 MHz     0,1%                                                                                                                                                                 
   996 MHz    90,5%                                                                                                                                                                 
Despertares por segundo: 457,0  intervalo: 15,0s                                                                                                                                    
Consumo de energía (estimado por ACPI): 33,2W (0,4 horas)                                                                                                                           
Causas principales de despertares:                                                                                                                                                  
  39,8% (254,3)       <interrup> : Teclado/ratón/touchpad PS/2                                                                                                                      
  16,8% (107,7)         <núcleo> : hrtimer_start_range_ns (tick_sched_timer)                                                                                                        
  14,3% ( 91,2)       <interrup> : ath, radeon@pci:0000:01:00.0                                                                                                                     
  11,8% ( 75,2)      <IPI núcleo> : Rescheduling interrupts                                                                                                                         
   7,4% ( 47,5)       <interrup> : interrupción extra de reloj                                                                                                                      
   3,6% ( 23,1)           firefox : hrtimer_start_range_ns (hrtimer_wakeup)
   2,2% ( 13,9)              Xorg : hrtimer_start_range_ns (hrtimer_wakeup)
   0,8% (  5,4)    plasma-desktop : hrtimer_start_range_ns (hrtimer_wakeup)
   0,5% (  3,2)          knotify4 : hrtimer_start_range_ns (hrtimer_wakeup)
   0,4% (  2,8)         <núcleo> : hrtimer_start (tick_sched_timer)
   0,4% (  2,4)       <interrup> : acpi
   0,3% (  2,1)         <núcleo> : sk_reset_timer (tcp_delack_timer)
   0,3% (  2,0)         <núcleo> : clocksource_watchdog (clocksource_watchdog)
   0,2% (  1,4)       <interrup> : sata_sis, eth0
   0,2% (  1,1)           firefox : sk_reset_timer (tcp_write_timer)
   0,1% (  0,9)              kwin : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,6)           firefox : sk_reset_timer (tcp_delack_timer)
   0,1% (  0,5)         <núcleo> : neigh_periodic_timer (neigh_periodic_timer)
   0,1% (  0,5)              phy0 : ieee80211_associated (ieee80211_sta_timer)
   0,1% (  0,4)          kwalletd : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,4)             kded4 : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,4)              Xorg : sk_reset_timer (tcp_delack_timer)
   0,1% (  0,3)         gpg-agent : hrtimer_start_range_ns (hrtimer_wakeup)
   0,0% (  0,3)           konsole : hrtimer_start_range_ns (hrtimer_wakeup)
   0,0% (  0,2)      <IPI núcleo> : TLB shootdowns
   0,0% (  0,2)       packagekitd : hrtimer_start_range_ns (hrtimer_wakeup)
   0,0% (  0,2)    NetworkManager : hrtimer_start_range_ns (hrtimer_wakeup)
   0,0% (  0,2)           krunner : hrtimer_start_range_ns (hrtimer_wakeup)
   0,0% (  0,1)        kerneloops : hrtimer_start_range_ns (hrtimer_wakeup)
   0,0% (  0,1)         <núcleo> : add_timer (sta_info_cleanup)
   0,0% (  0,1)         ssh-agent : hrtimer_start_range_ns (hrtimer_wakeup)
   0,0% (  0,1)         <núcleo> : ath5k_calibrate (ath5k_calibrate)
   0,0% (  0,1)      avahi-daemon : hrtimer_start_range_ns (hrtimer_wakeup)
   0,0% (  0,1)         <núcleo> : start_rt_bandwidth (sched_rt_period_timer)
   0,0% (  0,1)    plasma-desktop : add_timer (commit_timeout)
   0,0% (  0,1)              Xorg : hrtimer_start (it_real_fn)
   0,0% (  0,1)         klauncher : hrtimer_start_range_ns (hrtimer_wakeup)
   0,0% (  0,1)           pdflush : wb_kupdate (wb_timer_fn)
   0,0% (  0,1)              hald : hrtimer_start_range_ns (hrtimer_wakeup)

Un dispositivo USB está activo el 100,0% del tiempo:
Dispositivo USB  1-8 : USB2.0-CRW (Generic)

Estadísticas recientes de suspensión de USB
Nombre del dispositivo activo
100,0%  Dispositivo USB  1-8 : USB2.0-CRW (Generic)
  0,0%  Dispositivo USB  1-5 : USB 2.0 Image Capture Controller (Syntek Semiconductor)
  0,0%  Dispositivo USB usb3 : OHCI Host Controller (Linux 2.6.31-14-generic ohci_hcd)
  0,0%  Dispositivo USB usb2 : OHCI Host Controller (Linux 2.6.31-14-generic ohci_hcd)
100,0%  Dispositivo USB usb1 : EHCI Host Controller (Linux 2.6.31-14-generic ehci_hcd)
```It's curious "100,0%  Dispositivo USB  1-8 : USB2.0-CRW (Generic)", which I don't know what is it, but it's 100% of time enabled :S

(I'm spanish so sorry about my bad english :) )

Thanks in advance, I really need to get lower consumption :):popcorn:

---

### Post by peculiar penguin on 2009-11-02
You need to post your laptop's specs, without them we can only guess if that figure is reasonable or not - some laptops are designed to be very energy efficient, but there are also "desktop replacement" monsters with huge screens, multiple hard disks and powerful video cards that aren't really meant to be used unplugged.

---

### Post by aaronfc on 2009-11-03
Hi peculiar penguin, thanks for your response :D
Here I paste my lshw report:
```
lshw
linuxaaron                       
    description: Notebook        
    product: F5VL                
    vendor: ASUSTeK Computer Inc.
    version: 1.0                 
    serial: NF1S7C08900238       
    width: 32 bits               
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=A72781DC-B260-5496-1A00-001E8C8D5D2F
  *-core                                                                                 
       description: Motherboard                                                          
       product: F5VL                                                                     
       vendor: ASUSTeK Computer Inc.                                                     
       physical id: 0                                                                    
       version: 1.0                                                                      
       serial: BSN12345678901234567                                                      
       slot: To Be Filled By O.E.M.                                                      
     *-firmware                                                                          
          description: BIOS                                                              
          vendor: American Megatrends Inc.                                               
          physical id: 0                                                                 
          version: 213 (12/25/2007)                                                      
          size: 64KiB                                                                    
          capacity: 448KiB                                                               
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification                                                                                      
     *-cpu                                                                                                            
          description: CPU                                                                                            
          product: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz                                                    
          vendor: Intel Corp.                                                                                         
          physical id: 4                                                                                              
          bus info: cpu@0                                                                                             
          version: 6.15.13                                                                                            
          serial: 0000-06FD-0000-0000-0000-0000                                                                       
          slot: CPU 1                                                                                                 
          size: 996MHz                                                                                                
          capacity: 1837MHz                                                                                           
          width: 64 bits                                                                                              
          clock: 167MHz                                                                                               
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq                                                                                  
          configuration: id=1                                                                                         
        *-cache:0                                                                                                     
             description: L1 cache                                                                                    
             physical id: 5                                                                                           
             slot: L1-Cache                                                                                           
             size: 64KiB                                                                                              
             capacity: 64KiB                                                                                          
             capabilities: internal write-back instruction                                                            
        *-cache:1                                                                                                     
             description: L2 cache                                                                                    
             physical id: 6                                                                                           
             slot: L2-Cache                                                                                           
             size: 2MiB                                                                                               
             capacity: 2MiB                                                                                           
             capabilities: internal write-back unified                                                                
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
          physical id: 1b                                                                                             
          slot: System board or motherboard                                                                           
          size: 2GiB                                                                                                  
        *-bank:0                                                                                                      
             description: DIMM SDRAM Synchronous                                                                      
             product: PartNum0                                                                                        
             vendor: Manufacturer0                                                                                    
             physical id: 0                                                                                           
             serial: SerNum0                                                                                          
             slot: DIMM0                                                                                              
             size: 1GiB                                                                                               
             width: 64 bits                                                                                           
        *-bank:1                                                                                                      
             description: DIMM SDRAM Synchronous                                                                      
             product: PartNum1                                                                                        
             vendor: Manufacturer1                                                                                    
             physical id: 1                                                                                           
             serial: SerNum1                                                                                          
             slot: DIMM1                                                                                              
             size: 1GiB                                                                                               
             width: 64 bits                                                                                           
     *-pci                                                                                                            
          description: Host bridge                                                                                    
          product: 671MX                                                                                              
          vendor: Silicon Integrated Systems [SiS]                                                                    
          physical id: 100                                                                                            
          bus info: pci@0000:00:00.0                                                                                  
          version: 00                                                                                                 
          width: 32 bits                                                                                              
          clock: 33MHz                                                                                                
          configuration: latency=64                                                                                   
        *-pci:0                                                                                                       
             description: PCI bridge                                                                                  
             product: PCI-to-PCI bridge                                                                               
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: 1                                                                                           
             bus info: pci@0000:00:01.0                                                                               
             version: 00                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: pci pciexpress msi pm bus_master cap_list                                                  
             configuration: driver=pcieport-driver                                                                    
             resources: irq:24 ioport:a000(size=4096) memory:fa900000-fa9fffff ioport:cdf00000(size=268435456)        
           *-display UNCLAIMED                                                                                        
                description: VGA compatible controller                                                                
                product: Mobility Radeon X2300                                                                        
                vendor: ATI Technologies Inc                                                                          
                physical id: 0                                                                                        
                bus info: pci@0000:01:00.0                                                                            
                version: 00                                                                                           
                width: 32 bits                                                                                        
                clock: 33MHz                                                                                          
                capabilities: pm pciexpress msi bus_master cap_list                                                   
                configuration: latency=0                                                                              
                resources: memory:d0000000-d7ffffff(prefetchable) ioport:a800(size=256) memory:fa9f0000-fa9fffff memory:fa9c0000-fa9dffff(prefetchable)                                                                                     
        *-isa                                                                                                         
             description: ISA bridge                                                                                  
             product: SiS968 [MuTIOL Media IO]                                                                        
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: 2                                                                                           
             bus info: pci@0000:00:02.0                                                                               
             version: 01                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: isa bus_master                                                                             
             configuration: latency=0                                                                                 
        *-ide:0                                                                                                       
             description: IDE interface                                                                               
             product: 5513 [IDE]                                                                                      
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: 2.5                                                                                         
             bus info: pci@0000:00:02.5                                                                               
             logical name: scsi2                                                                                      
             version: 01                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: ide pm bus_master cap_list emulated                                                        
             configuration: driver=pata_sis latency=128                                                               
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffe0(size=16)        
           *-cdrom                                                                                                    
                description: DVD-RAM writer                                                                           
                product: DVD-RAM UJ-860S                                                                              
                vendor: MATSHITA                                                                                      
                physical id: 0.0.0                                                                                    
                bus info: scsi@2:0.0.0                                                                                
                logical name: /dev/cdrom                                                                              
                logical name: /dev/cdrw                                                                               
                logical name: /dev/dvd                                                                                
                logical name: /dev/dvdrw                                                                              
                logical name: /dev/scd0                                                                               
                logical name: /dev/sr0                                                                                
                version: 1.00                                                                                         
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                                            
                configuration: ansiversion=5 status=nodisc                                                            
        *-usb:0                                                                                                       
             description: USB Controller                                                                              
             product: USB 1.1 Controller                                                                              
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: 3                                                                                           
             bus info: pci@0000:00:03.0                                                                               
             version: 0f                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: bus_master                                                                                 
             configuration: driver=ohci_hcd latency=64 maxlatency=80                                                  
             resources: irq:20 memory:febff000-febfffff                                                               
        *-usb:1                                                                                                       
             description: USB Controller                                                                              
             product: USB 1.1 Controller                                                                              
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: 3.1                                                                                         
             bus info: pci@0000:00:03.1                                                                               
             version: 0f                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: bus_master                                                                                 
             configuration: driver=ohci_hcd latency=64 maxlatency=80                                                  
             resources: irq:21 memory:febfe000-febfefff                                                               
        *-usb:2                                                                                                       
             description: USB Controller                                                                              
             product: USB 2.0 Controller                                                                              
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: 3.3                                                                                         
             bus info: pci@0000:00:03.3                                                                               
             version: 00                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: pm bus_master cap_list                                                                     
             configuration: driver=ehci_hcd latency=64 maxlatency=80                                                  
             resources: irq:22 memory:febfd000-febfdfff                                                               
        *-ide:1                                                                                                       
             description: IDE interface                                                                               
             product: SATA Controller / IDE mode                                                                      
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: 5                                                                                           
             bus info: pci@0000:00:05.0                                                                               
             logical name: scsi0                                                                                      
             version: 03                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: ide pm bus_master cap_list emulated                                                        
             configuration: driver=sata_sis latency=64                                                                
             resources: irq:17 ioport:ec00(size=8) ioport:e800(size=4) ioport:e400(size=8) ioport:e000(size=4) ioport:dc00(size=16) ioport:d800(size=128)                                                                                   
           *-disk                                                                                                     
                description: ATA Disk                                                                                 
                product: ST9160821AS                                                                                  
                vendor: Seagate                                                                                       
                physical id: 0.0.0                                                                                    
                bus info: scsi@0:0.0.0                                                                                
                logical name: /dev/sda                                                                                
                version: 3.AL                                                                                         
                serial: 5MA8D8QW                                                                                      
                size: 149GiB (160GB)                                                                                  
                capabilities: partitioned partitioned:dos                                                             
                configuration: ansiversion=5 signature=bbc58b91                                                       
              *-volume:0                                                                                              
                   description: Windows NTFS volume                                                                   
                   physical id: 1                                                                                     
                   bus info: scsi@0:0.0.0,1                                                                           
                   logical name: /dev/sda1                                                                            
                   version: 3.1                                                                                       
                   serial: 0e213aca-a08f-264b-99c9-45773ed56c3a                                                       
                   size: 63GiB                                                                                        
                   capacity: 63GiB                                                                                    
                   capabilities: primary bootable ntfs initialized                                                    
                   configuration: clustersize=4096 created=2007-12-24 10:26:06 filesystem=ntfs label=VistaOS state=clean                                                                                                                    
              *-volume:1                                                                                              
                   description: Extended partition                                                                    
                   physical id: 2                                                                                     
                   bus info: scsi@0:0.0.0,2                                                                           
                   logical name: /dev/sda2                                                                            
                   size: 77GiB                                                                                        
                   capacity: 77GiB                                                                                    
                   capabilities: primary extended partitioned partitioned:extended                                    
                 *-logicalvolume:0                                                                                    
                      description: HPFS/NTFS partition                                                                
                      physical id: 5                                                                                  
                      logical name: /dev/sda5                                                                         
                      capacity: 66GiB                                                                                 
                 *-logicalvolume:1                                                                                    
                      description: Linux swap / Solaris partition                                                     
                      physical id: 6                                                                                  
                      logical name: /dev/sda6                                                                         
                      capacity: 2855MiB                                                                               
                      capabilities: nofs                                                                              
                 *-logicalvolume:2                                                                                    
                      description: Linux filesystem partition                                                         
                      physical id: 7                                                                                  
                      logical name: /dev/sda7                                                                         
                      logical name: /home                                                                             
                      capacity: 8134MiB                                                                               
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted 
              *-volume:2                                                                                              
                   description: EXT4 volume                                                                           
                   vendor: Linux                                                                                      
                   physical id: 3                                                                                     
                   bus info: scsi@0:0.0.0,3                                                                           
                   logical name: /dev/sda3                                                                            
                   logical name: /                                                                                    
                   version: 1.0                                                                                       
                   serial: 19942935-8206-4c91-bcb9-688be372bad0                                                       
                   size: 7993MiB                                                                                      
                   capacity: 7993MiB                                                                                  
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized                                                                                               
                   configuration: created=2007-12-27 00:15:58 filesystem=ext4 lastmountpoint=/\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;8&#65533;&#65533;&#65533;N&#65533;iW&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;N&#65533;&#65533;&#65533;N&#65533;&#65533;Y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533; modified=2009-10-30 11:28:49 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-11-03 22:47:22 state=mounted                                                
        *-pci:1                                                                                                       
             description: PCI bridge                                                                                  
             product: PCI-to-PCI bridge                                                                               
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: 6                                                                                           
             bus info: pci@0000:00:06.0                                                                               
             version: 00                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: pci msi pciexpress pm bus_master cap_list                                                  
             configuration: driver=pcieport-driver                                                                    
             resources: irq:25 memory:faa00000-faafffff                                                               
           *-network                                                                                                  
                description: Wireless interface                                                                       
                product: AR5001 Wireless Network Adapter                                                              
                vendor: Atheros Communications Inc.                                                                   
                physical id: 0                                                                                        
                bus info: pci@0000:02:00.0                                                                            
                logical name: wmaster0                                                                                
                version: 01                                                                                           
                serial: 00:15:af:62:71:8c                                                                             
                width: 64 bits                                                                                        
                clock: 33MHz                                                                                          
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless           
                configuration: broadcast=yes driver=ath5k ip=192.168.2.100 latency=0 multicast=yes wireless=IEEE 802.11bg                                                                                                                   
                resources: irq:16 memory:faaf0000-faafffff                                                            
        *-pci:2                                                                                                       
             description: PCI bridge                                                                                  
             product: PCI-to-PCI bridge                                                                               
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: 7                                                                                           
             bus info: pci@0000:00:07.0                                                                               
             version: 00                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: pci msi pciexpress pm bus_master cap_list                                                  
             configuration: driver=pcieport-driver                                                                    
             resources: irq:26 ioport:b000(size=8192) memory:fab00000-feafffff ioport:ddf00000(size=33554432)         
        *-network                                                                                                     
             description: Ethernet interface                                                                          
             product: RTL-8139/8139C/8139C+                                                                           
             vendor: Realtek Semiconductor Co., Ltd.                                                                  
             physical id: d                                                                                           
             bus info: pci@0000:00:0d.0                                                                               
             logical name: eth0                                                                                       
             version: 10                                                                                              
             serial: 00:1e:8c:8d:5d:2f                                                                                
             size: 10MB/s                                                                                             
             capacity: 100MB/s                                                                                        
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s                                                 
             resources: irq:17 ioport:d400(size=256) memory:febfcc00-febfccff                                         
        *-multimedia                                                                                                  
             description: Audio device                                                                                
             product: Azalia Audio Controller                                                                         
             vendor: Silicon Integrated Systems [SiS]                                                                 
             physical id: f                                                                                           
             bus info: pci@0000:00:0f.0                                                                               
             version: 00                                                                                              
             width: 32 bits                                                                                           
             clock: 33MHz                                                                                             
             capabilities: pm bus_master cap_list                                                                     
             configuration: driver=HDA Intel latency=0 maxlatency=11 mingnt=52                                        
             resources: irq:18 memory:febf8000-febfbfff                                                               
     *-scsi                                                                                                           
          physical id: 1                                                                                              
          bus info: usb@1:8                                                                                           
          logical name: scsi4                                                                                         
          capabilities: emulated scsi-host                                                                            
          configuration: driver=usb-storage                                                                           
        *-disk                                                                                                        
             description: SCSI Disk                                                                                   
             physical id: 0.0.0                                                                                       
             bus info: scsi@4:0.0.0                                                                                   
             logical name: /dev/sdb                                                                                   
```Thanks a lot for your help :) ¿any idea?

---

### Post by Axx83 on 2009-11-03
Vedo che sei italiano, al max mandami un msg privato, cmq ti rispondo in inglese x correttezza.

run
```
gedit usb_autosuspend.sh
```
and paste this
```
for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
done

for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "2" > $i
done
```
Close and save the file.

Now run
```
sudo ./usb_autosuspend.sh
```
and then re-run powertop

comes back when you have the results

---

### Post by aaronfc on 2009-11-03
Hello Axx83, sorry but I'm not italian :) I'm from spain, spanish :P you were very close :P

I did what you told me, but I don't apreciate any difference:
```
PowerTOP 1.11   (C) 2007, 2008 Intel Corporation 

Recolectando datos durante 15 segundos 


Cn                Residencia media
C0 (cpu ejecutando)        ( 0,9%)
C0                0,0ms ( 0,0%)   
C1 halt           0,0ms ( 0,0%)   
C2               10,2ms (23,6%)   
C3               10,3ms (75,5%)
P-estados (frecuencias)
  1,83 GHz     0,0%
  1328 MHz     0,0%
   996 MHz   100,0%
Despertares por segundo: 96,1   intervalo: 15,0s
Consumo de energía (estimado por ACPI): 31,9W (0,7 horas)
Causas principales de despertares:
  49,8% ( 54,5)       <interrup> : interrupción extra de reloj
  21,3% ( 23,3)       <interrup> : ath, radeon@pci:0000:01:00.0
  10,1% ( 11,0)           firefox : hrtimer_start_range_ns (hrtimer_wakeup)
   5,2% (  5,7)      <IPI núcleo> : Rescheduling interrupts
   4,4% (  4,8)         <núcleo> : hrtimer_start_range_ns (tick_sched_timer)
   2,2% (  2,4)       <interrup> : acpi
   1,9% (  2,1)         <núcleo> : hrtimer_start (tick_sched_timer)
   1,5% (  1,7)          knotify4 : hrtimer_start_range_ns (hrtimer_wakeup)
   1,0% (  1,1)         <núcleo> : clocksource_watchdog (clocksource_watchdog)
   0,5% (  0,5)    plasma-desktop : hrtimer_start_range_ns (hrtimer_wakeup)
   0,4% (  0,5)              kwin : hrtimer_start_range_ns (hrtimer_wakeup)
   0,2% (  0,3)         <núcleo> : neigh_periodic_timer (neigh_periodic_timer)
   0,2% (  0,3)              phy0 : ieee80211_associated (ieee80211_sta_timer)
   0,2% (  0,2)          kwalletd : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,1)           krunner : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,1)    NetworkManager : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,1)        kerneloops : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,1)         gpg-agent : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,1)       <interrup> : Teclado/ratón/touchpad PS/2
   0,1% (  0,1)         ssh-agent : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,1)         <núcleo> : igmp_heard_query (igmp_gq_timer_expire)
   0,1% (  0,1)         <núcleo> : add_timer (sta_info_cleanup)
   0,1% (  0,1)         klauncher : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,1)           dolphin : hrtimer_start_range_ns (hrtimer_wakeup)
   0,1% (  0,1)         <núcleo> : ath5k_calibrate (ath5k_calibrate)
   0,1% (  0,1)             kded4 : hrtimer_start_range_ns (hrtimer_wakeup)

Un dispositivo USB está activo el 100,0% del tiempo:
Dispositivo USB  1-8 : USB2.0-CRW (Generic)

Estadísticas recientes de suspensión de USB
Nombre del dispositivo activo
100,0%  Dispositivo USB  1-8 : USB2.0-CRW (Generic)
  0,0%  Dispositivo USB  1-5 : USB 2.0 Image Capture Controller (Syntek Semiconductor)
  0,0%  Dispositivo USB usb3 : OHCI Host Controller (Linux 2.6.31-14-generic ohci_hcd)
  0,0%  Dispositivo USB usb2 : OHCI Host Controller (Linux 2.6.31-14-generic ohci_hcd)
100,0%  Dispositivo USB usb1 : EHCI Host Controller (Linux 2.6.31-14-generic ehci_hcd)
```

¿? Any idea guys ?

---

### Post by peculiar penguin on 2009-11-03
Googling around I found a few complaints that this model is power hungry even when running Windows, which seems to be consistent with your own observations.

Considering that most manufacturers use Windows as the target platform and provide drivers optimized for it, that's a pretty bad sign overall... not sure if/how Linux can do better here.

The only thing I noticed which may have some potential is your GPU - it may support some power saving features (lowering clock speed when on battery power etc.) that often aren't enabled by default. It looks like you're using the radeon driver, see if you can get the "DynamicClocks" feature working (may have been renamed to ClockGating/DynamicPM? Not sure, maybe someone else with similar hardware can help you with this...).

---

### Post by aaronfc on 2009-11-04
ok thanks :) I'll continue trying to get it lower consumption :) very thanks to you, if anybody else can help me :P I'll check this post oftenly :)

Thanks!

---

### Post by Axx83 on 2009-11-04
your usb port doesn't go in autosuspend and that prevents the cpu to go idle. I have no idea why autosuspend in linux is so complicated but that's how it is.

I advice you to re-run that script that I made you wrote, on and off ac and then
```
sudo su
cat /sys/bus/usb/devices/*/power/level
```
and
```
cat /sys/bus/usb/devices/*/power/autosuspend
exit
```

all levels should say auto and all autosuspend should say a number above 0, in a normal case where usb get autosuspended.

Let us know.

---

