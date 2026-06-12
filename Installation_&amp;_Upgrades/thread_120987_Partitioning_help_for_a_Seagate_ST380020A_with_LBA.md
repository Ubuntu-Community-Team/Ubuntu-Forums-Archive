---
title: "Partitioning help for a Seagate ST380020A with LBA support through BIOS, 80G"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by RavenOfOdin on 2006-01-24
Hi. . .I think I've worked out a decent partitioning scheme for my drive (a 80GB Ultra ATA-100 Seagate with 5400 RPM) but I'd like some opinions.

D: HP_RECOVERY FAT32 5.01 GB
C: HP_PAVILION NTFS 51.4 GB
* Linux swap ext3 512 MB
* Linux native ext3 17.5 GB

Latter existing on ending half of drive since LBA supposedly allows boot from beyond the 0-1024 cylinder or 8.5 gigabyte limit, and I don't want to make things harder for the pre-existing recovery partition.

Or I think I could try these steps:

. Installing BootIt NG to hard drive ([http://terabyteunlimited.com](http://terabyteunlimited.com))
. Removing the 7.4 MB (unallocated) "primary" partition which shows up via PartitionMagic 8.0
. Turning off the "Limit Primaries" option in BootIt
. Declaring D: a Multi-OS boot partition

Anyone have ideas as to which could leave me better off?

---

### Post by Ocxic on 2006-01-24
you can get rid of your D: HP_RECOVERY partiton, it's basically useless as your recovery disks you get will work. 
scince d: is so small, you could make a /boot partition for your grub files around 500MB should be good
(caution, somtimes thiss will install grub to /boot/boot/grub instead of /boot/grub)
and partiton the rest of D: for your /home partition, and use the rest of you disk for the linux install. that will let you use the most out of your hard drive while still alowing you to dual boot.

---

### Post by RavenOfOdin on 2006-01-24
[QUOTE=Ocxic]you can get rid of your D: HP_RECOVERY partiton, it's basically useless as your recovery disks you get will work. 
scince d: is so small, you could make a /boot partition for your grub files around 500MB should be good
(caution, somtimes thiss will install grub to /boot/boot/grub instead of /boot/grub)
and partiton the rest of D: for your /home partition, and use the rest of you disk for the linux install. that will let you use the most out of your hard drive while still alowing you to dual boot.[/QUOTE]

No can do. I don't have recovery disks, comp wasn't sent with recovery disks, and most importantly I'm not in a position to have recovery disks sent to me.  I looked into burning a set of recovery disks a while back but got little to no information that I could actually use.

I assume you meant "use the 17.5 GB for the Linux install."

---

### Post by dueY on 2006-01-24
[QUOTE=RavenOfOdin]

D: HP_RECOVERY FAT32 5.01 GB
C: HP_PAVILION NTFS 51.4 GB
* Linux swap ext3 512 MB
* Linux native ext3 17.5 GB
[/QUOTE]

So what seems to be the problem here?  Those partitions look fine. :confused:

---

### Post by RavenOfOdin on 2006-01-24
[QUOTE=dueY]So what seems to be the problem here?  Those partitions look fine. :confused:[/QUOTE]

No problem, I just wanted opinions. Thanks for chipping in.

---

### Post by sir_cheats_a_lot on 2006-01-25
That is because with the new HP's you have to burn your recovery CD's yourself (six in total on the new ones i believe)  i don't remember exactly how to do the process  check your manual or HP's website to find out.

---

