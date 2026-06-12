---
title: "Need help recovering FakeRAID 0 partition table"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Epistaxis on 2009-05-03
Short version: I think I have a correct partition table, but it's only on one disk of a two-disk RAID 0. I would like to recover the original array's partition table (and data) with it. Does that make sense, and if so, how can I do it?

Long version:
[LIST]
I could not install Jaunty in ext4 on an Intel FakeRAID 0, even after following the several versions of the FakeRAIDHowTo, and even though the same instructions worked with previous Ubuntu versions.
[/LIST][LIST]
Even though I thought I was careful, I somehow wrote to the boot sector of only one disk (out of two). This broke the array.
[/LIST][LIST]
In the firmware configuration, I deleted the array and re-created it with what I think were the same parameters. The old partitions were not detected.
[/LIST][LIST] 
After I booted from LiveUSB and installed dmraid, Testdisk was able to detect the old partition table, so I let it write the table to the disk.
[/LIST][LIST]
Upon rebooting, BIOS froze every time it attempted to detect the drive. I had to physically unplug it (actually only one of the two drives) before I could even enter the BIOS menu and disable RAID.
[/LIST][LIST]
With the disks in disarray, I booted the LiveUSB and ran Testdisk on them separately. One contains garbage in the partition table, but the other seems to have a complete partition table for the entire array (twice as big as the individual disk).
[/LIST]

As far as I can tell, only the boot sectors of the disks are corrupted, so I should be able to recover all the data if I can just restore that part. I think I want to backup the partition table from the single disk that has it, wipe both disks' boot sectors so they won't freeze the BIOS, recreate the array, and restore the partition table from the backup. How can I manually edit the boot sector like this? And before I do any more damage, does this plan even make sense?

Once this is fixed, maybe I'll stop using RAID 0. But I want my data back first.

---

