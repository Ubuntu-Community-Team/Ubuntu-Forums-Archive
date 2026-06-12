---
title: "HDD Size Is Much Smaller Than Listed"
date: 2009-07-18
forum: Hardware
---

### Post by maporojo on 2009-07-18
I got a SONY VAIO FW490. It has Intel® Core&#8482; 2 Duo Processor P8700 (2.53GHz), 4GB DDR2-SDRAM, and ATI Mobility Radeon&#8482; HD4650 graphics card with 512MB vRAM. The HDD size is listed as 320GB. It came pre-installed with Windows Vista Home Premium. I created restoration disks and confirmed the HDD size was 320GB with about 10GB of the 320GB being used as a recovery partition.

Firstly, I installed Jaunty Jackalope (JJ) by creating a partition for it. Secondly, I decided to use the entire disk for JJ and I did this by using Partition Editor on an Ubuntu Live CD to format the partitions and then re-install JJ on the entire disk. After installation was complete, Partition Editor showed the entire disk space to be only ~300GB with ~11GB for swap.

Question 1: What happenned to the remaining ~20GB and how may I recover them?

I tried using the restoration disks created hoping to restore the system but found out that one of the DVD's is missing "critical" files and the process could not be continued. Therefore, no OS is installed at the moment.

The BIOS (by American Megatrends) shows that the HDD is 320GB but gparted cannot see the other ~20GB.

Question 2: Is there a utility that I can burn to a CD and use to format the HDD much like older desktops used to come with diskettes that allow one to format the HDD and be left with only the BIOS?

---

### Post by CREEPING DEATH on 2009-07-18
Gigabytes vs. gibibytes.  Some 'loss' is normal, merely formatting the drive takes capacity away.  It should be noted that EXT3 is more efficient than NTFS concerning this though.

CD

---

### Post by maporojo on 2009-07-18
I still think that ~20GB is a rather substantial amount to lose as a result of a single partitioning excercise. I had a 1GB RAM Pentium 4 machine with only 40GB before and I never experienced such a loss yet I partitioned it very many times.

---

### Post by Sarai the Geek on 2009-07-18
> **maporojo said:**
> I still think that ~20GB is a rather substantial amount to lose as a result of a single partitioning excercise. I had a 1GB RAM Pentium 4 machine with only 40GB before and I never experienced such a loss yet I partitioned it very many times.

It's the age old gb vs gib problem. Google GB vs GiB for a complete explanation!

---

