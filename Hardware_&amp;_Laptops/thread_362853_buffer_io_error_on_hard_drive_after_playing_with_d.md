---
title: "buffer i/o error on hard drive after playing with dvd and dvd software"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by oneiota on 2007-02-16
I've been using Ubuntu (Edgy Eft) on a new hard drive (Western Digital 250GB SATA SE16 3.5" 7200rpm ATA300, 16MB Cache WD2500KS, 8.9ms) for a few months.  All has been well until now.

Yesterday, after unsuccessfully trying to view a DVD on each of the two DVD drives, I installed gxine and tried again.  Upon removing a DVD from one of the drives and inserting it into another, I heard a constant, loud, whirring/scraping noise that I thought must be coming from the drive and found that the disk refused to eject. I turned the power off, and booted but found a buffer i/o error on device sda1 - the hard drive (not the dvd drive).

Now Ubuntu will only boot into read mode as root, asking me to run fcsk, which I have.  It reports buffer i/o errors on the device, sometimes prompting with messages like:

Error reading block 53411882 (Attempt to read block from filesystem resulted in short read) while doing inode scan. Ignore error<y>? yes

Force rewrite<y>? yes

Now fsck is continuing to report line after line of:

ata: translated ATA stat/err 0x51/01 to SCSI SK/ASC/ASCQ 0x3 ...

with the occasional:

Buffer I/O error on device sda1, logical block ...



Can anyone shed light on what might be happening here and what I need to do?  I find it hard to believe the new hard drive has really crashed but perhaps something became confused whilst a DVD was moved back and forth between DVD drives?

---

### Post by oneiota on 2007-02-16
Just an update now that fsck has finished.

Pass 2, 3, 4, 5 didn't show any error and the final line given is:

/dev/sda1: 191743/30146560 files (0.9% non-contiguous), 4353005/602919937 blocks

Now, the system is also able to boot properly and I can't find any problem.  Shouldn't I have damaged files?  How perplexing.  If anyone has insight, I would appreciate hearing.

---

