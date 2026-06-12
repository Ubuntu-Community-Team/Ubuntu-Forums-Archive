---
title: "pm-suspend bug on resume"
date: 2014-07-24
forum: Hardware
---

### Post by jeremy-munsch on 2014-07-24
Hi,

I just have a problem with pm-suspend on ubuntu14.04.

I'am using a lubuntu base, and i installed kde desktop on it wich is working nicely.
Im a using this laptop MSI GT70. Everithing works ok.

After resume on suspend i can see it works for 500 ms then seems xorg crashes, there are alors lot of threads on this i did research.

I tryed to create /etc/acpi/events/lid and did chmod +x on it

```
event=button/lid LID close
action=/usr/sbin/pm-suspend --quirk-save-pci
```


I tryed sudo dmidecode -t system

to manage to modify  /usr/lib/pm-utils/video-quirks/20-video-quirk-pm-misc.quirkdb 

/var/cache/pm-utils/last_known_working.quirkdb

[B]
So What works :[/B]
So what i did is to test quirks like : pm-suspend --quirk-save-pci which works
the other thing that works is create /etc/pm/sleep.d/fix-black-screen and chmod +x
```
#!/bin/bash

case $1 in
suspend)
    # Suspending to RAM.
    chvt 1
    sleep 1
;;
resume)
    # Resume from suspend.
    sleep 1
    chvt 7
;;
esac
```

**I'm trying actually to make pm-suspend --quirk-save-pci defautl behavious on lid close, and sleep generally. But i can't find out where to add default quirk for my laptop.**

my dmidecode
```
# dmidecode 2.12
SMBIOS 2.7 present.
78 structures occupying 2928 bytes.
Table at 0x000EC1A0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: E1763IMS.50T
    Release Date: 02/12/2014
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 3072 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Micro-Star International Co., Ltd.
    Product Name: GT70 2PC
    Version: REV:0.C
    Serial Number: FFFFFFFF
    UUID: 00000000-0000-0000-0000-448A5B409709
    Wake-up Type: Power Switch
    SKU Number: To be filled by O.E.M.
    Family: To be filled by O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: Micro-Star International Co., Ltd.
    Product Name: MS-1763
    Version: REV:0.C
    Serial Number: BSS-0123456789
    Asset Tag: To be filled by O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To be filled by O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
    Manufacturer: Micro-Star International
    Type: Notebook
    Lock: Not Present
    Version: N/A
    Serial Number: None
    Asset Tag: No Asset Tag
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0
    SKU Number: To be filled by O.E.M.

Handle 0x0004, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: PS2Mouse
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0005, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0006, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A1
    Internal Connector Type: None
    External Reference Designator: TV Out
    External Connector Type: Mini Centronics Type-14
    Port Type: Other

Handle 0x0007, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2A
    Internal Connector Type: None
    External Reference Designator: COM A
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2B
    Internal Connector Type: None
    External Reference Designator: Video
    External Connector Type: DB-15 female
    Port Type: Video Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3A1
    Internal Connector Type: None
    External Reference Designator: USB3
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9A1 - TPM HDR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9C1 - PCIE DOCKING CONN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2B3 - CPU FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6C2 - EXT HDMI
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J3C1 - GMCH FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1D1 - ITP
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E2 - MDC INTPSR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E4 - MDC INTPSR
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E3 - LPC HOT DOCKING
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9E1 - SCAN MATRIX
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9G1 - LPC SIDE BAND
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J8F1 - UNIFIED
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6F1 - LVDS
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2F1 - LAI FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2G1 - GFX VID
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1G6 - AC JACK
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001C, DMI type 9, 17 bytes
System Slot Information
    Designation: J6B2
    Type: x16 PCI Express
    Current Usage: In Use
    Length: Long
    ID: 0
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:01.0

Handle 0x001D, DMI type 9, 17 bytes
System Slot Information
    Designation: J6B1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.3

Handle 0x001E, DMI type 9, 17 bytes
System Slot Information
    Designation: J6D1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.4

Handle 0x001F, DMI type 9, 17 bytes
System Slot Information
    Designation: J7B1
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.5

Handle 0x0020, DMI type 9, 17 bytes
System Slot Information
    Designation: J8B4
    Type: x1 PCI Express
    Current Usage: In Use
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported
    Bus Address: 0000:00:1c.6

Handle 0x0021, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:    To Be Filled By O.E.M.

Handle 0x0022, DMI type 11, 5 bytes
OEM Strings
    String 1: To Be Filled By O.E.M.

Handle 0x0023, DMI type 12, 5 bytes
System Configuration Options
    Option 1: To Be Filled By O.E.M.

Handle 0x0024, DMI type 24, 5 bytes
Hardware Security
    Power-On Password Status: Disabled
    Keyboard Password Status: Disabled
    Administrator Password Status: Disabled
    Front Panel Reset Status: Disabled

Handle 0x0025, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x0026, DMI type 34, 11 bytes
Management Device
    Description: LM78-1
    Type: LM78
    Address: 0x00000000
    Address Type: I/O Port

Handle 0x0027, DMI type 26, 22 bytes
Voltage Probe
    Description: LM78A
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0028, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0029, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0026
    Component Handle: 0x0026
    Threshold Handle: 0x0027

Handle 0x002A, DMI type 28, 22 bytes
Temperature Probe
    Description: LM78A
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x002B, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x002C, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0026
    Component Handle: 0x0029
    Threshold Handle: 0x002A

Handle 0x002D, DMI type 27, 15 bytes
Cooling Device
    Temperature Probe Handle: 0x002A
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating
    Description: Cooling Dev 1

Handle 0x002E, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x002F, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0026
    Component Handle: 0x002C
    Threshold Handle: 0x002D

Handle 0x0030, DMI type 27, 15 bytes
Cooling Device
    Temperature Probe Handle: 0x002A
    Type: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating
    Description: Not Specified

Handle 0x0031, DMI type 36, 16 bytes
Management Device Threshold Data
    Lower Non-critical Threshold: 1
    Upper Non-critical Threshold: 2
    Lower Critical Threshold: 3
    Upper Critical Threshold: 4
    Lower Non-recoverable Threshold: 5
    Upper Non-recoverable Threshold: 6

Handle 0x0032, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0026
    Component Handle: 0x002F
    Threshold Handle: 0x0030

Handle 0x0033, DMI type 29, 22 bytes
Electrical Current Probe
    Description: ABC
    Location: <OUT OF SPEC>
    Status: <OUT OF SPEC>
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0034, DMI type 36, 16 bytes
Management Device Threshold Data

Handle 0x0035, DMI type 35, 11 bytes
Management Device Component
    Description: To Be Filled By O.E.M.
    Management Device Handle: 0x0026
    Component Handle: 0x0032
    Threshold Handle: 0x0030

Handle 0x0036, DMI type 26, 22 bytes
Voltage Probe
    Description: LM78A
    Location: Power Unit
    Status: OK
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0037, DMI type 28, 22 bytes
Temperature Probe
    Description: LM78A
    Location: Power Unit
    Status: OK
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x0038, DMI type 27, 15 bytes
Cooling Device
    Temperature Probe Handle: 0x0037
    Type: Power Supply Fan
    Status: OK
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating
    Description: Cooling Dev 1

Handle 0x0039, DMI type 29, 22 bytes
Electrical Current Probe
    Description: ABC
    Location: Power Unit
    Status: OK
    Maximum Value: Unknown
    Minimum Value: Unknown
    Resolution: Unknown
    Tolerance: Unknown
    Accuracy: Unknown
    OEM-specific Information: 0x00000000
    Nominal Value: Unknown

Handle 0x003A, DMI type 39, 22 bytes
System Power Supply
    Power Unit Group: 1
    Location: To Be Filled By O.E.M.
    Name: To Be Filled By O.E.M.
    Manufacturer: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Model Part Number: To Be Filled By O.E.M.
    Revision: To Be Filled By O.E.M.
    Max Power Capacity: Unknown
    Status: Present, OK
    Type: Switching
    Input Voltage Range Switching: Auto-switch
    Plugged: Yes
    Hot Replaceable: No
    Input Voltage Probe Handle: 0x0036
    Cooling Device Handle: 0x0038
    Input Current Probe Handle: 0x0039

Handle 0x003B, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard IGD
    Type: Video
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:02.0

Handle 0x003C, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard LAN
    Type: Ethernet
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:00:19.0

Handle 0x003D, DMI type 41, 11 bytes
Onboard Device
    Reference Designation:  Onboard 1394
    Type: Other
    Status: Enabled
    Type Instance: 1
    Bus Address: 0000:03:1c.2

Handle 0x003E, DMI type 7, 19 bytes
Cache Information
    Socket Designation: CPU Internal L1
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Other
    Associativity: 8-way Set-associative

Handle 0x003F, DMI type 4, 42 bytes
Processor Information
    Socket Designation: SOCKET 0
    Type: Central Processor
    Family: Core i7
    Manufacturer: Intel
    ID: C3 06 03 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 60, Stepping 3
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
    Version: Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
    Voltage: 1.2 V
    External Clock: 100 MHz
    Max Speed: 3800 MHz
    Current Speed: 2700 MHz
    Status: Populated, Enabled
    Upgrade: Socket rPGA988B
    L1 Cache Handle: 0x003E
    L2 Cache Handle: 0x0040
    L3 Cache Handle: 0x0041
    Serial Number: Not Specified
    Asset Tag: Fill By OEM
    Part Number: Fill By OEM
    Core Count: 4
    Core Enabled: 4
    Thread Count: 8
    Characteristics:
        64-bit capable

Handle 0x0040, DMI type 7, 19 bytes
Cache Information
    Socket Designation: CPU Internal L2
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 1024 kB
    Maximum Size: 1024 kB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0041, DMI type 7, 19 bytes
Cache Information
    Socket Designation: CPU Internal L3
    Configuration: Enabled, Not Socketed, Level 3
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 6144 kB
    Maximum Size: 6144 kB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 12-way Set-associative

Handle 0x0042, DMI type 16, 23 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x0043, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0042
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 9876543210
    Part Number: [Empty]
    Rank: Unknown
    Configured Clock Speed: Unknown

Handle 0x0044, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0042
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelA-DIMM1
    Bank Locator: BANK 1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1600 MHz
    Manufacturer: 1311
    Serial Number: 343B0E58
    Asset Tag: 9876543210
    Part Number: M2S8G64CC8HB5N-DI 
    Rank: 2
    Configured Clock Speed: 1600 MHz

Handle 0x0045, DMI type 20, 35 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 8 GB
    Physical Device Handle: 0x0044
    Memory Array Mapped Address Handle: 0x0049
    Partition Row Position: Unknown
    Interleave Position: Unknown
    Interleaved Data Depth: Unknown

Handle 0x0046, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0042
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: ChannelB-DIMM0
    Bank Locator: BANK 2
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 9876543210
    Part Number: [Empty]
    Rank: Unknown
    Configured Clock Speed: Unknown

Handle 0x0047, DMI type 17, 34 bytes
Memory Device
    Array Handle: 0x0042
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelB-DIMM1
    Bank Locator: BANK 3
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1600 MHz
    Manufacturer: 1311
    Serial Number: 163B0E56
    Asset Tag: 9876543210
    Part Number: M2S8G64CC8HB5N-DI 
    Rank: 2
    Configured Clock Speed: 1600 MHz

Handle 0x0048, DMI type 20, 35 bytes
Memory Device Mapped Address
    Starting Address: 0x00200000000
    Ending Address: 0x003FFFFFFFF
    Range Size: 8 GB
    Physical Device Handle: 0x0047
    Memory Array Mapped Address Handle: 0x0049
    Partition Row Position: Unknown
    Interleave Position: Unknown
    Interleaved Data Depth: Unknown

Handle 0x0049, DMI type 19, 31 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x003FFFFFFFF
    Range Size: 16 GB
    Physical Array Handle: 0x0042
    Partition Width: 4

Handle 0x004C, DMI type 136, 6 bytes
OEM-specific Type
    Header and Data:
        88 06 4C 00 00 00

Handle 0x004D, DMI type 131, 64 bytes
OEM-specific Type
    Header and Data:
        83 40 4D 00 35 00 00 00 00 00 00 00 00 00 00 00
        F8 00 4B 8C 00 00 00 00 01 20 00 00 00 00 09 00
        A7 05 14 00 00 00 00 00 C8 00 FF FF 00 00 00 00
        00 00 00 00 66 00 00 00 76 50 72 6F 00 00 00 00

Handle 0x004E, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Long
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x0050, DMI type 127, 4 bytes
End Of Table

```


So hope it may help some body. and thanks for helping me.

**EDIT** : switch on tty1 and doing sudo service lightdm restart make my session back.
I also tried to make /etc/acpi/events/lid
event=button/lid LID close
action=/etc/acpi/lid.sh

and /etc/acpi/lid.sh
#! /bin/bash
/usr/sbin/pm-suspend --quirk-save-pci

But it doesn't work.

**EDIT2**:

seems that it run with qurik save pci but still bug whereas pm-suspend --quirk-save-pci on console works

```
Initial commandline parameters: --quirk-save-pci
Fri Jul 25 02:09:13 CEST 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /etc/pm/sleep.d/00_check_touchpad_status suspend suspend:
/etc/pm/sleep.d/00_check_touchpad_status suspend suspend: not executable.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kwaadpepper-laptop 3.15.6-031506-generic #201407172034 SMP Fri Jul 18 00:36:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
alx                    41397  0 
mdio                   13561  1 alx
ctr                    13193  2 
ccm                    17856  2 
snd_hrtimer            12744  1 
bbswitch               13943  0 
snd_hda_codec_hdmi     48290  1 
snd_hda_codec_realtek    72575  1 
snd_hda_codec_generic    70087  1 snd_hda_codec_realtek
x86_pkg_temp_thermal    14312  0 
intel_powerclamp       19099  0 
kvm_intel             148919  0 
snd_hda_intel          30683  5 
snd_hda_controller     35518  1 snd_hda_intel
nvidia              10675219  39 
snd_hda_codec         144671  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
arc4                   12573  2 
snd_hwdep              13613  1 snd_hda_codec
uvcvideo               82299  0 
kvm                   463855  1 kvm_intel
ath9k                 147545  0 
videobuf2_vmalloc      13216  1 uvcvideo
snd_pcm               113863  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
videobuf2_memops       13362  1 videobuf2_vmalloc
ath9k_common           15984  1 ath9k
videobuf2_core         45435  1 uvcvideo
ath9k_hw              459576  2 ath9k_common,ath9k
videodev              149504  2 uvcvideo,videobuf2_core
ath3k                  13381  0 
rfcomm                 75078  12 
btusb                  32555  0 
crct10dif_pclmul       14268  0 
bnep                   19884  2 
crc32_pclmul           13180  0 
snd_seq_midi           13564  0 
ath                    29397  3 ath9k_common,ath9k,ath9k_hw
bluetooth             461911  23 bnep,ath3k,btusb,rfcomm
mac80211              663788  1 ath9k
ghash_clmulni_intel    13230  0 
snd_seq_midi_event     14899  1 snd_seq_midi
aesni_intel           152648  5 
snd_rawmidi            30865  1 snd_seq_midi
snd_seq                67636  3 snd_seq_midi_event,snd_seq_midi
6lowpan_iphc           18968  1 bluetooth
aes_x86_64             17131  1 aesni_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lrw                    13323  1 aesni_intel
gf128mul               14951  1 lrw
cfg80211              514187  4 ath,ath9k_common,ath9k,mac80211
snd_timer              30118  3 snd_hrtimer,snd_pcm,snd_seq
glue_helper            14095  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd                    74235  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
cryptd                 20531  3 ghash_clmulni_intel,aesni_intel,ablk_helper
soundcore              12680  2 snd,snd_hda_codec
rtsx_pci_ms            18337  0 
mei_me                 18562  0 
joydev                 17587  0 
mei                    87522  1 mei_me
memstick               16968  1 rtsx_pci_ms
serio_raw              13483  0 
lpc_ich                21176  0 
msi_wmi                13354  0 
sparse_keymap          13890  1 msi_wmi
mxm_wmi                13021  0 
wmi                    19379  2 msi_wmi,mxm_wmi
binfmt_misc            17508  1 
mac_hid                13275  0 
parport_pc             32906  0 
ppdev                  17711  0 
coretemp               13638  0 
lp                     17799  0 
parport                42481  3 lp,ppdev,parport_pc
hid_generic            12559  0 
hid_logitech_dj        18647  0 
usbhid                 53121  0 
hid                   106436  4 hid_generic,usbhid,hid_logitech_dj
rtsx_pci_sdmmc         23482  0 
i915                  877764  2 
i2c_algo_bit           13564  1 i915
drm_kms_helper         59729  1 i915
ahci                   30167  5 
psmouse               113095  0 
drm                   310655  6 i915,drm_kms_helper,nvidia
libahci                32191  1 ahci
rtsx_pci               46393  2 rtsx_pci_ms,rtsx_pci_sdmmc
video                  19932  1 i915
             total       used       free     shared    buffers     cached
Mem:      16351488    2908264   13443224      28872     133072    1044212
-/+ buffers/cache:    1730980   14620508
Swap:      3905532          0    3905532
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
Unloading alx kernel module ...
Done.
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Running hook /etc/pm/sleep.d/fix-black-screen suspend suspend:
/etc/pm/sleep.d/fix-black-screen suspend suspend: success.

Fri Jul 25 02:09:14 CEST 2014: performing suspend
Fri Jul 25 02:09:20 CEST 2014: Awake.
Fri Jul 25 02:09:20 CEST 2014: Running hooks for resume
Running hook /etc/pm/sleep.d/fix-black-screen resume suspend:
/etc/pm/sleep.d/fix-black-screen resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
Reloading alx kernel module ...
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /etc/pm/sleep.d/00_check_touchpad_status resume suspend:
/etc/pm/sleep.d/00_check_touchpad_status resume suspend: not executable.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.


```

---

### Post by Toz on 2014-07-24
> I'm trying actually to make pm-suspend --quirk-save-pci defautl behavious on lid close, and sleep generally. But i can't find out where to add default quirk for my laptop.
According to the [pm-suspend man file]("http://manpages.ubuntu.com/manpages/trusty/man8/pm-suspend.8.html"), the way to save the quirk for your system us to run, once:
```
sudo pm-suspend --quirk-save-pci  --store-quirks-as-lkw
```

Note that the man file also says that a kernel upgrade will overwrite the quirk file so you'll have to repeat this command after every upgrade.

---

### Post by jeremy-munsch on 2014-07-24
Thank you for your answer it seems that the quirk works but still it bugs. It works at leat form 500 ms, then crash and blackscreen.

```
Jul 25 02:32:21 localhost kernel: [ 1014.206831] atkbd serio0: Unknown key pressed (translated set 2, code 0x98 on isa0060/serio0).
Jul 25 02:32:21 localhost kernel: [ 1014.206834] atkbd serio0: Use 'setkeycodes e018 <keycode>' to make it known.
Jul 25 02:32:21 localhost kernel: [ 1014.210329] atkbd serio0: Unknown key released (translated set 2, code 0x98 on isa0060/serio0).
Jul 25 02:32:21 localhost kernel: [ 1014.210331] atkbd serio0: Use 'setkeycodes e018 <keycode>' to make it known.
Jul 25 02:32:21 localhost anacron[11636]: Anacron 2.3 started on 2014-07-25
Jul 25 02:32:21 localhost anacron[11636]: Normal exit (0 jobs run)
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> (eth1): carrier now OFF (device state 100, deferring action for 4 seconds)
Jul 25 02:32:21 localhost dhclient: receive_packet failed on eth1: Network is down
Jul 25 02:32:21 localhost NetworkManager[1002]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth1, iface: eth1)
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> (eth1): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> (eth1): deactivating device (reason 'removed') [36]
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> (eth1): canceled DHCP transaction, DHCP client pid 9404
Jul 25 02:32:21 localhost NetworkManager[1002]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/accept_ra': (2) Aucun fichier ou dossier de ce type
Jul 25 02:32:21 localhost NetworkManager[1002]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/eth1/use_tempaddr': (2) Aucun fichier ou dossier de ce type
Jul 25 02:32:21 localhost NetworkManager[1002]: <warn> (7) failed to find interface name for index
Jul 25 02:32:21 localhost NetworkManager[1002]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
Jul 25 02:32:21 localhost NetworkManager[1002]: <warn> (7) failed to find interface name for index
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> Policy set 'E.T Salon' (wlan0) as default for IPv4 routing and DNS.
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> Writing DNS information to /sbin/resolvconf
Jul 25 02:25:39 localhost dnsmasq[1602]: utilise le serveur de nom 192.168.1.1#53
Jul 25 02:32:21 localhost dnsmasq[1602]: configuration des serveurs amonts à partir de DBus
Jul 25 02:32:21 localhost dnsmasq[1602]: utilise le serveur de nom 192.168.1.1#53
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> (eth1): cleaning up...
Jul 25 02:32:21 localhost NetworkManager[1002]: <warn> (7) failed to find interface name for index
Jul 25 02:32:21 localhost NetworkManager[1002]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Jul 25 02:32:21 localhost NetworkManager[1002]: <error> [1406248341.612322] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Jul 25 02:32:21 localhost dbus[947]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 25 02:32:21 localhost dbus[947]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 25 02:32:21 localhost kernel: [ 1014.450767] PM: Syncing filesystems ... done.
Jul 25 02:32:21 localhost kernel: [ 1014.521730] PM: Preparing system for mem sleep
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> sleep requested (sleeping: no  enabled: yes)
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> sleeping or disabling...
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> (wlan0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Jul 25 02:32:21 localhost NetworkManager[1002]: <info> (wlan0): deactivating device (reason 'sleeping') [37]
Jul 25 02:32:27 localhost kernel: [ 1014.693982] Freezing user space processes ... (elapsed 0.001 seconds) done.
Jul 25 02:32:27 localhost kernel: [ 1014.695699] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Jul 25 02:32:27 localhost kernel: [ 1014.696827] PM: Entering mem sleep
Jul 25 02:32:27 localhost kernel: [ 1014.697011] Suspending console(s) (use no_console_suspend to debug)
Jul 25 02:32:27 localhost kernel: [ 1014.697158] wlan0: deauthenticating from 58:6d:8f:4a:af:cf by local choice (Reason: 3=DEAUTH_LEAVING)
Jul 25 02:32:27 localhost kernel: [ 1014.707207] cfg80211: Calling CRDA to update world regulatory domain
Jul 25 02:32:27 localhost kernel: [ 1014.707305] sd 5:0:0:0: [sdb] Synchronizing SCSI cache
Jul 25 02:32:27 localhost kernel: [ 1014.707425] sd 1:0:0:0: [sda] Synchronizing SCSI cache
Jul 25 02:32:27 localhost kernel: [ 1014.707453] sd 5:0:0:0: [sdb] Stopping disk
Jul 25 02:32:27 localhost kernel: [ 1014.708047] sd 1:0:0:0: [sda] Stopping disk
Jul 25 02:32:27 localhost kernel: [ 1014.762787] i8042 kbd 00:0b: System wakeup enabled by ACPI
Jul 25 02:32:27 localhost kernel: [ 1014.762795] i8042 aux 00:0a: System wakeup disabled by ACPI
Jul 25 02:32:27 localhost kernel: [ 1014.921892] ath: phy0: RX failed to go idle in 10 ms RXSM=0xdeadbeef
Jul 25 02:32:27 localhost kernel: [ 1014.933517] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xdeadbeef AR_DIAG_SW=0xdeadbeef DMADBG_7=0xdeadbeef
Jul 25 02:32:27 localhost kernel: [ 1015.225552] PM: suspend of devices complete after 528.599 msecs
Jul 25 02:32:27 localhost kernel: [ 1015.241603] PM: late suspend of devices complete after 16.053 msecs
Jul 25 02:32:27 localhost kernel: [ 1015.242051] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
Jul 25 02:32:27 localhost kernel: [ 1015.242236] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
Jul 25 02:32:27 localhost kernel: [ 1015.242257] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
Jul 25 02:32:27 localhost kernel: [ 1015.257526] PM: noirq suspend of devices complete after 15.926 msecs
Jul 25 02:32:27 localhost kernel: [ 1015.257724] ACPI: Preparing to enter system sleep state S3
Jul 25 02:32:27 localhost kernel: [ 1015.267919] PM: Saving platform NVS memory
Jul 25 02:32:27 localhost kernel: [ 1015.270139] Disabling non-boot CPUs ...
Jul 25 02:32:27 localhost kernel: [ 1015.270172] intel_pstate CPU 1 exiting
Jul 25 02:32:27 localhost kernel: [ 1015.271324] kvm: disabling virtualization on CPU1
Jul 25 02:32:27 localhost kernel: [ 1015.373439] smpboot: CPU 1 is now offline
Jul 25 02:32:27 localhost kernel: [ 1015.373721] intel_pstate CPU 2 exiting
Jul 25 02:32:27 localhost kernel: [ 1015.374859] kvm: disabling virtualization on CPU2
Jul 25 02:32:27 localhost kernel: [ 1015.477412] smpboot: CPU 2 is now offline
Jul 25 02:32:27 localhost kernel: [ 1015.477665] intel_pstate CPU 3 exiting
Jul 25 02:32:27 localhost kernel: [ 1015.478798] kvm: disabling virtualization on CPU3
Jul 25 02:32:27 localhost kernel: [ 1015.581382] smpboot: CPU 3 is now offline
Jul 25 02:32:27 localhost kernel: [ 1015.581618] intel_pstate CPU 4 exiting
Jul 25 02:32:27 localhost kernel: [ 1015.622582] kvm: disabling virtualization on CPU4
Jul 25 02:32:27 localhost kernel: [ 1015.725348] smpboot: CPU 4 is now offline
Jul 25 02:32:27 localhost kernel: [ 1015.725627] intel_pstate CPU 5 exiting
Jul 25 02:32:27 localhost kernel: [ 1015.725732] Broke affinity for irq 19
Jul 25 02:32:27 localhost kernel: [ 1015.726738] kvm: disabling virtualization on CPU5
Jul 25 02:32:27 localhost kernel: [ 1015.829303] smpboot: CPU 5 is now offline
Jul 25 02:32:27 localhost kernel: [ 1015.829555] intel_pstate CPU 6 exiting
Jul 25 02:32:27 localhost kernel: [ 1015.829642] Broke affinity for irq 16
Jul 25 02:32:27 localhost kernel: [ 1015.830650] kvm: disabling virtualization on CPU6
Jul 25 02:32:27 localhost kernel: [ 1015.830652] smpboot: CPU 6 is now offline
Jul 25 02:32:27 localhost kernel: [ 1015.830872] intel_pstate CPU 7 exiting
Jul 25 02:32:27 localhost kernel: [ 1015.830981] Broke affinity for irq 23
Jul 25 02:32:27 localhost kernel: [ 1015.830984] Broke affinity for irq 45
Jul 25 02:32:27 localhost kernel: [ 1015.831986] kvm: disabling virtualization on CPU7
Jul 25 02:32:27 localhost kernel: [ 1015.933267] smpboot: CPU 7 is now offline
Jul 25 02:32:27 localhost kernel: [ 1015.934665] ACPI: Low-level resume complete
Jul 25 02:32:27 localhost kernel: [ 1015.934702] PM: Restoring platform NVS memory
Jul 25 02:32:27 localhost kernel: [ 1015.935696] Enabling non-boot CPUs ...
Jul 25 02:32:27 localhost kernel: [ 1015.935736] x86: Booting SMP configuration:
Jul 25 02:32:27 localhost kernel: [ 1015.935737] smpboot: Booting Node 0 Processor 1 APIC 0x2
Jul 25 02:32:27 localhost kernel: [ 1015.947612] kvm: enabling virtualization on CPU1
Jul 25 02:32:27 localhost kernel: [ 1015.949814] Intel pstate controlling: cpu 1
Jul 25 02:32:27 localhost kernel: [ 1015.949875] CPU1 is up
Jul 25 02:32:27 localhost kernel: [ 1015.949893] smpboot: Booting Node 0 Processor 2 APIC 0x4
Jul 25 02:32:27 localhost kernel: [ 1015.961616] kvm: enabling virtualization on CPU2
Jul 25 02:32:27 localhost kernel: [ 1015.963869] Intel pstate controlling: cpu 2
Jul 25 02:32:27 localhost kernel: [ 1015.963920] CPU2 is up
Jul 25 02:32:27 localhost kernel: [ 1015.963938] smpboot: Booting Node 0 Processor 3 APIC 0x6
Jul 25 02:32:27 localhost kernel: [ 1015.975671] kvm: enabling virtualization on CPU3
Jul 25 02:32:27 localhost kernel: [ 1015.977872] Intel pstate controlling: cpu 3
Jul 25 02:32:27 localhost kernel: [ 1015.977918] CPU3 is up
Jul 25 02:32:27 localhost kernel: [ 1015.977934] smpboot: Booting Node 0 Processor 4 APIC 0x1
Jul 25 02:32:27 localhost kernel: [ 1015.989616] kvm: enabling virtualization on CPU4
Jul 25 02:32:27 localhost kernel: [ 1015.991785] Intel pstate controlling: cpu 4
Jul 25 02:32:27 localhost kernel: [ 1015.991831] CPU4 is up
Jul 25 02:32:27 localhost kernel: [ 1015.991845] smpboot: Booting Node 0 Processor 5 APIC 0x3
Jul 25 02:32:27 localhost kernel: [ 1016.003550] kvm: enabling virtualization on CPU5
Jul 25 02:32:27 localhost kernel: [ 1016.005676] Intel pstate controlling: cpu 5
Jul 25 02:32:27 localhost kernel: [ 1016.005711] CPU5 is up
Jul 25 02:32:27 localhost kernel: [ 1016.005723] smpboot: Booting Node 0 Processor 6 APIC 0x5
Jul 25 02:32:27 localhost kernel: [ 1016.017426] kvm: enabling virtualization on CPU6
Jul 25 02:32:27 localhost kernel: [ 1016.019557] Intel pstate controlling: cpu 6
Jul 25 02:32:27 localhost kernel: [ 1016.019590] CPU6 is up
Jul 25 02:32:27 localhost kernel: [ 1016.019602] smpboot: Booting Node 0 Processor 7 APIC 0x7
Jul 25 02:32:27 localhost kernel: [ 1016.031316] kvm: enabling virtualization on CPU7
Jul 25 02:32:27 localhost kernel: [ 1016.033539] Intel pstate controlling: cpu 7
Jul 25 02:32:27 localhost kernel: [ 1016.033571] CPU7 is up
Jul 25 02:32:27 localhost kernel: [ 1016.040097] ACPI: Waking up from system sleep state S3
Jul 25 02:32:27 localhost kernel: [ 1016.055503] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
Jul 25 02:32:27 localhost kernel: [ 1016.055518] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
Jul 25 02:32:27 localhost kernel: [ 1016.055521] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
Jul 25 02:32:27 localhost kernel: [ 1016.067620] PM: noirq resume of devices complete after 14.033 msecs
Jul 25 02:32:27 localhost kernel: [ 1016.067926] PM: early resume of devices complete after 0.285 msecs
Jul 25 02:32:27 localhost kernel: [ 1016.068006] mei_me 0000:00:16.0: irq 47 for MSI/MSI-X
Jul 25 02:32:27 localhost kernel: [ 1016.068141] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
Jul 25 02:32:27 localhost kernel: [ 1016.069722] sd 1:0:0:0: [sda] Starting disk
Jul 25 02:32:27 localhost kernel: [ 1016.069725] sd 5:0:0:0: [sdb] Starting disk
Jul 25 02:32:27 localhost kernel: [ 1016.255340] i8042 kbd 00:0b: System wakeup disabled by ACPI
Jul 25 02:32:27 localhost kernel: [ 1016.387247] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 25 02:32:27 localhost kernel: [ 1016.397053] ata3.00: configured for UDMA/100
Jul 25 02:32:27 localhost kernel: [ 1016.407245] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jul 25 02:32:27 localhost kernel: [ 1016.409762] ata2.00: configured for UDMA/133
Jul 25 02:32:27 localhost kernel: [ 1016.435399] usb 3-9: reset high-speed USB device number 4 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1016.435418] xhci_hcd 0000:00:14.0: Setup ERROR: setup context command for slot 3.
Jul 25 02:32:27 localhost kernel: [ 1016.435420] usb 3-9: hub failed to enable device, error -22
Jul 25 02:32:27 localhost kernel: [ 1016.547220] usb 3-9: reset high-speed USB device number 4 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1016.547268] xhci_hcd 0000:00:14.0: Setup ERROR: setup context command for slot 3.
Jul 25 02:32:27 localhost kernel: [ 1016.547269] usb 3-9: hub failed to enable device, error -22
Jul 25 02:32:27 localhost kernel: [ 1016.659210] usb 3-9: reset high-speed USB device number 4 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1016.706360] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8804192b6420
Jul 25 02:32:27 localhost kernel: [ 1016.843284] usb 3-1: reset full-speed USB device number 2 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1016.843294] xhci_hcd 0000:00:14.0: Setup ERROR: setup context command for slot 1.
Jul 25 02:32:27 localhost kernel: [ 1016.843295] usb 3-1: hub failed to enable device, error -22
Jul 25 02:32:27 localhost kernel: [ 1016.955124] usb 3-1: reset full-speed USB device number 2 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1016.955204] xhci_hcd 0000:00:14.0: Setup ERROR: setup context command for slot 1.
Jul 25 02:32:27 localhost kernel: [ 1016.955205] usb 3-1: hub failed to enable device, error -22
Jul 25 02:32:27 localhost kernel: [ 1017.067080] usb 3-1: reset full-speed USB device number 2 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1017.084263] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8804192b6300
Jul 25 02:32:27 localhost kernel: [ 1017.084263] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8804192b6360
Jul 25 02:32:27 localhost kernel: [ 1017.084264] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8804192b63c0
Jul 25 02:32:27 localhost kernel: [ 1017.195194] usb 3-8: reset full-speed USB device number 16 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1017.195262] xhci_hcd 0000:00:14.0: Setup ERROR: setup context command for slot 15.
Jul 25 02:32:27 localhost kernel: [ 1017.195263] usb 3-8: hub failed to enable device, error -22
Jul 25 02:32:27 localhost kernel: [ 1017.307026] usb 3-8: reset full-speed USB device number 16 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1017.307091] xhci_hcd 0000:00:14.0: Setup ERROR: setup context command for slot 15.
Jul 25 02:32:27 localhost kernel: [ 1017.307092] usb 3-8: hub failed to enable device, error -22
Jul 25 02:32:27 localhost kernel: [ 1017.419036] usb 3-8: reset full-speed USB device number 16 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1017.436323] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff880035e73ea0
Jul 25 02:32:27 localhost kernel: [ 1017.436325] usb 3-8: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jul 25 02:32:27 localhost kernel: [ 1017.436770] dpm_run_callback(): usb_dev_resume+0x0/0x20 returns -32
Jul 25 02:32:27 localhost kernel: [ 1017.436775] PM: Device 3-8 failed to resume async: error -32
Jul 25 02:32:27 localhost kernel: [ 1017.436848] PM: resume of devices complete after 1369.343 msecs
Jul 25 02:32:27 localhost kernel: [ 1017.449942] PM: Finishing wakeup.
Jul 25 02:32:27 localhost kernel: [ 1017.449943] Restarting tasks ... 
Jul 25 02:32:27 localhost kernel: [ 1017.450015] pci 0000:03:00.0: no hotplug settings from platform
Jul 25 02:32:27 localhost kernel: [ 1017.450049] ath9k 0000:04:00.0: no hotplug settings from platform
Jul 25 02:32:27 localhost kernel: [ 1017.450066] rtsx_pci 0000:05:00.0: no hotplug settings from platform
Jul 25 02:30:46 localhost wpa_supplicant[1081]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jul 25 02:32:27 localhost wpa_supplicant[1081]: wlan0: CTRL-EVENT-DISCONNECTED bssid=58:6d:8f:4a:af:cf reason=3 locally_generated=1
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 9401
Jul 25 02:32:27 localhost kernel: [ 1017.450736] done.
Jul 25 02:32:27 localhost kernel: [ 1017.451102] usb 3-8: USB disconnect, device number 16
Jul 25 02:32:27 localhost kernel: [ 1017.458118] cfg80211: World regulatory domain updated:
Jul 25 02:32:27 localhost kernel: [ 1017.458121] cfg80211:  DFS Master region: unset
Jul 25 02:32:27 localhost kernel: [ 1017.458122] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 25 02:32:27 localhost kernel: [ 1017.458125] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 25 02:32:27 localhost kernel: [ 1017.458127] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 25 02:32:27 localhost kernel: [ 1017.458128] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 25 02:32:27 localhost kernel: [ 1017.458129] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 25 02:32:27 localhost kernel: [ 1017.458130] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 25 02:32:27 localhost NetworkManager[1002]: <warn> DNS: plugin dnsmasq update failed
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> Removing DNS information from /sbin/resolvconf
Jul 25 02:32:27 localhost dnsmasq[1602]: configuration des serveurs amonts à partir de DBus
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): cleaning up...
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): taking down device.
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> NetworkManager state is now ASLEEP
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> wake requested (sleeping: yes  enabled: yes)
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> waking up and re-enabling...
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): bringing up device.
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): preparing device.
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> NetworkManager state is now DISCONNECTED
Jul 25 02:32:27 localhost kernel: [ 1017.499552] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0) supports 4 scan SSIDs
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): supplicant interface state: starting -> ready
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul 25 02:32:27 localhost NetworkManager[1002]: <warn> Trying to remove a non-existant call id.
Jul 25 02:32:27 localhost wpa_supplicant[1081]: wlan0: Reject scan trigger since one is already pending
Jul 25 02:32:27 localhost wpa_supplicant[1081]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jul 25 02:32:27 localhost NetworkManager[1002]: <info> (wlan0) supports 4 scan SSIDs
Jul 25 02:32:27 localhost kernel: [ 1017.582901] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Jul 25 02:32:27 localhost kernel: [ 1017.594970] video LNXVIDEO:00: Restoring backlight state
Jul 25 02:32:27 localhost kernel: [ 1017.594973] video LNXVIDEO:01: Restoring backlight state
Jul 25 02:32:27 localhost kernel: [ 1017.618885] usb 3-8: new full-speed USB device number 19 using xhci_hcd
Jul 25 02:32:27 localhost kernel: [ 1017.749106] usb 3-8: New USB device found, idVendor=1770, idProduct=ff00
Jul 25 02:32:27 localhost kernel: [ 1017.749109] usb 3-8: New USB device strings: Mfr=1, Product=1, SerialNumber=1
Jul 25 02:32:27 localhost kernel: [ 1017.749110] usb 3-8: Product: MSI EPF USB
Jul 25 02:32:27 localhost kernel: [ 1017.749111] usb 3-8: Manufacturer: MSI EPF USB
Jul 25 02:32:27 localhost kernel: [ 1017.749112] usb 3-8: SerialNumber: MSI EPF USB
Jul 25 02:32:27 localhost kernel: [ 1017.749220] usb 3-8: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jul 25 02:32:27 localhost mtp-probe: checking bus 3, device 19: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8"
Jul 25 02:32:27 localhost mtp-probe: bus: 3, device: 19 was not an MTP device
Jul 25 02:32:27 localhost kernel: [ 1017.750949] hid-generic 0003:1770:FF00.000A: hiddev0,hidraw2: USB HID v1.10 Device [MSI EPF USB MSI EPF USB] on usb-0000:00:14.0-8/input0
Jul 25 02:32:27 localhost bluetoothd[985]: Adapter /org/bluez/985/hci0 has been disabled
Jul 25 02:32:27 localhost bluetoothd[985]: Unregister path: /org/bluez/985/hci0
Jul 25 02:32:27 localhost bluetoothd[985]: hci0: Set IO Capability (0x0018) failed: Invalid Index (0x11)
Jul 25 02:32:27 localhost kernel: [ 1017.766879] usb 3-11: USB disconnect, device number 18
Jul 25 02:32:28 localhost kernel: [ 1018.006763] usb 3-11: new full-speed USB device number 20 using xhci_hcd
Jul 25 02:32:28 localhost kernel: [ 1018.136118] usb 3-11: string descriptor 0 malformed (err = -61), defaulting to 0x0409
Jul 25 02:32:28 localhost kernel: [ 1018.137955] usb 3-11: New USB device found, idVendor=0cf3, idProduct=3004
Jul 25 02:32:28 localhost kernel: [ 1018.137956] usb 3-11: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 25 02:32:28 localhost kernel: [ 1018.138705] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jul 25 02:32:28 localhost kernel: [ 1018.139991] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
Jul 25 02:32:28 localhost kernel: [ 1018.139994] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Jul 25 02:32:28 localhost kernel: [ 1018.139995] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
Jul 25 02:32:28 localhost kernel: [ 1018.142562] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
Jul 25 02:32:28 localhost kernel: [ 1018.142564] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Jul 25 02:32:28 localhost kernel: [ 1018.142565] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
Jul 25 02:32:28 localhost kernel: [ 1018.143814] ata6.00: configured for UDMA/133
Jul 25 02:32:28 localhost kernel: [ 1018.174215] usb 3-11: USB disconnect, device number 20
Jul 25 02:32:28 localhost kernel: [ 1018.446711] usb 3-11: new full-speed USB device number 21 using xhci_hcd
Jul 25 02:32:28 localhost kernel: [ 1018.575912] usb 3-11: string descriptor 0 malformed (err = -61), defaulting to 0x0409
Jul 25 02:32:28 localhost kernel: [ 1018.577779] usb 3-11: New USB device found, idVendor=0cf3, idProduct=3004
Jul 25 02:32:28 localhost kernel: [ 1018.577782] usb 3-11: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 25 02:32:28 localhost anacron[12195]: Anacron 2.3 started on 2014-07-25
Jul 25 02:32:28 localhost anacron[12195]: Normal exit (0 jobs run)
Jul 25 02:32:28 localhost bluetoothd[985]: Unknown command complete for opcode 19
Jul 25 02:32:28 localhost bluetoothd[985]: Adapter /org/bluez/985/hci0 has been enabled
Jul 25 02:32:28 localhost kernel: [ 1018.667531] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [48:1e:2a:b9:80:b7]
Jul 25 02:32:28 localhost NetworkManager[1002]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth1, iface: eth1)
Jul 25 02:32:28 localhost NetworkManager[1002]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Jul 25 02:32:28 localhost NetworkManager[1002]: <warn> failed to allocate link cache: (-12) Object not found
Jul 25 02:32:28 localhost NetworkManager[1002]: <info> (eth1): carrier is OFF
Jul 25 02:32:28 localhost NetworkManager[1002]: <info> (eth1): new Ethernet device (driver: 'alx' ifindex: 8)
Jul 25 02:32:28 localhost NetworkManager[1002]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/6
Jul 25 02:32:28 localhost NetworkManager[1002]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 25 02:32:28 localhost NetworkManager[1002]: <info> (eth1): bringing up device.
Jul 25 02:32:28 localhost NetworkManager[1002]: <info> (eth1): preparing device.
Jul 25 02:32:28 localhost NetworkManager[1002]: <info> (eth1): deactivating device (reason 'managed') [2]
Jul 25 02:32:28 localhost NetworkManager[1002]: <info> Added default wired connection 'Connexion filaire 1' for /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth1
Jul 25 02:32:28 localhost kernel: [ 1018.691236] alx 0000:03:00.0: irq 49 for MSI/MSI-X
Jul 25 02:32:28 localhost kernel: [ 1018.691406] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul 25 02:32:28 localhost anacron[12286]: Anacron 2.3 started on 2014-07-25
Jul 25 02:32:28 localhost anacron[12286]: Normal exit (0 jobs run)
Jul 25 02:32:28 localhost acpid: client 9811[0:0] has disconnected
Jul 25 02:32:28 localhost acpid: client connected from 9811[0:0]
Jul 25 02:32:28 localhost acpid: 1 client rule loaded
Jul 25 02:32:28 localhost acpid: client 9811[0:0] has disconnected
Jul 25 02:32:28 localhost acpid: client connected from 12131[0:0]
Jul 25 02:32:28 localhost acpid: 1 client rule loaded
Jul 25 02:32:29 localhost ntpd[9747]: Deleting interface #7 wlan0, fe80::8256:f2ff:fea5:c193#123, interface stats: received=0, sent=0, dropped=0, active_time=381 secs
Jul 25 02:32:29 localhost ntpd[9747]: Deleting interface #6 eth1, fe80::4a1e:2aff:feb9:80b7#123, interface stats: received=0, sent=0, dropped=0, active_time=381 secs
Jul 25 02:32:29 localhost ntpd[9747]: Deleting interface #4 eth1, 192.168.1.39#123, interface stats: received=12, sent=30, dropped=0, active_time=381 secs
Jul 25 02:32:29 localhost ntpd[9747]: 91.189.94.4 interface 192.168.1.39 -> (none)
Jul 25 02:32:29 localhost ntpd[9747]: 212.43.246.10 interface 192.168.1.39 -> (none)
Jul 25 02:32:29 localhost ntpd[9747]: 193.55.167.2 interface 192.168.1.39 -> (none)
Jul 25 02:32:29 localhost ntpd[9747]: 87.98.180.13 interface 192.168.1.39 -> (none)
Jul 25 02:32:29 localhost ntpd[9747]: 129.250.35.250 interface 192.168.1.39 -> (none)
Jul 25 02:32:29 localhost ntpd[9747]: Deleting interface #3 wlan0, 192.168.1.52#123, interface stats: received=0, sent=0, dropped=0, active_time=381 secs
Jul 25 02:32:29 localhost ntpd[9747]: peers refreshed
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Auto-activating connection 'E.T Salon'.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) starting connection 'E.T Salon'
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> NetworkManager state is now CONNECTING
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0/wireless): access point 'E.T Salon' has security, but secrets are required.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0/wireless): connection 'E.T Salon' has security, and secrets exist.  No new secrets needed.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Config: added 'ssid' value 'E.T Salon'
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Config: added 'scan_ssid' value '1'
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Config: added 'psk' value '<omitted>'
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Config: set interface ap_scan to 1
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jul 25 02:32:31 localhost wpa_supplicant[1081]: wlan0: SME: Trying to authenticate with 58:6d:8f:4a:af:cf (SSID='E.T Salon' freq=5180 MHz)
Jul 25 02:32:31 localhost kernel: [ 1021.007560] wlan0: authenticate with 58:6d:8f:4a:af:cf
Jul 25 02:32:31 localhost kernel: [ 1021.013722] wlan0: send auth to 58:6d:8f:4a:af:cf (try 1/3)
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jul 25 02:32:31 localhost wpa_supplicant[1081]: wlan0: Trying to associate with 58:6d:8f:4a:af:cf (SSID='E.T Salon' freq=5180 MHz)
Jul 25 02:32:31 localhost kernel: [ 1021.014700] wlan0: authenticated
Jul 25 02:32:31 localhost wpa_supplicant[1081]: wlan0: Associated with 58:6d:8f:4a:af:cf
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): supplicant interface state: authenticating -> associated
Jul 25 02:32:31 localhost kernel: [ 1021.017822] wlan0: associate with 58:6d:8f:4a:af:cf (try 1/3)
Jul 25 02:32:31 localhost kernel: [ 1021.019331] wlan0: RX AssocResp from 58:6d:8f:4a:af:cf (capab=0x11 status=0 aid=1)
Jul 25 02:32:31 localhost kernel: [ 1021.019362] wlan0: associated
Jul 25 02:32:31 localhost kernel: [ 1021.019377] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jul 25 02:32:31 localhost wpa_supplicant[1081]: wlan0: WPA: Key negotiation completed with 58:6d:8f:4a:af:cf [PTK=CCMP GTK=CCMP]
Jul 25 02:32:31 localhost wpa_supplicant[1081]: wlan0: CTRL-EVENT-CONNECTED - Connection to 58:6d:8f:4a:af:cf completed [id=0 id_str=]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'E.T Salon'.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> dhclient started with pid 12514
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 25 02:32:31 localhost dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jul 25 02:32:31 localhost dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jul 25 02:32:31 localhost dhclient: All rights reserved.
Jul 25 02:32:31 localhost dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 25 02:32:31 localhost dhclient: 
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 25 02:32:31 localhost dhclient: Listening on LPF/wlan0/80:56:f2:a5:c1:93
Jul 25 02:32:31 localhost dhclient: Sending on   LPF/wlan0/80:56:f2:a5:c1:93
Jul 25 02:32:31 localhost dhclient: Sending on   Socket/fallback
Jul 25 02:32:31 localhost dhclient: DHCPREQUEST of 192.168.1.52 on wlan0 to 255.255.255.255 port 67 (xid=0x761879ad)
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (eth1): carrier now ON (device state 20)
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (eth1): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Auto-activating connection 'Connexion filaire 1'.
Jul 25 02:32:31 localhost kernel: [ 1021.652842] alx 0000:03:00.0 eth1: NIC Up: 1 Gbps Full
Jul 25 02:32:31 localhost kernel: [ 1021.653061] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) starting connection 'Connexion filaire 1'
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> dhclient started with pid 12516
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Beginning IP6 addrconf.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Jul 25 02:32:31 localhost dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jul 25 02:32:31 localhost dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jul 25 02:32:31 localhost dhclient: All rights reserved.
Jul 25 02:32:31 localhost dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 25 02:32:31 localhost dhclient: 
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Jul 25 02:32:31 localhost dhclient: Listening on LPF/eth1/48:1e:2a:b9:80:b7
Jul 25 02:32:31 localhost dhclient: Sending on   LPF/eth1/48:1e:2a:b9:80:b7
Jul 25 02:32:31 localhost dhclient: Sending on   Socket/fallback
Jul 25 02:32:31 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x69ee3b4)
Jul 25 02:32:31 localhost dhclient: DHCPREQUEST of 192.168.1.39 on eth1 to 255.255.255.255 port 67 (xid=0x69ee3b4)
Jul 25 02:32:31 localhost dhclient: DHCPOFFER of 192.168.1.39 from 192.168.1.1
Jul 25 02:32:31 localhost dhclient: DHCPACK of 192.168.1.39 from 192.168.1.1
Jul 25 02:32:31 localhost dhclient: bound to 192.168.1.39 -- renewal in 41163 seconds.
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> (eth1): DHCPv4 state changed preinit -> bound
Jul 25 02:32:31 localhost NetworkManager[1002]: <info>   address 192.168.1.39
Jul 25 02:32:31 localhost NetworkManager[1002]: <info>   prefix 24 (255.255.255.0)
Jul 25 02:32:31 localhost NetworkManager[1002]: <info>   gateway 192.168.1.1
Jul 25 02:32:31 localhost NetworkManager[1002]: <info>   hostname 'kwaadpepper-laptop'
Jul 25 02:32:31 localhost NetworkManager[1002]: <info>   nameserver '192.168.1.1'
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 25 02:32:31 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Jul 25 02:32:31 localhost acpid: client 12131[0:0] has disconnected
Jul 25 02:32:21 localhost whoopsie[1249]: message repeated 5 times: [ online]
Jul 25 02:32:32 localhost whoopsie[1249]: offline
Jul 25 02:32:32 localhost NetworkManager[1002]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul 25 02:32:32 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Jul 25 02:32:32 localhost NetworkManager[1002]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 25 02:32:32 localhost NetworkManager[1002]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jul 25 02:32:32 localhost NetworkManager[1002]: <info> Policy set 'Connexion filaire 1' (eth1) as default for IPv4 routing and DNS.
Jul 25 02:32:32 localhost NetworkManager[1002]: <info> Writing DNS information to /sbin/resolvconf
Jul 25 02:32:32 localhost dnsmasq[1602]: configuration des serveurs amonts à partir de DBus
Jul 25 02:32:32 localhost dnsmasq[1602]: utilise le serveur de nom 192.168.1.1#53
Jul 25 02:32:32 localhost NetworkManager[1002]: <info> Activation (eth1) successful, device activated.
Jul 25 02:32:32 localhost ntpd[9747]: ntpd exiting on signal 15
Jul 25 02:32:32 localhost NetworkManager[1002]: <warn> error monitoring device for netlink events: erreur lors du traitement du message netlink : Object busy
Jul 25 02:32:32 localhost whoopsie[1249]: message repeated 5 times: [ offline]
Jul 25 02:32:32 localhost whoopsie[1249]: online
Jul 25 02:32:34 localhost dhclient: DHCPREQUEST of 192.168.1.52 on wlan0 to 255.255.255.255 port 67 (xid=0x761879ad)
Jul 25 02:32:34 localhost dhclient: DHCPACK of 192.168.1.52 from 192.168.1.1
Jul 25 02:32:34 localhost dhclient: bound to 192.168.1.52 -- renewal in 32945 seconds.
Jul 25 02:32:34 localhost NetworkManager[1002]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul 25 02:32:34 localhost NetworkManager[1002]: <info>   address 192.168.1.52
Jul 25 02:32:34 localhost NetworkManager[1002]: <info>   prefix 24 (255.255.255.0)
Jul 25 02:32:34 localhost NetworkManager[1002]: <info>   gateway 192.168.1.1
Jul 25 02:32:34 localhost NetworkManager[1002]: <info>   hostname 'kwaadpepper-laptop'
Jul 25 02:32:34 localhost NetworkManager[1002]: <info>   nameserver '192.168.1.1'
Jul 25 02:32:34 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 25 02:32:34 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul 25 02:32:35 localhost kernel: [ 1025.093893] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:35 localhost NetworkManager[1002]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul 25 02:32:35 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 25 02:32:35 localhost NetworkManager[1002]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.121': no such name
Jul 25 02:32:35 localhost NetworkManager[1002]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 25 02:32:35 localhost NetworkManager[1002]: <info> Writing DNS information to /sbin/resolvconf
Jul 25 02:32:35 localhost dnsmasq[1602]: configuration des serveurs amonts à partir de DBus
Jul 25 02:32:35 localhost dnsmasq[1602]: utilise le serveur de nom 192.168.1.1#53
Jul 25 02:32:35 localhost NetworkManager[1002]: <info> (wlan0): roamed from BSSID 58:6D:8F:4A:AF:CE (E.T Salon) to 58:6D:8F:4A:AF:CF (E.T Salon)
Jul 25 02:32:35 localhost NetworkManager[1002]: <info> Activation (wlan0) successful, device activated.
Jul 25 02:32:35 localhost NetworkManager[1002]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.121': no such name
Jul 25 02:32:35 localhost NetworkManager[1002]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.121': no such name
Jul 25 02:32:35 localhost NetworkManager[1002]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.121': no such name
Jul 25 02:32:35 localhost NetworkManager[1002]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.121': no such name
Jul 25 02:32:35 localhost NetworkManager[1002]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.121': no such name
Jul 25 02:32:36 localhost acpid: client 9811[0:0] has disconnected
Jul 25 02:32:36 localhost kernel: [ 1026.175710] nvidia 0000:01:00.0: irq 50 for MSI/MSI-X
Jul 25 02:32:36 localhost kernel: [ 1026.179744] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.179790] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.179814] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.179860] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.179899] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.179940] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.179987] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.180039] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.242248] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.242289] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost kernel: [ 1026.245763] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140214/nsarguments-95)
Jul 25 02:32:36 localhost acpid: client connected from 12765[0:0]
Jul 25 02:32:36 localhost acpid: 1 client rule loaded
Jul 25 02:32:36 localhost acpid: client connected from 12765[0:0]
Jul 25 02:32:36 localhost acpid: 1 client rule loaded
Jul 25 02:32:39 localhost dbus[947]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 25 02:32:39 localhost dbus[947]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 25 02:32:42 localhost rtkit-daemon[2741]: Successfully made thread 13386 of process 13386 (n/a) owned by '1000' high priority at nice level -11.
Jul 25 02:32:42 localhost rtkit-daemon[2741]: Supervising 1 threads of 1 processes of 1 users.
Jul 25 02:32:42 localhost pulseaudio[13386]: [pulseaudio] pid.c: Stale PID file, overwriting.
Jul 25 02:32:42 localhost rtkit-daemon[2741]: Successfully made thread 13387 of process 13386 (n/a) owned by '1000' RT at priority 5.
Jul 25 02:32:42 localhost rtkit-daemon[2741]: Supervising 2 threads of 1 processes of 1 users.
Jul 25 02:32:43 localhost NetworkManager[1002]: <warn> error monitoring device for netlink events: erreur lors du traitement du message netlink : Object busy
Jul 25 02:32:44 localhost ntpdate[12607]: adjust time server 91.189.89.199 offset 0.193593 sec
Jul 25 02:32:44 localhost ntpd[13415]: ntpd 4.2.6p5@1.2349-o Wed Oct  9 19:08:06 UTC 2013 (1)
Jul 25 02:32:44 localhost ntpd[13416]: proto: precision = 0.112 usec
Jul 25 02:32:44 localhost ntpd[13416]: ntp_io: estimated max descriptors: 2144, initial socket boundary: 16
Jul 25 02:32:44 localhost ntpd[13416]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Jul 25 02:32:44 localhost ntpd[13416]: Listen and drop on 1 v6wildcard :: UDP 123
Jul 25 02:32:44 localhost ntpd[13416]: Listen normally on 2 lo 127.0.0.1 UDP 123
Jul 25 02:32:44 localhost ntpd[13416]: Listen normally on 3 wlan0 192.168.1.52 UDP 123
Jul 25 02:32:44 localhost ntpd[13416]: Listen normally on 4 eth1 192.168.1.39 UDP 123
Jul 25 02:32:44 localhost ntpd[13416]: Listen normally on 5 lo ::1 UDP 123
Jul 25 02:32:44 localhost ntpd[13416]: Listen normally on 6 eth1 fe80::4a1e:2aff:feb9:80b7 UDP 123
Jul 25 02:32:44 localhost ntpd[13416]: Listen normally on 7 wlan0 fe80::8256:f2ff:fea5:c193 UDP 123
Jul 25 02:32:44 localhost ntpd[13416]: peers refreshed
Jul 25 02:32:44 localhost ntpd[13416]: Listening on routing socket on fd #24 for interface updates
Jul 25 02:32:46 localhost rtkit-daemon[2741]: Successfully made thread 13418 of process 13386 (n/a) owned by '1000' RT at priority 5.
Jul 25 02:32:46 localhost rtkit-daemon[2741]: Supervising 3 threads of 1 processes of 1 users.
Jul 25 02:32:46 localhost rtkit-daemon[2741]: Successfully made thread 13419 of process 13386 (n/a) owned by '1000' RT at priority 5.
Jul 25 02:32:46 localhost rtkit-daemon[2741]: Supervising 4 threads of 1 processes of 1 users.
Jul 25 02:32:48 localhost dbus[947]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Jul 25 02:32:48 localhost blueman-mechanism: Starting blueman-mechanism 
Jul 25 02:32:48 localhost dbus[947]: [system] Successfully activated service 'org.blueman.Mechanism'
Jul 25 02:32:48 localhost blueman-mechanism: loading RfKill 
Jul 25 02:32:48 localhost blueman-mechanism: loading Ppp 
Jul 25 02:32:48 localhost blueman-mechanism: loading Config 
Jul 25 02:32:48 localhost blueman-mechanism: loading Network 
Jul 25 02:32:50 localhost ntpd[13416]: ntpd exiting on signal 15
Jul 25 02:32:50 localhost wpa_supplicant[1081]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 25 02:32:51 localhost NetworkManager[1002]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 25 02:32:51 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 25 02:32:51 localhost NetworkManager[1002]: <info> (eth1): IP6 addrconf timed out or failed.
Jul 25 02:32:51 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 25 02:32:51 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 25 02:32:51 localhost NetworkManager[1002]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 25 02:32:51 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 25 02:32:51 localhost NetworkManager[1002]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.


```

I think it may be a KDE related problem but still can't find out where to look.

**EDIT**
Well it seems that even a simple pm-suspend works,  it's just a kde-power manager problem maybe, when it resume it quickly show log error, but not enough to read, it can't find this log. Using KDE suspend button it also works.
It looks like just lid close fails for unknown reason.

---

### Post by Toz on 2014-07-24
Does this laptop have more than one graphics card?
```
lspci -k | grep -A3 VGA
```

If its an optimus system, do you have bumblebee installed?

As for log files, since X is crashing, on recovery have a look at /var/log/Xorg.0.log.old, /var/log/pm-suspend.log and the results of:
```
cat /var/log/syslog | grep PM:
```
...might help.

---

### Post by jeremy-munsch on 2014-07-24
Yes it use optimus.
$ lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 1106
    Kernel driver in use: i915
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
--
01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 870M] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 1106
    Kernel driver in use: nvidia
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)


I used the last proprietary nvidia dirver downloaded form their site. I don't use bumblebee but primus i think, i can switch form integrated to dedicaced in nvidia config manager.

in Xorg.old
```

[  2391.456] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[  2391.456] X Protocol Version 11, Revision 0
[  2391.456] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  2391.456] Current Operating System: Linux kwaadpepper-laptop 3.15.6-031506-generic #201407172034 SMP Fri Jul 18 00:36:12 UTC 2014 x86_64
[  2391.456] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.15.6-031506-generic root=UUID=68debd3d-e029-469b-913f-f7b479b2fa42 ro quiet splash
[  2391.456] Build Date: 16 April 2014  01:36:29PM
[  2391.456] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[  2391.456] Current version of pixman: 0.30.2
[  2391.456]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[  2391.456] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2391.456] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 25 02:55:24 2014
[  2391.456] (==) Using config file: "/etc/X11/xorg.conf"
[  2391.456] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2391.456] (==) ServerLayout "layout"
[  2391.456] (**) |-->Screen "nvidia" (0)
[  2391.456] (**) |   |-->Monitor "<default monitor>"
[  2391.457] (**) |   |-->Device "nvidia"
[  2391.457] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[  2391.457] (**) |-->Inactive Device "intel"
[  2391.457] (==) Automatically adding devices
[  2391.457] (==) Automatically enabling devices
[  2391.457] (==) Automatically adding GPU devices
[  2391.457] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2391.457]     Entry deleted from font path.
[  2391.457] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2391.457]     Entry deleted from font path.
[  2391.457] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2391.457]     Entry deleted from font path.
[  2391.457] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2391.457]     Entry deleted from font path.
[  2391.457] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2391.457]     Entry deleted from font path.
[  2391.457] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  2391.457] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2391.457] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  2391.457] (II) Loader magic: 0x7fb729fe0d60
[  2391.457] (II) Module ABI versions:
[  2391.457]     X.Org ANSI C Emulation: 0.4
[  2391.457]     X.Org Video Driver: 15.0
[  2391.457]     X.Org XInput driver : 20.0
[  2391.457]     X.Org Server Extension : 8.0
[  2391.457] (II) xfree86: Adding drm device (/dev/dri/card1)
[  2391.457] (II) xfree86: Adding drm device (/dev/dri/card0)
[  2391.458] (--) PCI:*(0:0:2:0) 8086:0416:1462:1106 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[  2391.458] (--) PCI: (0:1:0:0) 10de:1199:1462:1106 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[  2391.458] Initializing built-in extension Generic Event Extension
[  2391.458] Initializing built-in extension SHAPE
[  2391.458] Initializing built-in extension MIT-SHM
[  2391.458] Initializing built-in extension XInputExtension
[  2391.458] Initializing built-in extension XTEST
[  2391.458] Initializing built-in extension BIG-REQUESTS
[  2391.458] Initializing built-in extension SYNC
[  2391.458] Initializing built-in extension XKEYBOARD
[  2391.458] Initializing built-in extension XC-MISC
[  2391.458] Initializing built-in extension SECURITY
[  2391.458] Initializing built-in extension XINERAMA
[  2391.458] Initializing built-in extension XFIXES
[  2391.458] Initializing built-in extension RENDER
[  2391.458] Initializing built-in extension RANDR
[  2391.458] Initializing built-in extension COMPOSITE
[  2391.458] Initializing built-in extension DAMAGE
[  2391.458] Initializing built-in extension MIT-SCREEN-SAVER
[  2391.458] Initializing built-in extension DOUBLE-BUFFER
[  2391.458] Initializing built-in extension RECORD
[  2391.458] Initializing built-in extension DPMS
[  2391.458] Initializing built-in extension Present
[  2391.458] Initializing built-in extension DRI3
[  2391.458] Initializing built-in extension X-Resource
[  2391.458] Initializing built-in extension XVideo
[  2391.458] Initializing built-in extension XVideo-MotionCompensation
[  2391.458] Initializing built-in extension SELinux
[  2391.458] Initializing built-in extension XFree86-VidModeExtension
[  2391.458] Initializing built-in extension XFree86-DGA
[  2391.458] Initializing built-in extension XFree86-DRI
[  2391.458] Initializing built-in extension DRI2
[  2391.458] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[  2391.458] (II) "glx" will be loaded by default.
[  2391.458] (WW) "xmir" is not to be loaded by default. Skipping.
[  2391.458] (II) LoadModule: "glx"
[  2391.458] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[  2391.464] (II) Module glx: vendor="NVIDIA Corporation"
[  2391.464]     compiled for 4.0.2, module version = 1.0.0
[  2391.464]     Module class: X.Org Server Extension
[  2391.464] (II) NVIDIA GLX Module  331.38  Wed Jan  8 19:10:17 PST 2014
[  2391.464] Loading extension GLX
[  2391.464] (II) LoadModule: "nvidia"
[  2391.464] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  2391.464] (II) Module nvidia: vendor="NVIDIA Corporation"
[  2391.464]     compiled for 4.0.2, module version = 1.0.0
[  2391.464]     Module class: X.Org Video Driver
[  2391.464] (II) LoadModule: "intel"
[  2391.464] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  2391.464] (II) Module intel: vendor="X.Org Foundation"
[  2391.464]     compiled for 1.15.0, module version = 2.99.910
[  2391.464]     Module class: X.Org Video Driver
[  2391.464]     ABI class: X.Org Video Driver, version 15.0
[  2391.464] (II) NVIDIA dlloader X Driver  331.38  Wed Jan  8 18:51:00 PST 2014
[  2391.464] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  2391.464] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[  2391.465] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[  2391.465] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[  2391.465] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[  2391.465] (++) using VT number 7

[  2391.468] (II) Loading sub module "fb"
[  2391.468] (II) LoadModule: "fb"
[  2391.468] (II) Loading /usr/lib/xorg/modules/libfb.so
[  2391.468] (II) Module fb: vendor="X.Org Foundation"
[  2391.468]     compiled for 1.15.1, module version = 1.0.0
[  2391.468]     ABI class: X.Org ANSI C Emulation, version 0.4
[  2391.468] (WW) Unresolved symbol: fbGetGCPrivateKey
[  2391.468] (II) Loading sub module "wfb"
[  2391.468] (II) LoadModule: "wfb"
[  2391.468] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  2391.468] (II) Module wfb: vendor="X.Org Foundation"
[  2391.468]     compiled for 1.15.1, module version = 1.0.0
[  2391.468]     ABI class: X.Org ANSI C Emulation, version 0.4
[  2391.468] (II) Loading sub module "ramdac"
[  2391.468] (II) LoadModule: "ramdac"
[  2391.468] (II) Module "ramdac" already built-in
[  2391.468] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>)
[  2391.468] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "nvidia" for depth/fbbpp 24/32
[  2391.468] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[  2391.468] (==) NVIDIA(0): RGB weight 888
[  2391.468] (==) NVIDIA(0): Default visual is TrueColor
[  2391.468] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  2391.468] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[  2391.468] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[  2391.468] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[  2391.468] (**) NVIDIA(0): Enabling 2D acceleration
[  2391.645] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[  2391.645] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 870M (GK104) at PCI:1:0:0 (GPU-0)
[  2391.645] (--) NVIDIA(0): Memory: 3145728 kBytes
[  2391.645] (--) NVIDIA(0): VideoBIOS: 80.04.ea.00.02
[  2391.645] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[  2391.648] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 870M at PCI:1:0:0
[  2391.648] (--) NVIDIA(0):     DFP-0
[  2391.648] (--) NVIDIA(0):     DFP-1
[  2391.648] (--) NVIDIA(0):     DFP-2
[  2391.648] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[  2391.648] (--) NVIDIA(0): DFP-0: 165.0 MHz maximum pixel clock
[  2391.648] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[  2391.648] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[  2391.648] (--) NVIDIA(0): DFP-2: Internal DisplayPort
[  2391.648] (--) NVIDIA(0): DFP-2: 960.0 MHz maximum pixel clock
[  2391.648] (==) NVIDIA(0): 
[  2391.648] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  2391.648] (==) NVIDIA(0):     will be used as the requested mode.
[  2391.648] (==) NVIDIA(0): 
[  2391.648] (--) NVIDIA(0): No enabled display devices found; starting anyway because
[  2391.648] (--) NVIDIA(0):     AllowEmptyInitialConfiguration is enabled
[  2391.648] (II) NVIDIA(0): Validated MetaModes:
[  2391.648] (II) NVIDIA(0):     "NULL"
[  2391.648] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[  2391.650] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[  2391.650] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[  2391.650] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[  2391.650] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[  2391.650] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[  2391.650] (==) intel(G0): RGB weight 888
[  2391.650] (==) intel(G0): Default visual is TrueColor
[  2391.650] (**) intel(G0): Option "AccelMethod" "SNA"
[  2391.650] (**) intel(G0): Framebuffer tiled
[  2391.650] (**) intel(G0): Pixmaps tiled
[  2391.650] (**) intel(G0): "Tear free" disabled
[  2391.650] (**) intel(G0): Forcing per-crtc-pixmaps? no
[  2391.650] (II) intel(G0): Output eDP1 has no monitor section
[  2391.651] (--) intel(G0): found backlight control interface acpi_video0 (type 'firmware')
[  2391.651] (II) intel(G0): Output VGA1 has no monitor section
[  2391.651] (II) intel(G0): Output VIRTUAL1 has no monitor section
[  2391.651] (--) intel(G0): Output eDP1 using initial mode  on pipe 0
[  2391.651] (==) intel(G0): DPI set to (96, 96)
[  2391.651] (II) Loading sub module "dri2"
[  2391.651] (II) LoadModule: "dri2"
[  2391.651] (II) Module "dri2" already built-in
[  2391.654] (--) Depth 24 pixmap format is 32 bpp
[  2391.654] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[  2391.654] (==) intel(G0): Backing store enabled
[  2391.654] (==) intel(G0): Silken mouse enabled
[  2391.654] (II) intel(G0): HW Cursor enabled
[  2391.654] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  2391.654] (==) intel(G0): DPMS enabled
[  2391.654] (II) intel(G0): [DRI2] Setup complete
[  2391.654] (II) intel(G0): [DRI2]   DRI driver: i965
[  2391.654] (II) intel(G0): [DRI2]   VDPAU driver: i965
[  2391.654] (II) intel(G0): direct rendering: DRI2 Enabled
[  2391.654] (WW) intel(G0): Option "AllowEmptyInitialConfiguration" is not used
[  2391.654] (WW) intel(G0): Option "IgnoreDisplayDevices" is not used
[  2391.654] (==) intel(G0): hotplug detection: "enabled"
[  2391.654] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[  2391.654] (II) NVIDIA:     access.
[  2391.665] (II) NVIDIA(0): Setting mode "NULL"
[  2391.674] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[  2391.674] Loading extension NV-GLX
[  2391.677] (==) NVIDIA(0): Disabling shared memory pixmaps
[  2391.677] (==) NVIDIA(0): Backing store enabled
[  2391.677] (==) NVIDIA(0): Silken mouse enabled
[  2391.677] (==) NVIDIA(0): DPMS enabled
[  2391.677] Loading extension NV-CONTROL
[  2391.677] (II) Loading sub module "dri2"
[  2391.677] (II) LoadModule: "dri2"
[  2391.677] (II) Module "dri2" already built-in
[  2391.677] (II) NVIDIA(0): [DRI2] Setup complete
[  2391.677] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[  2391.677] (--) RandR disabled
[  2391.680] (II) SELinux: Disabled on system
[  2391.680] (II) Initializing extension GLX
[  2391.682] (II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  2391.700] (II) intel(G0): Setting screen physical size to 508 x 285
[  2391.709] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  2391.710] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  2391.711] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2391.711] (II) LoadModule: "evdev"
[  2391.711] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2391.711] (II) Module evdev: vendor="X.Org Foundation"
[  2391.711]     compiled for 1.15.0, module version = 2.8.2
[  2391.711]     Module class: X.Org XInput Driver
[  2391.711]     ABI class: X.Org XInput driver, version 20.0
[  2391.711] (II) Using input driver 'evdev' for 'Power Button'
[  2391.711] (**) Power Button: always reports core events
[  2391.711] (**) evdev: Power Button: Device: "/dev/input/event2"
[  2391.711] (--) evdev: Power Button: Vendor 0 Product 0x1
[  2391.711] (--) evdev: Power Button: Found keys
[  2391.711] (II) evdev: Power Button: Configuring as keyboard
[  2391.711] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  2391.711] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  2391.711] (**) Option "xkb_rules" "evdev"
[  2391.711] (**) Option "xkb_model" "pc105"
[  2391.711] (**) Option "xkb_layout" "fr"
[  2391.711] (**) Option "xkb_variant" "oss"
[  2391.712] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[  2391.712] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[  2391.713] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  2391.713] (II) Using input driver 'evdev' for 'Video Bus'
[  2391.713] (**) Video Bus: always reports core events
[  2391.713] (**) evdev: Video Bus: Device: "/dev/input/event7"
[  2391.713] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  2391.713] (--) evdev: Video Bus: Found keys
[  2391.713] (II) evdev: Video Bus: Configuring as keyboard
[  2391.713] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event7"
[  2391.713] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  2391.713] (**) Option "xkb_rules" "evdev"
[  2391.713] (**) Option "xkb_model" "pc105"
[  2391.713] (**) Option "xkb_layout" "fr"
[  2391.713] (**) Option "xkb_variant" "oss"
[  2391.713] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  2391.713] (II) No input driver specified, ignoring this device.
[  2391.713] (II) This device may have been added with another device file.
[  2391.713] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[  2391.713] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  2391.713] (II) Using input driver 'evdev' for 'Video Bus'
[  2391.713] (**) Video Bus: always reports core events
[  2391.713] (**) evdev: Video Bus: Device: "/dev/input/event6"
[  2391.713] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  2391.713] (--) evdev: Video Bus: Found keys
[  2391.713] (II) evdev: Video Bus: Configuring as keyboard
[  2391.713] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:44/LNXVIDEO:00/input/input7/event6"
[  2391.713] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[  2391.713] (**) Option "xkb_rules" "evdev"
[  2391.713] (**) Option "xkb_model" "pc105"
[  2391.713] (**) Option "xkb_layout" "fr"
[  2391.713] (**) Option "xkb_variant" "oss"
[  2391.713] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  2391.713] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2391.713] (II) Using input driver 'evdev' for 'Power Button'
[  2391.713] (**) Power Button: always reports core events
[  2391.713] (**) evdev: Power Button: Device: "/dev/input/event1"
[  2391.713] (--) evdev: Power Button: Vendor 0 Product 0x1
[  2391.713] (--) evdev: Power Button: Found keys
[  2391.713] (II) evdev: Power Button: Configuring as keyboard
[  2391.713] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[  2391.713] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[  2391.713] (**) Option "xkb_rules" "evdev"
[  2391.713] (**) Option "xkb_model" "pc105"
[  2391.713] (**) Option "xkb_layout" "fr"
[  2391.713] (**) Option "xkb_variant" "oss"
[  2391.713] (II) config/udev: Adding drm device (/dev/dri/card1)
[  2391.713] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[  2391.714] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event14)
[  2391.714] (II) No input driver specified, ignoring this device.
[  2391.714] (II) This device may have been added with another device file.
[  2391.714] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event15)
[  2391.714] (II) No input driver specified, ignoring this device.
[  2391.714] (II) This device may have been added with another device file.
[  2391.714] (II) config/udev: Adding drm device (/dev/dri/card0)
[  2391.714] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[  2391.714] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:402d (/dev/input/event4)
[  2391.714] (**) Logitech Unifying Device. Wireless PID:402d: Applying InputClass "evdev pointer catchall"
[  2391.714] (**) Logitech Unifying Device. Wireless PID:402d: Applying InputClass "evdev keyboard catchall"
[  2391.714] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:402d'
[  2391.714] (**) Logitech Unifying Device. Wireless PID:402d: always reports core events
[  2391.714] (**) evdev: Logitech Unifying Device. Wireless PID:402d: Device: "/dev/input/event4"
[  2391.714] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Vendor 0x46d Product 0xc52b
[  2391.714] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found 20 mouse buttons
[  2391.714] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found scroll wheel(s)
[  2391.714] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found relative axes
[  2391.714] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found x and y relative axes
[  2391.714] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found keys
[  2391.714] (II) evdev: Logitech Unifying Device. Wireless PID:402d: Configuring as mouse
[  2391.714] (II) evdev: Logitech Unifying Device. Wireless PID:402d: Configuring as keyboard
[  2391.714] (II) evdev: Logitech Unifying Device. Wireless PID:402d: Adding scrollwheel support
[  2391.714] (**) evdev: Logitech Unifying Device. Wireless PID:402d: YAxisMapping: buttons 4 and 5
[  2391.714] (**) evdev: Logitech Unifying Device. Wireless PID:402d: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  2391.714] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004/input/input6/event4"
[  2391.714] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:402d" (type: KEYBOARD, id 10)
[  2391.714] (**) Option "xkb_rules" "evdev"
[  2391.714] (**) Option "xkb_model" "pc105"
[  2391.714] (**) Option "xkb_layout" "fr"
[  2391.714] (**) Option "xkb_variant" "oss"
[  2391.714] (II) evdev: Logitech Unifying Device. Wireless PID:402d: initialized for relative axes.
[  2391.714] (**) Logitech Unifying Device. Wireless PID:402d: (accel) keeping acceleration scheme 1
[  2391.714] (**) Logitech Unifying Device. Wireless PID:402d: (accel) acceleration profile 0
[  2391.714] (**) Logitech Unifying Device. Wireless PID:402d: (accel) acceleration factor: 2.000
[  2391.714] (**) Logitech Unifying Device. Wireless PID:402d: (accel) acceleration threshold: 4
[  2391.714] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:402d (/dev/input/mouse0)
[  2391.714] (II) No input driver specified, ignoring this device.
[  2391.714] (II) This device may have been added with another device file.
[  2391.715] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event9)
[  2391.715] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[  2391.715] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[  2391.715] (**) BisonCam, NB Pro: always reports core events
[  2391.715] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event9"
[  2391.715] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x14c
[  2391.715] (--) evdev: BisonCam, NB Pro: Found keys
[  2391.715] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[  2391.715] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.0/input/input10/event9"
[  2391.715] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 11)
[  2391.715] (**) Option "xkb_rules" "evdev"
[  2391.715] (**) Option "xkb_model" "pc105"
[  2391.715] (**) Option "xkb_layout" "fr"
[  2391.715] (**) Option "xkb_variant" "oss"
[  2391.715] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[  2391.715] (II) No input driver specified, ignoring this device.
[  2391.715] (II) This device may have been added with another device file.
[  2391.715] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event11)
[  2391.715] (II) No input driver specified, ignoring this device.
[  2391.715] (II) This device may have been added with another device file.
[  2391.715] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event12)
[  2391.715] (II) No input driver specified, ignoring this device.
[  2391.715] (II) This device may have been added with another device file.
[  2391.715] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event13)
[  2391.715] (II) No input driver specified, ignoring this device.
[  2391.715] (II) This device may have been added with another device file.
[  2391.715] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  2391.715] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  2391.715] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  2391.715] (**) AT Translated Set 2 keyboard: always reports core events
[  2391.715] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  2391.715] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  2391.715] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  2391.715] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  2391.715] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  2391.715] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[  2391.715] (**) Option "xkb_rules" "evdev"
[  2391.715] (**) Option "xkb_model" "pc105"
[  2391.715] (**) Option "xkb_layout" "fr"
[  2391.715] (**) Option "xkb_variant" "oss"
[  2391.716] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[  2391.716] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  2391.716] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  2391.716] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[  2391.716] (II) LoadModule: "synaptics"
[  2391.716] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  2391.716] (II) Module synaptics: vendor="X.Org Foundation"
[  2391.716]     compiled for 1.15.0, module version = 1.7.4
[  2391.716]     Module class: X.Org XInput Driver
[  2391.716]     ABI class: X.Org XInput driver, version 20.0
[  2391.716] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  2391.716] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  2391.716] (**) Option "Device" "/dev/input/event5"
[  2391.740] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[  2391.740] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692 (res 66)
[  2391.740] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680 (res 102)
[  2391.740] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  2391.740] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  2391.740] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  2391.740] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[  2391.740] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  2391.740] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  2391.752] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[  2391.752] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[  2391.752] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  2391.752] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[  2391.752] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[  2391.752] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  2391.752] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  2391.752] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  2391.752] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  2391.752] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  2391.752] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[  2391.752] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[  2391.753] (II) config/udev: Adding input device MSI WMI hotkeys (/dev/input/event8)
[  2391.753] (**) MSI WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  2391.753] (II) Using input driver 'evdev' for 'MSI WMI hotkeys'
[  2391.753] (**) MSI WMI hotkeys: always reports core events
[  2391.753] (**) evdev: MSI WMI hotkeys: Device: "/dev/input/event8"
[  2391.753] (--) evdev: MSI WMI hotkeys: Vendor 0 Product 0
[  2391.753] (--) evdev: MSI WMI hotkeys: Found keys
[  2391.753] (II) evdev: MSI WMI hotkeys: Configuring as keyboard
[  2391.753] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event8"
[  2391.753] (II) XINPUT: Adding extended input device "MSI WMI hotkeys" (type: KEYBOARD, id 14)
[  2391.753] (**) Option "xkb_rules" "evdev"
[  2391.753] (**) Option "xkb_model" "pc105"
[  2391.753] (**) Option "xkb_layout" "fr"
[  2391.753] (**) Option "xkb_variant" "oss"
[  2391.767] (II) intel(G0): EDID vendor "CMO", prod id 5920
[  2391.767] (II) intel(G0): Printing DDC gathered Modelines:
[  2391.768] (II) intel(G0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[  2391.768] reporting 8 6 17 132
[  2391.789] reporting 8 6 17 132
[  2391.792] reporting 8 6 17 132
[  2391.792] have a master to look out for
[  2391.792] need to create shared pixmap 1reporting 8 6 16 132
[  2392.866] have a master to look out for
[  2392.866] adjust shatters 0 1920
[  2392.868] need to create shared pixmap 1(II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  2393.195] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[  2393.321] reporting 8 6 16 132
[  2393.337] reporting 8 6 16 132
[  2393.425] reporting 8 6 16 132
[  2393.436] reporting 8 6 16 132
[  2393.449] reporting 8 6 16 132
[  2393.458] reporting 8 6 16 132
[  2393.467] reporting 8 6 16 132
[  2393.472] reporting 8 6 16 132
[  2393.493] reporting 8 6 16 132
[  2393.496] reporting 8 6 16 132
[  2393.536] reporting 8 6 16 132
[  2393.556] reporting 8 6 16 132
[  2393.563] reporting 8 6 16 132
[  2393.959] reporting 8 6 16 132
[  2394.181] reporting 8 6 16 132
[  2394.417] reporting 8 6 16 132
[  2394.426] reporting 8 6 16 132
[  2394.461] reporting 8 6 16 132
[  2394.657] reporting 8 6 16 132
[  2394.914] reporting 8 6 16 132
[  2395.254] reporting 8 6 16 132
[  2395.347] reporting 8 6 16 132
[  2395.874] reporting 8 6 16 132
[  2398.386] reporting 8 6 16 132
[  2398.481] reporting 8 6 16 132
[  2398.525] reporting 8 6 16 132
[  2398.534] reporting 8 6 16 132
[  2398.676] reporting 8 6 16 132
[  2398.832] reporting 8 6 16 132
[  2398.934] reporting 8 6 16 132
[  2399.018] reporting 8 6 16 132
[  2399.090] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[  2399.097] reporting 8 6 16 132
[  2399.108] reporting 8 6 16 132
[  2399.121] reporting 8 6 16 132
[  2399.139] reporting 8 6 16 132
[  2399.184] reporting 8 6 16 132
[  2399.208] reporting 8 6 16 132
[  2399.225] reporting 8 6 16 132
[  2399.263] reporting 8 6 16 132
[  2399.376] reporting 8 6 16 132
[  2399.409] reporting 8 6 16 132
[  2399.411] reporting 8 6 16 132
[  2399.732] reporting 8 6 16 132
[  2399.747] reporting 8 6 16 132
[  2399.768] reporting 8 6 16 132
[  2399.790] reporting 8 6 16 132
[  2399.821] reporting 8 6 16 132
[  2399.831] reporting 8 6 16 132
[  2399.845] reporting 8 6 16 132
[  2399.903] reporting 8 6 16 132
[  2400.131] reporting 8 6 16 132
[  2400.213] reporting 8 6 16 132
[  2400.220] reporting 8 6 16 132
[  2400.496] reporting 8 6 16 132
[  2530.845] reporting 8 6 16 132
[  2569.184] reporting 8 6 16 132
[  2616.153] reporting 8 6 16 132
[  2813.399] reporting 8 6 16 132
[  2836.947] reporting 8 6 16 132
[  2844.394] reporting 8 6 16 132
[  2853.693] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  2853.725] reporting 8 6 16 132
[  2853.747] (II) NVIDIA(0): Setting mode "NULL"
[  2853.768] (II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  2853.798] setversion 1.4 failed: Permission denied
[  2853.979] reporting 8 6 16 132
[  2947.687] reporting 8 6 16 132
[  2947.703] reporting 8 6 16 132
[  2947.879] reporting 8 6 16 132
[  2947.900] reporting 8 6 16 132
[  3111.711] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  3111.760] reporting 8 6 16 132
[  3111.784] (II) NVIDIA(0): Setting mode "NULL"
[  3111.802] (II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  3111.830] setversion 1.4 failed: Permission denied
[  3111.990] reporting 8 6 16 132
[  3302.034] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  3302.079] reporting 8 6 16 132
[  3302.100] (II) NVIDIA(0): Setting mode "NULL"
[  3302.119] (II) intel(G0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[  3302.281] reporting 8 6 16 132
[  3303.485] (WW) synaptics: SynPS/2 Synaptics TouchPad: can't grab event device, errno=16
[  3303.496] [dix] couldn't enable device 13
[  3312.086] (EE) 
[  3312.086] (EE) Backtrace:
[  3312.086] (EE) 0: /usr/bin/X (xorg_backtrace+0x48) [0x7fb729d5cc78]
[  3312.086] (EE) 1: /usr/bin/X (0x7fb729bb4000+0x1ac969) [0x7fb729d60969]
[  3312.086] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fb728cb1000+0x10340) [0x7fb728cc1340]
[  3312.086] (EE) 3: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fb721b00000+0xb774e) [0x7fb721bb774e]
[  3312.086] (EE) 4: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fb721b00000+0x5685d) [0x7fb721b5685d]
[  3312.086] (EE) 5: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fb721b00000+0x8f8ea) [0x7fb721b8f8ea]
[  3312.086] (EE) 6: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7fb721b00000+0x546df6) [0x7fb722046df6]
[  3312.086] (EE) 7: /usr/bin/X (RRCrtcDetachScanoutPixmap+0x6a) [0x7fb729cc524a]
[  3312.086] (EE) 8: /usr/bin/X (0x7fb729bb4000+0xd30e8) [0x7fb729c870e8]
[  3312.086] (EE) 9: /usr/bin/X (0x7fb729bb4000+0xd31ac) [0x7fb729c871ac]
[  3312.086] (EE) 10: /usr/bin/X (0x7fb729bb4000+0x117f42) [0x7fb729ccbf42]
[  3312.086] (EE) 11: /usr/bin/X (0x7fb729bb4000+0x77f92) [0x7fb729c2bf92]
[  3312.087] (EE) 12: /usr/bin/X (FreeClientResources+0x6c) [0x7fb729c2cfbc]
[  3312.087] (EE) 13: /usr/bin/X (FreeAllResources+0x47) [0x7fb729c2d067]
[  3312.087] (EE) 14: /usr/bin/X (0x7fb729bb4000+0x5997e) [0x7fb729c0d97e]
[  3312.087] (EE) 15: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7fb7276f0ec5]
[  3312.087] (EE) 16: /usr/bin/X (0x7fb729bb4000+0x44e7e) [0x7fb729bf8e7e]
[  3312.087] (EE) 
[  3312.087] (EE) Segmentation fault at address 0x30
[  3312.087] (EE) 
Fatal server error:
[  3312.087] (EE) **Caught signal 11 (Segmentation fault). Server aborting**
[  3312.087] (EE) 
[  3312.087] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  3312.087] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3312.087] (EE) 
[  3312.087] (EE) Server terminated with error (1). Closing log file.


```

pm-suspend:
```

Initial commandline parameters: --quirk-save-pci
Fri Jul 25 03:10:42 CEST 2014: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.

Running hook /etc/pm/sleep.d/00_check_touchpad_status suspend suspend:
/etc/pm/sleep.d/00_check_touchpad_status suspend suspend: not executable.

Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kwaadpepper-laptop 3.15.6-031506-generic #201407172034 SMP Fri Jul 18 00:36:12 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
alx                    41397  0 
mdio                   13561  1 alx
ctr                    13193  2 
ccm                    17856  2 
snd_hrtimer            12744  1 
bbswitch               13943  0 
bnep                   19884  2 
rfcomm                 75078  12 
binfmt_misc            17508  1 
snd_hda_codec_hdmi     48290  1 
snd_hda_codec_realtek    72575  1 
snd_hda_codec_generic    70087  1 snd_hda_codec_realtek
nvidia              10675219  39 
arc4                   12573  2 
snd_hda_intel          30683  10 
snd_hda_controller     35518  1 snd_hda_intel
uvcvideo               82299  0 
snd_hda_codec         144671  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
x86_pkg_temp_thermal    14312  0 
snd_hwdep              13613  1 snd_hda_codec
ath9k                 147545  0 
videobuf2_vmalloc      13216  1 uvcvideo
intel_powerclamp       19099  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         45435  1 uvcvideo
kvm_intel             148919  0 
ath9k_common           15984  1 ath9k
ath3k                  13381  0 
videodev              149504  2 uvcvideo,videobuf2_core
ath9k_hw              459576  2 ath9k_common,ath9k
btusb                  32555  0 
kvm                   463855  1 kvm_intel
bluetooth             461911  23 bnep,ath3k,btusb,rfcomm
snd_pcm               113863  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
ath                    29397  3 ath9k_common,ath9k,ath9k_hw
snd_seq_midi           13564  0 
6lowpan_iphc           18968  1 bluetooth
snd_seq_midi_event     14899  1 snd_seq_midi
crct10dif_pclmul       14268  0 
snd_rawmidi            30865  1 snd_seq_midi
crc32_pclmul           13180  0 
ghash_clmulni_intel    13230  0 
mac80211              663788  1 ath9k
snd_seq                67636  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              30118  3 snd_hrtimer,snd_pcm,snd_seq
aesni_intel           152648  5 
snd                    74235  32 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
aes_x86_64             17131  1 aesni_intel
lrw                    13323  1 aesni_intel
cfg80211              514187  4 ath,ath9k_common,ath9k,mac80211
soundcore              12680  2 snd,snd_hda_codec
gf128mul               14951  1 lrw
glue_helper            14095  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20531  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mei_me                 18562  0 
joydev                 17587  0 
rtsx_pci_ms            18337  0 
mei                    87522  1 mei_me
serio_raw              13483  0 
memstick               16968  1 rtsx_pci_ms
lpc_ich                21176  0 
msi_wmi                13354  0 
sparse_keymap          13890  1 msi_wmi
mxm_wmi                13021  0 
wmi                    19379  2 msi_wmi,mxm_wmi
mac_hid                13275  0 
parport_pc             32906  0 
ppdev                  17711  0 
coretemp               13638  0 
lp                     17799  0 
parport                42481  3 lp,ppdev,parport_pc
hid_generic            12559  0 
hid_logitech_dj        18647  0 
usbhid                 53121  0 
hid                   106436  4 hid_generic,usbhid,hid_logitech_dj
rtsx_pci_sdmmc         23482  0 
i915                  877764  2 
psmouse               113095  0 
i2c_algo_bit           13564  1 i915
drm_kms_helper         59729  1 i915
ahci                   30167  5 
libahci                32191  1 ahci
drm                   310655  6 i915,drm_kms_helper,nvidia
rtsx_pci               46393  2 rtsx_pci_ms,rtsx_pci_sdmmc
video                  19932  1 i915
             total       used       free     shared    buffers     cached
Mem:      16351488    3498668   12852820      31676     149448    1324300
-/+ buffers/cache:    2024920   14326568
Swap:      3905532          0    3905532
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
/etc/pm/sleep.d/10_grub-common suspend suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
Unloading alx kernel module ...
Done.
/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0
/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.

Fri Jul 25 03:10:42 CEST 2014: performing suspend
Fri Jul 25 03:10:48 CEST 2014: Awake.
Fri Jul 25 03:10:48 CEST 2014: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:
Reloading alx kernel module ...
/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.

Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
/etc/pm/sleep.d/10_grub-common resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.

Running hook /etc/pm/sleep.d/00_check_touchpad_status resume suspend:
/etc/pm/sleep.d/00_check_touchpad_status resume suspend: not executable.

Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.

Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

Fri Jul 25 03:10:49 CEST 2014: Finished.


```

on syslog
```

Jul 25 03:10:42 localhost kernel: [ 3297.921873] PM: Syncing filesystems ... done.
Jul 25 03:10:42 localhost kernel: [ 3297.925461] PM: Preparing system for mem sleep
Jul 25 03:10:48 localhost kernel: [ 3298.100690] PM: Entering mem sleep
Jul 25 03:10:48 localhost kernel: [ 3298.627301] PM: suspend of devices complete after 526.468 msecs
Jul 25 03:10:48 localhost kernel: [ 3298.643319] PM: late suspend of devices complete after 16.021 msecs
Jul 25 03:10:48 localhost kernel: [ 3298.659323] PM: noirq suspend of devices complete after 16.006 msecs
Jul 25 03:10:48 localhost kernel: [ 3298.669643] PM: Saving platform NVS memory
Jul 25 03:10:48 localhost kernel: [ 3299.301858] PM: Restoring platform NVS memory
Jul 25 03:10:48 localhost kernel: [ 3299.437417] PM: noirq resume of devices complete after 16.500 msecs
Jul 25 03:10:48 localhost kernel: [ 3299.437698] PM: early resume of devices complete after 0.260 msecs
Jul 25 03:10:48 localhost kernel: [ 3300.815012] **PM: Device 3-8 failed to resume async: error -32**
Jul 25 03:10:48 localhost kernel: [ 3300.815158] PM: resume of devices complete after 1377.879 msecs
Jul 25 03:10:48 localhost kernel: [ 3300.828234] PM: Finishing wakeup.


```

So it's a Sigsegment error, also **PM: Device 3-8 failed to resume async: error -32**, have to find that errorNo in docs
For now Iam gonna reinstall nvidia drivers

Cheers

EDIT:

I just reinstalled lastest nvidia driver from xedger ppa. It still fails, after resume i ran into kde lockscreen and when i log in xorg crash.

---

