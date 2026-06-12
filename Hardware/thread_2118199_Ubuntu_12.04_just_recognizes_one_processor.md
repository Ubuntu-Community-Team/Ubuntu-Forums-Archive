---
title: "Ubuntu 12.04 just recognizes one processor"
date: 2013-02-20
forum: Hardware
---

### Post by Plinio Santos on 2013-02-20
I installed Ubuntu 12.04 LTE in a machine that has an intel i3 processor. As far as I know, i3 processor is a multicore one and the OS should recognize 2 processors, just as Windows 7 does. Ubuntu 12 isn't recognizing it though. Is it a know issue? Have I missed some configuration?

the output of```
$ cat /proc/cpuinfo
```

is:
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 37
model name      : Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz
stepping        : 2
microcode       : 0x9
cpu MHz         : 2933.374
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc up arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5866.74
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

[ EDIT ]
Adding new info. The output of ```
$ lscpu
```

is:
```

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              2
CPU MHz:               2933.196
BogoMIPS:              5866.39
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K
NUMA node0 CPU(s):     0

```

---

### Post by jackyboy633 on 2013-02-20
Hi there,

Please can you do the following while your PC is booting:
1. Hold down the right SHIFT key to diaplay the GRUB menu.
2. Then press E while the 'Ubuntu' entry is highlighted.

If you find 'nolapic' on the screen, that is the cause of the problem, so delete that and you will be fine. :D

Hope this helps,
Jackyboy633

---

### Post by Plinio Santos on 2013-02-21
Thanks jackyboy633, but unfortunately me kernel command line does not has the nolapic option. There is the string "quiet splash $vt_handoff" though.

---

### Post by jackyboy633 on 2013-02-21
Hello again, 


Have you looked in the bios? You might have a setting in there that enables the multiple cores. Also, and what is the make and model of your PC?

---

### Post by Doug S on 2013-02-21
If your installation was normal, then I think that processor should show 2 cores and 4 threads. Maybe it is set to one core in the BIOS (but you said windows was O.K. so maybe not). Maybe the setting mentioned by jackyboy633 is done in the config file. Look at /boot/config* (the most recent). Example:```
doug@doug-64:~$ [COLOR=red]ls -l /boot/config*[/COLOR]
-rw-r--r-- 1 root root 140505 Dec  5 10:22 /boot/config-3.2.0-35-generic
-rw-r--r-- 1 root root 140505 Jan  8 14:25 /boot/config-3.2.0-36-generic
-rw-r--r-- 1 root root 140505 Jan 24 08:08 /boot/config-3.2.0-37-generic
doug@doug-64:~$ [COLOR=red]grep APIC /boot/config-3.2.0-37-generic[/COLOR]
CONFIG_X86_X2APIC=y
[COLOR=red]CONFIG_X86_LOCAL_APIC=y[/COLOR]
CONFIG_X86_IO_APIC=y
CONFIG_PCI_IOAPIC=y
CONFIG_KVM_APIC_ARCHITECTURE=y
```Also have a look at the log files for the CPU detection part of the boot process. Example (/var/log/kern.log):```
Feb 14 13:39:54 s15 kernel: [    0.062917] CPU0: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz stepping 07
Feb 14 13:39:54 s15 kernel: [    0.168899] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
Feb 14 13:39:54 s15 kernel: [    0.168904] PEBS disabled due to CPU errata.
Feb 14 13:39:54 s15 kernel: [    0.168906] ... version:                3
Feb 14 13:39:54 s15 kernel: [    0.168908] ... bit width:              48
Feb 14 13:39:54 s15 kernel: [    0.168909] ... generic registers:      4
Feb 14 13:39:54 s15 kernel: [    0.168911] ... value mask:             0000ffffffffffff
Feb 14 13:39:54 s15 kernel: [    0.168913] ... max period:             000000007fffffff
Feb 14 13:39:54 s15 kernel: [    0.168914] ... fixed-purpose events:   3
Feb 14 13:39:54 s15 kernel: [    0.168916] ... event mask:             000000070000000f
Feb 14 13:39:54 s15 kernel: [    0.169023] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 13:39:54 s15 kernel: [    0.169073] Booting Node   0, Processors  #1
Feb 14 13:39:54 s15 kernel: [    0.169076] smpboot cpu 1: start_ip = 98000
Feb 14 13:39:54 s15 kernel: [    0.276955] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 13:39:54 s15 kernel: [    0.277020]  #2
Feb 14 13:39:54 s15 kernel: [    0.277022] smpboot cpu 2: start_ip = 98000
Feb 14 13:39:54 s15 kernel: [    0.384897] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 13:39:54 s15 kernel: [    0.384957]  #3
Feb 14 13:39:54 s15 kernel: [    0.384958] smpboot cpu 3: start_ip = 98000
Feb 14 13:39:54 s15 kernel: [    0.492832] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 13:39:54 s15 kernel: [    0.492893]  #4
Feb 14 13:39:54 s15 kernel: [    0.492894] smpboot cpu 4: start_ip = 98000
Feb 14 13:39:54 s15 kernel: [    0.600670] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 13:39:54 s15 kernel: [    0.600739]  #5
Feb 14 13:39:54 s15 kernel: [    0.600741] smpboot cpu 5: start_ip = 98000
Feb 14 13:39:54 s15 kernel: [    0.708617] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 13:39:54 s15 kernel: [    0.708681]  #6
Feb 14 13:39:54 s15 kernel: [    0.708683] smpboot cpu 6: start_ip = 98000
Feb 14 13:39:54 s15 kernel: [    0.816558] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 13:39:54 s15 kernel: [    0.816619]  #7 Ok.
Feb 14 13:39:54 s15 kernel: [    0.816621] smpboot cpu 7: start_ip = 98000
Feb 14 13:39:54 s15 kernel: [    0.924495] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 13:39:54 s15 kernel: [    0.924521] Brought up 8 CPUs
Feb 14 13:39:54 s15 kernel: [    0.924523] Total of 8 processors activated (54577.36 BogoMIPS).

```There have been [bizarre cases ]("http://ubuntuforums.org/showthread.php?t=2084166&highlight=usb+hub")where linux does not realize there are more CPU's, but as far as I know those were with AMD processors.

---

### Post by Plinio Santos on 2013-02-22
Hi jackyboy633. I toke a look into my bios config, and the config that I think may be related with this issue are:

CPU realted:
Intel (R) Core (TM) i3 CPU 530 2.93GH
HT - enabled
A20M - disabled (I don't know what it is...)
Max CPUID Value Limit - disabled (I don't know what it is...)
Active processor cores - All (Max allowed value is 2)

Power: I think it does not matter, but how knows... :)
all config related with ACPI (around 4 config options) - disabled

---

### Post by Plinio Santos on 2013-02-22
Hi Doug S. Thanks for you answer.
As I told to jackyboy633, the BIOS seems to be fine.

Now, follows the output you asked:
```

$ grep APIC /boot/config-3.2.0-29-generic
CONFIG_X86_X2APIC=y
CONFIG_X86_LOCAL_APIC=y
CONFIG_X86_IO_APIC=y
CONFIG_PCI_IOAPIC=y
CONFIG_KVM_APIC_ARCHITECTURE=y

```

And form /var/log/kern.log :
```

Feb 22 08:37:27 MATTIDST002 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
...
Feb 22 08:37:27 MATTIDST002 kernel: [    0.003953] CPU0: Thermal monitoring enabled (TM1)
Feb 22 08:37:27 MATTIDST002 kernel: [    0.003961] using mwait in idle threads.
Feb 22 08:37:27 MATTIDST002 kernel: [    0.004000] SMP alternatives: switching to UP code
Feb 22 08:37:27 MATTIDST002 kernel: [    0.010870] Freeing SMP alternatives: 24k freed
Feb 22 08:37:27 MATTIDST002 kernel: [    0.010881] ACPI: Core revision 20110623
Feb 22 08:37:27 MATTIDST002 kernel: [    0.014752] ACPI: setting ELCR to 0200 (from cc60)
Feb 22 08:37:27 MATTIDST002 kernel: [    0.036996] ftrace: allocating 26998 entries in 106 pages
Feb 22 08:37:27 MATTIDST002 kernel: [    0.044302] weird, boot CPU (#0) not listed by the BIOS.
Feb 22 08:37:27 MATTIDST002 kernel: [    0.044304] SMP motherboard not detected.
Feb 22 08:37:27 MATTIDST002 kernel: [    0.150902] SMP disabled
Feb 22 08:37:27 MATTIDST002 kernel: [    0.150904] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
Feb 22 08:37:27 MATTIDST002 kernel: [    0.150911] ... version:                3
Feb 22 08:37:27 MATTIDST002 kernel: [    0.150912] ... bit width:              48
Feb 22 08:37:27 MATTIDST002 kernel: [    0.150914] ... generic registers:      4
Feb 22 08:37:27 MATTIDST002 kernel: [    0.150915] ... value mask:             0000ffffffffffff
Feb 22 08:37:27 MATTIDST002 kernel: [    0.150916] ... max period:             000000007fffffff
Feb 22 08:37:27 MATTIDST002 kernel: [    0.150917] ... fixed-purpose events:   3
Feb 22 08:37:27 MATTIDST002 kernel: [    0.150919] ... event mask:             000000070000000f
Feb 22 08:37:27 MATTIDST002 kernel: [    0.151032] NMI watchdog enabled, takes one hw-pmu counter.
Feb 22 08:37:27 MATTIDST002 kernel: [    0.151050] Brought up 1 CPUs
Feb 22 08:37:27 MATTIDST002 kernel: [    0.151052] Total of 1 processors activated (5866.45 BogoMIPS).

```

Seems that my ubuntu installation is missing some modules, is it right? If yes, how can I install the correct ones?
As this is a workstation setup and it toke a lot of time to setup this machine (setup development environment, bring up all network location, configure VPNs and so on), would be great if the solution does not involves things like format and reinstall all =p

---

### Post by Doug S on 2013-02-22
> Feb 22 08:37:27 MATTIDST002 kernel: [ 0.044302] weird, boot CPU (#0) not listed by the BIOS.
Feb 22 08:37:27 MATTIDST002 kernel: [ 0.044304] SMP motherboard not detected.
Feb 22 08:37:27 MATTIDST002 kernel: [ 0.150902] SMP disabled
Well, that seems to be your issue. As jackyboy633 asked previously, what is the make and model of your PC?> Seems that my ubuntu installation is missing some modules, is it right?I do not come to that conclusion from what has been posted.

---

### Post by Yellow Pasque on 2013-02-22
> what is the make and model of your PC?
dmidecode might be helpful too:
```
sudo dmidecode
```

---

### Post by Plinio Santos on 2013-02-25
> **Doug S said:**
> Well, that seems to be your issue. As jackyboy633 asked previously, what is the make and model of your PC?I do not come to that conclusion from what has been posted.

```

$ sudo lshw
  *-core
       description: Motherboard
       product: P7H55-M BR
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: X.0x
       serial: MS2222222222222222222222222
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0602
          date: 05/11/2011
          size: 64KiB
          capacity: 8128KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification

```

And:
```

$ sudo dmidecode
Handle 0x0000, DMI type 0, 24 bytes                                                                                                                                                                                                                                   
BIOS Information                                                                                                                                                                                                                                                      
        Vendor: American Megatrends Inc.                                                                                                                                                                                                                              
        Version: 0602                                                                                                                                                                                                                                                 
        Release Date: 05/11/2011                                                                                                                                                                                                                                      
        Address: 0xF0000                                                                                                                                                                                                                                              
        Runtime Size: 64 kB                                                                                                                                                                                                                                           
        ROM Size: 8192 kB                                                                                                                                                                                                                                             
        Characteristics:                                                                                                                                                                                                                                              
                ISA is supported                                                                                                                                                                                                                                      
                PCI is supported                                                                                                                                                                                                                                      
                PNP is supported                                                                                                                                                                                                                                      
                APM is supported                                                                                                                                                                                                                                      
                BIOS is upgradeable                                                                                                                                                                                                                                   
                BIOS shadowing is allowed                                                                                                                                                                                                                             
                ESCD support is available                                                                                                                                                                                                                             
                Boot from CD is supported                                                                                                                                                                                                                             
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 kB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                LS-120 boot is supported
                ATAPI Zip drive boot is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
        BIOS Revision: 8.15

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK Computer INC.
        Product Name: P7H55-M BR
        Version: X.0x
        Serial Number: MS2222222222222222222222222
        Asset Tag: To Be Filled By O.E.M.
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: To Be Filled By O.E.M.
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0

Handle 0x0004, DMI type 4, 42 bytes
Processor Information
        Socket Designation: LGA1156
        Type: Central Processor
        Family: Core i3
        Manufacturer: Intel            
        ID: 52 06 02 00 FF FB EB BF
        Signature: Type 0, Family 6, Model 37, Stepping 2
        Flags:
                FPU (Floating-point unit on-chip)
                VME (Virtual mode extension)
                DE (Debugging extension)
                PSE (Page size extension)
                TSC (Time stamp counter)
                MSR (Model specific registers)
                PAE (Physical address extension)
                MCE (Machine check exception)
                CX8 (CMPXCHG8 instruction supported)
                APIC (On-chip APIC hardware supported)
                SEP (Fast system call)
                MTRR (Memory type range registers)
                PGE (Page global enable)
                MCA (Machine check architecture)
                CMOV (Conditional move instruction supported)
                PAT (Page attribute table)
                PSE-36 (36-bit page size extension)
                CLFSH (CLFLUSH instruction supported)
                DS (Debug store)
                ACPI (ACPI supported)
                MMX (MMX technology supported)
                FXSR (FXSAVE and FXSTOR instructions supported)
                SSE (Streaming SIMD extensions)
                SSE2 (Streaming SIMD extensions 2)
                SS (Self-snoop)
                HTT (Multi-threading)
                TM (Thermal monitor supported)
                PBE (Pending break enabled)
        Version: Intel(R) Core(TM) i3 CPU 530 @ 2.93GHz              
        Voltage: 1.0 V
        External Clock: 133 MHz
        Max Speed: 3800 MHz
        Current Speed: 2933 MHz
        Status: Populated, Enabled
        Upgrade: Other
        L1 Cache Handle: 0x0005
        L2 Cache Handle: 0x0006
        L3 Cache Handle: 0x0007
        Serial Number: To Be Filled By O.E.M.
        Asset Tag: To Be Filled By O.E.M.
        Part Number: To Be Filled By O.E.M.
        Core Count: 2
        Core Enabled: 2
        Thread Count: 4
        Characteristics:
                64-bit capable


```

May an update of the BIOS fix it?

[EDIT]
I just figured out that my motherboard is running the newest BIOS version, i.e. 0602 : [http://support.asus.com/download.aspx?SLanguage=en&p=1&s=32&m=P7H55-M%2fBR&os=&hashedid=VrIElEVsZT8ok6lq](http://support.asus.com/download.aspx?SLanguage=en&p=1&s=32&m=P7H55-M%2fBR&os=&hashedid=VrIElEVsZT8ok6lq)

---

### Post by Yellow Pasque on 2013-02-25
A BIOS update could fix it, but Asus' site is being painfully uncooperative for me at the moment, so I can't check the changelog.

---

### Post by Plinio Santos on 2013-02-25
> **Temüjin said:**
> A BIOS update could fix it, but Asus' site is being painfully uncooperative for me at the moment, so I can't check the changelog.

I figured out that the motherboard is already runing with the latest BIOS version: 
[http://support.asus.com/download.aspx?SLanguage=en&p=1&s=32&m=P7H55-M%2fBR&os=&hashedid=VrIElEVsZT8ok6lq](http://support.asus.com/download.aspx?SLanguage=en&p=1&s=32&m=P7H55-M%2fBR&os=&hashedid=VrIElEVsZT8ok6lq)

---

### Post by Gyokuro on 2013-02-25
> **Plinio Santos said:**
> I installed Ubuntu 12.04 LTE in a machine that has an intel i3 processor. As far as I know, i3 processor is a multicore one and the OS should recognize 2 processors, just as Windows 7 does. Ubuntu 12 isn't recognizing it though. Is it a know issue? Have I missed some configuration?

the output of```
$ cat /proc/cpuinfo
```is:
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 37
model name      : Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz
stepping        : 2
microcode       : 0x9
cpu MHz         : 2933.374
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc up arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips        : 5866.74
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```[ EDIT ]
Adding new info. The output of ```
$ lscpu
```is:
```

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              2
CPU MHz:               2933.196
BogoMIPS:              5866.39
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K
NUMA node0 CPU(s):     0

```

Looking at your posted /proc/cpuinfo both cores got detected (0+1 but HT is missing) but what I can not find whether you have installed i386 or amd64 version of 12.04 LTS.  That will be interesting and a complete dump of your dmesg.

dmesg > dmesg.txt

As you have this cpu: [http://ark.intel.com/products/46472/Intel-Core-i3-530-Processor-4M-Cache-2_93-GHz](http://ark.intel.com/products/46472/Intel-Core-i3-530-Processor-4M-Cache-2_93-GHz)

also HT is not shown as you should have dual core + 2 HT = 4.

---

### Post by Plinio Santos on 2013-02-28
> **Gyokuro said:**
> Looking at your posted /proc/cpuinfo both cores got detected (0+1 but HT is missing) but what I can not find whether you have installed i386 or amd64 version of 12.04 LTS.
 
I'm using amd64 version.

>  That will be interesting and a complete dump of your dmesg.

dmesg > dmesg.txt



Log attached.

---

### Post by beejee on 2013-03-01
I believe this is your problem:

```

[    0.000000] ACPI: No APIC-table, disabling MPS
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
```

can you try passing acpi=off to grub and check the results?

---

### Post by beejee on 2013-03-01
> **Plinio Santos said:**
> 
Power: I think it does not matter, but how knows... :)
all config related with ACPI (around 4 config options) - disabled

Also, did you have this off or did you turn off the ACPI to find the cause of the missing cores in linux?

---

### Post by Plinio Santos on 2013-03-05
> **beejee said:**
> ... did you have this off or did you turn off the ACPI to find the cause of the missing cores in linux?

Those configs have always being set to disable.

I cant reboot this machine right now But will test with these changes and post the results as soon as possible, including use acpi=off in kernel command line.

---

### Post by Plinio Santos on 2013-03-06
> **beejee said:**
> Also, did you have this off or did you turn off the ACPI to find the cause of the missing cores in linux?

Uhuu! Amazing inside!
I enabled ACPI options in BIOS power section and Ubuntu is recognizing 4 CPUs now!

Thanks every one!

```

$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 37
Stepping:              2
CPU MHz:               1200.000
BogoMIPS:              5866.47
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K
NUMA node0 CPU(s):     0-3

```

---

