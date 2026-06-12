---
title: "Set up RAID0 in 9.04 existing installation"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by snorkytheweasel on 2009-10-22
9.04 existing installation with newly-added drive

I have 2 drives, 3 partitions: sda1,sdb1,sbd2. I set up different-sized partitions on sdb because somewhere in the dark recesses of my memory is the idea that RAID0 prefers "unbalanced" partition sizes. That might be old UNIX or ancient VMS, or maybe it's that I never had  a "matched" set of disks. Or perhaps my putersheimers kicked in. After all, I've forgotten more than I ever knew :)

How do I set up RAID 0 (stripe set, no parity) with IDE drives?

---

### Post by dstew on 2009-10-23
If you want to create a new RAID array and do a fresh install to it, you can use the Alternate Install CD.

If you want to create a RAID out of some free partitions, and not install Ubuntu to a RAID, you use the mdadm program. For example, if you want to create a RAID0 array, with the device name /dev/md0, out of partitions /dev/sda and /dev/sdb, the command would be```
mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
```The --level switch is the RAID type. This command creates the RAID0 device. To make it work, you use the mdadm --assemble command:```
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
```See [this How-To]("http://ubuntuforums.org/showthread.php?t=408461"), and/or the [mdadm man page]("http://linux.die.net/man/8/mdadm"). The command```
mdadm --assemble --scan
```will try to assemble the RAID automatically.

As far as the sizes of the partitions that make up the RAID, it seems the mdadm --create command will balk if the sizes are more than 1% different. You can try it with different-sized partitions and see what happens if you want.

---

