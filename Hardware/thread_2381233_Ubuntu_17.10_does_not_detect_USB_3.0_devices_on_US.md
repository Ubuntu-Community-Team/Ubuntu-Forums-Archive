---
title: "Ubuntu 17.10 does not detect USB 3.0 devices on USB 3.0 port"
date: 2017-12-28
forum: Hardware
---

### Post by Matematik on 2017-12-28
Just did a fresh install of Ubuntu 17.10, was previously on 16.04. For some reason USB 3 port no longer detects USB  3 devices. Old USB 2 drives seem to work on that port. When I plug in an external hard drive it starts spinning and the  light turns on, but I don't see any traces of the drive in the  filesystem. No /var/log/syslog activity either. The drives that don't work are NTFS formatted.

  ```

$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

$ lsusb -t
Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M

```

  USB 2 ports on my laptop are working fine.

Any suggestion suggestions on how to debug or fix this?

---

### Post by QIII on 2017-12-28
Hello!

Could you provide the specs on your machine?

---

### Post by Matematik on 2017-12-28
Absolutely, here are the specs:

[FONT=lucida console]```

$ sudo dmidecode -q
BIOS Information
    Vendor: American Megatrends Inc.
    Version: S400CA.206
    Release Date: 11/28/2012
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 6144 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
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
        ACPI is supported
        USB legacy is supported
        Smart battery is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 4.6

System Information
    Manufacturer: ASUSTeK COMPUTER INC.
    Product Name: S400CA
    Version: 1.0       
    Serial Number: D1N0BC083244038     
    UUID: 00009F3D-17DE-1A08-FFFF-50465D45949C
    Wake-up Type: Power Switch
    SKU Number: ASUS-NotebookSKU
    Family: S

Base Board Information
    Manufacturer: ASUSTeK COMPUTER INC.
    Product Name: S400CA
    Version: 1.0       
    Serial Number: BSN12345678901234567
    Asset Tag: ATN12345678901234567
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: MIDDLE              
    Type: Motherboard

Chassis Information
    Manufacturer: ASUSTeK COMPUTER INC.
    Type: Notebook
    Lock: Not Present
    Version: 1.0       
    Serial Number: D1N0BC083244038     
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

On Board Device 1 Information
    Type: Video
    Status: Enabled
    Description:  VGA
On Board Device 2 Information
    Type: Ethernet
    Status: Enabled
    Description:  GLAN
On Board Device 3 Information
    Type: Ethernet
    Status: Enabled
    Description:  WLAN
On Board Device 4 Information
    Type: Sound
    Status: Enabled
    Description:  Audio CODEC 
On Board Device 5 Information
    Type: SATA Controller
    Status: Enabled
    Description:  SATA Controller
On Board Device 6 Information
    Type: Other
    Status: Enabled
    Description:  USB 2.0 Controller
On Board Device 7 Information
    Type: Other
    Status: Enabled
    Description:  USB 3.0 Controller
On Board Device 8 Information
    Type: Other
    Status: Enabled
    Description:  SMBus Controller
On Board Device 9 Information
    Type: Other
    Status: Enabled
    Description:  Card Reader
On Board Device 10 Information
    Type: Other
    Status: Enabled
    Description:  Cmos Camera
On Board Device 11 Information
    Type: Other
    Status: Enabled
    Description:  Bluetooth

OEM Strings
    String 1: krZ+cZtuhuHmq
    String 2: 7cr6l5Gk48H6m
    String 3: 6dg5QA96vC7HW
    String 4: 90NB0051-M03010
    String 5:  
    String 6:  
    String 7:  
    String 8:  
    String 9:  
    String 10:  

System Configuration Options
    Option 1: DSN:      ET583194ZCM9R0            
    Option 2: DSN:C94954D56405                    
    Option 3: DSN:50465D45949C                    
    Option 4: SMI:00B2CA

System Boot Information
    Status: No errors detected

Cache Information
    Socket Designation: CPU Internal L2
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 512 kB
    Maximum Size: 512 kB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: Multi-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Cache Information
    Socket Designation: CPU Internal L1
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 128 kB
    Maximum Size: 128 kB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: Parity
    System Type: Data
    Associativity: 8-way Set-associative

Cache Information
    Socket Designation: CPU Internal L3
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

Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 32 GB
    Number Of Devices: 4

Processor Information
    Socket Designation: SOCKET 0
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
    Voltage: 1.7 V
    External Clock: 100 MHz
    Max Speed: 3800 MHz
    Current Speed: 1700 MHz
    Status: Populated, Enabled
    Upgrade: Socket rPGA988B
    Serial Number: Not Specified
    Asset Tag: Fill By OEM
    Part Number: Fill By OEM
    Core Count: 2
    Core Enabled: 2
    Thread Count: 4
    Characteristics:
        64-bit capable

Memory Device
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MT/s
    Manufacturer: Micron
    Serial Number: 00000000
    Asset Tag: 9876543210
    Part Number: 8JTF5126 4HZ1G6D 1
    Rank: 1
    Configured Clock Speed: 1333 MT/s

Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 4 GB
    Partition Row Position: Unknown
    Interleave Position: 1
    Interleaved Data Depth: 2

Memory Device
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: ChannelA-DIMM1
    Bank Locator: BANK 1
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 9876543210
    Part Number: [Empty]
    Rank: Unknown
    Configured Clock Speed: Unknown

Memory Device
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelB-DIMM0
    Bank Locator: BANK 2
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MT/s
    Manufacturer: 04CD
    Serial Number: 00000000
    Asset Tag: 9876543210
    Part Number: F3-12800CL9-4GBSQ
    Rank: 1
    Configured Clock Speed: 1333 MT/s

Memory Device Mapped Address
    Starting Address: 0x00100000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 4 GB
    Partition Row Position: Unknown
    Interleave Position: 2
    Interleaved Data Depth: 2

Memory Device
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: ChannelB-DIMM1
    Bank Locator: BANK 3
    Type: Unknown
    Type Detail: None
    Speed: Unknown
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Asset Tag: 9876543210
    Part Number: [Empty]
    Rank: Unknown
    Configured Clock Speed: Unknown

Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 8 GB
    Partition Width: 4

BIOS Language Information
    Language Description Format: Long
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

```
[/FONT]

---

