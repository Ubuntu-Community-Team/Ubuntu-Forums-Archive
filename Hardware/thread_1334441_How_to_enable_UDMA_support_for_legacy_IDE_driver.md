---
title: "How to enable UDMA support for legacy IDE driver?"
date: 2009-11-22
forum: Hardware
---

### Post by Teleken on 2009-11-22
Hello everyone!

I have an Intel SS4200-E NAS that is basically a stripped down computer with ICH7R, a single PCIe1x slot, 2xPATA 4xSATA 2xeSATA.  Long story short I have installed ubuntu 9.1 server x64 on a 6.4GB old 2.5" IDE drive so that I can use all the SATAs for raid.

It took much work and futzing but the only way that I was able to get the system to recognize both the IDE and SATA drives was to compile in the old IDE support and disable PATA support for the new driver.  Otherwise it would refuse to detect any of the PATA devices despite whatever bios setting I threw at it.

The only way that it partially worked was to have the bios IDE mode set to "compatible" in which case I got my IDE devices with full UDMA33 (so I know that it works) but only one of the SATA devices would show up.

I have searched through the kernel settings but cannot find anything to try to enable UDMA on the IDE device.

hdparm and /proc/ide show that DMA is disabled and it won't let me enable it.  I get about 2MB/sec read which is dismal (vs 15MB/sec with bios in compatibility mode).  Trying to use hdparm to enable DMA just throws an IDE error, yet hdparm -i indicates that mdma2 mode is active (but not UDMA2 - which does show up in compatibility mode).

Does anyone have any idea how to get UDMA to work with this setup?

Thanks!

---

### Post by m3741 on 2009-11-22
Holy moly. First off, from what I've read this is slightly specialized hardware. If it acts goofy, that doesn't surprise me.

On this device though, I just don't think that you can enable DMA on the IDE interface and have all of the SATA devices show up. If you read the specs on the software that comes installed with it, it loads everything into a ramdisk. The bootup is slow while the image decompresses but after that it's pretty fast. May I suggest you do the same thing with Ubuntu.

---

### Post by Teleken on 2009-11-22
Well from what I understand this is a pretty standard ICH7R with 2PATA 4SATA and an SiI3132 for the eSATA (although I could be wrong about that last part).  I can't see why UDMA would be unavailable on the IDE side of things when using any mode except for compatibility.

Yes, the stock software is setup to load into ram and execute from there, but that doesn't mean that it's a limitation of the hardware.  They also left bios settings unoptimized (for example they leave 8MB reserved for video card even though there is none), and since UDMA does work in compatibility mode there is obviously some mechanism for it to work.

The stock setup also has everything needed in a 40MB image - and I have no idea how to get ubuntu down that low.

---

### Post by m3741 on 2009-11-22
I realized that in my previous post I didn't include the link that made me think that the IDE port won't do DMA. In the interest of not stealing other people's ideas/work check out [http://ss4200.pbworks.com/Convert+SS4200-EHW+to+SS4200-E]("http://ss4200.pbworks.com/Convert+SS4200-EHW+to+SS4200-E"). While Googling around I ran into another post of yet another person having this exact same problem but I can't seem to find it again.

I know that it's not what you want to do (and I get the fact that it's the point of the matter to not do this) but you could always install Ubuntu on your SATA drives. Another option may be to start off with something like [Ubuntu MID]("http://www.ubuntu.com/products/mobile").

---

### Post by Teleken on 2009-11-22
Thanks for the links.  I've already been to the pbworks site and they don't seem to have any pointers.  I've run across several people with the problem but no solutions yet.

I just happen to have another motherboard with ICH7 chipset so I'll throw ubuntu on that and see if I have the same problem with the IDE UDMA as I'm having on the SS4200.

---

### Post by cascade9 on 2009-11-23
If you do have the same issues, maybe use a nice, cheap 8GB USB flash drive instead of a 6.4GB UDMA333 drive? The flash drive should be faster, and it will get you around these annoying issues.

---

### Post by Teleken on 2009-11-23
Thanks - I actually considered this and it's not a bad idea.  I'd still have the flash wear issues but it wouldn't be that bad.  I still want to try to get the UDMA to work on the IDE first but if not I may just end up doing that.  Thanks!

---

