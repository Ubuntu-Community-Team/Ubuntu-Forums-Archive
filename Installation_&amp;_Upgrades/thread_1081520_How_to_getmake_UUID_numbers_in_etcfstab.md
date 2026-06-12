---
title: "How to get/make UUID numbers in /etc/fstab"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by orangep on 2009-02-26
The most recent upgrade of Debian Linux for 64-bit cpus destroyed my system and left it unbootable, so I was finally forced to really give Ubuntu a try.
I cleared a disk drive and installed the latest stable version of
64-bit desktop Ubuntu onto it.

Installation went well. No major hassles except this:

I have multiple disk drives, and cannot list them in /etc/fstab correctly. The old style of listing them by drive names like /dev/sda1, /dev/sdb1, etc. no longer works as the various disk drives come up with different identifiers with every reboot. It's like identifier roulette.

I see that the installation routine has created a new kind of identifier for the root disk drive. All of the boot disk's partitions are
identified with labels like 
 "UUID=ab3e8667-10cf-4c60-af7a-38a22a0ba3ee", 

So how do I get such UUID numbers for the partitions on the other
disk drives?

TIA.

---

### Post by Pumalite on 2009-02-26
```
blkid
```

---

### Post by orangep on 2009-03-02
blkid

Yes, that's it. Thank you.

---

### Post by orangep on 2009-03-02
Well, one more question:
I have a secondary disk drive that also has a swap partition on it. Might as well use it. But it has no UUID number. Is there a way to create or assign one?

---

### Post by Pumalite on 2009-03-03
You meed only one /swap  per computer. (the kernel finds it)

---

### Post by HavocXphere on 2009-03-03
> **orangep said:**
> Is there a way to create or assign one?
UUIDs are assigned during partitioning. So unless its unpartitioned space it should already have a uuid.

---

