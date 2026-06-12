---
title: "[SOLVED] How to zero-fill unused space in a partition"
date: 2008-08-22
forum: General Help
---

### Post by mujambee on 2008-08-22
I need to fill with zeros all free space in a partition, without loosing data on it.

I don't mind secure file shreding or whatever, it is just that I want to dump the whole partition on a file and then compress that file. If free space is full of old data that will compress far less than a huge lot of zero.


I intend on doing it periodically, so the faster the method, the better for me.

Thanks...

---

### Post by az on 2008-08-22
> **mujambee said:**
> I need to fill with zeros all free space in a partition, without loosing data on it.

I don't mind secure file shreding or whatever, it is just that I want to dump the whole partition on a file and then compress that file. If free space is full of old data that will compress far less than a huge lot of zero.


I intend on doing it periodically, so the faster the method, the better for me.

Thanks...
That's not the most elegant way to back up your system but whatever.

mount the partition
cd into it and run:
touch file
dd if=/dev/zero of=file
let it run out of space and then 
rm file

If you are running ext3, you will still have the 5 per cent allocated to root that will not be touched, but you can decrease that using tune2fs.

---

### Post by fyo on 2008-08-22
I suggest adding specific parameters to dd. Since you are zeroing just for compression, it doesn't have to be EXACT. So just check free space and do:

```
dd if=/dev/zero of=outputfile bs=1024K count=1024
```

bs is blocksize. Since you are writing A LOT of data, this is an important parameter. Default is 512 BYTES. That's very low and on my system I achieve speed gains of 5-10x by using 1024K (that is, 1MB). count is the number of blocks to write.

If you want to automate the process, you could write a quick script to grep the amount of free space and use that appropriately.

Using dd like this is a quick and dirty way of achieving your goal. A more thorough method would involve acting on /dev/sdaX directly, but I'm unaware of a program that does that automatically.

---

### Post by mujambee on 2008-08-23
> **az said:**
> That's not the most elegant way to back up your system but whatever.


I know, I know, but it is a quick and dirty for a pendrive.

Thanks a lot to both of you...

---

