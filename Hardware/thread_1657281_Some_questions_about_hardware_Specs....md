---
title: "Some questions about hardware Specs..."
date: 2011-01-01
forum: Hardware
---

### Post by Linyx on 2011-01-01
[SIZE=2]Sorry if i place this thread in wrong Place.....

I want to know something about hardware....Including given Questions...

1) How Microprocessor Companies(Intel & AMD) names their Processors(Models)...?i means the arrangement of names...

2)I am Confused about the **CPU Clock**, PLZ someone Clear that to me....I have Pentium-D with 2.8GHz CPU....i thought that the Value "**2.8**" is actually the Clock of my each CPU. because this is also a Frequency...and when i See my hardware Specs from the Command "**lshw**", I see their in CPU tab > Clock = **800MHz**....so i am confused about this ....

3)When i open my** Memtest** in Grub-Menu, i see my **FSB** to be 200, and whenever i open specs of P-D dc7600 , i found their all CPU have 800....Can someone clear my concept with that....
Moreover My CPU is dc7600 ,2.8 , 945 Chip-set...

Thanks
[/SIZE]

---

### Post by cascade9 on 2011-01-01
1- complicated. Current its like this- 

AMD is pretty easy. X2 = dual core, X3 = triple core, X4 = quad core, X6 = hexacore. Athlon II- low CPU cache, Phenom II- high CPU cache. 

Intel is more complicated. i3- low end, (dual core only) i5- midrange (dual core and quad core) i7- top end (quad core and hexacore) 

2- Pentuin D 915/920 will run at 2.8GHz under full load. At partial load/idle, the CPU will 'downclock' (slow down) to save power and create less heat. 

3- Memtest is telling you 'real' speed. (the RAM is running at 200MHz). Itnel rated the P4 FSB (Front side bus) as '800MHz' but that is 'clock quadrupled'. Memtest is teling you the truth, intel was doing marketing.

---

### Post by Linyx on 2011-01-01
[SIZE=2]Thanks for reply ...:p

This means that my Each CPU has Max-Clock of 2.8....? isn't...?
Then what about the value> **Clock= 800Mh**z.... Is this is minimum Clock-Speed of Each Core....?
[/SIZE]

---

### Post by cascade9 on 2011-01-01
YERs, max clock it 2.8GHz. 800MHz will be the minimum core speed. ;)

---

### Post by Linyx on 2011-01-01
[SIZE=2]Thanks for that,,,I got it..:p

Another question comes to mind, for which i don't want to make another thread, and i don't want to Give time to Google to find out my given Question...

Actually i want to know how the data is processed my CPU....

First of all, let me clarify my question,
According to my approach .... Data is present on HDD first, then when PC is instructed by user to do something.....it **loads** the current data into Memory(RAM)..after that, Ram transfer/Kept data into External-Cache(L-2) > Internel cache(L-1) > ALU > Registry > from Registry data are transfer towards **Control-Unit**(Where they are Processed)....but **after** that i don't know what happens **next**...?....

In the above paragraph, if i am **missing** something ..plz Clarify that to me....

Excuse my English...;)
[/SIZE]

---

### Post by Linyx on 2011-01-02
[SIZE=2]bump[/SIZE]

---

### Post by cascade9 on 2011-01-04
> **Linyx said:**
> [SIZE=2]Actually i want to know how the data is processed my CPU....

First of all, let me clarify my question,
According to my approach .... Data is present on HDD first, then when PC is instructed by user to do something.....it **loads** the current data into Memory(RAM)..after that, Ram transfer/Kept data into External-Cache(L-2) > Internel cache(L-1) > ALU > Registry > from Registry data are transfer towards **Control-Unit**(Where they are Processed)....but **after** that i don't know what happens **next**...?....
[/SIZE]

I *think* that with the newer architectures, data can be moved from the HDD straight to L2/L1 cache, it doesnt need to go to RAM, and the same going back. 

BTW, L2 'external' cache? That is very old terminology, from the days of the Pentium and earlier CPUs, when the L2 cache was actualy 'external' to the CPU. Since the Pentium 2s/AMD Athlons L2 cache has been in the CPU package.

---

### Post by Linyx on 2011-01-07
> **cascade9 said:**
> I *think* that with the newer architectures, data can be moved from the HDD straight to L2/L1 cache, it doesnt need to go to RAM, and the same going back. 


[SIZE=2]You means in new Architecture data will not load to RAM..? i think every Running Process must be loaded to RAM first....................[/SIZE]

---

### Post by sktechnical on 2011-03-09
Hello,

I am newbie and planning on buying following configuration from TigerDirect (PC bundle) to run Linux as base OS (need some help with this but will come to that later) and run Windows on top of it.  On the other hand change all my existing boxes (AMD Sempron) box to linux and connect to to the new box to run Windows as vertual (I am not sure how this works too).

Any help with this is appreciated.


The PC Bundle specifications:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=57551&SRCCODE=WEM2605BY&cm_mmc=email-_-Main-_-WEM2605-_-tigeremail]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=57551&SRCCODE=WEM2605BY&cm_mmc=email-_-Main-_-WEM2605-_-tigeremail")

MSI 785GTM-E45 Motherboard
	  Processor Socket:  	AMD
	  Processor Interface:  	Socket AM2+
	  Form Factor:  	Micro ATX
	  Processors Supported:  	AMD Athlon
	  	AMD Sempron
	  	AMD Phenom
	  	AMD Phenom II
	  	AMD Athlon II
	
	  Additional Technologies:  	AMD Cool 'n' Quiet
	  HyperTransport Bus:  	2.6GHz
	  Northbridge:  	AMD® 785G and SB710 Chipset
	  Southbridge:  	SB710
	  Memory Type:  	DDR2
	  Maximum Memory Supported:  	8GB - 64-Bit
	  Channels:  	8 Channels
	  Audio Chipset:  	Realtek® High-End Audio
	  LAN Type:  	10/100/1000 Fast Ethernet
	  PS/2 Keyboard Connectors:  	1
	  PS/2 Mouse Connectors:  	1
	  USB Ports (Total):  	4
	  LAN Ports:  	1
	  Serial ATA 3.0Gb/s Headers:  	6
	  DVI Ports:  	1
	  HDMI Ports:  	1
	  PCI Slots:  	2
	  PCI Express X1 Slots:  	1
	  PCI Express X16 Slots:  	1
	  RAID Support:  	Yes
	  Length:  	24.4cm
	  Width:  	22.9cm
	
AMD Phenom II X4 920 Quad Core OEM Processor
	  Manufacturer:  	AMD
	  CPU Type:  	Desktop
	  Processor Interface:  	Socket AM2+
	  Processor Class:  	Phenom II
	  Processor Speed:  	2.80GHz
	  Cores:  	Quad
	  Cache Size:  	4 x 512KB L2
	  L2 Cache:  	2 MB
	  L3 Cache:  	6MB
	  Bus Speed:  	1800MHz (3600 MT/s)
	  Fan:  	Not Included
	  Wattage:  	125W
	  Additional Technologies:  	MMX
	  	Enhanced 3DNow!
	  	Cool'n'Quiet
	  	HyperTransport 3.0
	  Unlocked Multiplier:  	No
	  Instruction Set:  	SSE
	  	SSE2
	  	SSE3
	  	SSE4a
	  Integrated Graphics Core:  	No
	  Integrated Memory Controller:  	Yes
	
Zalman Hydraulic Bearing CPU Cooler
	  Fan Type:  	CPU Cooler
	  Socket Type:  	775
	  	AM2
	  	AM2+
	  	AM3
	  	1156
	  	1155
	  Bearing Type:  	Hydraulic
	  RPM:  	1400 ~ 2700 RPM
	  Connector(s):  	4 Pin (PWM)
	
Patriot 2048MB PC6400 DDR2 Memory
	  Memory Category:  	Desktop
	  Memory Type:  	DDR2
	  Memory Speed:  	PC6400
	  Memory Speed MHz:  	800MHz
	  Memory Size:  	2048MB
	  Total Memory Size:  	2GB
	
	  Memory Modules:  	1
	  Memory Socket:  	DIMM
	  Memory CAS Latency:  	6
	  Pins:  	240
	  ECC:  	No
	  Memory Buffer:  	Unbuffered
	
Seagate Barracuda 1TB Low Power Hard Drive
	  Drive Type:  	Internal
	  Interface:  	SATA-3G
	  Interface Type:  	SATA
	  Spindle Speed (RPM):  	5900
	  Buffer Memory:  	32MB
	  Average Latency (msec):  	5.5
	  Data Transfer Rate on Serial ATA:  	Up to 3000 Mb/sec
	  Temperature, Operating (°C):  	0 to 60
	  Temperature, Nonoperating (°C):  	-40 to 70
	  Shock, Operating: 2 msec (Gs):  	70
	  Shock, Nonoperating: 2 msec (Gs):  	350
	
Lite-On Internal 24X DVD Writer
	  Cache Size:  	CD: 2 MB
	  DVD+R Write Speed:  	24X
	  DVD+RW Rewrite Speed:  	8X
	  DVD-R Write Speed:  	24X
	  DVD-RW Rewrite Speed:  	6X
	  DVD Read Speed:  	16X
	  DVD-RAM Write Speed:  	12X
	  DVD Access Time:  	160 ms
	  CD Write Speed:  	48X
	  CD Rewrite Speed:  	32x
	  CD Read Speed:  	48X
	  CD Access Time:  	140 ms
	  Length:  	6.69"
	  Width:  	5.75"
	  Height:  	1.62"
	  Weight:  	1.98 lbs
	  Interface Type:  	SATA
	  Enclosure Type:  	Internal
	  Type:  	CD/DVD Burners
	
PowerUp G54-8019 Executive ATX Mid-Tower Case
	  120mm Fan Ports:  	2
	  120mm Fans Included:  	None
	  Form Factor:  	ATX Mid-Tower
	  Compatible Motherboards:  	ATX
	  	Micro ATX
	  	Flex ATX
	  Side Panel Type:  	Vented
	  Power Supply:  	Not Included
	  Material:  	SGCC
	  External 5.25" Drive Bays:  	4
	  External 3.5" Drive Bays:  	1
	  Internal 3.5" Drive Bays:  	7
	  Expansion Slots:  	7
	  Front USB Ports:  	2
	  Front FireWire Ports:  	None
	  Front Audio Ports:  	2
	  Front eSATA Ports:  	None
	  Depth:  	436mm
	  Width:  	180mm
	  Height:  	415mm
	
DiabloTek PSDA400 Power Supply
	  Form Factor:  	ATX
	  Wattage:  	400W
	  Modular Cabling:  	No
	  Fan:  	80 mm
	  Input Voltage:  	8A@115 / 5A@230 V
	  +3.3V:  	26 A
	  +5V:  	35 A
	  +12V 1:  	15 A
	  -12V:  	0.5 A
	  -5V:  	0.5 A
	  +5VSB:  	2.0 A
	  Motherboard Connector:  	20+4 Pin
	  4-Pin P4:  	1
	  4-Pin Floppy Connector:  	1
	  4-Pin Peripheral Connector:  	4
	  SATA Power Connector:  	4

---

