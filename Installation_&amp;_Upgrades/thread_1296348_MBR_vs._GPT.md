---
title: "MBR vs. GPT"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2009-10-20
I have a Vista notebook with:

C: Vista and all other files
D: HP Recovery partition
E: Optical drive
F: USB drive

I intend to split C so I have a multiboot Vista/Win 7/Ubuntu system as follows:

C: Vista
G: Win 7
H: My non-OS files
unused: Reserved for Ubuntu and expansion of other partitions
D: HP recovery partition
E: Optical drive
F: USB drive

I have 2 decisions to make:

1. C is currently 285GB. I need to decide on the size of each partition,
2. Whether to use MBR or GPT.

Presently, I do not have Win 7 compatible backup, or partitioning software that will support, as far as I know, GPT.

My question is should I convert all drives to GPT when I have such software?

Or, am I stuck with MBR?

This is on a 64-bit system.

---

### Post by dstew on 2009-10-20
What are MBR and GPT?

---

### Post by oldfred on 2009-10-20
MBR or master boot record is what we have been using to boot PC's since the introduction of the IBM pc. We have 4 partitions, but it was modified to allow converting one to an extended partition so we could add more logical partitions. It also has a maximum of 2TB and since they are now selling 2TB drives the next generation of drives will not use MBR.

GPT is a newer partitioning scheme used by Apple and some Windows servers. All the software you use must be GPT aware for it to work. Grub legacy (some versions) was modified to at least be GPT aware. New Grub2 is GPT aware.  

More Info:
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by dstew on 2009-10-21
Thanks oldfred. I knew what MBR stood for, but I had not heard of GPT until now.

---

