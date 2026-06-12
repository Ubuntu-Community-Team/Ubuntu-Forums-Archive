---
title: "Size limit for hard drive"
date: 2010-06-25
forum: Hardware
---

### Post by ags40 on 2010-06-25
Is there a size limit that Linux can addressed? Does it matter if it is SATA drive? Is there a better size? Thanks

---

### Post by oldfred on 2010-06-26
Linux is not the issue. It runs supercomputers also.

The issue is the MBR partitioning scheme used since the first IBM pc. MBR has a 2TiB limit. Apple has converted to GPT which is a lot larger.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by ags40 on 2010-06-26
Thanks very much!

---

### Post by efflandt on 2010-06-27
There may also be a BIOS limitation.

At one time (on a 386) I had to install an extra card to be able to do LBA and use more than 528 MB of a 540 MB drive (yes MB, not GB).

My current desktop (from 2004) boots fine from the far end of its 200 GB internal drive or 160 GB USB drive.  But for some reason it cannot boot from the far end of a 500 GB USB drive.  Grub rescue says "error: unknown filesystem" (it is ext3).  Even regular grub 1.98 prompt from my main hard drive cannot read that USB drive partition.  But Linux itself on that PC has no trouble auto mounting partitions on the 500 GB USB drive, and it boots fine on 2 other computers.

---

### Post by cascade9 on 2010-06-27
> **oldfred said:**
> Linux is not the issue. It runs supercomputers also.

The issue is the MBR partitioning scheme used since the first IBM pc. MBR has a 2TiB limit. Apple has converted to GPT which is a lot larger.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Yes, but the limit on the MBR is from HDDs 512b sectors. While the new WD 'advanced format' drives still pretend to use 512b sectors, in reality they are 4k sectors, and once somebody moves to 'real' 4k sectors, the 2TB limit wont be a rpoblem.... AFAIK anyway.

---

