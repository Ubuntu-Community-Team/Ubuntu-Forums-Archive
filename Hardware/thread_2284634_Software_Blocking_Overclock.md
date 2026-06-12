---
title: "Software Blocking Overclock?"
date: 2015-06-30
forum: Hardware
---

### Post by jordanmrodriguez on 2015-06-30
Hello Ubuntu Hivemind!!

I've recently built my first custom computer and installed Ubuntu Gnome Shell.

I have an i5-4690k CPU which is unlockable and overclockable.

It has a turbo boost to 4.0Ghz and I was hoping to overclock it to 4.3Ghz (something simple).

Whenever I adjusted my overclock in BIOS it showed no effect towards my CPU speeds once I booted into Ubuntu. I've used several tools to measure my CPU and they all read around 3.9Ghz. I also see a file that shows me a "Hardware Limit" of 3.9.

Now I wanted to test to see if Ubuntu had something in there that was overriding my BIOS settings so I underclocked my CPU in BIOS. I set the multiplier to 25 showing a CPU clock speed of 2.5Ghz.

This also had NO effect once I booted into Ubuntu, all of my benchmarks showed 3.9.

Is there any software I should be looking into at this point? Anything I should remove or edit?

---

### Post by dino99 on 2015-06-30
overclocking the cpu probably also means tweaking some other chipsets rate/voltage, as well as ram
then the system deals with powersaving  [https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

---

### Post by Yellow Pasque on 2015-07-01
What version of Ubuntu are you using? Have you tried i7z utility (available in repo)?
i7z will show you the turbo speed.

Also, a little info on your mobo wouldn't hurt:
```
sudo dmidecode -t bios -t processor -t baseboard
```

---

### Post by jordanmrodriguez on 2015-07-24
Sorry about the late reply, here is my results of your command.

# dmidecode 2.12
# SMBIOS entry point at 0x000f04d0
SMBIOS 2.8 present.


Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: V10.2
	Release Date: 11/10/2014
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 8192 kB
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


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: MSI
	Product Name:  Z97S SLI Krait Edition (MS-7922)
	Version: 2.0
	Serial Number: To be filled by O.E.M.
	Asset Tag: To be filled by O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To be filled by O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0


Handle 0x003A, DMI type 41, 11 bytes
Onboard Device
	Reference Designation:  Onboard IGD
	Type: Video
	Status: Enabled
	Type Instance: 1
	Bus Address: 0000:00:02.0


Handle 0x003B, DMI type 41, 11 bytes
Onboard Device
	Reference Designation:  Onboard LAN
	Type: Ethernet
	Status: Enabled
	Type Instance: 1
	Bus Address: 0000:00:19.0


Handle 0x003C, DMI type 41, 11 bytes
Onboard Device
	Reference Designation:  Onboard 1394
	Type: Other
	Status: Enabled
	Type Instance: 1
	Bus Address: 0000:03:1c.2


Handle 0x003D, DMI type 4, 42 bytes
Processor Information
	Socket Designation: SOCKET 0
	Type: Central Processor
	Family: Core i5
	Manufacturer: Intel
	ID: C3 06 03 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 60, Stepping 3
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
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Multi-threading)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Core(TM) i5-4690K CPU @ 3.50GHz
	Voltage: 1.2 V
	External Clock: 100 MHz
	Max Speed: 3800 MHz
	Current Speed: 3500 MHz
	Status: Populated, Enabled
	Upgrade: Socket BGA1155
	L1 Cache Handle: 0x003E
	L2 Cache Handle: 0x003F
	L3 Cache Handle: 0x0040
	Serial Number: Not Specified
	Asset Tag: Fill By OEM
	Part Number: Fill By OEM
	Core Count: 4
	Core Enabled: 4
	Thread Count: 4
	Characteristics:
		64-bit capable


Handle 0x004E, DMI type 13, 22 bytes
BIOS Language Information
	Language Description Format: Long
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

---

### Post by Yellow Pasque on 2015-07-26
Have you tried i7z utility (available in repo)? i7z will show you the turbo speed.

---

