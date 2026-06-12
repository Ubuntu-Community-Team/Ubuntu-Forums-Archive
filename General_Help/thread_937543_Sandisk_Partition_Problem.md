---
title: "Sandisk Partition Problem"
date: 2008-10-04
forum: General Help
---

### Post by kramulous on 2008-10-04
Howdy,

  I've been trying to fix this for days and now admit that I may need a little help.

  I bought a 4.0GB Memory stick PRO Duo for my PSP, plugged it in, was using it, copying videos onto it and watching and all of a sudden the PSP did not recognise the sandisk anymore.  It won't even format it anymore.

  When I type fdisk, I get:
> 
Disk /dev/sdb: 2080 MB, 2080374784 bytes
64 heads, 62 sectors/track, 1024 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Disk identifier: 0xac13aeb2

Disk /dev/sdb doesn't contain a valid partition table

Which is interesting since it is a 4GB (whatever - 2 would still be enough)

When I sudo fdisk /dev/sdb:
> 
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xbe42c979.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

The w(rite) does not fix anything.  

Starting again, a "p" verifies that there are no partitions so I create a new primary partition with all defaults.  When I "p", everything looks okay.  When I w(rite) it fdisk does its bit and quits.  A sudo fdisk -l still shows the output above.  Nothing seems to work.

When I "sudo gparted /dev/sdb", parted shows that there is 1.93GiB unallocated.  Trying to create a new "disk label", the stdout of gparted is "Unable to open /dev/sdb - unrecognised disk label."

I'm at a loss.  Any clues?

---

### Post by kramulous on 2008-10-08
Bumpity!

Although I realise that the sandisk may be stuffed.  Would just like confirmation before getting a new one.

---

