---
title: "Issues copying large files to external HD via USB"
date: 2010-12-03
forum: Hardware
---

### Post by earlycj5 on 2010-12-03
Hi all,
I've got a strange problem.

I'm trying to copy large files, >1gb, to my external EXT4 hard drive via USB.

I can move smaller files with no problems, but it seems to choke on large files giving me this error.

```

cp: writing `/media/blah/blah': Read-only file system large files

```

I know it's not read only.  My login has read/write permissions on it and I confirmed that I was able to move smaller files, ~2 to 20mb in size to this disk.

---

### Post by earlycj5 on 2010-12-05
Anyone have any ideas?

I've found out that I can rip DVDs directly to it, writing the file to the disk, but still cannot copy these types of files from my internal HD to the external drive.

---

### Post by DaithiF on 2010-12-05
most likely there are some errors on the disk, when this happens linux will remount the drive as read-only to avoid causing further damage to an already damaged filesystem.

assuming this is a fat or ntfs (ie. windows filesystem), then try run some disk check / repairs in windows.

or you can try running fsck on the drive from linux.

one other possibility -- fat(32) has a 4gb filesize limit -- are your files larger than this?  I don't think this would cause a readonly-remount so I suspect its the first suggestion, but worth a mention just in case.

---

### Post by earlycj5 on 2010-12-05
> **earlycj5 said:**
> Hi all,
I've got a strange problem.

I'm trying to copy large files, >1gb, to my external ***EXT4*** hard drive via USB.


> **DaithiF said:**
> 

assuming this is a fat or ntfs (ie. windows filesystem), then try run some disk check / repairs in windows.


Not that I don't appreciate the advice, but I'm assuming you didn't read my post either...

---

### Post by DaithiF on 2010-12-05
sorry, i missed that (obviously!)

still, the problem remains the same ... filesystem errors causing the filesystem to be remounted as readonly.  if you check dmesg or /var/log/messages when it happens you'll see some errors occurring.  try fsck'ing the (unmounted) drive partition to identify / repair the errors.

---

### Post by earlycj5 on 2010-12-05
> **DaithiF said:**
> sorry, i missed that (obviously!)

still, the problem remains the same ... filesystem errors causing the filesystem to be remounted as readonly.  if you check dmesg or /var/log/messages when it happens you'll see some errors occurring.  try fsck'ing the (unmounted) drive partition to identify / repair the errors.

fsck.ext4 returns this:

```

disklabel: clean, 27575/30531584 files, 49336535/122096000 blocks

```

I suspect you're onto something, I'll check the log files to see what I can find.

---

