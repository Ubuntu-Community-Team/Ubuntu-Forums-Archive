---
title: "modifying partition size; booting windows"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by gbttun on 2009-07-04
I've added Jaunty onto my Vista laptop. However, there's not enough space in the directory to DL anything else (couldn't do upgrades). I previously had Drake in a partition, but deleted it. My HD is partitioned like so:
[LIST]
[*]/dev/sda1                       nfts                  50.56GiB
[*]unallocated                     unallocated        12.96GiB
[*]/dev/sda4*                     extended          2.96GiB
[LIST]
[*]/dev/sda6             ext3                 2.33GiB
[*]/dev/sda7*           linux-swap         172.54MiB
[*]/dev/sda5*           linux-swap         478.47MiB
[/LIST]
[*]/dev/sda2                       nfts-presario      8.04GiB
[/LIST]the * represent the ones with key pictures next to the entry. I'm pretty sure that I shouldn't touch sda1 and sda2. I think sda6 (ext 3) is the directory on which Jaunty is currently running. GParted won't let me resize sda4, and I can only resize sda6 within limits presented by sda4. Is it advisable to delete sda4 and create a new partition within the unallocated space? also, how many linux-swap partitions do I really need?
 
Another issue I have is that I'm unable to boot Vista properly. From GRUB, I see two options to boot Windows--one runs an eternal 'vista is loading' window, the other a blue screen. I once put a bunch of files supposedly involved with startup on an ext. HD, but I've been able to start up Vista since then. Please advise.
 
Thank you in advance. :]

---

### Post by merlinus on 2009-07-04
If you do not have data that cannot be backed up within ubuntu, then it might be wise to reinstall.  You can use gparted from the live cd to delete all but sda1 and sda2, create a new extended partition, and then logical partitions within that for 9.04 / and swap.

This might also solve the windows booting problem as well.

---

### Post by Jonie on 2009-07-04
The other option that gives blue screen is valid, sadly it also means, that the ntfs is corrupted. It could have had some incosistencies before shirinking, it might have been moved on the disk - then the ntfs boot sector has to be updated to resolve the problem.

If your laptop didn't ship with a dvd recovery disk, you may try to donwload vista recovery iso (it's about 120 MB). Just google for it. Run filesystem check from there. If it still doesn't boot into vista afterwards, then repair of the ntfs boot sector is worth a try.

[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Download the system rescue cd:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Ubuntu live cd doesn't contain testdisk, it's still a wish feature.

Then I hope vista boots again and you may try to delete the logical volumes, then the extended partition, leaving the ntfs volumes. I recommend to do it so, because after shrinking you've got free space before the extended partition, there will be a lot of moving and resizing to be done. Reinstall ubuntu then. Or if you like, grow the extended parition to the beginning of free space, then you could be able to resize and move the logical volumes - without reinstall.

---

