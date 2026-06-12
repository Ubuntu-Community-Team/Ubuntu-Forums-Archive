---
title: "badblock / fsck error"
date: 2011-11-01
forum: Hardware
---

### Post by avix on 2011-11-01
I was running a surface test on one of my hard drives to see if it had bad sectors. I used bad-blocks

badblocks /dev/sdb1 > bad-blocks

then

fsck -t ext3 -l bad-blocks /dev/sdb1

what I ended up with was

Bad block 428607843 out of range; ignored.
Bad block 428629656 out of range; ignored.
(about 100 entries in the 4283****** and 6 in the 4286**** range)
Storage_2: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

Storage_2: ***** FILE SYSTEM WAS MODIFIED *****
Storage_2: 11/30531584 files (0.0% non-contiguous), 1966902/122096384 blocks
root@tux:~# 

is this ok now? I've done it 3 times and it still keeps kicking out the same error

I am confused.

---

### Post by ohnonot on 2012-11-03
i'm having the exact same problem right now.

websearches brought only [this]("http://www.linuxquestions.org/questions/linux-general-1/raid-disk-problem-attempt-to-read-block-from-filesystem-resulted-in-short-read-562434/"), basically.

i wouldn't want to through the drive away or buy a new one, if i can avoid it.

all help appreciated.

d.

---

### Post by avix on 2012-11-03
I have found this disk-utility to be my go to tool for testing hard drives. most drive manufactures also make diagnostic/testing software.


[http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

---

