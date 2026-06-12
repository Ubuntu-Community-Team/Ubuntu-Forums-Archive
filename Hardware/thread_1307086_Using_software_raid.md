---
title: "Using software raid"
date: 2009-10-30
forum: Hardware
---

### Post by billmilosz on 2009-10-30
I've got a machine that boots off an IDE drive, plain old IDE.  Got Ubuntu 9.10 64 bit on that drive, everything is good.

There are four other 1 TB drives in this computer.  When this machine ran Windows from that IDE drive, these four drives were set up as a pair of Intel SATA software raid mirrored drives.  Between them these drives store about 1.6 TB of important data.  Under Windows, using the four drives as a pair of mirrored drives gave me data security against a drive failure.

How do I set up software raid to mirror these data drives under Ubuntu 9.10, keeping in mind that they are NTFS and the data is already there.  Can I just set up and use DMRAID for this?  Since I am booting from an ordinary IDE drive I escape the complication of trying to set up booting from software raid.

Right now the drives show up as two NTFS volumes which I recognize as my data drives, and two drives with unkown partitions.

---

