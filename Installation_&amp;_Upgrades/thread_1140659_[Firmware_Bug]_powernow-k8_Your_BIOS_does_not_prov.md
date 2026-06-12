---
title: "[Firmware Bug] powernow-k8: Your BIOS does not provide ACPI _PSS objects"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by ea185028 on 2009-04-27
[Firmware Bug] powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your bios vendor

My current System Configuration is: 

Dual Vid Cards - GeForce 8600GT 680M 256MB DDR3 PCIEXXX
Motherboard - ASUS M2N-SLI Deluxe
2x - OCZ 1GB DDR800

After installing Hardware Drivers for NVIDIA (180) it prompted me to restart.. So I did.

Then after that it gave me this error.

Is there anything I can do to get through this, or are there any fixes for this? 


I'm a totally complete Ubuntu newbie so, detailed step by step instructions are very much appreciated.. Thank YOU

---

### Post by cariboo on 2009-04-27
It's a problem with the BIOS, I have the same problem, I went through trying to repair the problem with one of the kernel devs, in the end the only solution was to update the bios and complain to my motherboard manufacturer. I still have the problem, but except for waiting an extra second for the message to display every thing works as it should.

I suggest you do a bios update.

---

### Post by Omega_Spectral on 2009-04-30
same problem over here. I installed the "latest" bios from ASUS (idiots) and still no fix

---

### Post by kulight on 2009-06-01
i have the same issue with an msi board...

---

### Post by mkramer on 2009-07-03
Same issue here.  Asus M2N SLI Deluxe.  I upgraded to the latest BIOS from their website.  (1701).  Ubuntu 7 and 8 worked great.  The ubuntu 9 live CD doesn't work at all (install, live trial, and disc verify give the same error).

Considering that 7 and 8 work, is it certainly a firmware error?

---

### Post by RJARRRPCGP on 2009-07-03
This looks like the kernel may be broken! 

Because that shall never occur with a motherboard that was out before 9.04!

And I don't have this problem with my Asus P5QL Pro.

It don't look like the M2N series is newer than the P5Q series.

---

### Post by mkramer on 2009-07-03
I resolved this by enabling Cool 'N Quiet in the BIOS, which made the _PSS tables available to Linux.  (However, I ran into another hardware problem and gave up with the install. :))

---

### Post by Incitecite on 2009-07-17
I ran into this exact same problem as well after I installed and updated jaunty. I was able to get it to boot once with kernel 2.6.28-11. I haven't been able to get it to boot again though. Kernel 2.6.28-13, which I think was installed when I ran the updater, hasn't successfully loaded once though. 

My system is:

AMD 3800+ X2 @ 2Ghz
2Gb DDR400 RAM
Epox 9NPA+SLi Mobo
2 EvGa 7800GT's in SLI
Seagate 160Gb EIDE HDD
WD Caviar 500Gb HDD

I've been reading this is a BIOS issue. I have the latest BIOS for my mobo, but they were released in 2006 :/

I also read somewhere that this was fixed with a newer Kernel? Won't do much good If I can't boot into Ubuntu though. Every time I try to load it gives me the aforementioned error and a console. I really hope there's a fix to this...

---

### Post by couzin2000 on 2009-07-18
> **mkramer said:**
> I resolved this by enabling Cool 'N Quiet in the BIOS, which made the _PSS tables available to Linux.  (However, I ran into another hardware problem and gave up with the install. :))

Same thing for me - enabled Cool 'N Quiet, and the problem disappeared.

(Now if I could only get my Nvidia card to work...)

---

### Post by swordfishRU on 2009-08-20
With Asus M2N-MX SE Plus mainboard the problem was in MCP61 ACPI HPET TABLE setting. You've to disable this function.

---

### Post by talishka on 2009-09-04
Well, it's true if you active Cool'n'Quiet the error goes away. I just did it ant it works.
Before doing this i was havin some other issues, suddenly after a few hours i started to have I/O errors and then the file system becomes read only. 

I suspect this is a hardware problem, i've already tested with 4 sata harddrivers, and updated to the latest bios (m2n68-am se2 0901) and still happens.

I'll gonna try to change the motherboard and the power.

---

