---
title: "can I increase RAM memory or is it full already?"
date: 2016-09-14
forum: Hardware
---

### Post by marchello_lippi2 on 2016-09-14
Hi all, 

See characteristics below. 
Can I increase RAM memory or is it full already?

```

# dmidecode 2.12
SMBIOS 2.4 present.

Handle 0x0005, DMI type 5, 20 bytes
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
        Supported Memory Types:
                Standard
                EDO
        Memory Module Voltage: 3.3 V
        Associated Memory Slots: 2
                0x0006
                0x0007
        Enabled Error Correcting Capabilities:
                None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A0
        Bank Connections: 1
        Current Speed: 155 ns
        Type: Other Unknown EDO
        Installed Size: 1024 MB (Single-bank Connection)
        Enabled Size: 1024 MB (Single-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A1
        Bank Connections: 2
        Current Speed: 155 ns
        Type: Other Unknown EDO
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Error Status: OK

Handle 0x001F, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 8 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

Handle 0x0020, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001F
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: Unknown
        Type Detail: None
        Speed: 667 MHz
        Manufacturer:
        Serial Number:
        Asset Tag:
        Part Number:

Handle 0x0021, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001F
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A1
        Bank Locator: Bank2/3
        Type: Unknown
        Type Detail: None
        Speed: 667 MHz
        Manufacturer:
        Serial Number:
        Asset Tag:
        Part Number:

```

---

### Post by newbie-user on 2016-09-14
> **marchello_lippi2 said:**
> Hi all, 


Handle 0x001F, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 8 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2



Looks like it will support up to 8GB

---

