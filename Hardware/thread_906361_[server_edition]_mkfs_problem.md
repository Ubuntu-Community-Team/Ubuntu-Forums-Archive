---
title: "[server edition] mkfs problem"
date: 2008-08-31
forum: Hardware
---

### Post by herrbrand on 2008-08-31
hello

I made A partition as big as the hard drive. type is extended. when i try to format it with mkfs i get an message:
```

inodes_size(128) * inides_count(0) too big for a filesystem with 0 blocks, specify higher inode_radio (-i) or lower inode count (-N)

```
what i the best selution? when i look whit fdisk to the partion it say that it has 20008926 blocks.

* I am sorry for my bad english *

Robbert

---

### Post by GepettoBR on 2008-08-31
If you made only one partition in the entire drive, why make it extended?

Extended partitions aren't used themselves fo storing data, but for storing other partitions, called "logical partitions". If you only intend to have one partition, use a primary partition. That can be formatted normally.

---

### Post by herrbrand on 2008-08-31
hello

I have two hard drives in the pc. on the first hard drive runs the operating system. and i want to store website ftp files and suff on the second drive.

if i inderstand you right, then I cant use an extended drive for storing data and stuf? so i have to remove the partition and make an primary patition?

Robbert

---

### Post by herrbrand on 2008-08-31
i made an primary partition and it works now.

---

### Post by mrsteveman1 on 2008-08-31
An extended partition actually has no blocks in it to store things, but you can make logical partitions in the extended partition.

There's no reason to do that though if there is only one partition.

The extended partition just has another partition table since the main one at the start of the drive is too small for more than 4 partition entries.

---

