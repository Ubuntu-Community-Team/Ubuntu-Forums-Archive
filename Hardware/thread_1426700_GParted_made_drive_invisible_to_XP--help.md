---
title: "GParted made drive invisible to XP--help"
date: 2010-03-10
forum: Hardware
---

### Post by BobSongs on 2010-03-10
**System**: Compaq Presario C795TU Laptop

**Situation**: GParted was used to blank the HDD. (**Device** > **Create Partition Table**... , under "Advanced" drop-down button: Select new partition table type, **MSDOS** was chosen. ). The idea was: eliminate all existing partitions, create new ones for WinXP SP2 and Ubuntu. As we all know and love, XP must be installed first. However, when the Windows XP Setup (from CD ROM) reaches the point where it detects the drives, it claims there are no internal HDDs.

The GParted used was from **Puppy Linux**, most recent release. Since this point the Ubuntu ISO was downloaded, will be burned with its copy of GParted tested. Hopefully, it may have better results. However, assuming that Ubuntu cannot reset the drive to allow XP's Setup software to see it, is there a utility that might restore the HDD so that it is visible to XP's setup program? After blanking, Puppy did see the partitions that were cut. This is obviously not an issue for Linux.

I've used "Create Partition Table" under Ubuntu for my Dell Dimension 5150 without a hitch. XP & Karmic live happily side by side with Karmic purring ... and XP growling. :P So I was wondering if anyone has had this and managed to get past it.

Puppy described the HDD as sda1, so I'm assuming SATA. My HDD is SATA and XP SP2 had a successful install, no extra SATA drivers required.

Would this be a BIOS issue? I would rather doubt it. If it were, no system would see the HDD. =P

---

### Post by coffeecat on 2010-03-10
Apart from creating a partition table, have you tried creating just a single primary NTFS partition for XP? Then XP might recognise the disc. The XP install disc should be happy to install into the pre-prepared NTFS partition - I've certainly done it this way.

There shouldn't be anything wrong with the Puppy version of Gparted, but if that doesn't work I would certainly have a go with Gparted on the Ubuntu live CD. 

> **BobSongs said:**
> Puppy described the HDD as sda1, so I'm assuming SATA. My HDD is SATA and XP SP2 had a successful install, no extra SATA drivers required.

Both older parallel IDE drives and SATA drives have been designated sdx for the last two or three years - ever since the Linux kernel drivers for PATA and SATA drives were integrated. So that may not be a SATA. Whatever - XP SP2 comes with SATA drivers. It was pre-SP2 XP that you had to get up to various contortions to get it to install to a SATA drive.

Good luck!

---

### Post by BobSongs on 2010-03-10
Thanks, coffeecat

We'll try the one, single NTFS partition.

The way it was set up before, it was one large Extended partition with multiple Logical partitions within. We could return to that model. I'm just puzzled as to why XP can't see a drive that it did previously.

;-)

---

### Post by wilee-nilee on 2010-03-10
I had a similar problem with a wiped HD sata in a acer aspire netbook. I could download the drivers for this from acer, but I just changed the bios to IDE, problem solved, with no speed difference noticed.

A quick google search seems to show a driver need for XP to recognize the HD, and other available drivers for your computer.
[http://www.google.com/search?hl=en&source=hp&q=Compaq+Presario+C795TU+Laptop+sata+drivers+xp&aq=f&aqi=&aql=&oq=](http://www.google.com/search?hl=en&source=hp&q=Compaq+Presario+C795TU+Laptop+sata+drivers+xp&aq=f&aqi=&aql=&oq=)

---

### Post by BobSongs on 2010-03-10
Noted, Wilee: I'll remark that to the owner. We'll see what she says.

Thanks all.

I'll close the thread when it is successfully fixed, along with the solution we found.

---

### Post by coffeecat on 2010-03-11
> **BobSongs said:**
> The way it was set up before, it was one large Extended partition with multiple Logical partitions within.

I think that was your problem. XP can't boot from a logical partition (unless you do some gee-whiz hackery) so I guess the installer is set up not to recognise extended/logical partitions. Perhaps there is a bug in it which causes it not to recognise the disc if it's set up that way. I don't know - I'm just theorising here. When I said a single partition, make sure it's a primary of the size you want and leave the rest of the disc unallocated. Then, once you've installed XP, you can partition up the unallocated space for Ubuntu with Gparted on the live CD.

---

### Post by srs5694 on 2010-03-11
I'm not an expert on Windows installation, but I have a vague recollection of hearing that Windows will report that no drives can be found when it means that it doesn't *recognize* any *partitions* on the drives. In other words, you need to have a FAT or NTFS partition, or at least one marked with a FAT or NTFS type code (0x0c or 0x07, typically). If you created empty Linux partitions, or perhaps even an empty partition table with no defined partitions, you might trigger the behavior you report. You should be able to set up a suitable partition in GParted, or use fdisk along with mkdosfs or mkfs.ntfs, to do the job. Primary or logical shouldn't matter, although as others have said, Windows doesn't like booting from a logical partition, so your main XP partition should certainly be primary. (You can create logical partitions as data storage partitions, though.)

---

### Post by BobSongs on 2010-04-21
Essentially, the machine is a laptop that had the battery out and was using a direct link to the power lines.

A power failure caused the laptop to stop and completely messed up the Windows Registry. It was found that, upon careful analysis of the hard disk drive, a number of **bad sectors** showed up. This indicates that drive had been through a number of abuses due to both power-failures and overheating. I suppose there's only so much roasting a hard drive can tolerate before it begins to show signs of pre-mature ageing.

Thanks for the help. Bottom line: a new hard disk drive will be order & installed.

---

