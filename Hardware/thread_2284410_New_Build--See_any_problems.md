---
title: "New Build--See any problems?"
date: 2015-06-29
forum: Hardware
---

### Post by john409 on 2015-06-29
I probably should have checked here first!

I just ordered a new sytem and am planning on running it with Ubuntu[B].
[/B]Does anybody see any issues with my choices? I have always used pre-built systems before.[B]

Case -[/B] Corsair Obsidian 750D Black Aluminum / Steel ATX Full Tower Computer Case
**Motherboard -** ASRock 990FX Extreme9 AM3+ AMD 990FX + SB950 8 x SATA 6Gb/s USB 3.0 ATX AMD Motherboard with UEFI BIOS
**CPU - **AMD FX-8350 Black Edition Vishera 8-Core 4.0GHz (4.2GHz Turbo) Socket AM3+ 125W FD8350FRHKBOX Desktop Processor
**Power - **CORSAIR RM Series RM750 750W ATX12V v2.31 and EPS 2.92 80 PLUS GOLD Certified Full Modular Active PFC Power Supply
**RAM - **CORSAIR Vengeance Pro 16GB (2 x 8GB) 240-Pin DDR3 SDRAM DDR3 1866 Desktop Memory Model CMY16GX3M2A1866C9R (Red)
**Graphics - **GIGABYTE GV-R927XOC-2GD Radeon R9 270X 2GB 256-Bit GDDR5 PCI Express 3.0 HDCP Ready CrossFireX Support Video Card
**SSD - **Corsair Force LX Series CSSD-F256GBLX 2.5" 256GB SATA III MLC Internal Solid State Drive (SSD)
**SSD - **Kingston SSDNow V300 Series SV300S37A/120G 2.5" 120GB SATA III Internal Solid State Drive (SSD)
**HDD - **Seagate Barracuda ST1000DM003 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive Bare Drive
**Optical Drive - **Pioneer Black 16X BD-R 2X BD-RE 16X DVD+R 12X BD-ROM 4MB Cache SATA Blu-ray Burner BDR-209DBK

Thanks for the feedback!

---

### Post by Bucky Ball on 2015-06-29
Looks fine but no idea why you're using a 750W (though it's a good quality) power supply. Anything 80+ or better is good and will have appropriate safety switches and run virtually cold. 

Try one of the many power supply calculators and go for something more realistic. 500W should do it. Antec has a calculator and possibly Corsair have their own.

---

### Post by john409 on 2015-06-29
I had considered a 500W, but decided I may want to add that second graphics card for crossfire someday and each one is pulling 180W. 

My real concern is compatibility with the Motherboard, RAM, and CPU. I found specs on the Motherboard that does not mention support for 16GB of DDR3 at 1866, though I read that it does.

That and of course Ubuntu compatibility. I'm hoping that the components I chose are old enough to have drivers and whatnot supported. Everything I read on the AMD sight does not mention Linux only Windows.

---

### Post by Yellow Pasque on 2015-06-29
CrossFire isn't supported on Linux. Even on Windows, I question "future-proofing" a system for CF/SLI. I'd rather spend the money on a better single GPU.
So 750W is overkill and I highly doubt you'll ever make use of 16GB of RAM unless you regularly use VM's or do something else specialized. Going overboard on the amount of memory doesn't make sense like it used to.
Other than that, it looks okay to me. All of the major chipsets (northbridge, soutbridge, LAN, and audio) have been supported in Linux for a while. It will be a bit hot/noisy, but if you use pre-built systems, you're probably used to that.
The only Linux-specific snafus I can foresee are needing to work around USB3 issues (Gigabyte boards using the 990FX have issues with that) and maybe the mobo's sensor chip won't be supported, depending on which specific one they use. (But, at the very least, the sensor built into the CPU should work.)

> My real concern is compatibility with the Motherboard, RAM, and CPU. 
The CPU is supported by the mobo in all BIOS revisions, and the official specs list support for up to 64GB of DDR3-2400, so it should be okay. They don't list DDR3-1866 explicitly, but if they list 2100 and 2400, they probably just forgot it.

---

### Post by john409 on 2015-06-29
Hmm...I didn't realize crossfire was not a Linux ability. Would I be able to use SLI?

I don't actually have any USB 3.0 devices yet anyways, so maybe that will be ironed out before I get to it.

I'm glad to hear the RAM should be fine. It was on sale so I got 16 Gb for only a few bucks more than 8 Gb. It seemed like overkill to me too, but ... it was inside my budget.

i already ordered the power supply, so I guess I'm stuck with it, unless I return it and wait for another to arrive. I'll take a close look at it. Does a bigger power supply use more electricity even if my system isn't demanding it? (Thinking of the utility bill)

---

### Post by john409 on 2015-06-29
I have been using pcpartpicker.com to help with the build. It says I am using 100W-418W of power. So should I go a little over at 500W or is 450W enough?

---

### Post by oldfred on 2015-06-29
Some have issues with Asrock and its asmedia ports, even if DVD is plugged into a asmedia port.
And some systems have IOMMU issues. Not sure if your motherboard has that or not.

 Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677)


 Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)

---

### Post by john409 on 2015-06-29
Thank you for the Secure Boot link, I probably would have been pulling out my hair trying to get it to boot from a thumb drive with my Ubuntu install without that.

I will have to see if the IOMMU is an issue??? How am I supposed to access the command line to make a change like that in an initial install if it does not start?

---

### Post by Bucky Ball on 2015-06-29
> **john409 said:**
>  Does a bigger power supply use more electricity even if my system isn't demanding it? (Thinking of the utility bill)

Yep. At least it's 80+ meaning it is fairly enery efficient. Generic silver box PSUs are generally <70%, which is why they're hot (they create heat from the energy you're paying for instead of using all of it to power your computer).

---

### Post by oldfred on 2015-06-29
Originally the IOMMU was only Gigabyte boards, so not sure you even have issue.
But now have seen several others with the issue.
My Asus Intel based motherboard did not have that issue, but I did have a lot of UEFI settings to change to get it to work well.

But with those it was a UEFI setting. And there are boot options at grub menu to use soft IOMMU.

Best to install Ubuntu in UEFI boot mode, but with secure boot off.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Lots of links to useful UEFI install info in link in my signature if interested.

---

### Post by john409 on 2015-06-29
So I looked at the Motherboard documentation and it does mention IOMMU,  but only says that it is set at a default value of [Disable], so...I  guess I will have to wait and see?

---

