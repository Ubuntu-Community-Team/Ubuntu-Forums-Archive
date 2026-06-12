---
title: "Booting USB pendrive without BIOS support"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Spaceman9 on 2009-11-06
I used the Ubuntu 9.10 live cd to install Ubuntu into an 8GB pendrive. The problem is my BIOS was made in 2000 and doesn't support booting a USB pendrive. Does anyone know if there's anyway to boot a pendrive when BIOS doesn't support it? Thanks for any help.

---

### Post by juliopjuliop on 2009-11-06
Actually yes there is, its an excellent little thing called PLoP, wich is a bootloader that loads usb drivers and boots up the first usb storage device found, unfortunately this also means you should have only 1 usb storage device in as it will boot up the one you want.

Well onto the install, you would need to burn this to a cd for optimal results. Heres a link: [http://www.plop.at/en/bootmanagerdl.html]("http://www.plop.at/en/bootmanagerdl.html") just download the one at the top called plpbt-5.0.4.zip unpack it, there should be a file called plpbtin.iso and 2 other isos, ive personally had plpbtin.iso bootup all of the machines ive tried it on perfectly, so i recommend you burn that one to a cd. next step is as simple as setting bios to boot off cd and PLoP will load up, use the arrow keys to select the usb option and press enter, it should proceed to scan for usb storage drives and boot it up. Good luck.

---

### Post by Spaceman9 on 2009-11-07
I burned plpbtin.iso to a CD and it found Ubuntu in the USB pendrive and Ubuntu booted and the Ubuntu icon got bright and dim 4 times and the screen went black. I waited 3 minutes and nothing else happened. May be it's just because I'm using a computer I built in 2001 and I need newer hardware. 

Ubuntu 9.10 works fine from the Live CD though.

---

### Post by Herman on 2009-11-07
:D I found it was the plpbt.iso and not the plpbtin.iso that I needed to burn to disc to get a disk that allows one to use the arrow keys to select the usb option and press enter.

I was impressed that booting with plpbt.iso allowed me to boot GRUB2 in the MBR of my USB external SSD drive. 

Sadly though, GRUB2 was not able to subsequently boot Karmic, failing with the error message:
> error: biosdisk write error
press any key to continue ..._That's better than I though possible with this computer, I've never been able to boot the MBR of a USB drive at all with this particular computer until now.
I think plop boot manager seems like it has a lot of potential, I hope it's developers will keep up their good work.  

In case it's useful to anyone, here are my system specs by the output of dmidecode,
```
sudo dmidecode
``````
# dmidecode 2.9
SMBIOS 2.3 present.
46 structures occupying 1682 bytes.
Table at 0x000F0740.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 0301   
    Release Date: 07/31/2006
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 512 kB
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

Handle 0x0001, DMI type 1, 25 bytes
System Information
    Manufacturer: System manufacturer
    Product Name: System Product Name
    Version: System Version
    Serial Number: System Serial Number
    UUID: E0958FC7-75FE-D511-A33A-2B5551A96CF9
    Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: M2V-TVM
    Version: Rev 1.xx
    Serial Number: MB-1234567890

Handle 0x0003, DMI type 3, 17 bytes
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
    OEM Information: 0x00000003

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: CPU 1
    Type: Central Processor
    Family: Unknown
    Manufacturer: AMD              
    ID: F2 0F 05 00 FF FB 8B 07
    Version: AMD Athlon(tm) 64 Processor 3500+                   
    Voltage: 1.5 V
    External Clock: 200 MHz
    Max Speed: 2200 MHz
    Current Speed: 2200 MHz
    Status: Populated, Enabled
    Upgrade: Unknown
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: 0x0007
    Serial Number: To Be Filled By O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Part Number: To Be Filled By O.E.M.

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1-Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 64 KB
    Maximum Size: 64 KB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 4-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2-Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 512 KB
    Maximum Size: 512 KB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 4-way Set-associative

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
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: PS2Mouse
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0009, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1A1
    Internal Connector Type: None
    External Reference Designator: Keyboard
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2
    Internal Connector Type: None
    External Reference Designator: USB1
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A2
    Internal Connector Type: None
    External Reference Designator: USB2
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J4A1
    Internal Connector Type: None
    External Reference Designator: LPT 1
    External Connector Type: DB-25 male
    Port Type: Parallel Port ECP/EPP

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2A1
    Internal Connector Type: None
    External Reference Designator: COM A
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6A1
    Internal Connector Type: None
    External Reference Designator: Audio Mic In
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6A1
    Internal Connector Type: None
    External Reference Designator: Audio Line In
    External Connector Type: Mini Jack (headphones)
    Port Type: Audio Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6B1 - AUX IN
    Internal Connector Type: On Board Sound Input From CD-ROM
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Audio Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6B2 - CDIN
    Internal Connector Type: On Board Sound Input From CD-ROM
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Audio Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6J2 - PRI IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6J1 - SEC IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J4J1 - FLOPPY
    Internal Connector Type: On Board Floppy
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9H1 - FRONT PNL
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J1B1 - CHASSIS REAR FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2F1 - CPU FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J8B4 - FRONT FAN
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9G2 - FNT USB
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J6C3 - FP AUD
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9G1 - CONFIG
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J8C1 - SCSI LED
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9J2 - INTRUDER
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J9G4 - ITP
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: J2H1 - MAIN POWER
    Internal Connector Type: Other
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x0020, DMI type 9, 13 bytes
System Slot Information
    Designation: AGP
    Type: 32-bit AGP 4x
    Current Usage: Available
    Length: Short
    ID: 0
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0021, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0022, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 2
    Characteristics:
        3.3 V is provided
        Opening is shared
        PME signal is supported

Handle 0x0023, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:   To Be Filled By O.E.M.

Handle 0x0024, DMI type 11, 5 bytes
OEM Strings
    String 1: To Be Filled By O.E.M.
    String 2: To Be Filled By O.E.M.
    String 3: To Be Filled By O.E.M.
    String 4: To Be Filled By O.E.M.

Handle 0x0025, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x0026, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 8 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0027, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Array Handle: 0x0026
    Partition Width: 0

Handle 0x0028, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0026
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 72 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x0029, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x0028
    Memory Array Mapped Address Handle: 0x0027
    Partition Row Position: 1

Handle 0x002A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0026
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 72 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: DDR
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

Handle 0x002B, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00040000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x002A
    Memory Array Mapped Address Handle: 0x0027
    Partition Row Position: 1

Handle 0x002C, DMI type 32, 20 bytes
System Boot Information
    Status: No errors detected

Handle 0x002D, DMI type 127, 4 bytes
End Of Table

```

---

### Post by kontokuby on 2009-11-07
I've just managed to start xubuntu 9.10 from usb hard drive on a pc without bios usb boot option. Plop is the way to go, but unfortunately grub overloaded with features does some problems (biosdisk write error).
Reading this thread:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784)
inspired me to edit /boot/grub/grub.cfg and hash first two lines of the ubuntu loading section ('recordfail=1' and 'if [...] save_env recordfail ...') and it worked. It'll work only until the next grub config update, but I'm not planning any, since it's a portable drive used only for that purpose.
I'm not giving exact instructions because none of the developers would recommend editing grub.cfg... Although I hardly understand why they make it all so complicated..? It ought to be just a bootloader and as far as I understand those scripts, this recordfail thing is just to change the grub timer off or 10s wait or something close to this..

---

