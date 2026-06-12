---
title: "Problem about mounting the disk"
date: 2015-06-10
forum: Hardware
---

### Post by jake65 on 2015-06-10
Hi all,

I've encountered a problem about mounting the disk. I have a disk of volumn 1T whereas it cannot be mounted.
What is even worse, when typing ```
sudo lsblk -f sdb
``` I got:
```

NAME FSTYPE LABEL MOUNTPOINT
sdb               

```
Since not FTYPE is shown, when I try to mount it to some point, it won't work in any case.

Does anyone has an idea about this?
I appreciate any help!

Best,
Jake

---

### Post by Bashing-om on 2015-06-10
jake65; Hi ! Welcome to the forum .

1st thing that pops too mind is to inquire what is the file system(s) on the target hard drive ?
Then We would want to know if 'fdisk' sees the partitions:
```

sudo fdisk -lu

```
In the event the hard drive is in GPT partitioning then we 'look' at the drive with a different tool:
```

sudo part -l 

```

[INDENT][INDENT]with this info
[INDENT][INDENT][INDENT]we can start getting somewhere
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-06-10
Is this drive partitioned at all, or is it just a brand new, off-the-shelf disk with not even a partition table on it yet?

---

