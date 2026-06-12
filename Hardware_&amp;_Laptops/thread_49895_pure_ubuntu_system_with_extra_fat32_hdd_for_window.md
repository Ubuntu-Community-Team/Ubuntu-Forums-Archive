---
title: "pure ubuntu system with extra fat32 hdd for windows netowrk"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by sal on 2005-07-18
question:
i have my main system as a pure ubuntu system setup. not as dual-boot just Ubuntu. in it i have an 120gb fat32 hdd so my windows xp box can read and write to it. the thing i'm woundering about is fragmentation on the fat32 drive. what could i do to defrag it? i know i have seen a package in synaptic (i think called defragment), would i be able to install that and use that to defrag the fat32 hdd?
TIA

---

### Post by GTvulse on 2005-07-18
No. defrag only works with ext2, minix and xiafs filesystems (of which xiafs has already been removed from the 2.4.x kernels...). Notice that ext2 is not ext3, if you tried to run defrag on an ext3 filesystem you'll blow up the journal files to bits.

In order to defragment the FAT32 volume you'll need to do it remotely with some "server" type defragmenter. My first choice would be Raxco PerfectDisk, my second O&O Defrag  and my third, laging by a couple of miles, would be Diskeeper Pro, which btw is the commercial version of the defragger included with Windows since Win98.

Edit: Hmm... You may have better luck attaching the disk to the XP system and accesing it from Ubuntu using Samba.

---

### Post by sal on 2005-07-19
well let me ask you then,
how reliable is the "captive ntfs" thing for writing to an ntfs partition.

---

### Post by GTvulse on 2005-07-19
[QUOTE=sal]well let me ask you then,
how reliable is the "captive ntfs" thing for writing to an ntfs partition.[/QUOTE]
 I haven't used it myself, but I've read good reviews of it; it is basically like using ndiswrappers but for wrapping the Windows NT ntfs drivers. What I don't know is if it is compatible with 2.6 kernels. Another possibility (if you are going that route) is to use the native Linux NTFS drivers from Paragon.

---

