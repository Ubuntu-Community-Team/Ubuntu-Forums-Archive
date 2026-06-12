---
title: "Superblock doesn't exist?!"
date: 2009-04-19
forum: Hardware
---

### Post by murphy on 2009-04-19
Hi

i need your help. Some days ago i've put my hardware into a new tower. I started the pc, ubuntu started loading but stoped. I can't say why because my monitor says "signal out of range" during the startup.

So i used a live cd and started gparted. I have three partitions, one is the swap. Except this one all others have a small warning sign.

```
sudo fsck.ext3 -v -f /dev/sda1
fsck.ext3: No such file or directory while trying to open /dev/sda1

SuperBlock is not readable...
e2fsck -b 8193 <device>
```

So i tried to use testdisk. All partitions were found and no errors occured. I can even see all my files! TestDisk listed all super block backups and i tried to use them with the e2fsck command but it doesn't work.

Can anybody help me with that?

---

### Post by murphy on 2009-04-19
Now i have tried dd_rescue but it doesn't work
```

dd_rescue /dev/sda1 /mnt/image.dat
/dev/sda1 no such file or directory

```

Anybody got an idea?

---

