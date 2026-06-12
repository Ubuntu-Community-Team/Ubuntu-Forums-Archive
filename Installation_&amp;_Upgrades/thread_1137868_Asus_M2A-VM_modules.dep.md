---
title: "Asus M2A-VM modules.dep"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by zaiboot on 2009-04-26
Hello I have downloaded Jaunty Jackalope 9.04, and everything went ok. Change the language to spanish, the keyboard layout to spanish latin america, and when it tries to open an X-Window in the Live CD, it shows me:
```

modprobe: FATAL: Could not load /lib/modules/2.6.2.28-11-generic/modules.dep: No such file or directory

[[IMG]http://img8.imageshack.us/img8/7167/dsc01056n.jpg[/IMG]](http://img8.imageshack.us/my.php?image=dsc01056n.jpg)

```
and then busy box.

So, this is my configuration:
```

-------------------------
  CPU-Z version 1.50
-------------------------

Processors Map
------------------------------------------------------------------------------------

Number of processors	1
Number of threads	2

Processor 0
    -- Core 0
        -- Thread 0
    -- Core 1
        -- Thread 0


Processors Information
------------------------------------------------------------------------------------

Processor 1 (ID = 0)
Number of cores		2 (max 2)
Number of threads	2 (max 2)
Name			AMD Athlon 64 X2 5600+
Codename		Brisbane
Specification		AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
Package			Socket AM2 (940)
CPUID			F.B.2
Extended CPUID		F.6B
Brand ID		4
Core Stepping		BH-G2
Technology		65 nm
Core Speed		2899.9 MHz (14.5 x 200.0 MHz)
HT Link speed		1000.0 MHz
Stock frequency		2900 MHz
Instructions sets	MMX (+), 3DNow! (+), SSE, SSE2, SSE3, x86-64
L1 Data cache		2 x 64 KBytes, 2-way set associative, 64-byte line size
L1 Instruction cache	2 x 64 KBytes, 2-way set associative, 64-byte line size
L2 cache		2 x 512 KBytes, 16-way set associative, 64-byte line size
FID/VID Control		yes
max FID			14.5x
max VID			1.400 V
Features		XD, VT
K8 Thermal sensor	yes
K8 Revision ID		6.0
Attached device		PCI device at bus 0, device 24, function 0
Attached device		PCI device at bus 0, device 24, function 1
Attached device		PCI device at bus 0, device 24, function 2
Attached device		PCI device at bus 0, device 24, function 3


Thread dumps
------------------------------------------------------------------------------------

CPU Thread 0
APIC ID			0
Topology		Processor ID 0, Core ID 0, Thread ID 0
Type			02002008h
Max CPUID level		00000001h
Max CPUID ext. level	80000018h

Function		eax		ebx		ecx		edx
0x00000000		0x00000001	0x68747541	0x444D4163	0x69746E65
0x00000001		0x00060FB2	0x00020800	0x00002001	0x178BFBFF
0x80000000		0x80000018	0x68747541	0x444D4163	0x69746E65
0x80000001		0x00060FB2	0x000008DF	0x0000011F	0xEBD3FBFF
0x80000002		0x20444D41	0x6C687441	0x74286E6F	0x3620296D
0x80000003		0x32582034	0x61754420	0x6F43206C	0x50206572
0x80000004		0x65636F72	0x726F7373	0x30363520	0x00002B30
0x80000005		0xFF08FF08	0xFF20FF20	0x40020140	0x40020140
0x80000006		0x00000000	0x42004200	0x02008140	0x00000000
0x80000007		0x00000000	0x00000000	0x00000000	0x0000007F
0x80000008		0x00003028	0x00000000	0x00000001	0x00000000
0x80000009		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000A		0x00000001	0x00000040	0x00000000	0x00000002
0x8000000B		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000C		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000D		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000E		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000F		0x00000000	0x00000000	0x00000000	0x00000000
0x80000010		0x00000000	0x00000000	0x00000000	0x00000000
0x80000011		0x00000000	0x00000000	0x00000000	0x00000000
0x80000012		0x00000000	0x00000000	0x00000000	0x00000000
0x80000013		0x00000000	0x00000000	0x00000000	0x00000000
0x80000014		0x00000000	0x00000000	0x00000000	0x00000000
0x80000015		0x00000000	0x00000000	0x00000000	0x00000000
0x80000016		0x00000000	0x00000000	0x00000000	0x00000000
0x80000017		0x00000000	0x00000000	0x00000000	0x00000000
0x80000018		0x00000000	0x00000000	0x00000000	0x00000000

Cache descriptor	Level 1 I	64 KB	1 thread(s)	
Cache descriptor	Level 1 D	64 KB	1 thread(s)	
Cache descriptor	Level 2 U	512 KB	1 thread(s)	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00900
MSR 0xC001001E		edx = 0x00000000	eax = 0x00000060
MSR 0xC0010015		edx = 0x00000000	eax = 0x02000040
MSR 0xC0010042		edx = 0x31061208	eax = 0x06150215
MSR 0xC0010041		edx = 0x00000001	eax = 0x00000815

CPU Thread 1
APIC ID			1
Topology		Processor ID 0, Core ID 1, Thread ID 0
Type			02002008h
Max CPUID level		00000001h
Max CPUID ext. level	80000018h

Function		eax		ebx		ecx		edx
0x00000000		0x00000001	0x68747541	0x444D4163	0x69746E65
0x00000001		0x00060FB2	0x01020800	0x00002001	0x178BFBFF
0x80000000		0x80000018	0x68747541	0x444D4163	0x69746E65
0x80000001		0x00060FB2	0x000008DF	0x0000011F	0xEBD3FBFF
0x80000002		0x20444D41	0x6C687441	0x74286E6F	0x3620296D
0x80000003		0x32582034	0x61754420	0x6F43206C	0x50206572
0x80000004		0x65636F72	0x726F7373	0x30363520	0x00002B30
0x80000005		0xFF08FF08	0xFF20FF20	0x40020140	0x40020140
0x80000006		0x00000000	0x42004200	0x02008140	0x00000000
0x80000007		0x00000000	0x00000000	0x00000000	0x0000007F
0x80000008		0x00003028	0x00000000	0x00000001	0x00000000
0x80000009		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000A		0x00000001	0x00000040	0x00000000	0x00000002
0x8000000B		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000C		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000D		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000E		0x00000000	0x00000000	0x00000000	0x00000000
0x8000000F		0x00000000	0x00000000	0x00000000	0x00000000
0x80000010		0x00000000	0x00000000	0x00000000	0x00000000
0x80000011		0x00000000	0x00000000	0x00000000	0x00000000
0x80000012		0x00000000	0x00000000	0x00000000	0x00000000
0x80000013		0x00000000	0x00000000	0x00000000	0x00000000
0x80000014		0x00000000	0x00000000	0x00000000	0x00000000
0x80000015		0x00000000	0x00000000	0x00000000	0x00000000
0x80000016		0x00000000	0x00000000	0x00000000	0x00000000
0x80000017		0x00000000	0x00000000	0x00000000	0x00000000
0x80000018		0x00000000	0x00000000	0x00000000	0x00000000

Cache descriptor	Level 1 I	64 KB	1 thread(s)	
Cache descriptor	Level 1 D	64 KB	1 thread(s)	
Cache descriptor	Level 2 U	512 KB	1 thread(s)	

MSR 0x0000001B		edx = 0x00000000	eax = 0xFEE00800
MSR 0xC001001E		edx = 0x00000000	eax = 0x00000060
MSR 0xC0010015		edx = 0x00000000	eax = 0x02000040
MSR 0xC0010042		edx = 0x31061208	eax = 0x06150215
MSR 0xC0010041		edx = 0x00000001	eax = 0x00000815


Chipset
------------------------------------------------------------------------------

Northbridge		ATI RS690/RS690M rev. 00
Southbridge		ATI SB600 rev. 00
Memory Type		DDR2
Memory Size		4096 MBytes
Channels		Dual
Memory Frequency	362.5 MHz (CPU/8)
CAS#			6.0
RAS# to CAS#		6
RAS# Precharge		6
Cycle Time (tRAS)	18
Bank Cycle Time (tRC)	25
Command Rate		2T


Memory SPD
------------------------------------------------------------------------------

DIMM #1

General
Memory type		DDR2
Module format		Regular UDIMM
Manufacturer (ID)	Kingston (7F98000000000000)
Size			1024 MBytes
Max bandwidth		PC2-6400 (400 MHz)
Part number		99U5316-028.A00LF
Serial number		680D353A
Manufacturing date	Week 22/Year 08

Attributes
Number of banks		2
Data width		64 bits
Correction		None
Nominal Voltage		1.80 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		266	333	400	
CAS#			4.0	5.0	6.0	
RAS# to CAS# delay	4	5	6	
RAS# Precharge		4	5	6	
TRAS			12	15	18	
TRC			16	20	24	

DIMM #2

General
Memory type		DDR2
Module format		Regular UDIMM
Manufacturer (ID)	Kingston (7F98000000000000)
Size			1024 MBytes
Max bandwidth		PC2-6400 (400 MHz)
Part number		99U5316-028.A00LF
Serial number		660ED704
Manufacturing date	Week 22/Year 08

Attributes
Number of banks		2
Data width		64 bits
Correction		None
Nominal Voltage		1.80 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		266	333	400	
CAS#			4.0	5.0	6.0	
RAS# to CAS# delay	4	5	6	
RAS# Precharge		4	5	6	
TRAS			12	15	18	
TRC			16	20	24	

DIMM #3

General
Memory type		DDR2
Module format		Regular UDIMM
Manufacturer (ID)	Kingston (7F98000000000000)
Size			1024 MBytes
Max bandwidth		PC2-6400 (400 MHz)
Part number		99U5316-028.A00LF
Serial number		660ED604
Manufacturing date	Week 22/Year 08

Attributes
Number of banks		2
Data width		64 bits
Correction		None
Nominal Voltage		1.80 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		266	333	400	
CAS#			4.0	5.0	6.0	
RAS# to CAS# delay	4	5	6	
RAS# Precharge		4	5	6	
TRAS			12	15	18	
TRC			16	20	24	

DIMM #4

General
Memory type		DDR2
Module format		Regular UDIMM
Manufacturer (ID)	Kingston (7F98000000000000)
Size			1024 MBytes
Max bandwidth		PC2-6400 (400 MHz)
Part number		99U5316-028.A00LF
Serial number		660ED804
Manufacturing date	Week 22/Year 08

Attributes
Number of banks		2
Data width		64 bits
Correction		None
Nominal Voltage		1.80 Volts
EPP			no
XMP			no

Timings table
Frequency (MHz)		266	333	400	
CAS#			4.0	5.0	6.0	
RAS# to CAS# delay	4	5	6	
RAS# Precharge		4	5	6	
TRAS			12	15	18	
TRC			16	20	24	

Dump Module #1
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
10   0C 04 70 01 02 00 03 30 45 3D 50 3C 1E 3C 2D 80 
20   17 25 05 12 3C 1E 1E 00 00 3C 69 80 14 1E 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 3C 
40   7F 98 00 00 00 00 00 00 05 39 39 55 35 33 31 36 
50   2D 30 32 38 2E 41 30 30 4C 46 00 00 00 08 1C 68 
60   0D 35 3A 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F0   39 39 55 35 33 31 36 2D 30 32 38 2E 41 30 30 4C 


Dump Module #2
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
10   0C 04 70 01 02 00 03 30 45 3D 50 3C 1E 3C 2D 80 
20   17 25 05 12 3C 1E 1E 00 00 3C 69 80 14 1E 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 3C 
40   7F 98 00 00 00 00 00 00 05 39 39 55 35 33 31 36 
50   2D 30 32 38 2E 41 30 30 4C 46 00 00 00 08 1C 66 
60   0E D7 04 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F0   39 39 55 35 33 31 36 2D 30 32 38 2E 41 30 30 4C 


Dump Module #3
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
10   0C 04 70 01 02 00 03 30 45 3D 50 3C 1E 3C 2D 80 
20   17 25 05 12 3C 1E 1E 00 00 3C 69 80 14 1E 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 3C 
40   7F 98 00 00 00 00 00 00 05 39 39 55 35 33 31 36 
50   2D 30 32 38 2E 41 30 30 4C 46 00 00 00 08 1C 66 
60   0E D6 04 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F0   39 39 55 35 33 31 36 2D 30 32 38 2E 41 30 30 4C 


Dump Module #4
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   80 08 08 0E 0A 61 40 00 05 25 40 00 82 08 00 00 
10   0C 04 70 01 02 00 03 30 45 3D 50 3C 1E 3C 2D 80 
20   17 25 05 12 3C 1E 1E 00 00 3C 69 80 14 1E 00 00 
30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 3C 
40   7F 98 00 00 00 00 00 00 05 39 39 55 35 33 31 36 
50   2D 30 32 38 2E 41 30 30 4C 46 00 00 00 08 1C 66 
60   0E D8 04 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
F0   39 39 55 35 33 31 36 2D 30 32 38 2E 41 30 30 4C 


Monitoring
------------------------------------------------------------------------------

Mainboard Model		M2A-VM (0x190 - 0x5345A0)

LPCIO
-----------------------------------------------------
Vendor			ITE
Model			IT8716
Vendor ID		0x90
Chip ID			0x8716
Revision ID		0x1
Config Mode I/O address	0x2E

Dump config mode register space, LDN = 0x4
      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   00 00 00 00 00 00 00 04 00 00 00 00 00 00 00 00 
10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
20   87 16 01 00 00 40 0E 00 42 80 00 00 1F 00 00 00 
30   01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
60   02 28 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
70   00 02 00 00 04 04 00 00 00 00 00 00 00 00 00 00 


Hardware monitor
-----------------------------------------------------

ITE IT87 hardware monitor

Voltage sensor 0	1.36 Volts [0x55] (CPU VCORE)
Voltage sensor 1	3.33 Volts [0xD0] (VIN1)
Voltage sensor 3	4.97 Volts [0xB9] (+5V)
Voltage sensor 4	12.10 Volts [0xBD] (+12V)
Voltage sensor 7	5.05 Volts [0xBC] (+5V VCCH)
Voltage sensor 8	3.20 Volts [0xC8] (VBAT)
Temperature sensor 0	43°C (109°F) [0x2B] (TMPIN0)
Temperature sensor 1	39°C (102°F) [0x27] (TMPIN1)
Temperature sensor 2	25°C (76°F) [0x19] (TMPIN2)
Fan sensor 0		3392 RPM [0xC7] (FANIN0)

Dump hardware monitor
LPC Register space, base address = 0x0228

      0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
00   11 0A FF 07 00 00 00 00 00 80 40 09 17 C7 FF FF 
10   D0 D0 BF 30 D7 7F 80 82 00 FF FF 00 00 FF FF FF 
20   55 D0 00 B9 BD 00 00 BC C8 2B 27 19 CA 80 80 80 
30   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
40   FF FF FF FF FF FF 00 0D 2D FF FF FF FF FF FF FF 
50   FF 31 7F 7F 7F 50 F3 00 90 00 39 12 00 00 00 00 
60   00 32 7F 3C A0 00 FF FF 00 32 7F 3C A0 00 FF FF 
70   7F 7F 7F 00 00 00 FF FF FF FF FF FF FF FF FF FF 
80   FF FF 00 00 FD FF FF FF 00 00 FF C0 02 00 99 99 
90   7F 7F 7F 00 00 7F FF FF 7F 7F 7F 00 00 7F FF FF 
A0   00 00 00 00 00 00 00 FF FF FF FF FF FF FF FF FF 
B0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
C0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
D0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
E0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 
F0   FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF 



Hardware monitor
-----------------------------------------------------

AMD Athlon 64 X2 5600+ hardware monitor

Temperature sensor 0	20°C (67°F) [0x112] (Core #0)
Temperature sensor 1	14°C (57°F) [0xFC] (Core #1)

Dump hardware monitor



PCI Device List
------------------------------------------------------------------------------

Host Bridge
bus 0 (0x00), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x7910
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x40
	Header			0x00
PCI header
	Subvendor ID		0x1043
	Subsystem ID		0x826D
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	HyperTransport Capability
		Offset			C4h
		Revision		1.05
		Interface type		Slave/Primary
		Link 0 width (in/out)	16 bits/16 bits
		Link 0 frequency	1000MHz
		Link 1 width (in/out)	8 bits/8 bits
		Link 1 frequency	200MHz
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 10 79 06 00 20 22 00 00 00 06 00 40 00 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 6D 82 
	 30   00 00 00 00 C4 00 00 00 00 00 00 00 00 00 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 42 20 05 00 
	 50   43 10 6D 82 FF 00 00 00 00 00 00 00 00 00 00 00 
	 60   5F 00 00 00 00 00 00 00 00 02 20 00 98 F8 01 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   40 43 00 00 95 00 00 03 20 01 10 00 03 26 00 00 
	 90   00 00 00 D8 40 C4 40 E4 00 D0 00 00 01 00 00 00 
	 A0   00 00 00 00 00 00 00 00 07 01 00 00 49 01 10 07 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 08 00 80 01 60 00 11 11 D0 00 00 00 
	 D0   25 06 65 00 02 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 90 00 00 00 F7 FF FE FF 
	 F0   00 00 00 00 00 80 80 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 1 (0x01), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x7912
	Revision ID		0x00
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x63
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x01
	Int. Line		0xFF
	Int. Pin		0x00
Capabilities
	HyperTransport Capability
		Offset			44h
		Interface type		MSI Mapping
	Subsystem Vendor Capability
		Offset		B0h
		Subsystem ID	0x7912
		Sub. Vendor ID	0x1002
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 12 79 07 00 30 02 00 00 04 06 00 63 01 00 
	 10   00 00 00 00 00 00 00 00 00 01 01 44 C1 C1 20 22 
	 20   A0 FD B0 FD 01 F0 F1 F7 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 44 00 00 00 00 00 00 00 FF 00 0C 00 
	 40   00 00 00 00 08 B0 03 A8 00 00 00 00 02 10 12 79 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   0D 00 00 00 02 10 12 79 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 7 (0x07), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x7917
	Revision ID		0x00
	PI			0x00
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x08
	Latency			0x00
	Header			0x01
PCI header
	Primary bus		0x00
	Secondary bus		0x02
	Int. Line		0xFF
	Int. Pin		0x00
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.2
	PCI Express Capability
		Offset		58h
		Device type	Root Port of PCI-E Root Complex
		Port		4
		Version		1.0
		Physical slot	Integrated device
		Link width	1x (max 1x)
	Message Signalled Interrupts Capability
		Offset		80h
	Subsystem Vendor Capability
		Offset		B0h
		Subsystem ID	0x826D
		Sub. Vendor ID	0x1043
	HyperTransport Capability
		Offset			B8h
		Interface type		MSI Mapping
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 17 79 07 00 10 00 00 00 04 06 08 00 01 00 
	 10   00 00 00 00 00 00 00 00 00 02 02 00 D1 D1 00 00 
	 20   F0 FD F0 FD C1 FD C1 FD 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 50 00 00 00 00 00 00 00 FF 00 04 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   01 58 03 C8 00 00 00 00 10 80 41 00 20 80 00 00 
	 60   10 08 00 00 11 0C 10 04 00 00 11 30 00 00 00 00 
	 70   C0 03 48 00 00 00 01 00 00 00 00 00 00 00 00 00 
	 80   05 B0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   0D B8 00 00 43 10 6D 82 08 00 03 A8 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   A5 00 00 00 10 0F 0B 0A 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


IDE Controller
bus 0 (0x00), device 18 (0x12), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x4380
	Revision ID		0x00
	PI			0x8F
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (port)	0x0000FC00
	Address 1 (port)	0x0000F800
	Address 2 (port)	0x0000F400
	Address 3 (port)	0x0000F000
	Address 4 (port)	0x0000EC00
	Address 5 (memory)	0xFE02F000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x16
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		60h
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 80 43 07 00 30 02 00 8F 01 01 00 40 00 00 
	 10   01 FC 00 00 01 F8 00 00 01 F4 00 00 01 F0 00 00 
	 20   01 EC 00 00 00 F0 02 FE 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 60 00 00 00 00 00 00 00 16 01 00 00 
	 40   10 00 80 02 01 00 10 00 01 00 00 00 00 00 00 00 
	 50   05 00 84 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   01 00 22 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   12 00 10 00 0F 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 06 00 00 2C D5 00 B4 00 D5 00 B4 00 
	 90   D5 00 B4 00 D5 00 B4 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 78 00 00 00 00 00 00 00 78 00 00 
	 B0   00 00 00 00 00 78 00 00 00 00 00 00 00 78 00 00 
	 C0   00 20 00 00 80 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x4387
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x80
PCI header
	Address 0 (memory)	0xFE02E000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x10
	Int. Pin		0x01
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 87 43 07 00 A0 02 00 10 03 0C 08 40 80 00 
	 10   00 E0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 10 01 00 00 
	 40   80 1F 00 00 0A 84 B7 18 07 35 00 00 00 00 00 00 
	 50   00 8C 00 00 00 00 00 00 10 32 54 76 98 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 FF 00 00 80 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 1 (0x01)
Common header
	Vendor ID		0x1002
	Model ID		0x4388
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE02D000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x11
	Int. Pin		0x02
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 88 43 07 00 A0 02 00 10 03 0C 08 40 00 00 
	 10   00 D0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 11 02 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 2 (0x02)
Common header
	Vendor ID		0x1002
	Model ID		0x4389
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE02C000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x12
	Int. Pin		0x03
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 89 43 07 00 A0 02 00 10 03 0C 08 40 00 00 
	 10   00 C0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 12 03 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 3 (0x03)
Common header
	Vendor ID		0x1002
	Model ID		0x438A
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE02B000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x11
	Int. Pin		0x02
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 8A 43 07 00 A0 02 00 10 03 0C 08 40 00 00 
	 10   00 B0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 11 02 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB Controller (OHCI)
bus 0 (0x00), device 19 (0x13), function 4 (0x04)
Common header
	Vendor ID		0x1002
	Model ID		0x438B
	Revision ID		0x00
	PI			0x10
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE02A000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x12
	Int. Pin		0x03
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 8B 43 07 00 A0 02 00 10 03 0C 08 40 00 00 
	 10   00 A0 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 12 03 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


USB 2.0 Controller (EHCI)
bus 0 (0x00), device 19 (0x13), function 5 (0x05)
Common header
	Vendor ID		0x1002
	Model ID		0x4386
	Revision ID		0x00
	PI			0x20
	SubClass		0x03
	BaseClass		0x0C
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE029000
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x13
	Int. Pin		0x04
Capabilities
	Power Management Capability
		Offset		C0h
		Version		1.1
	Debug Port Capability
		Offset		E4h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 86 43 07 00 B0 02 00 20 03 0C 08 40 00 00 
	 10   00 90 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 C0 00 00 00 00 00 00 00 13 04 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 50   40 00 0E 00 01 00 00 00 00 00 00 00 00 00 00 00 
	 60   20 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   01 00 00 00 00 00 00 C0 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   01 E4 02 7E 00 00 40 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 0A 00 E0 20 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


SMBus Controller
bus 0 (0x00), device 20 (0x14), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x4385
	Revision ID		0x14
	PI			0x00
	SubClass		0x05
	BaseClass		0x0C
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Address 0 (port)	0x00000B00
	Address 1 (port)	0xFFFFFFFC
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	HyperTransport Capability
		Offset			B0h
		Interface type		MSI Mapping
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 85 43 03 04 30 02 14 00 05 0C 00 00 80 00 
	 10   01 0B 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 B0 00 00 00 00 00 00 00 00 00 00 00 
	 40   D4 39 00 04 00 00 00 00 0F FF 00 00 00 00 00 00 
	 50   F0 01 F0 08 F0 0F F0 07 11 0B F0 0F 00 00 00 00 
	 60   01 00 07 00 BF FF 9E 8F 3F 90 00 00 20 00 00 00 
	 70   00 01 00 00 08 00 C0 FE FF 6E 00 00 00 00 F0 0F 
	 80   F0 0A F0 0F 00 00 00 00 00 00 00 00 8C 00 00 80 
	 90   01 0B 00 00 F9 CE FF 00 00 00 00 00 00 00 00 00 
	 A0   00 00 FF FF FF FF F0 08 02 FD 02 02 16 7B 20 18 
	 B0   08 00 02 A8 00 00 00 00 00 00 00 00 F0 0F 08 1A 
	 C0   FF FF FF FF 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   D8 0C 00 00 00 00 44 00 00 00 00 00 AA 00 10 01 


IDE Controller
bus 0 (0x00), device 20 (0x14), function 1 (0x01)
Common header
	Vendor ID		0x1002
	Model ID		0x438C
	Revision ID		0x00
	PI			0x8A
	SubClass		0x01
	BaseClass		0x01
	Cache Line		0x00
	Latency			0x40
	Header			0x00
PCI header
	Address 4 (port)	0x0000E400
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0xFF
	Int. Pin		0x01
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 8C 43 05 00 20 02 00 8A 01 01 00 40 00 00 
	 10   01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 
	 20   01 E4 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 FF 01 00 00 
	 40   20 99 00 00 FF FF 00 00 00 00 40 00 00 00 00 00 
	 50   00 00 00 00 02 00 40 00 00 00 00 00 00 00 00 00 
	 60   00 00 40 00 10 2C 01 07 01 00 00 00 FF FF 0F 00 
	 70   05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Multimedia device
bus 0 (0x00), device 20 (0x14), function 2 (0x02)
Common header
	Vendor ID		0x1002
	Model ID		0x4383
	Revision ID		0x00
	PI			0x00
	SubClass		0x03
	BaseClass		0x04
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xFE020000
	Subvendor ID		0x1043
	Subsystem ID		0x8249
	Int. Line		0x10
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.1
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 83 43 06 00 10 04 00 00 03 04 08 40 00 00 
	 10   04 00 02 FE 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 49 82 
	 30   00 00 00 00 50 00 00 00 00 00 00 00 10 01 00 00 
	 40   00 00 00 00 01 00 00 00 00 00 00 00 01 00 00 00 
	 50   01 00 42 C8 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   05 00 80 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to ISA Bridge
bus 0 (0x00), device 20 (0x14), function 3 (0x03)
Common header
	Vendor ID		0x1002
	Model ID		0x438D
	Revision ID		0x00
	PI			0x00
	SubClass		0x01
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x1043
	Subsystem ID		0x81EF
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 8D 43 0F 00 20 02 00 00 01 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 EF 81 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 40   04 00 00 00 FF FF FF FF 3F FF 42 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 20 02 00 00 0E 00 0F 00 B0 FF FF FF 
	 70   67 45 23 01 00 00 00 00 00 00 00 00 05 00 00 00 
	 80   08 00 03 A8 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


PCI to PCI Bridge
bus 0 (0x00), device 20 (0x14), function 4 (0x04)
Common header
	Vendor ID		0x1002
	Model ID		0x4384
	Revision ID		0x00
	PI			0x01
	SubClass		0x04
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x40
	Header			0x81
PCI header
	Primary bus		0x00
	Secondary bus		0x03
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 84 43 27 00 A0 02 00 01 04 06 00 40 81 00 
	 10   00 00 00 00 00 00 00 00 00 03 03 40 F0 00 80 22 
	 20   F0 FF 00 00 F0 FF 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 04 00 
	 40   26 00 3C FF 00 00 00 00 0C 01 3F D1 00 00 00 00 
	 50   01 00 00 00 08 00 03 A8 00 00 00 00 85 00 FF FF 
	 60   CA 0E 17 00 BA 18 10 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 01 00 02 06 
	 E0   00 00 80 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Host Bridge
bus 0 (0x00), device 24 (0x18), function 0 (0x00)
Common header
	Vendor ID		0x1022
	Model ID		0x1100
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	HyperTransport Capability
		Offset			80h
		Revision		1.02
		Interface type		Host/Secondary
		Device number	0
		Link 0 width (in/out)	16 bits/16 bits
		Link 0 frequency	1000MHz
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   22 10 00 11 00 00 10 00 00 00 00 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 80 00 00 00 00 00 00 00 00 00 00 00 
	 40   01 01 01 00 01 01 01 00 01 01 01 00 01 01 01 00 
	 50   01 01 01 00 01 01 01 00 01 01 01 00 01 01 01 00 
	 60   00 00 01 00 E4 00 00 00 20 C8 2E 0F 0C 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   08 00 01 21 20 00 11 11 22 06 75 80 02 00 00 00 
	 90   78 01 70 01 00 00 03 00 07 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Host Bridge
bus 0 (0x00), device 24 (0x18), function 1 (0x01)
Common header
	Vendor ID		0x1022
	Model ID		0x1101
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   22 10 01 11 00 00 00 00 00 00 00 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 40   03 00 00 00 00 00 1F 01 00 00 00 00 01 00 00 00 
	 50   00 00 00 00 02 00 00 00 00 00 00 00 03 00 00 00 
	 60   00 00 00 00 04 00 00 00 00 00 00 00 05 00 00 00 
	 70   00 00 00 00 06 00 00 00 00 00 00 00 07 00 00 00 
	 80   03 0A 00 00 00 0B 00 00 03 00 F0 00 80 FF F7 00 
	 90   03 00 E0 00 00 FF DF 00 00 00 21 05 B0 02 F4 FD 
	 A0   04 56 18 28 A4 EE 32 FB 03 00 F8 00 00 02 FE 00 
	 B0   03 00 E0 00 80 3F E0 00 00 00 00 00 00 00 00 00 
	 C0   13 B0 00 00 00 F0 00 00 30 E0 C3 01 00 F0 6F 01 
	 D0   10 50 28 01 30 30 8C 01 30 30 EF 01 33 10 03 01 
	 E0   03 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   01 20 00 E0 00 00 00 00 00 00 00 00 00 00 00 00 


Host Bridge
bus 0 (0x00), device 24 (0x18), function 2 (0x02)
Common header
	Vendor ID		0x1022
	Model ID		0x1102
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   22 10 02 11 00 00 00 00 00 00 00 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 40   01 00 00 00 01 01 00 00 01 02 00 00 01 03 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   E0 3C F8 00 E0 3C F8 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 46 00 00 00 00 00 00 00 
	 80   22 00 00 00 00 00 00 00 35 F3 7E 0C 20 13 92 00 
	 90   30 0C 01 00 5B 80 10 77 24 00 00 80 20 25 20 00 
	 A0   EF 02 00 0C 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   AC 5D 66 32 26 00 00 00 EE 5F E5 0F E1 12 86 1E 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   4D 83 91 19 10 C2 50 64 37 03 90 EF E3 07 6C 6C 
	 E0   69 86 19 CD 38 06 64 A0 6D 95 21 B3 C9 06 04 4D 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Host Bridge
bus 0 (0x00), device 24 (0x18), function 3 (0x03)
Common header
	Vendor ID		0x1022
	Model ID		0x1103
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x06
	Cache Line		0x00
	Latency			0x00
	Header			0x80
PCI header
	Subvendor ID		0x0000
	Subsystem ID		0x0000
	Int. Line		0x00
	Int. Pin		0x00
Capabilities
	Secure Device Capability
		Offset		F0h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   22 10 03 11 00 00 10 00 00 00 00 06 00 00 80 00 
	 10   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 30   00 00 00 00 F0 00 00 00 00 00 00 00 00 00 00 00 
	 40   FF 3B 04 00 40 00 10 0A 00 00 00 00 00 00 00 00 
	 50   00 00 00 00 00 00 00 00 00 00 00 00 00 CD 2F FD 
	 60   4A 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   11 01 32 51 21 40 30 50 00 2A 00 08 1B 21 00 00 
	 80   00 00 07 23 13 21 13 21 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 81 12 00 00 70 BA 00 A0 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 01 A7 0D 00 00 00 60 0C 25 26 26 00 
	 E0   00 00 00 00 3E A0 41 00 19 17 00 00 00 00 00 00 
	 F0   0F 00 10 00 00 00 00 00 00 00 00 00 B2 0F 06 00 


VGA Controller
bus 1 (0x01), device 5 (0x05), function 0 (0x00)
Common header
	Vendor ID		0x1002
	Model ID		0x791E
	Revision ID		0x00
	PI			0x00
	SubClass		0x00
	BaseClass		0x03
	Cache Line		0x08
	Latency			0x40
	Header			0x00
PCI header
	Address 0 (memory)	0xF0000000
	Address 2 (memory)	0xFDBF0000
	Address 4 (port)	0x0000CC00
	Address 5 (memory)	0xFDA00000
	Subvendor ID		0x1043
	Subsystem ID		0x826D
	Int. Line		0x12
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		50h
		Version		1.1
	Message Signalled Interrupts Capability
		Offset		80h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   02 10 1E 79 07 00 10 00 00 00 00 03 08 40 00 00 
	 10   0C 00 00 F0 00 00 00 00 04 00 BF FD 00 00 00 00 
	 20   01 CC 00 00 00 00 A0 FD 00 00 00 00 43 10 6D 82 
	 30   00 00 00 00 50 00 00 00 00 00 00 00 12 01 00 00 
	 40   00 00 00 00 00 00 00 00 00 00 00 00 43 10 6D 82 
	 50   01 80 02 06 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 70   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   05 00 80 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 90   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 A0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 B0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


Ethernet Controller
bus 2 (0x02), device 0 (0x00), function 0 (0x00)
Common header
	Vendor ID		0x10EC
	Model ID		0x8168
	Revision ID		0x01
	PI			0x00
	SubClass		0x00
	BaseClass		0x02
	Cache Line		0x08
	Latency			0x00
	Header			0x00
PCI header
	Address 0 (port)	0x0000DC00
	Address 2 (memory)	0xFDFFF000
	Subvendor ID		0x1043
	Subsystem ID		0x81AA
	Int. Line		0x13
	Int. Pin		0x01
Capabilities
	Power Management Capability
		Offset		40h
		Version		1.1
	Virtual Product Data Capability
		Offset		48h
	Message Signalled Interrupts Capability
		Offset		50h
	PCI Express Capability
		Offset		60h
		Device type	PCI-E Endpoint Device
		Port		0
		Version		1.0
		Link width	1x (max 1x)
	Vendor Dependant Capability
		Offset		84h
Dump
	       0  1  2  3  4  5  6  7  8  9  A  B  C  D  E  F 
	 00   EC 10 68 81 07 00 10 00 01 00 00 02 08 00 00 00 
	 10   01 DC 00 00 00 00 00 00 04 F0 FF FD 00 00 00 00 
	 20   00 00 00 00 00 00 00 00 00 00 00 00 43 10 AA 81 
	 30   00 00 00 00 40 00 00 00 00 00 00 00 13 01 00 00 
	 40   01 48 C2 F7 00 00 00 00 03 50 00 00 00 00 00 00 
	 50   05 60 82 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 60   10 84 01 00 23 7F 00 00 10 58 10 00 11 F4 03 00 
	 70   00 00 11 10 00 00 00 00 00 00 00 00 00 00 00 00 
	 80   00 00 00 00 09 00 4C 01 01 1C 02 00 FB FF FF 11 
	 90   08 30 00 00 DE D5 05 00 5D A1 04 00 D7 03 00 00 
	 A0   02 28 FF 01 00 00 00 00 00 08 00 00 03 00 03 00 
	 B0   00 40 00 00 FF 3F FF 3F FF FF 00 00 00 00 00 00 
	 C0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 D0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 E0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
	 F0   00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 


DMI
------------------------------------------------------------------------------

DMI BIOS
--------
	vendor		Phoenix Technologies, LTD
	version		ASUS M2A-VM ACPI BIOS Revision 1604
	date		12/19/2007


DMI System Information
----------------------
	manufacturer	System manufacturer
	product		System Product Name
	version		System Version
	serial		System Serial Number
	UUID		40DA6FB7-4F08DD11-AE51001F-C6B03D1B


DMI Baseboard
-------------
	vendor		ASUSTeK Computer INC.
	model		M2A-VM
	revision	1.XX
	serial		123456789000


DMI System Enclosure
--------------------
	manufacturer	Chassis Manufacture
	chassis type	Desktop
	chassis serial	EVAL


DMI Processor
-------------
	manufacturer	AMD
	model		AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
	clock speed	2900.0 MHz
	FSB speed	200.0 MHz
	multiplier	14.5x


DMI Memory Controller
---------------------
	correction	64-bit ECC
	Max module size	2048 MBytes


DMI Memory Module
-----------------
	designation	A0
	size		1024 MBytes (double bank)


DMI Memory Module
-----------------
	designation	A1
	size		1024 MBytes (double bank)


DMI Memory Module
-----------------
	designation	A2
	size		1024 MBytes (double bank)


DMI Memory Module
-----------------
	designation	A3
	size		1024 MBytes (double bank)


DMI Port Connector
------------------
	designation	PRI_IDE (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	FLOPPY (internal)
	port type	8251 FIFO Compatible
	connector	On Board Floppy


DMI Port Connector
------------------
	designation	COM1 (internal)
	port type	Serial Port 16450
	connector	9 Pin Dual Inline (pin 10 cut)
	connector	DB-9 male


DMI Port Connector
------------------
	designation	LPT1 (internal)
	port type	Parallel Port ECP/EPP
	connector	DB-25 female
	connector	DB-25 female


DMI Port Connector
------------------
	designation	PS/2 Keyboard (internal)
	port type	Keyboard Port
	connector	PS/2
	connector	PS/2


DMI Port Connector
------------------
	designation	PS/2 Mouse (internal)
	port type	Mouse Port
	connector	PS/2
	connector	PS/2


DMI Port Connector
------------------
	designation	USB1 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB2 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB3 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB4 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB5 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB6 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB7 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB8 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB9 (external)
	port type	USB


DMI Port Connector
------------------
	designation	USB10 (external)
	port type	USB


DMI Port Connector
------------------
	designation	VIDEO (external)
	port type	Video Port
	connector	DB-15 female


DMI Port Connector
------------------
	designation	LINE_IN (internal)
	designation	LINE_IN (external)
	port type	Audio Port


DMI Port Connector
------------------
	designation	LINE_OUT (internal)
	designation	LINE_OUT (external)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	MIC_IN (internal)
	designation	MIC_IN (external)
	port type	Audio Port
	connector	Mini Jack (headphones)


DMI Port Connector
------------------
	designation	CD_IN (internal)
	designation	CD_IN (external)
	port type	Audio Port
	connector	On Board Sound Input From CD-ROM


DMI Port Connector
------------------
	designation	SPDIF_OUT (internal)
	designation	SPDIF_OUT (external)
	port type	Audio Port


DMI Port Connector
------------------
	designation	FP_AUDIO (internal)
	designation	FP_AUDIO (external)
	port type	Audio Port


DMI Port Connector
------------------
	designation	LAN_1 (external)
	port type	Network Port
	connector	RJ-45


DMI Port Connector
------------------
	designation	SATA1 (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	SATA2 (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	SATA3 (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	SATA4 (internal)
	connector	On Board IDE


DMI Port Connector
------------------
	designation	CPU_FAN1 (internal)


DMI Extension Slot
------------------
	designation	PCI1
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCI2
	type		PCI
	width		32 bits
	populated	no


DMI Extension Slot
------------------
	designation	PCIEX16
	type		A5
	populated	no


DMI Extension Slot
------------------
	designation	PCIEX1_1
	type		A5
	populated	no


DMI Physical Memory Array
-------------------------
	location	Motherboard
	usage		System Memory
	correction	None
	max capacity	8192 MBytes
	max# of devices	4


DMI Memory Device
-----------------
	designation	A0
	format		DIMM
	type		unknown
	total width	64 bits
	data width	64 bits
	size		1024 MBytes


DMI Memory Device
-----------------
	designation	A1
	format		DIMM
	type		unknown
	total width	64 bits
	data width	64 bits
	size		1024 MBytes


DMI Memory Device
-----------------
	designation	A2
	format		DIMM
	type		unknown
	total width	64 bits
	data width	64 bits
	size		1024 MBytes


DMI Memory Device
-----------------
	designation	A3
	format		DIMM
	type		unknown
	total width	64 bits
	data width	64 bits
	size		1024 MBytes


Display I2C
------------------------------------------------------------------------------

Resources
------------------------------------------------------------------------------

Port I/O Space, BA=0xFC00
Port I/O Space, BA=0xF800
Port I/O Space, BA=0xF400
Port I/O Space, BA=0xF000
Port I/O Space, BA=0xEC00
Memory I/O Space, BA=0x00000000FE02F000
Memory I/O Space, BA=0x00000000FE02E000
Memory I/O Space, BA=0x00000000FE02D000
Memory I/O Space, BA=0x00000000FE02C000
Memory I/O Space, BA=0x00000000FE02B000
Memory I/O Space, BA=0x00000000FE02A000
Memory I/O Space, BA=0x00000000FE029000
Port I/O Space, BA=0xB00
Port I/O Space, BA=0xFFFFFFFC
Port I/O Space, BA=0xE400
Memory I/O Space, BA=0x00000000FE020000
Memory I/O Space, BA=0x00000000F0000000
Memory I/O Space, BA=0x00000000FDBF0000
Port I/O Space, BA=0xCC00
Memory I/O Space, BA=0x00000000FDA00000
Port I/O Space, BA=0xDC00
Memory I/O Space, BA=0x00000000FDFFF000
Port I/O Space, BA=0x4008, size=0x4
Memory I/O Space, BA=0x00000000FEE00000, size=0x1000
Port I/O Space, BA=0x228
Port I/O Space, BA=0x2E
Port I/O Space, BA=0xCD0, size=0x100

```
There is something I can do? In order for the live CD works?
Thank you for your time.

---

### Post by keithmcc on 2009-04-29
I also have a M2A-VM.

I also get the ACPI message.

Mine proceeds to the desktop, but the background is black with no "Examples" or "Install" icons. After a minute I get a dialog about Nautilus crashing. Right-clicking on the background does nothing, but the menus work.

I made a "USB startup disk". This had problems similar to what zaiboot described with the CD - the modprobe message and busybox.

I checked the md5sum on the iso and did the integrity check on the CD menu.

The CD and "USB startup disk" work fine in 2 different Acer laptops and an older Asus desktop.

8.10, both CD and "USB startup disk" works fine on the M2A-VM.

We had 30 cm. of snow here today. How's Costa Rica?

---

### Post by keithmcc on 2009-05-06
(EDIT)**Ignore this paragraph - I do not have these problems when I use a different CDRW drive. I still have the problem of the USB startup disk giving FATAL modprobe error and going to busybox. **If I unplug all drives from my M2A-VM except for the CD drive then 9.04 (32 bit) boots up correctly. If I boot up with either a  hard drive connected or a USB drive plugged in I get the problems described above (black background, Nautilus crash).



zaiboot, what did you use to get the hardware config report?

(EDIT) [This thread]("http://ubuntuforums.org/showthread.php?t=1151209") seems to be about a similar problem.

---

### Post by whitewolfmac on 2009-05-07
That pic you have is the same thing that is happening to me, but i have a Gateway M-1617. It runs cd fine but not the live usb. The my desktop Gateway FX 6800-01e runs both just fine.

---

### Post by whitewolfmac on 2009-05-07
I for got to add something.

The live usb works on my Gateway FX 6800-01e.

What I am going to do is update the bios on the M-1617. Wail that is doing it's thing i am going to remove Fedora 11 off the flash drive, make the ubuntu live. This time with only 4 GB of storage instead off 14.7 GB. What ever the out come I will let you all know.

---

### Post by whitewolfmac on 2009-05-07
Well every thing was a was of time on that one. I got the same thing. I did notice that before I got the (initramfs) promp that there was a lot of activite on my hard drive. That is compared to booting the cd.

---

### Post by whitewolfmac on 2009-05-07
I was thinking today at work that may be if we installed uBuntu on the flash drive insted of makeing a live USB it may work. Will find out to night.

---

### Post by keithmcc on 2009-05-08
> **whitewolfmac said:**
> I was thinking today at work that may be if we installed uBuntu on the flash drive insted of makeing a live USB it may work. Will find out to night.Be sure to UNPLUG YOUR HARD DRIVE before trying this. Horrible things may happen if you don't.

(EDIT)I tried an install (not a "startup disk") on a 4GB USB drive with my M2A-VM using a non-suspect CD drive. When I boot it in the M2A-VM I get modprobe FATAL and busybox. It boots OK on my Acer Travelmate 2300 and Acer Aspire 3690 (the latter boots in 45 sec.).

The work-around suggested [ by bolucpap]("http://ubuntuforums.org/showthread.php?t=1134436&highlight=busybox#3") worked for me with the full install (not a "startup disk", I'll try that later) on a 4GB USB drive.

Also this workaround by [http://ubuntuforums.org/showpost.php?p=7329199&postcount=7]("http://ubuntuforums.org/showpost.php?p=7329199&postcount=7")Bonser worked on my full install (not a "startup disk"). This does not give the Ubuntu graphic, you need to pull the USB plug when it says "Starting, please wait" (not when it says "Grub starting, please wait")

---

### Post by keithmcc on 2009-06-10
I haven't got around to trying a pendrive type install.

I would use Jackalope despite the awkward boot workaround if suspend worked, but it doesn't for me.

---

### Post by zaiboot on 2009-06-26
> **keithmcc said:**
> (EDIT)**Ignore this paragraph - I do not have these problems when I use a different CDRW drive. I still have the problem of the USB startup disk giving FATAL modprobe error and going to busybox. **If I unplug all drives from my M2A-VM except for the CD drive then 9.04 (32 bit) boots up correctly. If I boot up with either a  hard drive connected or a USB drive plugged in I get the problems described above (black background, Nautilus crash).



zaiboot, what did you use to get the hardware config report?

(EDIT) [This thread]("http://ubuntuforums.org/showthread.php?t=1151209") seems to be about a similar problem.
Hello keithmcc

I use CPU-Z in windows.

---

### Post by keithmcc on 2009-06-28
> **zaiboot said:**
> Hello keithmcc

I use CPU-Z in windows.

Thanks, I will check that out.

I have not got around to trying the workarounds on the pendrive type install or the 64 bit version.

---

