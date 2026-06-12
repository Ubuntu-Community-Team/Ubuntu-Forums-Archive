---
title: "do_IRQ: 0.91 No irq handler for vector"
date: 2009-08-08
forum: Hardware
---

### Post by luisfpg on 2009-08-08
Hi.
I keep getting this message in TTYs, and the syslog is flooded by this message: do_IRQ: 0.91 No irq handler for vector
Does anyone have any idea?

---

### Post by luisfpg on 2009-08-09
Here is the full dmesg output just after logging in:
[luis@luis-desktop ~]$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset     
[    0.000000] Initializing cgroup subsys cpu        
[    0.000000] Linux version 2.6.28-15-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #48-Ubuntu SMP Wed Jul 29 08:53:35 UTC 2009 (Ubuntu 2.6.28-15.48-generic)                                                                                                                                                                                   
[    0.000000] Command line: root=UUID=be57c5ab-ba41-489e-ab50-3394f1e7d542 ro locale=pt_BR quiet splash                                                                            
[    0.000000] KERNEL supported cpus:                                                                                                                                               
[    0.000000]   Intel GenuineIntel                                                                                                                                                 
[    0.000000]   AMD AuthenticAMD                                                                                                                                                   
[    0.000000]   Centaur CentaurHauls                                                                                                                                               
[    0.000000] BIOS-provided physical RAM map:                                                                                                                                      
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)                                                                                                             
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)                                                                                                             
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)                                                                                                           
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)                                                                                                          
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)                                                                                                           
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)                                                                                                           
[    0.000000] DMI 2.4 present.                                                                                                                                                     
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.                                                                                                  
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x3ffffffff                                                                                                                        
[    0.000000] Scanning 0 areas for low memory corruption                                                                                                                           
[    0.000000] modified physical RAM map:                                                                                                                                           
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)                                                                                                            
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)                                                                                                              
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)                                                                                                            
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)                                                                                                            
[    0.000000]  modified: 0000000000100000 - 000000007fee0000 (usable)                                                                                                              
[    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)                                                                                                            
[    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)                                                                                                           
[    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)                                                                                                            
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)                                                                                                            
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)                                                                                                            
[    0.000000] init_memory_mapping: 0000000000000000-000000007fee0000                                                                                                               
[    0.000000]  0000000000 - 007fe00000 page 2M                                                                                                                                     
[    0.000000]  007fe00000 - 007fee0000 page 4k                                                                                                                                     
[    0.000000] kernel direct mapping tables up to 7fee0000 @ 10000-14000                                                                                                            
[    0.000000] last_map_addr: 7fee0000 end: 7fee0000                                                                                                                                
[    0.000000] RAMDISK: 37858000 - 37fef69e                                                                                                                                         
[    0.000000] ACPI: RSDP 000F75E0, 0024 (r2 AWARD )                                                                                                                                
[    0.000000] ACPI: XSDT 7FEE30C0, 004C (r1 AWARD  ASUSACPI 42302E31 AWRD        0)                                                                                                
[    0.000000] ACPI: FACP 7FEEB080, 00F4 (r3 AWARD  ASUSACPI 42302E31 AWRD        0)                                                                                                
[    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4)                                                                                                    
[    0.000000] ACPI: DSDT 7FEE3240, 7DDB (r1 AWARD  ASUSACPI     1000 MSFT  3000000)                                                                                                
[    0.000000] ACPI: FACS 7FEE0000, 0040                                                                                                                                            
[    0.000000] ACPI: HPET 7FEEB2C0, 0038 (r1 AWARD  ASUSACPI 42302E31 AWRD       98)                                                                                                
[    0.000000] ACPI: MCFG 7FEEB340, 003C (r1 AWARD  ASUSACPI 42302E31 AWRD        0)                                                                                                
[    0.000000] ACPI: APIC 7FEEB1C0, 0090 (r1 AWARD  ASUSACPI 42302E31 AWRD        0)                                                                                                
[    0.000000] ACPI: SSDT 7FEEB8A0, 0304 (r1 AWARD  ASUSACPI 42302E31 AWRD        0)                                                                                                
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                                                                  
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fee0000]                                                                                                         
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                                                        
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]                                                                                        
[    0.000000]   #2 [0000200000 - 0000b7bbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7bbb0]                                                                                        
[    0.000000]   #3 [0037858000 - 0037fef69e]          RAMDISK ==> [0037858000 - 0037fef69e]                                                                                        
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]                                                                                        
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]                                                                                        
[    0.000000] found SMP MP-table at [ffff8800000f5b40] 000f5b40                                                                                                                    
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0                                                                            
[    0.000000] Zone PFN ranges:                                                                                                                                                     
[    0.000000]   DMA      0x00000010 -> 0x00001000                                                                                                                                  
[    0.000000]   DMA32    0x00001000 -> 0x00100000                                                                                                                                  
[    0.000000]   Normal   0x00100000 -> 0x00100000                                                                                                                                  
[    0.000000] Movable zone start PFN for each node                                                                                                                                 
[    0.000000] early_node_map[2] active PFN ranges                                                                                                                                  
[    0.000000]     0: 0x00000010 -> 0x0000009f                                                                                                                                      
[    0.000000]     0: 0x00000100 -> 0x0007fee0                                                                                                                                      
[    0.000000] On node 0 totalpages: 523887                                                                                                                                         
[    0.000000]   DMA zone: 56 pages used for memmap                                                                                                                                 
[    0.000000]   DMA zone: 2531 pages reserved                                                                                                                                      
[    0.000000]   DMA zone: 1396 pages, LIFO batch:0                                                                                                                                 
[    0.000000]   DMA32 zone: 7109 pages used for memmap                                                                                                                             
[    0.000000]   DMA32 zone: 512795 pages, LIFO batch:31                                                                                                                            
[    0.000000]   Normal zone: 0 pages used for memmap                                                                                                                               
[    0.000000]   Movable zone: 0 pages used for memmap                                                                                                                              
[    0.000000] ACPI: PM-Timer IO Port: 0x408                                                                                                                                        
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                                                                  
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                                                                                                                   
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)                                                                                                                   
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)                                                                                                                  
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)                                                                                                                  
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])                                                                                                                  
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                                                                                                                  
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])                                                                                                                  
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])                                                                                                                  
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])                                                                                                              
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23                                                                                                        
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfecc0000] gsi_base[24])                                                                                                             
[    0.000000] IOAPIC[1]: apic_id 5, version 0, address 0xfecc0000, GSI 24-47                                                                                                       
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                                                                                             
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)                                                                                                           
[    0.000000] ACPI: IRQ0 used by override.                                                                                                                                         
[    0.000000] ACPI: IRQ2 used by override.                                                                                                                                         
[    0.000000] ACPI: IRQ9 used by override.                                                                                                                                         
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfe800000                                                                                                                           
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                                                                                  
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs                                                                                                                                 
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000                                                                                                    
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000                                                                                                    
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)                                                                                               
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data                                                                                                                       
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1                                                                                                                            
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 514191                                                                                          
[    0.000000] Kernel command line: root=UUID=be57c5ab-ba41-489e-ab50-3394f1e7d542 ro locale=pt_BR quiet splash                                                                     
[    0.000000] Initializing CPU#0                                                                                                                                                   
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)                                                                                                                
[    0.000000] Extended CMOS year: 2000                                                                                                                                             
[    0.000000] Fast TSC calibration using PIT                                                                                                                                       
[    0.000000] Detected 2128.009 MHz processor.                                                                                                                                     
[    0.004000] Console: colour VGA+ 80x25                                                                                                                                           
[    0.004000] console [tty0] enabled                                                                                                                                               
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)                                                                                                    
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)                                                                                                     
[    0.004000] allocated 20971520 bytes of page_cgroup                                                                                                                              
[    0.004000] please try cgroup_disable=memory option if you don't want                                                                                                            
[    0.004000] Scanning for low memory corruption every 60 seconds                                                                                                                  
[    0.004000] Checking aperture...                                                                                                                                                 
[    0.004000] AGP bridge at 00:00:00                                                                                                                                               
[    0.004000] Aperture from AGP @ d0000000 old size 32 MB                                                                                                                          
[    0.004000] Aperture from AGP @ d0000000 size 128 MB (APSIZE f20)                                                                                                                
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area                                                                                                                        
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!                                                                                                        
[    0.004000] Memory: 2024756k/2096000k available (4749k kernel code, 452k absent, 70124k reserved, 2523k data, 532k init)                                                         
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1                                                                                              
[    0.004000] hpet clockevent registered                                                                                                                                           
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer                                                                                                     
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4256.01 BogoMIPS (lpj=8512036)                                                            
[    0.004000] Security Framework initialized                                                                                                                                       
[    0.004000] SELinux:  Disabled at boot.                                                                                                                                          
[    0.004000] AppArmor: AppArmor initialized                                                                                                                                       
[    0.004000] Mount-cache hash table entries: 256                                                                                                                                  
[    0.004000] Initializing cgroup subsys ns                                                                                                                                        
[    0.004000] Initializing cgroup subsys cpuacct                                                                                                                                   
[    0.004000] Initializing cgroup subsys memory                                                                                                                                    
[    0.004000] Initializing cgroup subsys freezer                                                                                                                                   
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K                                                                                                                                
[    0.004000] CPU: L2 cache: 2048K                                                                                                                                                 
[    0.004000] CPU: Physical Processor ID: 0                                                                                                                                        
[    0.004000] CPU: Processor Core ID: 0                                                                                                                                            
[    0.004000] using mwait in idle threads.                                                                                                                                         
[    0.004000] ACPI: Core revision 20080926                                                                                                                                         
[    0.005124] ACPI: Checking initramfs for custom DSDT                                                                                                                             
[    0.320144] Setting APIC routing to flat                                                                                                                                         
[    0.321762] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                                                                                                                 
[    0.362668] CPU0: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06                                                                                                    
[    0.364001] Booting processor 1 APIC 0x1 ip 0x6000                                                                                                                               
[    0.004000] Initializing CPU#1                                                                                                                                                   
[    0.004000] Calibrating delay using timer specific routine.. 4262.87 BogoMIPS (lpj=8525752)                                                                                      
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K                                                                                                                                
[    0.004000] CPU: L2 cache: 2048K                                                                                                                                                 
[    0.004000] CPU: Physical Processor ID: 0                                                                                                                                        
[    0.004000] CPU: Processor Core ID: 1                                                                                                                                            
[    0.448508] CPU1: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz stepping 06                                                                                                    
[    0.448539] checking TSC synchronization [CPU#0 -> CPU#1]: passed.                                                                                                               
[    0.452060] Brought up 2 CPUs                                                                                                                                                    
[    0.452063] Total of 2 processors activated (8518.89 BogoMIPS).                                                                                                                  
[    0.452295] CPU0 attaching sched-domain:                                                                                                                                         
[    0.452298]  domain 0: span 0-1 level MC                                                                                                                                         
[    0.452301]   groups: 0 1                                                                                                                                                        
[    0.452307] CPU1 attaching sched-domain:                                                                                                                                         
[    0.452309]  domain 0: span 0-1 level MC                                                                                                                                         
[    0.452311]   groups: 1 0                                                                                                                                                        
[    0.452392] net_namespace: 1400 bytes                                                                                                                                            
[    0.452392] Booting paravirtualized kernel on bare hardware                                                                                                                      
[    0.452392] Time: 20:23:54  Date: 08/09/09                                                                                                                                       
[    0.452392] regulator: core version 0.5                                                                                                                                          
[    0.452392] NET: Registered protocol family 16                                                                                                                                   
[    0.452392] ACPI: bus type pci registered                                                                                                                                        
[    0.452392] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                                                                                     
[    0.452392] PCI: MCFG area at e0000000 reserved in E820                                                                                                                          
[    0.469306] PCI: Using MMCONFIG at e0000000 - efffffff                                                                                                                           
[    0.469311] PCI: Using configuration type 1 for base access                                                                                                                      
[    0.469357] mtrr: your CPUs had inconsistent fixed MTRR settings                                                                                                                 
[    0.469361] mtrr: probably your BIOS does not setup all CPUs.                                                                                                                    
[    0.469366] mtrr: corrected configuration.                                                                                                                                       
[    0.473620] ACPI: EC: Look up EC in DSDT                                                                                                                                         
[    0.490534] ACPI: Interpreter enabled                                                                                                                                            
[    0.490539] ACPI: (supports S0 S1 S3 S4 S5)                                                                                                                                      
[    0.490571] ACPI: Using IOAPIC for interrupt routing                                                                                                                             
[    0.504725] ACPI: No dock devices found.                                                                                                                                         
[    0.504739] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                                                                               
[    0.504810] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]                                                                                                         
[    0.505351] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold                                                                                                                
[    0.505356] pci 0000:00:02.0: PME# disabled                                                                                                                                      
[    0.505418] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold                                                                                                                
[    0.505422] pci 0000:00:03.0: PME# disabled                                                                                                                                      
[    0.505498] pci 0000:00:0f.0: reg 10 io port: [0xfc00-0xfc07]                                                                                                                    
[    0.505506] pci 0000:00:0f.0: reg 14 io port: [0xf800-0xf803]                                                                                                                    
[    0.505513] pci 0000:00:0f.0: reg 18 io port: [0xf400-0xf407]                                                                                                                    
[    0.505521] pci 0000:00:0f.0: reg 1c io port: [0xf000-0xf003]                                                                                                                    
[    0.505529] pci 0000:00:0f.0: reg 20 io port: [0xec00-0xec0f]                                                                                                                    
[    0.505536] pci 0000:00:0f.0: reg 24 io port: [0xe800-0xe8ff]                                                                                                                    
[    0.505612] pci 0000:00:0f.1: reg 20 io port: [0xe400-0xe40f]                                                                                                                    
[    0.505701] pci 0000:00:10.0: reg 20 io port: [0xe000-0xe01f]                                                                                                                    
[    0.505723] pci 0000:00:10.0: supports D1 D2                                                                                                                                     
[    0.505725] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.505729] pci 0000:00:10.0: PME# disabled                                                                                                                                      
[    0.505787] pci 0000:00:10.1: reg 20 io port: [0xdc00-0xdc1f]                                                                                                                    
[    0.505809] pci 0000:00:10.1: supports D1 D2                                                                                                                                     
[    0.505811] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.505815] pci 0000:00:10.1: PME# disabled                                                                                                                                      
[    0.505873] pci 0000:00:10.2: reg 20 io port: [0xd800-0xd81f]                                                                                                                    
[    0.505895] pci 0000:00:10.2: supports D1 D2                                                                                                                                     
[    0.505897] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.505901] pci 0000:00:10.2: PME# disabled                                                                                                                                      
[    0.505959] pci 0000:00:10.3: reg 20 io port: [0xd400-0xd41f]                                                                                                                    
[    0.505981] pci 0000:00:10.3: supports D1 D2                                                                                                                                     
[    0.505983] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.505987] pci 0000:00:10.3: PME# disabled                                                                                                                                      
[    0.506024] pci 0000:00:10.4: reg 10 32bit mmio: [0xdffff000-0xdffff0ff]                                                                                                         
[    0.506067] pci 0000:00:10.4: supports D1 D2                                                                                                                                     
[    0.506069] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold                                                                                                          
[    0.506074] pci 0000:00:10.4: PME# disabled                                                                                                                                      
[    0.506478] pci 0000:02:00.0: reg 10 32bit mmio: [0xdc000000-0xdcffffff]                                                                                                         
[    0.506490] pci 0000:02:00.0: reg 14 64bit mmio: [0xa0000000-0xbfffffff]                                                                                                         
[    0.506502] pci 0000:02:00.0: reg 1c 64bit mmio: [0xdd000000-0xddffffff]                                                                                                         
[    0.506509] pci 0000:02:00.0: reg 24 io port: [0xac00-0xac7f]                                                                                                                    
[    0.506516] pci 0000:02:00.0: reg 30 32bit mmio: [0xdefe0000-0xdeffffff]                                                                                                         
[    0.506586] pci 0000:00:02.0: bridge io port: [0xa000-0xafff]                                                                                                                    
[    0.506590] pci 0000:00:02.0: bridge 32bit mmio: [0xdc000000-0xdeffffff]                                                                                                         
[    0.506598] pci 0000:00:02.0: bridge 64bit mmio pref: [0xa0000000-0xbfffffff]                                                                                                    
[    0.506693] pci 0000:03:00.0: reg 24 32bit mmio: [0xdfefe000-0xdfefffff]                                                                                                         
[    0.506703] pci 0000:03:00.0: reg 30 32bit mmio: [0xdfee0000-0xdfeeffff]                                                                                                         
[    0.506717] pci 0000:03:00.0: PME# supported from D3hot                                                                                                                          
[    0.506722] pci 0000:03:00.0: PME# disabled                                                                                                                                      
[    0.506775] pci 0000:03:00.1: reg 10 io port: [0xcc00-0xcc07]                                                                                                                    
[    0.506784] pci 0000:03:00.1: reg 14 io port: [0xc800-0xc803]                                                                                                                    
[    0.506793] pci 0000:03:00.1: reg 18 io port: [0xc400-0xc407]                                                                                                                    
[    0.506802] pci 0000:03:00.1: reg 1c io port: [0xc000-0xc003]                                                                                                                    
[    0.506812] pci 0000:03:00.1: reg 20 io port: [0xbc00-0xbc0f]                                                                                                                    
[    0.506907] pci 0000:00:03.0: bridge io port: [0xb000-0xcfff]                                                                                                                    
[    0.506912] pci 0000:00:03.0: bridge 32bit mmio: [0xdfe00000-0xdfefffff]                                                                                                         
[    0.506966] pci 0000:04:07.0: reg 10 io port: [0x9c00-0x9cff]                                                                                                                    
[    0.506974] pci 0000:04:07.0: reg 14 32bit mmio: [0xdfdff000-0xdfdff0ff]                                                                                                         
[    0.507003] pci 0000:04:07.0: reg 30 32bit mmio: [0x000000-0x01ffff]                                                                                                             
[    0.507014] pci 0000:04:07.0: supports D1 D2                                                                                                                                     
[    0.507016] pci 0000:04:07.0: PME# supported from D1 D2 D3hot D3cold                                                                                                             
[    0.507020] pci 0000:04:07.0: PME# disabled                                                                                                                                      
[    0.507063] pci 0000:00:13.1: transparent bridge                                                                                                                                 
[    0.507067] pci 0000:00:13.1: bridge io port: [0x9000-0x9fff]                                                                                                                    
[    0.507071] pci 0000:00:13.1: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]                                                                                                         
[    0.507100] bus 00 -> node 0                                                                                                                                                     
[    0.507109] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                                                                                  
[    0.507668] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]                                                                                                             
[    0.507866] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]                                                                                                             
[    0.508076] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PB._PRT]                                                                                                             
[    0.613277] ACPI: PCI Root Bridge [PCI1] (0000:80)                                                                                                                               
[    0.613341] pci 0000:80:01.0: reg 10 64bit mmio: [0x9fffc000-0x9fffffff]                                                                                                         
[    0.613376] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold                                                                                                                
[    0.613380] pci 0000:80:01.0: PME# disabled                                                                                                                                      
[    0.613436] bus 80 -> node 0                                                                                                                                                     
[    0.613444] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]                                                                                                                  
[    0.614189] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)                                                                                                             
[    0.614468] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5                                                                                                           
[    0.614751] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)                                                                                                             
[    0.615033] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12)                                                                                                             
[    0.615303] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 *10 11 12)                                                                                                             
[    0.615545] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.                                                                                                
[    0.615787] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.                                                                                                
[    0.616059] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 *11 12)                                                                                                             
[    0.616257] ACPI: WMI: Mapper loaded                                                                                                                                             
[    0.616327] SCSI subsystem initialized                                                                                                                                           
[    0.616327] libata version 3.00 loaded.                                                                                                                                          
[    0.616327] usbcore: registered new interface driver usbfs                                                                                                                       
[    0.616327] usbcore: registered new interface driver hub                                                                                                                         
[    0.616327] usbcore: registered new device driver usb                                                                                                                            
[    0.616327] PCI: Using ACPI for IRQ routing                                                                                                                                      
[    0.628011] Bluetooth: Core ver 2.13                                                                                                                                             
[    0.628028] NET: Registered protocol family 31                                                                                                                                   
[    0.628028] Bluetooth: HCI device and connection manager initialized                                                                                                             
[    0.628028] Bluetooth: HCI socket layer initialized                                                                                                                              
[    0.628028] NET: Registered protocol family 8                                                                                                                                    
[    0.628028] NET: Registered protocol family 20                                                                                                                                   
[    0.628037] NetLabel: Initializing                                                                                                                                               
[    0.628039] NetLabel:  domain hash size = 128                                                                                                                                    
[    0.628041] NetLabel:  protocols = UNLABELED CIPSOv4                                                                                                                             
[    0.628056] NetLabel:  unlabeled traffic allowed by default                                                                                                                      
[    0.628094] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0                                                                                                                              
[    0.628099] hpet0: 3 comparators, 32-bit 14.318180 MHz counter                                                                                                                   
[    0.632075] AppArmor: AppArmor Filesystem Enabled                                                                                                                                
[    0.636009] Switched to high resolution mode on CPU 0                                                                                                                            
[    0.636409] Switched to high resolution mode on CPU 1                                                                                                                            
[    0.644046] pnp: PnP ACPI init                                                                                                                                                   
[    0.644056] ACPI: bus type pnp registered                                                                                                                                        
[    0.650295] pnp: PnP ACPI: found 16 devices                                                                                                                                      
[    0.650297] ACPI: ACPI bus type pnp unregistered                                                                                                                                 
[    0.650308] system 00:01: ioport range 0x400-0x47f has been reserved                                                                                                             
[    0.650311] system 00:01: ioport range 0x500-0x50f has been reserved                                                                                                             
[    0.650317] system 00:02: ioport range 0x4d0-0x4d1 has been reserved                                                                                                             
[    0.650320] system 00:02: ioport range 0x290-0x29f has been reserved                                                                                                             
[    0.650322] system 00:02: ioport range 0x800-0x805 has been reserved                                                                                                             
[    0.650325] system 00:02: ioport range 0x880-0x88f has been reserved                                                                                                             
[    0.650335] system 00:0c: iomem range 0x10000000-0x10000fff could not be reserved                                                                                                
[    0.650341] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved                                                                                                    
[    0.650348] system 00:0f: iomem range 0xd3000-0xd3fff has been reserved                                                                                                          
[    0.650351] system 00:0f: iomem range 0xf0000-0xf7fff could not be reserved                                                                                                      
[    0.650354] system 00:0f: iomem range 0xf8000-0xfbfff could not be reserved                                                                                                      
[    0.650356] system 00:0f: iomem range 0xfc000-0xfffff could not be reserved                                                                                                      
[    0.650359] system 00:0f: iomem range 0xfe800000-0xfe8000ff has been reserved                                                                                                    
[    0.650362] system 00:0f: iomem range 0x7fee0000-0x7fefffff could not be reserved                                                                                                
[    0.650365] system 00:0f: iomem range 0xffff0000-0xffffffff has been reserved                                                                                                    
[    0.650367] system 00:0f: iomem range 0x0-0x9ffff could not be reserved                                                                                                          
[    0.650370] system 00:0f: iomem range 0x100000-0x7fedffff could not be reserved                                                                                                  
[    0.650373] system 00:0f: iomem range 0xfec00000-0xfec00fff has been reserved                                                                                                    
[    0.650376] system 00:0f: iomem range 0xfee00000-0xfee00fff has been reserved                                                                                                    
[    0.650379] system 00:0f: iomem range 0xfff80000-0xfffeffff has been reserved                                                                                                    
[    0.655092] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01                                                                                                                  
[    0.655094] pci 0000:00:01.0:   IO window: disabled                                                                                                                              
[    0.655100] pci 0000:00:01.0:   MEM window: disabled                                                                                                                             
[    0.655104] pci 0000:00:01.0:   PREFETCH window: disabled                                                                                                                        
[    0.655111] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02                                                                                                                  
[    0.655114] pci 0000:00:02.0:   IO window: 0xa000-0xafff                                                                                                                         
[    0.655120] pci 0000:00:02.0:   MEM window: 0xdc000000-0xdeffffff                                                                                                                
[    0.655125] pci 0000:00:02.0:   PREFETCH window: 0x000000a0000000-0x000000bfffffff                                                                                               
[    0.655132] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03                                                                                                                  
[    0.655136] pci 0000:00:03.0:   IO window: 0xb000-0xcfff                                                                                                                         
[    0.655142] pci 0000:00:03.0:   MEM window: 0xdfe00000-0xdfefffff                                                                                                                
[    0.655147] pci 0000:00:03.0:   PREFETCH window: disabled                                                                                                                        
[    0.655155] pci 0000:00:13.1: PCI bridge, secondary bus 0000:04                                                                                                                  
[    0.655158] pci 0000:00:13.1:   IO window: 0x9000-0x9fff                                                                                                                         
[    0.655164] pci 0000:00:13.1:   MEM window: 0xdfd00000-0xdfdfffff                                                                                                                
[    0.655168] pci 0000:00:13.1:   PREFETCH window: 0x00000080000000-0x000000800fffff                                                                                               
[    0.655185] pci 0000:00:01.0: setting latency timer to 64                                                                                                                        
[    0.655197] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27                                                                                                         
[    0.655201] pci 0000:00:02.0: setting latency timer to 64                                                                                                                        
[    0.655211] pci 0000:00:03.0: PCI INT A -> GSI 31 (level, low) -> IRQ 31                                                                                                         
[    0.655216] pci 0000:00:03.0: setting latency timer to 64                                                                                                                        
[    0.655224] pci 0000:00:13.1: setting latency timer to 64                                                                                                                        
[    0.655228] bus: 00 index 0 io port: [0x00-0xffff]                                                                                                                               
[    0.655230] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]                                                                                                                  
[    0.655233] bus: 01 index 0 mmio: [0x0-0x0]                                                                                                                                      
[    0.655234] bus: 01 index 1 mmio: [0x0-0x0]                                                                                                                                      
[    0.655236] bus: 01 index 2 mmio: [0x0-0x0]                                                                                                                                      
[    0.655238] bus: 01 index 3 mmio: [0x0-0x0]                                                                                                                                      
[    0.655240] bus: 02 index 0 io port: [0xa000-0xafff]                                                                                                                             
[    0.655242] bus: 02 index 1 mmio: [0xdc000000-0xdeffffff]                                                                                                                        
[    0.655244] bus: 02 index 2 mmio: [0xa0000000-0xbfffffff]                                                                                                                        
[    0.655246] bus: 02 index 3 mmio: [0x0-0x0]                                                                                                                                      
[    0.655248] bus: 03 index 0 io port: [0xb000-0xcfff]                                                                                                                             
[    0.655250] bus: 03 index 1 mmio: [0xdfe00000-0xdfefffff]                                                                                                                        
[    0.655252] bus: 03 index 2 mmio: [0x0-0x0]                                                                                                                                      
[    0.655253] bus: 03 index 3 mmio: [0x0-0x0]                                                                                                                                      
[    0.655255] bus: 04 index 0 io port: [0x9000-0x9fff]                                                                                                                             
[    0.655257] bus: 04 index 1 mmio: [0xdfd00000-0xdfdfffff]                                                                                                                        
[    0.655260] bus: 04 index 2 mmio: [0x80000000-0x800fffff]                                                                                                                        
[    0.655262] bus: 04 index 3 io port: [0x00-0xffff]                                                                                                                               
[    0.655264] bus: 04 index 4 mmio: [0x000000-0xffffffffffffffff]                                                                                                                  
[    0.655266] bus: 80 index 0 io port: [0x00-0xffff]                                                                                                                               
[    0.655268] bus: 80 index 1 mmio: [0x000000-0xffffffffffffffff]                                                                                                                  
[    0.655278] NET: Registered protocol family 2                                                                                                                                    
[    0.688106] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)                                                                                                    
[    0.688427] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)                                                                                                
[    0.693527] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)                                                                                                         
[    0.694600] TCP: Hash tables configured (established 262144 bind 65536)                                                                                                          
[    0.694602] TCP reno registered                                                                                                                                                  
[    0.704213] NET: Registered protocol family 1                                                                                                                                    
[    0.704367] checking if image is initramfs... it is                                                                                                                              
[    1.554959] Freeing initrd memory: 7773k freed                                                                                                                                   
[    1.559500] audit: initializing netlink socket (disabled)                                                                                                                        
[    1.559538] type=2000 audit(1249849435.556:1): initialized                                                                                                                       
[    1.567353] HugeTLB registered 2 MB page size, pre-allocated 0 pages                                                                                                             
[    1.568508] VFS: Disk quotas dquot_6.5.1                                                                                                                                         
[    1.568555] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)                                                                                                            
[    1.569085] fuse init (API version 7.10)                                                                                                                                         
[    1.569152] msgmni has been set to 3971                                                                                                                                          
[    1.569316] alg: No test for stdrng (krng)                                                                                                                                       
[    1.569326] io scheduler noop registered                                                                                                                                         
[    1.569328] io scheduler anticipatory registered                                                                                                                                 
[    1.569330] io scheduler deadline registered                                                                                                                                     
[    1.569364] io scheduler cfq registered (default)                                                                                                                                
[    1.569380] PCI: VIA PCI bridge detected.Disabling DAC.                                                                                                                          
[    1.569504] pci 0000:02:00.0: Boot video device                                                                                                                                  
[    1.578634] pcieport-driver 0000:00:02.0: setting latency timer to 64                                                                                                            
[    1.578691] pcieport-driver 0000:00:02.0: found MSI capability                                                                                                                   
[    1.578730] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X                                                                                                                 
[    1.578744] pci_express 0000:00:02.0:pcie00: allocate port service                                                                                                               
[    1.578757] pci_express 0000:00:02.0:pcie01: allocate port service                                                                                                               
[    1.578766] pci_express 0000:00:02.0:pcie02: allocate port service                                                                                                               
[    1.578776] pci_express 0000:00:02.0:pcie03: allocate port service                                                                                                               
[    1.578839] pcieport-driver 0000:00:03.0: setting latency timer to 64                                                                                                            
[    1.578886] pcieport-driver 0000:00:03.0: found MSI capability                                                                                                                   
[    1.578927] pcieport-driver 0000:00:03.0: irq 2302 for MSI/MSI-X                                                                                                                 
[    1.578943] pci_express 0000:00:03.0:pcie00: allocate port service                                                                                                               
[    1.578953] pci_express 0000:00:03.0:pcie01: allocate port service                                                                                                               
[    1.578963] pci_express 0000:00:03.0:pcie02: allocate port service                                                                                                               
[    1.578973] pci_express 0000:00:03.0:pcie03: allocate port service                                                                                                               
[    1.584221] aer 0000:00:02.0:pcie01: service driver aer loaded                                                                                                                   
[    1.589352] aer 0000:00:03.0:pcie01: service driver aer loaded                                                                                                                   
[    1.589360] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                                                                                      
[    1.589913] pciehp 0000:00:02.0:pcie02: HPC vendor_id 1106 device_id a327 ss_vid 0 ss_did 0                                                                                      
[    1.589943] pciehp 0000:00:02.0:pcie02: service driver pciehp loaded                                                                                                             
[    1.590443] pciehp 0000:00:03.0:pcie02: HPC vendor_id 1106 device_id c327 ss_vid 0 ss_did 0                                                                                      
[    1.590472] pciehp 0000:00:03.0:pcie02: service driver pciehp loaded                                                                                                             
[    1.590481] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                                                                                          
[    1.590641] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                                                                            
[    1.590644] ACPI: Power Button (FF) [PWRF]                                                                                                                                       
[    1.590692] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                                                                   
[    1.590694] ACPI: Power Button (CM) [PWRB]                                                                                                                                       
[    1.590745] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2                                                                                   
[    1.590753] ACPI: Sleep Button (CM) [SLPB]                                                                                                                                       
[    1.590816] fan PNP0C0B:00: registered as cooling_device0                                                                                                                        
[    1.590822] ACPI: Fan [FAN] (on)                                                                                                                                                 
[    1.591834] ACPI: SSDT 7FEEB3C0, 0175 (r1 AWARD  ASUSACPI 42302E31 AWRD        0)                                                                                                
[    1.592195] processor ACPI_CPU:00: registered as cooling_device1                                                                                                                 
[    1.592400] ACPI: SSDT 7FEEB7D0, 00CE (r1 AWARD  ASUSACPI 42302E31 AWRD        0)                                                                                                
[    1.592807] processor ACPI_CPU:01: registered as cooling_device2                                                                                                                 
[    1.599951] thermal LNXTHERM:01: registered as thermal_zone0                                                                                                                     
[    1.600551] ACPI: Thermal Zone [THRM] (40 C)                                                                                                                                     
[    1.640780] Linux agpgart interface v0.103                                                                                                                                       
[    1.640789] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                                                                                                
[    1.640874] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                                                                 
[    1.641182] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                                                                      
[    1.641883] brd: module loaded                                                                                                                                                   
[    1.642161] loop: module loaded                                                                                                                                                  
[    1.642218] Fixed MDIO Bus: probed                                                                                                                                               
[    1.642223] PPP generic driver version 2.4.2                                                                                                                                     
[    1.642273] input: Macintosh mouse button emulation as /devices/virtual/input/input3                                                                                             
[    1.642296] Driver 'sd' needs updating - please use bus_type methods                                                                                                             
[    1.642304] Driver 'sr' needs updating - please use bus_type methods                                                                                                             
[    1.642344] ahci 0000:03:00.0: version 3.0                                                                                                                                       
[    1.642362] ahci 0000:03:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28                                                                                                        
[    1.642404] ahci 0000:03:00.0: PCI: Disallowing DAC for device                                                                                                                   
[    1.656563] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode                                                                                         
[    1.656567] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part                                                                                                     
[    1.656573] ahci 0000:03:00.0: setting latency timer to 64                                                                                                                       
[    1.656692] do_IRQ: 0.99 No irq handler for vector                                                                                                                               
[    1.656795] scsi0 : ahci                                                                                                                                                         
[    1.656887] scsi1 : ahci                                                                                                                                                         
[    1.656927] ata1: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe100 irq 28                                                                                                 
[    1.656930] ata2: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe180 irq 28                                                                                                 
[    1.976023] ata1: SATA link down (SStatus 0 SControl 300)                                                                                                                        
[    2.312022] ata2: SATA link down (SStatus 0 SControl 300)                                                                                                                        
[    2.328127] sata_via 0000:00:0f.0: version 2.4                                                                                                                                   
[    2.328139] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21                                                                                                    
[    2.328167] sata_via 0000:00:0f.0: routed to hard irq line 11                                                                                                                    
[    2.328247] scsi2 : sata_via                                                                                                                                                     
[    2.328306] scsi3 : sata_via                                                                                                                                                     
[    2.329911] ata3: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 21                                                                                                    
[    2.329913] ata4: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 21                                                                                                    
[    2.532010] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)                                                                                                               
[    2.696334] ata3.00: ATA-7: SAMSUNG SP2504C, VT100-50, max UDMA7                                                                                                                 
[    2.696337] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)                                                                                                         
[    2.736349] ata3.00: configured for UDMA/133                                                                                                                                     
[    2.940030] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)                                                                                                               
[    2.950722] isa bounce pool size: 16 pages                                                                                                                                       
[    2.950810] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5                                                                                         
[    2.950887] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)                                                                                              
[    2.950903] sd 2:0:0:0: [sda] Write Protect is off                                                                                                                               
[    2.950905] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                                                                            
[    2.950928] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    2.951002] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)                                                                                              
[    2.951015] sd 2:0:0:0: [sda] Write Protect is off                                                                                                                               
[    2.951017] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                                                                            
[    2.951039] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                              
[    2.951042]  sda: sda1 < sda5 > sda3 sda4                                                                                                                                        
[    2.954462] sd 2:0:0:0: [sda] Attached SCSI disk                                                                                                                                 
[    2.954517] sd 2:0:0:0: Attached scsi generic sg0 type 0                                                                                                                         
[    2.954780] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)                                                                                                            
[    2.954787] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 29 (level, low) -> IRQ 29                                                                                                
[    2.954814] pata_jmicron 0000:03:00.1: setting latency timer to 64                                                                                                               
[    2.954870] scsi4 : pata_jmicron                                                                                                                                                 
[    2.954918] scsi5 : pata_jmicron                                                                                                                                                 
[    2.954952] ata5: PATA max UDMA/100 cmd 0xcc00 ctl 0xc800 bmdma 0xbc00 irq 29                                                                                                    
[    2.954954] ata6: PATA max UDMA/100 cmd 0xc400 ctl 0xc000 bmdma 0xbc08 irq 29                                                                                                    
[    3.275263] pata_via 0000:00:0f.1: version 0.3.3                                                                                                                                 
[    3.275429] scsi6 : pata_via                                                                                                                                                     
[    3.275484] scsi7 : pata_via                                                                                                                                                     
[    3.276966] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14                                                                                                      
[    3.276968] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15                                                                                                      
[    3.440461] ata7.00: ATAPI: HL-DT-STDVD-RAM GSA-H22N, 1.02, max UDMA/66                                                                                                          
[    3.456336] ata7.00: configured for UDMA/66                                                                                                                                      
[    3.613315] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H22N 1.02 PQ: 0 ANSI: 5                                                                                         
[    3.617450] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray                                                                                                
[    3.617454] Uniform CD-ROM driver Revision: 3.20                                                                                                                                 
[    3.617559] sr 6:0:0:0: Attached scsi CD-ROM sr0                                                                                                                                 
[    3.617611] sr 6:0:0:0: Attached scsi generic sg1 type 5                                                                                                                         
[    3.617744] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                                                                                           
[    3.617763] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21                                                                                                    
[    3.617778] ehci_hcd 0000:00:10.4: EHCI Host Controller                                                                                                                          
[    3.617841] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1                                                                                                 
[    3.617874] ehci_hcd 0000:00:10.4: irq 21, io mem 0xdffff000                                                                                                                     
[    3.628010] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00                                                                                                                    
[    3.628091] usb usb1: configuration #1 chosen from 1 choice                                                                                                                      
[    3.628120] hub 1-0:1.0: USB hub found                                                                                                                                           
[    3.628130] hub 1-0:1.0: 8 ports detected                                                                                                                                        
[    3.628244] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                                                                               
[    3.628257] uhci_hcd: USB Universal Host Controller Interface driver                                                                                                             
[    3.628281] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20                                                                                                    
[    3.628290] uhci_hcd 0000:00:10.0: UHCI Host Controller                                                                                                                          
[    3.628328] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2                                                                                                 
[    3.628371] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000e000                                                                                                                    
[    3.628436] usb usb2: configuration #1 chosen from 1 choice                                                                                                                      
[    3.628461] hub 2-0:1.0: USB hub found                                                                                                                                           
[    3.628467] hub 2-0:1.0: 2 ports detected                                                                                                                                        
[    3.628534] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22                                                                                                    
[    3.628544] uhci_hcd 0000:00:10.1: UHCI Host Controller                                                                                                                          
[    3.628580] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3                                                                                                 
[    3.628621] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000dc00                                                                                                                    
[    3.628687] usb usb3: configuration #1 chosen from 1 choice                                                                                                                      
[    3.628707] hub 3-0:1.0: USB hub found                                                                                                                                           
[    3.628712] hub 3-0:1.0: 2 ports detected                                                                                                                                        
[    3.628783] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21                                                                                                    
[    3.628788] uhci_hcd 0000:00:10.2: UHCI Host Controller                                                                                                                          
[    3.628824] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4                                                                                                 
[    3.628842] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800                                                                                                                    
[    3.628905] usb usb4: configuration #1 chosen from 1 choice                                                                                                                      
[    3.628925] hub 4-0:1.0: USB hub found                                                                                                                                           
[    3.628930] hub 4-0:1.0: 2 ports detected                                                                                                                                        
[    3.629002] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23                                                                                                    
[    3.629010] uhci_hcd 0000:00:10.3: UHCI Host Controller                                                                                                                          
[    3.629043] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5                                                                                                 
[    3.629084] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000d400                                                                                                                    
[    3.629145] usb usb5: configuration #1 chosen from 1 choice                                                                                                                      
[    3.629165] hub 5-0:1.0: USB hub found                                                                                                                                           
[    3.629172] hub 5-0:1.0: 2 ports detected                                                                                                                                        
[    3.629290] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12                                                                                                              
[    3.629292] PNP: PS/2 controller doesn't have KBD irq; using default 1                                                                                                           
[    3.632431] serio: i8042 KBD port at 0x60,0x64 irq 1                                                                                                                             
[    3.632436] serio: i8042 AUX port at 0x60,0x64 irq 12                                                                                                                            
[    3.644078] mice: PS/2 mouse device common for all mice                                                                                                                          
[    3.692102] rtc_cmos 00:05: RTC can wake from S4                                                                                                                                 
[    3.692140] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0                                                                                                                
[    3.692193] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs                                                                                                         
[    3.692260] device-mapper: uevent: version 1.0.3                                                                                                                                 
[    3.692344] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]                                                                                     
[    3.692411] device-mapper: multipath: version 1.0.5 loaded                                                                                                                       
[    3.692414] device-mapper: multipath round-robin: version 1.0.0 loaded                                                                                                           
[    3.692502] cpuidle: using governor ladder                                                                                                                                       
[    3.692503] cpuidle: using governor menu                                                                                                                                         
[    3.692869] TCP cubic registered                                                                                                                                                 
[    3.692928] NET: Registered protocol family 10                                                                                                                                   
[    3.693279] lo: Disabled Privacy Extensions                                                                                                                                      
[    3.693527] NET: Registered protocol family 17                                                                                                                                   
[    3.693544] Bluetooth: L2CAP ver 2.11                                                                                                                                            
[    3.693546] Bluetooth: L2CAP socket layer initialized                                                                                                                            
[    3.693548] Bluetooth: SCO (Voice Link) ver 0.6                                                                                                                                  
[    3.693549] Bluetooth: SCO socket layer initialized                                                                                                                              
[    3.693575] Bluetooth: RFCOMM socket layer initialized                                                                                                                           
[    3.693584] Bluetooth: RFCOMM TTY layer initialized                                                                                                                              
[    3.693586] Bluetooth: RFCOMM ver 1.10                                                                                                                                           
[    3.695049] registered taskstats version 1                                                                                                                                       
[    3.695191]   Magic number: 5:632:396                                                                                                                                            
[    3.695284] rtc_cmos 00:05: setting system clock to 2009-08-09 20:23:57 UTC (1249849437)                                                                                         
[    3.695287] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                                                                                 
[    3.695288] EDD information not available.                                                                                                                                       
[    3.695323] Freeing unused kernel memory: 532k freed                                                                                                                             
[    3.695450] Write protecting the kernel read-only data: 6688k                                                                                                                    
[    3.751626] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    3.751681] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    3.751709] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    3.751739] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    3.751768] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    3.751826] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    3.751855] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    3.751884] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    3.896823] Floppy drive(s): fd0 is 1.44M                                                                                                                                        
[    3.920787] FDC 0 is a post-1991 82077                                                                                                                                           
[    3.941529] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded                                                                                                                      
[    3.941560] r8169 0000:04:07.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20                                                                                                       
[    3.941575] r8169 0000:04:07.0: PCI: Disallowing DAC for device                                                                                                                  
[    3.941605] r8169 0000:04:07.0: no PCI Express capability                                                                                                                        
[    3.942157] eth0: RTL8169sc/8110sc at 0xffffc2000007e000, 00:1a:92:31:80:4c, XID 18000000 IRQ 20                                                                                 
[    4.240515] usb 3-1: new low speed USB device using uhci_hcd and address 2                                                                                                       
[    4.326658] PM: Starting manual resume from disk                                                                                                                                 
[    4.326661] PM: Resume from partition 8:5                                                                                                                                        
[    4.326662] PM: Checking hibernation image.                                                                                                                                      
[    4.326829] PM: Resume from disk failed.                                                                                                                                         
[    4.334866] EXT4-fs: barriers enabled                                                                                                                                            
[    4.345145] kjournald2 starting.  Commit interval 5 seconds                                                                                                                      
[    4.345163] EXT4-fs: delayed allocation enabled                                                                                                                                  
[    4.345165] EXT4-fs: file extents enabled                                                                                                                                        
[    4.346034] EXT4-fs: mballoc enabled                                                                                                                                             
[    4.346038] EXT4-fs: mounted filesystem with ordered data mode.                                                                                                                  
[    4.401773] usb 3-1: configuration #1 chosen from 1 choice                                                                                                                       
[    4.644055] usb 3-2: new full speed USB device using uhci_hcd and address 3                                                                                                      
[    4.850773] usb 3-2: configuration #1 chosen from 1 choice                                                                                                                       
[    7.077367] __ratelimit: 3261 callbacks suppressed                                                                                                                               
[    7.077369] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    7.310047] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    7.320637] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    8.350018] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    8.430594] udev: starting version 141                                                                                                                                           
[    8.636322] input: PC Speaker as /devices/platform/pcspkr/input/input4                                                                                                           
[    8.742280] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume                                                                              
[    9.020064] parport_pc 00:0a: reported by Plug and Play ACPI                                                                                                                     
[    9.020147] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]                                                                                    
[    9.083941] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0904                                                                                     
[    9.083965] usbcore: registered new interface driver usblp                                                                                                                       
[    9.309183] nvidia: module license 'NVIDIA' taints kernel.                                                                                                                       
[    9.563777] nvidia 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24                                                                                                      
[    9.563787] nvidia 0000:02:00.0: setting latency timer to 64                                                                                                                     
[    9.564165] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009                                                                                 
[    9.572239] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4                                                                                                         
[    9.578191] ppdev: user-space parallel port driver                                                                                                                               
[    9.588834] agpgart: Detected VIA P4M890 chipset                                                                                                                                 
[    9.594481] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xd0000000                                                                                                          
[    9.615558] usbcore: registered new interface driver hiddev                                                                                                                      
[    9.628375] input: HID 0566:3108 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0/input/input5                                                                               
[    9.656439] generic-usb 0003:0566:3108.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 0566:3108] on usb-0000:00:10.1-1/input0                                                  
[    9.680057] input: HID 0566:3108 as /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.1/input/input6                                                                               
[    9.712215] generic-usb 0003:0566:3108.0002: input,hidraw1: USB HID v1.10 Device [HID 0566:3108] on usb-0000:00:10.1-1/input1                                                    
[    9.712245] usbcore: registered new interface driver usbhid                                                                                                                      
[    9.712266] usbhid: v2.6:USB HID core driver                                                                                                                                     
[    9.774152] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                                                                   
[    9.774240] HDA Intel 0000:80:01.0: setting latency timer to 64                                                                                                                  
[    9.774245] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device                                                                                                              
[    9.797360] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input7                                                                                     
[    9.879762] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    9.899490] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    9.909439] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    9.934786] lp0: using parport0 (interrupt-driven).                                                                                                                              
[    9.946625] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[    9.999201] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[   10.015023] Adding 2088376k swap on /dev/sda5.  Priority:-1 extents:1 across:2088376k                                                                                            
[   10.557502] EXT4 FS on sda3, internal journal on sda3:8                                                                                                                          
[   10.646089] do_IRQ: 0.91 No irq handler for vector                                                                                                                               
[   11.360317] kjournald starting.  Commit interval 5 seconds                                                                                                                       
[   11.364173] EXT3 FS on sda4, internal journal                                                                                                                                    
[   11.364179] EXT3-fs: mounted filesystem with ordered data mode.
[   12.364719] __ratelimit: 43 callbacks suppressed
[   12.364722] do_IRQ: 0.91 No irq handler for vector
[   12.364745] do_IRQ: 0.91 No irq handler for vector
[   12.724608] do_IRQ: 0.91 No irq handler for vector
[   12.895631] do_IRQ: 0.91 No irq handler for vector
[   12.895657] do_IRQ: 0.91 No irq handler for vector
[   13.059090] do_IRQ: 0.91 No irq handler for vector
[   13.589887] do_IRQ: 0.91 No irq handler for vector
[   13.589912] do_IRQ: 0.91 No irq handler for vector
[   13.608769] do_IRQ: 0.91 No irq handler for vector
[   14.105464] do_IRQ: 0.91 No irq handler for vector
[   15.453335] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.453338] Bluetooth: BNEP filters: protocol multicast
[   15.495211] Bridge firewalling registered
[   18.691102] ppdev0: registered pardevice
[   18.740613] ppdev0: unregistered pardevice
[   18.920605] __ratelimit: 62 callbacks suppressed
[   18.920608] do_IRQ: 0.91 No irq handler for vector
[   18.920629] do_IRQ: 0.91 No irq handler for vector
[   18.920658] do_IRQ: 0.91 No irq handler for vector
[   18.944941] do_IRQ: 0.91 No irq handler for vector
[   18.945228] do_IRQ: 0.91 No irq handler for vector
[   18.945431] do_IRQ: 0.91 No irq handler for vector
[   18.945839] do_IRQ: 0.91 No irq handler for vector
[   19.161710] do_IRQ: 0.91 No irq handler for vector
[   21.196757] r8169: eth0: link up
[   22.943803] do_IRQ: 0.91 No irq handler for vector
[   30.457740] CPU0 attaching NULL sched-domain.
[   30.457746] CPU1 attaching NULL sched-domain.
[   30.472077] CPU0 attaching sched-domain:
[   30.472081]  domain 0: span 0-1 level MC
[   30.472084]   groups: 0 1
[   30.472089] CPU1 attaching sched-domain:
[   30.472091]  domain 0: span 0-1 level MC
[   30.472093]   groups: 1 0
[   31.360007] eth0: no IPv6 routers present
[   36.006672] do_IRQ: 0.91 No irq handler for vector
[   48.105308] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   50.325037] do_IRQ: 0.91 No irq handler for vector
[   50.325059] do_IRQ: 0.91 No irq handler for vector
[   53.241806] do_IRQ: 0.91 No irq handler for vector
[   53.241856] do_IRQ: 0.91 No irq handler for vector
[   53.327950] do_IRQ: 0.91 No irq handler for vector
[   54.579994] do_IRQ: 0.91 No irq handler for vector
[   54.580806] do_IRQ: 0.91 No irq handler for vector
[   54.594205] do_IRQ: 0.91 No irq handler for vector
[   55.446774] do_IRQ: 0.91 No irq handler for vector
[   55.448078] do_IRQ: 0.91 No irq handler for vector
[   55.541347] do_IRQ: 0.91 No irq handler for vector
[   55.589649] do_IRQ: 0.91 No irq handler for vector
[   55.657587] do_IRQ: 0.91 No irq handler for vector
[   57.032300] do_IRQ: 0.91 No irq handler for vector
[   57.032615] do_IRQ: 0.91 No irq handler for vector
[   57.032702] do_IRQ: 0.91 No irq handler for vector
[   57.032730] do_IRQ: 0.91 No irq handler for vector
[   57.034127] do_IRQ: 0.91 No irq handler for vector

---

### Post by luisfpg on 2009-08-10
No one?
Could at least someone point me where to ask such a question?

---

### Post by JohanLingen on 2009-11-17
It seems to be related to the Asus P5VD2 motherboards, does that account for you, too?

Please refer to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/480997](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/480997)

---

### Post by luisfpg on 2009-11-17
Yeah, my one is a P5VD2-X.
I've tried to solve this issue in the kernel mailing list, but had no success: [http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-08/msg03954.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-08/msg03954.html)

---

### Post by Andur on 2009-11-25
**Solved**: The massive amount of entries in several logs occured after Installation of the ATI-Graphics Drivers on my PC...Its a bug on my VIA motherboard! :D

```
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: dfa00000-dfafffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [68] Power Management version 2
    Capabilities: [70] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
    Capabilities: [88] **HyperTransport: MSI Mapping Enable**- Fixed+
    Capabilities: [98] Subsystem: VIA Technologies, Inc. Device c323
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

```
To get rid of them, add a Kernel-Bootoption to your Grub-Bootloader. for Grub2 follow these steps:

1. sudo gedit /etc/default/grub
2. change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **pci=nomsi,noaer**"
3.sudo update-grub

:popcorn:and the syslog gets quiet and useable again...

---

### Post by luisfpg on 2009-12-23
Thank you so much for this tip!
Worked like a charm.
Hope the kernel devs manage to put this as default for these VIA chipsets...

---

### Post by guillermolisi on 2009-12-28
Thank you so much !!
I have two Asus P5VD2-X motherbords and this tip worked absolutely, with KK and Grub 1 in both cases.

---

### Post by Life On Mars on 2010-03-07
Thanks! 

I added 'quiet splash pci=nomsi,noaer' to default options in /boot/grub/menu.lst and it worked fine :-)

---

### Post by fallenshadow on 2010-11-16
Love you!! Got mine fixed too! :)  :KS

---

### Post by a3m-nix on 2011-02-05
thanks, work with my problem too... :p

---

