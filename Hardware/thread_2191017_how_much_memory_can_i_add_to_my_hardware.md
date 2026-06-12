---
title: "how much memory can i add to my hardware?"
date: 2013-11-30
forum: Hardware
---

### Post by tomerbd on 2013-11-30
I asked in superuser but did not get an answer, i don't understand how much memory I can add to my computer:



I ran following in Ubuntu and got this result:
> 
$ sudo dmidecode --type memory
# dmidecode 2.11
SMBIOS 2.5 present.

Handle 0x0008, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 1024 MB
    Maximum Total Memory Size: 2048 MB
    Supported Speeds:
        70 ns
        60 ns
        50 ns
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 3.3 V
    Associated Memory Slots: 2
        0x0009
        0x000A
    Enabled Error Correcting Capabilities:
        None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM0
    Bank Connections: 1
    Current Speed: 160 ns
    Type: Unknown
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM1
    Bank Connections: 0 5
    Current Speed: 162 ns
    Type: ECC DIMM
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0029, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 8 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x002B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0029
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 72 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: DDR2
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

Motherboard info:

# dmidecode 2.11
SMBIOS 2.5 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: MSI
    Product Name: MS-7309
    Version: 1.0
    Serial Number: To be filled by O.E.M.
    Asset Tag: To Be Filled By O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To Be Filled By O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

I don't understand if the maximum capacity is 2GB for each slot, but then it also says max 8GB so what is the maximum amount of memory I can add?  
When I open the computer I see a single slot captured that means that my current capacity is 2GB in one slot but can I add more to the other slot if yes how much? (I see two total slot one has a stick with 2GB, I wonder if i can add anything at all as the controller said max 2GB) and If I can add how much can I add...

thanks

---

### Post by rackit on 2013-11-30
Google the specs for your motherboard model - you may have to open the chassis and look directly on the board. You need to be running a 64 bit OS in order to utilize more than 4GB RAM though.

---

### Post by heir4c on 2013-11-30
> Maximum Capacity: 8 GB
This you can max use on the 2 slots together.

---

### Post by tomerbd on 2013-11-30
Thanks why does the controller says Maximum Total Memory Size: 2048 MB

---

### Post by heir4c on 2013-11-30
I don't know.
When I type that command here I get not that first text where it's say of the Maximum memory size.
But if you look at the specs of your motherboard on the internet (or the documentation that come with your motherboard) you will see that it support the 8GB.

---

### Post by Yellow Pasque on 2013-11-30
> **tomerbd said:**
> Thanks why does the controller says Maximum Total Memory Size: 2048 MB

I wouldn't trust that. dmidecode also says "Memory Module Voltage: 3.3 V", but 3.3V would probably fry DDR2 modules that the board uses.

---

