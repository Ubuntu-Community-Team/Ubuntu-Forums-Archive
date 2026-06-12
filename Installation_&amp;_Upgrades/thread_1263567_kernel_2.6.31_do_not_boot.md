---
title: "kernel 2.6.31 do not boot"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by litos on 2009-09-11
I had installed kernel 2.6.31 from http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31/ and this does not work

I use Acer TravelMate 4202 notebook

```
Sep 11 18:18:43 ls kernel: Inspecting /boot/System.map-2.6.31-020631-generic                                                 
Sep 11 18:18:43 ls kernel: Cannot find map file.                                                                             
Sep 11 18:18:43 ls kernel: Loaded 68830 symbols from 50 modules.                                                             
Sep 11 18:18:43 ls kernel: [    0.000000] Initializing cgroup subsys cpuset                                                  
Sep 11 18:18:43 ls kernel: [    0.000000] Initializing cgroup subsys cpu                                                     
Sep 11 18:18:43 ls kernel: [    0.000000] Linux version 2.6.31-020631-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #020631 SMP Thu Sep 10 22:34:46 UTC 2009                                                                            
Sep 11 18:18:43 ls kernel: [    0.000000] KERNEL supported cpus:                                                             
Sep 11 18:18:43 ls kernel: [    0.000000]   Intel GenuineIntel                                                               
Sep 11 18:18:43 ls kernel: [    0.000000]   AMD AuthenticAMD                                                                 
Sep 11 18:18:43 ls kernel: [    0.000000]   NSC Geode by NSC                                                                 
Sep 11 18:18:43 ls kernel: [    0.000000]   Cyrix CyrixInstead                                                               
Sep 11 18:18:43 ls kernel: [    0.000000]   Centaur CentaurHauls                                                             
Sep 11 18:18:43 ls kernel: [    0.000000]   Transmeta GenuineTMx86                                                           
Sep 11 18:18:43 ls kernel: [    0.000000]   Transmeta TransmetaCPU                                                           
Sep 11 18:18:43 ls kernel: [    0.000000]   UMC UMC UMC UMC                                                                  
Sep 11 18:18:43 ls kernel: [    0.000000] BIOS-provided physical RAM map:                                                    
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)                           
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001f680000 (usable)                           
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 000000001f680000 - 000000001f68b000 (ACPI data)                        
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 000000001f68b000 - 000000001f700000 (ACPI NVS)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)                         
Sep 11 18:18:43 ls kernel: [    0.000000] DMI present.                                                                       
Sep 11 18:18:43 ls kernel: [    0.000000] last_pfn = 0x1f680 max_arch_pfn = 0x100000                                         
Sep 11 18:18:43 ls kernel: [    0.000000] Scanning 1 areas for low memory corruption                                         
Sep 11 18:18:43 ls kernel: [    0.000000] modified physical RAM map:                                                         
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)                            
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)                            
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 0000000000100000 - 000000001f680000 (usable)                            
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 000000001f680000 - 000000001f68b000 (ACPI data)                         
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 000000001f68b000 - 000000001f700000 (ACPI NVS)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 000000001f700000 - 0000000020000000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)                          
Sep 11 18:18:43 ls kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001f680000                             
Sep 11 18:18:43 ls kernel: [    0.000000] RAMDISK: 1eeda000 - 1f66f257                                                       
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: RSDP 000f6570 00014 (v00 PTLTD )                                             
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: RSDT 1f684753 00040 (v01 PTLTD  Capell00 06040000  LTP 00000000)             
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: FACP 1f68ae20 00074 (v01 Acer   Grape    06040000 LOHR 0000005A)             
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: DSDT 1f68511b 05D05 (v01 Acer   CALISTGA 06040000 INTL 20050228)             
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: FACS 1f68bfc0 00040                                                          
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: APIC 1f68ae94 00068 (v01 Acer   Grape    06040000 LOHR 0000005A)             
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: HPET 1f68aefc 00038 (v01 Acer   Grape    06040000 LOHR 0000005A)             
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: MCFG 1f68af34 0003C (v01 Acer   Grape    06040000 LOHR 0000005A)             
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: APIC 1f68af70 00068 (v01 PTLTD  ^I APIC   06040000  LTP 00000000)            
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: BOOT 1f68afd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)             
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: SSDT 1f684793 004F6 (v01  PmRef    CpuPm 00003000 INTL 20050228)             
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0                                  
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org    
Sep 11 18:18:43 ls kernel: [    0.000000] 0MB HIGHMEM available.                                                             
Sep 11 18:18:43 ls kernel: [    0.000000] 502MB LOWMEM available.                                                            
Sep 11 18:18:43 ls kernel: [    0.000000]   mapped low ram: 0 - 1f680000                                                     
Sep 11 18:18:43 ls kernel: [    0.000000]   low ram: 0 - 1f680000                                                            
Sep 11 18:18:43 ls kernel: [    0.000000]   node 0 low ram: 00000000 - 1f680000                                              
Sep 11 18:18:43 ls kernel: [    0.000000]   node 0 bootmap 00008000 - 0000bed0                                               
Sep 11 18:18:43 ls kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f680000]                       
Sep 11 18:18:43 ls kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]      
Sep 11 18:18:43 ls kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]      
Sep 11 18:18:43 ls kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]      
Sep 11 18:18:43 ls kernel: [    0.000000]   #3 [0000100000 - 00008af040]    TEXT DATA BSS ==> [0000100000 - 00008af040]      
Sep 11 18:18:43 ls kernel: [    0.000000]   #4 [001eeda000 - 001f66f257]          RAMDISK ==> [001eeda000 - 001f66f257]      
Sep 11 18:18:43 ls kernel: [    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]      
Sep 11 18:18:43 ls kernel: [    0.000000]   #6 [00008b0000 - 00008b30f9]              BRK ==> [00008b0000 - 00008b30f9]      
Sep 11 18:18:43 ls kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]      
Sep 11 18:18:43 ls kernel: [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]      
Sep 11 18:18:43 ls kernel: [    0.000000] found SMP MP-table at [c00f6620] f6620                                             
Sep 11 18:18:43 ls kernel: [    0.000000] Zone PFN ranges:                                                                   
Sep 11 18:18:43 ls kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000                                                
Sep 11 18:18:43 ls kernel: [    0.000000]   Normal   0x00001000 -> 0x0001f680                                                
Sep 11 18:18:43 ls kernel: [    0.000000]   HighMem  0x0001f680 -> 0x0001f680                                                
Sep 11 18:18:43 ls kernel: [    0.000000] Movable zone start PFN for each node                                               
Sep 11 18:18:43 ls kernel: [    0.000000] early_node_map[3] active PFN ranges                                                
Sep 11 18:18:43 ls kernel: [    0.000000]     0: 0x00000000 -> 0x00000002                                                    
Sep 11 18:18:43 ls kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f                                                    
Sep 11 18:18:43 ls kernel: [    0.000000]     0: 0x00000100 -> 0x0001f680                                                    
Sep 11 18:18:43 ls kernel: [    0.000000] Using APIC driver default                                                          
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008                                                     
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)                                 
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)                                 
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])                                
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])                                
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])                            
Sep 11 18:18:43 ls kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23                     
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                           
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                        
Sep 11 18:18:43 ls kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                                      
Sep 11 18:18:43 ls kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information                                
Sep 11 18:18:43 ls kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000                                         
Sep 11 18:18:43 ls kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs                                               
Sep 11 18:18:43 ls kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000                  
Sep 11 18:18:43 ls kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000                  
Sep 11 18:18:43 ls kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000                  
Sep 11 18:18:43 ls kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000                  
Sep 11 18:18:43 ls kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)             
Sep 11 18:18:43 ls kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1                             
Sep 11 18:18:43 ls kernel: [    0.000000] PERCPU: Embedded 14 pages at c13f2000, static data 35004 bytes                     
Sep 11 18:18:43 ls kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127534        
Sep 11 18:18:43 ls kernel: [    0.000000] Kernel command line: root=UUID=0ea55185-e1d0-4375-8366-c082f92ef79d ro quiet splash                                                                                                                             
Sep 11 18:18:43 ls kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)                               
Sep 11 18:18:43 ls kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)                    
Sep 11 18:18:43 ls kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)                     
Sep 11 18:18:43 ls kernel: [    0.000000] Enabling fast FPU save and restore... done.                                        
Sep 11 18:18:43 ls kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.                              
Sep 11 18:18:43 ls kernel: [    0.000000] Initializing CPU#0                                                                 
Sep 11 18:18:43 ls kernel: [    0.000000] allocated 2572800 bytes of page_cgroup                                             
Sep 11 18:18:43 ls kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups         
Sep 11 18:18:43 ls kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)                                
Sep 11 18:18:43 ls kernel: [    0.000000] Memory: 491128k/514560k available (4530k kernel code, 22752k reserved, 2179k data, 568k init, 0k highmem)                                                                                                       
Sep 11 18:18:43 ls kernel: [    0.000000] virtual kernel memory layout:                                                      
Sep 11 18:18:43 ls kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)                                  
Sep 11 18:18:43 ls kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)                                  
Sep 11 18:18:43 ls kernel: [    0.000000]     vmalloc : 0xdfe80000 - 0xff7fe000   ( 505 MB)                                  
Sep 11 18:18:43 ls kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdf680000   ( 502 MB)                                  
Sep 11 18:18:43 ls kernel: [    0.000000]       .init : 0xc078e000 - 0xc081c000   ( 568 kB)                                  
Sep 11 18:18:43 ls kernel: [    0.000000]       .data : 0xc056c9b5 - 0xc078d708   (2179 kB)                                  
Sep 11 18:18:43 ls kernel: [    0.000000]       .text : 0xc0100000 - 0xc056c9b5   (4530 kB)                                  
Sep 11 18:18:43 ls kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.        
Sep 11 18:18:43 ls kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1            
Sep 11 18:18:43 ls kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424                                                           
Sep 11 18:18:43 ls kernel: [    0.000000] Fast TSC calibration using PIT                                                     
Sep 11 18:18:43 ls kernel: [    0.000000] Detected 1662.579 MHz processor.                                                   
Sep 11 18:18:43 ls kernel: [    0.001511] Console: colour VGA+ 80x25                                                         
Sep 11 18:18:43 ls kernel: [    0.001517] console [tty0] enabled                                                             
Sep 11 18:18:43 ls kernel: [    0.001750] HPET: 3 timers in total, 0 timers will be used for per-cpu timer                   
Sep 11 18:18:43 ls kernel: [    0.001759] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.15 BogoMIPS (lpj=6650316)                                                                                                       
Sep 11 18:18:43 ls kernel: [    0.001791] Security Framework initialized                                                     
Sep 11 18:18:43 ls kernel: [    0.001802] SELinux:  Disabled at boot.                                                        
Sep 11 18:18:43 ls kernel: [    0.001816] Mount-cache hash table entries: 512                                                
Sep 11 18:18:43 ls kernel: [    0.002041] Initializing cgroup subsys ns                                                      
Sep 11 18:18:43 ls kernel: [    0.002049] Initializing cgroup subsys cpuacct                                                 
Sep 11 18:18:43 ls kernel: [    0.002057] Initializing cgroup subsys memory                                                  
Sep 11 18:18:43 ls kernel: [    0.002070] Initializing cgroup subsys freezer                                                 
Sep 11 18:18:43 ls kernel: [    0.002074] Initializing cgroup subsys net_cls                                                 
Sep 11 18:18:43 ls kernel: [    0.002098] CPU: L1 I cache: 32K, L1 D cache: 32K                                              
Sep 11 18:18:43 ls kernel: [    0.002104] CPU: L2 cache: 2048K                                                               
Sep 11 18:18:43 ls kernel: [    0.002109] CPU: Physical Processor ID: 0                                                      
Sep 11 18:18:43 ls kernel: [    0.002113] CPU: Processor Core ID: 0                                                          
Sep 11 18:18:43 ls kernel: [    0.002121] using mwait in idle threads.                                                       
Sep 11 18:18:43 ls kernel: [    0.002131] Performance Counters: no PMU driver, software counters only.                       
Sep 11 18:18:43 ls kernel: [    0.002140] Checking 'hlt' instruction... OK.                                                  
Sep 11 18:18:43 ls kernel: [    0.021944] ACPI: Core revision 20090521                                                       
Sep 11 18:18:43 ls kernel: [    0.040497] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                               
Sep 11 18:18:43 ls kernel: [    0.081869] CPU0: Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08                  
Sep 11 18:18:43 ls kernel: [    0.084001] Booting processor 1 APIC 0x1 ip 0x6000                                             
Sep 11 18:18:43 ls kernel: [    0.004000] Initializing CPU#1                                                                 
Sep 11 18:18:43 ls kernel: [    0.004000] Calibrating delay using timer specific routine.. 3325.10 BogoMIPS (lpj=6650219)    
Sep 11 18:18:43 ls kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K                                              
Sep 11 18:18:43 ls kernel: [    0.004000] CPU: L2 cache: 2048K                                                               
Sep 11 18:18:43 ls kernel: [    0.004000] CPU: Physical Processor ID: 0                                                      
Sep 11 18:18:43 ls kernel: [    0.004000] CPU: Processor Core ID: 1                                                          
Sep 11 18:18:43 ls kernel: [    0.168914] CPU1: Genuine Intel(R) CPU           T2300  @ 1.66GHz stepping 08                  
Sep 11 18:18:43 ls kernel: [    0.168942] checking TSC synchronization [CPU#0 -> CPU#1]: passed.                             
Sep 11 18:18:43 ls kernel: [    0.172036] Brought up 2 CPUs                                                                  
Sep 11 18:18:43 ls kernel: [    0.172043] Total of 2 processors activated (6650.26 BogoMIPS).                                
Sep 11 18:18:43 ls kernel: [    0.172302] Booting paravirtualized kernel on bare hardware                                    
Sep 11 18:18:43 ls kernel: [    0.172394] regulator: core version 0.5                                                        
Sep 11 18:18:43 ls kernel: [    0.172394] Time:  9:18:26  Date: 09/11/09                                                     
Sep 11 18:18:43 ls kernel: [    0.172394] NET: Registered protocol family 16                                                 
Sep 11 18:18:43 ls kernel: [    0.172394] EISA bus registered                                                                
Sep 11 18:18:43 ls kernel: [    0.172394] ACPI: bus type pci registered                                                      
Sep 11 18:18:43 ls kernel: [    0.176026] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                   
Sep 11 18:18:43 ls kernel: [    0.176033] PCI: MCFG area at e0000000 reserved in E820                                        
Sep 11 18:18:43 ls kernel: [    0.176037] PCI: Using MMCONFIG for extended config space                                      
Sep 11 18:18:43 ls kernel: [    0.176042] PCI: Using configuration type 1 for base access                                    
Sep 11 18:18:43 ls kernel: [    0.184169] bio: create slab <bio-0> at 0                                                      
Sep 11 18:18:43 ls kernel: [    0.195896] ACPI: BIOS _OSI(Linux) query ignored                                               
Sep 11 18:18:43 ls kernel: [    0.197330] ACPI: Interpreter enabled                                                          
Sep 11 18:18:43 ls kernel: [    0.197343] ACPI: (supports S0 S3 S4 S5)                                                       
Sep 11 18:18:43 ls kernel: [    0.197385] ACPI: Using IOAPIC for interrupt routing                                           
Sep 11 18:18:43 ls kernel: [    0.204249] ACPI: EC: non-query interrupt received, switching to interrupt mode                
Sep 11 18:18:43 ls kernel: [    0.233878] ACPI: EC: GPE storm detected, transactions will use polling mode                   
Sep 11 18:18:43 ls kernel: [    0.268670] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62                      
Sep 11 18:18:43 ls kernel: [    0.268670] ACPI: EC: driver started in poll mode                                              
Sep 11 18:18:43 ls kernel: [    0.268670] ACPI: No dock devices found.                                                       
Sep 11 18:18:43 ls kernel: [    0.272739] ACPI: PCI Root Bridge [PCI0] (0000:00)                                             
Sep 11 18:18:43 ls kernel: [    0.272800] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold                              
Sep 11 18:18:43 ls kernel: [    0.272800] pci 0000:00:1b.0: PME# disabled                                                    
Sep 11 18:18:43 ls kernel: [    0.272800] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold                              
Sep 11 18:18:43 ls kernel: [    0.272800] pci 0000:00:1c.0: PME# disabled                                                    
Sep 11 18:18:43 ls kernel: [    0.272800] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold                              
Sep 11 18:18:43 ls kernel: [    0.272800] pci 0000:00:1c.1: PME# disabled                                                    
Sep 11 18:18:43 ls kernel: [    0.272849] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold                              
Sep 11 18:18:43 ls kernel: [    0.272857] pci 0000:00:1c.2: PME# disabled                                                    
Sep 11 18:18:43 ls kernel: [    0.272977] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold                              
Sep 11 18:18:43 ls kernel: [    0.272986] pci 0000:00:1c.3: PME# disabled                                                    
Sep 11 18:18:43 ls kernel: [    0.273518] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold                              
Sep 11 18:18:43 ls kernel: [    0.273527] pci 0000:00:1d.7: PME# disabled                                                    
Sep 11 18:18:43 ls kernel: [    0.273748] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO            
Sep 11 18:18:43 ls kernel: [    0.273757] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO                     
Sep 11 18:18:43 ls kernel: [    0.273768] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff20 (mask 000f)             
Sep 11 18:18:43 ls kernel: [    0.274750] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold                              
Sep 11 18:18:43 ls kernel: [    0.274766] pci 0000:05:00.0: PME# disabled                                                    
Sep 11 18:18:43 ls kernel: [    0.275059] pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold                        
Sep 11 18:18:43 ls kernel: [    0.275068] pci 0000:06:01.0: PME# disabled                                                    
Sep 11 18:18:43 ls kernel: [    0.276030] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold                        
Sep 11 18:18:43 ls kernel: [    0.276040] pci 0000:06:04.0: PME# disabled                                                    
Sep 11 18:18:43 ls kernel: [    0.276109] pci 0000:00:1e.0: transparent bridge                                               
Sep 11 18:18:43 ls kernel: [    0.284371] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 5 *6 10 12 14 15)                          
Sep 11 18:18:43 ls kernel: [    0.284375] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 5 6 *11 12 14 15)                          
Sep 11 18:18:43 ls kernel: [    0.284573] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 5 6 10 12 14 15) *11                       
Sep 11 18:18:43 ls kernel: [    0.284772] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 5 6 11 12 14 15) *10                       
Sep 11 18:18:43 ls kernel: [    0.284971] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 5 6 10 12 14 15) *0, disabled.             
Sep 11 18:18:43 ls kernel: [    0.285171] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 5 6 11 12 14 15) *10                       
Sep 11 18:18:43 ls kernel: [    0.285370] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 5 6 *10 12 14 15)                          
Sep 11 18:18:43 ls kernel: [    0.285568] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *5 6 11 12 14 15)                          
Sep 11 18:18:43 ls kernel: [    0.288049] SCSI subsystem initialized                                                         
Sep 11 18:18:43 ls kernel: [    0.288067] usbcore: registered new interface driver usbfs                                     
Sep 11 18:18:43 ls kernel: [    0.288067] usbcore: registered new interface driver hub                                       
Sep 11 18:18:43 ls kernel: [    0.288067] usbcore: registered new device driver usb                                          
Sep 11 18:18:43 ls kernel: [    0.288203] ACPI: WMI: Mapper loaded                                                           
Sep 11 18:18:43 ls kernel: [    0.288203] PCI: Using ACPI for IRQ routing                                                    
Sep 11 18:18:43 ls kernel: [    0.288203] pci 0000:00:1c.0: BAR 13: can't allocate resource                                  
Sep 11 18:18:43 ls kernel: [    0.288203] pci 0000:00:1c.0: BAR 14: can't allocate resource                                  
Sep 11 18:18:43 ls kernel: [    0.304015] Bluetooth: Core ver 2.15                                                           
Sep 11 18:18:43 ls kernel: [    0.304049] NET: Registered protocol family 31                                                 
Sep 11 18:18:43 ls kernel: [    0.304051] Bluetooth: HCI device and connection manager initialized                           
Sep 11 18:18:43 ls kernel: [    0.304058] Bluetooth: HCI socket layer initialized                                            
Sep 11 18:18:43 ls kernel: [    0.304062] NetLabel: Initializing                                                             
Sep 11 18:18:43 ls kernel: [    0.304066] NetLabel:  domain hash size = 128                                                  
Sep 11 18:18:43 ls kernel: [    0.304069] NetLabel:  protocols = UNLABELED CIPSOv4                                           
Sep 11 18:18:43 ls kernel: [    0.304100] NetLabel:  unlabeled traffic allowed by default                                    
Sep 11 18:18:43 ls kernel: [    0.304124] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0                                            
Sep 11 18:18:43 ls kernel: [    0.304124] hpet0: 3 comparators, 64-bit 14.318180 MHz counter                                 
Sep 11 18:18:43 ls kernel: [    0.328017] pnp: PnP ACPI init                                                                 
Sep 11 18:18:43 ls kernel: [    0.328039] ACPI: bus type pnp registered                                                      
Sep 11 18:18:43 ls kernel: [    0.405860] pnp: PnP ACPI: found 10 devices                                                    
Sep 11 18:18:43 ls kernel: [    0.405866] ACPI: ACPI bus type pnp unregistered                                               
Sep 11 18:18:43 ls kernel: [    0.405872] PnPBIOS: Disabled by ACPI PNP                                                      
Sep 11 18:18:43 ls kernel: [    0.405896] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved                  
Sep 11 18:18:43 ls kernel: [    0.405903] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved                  
Sep 11 18:18:43 ls kernel: [    0.405910] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved                  
Sep 11 18:18:43 ls kernel: [    0.405917] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved                  
Sep 11 18:18:43 ls kernel: [    0.405924] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved                  
Sep 11 18:18:43 ls kernel: [    0.405931] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved                  
Sep 11 18:18:43 ls kernel: [    0.405946] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved                  
Sep 11 18:18:43 ls kernel: [    0.405961] system 00:06: ioport range 0x800-0x80f has been reserved                           
Sep 11 18:18:43 ls kernel: [    0.405968] system 00:06: ioport range 0x1000-0x107f has been reserved                         
Sep 11 18:18:43 ls kernel: [    0.405975] system 00:06: ioport range 0x1180-0x11bf has been reserved                         
Sep 11 18:18:43 ls kernel: [    0.405981] system 00:06: ioport range 0x1640-0x164f has been reserved                         
Sep 11 18:18:43 ls kernel: [    0.405988] system 00:06: ioport range 0xff2c-0xff2f has been reserved                         
Sep 11 18:18:43 ls kernel: [    0.441711] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02                                
Sep 11 18:18:43 ls kernel: [    0.441716] pci 0000:00:1c.0:   IO window: disabled                                            
Sep 11 18:18:43 ls kernel: [    0.441726] pci 0000:00:1c.0:   MEM window: disabled                                           
Sep 11 18:18:43 ls kernel: [    0.441734] pci 0000:00:1c.0:   PREFETCH window: disabled                                      
Sep 11 18:18:43 ls kernel: [    0.441742] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03                                
Sep 11 18:18:43 ls kernel: [    0.441747] pci 0000:00:1c.1:   IO window: disabled                                            
Sep 11 18:18:43 ls kernel: [    0.441756] pci 0000:00:1c.1:   MEM window: disabled                                           
Sep 11 18:18:43 ls kernel: [    0.441764] pci 0000:00:1c.1:   PREFETCH window: disabled                                      
Sep 11 18:18:43 ls kernel: [    0.441773] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04                                
Sep 11 18:18:43 ls kernel: [    0.441778] pci 0000:00:1c.2:   IO window: disabled                                            
Sep 11 18:18:43 ls kernel: [    0.441787] pci 0000:00:1c.2:   MEM window: disabled                                           
Sep 11 18:18:43 ls kernel: [    0.441794] pci 0000:00:1c.2:   PREFETCH window: disabled                                      
Sep 11 18:18:43 ls kernel: [    0.441803] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05                                
Sep 11 18:18:43 ls kernel: [    0.441808] pci 0000:00:1c.3:   IO window: disabled                                            
Sep 11 18:18:43 ls kernel: [    0.441819] pci 0000:00:1c.3:   MEM window: 0xd0100000-0xd01fffff                              
Sep 11 18:18:43 ls kernel: [    0.441827] pci 0000:00:1c.3:   PREFETCH window: disabled                                      
Sep 11 18:18:43 ls kernel: [    0.441840] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07                            
Sep 11 18:18:43 ls kernel: [    0.441846] pci 0000:06:04.0:   IO window: 0x002000-0x0020ff                                   
Sep 11 18:18:43 ls kernel: [    0.441855] pci 0000:06:04.0:   IO window: 0x002400-0x0024ff                                   
Sep 11 18:18:43 ls kernel: [    0.441865] pci 0000:06:04.0:   PREFETCH window: 0x20000000-0x23ffffff                         
Sep 11 18:18:43 ls kernel: [    0.441874] pci 0000:06:04.0:   MEM window: 0x24000000-0x27ffffff                              
Sep 11 18:18:43 ls kernel: [    0.441884] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06                                
Sep 11 18:18:43 ls kernel: [    0.441891] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff                                       
Sep 11 18:18:43 ls kernel: [    0.441901] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd00fffff                              
Sep 11 18:18:43 ls kernel: [    0.441910] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff                         
Sep 11 18:18:43 ls kernel: [    0.441946] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                       
Sep 11 18:18:43 ls kernel: [    0.441984] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16                       
Sep 11 18:18:43 ls kernel: [    0.442018] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                       
Sep 11 18:18:43 ls kernel: [    0.442052] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19                       
Sep 11 18:18:43 ls kernel: [    0.442071] pci 0000:00:1e.0: enabling device (0004 -> 0007)                                   
Sep 11 18:18:43 ls kernel: [    0.442097] pci 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                       
Sep 11 18:18:43 ls kernel: [    0.442264] NET: Registered protocol family 2                                                  
Sep 11 18:18:43 ls kernel: [    0.442461] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)                    
Sep 11 18:18:43 ls kernel: [    0.443052] TCP established hash table entries: 16384 (order: 5, 131072 bytes)                 
Sep 11 18:18:43 ls kernel: [    0.443270] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)                        
Sep 11 18:18:43 ls kernel: [    0.443462] TCP: Hash tables configured (established 16384 bind 16384)                         
Sep 11 18:18:43 ls kernel: [    0.443467] TCP reno registered                                                                
Sep 11 18:18:43 ls kernel: [    0.443590] NET: Registered protocol family 1                                                  
Sep 11 18:18:43 ls kernel: [    0.443692] Trying to unpack rootfs image as initramfs...                                      
Sep 11 18:18:43 ls kernel: [    0.900758] Freeing initrd memory: 7764k freed                                                 
Sep 11 18:18:43 ls kernel: [    0.906579] Simple Boot Flag at 0x36 set to 0x1                                                
Sep 11 18:18:43 ls kernel: [    0.907456] cpufreq-nforce2: No nForce2 chipset.                                               
Sep 11 18:18:43 ls kernel: [    0.907715] Scanning for low memory corruption every 60 seconds                                
Sep 11 18:18:43 ls kernel: [    0.908285] audit: initializing netlink socket (disabled)                                      
Sep 11 18:18:43 ls kernel: [    0.908308] type=2000 audit(1252660706.905:1): initialized                                     
Sep 11 18:18:43 ls kernel: [    0.931213] HugeTLB registered 4 MB page size, pre-allocated 0 pages                           
Sep 11 18:18:43 ls kernel: [    0.938151] VFS: Disk quotas dquot_6.5.2                                                       
Sep 11 18:18:43 ls kernel: [    0.938348] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                         
Sep 11 18:18:43 ls kernel: [    0.940379] fuse init (API version 7.12)                                                       
Sep 11 18:18:43 ls kernel: [    0.940767] msgmni has been set to 974                                                         
Sep 11 18:18:43 ls kernel: [    0.941280] alg: No test for stdrng (krng)                                                     
Sep 11 18:18:43 ls kernel: [    0.941303] io scheduler noop registered                                                       
Sep 11 18:18:43 ls kernel: [    0.941309] io scheduler anticipatory registered                                               
Sep 11 18:18:43 ls kernel: [    0.941314] io scheduler deadline registered                                                   
Sep 11 18:18:43 ls kernel: [    0.941469] io scheduler cfq registered (default)                                              
Sep 11 18:18:43 ls kernel: [    2.544014] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001                   
Sep 11 18:18:43 ls kernel: [    2.546464] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                    
Sep 11 18:18:43 ls kernel: [    2.546929] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                        
Sep 11 18:18:43 ls kernel: [    2.600204] ACPI: AC Adapter [ACAD] (on-line)                                                  
Sep 11 18:18:43 ls kernel: [    2.600469] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0               
Sep 11 18:18:43 ls kernel: [    2.600476] ACPI: Power Button [PWRF]                                                          
Sep 11 18:18:43 ls kernel: [    2.600645] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1        
Sep 11 18:18:43 ls kernel: [    2.600724] ACPI: Lid Switch [LID]                                                             
Sep 11 18:18:43 ls kernel: [    2.600901] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2      
Sep 11 18:18:43 ls kernel: [    2.600907] ACPI: Sleep Button [SLPB]                                                          
Sep 11 18:18:43 ls kernel: [    2.601080] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3      
Sep 11 18:18:43 ls kernel: [    2.601086] ACPI: Power Button [PWRB]                                                          
Sep 11 18:18:43 ls kernel: [    2.602475] ACPI: SSDT 1f684eea 001A8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050228)             
Sep 11 18:18:43 ls kernel: [    2.603268] ACPI: SSDT 1f684c89 001DC (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)             
Sep 11 18:18:43 ls kernel: [    2.603985] Marking TSC unstable due to TSC halts in idle                                      
Sep 11 18:18:43 ls kernel: [    2.604104] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])                                    
Sep 11 18:18:43 ls kernel: [    2.604223] processor LNXCPU:00: registered as cooling_device0                                 
Sep 11 18:18:43 ls kernel: [    2.604232] ACPI: Processor [CPU0] (supports 8 throttling states)                              
Sep 11 18:18:43 ls kernel: [    2.604926] ACPI: SSDT 1f685092 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050228)             
Sep 11 18:18:43 ls kernel: [    2.605627] ACPI: SSDT 1f684e65 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050228)             
Sep 11 18:18:43 ls kernel: [    2.606560] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])                                    
Sep 11 18:18:43 ls kernel: [    2.606672] processor LNXCPU:01: registered as cooling_device1                                 
Sep 11 18:18:43 ls kernel: [    2.606682] ACPI: Processor [CPU1] (supports 8 throttling states)                              
Sep 11 18:18:43 ls kernel: [    2.792116] thermal LNXTHERM:01: registered as thermal_zone0                                   
Sep 11 18:18:43 ls kernel: [    2.792134] ACPI: Thermal Zone [TZ00] (47 C)                                                   
Sep 11 18:18:43 ls kernel: [    2.793017] thermal LNXTHERM:02: registered as thermal_zone1                                   
Sep 11 18:18:43 ls kernel: [    2.793035] ACPI: Thermal Zone [TZ01] (50 C)                                                   
Sep 11 18:18:43 ls kernel: [    2.793380] isapnp: Scanning for PnP cards...                                                  
Sep 11 18:18:43 ls kernel: [    3.147828] isapnp: No Plug & Play device found                                                
Sep 11 18:18:43 ls kernel: [    4.040183] ACPI: Battery Slot [BAT1] (battery present)                                        
Sep 11 18:18:43 ls kernel: [    4.040543] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled                            
Sep 11 18:18:43 ls kernel: [    4.046054] brd: module loaded                                                                 
Sep 11 18:18:43 ls kernel: [    4.048073] loop: module loaded                                                                
Sep 11 18:18:43 ls kernel: [    4.048432] input: Macintosh mouse button emulation as /devices/virtual/input/input4           
Sep 11 18:18:43 ls kernel: [    4.049091] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19                  
Sep 11 18:18:43 ls kernel: [    4.049279] scsi0 : ata_piix                                                                   
Sep 11 18:18:43 ls kernel: [    4.049584] scsi1 : ata_piix                                                                   
Sep 11 18:18:43 ls kernel: [    4.050963] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14                    
Sep 11 18:18:43 ls kernel: [    4.050970] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15                    
Sep 11 18:18:43 ls kernel: [    4.058285] Fixed MDIO Bus: probed                                                             
Sep 11 18:18:43 ls kernel: [    4.058623] PPP generic driver version 2.4.2                                                   
Sep 11 18:18:43 ls kernel: [    4.059091] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                         
Sep 11 18:18:43 ls kernel: [    4.059150] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23                  
Sep 11 18:18:43 ls kernel: [    4.059181] ehci_hcd 0000:00:1d.7: EHCI Host Controller                                        
Sep 11 18:18:43 ls kernel: [    4.059344] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1               
Sep 11 18:18:43 ls kernel: [    4.063273] ehci_hcd 0000:00:1d.7: debug port 1                                                
Sep 11 18:18:43 ls kernel: [    4.063311] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0544000                                   
Sep 11 18:18:43 ls kernel: [    4.077022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00                                  
Sep 11 18:18:43 ls kernel: [    4.077238] usb usb1: configuration #1 chosen from 1 choice                                    
Sep 11 18:18:43 ls kernel: [    4.077367] hub 1-0:1.0: USB hub found                                                         
Sep 11 18:18:43 ls kernel: [    4.077381] hub 1-0:1.0: 8 ports detected                                                      
Sep 11 18:18:43 ls kernel: [    4.077583] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                             
Sep 11 18:18:43 ls kernel: [    4.077683] uhci_hcd: USB Universal Host Controller Interface driver                           
Sep 11 18:18:43 ls kernel: [    4.077737] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23                  
Sep 11 18:18:43 ls kernel: [    4.077756] uhci_hcd 0000:00:1d.0: UHCI Host Controller                                        
Sep 11 18:18:43 ls kernel: [    4.077885] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2               
Sep 11 18:18:43 ls kernel: [    4.077922] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820                                  
Sep 11 18:18:43 ls kernel: [    4.078145] usb usb2: configuration #1 chosen from 1 choice                                    
Sep 11 18:18:43 ls kernel: [    4.078267] hub 2-0:1.0: USB hub found                                                         
Sep 11 18:18:43 ls kernel: [    4.078280] hub 2-0:1.0: 2 ports detected                                                      
Sep 11 18:18:43 ls kernel: [    4.078376] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19                  
Sep 11 18:18:43 ls kernel: [    4.078395] uhci_hcd 0000:00:1d.1: UHCI Host Controller                                        
Sep 11 18:18:43 ls kernel: [    4.078535] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3               
Sep 11 18:18:43 ls kernel: [    4.078583] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840                                  
Sep 11 18:18:43 ls kernel: [    4.078805] usb usb3: configuration #1 chosen from 1 choice                                    
Sep 11 18:18:43 ls kernel: [    4.078933] hub 3-0:1.0: USB hub found                                                         
Sep 11 18:18:43 ls kernel: [    4.078946] hub 3-0:1.0: 2 ports detected                                                      
Sep 11 18:18:43 ls kernel: [    4.079037] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                  
Sep 11 18:18:43 ls kernel: [    4.079055] uhci_hcd 0000:00:1d.2: UHCI Host Controller                                        
Sep 11 18:18:43 ls kernel: [    4.079187] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4               
Sep 11 18:18:43 ls kernel: [    4.079235] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860                                  
Sep 11 18:18:43 ls kernel: [    4.079456] usb usb4: configuration #1 chosen from 1 choice                                    
Sep 11 18:18:43 ls kernel: [    4.079585] hub 4-0:1.0: USB hub found                                                         
Sep 11 18:18:43 ls kernel: [    4.079599] hub 4-0:1.0: 2 ports detected                                                      
Sep 11 18:18:43 ls kernel: [    4.079692] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16                  
Sep 11 18:18:43 ls kernel: [    4.079710] uhci_hcd 0000:00:1d.3: UHCI Host Controller                                        
Sep 11 18:18:43 ls kernel: [    4.079839] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5               
Sep 11 18:18:43 ls kernel: [    4.079886] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880                                  
Sep 11 18:18:43 ls kernel: [    4.080116] usb usb5: configuration #1 chosen from 1 choice                                    
Sep 11 18:18:43 ls kernel: [    4.080240] hub 5-0:1.0: USB hub found                                                         
Sep 11 18:18:43 ls kernel: [    4.080254] hub 5-0:1.0: 2 ports detected                                                      
Sep 11 18:18:43 ls kernel: [    4.080650] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12             
Sep 11 18:18:43 ls kernel: [    4.081198] i8042.c: Detected active multiplexing controller, rev 1.1.                         
Sep 11 18:18:43 ls kernel: [    4.081301] serio: i8042 KBD port at 0x60,0x64 irq 1                                           
Sep 11 18:18:43 ls kernel: [    4.081312] serio: i8042 AUX0 port at 0x60,0x64 irq 12                                         
Sep 11 18:18:43 ls kernel: [    4.081321] serio: i8042 AUX1 port at 0x60,0x64 irq 12                                         
Sep 11 18:18:43 ls kernel: [    4.081327] serio: i8042 AUX2 port at 0x60,0x64 irq 12                                         
Sep 11 18:18:43 ls kernel: [    4.081334] serio: i8042 AUX3 port at 0x60,0x64 irq 12                                         
Sep 11 18:18:43 ls kernel: [    4.081848] mice: PS/2 mouse device common for all mice                                        
Sep 11 18:18:43 ls kernel: [    4.082608] rtc_cmos 00:07: RTC can wake from S4                                               
Sep 11 18:18:43 ls kernel: [    4.082758] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0                              
Sep 11 18:18:43 ls kernel: [    4.082800] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs                      
Sep 11 18:18:43 ls kernel: [    4.083266] device-mapper: uevent: version 1.0.3                                               
Sep 11 18:18:43 ls kernel: [    4.083578] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com   
Sep 11 18:18:43 ls kernel: [    4.083710] device-mapper: multipath: version 1.1.0 loaded                                     
Sep 11 18:18:43 ls kernel: [    4.083716] device-mapper: multipath round-robin: version 1.0.0 loaded                         
Sep 11 18:18:43 ls kernel: [    4.084178] EISA: Probing bus 0 at eisa.0                                                      
Sep 11 18:18:43 ls kernel: [    4.084190] Cannot allocate resource for EISA slot 1                                           
Sep 11 18:18:43 ls kernel: [    4.084195] Cannot allocate resource for EISA slot 2                                           
Sep 11 18:18:43 ls kernel: [    4.084230] EISA: Detected 0 cards.                                                            
Sep 11 18:18:43 ls kernel: [    4.085236] cpuidle: using governor ladder                                                     
Sep 11 18:18:43 ls kernel: [    4.085288] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5 
Sep 11 18:18:43 ls kernel: [    4.086808] cpuidle: using governor menu                                                       
Sep 11 18:18:43 ls kernel: [    4.088387] TCP cubic registered                                                               
Sep 11 18:18:43 ls kernel: [    4.089224] NET: Registered protocol family 10                                                 
Sep 11 18:18:43 ls kernel: [    4.090197] lo: Disabled Privacy Extensions                                                    
Sep 11 18:18:43 ls kernel: [    4.090961] NET: Registered protocol family 17                                                 
Sep 11 18:18:43 ls kernel: [    4.091107] Bluetooth: L2CAP ver 2.13                                                          
Sep 11 18:18:43 ls kernel: [    4.091111] Bluetooth: L2CAP socket layer initialized                                          
Sep 11 18:18:43 ls kernel: [    4.091117] Bluetooth: SCO (Voice Link) ver 0.6                                                
Sep 11 18:18:43 ls kernel: [    4.091120] Bluetooth: SCO socket layer initialized                                            
Sep 11 18:18:43 ls kernel: [    4.091170] Bluetooth: RFCOMM TTY layer initialized                                            
Sep 11 18:18:43 ls kernel: [    4.091176] Bluetooth: RFCOMM socket layer initialized                                         
Sep 11 18:18:43 ls kernel: [    4.091180] Bluetooth: RFCOMM ver 1.11                                                         
Sep 11 18:18:43 ls kernel: [    4.091965] Using IPI No-Shortcut mode                                                         
Sep 11 18:18:43 ls kernel: [    4.092320] registered taskstats version 1                                                     
Sep 11 18:18:43 ls kernel: [    4.092453]   Magic number: 9:69:323                                                           
Sep 11 18:18:43 ls kernel: [    4.092479] tty tty48: hash matches                                                            
Sep 11 18:18:43 ls kernel: [    4.092572] rtc_cmos 00:07: setting system clock to 2009-09-11 09:18:30 UTC (1252660710)       
Sep 11 18:18:43 ls kernel: [    4.092577] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                               
Sep 11 18:18:43 ls kernel: [    4.092580] EDD information not available.                                                     
Sep 11 18:18:43 ls kernel: [    4.220908] ata1.00: ATA-6: HTS541080G9AT00, MB4OA60A, max UDMA/100                            
Sep 11 18:18:43 ls kernel: [    4.220913] ata1.00: 156301488 sectors, multi 16: LBA48                                        
Sep 11 18:18:43 ls kernel: [    4.220959] ata1.01: ATAPI: HL-DT-ST DVDRAM GSA-4082N, HR02, max UDMA/33                       
Sep 11 18:18:43 ls kernel: [    4.220994] ata1.00: limited to UDMA/33 due to 40-wire cable                                   
Sep 11 18:18:43 ls kernel: [    4.236733] ata1.00: configured for UDMA/33                                                    
Sep 11 18:18:43 ls kernel: [    4.252447] ata1.01: configured for UDMA/33                                                    
Sep 11 18:18:43 ls kernel: [    4.254986] scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9AT00  MB4O PQ: 0 ANSI: 5       
Sep 11 18:18:43 ls kernel: [    4.255476] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)            
Sep 11 18:18:43 ls kernel: [    4.255542] sd 0:0:0:0: [sda] Write Protect is off                                             
Sep 11 18:18:43 ls kernel: [    4.255579] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                                                                         
Sep 11 18:18:43 ls kernel: [    4.255747]  sda:                                                                              
Sep 11 18:18:43 ls kernel: [    4.255983] sd 0:0:0:0: Attached scsi generic sg0 type 0                                       
Sep 11 18:18:43 ls kernel: [    4.281279]  sda1 sda2 < sda5                                                                  
Sep 11 18:18:43 ls kernel: [    4.297626] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4082N HR02 PQ: 0 ANSI: 5       
Sep 11 18:18:43 ls kernel: [    4.311538]  sda6 >                                                                            
Sep 11 18:18:43 ls kernel: [    4.319141] sd 0:0:0:0: [sda] Attached SCSI disk                                               
Sep 11 18:18:43 ls kernel: [    4.324211] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray              
Sep 11 18:18:43 ls kernel: [    4.324215] Uniform CD-ROM driver Revision: 3.20                                               
Sep 11 18:18:43 ls kernel: [    4.324677] sr 0:0:1:0: Attached scsi generic sg1 type 5                                       
Sep 11 18:18:43 ls kernel: [    4.500093] Clocksource tsc unstable (delta = -247379600 ns)                                   
Sep 11 18:18:43 ls kernel: [    4.572123] usb 5-1: new low speed USB device using uhci_hcd and address 2                     
Sep 11 18:18:43 ls kernel: [    4.608509] Freeing unused kernel memory: 568k freed                                           
Sep 11 18:18:43 ls kernel: [    4.608929] Write protecting the kernel text: 4532k                                            
Sep 11 18:18:43 ls kernel: [    4.608995] Write protecting the kernel read-only data: 1880k                                  
Sep 11 18:18:43 ls kernel: [    4.753081] usb 5-1: configuration #1 chosen from 1 choice                                     
Sep 11 18:18:43 ls kernel: [    4.964773] b44 0000:06:01.0: enabling device (0000 -> 0002)                                   
Sep 11 18:18:43 ls kernel: [    4.964831] b44 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21                       
Sep 11 18:18:43 ls kernel: [    5.030955] usbcore: registered new interface driver hiddev                                    
Sep 11 18:18:43 ls kernel: [    5.040145] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0                     
Sep 11 18:18:43 ls kernel: [    5.040178] b44.c:v2.0                                                                         
Sep 11 18:18:43 ls kernel: [    5.044390] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input6                                                                                                        
Sep 11 18:18:43 ls kernel: [    5.044623] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-1/input0                                                                              
Sep 11 18:18:43 ls kernel: [    5.044648] usbcore: registered new interface driver usbhid                                    
Sep 11 18:18:43 ls kernel: [    5.044652] usbhid: v2.6:USB HID core driver                                                   
Sep 11 18:18:43 ls kernel: [    5.061132] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:b0:f2:fb:4d                    
Sep 11 18:18:43 ls kernel: [    5.455970] PM: Starting manual resume from disk                                               
Sep 11 18:18:43 ls kernel: [    5.469531] EXT4-fs (sda5): barriers enabled                                                   
Sep 11 18:18:43 ls kernel: [    5.492881] kjournald2 starting: pid 1495, dev sda5:8, commit interval 5 seconds               
Sep 11 18:18:43 ls kernel: [    5.492901] EXT4-fs (sda5): delayed allocation enabled                                         
Sep 11 18:18:43 ls kernel: [    5.492906] EXT4-fs: file extents enabled                                                      
Sep 11 18:18:43 ls kernel: [    5.493504] EXT4-fs: mballoc enabled                                                           
Sep 11 18:18:43 ls kernel: [    5.493526] EXT4-fs (sda5): mounted filesystem with ordered data mode                          
Sep 11 18:18:43 ls kernel: [   11.461940] udev: starting version 141                                                         
Sep 11 18:18:43 ls kernel: [   11.680348] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input7                                                                                                                            
Sep 11 18:18:43 ls kernel: [   11.680409] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)                     
Sep 11 18:18:43 ls kernel: [   12.232174] cfg80211: Calling CRDA to update world regulatory domain                           
Sep 11 18:18:43 ls kernel: [   12.479204] cfg80211: World regulatory domain updated:                                         
Sep 11 18:18:43 ls kernel: [   12.479209] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)                
Sep 11 18:18:43 ls kernel: [   12.479213] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                     
Sep 11 18:18:43 ls kernel: [   12.479217] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                     
Sep 11 18:18:43 ls kernel: [   12.479221] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)                     
Sep 11 18:18:43 ls kernel: [   12.479224] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                     
Sep 11 18:18:43 ls kernel: [   12.479228] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)                     
Sep 11 18:18:43 ls kernel: [   12.533374] Linux agpgart interface v0.103                                                     
Sep 11 18:18:43 ls kernel: [   12.539067] agpgart-intel 0000:00:00.0: Intel 945GM Chipset                                    
Sep 11 18:18:43 ls kernel: [   12.539728] agpgart-intel 0000:00:00.0: detected 7932K stolen memory                           
Sep 11 18:18:43 ls kernel: [   12.542722] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000                      
Sep 11 18:18:43 ls kernel: [   12.553508] intel_rng: FWH not detected                                                        
Sep 11 18:18:43 ls kernel: [   12.647138] input: PC Speaker as /devices/platform/pcspkr/input/input8                         
Sep 11 18:18:43 ls kernel: [   12.703361] acer-wmi: Acer Laptop ACPI-WMI Extras                                              
Sep 11 18:18:43 ls kernel: [   12.832302] Registered led device: acer-wmi::mail                                              
Sep 11 18:18:43 ls kernel: [   13.033867] [drm] Initialized drm 1.1.0 20060810                                               
Sep 11 18:18:43 ls kernel: [   13.078859] yenta_cardbus 0000:06:04.0: CardBus bridge found [1025:0090]                       
Sep 11 18:18:43 ls kernel: [   13.078889] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI            
Sep 11 18:18:43 ls kernel: [   13.078893] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI                      
Sep 11 18:18:43 ls kernel: [   13.078900] yenta_cardbus 0000:06:04.0: TI: mfunc 0x00111c12, devctl 0x44                      
Sep 11 18:18:43 ls kernel: [   13.100478] iTCO_vendor_support: vendor-support=0                                              
Sep 11 18:18:43 ls kernel: [   13.114152] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05                                    
Sep 11 18:18:43 ls kernel: [   13.114263] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)          
Sep 11 18:18:43 ls kernel: [   13.114335] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)                               
Sep 11 18:18:43 ls kernel: [   13.205526] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                      
Sep 11 18:18:43 ls kernel: [   13.303636] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000       
Sep 11 18:18:43 ls kernel: [   13.311224] acerhdf: Acer Aspire One Fan driver, v.0.5.13                                      
Sep 11 18:18:43 ls kernel: [   13.312802] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 16                        
Sep 11 18:18:43 ls kernel: [   13.312807] yenta_cardbus 0000:06:04.0: Socket status: 30000006                                
Sep 11 18:18:43 ls kernel: [   13.312813] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a      
Sep 11 18:18:43 ls kernel: [   13.312823] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff  
Sep 11 18:18:43 ls kernel: [   13.312828] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.              
Sep 11 18:18:43 ls kernel: [   13.313119] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff                                                                                                                    
Sep 11 18:18:43 ls kernel: [   13.313123] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff                                                                                                                    
Sep 11 18:18:43 ls kernel: [   13.335383] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9   
Sep 11 18:18:43 ls kernel: [   13.341721] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks                                                                                                                         
Sep 11 18:18:43 ls kernel: [   13.341725] iwl3945: Copyright(c) 2003-2009 Intel Corporation                                  
Sep 11 18:18:43 ls kernel: [   13.341838] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19                   
Sep 11 18:18:43 ls kernel: [   13.412957] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels           
Sep 11 18:18:43 ls kernel: [   13.412963] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG                    
Sep 11 18:18:43 ls kernel: [   13.793631] [drm] TV-14: set mode NTSC 480i 0                                                  
Sep 11 18:18:43 ls kernel: [   13.919076] [drm] fb0: inteldrmfb frame buffer device                                          
Sep 11 18:18:43 ls kernel: [   13.919090] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0                  
Sep 11 18:18:43 ls kernel: [   14.105463] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22                 
Sep 11 18:18:43 ls kernel: [   14.193850] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10        
Sep 11 18:18:43 ls kernel: [   14.290674] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.                
Sep 11 18:18:43 ls kernel: [   14.292713] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7 
Sep 11 18:18:43 ls kernel: [   14.293594] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.                
Sep 11 18:18:43 ls kernel: [   14.294288] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.                
Sep 11 18:18:43 ls kernel: [   14.295190] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.                
Sep 11 18:18:43 ls kernel: [   14.421619] lp: driver loaded but no devices found                                             
Sep 11 18:18:43 ls kernel: [   14.535732] Adding 995988k swap on /dev/sda1.  Priority:-1 extents:1 across:995988k            
Sep 11 18:18:43 ls kernel: [   15.075573] EXT4-fs (sda5): internal journal on sda5:8                                         
Sep 11 18:18:43 ls kernel: [   15.937383] EXT4-fs (sda6): barriers enabled                                                   
Sep 11 18:18:43 ls kernel: [   15.945305] kjournald2 starting: pid 2756, dev sda6:8, commit interval 5 seconds               
Sep 11 18:18:43 ls kernel: [   15.945583] EXT4-fs (sda6): internal journal on sda6:8                                         
Sep 11 18:18:43 ls kernel: [   15.945587] EXT4-fs (sda6): delayed allocation enabled                                         
Sep 11 18:18:43 ls kernel: [   15.945592] EXT4-fs: file extents enabled                                                      
Sep 11 18:18:43 ls kernel: [   15.945959] EXT4-fs: mballoc enabled                                                           
Sep 11 18:18:43 ls kernel: [   15.945981] EXT4-fs (sda6): mounted filesystem with ordered data mode                          
Sep 11 18:18:45 ls kernel: [   19.570521] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                                       
Sep 11 18:18:45 ls kernel: [   19.570526] Bluetooth: BNEP filters: protocol multicast                                        
Sep 11 18:18:46 ls kernel: [   19.602433] Bridge firewalling registered                                                      
Sep 11 18:18:57 ls kernel: [   31.501223] ppdev: user-space parallel port driver                                             
Sep 11 18:18:58 ls kernel: [   32.574558] [drm] LVDS-8: set mode 1280x800 17                                                 
Sep 11 18:19:02 ls kernel: [   35.637149] ADDRCONF(NETDEV_UP): eth0: link is not ready                                       
Sep 11 18:19:02 ls kernel: [   35.638909] iwl3945 0000:05:00.0: firmware: requesting iwlwifi-3945-2.ucode                    
Sep 11 18:19:05 ls kernel: [   38.805191] b44: eth0: Link is up at 100 Mbps, full duplex.                                    
Sep 11 18:19:08 ls kernel: [   38.805196] b44: eth0: Flow control is off for TX and off for RX.                              
Sep 11 18:19:10 ls kernel: [   43.829625] iwl3945 0000:05:00.0: loaded firmware version 15.28.2.8                            
Sep 11 18:19:11 ls kernel: [   44.951927] Registered led device: iwl-phy0::radio                                             
Sep 11 18:19:11 ls kernel: [   44.951952] Registered led device: iwl-phy0::assoc                                             
Sep 11 18:19:11 ls kernel: [   44.951977] Registered led device: iwl-phy0::RX                                                
Sep 11 18:19:11 ls kernel: [   44.952009] Registered led device: iwl-phy0::TX                                                
Sep 11 18:19:33 ls kernel: [   51.341082] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                      
Sep 11 18:19:33 ls kernel: [   51.345553] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                  
Sep 11 18:19:41 ls kernel: [   73.357114] ------------[ cut here ]------------                                               
Sep 11 18:19:41 ls kernel: [   73.357150] WARNING: at /home/kernel-ppa/mainline/build/net/mac80211/scan.c:281 ieee80211_scan_completed+0x357/0x380 [mac80211]()                                                                                           
Sep 11 18:19:41 ls kernel: [   73.357154] Hardware name: TravelMate 4200                                                     
Sep 11 18:19:41 ls kernel: [   73.357156] Modules linked in: binfmt_misc ppdev bridge stp bnep lp parport snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm arc4 pcmcia ecb snd_seq_dummy joydev snd_seq_oss snd_seq_midi snd_rawmidi iwl3945 snd_seq_midi_event snd_seq snd_timer snd_seq_device i915 iwlcore iTCO_wdt iTCO_vendor_support yenta_socket rsrc_nonstatic drm snd pcmcia_core mac80211 acer_wmi psmouse serio_raw pcspkr intel_agp agpgart soundcore snd_page_alloc led_class i2c_algo_bit cfg80211 video output usbhid b44 ssb mii                                                    
Sep 11 18:19:41 ls kernel: [   73.357216] Pid: 2338, comm: iwl3945 Not tainted 2.6.31-020631-generic #020631                 
Sep 11 18:19:41 ls kernel: [   73.357219] Call Trace:                                                                        
Sep 11 18:19:41 ls kernel: [   73.357239]  [<e00c6f87>] ? ieee80211_scan_completed+0x357/0x380 [mac80211]                    
Sep 11 18:19:41 ls kernel: [   73.357250]  [<c014358c>] warn_slowpath_common+0x7c/0xa0                                       
Sep 11 18:19:41 ls kernel: [   73.357269]  [<e00c6f87>] ? ieee80211_scan_completed+0x357/0x380 [mac80211]                    
Sep 11 18:19:41 ls kernel: [   73.357275]  [<c01435c5>] warn_slowpath_null+0x15/0x20                                         
Sep 11 18:19:41 ls kernel: [   73.357293]  [<e00c6f87>] ieee80211_scan_completed+0x357/0x380 [mac80211]                      
Sep 11 18:19:41 ls kernel: [   73.357299]  [<c014e969>] ? try_to_del_timer_sync+0x49/0x60                                    
Sep 11 18:19:41 ls kernel: [   73.357322]  [<e0253bd9>] iwl_bg_scan_completed+0x39/0x80 [iwlcore]                            
Sep 11 18:19:41 ls kernel: [   73.357333]  [<c01555ed>] run_workqueue+0x6d/0x130                                             
Sep 11 18:19:41 ls kernel: [   73.357348]  [<e0253ba0>] ? iwl_bg_scan_completed+0x0/0x80 [iwlcore]                           
Sep 11 18:19:41 ls kernel: [   73.357357]  [<c0156e38>] worker_thread+0x88/0xe0                                              
Sep 11 18:19:41 ls kernel: [   73.357363]  [<c015a490>] ? autoremove_wake_function+0x0/0x40                                  
Sep 11 18:19:41 ls kernel: [   73.357369]  [<c0156db0>] ? worker_thread+0x0/0xe0                                             
Sep 11 18:19:41 ls kernel: [   73.357373]  [<c015a1ea>] kthread+0x7a/0x90                                                    
Sep 11 18:19:41 ls kernel: [   73.357377]  [<c015a170>] ? kthread+0x0/0x90                                                   
Sep 11 18:19:41 ls kernel: [   73.357383]  [<c0103b97>] kernel_thread_helper+0x7/0x10                                        
Sep 11 18:19:41 ls kernel: [   73.357387] ---[ end trace 6Sep 11 18:21:02 ls syslogd 1.5.0#5ubuntu3: restart. 
```

```
ls@ls:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

```

---

### Post by litos on 2009-09-11
Please send this bugtrace to developers, I do not know how do this.
Kernel 2.6.30 works fine

---

### Post by ahbart on 2009-09-11
Is his a question?
I'm using 2.6.31-10-generic on Karmic. And this one is working fine. 
I tried 2.6.31-rc8 before on Jaunty, and I could not boot after that.
So this could be an temporary issue.

---

### Post by ptn107 on 2009-09-11
The vanilla 2.6.31 kernel (both 32 and 64 bit) from kernel.org work fine in jaunty and karmic.

---

### Post by litos on 2009-09-11
I use Kubuntu 9.04

---

### Post by sgosnell on 2009-09-11
The generic .31 kernel won't boot on my EEE PC.  It hangs, and a cold boot is required.  .30 works fine, but .31 simply won't get past a blank screen.  The splash screen comes up for a few seconds, then a blank black screen and nothing else. Using Jaunty, standard Gnome desktop.

---

