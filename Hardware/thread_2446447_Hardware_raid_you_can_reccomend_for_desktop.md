---
title: "Hardware raid you can reccomend for desktop"
date: 2020-06-30
forum: Hardware
---

### Post by zephar123 on 2020-06-30
I have hardware raid on my servers, but it seems really difficult to find a good hardware raid that is compatible with desktop computers. I might just do another software raid, but wanted check first if anyone has a decent controler they can recommend that has caching on it. 

Thanks

Paul

PS MB is an AMD x470

---

### Post by TheFu on 2020-07-01
TL;DR
None that doesn't cost more than the MB and CPU.  

**Longer version ... **
It comes down to the reason for RAID.  The only valid reason to use HW-RAID over SW-RAID is to have a built-in battery on the RAID HBA so those last few writes get to the disk after power is lost.  A solid UPS and journalling file systems solve that problem with a number of other good things also included.  BTW, this applies to servers as well.  SW-RAID is tremendously flexible and fast.  I've moved SW-RAID systems between 3 physically different systems without any issues, usually as part of an OS upgrade.  Should also mention that the original plan was to use HW-RAID, but thankfully the drivers for the RAID level I wanted didn't support any recent kernel, so that card was relegated to being a JBOD controller only. Well over a decade later, I'm very happy with the results.

RAID is for high-availability. A single RAID card doesn't provide HA.  Current thinking is that having redundant, but cheap, systems which are constantly replicating storage at the block level behind the scenes provides much more assured redundancy than a single, expensive, server provides. 100% of the systems are redundant this way, not just the storage. Redundant storage isn't really useful when the PSU fails or, on a desktop, the GPU fails. Why bother with the expense when there are so many other single points of failure?
[https://arstechnica.com/gadgets/2020/06/western-digitals-smr-disks-arent-great-but-theyre-not-garbage/](https://arstechnica.com/gadgets/2020/06/western-digitals-smr-disks-arent-great-but-theyre-not-garbage/) may be interesting for you. The author works at a storage company and has a number of articles about RAID.

I've worked in places that did both techniques. It wasn't nearly as difficult once virtualization became the standard thanks to a multitude of VM storage replication methods.  My main desktop actually runs inside a VM.  It gets automatic, versioned, backups every day just like all the other systems. If it was more important, it would be near-real-time replicated to another system running 50% of the VMs (or less) using ceph or sheepdog.  Alas, the desktop files don't change THAT much in any important ways. Between a laptop, backup storage, and that important files are also backed up daily from the servers where they reside, data loss and data corruption just aren't concerns.

If you are still convinced to use HW-RAID, I'd begin by reading what the FreeNAS guys recommend because HW that works with BSD is usually excellent on Linux as well.  And LSI would be on my short list of vendors to consider.  I've been looking at an LSI SAS JBOD controller to expand my home storage server for some time.

---

### Post by SeijiSensei on 2020-07-01
LSI SAS controllers have been supported in the kernel for many years now.

Frankly, I don't see any strong arguments in favor of hardware RAID for a desktop machine.

---

### Post by zephar123 on 2020-07-02
Thanks guys, I  think ill stick with software raid and just make it a raid 10 this time. On server side the cards are affordable as their stuck to the hardware and that and appreciate the comments.

Paul

---

### Post by TheFu on 2020-07-02
> **zephar123 said:**
> Thanks guys, I  think ill stick with software raid and just make it a raid 10 this time. On server side the cards are affordable as their stuck to the hardware and that and appreciate the comments.

Have you considered using either ZFS or the LVM implementation of SW-RAiD?  As long as you are trying to learn new stuff, may as well get a volume manager involved.  Not saying anything more than consideration should be done.  mdadm first, then LVM works too.  But LVM stole much of the mdadm code and embedded it, so using just LVM commands should result in effectively the same redundancy.  in theory.

---

