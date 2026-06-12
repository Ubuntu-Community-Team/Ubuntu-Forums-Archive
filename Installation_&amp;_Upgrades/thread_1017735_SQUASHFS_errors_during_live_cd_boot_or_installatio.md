---
title: "SQUASHFS errors during live cd boot or installation"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by m_a_b on 2008-12-21
I am trying to install ubuntu 8.04 or 8.10 on a desktop system, and I am getting all kinds of errors but don't really know how to troubleshoot them.  The main thing it is doing is taking forever to load, so I restarted and repressed the splash screen and it appears that I am getting a bunch of squashfs errors.  I assumed that means i/o problems and booted back into windows and searched and sure enough, I think that it the problem.  

I am using an MSI 975X Platinum V2 MB with a Jmicron controller and ICH7DH.  The configuration I am using is my boot drive is a sata WD Raptor drive not using raid.  I also have an IDE storage drive on the Jmicron controller.  The cd drives are also on the IDE controller.  

```
On-Board IDE
  	  	
One Ultra DMA 66/100 IDE controller integrated in ICH7DH and JMicron JMB361
• 	Supports PIO, Bus Master operation modes
• 	Can connect up to 2 Ultra ATA 100 drives on IDE1 & 2 Ultra ATA133 drives on IDE2 (powered by JMicron JMB361 controller)
  	 
Serial ATAII controller integrated in ICH7DH
• 	Up to 300MB/s transfer speed
• 	Can connect up to 4 Serial ATA II drives
• 	Supports ACHI controller with SATAII RAID 0, 1, and 0+1
• 	Supports SATAII hot plug
  	 
JMicron JMB361 chipset
• 	Supports RAID 0, 1 and JBOD (onboard SATA5 & IDE2 connector)
• 	Can connect up to 2 Ultra ATA 133 drives on IDE2 & 2 SATA drives on SATA5 
```

So, my question is how can I get past this?  I have heard of people specifying specific drivers and things during installation, but I don't know how or what drivers to use.  Any help?

Here is my system configuration in case you need it:

```
MSI 975X Platinum V2
EVGA 256-P2-N624-AR GeForce 7900GS 256MB 256-bit GDDR3 PCI Express x16 SLI Supported Video Card
Western Digital Raptor WD1500ADFD 150GB 10000 RPM 16MB Cache SATA 1.5Gb/s Hard Drive (BOOT DRIVE)
CORSAIR XMS2 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory
Intel Core 2 Duo E6600 Conroe 2.4GHz 4M shared L2 Cache LGA 775 65W Dual-Core Processor
2 IDE CD drives, and 1 320 gb IDE HD just for storage capacity.

```

Please help!

---

### Post by snova on 2008-12-21
SquashFS is a filesystem used on the CD to store more data on the CD than would otherwise be possible, by compressing it.

It's probably a bad burn. First make sure you downloaded it without problems (check the md5sum: [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")), then try burning it again at a slow speed (4x, 2x, or even 1x).

---

### Post by m_a_b on 2008-12-21
the disk is good, I am sure of it.  I have used it before. I also downloaded the iso again and re-burned it just in case it somehow got scratched or something, but it did the same thing.  I am pretty sure it has to do with the i/o controller after doing some reading, but the people that fixed it didn't really say how they fixed it other than some really general statements.

---

### Post by m_a_b on 2008-12-21
some new info on the problem:

I decided to try turning of UDMA on the ide channels, so that would affect the CD drives and the storage HD and I did not get any squashfs errors this time.  So, that pretty much confirms a driver problem of some sort with the I/O controller.  

However, instead of booting into the gui, it booted to a terminal, tried to go to the gui a few times, then gave me the error: 

"The display server has been shut down about 6 times in the last 90 seconds.  It is likely that something bad is going on.  Waiting for 2 minutes before trying again on the display :O."

So does this mean that not only is there an I/O problem but also a graphics card incompatibility too?  Maybe this system just isn't right for linux?

---

### Post by m_a_b on 2008-12-22
anyone?

---

### Post by CRIMPS on 2009-02-25
I was receiving a ton of SQUASHFS errors when trying to install as well.  What I found, thanks to this [post]("http://ubuntuforums.org/showthread.php?t=993763&highlight=squashfs+error") is that my CDRom drive didn't recognize CD-R media.  The CD player was quite old, manufactured in 2001.  So, I swapped in a different CD player and I was able to install without issue.  

Hope this helps

Z

---

