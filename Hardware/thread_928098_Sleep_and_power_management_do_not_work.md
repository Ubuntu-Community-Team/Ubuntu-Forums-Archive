---
title: "Sleep and power management do not work"
date: 2008-09-23
forum: Hardware
---

### Post by xubcel on 2008-09-23
Hello.  I have installed Xubuntu 3 times but:

The display will sleep but the rest of the system will not sleep even after implementing Powertop suggestions.

Xubuntu is too power-hungry at idle (depletes battery 50% faster than Vista does) and no power-management attempts seems to change anything.

I have tweaked computers but I am new to Linux/Xubuntu (some advice seems to skip steps or not say what to do when advice generates errors).

I know that the Celeron 540 does not powerstep but both CPU and chipset are "mobile" (and some sources list M 540 as "stepping: a1") and I would appreciate knowing what I can do to replicate Vista's better idle performance.

Thank you.


System:


> Ubuntu 8.04.1 (boot screens alternate between "Xubuntu" and "Ubuntu")

2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux





cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 22
model name	: Intel(R) Celeron(R) CPU          540  @ 1.86GHz
stepping	: 1
cpu MHz		: 1862.035
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3728.29
clflush size	: 64



00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff00]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information





 dmidecode 2.9
SMBIOS 2.4 present.
22 structures occupying 1153 bytes.
Table at 0x000DC010.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: TOSHIBA
	Version: V2.50
	Release Date: 06/11/2008
	Address: 0xE5690
	Runtime Size: 108912 bytes
	ROM Size: 64 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		ACPI is supported
		USB legacy is supported
		AGP is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 2.80
	Firmware Revision: 2.80

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: TOSHIBA
	Product Name: Satellite A205
	Version: PSAE3U-07Y023
	Serial Number: 
	UUID: 4BFA6DD7-1E8A-11DD-8D72-001EEC391E99
	Wake-up Type: Power Switch
	SKU Number: 012345678912345678912345678
	Family: ABCDEFGHIJKLMNOPQRSTUVWXYZ

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: TOSHIBA
	Product Name: ISKAA
	Version: 1.00
	Serial Number: 

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: TOSHIBA
	Type: Notebook
	Lock: Not Present
	Version: N/A
	Serial Number: None
	Asset Tag: *
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: U2E1
	Type: Central Processor
	Family: Other
	Manufacturer: Intel
	ID: 61 06 01 00 FF FB EB AF
	Version: CPU Version
	Voltage: 3.3 V
	External Clock: Unknown
	Max Speed: 4096 MHz
	Current Speed: 1860 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

---

### Post by eldragon on 2008-09-29
ok, this is not exactly what you might be looking for. but there is a thread concerning a dell xps notebook that deals with power management and gives many advices on how to improve (or even beat windows's) battery life

check it here: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

there are several things you can tweak. maybe doing a lspci will give you more info on what you got in the laptop and see what really applies to you or not.


good luck

---

### Post by xubcel on 2008-09-29
Thank you, eldragon, I will look.

---

