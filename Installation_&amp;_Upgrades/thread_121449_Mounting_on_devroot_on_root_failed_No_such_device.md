---
title: "Mounting on /dev/root on root failed: No such device"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by jjthomas on 2006-01-25
I have a multiple OS system.  I have 6 drives as follows:
Drive 1 ATA Primary Master
Drive 2 ATA Primary Slave
CD-ROM on the Seconday Master (no Secondary Slave)
Drive 3, 4, 5, 6 are all SATA drivers.

Drive 1 is partitioned with XP, slackware SWAP SWAP and ubuntu.
ubuntu works on this drive

Drive 2 is nothing but a single root ubuntu partition
  it will not boot

I have tried installing ubuntu every which I can think off, on drive 5.  The install goes okay basically.  There is some warning messages about not being able to resize the partitions on drive 1.  Which is strange because I am not doing anything with the drive 1 partitions under the install screen except telling it not to use the drive 1 SWAP partitions.  I am installing SWAP partitions on drive 5.  

When I boot into the drive 5 (and drive 2) after the install I get the same consistent error:
Mounting on /dev/root on root failed: No such device

The only other thing I can add is that I use LILO instead of GRUB.  I tried using GRUB, but those installs failed as well.

-JJ

---

