---
title: "increase Ram or create  swap file ?"
date: 2012-11-12
forum: Hardware
---

### Post by integ on 2012-11-12
Hi,
 I have been noticing some system lag when opening over 8 tabs on my Chromium browser, using Libre Office Suite and especially when running XP on Vitual Box. 

My system  details are as below:
Pentium(R) Dual-Core CPU E5200 @ 2.50GHz × 2 
Intel® G33 x86/MMX/SSE2 
991.1 MiB DDR2 , HDD 300GB (with almost 200GB Free)
Ubuntu 12.04 

1) Should I buy additional RAM? If so,how much RAM can I add? Can I add it along with my existing 1GB RAM? And the new RAM should it be same DDR2 as existing  or can it be DDR3.

2)Or if I create a swap file, will that help. If so, of what size should it be.

---

### Post by howefield on 2012-11-12
I'd recommend more RAM.

Do you know which motherboard you have ?

---

### Post by Cheesemill on 2012-11-12
Can you post the output of:
```
sudo dmidecode -t memory
```It will tell us how many memory slots you have and what's in each one.

---

### Post by slickymaster on 2012-11-12
If I where you, I would upgrade your RAM memory, clearly 1 GB isn't enough for your needs.

Kingston recently announced the launch of memories Kingston HyperX Red to its product line of high performance, HyperX Blu. Why don't you take a look, they aren't so expensive as one might think.

You can take a look [here]("http://www.kingston.com/us/memory/hyperx").

---

### Post by varunendra on 2012-11-12
> **integ said:**
> 1) Should I buy additional RAM?Without any delay..! If it's default 12.04 (with unity 3D), it's an 'Achievement' that you can even start XP in a VM with mere 1GB ! ;)

Most of the earlier G33 boards did not support DDR3 (you can check that on your board manufacturer's site for your model). And if yours is already running on DDR2, it almost certainly doesn't have support for DDR3 (IIRC, the few boards that were launched with support for both DDR2 and DDR3 failed miserably in the market, so companies immediately stopped producing them).
If so, you'll have to buy a DDR2, and the same frequency as the existing one, even same brand if you can find it (actually, even the same 'lot' is the recommendation, but obviously that's not possible now :))
Please note that while a 'different frequency' RAM may work in parallel, such a combination is most likely to create strange problems on the system.

Any G33 board will have support for at least 4GB memory. As such, you may go with a good brand (entry level Kingston/Transcend would be fine) module of 2GB, same frequency. Or you can opt to go for new 2x2GB modules of same type (would be best !) and discard the current 1GB one.

Even if you have more than two RAM slots available, it doesn't make much sense to get more than 4GB memory for such an old board and CPU combination (unless you are a heavy gamer and have high-end graphics card for that). Especially when DDR2 has become so much costlier compared to DDR3s.

Bottomline for the mentioned combo (with mentioned usage) is- 
2 GB --> at least !
2 + 1 GB (same freq.) --> Fine (in fact Good, if you could find same brand/type)
2 + 2 GB (a new pair of same type) --> Great !
Anything above 4 GB --> Useless IMHO, and wouldn't make much performance difference even if has support for DR3 (which I highly doubt it has).

**PS :**
Regardless of the amount of RAM, I'd recommended to have an exactly 2GB swap partition, if you aren't hibernating. Or equal to RAM if you plan to use hibernation (which is often buggy and thus isn't enabled by default on 12.04).

Hope it helps.

---

### Post by integ on 2012-11-12
Hi Friends , 

Thank you for responding to my query. I will definitively be getting 2GB RAM added on to this system. Just in caseif the details you have asked me helps.

> @howefield : Do you know which motherboard you have ?

 description: Motherboard
       product: G31M-ES2L
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: FC
          date: 07/02/2009
          size: 128KiB
          capacity: 448KiB

> @Cheesemill : Can you post the output of:
Code: sudo dmidecode -t memory
It will tell us how many memory slots you have and what's in each one.

sudo dmidecode -t memory
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: 8-bit Parity
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 2048 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		Other
	Memory Module Voltage: 5.0 V
	Associated Memory Slots: 2
		0x0006
		0x0007
	Enabled Error Correcting Capabilities:
		None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 1
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2
	Current Speed: Unknown
	Type: Other
	Installed Size: 1024 MB (Single-bank Connection)
	Enabled Size: 1024 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0019, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 16 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: 667 MHz
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number: 

> @varunendra  : Regardless of the amount of RAM, I'd recommended to have an exactly 2GB swap partition, if you aren't hibernating. Or equal to RAM if you plan to use hibernation (which is often buggy and thus isn't enabled by default on 12.04.

Sure i will try increasing swap partition to 2 GB , currently I have 1GB swap partition. Along with increasing swap partition is it advisable to create a swap file. If so of what size.

---

### Post by integ on 2012-11-12
@ using free command result is : ( this report was taken while i was running 5 tabs on chromium, libre , gimp, and xp on virtual box) 

total used free shared buffers cached
Mem: 1014888 941484 73404 0 1332 185792
-/+ buffers/cache: 754360 260528
Swap: 1543724 736912 806812
this report was taken while i was running 5 tabs on chromium, libre , gimp, and xp on virtual box

---

### Post by varunendra on 2012-11-12
> **integ said:**
> 
 description: Motherboard
       product: G31M-ES2L
Exactly that is the board I had in mind while writing whatever I wrote :)
It doesn't support more than 4GB RAM anyway (no more than 2GB per memory bank - as can be verified by the dmidecode output).
[http://www.gigabyte.com/products/product-page.aspx?pid=3485#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3485#sp)
It's a really nice MB for its price, but kinda outdated now.

Just get a 667MHz Kingston/Transcend module and you should be good to go.
> **integ said:**
> Along with increasing swap partition is it advisable to create a swap file. If so of what size.While you can do so, I don't think it'll help in any performance improvement. So I'd suggest to leave the idea of creating a swap file.

---

### Post by integ on 2012-11-13
Thanks again , will do so. 
Wish you guys great festival.

---

