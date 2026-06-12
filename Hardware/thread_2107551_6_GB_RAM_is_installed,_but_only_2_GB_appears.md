---
title: "6 GB RAM is installed, but only 2 GB appears"
date: 2013-01-22
forum: Hardware
---

### Post by tuberculo on 2013-01-22
Hi.
I have a weird problem. 
My computer has 6 GB of RAM, but when I turn it on only 1.7 GB of RAM is available. If I run lshw, I can see that the all the RAM is installed. If I restart the system a few times, all the RAM is recognized properly.
Does anyone know the reason for this behavior?

free -m
```

             total       used       free     shared    buffers     cached
Mem:          1723        690       1033          0         78        231
-/+ buffers/cache:        381       1342
Swap:         9443          0       9443

```


sudo lshw -class memory
```

  *-firmware              
       descrição: BIOS
       fabricante: American Megatrends Inc.
       physical id: 0
       versão: P1.40
       date: 12/04/2012
       tamanho: 64KiB
       capacidade: 4032KiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
  *-memory
       descrição: Memória do sistema
       physical id: 8
       slot: Placa do sistema ou placa-mãe
       tamanho: 6GiB
     *-bank:0
          descrição: DIMM DDR3 Síncrono 1333 MHz (0,8 ns)
          produto: 9905471-006.A00LF
          fabricante: Kingston
          physical id: 0
          serial: 65206C13
          slot: A1_DIMM0
          tamanho: 4GiB
          largura: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:1
          descrição: DIMM DDR3 Síncrono 1333 MHz (0,8 ns)
          produto: 9905402-179.A00LF
          fabricante: Kingston
          physical id: 1
          serial: 7E13B005
          slot: A1_DIMM1
          tamanho: 2GiB
          largura: 64 bits
          clock: 1333MHz (0.8ns)
  *-cache:0
       descrição: L1 cache
       physical id: f
       slot: L1 CACHE
       tamanho: 384KiB
       capacidade: 384KiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
  *-cache:1
       descrição: L2 cache
       physical id: 10
       slot: L2 CACHE
       tamanho: 3MiB
       capacidade: 3MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified


```

uname -a
```

Linux Principal-sala 3.2.0-36-generic #57-Ubuntu SMP Tue Jan 8 21:44:52 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by sudodus on 2013-01-22
So sometimes, after several reboots, all the memory will be grabbed by Ubuntu!

- Could it be a bad connection? Move the RAM cards a little, pull out and push in again and check if it helps.

- Check if you get some error with ***memtest*** (that you can start from the grub menu at boot). Run it for a long time, overnight if possible, to catch an error that might show up only once in a while. I suggest that you reboot until your computer (and memtest) will grab all the RAM.

---

### Post by SeijiSensei on 2013-01-22
It doesn't look like you're using the 64-bit version of the kernel.  The 32-bit version cannot address all six gigabytes unless you have the -pae kernel installed, which uname does not report either.

Try booting from a 64-bit installation CD and run "Try Ubuntu".  When it finishes loading, run free again.  If you see all your memory, then you should consider upgrading to the 64-bit version.

---

### Post by sudodus on 2013-01-22
> **SeijiSensei said:**
> It doesn't look like you're using the 64-bit version of the kernel.  The 32-bit version cannot address all six gigabytes unless you have the -pae kernel installed, which uname does not report either.

Try booting from a 64-bit installation CD and run "Try Ubuntu".  When it finishes loading, run free again.  If you see all your memory, then you should consider upgrading to the 64-bit version.

But in post #1 [s]he wrote

uname -a
 
```
Linux Principal-sala 3.2.0-36-generic #57-Ubuntu SMP Tue Jan 8 21:44:52 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
which indicates a 64-bit kernel (x86_64)

---

### Post by SeijiSensei on 2013-01-22
Sorry, I guess I didn't scroll right far enough.

---

### Post by RAMChYLD on 2013-01-23
Given that you have to restart a few times to have it detected properly...

Do this: Pay attention to the BIOS memory check screen, and see if it's detected properly there. To make the BIOS screen stay longer, turn off quick memory check. If yes, run Memtest86 whenever you notice the BIOS detecting less RAM than installed.

If no, then I'd suspect either RAM not seated properly, bad RAM, or (sometimes) PSU too weak to drive that many bars of RAM. 

If yes, however, it may be a quirk with the firmware. Try upgrading your firmware and see if the problem goes away.

---

### Post by Joao Lacerda on 2013-01-23
Hi Tuberculo!

I have seen similar situation, and the problem was the sequence of 
the memory on the banks, but for this I would recommend you to take a 
look at the motherboard manual. if the memory are not placed correct 
it can result on bad work.

Eu ja vi algo semelhante a isto e o problema era a sequencia que as 
memorias estavam colocadas nos bancos, da uma olhada no site do 
fabricante do seu computador na maioria das vezes tem um manual la 
com as espicifações. num server que eu estou virando uma versao do 
Ubuntu elas estao colocadas com espacos vazios geralmente este bancos 
estao diferenciados com cores dois bancos pretos e dois brancos e se v
oce olhar as cores não estão juntas.. 



Boa sorte
Good luck.

Abraços.

João

---

### Post by Lightning Dragon on 2013-01-23
Hello,

I had the same problem, only with 4GB. For some reason it would only recognize 2 of the 4. I turned the computer off, unplugged the system, took out the RAM and then put them back in. However,  if you have a mixed number like 1*2GB and 1*GB, put the biggest RAM in the first slot.

I say you should definitely consult the manual to your motherboard like Joao Lacerda suggested. Something could be wrong with how they are in or with your BIOS setup. The last thing it could be is that something is wrong with the RAM itself, not with the BIOS or the computer/Ubuntu. I have also read that letting your computer sit for about 5 minutes off with nothing plugged in (PSU) with the RAM out sort of resets it, so you could try that too.

---

### Post by Yellow Pasque on 2013-01-23
What kind of motherboard is it? Look at this if not sure:
```
sudo dmidecode
```

It's always best to use RAM on the mobo vendor's list (though this is not always feasible) and use RAM in matched pairs.

---

### Post by tuberculo on 2013-01-26
Thanks for all the replies. 
I have already tried memtest, but I did not run it for a long time, I'll try that later. 
If I want, I always manage to have 6 GB of RAM, but I have to reboot a few times. That's annoying. I think the problem may be in Ubuntu because, in BIOS, all the memory is recognized every time. The command lshw also recognizes 6 GB.
My motherboard is A55M-HVS. There are only two banks. I have already switched positions, with no result. I also tried BIOS update.
I will try Lightning Dragon's idea later.

dmidecode:
```

# dmidecode 2.11
SMBIOS 2.7 present.
19 structures occupying 1146 bytes.
Table at 0x000E9690.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: P1.40
	Release Date: 12/04/2012
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 4096 kB
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
		BIOS boot specification is supported
		Targeted content distribution is supported
		UEFI is supported
	BIOS Revision: 4.6

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: To Be Filled By O.E.M.
	Product Name: To Be Filled By O.E.M.
	Version: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	UUID: 03000200-0400-0500-0006-000700080009
	Wake-up Type: Power Switch
	SKU Number: To Be Filled By O.E.M.
	Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASRock
	Product Name: A55M-HVS
	Version:                       
	Serial Number:                       
	Asset Tag:                       
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis:                       
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
	Manufacturer: To Be Filled By O.E.M.
	Type: Desktop
	Lock: Not Present
	Version: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0
	SKU Number: To be filled by O.E.M.

Handle 0x0004, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0005, DMI type 9, 17 bytes
System Slot Information
	Designation: PCIE2
	Type: x16 PCI Express
	Current Usage: In Use
	Length: Short
	ID: 17
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:00:02.0

Handle 0x0006, DMI type 9, 17 bytes
System Slot Information
	Designation: PCIE3
	Type: x4 PCI Express
	Current Usage: In Use
	Length: Short
	ID: 18
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:00:04.0

Handle 0x0007, DMI type 11, 5 bytes
OEM Strings
	String 1: To Be Filled By O.E.M.

Handle 0x0008, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 6 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x0009, DMI type 19, 31 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0017FFFFFFF
	Range Size: 6 GB
	Physical Array Handle: 0x0008
	Partition Width: 255

Handle 0x000A, DMI type 17, 34 bytes
Memory Device
	Array Handle: 0x0008
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: DIMM
	Set: None
	Locator: A1_DIMM0
	Bank Locator: A1_BANK0
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MHz
	Manufacturer: Kingston        
	Serial Number: 65206C13  
	Asset Tag: A1_AssetTagNum0
	Part Number: 9905471-006.A00LF 
	Rank: 2
	Configured Clock Speed: 533 MHz

Handle 0x000B, DMI type 20, 35 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Device Handle: 0x000A
	Memory Array Mapped Address Handle: 0x0009
	Partition Row Position: 1

Handle 0x000C, DMI type 17, 34 bytes
Memory Device
	Array Handle: 0x0008
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A1_DIMM1
	Bank Locator: A1_BANK1
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MHz
	Manufacturer: Kingston        
	Serial Number: 7E13B005  
	Asset Tag: A1_AssetTagNum1
	Part Number: 9905402-179.A00LF 
	Rank: 1
	Configured Clock Speed: 533 MHz

Handle 0x000D, DMI type 20, 35 bytes
Memory Device Mapped Address
	Starting Address: 0x00100000000
	Ending Address: 0x0017FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x000C
	Memory Array Mapped Address Handle: 0x0009
	Partition Row Position: 1

Handle 0x000E, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x000F, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 CACHE
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 384 kB
	Maximum Size: 384 kB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: 1 ns
	Error Correction Type: Multi-bit ECC
	System Type: Unified
	Associativity: 2-way Set-associative

Handle 0x0010, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 CACHE
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 3072 kB
	Maximum Size: 3072 kB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: 1 ns
	Error Correction Type: Multi-bit ECC
	System Type: Unified
	Associativity: 16-way Set-associative

Handle 0x0012, DMI type 4, 42 bytes
Processor Information
	Socket Designation: CPUSocket
	Type: Central Processor
	Family: S-Series
	Manufacturer: AMD
	ID: 10 0F 30 00 FF FB 8B 17
	Signature: Family 18, Model 1, Stepping 0
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
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		HTT (Multi-threading)
	Version: AMD A6-3500 APU with Radeon(tm) HD Graphics
	Voltage: 1.4 V
	External Clock: 100 MHz
	Max Speed: 2100 MHz
	Current Speed: 2100 MHz
	Status: Populated, Enabled
	Upgrade: Socket FM1
	L1 Cache Handle: 0x000F
	L2 Cache Handle: 0x0010
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Core Count: 3
	Core Enabled: 3
	Thread Count: 3
	Characteristics:
		64-bit capable

Handle 0x0013, DMI type 127, 4 bytes
End Of Table


```

---

### Post by sudodus on 2013-01-27
> **tuberculo said:**
> Thanks for all the replies. 
I have already tried memtest, but I did not run it for a long time, I'll try that later. 
If I want, I always manage to have 6 GB of RAM, but I have to reboot a few times. That's annoying. I think the problem may be in Ubuntu because, in BIOS, all the memory is recognized every time. [COLOR="Red"]The command lshw also recognizes 6 GB.[/COLOR]
My motherboard is A55M-HVS. There are only two banks. I have already switched positions, with no result. I also tried BIOS update.
I will try Lightning Dragon's idea later.

Did I understand this correctly: The command lshw also recognizes 6 GB [COLOR="red"]always[/COLOR]?

Then I am surprised that ***free*** will not show it. I suggest that you try Lightning Dragon's idea to change places of the RAM cards, and consult the manual to your motherboard like Joao Lacerda suggested.

---

### Post by Yellow Pasque on 2013-01-27
I would compare dmesg from a boot where you have 2GB and a boot where you have 6GB. So the next time you boot, check the mem, and if you have 2GB, save the dmesg:
```
dmesg -t > ~/dmesg2.txt
```
Then, boot until you have 6GB, and grab that dmesg:
```
dmesg -t > ~/dmesg6.txt
```

Then, check out the differences. (I would say to use diff utility, but that may be misleading).

---

### Post by tuberculo on 2013-02-15
Hi. 
I did not respond before because I was on vacation. 
Here are the dmesg outputs:

dmesg2.txt
```

Initializing cgroup subsys cpuset
Initializing cgroup subsys cpu
Linux version 3.2.0-37-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 (Ubuntu 3.2.0-37.58-generic 3.2.35)
Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=8d413c35-07e0-4d5e-b4ff-e2ee3856f4ae ro quiet splash vt.handoff=7
KERNEL supported cpus:
  Intel GenuineIntel
  AMD AuthenticAMD
  Centaur CentaurHauls
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000006e05f000 (usable)
 BIOS-e820: 000000006e05f000 - 000000006e0c1000 (reserved)
 BIOS-e820: 000000006e0c1000 - 000000006e18e000 (ACPI NVS)
 BIOS-e820: 000000006e18e000 - 000000006e6f6000 (reserved)
 BIOS-e820: 000000006e6f6000 - 000000006e6f7000 (usable)
 BIOS-e820: 000000006e6f7000 - 000000006e6ff000 (ACPI NVS)
 BIOS-e820: 000000006e6ff000 - 000000006eb13000 (usable)
 BIOS-e820: 000000006eb13000 - 000000006eef4000 (reserved)
 BIOS-e820: 000000006eef4000 - 000000006ef00000 (usable)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
 BIOS-e820: 00000000fed00000 - 00000000fed01000 (reserved)
 BIOS-e820: 00000000fed61000 - 00000000fed71000 (reserved)
 BIOS-e820: 00000000fed80000 - 00000000fed90000 (reserved)
 BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
NX (Execute Disable) protection: active
DMI 2.7 present.
DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./A55M-HVS, BIOS P1.40 12/04/2012
e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
No AGP bridge found
last_pfn = 0x6ef00 max_arch_pfn = 0x400000000
MTRR default type: uncachable
MTRR fixed ranges enabled:
  00000-9FFFF write-back
  A0000-BFFFF write-through
  C0000-CEFFF write-protect
  CF000-E7FFF uncachable
  E8000-FFFFF write-protect
MTRR variable ranges enabled:
  0 base 0000000000 mask FF80000000 write-back
  1 base 006EF00000 mask FFFFF00000 uncachable
  2 base 006F000000 mask FFFF000000 uncachable
  3 base 0070000000 mask FFF0000000 uncachable
  4 disabled
  5 disabled
  6 disabled
  7 disabled
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
original variable MTRRs
reg 0, base: 0GB, range: 2GB, type WB
reg 1, base: 1775MB, range: 1MB, type UC
reg 2, base: 1776MB, range: 16MB, type UC
reg 3, base: 1792MB, range: 256MB, type UC
total RAM covered: 1775M
Found optimal setting for mtrr clean up
 gran_size: 64K 	chunk_size: 512M 	num_reg: 4  	lose cover RAM: 0G
New variable MTRRs
reg 0, base: 0GB, range: 2GB, type WB
reg 1, base: 1775MB, range: 1MB, type UC
reg 2, base: 1776MB, range: 16MB, type UC
reg 3, base: 1792MB, range: 256MB, type UC
found SMP MP-table at [ffff8800000fd7d0] fd7d0
initial memory mapped : 0 - 20000000
Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Using GB pages for direct mapping
init_memory_mapping: 0000000000000000-000000006ef00000
 0000000000 - 0040000000 page 1G
 0040000000 - 006ee00000 page 2M
 006ee00000 - 006ef00000 page 4k
kernel direct mapping tables up to 6ef00000 @ 1fffd000-20000000
RAMDISK: 364ce000 - 3725f000
ACPI: RSDP 00000000000f0490 00024 (v02 ALASKA)
ACPI: XSDT 000000006e17e078 0006C (v01 ALASKA    A M I 01072009 AMI  00010013)
ACPI: FACP 000000006e184980 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
ACPI: DSDT 000000006e17e178 06803 (v02 ALASKA    A M I 00000000 INTL 20051117)
ACPI: FACS 000000006e18c080 00040
ACPI: APIC 000000006e184a90 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
ACPI: FPDT 000000006e184b08 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
ACPI: MCFG 000000006e184b50 0003C (v01 A M I  GMCH945. 01072009 MSFT 00000097)
ACPI: AAFT 000000006e184b90 00042 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
ACPI: HPET 000000006e184bd8 00038 (v01 ALASKA    A M I 01072009 AMI  00000005)
ACPI: SSDT 000000006e184c10 00AB0 (v01 AMD    POWERNOW 00000001 AMD  00000001)
ACPI: SSDT 000000006e1856c0 00695 (v02    AMD     ALIB 00000001 MSFT 04000000)
ACPI: BGRT 000000006e185d58 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
ACPI: Local APIC address 0xfee00000
No NUMA configuration found
Faking a node at 0000000000000000-000000006ef00000
Initmem setup node 0 0000000000000000-000000006ef00000
  NODE_DATA [000000006eefb000 - 000000006eefffff]
 [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88006c000000-ffff88006dbfffff] on node 0
Zone PFN ranges:
  DMA      0x00000010 -> 0x00001000
  DMA32    0x00001000 -> 0x00100000
  Normal   empty
Movable zone start PFN for each node
early_node_map[5] active PFN ranges
    0: 0x00000010 -> 0x0000009f
    0: 0x00000100 -> 0x0006e05f
    0: 0x0006e6f6 -> 0x0006e6f7
    0: 0x0006e6ff -> 0x0006eb13
    0: 0x0006eef4 -> 0x0006ef00
On node 0 totalpages: 451599
  DMA zone: 64 pages used for memmap
  DMA zone: 5 pages reserved
  DMA zone: 3914 pages, LIFO batch:0
  DMA32 zone: 7036 pages used for memmap
  DMA32 zone: 440580 pages, LIFO batch:31
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Using ACPI (MADT) for SMP configuration information
ACPI: HPET id: 0xffffffff base: 0xfed00000
SMP: Allowing 4 CPUs, 1 hotplug CPUs
nr_irqs_gsi: 40
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
PM: Registered nosave memory: 000000006e05f000 - 000000006e0c1000
PM: Registered nosave memory: 000000006e0c1000 - 000000006e18e000
PM: Registered nosave memory: 000000006e18e000 - 000000006e6f6000
PM: Registered nosave memory: 000000006e6f7000 - 000000006e6ff000
PM: Registered nosave memory: 000000006eb13000 - 000000006eef4000
Allocating PCI resources starting at 6ef00000 (gap: 6ef00000:71100000)
Booting paravirtualized kernel on bare hardware
setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
PERCPU: Embedded 28 pages/cpu @ffff88006e800000 s83136 r8192 d23360 u524288
pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
pcpu-alloc: [0] 0 1 2 3 
Built 1 zonelists in Node order, mobility grouping on.  Total pages: 444494
Policy zone: DMA32
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=8d413c35-07e0-4d5e-b4ff-e2ee3856f4ae ro quiet splash vt.handoff=7
PID hash table entries: 4096 (order: 3, 32768 bytes)
Checking aperture...
No AGP bridge found
Calgary: detecting Calgary via BIOS EBDA area
Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Memory: 1747552k/1817600k available (6569k kernel code, 11204k absent, 58844k reserved, 6634k data, 924k init)
SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Hierarchical RCU implementation.
	RCU dyntick-idle grace-period acceleration is enabled.
NR_IRQS:16640 nr_irqs:712 16
Extended CMOS year: 2000
spurious 8259A interrupt: IRQ7.
vt handoff: transparent VT on vt#7
Console: colour dummy device 80x25
console [tty0] enabled
allocated 14680064 bytes of page_cgroup
please try 'cgroup_disable=memory' option if you don't want memory cgroups
hpet clockevent registered
Fast TSC calibration using PIT
Detected 2096.211 MHz processor.
Calibrating delay loop (skipped), value calculated using timer frequency.. 4192.42 BogoMIPS (lpj=8384844)
pid_max: default: 32768 minimum: 301
Security Framework initialized
AppArmor: AppArmor initialized
Yama: becoming mindful.
Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Mount-cache hash table entries: 256
Initializing cgroup subsys cpuacct
Initializing cgroup subsys memory
Initializing cgroup subsys devices
Initializing cgroup subsys freezer
Initializing cgroup subsys blkio
Initializing cgroup subsys perf_event
tseg: 006ef00000
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
mce: CPU supports 6 MCE banks
ACPI: Core revision 20110623
ftrace: allocating 27033 entries in 107 pages
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
CPU0: AMD A6-3500 APU with Radeon(tm) HD Graphics stepping 00
Performance Events: AMD PMU driver.
... version:                0
... bit width:              48
... generic registers:      4
... value mask:             0000ffffffffffff
... max period:             00007fffffffffff
... fixed-purpose events:   0
... event mask:             000000000000000f
NMI watchdog enabled, takes one hw-pmu counter.
Booting Node   0, Processors  #1
smpboot cpu 1: start_ip = 9a000
NMI watchdog enabled, takes one hw-pmu counter.
 #2
smpboot cpu 2: start_ip = 9a000
NMI watchdog enabled, takes one hw-pmu counter.
Brought up 3 CPUs
Total of 3 processors activated (12576.95 BogoMIPS).
devtmpfs: initialized
EVM: security.selinux
EVM: security.SMACK64
EVM: security.capability
PM: Registering ACPI NVS region at 6e0c1000 (839680 bytes)
PM: Registering ACPI NVS region at 6e6f7000 (32768 bytes)
print_constraints: dummy: 
RTC time: 14:02:35, date: 02/13/13
NET: Registered protocol family 16
Extended Config Space enabled on 0 nodes
ACPI: bus type pci registered
PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Trying to unpack rootfs image as initramfs...
PCI: Using configuration type 1 for base access
bio: create slab <bio-0> at 0
ACPI: Added _OSI(Module Device)
ACPI: Added _OSI(Processor Device)
ACPI: Added _OSI(3.0 _SCP Extensions)
ACPI: Added _OSI(Processor Aggregator Device)
ACPI: EC: Look up EC in DSDT
ACPI: Executed 1 blocks of module-level executable AML code
ACPI: Interpreter enabled
ACPI: (supports S0 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
ACPI: No dock devices found.
HEST: Table not found.
PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
pci_root PNP0A03:00: host bridge window [io  0x0000-0x03af]
pci_root PNP0A03:00: host bridge window [io  0x03e0-0x0cf7]
pci_root PNP0A03:00: host bridge window [io  0x03b0-0x03df]
pci_root PNP0A03:00: host bridge window [io  0x1778-0xffff]
pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
pci_root PNP0A03:00: host bridge window [mem 0x7f000000-0xffffffff]
pci 0000:00:00.0: [1022:1705] type 0 class 0x000600
pci 0000:00:01.0: [1002:964a] type 0 class 0x000300
pci 0000:00:01.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
pci 0000:00:01.0: reg 14: [io  0xf000-0xf0ff]
pci 0000:00:01.0: reg 18: [mem 0xfef00000-0xfef3ffff]
pci 0000:00:01.0: supports D1 D2
pci 0000:00:01.1: [1002:1714] type 0 class 0x000403
pci 0000:00:01.1: reg 10: [mem 0xfef44000-0xfef47fff]
pci 0000:00:01.1: supports D1 D2
pci 0000:00:05.0: [1022:170a] type 1 class 0x000604
pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
pci 0000:00:05.0: PME# disabled
pci 0000:00:11.0: [1022:7800] type 0 class 0x000101
pci 0000:00:11.0: reg 10: [io  0xf190-0xf197]
pci 0000:00:11.0: reg 14: [io  0xf180-0xf183]
pci 0000:00:11.0: reg 18: [io  0xf170-0xf177]
pci 0000:00:11.0: reg 1c: [io  0xf160-0xf163]
pci 0000:00:11.0: reg 20: [io  0xf150-0xf15f]
pci 0000:00:11.0: reg 24: [mem 0xfef4f000-0xfef4f7ff]
pci 0000:00:11.0: set SATA to AHCI mode
pci 0000:00:12.0: [1022:7807] type 0 class 0x000c03
pci 0000:00:12.0: reg 10: [mem 0xfef4e000-0xfef4efff]
pci 0000:00:12.2: [1022:7808] type 0 class 0x000c03
pci 0000:00:12.2: reg 10: [mem 0xfef4d000-0xfef4d0ff]
pci 0000:00:12.2: supports D1 D2
pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
pci 0000:00:12.2: PME# disabled
pci 0000:00:13.0: [1022:7807] type 0 class 0x000c03
pci 0000:00:13.0: reg 10: [mem 0xfef4c000-0xfef4cfff]
pci 0000:00:13.2: [1022:7808] type 0 class 0x000c03
pci 0000:00:13.2: reg 10: [mem 0xfef4b000-0xfef4b0ff]
pci 0000:00:13.2: supports D1 D2
pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
pci 0000:00:13.2: PME# disabled
pci 0000:00:14.0: [1022:780b] type 0 class 0x000c05
pci 0000:00:14.1: [1022:780c] type 0 class 0x000101
pci 0000:00:14.1: reg 10: [io  0xf140-0xf147]
pci 0000:00:14.1: reg 14: [io  0xf130-0xf133]
pci 0000:00:14.1: reg 18: [io  0xf120-0xf127]
pci 0000:00:14.1: reg 1c: [io  0xf110-0xf113]
pci 0000:00:14.1: reg 20: [io  0xf100-0xf10f]
pci 0000:00:14.2: [1022:780d] type 0 class 0x000403
pci 0000:00:14.2: reg 10: [mem 0xfef40000-0xfef43fff 64bit]
pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
pci 0000:00:14.2: PME# disabled
pci 0000:00:14.3: [1022:780e] type 0 class 0x000601
pci 0000:00:14.4: [1022:780f] type 1 class 0x000604
pci 0000:00:14.5: [1022:7809] type 0 class 0x000c03
pci 0000:00:14.5: reg 10: [mem 0xfef4a000-0xfef4afff]
pci 0000:00:16.0: [1022:7807] type 0 class 0x000c03
pci 0000:00:16.0: reg 10: [mem 0xfef49000-0xfef49fff]
pci 0000:00:16.2: [1022:7808] type 0 class 0x000c03
pci 0000:00:16.2: reg 10: [mem 0xfef48000-0xfef480ff]
pci 0000:00:16.2: supports D1 D2
pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
pci 0000:00:16.2: PME# disabled
pci 0000:00:18.0: [1022:1700] type 0 class 0x000600
pci 0000:00:18.1: [1022:1701] type 0 class 0x000600
pci 0000:00:18.2: [1022:1702] type 0 class 0x000600
pci 0000:00:18.3: [1022:1703] type 0 class 0x000600
pci 0000:00:18.4: [1022:1704] type 0 class 0x000600
pci 0000:00:18.5: [1022:1718] type 0 class 0x000600
pci 0000:00:18.6: [1022:1716] type 0 class 0x000600
pci 0000:00:18.7: [1022:1719] type 0 class 0x000600
pci 0000:01:00.0: [10ec:8168] type 0 class 0x000200
pci 0000:01:00.0: reg 10: [io  0xe000-0xe0ff]
pci 0000:01:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
pci 0000:01:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
pci 0000:01:00.0: supports D1 D2
pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:01:00.0: PME# disabled
pci 0000:00:05.0: PCI bridge to [bus 01-01]
pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
pci 0000:00:14.4: PCI bridge to [bus 02-02] (subtractive decode)
pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
pci 0000:00:14.4:   bridge window [io  0x1778-0xffff] (subtractive decode)
pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
pci 0000:00:14.4:   bridge window [mem 0x7f000000-0xffffffff] (subtractive decode)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
 pci0000:00: Requesting ACPI _OSC control (0x1d)
 pci0000:00: ACPI _OSC control (0x1c) granted
ACPI: PCI Interrupt Link [LN24] (IRQs *24)
ACPI: PCI Interrupt Link [LN25] (IRQs *25)
ACPI: PCI Interrupt Link [LN26] (IRQs *26)
ACPI: PCI Interrupt Link [LN27] (IRQs *27)
ACPI: PCI Interrupt Link [LN28] (IRQs *28)
ACPI: PCI Interrupt Link [LN29] (IRQs *29)
ACPI: PCI Interrupt Link [LN30] (IRQs *30)
ACPI: PCI Interrupt Link [LN31] (IRQs *31)
ACPI: PCI Interrupt Link [LN32] (IRQs *32)
ACPI: PCI Interrupt Link [LN33] (IRQs *33)
ACPI: PCI Interrupt Link [LN34] (IRQs *34)
ACPI: PCI Interrupt Link [LN35] (IRQs *35)
ACPI: PCI Interrupt Link [LN36] (IRQs *36)
ACPI: PCI Interrupt Link [LN37] (IRQs *37)
ACPI: PCI Interrupt Link [LN38] (IRQs *38)
ACPI: PCI Interrupt Link [LN39] (IRQs *39)
ACPI: PCI Interrupt Link [LN40] (IRQs *40)
ACPI: PCI Interrupt Link [LN41] (IRQs *41)
ACPI: PCI Interrupt Link [LN42] (IRQs *42)
ACPI: PCI Interrupt Link [LN43] (IRQs *43)
ACPI: PCI Interrupt Link [LN44] (IRQs *44)
ACPI: PCI Interrupt Link [LN45] (IRQs *45)
ACPI: PCI Interrupt Link [LN46] (IRQs *46)
ACPI: PCI Interrupt Link [LN47] (IRQs *47)
ACPI: PCI Interrupt Link [LN48] (IRQs *48)
ACPI: PCI Interrupt Link [LN49] (IRQs *49)
ACPI: PCI Interrupt Link [LN50] (IRQs *50)
ACPI: PCI Interrupt Link [LN51] (IRQs *51)
ACPI: PCI Interrupt Link [LN52] (IRQs *52)
ACPI: PCI Interrupt Link [LN53] (IRQs *53)
ACPI: PCI Interrupt Link [LN54] (IRQs *54)
ACPI: PCI Interrupt Link [LN55] (IRQs *55)
ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11 14 15) *0
vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
vgaarb: loaded
vgaarb: bridge control possible 0000:00:01.0
i2c-core: driver [aat2870] using legacy suspend method
i2c-core: driver [aat2870] using legacy resume method
SCSI subsystem initialized
libata version 3.00 loaded.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
PCI: pci_cache_line_size set to 64 bytes
reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
reserve RAM buffer: 000000006e05f000 - 000000006fffffff 
reserve RAM buffer: 000000006e6f7000 - 000000006fffffff 
reserve RAM buffer: 000000006eb13000 - 000000006fffffff 
reserve RAM buffer: 000000006ef00000 - 000000006fffffff 
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Switching to clocksource hpet
AppArmor: AppArmor Filesystem Enabled
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp 00:00: [bus 00-ff]
pnp 00:00: [io  0x0cf8-0x0cff]
pnp 00:00: [io  0x0000-0x03af window]
pnp 00:00: [io  0x03e0-0x0cf7 window]
pnp 00:00: [io  0x03b0-0x03df window]
pnp 00:00: [io  0x1778-0xffff window]
pnp 00:00: [mem 0x000a0000-0x000bffff window]
pnp 00:00: [mem 0x000c0000-0x000dffff window]
pnp 00:00: [mem 0x7f000000-0xffffffff window]
pnp 00:00: [mem 0x00000000 window]
pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
pnp 00:01: [mem 0xe0000000-0xefffffff]
system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
pnp 00:02: [io  0x0010-0x001f]
pnp 00:02: [io  0x0022-0x003f]
pnp 00:02: [io  0x0063]
pnp 00:02: [io  0x0065]
pnp 00:02: [io  0x0067-0x006f]
pnp 00:02: [io  0x0072-0x007f]
pnp 00:02: [io  0x0080]
pnp 00:02: [io  0x0084-0x0086]
pnp 00:02: [io  0x0088]
pnp 00:02: [io  0x008c-0x008e]
pnp 00:02: [io  0x0090-0x009f]
pnp 00:02: [io  0x00a2-0x00bf]
pnp 00:02: [io  0x00b1]
pnp 00:02: [io  0x00e0-0x00ef]
pnp 00:02: [io  0x04d0-0x04d1]
pnp 00:02: [io  0x040b]
pnp 00:02: [io  0x04d6]
pnp 00:02: [io  0x0c00-0x0c01]
pnp 00:02: [io  0x0c14]
pnp 00:02: [io  0x0c50-0x0c51]
pnp 00:02: [io  0x0c52]
pnp 00:02: [io  0x0c6c]
pnp 00:02: [io  0x0c6f]
pnp 00:02: [io  0x0cd0-0x0cd1]
pnp 00:02: [io  0x0cd2-0x0cd3]
pnp 00:02: [io  0x0cd4-0x0cd5]
pnp 00:02: [io  0x0cd6-0x0cd7]
pnp 00:02: [io  0x0cd8-0x0cdf]
pnp 00:02: [io  0x0800-0x089f]
pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
pnp 00:02: [io  0x0000-0x000f]
pnp 00:02: [io  0x0b20-0x0b3f]
pnp 00:02: [io  0x0900-0x090f]
pnp 00:02: [io  0x0910-0x091f]
pnp 00:02: [io  0xfe00-0xfefe]
pnp 00:02: [io  0x0060-0x005f disabled]
pnp 00:02: [io  0x0064-0x0063 disabled]
pnp 00:02: [mem 0xfec00000-0xfec00fff]
pnp 00:02: [mem 0xfee00000-0xfee00fff]
pnp 00:02: [mem 0xfed80000-0xfed8ffff]
pnp 00:02: [mem 0xfed61000-0xfed70fff]
pnp 00:02: [mem 0xfec10000-0xfec10fff]
pnp 00:02: [mem 0xfed00000-0xfed00fff]
pnp 00:02: [mem 0xff000000-0xffffffff]
system 00:02: [io  0x04d0-0x04d1] has been reserved
system 00:02: [io  0x040b] has been reserved
system 00:02: [io  0x04d6] has been reserved
system 00:02: [io  0x0c00-0x0c01] has been reserved
system 00:02: [io  0x0c14] has been reserved
system 00:02: [io  0x0c50-0x0c51] has been reserved
system 00:02: [io  0x0c52] has been reserved
system 00:02: [io  0x0c6c] has been reserved
system 00:02: [io  0x0c6f] has been reserved
system 00:02: [io  0x0cd0-0x0cd1] has been reserved
system 00:02: [io  0x0cd2-0x0cd3] has been reserved
system 00:02: [io  0x0cd4-0x0cd5] has been reserved
system 00:02: [io  0x0cd6-0x0cd7] has been reserved
system 00:02: [io  0x0cd8-0x0cdf] has been reserved
system 00:02: [io  0x0800-0x089f] has been reserved
system 00:02: [io  0x0b20-0x0b3f] has been reserved
system 00:02: [io  0x0900-0x090f] has been reserved
system 00:02: [io  0x0910-0x091f] has been reserved
system 00:02: [io  0xfe00-0xfefe] has been reserved
system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
system 00:02: [mem 0xfed80000-0xfed8ffff] has been reserved
system 00:02: [mem 0xfed61000-0xfed70fff] has been reserved
system 00:02: [mem 0xfec10000-0xfec10fff] has been reserved
system 00:02: [mem 0xfed00000-0xfed00fff] has been reserved
system 00:02: [mem 0xff000000-0xffffffff] has been reserved
system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
pnp 00:03: [io  0x0290-0x029f]
pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
system 00:03: [io  0x0290-0x029f] has been reserved
system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:04: [io  0x0378-0x037f]
pnp 00:04: [io  0x0778-0x077f]
pnp 00:04: [irq 5]
pnp 00:04: [dma 3]
pnp 00:04: Plug and Play ACPI device, IDs PNP0401 (active)
pnp 00:05: [dma 4]
pnp 00:05: [io  0x0000-0x000f]
pnp 00:05: [io  0x0081-0x0083]
pnp 00:05: [io  0x0087]
pnp 00:05: [io  0x0089-0x008b]
pnp 00:05: [io  0x008f]
pnp 00:05: [io  0x00c0-0x00df]
pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
pnp 00:06: [io  0x0070-0x0071]
pnp 00:06: [irq 8]
pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
pnp 00:07: [io  0x0061]
pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
pnp 00:08: [io  0x0010-0x001f]
pnp 00:08: [io  0x0022-0x003f]
pnp 00:08: [io  0x0044-0x005f]
pnp 00:08: [io  0x0062-0x0063]
pnp 00:08: [io  0x0065-0x006f]
pnp 00:08: [io  0x0072-0x007f]
pnp 00:08: [io  0x0080]
pnp 00:08: [io  0x0084-0x0086]
pnp 00:08: [io  0x0088]
pnp 00:08: [io  0x008c-0x008e]
pnp 00:08: [io  0x0090-0x009f]
pnp 00:08: [io  0x00a2-0x00bf]
pnp 00:08: [io  0x00e0-0x00ef]
pnp 00:08: [io  0x04d0-0x04d1]
system 00:08: [io  0x04d0-0x04d1] has been reserved
system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:09: [io  0x00f0-0x00ff]
pnp 00:09: [irq 13]
pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
pnp 00:0a: [io  0x1770-0x1777]
system 00:0a: [io  0x1770-0x1777] has been reserved
system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:0b: [io  0x0060]
pnp 00:0b: [io  0x0064]
pnp 00:0b: [irq 1]
pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
pnp 00:0c: [io  0x03f8-0x03ff]
pnp 00:0c: [irq 4]
pnp 00:0c: [dma 0 disabled]
pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
pnp 00:0d: [mem 0xfed00000-0xfed003ff]
pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
pnp: PnP ACPI: found 14 devices
ACPI: ACPI bus type pnp unregistered
PCI: max bus depth: 1 pci_try_num: 2
pci 0000:00:05.0: PCI bridge to [bus 01-01]
pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
pci 0000:00:14.4: PCI bridge to [bus 02-02]
pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:05.0: setting latency timer to 64
pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
pci_bus 0000:00: resource 7 [io  0x1778-0xffff]
pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
pci_bus 0000:00: resource 10 [mem 0x7f000000-0xffffffff]
pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
pci_bus 0000:02: resource 4 [io  0x0000-0x03af]
pci_bus 0000:02: resource 5 [io  0x03e0-0x0cf7]
pci_bus 0000:02: resource 6 [io  0x03b0-0x03df]
pci_bus 0000:02: resource 7 [io  0x1778-0xffff]
pci_bus 0000:02: resource 8 [mem 0x000a0000-0x000bffff]
pci_bus 0000:02: resource 9 [mem 0x000c0000-0x000dffff]
pci_bus 0000:02: resource 10 [mem 0x7f000000-0xffffffff]
NET: Registered protocol family 2
IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
TCP: Hash tables configured (established 262144 bind 65536)
TCP reno registered
UDP hash table entries: 1024 (order: 3, 32768 bytes)
UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
NET: Registered protocol family 1
pci 0000:00:01.0: Boot video device
pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Freeing initrd memory: 13892k freed
pci 0000:00:12.0: PCI INT A disabled
pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:12.2: PCI INT B disabled
pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
pci 0000:00:13.0: PCI INT A disabled
pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:13.2: PCI INT B disabled
pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
pci 0000:00:14.5: PCI INT C disabled
pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
pci 0000:00:16.0: PCI INT A disabled
pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:16.2: PCI INT B disabled
PCI: CLS 64 bytes, default 64
perf: AMD IBS detected (0x000000ff)
audit: initializing netlink socket (disabled)
type=2000 audit(1360764155.820:1): initialized
HugeTLB registered 2 MB page size, pre-allocated 0 pages
VFS: Disk quotas dquot_6.5.2
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
fuse init (API version 7.17)
msgmni has been set to 3440
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
pcieport 0000:00:05.0: setting latency timer to 64
pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
pcieport 0000:00:05.0: Signaling PME through PCIe PME interrupt
pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
pcie_pme 0000:00:05.0:pcie01: service driver pcie_pme loaded
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: PCI Express Hot Plug Controller Driver version: 0.4
input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
ACPI: Power Button [PWRB]
input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
ACPI: Power Button [PWRF]
ACPI: acpi_idle registered with cpuidle
ERST: Table is not found!
GHES: HEST is not enabled!
Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Linux agpgart interface v0.103
brd: module loaded
loop: module loaded
ahci 0000:00:11.0: version 3.0
ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
ahci 0000:00:11.0: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0xf impl SATA mode
ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
scsi0 : ahci
scsi1 : ahci
scsi2 : ahci
scsi3 : ahci
ata1: SATA max UDMA/133 abar m2048@0xfef4f000 port 0xfef4f100 irq 19
ata2: SATA max UDMA/133 abar m2048@0xfef4f000 port 0xfef4f180 irq 19
ata3: SATA max UDMA/133 abar m2048@0xfef4f000 port 0xfef4f200 irq 19
ata4: SATA max UDMA/133 abar m2048@0xfef4f000 port 0xfef4f280 irq 19
pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pata_acpi 0000:00:14.1: PCI INT B disabled
Fixed MDIO Bus: probed
tun: Universal TUN/TAP device driver, 1.6
tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
PPP generic driver version 2.4.2
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
ehci_hcd 0000:00:12.2: EHCI Host Controller
ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
QUIRK: Enable AMD PLL fix
ehci_hcd 0000:00:12.2: debug port 1
ehci_hcd 0000:00:12.2: irq 17, io mem 0xfef4d000
ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 5 ports detected
ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
ehci_hcd 0000:00:13.2: EHCI Host Controller
ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
ehci_hcd 0000:00:13.2: debug port 1
ehci_hcd 0000:00:13.2: irq 17, io mem 0xfef4b000
ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 5 ports detected
ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
ehci_hcd 0000:00:16.2: EHCI Host Controller
ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
ehci_hcd 0000:00:16.2: debug port 1
ehci_hcd 0000:00:16.2: irq 17, io mem 0xfef48000
ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 4 ports detected
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:12.0: OHCI Host Controller
ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
ohci_hcd 0000:00:12.0: irq 18, io mem 0xfef4e000
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 5 ports detected
ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:13.0: OHCI Host Controller
ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
ohci_hcd 0000:00:13.0: irq 18, io mem 0xfef4c000
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 5 ports detected
ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:14.5: OHCI Host Controller
ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
ohci_hcd 0000:00:14.5: irq 18, io mem 0xfef4a000
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 2 ports detected
ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:16.0: OHCI Host Controller
ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
ohci_hcd 0000:00:16.0: irq 18, io mem 0xfef49000
hub 7-0:1.0: USB hub found
hub 7-0:1.0: 4 ports detected
uhci_hcd: USB Universal Host Controller Interface driver
usbcore: registered new interface driver libusual
i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
serio: i8042 KBD port at 0x60,0x64 irq 1
mousedev: PS/2 mouse device common for all mice
rtc_cmos 00:06: RTC can wake from S4
rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
device-mapper: uevent: version 1.0.3
device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
cpuidle: using governor ladder
cpuidle: using governor menu
EFI Variables Facility v0.08 2004-May-17
TCP cubic registered
NET: Registered protocol family 10
NET: Registered protocol family 17
Registering the dns_resolver key type
PM: Hibernation image not present or could not be loaded.
registered taskstats version 1
  Magic number: 1:397:30
rtc_cmos 00:06: setting system clock to 2013-02-13 14:02:36 UTC (1360764156)
powernow-k8: Found 1 AMD A6-3500 APU with Radeon(tm) HD Graphics (3 cpu cores) (version 2.20.00)
powernow-k8: Core Performance Boosting: on.
powernow-k8:    0 : pstate 0 (2100 MHz)
powernow-k8:    1 : pstate 1 (1900 MHz)
powernow-k8:    2 : pstate 2 (1600 MHz)
powernow-k8:    3 : pstate 3 (1400 MHz)
powernow-k8:    4 : pstate 4 (1200 MHz)
powernow-k8:    5 : pstate 5 (1000 MHz)
powernow-k8:    6 : pstate 6 (800 MHz)
BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
EDD information not available.
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
ata3: SATA link down (SStatus 0 SControl 300)
ata4: SATA link down (SStatus 0 SControl 300)
ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata2.00: ATA-7: ST3250410AS, 4.AAA, max UDMA/133
ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
ata2.00: configured for UDMA/133
ata1.00: ATA-8: MAXTOR STM3500320AS, MX1A, max UDMA/133
ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
ata1.00: configured for UDMA/133
scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM350032 MX1A PQ: 0 ANSI: 5
sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
sd 0:0:0:0: Attached scsi generic sg0 type 0
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
scsi 1:0:0:0: Direct-Access     ATA      ST3250410AS      4.AA PQ: 0 ANSI: 5
sd 1:0:0:0: Attached scsi generic sg1 type 0
sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 < sda5 >
sd 0:0:0:0: [sda] Attached SCSI disk
 sdb: sdb1 sdb2
sd 1:0:0:0: [sdb] Attached SCSI disk
Freeing unused kernel memory: 924k freed
Write protecting the kernel read-only data: 12288k
Freeing unused kernel memory: 1604k freed
Freeing unused kernel memory: 1196k freed
udevd[97]: starting version 175
r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
r8169 0000:01:00.0: setting latency timer to 64
r8169 0000:01:00.0: irq 41 for MSI/MSI-X
r8169 0000:01:00.0: eth0: RTL8168evl/8111evl at 0xffffc90000316000, bc:5f:f4:46:a8:67, XID 0c900800 IRQ 41
r8169 0000:01:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
usb 7-1: new low-speed USB device number 2 using ohci_hcd
pata_atiixp 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
scsi4 : pata_atiixp
scsi5 : pata_atiixp
ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf100 irq 14
ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf108 irq 15
input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:16.0/usb7/7-1/7-1:1.0/input/input3
generic-usb 0003:15D9:0A4C.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:16.0-1/input0
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
Refined TSC clocksource calibration: 2096.187 MHz.
Switching to clocksource tsc
EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Adding 8787548k swap on /dev/sdb2.  Priority:-1 extents:1 across:8787548k 
ADDRCONF(NETDEV_UP): eth0: link is not ready
udevd[439]: starting version 175
lp: driver loaded but no devices found
parport_pc 00:04: reported by Plug and Play ACPI
parport0: PC-style at 0x378, irq 5 [PCSPP,EPP]
piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
lp0: using parport0 (interrupt-driven).
ppdev: user-space parallel port driver
[drm] Initialized drm 1.1.0 20060810
udevd[539]: renamed network interface eth0 to eth1
type=1400 audit(1360764162.534:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=678 comm="apparmor_parser"
type=1400 audit(1360764162.534:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=726 comm="apparmor_parser"
type=1400 audit(1360764162.534:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=678 comm="apparmor_parser"
type=1400 audit(1360764162.534:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=726 comm="apparmor_parser"
type=1400 audit(1360764162.534:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=678 comm="apparmor_parser"
type=1400 audit(1360764162.534:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=726 comm="apparmor_parser"
[drm] radeon defaulting to kernel modesetting.
[drm] radeon kernel modesetting enabled.
radeon 0000:00:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
radeon 0000:00:01.0: setting latency timer to 64
[drm] initializing kernel modesetting (SUMO 0x1002:0x964A 0x1849:0x9640).
[drm] register mmio base: 0xFEF00000
[drm] register mmio size: 262144
ATOM BIOS: General
radeon 0000:00:01.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
radeon 0000:00:01.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[drm] Detected VRAM RAM=256M, BAR=256M
[drm] RAM width 32bits DDR
[TTM] Zone  kernel: Available graphics memory: 882584 kiB.
[TTM] Initializing pool allocator.
[drm] radeon: 256M of VRAM memory ready
[drm] radeon: 512M of GTT memory ready.
[drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[drm] Driver supports precise vblank timestamp query.
radeon 0000:00:01.0: irq 42 for MSI/MSI-X
radeon 0000:00:01.0: radeon: using MSI.
[drm] radeon: irq initialized.
[drm] GART: num cpu pages 131072, num gpu pages 131072
[drm] Loading SUMO Microcode
[drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
radeon 0000:00:01.0: WB enabled
[drm] ring test succeeded in 1 usecs
[drm] radeon: ib pool ready.
[drm] ib test succeeded in 0 usecs
[drm] Radeon Display Connectors
[drm] Connector 0:
[drm]   HDMI-A
[drm]   HPD2
[drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[drm]   Encoders:
[drm]     DFP1: INTERNAL_UNIPHY2
[drm] Connector 1:
[drm]   VGA
[drm]   HPD1
[drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[drm]   Encoders:
[drm]     CRT1: INTERNAL_UNIPHY2
[drm]     CRT1: NUTMEG
[drm] Internal thermal controller without fan control
[drm] radeon: power management initialized
[drm] fb mappable at 0xC0142000
[drm] vram apper at 0xC0000000
[drm] size 7299072
[drm] fb depth is 24
[drm]    pitch is 6912
fbcon: radeondrmfb (fb0) is primary device
Console: switching to colour frame buffer device 210x65
fb0: radeondrmfb frame buffer device
drm: registered panic notifier
[drm] Initialized radeon 2.12.0 20080528 for 0000:00:01.0 on minor 0
snd_hda_intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
snd_hda_intel 0000:00:01.1: irq 43 for MSI/MSI-X
snd_hda_intel 0000:00:01.1: setting latency timer to 64
HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input4
snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
input: HD-Audio Generic Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input5
input: HD-Audio Generic Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input6
input: HD-Audio Generic Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
input: HD-Audio Generic Line-Out as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
init: failsafe main process (913) killed by TERM signal
type=1400 audit(1360764175.466:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=971 comm="apparmor_parser"
type=1400 audit(1360764175.466:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=971 comm="apparmor_parser"
type=1400 audit(1360764175.466:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=971 comm="apparmor_parser"
type=1400 audit(1360764175.506:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=970 comm="apparmor_parser"
type=1400 audit(1360764175.562:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=974 comm="apparmor_parser"
type=1400 audit(1360764175.562:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=974 comm="apparmor_parser"
type=1400 audit(1360764175.666:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=975 comm="apparmor_parser"
type=1400 audit(1360764175.666:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=975 comm="apparmor_parser"
type=1400 audit(1360764175.710:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-digikam" pid=976 comm="apparmor_parser"
type=1400 audit(1360764175.710:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-digikam///usr/sbin/mysqld" pid=976 comm="apparmor_parser"
Bluetooth: Core ver 2.16
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP socket layer initialized
Bluetooth: SCO socket layer initialized
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM ver 1.11
zram: module is from the staging directory, the quality is unknown, you have been warned.
zram: Creating 3 devices ...
Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Bluetooth: BNEP filters: protocol multicast
Adding 294192k swap on /dev/zram0.  Priority:5 extents:1 across:294192k SS
Adding 294192k swap on /dev/zram1.  Priority:5 extents:1 across:294192k SS
Adding 294192k swap on /dev/zram2.  Priority:5 extents:1 across:294192k SS
vboxdrv: Found 3 processor cores.
vboxdrv: fAsync=0 offMin=0x5e8 offMax=0x855a
vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
vboxpci: IOMMU not found (not registered)
r8169 0000:01:00.0: eth1: link down
r8169 0000:01:00.0: eth1: link down
ADDRCONF(NETDEV_UP): eth1: link is not ready
ADDRCONF(NETDEV_UP): eth1: link is not ready
r8169 0000:01:00.0: eth1: link up
ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
init: plymouth-stop pre-start process (1550) terminated with status 1
eth1: no IPv6 routers present

```

dmesg6.txt
```

Initializing cgroup subsys cpuset
Initializing cgroup subsys cpu
Linux version 3.2.0-37-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 (Ubuntu 3.2.0-37.58-generic 3.2.35)
Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=8d413c35-07e0-4d5e-b4ff-e2ee3856f4ae ro quiet splash vt.handoff=7
KERNEL supported cpus:
  Intel GenuineIntel
  AMD AuthenticAMD
  Centaur CentaurHauls
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 00000000af05f000 (usable)
 BIOS-e820: 00000000af05f000 - 00000000af0c1000 (reserved)
 BIOS-e820: 00000000af0c1000 - 00000000af18e000 (ACPI NVS)
 BIOS-e820: 00000000af18e000 - 00000000af6f6000 (reserved)
 BIOS-e820: 00000000af6f6000 - 00000000af6f7000 (usable)
 BIOS-e820: 00000000af6f7000 - 00000000af6ff000 (ACPI NVS)
 BIOS-e820: 00000000af6ff000 - 00000000afb13000 (usable)
 BIOS-e820: 00000000afb13000 - 00000000afef4000 (reserved)
 BIOS-e820: 00000000afef4000 - 00000000aff00000 (usable)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
 BIOS-e820: 00000000fed00000 - 00000000fed01000 (reserved)
 BIOS-e820: 00000000fed61000 - 00000000fed71000 (reserved)
 BIOS-e820: 00000000fed80000 - 00000000fed90000 (reserved)
 BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
 BIOS-e820: 0000000100001000 - 00000001bf000000 (usable)
NX (Execute Disable) protection: active
DMI 2.7 present.
DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./A55M-HVS, BIOS P1.40 12/04/2012
e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
No AGP bridge found
last_pfn = 0x1bf000 max_arch_pfn = 0x400000000
MTRR default type: uncachable
MTRR fixed ranges enabled:
  00000-9FFFF write-back
  A0000-BFFFF write-through
  C0000-CEFFF write-protect
  CF000-E7FFF uncachable
  E8000-FFFFF write-protect
MTRR variable ranges enabled:
  0 base 0000000000 mask FF80000000 write-back
  1 base 0080000000 mask FFC0000000 write-back
  2 base 00AFF00000 mask FFFFF00000 uncachable
  3 base 00B0000000 mask FFF0000000 uncachable
  4 disabled
  5 disabled
  6 disabled
  7 disabled
TOM2: 00000001bf000000 aka 7152M
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
original variable MTRRs
reg 0, base: 0GB, range: 2GB, type WB
reg 1, base: 2GB, range: 1GB, type WB
reg 2, base: 2815MB, range: 1MB, type UC
reg 3, base: 2816MB, range: 256MB, type UC
total RAM covered: 2815M
Found optimal setting for mtrr clean up
 gran_size: 64K 	chunk_size: 2M 	num_reg: 4  	lose cover RAM: 0G
New variable MTRRs
reg 0, base: 0GB, range: 2GB, type WB
reg 1, base: 2GB, range: 512MB, type WB
reg 2, base: 2560MB, range: 256MB, type WB
reg 3, base: 2815MB, range: 1MB, type UC
e820 update range: 00000000aff00000 - 0000000100000000 (usable) ==> (reserved)
last_pfn = 0xaff00 max_arch_pfn = 0x400000000
found SMP MP-table at [ffff8800000fd7d0] fd7d0
initial memory mapped : 0 - 20000000
Base memory trampoline at [ffff88000009a000] 9a000 size 20480
Using GB pages for direct mapping
init_memory_mapping: 0000000000000000-00000000aff00000
 0000000000 - 0080000000 page 1G
 0080000000 - 00afe00000 page 2M
 00afe00000 - 00aff00000 page 4k
kernel direct mapping tables up to aff00000 @ 1fffd000-20000000
init_memory_mapping: 0000000100001000-00000001bf000000
 0100001000 - 0100200000 page 4k
 0100200000 - 0140000000 page 2M
 0140000000 - 0180000000 page 1G
 0180000000 - 01bf000000 page 2M
kernel direct mapping tables up to 1bf000000 @ afefc000-aff00000
RAMDISK: 364ce000 - 3725f000
ACPI: RSDP 00000000000f0490 00024 (v02 ALASKA)
ACPI: XSDT 00000000af17e078 0006C (v01 ALASKA    A M I 01072009 AMI  00010013)
ACPI: FACP 00000000af184980 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
ACPI: DSDT 00000000af17e178 06803 (v02 ALASKA    A M I 00000000 INTL 20051117)
ACPI: FACS 00000000af18c080 00040
ACPI: APIC 00000000af184a90 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
ACPI: FPDT 00000000af184b08 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
ACPI: MCFG 00000000af184b50 0003C (v01 A M I  GMCH945. 01072009 MSFT 00000097)
ACPI: AAFT 00000000af184b90 00042 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
ACPI: HPET 00000000af184bd8 00038 (v01 ALASKA    A M I 01072009 AMI  00000005)
ACPI: SSDT 00000000af184c10 00AB0 (v01 AMD    POWERNOW 00000001 AMD  00000001)
ACPI: SSDT 00000000af1856c0 00695 (v02    AMD     ALIB 00000001 MSFT 04000000)
ACPI: BGRT 00000000af185d58 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
ACPI: Local APIC address 0xfee00000
No NUMA configuration found
Faking a node at 0000000000000000-00000001bf000000
Initmem setup node 0 0000000000000000-00000001bf000000
  NODE_DATA [00000001beffb000 - 00000001beffffff]
 [ffffea0000000000-ffffea0006ffffff] PMD -> [ffff8801b8a00000-ffff8801be5fffff] on node 0
Zone PFN ranges:
  DMA      0x00000010 -> 0x00001000
  DMA32    0x00001000 -> 0x00100000
  Normal   0x00100000 -> 0x001bf000
Movable zone start PFN for each node
early_node_map[6] active PFN ranges
    0: 0x00000010 -> 0x0000009f
    0: 0x00000100 -> 0x000af05f
    0: 0x000af6f6 -> 0x000af6f7
    0: 0x000af6ff -> 0x000afb13
    0: 0x000afef4 -> 0x000aff00
    0: 0x00100001 -> 0x001bf000
On node 0 totalpages: 1500174
  DMA zone: 64 pages used for memmap
  DMA zone: 5 pages reserved
  DMA zone: 3914 pages, LIFO batch:0
  DMA32 zone: 16320 pages used for memmap
  DMA32 zone: 697536 pages, LIFO batch:31
  Normal zone: 12224 pages used for memmap
  Normal zone: 770111 pages, LIFO batch:31
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Using ACPI (MADT) for SMP configuration information
ACPI: HPET id: 0xffffffff base: 0xfed00000
SMP: Allowing 4 CPUs, 1 hotplug CPUs
nr_irqs_gsi: 40
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
PM: Registered nosave memory: 00000000af05f000 - 00000000af0c1000
PM: Registered nosave memory: 00000000af0c1000 - 00000000af18e000
PM: Registered nosave memory: 00000000af18e000 - 00000000af6f6000
PM: Registered nosave memory: 00000000af6f7000 - 00000000af6ff000
PM: Registered nosave memory: 00000000afb13000 - 00000000afef4000
PM: Registered nosave memory: 00000000aff00000 - 00000000e0000000
PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
PM: Registered nosave memory: 00000000fec11000 - 00000000fed00000
PM: Registered nosave memory: 00000000fed00000 - 00000000fed01000
PM: Registered nosave memory: 00000000fed01000 - 00000000fed61000
PM: Registered nosave memory: 00000000fed61000 - 00000000fed71000
PM: Registered nosave memory: 00000000fed71000 - 00000000fed80000
PM: Registered nosave memory: 00000000fed80000 - 00000000fed90000
PM: Registered nosave memory: 00000000fed90000 - 00000000ff000000
PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
PM: Registered nosave memory: 0000000100000000 - 0000000100001000
Allocating PCI resources starting at aff00000 (gap: aff00000:30100000)
Booting paravirtualized kernel on bare hardware
setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
PERCPU: Embedded 28 pages/cpu @ffff8801bec00000 s83136 r8192 d23360 u524288
pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
pcpu-alloc: [0] 0 1 2 3 
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1471561
Policy zone: Normal
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-37-generic root=UUID=8d413c35-07e0-4d5e-b4ff-e2ee3856f4ae ro quiet splash vt.handoff=7
PID hash table entries: 4096 (order: 3, 32768 bytes)
Checking aperture...
No AGP bridge found
Calgary: detecting Calgary via BIOS EBDA area
Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Memory: 5810252k/7323648k available (6569k kernel code, 1322952k absent, 190444k reserved, 6634k data, 924k init)
SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Hierarchical RCU implementation.
	RCU dyntick-idle grace-period acceleration is enabled.
NR_IRQS:16640 nr_irqs:712 16
Extended CMOS year: 2000
spurious 8259A interrupt: IRQ7.
vt handoff: transparent VT on vt#7
Console: colour dummy device 80x25
console [tty0] enabled
allocated 48234496 bytes of page_cgroup
please try 'cgroup_disable=memory' option if you don't want memory cgroups
hpet clockevent registered
Fast TSC calibration using PIT
Detected 2096.310 MHz processor.
Calibrating delay loop (skipped), value calculated using timer frequency.. 4192.62 BogoMIPS (lpj=8385240)
pid_max: default: 32768 minimum: 301
Security Framework initialized
AppArmor: AppArmor initialized
Yama: becoming mindful.
Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Mount-cache hash table entries: 256
Initializing cgroup subsys cpuacct
Initializing cgroup subsys memory
Initializing cgroup subsys devices
Initializing cgroup subsys freezer
Initializing cgroup subsys blkio
Initializing cgroup subsys perf_event
tseg: 00aff00000
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
mce: CPU supports 6 MCE banks
ACPI: Core revision 20110623
ftrace: allocating 27033 entries in 107 pages
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
CPU0: AMD A6-3500 APU with Radeon(tm) HD Graphics stepping 00
Performance Events: AMD PMU driver.
... version:                0
... bit width:              48
... generic registers:      4
... value mask:             0000ffffffffffff
... max period:             00007fffffffffff
... fixed-purpose events:   0
... event mask:             000000000000000f
NMI watchdog enabled, takes one hw-pmu counter.
Booting Node   0, Processors  #1
smpboot cpu 1: start_ip = 9a000
NMI watchdog enabled, takes one hw-pmu counter.
 #2
smpboot cpu 2: start_ip = 9a000
NMI watchdog enabled, takes one hw-pmu counter.
Brought up 3 CPUs
Total of 3 processors activated (12577.14 BogoMIPS).
devtmpfs: initialized
EVM: security.selinux
EVM: security.SMACK64
EVM: security.capability
PM: Registering ACPI NVS region at af0c1000 (839680 bytes)
PM: Registering ACPI NVS region at af6f7000 (32768 bytes)
print_constraints: dummy: 
RTC time: 14:06:09, date: 02/13/13
NET: Registered protocol family 16
Extended Config Space enabled on 0 nodes
ACPI: bus type pci registered
Trying to unpack rootfs image as initramfs...
PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
PCI: Using configuration type 1 for base access
bio: create slab <bio-0> at 0
ACPI: Added _OSI(Module Device)
ACPI: Added _OSI(Processor Device)
ACPI: Added _OSI(3.0 _SCP Extensions)
ACPI: Added _OSI(Processor Aggregator Device)
ACPI: EC: Look up EC in DSDT
ACPI: Executed 1 blocks of module-level executable AML code
ACPI: Interpreter enabled
ACPI: (supports S0 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
ACPI: No dock devices found.
HEST: Table not found.
PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
pci_root PNP0A03:00: host bridge window [io  0x0000-0x03af]
pci_root PNP0A03:00: host bridge window [io  0x03e0-0x0cf7]
pci_root PNP0A03:00: host bridge window [io  0x03b0-0x03df]
pci_root PNP0A03:00: host bridge window [io  0x1778-0xffff]
pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xffffffff]
pci 0000:00:00.0: [1022:1705] type 0 class 0x000600
pci 0000:00:01.0: [1002:964a] type 0 class 0x000300
pci 0000:00:01.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
pci 0000:00:01.0: reg 14: [io  0xf000-0xf0ff]
pci 0000:00:01.0: reg 18: [mem 0xfef00000-0xfef3ffff]
pci 0000:00:01.0: supports D1 D2
pci 0000:00:01.1: [1002:1714] type 0 class 0x000403
pci 0000:00:01.1: reg 10: [mem 0xfef44000-0xfef47fff]
pci 0000:00:01.1: supports D1 D2
pci 0000:00:05.0: [1022:170a] type 1 class 0x000604
pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
pci 0000:00:05.0: PME# disabled
pci 0000:00:11.0: [1022:7800] type 0 class 0x000101
pci 0000:00:11.0: reg 10: [io  0xf190-0xf197]
pci 0000:00:11.0: reg 14: [io  0xf180-0xf183]
pci 0000:00:11.0: reg 18: [io  0xf170-0xf177]
pci 0000:00:11.0: reg 1c: [io  0xf160-0xf163]
pci 0000:00:11.0: reg 20: [io  0xf150-0xf15f]
pci 0000:00:11.0: reg 24: [mem 0xfef4f000-0xfef4f7ff]
pci 0000:00:11.0: set SATA to AHCI mode
pci 0000:00:12.0: [1022:7807] type 0 class 0x000c03
pci 0000:00:12.0: reg 10: [mem 0xfef4e000-0xfef4efff]
pci 0000:00:12.2: [1022:7808] type 0 class 0x000c03
pci 0000:00:12.2: reg 10: [mem 0xfef4d000-0xfef4d0ff]
pci 0000:00:12.2: supports D1 D2
pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
pci 0000:00:12.2: PME# disabled
pci 0000:00:13.0: [1022:7807] type 0 class 0x000c03
pci 0000:00:13.0: reg 10: [mem 0xfef4c000-0xfef4cfff]
pci 0000:00:13.2: [1022:7808] type 0 class 0x000c03
pci 0000:00:13.2: reg 10: [mem 0xfef4b000-0xfef4b0ff]
pci 0000:00:13.2: supports D1 D2
pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
pci 0000:00:13.2: PME# disabled
pci 0000:00:14.0: [1022:780b] type 0 class 0x000c05
pci 0000:00:14.1: [1022:780c] type 0 class 0x000101
pci 0000:00:14.1: reg 10: [io  0xf140-0xf147]
pci 0000:00:14.1: reg 14: [io  0xf130-0xf133]
pci 0000:00:14.1: reg 18: [io  0xf120-0xf127]
pci 0000:00:14.1: reg 1c: [io  0xf110-0xf113]
pci 0000:00:14.1: reg 20: [io  0xf100-0xf10f]
pci 0000:00:14.2: [1022:780d] type 0 class 0x000403
pci 0000:00:14.2: reg 10: [mem 0xfef40000-0xfef43fff 64bit]
pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
pci 0000:00:14.2: PME# disabled
pci 0000:00:14.3: [1022:780e] type 0 class 0x000601
pci 0000:00:14.4: [1022:780f] type 1 class 0x000604
pci 0000:00:14.5: [1022:7809] type 0 class 0x000c03
pci 0000:00:14.5: reg 10: [mem 0xfef4a000-0xfef4afff]
pci 0000:00:16.0: [1022:7807] type 0 class 0x000c03
pci 0000:00:16.0: reg 10: [mem 0xfef49000-0xfef49fff]
pci 0000:00:16.2: [1022:7808] type 0 class 0x000c03
pci 0000:00:16.2: reg 10: [mem 0xfef48000-0xfef480ff]
pci 0000:00:16.2: supports D1 D2
pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
pci 0000:00:16.2: PME# disabled
pci 0000:00:18.0: [1022:1700] type 0 class 0x000600
pci 0000:00:18.1: [1022:1701] type 0 class 0x000600
pci 0000:00:18.2: [1022:1702] type 0 class 0x000600
pci 0000:00:18.3: [1022:1703] type 0 class 0x000600
pci 0000:00:18.4: [1022:1704] type 0 class 0x000600
pci 0000:00:18.5: [1022:1718] type 0 class 0x000600
pci 0000:00:18.6: [1022:1716] type 0 class 0x000600
pci 0000:00:18.7: [1022:1719] type 0 class 0x000600
pci 0000:01:00.0: [10ec:8168] type 0 class 0x000200
pci 0000:01:00.0: reg 10: [io  0xe000-0xe0ff]
pci 0000:01:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
pci 0000:01:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
pci 0000:01:00.0: supports D1 D2
pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:01:00.0: PME# disabled
pci 0000:00:05.0: PCI bridge to [bus 01-01]
pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
pci 0000:00:14.4: PCI bridge to [bus 02-02] (subtractive decode)
pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
pci 0000:00:14.4:   bridge window [io  0x1778-0xffff] (subtractive decode)
pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
 pci0000:00: Requesting ACPI _OSC control (0x1d)
 pci0000:00: ACPI _OSC control (0x1c) granted
ACPI: PCI Interrupt Link [LN24] (IRQs *24)
ACPI: PCI Interrupt Link [LN25] (IRQs *25)
ACPI: PCI Interrupt Link [LN26] (IRQs *26)
ACPI: PCI Interrupt Link [LN27] (IRQs *27)
ACPI: PCI Interrupt Link [LN28] (IRQs *28)
ACPI: PCI Interrupt Link [LN29] (IRQs *29)
ACPI: PCI Interrupt Link [LN30] (IRQs *30)
ACPI: PCI Interrupt Link [LN31] (IRQs *31)
ACPI: PCI Interrupt Link [LN32] (IRQs *32)
ACPI: PCI Interrupt Link [LN33] (IRQs *33)
ACPI: PCI Interrupt Link [LN34] (IRQs *34)
ACPI: PCI Interrupt Link [LN35] (IRQs *35)
ACPI: PCI Interrupt Link [LN36] (IRQs *36)
ACPI: PCI Interrupt Link [LN37] (IRQs *37)
ACPI: PCI Interrupt Link [LN38] (IRQs *38)
ACPI: PCI Interrupt Link [LN39] (IRQs *39)
ACPI: PCI Interrupt Link [LN40] (IRQs *40)
ACPI: PCI Interrupt Link [LN41] (IRQs *41)
ACPI: PCI Interrupt Link [LN42] (IRQs *42)
ACPI: PCI Interrupt Link [LN43] (IRQs *43)
ACPI: PCI Interrupt Link [LN44] (IRQs *44)
ACPI: PCI Interrupt Link [LN45] (IRQs *45)
ACPI: PCI Interrupt Link [LN46] (IRQs *46)
ACPI: PCI Interrupt Link [LN47] (IRQs *47)
ACPI: PCI Interrupt Link [LN48] (IRQs *48)
ACPI: PCI Interrupt Link [LN49] (IRQs *49)
ACPI: PCI Interrupt Link [LN50] (IRQs *50)
ACPI: PCI Interrupt Link [LN51] (IRQs *51)
ACPI: PCI Interrupt Link [LN52] (IRQs *52)
ACPI: PCI Interrupt Link [LN53] (IRQs *53)
ACPI: PCI Interrupt Link [LN54] (IRQs *54)
ACPI: PCI Interrupt Link [LN55] (IRQs *55)
ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11 14 15) *0
ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11 14 15) *0
vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
vgaarb: loaded
vgaarb: bridge control possible 0000:00:01.0
i2c-core: driver [aat2870] using legacy suspend method
i2c-core: driver [aat2870] using legacy resume method
SCSI subsystem initialized
libata version 3.00 loaded.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
PCI: pci_cache_line_size set to 64 bytes
reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
reserve RAM buffer: 00000000af05f000 - 00000000afffffff 
reserve RAM buffer: 00000000af6f7000 - 00000000afffffff 
reserve RAM buffer: 00000000afb13000 - 00000000afffffff 
reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
reserve RAM buffer: 00000001bf000000 - 00000001bfffffff 
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Switching to clocksource hpet
AppArmor: AppArmor Filesystem Enabled
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp 00:00: [bus 00-ff]
pnp 00:00: [io  0x0cf8-0x0cff]
pnp 00:00: [io  0x0000-0x03af window]
pnp 00:00: [io  0x03e0-0x0cf7 window]
pnp 00:00: [io  0x03b0-0x03df window]
pnp 00:00: [io  0x1778-0xffff window]
pnp 00:00: [mem 0x000a0000-0x000bffff window]
pnp 00:00: [mem 0x000c0000-0x000dffff window]
pnp 00:00: [mem 0xc0000000-0xffffffff window]
pnp 00:00: [mem 0x00000000 window]
pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
pnp 00:01: [mem 0xe0000000-0xefffffff]
system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
pnp 00:02: [io  0x0010-0x001f]
pnp 00:02: [io  0x0022-0x003f]
pnp 00:02: [io  0x0063]
pnp 00:02: [io  0x0065]
pnp 00:02: [io  0x0067-0x006f]
pnp 00:02: [io  0x0072-0x007f]
pnp 00:02: [io  0x0080]
pnp 00:02: [io  0x0084-0x0086]
pnp 00:02: [io  0x0088]
pnp 00:02: [io  0x008c-0x008e]
pnp 00:02: [io  0x0090-0x009f]
pnp 00:02: [io  0x00a2-0x00bf]
pnp 00:02: [io  0x00b1]
pnp 00:02: [io  0x00e0-0x00ef]
pnp 00:02: [io  0x04d0-0x04d1]
pnp 00:02: [io  0x040b]
pnp 00:02: [io  0x04d6]
pnp 00:02: [io  0x0c00-0x0c01]
pnp 00:02: [io  0x0c14]
pnp 00:02: [io  0x0c50-0x0c51]
pnp 00:02: [io  0x0c52]
pnp 00:02: [io  0x0c6c]
pnp 00:02: [io  0x0c6f]
pnp 00:02: [io  0x0cd0-0x0cd1]
pnp 00:02: [io  0x0cd2-0x0cd3]
pnp 00:02: [io  0x0cd4-0x0cd5]
pnp 00:02: [io  0x0cd6-0x0cd7]
pnp 00:02: [io  0x0cd8-0x0cdf]
pnp 00:02: [io  0x0800-0x089f]
pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
pnp 00:02: [io  0x0000-0x000f]
pnp 00:02: [io  0x0b20-0x0b3f]
pnp 00:02: [io  0x0900-0x090f]
pnp 00:02: [io  0x0910-0x091f]
pnp 00:02: [io  0xfe00-0xfefe]
pnp 00:02: [io  0x0060-0x005f disabled]
pnp 00:02: [io  0x0064-0x0063 disabled]
pnp 00:02: [mem 0xfec00000-0xfec00fff]
pnp 00:02: [mem 0xfee00000-0xfee00fff]
pnp 00:02: [mem 0xfed80000-0xfed8ffff]
pnp 00:02: [mem 0xfed61000-0xfed70fff]
pnp 00:02: [mem 0xfec10000-0xfec10fff]
pnp 00:02: [mem 0xfed00000-0xfed00fff]
pnp 00:02: [mem 0xff000000-0xffffffff]
system 00:02: [io  0x04d0-0x04d1] has been reserved
system 00:02: [io  0x040b] has been reserved
system 00:02: [io  0x04d6] has been reserved
system 00:02: [io  0x0c00-0x0c01] has been reserved
system 00:02: [io  0x0c14] has been reserved
system 00:02: [io  0x0c50-0x0c51] has been reserved
system 00:02: [io  0x0c52] has been reserved
system 00:02: [io  0x0c6c] has been reserved
system 00:02: [io  0x0c6f] has been reserved
system 00:02: [io  0x0cd0-0x0cd1] has been reserved
system 00:02: [io  0x0cd2-0x0cd3] has been reserved
system 00:02: [io  0x0cd4-0x0cd5] has been reserved
system 00:02: [io  0x0cd6-0x0cd7] has been reserved
system 00:02: [io  0x0cd8-0x0cdf] has been reserved
system 00:02: [io  0x0800-0x089f] has been reserved
system 00:02: [io  0x0b20-0x0b3f] has been reserved
system 00:02: [io  0x0900-0x090f] has been reserved
system 00:02: [io  0x0910-0x091f] has been reserved
system 00:02: [io  0xfe00-0xfefe] has been reserved
system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
system 00:02: [mem 0xfed80000-0xfed8ffff] has been reserved
system 00:02: [mem 0xfed61000-0xfed70fff] has been reserved
system 00:02: [mem 0xfec10000-0xfec10fff] has been reserved
system 00:02: [mem 0xfed00000-0xfed00fff] has been reserved
system 00:02: [mem 0xff000000-0xffffffff] has been reserved
system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
pnp 00:03: [io  0x0290-0x029f]
pnp 00:03: [io  0x0000-0xffffffffffffffff disabled]
system 00:03: [io  0x0290-0x029f] has been reserved
system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:04: [io  0x0378-0x037f]
pnp 00:04: [io  0x0778-0x077f]
pnp 00:04: [irq 5]
pnp 00:04: [dma 3]
pnp 00:04: Plug and Play ACPI device, IDs PNP0401 (active)
pnp 00:05: [dma 4]
pnp 00:05: [io  0x0000-0x000f]
pnp 00:05: [io  0x0081-0x0083]
pnp 00:05: [io  0x0087]
pnp 00:05: [io  0x0089-0x008b]
pnp 00:05: [io  0x008f]
pnp 00:05: [io  0x00c0-0x00df]
pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
pnp 00:06: [io  0x0070-0x0071]
pnp 00:06: [irq 8]
pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
pnp 00:07: [io  0x0061]
pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
pnp 00:08: [io  0x0010-0x001f]
pnp 00:08: [io  0x0022-0x003f]
pnp 00:08: [io  0x0044-0x005f]
pnp 00:08: [io  0x0062-0x0063]
pnp 00:08: [io  0x0065-0x006f]
pnp 00:08: [io  0x0072-0x007f]
pnp 00:08: [io  0x0080]
pnp 00:08: [io  0x0084-0x0086]
pnp 00:08: [io  0x0088]
pnp 00:08: [io  0x008c-0x008e]
pnp 00:08: [io  0x0090-0x009f]
pnp 00:08: [io  0x00a2-0x00bf]
pnp 00:08: [io  0x00e0-0x00ef]
pnp 00:08: [io  0x04d0-0x04d1]
system 00:08: [io  0x04d0-0x04d1] has been reserved
system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:09: [io  0x00f0-0x00ff]
pnp 00:09: [irq 13]
pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
pnp 00:0a: [io  0x1770-0x1777]
system 00:0a: [io  0x1770-0x1777] has been reserved
system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
pnp 00:0b: [io  0x0060]
pnp 00:0b: [io  0x0064]
pnp 00:0b: [irq 1]
pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
pnp 00:0c: [io  0x03f8-0x03ff]
pnp 00:0c: [irq 4]
pnp 00:0c: [dma 0 disabled]
pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
pnp 00:0d: [mem 0xfed00000-0xfed003ff]
pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
pnp: PnP ACPI: found 14 devices
ACPI: ACPI bus type pnp unregistered
PCI: max bus depth: 1 pci_try_num: 2
pci 0000:00:05.0: PCI bridge to [bus 01-01]
pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
pci 0000:00:05.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
pci 0000:00:14.4: PCI bridge to [bus 02-02]
pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:05.0: setting latency timer to 64
pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
pci_bus 0000:00: resource 7 [io  0x1778-0xffff]
pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
pci_bus 0000:02: resource 4 [io  0x0000-0x03af]
pci_bus 0000:02: resource 5 [io  0x03e0-0x0cf7]
pci_bus 0000:02: resource 6 [io  0x03b0-0x03df]
pci_bus 0000:02: resource 7 [io  0x1778-0xffff]
pci_bus 0000:02: resource 8 [mem 0x000a0000-0x000bffff]
pci_bus 0000:02: resource 9 [mem 0x000c0000-0x000dffff]
pci_bus 0000:02: resource 10 [mem 0xc0000000-0xffffffff]
NET: Registered protocol family 2
IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
TCP: Hash tables configured (established 524288 bind 65536)
TCP reno registered
UDP hash table entries: 4096 (order: 5, 131072 bytes)
UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
NET: Registered protocol family 1
pci 0000:00:01.0: Boot video device
pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Freeing initrd memory: 13892k freed
pci 0000:00:12.0: PCI INT A disabled
pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:12.2: PCI INT B disabled
pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
pci 0000:00:13.0: PCI INT A disabled
pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:13.2: PCI INT B disabled
pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
pci 0000:00:14.5: PCI INT C disabled
pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
pci 0000:00:16.0: PCI INT A disabled
pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pci 0000:00:16.2: PCI INT B disabled
PCI: CLS 64 bytes, default 64
PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Placing 64MB software IO TLB between ffff8800ab05f000 - ffff8800af05f000
software IO TLB at phys 0xab05f000 - 0xaf05f000
perf: AMD IBS detected (0x000000ff)
audit: initializing netlink socket (disabled)
type=2000 audit(1360764369.816:1): initialized
HugeTLB registered 2 MB page size, pre-allocated 0 pages
VFS: Disk quotas dquot_6.5.2
Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
fuse init (API version 7.17)
msgmni has been set to 11375
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
pcieport 0000:00:05.0: setting latency timer to 64
pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
pcieport 0000:00:05.0: Signaling PME through PCIe PME interrupt
pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
pcie_pme 0000:00:05.0:pcie01: service driver pcie_pme loaded
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: PCI Express Hot Plug Controller Driver version: 0.4
input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
ACPI: Power Button [PWRB]
input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
ACPI: Power Button [PWRF]
ACPI: acpi_idle registered with cpuidle
ERST: Table is not found!
GHES: HEST is not enabled!
Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Linux agpgart interface v0.103
brd: module loaded
loop: module loaded
ahci 0000:00:11.0: version 3.0
ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
ahci 0000:00:11.0: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0xf impl SATA mode
ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
scsi0 : ahci
scsi1 : ahci
scsi2 : ahci
scsi3 : ahci
ata1: SATA max UDMA/133 abar m2048@0xfef4f000 port 0xfef4f100 irq 19
ata2: SATA max UDMA/133 abar m2048@0xfef4f000 port 0xfef4f180 irq 19
ata3: SATA max UDMA/133 abar m2048@0xfef4f000 port 0xfef4f200 irq 19
ata4: SATA max UDMA/133 abar m2048@0xfef4f000 port 0xfef4f280 irq 19
pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
pata_acpi 0000:00:14.1: PCI INT B disabled
Fixed MDIO Bus: probed
tun: Universal TUN/TAP device driver, 1.6
tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
PPP generic driver version 2.4.2
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
ehci_hcd 0000:00:12.2: EHCI Host Controller
ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
QUIRK: Enable AMD PLL fix
ehci_hcd 0000:00:12.2: debug port 1
ehci_hcd 0000:00:12.2: irq 17, io mem 0xfef4d000
ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 5 ports detected
ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
ehci_hcd 0000:00:13.2: EHCI Host Controller
ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
ehci_hcd 0000:00:13.2: debug port 1
ehci_hcd 0000:00:13.2: irq 17, io mem 0xfef4b000
ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 5 ports detected
ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
ehci_hcd 0000:00:16.2: EHCI Host Controller
ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
ehci_hcd 0000:00:16.2: debug port 1
ehci_hcd 0000:00:16.2: irq 17, io mem 0xfef48000
ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 4 ports detected
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:12.0: OHCI Host Controller
ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
ohci_hcd 0000:00:12.0: irq 18, io mem 0xfef4e000
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 5 ports detected
ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:13.0: OHCI Host Controller
ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
ohci_hcd 0000:00:13.0: irq 18, io mem 0xfef4c000
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 5 ports detected
ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:14.5: OHCI Host Controller
ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
ohci_hcd 0000:00:14.5: irq 18, io mem 0xfef4a000
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 2 ports detected
ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:16.0: OHCI Host Controller
ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
ohci_hcd 0000:00:16.0: irq 18, io mem 0xfef49000
hub 7-0:1.0: USB hub found
hub 7-0:1.0: 4 ports detected
uhci_hcd: USB Universal Host Controller Interface driver
usbcore: registered new interface driver libusual
i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
serio: i8042 KBD port at 0x60,0x64 irq 1
mousedev: PS/2 mouse device common for all mice
rtc_cmos 00:06: RTC can wake from S4
rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
device-mapper: uevent: version 1.0.3
device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
cpuidle: using governor ladder
cpuidle: using governor menu
EFI Variables Facility v0.08 2004-May-17
TCP cubic registered
NET: Registered protocol family 10
NET: Registered protocol family 17
Registering the dns_resolver key type
PM: Hibernation image not present or could not be loaded.
registered taskstats version 1
  Magic number: 1:500:131
acpi PNP0C02:03: hash matches
acpi device:06: hash matches
rtc_cmos 00:06: setting system clock to 2013-02-13 14:06:11 UTC (1360764371)
powernow-k8: Found 1 AMD A6-3500 APU with Radeon(tm) HD Graphics (3 cpu cores) (version 2.20.00)
powernow-k8: Core Performance Boosting: on.
powernow-k8:    0 : pstate 0 (2100 MHz)
powernow-k8:    1 : pstate 1 (1900 MHz)
powernow-k8:    2 : pstate 2 (1600 MHz)
powernow-k8:    3 : pstate 3 (1400 MHz)
powernow-k8:    4 : pstate 4 (1200 MHz)
powernow-k8:    5 : pstate 5 (1000 MHz)
powernow-k8:    6 : pstate 6 (800 MHz)
BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
EDD information not available.
input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
ata3: SATA link down (SStatus 0 SControl 300)
ata4: SATA link down (SStatus 0 SControl 300)
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata2.00: ATA-7: ST3250410AS, 4.AAA, max UDMA/133
ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
ata2.00: configured for UDMA/133
ata1.00: ATA-8: MAXTOR STM3500320AS, MX1A, max UDMA/133
ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
ata1.00: configured for UDMA/133
scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM350032 MX1A PQ: 0 ANSI: 5
sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
sd 0:0:0:0: Attached scsi generic sg0 type 0
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
scsi 1:0:0:0: Direct-Access     ATA      ST3250410AS      4.AA PQ: 0 ANSI: 5
sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: Attached scsi generic sg1 type 0
sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdb: sdb1 sdb2
sd 1:0:0:0: [sdb] Attached SCSI disk
 sda: sda1 sda2 < sda5 >
sd 0:0:0:0: [sda] Attached SCSI disk
Freeing unused kernel memory: 924k freed
Write protecting the kernel read-only data: 12288k
Freeing unused kernel memory: 1604k freed
Freeing unused kernel memory: 1196k freed
udevd[97]: starting version 175
usb 7-1: new low-speed USB device number 2 using ohci_hcd
r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
r8169 0000:01:00.0: setting latency timer to 64
r8169 0000:01:00.0: irq 41 for MSI/MSI-X
r8169 0000:01:00.0: eth0: RTL8168evl/8111evl at 0xffffc90000c76000, bc:5f:f4:46:a8:67, XID 0c900800 IRQ 41
r8169 0000:01:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
pata_atiixp 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
scsi4 : pata_atiixp
scsi5 : pata_atiixp
ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf100 irq 14
ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf108 irq 15
Refined TSC clocksource calibration: 2096.187 MHz.
Switching to clocksource tsc
input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:16.0/usb7/7-1/7-1:1.0/input/input3
generic-usb 0003:15D9:0A4C.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:16.0-1/input0
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Adding 8787548k swap on /dev/sdb2.  Priority:-1 extents:1 across:8787548k 
ADDRCONF(NETDEV_UP): eth0: link is not ready
udevd[343]: starting version 175
lp: driver loaded but no devices found
[drm] Initialized drm 1.1.0 20060810
[drm] radeon defaulting to kernel modesetting.
[drm] radeon kernel modesetting enabled.
radeon 0000:00:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
radeon 0000:00:01.0: setting latency timer to 64
parport_pc 00:04: reported by Plug and Play ACPI
parport0: PC-style at 0x378, irq 5 [PCSPP,EPP]
[drm] initializing kernel modesetting (SUMO 0x1002:0x964A 0x1849:0x9640).
[drm] register mmio base: 0xFEF00000
[drm] register mmio size: 262144
ATOM BIOS: General
radeon 0000:00:01.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
radeon 0000:00:01.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[drm] Detected VRAM RAM=256M, BAR=256M
[drm] RAM width 32bits DDR
[TTM] Zone  kernel: Available graphics memory: 2913934 kiB.
[TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[TTM] Initializing pool allocator.
[drm] radeon: 256M of VRAM memory ready
[drm] radeon: 512M of GTT memory ready.
[drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[drm] Driver supports precise vblank timestamp query.
radeon 0000:00:01.0: irq 42 for MSI/MSI-X
radeon 0000:00:01.0: radeon: using MSI.
[drm] radeon: irq initialized.
[drm] GART: num cpu pages 131072, num gpu pages 131072
[drm] Loading SUMO Microcode
udevd[467]: renamed network interface eth0 to eth1
lp0: using parport0 (interrupt-driven).
type=1400 audit(1360764384.830:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=727 comm="apparmor_parser"
type=1400 audit(1360764384.830:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=738 comm="apparmor_parser"
type=1400 audit(1360764384.830:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=727 comm="apparmor_parser"
type=1400 audit(1360764384.830:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=738 comm="apparmor_parser"
type=1400 audit(1360764384.830:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=727 comm="apparmor_parser"
type=1400 audit(1360764384.830:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=738 comm="apparmor_parser"
ppdev: user-space parallel port driver
[drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
radeon 0000:00:01.0: WB enabled
[drm] ring test succeeded in 1 usecs
[drm] radeon: ib pool ready.
[drm] ib test succeeded in 0 usecs
[drm] Radeon Display Connectors
[drm] Connector 0:
[drm]   HDMI-A
[drm]   HPD2
[drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[drm]   Encoders:
[drm]     DFP1: INTERNAL_UNIPHY2
[drm] Connector 1:
[drm]   VGA
[drm]   HPD1
[drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[drm]   Encoders:
[drm]     CRT1: INTERNAL_UNIPHY2
[drm]     CRT1: NUTMEG
[drm] Internal thermal controller without fan control
[drm] radeon: power management initialized
[drm] fb mappable at 0xC0142000
[drm] vram apper at 0xC0000000
[drm] size 7299072
[drm] fb depth is 24
[drm]    pitch is 6912
fbcon: radeondrmfb (fb0) is primary device
Console: switching to colour frame buffer device 210x65
fb0: radeondrmfb frame buffer device
drm: registered panic notifier
[drm] Initialized radeon 2.12.0 20080528 for 0000:00:01.0 on minor 0
piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
snd_hda_intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
snd_hda_intel 0000:00:01.1: irq 43 for MSI/MSI-X
snd_hda_intel 0000:00:01.1: setting latency timer to 64
HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input4
snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
input: HD-Audio Generic Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input5
input: HD-Audio Generic Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input6
input: HD-Audio Generic Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
input: HD-Audio Generic Line-Out as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
init: failsafe main process (917) killed by TERM signal
Bluetooth: Core ver 2.16
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP socket layer initialized
Bluetooth: SCO socket layer initialized
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM ver 1.11
Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Bluetooth: BNEP filters: protocol multicast
type=1400 audit(1360764387.826:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=992 comm="apparmor_parser"
type=1400 audit(1360764387.830:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=992 comm="apparmor_parser"
type=1400 audit(1360764387.854:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1022 comm="apparmor_parser"
type=1400 audit(1360764387.854:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1021 comm="apparmor_parser"
r8169 0000:01:00.0: eth1: link down
r8169 0000:01:00.0: eth1: link down
ADDRCONF(NETDEV_UP): eth1: link is not ready
ADDRCONF(NETDEV_UP): eth1: link is not ready
zram: module is from the staging directory, the quality is unknown, you have been warned.
zram: Creating 3 devices ...
Adding 971308k swap on /dev/zram0.  Priority:5 extents:1 across:971308k SS
Adding 971308k swap on /dev/zram1.  Priority:5 extents:1 across:971308k SS
Adding 971308k swap on /dev/zram2.  Priority:5 extents:1 across:971308k SS
vboxdrv: Found 3 processor cores.
vboxdrv: fAsync=0 offMin=0x362 offMax=0x1652
vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
vboxpci: IOMMU not found (not registered)
r8169 0000:01:00.0: eth1: link up
ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
eth1: no IPv6 routers present

```

diff dmesg2.txt dmesg6.txt
```

13,21c13,21
<  BIOS-e820: 0000000000100000 - 000000006e05f000 (usable)
<  BIOS-e820: 000000006e05f000 - 000000006e0c1000 (reserved)
<  BIOS-e820: 000000006e0c1000 - 000000006e18e000 (ACPI NVS)
<  BIOS-e820: 000000006e18e000 - 000000006e6f6000 (reserved)
<  BIOS-e820: 000000006e6f6000 - 000000006e6f7000 (usable)
<  BIOS-e820: 000000006e6f7000 - 000000006e6ff000 (ACPI NVS)
<  BIOS-e820: 000000006e6ff000 - 000000006eb13000 (usable)
<  BIOS-e820: 000000006eb13000 - 000000006eef4000 (reserved)
<  BIOS-e820: 000000006eef4000 - 000000006ef00000 (usable)
---
>  BIOS-e820: 0000000000100000 - 00000000af05f000 (usable)
>  BIOS-e820: 00000000af05f000 - 00000000af0c1000 (reserved)
>  BIOS-e820: 00000000af0c1000 - 00000000af18e000 (ACPI NVS)
>  BIOS-e820: 00000000af18e000 - 00000000af6f6000 (reserved)
>  BIOS-e820: 00000000af6f6000 - 00000000af6f7000 (usable)
>  BIOS-e820: 00000000af6f7000 - 00000000af6ff000 (ACPI NVS)
>  BIOS-e820: 00000000af6ff000 - 00000000afb13000 (usable)
>  BIOS-e820: 00000000afb13000 - 00000000afef4000 (reserved)
>  BIOS-e820: 00000000afef4000 - 00000000aff00000 (usable)
28a29
>  BIOS-e820: 0000000100001000 - 00000001bf000000 (usable)
35c36
< last_pfn = 0x6ef00 max_arch_pfn = 0x400000000
---
> last_pfn = 0x1bf000 max_arch_pfn = 0x400000000
45,47c46,48
<   1 base 006EF00000 mask FFFFF00000 uncachable
<   2 base 006F000000 mask FFFF000000 uncachable
<   3 base 0070000000 mask FFF0000000 uncachable
---
>   1 base 0080000000 mask FFC0000000 write-back
>   2 base 00AFF00000 mask FFFFF00000 uncachable
>   3 base 00B0000000 mask FFF0000000 uncachable
51a53
> TOM2: 00000001bf000000 aka 7152M
55,58c57,60
< reg 1, base: 1775MB, range: 1MB, type UC
< reg 2, base: 1776MB, range: 16MB, type UC
< reg 3, base: 1792MB, range: 256MB, type UC
< total RAM covered: 1775M
---
> reg 1, base: 2GB, range: 1GB, type WB
> reg 2, base: 2815MB, range: 1MB, type UC
> reg 3, base: 2816MB, range: 256MB, type UC
> total RAM covered: 2815M
60c62
<  gran_size: 64K 	chunk_size: 512M 	num_reg: 4  	lose cover RAM: 0G
---
>  gran_size: 64K 	chunk_size: 2M 	num_reg: 4  	lose cover RAM: 0G
63,65c65,69
< reg 1, base: 1775MB, range: 1MB, type UC
< reg 2, base: 1776MB, range: 16MB, type UC
< reg 3, base: 1792MB, range: 256MB, type UC
---
> reg 1, base: 2GB, range: 512MB, type WB
> reg 2, base: 2560MB, range: 256MB, type WB
> reg 3, base: 2815MB, range: 1MB, type UC
> e820 update range: 00000000aff00000 - 0000000100000000 (usable) ==> (reserved)
> last_pfn = 0xaff00 max_arch_pfn = 0x400000000
70,74c74,84
< init_memory_mapping: 0000000000000000-000000006ef00000
<  0000000000 - 0040000000 page 1G
<  0040000000 - 006ee00000 page 2M
<  006ee00000 - 006ef00000 page 4k
< kernel direct mapping tables up to 6ef00000 @ 1fffd000-20000000
---
> init_memory_mapping: 0000000000000000-00000000aff00000
>  0000000000 - 0080000000 page 1G
>  0080000000 - 00afe00000 page 2M
>  00afe00000 - 00aff00000 page 4k
> kernel direct mapping tables up to aff00000 @ 1fffd000-20000000
> init_memory_mapping: 0000000100001000-00000001bf000000
>  0100001000 - 0100200000 page 4k
>  0100200000 - 0140000000 page 2M
>  0140000000 - 0180000000 page 1G
>  0180000000 - 01bf000000 page 2M
> kernel direct mapping tables up to 1bf000000 @ afefc000-aff00000
77,78c87,88
< ACPI: XSDT 000000006e17e078 0006C (v01 ALASKA    A M I 01072009 AMI  00010013)
< ACPI: FACP 000000006e184980 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
---
> ACPI: XSDT 00000000af17e078 0006C (v01 ALASKA    A M I 01072009 AMI  00010013)
> ACPI: FACP 00000000af184980 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
81,90c91,100
< ACPI: DSDT 000000006e17e178 06803 (v02 ALASKA    A M I 00000000 INTL 20051117)
< ACPI: FACS 000000006e18c080 00040
< ACPI: APIC 000000006e184a90 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
< ACPI: FPDT 000000006e184b08 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
< ACPI: MCFG 000000006e184b50 0003C (v01 A M I  GMCH945. 01072009 MSFT 00000097)
< ACPI: AAFT 000000006e184b90 00042 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
< ACPI: HPET 000000006e184bd8 00038 (v01 ALASKA    A M I 01072009 AMI  00000005)
< ACPI: SSDT 000000006e184c10 00AB0 (v01 AMD    POWERNOW 00000001 AMD  00000001)
< ACPI: SSDT 000000006e1856c0 00695 (v02    AMD     ALIB 00000001 MSFT 04000000)
< ACPI: BGRT 000000006e185d58 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
---
> ACPI: DSDT 00000000af17e178 06803 (v02 ALASKA    A M I 00000000 INTL 20051117)
> ACPI: FACS 00000000af18c080 00040
> ACPI: APIC 00000000af184a90 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
> ACPI: FPDT 00000000af184b08 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
> ACPI: MCFG 00000000af184b50 0003C (v01 A M I  GMCH945. 01072009 MSFT 00000097)
> ACPI: AAFT 00000000af184b90 00042 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
> ACPI: HPET 00000000af184bd8 00038 (v01 ALASKA    A M I 01072009 AMI  00000005)
> ACPI: SSDT 00000000af184c10 00AB0 (v01 AMD    POWERNOW 00000001 AMD  00000001)
> ACPI: SSDT 00000000af1856c0 00695 (v02    AMD     ALIB 00000001 MSFT 04000000)
> ACPI: BGRT 00000000af185d58 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
93,96c103,106
< Faking a node at 0000000000000000-000000006ef00000
< Initmem setup node 0 0000000000000000-000000006ef00000
<   NODE_DATA [000000006eefb000 - 000000006eefffff]
<  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88006c000000-ffff88006dbfffff] on node 0
---
> Faking a node at 0000000000000000-00000001bf000000
> Initmem setup node 0 0000000000000000-00000001bf000000
>   NODE_DATA [00000001beffb000 - 00000001beffffff]
>  [ffffea0000000000-ffffea0006ffffff] PMD -> [ffff8801b8a00000-ffff8801be5fffff] on node 0
100c110
<   Normal   empty
---
>   Normal   0x00100000 -> 0x001bf000
102c112
< early_node_map[5] active PFN ranges
---
> early_node_map[6] active PFN ranges
104,108c114,119
<     0: 0x00000100 -> 0x0006e05f
<     0: 0x0006e6f6 -> 0x0006e6f7
<     0: 0x0006e6ff -> 0x0006eb13
<     0: 0x0006eef4 -> 0x0006ef00
< On node 0 totalpages: 451599
---
>     0: 0x00000100 -> 0x000af05f
>     0: 0x000af6f6 -> 0x000af6f7
>     0: 0x000af6ff -> 0x000afb13
>     0: 0x000afef4 -> 0x000aff00
>     0: 0x00100001 -> 0x001bf000
> On node 0 totalpages: 1500174
112,113c123,126
<   DMA32 zone: 7036 pages used for memmap
<   DMA32 zone: 440580 pages, LIFO batch:31
---
>   DMA32 zone: 16320 pages used for memmap
>   DMA32 zone: 697536 pages, LIFO batch:31
>   Normal zone: 12224 pages used for memmap
>   Normal zone: 770111 pages, LIFO batch:31
135,140c148,168
< PM: Registered nosave memory: 000000006e05f000 - 000000006e0c1000
< PM: Registered nosave memory: 000000006e0c1000 - 000000006e18e000
< PM: Registered nosave memory: 000000006e18e000 - 000000006e6f6000
< PM: Registered nosave memory: 000000006e6f7000 - 000000006e6ff000
< PM: Registered nosave memory: 000000006eb13000 - 000000006eef4000
< Allocating PCI resources starting at 6ef00000 (gap: 6ef00000:71100000)
---
> PM: Registered nosave memory: 00000000af05f000 - 00000000af0c1000
> PM: Registered nosave memory: 00000000af0c1000 - 00000000af18e000
> PM: Registered nosave memory: 00000000af18e000 - 00000000af6f6000
> PM: Registered nosave memory: 00000000af6f7000 - 00000000af6ff000
> PM: Registered nosave memory: 00000000afb13000 - 00000000afef4000
> PM: Registered nosave memory: 00000000aff00000 - 00000000e0000000
> PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
> PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
> PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
> PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
> PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
> PM: Registered nosave memory: 00000000fec11000 - 00000000fed00000
> PM: Registered nosave memory: 00000000fed00000 - 00000000fed01000
> PM: Registered nosave memory: 00000000fed01000 - 00000000fed61000
> PM: Registered nosave memory: 00000000fed61000 - 00000000fed71000
> PM: Registered nosave memory: 00000000fed71000 - 00000000fed80000
> PM: Registered nosave memory: 00000000fed80000 - 00000000fed90000
> PM: Registered nosave memory: 00000000fed90000 - 00000000ff000000
> PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
> PM: Registered nosave memory: 0000000100000000 - 0000000100001000
> Allocating PCI resources starting at aff00000 (gap: aff00000:30100000)
143c171
< PERCPU: Embedded 28 pages/cpu @ffff88006e800000 s83136 r8192 d23360 u524288
---
> PERCPU: Embedded 28 pages/cpu @ffff8801bec00000 s83136 r8192 d23360 u524288
146,147c174,175
< Built 1 zonelists in Node order, mobility grouping on.  Total pages: 444494
< Policy zone: DMA32
---
> Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1471561
> Policy zone: Normal
154c182
< Memory: 1747552k/1817600k available (6569k kernel code, 11204k absent, 58844k reserved, 6634k data, 924k init)
---
> Memory: 5810252k/7323648k available (6569k kernel code, 1322952k absent, 190444k reserved, 6634k data, 924k init)
164c192
< allocated 14680064 bytes of page_cgroup
---
> allocated 48234496 bytes of page_cgroup
168,169c196,197
< Detected 2096.211 MHz processor.
< Calibrating delay loop (skipped), value calculated using timer frequency.. 4192.42 BogoMIPS (lpj=8384844)
---
> Detected 2096.310 MHz processor.
> Calibrating delay loop (skipped), value calculated using timer frequency.. 4192.62 BogoMIPS (lpj=8385240)
174,175c202,203
< Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
< Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
---
> Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
> Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
183c211
< tseg: 006ef00000
---
> tseg: 00aff00000
207c235
< Total of 3 processors activated (12576.95 BogoMIPS).
---
> Total of 3 processors activated (12577.14 BogoMIPS).
212,213c240,241
< PM: Registering ACPI NVS region at 6e0c1000 (839680 bytes)
< PM: Registering ACPI NVS region at 6e6f7000 (32768 bytes)
---
> PM: Registering ACPI NVS region at af0c1000 (839680 bytes)
> PM: Registering ACPI NVS region at af6f7000 (32768 bytes)
215c243
< RTC time: 14:02:35, date: 02/13/13
---
> RTC time: 14:06:09, date: 02/13/13
218a247
> Trying to unpack rootfs image as initramfs...
221d249
< Trying to unpack rootfs image as initramfs...
243c271
< pci_root PNP0A03:00: host bridge window [mem 0x7f000000-0xffffffff]
---
> pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xffffffff]
325c353
< pci 0000:00:14.4:   bridge window [mem 0x7f000000-0xffffffff] (subtractive decode)
---
> pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
383,386c411,415
< reserve RAM buffer: 000000006e05f000 - 000000006fffffff 
< reserve RAM buffer: 000000006e6f7000 - 000000006fffffff 
< reserve RAM buffer: 000000006eb13000 - 000000006fffffff 
< reserve RAM buffer: 000000006ef00000 - 000000006fffffff 
---
> reserve RAM buffer: 00000000af05f000 - 00000000afffffff 
> reserve RAM buffer: 00000000af6f7000 - 00000000afffffff 
> reserve RAM buffer: 00000000afb13000 - 00000000afffffff 
> reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
> reserve RAM buffer: 00000001bf000000 - 00000001bfffffff 
405c434
< pnp 00:00: [mem 0x7f000000-0xffffffff window]
---
> pnp 00:00: [mem 0xc0000000-0xffffffff window]
552c581
< pci_bus 0000:00: resource 10 [mem 0x7f000000-0xffffffff]
---
> pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
561c590
< pci_bus 0000:02: resource 10 [mem 0x7f000000-0xffffffff]
---
> pci_bus 0000:02: resource 10 [mem 0xc0000000-0xffffffff]
563,564c592,593
< IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
< TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
---
> IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
> TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
566c595
< TCP: Hash tables configured (established 262144 bind 65536)
---
> TCP: Hash tables configured (established 524288 bind 65536)
568,569c597,598
< UDP hash table entries: 1024 (order: 3, 32768 bytes)
< UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
---
> UDP hash table entries: 4096 (order: 5, 131072 bytes)
> UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
587a617,619
> PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
> Placing 64MB software IO TLB between ffff8800ab05f000 - ffff8800af05f000
> software IO TLB at phys 0xab05f000 - 0xaf05f000
590c622
< type=2000 audit(1360764155.820:1): initialized
---
> type=2000 audit(1360764369.816:1): initialized
595c627
< msgmni has been set to 3440
---
> msgmni has been set to 11375
712,713c744,747
<   Magic number: 1:397:30
< rtc_cmos 00:06: setting system clock to 2013-02-13 14:02:36 UTC (1360764156)
---
>   Magic number: 1:500:131
> acpi PNP0C02:03: hash matches
> acpi device:06: hash matches
> rtc_cmos 00:06: setting system clock to 2013-02-13 14:06:11 UTC (1360764371)
728d761
< ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
729a763
> ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
743d776
< sd 1:0:0:0: Attached scsi generic sg1 type 0
745a779
> sd 1:0:0:0: Attached scsi generic sg1 type 0
748,749d781
<  sda: sda1 sda2 < sda5 >
< sd 0:0:0:0: [sda] Attached SCSI disk
751a784,785
>  sda: sda1 sda2 < sda5 >
> sd 0:0:0:0: [sda] Attached SCSI disk
756a791
> usb 7-1: new low-speed USB device number 2 using ohci_hcd
761c796
< r8169 0000:01:00.0: eth0: RTL8168evl/8111evl at 0xffffc90000316000, bc:5f:f4:46:a8:67, XID 0c900800 IRQ 41
---
> r8169 0000:01:00.0: eth0: RTL8168evl/8111evl at 0xffffc90000c76000, bc:5f:f4:46:a8:67, XID 0c900800 IRQ 41
763d797
< usb 7-1: new low-speed USB device number 2 using ohci_hcd
768a803,804
> Refined TSC clocksource calibration: 2096.187 MHz.
> Switching to clocksource tsc
773,774d808
< Refined TSC clocksource calibration: 2096.187 MHz.
< Switching to clocksource tsc
778c812
< udevd[439]: starting version 175
---
> udevd[343]: starting version 175
780,784d813
< parport_pc 00:04: reported by Plug and Play ACPI
< parport0: PC-style at 0x378, irq 5 [PCSPP,EPP]
< piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
< lp0: using parport0 (interrupt-driven).
< ppdev: user-space parallel port driver
786,792d814
< udevd[539]: renamed network interface eth0 to eth1
< type=1400 audit(1360764162.534:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=678 comm="apparmor_parser"
< type=1400 audit(1360764162.534:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=726 comm="apparmor_parser"
< type=1400 audit(1360764162.534:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=678 comm="apparmor_parser"
< type=1400 audit(1360764162.534:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=726 comm="apparmor_parser"
< type=1400 audit(1360764162.534:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=678 comm="apparmor_parser"
< type=1400 audit(1360764162.534:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=726 comm="apparmor_parser"
796a819,820
> parport_pc 00:04: reported by Plug and Play ACPI
> parport0: PC-style at 0x378, irq 5 [PCSPP,EPP]
805c829,830
< [TTM] Zone  kernel: Available graphics memory: 882584 kiB.
---
> [TTM] Zone  kernel: Available graphics memory: 2913934 kiB.
> [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
815a841,849
> udevd[467]: renamed network interface eth0 to eth1
> lp0: using parport0 (interrupt-driven).
> type=1400 audit(1360764384.830:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=727 comm="apparmor_parser"
> type=1400 audit(1360764384.830:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=738 comm="apparmor_parser"
> type=1400 audit(1360764384.830:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=727 comm="apparmor_parser"
> type=1400 audit(1360764384.830:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=738 comm="apparmor_parser"
> type=1400 audit(1360764384.830:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=727 comm="apparmor_parser"
> type=1400 audit(1360764384.830:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=738 comm="apparmor_parser"
> ppdev: user-space parallel port driver
846a881
> piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
860,870c895
< init: failsafe main process (913) killed by TERM signal
< type=1400 audit(1360764175.466:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=971 comm="apparmor_parser"
< type=1400 audit(1360764175.466:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=971 comm="apparmor_parser"
< type=1400 audit(1360764175.466:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=971 comm="apparmor_parser"
< type=1400 audit(1360764175.506:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=970 comm="apparmor_parser"
< type=1400 audit(1360764175.562:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=974 comm="apparmor_parser"
< type=1400 audit(1360764175.562:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=974 comm="apparmor_parser"
< type=1400 audit(1360764175.666:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=975 comm="apparmor_parser"
< type=1400 audit(1360764175.666:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=975 comm="apparmor_parser"
< type=1400 audit(1360764175.710:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-digikam" pid=976 comm="apparmor_parser"
< type=1400 audit(1360764175.710:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-digikam///usr/sbin/mysqld" pid=976 comm="apparmor_parser"
---
> init: failsafe main process (917) killed by TERM signal
880,881d904
< zram: module is from the staging directory, the quality is unknown, you have been warned.
< zram: Creating 3 devices ...
884,891c907,910
< Adding 294192k swap on /dev/zram0.  Priority:5 extents:1 across:294192k SS
< Adding 294192k swap on /dev/zram1.  Priority:5 extents:1 across:294192k SS
< Adding 294192k swap on /dev/zram2.  Priority:5 extents:1 across:294192k SS
< vboxdrv: Found 3 processor cores.
< vboxdrv: fAsync=0 offMin=0x5e8 offMax=0x855a
< vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
< vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
< vboxpci: IOMMU not found (not registered)
---
> type=1400 audit(1360764387.826:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=992 comm="apparmor_parser"
> type=1400 audit(1360764387.830:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=992 comm="apparmor_parser"
> type=1400 audit(1360764387.854:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1022 comm="apparmor_parser"
> type=1400 audit(1360764387.854:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1021 comm="apparmor_parser"
895a915,924
> zram: module is from the staging directory, the quality is unknown, you have been warned.
> zram: Creating 3 devices ...
> Adding 971308k swap on /dev/zram0.  Priority:5 extents:1 across:971308k SS
> Adding 971308k swap on /dev/zram1.  Priority:5 extents:1 across:971308k SS
> Adding 971308k swap on /dev/zram2.  Priority:5 extents:1 across:971308k SS
> vboxdrv: Found 3 processor cores.
> vboxdrv: fAsync=0 offMin=0x362 offMax=0x1652
> vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
> vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
> vboxpci: IOMMU not found (not registered)
898d926
< init: plymouth-stop pre-start process (1550) terminated with status 1

```

---

### Post by Yellow Pasque on 2013-02-15
It looks like the BIOS isn't reporting the full memory map in the 2GB example. It lacks the line:
```
BIOS-e820: 0000000100001000 - 00000001bf000000 (usable)
```

I'm not sure what that means (suspecting a buggy BIOS).

---

### Post by Yellow Pasque on 2013-02-15
Another idea: try turning off the "Xfast RAM" in your BIOS/UEFI

---

### Post by tuberculo on 2013-02-18
> **Temüjin said:**
> Another idea: try turning off the "Xfast RAM" in your BIOS/UEFI

I could not find that option or anything similar to that.

---

