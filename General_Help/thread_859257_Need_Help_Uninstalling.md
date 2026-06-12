---
title: "Need Help Uninstalling"
date: 2008-07-14
forum: General Help
---

### Post by transnova on 2008-07-14
Hello I installed Ubuntu 7.something and would like to know how to uninstall it, its not that I don't like it, its just that I don't use it with having windows and all :( .

1. So I know I first have to do FIXMBR in the recovery mode of the windows disk, but it gives me this huge warning message, should I care about it at all?

2. also I have ubuntu on a ~40 gig partition, but my drive also shows besides my windows partition a 518 MB partition, is this part of ubuntu(could it be a swap partition)? can I delete it with out messing up windows?

3. after this how do I get the rest of my HD back, should i resize the windows partition, or just make a new one? b/c I have heard that resizing is dangerous.

I know this has been an enormous message, but thanks in advance for reading it and helping me

---

### Post by coffeecat on 2008-07-14
> **transnova said:**
> Hello I installed Ubuntu 7.something and would like to know how to uninstall it, its not that I don't like it, its just that I don't use it with having windows and all :( .

You don't have to uninstall. Just reuse or reformat the Linux partition and - bingo - it's gone.

> **transnova said:**
> 1. So I know I first have to do FIXMBR in the recovery mode of the windows disk, but it gives me this huge warning message, should I care about it at all?

I know it's huge, but can you post the message. Then someone might be able to help.

> **transnova said:**
> 2. also I have ubuntu on a ~40 gig partition, but my drive also shows besides my windows partition a 518 MB partition, is this part of ubuntu(could it be a swap partition)? can I delete it with out messing up windows?

The 518Mb (do you mean 512?) will be the swap partition. Linux uses a swap partition where Windows uses a file, so Windows won't need it. Best bet would be to delete both partitions and reuse the space. You could do this with a Windows partitioning utility, or boot up from the Ubuntu CD and use the partitioning tool (Gparted) under System > Administration.

> **transnova said:**
> 3. after this how do I get the rest of my HD back, should i resize the windows partition, or just make a new one? b/c I have heard that resizing is dangerous.

You could repartition the reclaimed space as an NTFS partition which would become your E: or whatever Windows drive. I don't really know about resizing a Windows C: partition, but I would image/ghost my Windows installation as a back-up first and use a Windows app/partition tool to do the resizing.

> **transnova said:**
> I know this has been an enormous message, but thanks in advance for reading it and helping me

No problems. I hope you come back to Linux sometime and good luck.

**Edit:** IMPORTANT. Fix your mbr **before** you reformat the Linux partition. Files needed for bootup are in the Linux partition. If you reformat that before repairing the mbr you won't be able to boot into Windows.

---

### Post by transnova on 2008-07-14
Here is the message I get:

** CAUTION **

This computer appears to have a non-standard or invalid master boot record.

FIXMBR may damage you partitiion tables if you proceed.

This could cause all the partitions on the currrent hard disk to become inaccessible.

If you are not having problems accessing your drive, do not continue.

Are you sure you want to write a new MBR?

---

### Post by coffeecat on 2008-07-14
My interpretation:

> This computer appears to have a non-standard or invalid master boot record.Fair enough. Grub stage 1 has overwritten the mbr.

> FIXMBR may damage you partitiion tables if you proceed.

This could cause all the partitions on the currrent hard disk to become inaccessible.I suppose in some circumstances this might be possible - perhaps with unusual Windows setups - but I don't know enough about the mbr and the partition table (which are adjacent in the first 512 bytes of the HD) to make a sensible comment. I have used fixmbr on a dual-boot, but it was over 2 years ago and I can't remember whether I got a warning like this - I probably did. Whatever - it didn't damage the partition table, or at least I was able to boot into Windows afterwards.

> Are you sure you want to write a new MBR? = "If your system becomes unusable, don't sue us (Microsoft)." :wink:

If I was in your position, I would make sure I had backed up Windows with some sort of imaging/ghosting software first (I use Acronis - excellent) so that if everything went wrong (I would hope unlikely) I could restore Windows to how it was without going through the tedium of re-installing and reconfiguring.

---

