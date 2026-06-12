---
title: "Mismatch b/w hardinfo and dmidecode output"
date: 2011-05-10
forum: Hardware
---

### Post by moiktran on 2011-05-10
Hi, I have two 2GB RAMs installed in my Lenovo T400, and I generated a report using the *hardinfo *util which gave the following output(notice the 3056MB instead of 4GB). 

> Processor    2x Intel(R) Core(TM)2 Duo CPU P8600 @ 2.40GHz
Memory    3056MB (2223MB used)
Operating System    Ubuntu 10.04 LTS
User Name    jean (Jean Abraham)
Date/Time    Tue 10 May 2011 09:57:00 AM EDT



But, when I run ```
sudo dmidecode --type memory
```, I get the below:
> # dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0007, DMI type 5, 20 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 4096 MB
    Maximum Total Memory Size: 8192 MB
    Supported Speeds:
        Other
    Supported Memory Types:
        DIMM
        SDRAM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 2
        0x0008
        0x0009
    Enabled Error Correcting Capabilities:
        Unknown

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM Slot 1
    Bank Connections: 0 1
    Current Speed: 42 ns
    Type: DIMM SDRAM
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: DIMM Slot 2
    Bank Connections: 2 3
    Current Speed: 42 ns
    Type: DIMM SDRAM
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Handle 0x002B, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x002C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x002B
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM 1
    Bank Locator: Bank 0/1
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1066 MHz (0.9 ns)
    Manufacturer: 80CE            
    Serial Number: 460AE308        
    Asset Tag: 0907
    Part Number: M471B5673EH1-CF8  

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x002B
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM 2
    Bank Locator: Bank 2/3
    Type: <OUT OF SPEC>
    Type Detail: Synchronous
    Speed: 1066 MHz (0.9 ns)
    Manufacturer: 830B            
    Serial Number: 26352D6A        
    Asset Tag: 0921
    Part Number: NT2GC64B8HA1NS-BECan someone please advise on what may be wrong? Thanks!

---

