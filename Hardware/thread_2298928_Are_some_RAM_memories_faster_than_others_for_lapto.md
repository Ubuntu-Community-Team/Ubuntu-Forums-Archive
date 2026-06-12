---
title: "Are some RAM memories faster than others for laptop computers"
date: 2015-10-14
forum: Hardware
---

### Post by Ralph L on 2015-10-14
I have a Toshiba Satellite A215-/S4697 laptop for which I want to buy additional RAM.  The current RAM is DDR2.  I can't seem to find an answer for the following questions:  
1.  Are there faster and slower memories available for a given laptop, or are they all the same, because they run off the same clock (or for some other reason)??  
2.  Also, is it possible to used DDR3 memory in this laptop, which is designed for DDR2??  
Any help is appreciated......

---

### Post by QIII on 2015-10-14
Hello!

1.  Yes, memory modules come in different operating speeds.

2.  No, you can't use DDR2 and DDR3 interchangeably.  They are incompatible both electronically and physically.

[This]("https://en.wikipedia.org/wiki/DDR2_SDRAM") gives a pretty good run-down.  Speeds are explained a bit in "Chips and Modules" and the physical differences are displayed in the image labeled "Comparison of memory modules for portable/mobile PCs (SO-DIMM)."

Just getting "faster" memory may not do you any good.  The motherboard may only be able to handle a particular data rate.  If that is the case, faster memory just won't run faster than the motherboard allows.

---

### Post by mastablasta on 2015-10-15
in any case increase DDR2 as much as you can per motherboard and CPU specs (and as much as you can afford).

---

### Post by Bucky Ball on 2015-10-15
> **QIII said:**
> The motherboard may only be able to handle a particular data rate. If that is the case, faster memory just won't run faster than the motherboard allows.

Important point, this. Faster RAM will probably be more expensive also, and if your machine can't use that speed, waste of money. 

[This]("http://www.ebay.com.au/gds/RAM-Speeds-Explained-SDRAM-DDR1-DDR2-DDR3-DDR4-DDR5-/10000000020781305/g.html?clk_rvr_id=911916461833&rmvSB=true") gives a brief overview, the important part being the list of possible ddr2 RAM speeds. 

DDR2 &#8211; 400Mhz, 533Mhz, 677Mhz, 800Mhz

I thought there were faster speeds than this, but haven't bought any RAM for a few years, so ... Find your motherboard manual or get searching online and find what the max speed your motherboard can take. Good luck. :)

---

### Post by Yellow Pasque on 2015-10-15
Unless they made this model with different CPU's, your CPU (Turion64 X2 TL-52) doesn't officially support DDR2-800.

Otherwise, what do you have in there now and are you looking to reuse it or replace it?
```
sudo dmidecode -t memory
```

> DDR2 – 400Mhz, 533Mhz, 677Mhz, 800Mhz I thought there were faster speeds than this, but haven't bought any RAM for a few years

There are faster speeds of DDR2 (I know there was at least 1066), but you have to loosen the timings, and it becomes counterproductive for a lot of the CPU's that use DDR2. A lot of buyers (and vendors) seem to be stuck in the, "Damn the timings.. More Bandwidth!" mentality of the Pentium4/D days.

---

### Post by Bucky Ball on 2015-10-15
> **QIII said:**
> There are faster speeds of DDR2 (I know there was at least 1066), but you have to loosen the timings, and it becomes counterproductive for a lot of the CPU's that use DDR2. A lot of buyers (and vendors) seem to be stuck in the, "Damn the timings.. More Bandwidth!" mentality of the Pentium4/D days.

Ah, ha. Thanks for that. Haven't diddled inside the P4 box for a couple of years when I actually did upgrade the DDR2 RAM, to what speed I don't remember. I do remember it was at the manufacturer's recommendation in the manual. :)

---

### Post by mcduck on 2015-10-15
Also if you plan adding more RAM, instead of replacing all existing modules, keep in mind that all RAM modules will run at the speed of the slowest installed module. So buying faster modules would be a waste of money unless you get rid of all the slow ones at the same time.

---

### Post by Ralph L on 2015-10-17
Thank you to everybody responding.  I learned some things.  I have 2 laptops:  Toshiba Satellite A215-S4697 and Dell Latitude D610.  Here are the outputs of running dmidecode on each:  
Toshiba Satellite A215-S4697```
ralph@lat1:~$ sudo dmidecode -t memory
[sudo] password for ralph: 
# dmidecode 2.12
SMBIOS 2.4 present.

Handle 0x0011, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x0012, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0011
	Error Information Handle: No Error
	Total Width: 128 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: 1
	Locator: S1
	Bank Locator: DIMM1
	Type: DDR2
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x0013, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0011
	Error Information Handle: No Error
	Total Width: 128 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: 2
	Locator: S2
	Bank Locator: DIMM2
	Type: DDR2
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

ralph@lat1:~$

```
Dell Latitude D610```
ralph@lat1:~$ sudo dmidecode -t memory
[sudo] password for ralph: 
# dmidecode 2.12
SMBIOS 2.3 present.

Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x1100, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM_A
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 533 MHz
	Manufacturer: C100000000000000
	Serial Number: 02038722
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x1101, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM_B
	Bank Locator: Not Specified
	Type: DDR
	Type Detail: Synchronous
	Speed: 667 MHz
	Manufacturer: CE00000000000000
	Serial Number: 9591EA05
	Asset Tag: Not Specified
	Part Number: Not Specified

ralph@lat1:~$
```
The speed of the current Toshiba memory is not listed, so no help there.  However, when I searched for memory for that model computer, all vendors listed 667 so I guess that is probably the fastest the motherboard can take.
To my surprise the Dell shows that I have two different speed memories in it.  Searching for memory came up with 667 speed again, so I am guessing that's the fastest speed the motherboard for that computer will take.  Although I wasn't planning on upgrading the Dell memory, I am considering doing that too.  Does anybody know if the Dell 610 actually runs the memory at 667, or does it run it at only 553????

---

### Post by Bucky Ball on 2015-10-17
Looks like a mismatched pair of 1Gb DDR sticks, meaning the speeds are different. One's 533 and the other's 667. The manufacturer codes also don't appear to match, but not sure if I'm reading them right, and the serial numbers are a long way apart.

As for what your board is capable of, I can't tell from this. Someone else perhaps can. If they are DDR sticks, then it is probable that is what the board is up to, but you never know. Why not have a quick search for the model and RAM?

* See this:

> According to the documents available on the Dell support page, the D610 uses either the 915 pm or 915 gm chipset.  Intel's specs on this chipset family indicate a 2 GB maximum on the memory controller.  A BIOS update would not help overcome this limit even if such an update were available.

From [here]("http://en.community.dell.com/support-forums/laptop/f/3518/t/19294811"). If you had the manual you could find out for sure.

---

### Post by Yellow Pasque on 2015-10-17
I wouldn't bother with the Dell. Intel doesn't list support for DDR2-667 on the chipset used in it. [http://ark.intel.com/products/27715/Intel-82915GM-Graphics-and-Memory-Controller](http://ark.intel.com/products/27715/Intel-82915GM-Graphics-and-Memory-Controller)
Even if it did, I don't think you would notice enough of a speed difference to justify spending money on it.

As for the Toshiba, the decision is made easier by it only having 512MB sticks. The only upgrades that really make sense are a 4GB set (2x2GB) or a 2GB (2x1GB) set of DDR2-667.

---

