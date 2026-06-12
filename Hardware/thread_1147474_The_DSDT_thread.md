---
title: "The DSDT thread"
date: 2009-05-03
forum: Hardware
---

### Post by 67GTA on 2009-05-03
I decided to start this thread to help, and maybe force some change if enough people are affected. It seems that Microsoft has started pushing their acpi aml compiler to motherboard/bios manufacturers. Their home brewed compiler is causing problems with a lot of newer PC's because errors are found in the Linux ACPI tables. Until recently manufacturers used the Intel AML compiler(iasl). It was open, and was an indusrty standard. I think this may be on purpose. This was brought up during the Microsoft antitrust lawsuit. I beleive this is also what was at the root of the recent Foxconn scandal [http://hehe2.net/thedarkside/even-more-incriminating-evidence-in-the-foxconn-debacle/](http://hehe2.net/thedarkside/even-more-incriminating-evidence-in-the-foxconn-debacle/)

If you read the email from Bill Gates that was used as evidence, he mentions patenting something to mess with other OS's. I beleive the Microsoft AML compiler was the result. The API's are open to anyone, but the Linux API's are clearly broken in a large number of PC's. Most people don't know what a DSDT is, or how to fix it. They try a Linux distro, only to have suspend/hibernate, temp, or various other ACPI functions not work, and just blame it on Linux being crappy. They don't realize that they could be sabatoged by MS. I wrote a how to here to show how to extract and fix your DSDT [http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt) as well as trying to help solve DSDT problems in this bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all) My goal is to try and help fix as many DSDT's as possible and have others post their fixed DSDT files in this thread. That way others can benefit, and maybe find a pattern so we can pressure manufacturers to stop this if they are identified. If this is too scary, then follow my how to to the point of getting your dsdt.dsl file, and email it to me. I will try to fix it for you and help you get it implemented. You can tell if your DSDT was compiled by Microsoft by running the following command in a terminal. ```
dmesg | grep MSFT
``` If this returns "anything", then yours is possibly broken. Ecspecially if you have trouble with heat/sleep. As we get one fixed, please post a copy of your fixed DSDT.aml file and a copy of the output of ```
sudo dmidecode
``` from a terminal in this thread. Please contact me through email for help so this thread won't become too long. I am afraid this is only going to get worse in the future unless something is done. Hopefully we can gather enough evidence here to get something started.

---

### Post by bcschmerker on 2009-05-06
> **67GTA said:**
> ...I wrote a how to here to show how to extract and fix your DSDT [http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt](http://ubuntuforums.org/showthread.php?t=1036051&highlight=dsdt) as well as trying to help solve DSDT problems in this bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247?comments=all) My goal is to try and help fix as many DSDT's as possible and have others post their fixed DSDT files in this thread. That way others can benefit, and maybe find a pattern so we can pressure manufacturers to stop this if they are identified. If this is too scary, then follow my how to to the point of getting your dsdt.dsl file, and email it to me. I will try to fix it for you and help you get it implemented. You can tell if your DSDT was compiled by Microsoft by running the following command in a terminal. ```
dmesg | grep MSFT
``` If this returns "anything", then yours is possibly broken. Ecspecially if you have trouble with heat/sleep. As we get one fixed, please post a copy of your fixed DSDT.aml file and a copy of the output of ```
sudo dmidecode
``` from a terminal in this thread. Please contact me through email for help so this thread won't become too long. I am afraid this is only going to get worse in the future unless something is done. Hopefully we can gather enough evidence here to get something started.I'm having the occasional random shutdown, and ended up tracing it to a Restricted package.  The following line printed when I executed dmesg | grep MSFT:
```
[    0.000000] ACPI: DSDT 7BEE3180, 6395 (r1 NVIDIA NVDAACPI    1000 MSFT  100000E)

```The obvious conclusion:  nVIDIA used the Microsoft assembler cited this Thread in preparing any number of restricted modules that my rebuilt Everex requires due to the GeForce/nForce chipset.  I'm already wondering whether I'll have to rebuild again, this time around the Asus/AMD 'board that I originally wanted?

---

### Post by CylnZ on 2009-05-07
5620 acer extensa
9.04 64bit
latest bios 1.35 from acer

```
laptop2:~$ dmesg | grep MSFT
[    0.000000] ACPI: DSDT 7F6D2BBA, 8FA9 (r2 INTEL  CRESTLNE  6040000 MSFT  3000000)
```

---

### Post by rainwalker on 2009-05-08
For what it's worth, I'm on an old Dell Inspiron 8600 and everything seems to work fine (suspend, hibernate is a bit slow but works, compiz, sound, etc). 
```
riley@riley-laptop:~$ dmesg | grep MSFT
[    0.000000] ACPI: DSDT 7FFF0C00, 2CF6 (r1 INT430 SYSFexxx     1001 MSFT  100000E)

```

---

### Post by 67GTA on 2009-05-08
> **rainwalker said:**
> For what it's worth, I'm on an old Dell Inspiron 8600 and everything seems to work fine (suspend, hibernate is a bit slow but works, compiz, sound, etc). 
```
riley@riley-laptop:~$ dmesg | grep MSFT
[    0.000000] ACPI: DSDT 7FFF0C00, 2CF6 (r1 INT430 SYSFexxx     1001 MSFT  100000E)

```

I've found for some reason Dell doesn't have a lot of dsdt errors. It has mostly been other OEM's.

---

### Post by JB_1980 on 2009-05-11
After playing around with the DSDT file per your thread, I have got my HP Pavilion dv9810us to load up without having to keep tapping some key.

Here is a copy of the sudo dmidecode:
```
joseph@joseph-laptop:~$ sudo dmidecode
[sudo] password for joseph: 
# dmidecode 2.9
SMBIOS 2.4 present.
19 structures occupying 726 bytes.
Table at 0x000F0B90.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Hewlett-Packard
	Version: F.2C    
	Release Date: 03/24/2008
	Address: 0xE4360
	Runtime Size: 113824 bytes
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		Smart battery is supported
		Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Hewlett-Packard
	Product Name: HP Pavilion dv9700 Notebook PC    
	Version: Rev 1
	Serial Number: 3CF811080T
	UUID: 33434638-3131-3038-3054-001E682C55A1
	Wake-up Type: Power Switch
	SKU Number: KN869UAR#AB
	Family: 103C_5335KV

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Quanta
	Product Name: 30D1
	Version: 85.26
	Serial Number: None1

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Quanta
	Type: Notebook
	Lock: Not Present
	Version: N/A
	Serial Number: None
	Asset Tag:                     
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000104

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket S1
	Type: Central Processor
	Family: Opteron
	Manufacturer: AMD
	ID: 82 0F 06 00 FF FB 8B 17
	Signature: Family 15, Model 104, Stepping 2
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
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		HTT (Hyper-threading technology)
	Version: AMD Turion(tm) 64 X2 Mobile TL60
	Voltage: 1.6 V
	External Clock: 200 MHz
	Max Speed: 2000 MHz
	Current Speed: 2000 MHz
	Status: Populated, Enabled
	Upgrade: None
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unified
	Associativity: Unknown

Handle 0x0007, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot 1
	Type: 64-bit PCI Express
	Current Usage: Available
	Length: Short
	ID: 0
	Characteristics:
		5.0 V is provided
		3.3 V is provided

Handle 0x0008, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Slot 2
	Type: 64-bit PCI Express
	Current Usage: Available
	Length: Short
	ID: 0
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0009, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:  64

Handle 0x000A, DMI type 11, 5 bytes
OEM Strings
	String 1: $HP$
	String 2: LOC#
	String 3: <BAD INDEX>

Invalid entry length (0). DMI table is broken! Stop.

```

It still says DMI table is broken, so I don't know what that means.

I also have attached the copy of my DSDT.aml file that works with my laptop. It may be of help to someone else.

---

### Post by bcschmerker on 2009-05-16
On my Everex running 8.04-LTS with Mozilla Firefox 3.0.10 and nVIDIA X Driver 173.14.12, I am beginning to recognize a pattern with the uncommanded shutdowns I have had to date:  Almost all these uncommanded shutdowns occur when viewing certain Web pages from services running Mirosoft IIS 6.0 (as identified by Header Spy 1.3.3.1).  I may have to investigate further from my eMachines/Gateway T3882, which (as a Windows box) is not affected by the problem under discussion this Thread; something in the Web-page code may be the trigger for the aforementioned shutdowns.  (The Mozilla Firefox 3.0.10 installation on the T3882 is as close to that of the Everex as extensions availability for Windows and LinUX, severally, permit as of May 2009.)

Update:  After switching to a Gigabyte MA78GM-S2HP, I no longer have the uncommanded shutdowns, but now I have different bugs in the DSDT from the Elitegroup GeForce6100SM-M.  Intel ASL, /usr/bin/iasl, returned the following StdOut+StdErr upon entering the command iasl -tc /home/bcschmerker/dsdt.dsl for my current BIOS settings as of this post:
```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/bcschmerker/dsdt.dsl  1885:             Method (WMAA, 3, NotSerialized)
Warning  1086 -     Not all control paths return a value ^  (WMAA)

/home/bcschmerker/dsdt.dsl  2052:     Method (\_WAK, 1, NotSerialized)
Warning  1079 -                                   ^ Reserved method must return a value (_WAK)

ASL Input:  /home/bcschmerker/dsdt.dsl - 7319 lines, 242706 bytes, 2322 keywords
AML Output: /home/bcschmerker/dsdt.aml - 23977 bytes 766 named objects 1556 executable opcodes

Compilation complete. 0 Errors, 2 Warnings, 0 Remarks, 974 Optimizations
```
What control paths need to be checked with Lines 1885 et seq?
```
            Method (WMAA, 3, NotSerialized)
            {
                If (LEqual (Arg0, 0x00))
                {
                    If (LOr (LOr (LNotEqual (Arg1, 0x01), LNotEqual (Arg1, 
                        0x02)), LNotEqual (Arg1, 0x06)))
                    {
                        CreateDWordField (Arg2, 0x00, WIID)
                    }

                    If (LEqual (Arg1, 0x01))
                    {
                        Return (AM01 ())
                    }
                    Else
                    {
                        If (LEqual (Arg1, 0x02))
                        {
                            Return (AM02 ())
                        }
                        Else
                        {
                            If (LEqual (Arg1, 0x03))
                            {
                                Return (AM03 (WIID))
                            }
                            Else
                            {
                                If (LEqual (Arg1, 0x04))
                                {
                                    CreateDWordField (Arg2, 0x04, IVAL)
                                    Return (AM04 (WIID, IVAL))
                                }
                                Else
                                {
                                    If (LEqual (Arg1, 0x05))
                                    {
                                        Return (AM05 (WIID))
                                    }
                                    Else
                                    {
                                        If (LEqual (Arg1, 0x06))
                                        {
                                            Return (AM06 ())
                                        }
                                        Else
                                        {
                                            If (LEqual (Arg1, 0x07))
                                            {
                                                AM07 (Arg2)
                                            }
                                            Else
                                            {
                                                If (LEqual (Arg1, 0x08))
                                                {
                                                    AM08 (WIID)
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            }

```
What statement should I use to return a value from the following excerpt, Lines 2052 et seq, including ensuring necessary data this Function?
```
    Method (\_WAK, 1, NotSerialized)
    {
        Store (0xFF, DBG1)
        If (LEqual (Arg0, 0x04))
        {
            If (LEqual (OSFL, 0x02))
            {
                Store (0x57, SMIP)
            }

            If (LEqual (OSFL, 0x01))
            {
                Store (0x56, SMIP)
            }

            If (LEqual (OSFL, 0x00))
            {
                If (LEqual (OSFX, 0x04))
                {
                    Store (0x59, SMIP)
                }
                Else
                {
                    If (LEqual (OSFX, 0x03))
                    {
                        Store (0x59, SMIP)
                    }
                    Else
                    {
                        Store (0x58, SMIP)
                    }
                }
            }

            If (LEqual (OSFX, 0x03))
            {
                Store (0x59, SMIP)
            }

            If (LEqual (OSFX, 0x04))
            {
                Store (0x59, SMIP)
            }
        }

        SWAK (Arg0)
        If (LEqual (OSFL, 0x01))
        {
            Notify (\_SB.PWRB, 0x02)
        }
        Else
        {
            If (LEqual (Arg0, 0x01))
            {
                And (P1, 0x04, Local0)
                If (LEqual (Local0, 0x00))
                {
                    Notify (\_SB.PWRB, 0x02)
                }
            }

            If (LEqual (Arg0, 0x03))
            {
                If (LEqual (RTCW, Zero))
                {
                    Notify (\_SB.PWRB, 0x02)
                }
            }
        }

        If (LEqual (Arg0, 0x04))
        {
            Notify (\_SB.PWRB, 0x02)
        }
    }

```

---

### Post by the_felis_leo on 2009-08-29
I have a HP dv9217ea with Intel Core 2 duo.
Seems fine working, but limited ACPI fonctionality;
More especially, no access to the Smart Battary,
and ACPI AML rapport a fixed constant for the design capacity, 
not the design capacity of the battery.

Futher more SMBIOS is broken;
The SKU value is replaced by a string consisting of 11 nulls !
so that the end of DMI block can't be found.

And I wonder why so many Bios Firmware ???? (cf lshw)

Original dmidecode :
```
# dmidecode 2.9
SMBIOS 2.4 present.
22 structures occupying 755 bytes.
Table at 0x000DF010.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: F.2D     
    Release Date: 11/26/2008
    Address: 0xE6D50
    Runtime Size: 103088 bytes
    ROM Size: 1024 kB
    Characteristics:
       (...)

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Hewlett-Packard
    Product Name: HP Pavilion dv9000 NotebookPC     
    Version: Rev 1
    Serial Number: CNF705116H
    UUID: 434E4637-3035-3131-3648-00238B81465B
    Wake-up Type: Power Switch
    SKU Number: <BAD INDEX>
    Family: <BAD INDEX>

Invalid entry length (0). DMI table is broken! Stop.
```patch for dmidecode, in dmi_decode (set SKU string )
```
                        /* dmi_string allow zero length strings */

                        if(h->length<0x1B) break;
                        {
                                char * SKU_ptr = dmi_string(h, data[0x19]) ;
                                int SKU_len = 11 ;
                                while ( SKU_len-- ) SKU_ptr[SKU_len] = ' ';
                        }
                        printf("\tSKU Number: %s\n",
                                dmi_string(h, data[0x19]));

                       /* dmi_table must again "look for the next handle" */
```patched demidecode output :
```
# dmidecode 2.9
SMBIOS 2.4 present.
22 structures occupying 755 bytes.
Table at 0x000DF010.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: F.2D     
    Release Date: 11/26/2008
    Address: 0xE6D50
    Runtime Size: 103088 bytes
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        Smart battery is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Hewlett-Packard
    Product Name: HP Pavilion dv9000 NotebookPC     
    Version: Rev 1
    Serial Number: CNF705116H
    UUID: 434E4637-3035-3131-3648-00238B81465B
    Wake-up Type: Power Switch
    SKU Number:            
    Family: 103C_5335KV

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Quanta
    Product Name: 30BD
    Version: 66.42
    Serial Number: None

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
    Manufacturer: Quanta
    Type: Notebook
    Lock: Not Present
    Version: N/A
    Serial Number: None
    Asset Tag:                     
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000000
    Height: 32 U
    Number Of Power Cords: 32

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
    Socket Designation: U2E1
    Type: Central Processor
    Family: Other
    Manufacturer: Intel
    ID: F6 06 00 00 FF FB EB BF
    Version: Intel(R) Core(TM)2 CPU T5200 
    Voltage: 1.8 V
    External Clock: 533 MHz
    Max Speed: 1600 MHz
    Current Speed: 1600 MHz
    Status: Populated, Enabled
    Upgrade: Socket 478
    L1 Cache Handle: 0x0005
    L2 Cache Handle: 0x0006
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Burst
        Pipeline Burst
        Asynchronous
    Installed SRAM Type: Asynchronous
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Socketed, Level 2
    Operational Mode: Write Back
    Location: External
    Installed Size: 2048 KB
    Maximum Size: 2048 KB
    Supported SRAM Types:
        Burst
        Pipeline Burst
        Asynchronous
    Installed SRAM Type: Burst
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x0007, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI Express Slot 1
    Type: 64-bit PCI Express
    Current Usage: Available
    Length: Short
    ID: 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided

Handle 0x0008, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI Express Slot 2
    Type: 64-bit PCI Express
    Current Usage: Available
    Length: Short
    ID: 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided
        PME signal is supported
        Hot-plug devices are supported

Handle 0x0009, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI Express Slot 3
    Type: 64-bit PCI Express
    Current Usage: Available
    Length: Short
    ID: 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided
        PME signal is supported

Handle 0x000A, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:    

Handle 0x000B, DMI type 11, 5 bytes
OEM Strings
    String 1: $HP$
    String 2: LOC#ABF

Handle 0x000C, DMI type 14, 8 bytes
Group Associations
    Name: Cpu Module
    Items: 1
        0x0015 (Processor)

Handle 0x000D, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x000E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 1
    Locator: DIMM 1
    Bank Locator: Bank 0,1
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz (1.9 ns)
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x000F, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: 1
    Locator: DIMM 2
    Bank Locator: Bank 2,3
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz (1.9 ns)
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified

Handle 0x0010, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Array Handle: 0x000D
    Partition Width: 0

Handle 0x0011, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x000E
    Memory Array Mapped Address Handle: 0x0010
    Partition Row Position: 2
    Interleave Position: 2
    Interleaved Data Depth: 2

Handle 0x0012, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00040000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 1 GB
    Physical Device Handle: 0x000F
    Memory Array Mapped Address Handle: 0x0010
    Partition Row Position: 2
    Interleave Position: 2
    Interleaved Data Depth: 2

Handle 0x0013, DMI type 32, 20 bytes
System Boot Information
    Status: <OUT OF SPEC>
    (An I say: no revelent !
      Boot Status is :   0c 01 02 03 04 05 06 07 08 09 )

Handle 0x0014, DMI type 127, 4 bytes
End Of Table

Handle 0x0015, DMI type 127, 4 bytes
End Of Table
```biosdecode :
```
# biosdecode 2.9
ACPI 2.0 present.
    OEM Identifier: HP    
    RSD Table 32-bit Address: 0x7FE7B2D3
    XSD Table 64-bit Address: 0x000000007FE7B327
SMBIOS 2.4 present.
    Structure Table Length: 755 bytes
    Structure Table Address: 0x000DF010
    Number Of Structures: 22
    Maximum Structure Size: 120 bytes
BIOS32 Service Directory present.
    Revision: 0
    Calling Interface Address: 0x000FD610
PNP BIOS 1.0 present.
    Event Notification: Not Supported
    Real Mode 16-bit Code Address: F000:BDC7
    Real Mode 16-bit Data Address: 0040:0000
    16-bit Protected Mode Code Address: 0x000FBDE5
    16-bit Protected Mode Data Address: 0x00000400
PCI Interrupt Routing 1.0 present.
    Router ID: 00:1f.0
    Exclusive IRQs: None
    Compatible Router: 8086:122e
    Slot Entry 1: ID 00:00, on-board
    Slot Entry 2: ID 00:07, on-board
    Slot Entry 3: ID 00:01, on-board
    Slot Entry 4: ID 01:00, slot number 6
    Slot Entry 5: ID 00:02, on-board
    Slot Entry 6: ID 00:1b, on-board
    Slot Entry 7: ID 00:1c, on-board
    Slot Entry 8: ID 02:00, slot number 7
    Slot Entry 9: ID 03:00, slot number 8
    Slot Entry 10: ID 05:00, slot number 9
    Slot Entry 11: ID 00:1d, on-board
    Slot Entry 12: ID 00:1f, on-board
    Slot Entry 13: ID 05:08, on-board
    Slot Entry 14: ID 05:05, on-board
```smbio-sys-info
```
Libsmbios version:      2.2.13
Product Name:           HP Pavilion dv9000 NotebookPC
Vendor:                 Hewlett-Packard
Version du BIOS:        F.2D
System ID:              0x0000
Service Tag:            CNF705116H
Express Service Code:   1284795716276537
Asset Tag:              
Property Ownership Tag: 
```lshw :
```
felis-kingdom             
    description: Computer
    product: HP Pavilion dv9000 NotebookPC
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF705116H
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=oem-specific uuid=434E4637-3035-3131-3648-00238B81465B
  *-core
       description: Motherboard
       physical id: 0
     *-firmware:0
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: F.2D (11/26/2008)
          size: 100KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-firmware:1
          description: BIOS
          physical id: 2
          size: 1MiB
          capabilities: pcmcia shadowing vesa int13floppynec int13floppytoshiba int13floppy720 int13floppy2880 int14serial int17printer
     *-firmware:2
          description: BIOS
          physical id: 3
          size: 1MiB
          capacity: 3136KiB
          capabilities: isa mca pcmcia pnp shadowing vesa bootselect socketedrom int13floppy360 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int10video
     *-firmware:3
          description: BIOS
          physical id: 5
          size: 828KiB
          capacity: 3264KiB
          capabilities: eisa pcmcia pnp apm upgrade shadowing escd bootselect pcmciaboot int13floppynec int13floppytoshiba int13floppy720 int13floppy2880 int14serial int17printer
     *-firmware:4
          description: BIOS
          physical id: 0
          size: 819KiB
          capacity: 6080KiB
          capabilities: isa mca pcmcia pnp shadowing vesa bootselect socketedrom int13floppynec int13floppytoshiba int13floppy720 int5printscreen int14serial int17printer
     *-firmware:5
          description: BIOS
          vendor: L2 Cache
          physical id: 3100
          version: &#65533;
          size: 642KiB
          capacity: 3264KiB
          capabilities: isa mca pcmcia apm shadowing vesa bootselect socketedrom edd int13floppy360 int13floppy2880 int5printscreen int14serial int10video
     *-firmware:6
          description: BIOS
          physical id: 3330
          version: (&#65533;)
          size: 819KiB
          capacity: 3392KiB
          capabilities: acpi netboot
     *-firmware:7
          description: BIOS
          physical id: 2020
          size: 554KiB
          capacity: 7040KiB
          capabilities: isa mca eisa pcmcia vesa escd int13floppy2880 int5printscreen int9keyboard int10video
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 CPU T5200
          slot: U2E1
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G70 [GeForce Go 7600]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:62:3b:47
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.10 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 00
                serial: 00:23:8b:81:46:5b
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-1 latency=0 link=no module=e1000e multicast=yes port=twisted pair
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 5
                bus info: pci@0000:07:05.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.1
                bus info: pci@0000:07:05.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 5.2
                bus info: pci@0000:07:05.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 5.3
                bus info: pci@0000:07:05.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 5.4
                bus info: pci@0000:07:05.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-4084N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KQ09
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: Hitachi HTS54161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SB4O
                serial: SB2404SJHDVLLE
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=887bb127
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 940b54b1-944b-ca43-b3f0-30794ce82d1a
                   size: 22MiB
                   capacity: 24MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-04-30 10:16:42 filesystem=ntfs label=BOOT state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/vista
                      capacity: 20GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noexec,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
                 *-logicalvolume:1
                      description: W95 FAT32 (LBA) partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /media/root
                      capacity: 512MiB
                      configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,gid=100,fmask=0002,dmask=0002,allow_utime=0020,codepage=cp850,iocharset=utf8,shortname=mixed state=mounted
                 *-logicalvolume:2
                      description: W95 FAT32 (LBA) partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /media/leo
                      capacity: 1536MiB
                      configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,gid=100,fmask=0002,dmask=0002,allow_utime=0020,codepage=cp850,iocharset=utf8,shortname=mixed state=mounted
                 *-logicalvolume:3
                      description: W95 FAT32 (LBA) partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /media/public
                      capacity: 4GiB
                      configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,gid=100,fmask=0002,dmask=0002,allow_utime=0020,codepage=cp850,iocharset=utf8,shortname=mixed state=mounted
                 *-logicalvolume:4
                      description: W95 FAT32 (LBA) partition
                      physical id: 9
                      logical name: /dev/sda9
                      logical name: /media/mp3
                      capacity: 16GiB
                      configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,gid=100,fmask=0002,dmask=0002,allow_utime=0020,codepage=cp850,iocharset=utf8,shortname=mixed state=mounted
                 *-logicalvolume:5
                      description: W95 FAT32 (LBA) partition
                      physical id: a
                      logical name: /dev/sda10
                      logical name: /media/divx
                      capacity: 16GiB
                      configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,gid=100,fmask=0002,dmask=0002,allow_utime=0020,codepage=cp850,iocharset=utf8,shortname=mixed state=mounted
                 *-logicalvolume:6
                      description: W95 FAT32 (LBA) partition
                      physical id: b
                      logical name: /dev/sda11
                      logical name: /media/download
                      capacity: 16GiB
                      configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,gid=100,fmask=0002,dmask=0002,allow_utime=0020,codepage=cp850,iocharset=utf8,shortname=mixed state=mounted
                 *-logicalvolume:7
                      description: W95 FAT32 (LBA) partition
                      physical id: c
                      logical name: /dev/sda12
                      logical name: /media/free
                      capacity: 8GiB
                      configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,gid=100,fmask=0002,dmask=0002,allow_utime=0020,codepage=cp850,iocharset=utf8,shortname=mixed state=mounted
                 *-logicalvolume:8
                      description: W95 FAT32 (LBA) partition
                      physical id: d
                      logical name: /dev/sda13
                      logical name: /media/websphere
                      capacity: 16GiB
                      configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,gid=100,fmask=0002,dmask=0002,allow_utime=0020,codepage=cp850,iocharset=utf8,shortname=mixed state=mounted
                 *-logicalvolume:9
                      description: Linux filesystem partition
                      physical id: e
                      logical name: /dev/sda14
                      capacity: 8GiB
                 *-logicalvolume:10
                      description: Linux filesystem partition
                      physical id: f
                      logical name: /dev/sda15
                      logical name: /
                      capacity: 6141MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=360,data=ordered state=mounted
                 *-logicalvolume:11
                      description: Linux swap / Solaris partition
                      physical id: 10
                      logical name: /dev/sda16
                      capacity: 2047MiB
                      capabilities: nofs
        *-serial
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0 module=i2c_i801
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:7b:da:22:08:48
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```finally the dsdt :
```
/*
 * Intel ACPI Component Architecture
 * AML Disassembler version 20081204
 *
 * Disassembly of dsdt.dat, Wed Aug 26 04:02:14 2009
 *
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x0000759D (30109)
 *     Revision         0x01 **** ACPI 1.0, no 64-bit math support
 *     Checksum         0x30
 *     OEM ID           "HP    "
 *     OEM Table ID     "30BD    "
 *     OEM Revision     0x06040000 (100925440)
 *     Compiler ID      "MSFT"
 *     Compiler Version 0x0100000E (16777230)
 */
DefinitionBlock ("dsdt.aml", "DSDT", 1, "HP    ", "30BD    ", 0x06040000)
{
    External (Z012)
    External (PDC1)
    External (PDC0)
    External (CFGD)
    External (\_PR_.CPU0._PPC)

    OperationRegion (PRT0, SystemIO, 0x80, 0x04)
    Field (PRT0, DWordAcc, Lock, Preserve)
    {
        P80H,   32
    }

    OperationRegion (S_IO, SystemIO, 0x06B0, 0x11)
    Field (S_IO, ByteAcc, NoLock, Preserve)
    {
        PMS0,   8, 
        PME0,   8, 
        PMS1,   8, 
        PMS2,   8, 
        PMS3,   8, 
        PME1,   8, 
        PME2,   8, 
        PME3,   8, 
        SMS1,   8, 
        SMS2,   8, 
        SME1,   8, 
        SME2,   8, 
        RT10,   1, 
        RT11,   1, 
            ,   1, 
        RT13,   1, 
                Offset (0x0E), 
        RT30,   1, 
        RT31,   1, 
        RT32,   1, 
        RT33,   1, 
        RT34,   1, 
        RT35,   1, 
        RT36,   1, 
        RT37,   1, 
                Offset (0x10), 
        DLPC,   1, 
        CK33,   1, 
        CK14,   1
    }

    OperationRegion (IO_T, SystemIO, 0x0800, 0x10)
    Field (IO_T, ByteAcc, NoLock, Preserve)
    {
                Offset (0x08), 
        TRP0,   8
    }

    OperationRegion (PMIO, SystemIO, 0x1000, 0x80)
    Field (PMIO, ByteAcc, NoLock, Preserve)
    {
                Offset (0x30), 
        GSMI,   1, 
            ,   3, 
        SLPE,   1, 
                Offset (0x42), 
            ,   1, 
        GPEC,   1
    }

    OperationRegion (GPIO, SystemIO, 0x1180, 0x3C)
    Field (GPIO, ByteAcc, NoLock, Preserve)
    {
        GU00,   8, 
        GU01,   8, 
        GU02,   8, 
        GU03,   8, 
        GIO0,   8, 
        GIO1,   8, 
        GIO2,   8, 
        GIO3,   8, 
                Offset (0x0C), 
        GL00,   8, 
            ,   4, 
        GP12,   1, 
                Offset (0x0E), 
        GL02,   8, 
            ,   1, 
        GP25,   1, 
        GP26,   1, 
                Offset (0x10), 
                Offset (0x18), 
        GB00,   8, 
        GB01,   8, 
        GB02,   8, 
        GB03,   8, 
                Offset (0x2C), 
        GIV0,   8, 
        GIV1,   8, 
        GIV2,   8, 
        GIV3,   8, 
        GU04,   8, 
        GU05,   8, 
        GU06,   8, 
        GU07,   8, 
        GIO4,   8, 
        GIO5,   8, 
        GIO6,   8, 
        GIO7,   8, 
            ,   7, 
        GP39,   1, 
        GL05,   8, 
        GL06,   8, 
        GL07,   8
    }

    OperationRegion (GNVS, SystemMemory, 0x7FE84DBC, 0x0100)
    Field (GNVS, AnyAcc, Lock, Preserve)
    {
        OSYS,   16, 
        SMIF,   8, 
        PRM0,   8, 
        PRM1,   8, 
        SCIF,   8, 
        PRM2,   8, 
        PRM3,   8, 
        LCKF,   8, 
        PRM4,   8, 
        PRM5,   8, 
        P80D,   32, 
        LIDS,   8, 
        PWRS,   8, 
        DBGS,   8, 
        LINX,   8, 
                Offset (0x14), 
        ACTT,   8, 
        PSVT,   8, 
        TC1V,   8, 
        TC2V,   8, 
        TSPV,   8, 
        CRTT,   8, 
        DTSE,   8, 
        DTS1,   8, 
        DTS2,   8, 
                Offset (0x1E), 
        BNUM,   8, 
        BCAP,   8, 
        B1SC,   8, 
        B2SC,   8, 
        B0SS,   8, 
        B1SS,   8, 
        B2SS,   8, 
                Offset (0x28), 
        APIC,   8, 
        MPEN,   8, 
                Offset (0x2B), 
        PPCM,   8, 
        PCP0,   8, 
        PCP1,   8, 
                Offset (0x32), 
        NATP,   8, 
        CMAP,   8, 
        CMBP,   8, 
        LPTP,   8, 
        FDCP,   8, 
        CMCP,   8, 
        CIRP,   8, 
                Offset (0x3C), 
        IGDS,   8, 
        TLST,   8, 
        CADL,   8, 
        PADL,   8, 
        CSTE,   16, 
        NSTE,   16, 
        SSTE,   16, 
        NDID,   8, 
        DID1,   32, 
        DID2,   32, 
        DID3,   32, 
        DID4,   32, 
        DID5,   32, 
                Offset (0x67), 
        BLCS,   8, 
        BRTL,   8, 
        ALSE,   8, 
        ALAF,   8, 
        LLOW,   8, 
        LHIH,   8, 
                Offset (0x6E), 
        EMAE,   8, 
        EMAP,   16, 
        EMAL,   16, 
                Offset (0x74), 
        MEFE,   8, 
                Offset (0x78), 
        TPMP,   8, 
        TPME,   8, 
                Offset (0x82), 
        GTF0,   56, 
        GTF2,   56, 
        IDEM,   8, 
                Offset (0xB4), 
        WMIA,   8, 
        WMIO,   8, 
        ACPS,   8, 
        HPBD,   8, 
        IVIM,   8, 
        EXTM,   8, 
        Z000,   8, 
        Z001,   8, 
        Z002,   8, 
        Z003,   8, 
        Z004,   8, 
        Z005,   8, 
        Z006,   8, 
        Z007,   8, 
        Z008,   8, 
        Z009,   8, 
        Z00A,   8, 
        EXCM,   8, 
        Z00B,   8
    }

    OperationRegion (RCRB, SystemMemory, 0xFED1C000, 0x4000)
    Field (RCRB, DWordAcc, Lock, Preserve)
    {
                Offset (0x1000), 
                Offset (0x3000), 
                Offset (0x3404), 
        HPAS,   2, 
            ,   5, 
        HPAE,   1, 
                Offset (0x3418), 
            ,   1, 
        PATD,   1, 
        SATD,   1, 
        SMBD,   1, 
        HDAD,   1, 
        A97D,   1, 
                Offset (0x341A), 
        RP1D,   1, 
        RP2D,   1, 
        RP3D,   1, 
        RP4D,   1, 
        RP5D,   1, 
        RP6D,   1
    }

    Mutex (MUTX, 0x00)
    Name (_S0, Package (0x03)
    {
        0x00, 
        0x00, 
        0x00
    })
    Name (_S3, Package (0x03)
    {
        0x05, 
        0x05, 
        0x00
    })
    Name (_S4, Package (0x03)
    {
        0x06, 
        0x06, 
        0x00
    })
    Name (_S5, Package (0x03)
    {
        0x07, 
        0x07, 
        0x00
    })
    Scope (\_PR)
    {
        Processor (CPU0, 0x00, 0x00001010, 0x06) {}
        Processor (CPU1, 0x01, 0x00001010, 0x06) {}
    }

    Name (\DSEN, 0x01)
    Name (\ECON, 0x00)
    Name (\GPIC, 0x00)
    Name (\CTYP, 0x00)
    Name (\L01C, 0x00)
    Name (\VFN0, 0x00)
    Method (\_PIC, 1, NotSerialized)
    {
        Store (Arg0, GPIC)
    }

    Name (SAV0, 0x00)
    Name (SAV1, 0x00)
    Name (SAV2, 0x00)
    Method (_PTS, 1, NotSerialized)
    {
        Store (0x00, P80D)
        P8XH (0x00, Arg0)
        Store (0x00, SLPE)
        Store (GP25, SAV0)
        Store (GP26, SAV1)
        Store (\_SB.PCI0.LPCB.EC0.WBSS, SAV2)
        If (LEqual (Arg0, 0x03))
        {
            TRAP (0x50)
            If (LEqual (OSYS, 0x07D6))
            {
                Store (0x00, GP25)
            }

            Store (0x01, SLPE)
            Store (0x53, P80H)
        }

        If (LEqual (Arg0, 0x04))
        {
            Store (0x01, SLPE)
            Store (0x54, P80H)
        }

        If (LEqual (Arg0, 0x05))
        {
            If (GSMI)
            {
                Store (0x01, SLPE)
            }
            Else
            {
                Store (0x00, SLPE)
            }
        }
    }

    Method (_WAK, 1, NotSerialized)
    {
        P8XH (0x00, 0xAB)
        If (LOr (LEqual (Arg0, 0x03), LEqual (Arg0, 0x04)))
        {
            If (And (CFGD, 0x01000000))
            {
                If (LAnd (And (CFGD, 0xF0), LEqual (OSYS, 0x07D1)))
                {
                    TRAP (0x3D)
                }
            }
        }

        If (LEqual (RP2D, 0x00))
        {
            Notify (\_SB.PCI0.RP02, 0x00)
        }

        If (LEqual (Arg0, 0x03))
        {
            TRAP (0x46)
        }

        If (LEqual (Arg0, 0x04))
        {
            Store (0x04, P80H)
            If (DTSE)
            {
                TRAP (0x47)
            }

            Notify (\_TZ.THR1, 0x80)
            TRAP (0x1D)
        }

        If (LEqual (OSYS, 0x07D2))
        {
            If (And (CFGD, 0x01))
            {
                If (LGreater (\_PR.CPU0._PPC, 0x00))
                {
                    Subtract (\_PR.CPU0._PPC, 0x01, \_PR.CPU0._PPC)
                    PNOT ()
                    Add (\_PR.CPU0._PPC, 0x01, \_PR.CPU0._PPC)
                    PNOT ()
                }
                Else
                {
                    Add (\_PR.CPU0._PPC, 0x01, \_PR.CPU0._PPC)
                    PNOT ()
                    Subtract (\_PR.CPU0._PPC, 0x01, \_PR.CPU0._PPC)
                    PNOT ()
                }
            }
        }

        If (LNotEqual (\_SB.PCI0.LPCB.EC0.WBSS, SAV2))
        {
            Store (0x01, \_SB.PCI0.LPCB.EC0.WBDS)
            Store (0x96, \_SB.PCI0.LPCB.EC0.DLYT)
        }
        Else
        {
            Store (SAV0, GP25)
            Store (SAV1, GP26)
        }

        Store (\_SB.PCI0.LPCB.EC0.QBBB, Local0)
        If (LEqual (Local0, 0x04))
        {
            Notify (\_SB.QBTN, 0x02)
        }

        If (LEqual (Local0, 0x05))
        {
            Notify (\_SB.DBTN, 0x02)
        }

        If (LEqual (Local0, 0x03))
        {
            Notify (\_SB.MBTN, 0x02)
        }

        If (LEqual (Local0, 0x10))
        {
            Notify (\_SB.EBTN, 0x02)
        }

        If (LEqual (Local0, 0x06))
        {
            Notify (\_SB.PBTN, 0x02)
        }

        If (LEqual (Local0, 0x12))
        {
            Notify (\_SB.VBTN, 0x02)
        }

        If (LEqual (Local0, 0x11))
        {
            Notify (\_SB.TBTN, 0x02)
        }

        P8XH (0x01, 0xCD)
        Return (Package (0x02)
        {
            0x00, 
            0x00
        })
    }

    Scope (\_GPE)
    {
        Method (_L01, 0, NotSerialized)
        {
            Add (L01C, 0x01, L01C)
            P8XH (0x00, 0x01)
            P8XH (0x01, L01C)
            Sleep (0x64)
            If (LAnd (LEqual (RP2D, 0x00), \_SB.PCI0.RP02.HPCS))
            {
                If (\_SB.PCI0.RP02.PDC2)
                {
                    Store (0x01, \_SB.PCI0.RP02.PDC2)
                    Store (0x01, \_SB.PCI0.RP02.HPCS)
                    Notify (\_SB.PCI0.RP02, 0x00)
                }
                Else
                {
                    Store (0x01, \_SB.PCI0.RP02.HPCS)
                }
            }
        }

        Method (_L02, 0, NotSerialized)
        {
            Store (0x00, GPEC)
            Notify (\_TZ.THR1, 0x80)
        }

        Method (_L07, 0, NotSerialized)
        {
            Store (0x20, \_SB.PCI0.SBUS.HSTS)
        }

        Method (_L09, 0, NotSerialized)
        {
            If (\_SB.PCI0.RP02.PSP2)
            {
                Store (0x01, \_SB.PCI0.RP02.PSP2)
                Store (0x01, \_SB.PCI0.RP02.PMCS)
                Notify (\_SB.PCI0.RP02, 0x02)
            }

            If (\_SB.PCI0.RP03.PSP3)
            {
                Store (0x01, \_SB.PCI0.RP03.PSP3)
                Store (0x01, \_SB.PCI0.RP03.PMCS)
                Notify (\_SB.PCI0.RP03, 0x02)
            }
        }

        Method (_L0B, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.PCIB, 0x02)
            Notify (\_SB.SLPB, 0x02)
        }

        Method (_L19, 0, NotSerialized)
        {
            Notify (\_SB.SLPB, 0x02)
        }
    }

    Method (VTOB, 1, NotSerialized)
    {
        Store (0x01, Local0)
        ShiftLeft (Local0, Arg0, Local0)
        Return (Local0)
    }

    Method (BTOV, 1, NotSerialized)
    {
        ShiftRight (Arg0, 0x01, Local0)
        Store (0x00, Local1)
        While (Local0)
        {
            Increment (Local1)
            ShiftRight (Local0, 0x01, Local0)
        }

        Return (Local1)
    }

    Method (MKWD, 2, NotSerialized)
    {
        If (And (Arg1, 0x80))
        {
            Store (0xFFFF0000, Local0)
        }
        Else
        {
            Store (Zero, Local0)
        }

        Or (Local0, Arg0, Local0)
        Or (Local0, ShiftLeft (Arg1, 0x08), Local0)
        Return (Local0)
    }

    Method (POSW, 1, NotSerialized)
    {
        If (And (Arg0, 0x8000))
        {
            If (LEqual (Arg0, 0xFFFF))
            {
                Return (0xFFFFFFFF)
            }
            Else
            {
                Not (Arg0, Local0)
                Increment (Local0)
                And (Local0, 0xFFFF, Local0)
                Return (Local0)
            }
        }
        Else
        {
            Return (Arg0)
        }
    }

    Method (GBFE, 3, NotSerialized)
    {
        CreateByteField (Arg0, Arg1, TIDX)
        Store (TIDX, Arg2)
    }

    Method (PBFE, 3, NotSerialized)
    {
        CreateByteField (Arg0, Arg1, TIDX)
        Store (Arg2, TIDX)
    }

    Method (ITOS, 1, NotSerialized)
    {
        Store (Buffer (0x09)
            {
                /* 0000 */    0x30, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                /* 0008 */    0x00
            }, Local0)
        Store (Buffer (0x11)
            {
                "0123456789ABCDEF"
            }, Local7)
        Store (0x08, Local1)
        Store (0x00, Local2)
        Store (0x00, Local3)
        While (Local1)
        {
            Decrement (Local1)
            And (ShiftRight (Arg0, ShiftLeft (Local1, 0x02)), 0x0F, Local4)
            If (Local4)
            {
                Store (Ones, Local3)
            }

            If (Local3)
            {
                GBFE (Local7, Local4, RefOf (Local5))
                PBFE (Local0, Local2, Local5)
                Increment (Local2)
            }
        }

        Return (Local0)
    }

    Method (GETB, 3, Serialized)
    {
        Multiply (Arg0, 0x08, Local0)
        Multiply (Arg1, 0x08, Local1)
        CreateField (Arg2, Local0, Local1, TBF3)
        Return (TBF3)
    }

    Method (HKDS, 1, Serialized)
    {
        If (LEqual (0x00, DSEN))
        {
            Store (Arg0, SMIF)
            Store (0x00, TRP0)
            If (LOr (LNotEqual (CADL, PADL), LEqual (NSTE, 0x01)))
            {
                Store (CADL, PADL)
                If (LOr (LGreater (OSYS, 0x07D0), LLess (OSYS, 0x07D6)))
                {
                    Notify (\_SB.PCI0, 0x00)
                }
                Else
                {
                    Notify (\_SB.PCI0.GFX0, 0x00)
                }

                Sleep (0x02EE)
            }

            Notify (\_SB.PCI0.GFX0, 0x80)
        }

        If (LEqual (0x01, DSEN))
        {
            If (LEqual (TRAP (Increment (Arg0)), 0x00))
            {
                Notify (\_SB.PCI0.GFX0, 0x81)
            }
        }
    }

    Method (P8XH, 2, Serialized)
    {
        If (LEqual (Arg0, 0x00))
        {
            Store (Or (And (P80D, 0xFFFFFF00), Arg1), P80D)
        }

        If (LEqual (Arg0, 0x01))
        {
            Store (Or (And (P80D, 0xFFFF00FF), ShiftLeft (Arg1, 0x08)
                ), P80D)
        }

        If (LEqual (Arg0, 0x02))
        {
            Store (Or (And (P80D, 0xFF00FFFF), ShiftLeft (Arg1, 0x10)
                ), P80D)
        }

        If (LEqual (Arg0, 0x03))
        {
            Store (Or (And (P80D, 0x00FFFFFF), ShiftLeft (Arg1, 0x18)
                ), P80D)
        }

        Store (P80D, P80H)
    }

    Method (PNOT, 0, Serialized)
    {
        If (MPEN)
        {
            If (And (PDC0, 0x08))
            {
                Notify (\_PR.CPU0, 0x80)
                If (And (PDC0, 0x10))
                {
                    Sleep (0x64)
                    Notify (\_PR.CPU0, 0x81)
                }
            }

            If (And (PDC1, 0x08))
            {
                Notify (\_PR.CPU1, 0x80)
                If (And (PDC1, 0x10))
                {
                    Sleep (0x64)
                    Notify (\_PR.CPU1, 0x81)
                }
            }
        }
        Else
        {
            Notify (\_PR.CPU0, 0x80)
            Sleep (0x64)
            Notify (\_PR.CPU0, 0x81)
        }
    }

    Method (TRAP, 1, Serialized)
    {
        Store (Arg0, SMIF)
        Store (0x00, TRP0)
        Return (SMIF)
    }

    Method (GETP, 1, Serialized)
    {
        If (LEqual (And (Arg0, 0x09), 0x00))
        {
            Return (0xFFFFFFFF)
        }

        If (LEqual (And (Arg0, 0x09), 0x08))
        {
            Return (0x0384)
        }

        ShiftRight (And (Arg0, 0x0300), 0x08, Local0)
        ShiftRight (And (Arg0, 0x3000), 0x0C, Local1)
        Return (Multiply (0x1E, Subtract (0x09, Add (Local0, Local1))
            ))
    }

    Method (GDMA, 5, Serialized)
    {
        If (Arg0)
        {
            If (LAnd (Arg1, Arg4))
            {
                Return (0x14)
            }

            If (LAnd (Arg2, Arg4))
            {
                Return (Multiply (Subtract (0x04, Arg3), 0x0F))
            }

            Return (Multiply (Subtract (0x04, Arg3), 0x1E))
        }

        Return (0xFFFFFFFF)
    }

    Method (GETT, 1, Serialized)
    {
        Return (Multiply (0x1E, Subtract (0x09, Add (And (ShiftRight (Arg0, 0x02
            ), 0x03), And (Arg0, 0x03)))))
    }

    Method (GETF, 3, Serialized)
    {
        Name (TMPF, 0x00)
        If (Arg0)
        {
            Or (TMPF, 0x01, TMPF)
        }

        If (And (Arg2, 0x02))
        {
            Or (TMPF, 0x02, TMPF)
        }

        If (Arg1)
        {
            Or (TMPF, 0x04, TMPF)
        }

        If (And (Arg2, 0x20))
        {
            Or (TMPF, 0x08, TMPF)
        }

        If (And (Arg2, 0x4000))
        {
            Or (TMPF, 0x10, TMPF)
        }

        Return (TMPF)
    }

    Method (SETP, 3, Serialized)
    {
        If (LGreater (Arg0, 0xF0))
        {
            Return (0x08)
        }
        Else
        {
            If (And (Arg1, 0x02))
            {
                If (LAnd (LLessEqual (Arg0, 0x78), And (Arg2, 0x02)))
                {
                    Return (0x2301)
                }

                If (LAnd (LLessEqual (Arg0, 0xB4), And (Arg2, 0x01)))
                {
                    Return (0x2101)
                }
            }

            Return (0x1001)
        }
    }

    Method (SDMA, 1, Serialized)
    {
        If (LLessEqual (Arg0, 0x14))
        {
            Return (0x01)
        }

        If (LLessEqual (Arg0, 0x1E))
        {
            Return (0x02)
        }

        If (LLessEqual (Arg0, 0x2D))
        {
            Return (0x01)
        }

        If (LLessEqual (Arg0, 0x3C))
        {
            Return (0x02)
        }

        If (LLessEqual (Arg0, 0x5A))
        {
            Return (0x01)
        }

        Return (0x00)
    }

    Method (SETT, 3, Serialized)
    {
        If (And (Arg1, 0x02))
        {
            If (LAnd (LLessEqual (Arg0, 0x78), And (Arg2, 0x02)))
            {
                Return (0x0B)
            }

            If (LAnd (LLessEqual (Arg0, 0xB4), And (Arg2, 0x01)))
            {
                Return (0x09)
            }
        }

        Return (0x04)
    }

    Scope (\_TZ)
    {
        Name (TPC, 0x78)
        Name (TP85, 0x6E)
        Name (TPTM, 0x4B)
        Name (TPAS, 0x5C)
        Name (TA85, 0x50)
        Name (DS01, 0x00)
        Name (DS02, 0x00)
        ThermalZone (THR1)
        {
            Method (_TMP, 0, NotSerialized)
            {
                If (ECON)
                {
                    Store (DTS1, DS01)
                    Store (DS01, \_SB.PCI0.LPCB.EC0.ECT1)
                    Store (DTS2, DS02)
                    Store (DS02, \_SB.PCI0.LPCB.EC0.ECT2)
                    Store ("Current temp is: ", Debug)
                    Store (DS01, Debug)
                    If (LGreater (DS01, DS02))
                    {
                        Store (\_SB.PCI0.LPCB.EC0.ECT1, \_SB.PCI0.LPCB.EC0.RG5B)
                        Return (Add (0x0AAC, Multiply (DS01, 0x0A)))
                    }
                    Else
                    {
                        Store (\_SB.PCI0.LPCB.EC0.ECT2, \_SB.PCI0.LPCB.EC0.RG5B)
                        Return (Add (0x0AAC, Multiply (DS02, 0x0A)))
                    }
                }
                Else
                {
                    Return (Add (0x0AAC, Multiply (TPTM, 0x0A)))
                }
            }

            Method (_CRT, 0, NotSerialized)
            {
                If (LEqual (\_SB.TJ85, 0x00))
                {
                    Return (Add (0x0AAC, Multiply (TPC, 0x0A)))
                }
                Else
                {
                    Return (Add (0x0AAC, Multiply (TP85, 0x0A)))
                }
            }

            Method (_PSL, 0, NotSerialized)
            {
                If (MPEN)
                {
                    Return (Package (0x02)
                    {
                        \_PR.CPU0, 
                        \_PR.CPU1
                    })
                }

                Return (Package (0x01)
                {
                    \_PR.CPU0
                })
            }

            Method (_PSV, 0, NotSerialized)
            {
                If (LEqual (\_SB.TJ85, 0x00))
                {
                    Return (Add (0x0AAC, Multiply (TPAS, 0x0A)))
                }
                Else
                {
                    Return (Add (0x0AAC, Multiply (TA85, 0x0A)))
                }
            }

            Method (_TC1, 0, NotSerialized)
            {
                Return (0x02)
            }

            Method (_TC2, 0, NotSerialized)
            {
                Return (0x03)
            }

            Method (_TSP, 0, NotSerialized)
            {
                Return (0x32)
            }
        }
    }

    Scope (\_SB)
    {
        Name (WIRE, 0x00)
        Device (MCFG)
        {
            Name (_HID, EisaId ("PNP0C02"))
            Name (_CRS, ResourceTemplate ()
            {
                DWordMemory (ResourceConsumer, PosDecode, MinFixed, MaxFixed, NonCacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0xE0000000,         // Range Minimum
                    0xEFFFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x10000000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
            })
        }

        Device (QBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x01)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (IVIM, 0x04))
                {
                    Notify (\_SB.QBTN, 0x02)
                }

                Return (Buffer (0x01)
                {
                    0x01
                })
            }
        }

        Device (DBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x02)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (IVIM, 0x05))
                {
                    Notify (\_SB.DBTN, 0x02)
                }

                Return (Buffer (0x01)
                {
                    0x02
                })
            }
        }

        Device (MBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x03)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (IVIM, 0x03))
                {
                    Notify (\_SB.MBTN, 0x02)
                }

                Return (Buffer (0x01)
                {
                    0x03
                })
            }
        }

        Device (EBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x04)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (IVIM, 0x10))
                {
                    Notify (\_SB.EBTN, 0x02)
                }

                Return (Buffer (0x01)
                {
                    0x04
                })
            }
        }

        Device (PBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x06)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (IVIM, 0x06))
                {
                    Notify (\_SB.PBTN, 0x02)
                }

                Return (Buffer (0x01)
                {
                    0x06
                })
            }
        }

        Device (VBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x07)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (IVIM, 0x12))
                {
                    Notify (\_SB.VBTN, 0x02)
                }

                Return (Buffer (0x01)
                {
                    0x07
                })
            }
        }

        Device (TBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x08)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (IVIM, 0x11))
                {
                    Notify (\_SB.TBTN, 0x02)
                }

                Return (Buffer (0x01)
                {
                    0x08
                })
            }
        }

        Device (PWRB)
        {
            Name (_HID, EisaId ("PNP0C0C"))
        }

        Device (SLPB)
        {
            Name (_HID, EisaId ("PNP0C0E"))
        }

        Device (ACAD)
        {
            Name (_HID, "ACPI0003")
            Name (_PCL, Package (0x01)
            {
                \_SB
            })
            Name (ACWT, 0x00)
            Method (_PSR, 0, NotSerialized)
            {
                Store (\_SB.ACST, ACWT)
                If (ECON)
                {
                    Store (\_SB.PCI0.LPCB.EC0.SW2S, \_SB.ACST)
                    Store (\_SB.ACST, ACPS)
                }
                Else
                {
                    Store (0x01, \_SB.ACST)
                    Store (\_SB.ACST, ACPS)
                }

                If (LNotEqual (ACWT, \_SB.ACST))
                {
                    TRAP (0x16)
                    Sleep (0x32)
                }

                Return (\_SB.ACST)
            }
        }

        Method (VTOB, 1, NotSerialized)
        {
            Store (0x01, Local0)
            ShiftLeft (Local0, Arg0, Local0)
            Return (Local0)
        }

        Method (BTOV, 1, NotSerialized)
        {
            ShiftRight (Arg0, 0x01, Local0)
            Store (0x00, Local1)
            While (Local0)
            {
                Increment (Local1)
                ShiftRight (Local0, 0x01, Local0)
            }

            Return (Local1)
        }

        Method (MKWD, 2, NotSerialized)
        {
            If (And (Arg1, 0x80))
            {
                Store (0xFFFF0000, Local0)
            }
            Else
            {
                Store (Zero, Local0)
            }

            Or (Local0, Arg0, Local0)
            Or (Local0, ShiftLeft (Arg1, 0x08), Local0)
            Return (Local0)
        }

        Method (POSW, 1, NotSerialized)
        {
            If (And (Arg0, 0x8000))
            {
                If (LEqual (Arg0, 0xFFFF))
                {
                    Return (0xFFFFFFFF)
                }
                Else
                {
                    Not (Arg0, Local0)
                    Increment (Local0)
                    And (Local0, 0xFFFF, Local0)
                    Return (Local0)
                }
            }
            Else
            {
                Return (Arg0)
            }
        }

        Method (GBFE, 3, NotSerialized)
        {
            CreateByteField (Arg0, Arg1, TIDX)
            Store (TIDX, Arg2)
        }

        Method (PBFE, 3, NotSerialized)
        {
            CreateByteField (Arg0, Arg1, TIDX)
            Store (Arg2, TIDX)
        }

        Method (ITOS, 1, NotSerialized)
        {
            Store (Buffer (0x05)
                {
                    0x20, 0x20, 0x20, 0x20, 0x20
                }, Local0)
            Store (Buffer (0x11)
                {
                    "0123456789ABCDEF"
                }, Local7)
            Store (0x05, Local1)
            Store (0x00, Local2)
            Store (0x00, Local3)
            While (Local1)
            {
                Decrement (Local1)
                And (ShiftRight (Arg0, ShiftLeft (Local1, 0x02)), 0x0F, Local4)
                GBFE (Local7, Local4, RefOf (Local5))
                PBFE (Local0, Local2, Local5)
                Increment (Local2)
            }

            Return (Local0)
        }

        Device (BAT0)
        {
            Name (_HID, EisaId ("PNP0C0A"))
            Name (_PCL, Package (0x01)
            {
                \_SB
            })
            Name (PBIF, Package (0x0D)
            {
                0x01, 
                0xFFFFFFFF, 
                0xFFFFFFFF, 
                0x01, 
                0xFFFFFFFF, 
                0xFA, 
                0x96, 
                0x0A, 
                0x19, 
                "BAT1", 
                " ", 
                " ", 
                " "
            })
            Name (PBST, Package (0x04)
            {
                0x00, 
                0xFFFFFFFF, 
                0xFFFFFFFF, 
                0x2710
            })
            Name (BAST, 0x00)
            Name (B1ST, 0x0F)
            Name (B1WT, 0x00)
            Method (_STA, 0, NotSerialized)
            {
                If (ECON)
                {
                    If (\_SB.PCI0.LPCB.EC0.MBTS)
                    {
                        Store (0x1F, B1ST)
                        Store (\_SB.PCI0.LPCB.EC0.BA1C, BCAP)
                    }
                    Else
                    {
                        Store (0x0F, B1ST)
                        Store (0xFF, BCAP)
                    }
                }
                Else
                {
                    Store (0x0F, B1ST)
                }

                Return (B1ST)
            }

            Method (_BIF, 0, NotSerialized)
            {
                If (ECON)
                {
                    If (\_SB.PCI0.LPCB.EC0.MBTS)
                    {
                        UPBI ()
                    }
                    Else
                    {
                        IVBI ()
                    }
                }
                Else
                {
                    IVBI ()
                }

                Return (PBIF)
            }

            Method (_BST, 0, NotSerialized)
            {
                If (ECON)
                {
                    If (\_SB.PCI0.LPCB.EC0.MBTS)
                    {
                        UPBS ()
                    }
                    Else
                    {
                        IVBS ()
                    }
                }
                Else
                {
                    IVBS ()
                }

                Return (PBST)
            }

            Method (UPBI, 0, NotSerialized)
            {
                If (LNot (\_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x10, RefOf (Local5))))
                {
                    If (LAnd (Local5, LNot (And (Local5, 0x8000))))
                    {
                        ShiftRight (Local5, 0x05, Local5)
                        ShiftLeft (Local5, 0x05, Local5)
                        Store (Local5, Index (PBIF, 0x02))
                        Divide (Local5, 0x64, , Local2)
                        Add (Local2, 0x01, Local2)
                        Multiply (Local2, 0x05, Local4)
                        Add (Local4, 0x02, Index (PBIF, 0x05))
                        Multiply (Local2, 0x03, Local4)
                        Add (Local4, 0x02, Index (PBIF, 0x06))
                    }
                }

                If (\_SB.PCI0.LPCB.EC0.MBNH)
                {
                    Store (0x2328, Index (PBIF, 0x01))
                    Store (0x1C20, Index (PBIF, 0x04))
                    Store ("OANI$", Index (PBIF, 0x09))
                    Store ("NiMH", Index (PBIF, 0x0B))
                }
                Else
                {
                    Store (0x1770, Index (PBIF, 0x01))
                    Store (0x39D0, Index (PBIF, 0x04))
                    Sleep (0x32)
                    Store ("LION", Index (PBIF, 0x0B))
                }

                Store ("Primary", Index (PBIF, 0x09))
                UPUM ()
                Store (0x01, Index (PBIF, 0x00))
            }

            Method (UPUM, 0, NotSerialized)
            {
                Store (Buffer (0x0A)
                    {
                        /* 0000 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0008 */    0x00, 0x00
                    }, Local0)
                Store (Buffer (0x05)
                    {
                        0x36, 0x35, 0x35, 0x33, 0x35
                    }, Local6)
                Store (Buffer (0x05)
                    {
                        0x31, 0x32, 0x33, 0x32, 0x31
                    }, Local7)
                Store ("Hewlett-Packard", Index (PBIF, 0x0C))
            }

            Method (UPBS, 0, NotSerialized)
            {
                Store (\_SB.PCI0.LPCB.EC0.MBRM, Local5)
                If (LNot (And (Local5, 0x8000)))
                {
                    ShiftRight (Local5, 0x05, Local5)
                    ShiftLeft (Local5, 0x05, Local5)
                    If (LNotEqual (Local5, DerefOf (Index (PBST, 0x02))))
                    {
                        Store (Local5, Index (PBST, 0x02))
                    }
                }

                Store (\_SB.PCI0.LPCB.EC0.MBCV, Index (PBST, 0x03))
                Store (\_SB.PCI0.LPCB.EC0.MBST, Index (PBST, 0x00))
                Store (\_SB.PCI0.LPCB.EC0.BA1C, BCAP)
            }

            Method (IVBI, 0, NotSerialized)
            {
                Store (0xFFFFFFFF, Index (PBIF, 0x01))
                Store (0xFFFFFFFF, Index (PBIF, 0x02))
                Store (0xFFFFFFFF, Index (PBIF, 0x04))
                Store ("Bad", Index (PBIF, 0x09))
                Store ("      ", Index (PBIF, 0x0A))
                Store ("Bad", Index (PBIF, 0x0B))
                Store ("Bad", Index (PBIF, 0x0C))
            }

            Method (IVBS, 0, NotSerialized)
            {
                Store (0x00, Index (PBST, 0x00))
                Store (0xFFFFFFFF, Index (PBST, 0x01))
                Store (0xFFFFFFFF, Index (PBST, 0x02))
                Store (0x2710, Index (PBST, 0x03))
                Store (0xFF, BCAP)
            }
        }

        OperationRegion (EXCO, SystemIO, 0x72, 0x02)
        Field (EXCO, ByteAcc, NoLock, Preserve)
        {
            INDX,   8, 
            DATA,   8
        }

        IndexField (INDX, DATA, ByteAcc, NoLock, Preserve)
        {
                    Offset (0x30), 
            BTWL,   2, 
            BTLS,   1, 
            BWLS,   1, 
            WWLS,   1, 
                    Offset (0x31), 
            WLSU,   1, 
            BTSU,   1, 
                ,   2, 
            ACST,   1, 
            PAID,   1, 
            CHPD,   2, 
                    Offset (0x67), 
                ,   2, 
            PFID,   3, 
            TJ85,   1, 
                    Offset (0x68), 
            CMPE,   8, 
                ,   1, 
            PTPE,   2
        }

        Device (LID)
        {
            Name (_HID, EisaId ("PNP0C0D"))
            Name (LSTS, 0x00)
            Method (_LID, 0, NotSerialized)
            {
                If (ECON)
                {
                    If (\_SB.PCI0.LPCB.EC0.LIDS)
                    {
                        Store (Zero, LSTS)
                    }
                    Else
                    {
                        Store (One, LSTS)
                    }
                }
                Else
                {
                    Store (One, LSTS)
                }

                Return (LSTS)
            }
        }

        Device (WMID)
        {
            Name (Z00C, Package (0x0E)
            {
                0x04, 
                0x04, 
                0x04, 
                0x00, 
                0x04, 
                0x04, 
                0x00, 
                0x00, 
                0x04, 
                0x04, 
                0x0C, 
                0x00, 
                0x00, 
                0x00
            })
            Method (Z00D, 2, NotSerialized)
            {
                CreateDWordField (Arg1, 0x00, Z00E)
                CreateDWordField (Arg1, 0x04, Z00F)
                CreateDWordField (Arg1, 0x08, Z00G)
                CreateDWordField (Arg1, 0x0C, Z00H)
                If (LEqual (Arg0, 0x01))
                {
                    Store (0x00, Local0)
                }

                If (LEqual (Arg0, 0x02))
                {
                    Store (0x04, Local0)
                }

                If (LEqual (Arg0, 0x03))
                {
                    Store (0x80, Local0)
                }

                If (LEqual (Arg0, 0x04))
                {
                    Store (0x0400, Local0)
                }

                If (LEqual (Arg0, 0x05))
                {
                    Store (0x1000, Local0)
                }

                Store (Buffer (Add (0x08, Local0)) {}, Local1)
                CreateDWordField (Local1, 0x00, Z00I)
                CreateDWordField (Local1, 0x04, Z00J)
                Store (0x4C494146, Z00I)
                Store (0x02, Z00J)
                If (LEqual (Z00E, 0x55434553))
                {
                    Store (0x03, Z00J)
                    BreakPoint
                    If (LEqual (Z00F, 0x01))
                    {
                        Store (0x04, Z00J)
                        If (LEqual (Z00G, 0x05))
                        {
                            Store (^Z00K (), Local2)
                            Store (0x00, Z00J)
                        }

                        If (LEqual (Z00G, 0x0E))
                        {
                            Store (^Z00L (), Local2)
                            Store (0x00, Z00J)
                        }

                        If (LEqual (Z00G, 0x07))
                        {
                            If (Z00H)
                            {
                                Store (DerefOf (Index (Arg1, 0x10)), Local3)
                                Store (^Z00M (Local3), Local2)
                                Store (0x00, Z00J)
                            }
                            Else
                            {
                                Store (0x05, Z00J)
                            }
                        }

                        If (LEqual (Z00G, 0x01))
                        {
                            Store (^Z00N (), Local2)
                            Store (0x00, Z00J)
                        }

                        If (LEqual (Z00G, 0x08))
                        {
                            Store (^Z00O (), Local2)
                            Store (0x00, Z00J)
                        }

                        If (LEqual (Z00G, 0x09))
                        {
                            Store (^Z00P (), Local2)
                            Store (0x00, Z00J)
                        }

                        If (LEqual (Z00G, 0x0A))
                        {
                            Store (^Z00Q (), Local2)
                            Store (0x00, Z00J)
                        }

                        If (LEqual (Z00G, 0x0C))
                        {
                            Store (^Z00R (), Local2)
                            Store (0x00, Z00J)
                        }
                    }

                    If (LEqual (Z00F, 0x02))
                    {
                        Store (0x04, Z00J)
                        If (LAnd (LGreater (Z00G, 0x00), LLessEqual (Z00G, 0x0C)))
                        {
                            If (LLess (Z00H, DerefOf (Index (Z00C, Subtract (Z00G, 0x01)
                                ))))
                            {
                                Store (0x05, Z00J)
                            }
                            Else
                            {
                                CreateDWordField (Arg1, 0x10, Z00S)
                                If (LEqual (Z00G, 0x05))
                                {
                                    Store (^Z00T (Z00S), Local2)
                                    Store (0x00, Z00J)
                                }

                                If (LEqual (Z00G, 0x01))
                                {
                                    Store (^Z00U (Z00S), Local2)
                                    Store (0x00, Z00J)
                                }

                                If (LEqual (Z00G, 0x09))
                                {
                                    Store (^Z00V (Z00S), Local2)
                                    Store (0x00, Z00J)
                                }

                                If (LEqual (Z00G, 0x0A))
                                {
                                    Store (^Z00W (Z00S), Local2)
                                    Store (0x00, Z00J)
                                }
                            }
                        }
                    }
                }

                If (LEqual (Z00J, 0x00))
                {
                    Store (DerefOf (Index (Local2, 0x00)), Z00J)
                    If (LEqual (Z00J, 0x00))
                    {
                        If (LLessEqual (DerefOf (Index (Local2, 0x01)), Local0))
                        {
                            Store (0x00, Local0)
                            While (LLess (Local0, DerefOf (Index (Local2, 0x01))))
                            {
                                Store (DerefOf (Index (DerefOf (Index (Local2, 0x02)), Local0)), 
                                    Index (Local1, Add (Local0, 0x08)))
                                Increment (Local0)
                            }

                            Store (0x53534150, Z00I)
                        }
                        Else
                        {
                            Store (0x05, Z00J)
                        }
                    }
                }

                Return (Local1)
            }

            Name (_HID, "PNP0C14")
            Name (_UID, 0x00)
            Name (Z00X, 0x00)
            Name (Z00Y, 0x00)
            Name (BUFF, Buffer (0x04)
            {
                0x00, 0x00, 0x00, 0x00
            })
            CreateByteField (BUFF, 0x00, OB0)
            CreateByteField (BUFF, 0x01, OB1)
            CreateByteField (BUFF, 0x02, OB2)
            CreateByteField (BUFF, 0x03, OB3)
            Name (_WDG, Buffer (0x50)
            {
                /* 0000 */    0x34, 0xF0, 0xB7, 0x5F, 0x63, 0x2C, 0xE9, 0x45, 
                /* 0008 */    0xBE, 0x91, 0x3D, 0x44, 0xE2, 0xC7, 0x07, 0xE4, 
                /* 0010 */    0x41, 0x44, 0x01, 0x02, 0x79, 0x42, 0xF2, 0x95, 
                /* 0018 */    0x7B, 0x4D, 0x34, 0x43, 0x93, 0x87, 0xAC, 0xCD, 
                /* 0020 */    0xC6, 0x7E, 0xF6, 0x1C, 0x80, 0x00, 0x01, 0x08, 
                /* 0028 */    0x21, 0x12, 0x90, 0x05, 0x66, 0xD5, 0xD1, 0x11, 
                /* 0030 */    0xB2, 0xF0, 0x00, 0xA0, 0xC9, 0x06, 0x29, 0x10, 
                /* 0038 */    0x41, 0x45, 0x01, 0x00, 0xD4, 0x2B, 0x99, 0xD0, 
                /* 0040 */    0x7C, 0xA4, 0xFE, 0x4E, 0xB0, 0x72, 0x32, 0x4A, 
                /* 0048 */    0xEC, 0x92, 0x29, 0x6C, 0x42, 0x43, 0x01, 0x00
            })
            Method (WQBC, 1, NotSerialized)
            {
                Store ("HP WMI WQBC)", Debug)
                TRAP (0x17)
                Store (WMIA, Local0)
                If (ECON)
                {
                    If (LEqual (\_SB.PCI0.LPCB.EC0.LIDS, 0x01))
                    {
                        And (Local0, 0xFE, Local0)
                    }
                }

                Return (Local0)
            }

            Method (WMAD, 3, NotSerialized)
            {
                Return (Z00D (Arg1, Arg2))
            }

            Method (Z00K, 0, NotSerialized)
            {
                Store ("HP WMI Command 0x5 (BIOS Read)", Debug)
                Store (0x01, \_SB.WIRE)
                And (\_SB.BTWL, 0x03, Local0)
                Or (Local0, 0x20, OB0)
                Store (\_SB.WWLS, Local1)
                ShiftLeft (Local1, 0x01, Local1)
                Store (\_SB.BWLS, Local2)
                ShiftLeft (Local2, 0x01, Local2)
                Store (\_SB.BTLS, Local3)
                ShiftLeft (Local3, 0x03, Local3)
                Or (Local1, Local3, Local1)
                Or (Local2, Local3, Local2)
                If (GP26)
                {
                    If (LNot (\_SB.WWLS))
                    {
                        Store (0x00, GP26)
                    }

                    If (LNot (\_SB.BTLS))
                    {
                        Store (0x00, GP26)
                    }
                }

                If (GP25)
                {
                    If (LNot (\_SB.BWLS))
                    {
                        Store (0x00, GP25)
                    }

                    If (LNot (\_SB.BTLS))
                    {
                        Store (0x00, GP25)
                    }
                }

                Or (GP26, Local1, Local1)
                Or (GP25, Local2, Local2)
                Store (0x00, OB2)
                Store (0x00, OB1)
                If (\_SB.WLSU)
                {
                    Or (Local1, 0x04, Local1)
                }

                If (\_SB.BTSU)
                {
                    Or (Local2, 0x04, Local2)
                }

                If (GP26)
                {
                    Or (Local1, 0x10, Local1)
                }
                Else
                {
                    And (Local1, 0xEF, Local1)
                }

                If (And (\_SB.BTWL, 0x01))
                {
                    Store (Local1, OB1)
                }

                If (And (\_SB.BTWL, 0x02))
                {
                    Store (Local2, OB2)
                }

                Store (0x00, OB3)
                Store (Package (0x03)
                    {
                        0x00, 
                        0x04, 
                        Buffer (0x04)
                        {
                            0x01, 0x02, 0x03, 0x04
                        }
                    }, Local0)
                Store (OB0, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                Store (OB1, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                Store (OB2, Index (DerefOf (Index (Local0, 0x02)), 0x02))
                Store (OB3, Index (DerefOf (Index (Local0, 0x02)), 0x03))
                Return (Local0)
            }

            Method (Z00T, 1, NotSerialized)
            {
                Store ("HP WMI Command 0x5 (BIOS Write)", Debug)
                If (And (\_SB.BTWL, 0x03))
                {
                    If (And (Arg0, 0x0800))
                    {
                        If (And (Arg0, 0x08))
                        {
                            Store (0x01, \_SB.WWLS)
                            Store (0x01, \_SB.BWLS)
                            If (\_SB.WLSU)
                            {
                                If (\_SB.BTLS)
                                {
                                    Store (0x01, GP26)
                                }
                            }
                            Else
                            {
                                Store (0x00, GP26)
                            }

                            If (\_SB.BTSU)
                            {
                                If (\_SB.BTLS)
                                {
                                    Store (0x01, GP25)
                                }
                            }
                            Else
                            {
                                Store (0x00, GP25)
                            }
                        }
                        Else
                        {
                            Store (0x00, \_SB.WWLS)
                            Store (0x00, GP26)
                            Store (0x00, \_SB.BWLS)
                            Store (0x00, GP25)
                        }
                    }

                    If (And (Arg0, 0x0100))
                    {
                        If (And (Arg0, 0x01))
                        {
                            Store (0x01, \_SB.WWLS)
                            If (\_SB.WLSU)
                            {
                                If (\_SB.BTLS)
                                {
                                    Store (0x01, GP26)
                                }
                            }
                            Else
                            {
                                Store (0x00, GP26)
                            }
                        }
                        Else
                        {
                            Store (0x00, \_SB.WWLS)
                            Store (0x00, GP26)
                        }
                    }

                    If (And (Arg0, 0x0200))
                    {
                        If (And (Arg0, 0x02))
                        {
                            Store (0x01, \_SB.BWLS)
                            If (\_SB.BTSU)
                            {
                                If (\_SB.BTLS)
                                {
                                    Store (0x01, GP25)
                                }
                            }
                            Else
                            {
                                Store (0x00, GP25)
                            }
                        }
                        Else
                        {
                            Store (0x00, \_SB.BWLS)
                            Store (0x00, GP25)
                        }
                    }

                    Return (Package (0x02)
                    {
                        0x00, 
                        0x00
                    })
                }
                Else
                {
                    Return (Package (0x02)
                    {
                        0x0D, 
                        0x00
                    })
                }
            }

            Method (Z00L, 0, NotSerialized)
            {
                Store ("HP WMI Command 0xE (BIOS Read)", Debug)
                Store (0x00, Local0)
                Store (Buffer (0x0A)
                    {
                        /* 0000 */    0x01, 0x01, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0008 */    0x00, 0x00
                    }, Local2)
                TRAP (0x1A)
                If (LNotEqual (Z000, 0xFF))
                {
                    Store (Z000, Index (Local2, 0x02))
                    Store (Z001, Index (Local2, 0x03))
                    Store (Z002, Index (Local2, 0x04))
                    Store (Z003, Index (Local2, 0x05))
                    Store (Z004, Index (Local2, 0x06))
                    Store (Z005, Index (Local2, 0x07))
                    Store (Z006, Index (Local2, 0x08))
                    Store (Z007, Index (Local2, 0x09))
                    Store (Local2, Local1)
                    Add (Local0, 0x0A, Local0)
                }

                Store (Package (0x03) {}, Local2)
                Store (0x00, Index (Local2, 0x00))
                Store (Local0, Index (Local2, 0x01))
                Store (Local1, Index (Local2, 0x02))
                Return (Local2)
            }

            Method (Z00M, 1, NotSerialized)
            {
                Store ("HP WMI Command 0x7 (BIOS Read)", Debug)
                Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0xFFFF)
                If (LNot (ECON))
                {
                    Store (Package (0x02)
                        {
                            0x0D, 
                            0x00
                        }, Local0)
                    Sleep (0x96)
                    Release (\_SB.PCI0.LPCB.EC0.MUT0)
                    Return (Local0)
                }

                If (Arg0)
                {
                    Store (Package (0x02)
                        {
                            0x06, 
                            0x00
                        }, Local0)
                    Sleep (0x96)
                    Release (\_SB.PCI0.LPCB.EC0.MUT0)
                    Return (Local0)
                }

                If (LNot (\_SB.PCI0.LPCB.EC0.MBTS))
                {
                    Store (Package (0x02)
                        {
                            0x06, 
                            0x00
                        }, Local0)
                    Sleep (0x96)
                    Release (\_SB.PCI0.LPCB.EC0.MUT0)
                    Return (Local0)
                }

                Store (Package (0x03)
                    {
                        0x00, 
                        0x80, 
                        Buffer (0x80) {}
                    }, Local0)
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x18, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x01))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x10, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x03))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x02))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x0F, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x05))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x04))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x0C, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x07))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x06))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x17, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x09))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x08))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x08, RefOf (Local1))
                Subtract (Local1, 0x0AAA, Local1)
                Divide (Local1, 0x0A, Local2, Local1)
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x0B))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x0A))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x09, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x0D))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x0C))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x0A, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x0F))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x0E))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x19, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x11))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x10))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x16, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x13))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x12))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x3F, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x15))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x14))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x3E, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x17))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x16))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x3D, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x19))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x18))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x3C, RefOf (Local1))
                Divide (Local1, 0x0100, Local2, Index (DerefOf (Index (Local0, 0x02)), 
                    0x1B))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x1A))
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x1C, RefOf (Local1))
                Store (ITOS (ToBCD (Local1)), Local3)
                Store (0x1C, Local2)
                Store (0x00, Local4)
                Store (SizeOf (Local3), Local1)
                While (Local1)
                {
                    GBFE (Local3, Local4, RefOf (Local5))
                    PBFE (DerefOf (Index (Local0, 0x02)), Local2, Local5)
                    Decrement (Local1)
                    Increment (Local2)
                    Increment (Local4)
                }

                Store (0x20, Index (DerefOf (Index (Local0, 0x02)), Local2))
                Increment (Local2)
                \_SB.PCI0.LPCB.EC0.SMRD (0x09, 0x16, 0x1B, RefOf (Local1))
                And (Local1, 0x1F, Local7)
                Store (ITOS (ToBCD (Local7)), Local6)
                And (Local1, 0x01E0, Local7)
                ShiftRight (Local7, 0x05, Local7)
                Store (ITOS (ToBCD (Local7)), Local5)
                ShiftRight (Local1, 0x09, Local7)
                Add (Local7, 0x07BC, Local7)
                Store (ITOS (ToBCD (Local7)), Local4)
                Store (0x02, Local1)
                Store (0x03, Local7)
                While (Local1)
                {
                    GBFE (Local5, Local7, RefOf (Local3))
                    PBFE (DerefOf (Index (Local0, 0x02)), Local2, Local3)
                    Decrement (Local1)
                    Increment (Local2)
                    Increment (Local7)
                }

                Store ("/", Index (DerefOf (Index (Local0, 0x02)), Local2))
                Increment (Local2)
                Store (0x02, Local1)
                Store (0x03, Local7)
                While (Local1)
                {
                    GBFE (Local6, Local7, RefOf (Local3))
                    PBFE (DerefOf (Index (Local0, 0x02)), Local2, Local3)
                    Decrement (Local1)
                    Increment (Local2)
                    Increment (Local7)
                }

                Store ("/", Index (DerefOf (Index (Local0, 0x02)), Local2))
                Increment (Local2)
                Store (0x04, Local1)
                Store (0x01, Local7)
                While (Local1)
                {
                    GBFE (Local4, Local7, RefOf (Local3))
                    PBFE (DerefOf (Index (Local0, 0x02)), Local2, Local3)
                    Decrement (Local1)
                    Increment (Local2)
                    Increment (Local7)
                }

                Store (0x00, Index (DerefOf (Index (Local0, 0x02)), Local2))
                \_SB.PCI0.LPCB.EC0.SMRD (0x0B, 0x16, 0x20, RefOf (Local1))
                Store (SizeOf (Local1), Local3)
                Store (0x2C, Local2)
                Store (0x00, Local4)
                While (Local3)
                {
                    GBFE (Local1, Local4, RefOf (Local5))
                    PBFE (DerefOf (Index (Local0, 0x02)), Local2, Local5)
                    Decrement (Local3)
                    Increment (Local2)
                    Increment (Local4)
                }

                Store (0x00, Index (DerefOf (Index (Local0, 0x02)), Local2))
                Sleep (0x96)
                Release (\_SB.PCI0.LPCB.EC0.MUT0)
                Return (Local0)
            }

            Method (Z00N, 0, NotSerialized)
            {
                Store ("HP WMI Command 0x1 (BIOS Read)", Debug)
                Store (WQBC (0x00), OB0)
                Or (OB0, 0x01, OB0)
                Store (0x00, OB1)
                Store (0x00, OB2)
                Store (0x00, OB3)
                Store (Package (0x03)
                    {
                        0x00, 
                        0x04, 
                        Buffer (0x04)
                        {
                            0x01, 0x02, 0x03, 0x04
                        }
                    }, Local0)
                Store (OB0, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                Store (OB1, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                Store (OB2, Index (DerefOf (Index (Local0, 0x02)), 0x02))
                Store (OB3, Index (DerefOf (Index (Local0, 0x02)), 0x03))
                Return (Local0)
            }

            Method (Z00U, 1, NotSerialized)
            {
                Store ("HP WMI Command 0x1 (BIOS Write)", Debug)
                And (Arg0, 0x07, Local0)
                If (LLessEqual (\_SB.PFID, 0x01))
                {
                    If (LEqual (\_SB.PCI0.GFX0.SWIT, 0x00))
                    {
                        Store (0x18, SMIF)
                        Store (0x00, TRP0)
                        Store (WMIO, Local1)
                        If (LEqual (Local0, Local1))
                        {
                            Return (Package (0x02)
                            {
                                0x00, 
                                0x00
                            })
                        }
                        Else
                        {
                            Store (0x00, NSTE)
                            If (LEqual (Local0, 0x01))
                            {
                                Store ("LCD", Debug)
                                Or (0x0808, NSTE, NSTE)
                            }

                            If (LEqual (Local0, 0x02))
                            {
                                Store ("CRT", Debug)
                                Or (0x0101, NSTE, NSTE)
                            }

                            If (LEqual (Local0, 0x03))
                            {
                                Store ("Both", Debug)
                                Or (0x0909, NSTE, NSTE)
                            }

                            If (LEqual (Local0, 0x04))
                            {
                                Store ("TV", Debug)
                                Or (0x0202, NSTE, NSTE)
                            }

                            If (LEqual (Local0, 0x05))
                            {
                                Store ("TV+LCD", Debug)
                                Or (0x0A0A, NSTE, NSTE)
                            }

                            If (LEqual (Local0, 0x06))
                            {
                                Store ("TV+CRT", Debug)
                                Or (0x0303, NSTE, NSTE)
                            }

                            If (LEqual (Local0, 0x07))
                            {
                                Store ("TV+CRT+LCD", Debug)
                                Or (0x0B0B, NSTE, NSTE)
                            }

                            Store (CADL, PADL)
                            If (LGreaterEqual (OSYS, 0x07D1))
                            {
                                Notify (\_SB.PCI0, 0x00)
                            }
                            Else
                            {
                                Notify (\_SB.PCI0.GFX0, 0x00)
                            }

                            Sleep (0x02EE)
                            Notify (\_SB.PCI0.GFX0, 0x80)
                            Return (Package (0x02)
                            {
                                0x00, 
                                0x00
                            })
                        }
                    }
                    Else
                    {
                        Return (Package (0x02)
                        {
                            0x00, 
                            0x00
                        })
                    }
                }
                Else
                {
                    TRAP (0x1B)
                    Store (Z008, Local1)
                    If (LEqual (Local0, Local1))
                    {
                        Return (Package (0x02)
                        {
                            0x00, 
                            0x00
                        })
                    }
                    Else
                    {
                        If (LEqual (Local0, 0x01))
                        {
                            Store ("LCD", Debug)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.LCDA)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.CRTA)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.TV0A)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.HDTV)
                        }

                        If (LEqual (Local0, 0x02))
                        {
                            Store ("CRT", Debug)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.LCDA)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.CRTA)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.TV0A)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.HDTV)
                        }

                        If (LEqual (Local0, 0x03))
                        {
                            Store ("Both", Debug)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.LCDA)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.CRTA)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.TV0A)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.HDTV)
                        }

                        If (LEqual (Local0, 0x04))
                        {
                            Store ("TV", Debug)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.LCDA)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.CRTA)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.TV0A)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.HDTV)
                        }

                        If (LEqual (Local0, 0x05))
                        {
                            Store ("LCD+TV", Debug)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.LCDA)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.CRTA)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.TV0A)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.HDTV)
                        }

                        If (LEqual (Local0, 0x06))
                        {
                            Store ("CRT+TV", Debug)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.LCDA)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.CRTA)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.TV0A)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.HDTV)
                        }

                        If (LEqual (Local0, 0x07))
                        {
                            Store ("LCD+CRT+TV", Debug)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.LCDA)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.CRTA)
                            Store (0x01, \_SB.PCI0.PEGP.VGA.TV0A)
                            Store (0x00, \_SB.PCI0.PEGP.VGA.HDTV)
                        }

                        If (LGreaterEqual (OSYS, 0x07D1))
                        {
                            Notify (\_SB.PCI0, 0x00)
                        }
                        Else
                        {
                            Notify (\_SB.PCI0.PEGP.VGA, 0x00)
                        }

                        Sleep (0x02EE)
                        Notify (\_SB.PCI0.PEGP.VGA, 0x80)
                        Return (Package (0x02)
                        {
                            0x00, 
                            0x00
                        })
                    }
                }
            }

            Method (Z00O, 0, NotSerialized)
            {
                Store ("HP WMI Command 0x8 (BIOS Read)", Debug)
                Store (Package (0x03)
                    {
                        0x00, 
                        0x80, 
                        Buffer (0x80)
                        {
                            /* 0000 */    0x31, 0x01, 0x9B, 0x01, 0xFF, 0x01, 0x63, 0x02, 
                            /* 0008 */    0xAE, 0x01, 0x64, 0x02, 0x9D, 0x01, 0xB6, 0x01, 
                            /* 0010 */    0xB7, 0x01, 0x65, 0x02, 0x66, 0x02, 0x67, 0x02, 
                            /* 0018 */    0x68, 0x02, 0xFF, 0xFF, 0xE4, 0x20, 0xE6, 0x20, 
                            /* 0020 */    0x42, 0x21, 0x70, 0x21, 0x00, 0x00
                        }
                    }, Local0)
                Return (Local0)
            }

            Method (Z00P, 0, NotSerialized)
            {
                Store ("HP WMI Command 0x9 (BIOS Read)", Debug)
                Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0xFFFF)
                Store (Package (0x03)
                    {
                        0x00, 
                        0x04, 
                        Buffer (0x04) {}
                    }, Local0)
                Store (\_SB.PCI0.LPCB.EC0.Z00Z (), Index (DerefOf (Index (Local0, 0x02)), 0x00))
                Release (\_SB.PCI0.LPCB.EC0.MUT0)
                Return (Local0)
            }

            Method (Z00V, 1, NotSerialized)
            {
                Store ("HP WMI Command 0x9 (BIOS Write)", Debug)
                Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0xFFFF)
                \_SB.PCI0.LPCB.EC0.Z010 (Arg0)
                Release (\_SB.PCI0.LPCB.EC0.MUT0)
                Return (Package (0x02)
                {
                    0x00, 
                    0x00
                })
            }

            Method (Z011, 0, NotSerialized)
            {
                Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0xFFFF)
                Store (Package (0x03)
                    {
                        0x00, 
                        0x04, 
                        Buffer (0x04) {}
                    }, Local0)
                If (ECON)
                {
                    Store (\_SB.PCI0.LPCB.EC0.QBHK, Local1)
                }

                Release (\_SB.PCI0.LPCB.EC0.MUT0)
                If (LEqual (Local1, 0x0D))
                {
                    Store ("Fn+ESC Pressed", Debug)
                    Store (0x31, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                    Store (0x01, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                }

                If (LEqual (Local1, 0x01))
                {
                    Store ("Fn+F1 Pressed", Debug)
                    Store (0x9B, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                    Store (0x01, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                }

                If (LEqual (Local1, 0x04))
                {
                    TRAP (0x19)
                    If (LEqual (EXTM, 0x00))
                    {
                        If (LEqual (EXCM, 0x00))
                        {
                            Store ("Fn+F4 Pressed", Debug)
                            If (LLessEqual (\_SB.PFID, 0x01))
                            {
                                If (IGDS)
                                {
                                    Store (0x01, TLST)
                                    HKDS (0x0A)
                                    \_SB.PCI0.LPCB.EC0.BPOL (0x03)
                                    Store (0x00, Local3)
                                    Store (0x00, Local4)
                                    Store (0x00, Local5)
                                    Store (0xAE, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                                    Store (0x01, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                                    ShiftLeft (And (NSTE, 0x01), 0x01, Local3)
                                    ShiftLeft (And (NSTE, 0x02), 0x01, Local4)
                                    ShiftRight (And (NSTE, 0x08), 0x03, Local5)
                                    Or (Local3, Local4, Local3)
                                    Or (Local3, Local5, Local3)
                                    Store (Local3, Index (DerefOf (Index (Local0, 0x02)), 0x02))
                                    ShiftLeft (And (CSTE, 0x01), 0x01, Local3)
                                    ShiftLeft (And (CSTE, 0x02), 0x01, Local4)
                                    ShiftRight (And (CSTE, 0x08), 0x03, Local5)
                                    Or (Local3, Local4, Local3)
                                    Or (Local3, Local5, Local3)
                                    Store (Local3, Index (DerefOf (Index (Local0, 0x02)), 0x03))
                                }
                            }
                            Else
                            {
                                TRAP (0x1B)
                                Store (Z00A, Local3)
                                Store (And (Local3, 0x01), \_SB.PCI0.PEGP.VGA.LCDA)
                                Store (ShiftRight (And (Local3, 0x02), 0x01), \_SB.PCI0.PEGP.VGA.CRTA)
                                Store (ShiftRight (And (Local3, 0x04), 0x02), \_SB.PCI0.PEGP.VGA.TV0A)
                                Store (ShiftRight (And (Local3, 0x08), 0x03), \_SB.PCI0.PEGP.VGA.HDTV)
                                Notify (\_SB.PCI0.PEGP.VGA, 0x80)
                                Store (0xAE, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                                Store (0x01, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                                Store (Z00A, Index (DerefOf (Index (Local0, 0x02)), 0x02))
                                Store (Z008, Local5)
                                Store (Local5, Index (DerefOf (Index (Local0, 0x02)), 0x03))
                            }
                        }
                    }
                }

                If (LEqual (Local1, 0x06))
                {
                    Store ("Fn+F6 Pressed", Debug)
                    Store (0x9D, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                    Store (0x01, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                }

                If (LEqual (Local1, 0x07))
                {
                    Store ("Fn+F7 Pressed", Debug)
                    If (LEqual (OSYS, 0x07D6))
                    {
                        If (IGDS)
                        {
                            Notify (\_SB.PCI0.GFX0.DD04, 0x87)
                        }
                        Else
                        {
                            Notify (\_SB.PCI0.PEGP.VGA.LCD, 0x87)
                        }
                    }
                    Else
                    {
                        Store (0x15, SMIF)
                        Store (0x00, TRP0)
                    }

                    Sleep (0x32)
                    Store (0xB6, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                    Store (0x01, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                }

                If (LEqual (Local1, 0x08))
                {
                    Store ("Fn+F8 Pressed", Debug)
                    If (LEqual (OSYS, 0x07D6))
                    {
                        If (IGDS)
                        {
                            Notify (\_SB.PCI0.GFX0.DD04, 0x86)
                        }
                        Else
                        {
                            Notify (\_SB.PCI0.PEGP.VGA.LCD, 0x86)
                        }
                    }
                    Else
                    {
                        Store (0x14, SMIF)
                        Store (0x00, TRP0)
                    }

                    Sleep (0x32)
                    Store (0xB7, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                    Store (0x01, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                }

                Return (Local0)
            }

            Method (Z00Q, 0, NotSerialized)
            {
                Store ("HP WMI Command 0xA (BIOS Read)", Debug)
                Return (Z011 ())
            }

            Method (Z00W, 1, NotSerialized)
            {
                Store ("HP WMI Command 0xA (BIOS Write)", Debug)
                And (Arg0, 0xFF, Local1)
                And (Arg0, 0xFF00, Local3)
                ShiftRight (Local3, 0x08, Local2)
                Store (Package (0x03)
                    {
                        0x00, 
                        0x04, 
                        Buffer (0x04) {}
                    }, Local0)
                Store (Local1, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                Store (Local2, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                If (LEqual (Arg0, 0x01AE))
                {
                    If (LLessEqual (\_SB.PFID, 0x01))
                    {
                        Store (0x01, TLST)
                        HKDS (0x0A)
                        ShiftLeft (And (NSTE, 0x01), 0x01, Local3)
                        ShiftLeft (And (NSTE, 0x02), 0x01, Local4)
                        ShiftRight (And (NSTE, 0x08), 0x03, Local5)
                        Or (Local3, Local4, Local3)
                        Or (Local3, Local5, Local3)
                        Store (Local3, Index (DerefOf (Index (Local0, 0x02)), 0x02))
                        ShiftLeft (And (CSTE, 0x01), 0x01, Local3)
                        ShiftLeft (And (CSTE, 0x02), 0x01, Local4)
                        ShiftRight (And (CSTE, 0x08), 0x03, Local5)
                        Or (Local3, Local4, Local3)
                        Or (Local3, Local5, Local3)
                        Store (Local3, Index (DerefOf (Index (Local0, 0x02)), 0x03))
                    }
                    Else
                    {
                        TRAP (0x1B)
                        Store (Z00A, Local3)
                        Store (And (Local3, 0x01), \_SB.PCI0.PEGP.VGA.LCDA)
                        Store (ShiftRight (And (Local3, 0x02), 0x01), \_SB.PCI0.PEGP.VGA.CRTA)
                        Store (ShiftRight (And (Local3, 0x04), 0x02), \_SB.PCI0.PEGP.VGA.TV0A)
                        Store (ShiftRight (And (Local3, 0x08), 0x03), \_SB.PCI0.PEGP.VGA.HDTV)
                        Notify (\_SB.PCI0.PEGP.VGA, 0x80)
                        Store (Z00A, Index (DerefOf (Index (Local0, 0x02)), 0x02))
                        Store (Z008, Index (DerefOf (Index (Local0, 0x02)), 0x03))
                    }
                }

                Return (Local0)
            }

            Method (Z00R, 0, NotSerialized)
            {
                Store ("HP WMI Command 0xC (BIOS Read)", Debug)
                Acquire (\_SB.PCI0.LPCB.EC0.MUT0, 0xFFFF)
                Store (Package (0x03)
                    {
                        0x00, 
                        0x04, 
                        Buffer (0x04) {}
                    }, Local0)
                If (ECON)
                {
                    Store (\_SB.PCI0.LPCB.EC0.QBBB, Local1)
                    Store (0x00, \_SB.PCI0.LPCB.EC0.QBBB)
                }

                If (LEqual (Local1, 0x03))
                {
                    Store (0xE4, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                    Store (0x20, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                }

                If (LEqual (Local1, 0x04))
                {
                    Store (0x42, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                    Store (0x21, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                }

                If (LEqual (Local1, 0x05))
                {
                    Store (0xE6, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                    Store (0x20, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                }

                If (LEqual (Local1, 0x10))
                {
                    Store (0x70, Index (DerefOf (Index (Local0, 0x02)), 0x00))
                    Store (0x21, Index (DerefOf (Index (Local0, 0x02)), 0x01))
                }

                Release (\_SB.PCI0.LPCB.EC0.MUT0)
                Return (Local0)
            }

            Method (_WED, 1, NotSerialized)
            {
                Concatenate (Z00X, Z00Y, Local0)
                Return (Local0)
            }

            Name (WQAE, Buffer (0x08A9)
            {
                /* 0000 */    0x46, 0x4F, 0x4D, 0x42, 0x01, 0x00, 0x00, 0x00, 
                /* 0008 */    0x99, 0x08, 0x00, 0x00, 0x8A, 0x3A, 0x00, 0x00, 
                /* 0010 */    0x44, 0x53, 0x00, 0x01, 0x1A, 0x7D, 0xDA, 0x54, 
                /* 0018 */    0x98, 0x4B, 0x9C, 0x00, 0x01, 0x06, 0x18, 0x42, 
                /* 0020 */    0x10, 0x13, 0x10, 0x22, 0x21, 0x04, 0x12, 0x01, 
                /* 0028 */    0xA1, 0xC8, 0x2C, 0x0C, 0x86, 0x10, 0x38, 0x2E, 
                /* 0030 */    0x84, 0x1C, 0x40, 0x88, 0x59, 0x50, 0x08, 0x21, 
                /* 0038 */    0x10, 0xEA, 0x4F, 0x20, 0xBF, 0x02, 0x10, 0x3A, 
                /* 0040 */    0x14, 0x20, 0x53, 0x80, 0x41, 0x01, 0x4E, 0x11, 
                /* 0048 */    0x44, 0xD0, 0xAB, 0x00, 0x9B, 0x02, 0x4C, 0x0A, 
                /* 0050 */    0xB0, 0x28, 0x40, 0xBB, 0x00, 0xCB, 0x02, 0x74, 
                /* 0058 */    0x0B, 0x90, 0x0E, 0x4B, 0x44, 0x82, 0xA3, 0xC4, 
                /* 0060 */    0x80, 0xA3, 0x74, 0x62, 0x0B, 0x37, 0x6C, 0xF0, 
                /* 0068 */    0x42, 0x51, 0x34, 0x83, 0x28, 0x09, 0x2A, 0x17, 
                /* 0070 */    0xE0, 0x1B, 0x41, 0xE0, 0xE5, 0x0A, 0x90, 0x3C, 
                /* 0078 */    0x01, 0x69, 0x16, 0x60, 0x58, 0x80, 0x75, 0x01, 
                /* 0080 */    0xB2, 0x87, 0x40, 0xA5, 0x0E, 0x01, 0x25, 0x67, 
                /* 0088 */    0x08, 0xA8, 0x01, 0xB4, 0x3A, 0x01, 0xE1, 0x57, 
                /* 0090 */    0x3A, 0x25, 0x24, 0x41, 0x38, 0x63, 0x15, 0x8F, 
                /* 0098 */    0xAF, 0x59, 0x34, 0x3D, 0x27, 0x39, 0xC7, 0x90, 
                /* 00A0 */    0xE3, 0x71, 0xA1, 0x07, 0xC1, 0x05, 0x78, 0x18, 
                /* 00A8 */    0x06, 0x1D, 0xB2, 0x22, 0x6B, 0x80, 0xC1, 0x58, 
                /* 00B0 */    0x18, 0x0B, 0x75, 0x31, 0x6A, 0xD4, 0x48, 0xD9, 
                /* 00B8 */    0x80, 0x0C, 0x51, 0x12, 0x1C, 0x6A, 0xD4, 0x96, 
                /* 00C0 */    0x28, 0xC0, 0xFC, 0x38, 0x34, 0xBB, 0xB6, 0xC7, 
                /* 00C8 */    0x42, 0x20, 0x99, 0xB4, 0xA1, 0xA0, 0xA4, 0x40, 
                /* 00D0 */    0x68, 0x6C, 0x67, 0xEA, 0x19, 0x45, 0x3C, 0x52, 
                /* 00D8 */    0xC3, 0x24, 0xF0, 0x28, 0x22, 0x1B, 0x8D, 0x43, 
                /* 00E0 */    0x63, 0x87, 0xE1, 0x61, 0x06, 0x3B, 0x88, 0xC3, 
                /* 00E8 */    0x38, 0xE6, 0xC8, 0x09, 0x3C, 0xA1, 0x23, 0x3D, 
                /* 00F0 */    0xF2, 0xC2, 0xE6, 0x29, 0xD4, 0x18, 0xCD, 0x41, 
                /* 00F8 */    0x11, 0xB8, 0xD0, 0x18, 0x19, 0x10, 0xF2, 0x3C, 
                /* 0100 */    0x7E, 0x8D, 0xC4, 0x04, 0x76, 0x2F, 0xC0, 0x1A, 
                /* 0108 */    0xA6, 0x60, 0x1B, 0x9B, 0x98, 0xFE, 0xFF, 0x10, 
                /* 0110 */    0x47, 0x1E, 0xA3, 0xAD, 0xB9, 0x0B, 0x29, 0x4C, 
                /* 0118 */    0x8C, 0x28, 0xC1, 0xE2, 0x55, 0x3C, 0x0D, 0xA1, 
                /* 0120 */    0x3C, 0x29, 0x84, 0x8A, 0x54, 0x19, 0x8A, 0x86, 
                /* 0128 */    0x1E, 0xA5, 0x42, 0x01, 0xCE, 0xE6, 0x21, 0xDC, 
                /* 0130 */    0x1A, 0x41, 0x85, 0x10, 0x2B, 0x52, 0xAC, 0xF6, 
                /* 0138 */    0x07, 0x41, 0x42, 0x2E, 0x5B, 0xC7, 0x07, 0x47, 
                /* 0140 */    0x1A, 0x0D, 0xEA, 0x50, 0xE0, 0xB1, 0x7B, 0xDC, 
                /* 0148 */    0xCF, 0x02, 0x3E, 0x08, 0x9C, 0x5B, 0x90, 0xA3, 
                /* 0150 */    0x3B, 0x8B, 0x47, 0x85, 0x83, 0xF6, 0xF0, 0xD8, 
                /* 0158 */    0x6D, 0xC0, 0x67, 0x08, 0x9F, 0x02, 0xF0, 0xAE, 
                /* 0160 */    0x01, 0x35, 0xFD, 0x83, 0x67, 0x82, 0xE0, 0x50, 
                /* 0168 */    0x43, 0xF4, 0xA8, 0xC3, 0x9D, 0xC0, 0x21, 0x32, 
                /* 0170 */    0x40, 0x4F, 0xEA, 0xB8, 0xB1, 0x83, 0x3B, 0x99, 
                /* 0178 */    0x83, 0x7E, 0x6F, 0x68, 0xF6, 0xC6, 0x40, 0x08, 
                /* 0180 */    0x8E, 0xC7, 0x97, 0x05, 0x36, 0xE1, 0x04, 0x96, 
                /* 0188 */    0x3F, 0x08, 0xD4, 0xC8, 0x0C, 0xED, 0x51, 0x9E, 
                /* 0190 */    0x56, 0xCC, 0x90, 0xCF, 0x0C, 0x26, 0xB0, 0x58, 
                /* 0198 */    0x08, 0x29, 0x80, 0xD0, 0x78, 0xC0, 0x7F, 0x03, 
                /* 01A0 */    0x78, 0xC0, 0xF0, 0xCD, 0xC0, 0xF3, 0x35, 0xC1, 
                /* 01A8 */    0xB0, 0x10, 0x32, 0xB2, 0x0A, 0x8F, 0x87, 0x8E, 
                /* 01B0 */    0xC2, 0xD7, 0x83, 0xC3, 0x39, 0xAD, 0x78, 0x26, 
                /* 01B8 */    0x18, 0x0E, 0x42, 0x27, 0x09, 0x8B, 0x1A, 0x36, 
                /* 01C0 */    0x3D, 0x39, 0xF0, 0x43, 0x03, 0xBB, 0x19, 0x9C, 
                /* 01C8 */    0xC1, 0x23, 0x80, 0x47, 0x72, 0x42, 0xFE, 0x98, 
                /* 01D0 */    0x78, 0x60, 0xF0, 0x01, 0xF1, 0xDE, 0xA7, 0x4C, 
                /* 01D8 */    0x46, 0x70, 0xA6, 0x06, 0xF4, 0x71, 0xC0, 0xFF, 
                /* 01E0 */    0xFF, 0xA1, 0xF0, 0x21, 0x7A, 0x7C, 0xA7, 0x7C, 
                /* 01E8 */    0xBC, 0x96, 0x00, 0x21, 0x59, 0xE3, 0x84, 0x7E, 
                /* 01F0 */    0x87, 0xF0, 0xF1, 0xC3, 0x47, 0x16, 0x47, 0x84, 
                /* 01F8 */    0x90, 0x93, 0x53, 0x00, 0x1A, 0xF8, 0x74, 0xCF, 
                /* 0200 */    0x2E, 0xC2, 0xE9, 0x7A, 0x52, 0x0E, 0x34, 0x0C, 
                /* 0208 */    0x3A, 0x4E, 0x70, 0x9C, 0x07, 0xC0, 0x31, 0x4E, 
                /* 0210 */    0xF8, 0xE7, 0x02, 0xF8, 0x03, 0xE4, 0xA7, 0x8C, 
                /* 0218 */    0x57, 0x8C, 0x04, 0x8E, 0x39, 0x42, 0xF4, 0xB9, 
                /* 0220 */    0xC6, 0x23, 0xC4, 0xC2, 0x3F, 0x55, 0x14, 0x3E, 
                /* 0228 */    0x10, 0x32, 0x46, 0x70, 0x01, 0x7A, 0x8C, 0xC0, 
                /* 0230 */    0x37, 0xE0, 0x18, 0xD1, 0x47, 0x09, 0xAE, 0xFE, 
                /* 0238 */    0xA0, 0x41, 0x07, 0x88, 0xFB, 0xFF, 0x0F, 0x10, 
                /* 0240 */    0x3E, 0xA8, 0x07, 0x08, 0x7C, 0xA3, 0x1F, 0x3D, 
                /* 0248 */    0xD0, 0xE3, 0xB2, 0xE8, 0xF3, 0x80, 0x8C, 0x9F, 
                /* 0250 */    0x68, 0x34, 0x2F, 0x7E, 0x3A, 0xE0, 0x87, 0x0F, 
                /* 0258 */    0xF0, 0x80, 0x7A, 0x48, 0x38, 0x50, 0xCC, 0xB4, 
                /* 0260 */    0x39, 0xE8, 0xB3, 0xCB, 0xA1, 0x63, 0x87, 0x0B, 
                /* 0268 */    0xFE, 0x13, 0x08, 0xB8, 0xE4, 0x1D, 0xC2, 0x40, 
                /* 0270 */    0x31, 0x62, 0xFC, 0x39, 0xC8, 0xA7, 0x30, 0xF0, 
                /* 0278 */    0xFF, 0xFF, 0x4F, 0x61, 0xB8, 0x11, 0xF0, 0x20, 
                /* 0280 */    0xAF, 0x05, 0x9F, 0xB6, 0xA8, 0x74, 0x18, 0xD4, 
                /* 0288 */    0x81, 0x0B, 0x30, 0x09, 0x1A, 0xE1, 0x59, 0xA2, 
                /* 0290 */    0x36, 0x08, 0x01, 0xBF, 0x4D, 0xBC, 0x6D, 0xF9, 
                /* 0298 */    0x16, 0x10, 0xE7, 0xC8, 0x7B, 0x3B, 0x70, 0x11, 
                /* 02A0 */    0x8C, 0x08, 0xA7, 0x1D, 0xCA, 0x63, 0x88, 0x18, 
                /* 02A8 */    0x23, 0xCA, 0xE3, 0x96, 0x51, 0xDE, 0xB6, 0x5E, 
                /* 02B0 */    0x00, 0xE2, 0x9D, 0xE5, 0xF3, 0x96, 0x31, 0x82, 
                /* 02B8 */    0x47, 0x7E, 0xE0, 0x62, 0x62, 0xDF, 0x13, 0xFA, 
                /* 02C0 */    0xB9, 0xF9, 0xC0, 0x05, 0x38, 0xFB, 0xFF, 0x1F, 
                /* 02C8 */    0xB8, 0x00, 0x0E, 0x05, 0x3D, 0x0C, 0xA1, 0x87, 
                /* 02D0 */    0xE1, 0xA9, 0x9C, 0xCB, 0x13, 0xE5, 0xA9, 0x44, 
                /* 02D8 */    0x8C, 0x1A, 0x26, 0xEA, 0x33, 0x94, 0x2F, 0x1A, 
                /* 02E0 */    0x3E, 0x10, 0x81, 0xEF, 0xCC, 0x05, 0xFC, 0xFE, 
                /* 02E8 */    0xFF, 0x07, 0x22, 0x38, 0x02, 0xCF, 0x34, 0xA0, 
                /* 02F0 */    0xF4, 0x39, 0x03, 0x81, 0x9C, 0x8A, 0x0F, 0x35, 
                /* 02F8 */    0xC0, 0x48, 0xF4, 0xAB, 0xC1, 0x27, 0x1A, 0x2A, 
                /* 0300 */    0x13, 0x06, 0x75, 0xA8, 0x01, 0x4C, 0x5E, 0x61, 
                /* 0308 */    0x9E, 0x46, 0xCF, 0xF9, 0x59, 0xC6, 0xA7, 0x1A, 
                /* 0310 */    0x1F, 0x4A, 0x8D, 0x63, 0x88, 0x97, 0x99, 0x87, 
                /* 0318 */    0x1A, 0x1F, 0x0B, 0x5E, 0x49, 0x7D, 0xA8, 0x31, 
                /* 0320 */    0x54, 0x9C, 0x87, 0x1A, 0x9F, 0x48, 0x03, 0x45, 
                /* 0328 */    0x7D, 0xB3, 0x79, 0xB6, 0x31, 0x7A, 0x7C, 0xDF, 
                /* 0330 */    0x50, 0x0D, 0xF1, 0x50, 0xC3, 0x84, 0xBD, 0x23, 
                /* 0338 */    0xF4, 0xC1, 0xF5, 0xA1, 0x06, 0x1C, 0xFF, 0xFF, 
                /* 0340 */    0x43, 0x0D, 0xC0, 0xFF, 0xFF, 0xFF, 0xA1, 0x06, 
                /* 0348 */    0x70, 0x74, 0x34, 0x80, 0x73, 0x64, 0xC4, 0x1D, 
                /* 0350 */    0x0D, 0xC0, 0x75, 0x28, 0x05, 0x0E, 0x47, 0x03, 
                /* 0358 */    0xE0, 0x71, 0x14, 0x02, 0xF3, 0x85, 0xC6, 0x47, 
                /* 0360 */    0x21, 0x60, 0xF1, 0xFF, 0x3F, 0x0A, 0xE1, 0x64, 
                /* 0368 */    0x9F, 0x83, 0x50, 0x42, 0x8F, 0x42, 0x80, 0x54, 
                /* 0370 */    0xC8, 0xA7, 0x88, 0x67, 0x1F, 0x5F, 0x7E, 0x1E, 
                /* 0378 */    0x08, 0x22, 0xBC, 0xE6, 0xFB, 0x14, 0xE4, 0x43, 
                /* 0380 */    0xBE, 0x8F, 0x42, 0x0C, 0xC6, 0x50, 0xBE, 0x06, 
                /* 0388 */    0xF9, 0x28, 0xC4, 0xA0, 0x5E, 0x83, 0x7C, 0xDF, 
                /* 0390 */    0x37, 0xC8, 0x91, 0x18, 0xFB, 0x99, 0xC0, 0x47, 
                /* 0398 */    0x21, 0x26, 0xED, 0x28, 0x04, 0x28, 0xFC, 0xFF, 
                /* 03A0 */    0x1F, 0x85, 0x00, 0xFE, 0xFF, 0xFF, 0x8F, 0x42, 
                /* 03A8 */    0x80, 0xB3, 0x00, 0x47, 0x03, 0xD0, 0x4D, 0xEB, 
                /* 03B0 */    0x51, 0x08, 0xBC, 0x77, 0x96, 0xD3, 0x3E, 0x01, 
                /* 03B8 */    0x9F, 0x85, 0x00, 0xB3, 0xFF, 0xFF, 0xB3, 0x10, 
                /* 03C0 */    0x30, 0x3B, 0x0A, 0x45, 0x3D, 0xE8, 0x57, 0xA1, 
                /* 03C8 */    0x27, 0x80, 0x17, 0x80, 0x18, 0x61, 0xDE, 0x81, 
                /* 03D0 */    0x5E, 0x32, 0xD9, 0x5D, 0xDC, 0x38, 0x4F, 0x2E, 
                /* 03D8 */    0xA7, 0x6D, 0x94, 0x97, 0x20, 0x1F, 0x28, 0x9E, 
                /* 03E0 */    0x85, 0x0C, 0xF5, 0x2E, 0x14, 0xF4, 0x8D, 0xDC, 
                /* 03E8 */    0xA3, 0x8C, 0x19, 0x3F, 0xC4, 0xF3, 0x90, 0x21, 
                /* 03F0 */    0x9E, 0x85, 0x00, 0x76, 0xFD, 0xFF, 0xCF, 0x42, 
                /* 03F8 */    0x00, 0xFF, 0xFF, 0xFF, 0x47, 0x03, 0xF8, 0x2F, 
                /* 0400 */    0x00, 0x9F, 0x85, 0x80, 0xE7, 0x09, 0xE0, 0x41, 
                /* 0408 */    0xDB, 0x67, 0x21, 0x80, 0x33, 0x87, 0xCB, 0xF3, 
                /* 0410 */    0x0F, 0x7A, 0x60, 0xEF, 0x11, 0x9E, 0xF5, 0x71, 
                /* 0418 */    0xBF, 0x5E, 0x7A, 0xE0, 0x0F, 0x05, 0xCF, 0x42, 
                /* 0420 */    0x0C, 0xEB, 0x98, 0x7C, 0x16, 0x62, 0x10, 0x2F, 
                /* 0428 */    0x9A, 0x86, 0x78, 0xE1, 0xF4, 0x61, 0xC0, 0xFF, 
                /* 0430 */    0x7F, 0xBC, 0xC0, 0xAF, 0x9C, 0x06, 0x0A, 0x12, 
                /* 0438 */    0xE8, 0x59, 0x08, 0x60, 0xFC, 0xFF, 0xFF, 0x2C, 
                /* 0440 */    0x04, 0x90, 0x71, 0x8D, 0x3A, 0x0B, 0x01, 0xCB, 
                /* 0448 */    0x63, 0x0C, 0x3B, 0xAD, 0x24, 0xF8, 0xFF, 0x3F, 
                /* 0450 */    0x0B, 0x01, 0x9F, 0x5C, 0x46, 0x0E, 0x42, 0x98, 
                /* 0458 */    0x88, 0x6F, 0x05, 0x1F, 0x33, 0x01, 0xA5, 0xE7, 
                /* 0460 */    0xA0, 0x17, 0x77, 0x63, 0x04, 0x7E, 0x91, 0x78, 
                /* 0468 */    0xCC, 0x64, 0x47, 0x4D, 0xC3, 0x3C, 0x0B, 0x19, 
                /* 0470 */    0xEF, 0x30, 0xCE, 0xE0, 0x09, 0xDE, 0x93, 0x7F, 
                /* 0478 */    0x16, 0x62, 0x60, 0xC7, 0x18, 0xEC, 0x51, 0xC8, 
                /* 0480 */    0xA0, 0x06, 0x8F, 0x1D, 0x22, 0x4C, 0xA0, 0x67, 
                /* 0488 */    0x21, 0x16, 0x6A, 0xDC, 0x3A, 0x7F, 0xF8, 0x2C, 
                /* 0490 */    0x04, 0xBC, 0xFF, 0xFF, 0x67, 0x21, 0xC0, 0xD3, 
                /* 0498 */    0x61, 0xC3, 0x67, 0x0D, 0xF0, 0x0C, 0xDF, 0xA3, 
                /* 04A0 */    0x3A, 0x87, 0xC7, 0x63, 0xE0, 0x92, 0x55, 0xC7, 
                /* 04A8 */    0x09, 0x83, 0xE5, 0x5E, 0xA7, 0x6C, 0x9C, 0x61, 
                /* 04B0 */    0xE8, 0x20, 0xAC, 0x0E, 0x48, 0xC3, 0xC1, 0xDC, 
                /* 04B8 */    0x43, 0x0E, 0xE2, 0x7C, 0xD8, 0x40, 0xAD, 0x08, 
                /* 04C0 */    0x4E, 0xC7, 0x24, 0x0F, 0xDA, 0x5A, 0x28, 0xA4, 
                /* 04C8 */    0x80, 0x46, 0x03, 0x32, 0xBC, 0x33, 0x9F, 0x96, 
                /* 04D0 */    0x28, 0x88, 0x01, 0x7D, 0x02, 0xB2, 0x8D, 0x73, 
                /* 04D8 */    0x00, 0x6A, 0x2F, 0x9A, 0x02, 0x39, 0xDA, 0x60, 
                /* 04E0 */    0xF4, 0x5F, 0x16, 0xE8, 0x6C, 0x7C, 0x0D, 0xE0, 
                /* 04E8 */    0x1A, 0x20, 0x74, 0x30, 0x30, 0xB4, 0xD5, 0xDC, 
                /* 04F0 */    0x62, 0x50, 0x60, 0xC6, 0x7F, 0x70, 0x31, 0x81, 
                /* 04F8 */    0x8F, 0x2E, 0xF8, 0xB3, 0x00, 0xEE, 0xFF, 0x3F, 
                /* 0500 */    0x5C, 0x8F, 0xF6, 0x5D, 0xA0, 0xEA, 0xC9, 0xEA, 
                /* 0508 */    0x8A, 0x60, 0x75, 0x97, 0x17, 0x08, 0x33, 0x32, 
                /* 0510 */    0x41, 0x7D, 0x07, 0x02, 0x50, 0x00, 0xF9, 0x0E, 
                /* 0518 */    0xE0, 0xA3, 0xD3, 0x73, 0x00, 0x9B, 0x48, 0x88, 
                /* 0520 */    0x30, 0xD1, 0x8C, 0x8E, 0x98, 0x30, 0x2A, 0xFA, 
                /* 0528 */    0x84, 0x29, 0x88, 0x27, 0xEC, 0x58, 0x13, 0x46, 
                /* 0530 */    0xCF, 0xC4, 0x77, 0x1B, 0x36, 0x62, 0x4C, 0x88, 
                /* 0538 */    0xDB, 0x06, 0xB4, 0x09, 0x06, 0xF5, 0x3D, 0x08, 
                /* 0540 */    0xD6, 0x90, 0xF9, 0x58, 0x7C, 0x67, 0xC0, 0x4D, 
                /* 0548 */    0x19, 0x8C, 0x73, 0x62, 0xD7, 0x04, 0x0B, 0x9C, 
                /* 0550 */    0x33, 0xC8, 0xE1, 0x31, 0xD7, 0x2F, 0x7E, 0x5B, 
                /* 0558 */    0xF2, 0xE8, 0xF8, 0x41, 0xC1, 0x37, 0x1C, 0x86, 
                /* 0560 */    0xFD, 0x30, 0xE6, 0x19, 0xBD, 0x8A, 0xF9, 0xE6, 
                /* 0568 */    0x86, 0x81, 0xF5, 0x78, 0x39, 0xAC, 0xD1, 0xC2, 
                /* 0570 */    0x1E, 0xDA, 0xAB, 0x87, 0xCF, 0x2D, 0x3E, 0x4F, 
                /* 0578 */    0x18, 0x23, 0xAC, 0x2F, 0x2C, 0xE0, 0x00, 0xFC, 
                /* 0580 */    0xFF, 0xBF, 0x5A, 0xC1, 0xBE, 0x6B, 0x80, 0xE7, 
                /* 0588 */    0x26, 0xE4, 0xBB, 0x06, 0xC0, 0xDA, 0xFF, 0xFF, 
                /* 0590 */    0x5D, 0x03, 0xFE, 0x35, 0xC1, 0x77, 0x0D, 0xE0, 
                /* 0598 */    0x3D, 0x74, 0xDF, 0x35, 0x80, 0x6B, 0xF6, 0xBB, 
                /* 05A0 */    0x06, 0xEA, 0x18, 0x60, 0x85, 0x77, 0x0D, 0x68, 
                /* 05A8 */    0xB7, 0xB4, 0x57, 0xB4, 0x87, 0x2A, 0x6B, 0xBA, 
                /* 05B0 */    0x6C, 0xA0, 0xD4, 0x5C, 0x36, 0x00, 0x6D, 0xFF, 
                /* 05B8 */    0xFF, 0xCB, 0x06, 0xB0, 0x91, 0x32, 0x61, 0x54, 
                /* 05C0 */    0xF8, 0x09, 0x53, 0x10, 0x4F, 0xD8, 0xC1, 0x2E, 
                /* 05C8 */    0x1B, 0xA0, 0x88, 0x71, 0xD9, 0x00, 0xFD, 0xD8, 
                /* 05D0 */    0x5E, 0x36, 0x80, 0xC1, 0x3D, 0x81, 0xDF, 0x36, 
                /* 05D8 */    0x80, 0x37, 0xA4, 0x6F, 0x1B, 0xC0, 0xF4, 0xFF, 
                /* 05E0 */    0x0F, 0x31, 0xFF, 0x6D, 0x03, 0xC5, 0x61, 0x95, 
                /* 05E8 */    0xB7, 0x0D, 0x88, 0x87, 0x77, 0x46, 0x60, 0x55, 
                /* 05F0 */    0xD7, 0x0D, 0x94, 0x9E, 0xEB, 0x06, 0x40, 0x02, 
                /* 05F8 */    0x31, 0x13, 0x46, 0xC5, 0x9F, 0x30, 0x05, 0xF1, 
                /* 0600 */    0x84, 0x1D, 0xED, 0xBA, 0x01, 0x8A, 0x20, 0xD7, 
                /* 0608 */    0x0D, 0xD0, 0xCF, 0xEB, 0x94, 0xC1, 0xFA, 0xFF, 
                /* 0610 */    0xBF, 0x6E, 0x60, 0x2F, 0x0A, 0x98, 0xFB, 0x06, 
                /* 0618 */    0xF0, 0x86, 0xE5, 0xF7, 0x0D, 0xC0, 0xC7, 0xE5, 
                /* 0620 */    0x1B, 0x73, 0xDF, 0x00, 0x6C, 0xFE, 0xFF, 0xEF, 
                /* 0628 */    0x1B, 0x00, 0x13, 0x2E, 0x0A, 0xB8, 0xFB, 0x06, 
                /* 0630 */    0xF0, 0xBE, 0x48, 0xFB, 0xBE, 0x01, 0x5C, 0x83, 
                /* 0638 */    0x49, 0xF8, 0xFF, 0xDF, 0xF5, 0xE8, 0x0B, 0x40, 
                /* 0640 */    0x51, 0x60, 0x50, 0x43, 0xF2, 0x99, 0x00, 0x3F, 
                /* 0648 */    0xBA, 0x83, 0x3B, 0xA6, 0xE0, 0x4C, 0x12, 0x1C, 
                /* 0650 */    0x6A, 0xE0, 0xBE, 0x02, 0x3C, 0xCD, 0x9F, 0xD6, 
                /* 0658 */    0x7B, 0xBD, 0xE7, 0xF1, 0x24, 0x10, 0x92, 0x1D, 
                /* 0660 */    0x61, 0x7C, 0x6C, 0x43, 0x9C, 0x0C, 0xC8, 0x41, 
                /* 0668 */    0xDC, 0x47, 0xF7, 0x88, 0xEF, 0xE1, 0x86, 0x49, 
                /* 0670 */    0xE0, 0x21, 0x33, 0x34, 0x0E, 0x8D, 0x1D, 0x86, 
                /* 0678 */    0xEF, 0x02, 0xC1, 0x0E, 0xE2, 0x30, 0xCE, 0xD7, 
                /* 0680 */    0x04, 0x9E, 0xD0, 0x83, 0xC0, 0x7B, 0xF9, 0xA3, 
                /* 0688 */    0x41, 0xF1, 0x77, 0x03, 0x4A, 0x60, 0xB8, 0xD0, 
                /* 0690 */    0x98, 0x91, 0xFA, 0x6C, 0xFF, 0x8E, 0x70, 0x24, 
                /* 0698 */    0x26, 0xB0, 0x7B, 0x48, 0x59, 0x13, 0xA0, 0xF1, 
                /* 06A0 */    0x96, 0x43, 0x20, 0x7A, 0xC3, 0x91, 0x2D, 0x14, 
                /* 06A8 */    0xCD, 0x2D, 0xCA, 0xFB, 0x42, 0x14, 0x3B, 0x43, 
                /* 06B0 */    0x10, 0x46, 0x94, 0x60, 0x41, 0x9E, 0xD6, 0x62, 
                /* 06B8 */    0x45, 0x79, 0x66, 0x37, 0x42, 0xC4, 0x10, 0xAF, 
                /* 06C0 */    0x0C, 0x81, 0x5E, 0x12, 0xC2, 0x07, 0x79, 0xEC, 
                /* 06C8 */    0x89, 0xD3, 0xFE, 0x20, 0x88, 0xF8, 0x17, 0x82, 
                /* 06D0 */    0x3C, 0x80, 0x28, 0xD2, 0x68, 0x50, 0xE7, 0x06, 
                /* 06D8 */    0x8F, 0xDD, 0x87, 0x10, 0x5F, 0xFE, 0x7D, 0xB8, 
                /* 06E0 */    0xF7, 0xE8, 0x0E, 0xEE, 0x45, 0xFE, 0xA0, 0x3D, 
                /* 06E8 */    0x3C, 0x76, 0xC2, 0xF0, 0x41, 0x03, 0x8E, 0x6B, 
                /* 06F0 */    0x40, 0x4D, 0xFF, 0x19, 0x01, 0x2C, 0x97, 0x7F, 
                /* 06F8 */    0xF8, 0xE3, 0xF1, 0x3D, 0xC1, 0xF3, 0x39, 0xE1, 
                /* 0700 */    0x04, 0x96, 0x3F, 0x08, 0xD4, 0x71, 0x84, 0xCF, 
                /* 0708 */    0xF3, 0x85, 0xC3, 0x90, 0xCF, 0x02, 0x87, 0xC5, 
                /* 0710 */    0xC4, 0x0A, 0xF8, 0xFF, 0x9F, 0x4C, 0xD8, 0x78, 
                /* 0718 */    0xC0, 0x7F, 0x0F, 0x79, 0xFD, 0xF7, 0xCD, 0xC0, 
                /* 0720 */    0xF3, 0x35, 0xC1, 0x88, 0x10, 0x72, 0x32, 0x1E, 
                /* 0728 */    0x34, 0xE8, 0xD9, 0xF8, 0x80, 0xE1, 0xEB, 0x09, 
                /* 0730 */    0x3B, 0x77, 0x70, 0x51, 0xE7, 0x0E, 0xD4, 0xD1, 
                /* 0738 */    0xC1, 0xA7, 0x06, 0x76, 0xB3, 0xC1, 0x1C, 0xB7, 
                /* 0740 */    0xF9, 0x59, 0x03, 0xFC, 0x23, 0x84, 0x7F, 0x7B, 
                /* 0748 */    0xF0, 0xBC, 0x7C, 0x65, 0x78, 0x75, 0x48, 0xE0, 
                /* 0750 */    0x90, 0x23, 0x44, 0x8F, 0xCB, 0x23, 0xC4, 0x9C, 
                /* 0758 */    0x6F, 0x30, 0x43, 0x04, 0xD7, 0x59, 0x00, 0x1C, 
                /* 0760 */    0x43, 0x04, 0x3E, 0x67, 0x4C, 0x9F, 0x71, 0x60, 
                /* 0768 */    0xFE, 0xFF, 0xCF, 0x38, 0xEC, 0xD2, 0xC3, 0x07, 
                /* 0770 */    0x6A, 0x78, 0x13, 0xF8, 0xFE, 0x8C, 0x3B, 0xD2, 
                /* 0778 */    0x18, 0x9C, 0x1F, 0x33, 0x1E, 0x76, 0x18, 0xF8, 
                /* 0780 */    0xFB, 0x8E, 0x67, 0x70, 0x34, 0x3E, 0xA0, 0x18, 
                /* 0788 */    0x21, 0xF8, 0x73, 0xC9, 0x73, 0x8A, 0x35, 0x0F, 
                /* 0790 */    0x52, 0x33, 0x7A, 0x67, 0x38, 0x04, 0x76, 0xB3, 
                /* 0798 */    0xC2, 0x1D, 0x38, 0x3C, 0x04, 0x3E, 0x80, 0x56, 
                /* 07A0 */    0x27, 0x47, 0x4E, 0x3F, 0xA7, 0x84, 0x1B, 0x3E, 
                /* 07A8 */    0xBF, 0x0A, 0x60, 0x0E, 0x41, 0x38, 0x85, 0x36, 
                /* 07B0 */    0x7D, 0x6A, 0x34, 0x6A, 0xD5, 0xA0, 0x4C, 0x8D, 
                /* 07B8 */    0x32, 0x0D, 0x6A, 0xF5, 0xA9, 0xD4, 0x98, 0xB1, 
                /* 07C0 */    0x0B, 0x8B, 0x03, 0xBE, 0x02, 0x74, 0x1C, 0xB0, 
                /* 07C8 */    0x3C, 0x0A, 0x1D, 0xC1, 0xC8, 0x9B, 0x40, 0x20, 
                /* 07D0 */    0x0E, 0x0B, 0x42, 0x23, 0xBD, 0x71, 0x04, 0x62, 
                /* 07D8 */    0xC9, 0xEF, 0x2F, 0x81, 0x58, 0xEE, 0x03, 0x45, 
                /* 07E0 */    0x20, 0x0E, 0x68, 0x02, 0x9C, 0xAA, 0x00, 0xA7, 
                /* 07E8 */    0xAF, 0x01, 0x81, 0x38, 0x32, 0x08, 0x15, 0xFA, 
                /* 07F0 */    0x35, 0x13, 0x88, 0x63, 0x82, 0xD0, 0x50, 0x3E, 
                /* 07F8 */    0x40, 0x98, 0xF4, 0x17, 0x80, 0x00, 0x89, 0x11, 
                /* 0800 */    0x10, 0x16, 0xEE, 0xE5, 0x20, 0x10, 0x4B, 0x7B, 
                /* 0808 */    0x2D, 0x08, 0xC4, 0x42, 0xAC, 0x80, 0xB0, 0xB8, 
                /* 0810 */    0x20, 0x34, 0x9C, 0x16, 0x10, 0x26, 0xC9, 0x0C, 
                /* 0818 */    0x08, 0x0B, 0x04, 0x42, 0xE5, 0x3F, 0xD3, 0x04, 
                /* 0820 */    0x62, 0x91, 0x6E, 0x00, 0xE9, 0xBA, 0x05, 0xE2, 
                /* 0828 */    0x20, 0x7A, 0x40, 0x98, 0x0C, 0x3F, 0x20, 0x2C, 
                /* 0830 */    0x34, 0x08, 0x8D, 0xF6, 0x6C, 0x10, 0x20, 0x31, 
                /* 0838 */    0x04, 0xC2, 0xE2, 0x3B, 0x02, 0x61, 0xE2, 0xDF, 
                /* 0840 */    0x44, 0x02, 0x71, 0x4A, 0x4B, 0x10, 0x37, 0xA5, 
                /* 0848 */    0x01, 0x06, 0x11, 0x90, 0x93, 0x6A, 0x02, 0x62, 
                /* 0850 */    0xB9, 0x41, 0x34, 0x24, 0xF2, 0xB0, 0x10, 0x90, 
                /* 0858 */    0x93, 0x82, 0x68, 0xC0, 0xC4, 0x14, 0x90, 0xFF, 
                /* 0860 */    0xFF, 0x43, 0x13, 0x88, 0x80, 0x9C, 0xCA, 0x15, 
                /* 0868 */    0x10, 0x8B, 0x08, 0x22, 0x20, 0x27, 0x7B, 0x52, 
                /* 0870 */    0x09, 0xC8, 0x39, 0x41, 0x74, 0x04, 0x20, 0xBA, 
                /* 0878 */    0x80, 0x58, 0x3E, 0x10, 0x01, 0x39, 0x96, 0x2F, 
                /* 0880 */    0x20, 0x16, 0x12, 0x44, 0x40, 0x4E, 0xF4, 0xF3, 
                /* 0888 */    0x09, 0x44, 0xE2, 0x81, 0x68, 0x10, 0xE4, 0x3F, 
                /* 0890 */    0x21, 0x20, 0x67, 0x04, 0x11, 0x10, 0x79, 0x12, 
                /* 0898 */    0x05, 0x21, 0x9A, 0x3E, 0x62, 0x02, 0x71, 0x6A, 
                /* 08A0 */    0x10, 0x9A, 0xEC, 0x27, 0x14, 0x84, 0xFC, 0xFF, 
                /* 08A8 */    0x01
            })
        }

        Device (PCI0)
        {
            Method (_INI, 0, NotSerialized)
            {
                If (DTSE)
                {
                    TRAP (0x47)
                }

                Store (0x07D0, OSYS)
                If (CondRefOf (_OSI, Local0))
                {
                    If (\_OSI ("Linux"))
                    {
                        Store (0x01, LINX)
                    }

                    If (\_OSI ("Windows 2001"))
                    {
                        Store (0x07D1, OSYS)
                    }

                    If (\_OSI ("Windows 2001 SP1"))
                    {
                        Store (0x07D1, OSYS)
                    }

                    If (\_OSI ("Windows 2001 SP2"))
                    {
                        Store (0x07D2, OSYS)
                    }

                    If (\_OSI ("Windows 2006"))
                    {
                        Store (0x07D6, OSYS)
                    }
                }

                If (LAnd (MPEN, LEqual (OSYS, 0x07D1)))
                {
                    TRAP (0x3D)
                }

                TRAP (0x32)
            }

            Name (SUPP, 0x00)
            Name (CTRL, 0x00)
            Method (_OSC, 4, NotSerialized)
            {
                If (LEqual (Arg0, ToUUID("33DB4D5B-1FF7-401C-9657-7441C03DD766")))
                {
                    
                    CreateDWordField (Arg3, 0x00, CDW1)
                    CreateDWordField (Arg3, 0x04, CDW2)
                    CreateDWordField (Arg3, 0x08, CDW3)
                    Store (CDW2, SUPP)
                    Store (CDW3, CTRL)
                    If (LNotEqual (And (SUPP, 0x16), 0x16))
                    {
                        And (CTRL, 0x1E, CTRL)
                    }

                    And (CTRL, 0x1D, CTRL)
                    If (Not (And (CDW1, 0x01)))
                    {
                        If (And (CTRL, 0x01))
                        {
                            Store (0x00, \_SB.PCI0.RP02.HPCE)
                            Store (0x01, \_SB.PCI0.RP02.HPCS)
                        }

                        If (And (CTRL, 0x04))
                        {
                            Store (0x00, \_SB.PCI0.RP02.PMCE)
                            Store (0x01, \_SB.PCI0.RP02.PMCS)
                        }
                    }

                    If (LNotEqual (Arg1, One))
                    {
                        Or (CDW1, 0x08, CDW1)
                    }

                    If (LNotEqual (CDW3, CTRL))
                    {
                        Or (CDW1, 0x10, CDW1)
                    }

                    Store (CTRL, CDW3)
                    Return (Arg3)
                }
                Else
                {
                    Or (CDW1, 0x04, CDW1)
                    Return (Arg3)
                }
            }

            Name (_HID, EisaId ("PNP0A08"))
            Name (_CID, EisaId ("PNP0A03"))
            Name (_ADR, 0x00)
            Name (_BBN, 0x00)
            OperationRegion (HBUS, PCI_Config, 0x40, 0xC0)
            Field (HBUS, DWordAcc, NoLock, Preserve)
            {
                        Offset (0x50), 
                    ,   4, 
                PM0H,   2, 
                        Offset (0x51), 
                PM1L,   2, 
                    ,   2, 
                PM1H,   2, 
                        Offset (0x52), 
                PM2L,   2, 
                    ,   2, 
                PM2H,   2, 
                        Offset (0x53), 
                PM3L,   2, 
                    ,   2, 
                PM3H,   2, 
                        Offset (0x54), 
                PM4L,   2, 
                    ,   2, 
                PM4H,   2, 
                        Offset (0x55), 
                PM5L,   2, 
                    ,   2, 
                PM5H,   2, 
                        Offset (0x56), 
                PM6L,   2, 
                    ,   2, 
                PM6H,   2, 
                        Offset (0x57), 
                    ,   7, 
                HENA,   1, 
                        Offset (0x5C), 
                    ,   3, 
                TOUD,   5
            }

            Name (BUF0, ResourceTemplate ()
            {
                WordBusNumber (ResourceProducer, MinFixed, MaxFixed, PosDecode,
                    0x0000,             // Granularity
                    0x0000,             // Range Minimum
                    0x00FF,             // Range Maximum
                    0x0000,             // Translation Offset
                    0x0100,             // Length
                    ,, )
                DWordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0x00000CF7,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000CF8,         // Length
                    ,, , TypeStatic)
                IO (Decode16,
                    0x0CF8,             // Range Minimum
                    0x0CF8,             // Range Maximum
                    0x01,               // Alignment
                    0x08,               // Length
                    )
                DWordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x00000000,         // Granularity
                    0x00000D00,         // Range Minimum
                    0x0000FFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x0000F300,         // Length
                    ,, , TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000A0000,         // Range Minimum
                    0x000BFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00020000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C0000,         // Range Minimum
                    0x000C3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y00, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C4000,         // Range Minimum
                    0x000C7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y01, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C8000,         // Range Minimum
                    0x000CBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y02, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000CC000,         // Range Minimum
                    0x000CFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y03, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D0000,         // Range Minimum
                    0x000D3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y04, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D4000,         // Range Minimum
                    0x000D7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y05, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D8000,         // Range Minimum
                    0x000DBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y06, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000DC000,         // Range Minimum
                    0x000DFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y07, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E0000,         // Range Minimum
                    0x000E3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y08, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E4000,         // Range Minimum
                    0x000E7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y09, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E8000,         // Range Minimum
                    0x000EBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y0A, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000EC000,         // Range Minimum
                    0x000EFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y0B, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000F0000,         // Range Minimum
                    0x000FFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00010000,         // Length
                    ,, _Y0C, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0xFEBFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, _Y0E, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0xFED40000,         // Range Minimum
                    0xFED44FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, _Y0D, AddressRangeMemory, TypeStatic)
            })
            Method (_CRS, 0, Serialized)
            {
                If (PM1L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y00._LEN, C0LN)
                    Store (Zero, C0LN)
                }

                If (LEqual (PM1L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y00._RW, C0RW)
                    Store (Zero, C0RW)
                }

                If (PM1H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y01._LEN, C4LN)
                    Store (Zero, C4LN)
                }

                If (LEqual (PM1H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y01._RW, C4RW)
                    Store (Zero, C4RW)
                }

                If (PM2L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y02._LEN, C8LN)
                    Store (Zero, C8LN)
                }

                If (LEqual (PM2L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y02._RW, C8RW)
                    Store (Zero, C8RW)
                }

                If (PM2H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y03._LEN, CCLN)
                    Store (Zero, CCLN)
                }

                If (LEqual (PM2H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y03._RW, CCRW)
                    Store (Zero, CCRW)
                }

                If (PM3L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y04._LEN, D0LN)
                    Store (Zero, D0LN)
                }

                If (LEqual (PM3L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y04._RW, D0RW)
                    Store (Zero, D0RW)
                }

                If (PM3H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y05._LEN, D4LN)
                    Store (Zero, D4LN)
                }

                If (LEqual (PM3H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y05._RW, D4RW)
                    Store (Zero, D4RW)
                }

                If (PM4L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y06._LEN, D8LN)
                    Store (Zero, D8LN)
                }

                If (LEqual (PM4L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y06._RW, D8RW)
                    Store (Zero, D8RW)
                }

                If (PM4H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y07._LEN, DCLN)
                    Store (Zero, DCLN)
                }

                If (LEqual (PM4H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y07._RW, DCRW)
                    Store (Zero, DCRW)
                }

                If (PM5L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y08._LEN, E0LN)
                    Store (Zero, E0LN)
                }

                If (LEqual (PM5L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y08._RW, E0RW)
                    Store (Zero, E0RW)
                }

                If (PM5H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y09._LEN, E4LN)
                    Store (Zero, E4LN)
                }

                If (LEqual (PM5H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y09._RW, E4RW)
                    Store (Zero, E4RW)
                }

                If (PM6L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0A._LEN, E8LN)
                    Store (Zero, E8LN)
                }

                If (LEqual (PM6L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0A._RW, E8RW)
                    Store (Zero, E8RW)
                }

                If (PM6H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0B._LEN, ECLN)
                    Store (Zero, ECLN)
                }

                If (LEqual (PM6H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0B._RW, ECRW)
                    Store (Zero, ECRW)
                }

                If (PM0H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0C._LEN, F0LN)
                    Store (Zero, F0LN)
                }

                If (LEqual (PM0H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0C._RW, F0RW)
                    Store (Zero, F0RW)
                }

                If (TPMP)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0D._LEN, TPML)
                    Store (0x5000, TPML)
                }

                CreateDWordField (BUF0, \_SB.PCI0._Y0E._MIN, M1MN)
                CreateDWordField (BUF0, \_SB.PCI0._Y0E._MAX, M1MX)
                CreateDWordField (BUF0, \_SB.PCI0._Y0E._LEN, M1LN)
                ShiftLeft (TOUD, 0x1B, M1MN)
                Add (Subtract (M1MX, M1MN), 0x01, M1LN)
                Return (BUF0)
            }

            Method (_PRT, 0, NotSerialized)
            {
                    Return (Package (0x11)
                    {
                        Package (0x04)
                        {
                            0x0001FFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0002FFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0007FFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x001BFFFF, 
                            0x00, 
                            0x00, 
                            0x16
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x00, 
                            0x00, 
                            0x11
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x01, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x02, 
                            0x00, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x03, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x00, 
                            0x00, 
                            0x17
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x01, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x02, 
                            0x00, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x03, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x001EFFFF, 
                            0x00, 
                            0x00, 
                            0x16
                        }, 

                        Package (0x04)
                        {
                            0x001EFFFF, 
                            0x01, 
                            0x00, 
                            0x14
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x00, 
                            0x00, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x01, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x03, 
                            0x00, 
                            0x10
                        }
                    })
            }

            Device (PDRC)
            {
                Name (_HID, EisaId ("PNP0C02"))
                Name (_UID, 0x01)
                Name (BUF0, ResourceTemplate ()
                {
                    Memory32Fixed (ReadWrite,
                        0xE0000000,         // Address Base
                        0x10000000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED14000,         // Address Base
                        0x00004000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED18000,         // Address Base
                        0x00001000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED19000,         // Address Base
                        0x00001000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED1C000,         // Address Base
                        0x00004000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED20000,         // Address Base
                        0x00020000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED40000,         // Address Base
                        0x00005000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED45000,         // Address Base
                        0x0004B000,         // Address Length
                        )
                })
                Name (BUF1, ResourceTemplate ()
                {
                    Memory32Fixed (ReadWrite,
                        0xE0000000,         // Address Base
                        0x10000000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED14000,         // Address Base
                        0x00004000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED18000,         // Address Base
                        0x00001000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED19000,         // Address Base
                        0x00001000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED1C000,         // Address Base
                        0x00004000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED20000,         // Address Base
                        0x00020000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED45000,         // Address Base
                        0x0004B000,         // Address Length
                        )
                })
                Method (_CRS, 0, Serialized)
                {
                    If (LNot (TPMP))
                    {
                        Return (BUF0)
                    }

                    Return (BUF1)
                }
            }

            Name (BCL1, Package (0x0D)
            {
                0x5F, 
                0x2B, 
                0x14, 
                0x18, 
                0x1C, 
                0x20, 
                0x25, 
                0x2B, 
                0x32, 
                0x3B, 
                0x45, 
                0x51, 
                0x5F
            })
            Name (BCL2, Package (0x0D)
            {
                0x64, 
                0x2E, 
                0x14, 
                0x19, 
                0x1F, 
                0x24, 
                0x29, 
                0x2E, 
                0x34, 
                0x3D, 
                0x48, 
                0x55, 
                0x64
            })
            Method (SBCM, 1, NotSerialized)
            {
                Store (Arg0, \_SB.PCI0.LPCB.EC0.BRTL)
                Store (Arg0, Z00B)
                TRAP (0x1C)
            }

            Device (PEGP)
            {
                Name (_ADR, 0x00010000)
                Method (_PRT, 0, NotSerialized)
                {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x13
                            }
                        })
                }

                Device (VGA)
                {
                    Name (_ADR, 0x00)
                    Name (SWIT, 0x01)
                    Name (CRTA, 0x01)
                    Name (LCDA, 0x01)
                    Name (TV0A, 0x01)
                    Name (HDTV, 0x01)
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }

                    Name (_PSC, 0x00)
                    Method (_PS0, 0, NotSerialized)
                    {
                        Store (0x00, _PSC)
                    }

                    Method (_PS3, 0, NotSerialized)
                    {
                        Store (0x03, _PSC)
                    }

                    Method (_DOS, 1, NotSerialized)
                    {
                        Store (And (Arg0, 0x03), SWIT)
                    }

                    Method (_DOD, 0, NotSerialized)
                    {
                        Return (Package (0x04)
                        {
                            0x00010100, 
                            0x00010118, 
                            0x00010200, 
                            0x00010121
                        })
                    }

                    Device (CRT)
                    {
                        Name (_ADR, 0x0100)
                        Method (_DCS, 0, NotSerialized)
                        {
                            If (CRTA)
                            {
                                Return (0x1F)
                            }
                            Else
                            {
                                Return (0x1D)
                            }
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (CRTA)
                            {
                                Return (0x01)
                            }
                            Else
                            {
                                Return (0x00)
                            }
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }

                    Device (TV0)
                    {
                        Name (_ADR, 0x0200)
                        Method (_DCS, 0, NotSerialized)
                        {
                            If (TV0A)
                            {
                                Return (0x1F)
                            }
                            Else
                            {
                                Return (0x1D)
                            }
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (TV0A)
                            {
                                Return (0x01)
                            }
                            Else
                            {
                                Return (0x00)
                            }
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }

                    Device (LCD)
                    {
                        Name (_ADR, 0x0118)
                        Method (_DCS, 0, NotSerialized)
                        {
                            If (LCDA)
                            {
                                Return (0x1F)
                            }
                            Else
                            {
                                Return (0x1D)
                            }
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (LCDA)
                            {
                                Return (0x01)
                            }
                            Else
                            {
                                Return (0x00)
                            }
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }

                        Method (_BCL, 0, NotSerialized)
                        {
                            If (LEqual (\_SB.PTPE, 0x01))
                            {
                                Return (\_SB.PCI0.BCL1)
                            }
                            Else
                            {
                                Return (\_SB.PCI0.BCL2)
                            }
                        }

                        Method (_BCM, 1, NotSerialized)
                        {
                            \_SB.PCI0.SBCM (Arg0)
                        }

                        Method (_BQC, 0, NotSerialized)
                        {
                            Return (\_SB.PCI0.LPCB.EC0.BRTL)
                        }
                    }

                    Device (HDMI)
                    {
                        Name (_ADR, 0x0121)
                        Method (_DCS, 0, NotSerialized)
                        {
                            If (HDTV)
                            {
                                Return (0x1F)
                            }
                            Else
                            {
                                Return (0x1D)
                            }
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (HDTV)
                            {
                                Return (0x01)
                            }
                            Else
                            {
                                Return (0x00)
                            }
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                        }
                    }
                }
            }

            Device (GFX0)
            {
                Name (_ADR, 0x00020000)
                Name (SWIT, 0x01)
                Method (_DOS, 1, NotSerialized)
                {
                    Store (Arg0, SWIT)
                    Store (And (Arg0, 0x03), DSEN)
                }

                Method (_DOD, 0, NotSerialized)
                {
                    If (LEqual (NDID, 0x01))
                    {
                        Name (TMP1, Package (0x01)
                        {
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP1, 0x00))
                        Return (TMP1)
                    }

                    If (LEqual (NDID, 0x02))
                    {
                        Name (TMP2, Package (0x02)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP2, 0x00))
                        Store (Or (0x00010000, DID2), Index (TMP2, 0x01))
                        Return (TMP2)
                    }

                    If (LEqual (NDID, 0x03))
                    {
                        Name (TMP3, Package (0x03)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP3, 0x00))
                        Store (Or (0x00010000, DID2), Index (TMP3, 0x01))
                        Store (Or (0x00010000, DID3), Index (TMP3, 0x02))
                        Return (TMP3)
                    }

                    If (LEqual (NDID, 0x04))
                    {
                        Name (TMP4, Package (0x04)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP4, 0x00))
                        Store (Or (0x00010000, DID2), Index (TMP4, 0x01))
                        Store (Or (0x00010000, DID3), Index (TMP4, 0x02))
                        Store (Or (0x00010000, DID4), Index (TMP4, 0x03))
                        Return (TMP4)
                    }

                    Name (TMP5, Package (0x05)
                    {
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF, 
                        0xFFFFFFFF
                    })
                    Store (Or (0x00010000, DID1), Index (TMP5, 0x00))
                    Store (Or (0x00010000, DID2), Index (TMP5, 0x01))
                    Store (Or (0x00010000, DID3), Index (TMP5, 0x02))
                    Store (Or (0x00010000, DID4), Index (TMP5, 0x03))
                    Store (Or (0x00010000, DID5), Index (TMP5, 0x04))
                    Return (TMP5)
                }

                Device (DD01)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID1))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (0x01)
                        If (And (CSTE, 0x01))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, 0x01))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD02)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID2))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (0x01)
                        If (And (CSTE, 0x02))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, 0x02))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD03)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID3))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (0x01)
                        If (And (CSTE, 0x04))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, 0x04))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD04)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID4))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (0x01)
                        If (And (CSTE, 0x08))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, 0x08))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }

                    Method (_BCL, 0, NotSerialized)
                    {
                        If (LEqual (\_SB.PTPE, 0x01))
                        {
                            Return (\_SB.PCI0.BCL1)
                        }
                        Else
                        {
                            Return (\_SB.PCI0.BCL2)
                        }
                    }

                    Method (_BCM, 1, NotSerialized)
                    {
                        \_SB.PCI0.SBCM (Arg0)
                    }

                    Method (_BQC, 0, NotSerialized)
                    {
                        Return (\_SB.PCI0.LPCB.EC0.BRTL)
                    }
                }

                Device (DD05)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        Return (And (0xFFFF, DID5))
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        TRAP (0x01)
                        If (And (CSTE, 0x10))
                        {
                            Return (0x1F)
                        }

                        Return (0x1D)
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        If (And (NSTE, 0x10))
                        {
                            Return (0x01)
                        }

                        Return (0x00)
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }
            }

            Device (HDEF)
            {
                Name (_ADR, 0x001B0000)
            }

            Device (RP01)
            {
                Name (_ADR, 0x001C0000)
                OperationRegion (P1CS, PCI_Config, 0x40, 0x0100)
                Field (P1CS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x1A), 
                    ABP1,   1, 
                        ,   2, 
                    PDC1,   1, 
                        ,   2, 
                    PDS1,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSP1,   1, 
                            Offset (0x9C), 
                        ,   30, 
                    HPCS,   1, 
                    PMCS,   1
                }

                Device (PXS1)
                {
                    Name (_ADR, 0x00)
                }

                Method (_PRT, 0, NotSerialized)
                {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x13
                            }
                        })
                }
            }

            Device (RP02)
            {
                Name (_ADR, 0x001C0001)
                Name (_HPP, Package (0x04)
                {
                    0x10, 
                    0x40, 
                    0x01, 
                    0x00
                })
                OperationRegion (P2CS, PCI_Config, 0x40, 0x0100)
                Field (P2CS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x1A), 
                    ABP2,   1, 
                        ,   2, 
                    PDC2,   1, 
                        ,   2, 
                    PDS2,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSP2,   1, 
                            Offset (0x98), 
                        ,   30, 
                    HPCE,   1, 
                    PMCE,   1, 
                        ,   30, 
                    HPCS,   1, 
                    PMCS,   1
                }

                Device (PXS2)
                {
                    Name (_ADR, 0x00)
                    Method (_RMV, 0, NotSerialized)
                    {
                        Return (0x01)
                    }

                    Method (_STA, 0, NotSerialized)
                    {
                        If (\_SB.PCI0.RP02.PDS2)
                        {
                            Return (0x0F)
                        }
                        Else
                        {
                            Return (0x00)
                        }
                    }
                }

                Name (_PRW, Package (0x02)
                {
                    0x09, 
                    0x03
                })
                Method (_PRT, 0, NotSerialized)
                {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x13
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x10
                            }
                        })
                }
            }

            Device (RP03)
            {
                Name (_ADR, 0x001C0002)
                OperationRegion (P3CS, PCI_Config, 0x40, 0x0100)
                Field (P3CS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x1A), 
                    ABP3,   1, 
                        ,   2, 
                    PDC3,   1, 
                        ,   2, 
                    PDS3,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSP3,   1, 
                            Offset (0x9C), 
                        ,   30, 
                    HPCS,   1, 
                    PMCS,   1
                }

                Device (PXS3)
                {
                    Name (_ADR, 0x00)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x04
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        If (\_SB.PCI0.RP03.PDS3)
                        {
                            Return (0x0F)
                        }
                        Else
                        {
                            Return (0x00)
                        }
                    }
                }

                Method (_PRT, 0, NotSerialized)
                {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x13
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x11
                            }
                        })
                }
            }

            Device (USB1)
            {
                Name (_ADR, 0x001D0000)
                OperationRegion (U1CS, PCI_Config, 0xC4, 0x04)
                Field (U1CS, DWordAcc, NoLock, Preserve)
                {
                    U1EN,   2
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB2)
            {
                Name (_ADR, 0x001D0001)
                OperationRegion (U2CS, PCI_Config, 0xC4, 0x04)
                Field (U2CS, DWordAcc, NoLock, Preserve)
                {
                    U2EN,   2
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB3)
            {
                Name (_ADR, 0x001D0002)
                OperationRegion (U2CS, PCI_Config, 0xC4, 0x04)
                Field (U2CS, DWordAcc, NoLock, Preserve)
                {
                    U3EN,   2
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB4)
            {
                Name (_ADR, 0x001D0003)
                Device (HUB4)
                {
                    Name (_ADR, 0x00)
                    Device (EXPC)
                    {
                        Name (_ADR, 0x01)
                    }

                    Device (NEXP)
                    {
                        Name (_ADR, 0x02)
                        Name (_EJD, "_SB.PCI0.RP02.PXS2")
                    }
                }

                OperationRegion (U4CS, PCI_Config, 0xC4, 0x04)
                Field (U4CS, DWordAcc, NoLock, Preserve)
                {
                    U4EN,   2
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB7)
            {
                Name (_ADR, 0x001D0007)
            }

            Device (PCIB)
            {
                Name (_ADR, 0x001E0000)
                Device (LANC)
                {
                    Name (_ADR, 0x00080000)
                    Name (_PRW, Package (0x02)
                    {
                        0x0B, 
                        0x04
                    })
                }

                Device (CARD)
                {
                    Name (_ADR, 0x00090000)
                }

                Method (_PRT, 0, NotSerialized)
                {
                        Return (Package (0x06)
                        {
                            Package (0x04)
                            {
                                0x0008FFFF, 
                                0x00, 
                                0x00, 
                                0x14
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x00, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x01, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x02, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x03, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0x0005FFFF, 
                                0x04, 
                                0x00, 
                                0x11
                            }
                        })
                }
            }

            Device (LPCB)
            {
                Name (_ADR, 0x001F0000)
                OperationRegion (LPC0, PCI_Config, 0x40, 0xC0)
                Field (LPC0, AnyAcc, NoLock, Preserve)
                {
                            Offset (0x20), 
                    PARC,   8, 
                    PBRC,   8, 
                    PCRC,   8, 
                    PDRC,   8, 
                            Offset (0x28), 
                    PERC,   8, 
                    PFRC,   8, 
                    PGRC,   8, 
                    PHRC,   8, 
                            Offset (0x40), 
                    IOD0,   8, 
                    IOD1,   8
                }

                Name (IPRA, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {11}
                })
                Name (IPRB, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {3}
                })
                Name (IPRC, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {3}
                })
                Name (IPRD, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {4}
                })
                Name (IPRE, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {10}
                })
                Name (IPRF, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {11}
                })
                Name (IPRG, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {5}
                })
                Name (IPRH, ResourceTemplate ()
                {
                    IRQ (Level, ActiveLow, Shared, )
                        {7}
                })
                Device (LNKA)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x01)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PARC)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (IPRA)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLA, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y0F)
                                {}
                        })
                        CreateWordField (RTLA, \_SB.PCI0.LPCB.LNKA._CRS._Y0F._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PARC, 0x0F), IRQ0)
                        Return (RTLA)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PARC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PARC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKB)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x02)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PBRC)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (IPRB)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLB, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y10)
                                {}
                        })
                        CreateWordField (RTLB, \_SB.PCI0.LPCB.LNKB._CRS._Y10._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PBRC, 0x0F), IRQ0)
                        Return (RTLB)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PBRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PBRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKC)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x03)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PCRC)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (IPRC)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLC, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y11)
                                {}
                        })
                        CreateWordField (RTLC, \_SB.PCI0.LPCB.LNKC._CRS._Y11._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PCRC, 0x0F), IRQ0)
                        Return (RTLC)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PCRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PCRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKD)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x04)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PDRC)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (IPRD)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLD, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y12)
                                {}
                        })
                        CreateWordField (RTLD, \_SB.PCI0.LPCB.LNKD._CRS._Y12._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PDRC, 0x0F), IRQ0)
                        Return (RTLD)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PDRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PDRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKE)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x05)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PERC)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (IPRE)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLE, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y13)
                                {}
                        })
                        CreateWordField (RTLE, \_SB.PCI0.LPCB.LNKE._CRS._Y13._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PERC, 0x0F), IRQ0)
                        Return (RTLE)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PERC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PERC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKF)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x06)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PFRC)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (IPRF)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLF, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y14)
                                {}
                        })
                        CreateWordField (RTLF, \_SB.PCI0.LPCB.LNKF._CRS._Y14._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PFRC, 0x0F), IRQ0)
                        Return (RTLF)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PFRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PFRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKG)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x07)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PGRC)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (IPRG)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLG, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y15)
                                {}
                        })
                        CreateWordField (RTLG, \_SB.PCI0.LPCB.LNKG._CRS._Y15._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PGRC, 0x0F), IRQ0)
                        Return (RTLG)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PGRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PGRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKH)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x08)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PHRC)
                    }

                    Method (_PRS, 0, NotSerialized)
                    {
                        Return (IPRH)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLH, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y16)
                                {}
                        })
                        CreateWordField (RTLH, \_SB.PCI0.LPCB.LNKH._CRS._Y16._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PHRC, 0x0F), IRQ0)
                        Return (RTLH)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PHRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PHRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (EC0)
                {
                    Name (_HID, EisaId ("PNP0C09"))
                    Name (_UID, 0x01)
                    Method (_CRS, 0, NotSerialized)
                    {
                        Name (BFFR, ResourceTemplate ()
                        {
                            IO (Decode16,
                                0x0062,             // Range Minimum
                                0x0062,             // Range Maximum
                                0x00,               // Alignment
                                0x01,               // Length
                                )
                            IO (Decode16,
                                0x0066,             // Range Minimum
                                0x0066,             // Range Maximum
                                0x00,               // Alignment
                                0x01,               // Length
                                )
                        })
                        Return (BFFR)
                    }

                    OperationRegion (ERAM, EmbeddedControl, 0x00, 0xFF)
                    Field (ERAM, ByteAcc, NoLock, Preserve)
                    {
                        SMPR,   8, 
                        SMST,   8, 
                        SMAD,   8, 
                        SMCM,   8, 
                        SMD0,   256, 
                        BCNT,   8, 
                                Offset (0x40), 
                        SW2S,   1, 
                                Offset (0x4E), 
                        LIDE,   1, 
                                Offset (0x52), 
                        LIDS,   1, 
                        WBSS,   1, 
                                Offset (0x59), 
                        ECT1,   8, 
                        ECT2,   8, 
                        RG5B,   8, 
                                Offset (0x82), 
                        MBST,   8, 
                                Offset (0x85), 
                        MBRM,   16, 
                        MBCV,   16, 
                                Offset (0xA0), 
                        QBHK,   8, 
                                Offset (0xA2), 
                        QBBB,   8, 
                                Offset (0xA4), 
                        MBTS,   1, 
                        MBTF,   1, 
                                Offset (0xA5), 
                        MBTC,   1, 
                            ,   2, 
                        MBNH,   1, 
                                Offset (0xA6), 
                        BA1C,   8, 
                                Offset (0xCF), 
                        DLYC,   8, 
                        EBPL,   1, 
                                Offset (0xD6), 
                        DBPL,   8, 
                                Offset (0xDB), 
                        PSKB,   1, 
                        PSTP,   1, 
                        PSBA,   1, 
                                Offset (0xDF), 
                        ECBW,   1, 
                                Offset (0xE0), 
                        DLYT,   8, 
                                Offset (0xE2), 
                        BRTL,   8, 
                                Offset (0xE6), 
                        SFHK,   8
                    }

                    Name (BATO, 0x00)
                    Name (BATN, 0x00)
                    Name (BATF, 0xC0)
                    Name (WBDS, 0x00)
                    Method (_REG, 2, NotSerialized)
                    {
                        If (LAnd (LEqual (Arg0, 0x03), LEqual (Arg1, 0x01)))
                        {
                            Store (0x01, ECON)
                        }
                    }

                    Method (BPOL, 1, NotSerialized)
                    {
                        Store (Arg0, DBPL)
                        Store (0x01, EBPL)
                    }

                    Method (BPOM, 0, NotSerialized)
                    {
                        Store (0x00, DBPL)
                        Store (0x00, EBPL)
                    }

                    Name (_GPE, 0x17)
                    Method (_Q09, 0, NotSerialized)
                    {
                        If (LGreaterEqual (OSYS, 0x07D1))
                        {
                            BPOM ()
                            Notify (\_SB.BAT0, 0x80)
                            Notify (\_SB.ACAD, 0x80)
                        }

                        If (LEqual (OSYS, 0x07D0))
                        {
                            Notify (\_SB.BAT0, 0x80)
                            Notify (\_SB.BAT0, 0x00)
                            Notify (\_SB.ACAD, 0x00)
                        }

                        If (WBDS)
                        {
                            If (WBSS)
                            {
                                Store (0x01, GP26)
                                Store (0x01, GP25)
                                Store (0x01, \_SB.BTLS)
                            }
                            Else
                            {
                                Store (0x00, GP26)
                                Store (0x00, GP25)
                                Store (0x00, \_SB.BTLS)
                            }

                            Store (0x05, \_SB.WMID.Z00X)
                            Store (0x00, \_SB.WMID.Z00Y)
                            Notify (\_SB.WMID, 0x80)
                            Store (0x00, WBDS)
                        }
                    }

                    Method (_Q20, 0, NotSerialized)
                    {
                        GBAS ()
                        If (And (0x40, BATF))
                        {
                            Notify (\_SB.BAT0, 0x81)
                        }

                        If (And (0x02, BATF))
                        {
                            Notify (\_PR.CPU0, 0x80)
                            Notify (\_SB.ACAD, 0x80)
                        }

                        Notify (\_SB.BAT0, 0x80)
                        BPOL (0x05)
                    }

                    Method (GBAS, 0, NotSerialized)
                    {
                        Store (0x00, BATF)
                        Store (MBTS, Local0)
                        Store (SW2S, Local1)
                        ShiftLeft (Local0, 0x06, Local0)
                        ShiftLeft (Local1, 0x01, Local1)
                        If (LNotEqual (And (BATO, 0x40), Local0))
                        {
                            Or (BATF, 0x40, BATF)
                        }

                        If (LNotEqual (And (BATO, 0x02), Local1))
                        {
                            Or (BATF, 0x02, BATF)
                        }

                        Store (BATF, BATO)
                    }

                    Method (_Q80, 0, NotSerialized)
                    {
                        Store ("_Q80 : Temperature Up", Debug)
                        Notify (\_TZ.THR1, 0x80)
                    }

                    Method (_Q81, 0, NotSerialized)
                    {
                        Store ("_Q81 : Temperature Down", Debug)
                        Notify (\_TZ.THR1, 0x80)
                    }

                    Name (SUDK, 0x00)
                    Method (_Q8A, 0, NotSerialized)
                    {
                        If (LIDE)
                        {
                            Store ("_Q8A : LID Switch Event", Debug)
                            Store (0x01, LIDE)
                            Notify (\_SB.LID, 0x80)
                        }
                    }

                    Mutex (VGMX, 0x00)
                    Method (_Q0D, 0, NotSerialized)
                    {
                        Store ("_Q0D : Switch Display (Fn+F4)", Debug)
                        TRAP (0x19)
                        If (LEqual (EXTM, 0x00))
                        {
                            If (LLessEqual (\_SB.PFID, 0x01))
                            {
                                If (LEqual (EXCM, 0x00))
                                {
                                    If (IGDS)
                                    {
                                        Store (0x01, TLST)
                                        HKDS (0x0A)
                                        BPOL (0x03)
                                    }
                                }
                            }
                            Else
                            {
                                TRAP (0x1B)
                                Store (Z00A, Local0)
                                Store (And (Local0, 0x01), \_SB.PCI0.PEGP.VGA.LCDA)
                                Store (ShiftRight (And (Local0, 0x02), 0x01), \_SB.PCI0.PEGP.VGA.CRTA)
                                Store (ShiftRight (And (Local0, 0x04), 0x02), \_SB.PCI0.PEGP.VGA.TV0A)
                                Store (ShiftRight (And (Local0, 0x08), 0x03), \_SB.PCI0.PEGP.VGA.HDTV)
                                Notify (\_SB.PCI0.PEGP.VGA, 0x80)
                            }
                        }
                    }

                    Method (_Q0E, 0, NotSerialized)
                    {
                        Notify (\_SB.SLPB, 0x80)
                    }

                    Method (_Q11, 0, NotSerialized)
                    {
                        If (LEqual (OSYS, 0x07D6))
                        {
                            If (IGDS)
                            {
                                Notify (\_SB.PCI0.GFX0.DD04, 0x86)
                            }
                            Else
                            {
                                Notify (\_SB.PCI0.PEGP.VGA.LCD, 0x86)
                            }
                        }
                        Else
                        {
                            Store (0x14, SMIF)
                            Store (0x00, TRP0)
                        }

                        Sleep (0x32)
                    }

                    Method (_Q10, 0, NotSerialized)
                    {
                        If (LEqual (OSYS, 0x07D6))
                        {
                            If (IGDS)
                            {
                                Notify (\_SB.PCI0.GFX0.DD04, 0x87)
                            }
                            Else
                            {
                                Notify (\_SB.PCI0.PEGP.VGA.LCD, 0x87)
                            }
                        }
                        Else
                        {
                            Store (0x15, SMIF)
                            Store (0x00, TRP0)
                        }

                        Sleep (0x32)
                    }

                    Method (_Q15, 0, NotSerialized)
                    {
                        Store ("!!! Wireless Button pressed !!!", Debug)
                        If (\_SB.PCI0.LPCB.EC0.WBSS)
                        {
                            Store (0x00, BTLS)
                        }
                        Else
                        {
                            Store (0x01, BTLS)
                        }

                        If (LOr (\_SB.BTSU, \_SB.WLSU))
                        {
                            If (\_SB.BTLS)
                            {
                                Store (0x00, \_SB.BTLS)
                                Store (0x00, GP25)
                                Store (0x00, GP26)
                            }
                            Else
                            {
                                Store (0x01, \_SB.BTLS)
                                If (\_SB.WLSU)
                                {
                                    If (\_SB.WIRE)
                                    {
                                        If (\_SB.WWLS)
                                        {
                                            Store (0x01, GP26)
                                        }
                                    }
                                    Else
                                    {
                                        Store (0x01, GP26)
                                    }
                                }

                                If (\_SB.BTSU)
                                {
                                    If (\_SB.WIRE)
                                    {
                                        If (\_SB.BWLS)
                                        {
                                            Store (0x01, GP25)
                                        }
                                    }
                                    Else
                                    {
                                        Store (0x01, GP25)
                                    }
                                }
                            }
                        }
                        Else
                        {
                            Store (0x00, \_SB.BTLS)
                            Store (0x00, GP25)
                            Store (0x00, GP26)
                        }

                        Store (0x05, \_SB.WMID.Z00X)
                        Store (0x00, \_SB.WMID.Z00Y)
                        Notify (\_SB.WMID, 0x80)
                    }

                    Method (_Q16, 0, NotSerialized)
                    {
                        Store ("!!! DVD/Music Button pressed !!!", Debug)
                        If (LEqual (OSYS, 0x07D6))
                        {
                            If (ECON)
                            {
                                Store (\_SB.PCI0.LPCB.EC0.QBBB, Local0)
                                If (LEqual (Local0, 0x04))
                                {
                                    Notify (\_SB.QBTN, 0x80)
                                }

                                If (LEqual (Local0, 0x05))
                                {
                                    Notify (\_SB.DBTN, 0x80)
                                }

                                If (LEqual (Local0, 0x03))
                                {
                                    Notify (\_SB.MBTN, 0x80)
                                }

                                If (LEqual (Local0, 0x10))
                                {
                                    Notify (\_SB.EBTN, 0x80)
                                }

                                If (LEqual (Local0, 0x06))
                                {
                                    Notify (\_SB.PBTN, 0x80)
                                }

                                If (LEqual (Local0, 0x12))
                                {
                                    Notify (\_SB.VBTN, 0x80)
                                }

                                If (LEqual (Local0, 0x11))
                                {
                                    Notify (\_SB.TBTN, 0x80)
                                }
                            }
                        }
                        Else
                        {
                            Store (0x04, \_SB.WMID.Z00X)
                            Store (0x00, \_SB.WMID.Z00Y)
                            Notify (\_SB.WMID, 0x80)
                        }
                    }

                    Method (_Q8E, 0, NotSerialized)
                    {
                        Store ("!!! CPU Throttling. !!!", Debug)
                        TRAP (0x1E)
                    }

                    Method (_Q8F, 0, NotSerialized)
                    {
                        Store ("!!! Restore CPU Throttling to default setting. !!!", Debug)
                        TRAP (0x1F)
                    }

                    Field (ERAM, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x04), 
                        SMW0,   16
                    }

                    Field (ERAM, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x04), 
                        SMB0,   8
                    }

                    Field (ERAM, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x04), 
                        FLD0,   64
                    }

                    Field (ERAM, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x04), 
                        FLD1,   128
                    }

                    Field (ERAM, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x04), 
                        FLD2,   192
                    }

                    Field (ERAM, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0x04), 
                        FLD3,   256
                    }

                    Mutex (MUT0, 0x00)
                    Method (SMRD, 4, NotSerialized)
                    {
                        If (LNot (ECON))
                        {
                            Return (0xFF)
                        }

                        If (LNotEqual (Arg0, 0x07))
                        {
                            If (LNotEqual (Arg0, 0x09))
                            {
                                If (LNotEqual (Arg0, 0x0B))
                                {
                                    Return (0x19)
                                }
                            }
                        }

                        Acquire (MUT0, 0xFFFF)
                        Store (0x04, Local0)
                        While (LGreater (Local0, 0x01))
                        {
                            And (SMST, 0x40, SMST)
                            Store (Arg2, SMCM)
                            Store (Arg1, SMAD)
                            Store (Arg0, SMPR)
                            Store (0x00, Local3)
                            While (LNot (And (SMST, 0xBF, Local1)))
                            {
                                Sleep (0x02)
                                Increment (Local3)
                                If (LEqual (Local3, 0x32))
                                {
                                    And (SMST, 0x40, SMST)
                                    Store (Arg2, SMCM)
                                    Store (Arg1, SMAD)
                                    Store (Arg0, SMPR)
                                    Store (0x00, Local3)
                                }
                            }

                            If (LEqual (Local1, 0x80))
                            {
                                Store (0x00, Local0)
                            }
                            Else
                            {
                                Decrement (Local0)
                            }
                        }

                        If (Local0)
                        {
                            Store (And (Local1, 0x1F), Local0)
                        }
                        Else
                        {
                            If (LEqual (Arg0, 0x07))
                            {
                                Store (SMB0, Arg3)
                            }

                            If (LEqual (Arg0, 0x09))
                            {
                                Store (SMW0, Arg3)
                            }

                            If (LEqual (Arg0, 0x0B))
                            {
                                Store (BCNT, Local3)
                                ShiftRight (0x0100, 0x03, Local2)
                                If (LGreater (Local3, Local2))
                                {
                                    Store (Local2, Local3)
                                }

                                If (LLess (Local3, 0x09))
                                {
                                    Store (FLD0, Local2)
                                }
                                Else
                                {
                                    If (LLess (Local3, 0x11))
                                    {
                                        Store (FLD1, Local2)
                                    }
                                    Else
                                    {
                                        If (LLess (Local3, 0x19))
                                        {
                                            Store (FLD2, Local2)
                                        }
                                        Else
                                        {
                                            Store (FLD3, Local2)
                                        }
                                    }
                                }

                                Increment (Local3)
                                Store (Buffer (Local3) {}, Local4)
                                Decrement (Local3)
                                Store (Zero, Local5)
                                While (LGreater (Local3, Local5))
                                {
                                    GBFE (Local2, Local5, RefOf (Local6))
                                    PBFE (Local4, Local5, Local6)
                                    Increment (Local5)
                                }

                                PBFE (Local4, Local5, 0x00)
                                Store (Local4, Arg3)
                            }
                        }

                        Release (MUT0)
                        Return (Local0)
                    }

                    Method (SMWR, 4, NotSerialized)
                    {
                        If (LNot (ECON))
                        {
                            Return (0xFF)
                        }

                        If (LNotEqual (Arg0, 0x06))
                        {
                            If (LNotEqual (Arg0, 0x08))
                            {
                                If (LNotEqual (Arg0, 0x0A))
                                {
                                    Return (0x19)
                                }
                            }
                        }

                        Acquire (MUT0, 0xFFFF)
                        Store (0x04, Local0)
                        While (LGreater (Local0, 0x01))
                        {
                            If (LEqual (Arg0, 0x06))
                            {
                                Store (Arg3, SMB0)
                            }

                            If (LEqual (Arg0, 0x08))
                            {
                                Store (Arg3, SMW0)
                            }

                            If (LEqual (Arg0, 0x0A))
                            {
                                Store (Arg3, SMD0)
                            }

                            And (SMST, 0x40, SMST)
                            Store (Arg2, SMCM)
                            Store (Arg1, SMAD)
                            Store (Arg0, SMPR)
                            Store (0x00, Local3)
                            While (LNot (And (SMST, 0xBF, Local1)))
                            {
                                Sleep (0x02)
                                Increment (Local3)
                                If (LEqual (Local3, 0x32))
                                {
                                    And (SMST, 0x40, SMST)
                                    Store (Arg2, SMCM)
                                    Store (Arg1, SMAD)
                                    Store (Arg0, SMPR)
                                    Store (0x00, Local3)
                                }
                            }

                            If (LEqual (Local1, 0x80))
                            {
                                Store (0x00, Local0)
                            }
                            Else
                            {
                                Decrement (Local0)
                            }
                        }

                        If (Local0)
                        {
                            Store (And (Local1, 0x1F), Local0)
                        }

                        Release (MUT0)
                        Return (Local0)
                    }

                    Method (Z00Z, 0, Serialized)
                    {
                        If (ECON)
                        {
                            Store (SFHK, Local0)
                        }

                        Return (Local0)
                    }

                    Method (Z010, 1, Serialized)
                    {
                        If (ECON)
                        {
                            Store (Arg0, SFHK)
                        }
                    }
                }

                Device (DMAC)
                {
                    Name (_HID, EisaId ("PNP0200"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        IO (Decode16,
                            0x0081,             // Range Minimum
                            0x0081,             // Range Maximum
                            0x01,               // Alignment
                            0x11,               // Length
                            )
                        IO (Decode16,
                            0x0093,             // Range Minimum
                            0x0093,             // Range Maximum
                            0x01,               // Alignment
                            0x0D,               // Length
                            )
                        IO (Decode16,
                            0x00C0,             // Range Minimum
                            0x00C0,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        DMA (Compatibility, NotBusMaster, Transfer8_16, )
                            {4}
                    })
                }

                Device (HPET)
                {
                    Name (_HID, EisaId ("PNP0103"))
                    Name (_CID, EisaId ("PNP0C01"))
                    Name (BUF0, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadOnly,
                            0xFED00000,         // Address Base
                            0x00000400,         // Address Length
                            _Y17)
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        If (LGreaterEqual (OSYS, 0x07D1))
                        {
                            If (HPAE)
                            {
                                Return (0x0F)
                            }
                        }
                        Else
                        {
                            If (HPAE)
                            {
                                Return (0x0B)
                            }
                        }

                        Return (0x00)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        If (HPAE)
                        {
                            CreateDWordField (BUF0, \_SB.PCI0.LPCB.HPET._Y17._BAS, HPT0)
                            If (LEqual (HPAS, 0x01))
                            {
                                Store (0xFED01000, HPT0)
                            }

                            If (LEqual (HPAS, 0x02))
                            {
                                Store (0xFED02000, HPT0)
                            }

                            If (LEqual (HPAS, 0x03))
                            {
                                Store (0xFED03000, HPT0)
                            }
                        }

                        Return (BUF0)
                    }
                }

                Device (IPIC)
                {
                    Name (_HID, EisaId ("PNP0000"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0020,             // Range Minimum
                            0x0020,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0024,             // Range Minimum
                            0x0024,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0028,             // Range Minimum
                            0x0028,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x002C,             // Range Minimum
                            0x002C,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0030,             // Range Minimum
                            0x0030,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0034,             // Range Minimum
                            0x0034,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0038,             // Range Minimum
                            0x0038,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x003C,             // Range Minimum
                            0x003C,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A0,             // Range Minimum
                            0x00A0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A4,             // Range Minimum
                            0x00A4,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A8,             // Range Minimum
                            0x00A8,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00AC,             // Range Minimum
                            0x00AC,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B0,             // Range Minimum
                            0x00B0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B4,             // Range Minimum
                            0x00B4,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B8,             // Range Minimum
                            0x00B8,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00BC,             // Range Minimum
                            0x00BC,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x04D0,             // Range Minimum
                            0x04D0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IRQNoFlags ()
                            {2}
                    })
                }

                Device (MATH)
                {
                    Name (_HID, EisaId ("PNP0C04"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x00F0,             // Range Minimum
                            0x00F0,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IRQNoFlags ()
                            {13}
                    })
                }

                Device (LDRC)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x02)
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x002E,             // Range Minimum
                            0x002E,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0061,             // Range Minimum
                            0x0061,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0063,             // Range Minimum
                            0x0063,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0065,             // Range Minimum
                            0x0065,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0067,             // Range Minimum
                            0x0067,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0080,             // Range Minimum
                            0x0080,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0092,             // Range Minimum
                            0x0092,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x00B2,             // Range Minimum
                            0x00B2,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0380,             // Range Minimum
                            0x0380,             // Range Maximum
                            0x01,               // Alignment
                            0x04,               // Length
                            )
                        IO (Decode16,
                            0x0680,             // Range Minimum
                            0x0680,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        IO (Decode16,
                            0x0800,             // Range Minimum
                            0x0800,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x1000,             // Range Minimum
                            0x1000,             // Range Maximum
                            0x01,               // Alignment
                            0x80,               // Length
                            )
                        IO (Decode16,
                            0x1180,             // Range Minimum
                            0x1180,             // Range Maximum
                            0x01,               // Alignment
                            0x40,               // Length
                            )
                        IO (Decode16,
                            0x1640,             // Range Minimum
                            0x1640,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                    })
                }

                Device (CDRC)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x03)
                    Name (BUF0, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x06B0,             // Range Minimum
                            0x06B0,             // Range Maximum
                            0x01,               // Alignment
                            0x40,               // Length
                            )
                    })
                    Name (BUF1, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x06B0,             // Range Minimum
                            0x06B0,             // Range Maximum
                            0x01,               // Alignment
                            0x50,               // Length
                            )
                    })
                    Name (BUF2, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x06A0,             // Range Minimum
                            0x06A0,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x06B0,             // Range Minimum
                            0x06B0,             // Range Maximum
                            0x01,               // Alignment
                            0x40,               // Length
                            )
                    })
                    Name (BUF3, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x06A0,             // Range Minimum
                            0x06A0,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x06B0,             // Range Minimum
                            0x06B0,             // Range Maximum
                            0x01,               // Alignment
                            0x50,               // Length
                            )
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        If (EMAE)
                        {
                            If (CIRP)
                            {
                                Return (BUF0)
                            }

                            Return (BUF1)
                        }
                        Else
                        {
                            If (CIRP)
                            {
                                Return (BUF2)
                            }

                            Return (BUF3)
                        }
                    }
                }

                Device (RTC)
                {
                    Name (_HID, EisaId ("PNP0B00"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x01,               // Alignment
                            0x08,               // Length
                            )
                        IRQNoFlags ()
                            {8}
                    })
                }

                Device (TIMR)
                {
                    Name (_HID, EisaId ("PNP0100"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0040,             // Range Minimum
                            0x0040,             // Range Maximum
                            0x01,               // Alignment
                            0x04,               // Length
                            )
                        IO (Decode16,
                            0x0050,             // Range Minimum
                            0x0050,             // Range Maximum
                            0x10,               // Alignment
                            0x04,               // Length
                            )
                        IRQNoFlags ()
                            {0}
                    })
                }

                Device (QLBD)
                {
                    Name (_HID, "HPQ0006")
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }
                }

                Device (PS2K)
                {
                    Name (_HID, EisaId ("PNP0303"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0060,             // Range Minimum
                            0x0060,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0064,             // Range Minimum
                            0x0064,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IRQ (Edge, ActiveHigh, Exclusive, )
                            {1}
                    })
                    Name (_PRW, Package (0x02)
                    {
                        0x19, 
                        0x03
                    })
                    Method (_PSW, 1, NotSerialized)
                    {
                        If (ECON)
                        {
                            Store (Arg0, \_SB.PCI0.LPCB.EC0.PSKB)
                        }
                    }
                }

                Device (PS2M)
                {
                    Method (_HID, 0, NotSerialized)
                    {
                        If (HPBD)
                        {
                            Return ("*SYN012C")
                        }
                        Else
                        {
                            Return ("*SYN012B")
                        }
                    }

                    Name (_CID, Package (0x03)
                    {
                        EisaId ("SYN0100"), 
                        EisaId ("SYN0002"), 
                        EisaId ("PNP0F13")
                    })
                    Name (_CRS, ResourceTemplate ()
                    {
                        IRQ (Edge, ActiveHigh, Exclusive, )
                            {12}
                    })
                    Name (_PRW, Package (0x02)
                    {
                        0x19, 
                        0x03
                    })
                    Method (_PSW, 1, NotSerialized)
                    {
                        If (ECON)
                        {
                            Store (Arg0, \_SB.PCI0.LPCB.EC0.PSTP)
                        }
                    }
                }
            }

            Device (PATA)
            {
                Name (_ADR, 0x001F0001)
                OperationRegion (PACS, PCI_Config, 0x40, 0xC0)
                Field (PACS, DWordAcc, NoLock, Preserve)
                {
                    PRIT,   16, 
                            Offset (0x04), 
                    PSIT,   4, 
                            Offset (0x08), 
                    SYNC,   4, 
                            Offset (0x0A), 
                    SDT0,   2, 
                        ,   2, 
                    SDT1,   2, 
                            Offset (0x14), 
                    ICR0,   4, 
                    ICR1,   4, 
                    ICR2,   4, 
                    ICR3,   4, 
                    ICR4,   4, 
                    ICR5,   4
                }

                Device (PRID)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Name (PBUF, Buffer (0x14)
                        {
                            /* 0000 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                            /* 0008 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                            /* 0010 */    0x00, 0x00, 0x00, 0x00
                        })
                        CreateDWordField (PBUF, 0x00, PIO0)
                        CreateDWordField (PBUF, 0x04, DMA0)
                        CreateDWordField (PBUF, 0x08, PIO1)
                        CreateDWordField (PBUF, 0x0C, DMA1)
                        CreateDWordField (PBUF, 0x10, FLAG)
                        Store (GETP (PRIT), PIO0)
                        Store (GDMA (And (SYNC, 0x01), And (ICR3, 0x01), 
                            And (ICR0, 0x01), SDT0, And (ICR1, 0x01)), DMA0)
                        If (LEqual (DMA0, 0xFFFFFFFF))
                        {
                            Store (PIO0, DMA0)
                        }

                        If (And (PRIT, 0x4000))
                        {
                            If (LEqual (And (PRIT, 0x90), 0x80))
                            {
                                Store (0x0384, PIO1)
                            }
                            Else
                            {
                                Store (GETT (PSIT), PIO1)
                            }
                        }
                        Else
                        {
                            Store (0xFFFFFFFF, PIO1)
                        }

                        Store (GDMA (And (SYNC, 0x02), And (ICR3, 0x02), 
                            And (ICR0, 0x02), SDT1, And (ICR1, 0x02)), DMA1)
                        If (LEqual (DMA1, 0xFFFFFFFF))
                        {
                            Store (PIO1, DMA1)
                        }

                        Store (GETF (And (SYNC, 0x01), And (SYNC, 0x02), 
                            PRIT), FLAG)
                        If (And (LEqual (PIO0, 0xFFFFFFFF), LEqual (DMA0, 0xFFFFFFFF)))
                        {
                            Store (0x78, PIO0)
                            Store (0x14, DMA0)
                            Store (0x03, FLAG)
                        }

                        Return (PBUF)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        CreateDWordField (Arg0, 0x00, PIO0)
                        CreateDWordField (Arg0, 0x04, DMA0)
                        CreateDWordField (Arg0, 0x08, PIO1)
                        CreateDWordField (Arg0, 0x0C, DMA1)
                        CreateDWordField (Arg0, 0x10, FLAG)
                        If (LEqual (SizeOf (Arg1), 0x0200))
                        {
                            And (PRIT, 0xC0F0, PRIT)
                            And (SYNC, 0x02, SYNC)
                            Store (0x00, SDT0)
                            And (ICR0, 0x02, ICR0)
                            And (ICR1, 0x02, ICR1)
                            And (ICR3, 0x02, ICR3)
                            And (ICR5, 0x02, ICR5)
                            CreateWordField (Arg1, 0x62, W490)
                            CreateWordField (Arg1, 0x6A, W530)
                            CreateWordField (Arg1, 0x7E, W630)
                            CreateWordField (Arg1, 0x80, W640)
                            CreateWordField (Arg1, 0xB0, W880)
                            CreateWordField (Arg1, 0xBA, W930)
                            Or (PRIT, 0x8000, PRIT)
                            If (LAnd (And (FLAG, 0x02), And (W490, 0x0800)))
                            {
                                Or (PRIT, 0x02, PRIT)
                            }

                            Or (PRIT, SETP (PIO0, W530, W640), PRIT)
                            If (And (FLAG, 0x01))
                            {
                                Or (SYNC, 0x01, SYNC)
                                Store (SDMA (DMA0), SDT0)
                                If (LLess (DMA0, 0x1E))
                                {
                                    Or (ICR3, 0x01, ICR3)
                                }

                                If (LLess (DMA0, 0x3C))
                                {
                                    Or (ICR0, 0x01, ICR0)
                                }

                                If (And (W930, 0x2000))
                                {
                                    Or (ICR1, 0x01, ICR1)
                                }
                            }
                        }

                        If (LEqual (SizeOf (Arg2), 0x0200))
                        {
                            And (PRIT, 0xBF0F, PRIT)
                            Store (0x00, PSIT)
                            And (SYNC, 0x01, SYNC)
                            Store (0x00, SDT1)
                            And (ICR0, 0x01, ICR0)
                            And (ICR1, 0x01, ICR1)
                            And (ICR3, 0x01, ICR3)
                            And (ICR5, 0x01, ICR5)
                            CreateWordField (Arg2, 0x62, W491)
                            CreateWordField (Arg2, 0x6A, W531)
                            CreateWordField (Arg2, 0x7E, W631)
                            CreateWordField (Arg2, 0x80, W641)
                            CreateWordField (Arg2, 0xB0, W881)
                            CreateWordField (Arg2, 0xBA, W931)
                            Or (PRIT, 0x8040, PRIT)
                            If (LAnd (And (FLAG, 0x08), And (W491, 0x0800)))
                            {
                                Or (PRIT, 0x20, PRIT)
                            }

                            If (And (FLAG, 0x10))
                            {
                                Or (PRIT, 0x4000, PRIT)
                                If (LGreater (PIO1, 0xF0))
                                {
                                    Or (PRIT, 0x80, PRIT)
                                }
                                Else
                                {
                                    Or (PRIT, 0x10, PRIT)
                                    Store (SETT (PIO1, W531, W641), PSIT)
                                }
                            }

                            If (And (FLAG, 0x04))
                            {
                                Or (SYNC, 0x02, SYNC)
                                Store (SDMA (DMA1), SDT1)
                                If (LLess (DMA1, 0x1E))
                                {
                                    Or (ICR3, 0x02, ICR3)
                                }

                                If (LLess (DMA1, 0x3C))
                                {
                                    Or (ICR0, 0x02, ICR0)
                                }

                                If (And (W931, 0x2000))
                                {
                                    Or (ICR1, 0x02, ICR1)
                                }
                            }
                        }
                    }

                    Device (P_D0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Name (PIB0, Buffer (0x0E)
                            {
                                /* 0000 */    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF, 0x03, 
                                /* 0008 */    0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                            })
                            CreateByteField (PIB0, 0x01, PMD0)
                            CreateByteField (PIB0, 0x08, DMD0)
                            If (And (PRIT, 0x02))
                            {
                                If (LEqual (And (PRIT, 0x09), 0x08))
                                {
                                    Store (0x08, PMD0)
                                }
                                Else
                                {
                                    Store (0x0A, PMD0)
                                    ShiftRight (And (PRIT, 0x0300), 0x08, Local0)
                                    ShiftRight (And (PRIT, 0x3000), 0x0C, Local1)
                                    Add (Local0, Local1, Local2)
                                    If (LEqual (0x03, Local2))
                                    {
                                        Store (0x0B, PMD0)
                                    }

                                    If (LEqual (0x05, Local2))
                                    {
                                        Store (0x0C, PMD0)
                                    }
                                }
                            }
                            Else
                            {
                                Store (0x01, PMD0)
                            }

                            If (And (SYNC, 0x01))
                            {
                                Store (Or (SDT0, 0x40), DMD0)
                                If (And (ICR1, 0x01))
                                {
                                    If (And (ICR0, 0x01))
                                    {
                                        Add (DMD0, 0x02, DMD0)
                                    }

                                    If (And (ICR3, 0x01))
                                    {
                                        Store (0x45, DMD0)
                                    }
                                }
                            }
                            Else
                            {
                                Or (Subtract (And (PMD0, 0x07), 0x02), 0x20, DMD0)
                            }

                            Return (PIB0)
                        }
                    }

                    Device (P_D1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Name (PIB1, Buffer (0x0E)
                            {
                                /* 0000 */    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF, 0x03, 
                                /* 0008 */    0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                            })
                            CreateByteField (PIB1, 0x01, PMD1)
                            CreateByteField (PIB1, 0x08, DMD1)
                            If (And (PRIT, 0x20))
                            {
                                If (LEqual (And (PRIT, 0x90), 0x80))
                                {
                                    Store (0x08, PMD1)
                                }
                                Else
                                {
                                    Add (And (PSIT, 0x03), ShiftRight (And (PSIT, 0x0C), 
                                        0x02), Local0)
                                    If (LEqual (0x05, Local0))
                                    {
                                        Store (0x0C, PMD1)
                                    }
                                    Else
                                    {
                                        If (LEqual (0x03, Local0))
                                        {
                                            Store (0x0B, PMD1)
                                        }
                                        Else
                                        {
                                            Store (0x0A, PMD1)
                                        }
                                    }
                                }
                            }
                            Else
                            {
                                Store (0x01, PMD1)
                            }

                            If (And (SYNC, 0x02))
                            {
                                Store (Or (SDT1, 0x40), DMD1)
                                If (And (ICR1, 0x02))
                                {
                                    If (And (ICR0, 0x02))
                                    {
                                        Add (DMD1, 0x02, DMD1)
                                    }

                                    If (And (ICR3, 0x02))
                                    {
                                        Store (0x45, DMD1)
                                    }
                                }
                            }
                            Else
                            {
                                Or (Subtract (And (PMD1, 0x07), 0x02), 0x20, DMD1)
                            }

                            Return (PIB1)
                        }
                    }
                }
            }

            Device (SATA)
            {
                Name (_ADR, 0x001F0002)
                OperationRegion (SACS, PCI_Config, 0x40, 0xC0)
                Field (SACS, DWordAcc, NoLock, Preserve)
                {
                    PRIT,   16, 
                    SECT,   16, 
                    PSIT,   4, 
                    SSIT,   4, 
                            Offset (0x08), 
                    SYNC,   4, 
                            Offset (0x0A), 
                    SDT0,   2, 
                        ,   2, 
                    SDT1,   2, 
                            Offset (0x0B), 
                    SDT2,   2, 
                        ,   2, 
                    SDT3,   2, 
                            Offset (0x14), 
                    ICR0,   4, 
                    ICR1,   4, 
                    ICR2,   4, 
                    ICR3,   4, 
                    ICR4,   4, 
                    ICR5,   4, 
                            Offset (0x50), 
                    MAPV,   2
                }
            }

            Device (SBUS)
            {
                Name (_ADR, 0x001F0003)
                OperationRegion (SMBP, PCI_Config, 0x40, 0xC0)
                Field (SMBP, DWordAcc, NoLock, Preserve)
                {
                        ,   2, 
                    I2CE,   1
                }

                OperationRegion (SMBI, SystemIO, 0x18E0, 0x10)
                Field (SMBI, ByteAcc, NoLock, Preserve)
                {
                    HSTS,   8, 
                            Offset (0x02), 
                    HCON,   8, 
                    HCOM,   8, 
                    TXSA,   8, 
                    DAT0,   8, 
                    DAT1,   8, 
                    HBDR,   8, 
                    PECR,   8, 
                    RXSA,   8, 
                    SDAT,   16
                }

                Method (SSXB, 2, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    Store (0x48, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SRXB, 1, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0xFFFF)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (0x44, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (DAT0)
                    }

                    Return (0xFFFF)
                }

                Method (SWRB, 3, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    Store (Arg2, DAT0)
                    Store (0x48, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SRDB, 2, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0xFFFF)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (Arg1, HCOM)
                    Store (0x48, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (DAT0)
                    }

                    Return (0xFFFF)
                }

                Method (SBLW, 4, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (Arg3, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    Store (SizeOf (Arg2), DAT0)
                    Store (0x00, Local1)
                    Store (DerefOf (Index (Arg2, 0x00)), HBDR)
                    Store (0x54, HCON)
                    While (LGreater (SizeOf (Arg2), Local1))
                    {
                        Store (0x0FA0, Local0)
                        While (LAnd (LNot (And (HSTS, 0x80)), Local0))
                        {
                            Decrement (Local0)
                            Stall (0x32)
                        }

                        If (LNot (Local0))
                        {
                            KILL ()
                            Return (0x00)
                        }

                        Store (0x80, HSTS)
                        Increment (Local1)
                        If (LGreater (SizeOf (Arg2), Local1))
                        {
                            Store (DerefOf (Index (Arg2, Local1)), HBDR)
                        }
                    }

                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SBLR, 3, Serialized)
                {
                    Name (TBUF, Buffer (0x0100) {})
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (Arg2, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (Arg1, HCOM)
                    Store (0x54, HCON)
                    Store (0x0FA0, Local0)
                    While (LAnd (LNot (And (HSTS, 0x80)), Local0))
                    {
                        Decrement (Local0)
                        Stall (0x32)
                    }

                    If (LNot (Local0))
                    {
                        KILL ()
                        Return (0x00)
                    }

                    Store (DAT0, Index (TBUF, 0x00))
                    Store (0x80, HSTS)
                    Store (0x01, Local1)
                    While (LLess (Local1, DerefOf (Index (TBUF, 0x00))))
                    {
                        Store (0x0FA0, Local0)
                        While (LAnd (LNot (And (HSTS, 0x80)), Local0))
                        {
                            Decrement (Local0)
                            Stall (0x32)
                        }

                        If (LNot (Local0))
                        {
                            KILL ()
                            Return (0x00)
                        }

                        Store (HBDR, Index (TBUF, Local1))
                        Store (0x80, HSTS)
                        Increment (Local1)
                    }

                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (TBUF)
                    }

                    Return (0x00)
                }

                Method (STRT, 0, Serialized)
                {
                    Store (0xC8, Local0)
                    While (Local0)
                    {
                        If (And (HSTS, 0x40))
                        {
                            Decrement (Local0)
                            Sleep (0x01)
                            If (LEqual (Local0, 0x00))
                            {
                                Return (0x01)
                            }
                        }
                        Else
                        {
                            Store (0x00, Local0)
                        }
                    }

                    Store (0x0FA0, Local0)
                    While (Local0)
                    {
                        If (And (HSTS, 0x01))
                        {
                            Decrement (Local0)
                            Stall (0x32)
                            If (LEqual (Local0, 0x00))
                            {
                                KILL ()
                            }
                        }
                        Else
                        {
                            Return (0x00)
                        }
                    }

                    Return (0x01)
                }

                Method (COMP, 0, Serialized)
                {
                    Store (0x0FA0, Local0)
                    While (Local0)
                    {
                        If (And (HSTS, 0x02))
                        {
                            Return (0x01)
                        }
                        Else
                        {
                            Decrement (Local0)
                            Stall (0x32)
                            If (LEqual (Local0, 0x00))
                            {
                                KILL ()
                            }
                        }
                    }

                    Return (0x00)
                }

                Method (KILL, 0, Serialized)
                {
                    Or (HCON, 0x02, HCON)
                    Or (HSTS, 0xFF, HSTS)
                }
            }
        }
    }
}
```Notice that "iasl -d" doesn't like ToUUID in _OSC method
I have fixed that.

Notice also the "Store (0x1770, Index (PBIF, 0x01))" in BAT0.UPBI method for LION,
that say that battery design capacity is 6000mWh,
whereas the real battery design capacity is 4200mWh.
I have to trace SBUS ref to discover the SmartBattery and then update the dsdt.

---

### Post by sergiom99 on 2009-08-30
Hi.
I've been using my custom DSDT for a couple of months now. (Thanks GTA!)
However, dmesg still returns some MSFT.

> $ dmesg |grep MSFT
[    0.000000] ACPI: DSDT 77F5C13A, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)


> $ sudo dmidecode 
# dmidecode 2.9                  
SMBIOS 2.4 present.              
19 structures occupying 726 bytes.
Table at 0x000F0B20.              

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information                   
        Vendor: Hewlett-Packard    
        Version: F.32              
        Release Date: 03/03/2009   
        Address: 0xE42D0           
        Runtime Size: 113968 bytes 
        ROM Size: 1024 kB          
        Characteristics:           
                ISA is supported   
                PCI is supported   
                PNP is supported   
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)      
                Printer services are supported (int 17h)     
                ACPI is supported                            
                USB legacy is supported                      
                AGP is supported                             
                Smart battery is supported                   
                Targeted content distribution is supported   

Handle 0x0001, DMI type 1, 27 bytes
System Information                 
        Manufacturer: Hewlett-Packard
        Product Name: HP Pavilion dv6500 Notebook PC    
        Version: Rev 1                                  
        Serial Number: CNF7453NL6                       
        UUID: 434E4637-3435-334E-4C36-001B24D4E59C      
        Wake-up Type: Power Switch                      
        SKU Number: GS687UA#ABA                         
        Family: 103C_5335KV                             

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information            
        Manufacturer: Quanta      
        Product Name: 30CF        
        Version: 85.26            
        Serial Number: None1      

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information                
        Manufacturer: Quanta       
        Type: Notebook             
        Lock: Not Present          
        Version: N/A               
        Serial Number: None        
        Asset Tag:                     
        Boot-up State: Safe            
        Power Supply State: Safe       
        Thermal State: Safe            
        Security Status: None          
        OEM Information: 0x00000004    

Handle 0x0004, DMI type 4, 35 bytes
Processor Information              
        Socket Designation: Socket S1
        Type: Central Processor      
        Family: Opteron              
        Manufacturer: AMD            
        ID: 81 0F 06 00 FF FB 8B 17  
        Signature: Family 15, Model 104, Stepping 1
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
                MMX (MMX technology supported)               
                FXSR (Fast floating-point save and restore)  
                SSE (Streaming SIMD extensions)              
                SSE2 (Streaming SIMD extensions 2)           
                HTT (Hyper-threading technology)             
        Version: AMD Turion(tm) 64 X2 Mobile TL58            
        Voltage: 1.6 V                                       
        External Clock: 200 MHz                              
        Max Speed: 1900 MHz                                  
        Current Speed: 1900 MHz                              
        Status: Populated, Enabled                           
        Upgrade: None                                        
        L1 Cache Handle: 0x0005                              
        L2 Cache Handle: 0x0006                              
        L3 Cache Handle: Not Provided                        
        Serial Number: Not Specified                         
        Asset Tag: Not Specified                             
        Part Number: Not Specified                           

Handle 0x0005, DMI type 7, 19 bytes
Cache Information                  
        Socket Designation: L1 Cache
        Configuration: Enabled, Not Socketed, Level 1
        Operational Mode: Write Back                 
        Location: Internal                           
        Installed Size: 64 KB                        
        Maximum Size: 64 KB                          
        Supported SRAM Types:                        
                Burst                                
                Pipeline Burst                       
                Asynchronous                         
        Installed SRAM Type: Asynchronous            
        Speed: Unknown                               
        Error Correction Type: Unknown               
        System Type: Unknown                         
        Associativity: Unknown                       

Handle 0x0006, DMI type 7, 19 bytes
Cache Information                  
        Socket Designation: L2 Cache
        Configuration: Enabled, Not Socketed, Level 2
        Operational Mode: Write Through              
        Location: Internal                           
        Installed Size: 1024 KB                      
        Maximum Size: 1024 KB                        
        Supported SRAM Types:                        
                Burst                                
                Pipeline Burst                       
                Synchronous                          
        Installed SRAM Type: Synchronous             
        Speed: Unknown                               
        Error Correction Type: Unknown               
        System Type: Unified                         
        Associativity: Unknown                       

Handle 0x0007, DMI type 9, 13 bytes
System Slot Information            
        Designation: PCI Express Slot 1
        Type: 64-bit PCI Express       
        Current Usage: Available       
        Length: Short                  
        ID: 0                          
        Characteristics:               
                5.0 V is provided      
                3.3 V is provided      

Handle 0x0008, DMI type 9, 13 bytes
System Slot Information            
        Designation: PCI Express Slot 2
        Type: 64-bit PCI Express       
        Current Usage: Available       
        Length: Short                  
        ID: 0                          
        Characteristics:               
                5.0 V is provided      
                3.3 V is provided      
                PME signal is supported
                Hot-plug devices are supported

Handle 0x0009, DMI type 10, 6 bytes
On Board Device Information        
        Type: Video                
        Status: Enabled            
        Description: 128           

Handle 0x000A, DMI type 11, 5 bytes
OEM Strings                        
        String 1: $HP$             
        String 2: LOC#ABA          
        String 3: ABS 72/73 81 82 83 84

Handle 0x000B, DMI type 16, 15 bytes
Physical Memory Array               
        Location: System Board Or Motherboard
        Use: System Memory                   
        Error Correction Type: None          
        Maximum Capacity: 2 GB               
        Error Information Handle: Not Provided
        Number Of Devices: 2                  

Handle 0x000C, DMI type 17, 27 bytes
Memory Device                       
        Array Handle: 0x000B        
        Error Information Handle: No Error
        Total Width: 64 bits              
        Data Width: 64 bits               
        Size: 1024 MB                     
        Form Factor: DIMM                 
        Set: 1                            
        Locator: DIMM 1                   
        Bank Locator: Bank 0,1            
        Type: DDR2                        
        Type Detail: Synchronous          
        Speed: 667 MHz (1.5 ns)           
        Manufacturer: Not Specified       
        Serial Number: Not Specified      
        Asset Tag: Not Specified          
        Part Number: Not Specified        

Handle 0x000D, DMI type 17, 27 bytes
Memory Device                       
        Array Handle: 0x000B        
        Error Information Handle: No Error
        Total Width: 64 bits              
        Data Width: 64 bits               
        Size: 1024 MB                     
        Form Factor: DIMM                 
        Set: 1                            
        Locator: DIMM 2                   
        Bank Locator: Bank 2,3            
        Type: DDR2                        
        Type Detail: Unknown              
        Speed: 667 MHz (1.5 ns)           
        Manufacturer: Not Specified       
        Serial Number: Not Specified      
        Asset Tag: Not Specified          
        Part Number: Not Specified        

Handle 0x000E, DMI type 19, 15 bytes
Memory Array Mapped Address         
        Starting Address: 0x00000000000
        Ending Address: 0x0007FFFFFFF  
        Range Size: 2 GB               
        Physical Array Handle: 0x000B  
        Partition Width: 0             

Handle 0x000F, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00000000000
        Ending Address: 0x0003FFFFFFF
        Range Size: 1 GB
        Physical Device Handle: 0x000C
        Memory Array Mapped Address Handle: 0x000E
        Partition Row Position: 2
        Interleave Position: 2
        Interleaved Data Depth: 2

Handle 0x0010, DMI type 20, 19 bytes
Memory Device Mapped Address
        Starting Address: 0x00040000000
        Ending Address: 0x0007FFFFFFF
        Range Size: 1 GB
        Physical Device Handle: 0x000D
        Memory Array Mapped Address Handle: 0x000E
        Partition Row Position: 2
        Interleave Position: 2
        Interleaved Data Depth: 2

Handle 0x0011, DMI type 32, 20 bytes
System Boot Information
        Status: <OUT OF SPEC>

Handle 0x0012, DMI type 127, 4 bytes
End Of Table


And my fixed DSDT.
HP Pavilion 6646us

---

### Post by 67GTA on 2009-08-31
[sergiom99]("http://ubuntuforums.org/member.php?u=458575"):

That is normal. The DSDT in your BIOS was compiled with MSFT. The one you are using was compiled with IASL. We are just bypassing the original. You should see this if it was replaced:

ACPI: Checking initramfs for custom DSDT                                                                                    
 ACPI: Found DSDT in DSDT.aml.                                                                                               
 ACPI: Override [DSDT-   MCP67], this is unsafe: tainting kernel                                                             
 ACPI: Table DSDT replaced by host OS                                                                                        
 ACPI: DSDT 00000000, 7CB3 (r1 NVIDIA    MCP67  6040000 INTL 20061109)

---

### Post by sergiom99 on 2009-08-31
yes thats right.
What about the changes in the new kernel and the lack of support for custom DSDT files?

---

### Post by 67GTA on 2009-09-01
From 2.6.30 and forward, the acpi_dsdt patch will no longer be used in any disto from what I've gathered. Linus and the main kernel devs don't want to use it anymore. They want to fix the bugs instead of "covering" them up. I just wish we would have had some notice. The patch can be found here: [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)  I have successfully built 2.6.30 on Jaunty with the patch using kernelcheck [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) This is the easiest way I've ever compiled a custom kernel. The only trouble is if you want the Debian/Ubuntu security updates, you will have to recompile them yourself. Hopefully everyone will submit their bugs, and they get fixed pretty quickly. I'm still waiting on word from Opensuse about custom DSDT support for 11.2.

---

### Post by 67GTA on 2009-09-01
Right after I posted this, one of the Opensuse kernel devs answered my bug report. I was thinking of switching to Opensuse when 11.2 was final anyway. Looks like they are still going to use it: [https://bugzilla.novell.com/show_bug.cgi?id=533555](https://bugzilla.novell.com/show_bug.cgi?id=533555)

---

### Post by sergiom99 on 2009-09-01
> **67GTA said:**
> From 2.6.30 and forward, the acpi_dsdt patch will no longer be used in any disto from what I've gathered. Linus and the main kernel devs don't want to use it anymore. They want to fix the bugs instead of "covering" them up. I just wish we would have had some notice. The patch can be found here: [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)  I have successfully built 2.6.30 on Jaunty with the patch using kernelcheck [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) This is the easiest way I've ever compiled a custom kernel. The only trouble is if you want the Debian/Ubuntu security updates, you will have to recompile them yourself. Hopefully everyone will submit their bugs, and they get fixed pretty quickly. I'm still waiting on word from Opensuse about custom DSDT support for 11.2.

You and I already filed bug reports in Launchpad. 
Is there anything else we could do to get it fixed upstream?

---

### Post by 67GTA on 2009-09-01
Maybe if we file a bug upstream with the main kernel devs it will help. I will look this weekend at filing one. It is a little more complex than launchpad.

---

### Post by sergiom99 on 2009-09-01
Post it here and I'll add my comments and data.

---

### Post by the_felis_leo on 2009-09-02
> **67GTA said:**
> Linus and the main kernel devs (...) want to fix the bugs instead of "covering" them up.


Humm, yes, I well understand.
ACtually I'm wondering utility of rebuilding a full functionnal DSDT.

DSDT is usefull if provided by manufacturer in order to run any OS.
But writing a DSDT just for Linux is just as writing an ordinary driver.


On the middle, we could use Linux as BIOS :p  (now  renamed CoreBoot)

---

### Post by 67GTA on 2009-09-19
I found a bug on bugzilla that details the only real remaining problem that I need a custom dsdt for. The thermal trip points are not seen, and the laptop runs hot. I know I fixed this for sergiom99 for sure, and many others. There was some code released that only tells the kernel to ignore the trip points, but the heat issue remains without a custom dsdt. The ubuntu devs aren't going to fix this. They will only wait for a fix from upstream.

[http://bugzilla.kernel.org/show_bug.cgi?id=10686](http://bugzilla.kernel.org/show_bug.cgi?id=10686)

9.10 still has this problem. I am testing Opensuse 11.2 milestone 7 at the moment, and it seems to be running cooler for some unknown reason. Also, I filed a bug, and  the Opensuse devs are trying to get the custom dsdt patch to work with 2.6.31 instead of just dropping it.

[https://bugzilla.novell.com/show_bug.cgi?id=533555](https://bugzilla.novell.com/show_bug.cgi?id=533555)

I am going to move to Opensuse when 11.2 goes final. I will file a bug for the heat problem also, to see if the Opensuse devs have any more insight into this problem. I will post a link to it when I get it done. I have teetered back and forth between Ubuntu and Suse for years. The fact that Suse is independently developed means they actually have to fix the majority of their code. Ubuntu is easier out of the box, but Opensuse is just more professional under the hood.

---

### Post by sergiom99 on 2009-10-30
Have you guys tried KK?

---

### Post by krantix on 2009-11-01
I will have to switch to SUSE too if devs do not care of such a dangerous problem (gpu runs at 120 degrees!)...

---

