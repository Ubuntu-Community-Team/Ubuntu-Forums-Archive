---
title: "How to build a PC that is 100% compatible with Ubuntu"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by Uboontu on 2007-08-22
Hey, "Ubuntuers",

I was thinking of buying one of those Ubuntu Dell desktop PC's but then realized that they are not available in my country (Canada), so I decided to build a PC myself that is compatible with Ubuntu. I am wondering if you guys could give me some advices on how to choose the components (motherboards, graphic cards, etc) to make sure that the PC will be 100% compatible with Ubuntu. I'm asking this because I have had many failures trying to install Ubuntu on my laptop (HP Pavilion DV5000), so I am really starting to be afraid of hardware problems.

Thanks.

---

### Post by WiseElben on 2007-08-22
Check out: [http://www.linuxcompatible.org/compatibility.html](http://www.linuxcompatible.org/compatibility.html)

Building a Linux-compatible computer isn't hard. You can go with either AMD or Intel for your processor, and the motherboard doesn't really matter. What you need to watch out for is the graphics card and wireless card. Go with Intel for those two components because there are more drivers readily available.

As for the other components (HD, DVD Drive, etc), just go with whatever you want. The software that comes with it wouldn't run on Linux (usually), but those software usually suck anyways.

---

### Post by daveshields on 2007-08-22
My experience is that the motherboard does matter. For example, I recently upgraded one of my boxes to use the BIOSTAR TFORCE 550 Socket AM2 NVIDIA nForce 550 MCP ATX AMD . It was a disaster, and I wasted lots of hours until I figured out I needed to install a BIOS update. Then it provd to be a champ running Ubuntu.

The motherboard determines which processor and memory you must use, as well as the available kinds of connections for external devices. 

I built a machine from scratch a couple of weeks ago. I was aiming for low cost, with adequate performance for a desktop, aiming to spend about $50-$60 for each of the key parts (I had display, cd/dvd drive, mouse and keyboard at hand). I built the machine with parts from [http://newegg.com]("http://newegg.com"). Read the user comments to find mention of "Linux" or "Ubuntu," and pay particular attention to *negative* comments.

I used the following:

Rosewill R604TSB-N 120mm Fan ATX Mid Tower Computer Case+450W Power Supply. I picked this because it came with power supply.

ECS GeForce6100SM-M (1.0) Socket AM2 NVIDIA GeForce 6100S Micro ATX AMD Motherboard. This motherboard has the advantage of builtin graphics that is adequate for 1280x1024 resolution, so you don't need to buy a separate video card if you are just doing basic text processing.

AMD Athlon 64 3000+ Orleans 1.8GHz Socket AM2 Processor Model ADA3000CNBOX - Retail. The "retail" part is important. It means that it comes with a fan. If you buy "OEM" then you will have to buy a fan separately.

Kingston 1GB 240-Pin DDR2 SDRAM DDR2 667 (PC2 5300) Desktop Memory Model KVR667D2N5/1G

Western Digital Caviar SE16 WD2500KS 250GB 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drive


I was able to install Ubuntu 7.04 the first time I booted up the system.



Note that many recent motherboards have only one IDE connector and so can support at most two IDE devices. The supplied cable may not allow connecting both a cdrom/dvd drive and a hard disk drive. For example, when I upgraded another box to use a a new motherboard, I found it necessary to buy a SATA cdrom drive so I could use an IDE-type hard disk. If you are starting from scratch then I would recommend using SATA technology.

---

