---
title: "Remove Thinkpad recovery partition while in linux?"
date: 2008-09-12
forum: Hardware
---

### Post by greymarch on 2008-09-12
I have a T61p thinkpad laptop.  I have Vista 64 Ultimate and Linux Ubuntu 8.04 installed on the machine.  I use GRUB to dual-boot either OS.

I want to remove the IBM recovery partition.  I need the disk space for other things.

This is what Gparted (when running in Linux) tells me about my partitions:

/dev/sda1/ is the recovery partition
/dev/sda2/ is the Windows partition, and it is flagged to boot
/dev/sda3/ is my Linux partition

What I want to know is, can I remove the recovery partition using gparted in Linux, without ruining windows, linux, or the ability to boot my machine? Gparted in Linux will let me try to delete the recovery partition, but obviously I havent tried it yet.  If I shouldnt use Gparted in Linux, then what would be the best way to remove the recovery partition, given the setup of my system?

---

### Post by russlar on 2008-09-12
> **greymarch said:**
> I have a T61p thinkpad laptop.  I have Vista 64 Ultimate and Linux Ubuntu 8.04 installed on the machine.  I use GRUB to dual-boot either OS.

I want to remove the IBM recovery partition.  I need the disk space for other things.

This is what Gparted (when running in Linux) tells me about my partitions:

/dev/sda1/ is the recovery partition
/dev/sda2/ is the Windows partition, and it is flagged to boot
/dev/sda3/ is my Linux partition

**What I want to know is, can I remove the recovery partition using gparted in Linux, without ruining windows, linux, or the ability to boot my machine?** Gparted in Linux will let me try to delete the recovery partition, but obviously I havent tried it yet.  If I shouldnt use Gparted in Linux, then what would be the best way to remove the recovery partition, given the setup of my system?

You're safe to nuke the recovery partition.

---

