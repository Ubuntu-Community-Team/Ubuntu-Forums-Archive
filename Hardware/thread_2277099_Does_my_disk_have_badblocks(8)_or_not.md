---
title: "Does my disk have badblocks(8) or not?"
date: 2015-05-06
forum: Hardware
---

### Post by azzamite on 2015-05-06
The authors of the badblocks(8) tool forgot to mention in the man page what their output means

```
LANG=c sudo fsck.ext4 /dev/sdc1 -c
e2fsck 1.42.12 (29-Aug-2014)
Checking for bad blocks (read-only test):   0.05% done, 10:04 elapsed. (74/0/0 errors)
```

So... what does 74/0/0 means?

Should I start to worry about it?

---

### Post by SeijiSensei on 2015-05-06
[http://unix.stackexchange.com/questions/65349/how-to-interpret-badblocks-output](http://unix.stackexchange.com/questions/65349/how-to-interpret-badblocks-output)

Yes. The 74 represents read errors.  The numbers are read errors/write errors/compare errors.  However if you format the drive with fsck -c then the formatter will mark those blocks unusable.  If there aren't many of them, the rest of the partition should be fine.

I ran a test on one of my unmounted partitions and got
```
$ sudo badblocks -sv /dev/sda7 
Checking blocks 0 to 19998719
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)
```
when it was done.  You may just need to be patient and see what happens when the format completes. Expect to be waiting quite a while.  This took about five minutes for a 10GB partition.

---

### Post by azzamite on 2015-05-06
> **SeijiSensei said:**
> [http://unix.stackexchange.com/questions/65349/how-to-interpret-badblocks-output](http://unix.stackexchange.com/questions/65349/how-to-interpret-badblocks-output)

Yes. The 74 represents read errors/write errors/compare errors...

Thanks, that's what I was fearing... my disk fell from 2m high, I'll be surprised if it's not mostly useless after that :(

---

