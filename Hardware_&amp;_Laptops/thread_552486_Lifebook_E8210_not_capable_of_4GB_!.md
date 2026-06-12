---
title: "Lifebook E8210 not capable of 4GB ?!"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by Miraculix on 2007-09-16
Hi,

it seems that my FSC E8210 (Core2Duo T7200, 2GHz) is not able to use the 
possible full amount of 4GB RAM: an exchange of the original 1GB SODIMM 
module by 2x2GB (Kingston KVR667D2S5/2GB) resulted in an Ubuntu 7.04 
(desktop, i386 SMP kernel 2.6.20-16, ATI  X1400 running under fglrx) that was 
*extremely* slowed down.

Additionally, 'hwinfo --memory' reported 3GB+256MB only.

Checking the BIOS (Trusted Phoenix Version 1.21, 23. Feb 2007), the info screen
displayed that two banks DDR2 RAM with 2048MB each have been detected, but
giving 3328MB in total only (which is obviously less than 4GB if I have done my 
math correctly...).

Switching back the module in the first bank to 1GB and keep the new 2GB in 
the second bank, everything went back to normal apart that the laptop now
running with 3GB instead of 1GB...

Here are some relevant lines of the output of 'sudo dmidecode':

[INDENT]
# dmidecode 2.8
SMBIOS 2.4 present.
63 structures occupying 1695 bytes.
Table at 0x000E5190.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: FUJITSU // Phoenix Technologies Ltd.
        Version: Version 1.21 
        Release Date: 02/23/2007
        Address: 0xE0000
        Runtime Size: 128 kB
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                3.5"/720 KB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
        BIOS Revision: 1.33

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: FUJITSU SIEMENS
        Product Name: LIFEBOOK E8210
        Version:  
        Serial Number: YK2C0*****
        UUID: ********-****-****-****-************
        Wake-up Type: Power Switch
        SKU Number:  
        Family:  

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM1
        Bank Connections: 0 1
        Current Speed: Unknown
        Type: Other
        Installed Size: 1024 MB (Double-bank Connection)
        Enabled Size: 1024 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: DIMM2
        Bank Connections: 2 3
        Current Speed: Unknown
        Type: Other
        Installed Size: 2048 MB (Double-bank Connection)
        Enabled Size: 2048 MB (Double-bank Connection)
        Error Status: OK

Handle 0x0029, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

Handle 0x002A, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0029
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 1024 MB
        Form Factor: SODIMM
        Set: None
        Locator: DDRII 1
        Bank Locator: Bank 0/1
        Type: DDR2
        Type Detail: Synchronous
        Speed: 333 MHz (3.0 ns)
        Manufacturer: Not Specified
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified

Handle 0x002B, DMI type 17, 27 bytes
Memory Device
        Array Handle: 0x0029
        Error Information Handle: Not Provided
        Total Width: 64 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: None
        Locator: DDRII 2
        Bank Locator: Bank 2/3
        Type: DDR2
        Type Detail: Synchronous
        Speed: 333 MHz (3.0 ns)
        Manufacturer: Not Specified
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified

Handle 0x002C, DMI type 19, 15 bytes
Memory Array Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x000BFFFFFFF
        Range Size: 3 GB
        Physical Array Handle: 0x0029
        Partition Width: 0

Handle 0x002D, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0003FFFFFFF
        Range Size: 1 GB
        Physical Device Handle: 0x002A
        Memory Array Mapped Address Handle: 0x002C
        Partition Row Position: 1

Handle 0x002E, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00040000000
        Ending Address: 0x000BFFFFFFF
        Range Size: 2 GB
        Physical Device Handle: 0x002B
        Memory Array Mapped Address Handle: 0x002C
        Partition Row Position: 1
[/INDENT]


Any comments and / or suggestions how to get all 4GB up and running?
Or is this simply impossible for this combination of board and bios despite
all data sheets provided by FSC?!

---

### Post by Syke on 2007-09-17
Sounds like that's the stock 32-bit Ubuntu kernel. If you want to go beyond 3 GB, you'll need either a custom kernel, or go with 64-bit Ubuntu.

---

### Post by Miraculix on 2007-09-17
> 
Sounds like that's the stock 32-bit Ubuntu kernel. If you want to go beyond 3 GB, you'll need either a custom kernel, or go with 64-bit Ubuntu.


... oh, I forgot to mention this: I already tried (nearly?) everything: ubuntu server i386, 
ubuntu amd64, and recompiling the i386 2.6.20-16 kernel with 64GB support.

Well, since these trial versions did not use fglrx the laptop was not slowed down at least.
However, there was still this 1GB missing...

---

### Post by Miraculix on 2007-09-28
Well, for those who are (still?) interested: 

This type of notebook (and many others) are definitely not worth for an upgrade to the full 4GB.
It is the Intel 945 GM/PM chipset that causes this 1GB PCI memory gap problem. Here is an 
official answer I got from the Fujitsu Siemens helpdesk:

> 
Originalkommentar von Intel:

The NAPA chipset (945GM/PM)supports a maximum of 4GB memory.
The maximum amount of useable memory will be about 3.5GB.
This limitation is caused by the operating system taking up some of the memory for it's own use, the logical memory used for I/O mapping etc.
However it's not strictly correct to blame only the O/S. The issue is due to the combination of O/S and Chipset.

A 32 bit O/S can address up to 4GB so if you used a 32 bit O/S and a chipset which supports say 8GB (965G/P) you will still only see 3.5GB useable memory.
If you use a 64 bit O/S and a chipset which supports only 4GB, again you will only see 3.5GB useable memory.
You will need both a 64bit O/S AND a chipset which supports 8GB (on which you install only 4GB) to see the full 4GB.
Note if you use a chipset which supports 8GB and fill it with 8GB memory, again you will only see 7.5GB useable memory.


... and all this is well known... see [http://thingsthatshouldbeeasy.blogspot.com/2007/05/memory-issues-with-gateway-cx210x.html]("http://thingsthatshouldbeeasy.blogspot.com/2007/05/memory-issues-with-gateway-cx210x.html")

Hope this helps/warns others who are planning to upgrade their i945-based notebooks!

---

