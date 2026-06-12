---
title: "How to fix GRUB after changing hard drives (with UUIDs)"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by rabinnh on 2009-03-04
I thought some other people might find this useful, since I couldn't find it in a search.

I have an external SATA drive that was booting Ubuntu, and an internal SCSI drive booting XP.  The way it worked based on BIOS order was if the SATA drive was powered up, it would boot first.  Otherwise the internal SCSI drive would boot.

Since I found that I only occasionally boot into XP these days (to sync my BBm for example), I decided to switch drives.  Here is how I got it to work.  I'll skip how I got XP on the SATA, that was easy.  Here is how I moved Ubuntu (Intrepid) to the internal 15K SCSI:

NOTE: You must either backup your Ubuntu installation using tar, cp, or something else or be able to access both HDs at the same time.
1) Booted the LiveCD.
2) Told installer to remove all partitions from the SCSI drive
3) Let Ubuntu partition and install on the SCSI drive.
NOTE: It would be just as effective to use gparted, but I wanted to ensure that the disk was prepared just as it would be on a normal installation.
4) Boot from the LiveCD into Live mode
5) As su, delete all files from both the boot and run partitions of the SCSI drive.
6) rsync files from my original installation to the /boot and / partitions on the SCSI drive.
NOTE: Here is the key part
7) As su, run "blkid".  Note the UUIDs of the partitions on the new drive 
8) As su, use nano to open both /boot/grub/menu.lst and /etc/fstab
9) Match the UUIDs in the 2 files. The GRUB line "uuid XXXX" should correspond to the "/boot" partition.  The GRUB line "kernel" should be the "/" partition.
10) Edit the UUIDs in fstab to the new ones that you identified with blkid. Save
11) Edit the UUIDs in menu.lst the same way. Save.
NOTE: this next part is documented everywhere. For example [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/).
12) Run GRUB as su
13) type "find /boot/grub/stage1".  If it doesn't find it, try "find /grub/stage1"
14) Note the hdx,x where x is 0, 1, etc.
15) Type "root (hdx,x)" using the info from step 14
16) Type "setup (hdx) using the info from step 14.
17) Reboot and enjoy.

Everything is working perfectly on my system.  64 bit Intrepid on a Quad core Xeon with a 15K U320 SCSI drive.  And compix.  Aaaaaaahhhhhhhhh!


15) type "root (hdx)

---

