---
title: "FAT32 files created in linux disappear"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by weizilla on 2006-03-25
I have a Fat32 partition mounted in linux. I would write files to the partition by setting it as the default directory for Gaim. However, after booting back into windows and then into linux a few times, the files would no longer be there in linux. I have changed my fstab entry since then but if i remember correctly, the mount options were:
rw,auto,iocharset=utf8,uid=1000,gid=1000,umask=0007
I also downloaded a 20mb mp3 song into one of the directories but windows ran a chkdsk on the drive and said that the file had invalid size.

I ultimatly want to be able to share my thunderbird e-mail profile between windows and linux but i am hesitant because of these hard drive problems.

Has anyone else encountered this problem as well or can provide help?

also, would someone be able to provide their fstab info for a fat32 partition where they know that they have the correct mounting options that's tested and never had problems?

---

### Post by gerbman on 2006-03-26
[QUOTE=weizilla]also, would someone be able to provide their fstab info for a fat32 partition where they know that they have the correct mounting options that's tested and never had problems?[/QUOTE]
I have a second hard drive formatted as a single FAT32 partition. The following is the entry in my fstab for this drive:```
/dev/hdb1       /mnt/hd2        vfat    defaults,uid=gerb       0       0
```Where 'gerb' is my username. I can read/write this drive with no problems.

---

### Post by weizilla on 2006-03-27
i think i know what the problem was
i was using linux and something happened and it crashed or umounted before the files were written to the partition

is there any ways to prevent this? like decreasing the delay in writing to the drive or something?

---

### Post by gerbman on 2006-03-27
[QUOTE=weizilla]is there any ways to prevent this? like decreasing the delay in writing to the drive or something?[/QUOTE]
Hmmm, not that I know of. But, then again, there are a lot of things I don't know ;-) I would hope your system doesn't crash often enough to necessitate such a change, but I just lost a hard drive the other day so I really don't know what to think anymore.

Cheers!

---

### Post by weizilla on 2006-04-04
I have successfully figured out how to share files between windows and linux for thunderbird and firefox, however, for some reason, in linux, whenever i write to any of the files, windows thinks they're corrupted. 
like thunderbird keeps on redownload my e-mail messages because the file whichs keeps track of this is corrupted and gaim keeps on forgetting my preferences for the same reason.

has anyone else have this problem?

---

