---
title: "dmidecode output on RAM"
date: 2016-03-01
forum: Hardware
---

### Post by BL4CKFIRE64 on 2016-03-01
Hi,

I have a Dell PowerEdge C6100 XS23-TY3 machine and each node has 12 DIMMS, but the node I am using for a SAN is being a bit confusing. I'm trying to find out how much memory this machine can take and how much is in each slot currently without powering off the machine to physically look. Does anyone know why my machine is only displaying 9 ports instead of 12? Does this mean my ports are bad? And how much my max is?

```
[root@san ~]# dmidecode -t 16
# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x0012, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: Multi-bit ECC
        Maximum Capacity: 48 GB
        Error Information Handle: Not Provided
        Number Of Devices: 6

Handle 0x0026, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: Multi-bit ECC
        Maximum Capacity: 24 GB
        Error Information Handle: Not Provided
        Number Of Devices: 3
```

```
[root@san ~]# dmidecode -t 17|grep Size
        Size: 4096 MB
        Size: 4096 MB
        Size: 4096 MB
        Size: 4096 MB
        Size: 4096 MB
        Size: 4096 MB
        Size: No Module Installed
        Size: 4096 MB
        Size: 4096 MB

```

---

### Post by Bashing-om on 2016-03-01
BL4CKFIRE64; Hello;

Perhaps a different look ?
```

sudo dmidecode -t memory

```
for reference my output:
```

sysop@1404mini:~$ sudo dmidecode -t memory
[sudo] password for sysop: 
# dmidecode 2.12
SMBIOS 2.5 present.

Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
        Error Detecting Method: 64-bit ECC
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 4096 MB
        Maximum Total Memory Size: 16384 MB
        Supported Speeds:
                70 ns
                60 ns
                50 ns
        Supported Memory Types:
                Standard
                DIMM
        Memory Module Voltage: 2.9 V
        Associated Memory Slots: 4
                0x0006
                0x0007
                0x0008
                0x0009
        Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A0
        Bank Connections: 0 1
        Current Speed: 5 ns
        Type: Other Unknown EDO
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A1
        Bank Connections: 2 3
        Current Speed: 5 ns
        Type: Other Unknown EDO
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A2
        Bank Connections: None
        Current Speed: 5 ns
        Type: Other Unknown EDO
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK
Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A3
        Bank Connections: None
        Current Speed: 5 ns
        Type: Other Unknown EDO
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x001D, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 16 GB
        Error Information Handle: Not Provided
        Number Of Devices: 4

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001D
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x001F, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001D
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
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x0020, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001D
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A2
        Bank Locator: Bank4/5
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x0021, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001D
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A3
        Bank Locator: Bank6/7
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

sysop@1404mini:~$

```
where On this ole box I have 4 Gigs of ram installed, and a possibility of 16 .

[INDENT][INDENT]hope this helps a bit 
[/INDENT][/INDENT]

---

### Post by BL4CKFIRE64 on 2016-03-01
> **Bashing-om said:**
> BL4CKFIRE64; Hello;

Perhaps a different look ?
```

sudo dmidecode -t memory

```
for reference my output:
```

sysop@1404mini:~$ sudo dmidecode -t memory
[sudo] password for sysop: 
# dmidecode 2.12
SMBIOS 2.5 present.

Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
        Error Detecting Method: 64-bit ECC
        Error Correcting Capabilities:
                None
        Supported Interleave: One-way Interleave
        Current Interleave: One-way Interleave
        Maximum Memory Module Size: 4096 MB
        Maximum Total Memory Size: 16384 MB
        Supported Speeds:
                70 ns
                60 ns
                50 ns
        Supported Memory Types:
                Standard
                DIMM
        Memory Module Voltage: 2.9 V
        Associated Memory Slots: 4
                0x0006
                0x0007
                0x0008
                0x0009
        Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A0
        Bank Connections: 0 1
        Current Speed: 5 ns
        Type: Other Unknown EDO
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A1
        Bank Connections: 2 3
        Current Speed: 5 ns
        Type: Other Unknown EDO
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A2
        Bank Connections: None
        Current Speed: 5 ns
        Type: Other Unknown EDO
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK
Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A3
        Bank Connections: None
        Current Speed: 5 ns
        Type: Other Unknown EDO
        Installed Size: Not Installed
        Enabled Size: Not Installed
        Error Status: OK

Handle 0x001D, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 16 GB
        Error Information Handle: Not Provided
        Number Of Devices: 4

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001D
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: DIMM
        Set: None
        Locator: A0
        Bank Locator: Bank0/1
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x001F, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001D
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
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x0020, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001D
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A2
        Bank Locator: Bank4/5
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

Handle 0x0021, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x001D
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: No Module Installed
        Form Factor: DIMM
        Set: None
        Locator: A3
        Bank Locator: Bank6/7
        Type: Unknown
        Type Detail: None
        Speed: Unknown
        Manufacturer: None
        Serial Number: None
        Asset Tag: None
        Part Number: None

sysop@1404mini:~$

```
where On this ole box I have 4 Gigs of ram installed, and a possibility of 16 .

[INDENT][INDENT]hope this helps a bit 
[/INDENT][/INDENT]


That does the same thing, only shows 9 ports instead of 12

---

