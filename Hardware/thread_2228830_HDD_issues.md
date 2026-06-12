---
title: "HDD issues"
date: 2014-06-09
forum: Hardware
---

### Post by oO Flowzilla Oo on 2014-06-09
Hello people. I have an Acer Aspire 5315 and a Toshiba 500GB HDD with Ubuntu 13.04 (I believe) installed on it. This problem started a few day's ago and I've yet to solve it. When Ubuntu boots, it takes me to this purple GRUB 2.0 screen and afterwards a command window-type of message tells me that there are kernel issues. This is like the fourth time that this issue has happened to me, the other times I had to wipe out the HDD which made me lose a lot of important data. I don't know why this happens as it's completely random, I didn't install any suspicious software or anything. I'm not interested in having Ubuntu installed on this HDD anymore and would like to use it as an external HDD for storage, what it was before I installed Ubuntu on it. 

The issue with this is that the Ubuntu-side of the HDD won't show up on Windows 7, even with ext2/3/4 readers installed. I can see only see 242 MB of storage, and without the readers, which is a very small number compared to 450+ GB. I would appreciate a response. Cheers.

---

### Post by Bashing-om on 2014-06-09
oO Flowzilla Oo; HoKay;

1. Is the hard drive helathy ? what is the SMART status from 'disk utility' in ubuntu ?
2. From the liveDVD/USB environment, what does GParted relate about the hard drive ?
3. From the liveDVD/USB environment, what returns from terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
4. From the liveDVD/USB what returns from a file system check ?
#From liveDVD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```

If all returns positive, hey
[INDENT][INDENT][INDENT][INDENT]there should be no problem
[/INDENT][/INDENT][/INDENT][/INDENT]

---

