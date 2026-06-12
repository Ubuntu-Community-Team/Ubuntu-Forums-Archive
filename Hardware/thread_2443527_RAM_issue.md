---
title: "RAM issue"
date: 2020-05-16
forum: Hardware
---

### Post by mudpuppy630511 on 2020-05-16
I recently upgraded my Dell Latitude E5400 form 2GB to 4GB. I purposefully went through the full RAM check at the boot. I've been able to get SWTOR running on Lutris. Problem I have is that when I select system specs, my RAM still shows up as 1.94GB, when I know that is false. Did I miss a step in the process?

---

### Post by CelticWarrior on 2020-05-17
It's 32-bit hardware so there's a memory limit.
And also this: [https://www.dell.com/community/Laptops-General-Read-Only/How-do-I-upgrade-RAM-in-Latitude-E5400/td-p/3160539](https://www.dell.com/community/Laptops-General-Read-Only/How-do-I-upgrade-RAM-in-Latitude-E5400/td-p/3160539)

---

### Post by Yellow Pasque on 2020-05-17
Can you show?:
```
sudo dmidecode -t memory bios
```

> It's 32-bit hardware so there's a memory limit.
From what I can see, it's a Core2 Duo CPU and G45 chipset, so it supports 64-bit.

---

### Post by CelticWarrior on 2020-05-17
> **Yellow Pasque said:**
> Can you show?:
```
sudo dmidecode -t memory bios
```


From what I can see, it's a Core2 Duo CPU and G45 chipset, so it supports 64-bit.

Yes, that version is 64-bit but the more common variant (and cheaper) of the E5400 model came with a 32-bit Dual Core CPU and was this one with reported issues with RAM upgrades.

---

### Post by Yellow Pasque on 2020-05-17
> **CelticWarrior said:**
> the more common variant (and cheaper) of the E5400 model came with a 32-bit Dual Core CPU

What model CPU specifically? A link would be helpful.
All the CPU's I see from Googling are Core 2 Duo-based (Merom core, specifically).

---

### Post by mudpuppy630511 on 2020-05-17
> **Yellow Pasque said:**
> What model CPU specifically? A link would be helpful.
All the CPU's I see from Googling are Core 2 Duo-based (Merom core, specifically).

It is a 64-Bit OS, and it is a Core 2 DUO Based @ 2GHz x 2. The RAM is listed to be 1.92 GiB (this is false now)
And here is the Terminal Info:

# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.4 present.

Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 8 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x1100, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM_A
	Bank Locator: Not Specified
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MT/s
	Manufacturer: CE00000000000000
	Serial Number: 757C3AB1
	Asset Tag: 51140C
	Part Number: M4 70T5663QZ3-CE6 

Handle 0x1101, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM_B
	Bank Locator: Not Specified
	Type: DDR2
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer:                 
	Serial Number:         
	Asset Tag:       
	Part Number:                   

Is there a way to correct the discrepancy? Here is the 4GB RAM details I bought:

4GB Kit (2GBX2) DDR2 667 sodimm RAM, Kuesuny PC2-5300 / PC2-5300S CL5 200-Pin Non-ECC Unbuffered Notebook Laptop Memory Modules

I hope this helps to come to a solution as to why the system info does not show the new amount of RAM.

---

### Post by CelticWarrior on 2020-05-17
That memory is expected not to work (or only half to be detected). This is the only memory type which is known to be compatible, other than the ones sold by Dell: [https://www.memoryc.com/dell-laptop-latitude-e5400-memory-upgrade.html#sysdetails](https://www.memoryc.com/dell-laptop-latitude-e5400-memory-upgrade.html#sysdetails)

Single-sided. Yours is probably double-sided, not all chipsets of this vintage supported both. Anyway, parts for a computer that belongs to a museum is a waste of money.

---

### Post by Yellow Pasque on 2020-05-17
> Size: No Module Installed

dmidecode is not seeing a module installed. This probably means the BIOS does not recognize the stick (check in your BIOS to see how much RAM reported). If BIOS reports only 2GB, then it probably means you either have a defective stick or did not seat it properly, or the BIOS does not like it for some other reason.

---

### Post by mudpuppy630511 on 2020-05-17
> **Yellow Pasque said:**
> dmidecode is not seeing a module installed. This probably means the BIOS does not recognize the stick (check in your BIOS to see how much RAM reported). If BIOS reports only 2GB, then it probably means you either have a defective stick or did not seat it properly, or the BIOS does not like it for some other reason.

Oh Snap. I hadn't thought about that, but had that as a back burner though. I'll check the seating. I can't remember the command to enter BIOS.

To you Celtic Warrior:

[QUOTE=CelticWarrior 

Re: RAM issue
    That memory is expected not to work (or only half to be detected). This is the only memory type which is known to be compatible, other than the ones sold by Dell: [https://www.memoryc.com/dell-laptop-...tml#sysdetails](https://www.memoryc.com/dell-laptop-...tml#sysdetails) 

    Single-sided. Yours is probably double-sided, not all chipsets of this vintage supported both. Anyway, parts for a computer that belongs to a museum is a waste of money.[/QUOTE] 

The terminal line indicates, that the max I can upgrade to is 8GB.

---

### Post by Yellow Pasque on 2020-05-18
> **mudpuppy630511 said:**
> The terminal line indicates, that the max I can upgrade to is 8GB.

The manual says that only models with discrete Nvidia GPU can be upgraded to 8GB. It also says to press F2 when you start your computer to enter the BIOS.
[https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e5400_service%20manual_en-us.pdf](https://downloads.dell.com/manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e5400_service%20manual_en-us.pdf)

---

