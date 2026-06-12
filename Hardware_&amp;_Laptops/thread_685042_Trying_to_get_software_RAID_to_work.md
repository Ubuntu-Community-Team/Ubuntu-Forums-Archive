---
title: "Trying to get software RAID to work"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by murbanci on 2008-02-01
I am currently running Ubuntu 7.10 and am trying to link two drives using RAID 0.  I have tried following [this tutorial]("http://ubuntuforums.org/showthread.php?t=408461&highlight=software+raid"), however when i enter the command to configure raid using mdadm i get this error:
```
mdadm: failed to create /dev/md0

```

I checked to make sure that /dev/md0 exists and it does so what am i doing wrong?  Thanks for your help.

---

### Post by jmate24 on 2008-02-02
what's the specs and manufacture(dell, hp, etc...) of your computer, what are the two hard drives manufacturers and whether or not they are IDE or SATA, and how old is are the drives and your computer?

---

### Post by murbanci on 2008-02-02
> **jmate24 said:**
> what's the specs and manufacture(dell, hp, etc...) of your computer, what are the two hard drives manufacturers and whether or not they are IDE or SATA, and how old is are the drives and your computer?

ASRock 4CoreDual-SATA2 LGA 775 VIA PT880 Pro/PT880 Ultra ATX Intel Motherboard
GIGABYTE GV-NX72G512P1 GeForce 7200GS 128MB 32-bit GDDR2 PCI Express x16 SLI Supported 
       Video Card
Intel Pentium D 925 Presler 3.0GHz LGA 775 95W Dual-Core Processor
Seagate Barracuda 7200.10 ST3250310AS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive   x2

Everything is about 2 months old.

---

