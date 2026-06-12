---
title: "Can't mount new hard disk"
date: 2010-04-06
forum: Hardware
---

### Post by Sciamano on 2010-04-06
Hi!
I've bought a new hard disk (a 1.5Tb Western Digital Green Caviar drive) and the system recognizes it.
If I open Dolphin it can be seen on the left side, and if I click on it, it correctly mounts.
The problem is I can't seem to make it auto-mount at startup.

I've set this line in the fstab:

```
UUID=740987ba-5ca0-4fdc-aaac-13fbeda16199 /media/storage  ext3    defaults,user        0       3
```

but when I restart, the drive is not mounted (and, yes, I've created */media/storage* !) and if I click on it in Dolphin as I described above, it won't mount and I receive this error:

```
Unable to mount /dev/sda2 
org.freedesktop.hal.device.volume.permissiondenied - The volume is already mounted in fstab or the drive is busy
```

:confused:

Any suggestions?
Thanks

---

### Post by Sciamano on 2010-04-07
No one?
Please help, this is frustrating :(

---

### Post by Sciamano on 2010-04-26
I'm still having this issue. The incredible thing is that sometimes the drive mounts correctly, and sometime it gives out the error.
No one can help? :(

---

### Post by Sciamano on 2010-04-27
no one?? :(

---

### Post by dannyboy79 on 2010-04-27
you need to settle down! this isn't paid support you know that. if you want quick answers than look into irc chat in #ubuntu on irc.freenode.net.  

so, let's start over here.
comment out the line in fstab that you added to mount this drive first of all. also, how is this drive connected, SATA, PATA, USB, eSATA, or FIREWIRE? once you have commented it out
issue these commands
```
sudo umount /media/storage
```
```
sudo umount /dev/sda2
```

prove to me that the drive has that UUID by showing me output from a terminal command. 


it would be best to restart the computer.
 once it's back up and running
what does
```
dmesg
```
show as far as information relating to that hard drive. it'll depend if it's USB or SATA or what.

---

### Post by Sciamano on 2010-04-27
Considering I opened this thread some three weeks ago, I don't think I can be accused of being impatient... ;)

The drive is an internal SATA drive, and everything is setup correctly (I'm not that much of a newbie, I've been using Ubuntu on many PCs since Dapper Drake).

I can't send terminal outputs because I'm not on that PC right now, but consider that the 'new' drive gets mounted correctly every now and then (and if I set it up wrong, for example with a wrong UUID, it definitely wouldn't mount ever).

Also most of the times, after entering Kubuntu, the drive will not be mounted (giving the error described in the first post) but if I leave the PC running for an hour or so, when I get back I find the drive has correctly mounted by itself... :O

Basically, every time I boot, I can't use the new drive until an hour or so has passed... and this is what's frustrating...

---

### Post by dannyboy79 on 2010-04-27
output should be within kern.log or syslog or dmesg about the drive not mounting upon bootup. i am not sure if defaults is used anymore within fstab. my ext3 drives are mounted using this in my fstab

UUID=cfa7b50f-a579-430b-830b-e3cdf19ffd48 /var/lib/mythtv       ext3    relatime        0       2

what sata chipset do you have? if you issue 
lsmod | grep sata

you should see it. is this your only sata drive? here's some info on fstab, [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Sciamano on 2010-04-27
> **dannyboy79 said:**
> output should be within kern.log or syslog or dmesg about the drive not mounting upon bootup. 

I can't seem to find any error message in the logs.

> i am not sure if defaults is used anymore within fstab. my ext3 drives are mounted using this in my fstab

UUID=cfa7b50f-a579-430b-830b-e3cdf19ffd48 /var/lib/mythtv       ext3    relatime        0       2

I can try changing this and see what happens.

> what sata chipset do you have? if you issue 
lsmod | grep sata

you should see it. is this your only sata drive? here's some info on fstab, [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

The output of *lsmod | grep sata* is empty. I'm not sure which chipset I have, my mainboard is an Asus P7P55D if this helps.

This is not the only sata drive in the system, there is also a Seagate Barracuda 500Gb (on which / and /home are located) which works flawlessly.
All considering, also the WD drive works correctly once it mounts (that is once I allow it about an hour time to mount :P)

---

### Post by dannyboy79 on 2010-04-27
not sure why a module didn't appear for your sata chipset, maybe it's built right into the kernel.?.?  did you hook the new drive to the additional internal sata port which is controlled by the JMicron Controller? have you tried another sata port? the jmicron controller should be supported with any kernel after 2.6.18 but it may be worth a shot to move the new hdd to a different sata port. it appears on the surface that you did everything correctly.
can you issue a 
sudo mount -a
and then does the drive mount? maybe a bios setting? AHCI or whatever. it's strange if your other sata drives mount fine?

---

### Post by Sciamano on 2010-04-28
> **dannyboy79 said:**
> not sure why a module didn't appear for your sata chipset, maybe it's built right into the kernel.?.?  did you hook the new drive to the additional internal sata port which is controlled by the JMicron Controller? have you tried another sata port? the jmicron controller should be supported with any kernel after 2.6.18 but it may be worth a shot to move the new hdd to a different sata port. it appears on the surface that you did everything correctly.
can you issue a 
sudo mount -a
and then does the drive mount? maybe a bios setting? AHCI or whatever. it's strange if your other sata drives mount fine?

The port I hooked the drive to is not the additional JMicron port, it's one of those directly controlled by the mainboard's chipset.
The JMicron controller works, though, because I had to move some data from some old PATA drives, and hooked them to the JMicron controlled ports withouth any problems.
I'll try moving the drive to another port, just to be sure, although the fact that the drive works perfectly in Windows tells me it's not an hardware related problem.
What I suspect is that this drive being a "green" drive, with special low energy consumption "mechanisms", it might not be totally compatible with Ubuntu right now. Maybe it goes in some kind of "low consumption shutdown" at the system startup and Ubuntu does not know how to wake it up. I have no proof about what I'm saying, but the drive works flawlessly in Windows, so it must be something Ubuntu-related, IMHO.

I've found this bug which looks similar to what I'm experiencing:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/528907](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/528907)
although the error message is a little different, and there's no mention about the drives mounting after a while, like it happens to me.

"sudo mount -a" gives the same error (The volume is already mounted in fstab or the drive is busy, or something like that. I can't replicate right now, because the drive is correctly working atm).

:(

---

### Post by P4man on 2010-04-28
Can you confirm its not a dolphin issue, by trying to browse the drive from the cli when its not working in dolphin? If its not a dolphin problem, post the output of dmesg.

---

### Post by Sciamano on 2010-04-28
> **P4man said:**
> Can you confirm its not a dolphin issue, by trying to browse the drive from the cli when its not working in dolphin? If its not a dolphin problem, post the output of dmesg.

I don't think it's a Dolphin problem because I've tried to mount the disk manually many times (and navigate to it via terminal), without success.
Also, being the disk in the fstab, Dolphin should find the disk already mounted when it starts, which is not the case.

Here is the output of dmesg (it's very long but I kept it all because the last two lines might be important):

```
[    0.000000] Initializing cgroup subsys cpuset                                                                                      
[    0.000000] Initializing cgroup subsys cpu                                                                                         
[    0.000000] Linux version 2.6.31-20-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 (Ubuntu 2.6.31-20.58-generic)                                                                                      
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=55b2f027-e93f-407d-bac4-e4e054f9b14b ro quiet splash
[    0.000000] KERNEL supported cpus:                                                                                                 
[    0.000000]   Intel GenuineIntel                                                                                                   
[    0.000000]   AMD AuthenticAMD                                                                                                     
[    0.000000]   Centaur CentaurHauls                                                                                                 
[    0.000000] BIOS-provided physical RAM map:                                                                                        
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)                                                               
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)                                                             
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)                                                             
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf770000 (usable)                                                               
[    0.000000]  BIOS-e820: 00000000bf770000 - 00000000bf788000 (ACPI data)                                                            
[    0.000000]  BIOS-e820: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)                                                             
[    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)                                                             
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)                                                             
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)                                                             
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)                                                               
[    0.000000] DMI 2.6 present.                                                                                                       
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.                                                        
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)                                         
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000                                                                         
[    0.000000] MTRR default type: uncachable                                                                                          
[    0.000000] MTRR fixed ranges enabled:                                                                                             
[    0.000000]   00000-9FFFF write-back                                                                                               
[    0.000000]   A0000-BFFFF uncachable                                                                                               
[    0.000000]   C0000-CFFFF write-protect                                                                                            
[    0.000000]   D0000-DFFFF uncachable                                                                                               
[    0.000000]   E0000-E7FFF write-through                                                                                            
[    0.000000]   E8000-FFFFF write-protect                                                                                            
[    0.000000] MTRR variable ranges enabled:                                                                                          
[    0.000000]   0 base 000000000 mask F00000000 write-back                                                                           
[    0.000000]   1 base 100000000 mask FC0000000 write-back                                                                           
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable                                                                           
[    0.000000]   3 disabled                                                                                                           
[    0.000000]   4 disabled                                                                                                           
[    0.000000]   5 disabled                                                                                                           
[    0.000000]   6 disabled                                                                                                           
[    0.000000]   7 disabled                                                                                                           
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                                                       
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)                                         
[    0.000000] last_pfn = 0xbf770 max_arch_pfn = 0x400000000                                                                          
[    0.000000] Scanning 0 areas for low memory corruption                                                                             
[    0.000000] modified physical RAM map:                                                                                             
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)                                                              
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)                                                                
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)                                                              
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)                                                              
[    0.000000]  modified: 0000000000100000 - 00000000bf770000 (usable)                                                                
[    0.000000]  modified: 00000000bf770000 - 00000000bf788000 (ACPI data)                                                             
[    0.000000]  modified: 00000000bf788000 - 00000000bf7dc000 (ACPI NVS)                                                              
[    0.000000]  modified: 00000000bf7dc000 - 00000000c0000000 (reserved)                                                              
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)                                                              
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)                                                              
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)                                                                
[    0.000000] initial memory mapped : 0 - 20000000                                                                                   
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf770000                                                                 
[    0.000000] NX (Execute Disable) protection: active                                                                                
[    0.000000]  0000000000 - 00bf600000 page 2M                                                                                       
[    0.000000]  00bf600000 - 00bf770000 page 4k                                                                                       
[    0.000000] kernel direct mapping tables up to bf770000 @ 10000-15000                                                              
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000                                                                 
[    0.000000] NX (Execute Disable) protection: active                                                                                
[    0.000000]  0100000000 - 0140000000 page 2M                                                                                       
[    0.000000] kernel direct mapping tables up to 140000000 @ 13000-19000                                                             
[    0.000000] RAMDISK: 3786d000 - 37feff1a                                                                                           
[    0.000000] ACPI: RSDP 00000000000fb970 00014 (v00 ACPIAM)                                                                         
[    0.000000] ACPI: RSDT 00000000bf770000 00044 (v01 120709 RSDT1452 20091207 MSFT 00000097)                                         
[    0.000000] ACPI: FACP 00000000bf770200 00084 (v01 120709 FACP1452 20091207 MSFT 00000097)                                         
[    0.000000] ACPI: DSDT 00000000bf7704a0 0EE56 (v01  A1326 A1326001 00000001 INTL 20060113)                                         
[    0.000000] ACPI: FACS 00000000bf788000 00040                                                                                      
[    0.000000] ACPI: APIC 00000000bf770390 000CC (v01 120709 APIC1452 20091207 MSFT 00000097)                                         
[    0.000000] ACPI: MCFG 00000000bf770460 0003C (v01 120709 OEMMCFG  20091207 MSFT 00000097)                                         
[    0.000000] ACPI: OEMB 00000000bf788040 00072 (v01 120709 OEMB1452 20091207 MSFT 00000097)                                         
[    0.000000] ACPI: HPET 00000000bf77f7a0 00038 (v01 120709 OEMHPET  20091207 MSFT 00000097)                                         
[    0.000000] ACPI: ASPT 00000000bf77fa40 00034 (v06 120709 PerfTune 20091207 MSFT 00000097)                                         
[    0.000000] ACPI: OSFR 00000000bf77fa80 000B0 (v01 120709 OEMOSFR  20091207 MSFT 00000097)                                         
[    0.000000] ACPI: SSDT 00000000bf7896d0 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)                                         
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                    
[    0.000000] No NUMA configuration found                                                                                            
[    0.000000] Faking a node at 0000000000000000-0000000140000000                                                                     
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000                                                                 
[    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]                                                                      
[    0.000000]   bootmap [0000000000019000 -  0000000000040fff] pages 28                                                              
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]                                                           
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                          
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]                                          
[    0.000000]   #2 [0001000000 - 00019e8c8c]    TEXT DATA BSS ==> [0001000000 - 00019e8c8c]                                          
[    0.000000]   #3 [003786d000 - 0037feff1a]          RAMDISK ==> [003786d000 - 0037feff1a]                                          
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]                                          
[    0.000000]   #5 [00019e9000 - 00019e92bc]              BRK ==> [00019e9000 - 00019e92bc]                                          
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]                                          
[    0.000000]   #7 [0000013000 - 0000014000]          PGTABLE ==> [0000013000 - 0000014000]                                          
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780                                                                         
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0                              
[    0.000000] Zone PFN ranges:                                                                                                       
[    0.000000]   DMA      0x00000010 -> 0x00001000                                                                                    
[    0.000000]   DMA32    0x00001000 -> 0x00100000                                                                                    
[    0.000000]   Normal   0x00100000 -> 0x00140000                                                                                    
[    0.000000] Movable zone start PFN for each node                                                                                   
[    0.000000] early_node_map[3] active PFN ranges                                                                                    
[    0.000000]     0: 0x00000010 -> 0x0000009f                                                                                        
[    0.000000]     0: 0x00000100 -> 0x000bf770                                                                                        
[    0.000000]     0: 0x00100000 -> 0x00140000                                                                                        
[    0.000000] On node 0 totalpages: 1046271                                                                                          
[    0.000000]   DMA zone: 56 pages used for memmap                                                                                   
[    0.000000]   DMA zone: 103 pages reserved                                                                                         
[    0.000000]   DMA zone: 3824 pages, LIFO batch:0                                                                                   
[    0.000000]   DMA32 zone: 14280 pages used for memmap                                                                              
[    0.000000]   DMA32 zone: 765864 pages, LIFO batch:31                                                                              
[    0.000000]   Normal zone: 3584 pages used for memmap                                                                              
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31                                                                             
[    0.000000] ACPI: PM-Timer IO Port: 0x808                                                                                          
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)                                                                     
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)                                                                     
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)                                                                     
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)                                                                     
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)                                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)                                                                    
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])                                                                
[    0.000000] IOAPIC[0]: apic_id 7, version 32, address 0xfec00000, GSI 0-23                                                         
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                                               
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                                                            
[    0.000000] ACPI: IRQ0 used by override.                                                                                           
[    0.000000] ACPI: IRQ2 used by override.                                                                                           
[    0.000000] ACPI: IRQ9 used by override.                                                                                           
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                                    
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000                                                                             
[    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs                                                                                 
[    0.000000] nr_irqs_gsi: 24                                                                                                        
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000                                                      
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000                                                      
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000                                                      
[    0.000000] PM: Registered nosave memory: 00000000bf770000 - 00000000bf788000                                                      
[    0.000000] PM: Registered nosave memory: 00000000bf788000 - 00000000bf7dc000                                                      
[    0.000000] PM: Registered nosave memory: 00000000bf7dc000 - 00000000c0000000                                                      
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000                                                      
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000                                                      
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000                                                      
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000                                                      
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)                                                 
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:16 nr_node_ids:1                                                              
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes                                                 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028248                                           
[    0.000000] Policy zone: Normal                                                                                                    
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=55b2f027-e93f-407d-bac4-e4e054f9b14b ro quiet splash                                                                                                                               
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)                                                                  
[    0.000000] Initializing CPU#0                                                                                                     
[    0.000000] Checking aperture...                                                                                                   
[    0.000000] No AGP bridge found                                                                                                    
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area                                                                          
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!                                                          
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)                                                              
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000                                               
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000                                                                        
[    0.000000] Memory: 4041784k/5242880k available (5327k kernel code, 1057796k absent, 143300k reserved, 3014k data, 664k init)      
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1                                               
[    0.000000] NR_IRQS:4352 nr_irqs:536                                                                                               
[    0.000000] Fast TSC calibration using PIT                                                                                         
[    0.000000] Detected 2674.548 MHz processor.                                                                                       
[    0.001529] Console: colour VGA+ 80x25                                                                                             
[    0.001531] console [tty0] enabled                                                                                                 
[    0.008156] allocated 41943040 bytes of page_cgroup                                                                                
[    0.008157] please try 'cgroup_disable=memory' option if you don't want memory cgroups                                             
[    0.008272] hpet clockevent registered                                                                                             
[    0.008279]   alloc irq_desc for 24 on node 0                                                                                      
[    0.008281]   alloc kstat_irqs on node 0                                                                                           
[    0.008287]   alloc irq_desc for 25 on node 0                                                                                      
[    0.008288]   alloc kstat_irqs on node 0                                                                                           
[    0.008291]   alloc irq_desc for 26 on node 0                                                                                      
[    0.008292]   alloc kstat_irqs on node 0                                                                                           
[    0.008295]   alloc irq_desc for 27 on node 0                                                                                      
[    0.008296]   alloc kstat_irqs on node 0                                                                                           
[    0.008298]   alloc irq_desc for 28 on node 0                                                                                      
[    0.008299]   alloc kstat_irqs on node 0                                                                                           
[    0.008301] HPET: 8 timers in total, 5 timers will be used for per-cpu timer                                                       
[    0.008306] Calibrating delay loop (skipped), value calculated using timer frequency.. 5349.09 BogoMIPS (lpj=26745480)             
[    0.008319] Security Framework initialized                                                                                         
[    0.008332] AppArmor: AppArmor initialized                                                                                         
[    0.008567] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)                                                     
[    0.009320] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)                                                       
[    0.009636] Mount-cache hash table entries: 256                                                                                    
[    0.009717] Initializing cgroup subsys ns                                                                                          
[    0.009720] Initializing cgroup subsys cpuacct                                                                                     
[    0.009723] Initializing cgroup subsys memory                                                                                      
[    0.009727] Initializing cgroup subsys freezer                                                                                     
[    0.009728] Initializing cgroup subsys net_cls                                                                                     
[    0.009737] CPU: Physical Processor ID: 0                                                                                          
[    0.009738] CPU: Processor Core ID: 0                                                                                              
[    0.009741] CPU: L1 I cache: 32K, L1 D cache: 32K                                                                                  
[    0.009742] CPU: L2 cache: 256K                                                                                                    
[    0.009743] CPU: L3 cache: 8192K                                                                                                   
[    0.009745] CPU 0/0x0 -> Node 0                                                                                                    
[    0.009747] mce: CPU supports 9 MCE banks                                                                                          
[    0.009755] CPU0: Thermal monitoring enabled (TM1)                                                                                 
[    0.009758] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6 CMCI:8                                                                     
[    0.009764] using mwait in idle threads.                                                                                           
[    0.009765] Performance Counters: Nehalem/Corei7 events, Intel PMU driver.                                                         
[    0.009769] ... version:                 3                                                                                         
[    0.009770] ... bit width:               48                                                                                        
[    0.009770] ... generic counters:        4                                                                                         
[    0.009772] ... value mask:              0000ffffffffffff                                                                          
[    0.009773] ... max period:              000000007fffffff                                                                          
[    0.009774] ... fixed-purpose counters:  3                                                                                         
[    0.009775] ... counter mask:            000000070000000f                                                                          
[    0.011371] ACPI: Core revision 20090521                                                                                           
[    0.128446] Setting APIC routing to flat                                                                                           
[    0.128773] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                                                                   
[    0.228554] CPU0: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05                                                      
[    0.347644] Booting processor 1 APIC 0x2 ip 0x6000                                                                                 
[    0.358120] Initializing CPU#1                                                                                                     
[    0.507218] Calibrating delay using timer specific routine.. 5349.85 BogoMIPS (lpj=26749298)                                       
[    0.507224] CPU: Physical Processor ID: 0                                                                                          
[    0.507224] CPU: Processor Core ID: 1                                                                                              
[    0.507226] CPU: L1 I cache: 32K, L1 D cache: 32K                                                                                  
[    0.507228] CPU: L2 cache: 256K                                                                                                    
[    0.507228] CPU: L3 cache: 8192K                                                                                                   
[    0.507230] CPU 1/0x2 -> Node 0                                                                                                    
[    0.507232] mce: CPU supports 9 MCE banks                                                                                          
[    0.507240] CPU1: Thermal monitoring enabled (TM1)                                                                                 
[    0.507242] CPU 1 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8                                                                       
[    0.507870] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106                                                       
[    0.508457] CPU1: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05                                                      
[    0.508464] Skipping synchronization checks as TSC is reliable.                                                                    
[    0.508528] Booting processor 2 APIC 0x4 ip 0x6000                                                                                 
[    0.518865] Initializing CPU#2                                                                                                     
[    0.666876] Calibrating delay using timer specific routine.. 5349.85 BogoMIPS (lpj=26749298)                                       
[    0.666882] CPU: Physical Processor ID: 0                                                                                          
[    0.666883] CPU: Processor Core ID: 2                                                                                              
[    0.666885] CPU: L1 I cache: 32K, L1 D cache: 32K                                                                                  
[    0.666886] CPU: L2 cache: 256K                                                                                                    
[    0.666887] CPU: L3 cache: 8192K                                                                                                   
[    0.666889] CPU 2/0x4 -> Node 0                                                                                                    
[    0.666891] mce: CPU supports 9 MCE banks                                                                                          
[    0.666898] CPU2: Thermal monitoring enabled (TM1)                                                                                 
[    0.666901] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8                                                                       
[    0.667532] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106                                                       
[    0.668141] CPU2: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05                                                      
[    0.668149] Skipping synchronization checks as TSC is reliable.                                                                    
[    0.668214] Booting processor 3 APIC 0x6 ip 0x6000                                                                                 
[    0.678551] Initializing CPU#3                                                                                                     
[    0.826535] Calibrating delay using timer specific routine.. 5349.85 BogoMIPS (lpj=26749286)                                       
[    0.826541] CPU: Physical Processor ID: 0                                                                                          
[    0.826542] CPU: Processor Core ID: 3                                                                                              
[    0.826544] CPU: L1 I cache: 32K, L1 D cache: 32K                                                                                  
[    0.826545] CPU: L2 cache: 256K                                                                                                    
[    0.826546] CPU: L3 cache: 8192K                                                                                                   
[    0.826548] CPU 3/0x6 -> Node 0                                                                                                    
[    0.826550] mce: CPU supports 9 MCE banks                                                                                          
[    0.826557] CPU3: Thermal monitoring enabled (TM1)                                                                                 
[    0.826560] CPU 3 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6 SHD:8                                                                       
[    0.827186] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106                                                       
[    0.827827] CPU3: Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz stepping 05                                                      
[    0.827834] Skipping synchronization checks as TSC is reliable.                                                                    
[    0.827848] Brought up 4 CPUs                                                                                                      
[    0.827850] Total of 4 processors activated (21398.67 BogoMIPS).                                                                   
[    0.827902] CPU0 attaching sched-domain:                                                                                           
[    0.827904]  domain 0: span 0-3 level MC                                                                                           
[    0.827905]   groups: 0 1 2 3                                                                                                      
[    0.827909] CPU1 attaching sched-domain:                                                                                           
[    0.827911]  domain 0: span 0-3 level MC                                                                                           
[    0.827912]   groups: 1 2 3 0                                                                                                      
[    0.827915] CPU2 attaching sched-domain:                                                                                           
[    0.827916]  domain 0: span 0-3 level MC                                                                                           
[    0.827918]   groups: 2 3 0 1                                                                                                      
[    0.827921] CPU3 attaching sched-domain:                                                                                           
[    0.827922]  domain 0: span 0-3 level MC                                                                                           
[    0.827923]   groups: 3 0 1 2                                                                                                      
[    0.828122] Booting paravirtualized kernel on bare hardware                                                                        
[    0.828254] regulator: core version 0.5                                                                                            
[    0.828277] Time: 22:41:46  Date: 04/26/10                                                                                         
[    0.828309] NET: Registered protocol family 16                                                                                     
[    0.828390] ACPI: bus type pci registered                                                                                          
[    0.828440] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                                       
[    0.828441] PCI: Not using MMCONFIG.                                                                                               
[    0.828443] PCI: Using configuration type 1 for base access                                                                        
[    0.828983] bio: create slab <bio-0> at 0                                                                                          
[    0.829778] ACPI: EC: Look up EC in DSDT                                                                                           
[    0.843254] ACPI: Interpreter enabled                                                                                              
[    0.843257] ACPI: (supports S0 S1 S3 S4 S5)                                                                                        
[    0.843273] ACPI: Using IOAPIC for interrupt routing                                                                               
[    0.843317] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                                       
[    0.846131] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources                                                      
[    0.850963] PCI: Using MMCONFIG at e0000000 - efffffff                                                                             
[    0.858810] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62                                                          
[    0.858812] ACPI: EC: driver started in poll mode                                                                                  
[    0.858872] ACPI Warning: Incorrect checksum in table [OEMB] - 13, should be 12 20090521 tbutils-246                               
[    0.859000] ACPI: No dock devices found.                                                                                           
[    0.859269] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                                 
[    0.859364] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold                                                                  
[    0.859367] pci 0000:00:03.0: PME# disabled                                                                                        
[    0.859611] pci 0000:00:1a.0: reg 10 32bit mmio: [0xf7ffe000-0xf7ffe3ff]                                                           
[    0.859660] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold                                                                  
[    0.859663] pci 0000:00:1a.0: PME# disabled                                                                                        
[    0.859698] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7ff8000-0xf7ffbfff]                                                           
[    0.859734] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold                                                                  
[    0.859737] pci 0000:00:1b.0: PME# disabled                                                                                        
[    0.859789] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold                                                                  
[    0.859792] pci 0000:00:1c.0: PME# disabled                                                                                        
[    0.859846] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold                                                                  
[    0.859849] pci 0000:00:1c.4: PME# disabled                                                                                        
[    0.859899] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold                                                                  
[    0.859902] pci 0000:00:1c.5: PME# disabled                                                                                        
[    0.859953] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold                                                                  
[    0.859956] pci 0000:00:1c.6: PME# disabled                                                                                        
[    0.860006] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold                                                                  
[    0.860009] pci 0000:00:1c.7: PME# disabled                                                                                        
[    0.860055] pci 0000:00:1d.0: reg 10 32bit mmio: [0xf7ffd000-0xf7ffd3ff]                                                           
[    0.860103] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold                                                                  
[    0.860107] pci 0000:00:1d.0: PME# disabled                                                                                        
[    0.860257] pci 0000:00:1f.2: reg 10 io port: [0x9c00-0x9c07]                                                                      
[    0.860262] pci 0000:00:1f.2: reg 14 io port: [0x9880-0x9883]                                                                      
[    0.860266] pci 0000:00:1f.2: reg 18 io port: [0x9800-0x9807]                                                                      
[    0.860271] pci 0000:00:1f.2: reg 1c io port: [0x9480-0x9483]                                                                      
[    0.860276] pci 0000:00:1f.2: reg 20 io port: [0x9400-0x940f]                                                                      
[    0.860280] pci 0000:00:1f.2: reg 24 io port: [0x9080-0x908f]                                                                      
[    0.860320] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf7ffc000-0xf7ffc0ff]                                                           
[    0.860331] pci 0000:00:1f.3: reg 20 io port: [0xffe0-0xffff]                                                                      
[    0.860368] pci 0000:00:1f.5: reg 10 io port: [0xac00-0xac07]                                                                      
[    0.860373] pci 0000:00:1f.5: reg 14 io port: [0xa880-0xa883]                                                                      
[    0.860378] pci 0000:00:1f.5: reg 18 io port: [0xa800-0xa807]                                                                      
[    0.860382] pci 0000:00:1f.5: reg 1c io port: [0xa480-0xa483]                                                                      
[    0.860387] pci 0000:00:1f.5: reg 20 io port: [0xa400-0xa40f]                                                                      
[    0.860392] pci 0000:00:1f.5: reg 24 io port: [0xa080-0xa08f]                                                                      
[    0.860445] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]                                                           
[    0.860454] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]                                                           
[    0.860462] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf8000000-0xf9ffffff]                                                           
[    0.860467] pci 0000:01:00.0: reg 24 io port: [0xbc00-0xbc7f]                                                                      
[    0.860472] pci 0000:01:00.0: reg 30 32bit mmio: [0xfbbe0000-0xfbbfffff]                                                           
[    0.860520] pci 0000:00:03.0: bridge io port: [0xb000-0xbfff]                                                                      
[    0.860523] pci 0000:00:03.0: bridge 32bit mmio: [0xf8000000-0xfbbfffff]                                                           
[    0.860527] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]                                                      
[    0.860724] pci 0000:03:00.0: reg 24 32bit mmio: [0xfbdfe000-0xfbdfffff]                                                           
[    0.860760] pci 0000:03:00.0: PME# supported from D3hot                                                                            
[    0.860764] pci 0000:03:00.0: PME# disabled                                                                                        
[    0.860814] pci 0000:03:00.1: reg 10 io port: [0xdc00-0xdc07]                                                                      
[    0.860822] pci 0000:03:00.1: reg 14 io port: [0xd880-0xd883]                                                                      
[    0.860830] pci 0000:03:00.1: reg 18 io port: [0xd800-0xd807]                                                                      
[    0.860838] pci 0000:03:00.1: reg 1c io port: [0xd480-0xd483]                                                                      
[    0.860846] pci 0000:03:00.1: reg 20 io port: [0xd400-0xd40f]                                                                      
[    0.860930] pci 0000:00:1c.6: bridge io port: [0xd000-0xdfff]                                                                      
[    0.860933] pci 0000:00:1c.6: bridge 32bit mmio: [0xfbd00000-0xfbdfffff]                                                           
[    0.860978] pci 0000:02:00.0: reg 10 io port: [0xc800-0xc8ff]                                                                      
[    0.860996] pci 0000:02:00.0: reg 18 64bit mmio: [0xf6fff000-0xf6ffffff]                                                           
[    0.861008] pci 0000:02:00.0: reg 20 64bit mmio: [0xf6ff8000-0xf6ffbfff]                                                           
[    0.861016] pci 0000:02:00.0: reg 30 32bit mmio: [0xfbcf0000-0xfbcfffff]                                                           
[    0.861052] pci 0000:02:00.0: supports D1 D2                                                                                       
[    0.861053] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold                                                            
[    0.861058] pci 0000:02:00.0: PME# disabled                                                                                        
[    0.861110] pci 0000:00:1c.7: bridge io port: [0xc000-0xcfff]                                                                      
[    0.861113] pci 0000:00:1c.7: bridge 32bit mmio: [0xfbc00000-0xfbcfffff]                                                           
[    0.861118] pci 0000:00:1c.7: bridge 64bit mmio pref: [0xf6f00000-0xf6ffffff]                                                      
[    0.861149] pci 0000:07:01.0: reg 10 io port: [0xe800-0xe8ff]                                                                      
[    0.861155] pci 0000:07:01.0: reg 14 32bit mmio: [0xfbeffc00-0xfbeffcff]                                                           
[    0.861193] pci 0000:07:01.0: supports D1 D2                                                                                       
[    0.861195] pci 0000:07:01.0: PME# supported from D1 D2 D3hot D3cold                                                               
[    0.861198] pci 0000:07:01.0: PME# disabled                                                                                        
[    0.861232] pci 0000:07:04.0: reg 10 32bit mmio: [0xfbeff000-0xfbeff7ff]                                                           
[    0.861238] pci 0000:07:04.0: reg 14 io port: [0xec00-0xec7f]                                                                      
[    0.861277] pci 0000:07:04.0: supports D2                                                                                          
[    0.861279] pci 0000:07:04.0: PME# supported from D2 D3hot D3cold                                                                  
[    0.861282] pci 0000:07:04.0: PME# disabled                                                                                        
[    0.861319] pci 0000:00:1e.0: transparent bridge                                                                                   
[    0.861322] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]                                                                      
[    0.861326] pci 0000:00:1e.0: bridge 32bit mmio: [0xfbe00000-0xfbefffff]                                                           
[    0.861355] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                                    
[    0.861501] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]                                                               
[    0.861610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]                                                               
[    0.861666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]                                                               
[    0.861713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]                                                               
[    0.861760] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR25._PRT]                                                               
[    0.861807] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR26._PRT]                                                               
[    0.861864] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR27._PRT]                                                               
[    0.881383] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)                                                         
[    0.881492] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)                                                                              
[    0.881597] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 14 *15)                                                         
[    0.881705] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)                                                         
[    0.881812] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.                                            
[    0.881919] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)                                                         
[    0.882026] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)                                                         
[    0.882133] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 *7 10 11 12 14 15)                                                         
[    0.882249] SCSI subsystem initialized                                                                                             
[    0.882301] libata version 3.00 loaded.                                                                                            
[    0.882345] usbcore: registered new interface driver usbfs                                                                         
[    0.882353] usbcore: registered new interface driver hub                                                                           
[    0.882367] usbcore: registered new device driver usb                                                                              
[    0.882440] ACPI: WMI: Mapper loaded                                                                                               
[    0.882442] PCI: Using ACPI for IRQ routing                                                                                        
[    0.906379] Bluetooth: Core ver 2.15                                                                                               
[    0.906415] NET: Registered protocol family 31                                                                                     
[    0.906418] Bluetooth: HCI device and connection manager initialized                                                               
[    0.906422] Bluetooth: HCI socket layer initialized                                                                                
[    0.906424] NetLabel: Initializing                                                                                                 
[    0.906426] NetLabel:  domain hash size = 128                                                                                      
[    0.906429] NetLabel:  protocols = UNLABELED CIPSOv4                                                                               
[    0.906446] NetLabel:  unlabeled traffic allowed by default                                                                        
[    0.906492] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0                                                            
[    0.906497] hpet0: 8 comparators, 64-bit 14.318180 MHz counter                                                                     
[    0.916370] hpet: hpet2 irq 24 for MSI                                                                                             
[    0.917586] hpet: hpet3 irq 25 for MSI                                                                                             
[    0.927572] hpet: hpet4 irq 26 for MSI                                                                                             
[    0.937545] hpet: hpet5 irq 27 for MSI                                                                                             
[    0.946338] Switched to high resolution mode on CPU 0                                                                              
[    0.947541] Switched to high resolution mode on CPU 3                                                                              
[    0.947546] Switched to high resolution mode on CPU 1                                                                              
[    0.947550] Switched to high resolution mode on CPU 2                                                                              
[    0.966295] pnp: PnP ACPI init                                                                                                     
[    0.966307] ACPI: bus type pnp registered                                                                                          
[    0.968952] pnp: PnP ACPI: found 16 devices                                                                                        
[    0.968953] ACPI: ACPI bus type pnp unregistered                                                                                   
[    0.968960] system 00:01: iomem range 0xfc000000-0xfcffffff has been reserved                                                      
[    0.968962] system 00:01: iomem range 0xfd000000-0xfdffffff has been reserved                                                      
[    0.968964] system 00:01: iomem range 0xfe000000-0xfebfffff has been reserved                                                      
[    0.968966] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved                                                      
[    0.968970] system 00:06: ioport range 0x290-0x29f has been reserved                                                               
[    0.968974] system 00:07: ioport range 0x4d0-0x4d1 has been reserved                                                               
[    0.968976] system 00:07: ioport range 0x800-0x87f has been reserved                                                               
[    0.968978] system 00:07: ioport range 0x500-0x57f has been reserved                                                               
[    0.968979] system 00:07: ioport range 0x600-0x607 has been reserved                                                               
[    0.968981] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved                                                      
[    0.968985] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved                                                      
[    0.968987] system 00:07: iomem range 0xfed40000-0xfed8ffff has been reserved                                                      
[    0.968991] system 00:0a: iomem range 0xffc00000-0xffdfffff has been reserved                                                      
[    0.968994] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved                                                  
[    0.968996] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved                                                      
[    0.969000] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved                                                      
[    0.969003] system 00:0f: iomem range 0x0-0x9ffff could not be reserved                                                            
[    0.969005] system 00:0f: iomem range 0xc0000-0xcffff has been reserved                                                            
[    0.969007] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved                                                        
[    0.969009] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved                                                    
[    0.969011] system 00:0f: iomem range 0xfed90000-0xffffffff could not be reserved                                                  
[    0.973600] AppArmor: AppArmor Filesystem Enabled                                                                                  
[    0.973649] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01                                                                    
[    0.973651] pci 0000:00:03.0:   IO window: 0xb000-0xbfff                                                                           
[    0.973654] pci 0000:00:03.0:   MEM window: 0xf8000000-0xfbbfffff                                                                  
[    0.973657] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff                                                 
[    0.973661] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:06                                                                    
[    0.973662] pci 0000:00:1c.0:   IO window: disabled                                                                                
[    0.973666] pci 0000:00:1c.0:   MEM window: disabled                                                                               
[    0.973668] pci 0000:00:1c.0:   PREFETCH window: disabled                                                                          
[    0.973671] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05                                                                    
[    0.973673] pci 0000:00:1c.4:   IO window: disabled                                                                                
[    0.973676] pci 0000:00:1c.4:   MEM window: disabled                                                                               
[    0.973679] pci 0000:00:1c.4:   PREFETCH window: disabled                                                                          
[    0.973682] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04                                                                    
[    0.973683] pci 0000:00:1c.5:   IO window: disabled                                                                                
[    0.973686] pci 0000:00:1c.5:   MEM window: disabled                                                                               
[    0.973689] pci 0000:00:1c.5:   PREFETCH window: disabled                                                                          
[    0.973692] pci 0000:00:1c.6: PCI bridge, secondary bus 0000:03                                                                    
[    0.973695] pci 0000:00:1c.6:   IO window: 0xd000-0xdfff                                                                           
[    0.973698] pci 0000:00:1c.6:   MEM window: 0xfbd00000-0xfbdfffff                                                                  
[    0.973701] pci 0000:00:1c.6:   PREFETCH window: disabled                                                                          
[    0.973704] pci 0000:00:1c.7: PCI bridge, secondary bus 0000:02                                                                    
[    0.973707] pci 0000:00:1c.7:   IO window: 0xc000-0xcfff                                                                           
[    0.973710] pci 0000:00:1c.7:   MEM window: 0xfbc00000-0xfbcfffff                                                                  
[    0.973713] pci 0000:00:1c.7:   PREFETCH window: 0x000000f6f00000-0x000000f6ffffff                                                 
[    0.973718] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07                                                                    
[    0.973721] pci 0000:00:1e.0:   IO window: 0xe000-0xefff                                                                           
[    0.973724] pci 0000:00:1e.0:   MEM window: 0xfbe00000-0xfbefffff                                                                  
[    0.973727] pci 0000:00:1e.0:   PREFETCH window: disabled                                                                          
[    0.973737]   alloc irq_desc for 16 on node 0                                                                                      
[    0.973738]   alloc kstat_irqs on node 0                                                                                           
[    0.973742] pci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                           
[    0.973745] pci 0000:00:03.0: setting latency timer to 64                                                                          
[    0.973750]   alloc irq_desc for 17 on node 0                                                                                      
[    0.973751]   alloc kstat_irqs on node 0                                                                                           
[    0.973753] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                           
[    0.973756] pci 0000:00:1c.0: setting latency timer to 64                                                                          
[    0.973762] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                           
[    0.973765] pci 0000:00:1c.4: setting latency timer to 64                                                                          
[    0.973770] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16                                                           
[    0.973773] pci 0000:00:1c.5: setting latency timer to 64                                                                          
[    0.973778]   alloc irq_desc for 18 on node 0                                                                                      
[    0.973779]   alloc kstat_irqs on node 0                                                                                           
[    0.973781] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                                           
[    0.973784] pci 0000:00:1c.6: setting latency timer to 64                                                                          
[    0.973789]   alloc irq_desc for 19 on node 0                                                                                      
[    0.973791]   alloc kstat_irqs on node 0                                                                                           
[    0.973793] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19                                                           
[    0.973796] pci 0000:00:1c.7: setting latency timer to 64                                                                          
[    0.973801] pci 0000:00:1e.0: setting latency timer to 64                                                                          
[    0.973804] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]                                                                         
[    0.973806] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]                                                         
[    0.973807] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]                                                                       
[    0.973809] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbbfffff]                                                               
[    0.973811] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]                                                           
[    0.973813] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]                                                                       
[    0.973814] pci_bus 0000:03: resource 1 mem: [0xfbd00000-0xfbdfffff]                                                               
[    0.973816] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]                                                                       
[    0.973817] pci_bus 0000:02: resource 1 mem: [0xfbc00000-0xfbcfffff]                                                               
[    0.973819] pci_bus 0000:02: resource 2 pref mem [0xf6f00000-0xf6ffffff]                                                           
[    0.973821] pci_bus 0000:07: resource 0 io:  [0xe000-0xefff]                                                                       
[    0.973822] pci_bus 0000:07: resource 1 mem: [0xfbe00000-0xfbefffff]                                                               
[    0.973824] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]                                                                         
[    0.973825] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]                                                         
[    0.973848] NET: Registered protocol family 2                                                                                      
[    0.973967] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)                                                    
[    0.974674] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)                                                  
[    0.976984] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)                                                           
[    0.977262] TCP: Hash tables configured (established 524288 bind 65536)                                                            
[    0.977264] TCP reno registered                                                                                                    
[    0.977351] NET: Registered protocol family 1                                                                                      
[    0.977389] Trying to unpack rootfs image as initramfs...                                                                          
[    1.111633] Freeing initrd memory: 7691k freed                                                                                     
[    1.112890] Scanning for low memory corruption every 60 seconds                                                                    
[    1.112976] audit: initializing netlink socket (disabled)                                                                          
[    1.112988] type=2000 audit(1272321705.880:1): initialized                                                                         
[    1.120583] HugeTLB registered 2 MB page size, pre-allocated 0 pages                                                               
[    1.121542] VFS: Disk quotas dquot_6.5.2                                                                                           
[    1.121581] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)                                                              
[    1.121995] fuse init (API version 7.12)                                                                                           
[    1.122049] msgmni has been set to 7909                                                                                            
[    1.122191] alg: No test for stdrng (krng)                                                                                         
[    1.122197] io scheduler noop registered                                                                                           
[    1.122199] io scheduler anticipatory registered                                                                                   
[    1.122200] io scheduler deadline registered                                                                                       
[    1.122230] io scheduler cfq registered (default)                                                                                  
[    1.122292] pci 0000:01:00.0: Boot video device                                                                                    
[    1.122391]   alloc irq_desc for 29 on node 0                                                                                      
[    1.122392]   alloc kstat_irqs on node 0                                                                                           
[    1.122399] pcieport-driver 0000:00:03.0: irq 29 for MSI/MSI-X                                                                     
[    1.122404] pcieport-driver 0000:00:03.0: setting latency timer to 64                                                              
[    1.122499]   alloc irq_desc for 30 on node 0                                                                                      
[    1.122500]   alloc kstat_irqs on node 0                                                                                           
[    1.122506] pcieport-driver 0000:00:1c.0: irq 30 for MSI/MSI-X                                                                     
[    1.122513] pcieport-driver 0000:00:1c.0: setting latency timer to 64                                                              
[    1.122610]   alloc irq_desc for 31 on node 0                                                                                      
[    1.122611]   alloc kstat_irqs on node 0                                                                                           
[    1.122617] pcieport-driver 0000:00:1c.4: irq 31 for MSI/MSI-X                                                                     
[    1.122623] pcieport-driver 0000:00:1c.4: setting latency timer to 64                                                              
[    1.122722]   alloc irq_desc for 32 on node 0                                                                                      
[    1.122723]   alloc kstat_irqs on node 0                                                                                           
[    1.122729] pcieport-driver 0000:00:1c.5: irq 32 for MSI/MSI-X                                                                     
[    1.122735] pcieport-driver 0000:00:1c.5: setting latency timer to 64                                                              
[    1.122834]   alloc irq_desc for 33 on node 0                                                                                      
[    1.122835]   alloc kstat_irqs on node 0                                                                                           
[    1.122841] pcieport-driver 0000:00:1c.6: irq 33 for MSI/MSI-X                                                                     
[    1.122847] pcieport-driver 0000:00:1c.6: setting latency timer to 64                                                              
[    1.122944]   alloc irq_desc for 34 on node 0                                                                                      
[    1.122946]   alloc kstat_irqs on node 0                                                                                           
[    1.122951] pcieport-driver 0000:00:1c.7: irq 34 for MSI/MSI-X                                                                     
[    1.122957] pcieport-driver 0000:00:1c.7: setting latency timer to 64                                                              
[    1.123025] Firmware did not grant requested _OSC control                                                                          
[    1.123027] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support                                             
[    1.123034] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                                        
[    1.123044] Firmware did not grant requested _OSC control                                                                          
[    1.123056] Firmware did not grant requested _OSC control                                                                          
[    1.123066] Firmware did not grant requested _OSC control                                                                          
[    1.123075] Firmware did not grant requested _OSC control                                                                          
[    1.123085] Firmware did not grant requested _OSC control                                                                          
[    1.123103] Firmware did not grant requested _OSC control                                                                          
[    1.123113] Firmware did not grant requested _OSC control                                                                          
[    1.123122] Firmware did not grant requested _OSC control                                                                          
[    1.123131] Firmware did not grant requested _OSC control                                                                          
[    1.123141] Firmware did not grant requested _OSC control                                                                          
[    1.123151] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                                            
[    1.123223] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                                   
[    1.123225] ACPI: Power Button [PWRF]                                                                                              
[    1.123260] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                                          
[    1.123262] ACPI: Power Button [PWRB]                                                                                              
[    1.124097] ACPI: SSDT 00000000bf7880c0 01130 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)                                         
[    1.124465] ACPI: SSDT 00000000bf7891f0 004D5 (v01  PmRef  P001Cst 00003001 INTL 20060113)                                         
[    1.124807] Monitor-Mwait will be used to enter C-1 state                                                                          
[    1.124822] Monitor-Mwait will be used to enter C-2 state                                                                          
[    1.124835] Monitor-Mwait will be used to enter C-3 state                                                                          
[    1.124849] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])                                                                        
[    1.124865] processor LNXCPU:00: registered as cooling_device0                                                                     
[    1.125046] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])                                                                        
[    1.125058] processor LNXCPU:01: registered as cooling_device1                                                                     
[    1.125240] ACPI: CPU2 (power states: C1[C1] C2[C2] C3[C3])                                                                        
[    1.125252] processor LNXCPU:02: registered as cooling_device2                                                                     
[    1.125435] ACPI: CPU3 (power states: C1[C1] C2[C2] C3[C3])                                                                        
[    1.125446] processor LNXCPU:03: registered as cooling_device3                                                                     
[    1.128483] Linux agpgart interface v0.103                                                                                         
[    1.128489] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled                                                                
[    1.128581] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                   
[    1.128828] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                                        
[    1.129448] brd: module loaded                                                                                                     
[    1.129727] loop: module loaded                                                                                                    
[    1.129768] input: Macintosh mouse button emulation as /devices/virtual/input/input2                                               
[    1.129834] ahci 0000:03:00.0: version 3.0                                                                                         
[    1.129847] ahci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18                                                          
[    1.145930] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode                                           
[    1.145936] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part                                                       
[    1.145943] ahci 0000:03:00.0: setting latency timer to 64                                                                         
[    1.146112] scsi0 : ahci                                                                                                           
[    1.146164] scsi1 : ahci                                                                                                           
[    1.146210] ata1: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 18                                                   
[    1.146213] ata2: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 18                                                   
[    1.146262] ata_piix 0000:00:1f.2: version 2.13                                                                                    
[    1.146270]   alloc irq_desc for 21 on node 0                                                                                      
[    1.146271]   alloc kstat_irqs on node 0                                                                                           
[    1.146275] ata_piix 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21                                                      
[    1.146279] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]                                                                             
[    1.146302] ata_piix 0000:00:1f.2: setting latency timer to 64                                                                     
[    1.146336] scsi2 : ata_piix                                                                                                       
[    1.146367] scsi3 : ata_piix                                                                                                       
[    1.147517] ata3: SATA max UDMA/133 cmd 0x9c00 ctl 0x9880 bmdma 0x9400 irq 21                                                      
[    1.147522] ata4: SATA max UDMA/133 cmd 0x9800 ctl 0x9480 bmdma 0x9408 irq 21                                                      
[    1.147559] ata_piix 0000:00:1f.5: PCI INT D -> GSI 21 (level, low) -> IRQ 21                                                      
[    1.147563] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]                                                                             
[    1.147587] ata_piix 0000:00:1f.5: setting latency timer to 64                                                                     
[    1.147610] scsi4 : ata_piix                                                                                                       
[    1.147641] scsi5 : ata_piix                                                                                                       
[    1.148530] ata5: SATA max UDMA/133 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 21                                                      
[    1.148533] ata6: SATA max UDMA/133 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 21                                                      
[    1.148754] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)                                                              
[    1.148759] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19                                                  
[    1.148778] pata_jmicron 0000:03:00.1: setting latency timer to 64                                                                 
[    1.148816] scsi6 : pata_jmicron                                                                                                   
[    1.148850] scsi7 : pata_jmicron                                                                                                   
[    1.149267] ata7: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 19                                                      
[    1.149269] ata8: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 19                                                      
[    1.149582] Fixed MDIO Bus: probed                                                                                                 
[    1.149603] PPP generic driver version 2.4.2                                                                                       
[    1.149651] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                                             
[    1.149684] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                      
[    1.149693] ehci_hcd 0000:00:1a.0: setting latency timer to 64                                                                     
[    1.149697] ehci_hcd 0000:00:1a.0: EHCI Host Controller                                                                            
[    1.149716] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1                                                   
[    1.153611] ehci_hcd 0000:00:1a.0: debug port 2                                                                                    
[    1.153615] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported                                                          
[    1.153625] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7ffe000                                                                       
[    1.175814] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00                                                                      
[    1.175904] usb usb1: configuration #1 chosen from 1 choice                                                                        
[    1.175922] hub 1-0:1.0: USB hub found                                                                                             
[    1.175926] hub 1-0:1.0: 2 ports detected                                                                                          
[    1.175977]   alloc irq_desc for 23 on node 0                                                                                      
[    1.175979]   alloc kstat_irqs on node 0                                                                                           
[    1.175982] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23                                                      
[    1.175990] ehci_hcd 0000:00:1d.0: setting latency timer to 64                                                                     
[    1.175993] ehci_hcd 0000:00:1d.0: EHCI Host Controller                                                                            
[    1.176012] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2                                                   
[    1.179893] ehci_hcd 0000:00:1d.0: debug port 2                                                                                    
[    1.179897] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported                                                          
[    1.179907] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7ffd000                                                                       
[    1.195769] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00                                                                      
[    1.195854] usb usb2: configuration #1 chosen from 1 choice                                                                        
[    1.195873] hub 2-0:1.0: USB hub found                                                                                             
[    1.195877] hub 2-0:1.0: 2 ports detected                                                                                          
[    1.195911] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                                 
[    1.195921] uhci_hcd: USB Universal Host Controller Interface driver                                                               
[    1.195980] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1                                                                 
[    1.195981] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp                         
[    1.196442] serio: i8042 KBD port at 0x60,0x64 irq 1                                                                               
[    1.196478] mice: PS/2 mouse device common for all mice                                                                            
[    1.196526] rtc_cmos 00:03: RTC can wake from S4                                                                                   
[    1.196547] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0                                                                  
[    1.196570] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs                                                          
[    1.196652] device-mapper: uevent: version 1.0.3                                                                                   
[    1.196701] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com                                       
[    1.196752] device-mapper: multipath: version 1.1.0 loaded                                                                         
[    1.196754] device-mapper: multipath round-robin: version 1.0.0 loaded                                                             
[    1.196946] cpuidle: using governor ladder                                                                                         
[    1.197069] cpuidle: using governor menu                                                                                           
[    1.197364] TCP cubic registered                                                                                                   
[    1.197450] NET: Registered protocol family 10                                                                                     
[    1.197796] lo: Disabled Privacy Extensions                                                                                        
[    1.197997] NET: Registered protocol family 17                                                                                     
[    1.198010] Bluetooth: L2CAP ver 2.13                                                                                              
[    1.198011] Bluetooth: L2CAP socket layer initialized                                                                              
[    1.198013] Bluetooth: SCO (Voice Link) ver 0.6                                                                                    
[    1.198014] Bluetooth: SCO socket layer initialized                                                                                
[    1.198030] Bluetooth: RFCOMM TTY layer initialized                                                                                
[    1.198032] Bluetooth: RFCOMM socket layer initialized                                                                             
[    1.198033] Bluetooth: RFCOMM ver 1.11                                                                                             
[    1.199114] PM: Resume from disk failed.                                                                                           
[    1.199122] registered taskstats version 1                                                                                         
[    1.199219]   Magic number: 6:409:705                                                                                              
[    1.199377] rtc_cmos 00:03: setting system clock to 2010-04-26 22:41:46 UTC (1272321706)                                           
[    1.199382] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                                   
[    1.199384] EDD information not available.                                                                                         
[    1.215466] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3                                     
[    1.495214] usb 1-1: new high speed USB device using ehci_hcd and address 2                                                        
[    1.506065] ata5: SATA link down (SStatus 0 SControl 300)                                                                          
[    1.506097] ata2: SATA link down (SStatus 0 SControl 300)                                                                          
[    1.516842] ata6: SATA link down (SStatus 0 SControl 300)                                                                          
[    1.516881] ata1: SATA link down (SStatus 0 SControl 300)                                                                          
[    1.646566] usb 1-1: configuration #1 chosen from 1 choice                                                                         
[    1.646758] hub 1-1:1.0: USB hub found                                                                                             
[    1.646969] hub 1-1:1.0: 6 ports detected                                                                                          
[    1.764655] usb 2-1: new high speed USB device using ehci_hcd and address 2                                                        
[    1.914763] usb 2-1: configuration #1 chosen from 1 choice                                                                         
[    1.914959] hub 2-1:1.0: USB hub found                                                                                             
[    1.915157] hub 2-1:1.0: 8 ports detected                                                                                          
[    2.024075] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)                                                              
[    2.024092] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                                                              
[    2.024300] ata4.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                                                              
[    2.024310] ata4.01: SATA link down (SStatus 0 SControl 300)                                                                       
[    2.044937] ata4.00: ATA-8: ST3500418AS, CC38, max UDMA/133                                                                        
[    2.044943] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)                                                           
[    2.064211] ata3.00: ATAPI: Optiarc DVD RW AD-7241S, 1.03, max UDMA/100                                                            
[    2.071815] ata3.01: ATA-8: WDC WD15EARS-00Z5B1, 80.00A80, max UDMA/133                                                            
[    2.071820] ata3.01: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)                                                          
[    2.084568] ata4.00: configured for UDMA/133                                                                                       
[    2.104019] ata3.00: configured for UDMA/100                                                                                       
[    2.125030] ata3.01: configured for UDMA/133                                                                                       
[    2.127370] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7241S  1.03 PQ: 0 ANSI: 5                                           
[    2.132865] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray                                                  
[    2.132870] Uniform CD-ROM driver Revision: 3.20                                                                                   
[    2.132971] sr 2:0:0:0: Attached scsi CD-ROM sr0                                                                                   
[    2.133012] sr 2:0:0:0: Attached scsi generic sg0 type 5                                                                           
[    2.133051] scsi 2:0:1:0: Direct-Access     ATA      WDC WD15EARS-00Z 80.0 PQ: 0 ANSI: 5                                           
[    2.133215] sd 2:0:1:0: Attached scsi generic sg1 type 0                                                                           
[    2.133227] sd 2:0:1:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)                                               
[    2.133255] sd 2:0:1:0: [sda] Write Protect is off                                                                                 
[    2.133257] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00                                                                              
[    2.133270] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                
[    2.133301] scsi 3:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5                                           
[    2.133339]  sda:                                                                                                                  
[    2.133394] sd 3:0:0:0: Attached scsi generic sg2 type 0                                                                           
[    2.133427] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)                                                  
[    2.133453] sd 3:0:0:0: [sdb] Write Protect is off                                                                                 
[    2.133455] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00                                                                              
[    2.133467] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                
[    2.133533]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 sda1 sda2                                                                             
[    2.164489]  sdb6 >                                                                                                                
[    2.164846] sd 3:0:0:0: [sdb] Attached SCSI disk                                                                                   
[    2.186544] sd 2:0:1:0: [sda] Attached SCSI disk                                                                                   
[    2.193957] usb 2-1.7: new full speed USB device using ehci_hcd and address 3                                                      
[    2.303973] usb 2-1.7: configuration #1 chosen from 1 choice                                                                       
[    2.304094] hub 2-1.7:1.0: USB hub found                                                                                           
[    2.304323] hub 2-1.7:1.0: 4 ports detected                                                                                        
[    2.305601] Freeing unused kernel memory: 664k freed                                                                               
[    2.305703] Write protecting the kernel read-only data: 7596k                                                                      
[    2.380849] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded                                                                        
[    2.380864] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19                                                         
[    2.380903] r8169 0000:02:00.0: setting latency timer to 64                                                                        
[    2.380942]   alloc irq_desc for 35 on node 0                                                                                      
[    2.380943]   alloc kstat_irqs on node 0                                                                                           
[    2.380954] r8169 0000:02:00.0: irq 35 for MSI/MSI-X                                                                               
[    2.381302] eth0: RTL8168d/8111d at 0xffffc9000067a000, e0:cb:4e:9e:0f:fd, XID 283000c0 IRQ 35                                     
[    2.393138] 8139too Fast Ethernet driver 0.9.28                                                                                    
[    2.393233] usb 2-1.8: new low speed USB device using ehci_hcd and address 4                                                       
[    2.393253] 8139too 0000:07:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                       
[    2.394152] eth1: RealTek RTL8139 at 0xe800, 00:24:01:ee:ef:66, IRQ 16                                                             
[    2.395237] ohci1394 0000:07:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19                                                      
[    2.455039] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fbeff000-fbeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]   
[    2.509283] usb 2-1.8: configuration #1 chosen from 1 choice                                                                       
[    2.512893] usbcore: registered new interface driver hiddev                                                                        
[    2.516586] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8:1.0/input/input4                 
[    2.516620] generic-usb 0003:046D:C506.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.8/input0                                                                                                                                   
[    2.516628] usbcore: registered new interface driver usbhid                                                                        
[    2.516629] usbhid: v2.6:USB HID core driver                                                                                       
[    3.613914] PM: Starting manual resume from disk                                                                                   
[    3.613917] PM: Resume from partition 8:1                                                                                          
[    3.613917] PM: Checking hibernation image.                                                                                        
[    3.614130] PM: Resume from disk failed.                                                                                           
[    3.635834] EXT4-fs (sdb5): barriers enabled                                                                                       
[    3.650255] kjournald2 starting: pid 461, dev sdb5:8, commit interval 5 seconds                                                    
[    3.670427] EXT4-fs (sdb5): delayed allocation enabled                                                                             
[    3.670429] EXT4-fs: file extents enabled                                                                                          
[    3.671021] EXT4-fs: mballoc enabled                                                                                               
[    3.671030] EXT4-fs (sdb5): mounted filesystem with ordered data mode                                                              
[    3.780308] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000f72a47]                                                        
[    4.162599] type=1505 audit(1272321709.466:2): operation="profile_load" pid=488 name=/sbin/dhclient3                               
[    4.162950] type=1505 audit(1272321709.466:3): operation="profile_load" pid=488 name=/usr/lib/NetworkManager/nm-dhcp-client.action 
[    4.163138] type=1505 audit(1272321709.466:4): operation="profile_load" pid=488 name=/usr/lib/connman/scripts/dhclient-script      
[    4.197535] type=1505 audit(1272321709.496:5): operation="profile_load" pid=490 name=/usr/lib/cups/backend/cups-pdf                
[    4.197937] type=1505 audit(1272321709.496:6): operation="profile_load" pid=490 name=/usr/sbin/cupsd                               
[    4.199815] type=1505 audit(1272321709.506:7): operation="profile_load" pid=491 name=/usr/sbin/mysqld-akonadi                      
[    4.201267] type=1505 audit(1272321709.506:8): operation="profile_load" pid=492 name=/usr/sbin/tcpdump                             
[   12.272110] Adding 4000176k swap on /dev/sda1.  Priority:-1 extents:1 across:4000176k                                              
[   12.280096] udev: starting version 147                                                                                             
[   12.306934] lp: driver loaded but no devices found                                                                                 
[   12.326655] nvidia: module license 'NVIDIA' taints kernel.                                                                         
[   12.326657] Disabling lock debugging due to kernel taint                                                                           
[   12.344078] ip_tables: (C) 2000-2006 Netfilter Core Team                                                                           
[   12.348964] eth1: link down                                                                                                        
[   12.349285] ADDRCONF(NETDEV_UP): eth1: link is not ready                                                                           
[   12.377711]   alloc irq_desc for 22 on node 0                                                                                      
[   12.377713]   alloc kstat_irqs on node 0                                                                                           
[   12.377718] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22                                                     
[   12.377813] HDA Intel 0000:00:1b.0: setting latency timer to 64                                                                    
[   12.533860] EXT4-fs (sdb5): internal journal on sdb5:8                                                                             
[   12.579559] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                        
[   12.579564] nvidia 0000:01:00.0: setting latency timer to 64                                                                       
[   12.580170] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010                                
[   13.158087] EXT4-fs (sdb6): barriers enabled                                                                                       
[   13.160949] kjournald2 starting: pid 908, dev sdb6:8, commit interval 5 seconds                                                    
[   13.161897] EXT4-fs (sdb6): internal journal on sdb6:8                                                                             
[   13.161904] EXT4-fs (sdb6): delayed allocation enabled                                                                             
[   13.161908] EXT4-fs: file extents enabled                                                                                          
[   13.167649] EXT4-fs: mballoc enabled                                                                                               
[   13.167658] EXT4-fs (sdb6): mounted filesystem with ordered data mode                                                              
[   13.236065] type=1505 audit(1272314518.556:9): operation="profile_replace" pid=1053 name=/sbin/dhclient3                           
[   13.236407] type=1505 audit(1272314518.556:10): operation="profile_replace" pid=1053 name=/usr/lib/NetworkManager/nm-dhcp-client.action                                                                                                                                  
[   13.236594] type=1505 audit(1272314518.556:11): operation="profile_replace" pid=1053 name=/usr/lib/connman/scripts/dhclient-script 
[   13.238140] type=1505 audit(1272314518.556:12): operation="profile_replace" pid=1055 name=/usr/lib/cups/backend/cups-pdf           
[   13.238534] type=1505 audit(1272314518.566:13): operation="profile_replace" pid=1055 name=/usr/sbin/cupsd                          
[   13.239915] type=1505 audit(1272314518.566:14): operation="profile_replace" pid=1056 name=/usr/sbin/mysqld-akonadi                 
[   13.240796] type=1505 audit(1272314518.566:15): operation="profile_replace" pid=1057 name=/usr/sbin/tcpdump                        
[   13.243391] r8169: eth0: link up                                                                                                   
[   13.243395] r8169: eth0: link up                                                                                                   
[   15.065346] vboxdrv: Trying to deactivate the NMI watchdog permanently...                                                          
[   15.065348] vboxdrv: Successfully done.                                                                                            
[   15.065349] vboxdrv: Found 4 processor cores.                                                                                      
[   15.065376] VBoxDrv: dbg - g_abExecMemory=ffffffffa0bde460                                                                         
[   15.065817] vboxdrv: fAsync=0 offMin=0x18a offMax=0x1fe9b                                                                          
[   15.065839] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.                                                     
[   15.065840] vboxdrv: Successfully loaded version 3.1.6 (interface 0x00100001).                                                     
[   15.192709] usplash:424 freeing invalid memtype fffffffff9000000-fffffffff9e00000                                                  
[   15.306592] ppdev: user-space parallel port driver                                                                                 
[   16.480901] CPU0 attaching NULL sched-domain.                                                                                      
[   16.480904] CPU1 attaching NULL sched-domain.                                                                                      
[   16.480906] CPU2 attaching NULL sched-domain.                                                                                      
[   16.480907] CPU3 attaching NULL sched-domain.                                                                                      
[   16.521287] CPU0 attaching sched-domain:                                                                                           
[   16.521290]  domain 0: span 0-3 level MC                                                                                           
[   16.521292]   groups: 0 1 2 3                                                                                                      
[   16.521295]   domain 1: span 0-3 level CPU                                                                                         
[   16.521296]    groups: 0-3 (__cpu_power = 4096)                                                                                    
[   16.521300] CPU1 attaching sched-domain:                                                                                           
[   16.521301]  domain 0: span 0-3 level MC                                                                                           
[   16.521302]   groups: 1 2 3 0                                                                                                      
[   16.521305]   domain 1: span 0-3 level CPU                                                                                         
[   16.521306]    groups: 0-3 (__cpu_power = 4096)                                                                                    
[   16.521309] CPU2 attaching sched-domain:                                                                                           
[   16.521310]  domain 0: span 0-3 level MC                                                                                           
[   16.521311]   groups: 2 3 0 1                                                                                                      
[   16.521314]   domain 1: span 0-3 level CPU                                                                                         
[   16.521315]    groups: 0-3 (__cpu_power = 4096)                                                                                    
[   16.521318] CPU3 attaching sched-domain:                                                                                           
[   16.521319]  domain 0: span 0-3 level MC
[   16.521320]   groups: 3 0 1 2
[   16.521323]   domain 1: span 0-3 level CPU
[   16.521324]    groups: 0-3 (__cpu_power = 4096)
[   18.021305] CPU0 attaching NULL sched-domain.
[   18.021313] CPU1 attaching NULL sched-domain.
[   18.021316] CPU2 attaching NULL sched-domain.
[   18.021319] CPU3 attaching NULL sched-domain.
[   18.048599] CPU0 attaching sched-domain:
[   18.048604]  domain 0: span 0-3 level MC
[   18.048608]   groups: 0 1 2 3
[   18.048616] CPU1 attaching sched-domain:
[   18.048619]  domain 0: span 0-3 level MC
[   18.048622]   groups: 1 2 3 0
[   18.048629] CPU2 attaching sched-domain:
[   18.048632]  domain 0: span 0-3 level MC
[   18.048635]   groups: 2 3 0 1
[   18.048641] CPU3 attaching sched-domain:
[   18.048644]  domain 0: span 0-3 level MC
[   18.048647]   groups: 3 0 1 2
[   24.093286] eth0: no IPv6 routers present
[ 1984.090950] kjournald starting.  Commit interval 5 seconds
[ 1984.091630] EXT3 FS on sda2, internal journal
[ 1984.091638] EXT3-fs: mounted filesystem with writeback data mode.

```

---

### Post by P4man on 2010-04-28
I see you have your swap partition on that drive, on sda1. Im just guessing here, but is it possible its only mounting your ext partition after it accesses (needs) your swap? (the "hour" you have to wait) Is your swap available all the time?

```
swapon -s

```

Not that any of this would actually explain what you are seeing...

edit: can you post your entire fstab?

---

### Post by Sciamano on 2010-04-28
> **P4man said:**
> I see you have your swap partition on that drive, on sda1. Im just guessing here, but is it possible its only mounting your ext partition after it accesses (needs) your swap? (the "hour" you have to wait) Is your swap available all the time?

```
swapon -s

```

Not that any of this would actually explain what you are seeing...

I really don't know... Might be. Although the fact that during that "hour" the PC just stays on without doing anything, would hardly explain why the swap partition would be needed after that time. But who knows? I'll check this too.
I'm on a different PC now (I'm at work, and the 'faulty' drive is on my home PC)

> edit: can you post your entire fstab?

I'll do that as soon as I get home. But it's pretty clean, there's just /, /home, /swap, /storage and /cdrom to be mounted.
Nothing else...

---

### Post by P4man on 2010-04-28
> **Sciamano said:**
> I really don't know... Might be. Although the fact that during that "hour" the PC just stays on without doing anything, would hardly explain why the swap partition would be needed after that time.

Well, i notice ubuntu sometimes swaps a few  MB on my machine  after a while, for no apparent reason as I got plenty of free ram. it doesnt do it after a fresh boot, but I cant say I kept on eye on when it does it. Could well be after an hour. 

Anyway, its a stretch, but if nothing else, it would be interesting to see if the drive itself is working properly even if the ext filesystem isnt mounting. Would narrow down a bit the possible causes.

---

### Post by Sciamano on 2010-04-28
> **P4man said:**
> Well, i notice ubuntu sometimes swaps a few  MB on my machine  after a while, for no apparent reason as I got plenty of free ram. it doesnt do it after a fresh boot, but I cant say I kept on eye on when it does it. Could well be after an hour. 

Anyway, its a stretch, but if nothing else, it would be interesting to see if the drive itself is working properly even if the ext filesystem isnt mounting. Would narrow down a bit the possible causes.

I'll report on this in a few hours. Now I'm curious too :)

---

### Post by Sciamano on 2010-04-28
Ok, Murphy's Law is in charge right now, and even though I've rebooted many times, the drive is currently mounting correctly.
As I said, this problem happens intermittently, so I'll have to wait until it happens again before I try the swap thing :)

---

### Post by dannyboy79 on 2010-04-28
you did change the sata it uses right? maybe that fixed it?

---

### Post by Sciamano on 2010-04-28
> **dannyboy79 said:**
> you did change the sata it uses right? maybe that fixed it?

No I didn't. I didn't have the time... :confused:

---

