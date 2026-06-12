---
title: "Mobo asus p5ql pro bios"
date: 2010-02-18
forum: Hardware
---

### Post by isosi on 2010-02-18
I am interesting if i need too do something with bios dsdt table for
Asus p5ql pro motherboard? 

I am 100% sure that there are some few "not special msft" errors. How to find out if i have some issues that is coming from dsdt and what to do if i have?

---

### Post by isosi on 2010-03-05
P5QL PRO BIOS 1004   in another words v 10.4 (for more details dmidecode output  will follow in another post)


For direction on using dsdt I used [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

dsdt table obtained by 

sudo cat /proc/acpi/dsdt > dsdt.dat 

If somebody know how to obtain dsdt table directly from BIOS rom file, then you are welcome to share your ideas ;) 
Because dsdt table (i think but not sure 100%) is preprocessed during boot and may have some value that depends on ram size and another connected devices.

some ideas how to "fix" warnings, remarks that are following below, will be in next post.  

iasl -tc  dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2621:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  2702:                             Name (_T_1, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

dsdt.dsl  2736:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  2802:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  2872:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  5598:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  5614:                 Name (_T_0, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_0)

dsdt.dsl  5708:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  5807:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6401:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6430:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6484:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6498:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6617:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6687:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6778:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6792:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6886:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6928:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  6932:                 Name (_T_1, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_1)

dsdt.dsl  7128:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  7191:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  7291:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  7314:             Name (_T_0, Zero)
Remark   5110 -                      ^ Use of compiler reserved name (_T_0)

dsdt.dsl  7370:                 Name (_T_0, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_0)

dsdt.dsl  7416:                 Name (_T_1, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_1)

dsdt.dsl  7961:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  7975:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  7990:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8005:             Acquire (MUTE, 0x0FFF)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8019:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8034:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8049:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  9009:         Method (VGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (VGET)

dsdt.dsl  9054:         Method (TGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (TGET)

dsdt.dsl  9098:         Method (FGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (FGET)

dsdt.dsl  9124:             Store (VGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl  9166:             Store (TGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl  9199:             Store (FGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

ASL Input:  dsdt.dsl - 9430 lines, 305182 bytes, 4333 keywords
AML Output: dsdt.aml - 34952 bytes, 939 named objects, 3394 executable opcodes

Compilation complete. 0 Errors, 13 Warnings, 26 Remarks, 67 Optimizations

---

### Post by isosi on 2010-03-05
sudo dmidecode > dmidecode.txt

# dmidecode 2.9
SMBIOS 2.5 present.
62 structures occupying 2309 bytes.
Table at 0x000F0710.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 1004   
    Release Date: 07/01/2009
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 1024 kB
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
        3.5"/720 KB floppy services are supported (int 13h)
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
    BIOS Revision: 10.4

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: System manufacturer
    Product Name: P5QL PRO
    Version: System Version
    Serial Number: System Serial Number
    UUID:  removed from post information 
    Wake-up Type: Power Switch
    SKU Number: To Be Filled By O.E.M.
    Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: P5QL PRO
    Version: Rev 1.xx
    Serial Number: MS1C88B83402632
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: Chassis Manufacture
    Type: Desktop
    Lock: Not Present
    Version: Chassis Version
    Serial Number: Chassis Serial Number
    Asset Tag: Asset-1234567890
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000011
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
    Socket Designation: LGA775
    Type: Central Processor
    Family: <OUT OF SPEC>
    Manufacturer: Intel            
    ID: 77 06 01 00 FF FB EB BF
    Version: Intel(R) Core(TM)2 Quad CPU Q8200 @ 2.33GHz         
    Voltage: 1.2 V
    External Clock: 333 MHz
    Max Speed: 3800 MHz
    Current Speed: 2333 MHz
    Status: Populated, Enabled
    Upgrade: Other
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.
    Core Count: 4
    Core Enabled: 4
    Thread Count: 4
    Characteristics:
        64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 128 KB
    Maximum Size: 128 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Parity
    System Type: Data
    Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 4096 KB
    Maximum Size: 4096 KB
    Supported SRAM Types:
        Other
    Installed SRAM Type: Other
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L3-Cache
    Configuration: Disabled, Not Socketed, Level 3
    Operational Mode: Unknown
    Location: Internal
    Installed Size: 0 KB
    Maximum Size: 0 KB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0008, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Keyboard
    Internal Connector Type: None
    External Reference Designator: PS/2 Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Mouse
    Internal Connector Type: None
    External Reference Designator: PS/2 Mouse
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB12
    Internal Connector Type: None
    External Reference Designator: USB12
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB34
    Internal Connector Type: None
    External Reference Designator: USB34
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB56
    Internal Connector Type: None
    External Reference Designator: USB56
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: GbE LAN
    Internal Connector Type: None
    External Reference Designator: GbE LAN
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM 1
    Internal Connector Type: None
    External Reference Designator: COM 1
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SPDIF_OUT
    Internal Connector Type: None
    External Reference Designator: SPDIF_OUT
    External Connector Type: On Board Sound Input From CD-ROM
    Port Type: Audio Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SPDIF_O1
    Internal Connector Type: None
    External Reference Designator: SPDIF_O1
    External Connector Type: On Board Sound Input From CD-ROM
    Port Type: Audio Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Line In
    Internal Connector Type: None
    External Reference Designator: Audio_Line In
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Line Out
    Internal Connector Type: None
    External Reference Designator: Audio_Line Out
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Mic In
    Internal Connector Type: None
    External Reference Designator: Audio_Mic In
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Center/LFE
    Internal Connector Type: None
    External Reference Designator: Audio_Center/LFE
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Surround OUT
    Internal Connector Type: None
    External Reference Designator: Audio_Surround OUT
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Audio_Surround Back
    Internal Connector Type: None
    External Reference Designator: Audio_Surround Back
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA1
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA2
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA3
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA4
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA5
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SATA6
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PRI_EIDE
    Internal Connector Type: SAS/SATA Plug Receptacle
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: SATA

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB78
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB910
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB1112
    Internal Connector Type: Access Bus (USB)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: USB

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: FLOPPY
    Internal Connector Type: On Board Floppy
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CD
    Internal Connector Type: On Board Sound Input From CD-ROM
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Audio Port

Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: AAFP
    Internal Connector Type: Mini Jack (headphones)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Audio Port

Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CPU_FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0025, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PWR_FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0026, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: CHA_FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0027, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIEX16
    Type: 32-bit PCI Express
    Current Usage: In Use
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0028, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIEX1_1
    Type: 64-bit PCI Express
    Current Usage: In Use
    Length: Short
    ID: 8
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0029, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIEX1_2
    Type: 32-bit PCI Express
    Current Usage: Available
    Length: Short
    ID: 9
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x002A, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI_1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x002B, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI_2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 3
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x002C, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI_3
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 4
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x002D, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description:  Onboard Ethernet

Handle 0x002E, DMI type 11, 5 bytes
OEM Strings
    String 1: 0022159BB79C
    String 2: To Be Filled By O.E.M.
    String 3: To Be Filled By O.E.M.
    String 4: To Be Filled By O.E.M.

Handle 0x002F, DMI type 12, 5 bytes
System Configuration Options
    Option 1: To Be Filled By O.E.M.

Handle 0x0030, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x0031, DMI type 15, 55 bytes
System Event Log
    Area Length: 1008 bytes
    Header Start Offset: 0x2010
    Data Start Offset: 0x2010
    Access Method: OEM-specific
    Access Address: Unknown
    Status: Valid, Not Full
    Change Token: 0x00000000
    Header Format: No Header
    Supported Log Type Descriptors: 1
    Descriptor 1: OEM-specific
    Data Format 1: POST results bitmap

Handle 0x0032, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x0033, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Array Handle: 0x0032
    Partition Width: 0

Handle 0x0034, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: DDR
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x0035, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x0034
    Memory Array Mapped Address Handle: 0x0033
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x0036, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

Handle 0x0037, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000003FF
    Range Size: 1 kB
    Physical Device Handle: 0x0036
    Memory Array Mapped Address Handle: 0x0033
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x0038, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM2
    Bank Locator: BANK2
    Type: DDR
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: Manufacturer2
    Serial Number: SerNum2
    Asset Tag: AssetTagNum2
    Part Number: PartNum2

Handle 0x0039, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00044000000
    Ending Address: 0x00083FFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x0038
    Memory Array Mapped Address Handle: 0x0033
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x003A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0032
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM3
    Bank Locator: BANK3
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Manufacturer3
    Serial Number: SerNum3
    Asset Tag: AssetTagNum3
    Part Number: PartNum3

Handle 0x003B, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000000003FF
    Range Size: 1 kB
    Physical Device Handle: 0x003A
    Memory Array Mapped Address Handle: 0x0033
    Partition Row Position: 1
    Interleaved Data Depth: 1

Handle 0x003C, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x003D, DMI type 127, 4 bytes
End Of Table

---

### Post by isosi on 2010-03-05
dsdt.dsl  2621:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

and

dsdt.dsl  2702:                             Name (_T_1, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

this kind remarks i decided to fix simple by text editor replacing all
wariants "_T_0" to "T_0" and "_T_1" to "T_1" in the file dsdt.dsl

this kind warnings :
dsdt.dsl  7961:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator  timeout is ignored

i decided to fix by replacing (MUTE, 0x0xxx) to (MUTE, 0xFFFF)

according to  very interesting post  [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249) (**A possible bug in Foxconn boards BIOS affects Linux ACPI**)
This post   was very interesting to read and  realize about manufacture support, that Einstein was true by stating "Only two things are infinite, the universe and human stupidity, and I'm  not sure about the former." [http://en.wikiquote.org/wiki/Stupidity](http://en.wikiquote.org/wiki/Stupidity)   and all consequences that go out of that.

---

