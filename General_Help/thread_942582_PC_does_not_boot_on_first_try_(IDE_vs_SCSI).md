---
title: "PC does not boot on first try (IDE vs SCSI?)"
date: 2008-10-09
forum: General Help
---

### Post by abeeber on 2008-10-09
Good day everyone,

I have a strange problem. I have installed ubuntu (various iterations of it using the 8.04 version with the latest kernal) on a P4 PC using an ASUS P800 motherboard with a GE7300 AGP video card.

The installation works well and I typically patch the machine up to the latest and greatest.

However, when I go to use the machine again say after a couple of hours, it fails to boot on the first try. Typically the splash screen seems to hang and there is no disk IO. In troubleshooting this issue I noticed an error - ATA1 is slow to respond.

When I force a reboot, the boot process works fine with plenty of disk IO.

When I look at Grub and the disk configuration in general I noticed that my IDE HDD devices are listed as SCSI devices and not IDE devices so that under ubuntu they are listed as SDA1 vs HDA1 and mounted under /media instead of /mnt.

So my questions are: 
1. How do I configure the OS so that it boots first time? Is the ATA1 is slow to respond error the issue and if so how to I fix that? I have not found a good fix for this as yet.
2. Is the detection of IDE drives as SCSI drives an issue relating to my first question? Can I change the OS so my IDE devices are listed as HDA devices?

Thanks in advance for any help. I appreciate the help.

Andrew Beeber

---

