---
title: "New NIC: which pci slot?"
date: 2017-09-08
forum: Hardware
---

### Post by outofnicks on 2017-09-08
The onboard ethernet in my custom-built tower was zapped by lightning so I'm in the market for a network card for direct cable connection.
I have two PCI slots available, not sure which one is best?

The uppermost one is a PCI Expresss 32-bit short length, with 11 pins in one group and 7 pins in the other. There is another one identical to this, but it's blocked by the graphics card so doesn't count.

The second one is at the bottom, with 49 pins + 11 pins. There is not a label on the motherboard for it that I can see. Curious about that, as I have an old network card that fits in this slot, but it isn't working. The  green exterior light comes on, and an orange light is on when a cable is connected. But ifconfig only shows localhost. It's a CNet Pro200WL. It came out of my Dell 4400 which I ran Linux on for many years before putting this tower together, and I believe it was working, or I was using the onboard ethernet...can't remember :confuse

So I'm off to ebay looking, and wondering...I see the short length pin groups most on ebay, many for less than $10 USD and I have read that Intel cards are the best bet.

Would a PCIex1 NIC be plug-and-play, or would I have to search for drivers? 
Would the 49+11 slot be better for some reason? I'd like to get the old NIC going until I get a new one if possible. Any pointers are appreciated!

Here's all the info on my box if it's any help:

```
Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: American Megatrends Inc.
        Version: 0209   
        Release Date: 12/10/2010
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
        BIOS Revision: 8.14

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: System manufacturer
        Product Name: System Product Name
        Version: System Version
        Serial Number: System Serial Number
        UUID: 60568584-E225-E011-A13F-BCAEC5543E5A
        Wake-up Type: Power Switch
        SKU Number: To Be Filled By O.E.M.
        Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK Computer INC.
        Product Name: P5G41T-M LX3
        Version: Rev X.0x
        Serial Number: 108613450001058
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
        OEM Information: 0x00000001
        Height: Unspecified
        Number Of Power Cords: 1
        Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
        Socket Designation: LGA775
        Type: Central Processor
        Family: Other
        Manufacturer: Intel            
        ID: 7A 06 01 00 FF FB EB BF
        Version: Pentium(R) Dual-Core CPU E6500 @ 2.93GHz            
        Voltage: 1.3 V
        External Clock: 266 MHz
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
        Thread Count: 2
        Characteristics:
                64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
        Socket Designation: L1-Cache
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Back
        Location: Internal
        Installed Size: 64 kB
        Maximum Size: 64 kB
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
        Installed Size: 2048 kB
        Maximum Size: 2048 kB
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
        Installed Size: 0 kB
        Maximum Size: 0 kB
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
        Internal Reference Designator: COM1
        Internal Connector Type: None
        External Reference Designator: COM
        External Connector Type: DB-9 male
        Port Type: Serial Port 16550A Compatible

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: LAN1
        Internal Connector Type: None
        External Reference Designator: GbE LAN
        External Connector Type: RJ-45
        Port Type: Network Port

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: USB1_2
        Internal Connector Type: None
        External Reference Designator: USB1_2
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: USB3_4
        Internal Connector Type: None
        External Reference Designator: USB3_4
        External Connector Type: Access Bus (USB)
        Port Type: USB

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Audio_Line In
        Internal Connector Type: None
        External Reference Designator: Audio_Line In
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port


Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Audio_Line Out
        Internal Connector Type: None
        External Reference Designator: Audio_Line Out
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: Audio_Mic In
        Internal Connector Type: None
        External Reference Designator: Audio_Mic In
        External Connector Type: Mini Jack (headphones)
        Port Type: Audio Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: SPDIF_OUT
        Internal Connector Type: None
        External Reference Designator: SPDIF_OUT
        External Connector Type: On Board Sound Input From CD-ROM
        Port Type: Audio Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: PANEL
        Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
        External Reference Designator: PANEL
        External Connector Type: Other
        Port Type: Other

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: VGA
        Internal Connector Type: None
        External Reference Designator: VGA port
        External Connector Type: Other
        Port Type: Video Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: SATA1
        Internal Connector Type: SAS/SATA Plug Receptacle
        External Reference Designator: Not Specified
        External Connector Type: None
        Port Type: SATA

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: SATA2
        Internal Connector Type: SAS/SATA Plug Receptacle
        External Reference Designator: Not Specified
        External Connector Type: None
        Port Type: SATA


Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: SATA3
        Internal Connector Type: SAS/SATA Plug Receptacle
        External Reference Designator: Not Specified
        External Connector Type: None
        Port Type: SATA

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: SATA4
        Internal Connector Type: SAS/SATA Plug Receptacle
        External Reference Designator: Not Specified
        External Connector Type: None
        Port Type: SATA

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: USB5_6
        Internal Connector Type: Access Bus (USB)
        External Reference Designator: Not Specified
        External Connector Type: None
        Port Type: USB

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: USB7_8
        Internal Connector Type: Access Bus (USB)
        External Reference Designator: Not Specified
        External Connector Type: None
        Port Type: USB

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: AAFP
        Internal Connector Type: Mini Jack (headphones)
        External Reference Designator: Not Specified
        External Connector Type: None
        Port Type: Audio Port

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CPU_FAN
        Internal Connector Type: Other
        External Reference Designator: Not Specified
        External Connector Type: None
        Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
        Internal Reference Designator: CHA_FAN
        Internal Connector Type: Other
        External Reference Designator: Not Specified
        External Connector Type: None
        Port Type: Other


Handle 0x001D, DMI type 9, 13 bytes
System Slot Information
        Designation: PCI_1
        Type: 64-bit PCI Express
        Current Usage: In Use
        Length: Short
        ID: 1
        Characteristics:
                3.3 V is provided
                Opening is shared
                PME signal is supported

Handle 0x001E, DMI type 9, 13 bytes
System Slot Information
        Designation: PCIEX16_1
        Type: 32-bit PCI Express
        Current Usage: In Use
        Length: Short
        ID: 16
        Characteristics:
                3.3 V is provided
                Opening is shared
                PME signal is supported

Handle 0x001F, DMI type 9, 13 bytes
System Slot Information
        Designation: PCIEX1_1
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Short
        ID: 32
        Characteristics:
                3.3 V is provided
                Opening is shared
                PME signal is supported

Handle 0x0020, DMI type 9, 13 bytes
System Slot Information
        Designation: PCIEX1_2
        Type: 32-bit PCI Express
        Current Usage: Available
        Length: Short
        ID: 33
        Characteristics:
                3.3 V is provided
                Opening is shared
                PME signal is supported

Handle 0x0021, DMI type 10, 6 bytes
On Board Device Information
        Type: Ethernet
        Status: Enabled
        Description:  Onboard Ethernet

Handle 0x0022, DMI type 11, 5 bytes
OEM Strings
        String 1: BCAEC5543E5A


Handle 0x0025, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 8 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2


Handle 0x0027, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0025
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM A1
        Bank Locator: BANK0
        Type: Other
        Type Detail: Synchronous
        Speed: 1333 MHz
        Manufacturer: Manufacturer0
        Serial Number: SerNum0
        Asset Tag: AssetTagNum0
        Part Number: PartNum0


Handle 0x0029, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0025
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 4096 MB
        Form Factor: DIMM
        Set: None
        Locator: DIMM B1
        Bank Locator: BANK1
        Type: Other
        Type Detail: Synchronous
        Speed: 1333 MHz
        Manufacturer: Manufacturer1
        Serial Number: SerNum1
        Asset Tag: AssetTagNum1
        Part Number: PartNum1


End Of Table
```

---

### Post by him610 on 2017-09-08
Be advised there is a difference between a PCI slot and a PCIe slot.
If your NIC will operate from the slot with fewer connections then use that one. You never know when you may need the one with more connections.

---

### Post by outofnicks on 2017-09-08
> **him610 said:**
> Be advised there is a difference between a PCI slot and a PCIe slot.
If your NIC will operate from the slot with fewer connections then use that one. You never know when you may need the one with more connections.

I appreciate the advice, there's so many types of PCI configurations to confuse me.

I've been looking on Newegg for new and refurbished cards as well. I wonder if something like this would be good:

[https://www.newegg.com/Product/Product.aspx?Item=9SIA4A04UG6208&cm_re=network_card-_-33-106-010-_-Product](https://www.newegg.com/Product/Product.aspx?Item=9SIA4A04UG6208&cm_re=network_card-_-33-106-010-_-Product)

---

### Post by him610 on 2017-09-09
Probably yes, the referenced *Intel EXPI9400PT Gigabit Copper Connection for Servers 10/100/1000Mbps PCI-Express 1 x RJ45* will more than likely work for you. I would have no reservations about installing this card in any one of my systems. It is a little long in the tooth, but that usually translates to good support by Linux.

---

### Post by Yellow Pasque on 2017-09-09
Supposedly, the cnet card works with dmfe driver:
[https://github.com/torvalds/linux/blob/master/Documentation/networking/dmfe.txt](https://github.com/torvalds/linux/blob/master/Documentation/networking/dmfe.txt)

> This driver provides kernel support for Davicom DM9102(A)/DM9132/DM9801 ethernet cards ( CNET
10/100 ethernet cards uses Davicom chipset too, so this driver supports CNET cards too )

---

