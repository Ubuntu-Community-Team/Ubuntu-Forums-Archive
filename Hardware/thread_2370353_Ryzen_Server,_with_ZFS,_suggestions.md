---
title: "Ryzen Server, with ZFS, suggestions"
date: 2017-09-02
forum: Hardware
---

### Post by kryten2k352 on 2017-09-02
Hi

I'm a daily Ubuntu user at home and at work (Web Programmer). I've got a Ubuntu home server running currently that's used for Plex, Deluge and Samba.

My current setup is not that great, some alright hardware but the disks are JBOD and not at all optimised.

I'm looking at getting a Ryzen CPU setup, ECC RAM and some professional NAS disks.

I've heard some things about Ryzen not being that good for Linux. Is this still true?

I've also no experience with ZFS at all. My initial thoughts were to get a RAID controller and use RAID 6, but RAID controller (good ones) are very expensive and I've heard you don't need this for good performance (and data redundancy)?

Can anyone advise on the best setup for a NAS using ZFS and Ubuntu?

Also, would it be worth getting a super fast M.2 SSD for caching with ZFS?

---

### Post by TheFu on 2017-09-03
Every CPU has strengths and weaknesses.  Ryzen had issues with most CPUs under very high, multithreaded, loads.  To cause the issue, people were running 3 concurrent compiles of very large software projects.  This would cause the CPU to segfault. That is very bad.  Very few people in the wild ever saw this, because they don't push their CPUs with that sort of workload for long.

AMD has corrected the issue and new chips shipped in the last few weeks are not showing the issue.  AMD has been replacing CPUs, when asked.  How someone can ensure they get a CPU from the "good, newer, batches" - I don't know.  The issue doesn't show up on Windows.

Professional NAS disks?  I wouldn't bother, unless they are a fantastic deal.  Backblaze has been publishing quarterly reports concerning their 60K+ drive failure rates for the last few years.  Certain vendors have a much higher failure rate than others.  Do your research.  The 17Q2 data was released last week.

ZFS likes to have 6 HDDs.  I've never used it on Linux, so cannot say whether it is good or bad.

ZFS and RAID never replace backups.  Always include a backup method in your solution budget.  
Running ZFS means that ECC RAM also makes sense, but how often have RAM issues cause data problems for you over the years?  Motherboards that support ECC cost a little more. ECC RAM costs a little more.

Backups are 1000x more important than ECC RAM or RAID or ZFS.

For media, disk performance really isn't very important.  Streaming blueray only needs USB2 speeds.  Normal SATA connected disks easily handle 4K video.

I think Ryzen is a great CPU, with the caveats above.  I wouldn't use it for playback of video (too noisy), but if you want to host plex on it, fine.  I would move to NFS and drop Samba, if you can.  My NAS/Plex system handles everything with a $50 Intel G3258 CPU.  For a NAS and media center library, transcoding system, more just isn't needed.  For the storage, I use a mix of LVM, but limit every LV to a size I can easily chunk into a backup disk.  Actually, there are 4 backup disks for that system.  Picked up an 8T disk last month for $160. Hard to refuse at that price from a known-good vendor.

OTOH, if you want to run 30 VMs then a Ryzen CPU makes sense.  I'm looking at a Ryzen 5 1600 (65W, fan included) to replace 3 of my other systems that are 7+ yrs old.  Those are 1st generation Core i5 and Core i7 systems, not slow for their time.  I won't use it for my Plex or storage system.  It will be a VM host system for about 20 VMs that run to support some clients and personal needs.

I'd look forward to reading what others think too.

---

### Post by mastablasta on 2017-09-05
> **kryten2k352 said:**
> 
I'm looking at getting a Ryzen CPU setup, ECC RAM and some professional NAS disks.


what is the purpose of the server? only plex and file server?

What is the reason for using ZFS?

---

### Post by TheFu on 2017-09-05
ZFS makes a lot of sense for media storage.  And if using ZFS, using ECC RAM is highly recommended. ZFS validates that what was sent to the disk is actually written there.  Best to have ECC RAM for the extra validation.  Reading some of the FreeNAS forum posts about this will provide a better explanation for ECC with ZFS.  Storage pool management and snapshots under ZFS should be easier. 

I think bitrot is a real thing for data that doesn't get refresh yearly.  ZFS should fight that, in theory.  For non-ZFS file systems, I've been temped to use separate parity files - maybe 1% - just to have a way to validate the files aren't corrupted over time. ZFS would be a more elegant solution, perhaps?

But Ryzen is overkill for Plex, Samba, storage and downloading. A $50 CPU easily handles that workload.  EASILY. But if the OP needs more significant workloads like transcoding hidef media or compiled software development or running 5+ VMs or all of these things, then I can easily see where Ryzen makes sense.

---

