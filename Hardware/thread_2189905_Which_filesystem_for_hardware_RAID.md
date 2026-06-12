---
title: "Which filesystem for hardware RAID?"
date: 2013-11-24
forum: Hardware
---

### Post by geohei on 2013-11-24
Hi.

I have hardware RAID1 (ICP GDT8546RZ) installed in my 12.04 server machine.
2x 2TB HDDs, each array as RAID1.

Which filesystem is best and why?
btrfs, zfs or simply ext4?

Speed is not relevant.

This forum as well as Google shows some hits, but I didn't find any answer yet on what to take or leave? This is partially because btrfs is still changing quite a lot.

Thanks,

---

### Post by tgalati4 on 2013-11-24
Is this server for home use?  If so, then probably ext4.  If it is for business use, then ext4 or zfs.  zfs gives you some data protection with checksums for each file stored in the file system.  btrfs gives you some speed improvement, but with hardware RAID, you may not notice it, since hardware RAID is usually pretty fast already.

The only way to know for sure is to try each one for a month and do some performance tests.  Install *phoronix-test-suite* and run some of the disk I/O tests.  Let us know the results.

If these are new disk drives, then you will want to break them in and test the system for overall reliability before committing data to them.

---

### Post by geohei on 2013-11-25
Yes, it's a private server.

btrfs speed improvement - speed is not important to me for that system. Data integrity however is. Bit rot should be detected and corrected (HHDs are in RAID1 arrays). So ... checksum features are desired.

You don't talk about btrfs stability and compatibility between kernel versions.

phoronix-test-suite ... I had a quick look ... will look closer as soon as time permits.

Only 2 of the 4 HDDs are new. They were tested thoroughly prior installation to avoid surprises.

How stable is zfs in relation to btrfs and ext4?

---

