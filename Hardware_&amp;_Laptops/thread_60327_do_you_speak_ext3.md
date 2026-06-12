---
title: "do you speak ext3?"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by phen on 2005-08-27
My Harddisk crashes approx. once in a week. It usually happens like this: Programs crash (because they can't to the harddisk anymore), i allready know the error and check dmesg. nothing. more and more programs crash. after a minute the os sets my root partition to read-only, and i can run fsck again. I will have to fix hundreds of inodes, blocks etc. thereafter, the system works for 4 days.


today it was the first time that i was able to see the actual error message:
```

ext3-fs error(device hda4) ext3_readdir: bad entry in directory #2376419: rec_len is smaller than minimal -offset=0, inode 3671 rec_len=0, name_len=0

set filesystem read only

```

i am wondering what this could mean? does anyone of you understand this error? can i throw my harddisk away? (reformatting, repartitioning didn't help, it happens usually after rebooting from winxp into ubuntu)

thanks for your help!

kai

---

### Post by stepper on 2005-08-27
Same thing happened to me, I deleted all partitions  and re-partioned accordingly on my 80 GB Samsung HDD. Also got the [Ultimate Boot CD](http://www.ultimatebootcd.com/) and used the filesystem tools to analyse the partions for bad blocks.

---

