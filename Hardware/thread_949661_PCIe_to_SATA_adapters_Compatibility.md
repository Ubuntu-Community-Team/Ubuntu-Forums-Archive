---
title: "PCIe to SATA adapters: Compatibility"
date: 2008-10-16
forum: Hardware
---

### Post by AusIV4 on 2008-10-16
I'm starting to run out of disk space on my MythTV box, and all of the IDE and SATA ports on my motherboard are taken up. Hoping to add a few drives to my system, I've started looking at PCI-Express to SATA cards. 

While I've found a wide variety of cards on Newegg, I haven't been able to find much information on which cards (if any) work well under Linux. I don't need RAID capabilities, as I'll be adding these disks to an existing software RAID. I'm looking to keep costs relatively low, so I don't need anything fancy - anything that has two SATA ports and runs on Linux suits my needs just fine.

---

### Post by markbuntu on 2008-10-16
I have a SIIG SATA PCI card on my machine. It is plain PCI and it seems to work and I can access the drives on it but I think it is causing me some problems with the boot sectors on the disks attached to it where I have some Ubuntu distros installed, Grub errors, etc. I have to boot them from the bios, even chainload fails to work with these drives. It has its own bios which runs after the regular bios and I think that may be part of the problem. I should probably look for a bios update for it....

If you are just using it for storage though, it will probably work OK since I have no problem accessing the files on the disks from my other distros on the "main" hard drives attached to the mobo and it seems pretty fast for that though I have not run any benchmarks or anything. It worked OOB and caused me no problems with the other drives or OSs. 

It is cheap too, which is why I bought it. Figured I could just toss it if it didn't work and no big loss but I am using it somewhat. If someone knows of one that really works for everything please help us out here.

---

