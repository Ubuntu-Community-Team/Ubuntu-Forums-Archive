---
title: "Memory Upgrade - Need help."
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by kenweill on 2006-01-06
Hi.

I have some questions before upgrading/adding a memory chip for my computer.

I currently have 256MB(266 MHz) memory of my computer. I want to add a new memory chip for my computer. 512MB. So that it would be 256MB+512MB = 768 MB.

But the memory chip available in my area is 512MB with 400MHz.

Is it okey in Ubuntu to use both 266MHz and 400Mhz memory?

In Windows 9x, Me, and 2000, it will cause an error. I don't know in XP. And i don't know in Ubuntu.

Need immediate help.

---

### Post by buckley on 2006-01-06
[QUOTE=kenweill]Hi.

I have some questions before upgrading/adding a memory chip for my computer.

I currently have 256MB(266 MHz) memory of my computer. I want to add a new memory chip for my computer. 512MB. So that it would be 256MB+512MB = 768 MB.

But the memory chip available in my area is 512MB with 400MHz.

Is it okey in Ubuntu to use both 266MHz and 400Mhz memory?

In Windows 9x, Me, and 2000, it will cause an error. I don't know in XP. And i don't know in Ubuntu.

Need immediate help.[/QUOTE]

the problem is not in the OS, but in the hardware.... generally what will happen if you put in 2 sticks of different speeds is your motherboard will underlock the faster memory to the speeds of the slower.  you will probably get the same performance, if not better, by simply using the new 512 stick, and cashing in the old stick and buying another of the 400MHz speed

---

### Post by Mr Frosti on 2006-01-06
Memory configurations operates at a lower level then the operating system. This is configured by the system BIOS. Consult your motherboard's manual, or online website for specific details on memory upgradability. 

Typically, different speeds of memory in the same machine will operate at the lowest common speed. If you have a PC2700 (333 Mhz) and a PC3200 (400 Mhz), both will run at 333 Mhz in the same system. Usually faster RAM in a same series will down-clock to operate at a slower speed. 

You are looking at 256MB of PC2100 (166 Mhz), and 512 MB of PC3200 (400 Mhz), so you will be paying for additional speed that goes unused, if the faster stick is available to underclock that slowly. Usually PC3200 will only run at either 400 Mhz or 333 Mhz.

This all being taken into consideration, I believe more memory is better than faster memory for most tasks.

---

### Post by kenweill on 2006-01-06
So, will it still work in Ubuntu? Having different memory speeds?

I have experience having different memory speeds in Windows 95/98, and it produces Registry Errors. Solved only after removing the other one. 

Anyway, I will be using it for Ubuntu thats why I wanted to make sure first if will it be okey in Ubuntu.

Thanks for the reply.

---

### Post by buckley on 2006-01-06
now this is all assuming that your motherboard is capable of doing such a task.... i would look up the manual and double check to see what it says about memory.  Some boards support the feature, some do not.  

In your case, I fear that since you had registry errors in windows, it may not want to work nicely.  but no way to tell for sure until you try.

---

### Post by kenweill on 2006-01-06
I don't have a motherboard manual. Its a branded computer.
IBM ThinkCentre A50.

I have a manual but theres no info about motherboard or hardware.

My experience on Registry Errors is not from this machine. Its another machine. Older machine with Celeron 800MHz.

This is the information thats been detected when I login to IBM website(using Internet Explorer under Windows XP):

Product: ThinkCentre A50 8175-1QA 
Operating system: Windows XP
 
Original description: Intel® Pentium® 4 2.8GHz (512KB), 400MHz FSB, 128MB, 40GB 7200RPM IDE HDD, PCI Tower (3x4), Intel 865GV, 48x CD-ROM, Intel 10/100 Ethernet, DOS License
 
Architecture 
System board / Form factor 
Tower (4x4) with Intel 865G chipset 
Tower (3x4) with Intel 865GV chipset 
Supports Intel® Northwood Pentium® 4processors with 533MHz or 800MHz Front Side Bus (FSB) and 512KB L2 cache 
Supports Intel® Prescott Pentium® 4 processors with 800MHz FSB and 1MB L2 cache 
Supports Intel® Northwood Celeron® processors with 400MHz FSB and 128KB L2 cache 
uATX 
478 pin mPGA socket 
 
Processor 
Intel® Prescott Pentium® 4 2.4GHz to 3.2GHz 
Intel® Northwood Pentium® 4 2.4GHz to 3.2GHz 
Intel® Celeron® 2.0GHz to 2.6GHz 
 
Cache 
128KB to 1MB cache, processor dependent 
 
Chipsets 
Intel 865G or 865GV chipset 
Integrated Intel Extreme Graphics 2 
I/O Controller Hub (ICH5) for PCI 2.2 bus 
AC '97 2.3 Digital controller 
 
IDE controller 
2 Ultra ATA-100 connectors 
2 separate channels, 4 drive support 
 
Memory 
333MHz DDR (Double Data Rate) dual channel memory support 
PC2700 (333MHz) and PC2100 (266MHz) SDRAM memory supported 
Four 184 pin DDR DIMM sockets 
Supports a maximum memory up to 4.0GB 
ECC or parity memory is not supported 
Option part numbers for memory 
Note: BIOS will reflect 266MHz with Celeron processor  
Audio 
SoundMAX Cadenza with SPX 
Integrated PCI AC'97 2.3 compliant CODEC 
ADI 1981B CODEC 
Rear - Microphone input, line-in, line-out/headphone output 
Front - Microphone input, line-out/headphone output 
Software-based audio (done by processor and ICH5) 
Two piece external active speakers (on selected models) 
 
Keyboard and mouse 
Preferred Pro full-size keyboard 
Optical wheel mouse 
Option part numbers for pointing device 
 

Communications 
Networking 
Integrated Intel 10/100 Ethernet with Wake on LAN 
Option part numbers for networking 
  

Expansion 
Bays 
Two 5.25 inch, half-height 1.6 inch, external access, optical drives 
One 3.5-inch, slim height, floppy drive 
One 3.5-inch, slim height, hard disk drive (populated)
 
External ports 
Six USB ports (two in front, four in back), USB 2.0 
One ethernet RJ-45 
One serial 9-pin 16550 compatible 
One 25-pin parallel port (EPP, ECP), IEEE 1284 
Keyboard, monitor, and mouse ports 
Audio line in, headphone out, and microphone in jacks 
 
Slots 
Slot 1: full height, full length, AGP 32-bit AGP 8X (1.5v) (865G only) 
Slot 2: full height, full length, 32-bit PCI 2.2 (5v) 
Slot 3: full height, full length, 32-bit PCI 2.2 (5v) 
Slot 4: full height, full length, 32-bit PCI 2.2 (5v) 
Up to 175mm length 
 
 
 
 

Power 
Power management 
APM 1.2 and ACPI 1.0b compliant 
Wake on Serial port from ACPI S1, S3, and S5 
Wake on Lan from ACPI S1, S3, and S5 
Wake on USB from ACPI S1 and S3 
Wake on PS/2 keyboard/mouse from ACPI S1 and S3 
Energy Star complaint 
One Watt executive order (FEMP) 
 
Power supply 
230 watt supply with variable fan speed 
110 volt or 220 volt operation controlled by a switch on the back of the unit 
  

Security 
U-Bolt anchoring feature 
Security slot (for attachment of optional cable lock) 
Power-on password 
Configuration password (administrator password) 
Boot sequence control 
Diskette boot inhibit 
Boot without keyboard or mouse 
Diskette I/O control 
Hardfile I/O control 
Serial port I/O control 
Parallel port I/O control 
  

Software 
Operating system 
Microsoft Windows XP Home 
Microsoft Windows XP Professional 
Note: Preloaded software utilizes the disk-to-disk recovery method.
  

Storage 
Optical drive 
48x CD-ROM 
48x32x48x CD-RW 
Option part numbers for CD-ROM drives 
 
Hard disk drive features 
ATA-100 7200RPM EIDE supported 
Option part numbers for hard disk drives 
 
Video 
Integrated Intel Extreme Graphics 2 
15-pin VGA output on planar 
Uses system memory for video memory 
Uses Intel Dynamic Video Memory Technology (DVMT) 
32-bit Z-buffer depth 
300MHz DAC 
DVI-D port available for optional DVI-D connector adapter 
For models without a separate video card, memory supports both system and video. System memory used by video may be up to 32MB if the system has 128MB installed, and up to 64MB if the system has 256MB or more system memory installed, depending on video mode.
 
Resolution, maximum color depth, and refresh rates 
640x480x16M colors (60, 72, 75, 85, 100, 120 Hz) 
800x600x16M colors (60, 72, 75, 85, 100, 120 Hz) 
1024x768x16M colors (60, 70, 75, 85, 100, 120 Hz) 
1152x864x16M colors (60, 75, 85, 100 Hz) 
1280x1024x16M colors (60, 75, 85, 100, 120 Hz) 
1600x1200x16M colors (60, 75, 85, 100 Hz) 
1920x1440x16M colors (60 Hz) 
2048x1536x16M colors (60 Hz)

---

### Post by buckley on 2006-01-06
yea all that isnt really much help... your best bet is to just install the ram, and go into your BIOS and see what it tells you.

---

### Post by kenweill on 2006-01-06
[QUOTE=buckley]yea all that isnt really much help... your best bet is to just install the ram, and go into your BIOS and see what it tells you.[/QUOTE]

Okey.
Thanks alot to all of you for your help.

I'll just post my results later.

---

### Post by TransitMan on 2006-01-06
From you listing of the specs for the computer, the fastest memory compatable is 333mhz. A 400mhz chip may work, but mixing such extreme speeds may lead to a hardware issue, and not a software issue.

My advice, pull the 256/266mhz stick, replace it with the 512/400mhz stick and see how it goes.
If memory serves correctly, the 512 will clock down to 333mhz, but it is doubtful it would clock down to 266mhz. Too much of a difference there.

---

### Post by kenweill on 2006-01-11
It works fine. Its much faster, having large memory.

I installed both 266Mhz and 400Mhz. All clocked at 266 Mhz.

Thank you all for all your help.

---

