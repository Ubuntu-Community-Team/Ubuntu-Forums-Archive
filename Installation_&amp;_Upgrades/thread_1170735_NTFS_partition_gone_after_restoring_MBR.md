---
title: "NTFS partition gone after restoring MBR"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by The_Bash on 2009-05-26
To make a dual boot (ubuntu/windows) I repartitioned my drive using a live CD. I followed [this]("https://help.ubuntu.com/community/WindowsDualBoot#Issues%20with%20Windows%20XP%20and%20NTFS") (click to open) guide. After installing Windows, I rebooted with the live CD and restored my MBR (which I backed up earlier) with the 'dd' command. Then I wanted to add Windows to my Grub but to my surprise, my windows (NTFS) partition is gone. In gparted there is only 1 main drive which is the full size of my disk. The partition I created and installed Windows on appears to be gone. I didn't remove it, so I'm guessing Gparted is wrong. Any tips on how to solve this?

---

### Post by ronparent on 2009-05-26
This is totally puzzling. The only thing I can think of is that in attepting to restore the mbr you may have also restored the original partition table? I wouldn't think this was possible. If this were the case you would have effectively wiped out the new windows partition.

I would suggest that if you install windows again that you simply use the grub commands find **/boot/grub/stage1**, **root (hd0,0)** (or whatever your output from the prior command is) and **setup (hd0)**. That in itself would restore grub to the mbr. Then you could gedit menu.lst to add your windows installation. Good luck.

---

### Post by coffeecat on 2009-05-26
> **ronparent said:**
> This is totally puzzling. The only thing I can think of is that in attepting to restore the mbr you may have also restored the original partition table? I wouldn't think this was possible.

Unfortunately, I believe this is eminently possible or at least something like it. The partition table occupies the area on the hard disk immediately after the mbr, so a mistake in the dd command wouldn't restore the original partition table, but it looks as though it has rewritten the partition table from somewhere.

**The_Bash**, can you post the exact dd command you used?

**Edit:** [Wikipedia article about mbr/partition table](http://en.wikipedia.org/wiki/Master_boot_record). The two together only occupy 512 bytes, so if that dd command copied 512 bytes, that's the partition table overwritten.

---

### Post by The_Bash on 2009-05-27
I used this command to backup my MBR:
```
sudo dd if=/dev/hda of=/mbr.bin bs=512 count=1
```

Then I used this command to restore the MBR:
```
sudo dd if=/disk/hda/mbr.bin of=/dev/hda bs=512 count=1
```
(At least this should have been the command, but since I used it with the Live CD I can't find it back. So I'm not sure if it was a type-o)
I had to replace 'hda' with 'drive' because the partition was called that way after I mounted it in the Live CD.

//edit

I discovered that the NTFS partition should still be around. The size of my disk is now 49.8 GB. My disk has a capacity of 100GB. This is compliant with the way I partitioned the disk. I resized it to 50GB ext3 and 45GB ntfs. Now I have to find a way to 'unhide' my NTFS partition.

---

