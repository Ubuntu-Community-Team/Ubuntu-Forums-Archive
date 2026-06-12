---
title: "Overclocking via BIOS null after loading"
date: 2016-02-05
forum: Hardware
---

### Post by Fredo_p on 2016-02-05
No matter what I try, I can't get the settings that I have in my UGuru to stay when Ubuntu loads. I've core the freq and voltage set to what I want but it all gets set to what ever cpufreq's ondemand settings are (I think 3.02). When I run cpupower, it says the max freq that can be achieved is 3.02 even though I'm OCing at 3.78. I have never had any luck using cpufreq or cpupower. I've spent a few hours trying to figure out how to use them and locate files that site recommend I change but don't exist.

Is there any way for Ubuntu to be able to recognize what the settings are in BIOS via UGuru and not have them be some lower default? I'm running a hand built tower and not a laptop.

[B]_SPECS_
Mobo:[/B]   Abit IP35 Pro
**CPU:    **&#8203;[COLOR=#545454][FONT=arial]Intel Core 2 Duo Processor [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**E6750**[/FONT][/COLOR][COLOR=#545454][FONT=arial] (4M Cache, 2.66 GHz, 1333 MHz FSB)
 
----------------------------------------------------------------------------------------------------------
[/FONT][/COLOR]
# dmidecode 2.12
SMBIOS 2.5 present.


Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
........Vendor: Phoenix Technologies, LTD
........Version: 6.00 PG
........Release Date: 05/26/2008
........Address: 0xE0000
........Runtime Size: 128 kB
........ROM Size: 1024 kB
........Characteristics:
................ISA is supported
................PCI is supported
................PNP is supported
................APM is supported
................BIOS is upgradeable
................BIOS shadowing is allowed
................Boot from CD is supported
................Selectable boot is supported
................BIOS ROM is socketed
................EDD is supported
................5.25"/360 kB floppy services are supported (int 13h)
................5.25"/1.2 MB floppy services are supported (int 13h)
................3.5"/720 kB floppy services are supported (int 13h)
................3.5"/2.88 MB floppy services are supported (int 13h)
................Print screen service is supported (int 5h)
................8042 keyboard services are supported (int 9h)
................Serial services are supported (int 14h)
................Printer services are supported (int 17h)
................CGA/mono video services are supported (int 10h)
................ACPI is supported
................USB legacy is supported
................LS-120 boot is supported
................ATAPI Zip drive boot is supported
................BIOS boot specification is supported
................Targeted content distribution is supported


Handle 0x0002, DMI type 2, 10 bytes
Base Board Information
........Manufacturer: [http://www.abit.com.tw/](http://www.abit.com.tw/)
........Product Name: IP35 Pro(Intel P35-ICH9R)
........Version: 1.0
........Serial Number:  
........Asset Tag:  
........Features:
................Board is a hosting board


Handle 0x0004, DMI type 4, 40 bytes
Processor Information
........Socket Designation: Socket 775
........Type: Central Processor
........Family: Other
........Manufacturer: Intel
........ID: FB 06 00 00 FF FB EB BF
........Signature: Type 0, Family 6, Model 15, Stepping 11
........Flags:
................FPU (Floating-point unit on-chip)
................VME (Virtual mode extension)
................DE (Debugging extension)
................PSE (Page size extension)
................TSC (Time stamp counter)
................MSR (Model specific registers)
................PAE (Physical address extension)
................MCE (Machine check exception)
................CX8 (CMPXCHG8 instruction supported)
................APIC (On-chip APIC hardware supported)
................SEP (Fast system call)
................MTRR (Memory type range registers)
................PGE (Page global enable)
................MCA (Machine check architecture)
................CMOV (Conditional move instruction supported)
................PAT (Page attribute table)
................PSE-36 (36-bit page size extension)
................CLFSH (CLFLUSH instruction supported)
................DS (Debug store)
................ACPI (ACPI supported)
................MMX (MMX technology supported)
................FXSR (FXSAVE and FXSTOR instructions supported)
................SSE (Streaming SIMD extensions)
................SSE2 (Streaming SIMD extensions 2)
................SS (Self-snoop)
................HTT (Multi-threading)
................TM (Thermal monitor supported)
................PBE (Pending break enabled)
........Version: Intel(R) Core(TM)2 Duo
........Voltage: 0.0 V
........External Clock: 378 MHz
........Max Speed: 4000 MHz
........Current Speed: 3024 MHz
........Status: Populated, Enabled
........Upgrade: ZIF Socket
........L1 Cache Handle: 0x000A
........L2 Cache Handle: 0x000B
........L3 Cache Handle: Not Provided
........Serial Number:  
........Asset Tag:  
........Part Number:  
........Characteristics: None


Handle 0x0013, DMI type 13, 22 bytes
BIOS Language Information
........Language Description Format: Long
........Installable Languages: 3
................n|US|iso8859-1
................n|US|iso8859-1
................r|CA|iso8859-1
........Currently Installed Language: n|US|iso8859-1

# dmidecode 2.12
SMBIOS 2.5 present.
------------------------------------------------------------------------------------
**$ cpupower frequency-info**
analyzing CPU 0:
..driver: acpi-cpufreq
..CPUs which run at the same hardware frequency: 0
..CPUs which need to have their frequency coordinated by software: 0
..maximum transition latency: 10.0 us.
..hardware limits: 2.27 GHz - 3.02 GHz
..available frequency steps: 3.02 GHz, 2.27 GHz
..available cpufreq governors: conservative, ondemand, userspace, powersave, performance
..current policy: frequency should be within 2.27 GHz and 3.02 GHz.
.................The governor "ondemand" may decide which speed to use
.................within this range.
..current CPU frequency is 2.27 GHz.
..cpufreq stats: 3.02 GHz:28.29%, 2.27 GHz:71.71%  (104907)
..boost state support:
....Supported: no
....Active: no

---

