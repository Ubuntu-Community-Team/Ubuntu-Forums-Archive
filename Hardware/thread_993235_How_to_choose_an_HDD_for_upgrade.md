---
title: "How to choose an HDD for upgrade"
date: 2008-11-25
forum: Hardware
---

### Post by tezer on 2008-11-25
Hello!
I have a computer which is used as a Samba/FTP server. Currently it has one 80Gb HDD which is not enough. I am thinking about buying another one of a bigger size. The problem is I do not know what is the maximum size (and type) of HDD the system can support (bios first of all), as the computer is rather old.
So here comes the specifications:

```
Dell Precision Workstation 450

BIOS Information
	Vendor: Dell Computer Corporation
	Version: A00
	Release Date: 11/07/2002

Base Board Information
	Manufacturer: Dell Computer Corp.
	Product Name: 09N167

HDD currently installed:
/dev/sda1
Model Family:     IBM/Hitachi Deskstar GXP-180
Device Model:     IC35L090AVV207-0
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 3a

```
So my questions are:
1. Do I need IDE or SCSI?
2. What is the biggest size supported by BIOS?
3. Should I upgrade the BIOS?
4. Can you recomment (or not recommend) any particular model of HDD?

Thanks in advance!

---

### Post by cariboo on 2008-11-25
Size doesn't matter, you can use a big a hard drive as you can afford. If you are using IDE, I would stick with IDE.

Your bios doesn't need to be upgraded if you are only using the computer for Linux. Several years ago I had a dual 223Mhz processor mother board that could only see a maximum of 32Gb. As larger disks became available I just put larger capacity disks in it. When I retired it was running 4 80Gb hard drives with no problems at all.

As for recomendations go, almost all hard drives are fairly reliable, I would suggest getting one with at least a 3 year warranty.

Jim

---

### Post by tezer on 2008-11-25
> **cariboo907 said:**
>  If you are using IDE, I would stick with IDE.

Thanks for your advice. But I am a little bit confused: I thought my HDD is IDE, but I read that /dev/sda1 stands for the SCSI drives. So what do I have?:confused:

---

