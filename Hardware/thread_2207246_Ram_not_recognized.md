---
title: "Ram not recognized"
date: 2014-02-22
forum: Hardware
---

### Post by Benic on 2014-02-22
Hi! I don't know why, but Ubuntu (13.10 64-bits) is not recognizing all the RAM. I've got 4*1Gb DDR1 dual channel modules installed and Ubuntu is only reporting 2.8 even if BIOS is recognizing all four modules. Here's some info that might help : 

```

free -m
             total       used       free     shared    buffers     cached
Mem:          2883       1339       1544          0         83        528
-/+ buffers/cache:        726       2156
Swap:         2012          0       2012

sudo dmidecode -t memory
# dmidecode 2.12
SMBIOS 2.3 present.

Handle 0x0007, DMI type 5, 24 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 4096 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		Other
		Unknown
		Standard
		FPM
		EDO
		Parity
		ECC
		SIMM
		DIMM
		Burst EDO
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 4
		0x0008
		0x0009
		0x000A
		0x000B
	Enabled Error Correcting Capabilities:
		None

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: CH A DIMM0
	Bank Connections: 0 0
	Current Speed: 5 ns
	Type: DIMM SDRAM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: CH A DIMM1
	Bank Connections: 0 0
	Current Speed: 5 ns
	Type: DIMM SDRAM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: CH B DIMM0
	Bank Connections: 0 0
	Current Speed: 5 ns
	Type: DIMM SDRAM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: CH B DIMM1
	Bank Connections: 0 0
	Current Speed: 5 ns
	Type: DIMM SDRAM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0040, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: 0x003F
	Number Of Devices: 4

Handle 0x0042, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: 0x003F
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: 1
	Locator: J6G1
	Bank Locator: CHANNEL A DIMM0
	Type: DDR
	Type Detail: Synchronous
	Speed: 400 MHz
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

Handle 0x0044, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: 0x003F
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: 2
	Locator: J6G2
	Bank Locator: CHANNEL A DIMM1
	Type: DDR
	Type Detail: Synchronous
	Speed: 400 MHz
	Manufacturer: Manufacturer2
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: PartNum2

Handle 0x0046, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: 0x003F
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: 1
	Locator: J6H1
	Bank Locator: CHANNEL B DIMM0
	Type: DDR
	Type Detail: Synchronous
	Speed: 400 MHz
	Manufacturer: Manufacturer3
	Serial Number: SerNum3
	Asset Tag: AssetTagNum3
	Part Number: PartNum3

Handle 0x0048, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: 0x003F
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: 2
	Locator: J6H2
	Bank Locator: CHANNEL B DIMM1
	Type: DDR
	Type Detail: Synchronous
	Speed: 400 MHz
	Manufacturer: Manufacturer4
	Serial Number: SerNum4
	Asset Tag: AssetTagNum4
	Part Number: PartNum4

```

Any clues about what's wrong? Thanks!!!

---

### Post by J_Me on 2014-02-23
Your graphics card will steal some of your RAM, I don't konw how it works but what ever the size of your gpu memory is, that amount is taken away from from the total system RAM.

---

### Post by Benic on 2014-02-25
Yeah, you're right. I've found the manual and it says the board can chew up to 750 mb right away. 1.2 gb (and I'm not using the board GPU) seems a bit excessive to me, but there's nothing I can do about it I guess...

---

### Post by Yellow Pasque on 2014-02-25
What kind of motherboard is it?

---

### Post by Benic on 2014-02-25
It's an old Intel D915GAG. I've tried several bios settings without noting any difference.

---

### Post by Yellow Pasque on 2014-02-25
Are you running latest BIOS?

```
sudo dmidecode -t 0,1,2
```

---

### Post by mastablasta on 2014-02-26
usually in BIOS you could set the amount of ram for the GPU. though i am not familiar with intel that is how it is in nvidia and AMD. heck even in raspbery pi you can do it like so.

---

### Post by Yellow Pasque on 2014-02-26
> **mastablasta said:**
> usually in BIOS you could set the amount of ram for the GPU

Modern Intel GPU's allocate dynamically instead of using a static setting configurable in BIOS. A 915G should only be taking 256MB at most (and only under high GPU load).

Please respond to question and give output I asked for in my last post...

---

