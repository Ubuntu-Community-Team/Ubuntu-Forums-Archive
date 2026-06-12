---
title: "Overheating problems with CPU"
date: 2018-07-08
forum: Hardware
---

### Post by LastGunslinger on 2018-07-08
Ive done a fair bit of a research and come up short unfortunately, Synopsis: My laptop HDD went poof a few weeks ago, thankfully i had an SSD installed, but its too small to run windows stably without a new drive. So i had to turn back to Kubuntu for the moment, and the problem i've been having lately is overheating issues with my processor, its got an auto turbo boost in it, and linux wants to run it at max clock speed all the time, normally this wouldnt be an issue, because buy a laptop cooler right? Clean the vents right? Let me explain further, my financial situation is tight, im NOT ABLE to buy any new hardware or components, or a new laptop, or even cheap materials to rig up an AC cooler for my existing crappy cooler to begin with. My thermal paste is good, checked it yesterday, fan speed is at maximum already, yes im also aware of trying to adjust clock speed from BIOS but it flatly refuses to let me to let me modify the clock speed in BIOS, probably due to the turbo boost.
So, i dont want to overclock, i want to underclock my processor to run at a consistent 1.8 Ghz as apposed to the constant (and mildly frustrating) 2.4. But i've been unable to find any software native to linux, any suggestions on how to PERMANENTLY lower clock speed? Yes yes, im aware that modifying these sorts of things can be dangerous if done incorrectly, lets skip all the warnings and 'beyond this point be dragons' speeches. My processor is running at a constant temp of 65 to 70 Celsius, which can be dangerous on its own over time. 
Thank you in Advance

---

### Post by pqwoerituytrueiwoq on 2018-07-08
Try the power save governor
```
echo powersave | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```
this will give you a list of options for the above
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```
there may be a option in your bios to disable turbo

---

### Post by LastGunslinger on 2018-07-08
When i tried to boot BIOS this time, all it showed me was a gray clipped screen, so yay for that. Looks like BIOS is out of the picture entirely now
So far as powersave goes, it doesnt help either. Clock speed is still a constant 2.4

---

### Post by Yellow Pasque on 2018-07-09
What kind of laptop and CPU are we talking about here?

>  My processor is running at a constant temp of 65 to 70 Celsius

This is probably not dangerous for a laptop. Laptop CPU's are made to run at much higher temps than desktop counterparts.

---

### Post by Doug S on 2018-07-09
> **Temüjin said:**
> What kind of laptop and CPU are we talking about here?+1, we need to know this. In addition to what pqwoerituytrueiwoq asked for, we also need to know the CPU frequency scaling driver, so both and for example:

```
doug@s15:~/temp$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
doug@s15:~/temp$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave

```

---

### Post by LastGunslinger on 2018-07-10
Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
I was actually not aware of this fact actually, i've only ever had desktops until now, whats the normal meltdown or beyond this point be dragons temp for most laptop CPUs?

---

### Post by LastGunslinger on 2018-07-10
```
wulf@CITADEL:~$ lscpu
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              4
On-line CPU(s) list: 0-3
Thread(s) per core:  2
Core(s) per socket:  2
Socket(s):           1
NUMA node(s):        1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               58
Model name:          Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
Stepping:            9
CPU MHz:             1424.413
CPU max MHz:         2600.0000
CPU min MHz:         800.0000
BogoMIPS:            3392.58
Virtualization:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            3072K
NUMA node0 CPU(s):   0-3
Flags:                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36  clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm  constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc  cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3  cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes  xsave avx f16c rdrand lahf_lm cpuid_fault epb pti ibrs ibpb stibp  tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm  ida arat pln pts
```
```
wulf@CITADEL:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_pstate
intel_pstate
intel_pstate
intel_pstate
wulf@CITADEL:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
powersave
powersave
powersave
powersave
wulf@CITADEL:~$ 
```
Are the outputs of both
Not entirely sure how to get the output of each result, im not the most knowledgeable in the inner workings of Kubuntu, sorry about that :(

---

### Post by Doug S on 2018-07-10
> **LastGunslinger said:**
> Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
I was actually not aware of this fact actually, i've only ever had desktops until now, whats the normal meltdown or beyond this point be dragons temp for most laptop CPUs?105 degrees C for your particular processor. You can use turbostat (in the linux-tools-common package) to obtain more details.

You can disable turbo with this command:
```
echo "1" | sudo tee /sys/devices/system/cpu/intel_pstate/no_turbo
```

You can further (or instead) reduce the maximum clock rate with, for example, this command:

```
echo 70 | sudo tee /sys/devices/system/cpu/intel_pstate/max_perf_pct
```

---

### Post by Yellow Pasque on 2018-07-10
```
CPU MHz: 1424.413
```
That seems to indicate the CPU was running at 1.4GHz when you ran the command.

> whats the normal meltdown or beyond this point be dragons temp for most laptop CPUs? 
It varies. Tjunction is listed as 105C for your CPU: [https://ark.intel.com/products/65707/Intel-Core-i5-3317U-Processor-3M-Cache-up-to-2_60-GHz](https://ark.intel.com/products/65707/Intel-Core-i5-3317U-Processor-3M-Cache-up-to-2_60-GHz)
I wouldn't be comfortable going above 90C for extended periods of time though. If you were overheating, your laptop would throttle the CPU or shut down completely to prevent damage.

---

### Post by LastGunslinger on 2018-07-11
Very useful to know. Turbo has been disabled, thank you for your help, all of you, and please pardon my dense nature and ignorance with this subject. I will mark this thread as SOLVED

---

### Post by Yellow Pasque on 2018-07-11
It seems like a band-aid solution to me. Did this make a difference in temps and/or quiet the fan? Even if it did, you're still sacrificing performance. There's no reason you shouldn't be able to use turbo unless it's a really poorly designed chassis.
I wonder if a BIOS update would help (you never told us what model laptop you have). dmidecode might be helpful:
```
sudo dmidecode
```
(Use code tags because it's a lot of text)

You also said your CPU was running constant 2.4GHz, but the output you gave showed 1.4GHz. It doesn't make sense.

---

### Post by LastGunslinger on 2018-07-13
I appreciate the response, truly, but i dont really need the turbo. This thing is a potato, and the guy i got it from is a retard and didnt properly care for it. Since ive had it, ive had to dissemble and jury rig several components, the wifi adapter is throwing fault codes as are many other pieces of hardware. The design for this laptop is sound so far as i can tell, and disabling turbo has made a difference. Its now not climbing above 50 Celsius as a result, which is within my personal comfort zone. But to satisfy your curiosity, its an HP Envy touchpad sleekbook.

```

wulf@CITADEL:~$ sudo dmidecode
[sudo] password for wulf: 
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.
48 structures occupying 2207 bytes.
Table at 0x000E70B0.

Handle 0x0000, DMI type 16, 23 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 16 GB
        Error Information Handle: 0x0009
        Number Of Devices: 2

Handle 0x0001, DMI type 17, 34 bytes
Memory Device
        Array Handle: 0x0000
        Error Information Handle: 0x0003
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: SODIMM
        Set: None
        Locator: Bottom-Slot 1(left)
        Bank Locator: BANK 0
        Type: DDR3
        Type Detail: Synchronous
        Speed: 1333 MT/s
        Manufacturer: Unknown
        Serial Number: 00000000
        Asset Tag: Unknown
        Part Number:                   
        Rank: 2
        Configured Clock Speed: 1333 MT/s

Handle 0x0004, DMI type 20, 35 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000FFFFFFFF
        Range Size: 4 GB
        Physical Device Handle: 0x0001
        Memory Array Mapped Address Handle: 0x000A
        Partition Row Position: 1
        Interleave Position: 1
        Interleaved Data Depth: 1

Handle 0x0005, DMI type 17, 34 bytes
Memory Device
        Array Handle: 0x0000
        Error Information Handle: 0x0007
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: SODIMM
        Set: None
        Locator: Bottom-Slot 2(right)
        Bank Locator: BANK 2
        Type: DDR3
        Type Detail: Synchronous
        Speed: 1333 MT/s
        Manufacturer: Unknown
        Serial Number: 00000000
        Asset Tag: Unknown
        Part Number:                   
        Rank: 2
        Configured Clock Speed: 1333 MT/s

Handle 0x0008, DMI type 20, 35 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000FFFFFFFF
        Range Size: 4 GB
        Physical Device Handle: 0x0005
        Memory Array Mapped Address Handle: 0x000A
        Partition Row Position: 1
        Interleave Position: 2
        Interleaved Data Depth: 1

Handle 0x000A, DMI type 19, 31 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x001FFFFFFFF
        Range Size: 8 GB
        Physical Array Handle: 0x0000
        Partition Width: 2

Handle 0x000C, DMI type 0, 24 bytes
BIOS Information
        Vendor: Insyde
        Version: F.25
        Release Date: 05/16/2014
        Address: 0xE0000
        Runtime Size: 128 kB
        ROM Size: 4608 kB
        Characteristics:
                PCI is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
                Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
                5.25"/360 kB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 kB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
                UEFI is supported
        BIOS Revision: 15.37
        Firmware Revision: 72.66

Handle 0x000D, DMI type 1, 27 bytes
System Information
        Manufacturer: Hewlett-Packard
        Product Name: HP ENVY TouchSmart Sleekbook 4
        Version: 0888110022305900000320130
        Serial Number: CND24307L2
        UUID: 2A611389-D5FE-E111-83C6-84349715FA16
        Wake-up Type: Power Switch
        SKU Number: C2K73UA#ABA
        Family: 103C_5335KV G=N L=CON B=HP S=ENV

Handle 0x000E, DMI type 2, 16 bytes
Base Board Information
        Manufacturer: Hewlett-Packard
        Product Name: 1894
        Version: 72.66
        Serial Number: PDENND21V3HC0I
        Asset Tag: Type2 - Board Asset Tag
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Type2 - Board Chassis Location
        Chassis Handle: 0x000F
        Type: Motherboard
        Contained Object Handles: 0

Handle 0x000F, DMI type 3, 23 bytes
Chassis Information
        Manufacturer: Hewlett-Packard
        Type: Notebook
        Lock: Not Present
        Version: Chassis Version
        Serial Number: Chassis Serial Number
        Asset Tag: Chassis Asset Tag
        Boot-up State: Safe
        Power Supply State: Safe
        Thermal State: Safe
        Security Status: None
        OEM Information: 0x00000059
        Height: Unspecified
        Number Of Power Cords: 1
        Contained Elements: 0
        SKU Number: Not Specified

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J1A1
        Internal Connector Type: None
        External Reference Designator: Keyboard
        External Connector Type: PS/2
        Port Type: Keyboard Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J1A1
        Internal Connector Type: None
        External Reference Designator: Mouse
        External Connector Type: PS/2
        Port Type: Mouse Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J2A2
        Internal Connector Type: None
        External Reference Designator: COM 1
        External Connector Type: DB-9 male
        Port Type: Serial Port 16550A Compatible

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J3A1
        Internal Connector Type: None
        External Reference Designator: USB
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J3A1
        Internal Connector Type: None
        External Reference Designator: USB
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J3A1
        Internal Connector Type: None
        External Reference Designator: USB
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J5A1
        Internal Connector Type: None
        External Reference Designator: USB
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J5A1
        Internal Connector Type: None
        External Reference Designator: USB
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J5A1
        Internal Connector Type: None
        External Reference Designator: Network
        External Connector Type: RJ-45
        Port Type: Network Port

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J9G2
        Internal Connector Type: On Board Floppy
        External Reference Designator: OnBoard Floppy Type
        External Connector Type: None
        Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J7J1
        Internal Connector Type: On Board IDE
        External Reference Designator: OnBoard Primary IDE
        External Connector Type: None
        Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J2A1
        Internal Connector Type: None
        External Reference Designator: TV OUT
        External Connector Type: Mini DIN
        Port Type: Video Port

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J2A2
        Internal Connector Type: None
        External Reference Designator: CRT
        External Connector Type: DB-15 female
        Port Type: Video Port

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J30
        Internal Connector Type: None
        External Reference Designator: Microphone In
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J30
        Internal Connector Type: None
        External Reference Designator: Line In
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: J30
        Internal Connector Type: None
        External Reference Designator: Speaker Out
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port

Handle 0x0020, DMI type 9, 17 bytes
System Slot Information
        Designation: J5C1
        Type: x16 PCI Express x16
        Current Usage: Available
        Length: Other
        ID: 1
        Characteristics:
                PME signal is supported
                Hot-plug devices are supported
        Bus Address: 0000:00:01.0

Handle 0x0021, DMI type 9, 17 bytes
System Slot Information
        Designation: J6C1
        Type: x4 PCI Express x4
        Current Usage: Available
        Length: Other
        ID: 2
        Characteristics:
                PME signal is supported
                Hot-plug devices are supported
        Bus Address: 0000:00:1c.0

Handle 0x0022, DMI type 9, 17 bytes
System Slot Information
        Designation: J6C2
        Type: x1 PCI Express x1
        Current Usage: Available
        Length: Other
        ID: 3
        Characteristics:
                PME signal is supported
                Hot-plug devices are supported
        Bus Address: 0000:00:1c.1

Handle 0x0023, DMI type 9, 17 bytes
System Slot Information
        Designation: J6D2
        Type: x1 PCI Express x1
        Current Usage: Available
        Length: Other
        ID: 4
        Characteristics:
                PME signal is supported
                Hot-plug devices are supported
        Bus Address: 0000:00:1c.2

Handle 0x0024, DMI type 9, 17 bytes
System Slot Information
        Designation: J7C1
        Type: x1 PCI Express x1
        Current Usage: Available
        Length: Other
        ID: 5
        Characteristics:
                PME signal is supported
                Hot-plug devices are supported
        Bus Address: 0000:00:1c.3

Handle 0x0025, DMI type 9, 17 bytes
System Slot Information
        Designation: J7D2
        Type: x1 PCI Express x1
        Current Usage: Available
        Length: Other
        ID: 6
        Characteristics:
                PME signal is supported
                Hot-plug devices are supported
        Bus Address: 0000:00:1c.4

Handle 0x0026, DMI type 9, 17 bytes
System Slot Information
        Designation: J8C1
        Type: x1 PCI Express x1
        Current Usage: Available
        Length: Other
        ID: 7
        Characteristics:
                PME signal is supported
                Hot-plug devices are supported
        Bus Address: 0000:00:1c.5

Handle 0x0027, DMI type 9, 17 bytes
System Slot Information
        Designation: J8C2
        Type: x16 PCI Express x16
        Current Usage: Available
        Length: Other
        ID: 8
        Characteristics:
                PME signal is supported
                Hot-plug devices are supported
        Bus Address: 0000:00:1c.7

Handle 0x0028, DMI type 11, 5 bytes
OEM Strings
        String 1: $HP$
        String 2: LOC#   
        String 3: ABS 70/71 78 79 7A 7B
        String 4: CNB1 0888110022305900000320130
        String 5: HP_Mute_LED_P_G
        String 6: String6 for Original Equipment Manufacturer
        String 7: String7 for Original Equipment Manufacturer
        String 8: String8 for Original Equipment Manufacturer

Handle 0x002A, DMI type 13, 22 bytes
BIOS Language Information
        Language Description Format: Long
        Installable Languages: 4
                en|US|iso8859-1
                fr|CA|iso8859-1
                es|ES|iso8859-1
                zh|TW|unicode
        Currently Installed Language: en|US|iso8859-1

Handle 0x002D, DMI type 22, 26 bytes
Portable Battery
        Location: Primary
        Manufacturer: 23-1C
        Name: EL04052
        Chemistry: Lithium Ion
        Design Capacity: 52540 mWh
        Design Voltage: 14800 mV
        SBDS Version: 1
        Maximum Error: 1%
        SBDS Serial Number: 084E
        SBDS Manufacture Date: 2012-09-22
        OEM-specific Information: 0x0000FFFF

Handle 0x002E, DMI type 24, 5 bytes
Hardware Security
        Power-On Password Status: Disabled
        Keyboard Password Status: Disabled
        Administrator Password Status: Disabled
        Front Panel Reset Status: Disabled

Handle 0x0031, DMI type 32, 20 bytes
System Boot Information
        Status: No errors detected

Handle 0x0034, DMI type 41, 11 bytes
Onboard Device
        Reference Designation: Realtek PCIe GBE Family Controller
        Type: Ethernet
        Status: Enabled
        Type Instance: 1
        Bus Address: 0000:01:00.2

Handle 0x0039, DMI type 131, 64 bytes
OEM-specific Type
        Header and Data:
                83 40 39 00 11 00 00 00 00 00 00 00 00 00 00 00
                F8 00 57 1E FF FF FF FF 01 20 00 00 01 00 08 00
                E0 04 00 00 00 00 00 00 C8 00 FF FF 00 00 00 00
                00 FF 00 00 66 00 00 00 76 50 72 6F 00 00 00 00

Handle 0x003A, DMI type 41, 11 bytes
Onboard Device
        Reference Designation: Atheros WLAN Atheros AR9565 Mango 802.11bgn 1x1 WiFi + BT4.0 co
        Type: Other
        Status: Enabled
        Type Instance: 1
        Bus Address: 0000:02:00.0

Handle 0x003B, DMI type 4, 42 bytes
Processor Information
        Socket Designation: U3E1
        Type: Central Processor
        Family: Core i5
        Manufacturer: Intel(R) Corporation
        ID: A9 06 03 00 FF FB EB BF
        Signature: Type 0, Family 6, Model 58, Stepping 9
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
        Version: Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz
        Voltage: 0.8 V
        External Clock: 100 MHz
        Max Speed: 1700 MHz
        Current Speed: 1700 MHz
        Status: Populated, Enabled
        Upgrade: Socket rPGA988B
        L1 Cache Handle: 0x003D
        L2 Cache Handle: 0x003E
        L3 Cache Handle: 0x003F
        Serial Number: To Be Filled By O.E.M.
        Asset Tag: To Be Filled By O.E.M.
        Part Number: To Be Filled By O.E.M.
        Core Count: 2
        Core Enabled: 2
        Thread Count: 4
        Characteristics:
                64-bit capable
                Multi-Core
                Hardware Thread
                Execute Protection
                Enhanced Virtualization
                Power/Performance Control

Handle 0x003C, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 32 kB
        Maximum Size: 32 kB
        Supported SRAM Types:
                Unknown
        Installed SRAM Type: Unknown
        Speed: Unknown
        Error Correction Type: Parity
        System Type: Data
        Associativity: 8-way Set-associative

Handle 0x003D, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1 Cache
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 32 kB
        Maximum Size: 32 kB
        Supported SRAM Types:
                Unknown
        Installed SRAM Type: Unknown
        Speed: Unknown
        Error Correction Type: Parity
        System Type: Instruction
        Associativity: 8-way Set-associative

Handle 0x003E, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L2 Cache
        Configuration: Enabled, Not Socketed, Level 2
        Operational Mode: Write Through
        Location: Internal
        Installed Size: 256 kB
        Maximum Size: 256 kB
        Supported SRAM Types:
                Unknown
        Installed SRAM Type: Unknown
        Speed: Unknown
        Error Correction Type: Multi-bit ECC
        System Type: Unified
        Associativity: 8-way Set-associative

Handle 0x003F, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L3 Cache
        Configuration: Enabled, Not Socketed, Level 3
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 3072 kB
        Maximum Size: 3072 kB
        Supported SRAM Types:
                Unknown
        Installed SRAM Type: Unknown
        Speed: Unknown
        Error Correction Type: Multi-bit ECC
        System Type: Unified
        Associativity: 12-way Set-associative

Handle 0x0040, DMI type 127, 4 bytes
End Of Table

wulf@CITADEL:~$ 

```


This is the output of the command you requested.

Its actually a rather good computer, just old and worn out. If this had been originally mine it would be in far better shape mechanically than it is, but as we all know here in the PC world, people neglect their electronics far more than they should. Im going to be getting my CDL here soon and im going to use this useless **** as a Frisbee and then target practice after custom ordering a brand new one. My overheat problems have officially come to a conclusion, i have to baby this thing at all cost for the moment as its my only connection to the outside world at the moment, even if that means sacrificing performance.

---

### Post by Yellow Pasque on 2018-07-13
Thanks for the output. You are running the latest BIOS (F.25). I couldn't find any similar complaints about this particular model running at full speed under Linux.

> Its now not climbing above 50 Celsius as a result, which is within my personal comfort zone.

That's good to hear. If you're happy, then I'm happy. Hopefully, the fan is quieter too.

---

### Post by LastGunslinger on 2018-07-14
Im deaf as a post and am usually wearing headphones anyway, so the fan sound doesn't bother me much anyways xD

---

