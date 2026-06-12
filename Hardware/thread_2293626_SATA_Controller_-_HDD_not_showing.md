---
title: "SATA Controller - HDD not showing"
date: 2015-09-06
forum: Hardware
---

### Post by ipillinger on 2015-09-06
Hi,

I recently purchased a SATA controller so I could add more hard drives to my media server/storage machine. 

The controller is a [StarTech 2-Port SATA 6Gbps PCI Express Controller]("http://www.startech.com/uk/Cards-Adapters/HDD-Controllers/SATA-Cards/2-Port-PCI-Express-SATA-6-Gbps-Controller-Card~PEXSAT32") which uses the Marvell 88SE9128 chipset. On the StarTech page it lists the card as being compatible with Linux. I've tried contacting their support but have not had any response.

I'm running Lubuntu 14.04.

The motherboard's BIOS is set to AHCI and I can see the controller's BIOS during boot when a drive is connected. I can also enter this BIOS and see the attached HDD.

When in Lubuntu I cannot see the attached drive in Disk (DiskUtility) or Gparted. However, the drive works fine when connected to a motherboard SATA port. The drive is formatted with EXT4.

When I run the command: 
```
lspci -v
```

I can see the controller listed and using the AHCI driver:
```
01:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9123 PCIe SATA 6.0 Gb/s controller (rev 11) (prog-if 01 [AHCI 1.0])
    Subsystem: Marvell Technology Group Ltd. 88SE9123 PCIe SATA 6.0 Gb/s controller
    Flags: bus master, fast devsel, latency 0, IRQ 50
    I/O ports at e040 [size=8]
    I/O ports at e030 [size=4]
    I/O ports at e020 [size=8]
    I/O ports at e010 [size=4]
    I/O ports at e000 [size=16]
    Memory at fea10000 (32-bit, non-prefetchable) [size=2K]
    Expansion ROM at fea00000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
```

Whilst I do have a fair amount of experience with Ubuntu-based distros, and I'm comfortable using the command line, I'm by no-means an expert and could do with a little help with this.

Thanks.


**UPDATE**

After running both the Ubuntu and Lubuntu Live images, the drive connected to the controller was appearing as normal. So it would seem that there is something wrong with my current installation of Lubuntu. As my OS is on its own drive, I think the easiest thing to do would be to perform a fresh reinstall. I'll come back and edit this post with another update and hopefully mark it as solved.

---

### Post by mike_johnson2 on 2016-02-13
I saw this post was marked as solved. But, it didn't help me much because I didn't see the solution posted anywhere.
I had a similar problem with a four port Startech card, and finally figured out a solution which I posted.
So, if you or anyone still needs help you can check my answer here;
[http://ubuntuforums.org/showthread.php?t=2312863&p=13439099#post13439099](http://ubuntuforums.org/showthread.php?t=2312863&p=13439099#post13439099)

---

### Post by RobTheBold on 2016-06-09
Too bad this question didn't get updated with a more detailed solution. I had a very similar problem with a Marvell 88SE9172 eSATA controller on my Kubuntu machine's motherboard. Some mad googling found a bunch of stuff that didn't work, but also hinted that there was an Intel IOMMU bug that kept such eSATA ports from operating as AHCI devices (and therefore showing up as ATA drives). Even though I have an AMD-based MB, I was out of good ideas and I tried disabling IOMMU in the BIOS settings and adding GRUB_CMDLINE_LINUX="iommu=soft" to /etc/default/grub. After a reboot, the external drive showed up as a proper SCSI device and could be mounted with no problems.

---

