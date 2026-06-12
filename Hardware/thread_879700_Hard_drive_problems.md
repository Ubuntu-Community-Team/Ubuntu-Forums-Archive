---
title: "Hard drive problems"
date: 2008-08-04
forum: Hardware
---

### Post by mpgarate on 2008-08-04
one of my ext3 partitions gave an error during the normal check, and does not mount automatically. I can mount it, but then it says the device is full. what should I run to repair this, or retry the scan while the os is running?

---

### Post by cdtech on 2008-08-04
What partition is it?

Can you show the output of the command:
```
df -H
```

Sounds like you need to clean out some data maybe.

---

### Post by sayad on 2008-08-04
Try teh Powerquest partition magic to make partitions.this is teh only softwrae i have seen that gives me totral partition protection.Then you have to use teh xp cd for the repair of teh hard disk.Thsi is important

---

### Post by mpgarate on 2008-08-05
running df -H also says that the disk is full, but in windows it says I have over 6GB free. Also I have just deleted over 1 GB of data from ubuntu and df -H still shows 0 free on the disk

---

### Post by mc4man on 2008-08-05
How are you deleting in that partition ? (shift+delete, delete, or move to trash)
Enable 'show hidden files' and look for a .trash or go file -> empty trash

---

### Post by mpgarate on 2008-08-05
I pressed delete, emptied trash, viewed hidden folders, and deleted the only one which was named .trash-1000, it still says 0 bytes free.

I just ran


sudo fsck -t ext2 /dev/sda3

after unmounting it, I remounted and the problem is still there.

---

### Post by mc4man on 2008-08-05
with it mounted try df -i

---

### Post by mpgarate on 2008-08-09
in windows I deleted several gig of data, and now it works in ubuntu again. still, ubuntu registered 0 bytes free when there was over 6gb free. not so good

---

