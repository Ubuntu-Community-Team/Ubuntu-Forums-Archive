---
title: "Sharing a Fat32 partition with installed games and programs?"
date: 2005-11-04
forum: General Help
---

### Post by Effect on 2005-11-04
Been wondering. Is this the best way to use a program like Wine or whatever is used to play games in Linux (the thing Transgaming sells)? Install said programs and games on the Fat32 partition and run them from there while in Windows and again from Linux with Wine or something else?

Will this cause the drive to be corrupted by doing this? If I save something from in Linux will I be able to see those files while in Windows and just not open them or will the not show at all? While in Windows I know the drive Linux is installed on doesn't show at all so wanted to be sure.

Or does the partition have to be something else other then Fat32? Would using a program like Partition Manager work to convert an already setup drive with programs or should I do a clean format? Thanks.

---

### Post by RAOF on 2005-11-04
Anything you save onto a FAT32 partition will be readable by both windows & linux (and, I believe, Mac OSX, if you're that way inclined :)).  The reason why windows can't see your linux partition is that windows doesn't recognise anything but windows-formatted-partitions (NTFS or FAT12/16/32).  Linux can read/write to practiacally every partition-format (but it can't write to NTFS).  Anything you want to share between windows & linux will have to be on a FAT32 partition.

Re: running games in linux.  Why would you bother, if you've got a windows install?  True, there's a certain amount of geek-cred to be gained, but games just work(tm) in windows.  They're designed to.  You don't need to mess around with trying to provide windows APIs on linux.

---

