---
title: "Advice for WinXP/Ubuntu Intrepid Dual boot on RAID disk"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by mat106 on 2009-03-10
Hi

I've been using Windows for many years and more recently have been trying out Ubuntu 8.10 using VMWare. I now want to take a step further and install Ubuntu but want a Windows XP Professional / Ubuntu Intrepid dual boot system. I've read quite a bit of the documentation but need some advice/confirmation about how to do things. 

The system on which i want to set things up is currently running Windows XP Professional but i don't mind reformatting and starting everything from scratch (i would actually prefer it in fact) since all my data is backed up on external disks.

This is the system on which i'd like to set things up (not all info is probably relevant but anyhow...)

1. Dell XPS 710
2. Core 2 Quad-Core Processor QX6600 (2.4 GHz, 1066FSB, 8Mb Cache)
3. RAM - 4GB (4x1Gb) 667 Mhz DDR2
4. Hard drive - 640GB Serial ATA Raid 0 "Stripe" (2x320GB) Dual HDD Config 
5. Graphics Card - DUAL 256Mb nVidia 8600GTS

Don't really mind whether the hard disk stays as Raid 0 or becomes Raid 1 - Given that i actually store most of my data on external backed up drives i'd like to go for the configuration that would give the best performance. I think the hard disk is a FakeRAID but i'm not sure. Can anyone advice on how to check and subsequently how it affects the documentation i should follow for the set up process?

This is the kind of setup i'm after (if not recommended for some reason please say so :))

1. Dual boot Windows XP Professional 32bit / Ubuntu Intrepid (64bit if possible)
2. Each operating system on it's own partition (Primary, Extended, Logical, NTFS, FAT32 etc... need some advice on that) so that i can easily re-install/upgrade.
3. Data for each operating system on a separate partition (e.g. /home on it's own partition?)
4. Ability to share data between OS (by having a shared partition?)

I've already read through the following articles 

1. Windows Dual Boot ([https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot))
2. InstallationSoftwareRAID ([https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID))
3. How to Partition ([https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition))
4. FakeRaidHowTo ([https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto))
5. Various articles from [http://reformedmusings.wordpress.com](http://reformedmusings.wordpress.com)

but the RAID and Partitioning stuff i'm not sure about and therefore need guidance on which how-to/articles/parts-of-articles i should be following to set up the configuration i want. I think the FakeRaidHowTo is what i need to follow but i'm not sure.

For example, in the Windows Dual Boot how-to it states that it's easier to start by installing windows and then partition to install Ubuntu but there's no mention in there about RAID disks. In the FakeRaidHowTo in doesn't talk about installing windows first. Also i'm not sure for example whether after doing step 2 in FakeRaidHowTo whether i also need to do step 5.

As i said further up, i don't mind formatting and starting fresh both as a learning process and in order to get things "right"

Thanks, in advance, for your advice.

---

