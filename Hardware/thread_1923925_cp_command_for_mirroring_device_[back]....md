---
title: "cp command for mirroring device [back]..."
date: 2012-02-11
forum: Hardware
---

### Post by Moozillaaa on 2012-02-11
Only an expert will understand this one...

I do weekly backups with a script that clones my entire partition, using the cp command.

Now, I need to restore my partition from the backup. But I see that when I did the first backup last year, I did the cp command TO a spare partition, that was LARGER than my 'home' partition.

Can I do the cp 'back' to the original partition? Are the larger partitions' boundaries re-defined, since the origin partition is smaller?

---

### Post by ahallubuntu on 2012-02-11
I don't know what's actually in your "mirroring script," but the "cp" command doesn't care about partitions, it cares only about files.  

So if your original partition was 100GB of which only 20GB were used, and you copied that 20GB worth of files to a spare (mirror) partition that had only 30GB of space, you'd still have only 20GB worth of files.  If you need to copy them back, you still copy only 20GB.  The fact that the original was 100GB total size or the mirror was only 30GB total size is not important.

...unless you are using something else besides the "cp" command in that script?  ("rsync" is a far better choice than cp for file backup by the way).

---

### Post by Moozillaaa on 2012-02-11
I don't think you are completely correct there, ahallubuntu...> but the "cp" command doesn't care about partitions, it cares only about files

This syntax DOES have partition size dependencies of a sort, in addition to file contents [dependencies].

It copies 3 partitions, on device a, **in their entirety**, to device d. If device d is a RAW drive without filesystem formatting, [B]it will create the partitions and the filesystem.
[/B]
The syntax below copies files, AND creates partitions. With my current partition configuration, the cp line in the script is:

***cp  /dev/sda  /dev/sdd***

...................

Now ...

since my partition sd[SIZE=3]**a**[/SIZE]2 is smaller than my ORIGINAL partition sd[SIZE=3]**d**[/SIZE]2, the question now is, did the first cp task redefine the partition boundary, of sdd2.

If it did, I SHOULD be able to now reverse the syntax, to restore my sda2, from sdd2.

Anybody?

---

### Post by ahallubuntu on 2012-02-11
I've never tried doing a device to device copy like that since it seems so inefficient.  If you really need to copy the whole partition (not just files), use dd instead and copy the whole partition to a FILE on another partition.  Like this:

dd if=/dev/sda of=/some/other/filesystem/notsda/backupsda.img 

Then you'll wind up with a huge file "backupsda.img" that you can also compress:


bzip2 backupsda.img 
#this will take a long time, though - gzip is faster but won't make file as small).

If you need to restore it to sda someday, do this:

bzip2 -d backupsda.img | dd of=/dev/sda

That way, you really don't care at all about the size of the other partition, since you are saving it to a FILE not a partition.

If you want to backup just files, use rsync, which will copy only the changes since last the last copy (great for incremental backup too).  But rsync isn't a good solution for backing up working file systems - great for data though.

If you really want to do these direct device partition to partition copies (never even tried it myself, surprised that even works), then you need to make sure the partition sizes are the same ahead of time - or use Gparted later to resize partitions before doing the cp back if need be.

---

### Post by Moozillaaa on 2012-02-12
Sounds great - I'll keep it in mind in the future.

In the meantime, I just need to know about copying back TO the partition in need of restore function. No problem if you didn't know that cp is used for partition mirroring too...

>>>>>>>>>>>>>>>>>>>>>>>>>>

Anybody know if partition boundaries are re-defined by device/partition copy task?

---

### Post by savanna on 2012-02-12
Yes, you can copy them back - cp only works with files.

You're probably better off using rsync to do backups like this - it'll be faster as it only copies the changes, not every file.

---

### Post by Moozillaaa on 2012-02-12
> **savanna said:**
> Yes, you can copy them back - cp only works with files.


2nd ed.: There's a rule in this forum against malicious commands. It probably applies to your ignorant commands too, **which could cause the SAME damage as a malicious command** (incidentally, what will the syntax be for my task huh???). I already know better about blindly doing this task.

Trying to help is NO EXCUSE. You could have caused serious damage by your ignorance.

....................

Thanks. You've demonstrated willful ignorance - you're wrong, and you didn't attempt to inform yourself either.

Try reading the posts. See that I informed the other poster, who made the same mistake that you did. 

ed.: even my thread title implies by itself that you're wrong. It SHOULD have made you read the posts...

======================

Does anybody know if partition boundaries are re-defined by cp write task?

---

### Post by matt_symes on 2012-02-12
Hi

EDIT:I had to re-read your question.

> since my partition sda2 is smaller than my ORIGINAL partition sdd2, the question now is, did the first cp task redefine the partition boundary, of sdd2.

It should have overwritten the partition table of sdd using the partition table from sda.

> Does anybody know if partition boundaries are re-defined by cp write task? 

I'm pretty sure; no. It copies the partition table and files (amongst other things). If i remember correctly, a device level cp works in pretty much the same way as dd. Therefore the backup device should have a partition table the same as sda.

Assuming your revert command would be 

```
cp /dev/sdd /dev/sda
```

then it should copy the partition table back and the files, overwriting what was in the partition table of sda.

Take a look at the partition table in the backup (/dev/sdd) using fdisk if you can. Compare it to sda.

Try it out on a spare drive if unsure.

Please don't be rude to others trying to help you. It reflects badly on you and not them.

Kind regards

---

### Post by Moozillaaa on 2012-02-12
Thanks! That's VERY good information... 

My 'revert' command will be cp  /dev/sdd2  /dev/sda2. Does this make a difference in your answer here? Thanks again...

..........

I edited my previous post to make a point about malicious commands and ignorant commands. 

Even if someone is trying to help, it makes no difference to someone who might have just wiped out 2 partitions, instead of just 1 partition. Conceivably, if this cp task did NOT work as you say, it could do exactly that - wipe out 2 partitions.

---

