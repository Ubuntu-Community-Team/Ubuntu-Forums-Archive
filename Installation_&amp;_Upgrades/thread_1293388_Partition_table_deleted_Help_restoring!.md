---
title: "Partition table deleted? Help restoring!"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by LeftyAce on 2009-10-17
Hi all,

It looks like all my partitions are gone.

I needed to make room for a logical partition (I had 4 primaries), so I did a dd backup of /dev/sda4 (the partition housing /)

I then used the gparted boot cd to delete the partition.  I tried to dd the image back into the space, and it said "no space on disk".  I figured, "oh, first I have to create a partition here".  So I attempted to create an extended partition in the space, and got an error.  gparted attempted to refresh its view of the drive, and now shows no partitions at all (ACK!)

The drive formerly held a windowsXP NTFS partition, an ext4 /home partition, an ext4 / partition, and a FAT32 IBM recovery partition.  The computer has no CD drive (it's a Thinkpad X61) so if I decide to just nuke everything and start over, I lose my windows install permanently.

I'm guessing all my data is still there, but I've deleted the partition table? If so, is there a way to get it back, since I backed up the root partition? I've googled around some, but I don't want to try anything I'm not certain of, because as soon as I start writing to the drive, I may kill the stuff I'm trying to save.

 Any help is enormously appreciated.

---

### Post by LeftyAce on 2009-10-17
This is a most useless update, but I tracked down a linux guru in my dorm (yay engineering college), and he managed to reconstruct the partition table (I hadn't rebooted yet).  So it's working, but if others have this situation, I can't help you with how to fix it :-(

---

