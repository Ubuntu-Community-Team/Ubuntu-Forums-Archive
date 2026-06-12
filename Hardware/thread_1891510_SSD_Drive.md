---
title: "SSD Drive"
date: 2011-12-05
forum: Hardware
---

### Post by Bobhuber on 2011-12-05
Lots of horror stories out there.Recommendations on a sata 3 SSD drive ?? 60 GB

---

### Post by LinuxFan999 on 2011-12-05
I personally think that SSDs are unreliable junk, but Intel makes the most reliable SSDs.
If you want something faster, try the OCZ vertex 3, which is SATA III capable and is very fast, and comes in a 60GB variant, as well as other capacities.

---

### Post by dabl on 2011-12-05
> **LinuxFan999 said:**
> I personally think that SSDs are unreliable junk

Or ...

I own 4 SSDs:

1. EeePC 4G/701, from 2008.  Runs aptosid Linux, never had a problem.

2. OCZ RevoDrive PCI-e SSD, 120GB, runs aptosid Linux and a couple of VMs, installed Nov. 2010, no problems to date.

3. Kingston SS100S2, cheapo 15GB SATA SSD, used to boot the #2 aptosid system.

4. OCZ Vertex Plus OCZSSD2-1VTXPL120G 120GB SSD, installed in a Dell Latitude E6500 in October, also running Linux, no issues to date.

So, reports vary.  :D

---

### Post by pqwoerituytrueiwoq on 2011-12-05
@dabl i think that Kingston drive is a 16gb

i am on my second one of that drive (KINGSTON SS100S216G) the 1st one failed in under a week RMAed under warranty have have had no issues with my replacement (56.4 power on days and counting)
use a ssd in a low write environment (especially mine) if you use ext3/ext4 be sure to disable the access time feature

this is my fstab only / (sda1) is on my ssd
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4    discard,errors=remount-ro,noatime,nodiratime 0       1
# /home was on /dev/sdb3 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4    defaults                             0       2
# /mnt/HardDisks was on /dev/sdb5 during installation
UUID=51b2b46b-891c-490c-b8a6-a878595194b6 /mnt/HardDisks  ext4    defaults                             0       2
# /mnt/DiskImages was on /dev/sdb6 during installation
UUID=89068a31-dc74-4dad-bf5f-8bfec96850de /mnt/DiskImages ext4    defaults                             0       2
# /var was on /dev/sdb2 during installation
UUID=5cae72de-be5c-4586-90ec-c65ce056555b /var            ext4    defaults                             0       2
# /tmp was made a ram disk after installation
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777           0       0
# swap was on /dev/sdb4 during installation
UUID=047fac32-955c-4318-b70c-479c433a24a8 none            swap    sw                                   0       0
```

---

### Post by dabl on 2011-12-06
> **pqwoerituytrueiwoq said:**
> @dabl i think that Kingston drive is a 16gb


Ooops, yes, you are correct.  It formats to less than that, but it was sold as a 16GB capacity.

While I'm at it, I forgot about the 40GB OCZ SATA drive that I put in my Toshiba NB205 netbook about October of 2010.  It's been to Europe and back, and dropped on the floor several times. It's an ext4 filesystem, but I set it to slower journalling than default, and mounted the logs on tmpfs (so they disappear every shutdown).  It gets used daily, and no problems at all on that one either.

---

