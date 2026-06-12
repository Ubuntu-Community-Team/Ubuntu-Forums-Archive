---
title: "Ubuntu on my Laptop - Some Questions"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by DieseL1988 on 2007-05-11
Ok first things first, heres the spec of my laptop...

Inspiron 6400 Dual-Core Processor T2080(1.73GHz/533MHz/1MB)
Wide Sreen 15.4" WXGA (1280x800) TFT Display
Memory Dual-Channel 1024MB (2x512) 533MHz DDR2 SDRAM
Hard Drive 60GB Serial ATA (5400 RPM)
Fixed Internal 8X DVD+/-RW Drive including software, for Vista only
Battery Primary 6 cell 53W/HR LI-ION
Graphics Card Intel Media Accelerator 950 Up to 256MB of shared Memory with TV and S-Video Output
Dell Wireless 1390 802.11b/g 54Mbps Mini-PCI Wireless Card, for Dual Core Processors

-----------------

OK, so what I want to know is...

Will Ubuntu run on this laptop? and will all my hardware work like it does in windows?

Does Ubuntu support widescreen? (I tried the live CD and it looked ugly)

What kind of wireless support would I get? for example would I be able to search for broadcasting networks etc. like I can in windows.

Will Beryl run on this laptop? and how well do you think it would run?

Lastly - I have a 10GB partition which is currently Dell's "recovery" drive. Well I have all the driver discs etc. so I could probably format that, would it be big enough to install ubuntu on? (for testing purposes)

---

### Post by kthijs on 2007-05-11
Well I don't know about compatibility, but Ubuntu does support 1280x800 if your graphics driver works ok.
And 10 gb is enough to install Ubuntu and play around with it a bit.

---

### Post by kebes on 2007-05-11
> **DieseL1988 said:**
> 
Will Ubuntu run on this laptop? and will all my hardware work like it does in windows?
According to the Hardware compatibility list:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)
The Inspiron 6400 does work with Ubuntu. Unfortunately, there are one or two glitches that need to be fixed manually before everything will work perfectly.


> Does Ubuntu support widescreen? (I tried the live CD and it looked ugly)
This is a known issue with a known solution. The solution is described here:
[https://wiki.kubuntu.org/LaptopTestingTeam/DellInspiron6400?highlight=%28laptop%29%7C%28dell%29#head-8d3c168d75967466e4d7835b0c263000c60536fe](https://wiki.kubuntu.org/LaptopTestingTeam/DellInspiron6400?highlight=%28laptop%29%7C%28dell%29#head-8d3c168d75967466e4d7835b0c263000c60536fe)


> What kind of wireless support would I get? for example would I be able to search for broadcasting networks etc. like I can in windows.
Once wireless is enabled, yes it will auto-detect nearby networks. From what I can see in the hardware docs, wireless should work on that laptop with the latest version of Ubuntu.

> Will Beryl run on this laptop? and how well do you think it would run?
Looking at your specs, I think Beryl would run just fine. (It is, however, beta software so there will be bugs! You have been warned! :)

> Lastly - I have a 10GB partition which is currently Dell's "recovery" drive. Well I have all the driver discs etc. so I could probably format that, would it be big enough to install ubuntu on? (for testing purposes)
10 GB is big enough for a standard Ubuntu install (typically uses up ~4Gb before you start installing tons of software and accumulating files). The Ubuntu installer can also resize existing partitions (backup your data first, just in case!) so that is another option. Of course you need to have enough free space on the partition you're about to resize.


I realize that the links I provided above might look cryptic if you've never used Linux before. If you have any further questions, the forums are here to help you in any way we can! Good luck...

---

