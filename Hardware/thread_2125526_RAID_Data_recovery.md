---
title: "RAID: Data recovery"
date: 2013-03-14
forum: Hardware
---

### Post by leezer3 on 2013-03-14
OK, so made the dense mistake of trying to switch some drives to a new RAID card.
Everything went OK, apart from one drive. 
This isn't being recognised, and the MBR/ partition table appears to have been eaten by the raid card. I know *exactly* what was there in terms of partitions, but I can't get anything to find them or recreate them sucessfully. 
The drive was (is) a single 400gb drive, with GRUB installed on the MBR and a single XFS partition.

Results at the moment:
**Testdisk**
* Intel/ PC partition table- Nothing found.
* Non-partitioned drive- Finds multiple HFS (??) and XFS partitions, none of which are recoverable.
**Manual Partition Recreation**
* Attempting to mount the recreated partition gives a slew of complaints about not being ext2, ext3 or ext4 and a bad XFS superblock.
* XFS_Check dies with a bad superblock error.
* XFS_Repair finds various backup superblock candidates and discards them.

I'm currently scanning with gpart, but does anyone have any ideas please?
Leaning towards photorec if gpart doesn't find anything. Not the end of the world if the data goes walkies, but I'd rather it didn't!

---

