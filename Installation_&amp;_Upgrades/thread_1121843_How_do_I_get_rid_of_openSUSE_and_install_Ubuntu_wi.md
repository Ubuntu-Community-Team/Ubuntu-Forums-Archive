---
title: "How do I get rid of openSUSE and install Ubuntu without ruining my boot partition?"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by wripley on 2009-04-10
I tried a few different versions of linux before, and I decided that, for what I want it to do, Ubuntu is the best for me.  Right now I have openSUSE installed on my laptop with XP also on it.  Right now, the boot loader is grub, and I don't know what partitions I can get rid of without messing up my boot record.  Last time I tried to do this, my boot partitions got messed up and I got the NTLDR is missing error when I tried to boot XP, which I still need [as a crutch] for some things.

To help, I have the following show up on Partition Magic in XP:
Local Disk (C:) NTFS Status: None Pri/Log: Primary
{*} Extended Status: Active Pri/Log Primary
SWAPSPACE2{*.} Linux Swap Status: None Pri/Log: Logical
Local Disk {*.} Linux Ext3 Status: None Pri/Log: Logical
Local Disk {*.} Linux Ext3 Status: None Pri/Log: Logical

It also shows the sizes, but I don't know if thats all that important for you to help me.  Any help would be appreciated.

PS: Will Ubuntu Studios 8.10 work as well as the LiveCD of Ubuntu 8.10?  Specifically, my trackpad never works with linux, but it does in 8.10.

---

### Post by cariboo on 2009-04-10
When you get to the partitioning section of the installation, choose manual and and just mark the openSuse to be formatted and install to that partition. Grub will be overwritten, but it shouldn't change anything.

JIm

---

### Post by stargate2500 on 2009-04-10
What partition is first and which one has the boot loader. I have four os's
and xp first second is ubuntu third is opensuse and fourth is puppy. When I'd stall opensuse I'd messed up the boot loader. Find out which order then how can it be done. So you don't make the same mistake...

---

### Post by wripley on 2009-04-10
> **stargate2500 said:**
> What partition is first and which one has the boot loader. I have four os's
and xp first second is ubuntu third is opensuse and fourth is puppy. When I'd stall opensuse I'd messed up the boot loader. Find out which order then how can it be done. So you don't make the same mistake...

I think the partition that is "active" is the one with the boot loader on it, which is one of the openSUSE partitions.

PS thanks cariboo and stargate

---

