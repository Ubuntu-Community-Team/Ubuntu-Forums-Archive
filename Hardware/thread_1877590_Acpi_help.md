---
title: "Acpi help"
date: 2011-11-08
forum: Hardware
---

### Post by TREESofRIGHTEOUSNESS on 2011-11-08
Hi, over the past year or so, I have tried often to resolve this issue, I have searched for a long time, and so forth, but I really just need some FIX
here's the problem...
I can only boot using acpi=off
which I think is a bad deal to turn it off completely.
I have tried NUMEROUS other options...
acpi=force
noacpi
noapic
nolapic
acpi=oldboot
acpi=ht
pci=routeirq
and many others....

SO, HOW do I find out what the problem is?
I ran "sudo dmidecode"  (SEE attachment)
and found my BIOS supports acpi, so I would like to know what else I can do, how I can fix this, or how I can debug it myself.  ANY real help is VERY welcome...

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-08
Can anyone help???

---

### Post by Redblade20XX on 2011-11-08
How old is the computer? Motherboard specs? Is it an OEM or a custom made? Any additional hardware you installed? Since it seems to be a kernel problem, due to changes included in the grub for kernel parameters, it might be hardware related.

- Red

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-08
> **Redblade20XX said:**
> How old is the computer? Motherboard specs? Is it an OEM or a custom made? Any additional hardware you installed? Since it seems to be a kernel problem, due to changes included in the grub for kernel parameters, it might be hardware related.

- Red

lscpi puts out this
```
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

```cat /proc/cpuinfo puts out this
```
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 4
model name    : AMD Athlon(tm) 64 Processor 3200+
stepping    : 8
cpu MHz        : 797.906
cache size    : 1024 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up
bogomips    : 1595.81
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

```and here is the DMI decode
```
# dmidecode 2.9
SMBIOS 2.31 present.
20 structures occupying 631 bytes.
Table at 0x000F0C10.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: Hewlett-Packard 
    Version: F.11
    Release Date: 04/30/2004
    Address: 0xE3690
    Runtime Size: 117104 bytes
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
    Manufacturer: Hewlett-Packard 
    Product Name: Presario R3200 (PF153UA#ABA)  
    Version: F.11
    Serial Number: CND4240WPW
    UUID: 4CF29E6B-B68E-11D8-A3CB-000FB0010731
    Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Compal 
    Product Name: 08A0
    Version: 32.22
    Serial Number: CND4240WPW

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
    Manufacturer: Compal 
    Type: Notebook
    Lock: Not Present
    Version: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Boot-up State: Unknown
    Power Supply State: Unknown
    Thermal State: Unknown
    Security Status: Unknown
    OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: Socket A
    Type: Central Processor
    Family: Athlon 64
    Manufacturer: AMD
    ID: 48 0F 00 00 FF F9 8B 07
    Signature: Family 15, Model 4, Stepping 8
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
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        MMX (MMX technology supported)
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
    Version: AMD Athlon(tm) 64
    Voltage: 1.6 V
    External Clock: 133 MHz
    Max Speed: 2000 MHz
    Current Speed: 800 MHz
    Status: Populated, Enabled
    Upgrade: None
    L1 Cache Handle: 0x0008
    L2 Cache Handle: 0x0009
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: 128-bit ECC
    Error Correcting Capabilities:
        Other
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 4096 MB
    Maximum Total Memory Size: 8192 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        SDRAM
    Memory Module Voltage: 3.3 V
    Associated Memory Slots: 2
        0x0006
        0x0007
    Enabled Error Correcting Capabilities:
        Unknown

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIM0
    Bank Connections: 1 0
    Current Speed: 10 ns
    Type: DIMM SDRAM
    Installed Size: 256 MB (Double-bank Connection)
    Enabled Size: 256 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIM1
    Bank Connections: 3 2
    Current Speed: 10 ns
    Type: DIMM SDRAM
    Installed Size: 256 MB (Double-bank Connection)
    Enabled Size: 256 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 64 KB
    Maximum Size: 64 KB
    Supported SRAM Types:
        Burst
        Pipeline Burst
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 1024 KB
    Maximum Size: 512 KB
    Supported SRAM Types:
        Burst
        Pipeline Burst
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unified
    Associativity: Unknown

Handle 0x000A, DMI type 9, 13 bytes
System Slot Information
    Designation: AGP Slot
    Type: 32-bit AGP 2x
    Current Usage: Unknown
    Length: Long
    ID: 0
    Characteristics:
        3.3 V is provided
        PME signal is supported

Handle 0x000B, DMI type 11, 5 bytes
OEM Strings
    String 1: 0
    String 2: 0
    String 3: .........................

Handle 0x000C, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x000D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000C
    Error Information Handle: No Error
    Total Width: 32 bits
    Data Width: 32 bits
    Size: 256 MB
    Form Factor: DIMM
    Set: 1
    Locator: S1
    Bank Locator: Bank 1
    Type: DRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x000E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000C
    Error Information Handle: No Error
    Total Width: 32 bits
    Data Width: 32 bits
    Size: 256 MB
    Form Factor: DIMM
    Set: 2
    Locator: S2
    Bank Locator: Bank 2
    Type: DRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x000F, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0001FFFFFFF
    Range Size: 512 MB
    Physical Array Handle: 0x000C
    Partition Width: 0

Handle 0x0010, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0000FFFFFFF
    Range Size: 256 MB
    Physical Device Handle: 0x000D
    Memory Array Mapped Address Handle: 0x000F
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x0011, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00010000000
    Ending Address: 0x0001FFFFFFF
    Range Size: 256 MB
    Physical Device Handle: 0x000E
    Memory Array Mapped Address Handle: 0x000F
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x0012, DMI type 32, 20 bytes
System Boot Information
    Status: <OUT OF SPEC>

Handle 0x0013, DMI type 127, 4 bytes
End Of Table

```

Thanks!!!

---

### Post by Toz on 2011-11-08
What exactly happens when you try to boot without the acpi=off parameter?

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-09
The computer locks, and sits there until I manually turn it off (which I do not like to do... for obvious reasons)
The screen says something like

Running /scripts/init-bottom...done.
3.548122  firewire_core: created device fw0: GUID 463f0200463f0300s400
5.140033 floppy0:no floppy controllers found

it hangs on firewire, or floppy.
If I change the parameters and try to boot with acpi=off it will hang on the first boot usually.

I am not sure what the problem is, but I don't think it really is the absence of a floppy or the firewire port's existence causing the problem.

Thanks for attending to my issue I really appreciate this.  it has been frustrating trying to research this issue... though I have learned a lot, and I think you will probably educate me more.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-09
Ok!
the screen shows something like

running /scripts/init-bottom ...done.
3.548122  firewire_core: created device fw0: GUID 463f0200463f0300s400
5.140033  floppy0:no floppy controllers found

It hangs either when the firewire line shows up, or the floppy.... though I think it isn't related to those...

One other detail, that might be important, I do not have a battery in my computer, I just run it off the cord.
Thanks

---

### Post by Toz on 2011-11-09
Is it a hang or a case of no graphics video (uninitialized video)? Can you Ctrl+Alt+F1 and get a text login screen? Have you tried booting with the **nomodeset** kernel parameter?

---

### Post by rj45 on 2011-11-10
Same problem has been happening to me since 11.04 (grub 1.99)  with a HP DM4 laptop.  It's a problem with grub setting video modes and DKMS.  The only way I can reliably boot is with the kernel arg "acpi=off".

---

### Post by Toz on 2011-11-10
@rj45, looks like the DM4 has the hybrid (dual video card) setup. There are numerous threads on this board about getting that kind of setup to work. Just googled and also found this: [http://linux-hybrid-graphics.blogspot.com/2010/08/howto-linux-hybrid-graphics-hp-pavilion.html]("http://linux-hybrid-graphics.blogspot.com/2010/08/howto-linux-hybrid-graphics-hp-pavilion.html").

Other links: 
- [http://ubuntuforums.org/showthread.php?t=1849051&highlight=dm4]("http://ubuntuforums.org/showthread.php?t=1849051&highlight=dm4")
- [http://ubuntuforums.org/showthread.php?t=1843089&highlight=dm4]("http://ubuntuforums.org/showthread.php?t=1843089&highlight=dm4") (see last post)

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-10
I'm pretty sure I've done the Ctrl+Alt+F1...  I tried all the key combos I could think of, but the computer just hangs there, the light for the HD just stays off (so it is inactive).  I have tried nomodeset, as well, and xforcevesa...  but I get the same result.
So far the only parameter that has worked is acpi=off...  but if you know one I haven't done, I would love to get this working.  The strange thing is, when I have used puppylinux on this computer, I don't need acpi=off, and it boots fine.  (I have used lupu and slacko )

I have tried a lot of other distros and have the same issue... so I am pretty convinced it is something in the kernel.
But... I am no programmer....

---

### Post by rj45 on 2011-11-10
> **Toz said:**
> @rj45, looks like the DM4 has the hybrid (dual video card) setup. There are numerous threads on this board about getting that kind of setup to work. Just googled and also found this: [http://linux-hybrid-graphics.blogspot.com/2010/08/howto-linux-hybrid-graphics-hp-pavilion.html]("http://linux-hybrid-graphics.blogspot.com/2010/08/howto-linux-hybrid-graphics-hp-pavilion.html").

Other links: 
- [http://ubuntuforums.org/showthread.php?t=1849051&highlight=dm4]("http://ubuntuforums.org/showthread.php?t=1849051&highlight=dm4")
- [http://ubuntuforums.org/showthread.php?t=1843089&highlight=dm4]("http://ubuntuforums.org/showthread.php?t=1843089&highlight=dm4") (see last post)

Thanks Toz!
I am not concerned with dual graphic card issues - I could turn off the ATI card permanently and not miss it.
Just like the original poster, my laptop locks up hard if I don't use the "acpi=off" parameter.  I reserched this at length, and spent many hours troubleshooting - it's due to the changes in GRUB2 that makes graphic calls to DKMS before the main graphics drivers ever get loaded.  Haven't found a good solution yet.  Loaded 11.10 from scratch yesterday, and determined to fix it.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-10
If it were just the GRUB2, I wouldn't be able to boot puppy w/o the acpi=off option.  But I have booted puppy (installed in a separate partition on the HD) from the GRUB2 screen.  I believe it is in the kernel not in GRUB2.  Because Lucid Puppy and Slackopuppy both boot fine... and they use older kernels.
I think it uses 2.6.37-{6?}. something...  The first Ubuntu (I have installed Ubuntu, Lubuntu, and Xubuntu on it at different times.. to find the fastest one for that computer) I installed on it was 10.04 which used 2.6.38-{8?} or something like that.
I may very well be wrong on the kernel issue... I looked @ kernel.org to find that kernel.... but it goes from 2.6.34.10 --> 2.6.38.8
Can I run the older kernel with 11.10 somehow?  it seems like there are very likely some things in the newer kernel that are needed to load 11.10...  but I am no programmer.

---

### Post by Toz on 2011-11-11
> **TREESofRIGHTEOUSNESS said:**
> I'm pretty sure I've done the Ctrl+Alt+F1...  I tried all the key combos I could think of, but the computer just hangs there, the light for the HD just stays off (so it is inactive).  I have tried nomodeset, as well, and xforcevesa...  but I get the same result.
So far the only parameter that has worked is acpi=off...  but if you know one I haven't done, I would love to get this working.  The strange thing is, when I have used puppylinux on this computer, I don't need acpi=off, and it boots fine.  (I have used lupu and slacko )

I have tried a lot of other distros and have the same issue... so I am pretty convinced it is something in the kernel.
But... I am no programmer....

It would be interesting to see your dmesg log file. Can you try booting without the acpi=off parameter again (the system will hang), then restart and login with acpi=off. Then post back the files /var/log/dmesg and /var/log/dmesg.0.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
I booted with acpi=off and nomodeset, but it still hung this time..do you want me to post that?

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
OK, I rebooted w/o acpi=off and it hung up, and then rebooted, and it hung again... and rebooted and now I am posting....

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Hewlett-Packard  Presario R3200 (PF153UA#ABA)  /08A0, BIOS F.11 04/30/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-D3FFF write-back
[    0.000000]   D4000-D4FFF write-protect
[    0.000000]   D5000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff70000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff70000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 1e404000 - 1f102000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff70000
[    0.000000]   low ram: 0 - 1ff70000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff70
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ff70
[    0.000000] On node 0 totalpages: 130815
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map dfb6f200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dff80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @df400000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b61c59af-7f66-4df5-b2d5-928314a8ddd3 ro acpi=off
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2094592 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 493808k/523712k available (5329k kernel code, 29452k reserved, 2589k data, 696k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=de006000 soft=de008000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 797.800 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 1595.60 BogoMIPS (lpj=3191200)
[    0.004159] pid_max: default: 32768 minimum: 301
[    0.004292] Security Framework initialized
[    0.004417] AppArmor: AppArmor initialized
[    0.004490] Yama: becoming mindful.
[    0.004717] Mount-cache hash table entries: 512
[    0.005112] Initializing cgroup subsys cpuacct
[    0.005198] Initializing cgroup subsys memory
[    0.005291] Initializing cgroup subsys devices
[    0.005367] Initializing cgroup subsys freezer
[    0.005442] Initializing cgroup subsys net_cls
[    0.005517] Initializing cgroup subsys blkio
[    0.005604] Initializing cgroup subsys perf_event
[    0.005742] mce: CPU supports 5 MCE banks
[    0.006327] SMP alternatives: switching to UP code
[    0.028631] Freeing SMP alternatives: 24k freed
[    0.028741] ftrace: allocating 24885 entries in 49 pages
[    0.032163] weird, boot CPU (#0) not listed by the BIOS.
[    0.032242] SMP motherboard not detected.
[    0.032314] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.140030] SMP disabled
[    0.140098] Performance Events: AMD PMU driver.
[    0.140225] ... version:                0
[    0.140294] ... bit width:              48
[    0.140364] ... generic registers:      4
[    0.140434] ... value mask:             0000ffffffffffff
[    0.140506] ... max period:             00007fffffffffff
[    0.140578] ... fixed-purpose events:   0
[    0.140648] ... event mask:             000000000000000f
[    0.141759] Brought up 1 CPUs
[    0.141829] Total of 1 processors activated (1595.60 BogoMIPS).
[    0.142144] devtmpfs: initialized
[    0.142557] PM: Registering ACPI NVS region at 1ff7f000 (4096 bytes)
[    0.148123] print_constraints: dummy: 
[    0.148225] Time: 13:14:00  Date: 11/11/11
[    0.148380] NET: Registered protocol family 16
[    0.148768] EISA bus registered
[    0.148845] node 0 link 0: io port [1000, fffff]
[    0.148854] TOM: 0000000020000000 aka 512M
[    0.148928] node 0 link 0: mmio [a0000, bffff]
[    0.148936] node 0 link 0: mmio [20000000, fe0bffff]
[    0.148944] bus: [00, ff] on node 0 link 0
[    0.148953] bus: 00 index 0 [io  0x0000-0xffff]
[    0.148960] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.148966] bus: 00 index 2 [mem 0x20000000-0xffffffff]
[    0.149325] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[    0.149400] PCI: Using configuration type 1 for base access
[    0.152489] bio: create slab <bio-0> at 0
[    0.152761] ACPI: Interpreter disabled.
[    0.152972] vgaarb: loaded
[    0.153630] SCSI subsystem initialized
[    0.153801] libata version 3.00 loaded.
[    0.153916] usbcore: registered new interface driver usbfs
[    0.154016] usbcore: registered new interface driver hub
[    0.154147] usbcore: registered new device driver usb
[    0.154442] PCI: Probing PCI hardware
[    0.154513] PCI: Probing PCI hardware (bus 00)
[    0.154602] pci 0000:00:00.0: [10de:00d1] type 0 class 0x000600
[    0.154620] pci 0000:00:00.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.154697] pci 0000:00:01.0: [10de:00d0] type 0 class 0x000601
[    0.154762] pci 0000:00:01.1: [10de:00d4] type 0 class 0x000c05
[    0.154800] pci 0000:00:01.1: reg 20: [io  0x2040-0x207f]
[    0.154813] pci 0000:00:01.1: reg 24: [io  0x2000-0x203f]
[    0.154838] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.154847] pci 0000:00:01.1: PME# disabled
[    0.154876] pci 0000:00:02.0: [10de:00d7] type 0 class 0x000c03
[    0.154894] pci 0000:00:02.0: reg 10: [mem 0xe0000000-0xe0000fff]
[    0.154943] pci 0000:00:02.0: supports D1 D2
[    0.154950] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.154958] pci 0000:00:02.0: PME# disabled
[    0.154983] pci 0000:00:02.1: [10de:00d7] type 0 class 0x000c03
[    0.155001] pci 0000:00:02.1: reg 10: [mem 0xe0001000-0xe0001fff]
[    0.155050] pci 0000:00:02.1: supports D1 D2
[    0.155057] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.155065] pci 0000:00:02.1: PME# disabled
[    0.155088] pci 0000:00:02.2: [10de:00d8] type 0 class 0x000c03
[    0.155106] pci 0000:00:02.2: reg 10: [mem 0xe0004000-0xe00040ff]
[    0.155155] pci 0000:00:02.2: supports D1 D2
[    0.155162] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.155170] pci 0000:00:02.2: PME# disabled
[    0.155202] pci 0000:00:06.0: [10de:00da] type 0 class 0x000401
[    0.155219] pci 0000:00:06.0: reg 10: [io  0x1400-0x14ff]
[    0.155232] pci 0000:00:06.0: reg 14: [io  0x1c00-0x1c7f]
[    0.155245] pci 0000:00:06.0: reg 18: [mem 0xe0002000-0xe0002fff]
[    0.155283] pci 0000:00:06.0: supports D1 D2
[    0.155306] pci 0000:00:06.1: [10de:00d9] type 0 class 0x000703
[    0.155323] pci 0000:00:06.1: reg 10: [io  0x1800-0x18ff]
[    0.155336] pci 0000:00:06.1: reg 14: [io  0x1c80-0x1cff]
[    0.155348] pci 0000:00:06.1: reg 18: [mem 0xe0003000-0xe0003fff]
[    0.155388] pci 0000:00:06.1: PME# supported from D3cold
[    0.155396] pci 0000:00:06.1: PME# disabled
[    0.155425] pci 0000:00:08.0: [10de:00d5] type 0 class 0x000101
[    0.155462] pci 0000:00:08.0: reg 20: [io  0x2080-0x208f]
[    0.155507] pci 0000:00:0a.0: [10de:00dd] type 1 class 0x000604
[    0.155547] pci 0000:00:0b.0: [10de:00d2] type 1 class 0x000604
[    0.155612] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.155659] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.155697] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.155735] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.155774] PCI: peer root bus 00 res updated from pci conf
[    0.155809] pci 0000:02:00.0: [104c:8026] type 0 class 0x000c00
[    0.155832] pci 0000:02:00.0: reg 10: [mem 0xe0108000-0xe01087ff]
[    0.155848] pci 0000:02:00.0: reg 14: [mem 0xe0100000-0xe0103fff]
[    0.155909] pci 0000:02:00.0: supports D1 D2
[    0.155915] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.155924] pci 0000:02:00.0: PME# disabled
[    0.155951] pci 0000:02:01.0: [10ec:8139] type 0 class 0x000200
[    0.155973] pci 0000:02:01.0: reg 10: [io  0x7000-0x70ff]
[    0.155988] pci 0000:02:01.0: reg 14: [mem 0xe0108800-0xe01088ff]
[    0.156057] pci 0000:02:01.0: supports D1 D2
[    0.156063] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.156073] pci 0000:02:01.0: PME# disabled
[    0.156096] pci 0000:02:02.0: [14e4:4320] type 0 class 0x000280
[    0.156114] pci 0000:02:02.0: reg 10: [mem 0xe0104000-0xe0105fff]
[    0.156187] pci 0000:02:04.0: [104c:ac54] type 2 class 0x000607
[    0.156210] pci 0000:02:04.0: reg 10: [mem 0xe0106000-0xe0106fff]
[    0.156233] pci 0000:02:04.0: supports D1 D2
[    0.156240] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156249] pci 0000:02:04.0: PME# disabled
[    0.156275] pci 0000:02:04.1: [104c:ac54] type 2 class 0x000607
[    0.156298] pci 0000:02:04.1: reg 10: [mem 0xe0107000-0xe0107fff]
[    0.156322] pci 0000:02:04.1: supports D1 D2
[    0.156328] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156337] pci 0000:02:04.1: PME# disabled
[    0.156365] pci 0000:02:04.2: [104c:8201] type 0 class 0x000880
[    0.156385] pci 0000:02:04.2: reg 10: [io  0x7400-0x743f]
[    0.156494] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.156569] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.156579] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.156589] pci 0000:00:0a.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.156641] pci_bus 0000:03: [bus 03-06] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.156769] pci_bus 0000:07: [bus 07-0a] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.156894] pci 0000:01:00.0: [10de:0179] type 0 class 0x000300
[    0.156920] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
[    0.156937] pci 0000:01:00.0: reg 14: [mem 0xf0000000-0xf7ffffff pref]
[    0.156954] pci 0000:01:00.0: reg 18: [mem 0xf8000000-0xf807ffff pref]
[    0.156995] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.157074] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.157150] pci 0000:00:0b.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.157160] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.157170] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.158873] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.159124] pci 0000:00:01.0: default IRQ router [10de:00d0]
[    0.159260] PCI: pci_cache_line_size set to 64 bytes
[    0.159366] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.159374] reserve RAM buffer: 000000001ff70000 - 000000001fffffff 
[    0.159632] NetLabel: Initializing
[    0.159701] NetLabel:  domain hash size = 128
[    0.159771] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.159866] NetLabel:  unlabeled traffic allowed by default
[    0.177675] AppArmor: AppArmor Filesystem Enabled
[    0.177795] pnp: PnP ACPI: disabled
[    0.177866] PnPBIOS: Scanning system for PnP BIOS support...
[    0.177976] PnPBIOS: Found PnP BIOS installation structure at 0xc00f72c0
[    0.178054] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb71e, dseg 0x400
[    0.179000] pnp 00:00: [mem 0x00000000-0xffffffff disabled]
[    0.179008] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.179015] pnp 00:00: [mem 0x00100000-0x1ff7ffff]
[    0.179126] system 00:00: Plug and Play BIOS device, IDs PNP0c01 (disabled)
[    0.179144] pnp 00:01: [io  0x0000-0x000f]
[    0.179151] pnp 00:01: [io  0x0081-0x008f]
[    0.179157] pnp 00:01: [io  0x00c0-0x00df]
[    0.179164] pnp 00:01: [dma 4]
[    0.179218] pnp 00:01: Plug and Play BIOS device, IDs PNP0200 (active)
[    0.179234] pnp 00:02: [io  0x0020-0x0021]
[    0.179240] pnp 00:02: [io  0x00a0-0x00a1]
[    0.179248] pnp 00:02: [irq 2]
[    0.179294] pnp 00:02: Plug and Play BIOS device, IDs PNP0000 (active)
[    0.179309] pnp 00:03: [io  0x0040-0x0043]
[    0.179315] pnp 00:03: [irq 0]
[    0.179361] pnp 00:03: Plug and Play BIOS device, IDs PNP0100 (active)
[    0.179377] pnp 00:04: [io  0x0070-0x0071]
[    0.179383] pnp 00:04: [irq 8]
[    0.179429] pnp 00:04: Plug and Play BIOS device, IDs PNP0b00 (active)
[    0.179444] pnp 00:05: [io  0x0060]
[    0.179450] pnp 00:05: [io  0x0064]
[    0.179456] pnp 00:05: [irq 1]
[    0.179502] pnp 00:05: Plug and Play BIOS device, IDs PNP0303 (active)
[    0.179518] pnp 00:06: [io  0x00f0-0x00ff]
[    0.179524] pnp 00:06: [irq 13]
[    0.179578] pnp 00:06: Plug and Play BIOS device, IDs PNP0c04 (active)
[    0.179593] pnp 00:07: [io  0x0061]
[    0.179640] pnp 00:07: Plug and Play BIOS device, IDs PNP0800 (active)
[    0.179657] pnp 00:08: [mem 0x000d0000-0x000d3fff]
[    0.179745] system 00:08: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.179825] system 00:08: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.179841] pnp 00:09: [io  0xfe00-0xfe01]
[    0.179934] system 00:09: [io  0xfe00-0xfe01] has been reserved
[    0.180020] system 00:09: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.180037] pnp 00:0a: [io  0x0cf8-0x0cff]
[    0.180087] pnp 00:0a: Plug and Play BIOS device, IDs PNP0a03 (active)
[    0.180104] pnp 00:0b: [io  0x004e-0x004f]
[    0.180202] system 00:0b: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.180356] pnp 00:0c: [mem 0x000cfc00-0x000cffff]
[    0.180443] system 00:0c: [mem 0x000cfc00-0x000cffff] has been reserved
[    0.180522] system 00:0c: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.181176] pnp 00:0e: [irq 12]
[    0.181234] pnp 00:0e: Plug and Play BIOS device, IDs PNP0f13 (active)
[    0.182253] pnp 00:12: [io  0x0378-0x037f]
[    0.182260] pnp 00:12: [io  0x0778-0x077f]
[    0.182266] pnp 00:12: [irq 7]
[    0.182272] pnp 00:12: [dma 1]
[    0.182400] pnp 00:12: Plug and Play BIOS device, IDs PNP0401 (active)
[    0.182411] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[    0.186958] PCI: max bus depth: 2 pci_try_num: 3
[    0.186995] pci 0000:00:0a.0: BAR 15: assigned [mem 0x20000000-0x27ffffff pref]
[    0.187096] pci 0000:02:04.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.187191] pci 0000:02:04.0: BAR 16: can't assign mem (size 0x4000000)
[    0.187269] pci 0000:02:04.1: BAR 15: assigned [mem 0x24000000-0x27ffffff pref]
[    0.187363] pci 0000:02:04.1: BAR 16: can't assign mem (size 0x4000000)
[    0.187440] pci 0000:02:04.0: BAR 13: assigned [io  0x3000-0x30ff]
[    0.187517] pci 0000:02:04.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.187593] pci 0000:02:04.1: BAR 13: assigned [io  0x3800-0x38ff]
[    0.187669] pci 0000:02:04.1: BAR 14: assigned [io  0x3c00-0x3cff]
[    0.187745] pci 0000:02:04.0: CardBus bridge to [bus 03-06]
[    0.187820] pci 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[    0.187899] pci 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[    0.187977] pci 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.188020] pci 0000:02:04.1: CardBus bridge to [bus 07-0a]
[    0.188094] pci 0000:02:04.1:   bridge window [io  0x3800-0x38ff]
[    0.188171] pci 0000:02:04.1:   bridge window [io  0x3c00-0x3cff]
[    0.188249] pci 0000:02:04.1:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.188343] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.188417] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.188495] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.188574] pci 0000:00:0a.0:   bridge window [mem 0x20000000-0x27ffffff pref]
[    0.188671] pci 0000:01:00.0: BAR 6: assigned [mem 0xf8080000-0xf809ffff pref]
[    0.188764] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.188837] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.188914] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.188994] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.189098] pci 0000:00:0a.0: setting latency timer to 64
[    0.189131] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.189139] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.189147] pci_bus 0000:00: resource 6 [mem 0x20000000-0xffffffff]
[    0.189155] pci_bus 0000:02: resource 0 [io  0x3000-0x7fff]
[    0.189162] pci_bus 0000:02: resource 1 [mem 0xe0100000-0xe17fffff]
[    0.189170] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.189178] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.189185] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.189193] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.189200] pci_bus 0000:07: resource 0 [io  0x3800-0x38ff]
[    0.189207] pci_bus 0000:07: resource 1 [io  0x3c00-0x3cff]
[    0.189215] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.189223] pci_bus 0000:01: resource 1 [mem 0xe2000000-0xe2ffffff]
[    0.189231] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf80fffff pref]
[    0.189323] NET: Registered protocol family 2
[    0.189530] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.190078] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.190357] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.190624] TCP: Hash tables configured (established 16384 bind 16384)
[    0.190699] TCP reno registered
[    0.192020] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.192105] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.192335] NET: Registered protocol family 1
[    0.336104] PCI: CLS mismatch (64 != 32), using 64 bytes
[    0.336129] pci 0000:01:00.0: Boot video device
[    0.336800] audit: initializing netlink socket (disabled)
[    0.336887] type=2000 audit(1321017240.336:1): initialized
[    0.396665] Trying to unpack rootfs image as initramfs...
[    0.468219] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.477355] VFS: Disk quotas dquot_6.5.2
[    0.477582] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.484170] fuse init (API version 7.16)
[    0.484496] msgmni has been set to 964
[    0.496800] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.496958] io scheduler noop registered
[    0.497028] io scheduler deadline registered
[    0.497134] io scheduler cfq registered (default)
[    0.497586] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.497727] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.498145] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.501726] Linux agpgart interface v0.103
[    0.501853] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[    0.501934] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    0.502033] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    0.509135] isapnp: Scanning for PnP cards...
[    0.568819] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.576743] brd: module loaded
[    0.578394] loop: module loaded
[    0.578961] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.579988] Fixed MDIO Bus: probed
[    0.580116] PPP generic driver version 2.4.2
[    0.580285] tun: Universal TUN/TAP device driver, 1.6
[    0.580357] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.580615] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.580736] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    0.580744] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    0.580914] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.581058] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    0.581079] ehci_hcd 0000:00:02.2: irq 10, io mem 0xe0004000
[    0.592501] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.592926] hub 1-0:1.0: USB hub found
[    0.593004] hub 1-0:1.0: 6 ports detected
[    0.593242] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.593365] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.593374] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.593533] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.593652] ohci_hcd 0000:00:02.0: irq 11, io mem 0xe0000000
[    0.677024] hub 2-0:1.0: USB hub found
[    0.677110] hub 2-0:1.0: 3 ports detected
[    0.677362] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    0.677371] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    0.677537] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    0.677661] ohci_hcd 0000:00:02.1: irq 10, io mem 0xe0001000
[    0.742655] hub 3-0:1.0: USB hub found
[    0.742740] hub 3-0:1.0: 3 ports detected
[    0.742979] uhci_hcd: USB Universal Host Controller Interface driver
[    0.743282] i8042: PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.749347] i8042: Detected active multiplexing controller, rev 1.1
[    0.772618] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.772715] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.772883] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.773025] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.773159] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.773552] mousedev: PS/2 mouse device common for all mice
[    0.773922] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.774018] rtc0: alarms up to one day, 114 bytes nvram
[    0.774376] device-mapper: uevent: version 1.0.3
[    0.774640] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.774820] EISA: Probing bus 0 at eisa.0
[    0.774895] EISA: Cannot allocate resource for mainboard
[    0.774969] Cannot allocate resource for EISA slot 1
[    0.775042] Cannot allocate resource for EISA slot 2
[    0.775115] Cannot allocate resource for EISA slot 3
[    0.775187] Cannot allocate resource for EISA slot 4
[    0.775260] Cannot allocate resource for EISA slot 5
[    0.775333] Cannot allocate resource for EISA slot 6
[    0.775405] Cannot allocate resource for EISA slot 7
[    0.775478] Cannot allocate resource for EISA slot 8
[    0.775550] EISA: Detected 0 cards.
[    0.775634] cpufreq-nforce2: No nForce2 chipset.
[    0.775707] cpuidle: using governor ladder
[    0.775776] cpuidle: using governor menu
[    0.775846] EFI Variables Facility v0.08 2004-May-17
[    0.779473] TCP cubic registered
[    0.779917] NET: Registered protocol family 10
[    0.781364] NET: Registered protocol family 17
[    0.784358] Registering the dns_resolver key type
[    0.784467] Using IPI No-Shortcut mode
[    0.784760] PM: Hibernation image not present or could not be loaded.
[    0.784785] registered taskstats version 1
[    0.838991] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.088089] isapnp: No Plug & Play device found
[    1.296805] usb 2-2: new low speed USB device number 2 using ohci_hcd
[    1.396553] Switching to clocksource tsc
[    1.665928] Freeing initrd memory: 13304k freed
[    1.699184]   Magic number: 3:403:230
[    1.699378] rtc_cmos 00:04: setting system clock to 2011-11-11 13:14:02 UTC (1321017242)
[    1.699475] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    1.704338] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.704414] powernow-k8: Make sure that your BIOS is up to date and Cool'N'Quiet support is enabled in BIOS setup
[    1.704516] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.704588] EDD information not available.
[    1.704926] Freeing unused kernel memory: 696k freed
[    1.705835] Write protecting the kernel text: 5332k
[    1.705995] Write protecting the kernel read-only data: 2188k
[    1.745151] udevd[77]: starting version 173
[    1.918908] pata_amd 0000:00:08.0: version 0.4.1
[    1.919001] pata_amd 0000:00:08.0: setting latency timer to 64
[    1.965990] scsi0 : pata_amd
[    1.971732] scsi1 : pata_amd
[    1.986417] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    1.986504] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    2.013123] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.013248] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.027818] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.027833] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.027844] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.027854] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.027864] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.031268] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    2.340290] ata1.00: ATA-6: FUJITSU MHT2060AT PL, 0022, max UDMA/100
[    2.340376] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.340461] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x0
[    2.356195] ata1.00: configured for UDMA/100
[    2.356529] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    2.357005] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.357380] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.357585] sd 0:0:0:0: [sda] Write Protect is off
[    2.357660] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.357710] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.465427]  sda: sda1 sda2 < sda5 >
[    2.466138] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.536155] ata2.00: ATAPI: SD-R6252, 1A11, max MWDMA2
[    2.536236] ata2: nv_mode_filter: 0x39f&0xfffff->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x0
[    2.568094] ata2.00: configured for MWDMA2
[    2.574170] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6252 1A11 PQ: 0 ANSI: 5
[    2.578542] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.578620] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.578915] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.579042] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.581844] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.583537] 8139too 0000:02:01.0: eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:01:07:31, IRQ 10
[    2.593788] input: HID 04b3:310b as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input1
[    2.594134] generic-usb 0003:04B3:310B.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:02.0-2/input0
[    2.594270] usbcore: registered new interface driver usbhid
[    2.594343] usbhid: USB HID core driver
[    2.644074] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.004166] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.004250] EXT4-fs (sda1): write access will be enabled during recovery
[    3.070047] EXT4-fs (sda1): recovery complete
[    3.070653] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.144160] firewire_core: created device fw0: GUID 463f0200463f0200, S400
[   30.380407] udevd[260]: starting version 173
[   30.444689] lp: driver loaded but no devices found
[   30.509501] Adding 521212k swap on /dev/sda5.  Priority:-1 extents:1 across:521212k 
[   30.678547] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[   30.684063] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   30.747715] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[   30.992738] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.265073] type=1400 audit(1321017272.061:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=460 comm="apparmor_parser"
[   31.271647] type=1400 audit(1321017272.069:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
[   31.272416] type=1400 audit(1321017272.069:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=460 comm="apparmor_parser"
[   31.340161] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.385541] nf_conntrack version 0.5.0 (7934 buckets, 31736 max)
[   31.443472] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006d]
[   31.443504] yenta_cardbus 0000:02:04.0: CardBus bridge to [bus 03-06]
[   31.443514] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[   31.443525] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[   31.443536] yenta_cardbus 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[   31.443546] yenta_cardbus 0000:02:04.0:   bridge window [mem 0xe0400000-0xe07fffff]
[   31.443557] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   31.443567] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   31.443574] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   31.443585] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   31.445385] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   31.577583] cfg80211: Calling CRDA to update world regulatory domain
[   31.677281] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x02f8, PCI irq 11
[   31.677292] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   31.677302] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   31.677323] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   31.677333] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   31.810112] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input2
[   31.831780] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input3
[   31.889919] nvidia: module license 'NVIDIA' taints kernel.
[   31.889931] Disabling lock debugging due to kernel taint
[   32.021725]  0x7000-0x70ff 0x7400-0x743f
[   32.615997] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe0100000-0xe17fffff]
[   32.616012] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0100000-0xe17fffff: excluding 0xe0100000-0xe026ffff 0xe03e0000-0xe082ffff
[   32.616047] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   32.616057] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   32.653304] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006d]
[   32.653334] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   32.653343] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   32.653354] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   32.764026] 8139too 0000:02:01.0: eth0: link down
[   32.767222] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.788262] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   32.883874] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x02f8, PCI irq 10
[   32.883885] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   32.883895] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   32.883916] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   32.883926] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   32.893691] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   32.893703] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893711] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   32.893720] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893727] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   32.893735] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893742] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   32.893751] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893757] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   32.893766] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893773] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   32.893781] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893788] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   32.893796] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893803] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   32.893811] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893818] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   32.893827] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893834] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   32.893842] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893849] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   32.893857] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893864] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   32.893872] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893879] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   32.893888] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.893895] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   32.893903] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.948174] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   32.989848] type=1400 audit(1321017273.785:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=675 comm="apparmor_parser"
[   33.000988] type=1400 audit(1321017273.797:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=680 comm="apparmor_parser"
[   33.005093] type=1400 audit(1321017273.801:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=680 comm="apparmor_parser"
[   33.005867] type=1400 audit(1321017273.801:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=680 comm="apparmor_parser"
[   33.040845] Registered led device: b43-phy0::tx
[   33.040986] Registered led device: b43-phy0::rx
[   33.041101] Registered led device: b43-phy0::radio
[   33.041199] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   33.056340] type=1400 audit(1321017273.853:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=684 comm="apparmor_parser"
[   33.086109] type=1400 audit(1321017273.881:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=684 comm="apparmor_parser"
[   33.111727] type=1400 audit(1321017273.909:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=684 comm="apparmor_parser"
[   33.332310]  0x7000-0x70ff 0x7400-0x743f
[   33.528345] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0xe0100000-0xe17fffff]
[   33.528358] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe0100000-0xe17fffff: excluding 0xe0100000-0xe026ffff 0xe03e0000-0xe082ffff 0xe0b10000-0xe10cffff
[   33.528397] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   33.528406] pcmcia_socket pcmcia_socket1: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   33.981864] apm: BIOS not found.
[   34.041342] init: failsafe main process (719) killed by TERM signal
[   34.044288] init: apport pre-start process (760) terminated with status 1
[   34.050204] init: alsa-restore main process (769) terminated with status 19
[   34.145030] init: apport post-stop process (798) terminated with status 1
```

and dmesg.0

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Hewlett-Packard  Presario R3200 (PF153UA#ABA)  /08A0, BIOS F.11 04/30/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-D3FFF write-back
[    0.000000]   D4000-D4FFF write-protect
[    0.000000]   D5000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff70000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff70000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 1e041000 - 1ed3f000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff70000
[    0.000000]   low ram: 0 - 1ff70000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff70
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ff70
[    0.000000] On node 0 totalpages: 130815
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map dfb6f200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dff80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @df400000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b61c59af-7f66-4df5-b2d5-928314a8ddd3 ro acpi=off nomodeset
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2094592 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 493808k/523712k available (5329k kernel code, 29452k reserved, 2589k data, 696k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=df006000 soft=df008000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 797.843 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 1595.68 BogoMIPS (lpj=3191372)
[    0.004159] pid_max: default: 32768 minimum: 301
[    0.004292] Security Framework initialized
[    0.004416] AppArmor: AppArmor initialized
[    0.004490] Yama: becoming mindful.
[    0.004716] Mount-cache hash table entries: 512
[    0.005111] Initializing cgroup subsys cpuacct
[    0.005198] Initializing cgroup subsys memory
[    0.005291] Initializing cgroup subsys devices
[    0.005367] Initializing cgroup subsys freezer
[    0.005442] Initializing cgroup subsys net_cls
[    0.005517] Initializing cgroup subsys blkio
[    0.005604] Initializing cgroup subsys perf_event
[    0.005742] mce: CPU supports 5 MCE banks
[    0.006328] SMP alternatives: switching to UP code
[    0.028632] Freeing SMP alternatives: 24k freed
[    0.028743] ftrace: allocating 24885 entries in 49 pages
[    0.032163] weird, boot CPU (#0) not listed by the BIOS.
[    0.032242] SMP motherboard not detected.
[    0.032314] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.140030] SMP disabled
[    0.140098] Performance Events: AMD PMU driver.
[    0.140225] ... version:                0
[    0.140296] ... bit width:              48
[    0.140365] ... generic registers:      4
[    0.140435] ... value mask:             0000ffffffffffff
[    0.140508] ... max period:             00007fffffffffff
[    0.140580] ... fixed-purpose events:   0
[    0.140650] ... event mask:             000000000000000f
[    0.141760] Brought up 1 CPUs
[    0.141830] Total of 1 processors activated (1595.68 BogoMIPS).
[    0.142145] devtmpfs: initialized
[    0.142558] PM: Registering ACPI NVS region at 1ff7f000 (4096 bytes)
[    0.148123] print_constraints: dummy: 
[    0.148225] Time: 12:30:04  Date: 11/11/11
[    0.148378] NET: Registered protocol family 16
[    0.148768] EISA bus registered
[    0.148845] node 0 link 0: io port [1000, fffff]
[    0.148853] TOM: 0000000020000000 aka 512M
[    0.148928] node 0 link 0: mmio [a0000, bffff]
[    0.148936] node 0 link 0: mmio [20000000, fe0bffff]
[    0.148944] bus: [00, ff] on node 0 link 0
[    0.148953] bus: 00 index 0 [io  0x0000-0xffff]
[    0.148960] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.148966] bus: 00 index 2 [mem 0x20000000-0xffffffff]
[    0.149326] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[    0.149401] PCI: Using configuration type 1 for base access
[    0.152491] bio: create slab <bio-0> at 0
[    0.152763] ACPI: Interpreter disabled.
[    0.152974] vgaarb: loaded
[    0.153633] SCSI subsystem initialized
[    0.153805] libata version 3.00 loaded.
[    0.153919] usbcore: registered new interface driver usbfs
[    0.154020] usbcore: registered new interface driver hub
[    0.154151] usbcore: registered new device driver usb
[    0.154446] PCI: Probing PCI hardware
[    0.154518] PCI: Probing PCI hardware (bus 00)
[    0.154607] pci 0000:00:00.0: [10de:00d1] type 0 class 0x000600
[    0.154624] pci 0000:00:00.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.154702] pci 0000:00:01.0: [10de:00d0] type 0 class 0x000601
[    0.154767] pci 0000:00:01.1: [10de:00d4] type 0 class 0x000c05
[    0.154805] pci 0000:00:01.1: reg 20: [io  0x2040-0x207f]
[    0.154818] pci 0000:00:01.1: reg 24: [io  0x2000-0x203f]
[    0.154843] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.154852] pci 0000:00:01.1: PME# disabled
[    0.154881] pci 0000:00:02.0: [10de:00d7] type 0 class 0x000c03
[    0.154899] pci 0000:00:02.0: reg 10: [mem 0xe0000000-0xe0000fff]
[    0.154948] pci 0000:00:02.0: supports D1 D2
[    0.154955] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.154963] pci 0000:00:02.0: PME# disabled
[    0.154988] pci 0000:00:02.1: [10de:00d7] type 0 class 0x000c03
[    0.155006] pci 0000:00:02.1: reg 10: [mem 0xe0001000-0xe0001fff]
[    0.155055] pci 0000:00:02.1: supports D1 D2
[    0.155062] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.155070] pci 0000:00:02.1: PME# disabled
[    0.155093] pci 0000:00:02.2: [10de:00d8] type 0 class 0x000c03
[    0.155111] pci 0000:00:02.2: reg 10: [mem 0xe0004000-0xe00040ff]
[    0.155161] pci 0000:00:02.2: supports D1 D2
[    0.155167] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.155176] pci 0000:00:02.2: PME# disabled
[    0.155207] pci 0000:00:06.0: [10de:00da] type 0 class 0x000401
[    0.155225] pci 0000:00:06.0: reg 10: [io  0x1400-0x14ff]
[    0.155237] pci 0000:00:06.0: reg 14: [io  0x1c00-0x1c7f]
[    0.155250] pci 0000:00:06.0: reg 18: [mem 0xe0002000-0xe0002fff]
[    0.155289] pci 0000:00:06.0: supports D1 D2
[    0.155311] pci 0000:00:06.1: [10de:00d9] type 0 class 0x000703
[    0.155329] pci 0000:00:06.1: reg 10: [io  0x1800-0x18ff]
[    0.155341] pci 0000:00:06.1: reg 14: [io  0x1c80-0x1cff]
[    0.155354] pci 0000:00:06.1: reg 18: [mem 0xe0003000-0xe0003fff]
[    0.155393] pci 0000:00:06.1: PME# supported from D3cold
[    0.155401] pci 0000:00:06.1: PME# disabled
[    0.155431] pci 0000:00:08.0: [10de:00d5] type 0 class 0x000101
[    0.155468] pci 0000:00:08.0: reg 20: [io  0x2080-0x208f]
[    0.155513] pci 0000:00:0a.0: [10de:00dd] type 1 class 0x000604
[    0.155553] pci 0000:00:0b.0: [10de:00d2] type 1 class 0x000604
[    0.155618] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.155664] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.155703] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.155741] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.155779] PCI: peer root bus 00 res updated from pci conf
[    0.155815] pci 0000:02:00.0: [104c:8026] type 0 class 0x000c00
[    0.155838] pci 0000:02:00.0: reg 10: [mem 0xe0108000-0xe01087ff]
[    0.155854] pci 0000:02:00.0: reg 14: [mem 0xe0100000-0xe0103fff]
[    0.155915] pci 0000:02:00.0: supports D1 D2
[    0.155921] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.155930] pci 0000:02:00.0: PME# disabled
[    0.155957] pci 0000:02:01.0: [10ec:8139] type 0 class 0x000200
[    0.155978] pci 0000:02:01.0: reg 10: [io  0x7000-0x70ff]
[    0.155994] pci 0000:02:01.0: reg 14: [mem 0xe0108800-0xe01088ff]
[    0.156063] pci 0000:02:01.0: supports D1 D2
[    0.156070] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.156079] pci 0000:02:01.0: PME# disabled
[    0.156102] pci 0000:02:02.0: [14e4:4320] type 0 class 0x000280
[    0.156120] pci 0000:02:02.0: reg 10: [mem 0xe0104000-0xe0105fff]
[    0.156193] pci 0000:02:04.0: [104c:ac54] type 2 class 0x000607
[    0.156216] pci 0000:02:04.0: reg 10: [mem 0xe0106000-0xe0106fff]
[    0.156240] pci 0000:02:04.0: supports D1 D2
[    0.156246] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156256] pci 0000:02:04.0: PME# disabled
[    0.156282] pci 0000:02:04.1: [104c:ac54] type 2 class 0x000607
[    0.156305] pci 0000:02:04.1: reg 10: [mem 0xe0107000-0xe0107fff]
[    0.156328] pci 0000:02:04.1: supports D1 D2
[    0.156335] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.156344] pci 0000:02:04.1: PME# disabled
[    0.156371] pci 0000:02:04.2: [104c:8201] type 0 class 0x000880
[    0.156392] pci 0000:02:04.2: reg 10: [io  0x7400-0x743f]
[    0.156500] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.156576] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.156585] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.156595] pci 0000:00:0a.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.156648] pci_bus 0000:03: [bus 03-06] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.156776] pci_bus 0000:07: [bus 07-0a] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.156902] pci 0000:01:00.0: [10de:0179] type 0 class 0x000300
[    0.156928] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
[    0.156945] pci 0000:01:00.0: reg 14: [mem 0xf0000000-0xf7ffffff pref]
[    0.156961] pci 0000:01:00.0: reg 18: [mem 0xf8000000-0xf807ffff pref]
[    0.157003] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.157082] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.157158] pci 0000:00:0b.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.157168] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.157178] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.158880] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.159132] pci 0000:00:01.0: default IRQ router [10de:00d0]
[    0.159268] PCI: pci_cache_line_size set to 64 bytes
[    0.159375] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.159382] reserve RAM buffer: 000000001ff70000 - 000000001fffffff 
[    0.159640] NetLabel: Initializing
[    0.159709] NetLabel:  domain hash size = 128
[    0.159779] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.159875] NetLabel:  unlabeled traffic allowed by default
[    0.177691] AppArmor: AppArmor Filesystem Enabled
[    0.177810] pnp: PnP ACPI: disabled
[    0.177882] PnPBIOS: Scanning system for PnP BIOS support...
[    0.177993] PnPBIOS: Found PnP BIOS installation structure at 0xc00f72c0
[    0.178070] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb71e, dseg 0x400
[    0.179017] pnp 00:00: [mem 0x00000000-0xffffffff disabled]
[    0.179024] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.179032] pnp 00:00: [mem 0x00100000-0x1ff7ffff]
[    0.179143] system 00:00: Plug and Play BIOS device, IDs PNP0c01 (disabled)
[    0.179161] pnp 00:01: [io  0x0000-0x000f]
[    0.179167] pnp 00:01: [io  0x0081-0x008f]
[    0.179174] pnp 00:01: [io  0x00c0-0x00df]
[    0.179181] pnp 00:01: [dma 4]
[    0.179235] pnp 00:01: Plug and Play BIOS device, IDs PNP0200 (active)
[    0.179251] pnp 00:02: [io  0x0020-0x0021]
[    0.179257] pnp 00:02: [io  0x00a0-0x00a1]
[    0.179264] pnp 00:02: [irq 2]
[    0.179310] pnp 00:02: Plug and Play BIOS device, IDs PNP0000 (active)
[    0.179326] pnp 00:03: [io  0x0040-0x0043]
[    0.179332] pnp 00:03: [irq 0]
[    0.179378] pnp 00:03: Plug and Play BIOS device, IDs PNP0100 (active)
[    0.179394] pnp 00:04: [io  0x0070-0x0071]
[    0.179400] pnp 00:04: [irq 8]
[    0.179446] pnp 00:04: Plug and Play BIOS device, IDs PNP0b00 (active)
[    0.179461] pnp 00:05: [io  0x0060]
[    0.179467] pnp 00:05: [io  0x0064]
[    0.179473] pnp 00:05: [irq 1]
[    0.179519] pnp 00:05: Plug and Play BIOS device, IDs PNP0303 (active)
[    0.179535] pnp 00:06: [io  0x00f0-0x00ff]
[    0.179541] pnp 00:06: [irq 13]
[    0.179595] pnp 00:06: Plug and Play BIOS device, IDs PNP0c04 (active)
[    0.179610] pnp 00:07: [io  0x0061]
[    0.179657] pnp 00:07: Plug and Play BIOS device, IDs PNP0800 (active)
[    0.179674] pnp 00:08: [mem 0x000d0000-0x000d3fff]
[    0.179763] system 00:08: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.179843] system 00:08: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.179859] pnp 00:09: [io  0xfe00-0xfe01]
[    0.179952] system 00:09: [io  0xfe00-0xfe01] has been reserved
[    0.180020] system 00:09: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.180037] pnp 00:0a: [io  0x0cf8-0x0cff]
[    0.180087] pnp 00:0a: Plug and Play BIOS device, IDs PNP0a03 (active)
[    0.180103] pnp 00:0b: [io  0x004e-0x004f]
[    0.180202] system 00:0b: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.180356] pnp 00:0c: [mem 0x000cfc00-0x000cffff]
[    0.180443] system 00:0c: [mem 0x000cfc00-0x000cffff] has been reserved
[    0.180522] system 00:0c: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.181176] pnp 00:0e: [irq 12]
[    0.181234] pnp 00:0e: Plug and Play BIOS device, IDs PNP0f13 (active)
[    0.182253] pnp 00:12: [io  0x0378-0x037f]
[    0.182260] pnp 00:12: [io  0x0778-0x077f]
[    0.182266] pnp 00:12: [irq 7]
[    0.182272] pnp 00:12: [dma 1]
[    0.182400] pnp 00:12: Plug and Play BIOS device, IDs PNP0401 (active)
[    0.182411] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[    0.186980] PCI: max bus depth: 2 pci_try_num: 3
[    0.187018] pci 0000:00:0a.0: BAR 15: assigned [mem 0x20000000-0x27ffffff pref]
[    0.187119] pci 0000:02:04.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.187214] pci 0000:02:04.0: BAR 16: can't assign mem (size 0x4000000)
[    0.187292] pci 0000:02:04.1: BAR 15: assigned [mem 0x24000000-0x27ffffff pref]
[    0.187386] pci 0000:02:04.1: BAR 16: can't assign mem (size 0x4000000)
[    0.187464] pci 0000:02:04.0: BAR 13: assigned [io  0x3000-0x30ff]
[    0.187541] pci 0000:02:04.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.187617] pci 0000:02:04.1: BAR 13: assigned [io  0x3800-0x38ff]
[    0.187695] pci 0000:02:04.1: BAR 14: assigned [io  0x3c00-0x3cff]
[    0.187771] pci 0000:02:04.0: CardBus bridge to [bus 03-06]
[    0.187846] pci 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[    0.187924] pci 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[    0.188003] pci 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.188020] pci 0000:02:04.1: CardBus bridge to [bus 07-0a]
[    0.188094] pci 0000:02:04.1:   bridge window [io  0x3800-0x38ff]
[    0.188171] pci 0000:02:04.1:   bridge window [io  0x3c00-0x3cff]
[    0.188249] pci 0000:02:04.1:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.188343] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.188418] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.188496] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.188574] pci 0000:00:0a.0:   bridge window [mem 0x20000000-0x27ffffff pref]
[    0.188672] pci 0000:01:00.0: BAR 6: assigned [mem 0xf8080000-0xf809ffff pref]
[    0.188765] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.188838] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.188916] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.188996] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.189101] pci 0000:00:0a.0: setting latency timer to 64
[    0.189134] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.189142] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.189150] pci_bus 0000:00: resource 6 [mem 0x20000000-0xffffffff]
[    0.189158] pci_bus 0000:02: resource 0 [io  0x3000-0x7fff]
[    0.189165] pci_bus 0000:02: resource 1 [mem 0xe0100000-0xe17fffff]
[    0.189173] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.189181] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.189188] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.189196] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.189204] pci_bus 0000:07: resource 0 [io  0x3800-0x38ff]
[    0.189211] pci_bus 0000:07: resource 1 [io  0x3c00-0x3cff]
[    0.189218] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.189226] pci_bus 0000:01: resource 1 [mem 0xe2000000-0xe2ffffff]
[    0.189234] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf80fffff pref]
[    0.189326] NET: Registered protocol family 2
[    0.189533] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.190081] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.190360] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.190627] TCP: Hash tables configured (established 16384 bind 16384)
[    0.190702] TCP reno registered
[    0.192020] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.192105] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.192334] NET: Registered protocol family 1
[    0.336104] PCI: CLS mismatch (64 != 32), using 64 bytes
[    0.336129] pci 0000:01:00.0: Boot video device
[    0.336800] audit: initializing netlink socket (disabled)
[    0.336887] type=2000 audit(1321014604.336:1): initialized
[    0.396666] Trying to unpack rootfs image as initramfs...
[    0.468228] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.477393] VFS: Disk quotas dquot_6.5.2
[    0.477621] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.484186] fuse init (API version 7.16)
[    0.484512] msgmni has been set to 964
[    0.496818] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.496977] io scheduler noop registered
[    0.497048] io scheduler deadline registered
[    0.497154] io scheduler cfq registered (default)
[    0.497603] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.497743] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.498161] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.501744] Linux agpgart interface v0.103
[    0.501870] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[    0.501952] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    0.502052] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    0.509153] isapnp: Scanning for PnP cards...
[    0.568809] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.576762] brd: module loaded
[    0.578403] loop: module loaded
[    0.578971] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.579997] Fixed MDIO Bus: probed
[    0.580115] PPP generic driver version 2.4.2
[    0.580285] tun: Universal TUN/TAP device driver, 1.6
[    0.580357] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.580615] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.580736] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    0.580745] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    0.580914] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.581059] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    0.581080] ehci_hcd 0000:00:02.2: irq 10, io mem 0xe0004000
[    0.592475] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.592901] hub 1-0:1.0: USB hub found
[    0.592979] hub 1-0:1.0: 6 ports detected
[    0.593217] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.593340] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.593348] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.593508] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.593628] ohci_hcd 0000:00:02.0: irq 11, io mem 0xe0000000
[    0.677001] hub 2-0:1.0: USB hub found
[    0.677087] hub 2-0:1.0: 3 ports detected
[    0.677339] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    0.677348] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    0.677514] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    0.677638] ohci_hcd 0000:00:02.1: irq 10, io mem 0xe0001000
[    0.742592] hub 3-0:1.0: USB hub found
[    0.742678] hub 3-0:1.0: 3 ports detected
[    0.742916] uhci_hcd: USB Universal Host Controller Interface driver
[    0.743219] i8042: PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.749908] i8042: Detected active multiplexing controller, rev 1.1
[    0.776070] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.780953] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.781121] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.781266] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.781403] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.781804] mousedev: PS/2 mouse device common for all mice
[    0.782173] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.782270] rtc0: alarms up to one day, 114 bytes nvram
[    0.782626] device-mapper: uevent: version 1.0.3
[    0.782888] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.783069] EISA: Probing bus 0 at eisa.0
[    0.783144] EISA: Cannot allocate resource for mainboard
[    0.783219] Cannot allocate resource for EISA slot 1
[    0.783292] Cannot allocate resource for EISA slot 2
[    0.783364] Cannot allocate resource for EISA slot 3
[    0.783437] Cannot allocate resource for EISA slot 4
[    0.783510] Cannot allocate resource for EISA slot 5
[    0.783583] Cannot allocate resource for EISA slot 6
[    0.783655] Cannot allocate resource for EISA slot 7
[    0.783728] Cannot allocate resource for EISA slot 8
[    0.783800] EISA: Detected 0 cards.
[    0.783885] cpufreq-nforce2: No nForce2 chipset.
[    0.783957] cpuidle: using governor ladder
[    0.784027] cpuidle: using governor menu
[    0.784057] EFI Variables Facility v0.08 2004-May-17
[    0.784804] TCP cubic registered
[    0.785253] NET: Registered protocol family 10
[    0.790601] NET: Registered protocol family 17
[    0.790713] Registering the dns_resolver key type
[    0.790825] Using IPI No-Shortcut mode
[    0.791101] PM: Hibernation image not present or could not be loaded.
[    0.791125] registered taskstats version 1
[    0.971827] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.083654] isapnp: No Plug & Play device found
[    1.168443] usb 3-1: new low speed USB device number 2 using ohci_hcd
[    1.396267] Switching to clocksource tsc
[    1.673157] Freeing initrd memory: 13304k freed
[    1.706379]   Magic number: 3:606:531
[    1.706493] tty ttyS11: hash matches
[    1.706644] rtc_cmos 00:04: setting system clock to 2011-11-11 12:30:06 UTC (1321014606)
[    1.706741] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    1.711602] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.711677] powernow-k8: Make sure that your BIOS is up to date and Cool'N'Quiet support is enabled in BIOS setup
[    1.711779] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.711852] EDD information not available.
[    1.712193] Freeing unused kernel memory: 696k freed
[    1.713093] Write protecting the kernel text: 5332k
[    1.713253] Write protecting the kernel read-only data: 2188k
[    1.752703] udevd[77]: starting version 173
[    1.953873] pata_amd 0000:00:08.0: version 0.4.1
[    1.953968] pata_amd 0000:00:08.0: setting latency timer to 64
[    1.995241] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.995367] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.998733] scsi0 : pata_amd
[    2.002323] scsi1 : pata_amd
[    2.002524] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    2.002602] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    2.011736] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.011751] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.011762] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.011773] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.011783] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.041647] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.058032] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    2.059724] 8139too 0000:02:01.0: eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:01:07:31, IRQ 10
[    2.390549] ata1.00: ATA-6: FUJITSU MHT2060AT PL, 0022, max UDMA/100
[    2.390636] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.390719] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x0
[    2.404434] ata1.00: configured for UDMA/100
[    2.404764] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    2.405225] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.405602] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.405812] sd 0:0:0:0: [sda] Write Protect is off
[    2.405886] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.405937] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.513445]  sda: sda1 sda2 < sda5 >
[    2.514146] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.584387] ata2.00: ATAPI: SD-R6252, 1A11, max MWDMA2
[    2.584469] ata2: nv_mode_filter: 0x39f&0xfffff->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x0
[    2.616325] ata2.00: configured for MWDMA2
[    2.622486] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6252 1A11 PQ: 0 ANSI: 5
[    2.626858] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.626936] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.627238] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.627373] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.639364] input: HID 04b3:310b as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input1
[    2.639714] generic-usb 0003:04B3:310B.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:02.1-1/input0
[    2.639850] usbcore: registered new interface driver usbhid
[    2.639923] usbhid: USB HID core driver
[    2.688188] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.052184] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.052268] EXT4-fs (sda1): write access will be enabled during recovery
[    3.118040] EXT4-fs (sda1): recovery complete
[    3.118541] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.188354] firewire_core: created device fw0: GUID 463f0200463f0200, S400
[   30.281711] udevd[260]: starting version 173
[   30.360333] lp: driver loaded but no devices found
[   30.410729] Adding 521212k swap on /dev/sda5.  Priority:-1 extents:1 across:521212k 
[   30.624923] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[   30.626816] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   30.664784] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[   30.828297] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.172166] type=1400 audit(1321014635.961:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=458 comm="apparmor_parser"
[   31.172706] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006d]
[   31.172736] yenta_cardbus 0000:02:04.0: CardBus bridge to [bus 03-06]
[   31.172746] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[   31.172756] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[   31.172767] yenta_cardbus 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[   31.172778] yenta_cardbus 0000:02:04.0:   bridge window [mem 0xe0400000-0xe07fffff]
[   31.172789] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   31.172799] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   31.172807] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   31.172817] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   31.186572] type=1400 audit(1321014635.977:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=458 comm="apparmor_parser"
[   31.187344] type=1400 audit(1321014635.977:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=458 comm="apparmor_parser"
[   31.197212] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.267062] nf_conntrack version 0.5.0 (7934 buckets, 31736 max)
[   31.354265] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   31.410856] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x02f8, PCI irq 11
[   31.410867] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   31.410877] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   31.410898] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   31.410908] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   31.657616] cfg80211: Calling CRDA to update world regulatory domain
[   31.700306]  0x7000-0x70ff 0x7400-0x743f
[   31.848259] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe0100000-0xe17fffff]
[   31.848273] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0100000-0xe17fffff: excluding 0xe0100000-0xe026ffff 0xe03e0000-0xe082ffff
[   31.848312] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   31.848322] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   31.897801] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006d]
[   31.897831] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   31.897840] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   31.897851] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   31.939231] nvidia: module license 'NVIDIA' taints kernel.
[   31.939243] Disabling lock debugging due to kernel taint
[   32.044500] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input2
[   32.065009] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input3
[   32.129981] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x02f8, PCI irq 10
[   32.129993] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   32.130003] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   32.130024] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   32.130035] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   32.268503] 8139too 0000:02:01.0: eth0: link down
[   32.271191] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.519131] type=1400 audit(1321014637.309:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=702 comm="apparmor_parser"
[   32.533682] type=1400 audit(1321014637.325:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=704 comm="apparmor_parser"
[   32.535270] type=1400 audit(1321014637.325:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=704 comm="apparmor_parser"
[   32.536041] type=1400 audit(1321014637.325:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=704 comm="apparmor_parser"
[   32.584557] type=1400 audit(1321014637.373:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=705 comm="apparmor_parser"
[   32.633736] type=1400 audit(1321014637.425:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=705 comm="apparmor_parser"
[   32.664356]  0x7000-0x70ff 0x7400-0x743f
[   32.671002] type=1400 audit(1321014637.461:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=705 comm="apparmor_parser"
[   32.736174] 
[   32.736191] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0xe0100000-0xe17fffff]
[   32.736203] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe0100000-0xe17fffff: excluding 0xe0100000-0xe026ffff 0xe03e0000-0xe082ffff 0xe0b10000-0xe10cffff
[   32.736244] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   32.736253] pcmcia_socket pcmcia_socket1: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   32.784748] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   32.881835] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   32.881848] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881857] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   32.881866] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881873] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   32.881881] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881888] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   32.881896] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881903] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   32.881911] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881918] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   32.881926] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881933] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   32.881941] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881948] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   32.881956] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881963] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   32.881971] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881978] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   32.881986] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.881993] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   32.882001] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.882008] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   32.882016] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.882023] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   32.882031] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[   32.882038] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   32.882046] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[   33.444798] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   33.468432] Registered led device: b43-phy0::tx
[   33.470526] Registered led device: b43-phy0::rx
[   33.470654] Registered led device: b43-phy0::radio
[   33.470757] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   33.779999] apm: BIOS not found.
[   33.838524] init: failsafe main process (718) killed by TERM signal
[   33.842018] init: apport pre-start process (793) terminated with status 1
[   33.849479] init: alsa-restore main process (799) terminated with status 19
[   33.910699] init: apport post-stop process (823) terminated with status 1
[   34.030137] Intel ICH 0000:00:06.0: setting latency timer to 64
```

thanks again for your help Toz!!

---

### Post by rj45 on 2011-11-11
> **rj45 said:**
> Thanks Toz!
I am not concerned with dual graphic card issues - I could turn off the ATI card permanently and not miss it.
Just like the original poster, my laptop locks up hard if I don't use the "acpi=off" parameter.  I reserched this at length, and spent many hours troubleshooting - it's due to the changes in GRUB2 that makes graphic calls to DKMS before the main graphics drivers ever get loaded.  Haven't found a good solution yet.  Loaded 11.10 from scratch yesterday, and determined to fix it.

Thanks again for the help.
Looks like my issue is now solved - something changed between 11.04 and 11.10 - I can now boot reliably with kernel args:
"nomodeset nosplash acpi_osi=Linux"

---

### Post by rj45 on 2011-11-11
@TREESofRIGHTEOUSNESS
Please try these kernel boot arguments (and only these)
"nomodeset nosplash acpi_osi=Linux"

Works for me.
regards,

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
ok, I will try it, and let you know if it worked... Thanks!!

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
nope.... same old problem....  Thanks for the suggestion!!

---

### Post by Toz on 2011-11-11
> **TREESofRIGHTEOUSNESS said:**
> OK, I rebooted w/o acpi=off and it hung up, and then rebooted, and it hung again... and rebooted and now I am posting....

Because you ended up booting twice, we missed the log file for the boot without acpi=off. The way it works is that the current boot log becomes dmesg, the previous becomes dmesg.0, the one before that dmesg.1.gz (its zipped), the one before that dmesg.2.gz, etc.

Any chance you could try it again? I'd like to see the log for acpi=off?

Thanks

---

### Post by Toz on 2011-11-11
A couple of more things I noticed from reviewing your log files:
> [    0.032163] weird, boot CPU (#0) not listed by the BIOS.
[    0.774895] EISA: Cannot allocate resource for mainboard
[    1.704338] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.704414] powernow-k8: Make sure that your BIOS is up to date and Cool'N'Quiet support is enabled in BIOS setup
[   33.981864] apm: BIOS not found.

1. Is your bios up to date? Check to see if there is an update available.

2. Is apic enabled in your bios?

3. Is "Cool & Quiet" enabled in your bios? If its set to auto, try other settings.

4. Try with turning off "Plug & Play" in the bios.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
BIOS is not up to date... but I don't use windows.... so......
I will check those other settings... but I don't remember seeing anything like that in BIOS...

here is dmesg.0

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Hewlett-Packard  Presario R3200 (PF153UA#ABA)  /08A0, BIOS F.11 04/30/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-D3FFF write-back
[    0.000000]   D4000-D4FFF write-protect
[    0.000000]   D5000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff70000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff70000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 1dcb2000 - 1e9b0000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff70000
[    0.000000]   low ram: 0 - 1ff70000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff70
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ff70
[    0.000000] On node 0 totalpages: 130815
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map dfb6f200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dff80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @df400000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b61c59af-7f66-4df5-b2d5-928314a8ddd3 ro acpi=off
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2094592 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 493808k/523712k available (5329k kernel code, 29452k reserved, 2589k data, 696k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=df006000 soft=df008000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 797.889 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 1595.77 BogoMIPS (lpj=3191556)
[    0.008160] pid_max: default: 32768 minimum: 301
[    0.008292] Security Framework initialized
[    0.008417] AppArmor: AppArmor initialized
[    0.008490] Yama: becoming mindful.
[    0.008717] Mount-cache hash table entries: 512
[    0.009112] Initializing cgroup subsys cpuacct
[    0.009198] Initializing cgroup subsys memory
[    0.009291] Initializing cgroup subsys devices
[    0.009367] Initializing cgroup subsys freezer
[    0.009442] Initializing cgroup subsys net_cls
[    0.009518] Initializing cgroup subsys blkio
[    0.009605] Initializing cgroup subsys perf_event
[    0.009743] mce: CPU supports 5 MCE banks
[    0.010330] SMP alternatives: switching to UP code
[    0.032433] Freeing SMP alternatives: 24k freed
[    0.032544] ftrace: allocating 24885 entries in 49 pages
[    0.036163] weird, boot CPU (#0) not listed by the BIOS.
[    0.036242] SMP motherboard not detected.
[    0.036314] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.144031] SMP disabled
[    0.144099] Performance Events: AMD PMU driver.
[    0.144225] ... version:                0
[    0.144295] ... bit width:              48
[    0.144365] ... generic registers:      4
[    0.144435] ... value mask:             0000ffffffffffff
[    0.144509] ... max period:             00007fffffffffff
[    0.144581] ... fixed-purpose events:   0
[    0.144651] ... event mask:             000000000000000f
[    0.145763] Brought up 1 CPUs
[    0.145833] Total of 1 processors activated (1595.77 BogoMIPS).
[    0.146148] devtmpfs: initialized
[    0.146562] PM: Registering ACPI NVS region at 1ff7f000 (4096 bytes)
[    0.152127] print_constraints: dummy: 
[    0.152229] Time: 21:40:37  Date: 11/11/11
[    0.152384] NET: Registered protocol family 16
[    0.152773] EISA bus registered
[    0.152849] node 0 link 0: io port [1000, fffff]
[    0.152858] TOM: 0000000020000000 aka 512M
[    0.152932] node 0 link 0: mmio [a0000, bffff]
[    0.152941] node 0 link 0: mmio [20000000, fe0bffff]
[    0.152949] bus: [00, ff] on node 0 link 0
[    0.152957] bus: 00 index 0 [io  0x0000-0xffff]
[    0.152964] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.152971] bus: 00 index 2 [mem 0x20000000-0xffffffff]
[    0.153330] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[    0.153406] PCI: Using configuration type 1 for base access
[    0.156495] bio: create slab <bio-0> at 0
[    0.156767] ACPI: Interpreter disabled.
[    0.156978] vgaarb: loaded
[    0.157636] SCSI subsystem initialized
[    0.157807] libata version 3.00 loaded.
[    0.157922] usbcore: registered new interface driver usbfs
[    0.158022] usbcore: registered new interface driver hub
[    0.158153] usbcore: registered new device driver usb
[    0.158447] PCI: Probing PCI hardware
[    0.158519] PCI: Probing PCI hardware (bus 00)
[    0.158608] pci 0000:00:00.0: [10de:00d1] type 0 class 0x000600
[    0.158626] pci 0000:00:00.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.158703] pci 0000:00:01.0: [10de:00d0] type 0 class 0x000601
[    0.158768] pci 0000:00:01.1: [10de:00d4] type 0 class 0x000c05
[    0.158806] pci 0000:00:01.1: reg 20: [io  0x2040-0x207f]
[    0.158819] pci 0000:00:01.1: reg 24: [io  0x2000-0x203f]
[    0.158844] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.158853] pci 0000:00:01.1: PME# disabled
[    0.158882] pci 0000:00:02.0: [10de:00d7] type 0 class 0x000c03
[    0.158900] pci 0000:00:02.0: reg 10: [mem 0xe0000000-0xe0000fff]
[    0.158949] pci 0000:00:02.0: supports D1 D2
[    0.158956] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.158964] pci 0000:00:02.0: PME# disabled
[    0.158989] pci 0000:00:02.1: [10de:00d7] type 0 class 0x000c03
[    0.159007] pci 0000:00:02.1: reg 10: [mem 0xe0001000-0xe0001fff]
[    0.159057] pci 0000:00:02.1: supports D1 D2
[    0.159063] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159071] pci 0000:00:02.1: PME# disabled
[    0.159094] pci 0000:00:02.2: [10de:00d8] type 0 class 0x000c03
[    0.159112] pci 0000:00:02.2: reg 10: [mem 0xe0004000-0xe00040ff]
[    0.159162] pci 0000:00:02.2: supports D1 D2
[    0.159168] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159177] pci 0000:00:02.2: PME# disabled
[    0.159209] pci 0000:00:06.0: [10de:00da] type 0 class 0x000401
[    0.159226] pci 0000:00:06.0: reg 10: [io  0x1400-0x14ff]
[    0.159239] pci 0000:00:06.0: reg 14: [io  0x1c00-0x1c7f]
[    0.159251] pci 0000:00:06.0: reg 18: [mem 0xe0002000-0xe0002fff]
[    0.159290] pci 0000:00:06.0: supports D1 D2
[    0.159313] pci 0000:00:06.1: [10de:00d9] type 0 class 0x000703
[    0.159330] pci 0000:00:06.1: reg 10: [io  0x1800-0x18ff]
[    0.159343] pci 0000:00:06.1: reg 14: [io  0x1c80-0x1cff]
[    0.159355] pci 0000:00:06.1: reg 18: [mem 0xe0003000-0xe0003fff]
[    0.159395] pci 0000:00:06.1: PME# supported from D3cold
[    0.159403] pci 0000:00:06.1: PME# disabled
[    0.159433] pci 0000:00:08.0: [10de:00d5] type 0 class 0x000101
[    0.159470] pci 0000:00:08.0: reg 20: [io  0x2080-0x208f]
[    0.159514] pci 0000:00:0a.0: [10de:00dd] type 1 class 0x000604
[    0.159555] pci 0000:00:0b.0: [10de:00d2] type 1 class 0x000604
[    0.159619] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.159666] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.159704] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.159742] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.159781] PCI: peer root bus 00 res updated from pci conf
[    0.159817] pci 0000:02:00.0: [104c:8026] type 0 class 0x000c00
[    0.159840] pci 0000:02:00.0: reg 10: [mem 0xe0108000-0xe01087ff]
[    0.159855] pci 0000:02:00.0: reg 14: [mem 0xe0100000-0xe0103fff]
[    0.159917] pci 0000:02:00.0: supports D1 D2
[    0.159923] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.159932] pci 0000:02:00.0: PME# disabled
[    0.159958] pci 0000:02:01.0: [10ec:8139] type 0 class 0x000200
[    0.159980] pci 0000:02:01.0: reg 10: [io  0x7000-0x70ff]
[    0.159995] pci 0000:02:01.0: reg 14: [mem 0xe0108800-0xe01088ff]
[    0.160065] pci 0000:02:01.0: supports D1 D2
[    0.160072] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.160081] pci 0000:02:01.0: PME# disabled
[    0.160104] pci 0000:02:02.0: [14e4:4320] type 0 class 0x000280
[    0.160123] pci 0000:02:02.0: reg 10: [mem 0xe0104000-0xe0105fff]
[    0.160196] pci 0000:02:04.0: [104c:ac54] type 2 class 0x000607
[    0.160219] pci 0000:02:04.0: reg 10: [mem 0xe0106000-0xe0106fff]
[    0.160243] pci 0000:02:04.0: supports D1 D2
[    0.160249] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160258] pci 0000:02:04.0: PME# disabled
[    0.160285] pci 0000:02:04.1: [104c:ac54] type 2 class 0x000607
[    0.160307] pci 0000:02:04.1: reg 10: [mem 0xe0107000-0xe0107fff]
[    0.160331] pci 0000:02:04.1: supports D1 D2
[    0.160337] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160346] pci 0000:02:04.1: PME# disabled
[    0.160374] pci 0000:02:04.2: [104c:8201] type 0 class 0x000880
[    0.160394] pci 0000:02:04.2: reg 10: [io  0x7400-0x743f]
[    0.160503] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.160579] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.160588] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.160598] pci 0000:00:0a.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.160650] pci_bus 0000:03: [bus 03-06] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.160778] pci_bus 0000:07: [bus 07-0a] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.160903] pci 0000:01:00.0: [10de:0179] type 0 class 0x000300
[    0.160930] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
[    0.160946] pci 0000:01:00.0: reg 14: [mem 0xf0000000-0xf7ffffff pref]
[    0.160963] pci 0000:01:00.0: reg 18: [mem 0xf8000000-0xf807ffff pref]
[    0.161005] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.161084] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.161160] pci 0000:00:0b.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.161170] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.161180] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.162883] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.163135] pci 0000:00:01.0: default IRQ router [10de:00d0]
[    0.163271] PCI: pci_cache_line_size set to 64 bytes
[    0.163378] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.163385] reserve RAM buffer: 000000001ff70000 - 000000001fffffff 
[    0.163643] NetLabel: Initializing
[    0.163713] NetLabel:  domain hash size = 128
[    0.163782] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.163878] NetLabel:  unlabeled traffic allowed by default
[    0.181690] AppArmor: AppArmor Filesystem Enabled
[    0.181810] pnp: PnP ACPI: disabled
[    0.181882] PnPBIOS: Scanning system for PnP BIOS support...
[    0.181992] PnPBIOS: Found PnP BIOS installation structure at 0xc00f72c0
[    0.182069] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb71e, dseg 0x400
[    0.183016] pnp 00:00: [mem 0x00000000-0xffffffff disabled]
[    0.183024] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.183031] pnp 00:00: [mem 0x00100000-0x1ff7ffff]
[    0.183142] system 00:00: Plug and Play BIOS device, IDs PNP0c01 (disabled)
[    0.183160] pnp 00:01: [io  0x0000-0x000f]
[    0.183166] pnp 00:01: [io  0x0081-0x008f]
[    0.183173] pnp 00:01: [io  0x00c0-0x00df]
[    0.183179] pnp 00:01: [dma 4]
[    0.183234] pnp 00:01: Plug and Play BIOS device, IDs PNP0200 (active)
[    0.183250] pnp 00:02: [io  0x0020-0x0021]
[    0.183256] pnp 00:02: [io  0x00a0-0x00a1]
[    0.183263] pnp 00:02: [irq 2]
[    0.183310] pnp 00:02: Plug and Play BIOS device, IDs PNP0000 (active)
[    0.183325] pnp 00:03: [io  0x0040-0x0043]
[    0.183331] pnp 00:03: [irq 0]
[    0.183377] pnp 00:03: Plug and Play BIOS device, IDs PNP0100 (active)
[    0.183393] pnp 00:04: [io  0x0070-0x0071]
[    0.183399] pnp 00:04: [irq 8]
[    0.183445] pnp 00:04: Plug and Play BIOS device, IDs PNP0b00 (active)
[    0.183460] pnp 00:05: [io  0x0060]
[    0.183466] pnp 00:05: [io  0x0064]
[    0.183472] pnp 00:05: [irq 1]
[    0.183518] pnp 00:05: Plug and Play BIOS device, IDs PNP0303 (active)
[    0.183534] pnp 00:06: [io  0x00f0-0x00ff]
[    0.183540] pnp 00:06: [irq 13]
[    0.183594] pnp 00:06: Plug and Play BIOS device, IDs PNP0c04 (active)
[    0.183609] pnp 00:07: [io  0x0061]
[    0.183656] pnp 00:07: Plug and Play BIOS device, IDs PNP0800 (active)
[    0.183672] pnp 00:08: [mem 0x000d0000-0x000d3fff]
[    0.183760] system 00:08: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.183840] system 00:08: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.183857] pnp 00:09: [io  0xfe00-0xfe01]
[    0.183950] system 00:09: [io  0xfe00-0xfe01] has been reserved
[    0.184020] system 00:09: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.184037] pnp 00:0a: [io  0x0cf8-0x0cff]
[    0.184088] pnp 00:0a: Plug and Play BIOS device, IDs PNP0a03 (active)
[    0.184104] pnp 00:0b: [io  0x004e-0x004f]
[    0.184203] system 00:0b: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.184356] pnp 00:0c: [mem 0x000cfc00-0x000cffff]
[    0.184443] system 00:0c: [mem 0x000cfc00-0x000cffff] has been reserved
[    0.184522] system 00:0c: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.185176] pnp 00:0e: [irq 12]
[    0.185234] pnp 00:0e: Plug and Play BIOS device, IDs PNP0f13 (active)
[    0.186253] pnp 00:12: [io  0x0378-0x037f]
[    0.186260] pnp 00:12: [io  0x0778-0x077f]
[    0.186266] pnp 00:12: [irq 7]
[    0.186272] pnp 00:12: [dma 1]
[    0.186400] pnp 00:12: Plug and Play BIOS device, IDs PNP0401 (active)
[    0.186411] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[    0.190986] PCI: max bus depth: 2 pci_try_num: 3
[    0.191024] pci 0000:00:0a.0: BAR 15: assigned [mem 0x20000000-0x27ffffff pref]
[    0.191124] pci 0000:02:04.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.191219] pci 0000:02:04.0: BAR 16: can't assign mem (size 0x4000000)
[    0.191299] pci 0000:02:04.1: BAR 15: assigned [mem 0x24000000-0x27ffffff pref]
[    0.191392] pci 0000:02:04.1: BAR 16: can't assign mem (size 0x4000000)
[    0.191470] pci 0000:02:04.0: BAR 13: assigned [io  0x3000-0x30ff]
[    0.191546] pci 0000:02:04.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.191622] pci 0000:02:04.1: BAR 13: assigned [io  0x3800-0x38ff]
[    0.191699] pci 0000:02:04.1: BAR 14: assigned [io  0x3c00-0x3cff]
[    0.191775] pci 0000:02:04.0: CardBus bridge to [bus 03-06]
[    0.191850] pci 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[    0.191928] pci 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[    0.192007] pci 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.192020] pci 0000:02:04.1: CardBus bridge to [bus 07-0a]
[    0.192094] pci 0000:02:04.1:   bridge window [io  0x3800-0x38ff]
[    0.192171] pci 0000:02:04.1:   bridge window [io  0x3c00-0x3cff]
[    0.192249] pci 0000:02:04.1:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.192343] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.192418] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.192496] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.192574] pci 0000:00:0a.0:   bridge window [mem 0x20000000-0x27ffffff pref]
[    0.192672] pci 0000:01:00.0: BAR 6: assigned [mem 0xf8080000-0xf809ffff pref]
[    0.192765] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.192838] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.192915] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.192995] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.193099] pci 0000:00:0a.0: setting latency timer to 64
[    0.193133] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.193140] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.193148] pci_bus 0000:00: resource 6 [mem 0x20000000-0xffffffff]
[    0.193156] pci_bus 0000:02: resource 0 [io  0x3000-0x7fff]
[    0.193163] pci_bus 0000:02: resource 1 [mem 0xe0100000-0xe17fffff]
[    0.193171] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.193179] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.193186] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.193194] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.193202] pci_bus 0000:07: resource 0 [io  0x3800-0x38ff]
[    0.193209] pci_bus 0000:07: resource 1 [io  0x3c00-0x3cff]
[    0.193216] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.193224] pci_bus 0000:01: resource 1 [mem 0xe2000000-0xe2ffffff]
[    0.193232] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf80fffff pref]
[    0.193324] NET: Registered protocol family 2
[    0.193532] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.194080] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.194359] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.194625] TCP: Hash tables configured (established 16384 bind 16384)
[    0.194700] TCP reno registered
[    0.196020] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.196105] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.196335] NET: Registered protocol family 1
[    0.344104] PCI: CLS mismatch (64 != 32), using 64 bytes
[    0.344129] pci 0000:01:00.0: Boot video device
[    0.344800] audit: initializing netlink socket (disabled)
[    0.344887] type=2000 audit(1321047637.344:1): initialized
[    0.404666] Trying to unpack rootfs image as initramfs...
[    0.476245] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.485453] VFS: Disk quotas dquot_6.5.2
[    0.485682] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.492334] fuse init (API version 7.16)
[    0.492665] msgmni has been set to 964
[    0.504962] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.505122] io scheduler noop registered
[    0.505193] io scheduler deadline registered
[    0.505302] io scheduler cfq registered (default)
[    0.505750] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.505892] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.506310] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.509913] Linux agpgart interface v0.103
[    0.510040] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[    0.510121] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    0.510222] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    0.517325] isapnp: Scanning for PnP cards...
[    0.576992] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.584920] brd: module loaded
[    0.586622] loop: module loaded
[    0.587193] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.588233] Fixed MDIO Bus: probed
[    0.588373] PPP generic driver version 2.4.2
[    0.588542] tun: Universal TUN/TAP device driver, 1.6
[    0.588614] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.588871] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.588992] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    0.589000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    0.589170] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.589315] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    0.589336] ehci_hcd 0000:00:02.2: irq 10, io mem 0xe0004000
[    0.600714] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.601134] hub 1-0:1.0: USB hub found
[    0.601211] hub 1-0:1.0: 6 ports detected
[    0.601446] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.601569] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.601577] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.601735] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.601855] ohci_hcd 0000:00:02.0: irq 11, io mem 0xe0000000
[    0.670400] hub 2-0:1.0: USB hub found
[    0.670485] hub 2-0:1.0: 3 ports detected
[    0.670731] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    0.670739] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    0.670901] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    0.671023] ohci_hcd 0000:00:02.1: irq 10, io mem 0xe0001000
[    0.750819] hub 3-0:1.0: USB hub found
[    0.750904] hub 3-0:1.0: 3 ports detected
[    0.751142] uhci_hcd: USB Universal Host Controller Interface driver
[    0.751444] i8042: PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.760051] i8042: Detected active multiplexing controller, rev 1.1
[    0.892065] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.892153] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.892229] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.892304] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.892379] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.892671] mousedev: PS/2 mouse device common for all mice
[    0.900385] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.900483] rtc0: alarms up to one day, 114 bytes nvram
[    0.900845] device-mapper: uevent: version 1.0.3
[    0.901111] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.901289] EISA: Probing bus 0 at eisa.0
[    0.901364] EISA: Cannot allocate resource for mainboard
[    0.901438] Cannot allocate resource for EISA slot 1
[    0.901511] Cannot allocate resource for EISA slot 2
[    0.901583] Cannot allocate resource for EISA slot 3
[    0.901656] Cannot allocate resource for EISA slot 4
[    0.901728] Cannot allocate resource for EISA slot 5
[    0.901801] Cannot allocate resource for EISA slot 6
[    0.901873] Cannot allocate resource for EISA slot 7
[    0.901946] Cannot allocate resource for EISA slot 8
[    0.902018] EISA: Detected 0 cards.
[    0.902103] cpufreq-nforce2: No nForce2 chipset.
[    0.902176] cpuidle: using governor ladder
[    0.902246] cpuidle: using governor menu
[    0.902316] EFI Variables Facility v0.08 2004-May-17
[    0.903034] TCP cubic registered
[    0.908037] NET: Registered protocol family 10
[    0.909424] NET: Registered protocol family 17
[    0.909537] Registering the dns_resolver key type
[    0.909695] Using IPI No-Shortcut mode
[    0.909977] PM: Hibernation image not present or could not be loaded.
[    0.910001] registered taskstats version 1
[    0.926367] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.063157] isapnp: No Plug & Play device found
[    1.312322] usb 2-2: new low speed USB device number 2 using ohci_hcd
[    1.404197] Switching to clocksource tsc
[    1.683623] Freeing initrd memory: 13304k freed
[    1.716815]   Magic number: 3:219:702
[    1.717010] rtc_cmos 00:04: setting system clock to 2011-11-11 21:40:39 UTC (1321047639)
[    1.717107] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    1.721958] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.722034] powernow-k8: Make sure that your BIOS is up to date and Cool'N'Quiet support is enabled in BIOS setup
[    1.722136] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.722209] EDD information not available.
[    1.722537] Freeing unused kernel memory: 696k freed
[    1.723451] Write protecting the kernel text: 5332k
[    1.723609] Write protecting the kernel read-only data: 2188k
[    1.762764] udevd[76]: starting version 173
[    1.939306] pata_amd 0000:00:08.0: version 0.4.1
[    1.939402] pata_amd 0000:00:08.0: setting latency timer to 64
[    1.993900] scsi0 : pata_amd
[    1.997820] scsi1 : pata_amd
[    1.998025] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    1.998104] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    2.011515] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.011640] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.050982] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.050997] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.051008] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.051019] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.051029] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.054466] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    2.393791] ata1.00: ATA-6: FUJITSU MHT2060AT PL, 0022, max UDMA/100
[    2.393877] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.393961] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x0
[    2.408448] ata1.00: configured for UDMA/100
[    2.408783] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    2.409258] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.409638] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.409845] sd 0:0:0:0: [sda] Write Protect is off
[    2.409921] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.409973] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.515845]  sda: sda1 sda2 < sda5 >
[    2.516571] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.588389] ata2.00: ATAPI: SD-R6252, 1A11, max MWDMA2
[    2.588471] ata2: nv_mode_filter: 0x39f&0xfffff->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x0
[    2.620337] ata2.00: configured for MWDMA2
[    2.626555] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6252 1A11 PQ: 0 ANSI: 5
[    2.631175] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.631253] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.631545] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.631672] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.634910] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.639662] 8139too 0000:02:01.0: eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:01:07:31, IRQ 10
[    2.643255] input: HID 04b3:310b as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input1
[    2.643614] generic-usb 0003:04B3:310B.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:02.0-2/input0
[    2.643748] usbcore: registered new interface driver usbhid
[    2.643821] usbhid: USB HID core driver
[    2.700172] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.054589] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.054674] EXT4-fs (sda1): write access will be enabled during recovery
[    3.120317] EXT4-fs (sda1): recovery complete
[    3.120885] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.200324] firewire_core: created device fw0: GUID 463f0200463f0200, S400
[   30.600921] udevd[261]: starting version 173
[   30.670359] lp: driver loaded but no devices found
[   30.715718] Adding 521212k swap on /dev/sda5.  Priority:-1 extents:1 across:521212k 
[   30.950551] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[   30.950687] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   30.951896] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[   31.178761] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.516383] type=1400 audit(1321047669.296:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=471 comm="apparmor_parser"
[   31.518361] type=1400 audit(1321047669.296:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=471 comm="apparmor_parser"
[   31.519126] type=1400 audit(1321047669.296:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=471 comm="apparmor_parser"
[   31.531634] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.707749] nf_conntrack version 0.5.0 (7934 buckets, 31736 max)
[   31.807732] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   32.002450] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006d]
[   32.002483] yenta_cardbus 0000:02:04.0: CardBus bridge to [bus 03-06]
[   32.002492] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[   32.002503] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[   32.002514] yenta_cardbus 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[   32.002525] yenta_cardbus 0000:02:04.0:   bridge window [mem 0xe0400000-0xe07fffff]
[   32.002536] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   32.002546] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   32.002553] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   32.002564] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   32.234777] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x02f8, PCI irq 11
[   32.234788] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   32.234799] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   32.234820] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   32.234830] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   32.550162] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input2
[   32.571505] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input3
[   32.744246] cfg80211: Calling CRDA to update world regulatory domain
[   32.776088] nvidia: module license 'NVIDIA' taints kernel.
[   32.776099] Disabling lock debugging due to kernel taint
[   32.803632]  0x7000-0x70ff 0x7400-0x743f
[   33.689620] 8139too 0000:02:01.0: eth0: link down
[   33.689829] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.789124] 
[   33.789140] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe0100000-0xe17fffff]
[   33.789153] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0100000-0xe17fffff: excluding 0xe0100000-0xe026ffff 0xe03e0000-0xe082ffff
[   33.789190] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   33.789199] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   33.839067] type=1400 audit(1321047671.616:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=675 comm="apparmor_parser"
[   33.845315] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006d]
[   33.845344] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   33.845352] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   33.845363] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   33.853458] type=1400 audit(1321047671.632:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=683 comm="apparmor_parser"
[   33.854653] type=1400 audit(1321047671.632:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=683 comm="apparmor_parser"
[   33.855425] type=1400 audit(1321047671.632:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=683 comm="apparmor_parser"
[   33.901053] type=1400 audit(1321047671.680:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=689 comm="apparmor_parser"
[   33.933248] type=1400 audit(1321047671.712:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=689 comm="apparmor_parser"
[   33.954134] type=1400 audit(1321047671.732:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=689 comm="apparmor_parser"
[   34.080538] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x02f8, PCI irq 10
[   34.080549] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   34.080560] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   34.080579] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   34.080589] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   34.304330] apm: BIOS not found.
[   34.358643] init: apport pre-start process (748) terminated with status 1
[   34.362100] init: alsa-restore main process (753) terminated with status 19
[   34.415779] init: apport post-stop process (777) terminated with status 1
[   34.678835]  0x7000-0x70ff 0x7400-0x743f
```

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
I checked my BIOS... and there were no options like that.... I have read that trying to update the BIOS in Linux is a last ditch effort.  I don't really want to load windows on here just to update BIOS....
I have considered doing it before.... but I never have.
If so... do you know a good way to do it... I am sure wine is a bad deal, since it is kinda buggy  with some windows programs, I don't want to half flash my BIOS and end up with a brick....
I'd rather just use acpi=off.... :)

---

### Post by matt_symes on 2011-11-11
Hi

Do you mind if i ask a question ?

Can you boot into bash directly from initramfs without calling  /sbin/init that, if the acpi=off kernel command is not part of the  kernel command line ? 

It would require the kernel command line parameter init=/bin/bash and the removal of acpi=off.

That may be quite informative.

Kind regards

---

### Post by Toz on 2011-11-11
> **TREESofRIGHTEOUSNESS said:**
> BIOS is not up to date... but I don't use windows.... so......
I will check those other settings... but I don't remember seeing anything like that in BIOS...

here is dmesg.0
Unfortunately, this log file is also generated with the acpi=off paramater. You can check by:
```
cat /var/log/dmesg | grep "Kernel command line"
```
...or for the compressed files...
```
zcat /var/log/dmesg.1 | grep "Kernel command line"
```

I'm curious to see a dmesg log file from a boot where you don't have acpi=off to see how it compares.

---

### Post by Toz on 2011-11-11
> **matt_symes said:**
> Hi

Do you mind if i ask a question ?

Can you boot into bash directly from initramfs without calling  /sbin/init that, if the acpi=off kernel command is not part of the  kernel command line ? 

It would require the kernel command line parameter init=/bin/bash and the removal of acpi=off.

That may be quite informative.

Kind regards

Interesting approach. This might yield some good information as well. Thanks.

A cursory search on Google doesn't yield similar problems with other Presario R3200s. In fact, most seem to boot fine. Leads me to think its something specific with the hardware configuration. OR possibly an out-dated or buggy bios.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
@Toz  it is actually a Presario R3000...
OK.. I hope I got this right...

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Hewlett-Packard  Presario R3200 (PF153UA#ABA)  /08A0, BIOS F.11 04/30/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-D3FFF write-back
[    0.000000]   D4000-D4FFF write-protect
[    0.000000]   D5000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff70000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff70000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 1dcb2000 - 1e9b0000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff70000
[    0.000000]   low ram: 0 - 1ff70000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff70
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ff70
[    0.000000] On node 0 totalpages: 130815
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map dfb6f200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dff80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @df400000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b61c59af-7f66-4df5-b2d5-928314a8ddd3 ro acpi=off
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2094592 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 493808k/523712k available (5329k kernel code, 29452k reserved, 2589k data, 696k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=df006000 soft=df008000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 797.889 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 1595.77 BogoMIPS (lpj=3191556)
[    0.008160] pid_max: default: 32768 minimum: 301
[    0.008292] Security Framework initialized
[    0.008417] AppArmor: AppArmor initialized
[    0.008490] Yama: becoming mindful.
[    0.008717] Mount-cache hash table entries: 512
[    0.009112] Initializing cgroup subsys cpuacct
[    0.009198] Initializing cgroup subsys memory
[    0.009291] Initializing cgroup subsys devices
[    0.009367] Initializing cgroup subsys freezer
[    0.009442] Initializing cgroup subsys net_cls
[    0.009518] Initializing cgroup subsys blkio
[    0.009605] Initializing cgroup subsys perf_event
[    0.009743] mce: CPU supports 5 MCE banks
[    0.010330] SMP alternatives: switching to UP code
[    0.032433] Freeing SMP alternatives: 24k freed
[    0.032544] ftrace: allocating 24885 entries in 49 pages
[    0.036163] weird, boot CPU (#0) not listed by the BIOS.
[    0.036242] SMP motherboard not detected.
[    0.036314] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.144031] SMP disabled
[    0.144099] Performance Events: AMD PMU driver.
[    0.144225] ... version:                0
[    0.144295] ... bit width:              48
[    0.144365] ... generic registers:      4
[    0.144435] ... value mask:             0000ffffffffffff
[    0.144509] ... max period:             00007fffffffffff
[    0.144581] ... fixed-purpose events:   0
[    0.144651] ... event mask:             000000000000000f
[    0.145763] Brought up 1 CPUs
[    0.145833] Total of 1 processors activated (1595.77 BogoMIPS).
[    0.146148] devtmpfs: initialized
[    0.146562] PM: Registering ACPI NVS region at 1ff7f000 (4096 bytes)
[    0.152127] print_constraints: dummy: 
[    0.152229] Time: 21:40:37  Date: 11/11/11
[    0.152384] NET: Registered protocol family 16
[    0.152773] EISA bus registered
[    0.152849] node 0 link 0: io port [1000, fffff]
[    0.152858] TOM: 0000000020000000 aka 512M
[    0.152932] node 0 link 0: mmio [a0000, bffff]
[    0.152941] node 0 link 0: mmio [20000000, fe0bffff]
[    0.152949] bus: [00, ff] on node 0 link 0
[    0.152957] bus: 00 index 0 [io  0x0000-0xffff]
[    0.152964] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.152971] bus: 00 index 2 [mem 0x20000000-0xffffffff]
[    0.153330] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[    0.153406] PCI: Using configuration type 1 for base access
[    0.156495] bio: create slab <bio-0> at 0
[    0.156767] ACPI: Interpreter disabled.
[    0.156978] vgaarb: loaded
[    0.157636] SCSI subsystem initialized
[    0.157807] libata version 3.00 loaded.
[    0.157922] usbcore: registered new interface driver usbfs
[    0.158022] usbcore: registered new interface driver hub
[    0.158153] usbcore: registered new device driver usb
[    0.158447] PCI: Probing PCI hardware
[    0.158519] PCI: Probing PCI hardware (bus 00)
[    0.158608] pci 0000:00:00.0: [10de:00d1] type 0 class 0x000600
[    0.158626] pci 0000:00:00.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.158703] pci 0000:00:01.0: [10de:00d0] type 0 class 0x000601
[    0.158768] pci 0000:00:01.1: [10de:00d4] type 0 class 0x000c05
[    0.158806] pci 0000:00:01.1: reg 20: [io  0x2040-0x207f]
[    0.158819] pci 0000:00:01.1: reg 24: [io  0x2000-0x203f]
[    0.158844] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.158853] pci 0000:00:01.1: PME# disabled
[    0.158882] pci 0000:00:02.0: [10de:00d7] type 0 class 0x000c03
[    0.158900] pci 0000:00:02.0: reg 10: [mem 0xe0000000-0xe0000fff]
[    0.158949] pci 0000:00:02.0: supports D1 D2
[    0.158956] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.158964] pci 0000:00:02.0: PME# disabled
[    0.158989] pci 0000:00:02.1: [10de:00d7] type 0 class 0x000c03
[    0.159007] pci 0000:00:02.1: reg 10: [mem 0xe0001000-0xe0001fff]
[    0.159057] pci 0000:00:02.1: supports D1 D2
[    0.159063] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159071] pci 0000:00:02.1: PME# disabled
[    0.159094] pci 0000:00:02.2: [10de:00d8] type 0 class 0x000c03
[    0.159112] pci 0000:00:02.2: reg 10: [mem 0xe0004000-0xe00040ff]
[    0.159162] pci 0000:00:02.2: supports D1 D2
[    0.159168] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159177] pci 0000:00:02.2: PME# disabled
[    0.159209] pci 0000:00:06.0: [10de:00da] type 0 class 0x000401
[    0.159226] pci 0000:00:06.0: reg 10: [io  0x1400-0x14ff]
[    0.159239] pci 0000:00:06.0: reg 14: [io  0x1c00-0x1c7f]
[    0.159251] pci 0000:00:06.0: reg 18: [mem 0xe0002000-0xe0002fff]
[    0.159290] pci 0000:00:06.0: supports D1 D2
[    0.159313] pci 0000:00:06.1: [10de:00d9] type 0 class 0x000703
[    0.159330] pci 0000:00:06.1: reg 10: [io  0x1800-0x18ff]
[    0.159343] pci 0000:00:06.1: reg 14: [io  0x1c80-0x1cff]
[    0.159355] pci 0000:00:06.1: reg 18: [mem 0xe0003000-0xe0003fff]
[    0.159395] pci 0000:00:06.1: PME# supported from D3cold
[    0.159403] pci 0000:00:06.1: PME# disabled
[    0.159433] pci 0000:00:08.0: [10de:00d5] type 0 class 0x000101
[    0.159470] pci 0000:00:08.0: reg 20: [io  0x2080-0x208f]
[    0.159514] pci 0000:00:0a.0: [10de:00dd] type 1 class 0x000604
[    0.159555] pci 0000:00:0b.0: [10de:00d2] type 1 class 0x000604
[    0.159619] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.159666] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.159704] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.159742] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.159781] PCI: peer root bus 00 res updated from pci conf
[    0.159817] pci 0000:02:00.0: [104c:8026] type 0 class 0x000c00
[    0.159840] pci 0000:02:00.0: reg 10: [mem 0xe0108000-0xe01087ff]
[    0.159855] pci 0000:02:00.0: reg 14: [mem 0xe0100000-0xe0103fff]
[    0.159917] pci 0000:02:00.0: supports D1 D2
[    0.159923] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.159932] pci 0000:02:00.0: PME# disabled
[    0.159958] pci 0000:02:01.0: [10ec:8139] type 0 class 0x000200
[    0.159980] pci 0000:02:01.0: reg 10: [io  0x7000-0x70ff]
[    0.159995] pci 0000:02:01.0: reg 14: [mem 0xe0108800-0xe01088ff]
[    0.160065] pci 0000:02:01.0: supports D1 D2
[    0.160072] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.160081] pci 0000:02:01.0: PME# disabled
[    0.160104] pci 0000:02:02.0: [14e4:4320] type 0 class 0x000280
[    0.160123] pci 0000:02:02.0: reg 10: [mem 0xe0104000-0xe0105fff]
[    0.160196] pci 0000:02:04.0: [104c:ac54] type 2 class 0x000607
[    0.160219] pci 0000:02:04.0: reg 10: [mem 0xe0106000-0xe0106fff]
[    0.160243] pci 0000:02:04.0: supports D1 D2
[    0.160249] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160258] pci 0000:02:04.0: PME# disabled
[    0.160285] pci 0000:02:04.1: [104c:ac54] type 2 class 0x000607
[    0.160307] pci 0000:02:04.1: reg 10: [mem 0xe0107000-0xe0107fff]
[    0.160331] pci 0000:02:04.1: supports D1 D2
[    0.160337] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160346] pci 0000:02:04.1: PME# disabled
[    0.160374] pci 0000:02:04.2: [104c:8201] type 0 class 0x000880
[    0.160394] pci 0000:02:04.2: reg 10: [io  0x7400-0x743f]
[    0.160503] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.160579] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.160588] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.160598] pci 0000:00:0a.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.160650] pci_bus 0000:03: [bus 03-06] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.160778] pci_bus 0000:07: [bus 07-0a] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.160903] pci 0000:01:00.0: [10de:0179] type 0 class 0x000300
[    0.160930] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
[    0.160946] pci 0000:01:00.0: reg 14: [mem 0xf0000000-0xf7ffffff pref]
[    0.160963] pci 0000:01:00.0: reg 18: [mem 0xf8000000-0xf807ffff pref]
[    0.161005] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.161084] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.161160] pci 0000:00:0b.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.161170] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.161180] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.162883] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.163135] pci 0000:00:01.0: default IRQ router [10de:00d0]
[    0.163271] PCI: pci_cache_line_size set to 64 bytes
[    0.163378] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.163385] reserve RAM buffer: 000000001ff70000 - 000000001fffffff 
[    0.163643] NetLabel: Initializing
[    0.163713] NetLabel:  domain hash size = 128
[    0.163782] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.163878] NetLabel:  unlabeled traffic allowed by default
[    0.181690] AppArmor: AppArmor Filesystem Enabled
[    0.181810] pnp: PnP ACPI: disabled
[    0.181882] PnPBIOS: Scanning system for PnP BIOS support...
[    0.181992] PnPBIOS: Found PnP BIOS installation structure at 0xc00f72c0
[    0.182069] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb71e, dseg 0x400
[    0.183016] pnp 00:00: [mem 0x00000000-0xffffffff disabled]
[    0.183024] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.183031] pnp 00:00: [mem 0x00100000-0x1ff7ffff]
[    0.183142] system 00:00: Plug and Play BIOS device, IDs PNP0c01 (disabled)
[    0.183160] pnp 00:01: [io  0x0000-0x000f]
[    0.183166] pnp 00:01: [io  0x0081-0x008f]
[    0.183173] pnp 00:01: [io  0x00c0-0x00df]
[    0.183179] pnp 00:01: [dma 4]
[    0.183234] pnp 00:01: Plug and Play BIOS device, IDs PNP0200 (active)
[    0.183250] pnp 00:02: [io  0x0020-0x0021]
[    0.183256] pnp 00:02: [io  0x00a0-0x00a1]
[    0.183263] pnp 00:02: [irq 2]
[    0.183310] pnp 00:02: Plug and Play BIOS device, IDs PNP0000 (active)
[    0.183325] pnp 00:03: [io  0x0040-0x0043]
[    0.183331] pnp 00:03: [irq 0]
[    0.183377] pnp 00:03: Plug and Play BIOS device, IDs PNP0100 (active)
[    0.183393] pnp 00:04: [io  0x0070-0x0071]
[    0.183399] pnp 00:04: [irq 8]
[    0.183445] pnp 00:04: Plug and Play BIOS device, IDs PNP0b00 (active)
[    0.183460] pnp 00:05: [io  0x0060]
[    0.183466] pnp 00:05: [io  0x0064]
[    0.183472] pnp 00:05: [irq 1]
[    0.183518] pnp 00:05: Plug and Play BIOS device, IDs PNP0303 (active)
[    0.183534] pnp 00:06: [io  0x00f0-0x00ff]
[    0.183540] pnp 00:06: [irq 13]
[    0.183594] pnp 00:06: Plug and Play BIOS device, IDs PNP0c04 (active)
[    0.183609] pnp 00:07: [io  0x0061]
[    0.183656] pnp 00:07: Plug and Play BIOS device, IDs PNP0800 (active)
[    0.183672] pnp 00:08: [mem 0x000d0000-0x000d3fff]
[    0.183760] system 00:08: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.183840] system 00:08: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.183857] pnp 00:09: [io  0xfe00-0xfe01]
[    0.183950] system 00:09: [io  0xfe00-0xfe01] has been reserved
[    0.184020] system 00:09: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.184037] pnp 00:0a: [io  0x0cf8-0x0cff]
[    0.184088] pnp 00:0a: Plug and Play BIOS device, IDs PNP0a03 (active)
[    0.184104] pnp 00:0b: [io  0x004e-0x004f]
[    0.184203] system 00:0b: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.184356] pnp 00:0c: [mem 0x000cfc00-0x000cffff]
[    0.184443] system 00:0c: [mem 0x000cfc00-0x000cffff] has been reserved
[    0.184522] system 00:0c: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.185176] pnp 00:0e: [irq 12]
[    0.185234] pnp 00:0e: Plug and Play BIOS device, IDs PNP0f13 (active)
[    0.186253] pnp 00:12: [io  0x0378-0x037f]
[    0.186260] pnp 00:12: [io  0x0778-0x077f]
[    0.186266] pnp 00:12: [irq 7]
[    0.186272] pnp 00:12: [dma 1]
[    0.186400] pnp 00:12: Plug and Play BIOS device, IDs PNP0401 (active)
[    0.186411] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[    0.190986] PCI: max bus depth: 2 pci_try_num: 3
[    0.191024] pci 0000:00:0a.0: BAR 15: assigned [mem 0x20000000-0x27ffffff pref]
[    0.191124] pci 0000:02:04.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.191219] pci 0000:02:04.0: BAR 16: can't assign mem (size 0x4000000)
[    0.191299] pci 0000:02:04.1: BAR 15: assigned [mem 0x24000000-0x27ffffff pref]
[    0.191392] pci 0000:02:04.1: BAR 16: can't assign mem (size 0x4000000)
[    0.191470] pci 0000:02:04.0: BAR 13: assigned [io  0x3000-0x30ff]
[    0.191546] pci 0000:02:04.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.191622] pci 0000:02:04.1: BAR 13: assigned [io  0x3800-0x38ff]
[    0.191699] pci 0000:02:04.1: BAR 14: assigned [io  0x3c00-0x3cff]
[    0.191775] pci 0000:02:04.0: CardBus bridge to [bus 03-06]
[    0.191850] pci 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[    0.191928] pci 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[    0.192007] pci 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.192020] pci 0000:02:04.1: CardBus bridge to [bus 07-0a]
[    0.192094] pci 0000:02:04.1:   bridge window [io  0x3800-0x38ff]
[    0.192171] pci 0000:02:04.1:   bridge window [io  0x3c00-0x3cff]
[    0.192249] pci 0000:02:04.1:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.192343] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.192418] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.192496] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.192574] pci 0000:00:0a.0:   bridge window [mem 0x20000000-0x27ffffff pref]
[    0.192672] pci 0000:01:00.0: BAR 6: assigned [mem 0xf8080000-0xf809ffff pref]
[    0.192765] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.192838] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.192915] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.192995] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.193099] pci 0000:00:0a.0: setting latency timer to 64
[    0.193133] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.193140] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.193148] pci_bus 0000:00: resource 6 [mem 0x20000000-0xffffffff]
[    0.193156] pci_bus 0000:02: resource 0 [io  0x3000-0x7fff]
[    0.193163] pci_bus 0000:02: resource 1 [mem 0xe0100000-0xe17fffff]
[    0.193171] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.193179] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.193186] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.193194] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.193202] pci_bus 0000:07: resource 0 [io  0x3800-0x38ff]
[    0.193209] pci_bus 0000:07: resource 1 [io  0x3c00-0x3cff]
[    0.193216] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.193224] pci_bus 0000:01: resource 1 [mem 0xe2000000-0xe2ffffff]
[    0.193232] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf80fffff pref]
[    0.193324] NET: Registered protocol family 2
[    0.193532] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.194080] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.194359] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.194625] TCP: Hash tables configured (established 16384 bind 16384)
[    0.194700] TCP reno registered
[    0.196020] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.196105] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.196335] NET: Registered protocol family 1
[    0.344104] PCI: CLS mismatch (64 != 32), using 64 bytes
[    0.344129] pci 0000:01:00.0: Boot video device
[    0.344800] audit: initializing netlink socket (disabled)
[    0.344887] type=2000 audit(1321047637.344:1): initialized
[    0.404666] Trying to unpack rootfs image as initramfs...
[    0.476245] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.485453] VFS: Disk quotas dquot_6.5.2
[    0.485682] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.492334] fuse init (API version 7.16)
[    0.492665] msgmni has been set to 964
[    0.504962] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.505122] io scheduler noop registered
[    0.505193] io scheduler deadline registered
[    0.505302] io scheduler cfq registered (default)
[    0.505750] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.505892] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.506310] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.509913] Linux agpgart interface v0.103
[    0.510040] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[    0.510121] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    0.510222] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    0.517325] isapnp: Scanning for PnP cards...
[    0.576992] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.584920] brd: module loaded
[    0.586622] loop: module loaded
[    0.587193] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.588233] Fixed MDIO Bus: probed
[    0.588373] PPP generic driver version 2.4.2
[    0.588542] tun: Universal TUN/TAP device driver, 1.6
[    0.588614] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.588871] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.588992] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    0.589000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    0.589170] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.589315] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    0.589336] ehci_hcd 0000:00:02.2: irq 10, io mem 0xe0004000
[    0.600714] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.601134] hub 1-0:1.0: USB hub found
[    0.601211] hub 1-0:1.0: 6 ports detected
[    0.601446] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.601569] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.601577] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.601735] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.601855] ohci_hcd 0000:00:02.0: irq 11, io mem 0xe0000000
[    0.670400] hub 2-0:1.0: USB hub found
[    0.670485] hub 2-0:1.0: 3 ports detected
[    0.670731] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    0.670739] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    0.670901] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    0.671023] ohci_hcd 0000:00:02.1: irq 10, io mem 0xe0001000
[    0.750819] hub 3-0:1.0: USB hub found
[    0.750904] hub 3-0:1.0: 3 ports detected
[    0.751142] uhci_hcd: USB Universal Host Controller Interface driver
[    0.751444] i8042: PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.760051] i8042: Detected active multiplexing controller, rev 1.1
[    0.892065] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.892153] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.892229] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.892304] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.892379] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.892671] mousedev: PS/2 mouse device common for all mice
[    0.900385] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.900483] rtc0: alarms up to one day, 114 bytes nvram
[    0.900845] device-mapper: uevent: version 1.0.3
[    0.901111] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.901289] EISA: Probing bus 0 at eisa.0
[    0.901364] EISA: Cannot allocate resource for mainboard
[    0.901438] Cannot allocate resource for EISA slot 1
[    0.901511] Cannot allocate resource for EISA slot 2
[    0.901583] Cannot allocate resource for EISA slot 3
[    0.901656] Cannot allocate resource for EISA slot 4
[    0.901728] Cannot allocate resource for EISA slot 5
[    0.901801] Cannot allocate resource for EISA slot 6
[    0.901873] Cannot allocate resource for EISA slot 7
[    0.901946] Cannot allocate resource for EISA slot 8
[    0.902018] EISA: Detected 0 cards.
[    0.902103] cpufreq-nforce2: No nForce2 chipset.
[    0.902176] cpuidle: using governor ladder
[    0.902246] cpuidle: using governor menu
[    0.902316] EFI Variables Facility v0.08 2004-May-17
[    0.903034] TCP cubic registered
[    0.908037] NET: Registered protocol family 10
[    0.909424] NET: Registered protocol family 17
[    0.909537] Registering the dns_resolver key type
[    0.909695] Using IPI No-Shortcut mode
[    0.909977] PM: Hibernation image not present or could not be loaded.
[    0.910001] registered taskstats version 1
[    0.926367] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.063157] isapnp: No Plug & Play device found
[    1.312322] usb 2-2: new low speed USB device number 2 using ohci_hcd
[    1.404197] Switching to clocksource tsc
[    1.683623] Freeing initrd memory: 13304k freed
[    1.716815]   Magic number: 3:219:702
[    1.717010] rtc_cmos 00:04: setting system clock to 2011-11-11 21:40:39 UTC (1321047639)
[    1.717107] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    1.721958] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.722034] powernow-k8: Make sure that your BIOS is up to date and Cool'N'Quiet support is enabled in BIOS setup
[    1.722136] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.722209] EDD information not available.
[    1.722537] Freeing unused kernel memory: 696k freed
[    1.723451] Write protecting the kernel text: 5332k
[    1.723609] Write protecting the kernel read-only data: 2188k
[    1.762764] udevd[76]: starting version 173
[    1.939306] pata_amd 0000:00:08.0: version 0.4.1
[    1.939402] pata_amd 0000:00:08.0: setting latency timer to 64
[    1.993900] scsi0 : pata_amd
[    1.997820] scsi1 : pata_amd
[    1.998025] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    1.998104] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    2.011515] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.011640] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.050982] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.050997] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.051008] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.051019] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.051029] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.054466] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    2.393791] ata1.00: ATA-6: FUJITSU MHT2060AT PL, 0022, max UDMA/100
[    2.393877] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.393961] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x0
[    2.408448] ata1.00: configured for UDMA/100
[    2.408783] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    2.409258] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.409638] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.409845] sd 0:0:0:0: [sda] Write Protect is off
[    2.409921] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.409973] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.515845]  sda: sda1 sda2 < sda5 >
[    2.516571] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.588389] ata2.00: ATAPI: SD-R6252, 1A11, max MWDMA2
[    2.588471] ata2: nv_mode_filter: 0x39f&0xfffff->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x0
[    2.620337] ata2.00: configured for MWDMA2
[    2.626555] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6252 1A11 PQ: 0 ANSI: 5
[    2.631175] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.631253] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.631545] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.631672] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.634910] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.639662] 8139too 0000:02:01.0: eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:01:07:31, IRQ 10
[    2.643255] input: HID 04b3:310b as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input1
[    2.643614] generic-usb 0003:04B3:310B.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:02.0-2/input0
[    2.643748] usbcore: registered new interface driver usbhid
[    2.643821] usbhid: USB HID core driver
[    2.700172] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.054589] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.054674] EXT4-fs (sda1): write access will be enabled during recovery
[    3.120317] EXT4-fs (sda1): recovery complete
[    3.120885] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.200324] firewire_core: created device fw0: GUID 463f0200463f0200, S400
[   30.600921] udevd[261]: starting version 173
[   30.670359] lp: driver loaded but no devices found
[   30.715718] Adding 521212k swap on /dev/sda5.  Priority:-1 extents:1 across:521212k 
[   30.950551] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[   30.950687] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   30.951896] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[   31.178761] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.516383] type=1400 audit(1321047669.296:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=471 comm="apparmor_parser"
[   31.518361] type=1400 audit(1321047669.296:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=471 comm="apparmor_parser"
[   31.519126] type=1400 audit(1321047669.296:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=471 comm="apparmor_parser"
[   31.531634] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.707749] nf_conntrack version 0.5.0 (7934 buckets, 31736 max)
[   31.807732] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   32.002450] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006d]
[   32.002483] yenta_cardbus 0000:02:04.0: CardBus bridge to [bus 03-06]
[   32.002492] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[   32.002503] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[   32.002514] yenta_cardbus 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[   32.002525] yenta_cardbus 0000:02:04.0:   bridge window [mem 0xe0400000-0xe07fffff]
[   32.002536] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   32.002546] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   32.002553] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   32.002564] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   32.234777] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x02f8, PCI irq 11
[   32.234788] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   32.234799] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   32.234820] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   32.234830] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   32.550162] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input2
[   32.571505] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input3
[   32.744246] cfg80211: Calling CRDA to update world regulatory domain
[   32.776088] nvidia: module license 'NVIDIA' taints kernel.
[   32.776099] Disabling lock debugging due to kernel taint
[   32.803632]  0x7000-0x70ff 0x7400-0x743f
[   33.689620] 8139too 0000:02:01.0: eth0: link down
[   33.689829] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.789124] 
[   33.789140] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe0100000-0xe17fffff]
[   33.789153] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0100000-0xe17fffff: excluding 0xe0100000-0xe026ffff 0xe03e0000-0xe082ffff
[   33.789190] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   33.789199] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   33.839067] type=1400 audit(1321047671.616:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=675 comm="apparmor_parser"
[   33.845315] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006d]
[   33.845344] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   33.845352] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   33.845363] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   33.853458] type=1400 audit(1321047671.632:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=683 comm="apparmor_parser"
[   33.854653] type=1400 audit(1321047671.632:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=683 comm="apparmor_parser"
[   33.855425] type=1400 audit(1321047671.632:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=683 comm="apparmor_parser"
[   33.901053] type=1400 audit(1321047671.680:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=689 comm="apparmor_parser"
[   33.933248] type=1400 audit(1321047671.712:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=689 comm="apparmor_parser"
[   33.954134] type=1400 audit(1321047671.732:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=689 comm="apparmor_parser"
[   34.080538] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x02f8, PCI irq 10
[   34.080549] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   34.080560] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   34.080579] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   34.080589] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   34.304330] apm: BIOS not found.
[   34.358643] init: apport pre-start process (748) terminated with status 1
[   34.362100] init: alsa-restore main process (753) terminated with status 19
[   34.415779] init: apport post-stop process (777) terminated with status 1
[   34.678835]  0x7000-0x70ff 0x7400-0x743f
```

@matt_symmes I will try it and see what happens, and let you guys know.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-11
Ok... I took off "acpi=off" and added "init=/bin/bash"
and it locked up (very quickly I might add)
Well... I really appreciate all of your attention to this issue of mine!  I have tried @ launchpad a few times to get help/figure out what's up (hence finding the 'acpi=off' feature)

It is weird...  a majority of distros have done it (in LiveCD mode...)  but any of the puppy distros I have tried don't have that problem.  well... thanks again!

---

### Post by Toz on 2011-11-11
> **TREESofRIGHTEOUSNESS said:**
> @Toz  it is actually a Presario R3000...
OK.. I hope I got this right...

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7f000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7f000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Hewlett-Packard  Presario R3200 (PF153UA#ABA)  /08A0, BIOS F.11 04/30/2004
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ff70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-D3FFF write-back
[    0.000000]   D4000-D4FFF write-protect
[    0.000000]   D5000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000001ff70000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001ff70000 page 4k
[    0.000000] kernel direct mapping tables up to 1ff70000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 1dcb2000 - 1e9b0000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ff70000
[    0.000000]   low ram: 0 - 1ff70000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ff70
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ff70
[    0.000000] On node 0 totalpages: 130815
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map dfb6f200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dff80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @df400000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b61c59af-7f66-4df5-b2d5-928314a8ddd3 ro acpi=off
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2094592 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 493808k/523712k available (5329k kernel code, 29452k reserved, 2589k data, 696k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe0770000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=df006000 soft=df008000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 797.889 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 1595.77 BogoMIPS (lpj=3191556)
[    0.008160] pid_max: default: 32768 minimum: 301
[    0.008292] Security Framework initialized
[    0.008417] AppArmor: AppArmor initialized
[    0.008490] Yama: becoming mindful.
[    0.008717] Mount-cache hash table entries: 512
[    0.009112] Initializing cgroup subsys cpuacct
[    0.009198] Initializing cgroup subsys memory
[    0.009291] Initializing cgroup subsys devices
[    0.009367] Initializing cgroup subsys freezer
[    0.009442] Initializing cgroup subsys net_cls
[    0.009518] Initializing cgroup subsys blkio
[    0.009605] Initializing cgroup subsys perf_event
[    0.009743] mce: CPU supports 5 MCE banks
[    0.010330] SMP alternatives: switching to UP code
[    0.032433] Freeing SMP alternatives: 24k freed
[    0.032544] ftrace: allocating 24885 entries in 49 pages
[    0.036163] weird, boot CPU (#0) not listed by the BIOS.
[    0.036242] SMP motherboard not detected.
[    0.036314] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.144031] SMP disabled
[    0.144099] Performance Events: AMD PMU driver.
[    0.144225] ... version:                0
[    0.144295] ... bit width:              48
[    0.144365] ... generic registers:      4
[    0.144435] ... value mask:             0000ffffffffffff
[    0.144509] ... max period:             00007fffffffffff
[    0.144581] ... fixed-purpose events:   0
[    0.144651] ... event mask:             000000000000000f
[    0.145763] Brought up 1 CPUs
[    0.145833] Total of 1 processors activated (1595.77 BogoMIPS).
[    0.146148] devtmpfs: initialized
[    0.146562] PM: Registering ACPI NVS region at 1ff7f000 (4096 bytes)
[    0.152127] print_constraints: dummy: 
[    0.152229] Time: 21:40:37  Date: 11/11/11
[    0.152384] NET: Registered protocol family 16
[    0.152773] EISA bus registered
[    0.152849] node 0 link 0: io port [1000, fffff]
[    0.152858] TOM: 0000000020000000 aka 512M
[    0.152932] node 0 link 0: mmio [a0000, bffff]
[    0.152941] node 0 link 0: mmio [20000000, fe0bffff]
[    0.152949] bus: [00, ff] on node 0 link 0
[    0.152957] bus: 00 index 0 [io  0x0000-0xffff]
[    0.152964] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.152971] bus: 00 index 2 [mem 0x20000000-0xffffffff]
[    0.153330] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[    0.153406] PCI: Using configuration type 1 for base access
[    0.156495] bio: create slab <bio-0> at 0
[    0.156767] ACPI: Interpreter disabled.
[    0.156978] vgaarb: loaded
[    0.157636] SCSI subsystem initialized
[    0.157807] libata version 3.00 loaded.
[    0.157922] usbcore: registered new interface driver usbfs
[    0.158022] usbcore: registered new interface driver hub
[    0.158153] usbcore: registered new device driver usb
[    0.158447] PCI: Probing PCI hardware
[    0.158519] PCI: Probing PCI hardware (bus 00)
[    0.158608] pci 0000:00:00.0: [10de:00d1] type 0 class 0x000600
[    0.158626] pci 0000:00:00.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.158703] pci 0000:00:01.0: [10de:00d0] type 0 class 0x000601
[    0.158768] pci 0000:00:01.1: [10de:00d4] type 0 class 0x000c05
[    0.158806] pci 0000:00:01.1: reg 20: [io  0x2040-0x207f]
[    0.158819] pci 0000:00:01.1: reg 24: [io  0x2000-0x203f]
[    0.158844] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.158853] pci 0000:00:01.1: PME# disabled
[    0.158882] pci 0000:00:02.0: [10de:00d7] type 0 class 0x000c03
[    0.158900] pci 0000:00:02.0: reg 10: [mem 0xe0000000-0xe0000fff]
[    0.158949] pci 0000:00:02.0: supports D1 D2
[    0.158956] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.158964] pci 0000:00:02.0: PME# disabled
[    0.158989] pci 0000:00:02.1: [10de:00d7] type 0 class 0x000c03
[    0.159007] pci 0000:00:02.1: reg 10: [mem 0xe0001000-0xe0001fff]
[    0.159057] pci 0000:00:02.1: supports D1 D2
[    0.159063] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159071] pci 0000:00:02.1: PME# disabled
[    0.159094] pci 0000:00:02.2: [10de:00d8] type 0 class 0x000c03
[    0.159112] pci 0000:00:02.2: reg 10: [mem 0xe0004000-0xe00040ff]
[    0.159162] pci 0000:00:02.2: supports D1 D2
[    0.159168] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159177] pci 0000:00:02.2: PME# disabled
[    0.159209] pci 0000:00:06.0: [10de:00da] type 0 class 0x000401
[    0.159226] pci 0000:00:06.0: reg 10: [io  0x1400-0x14ff]
[    0.159239] pci 0000:00:06.0: reg 14: [io  0x1c00-0x1c7f]
[    0.159251] pci 0000:00:06.0: reg 18: [mem 0xe0002000-0xe0002fff]
[    0.159290] pci 0000:00:06.0: supports D1 D2
[    0.159313] pci 0000:00:06.1: [10de:00d9] type 0 class 0x000703
[    0.159330] pci 0000:00:06.1: reg 10: [io  0x1800-0x18ff]
[    0.159343] pci 0000:00:06.1: reg 14: [io  0x1c80-0x1cff]
[    0.159355] pci 0000:00:06.1: reg 18: [mem 0xe0003000-0xe0003fff]
[    0.159395] pci 0000:00:06.1: PME# supported from D3cold
[    0.159403] pci 0000:00:06.1: PME# disabled
[    0.159433] pci 0000:00:08.0: [10de:00d5] type 0 class 0x000101
[    0.159470] pci 0000:00:08.0: reg 20: [io  0x2080-0x208f]
[    0.159514] pci 0000:00:0a.0: [10de:00dd] type 1 class 0x000604
[    0.159555] pci 0000:00:0b.0: [10de:00d2] type 1 class 0x000604
[    0.159619] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.159666] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.159704] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.159742] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.159781] PCI: peer root bus 00 res updated from pci conf
[    0.159817] pci 0000:02:00.0: [104c:8026] type 0 class 0x000c00
[    0.159840] pci 0000:02:00.0: reg 10: [mem 0xe0108000-0xe01087ff]
[    0.159855] pci 0000:02:00.0: reg 14: [mem 0xe0100000-0xe0103fff]
[    0.159917] pci 0000:02:00.0: supports D1 D2
[    0.159923] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.159932] pci 0000:02:00.0: PME# disabled
[    0.159958] pci 0000:02:01.0: [10ec:8139] type 0 class 0x000200
[    0.159980] pci 0000:02:01.0: reg 10: [io  0x7000-0x70ff]
[    0.159995] pci 0000:02:01.0: reg 14: [mem 0xe0108800-0xe01088ff]
[    0.160065] pci 0000:02:01.0: supports D1 D2
[    0.160072] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.160081] pci 0000:02:01.0: PME# disabled
[    0.160104] pci 0000:02:02.0: [14e4:4320] type 0 class 0x000280
[    0.160123] pci 0000:02:02.0: reg 10: [mem 0xe0104000-0xe0105fff]
[    0.160196] pci 0000:02:04.0: [104c:ac54] type 2 class 0x000607
[    0.160219] pci 0000:02:04.0: reg 10: [mem 0xe0106000-0xe0106fff]
[    0.160243] pci 0000:02:04.0: supports D1 D2
[    0.160249] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160258] pci 0000:02:04.0: PME# disabled
[    0.160285] pci 0000:02:04.1: [104c:ac54] type 2 class 0x000607
[    0.160307] pci 0000:02:04.1: reg 10: [mem 0xe0107000-0xe0107fff]
[    0.160331] pci 0000:02:04.1: supports D1 D2
[    0.160337] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.160346] pci 0000:02:04.1: PME# disabled
[    0.160374] pci 0000:02:04.2: [104c:8201] type 0 class 0x000880
[    0.160394] pci 0000:02:04.2: reg 10: [io  0x7400-0x743f]
[    0.160503] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.160579] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.160588] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.160598] pci 0000:00:0a.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.160650] pci_bus 0000:03: [bus 03-06] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.160778] pci_bus 0000:07: [bus 07-0a] partially hidden behind bridge 0000:02 [bus 02-02]
[    0.160903] pci 0000:01:00.0: [10de:0179] type 0 class 0x000300
[    0.160930] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
[    0.160946] pci 0000:01:00.0: reg 14: [mem 0xf0000000-0xf7ffffff pref]
[    0.160963] pci 0000:01:00.0: reg 18: [mem 0xf8000000-0xf807ffff pref]
[    0.161005] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.161084] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.161160] pci 0000:00:0b.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.161170] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.161180] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.162883] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.163135] pci 0000:00:01.0: default IRQ router [10de:00d0]
[    0.163271] PCI: pci_cache_line_size set to 64 bytes
[    0.163378] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.163385] reserve RAM buffer: 000000001ff70000 - 000000001fffffff 
[    0.163643] NetLabel: Initializing
[    0.163713] NetLabel:  domain hash size = 128
[    0.163782] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.163878] NetLabel:  unlabeled traffic allowed by default
[    0.181690] AppArmor: AppArmor Filesystem Enabled
[    0.181810] pnp: PnP ACPI: disabled
[    0.181882] PnPBIOS: Scanning system for PnP BIOS support...
[    0.181992] PnPBIOS: Found PnP BIOS installation structure at 0xc00f72c0
[    0.182069] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb71e, dseg 0x400
[    0.183016] pnp 00:00: [mem 0x00000000-0xffffffff disabled]
[    0.183024] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.183031] pnp 00:00: [mem 0x00100000-0x1ff7ffff]
[    0.183142] system 00:00: Plug and Play BIOS device, IDs PNP0c01 (disabled)
[    0.183160] pnp 00:01: [io  0x0000-0x000f]
[    0.183166] pnp 00:01: [io  0x0081-0x008f]
[    0.183173] pnp 00:01: [io  0x00c0-0x00df]
[    0.183179] pnp 00:01: [dma 4]
[    0.183234] pnp 00:01: Plug and Play BIOS device, IDs PNP0200 (active)
[    0.183250] pnp 00:02: [io  0x0020-0x0021]
[    0.183256] pnp 00:02: [io  0x00a0-0x00a1]
[    0.183263] pnp 00:02: [irq 2]
[    0.183310] pnp 00:02: Plug and Play BIOS device, IDs PNP0000 (active)
[    0.183325] pnp 00:03: [io  0x0040-0x0043]
[    0.183331] pnp 00:03: [irq 0]
[    0.183377] pnp 00:03: Plug and Play BIOS device, IDs PNP0100 (active)
[    0.183393] pnp 00:04: [io  0x0070-0x0071]
[    0.183399] pnp 00:04: [irq 8]
[    0.183445] pnp 00:04: Plug and Play BIOS device, IDs PNP0b00 (active)
[    0.183460] pnp 00:05: [io  0x0060]
[    0.183466] pnp 00:05: [io  0x0064]
[    0.183472] pnp 00:05: [irq 1]
[    0.183518] pnp 00:05: Plug and Play BIOS device, IDs PNP0303 (active)
[    0.183534] pnp 00:06: [io  0x00f0-0x00ff]
[    0.183540] pnp 00:06: [irq 13]
[    0.183594] pnp 00:06: Plug and Play BIOS device, IDs PNP0c04 (active)
[    0.183609] pnp 00:07: [io  0x0061]
[    0.183656] pnp 00:07: Plug and Play BIOS device, IDs PNP0800 (active)
[    0.183672] pnp 00:08: [mem 0x000d0000-0x000d3fff]
[    0.183760] system 00:08: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.183840] system 00:08: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.183857] pnp 00:09: [io  0xfe00-0xfe01]
[    0.183950] system 00:09: [io  0xfe00-0xfe01] has been reserved
[    0.184020] system 00:09: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.184037] pnp 00:0a: [io  0x0cf8-0x0cff]
[    0.184088] pnp 00:0a: Plug and Play BIOS device, IDs PNP0a03 (active)
[    0.184104] pnp 00:0b: [io  0x004e-0x004f]
[    0.184203] system 00:0b: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.184356] pnp 00:0c: [mem 0x000cfc00-0x000cffff]
[    0.184443] system 00:0c: [mem 0x000cfc00-0x000cffff] has been reserved
[    0.184522] system 00:0c: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.185176] pnp 00:0e: [irq 12]
[    0.185234] pnp 00:0e: Plug and Play BIOS device, IDs PNP0f13 (active)
[    0.186253] pnp 00:12: [io  0x0378-0x037f]
[    0.186260] pnp 00:12: [io  0x0778-0x077f]
[    0.186266] pnp 00:12: [irq 7]
[    0.186272] pnp 00:12: [dma 1]
[    0.186400] pnp 00:12: Plug and Play BIOS device, IDs PNP0401 (active)
[    0.186411] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[    0.190986] PCI: max bus depth: 2 pci_try_num: 3
[    0.191024] pci 0000:00:0a.0: BAR 15: assigned [mem 0x20000000-0x27ffffff pref]
[    0.191124] pci 0000:02:04.0: BAR 15: assigned [mem 0x20000000-0x23ffffff pref]
[    0.191219] pci 0000:02:04.0: BAR 16: can't assign mem (size 0x4000000)
[    0.191299] pci 0000:02:04.1: BAR 15: assigned [mem 0x24000000-0x27ffffff pref]
[    0.191392] pci 0000:02:04.1: BAR 16: can't assign mem (size 0x4000000)
[    0.191470] pci 0000:02:04.0: BAR 13: assigned [io  0x3000-0x30ff]
[    0.191546] pci 0000:02:04.0: BAR 14: assigned [io  0x3400-0x34ff]
[    0.191622] pci 0000:02:04.1: BAR 13: assigned [io  0x3800-0x38ff]
[    0.191699] pci 0000:02:04.1: BAR 14: assigned [io  0x3c00-0x3cff]
[    0.191775] pci 0000:02:04.0: CardBus bridge to [bus 03-06]
[    0.191850] pci 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[    0.191928] pci 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[    0.192007] pci 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[    0.192020] pci 0000:02:04.1: CardBus bridge to [bus 07-0a]
[    0.192094] pci 0000:02:04.1:   bridge window [io  0x3800-0x38ff]
[    0.192171] pci 0000:02:04.1:   bridge window [io  0x3c00-0x3cff]
[    0.192249] pci 0000:02:04.1:   bridge window [mem 0x24000000-0x27ffffff pref]
[    0.192343] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.192418] pci 0000:00:0a.0:   bridge window [io  0x3000-0x7fff]
[    0.192496] pci 0000:00:0a.0:   bridge window [mem 0xe0100000-0xe17fffff]
[    0.192574] pci 0000:00:0a.0:   bridge window [mem 0x20000000-0x27ffffff pref]
[    0.192672] pci 0000:01:00.0: BAR 6: assigned [mem 0xf8080000-0xf809ffff pref]
[    0.192765] pci 0000:00:0b.0: PCI bridge to [bus 01-01]
[    0.192838] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.192915] pci 0000:00:0b.0:   bridge window [mem 0xe2000000-0xe2ffffff]
[    0.192995] pci 0000:00:0b.0:   bridge window [mem 0xf0000000-0xf80fffff pref]
[    0.193099] pci 0000:00:0a.0: setting latency timer to 64
[    0.193133] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.193140] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.193148] pci_bus 0000:00: resource 6 [mem 0x20000000-0xffffffff]
[    0.193156] pci_bus 0000:02: resource 0 [io  0x3000-0x7fff]
[    0.193163] pci_bus 0000:02: resource 1 [mem 0xe0100000-0xe17fffff]
[    0.193171] pci_bus 0000:02: resource 2 [mem 0x20000000-0x27ffffff pref]
[    0.193179] pci_bus 0000:03: resource 0 [io  0x3000-0x30ff]
[    0.193186] pci_bus 0000:03: resource 1 [io  0x3400-0x34ff]
[    0.193194] pci_bus 0000:03: resource 2 [mem 0x20000000-0x23ffffff pref]
[    0.193202] pci_bus 0000:07: resource 0 [io  0x3800-0x38ff]
[    0.193209] pci_bus 0000:07: resource 1 [io  0x3c00-0x3cff]
[    0.193216] pci_bus 0000:07: resource 2 [mem 0x24000000-0x27ffffff pref]
[    0.193224] pci_bus 0000:01: resource 1 [mem 0xe2000000-0xe2ffffff]
[    0.193232] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf80fffff pref]
[    0.193324] NET: Registered protocol family 2
[    0.193532] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.194080] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.194359] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.194625] TCP: Hash tables configured (established 16384 bind 16384)
[    0.194700] TCP reno registered
[    0.196020] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.196105] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.196335] NET: Registered protocol family 1
[    0.344104] PCI: CLS mismatch (64 != 32), using 64 bytes
[    0.344129] pci 0000:01:00.0: Boot video device
[    0.344800] audit: initializing netlink socket (disabled)
[    0.344887] type=2000 audit(1321047637.344:1): initialized
[    0.404666] Trying to unpack rootfs image as initramfs...
[    0.476245] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.485453] VFS: Disk quotas dquot_6.5.2
[    0.485682] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.492334] fuse init (API version 7.16)
[    0.492665] msgmni has been set to 964
[    0.504962] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.505122] io scheduler noop registered
[    0.505193] io scheduler deadline registered
[    0.505302] io scheduler cfq registered (default)
[    0.505750] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.505892] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.506310] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.509913] Linux agpgart interface v0.103
[    0.510040] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[    0.510121] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    0.510222] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    0.517325] isapnp: Scanning for PnP cards...
[    0.576992] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.584920] brd: module loaded
[    0.586622] loop: module loaded
[    0.587193] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.588233] Fixed MDIO Bus: probed
[    0.588373] PPP generic driver version 2.4.2
[    0.588542] tun: Universal TUN/TAP device driver, 1.6
[    0.588614] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.588871] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.588992] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    0.589000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    0.589170] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.589315] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    0.589336] ehci_hcd 0000:00:02.2: irq 10, io mem 0xe0004000
[    0.600714] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.601134] hub 1-0:1.0: USB hub found
[    0.601211] hub 1-0:1.0: 6 ports detected
[    0.601446] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.601569] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.601577] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.601735] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.601855] ohci_hcd 0000:00:02.0: irq 11, io mem 0xe0000000
[    0.670400] hub 2-0:1.0: USB hub found
[    0.670485] hub 2-0:1.0: 3 ports detected
[    0.670731] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    0.670739] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    0.670901] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    0.671023] ohci_hcd 0000:00:02.1: irq 10, io mem 0xe0001000
[    0.750819] hub 3-0:1.0: USB hub found
[    0.750904] hub 3-0:1.0: 3 ports detected
[    0.751142] uhci_hcd: USB Universal Host Controller Interface driver
[    0.751444] i8042: PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    0.760051] i8042: Detected active multiplexing controller, rev 1.1
[    0.892065] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.892153] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.892229] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.892304] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.892379] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.892671] mousedev: PS/2 mouse device common for all mice
[    0.900385] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.900483] rtc0: alarms up to one day, 114 bytes nvram
[    0.900845] device-mapper: uevent: version 1.0.3
[    0.901111] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.901289] EISA: Probing bus 0 at eisa.0
[    0.901364] EISA: Cannot allocate resource for mainboard
[    0.901438] Cannot allocate resource for EISA slot 1
[    0.901511] Cannot allocate resource for EISA slot 2
[    0.901583] Cannot allocate resource for EISA slot 3
[    0.901656] Cannot allocate resource for EISA slot 4
[    0.901728] Cannot allocate resource for EISA slot 5
[    0.901801] Cannot allocate resource for EISA slot 6
[    0.901873] Cannot allocate resource for EISA slot 7
[    0.901946] Cannot allocate resource for EISA slot 8
[    0.902018] EISA: Detected 0 cards.
[    0.902103] cpufreq-nforce2: No nForce2 chipset.
[    0.902176] cpuidle: using governor ladder
[    0.902246] cpuidle: using governor menu
[    0.902316] EFI Variables Facility v0.08 2004-May-17
[    0.903034] TCP cubic registered
[    0.908037] NET: Registered protocol family 10
[    0.909424] NET: Registered protocol family 17
[    0.909537] Registering the dns_resolver key type
[    0.909695] Using IPI No-Shortcut mode
[    0.909977] PM: Hibernation image not present or could not be loaded.
[    0.910001] registered taskstats version 1
[    0.926367] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.063157] isapnp: No Plug & Play device found
[    1.312322] usb 2-2: new low speed USB device number 2 using ohci_hcd
[    1.404197] Switching to clocksource tsc
[    1.683623] Freeing initrd memory: 13304k freed
[    1.716815]   Magic number: 3:219:702
[    1.717010] rtc_cmos 00:04: setting system clock to 2011-11-11 21:40:39 UTC (1321047639)
[    1.717107] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    1.721958] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.722034] powernow-k8: Make sure that your BIOS is up to date and Cool'N'Quiet support is enabled in BIOS setup
[    1.722136] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.722209] EDD information not available.
[    1.722537] Freeing unused kernel memory: 696k freed
[    1.723451] Write protecting the kernel text: 5332k
[    1.723609] Write protecting the kernel read-only data: 2188k
[    1.762764] udevd[76]: starting version 173
[    1.939306] pata_amd 0000:00:08.0: version 0.4.1
[    1.939402] pata_amd 0000:00:08.0: setting latency timer to 64
[    1.993900] scsi0 : pata_amd
[    1.997820] scsi1 : pata_amd
[    1.998025] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    1.998104] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    2.011515] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.011640] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.050982] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    2.050997] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    2.051008] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    2.051019] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    2.051029] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    2.054466] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    2.393791] ata1.00: ATA-6: FUJITSU MHT2060AT PL, 0022, max UDMA/100
[    2.393877] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.393961] ata1: nv_mode_filter: 0x3f39f&0x3f3ff->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x0
[    2.408448] ata1.00: configured for UDMA/100
[    2.408783] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    2.409258] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.409638] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.409845] sd 0:0:0:0: [sda] Write Protect is off
[    2.409921] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.409973] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.515845]  sda: sda1 sda2 < sda5 >
[    2.516571] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.588389] ata2.00: ATAPI: SD-R6252, 1A11, max MWDMA2
[    2.588471] ata2: nv_mode_filter: 0x39f&0xfffff->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x0
[    2.620337] ata2.00: configured for MWDMA2
[    2.626555] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6252 1A11 PQ: 0 ANSI: 5
[    2.631175] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.631253] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.631545] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.631672] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.634910] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.639662] 8139too 0000:02:01.0: eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:01:07:31, IRQ 10
[    2.643255] input: HID 04b3:310b as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input1
[    2.643614] generic-usb 0003:04B3:310B.0001: input,hidraw0: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:02.0-2/input0
[    2.643748] usbcore: registered new interface driver usbhid
[    2.643821] usbhid: USB HID core driver
[    2.700172] firewire_ohci: Added fw-ohci device 0000:02:00.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.054589] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.054674] EXT4-fs (sda1): write access will be enabled during recovery
[    3.120317] EXT4-fs (sda1): recovery complete
[    3.120885] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.200324] firewire_core: created device fw0: GUID 463f0200463f0200, S400
[   30.600921] udevd[261]: starting version 173
[   30.670359] lp: driver loaded but no devices found
[   30.715718] Adding 521212k swap on /dev/sda5.  Priority:-1 extents:1 across:521212k 
[   30.950551] i2c i2c-0: nForce2 SMBus adapter at 0x2040
[   30.950687] i2c i2c-1: nForce2 SMBus adapter at 0x2000
[   30.951896] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[   31.178761] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.516383] type=1400 audit(1321047669.296:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=471 comm="apparmor_parser"
[   31.518361] type=1400 audit(1321047669.296:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=471 comm="apparmor_parser"
[   31.519126] type=1400 audit(1321047669.296:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=471 comm="apparmor_parser"
[   31.531634] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.707749] nf_conntrack version 0.5.0 (7934 buckets, 31736 max)
[   31.807732] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   32.002450] yenta_cardbus 0000:02:04.0: CardBus bridge found [103c:006d]
[   32.002483] yenta_cardbus 0000:02:04.0: CardBus bridge to [bus 03-06]
[   32.002492] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3000-0x30ff]
[   32.002503] yenta_cardbus 0000:02:04.0:   bridge window [io  0x3400-0x34ff]
[   32.002514] yenta_cardbus 0000:02:04.0:   bridge window [mem 0x20000000-0x23ffffff pref]
[   32.002525] yenta_cardbus 0000:02:04.0:   bridge window [mem 0xe0400000-0xe07fffff]
[   32.002536] yenta_cardbus 0000:02:04.0: Enabling burst memory read transactions
[   32.002546] yenta_cardbus 0000:02:04.0: Using CSCINT to route CSC interrupts to PCI
[   32.002553] yenta_cardbus 0000:02:04.0: Routing CardBus interrupts to PCI
[   32.002564] yenta_cardbus 0000:02:04.0: TI: mfunc 0x01111d22, devctl 0x64
[   32.234777] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x02f8, PCI irq 11
[   32.234788] yenta_cardbus 0000:02:04.0: Socket status: 30000086
[   32.234799] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   32.234820] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   32.234830] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   32.550162] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input2
[   32.571505] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input3
[   32.744246] cfg80211: Calling CRDA to update world regulatory domain
[   32.776088] nvidia: module license 'NVIDIA' taints kernel.
[   32.776099] Disabling lock debugging due to kernel taint
[   32.803632]  0x7000-0x70ff 0x7400-0x743f
[   33.689620] 8139too 0000:02:01.0: eth0: link down
[   33.689829] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.789124] 
[   33.789140] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0xe0100000-0xe17fffff]
[   33.789153] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe0100000-0xe17fffff: excluding 0xe0100000-0xe026ffff 0xe03e0000-0xe082ffff
[   33.789190] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge window: [mem 0x20000000-0x27ffffff pref]
[   33.789199] pcmcia_socket pcmcia_socket0: cs: memory probe 0x20000000-0x27ffffff: excluding 0x20000000-0x27ffffff
[   33.839067] type=1400 audit(1321047671.616:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=675 comm="apparmor_parser"
[   33.845315] yenta_cardbus 0000:02:04.1: CardBus bridge found [103c:006d]
[   33.845344] yenta_cardbus 0000:02:04.1: Using CSCINT to route CSC interrupts to PCI
[   33.845352] yenta_cardbus 0000:02:04.1: Routing CardBus interrupts to PCI
[   33.845363] yenta_cardbus 0000:02:04.1: TI: mfunc 0x01111d22, devctl 0x64
[   33.853458] type=1400 audit(1321047671.632:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=683 comm="apparmor_parser"
[   33.854653] type=1400 audit(1321047671.632:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=683 comm="apparmor_parser"
[   33.855425] type=1400 audit(1321047671.632:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=683 comm="apparmor_parser"
[   33.901053] type=1400 audit(1321047671.680:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=689 comm="apparmor_parser"
[   33.933248] type=1400 audit(1321047671.712:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=689 comm="apparmor_parser"
[   33.954134] type=1400 audit(1321047671.732:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=689 comm="apparmor_parser"
[   34.080538] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x02f8, PCI irq 10
[   34.080549] yenta_cardbus 0000:02:04.1: Socket status: 30000006
[   34.080560] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   34.080579] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge window: [io  0x3000-0x7fff]
[   34.080589] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x7fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   34.304330] apm: BIOS not found.
[   34.358643] init: apport pre-start process (748) terminated with status 1
[   34.362100] init: alsa-restore main process (753) terminated with status 19
[   34.415779] init: apport post-stop process (777) terminated with status 1
[   34.678835]  0x7000-0x70ff 0x7400-0x743f
```

@matt_symmes I will try it and see what happens, and let you guys know.

Sorry, still showing acpi=off. Can you zip all of your dmesg files together and post them? I'm wondering if maybe there is no log file created when you don't use acpi-off.

---

### Post by Toz on 2011-11-11
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421244]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421244")
Have you tried **nohz=off**?

Also, on a bit of a weird hunch, can you try the kernel parameter **acpi_osi="Windows 2006"**? (If you do are testing this by changing /etc/default/grub and running update-grub, you may need to use **acpi_osi=\"Windows 2006\"**)

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-12
I have not tried nohz=off, but I will.  and if that doesn't do, I will try the windows 2006 one...
then I will try to boot with acpi=off and send it your way

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-12
Ok.... here are all of them.... I tried both of the boot params and nothing BUT.. when I booted afterward w/o acpi=off IT WORKED!!  Now that is bizarre!

---

### Post by rj45 on 2011-11-12
> **TREESofRIGHTEOUSNESS said:**
> Ok.... here are all of them.... I tried both of the boot params and nothing BUT.. when I booted afterward w/o acpi=off IT WORKED!!  Now that is bizarre!

That's what was happening to me with 11.04 - I was able to boot for a few weeks without "acpi=off", then something changed (maybe an update) and I need to put that param back in.  It didn't bother me, but my laptop ran very hot - I saw temps about 90C, way too hot for me.

good luck, I'll keep monitoring this thread for a while.....

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-12
My only big issue is having to manually turn it off after the system halts....
I haven't monitored the temp, though....  what app do you use?

---

### Post by rj45 on 2011-11-12
> **TREESofRIGHTEOUSNESS said:**
> My only big issue is having to manually turn it off after the system halts....
I haven't monitored the temp, though....  what app do you use?

lm-sensors

do this:
sudo apt-get install lm-sensors
sudo sensors-detect
(let it automatically modify your modules file)
reboot
then as regular user or root, doesn't matter
sensors <enter>
reports current CPU and motherboard temps
repeat "sensors" after 5 or 10 minutes. to see trends

---

### Post by Toz on 2011-11-12
> **TREESofRIGHTEOUSNESS said:**
> Ok.... here are all of them.... I tried both of the boot params and nothing BUT.. when I booted afterward w/o acpi=off IT WORKED!!  Now that is bizarre!

That is bizarre. Many of those error message are gone from the log file where acpi is enabled. Did you change any settings in the BIOS?

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-12
no.  I just tried those 2 options that were suggested.  My BIOS is very basic. Just boot options, and security options.
I haven't shutdown since I posted, so if you need me to check something else let me know

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
well.  I shutdown that time, and my computer powered itself off, which was nice... but now it does the same thing.  I wonder if using the windows parameter tricked the computer into thinking it did something, so the next time it booted it thought everything was fine.  Is there a way to permenantly trick it into using ACPI? Since it worked that one time, there MUST be a solution.
Thanks again for your tireless efforts, it seems as though there was some sort of breakthrough, though I don't understand it.

---

### Post by Toz on 2011-11-13
> **TREESofRIGHTEOUSNESS said:**
> well.  I shutdown that time, and my computer powered itself off, which was nice... but now it does the same thing.  I wonder if using the windows parameter tricked the computer into thinking it did something, so the next time it booted it thought everything was fine.  Is there a way to permenantly trick it into using ACPI? Since it worked that one time, there MUST be a solution.
Thanks again for your tireless efforts, it seems as though there was some sort of breakthrough, though I don't understand it.

If the **acpi_osi="Windows 2006"** worked, then add it to **/etc/default/grub** at the end of the GRUB_CMDLINE_LINUX_DEFAULT line so that it looks something like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Windows 2006\""
```
...(note the addition of the backspace escape characters,) then run:
```
sudo update-grub
```
...to make it permanent.

*Note, you may need to use:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Windows 2006\\\""
```
...to properly escape the parameter. See: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445952]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445952").

Running:
```
cat /proc/cmdline
```
...after you boot will tell us how it was processed.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
Well... it didn't boot with that param... I will try it with the "/" appended... to see if that works.  And I'll log back in.
After I ran that, and booted w/o acpi=off it ran fine.... ONCE
but.  I will give that a try to see if it works.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
Ok, I tried

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Windows 2006\\\""
```

and it worked.  It booted quite nicely, and I am very thankful for your efforts.  I will keep this open, for a while, to make sure it boots again, and will shutdown properly and all that.
I guess the additional /'s helped it to work right.
Thank you ever so much Toz!!!
You have been quite a blessing to me by helping me finally get this to work (well, I hope it is final)

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
Oh... here is the
```

cat /proc/cmdline

```

```

BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b61c59af-7f66-4df5-b2d5-928314a8ddd3 ro quiet splash acpi_osi=\"Windows 2006\" vt.handoff=7

```

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
AHHHHH!!!!!
Well, it hasn't worked a second (third, or fourth) time.
It was a 1 hit wonder.  So.... if it worked once, and not twice.... what is the issue?
Why would it work, but not EVERY time?

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
Ok, I tired the same thing with Windows 200(1/0) and both sorta worked for a bit...
I saw this link when searching
[http://en.gentoo-wiki.com/wiki/ACPI/Fix_common_problems](http://en.gentoo-wiki.com/wiki/ACPI/Fix_common_problems)
could it be a DSDT problem?  I don't know a whole lot....
what are the other options I saw something else about the 2001, like P1 or something....  This comp had XP on it when I got it....  whew,,,  thanks again for helping.

---

### Post by Toz on 2011-11-13
> **TREESofRIGHTEOUSNESS said:**
> Oh... here is the
```

cat /proc/cmdline

```

```

BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b61c59af-7f66-4df5-b2d5-928314a8ddd3 ro quiet splash acpi_osi=\"Windows 2006\" vt.handoff=7

```

This doesn't look right. Try instead:
```
...ro quiet splash acpi_osi=\"Windows 2006\"
```

---

### Post by Toz on 2011-11-13
> **TREESofRIGHTEOUSNESS said:**
> Ok, I tired the same thing with Windows 200(1/0) and both sorta worked for a bit...
I saw this link when searching
[http://en.gentoo-wiki.com/wiki/ACPI/Fix_common_problems](http://en.gentoo-wiki.com/wiki/ACPI/Fix_common_problems)
could it be a DSDT problem?  I don't know a whole lot....
what are the other options I saw something else about the 2001, like P1 or something....  This comp had XP on it when I got it....  whew,,,  thanks again for helping.

I'm convinced its some sort of bios problem. Too bad you can't upgrade the bios. The gentoo article is good, but those commands won't work on ubuntu. If you want to try to debug the dsdt code, have a look at these links:
- [http://ubuntuforums.org/showthread.php?t=1036051]("http://ubuntuforums.org/showthread.php?t=1036051")
- [https://wiki.ubuntu.com/BIOSandUbuntu]("https://wiki.ubuntu.com/BIOSandUbuntu").

Unfortunately, I've never debugged DSDT code, so I might not be able to provide much assistance.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
Hmm...  it might be a BIOS problem, I definitely have never done anything like debugging DSDT...
I also noticed most people that were reporting good installed versions had installed the 64 bit OS.
Whew.  Well... I will try the Windows line again....  I will also try it w/ 2000 and 2001, to see if anyof those work either.  If nothing else, I will ask around to see if anyone has a windows disk I can install to update... it is just a pain, I will have to back it all up, and reinstall everything.  It would sure be nice if they would make linux BIOS flashing tools...  oh well.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-13
[https://wiki.ubuntu.com/BIOSandUbuntu](https://wiki.ubuntu.com/BIOSandUbuntu)
suggests getting ```
fwts
```
I will try that and check the log... if I am stumped I will post it and hope you can help me figure it out...  Thanks again... hopefully, though changing the amount of "\" will work.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-14
```
00388 dmi_decode      FAILED [MEDIUM] DMIOutOfSpec: Test 1, DMI type System Boot: Out of spec check.
00389 dmi_decode      DMI table dump:
00390 dmi_decode      # dmidecode 2.9
```
came up using fwts... and also some errors with DSDT....
So, anyhow.... I tried using "Windows SP2"  and it worked (this time)
Oh... why do you want me to take the vt.handoff line out?  I didn't add that line in.  I copied your line of code, and for some reason it inserts that in there.

---

### Post by Toz on 2011-11-14
Here is a description of what vt.handoff does: [http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg]("http://askubuntu.com/questions/32999/what-is-vt-handoff-7-parameter-in-grub-cfg").

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-14
well... I am trying something totally different now.  I wiped out my install, and installed the 64 bit version (since this is AMD)  I have run it successfully with the acpi_osi=\"Windows 2006\" option.  This may be the final post before I mark it solved.... we shall see....

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-14
so far this has worked flawlessly.
I guess the AMD needed the 64 bit (w/ Win 2006 option).
It may be that the BIOS is bad, but there seems to always be a workaround in Linux.
Thanks for spurring me onward Toz.  If it keeps working I will mark it as solved.

---

### Post by northd_tech on 2011-11-15
> **TREESofRIGHTEOUSNESS said:**
> I checked my BIOS... and there were no options like that.... I have read that trying to update the BIOS in Linux is a last ditch effort.  I don't really want to load windows on here just to update BIOS....
I have considered doing it before.... but I never have.
If so... do you know a good way to do it... I am sure wine is a bad deal, since it is kinda buggy  with some windows programs, I don't want to half flash my BIOS and end up with a brick....
I'd rather just use acpi=off.... 

Have you looked for a DOS-based Flash utility from your motherboard manufacturer (some still issue them, and I've seen recommendations to ALWAYS flash BIOS (and other EEPROM's) from a DOS or "DOS-like" OS from several manufacturers.) I've also seen where one manufacturer only has Windows-based flash utilities for their AWARD BIOS (just an arbitrary example) where another motherboard/computer manufacturer will release both DOS- and Windows-based flash utilities for their AWARD BIOS.  In this case, they nearly ALWAYS recommend flashing from DOS (although I have used the first company's BIOS image file with the 2nd company's DOS-based utility).  I would be ABSOLUTELY CERTAIN the programs are for the same BRAND of BIOS (but flash utility version number often makes little to no difference).

I think that might be what I did on my HP laptop a couple of months ago (with a #@*^ "HP-ized"/hidden Phoenix BIOS) to get AMD-V hypertransport virtualization running for VMware and VirtualBox.

A couple of possibilities- if you can locate a DOS-based flash utility (and a newer BIOS image file that is correct for your mainboard), consider the freeware, non-Micro$oft FreeDOS .ISO:

[http://www.freedos.org/freedos/files/](http://www.freedos.org/freedos/files/)

There are also many places where one can download various DOS &  Win95 & 98 "boot floppy" images that could be converted to a boot CD  with the proper CD writing software.

I would be sure to play with your new "DOS" for several hours to **test its relaibility and function** BEFORE any ROM flashing though- there's a TON of free DOS programs, games, and "abandonware" on the web if you search a litte.

Option #2:  Have you looked into the Linux package **flashrom**?  (I had to use something a little similar- **fxload**- to try to get an external CDRW spinning again under Ubuntu to read some old archived data).

[http://packages.ubuntu.com/natty/flashrom](http://packages.ubuntu.com/natty/flashrom)

I haven't used "flashrom" under Ubuntu personally YET, but I have used DOS to flash many BIOS'es and various cards with "flash" ROMs.  I've used Win Vista a few times too (but it ALWAYS makes me QUITE nervous to do so).  

I also like an EXTREMELY FULL battery with "live" AC power throughout the process for laptops and/or a battery-backed UPS for desktop PC's AND laptops.  I've even heard of using a diesel- or gasoline-powered generator or [relatively large like my 800 Watt] car DC-to-AC inverter to power the computer with a RELIABLE, idling automobile and a full-ish tank of fuel.

Also on your working ACPI 'workaround-' have you tried these commands to see if you really are getting "Awake" signals from the ACPI system?  (It might take several hours/days to see several Suspend/Awake cycles though).  I've got a UF thread filed somewhere in my notes that listed the terminal commands to force suspend and hibernate for testing reasons- I'll try to find them for you.

```

cat /var/log/pm-suspend.log | grep Nov
tail -n 100 /var/log/pm-suspend.log
dmesg | egrep 'wake|acpi|uspend|bernat|ower|esume|ailed'

cat /var/log/pm-suspend.log  | grep wake

```

I recently upgraded my NVIDIA drivers to the new(est?) 285.05.09 drivers and my intermittent Suspend problems seem to have disappeared a couple of days ago.

This makes me think you might have something in common with my NVIDIA graphics 64bit AMD laptop:

> 00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices **[AMD] K8 [Athlon64/Opteron] HyperTransport Technology** Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: **nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)**


My recent NVIDIA-ACPI-Suspend discoveries are chronicled here:

[http://ubuntuforums.org/showpost.php?p=11460223&postcount=21](http://ubuntuforums.org/showpost.php?p=11460223&postcount=21)

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-16
@[northd_tech]("http://ubuntuforums.org/member.php?u=938429")

For BIOS flashing it lists
Microsoft Windows XP 32-bit Home Edition with Service Pack 2 (SP2)
Microsoft Windows XP 32-bit Professional with SP2 
on the website
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-31250-1&cc=us&dlc=en&lc=en&os=228&product=442915&sw_lang=](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-31250-1&cc=us&dlc=en&lc=en&os=228&product=442915&sw_lang=)

I am not too sure I want to flash my BIOS w/o running XP SP2....  my BIOS is way outdated I'm sure Toz is right that I need to flash my BIOS mine is
```

 Vendor: Hewlett-Packard 
     Version: F.11 
    Release Date: 04/30/2004

```and the current one is version F.35....  So I am adequately sure my BIOS is out of date.


I don't have a battery and therefore don't need to suspend, but if I did I am sure your link would be very appreciated.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-16
I've checked out flashrom before, and they state on their page [http://www.flashrom.org/Laptops](http://www.flashrom.org/Laptops)
that they recommend using the vendor utility.... so...
I may have to locate someone's XP disk.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-29
Well...I installed Hardy Heron, and it works SOOOOOO much better.  I don't need to add anything to the boot line.  works out of box!!!
So it MUST be something in the kernel that changed.  I tried Feisty, and it worked also...  (but a little to old for my tastes

---

### Post by TREESofRIGHTEOUSNESS on 2013-03-21
Ok the long overdue update.
It was mostdefinetly something in the Kernel.  A bisection was done, and after lots of effort, I decided to try the 64 bit version (simply because I was tired of the hassle).
Now it works perfectly.  So the SOLUTION is AMD64 version of 12.04.  12.10 has some bugs.... and 13.04 requries another workaround (nomodeset) but it is not even out yet....
So.... AMD version of 12.04 is the solution that will outlive this old computer!!

---

