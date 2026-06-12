---
title: "sudden software raid corruption"
date: 2008-09-22
forum: General Help
---

### Post by RSaldo on 2008-09-22
I have two systems, both with AMD Athlon(tm) 64 X2 Dual Cores, both run 6.06 lts (kernels  2.6.15-28-k7 #1 SMP PREEMPT  and 2.6.15-51-k7 #1 SMP PREEMPT)
Both has a raid5 devices on them.
One consists of 5 320g sata discs (effectively 1200g) the other 5x1Tb usb (effectively 4Tb). Both used to have ext3 fs's on them.
After running for some time now both systems started to show signs of severe corruption.
var/log/messages is full of strange stuff, mostly relating to filesystem corruption, but also i/o failure (on a raid device!).
I then cleared the devices and put reiserfs on instead of ext3.
Same problem, now I get a lot of this:



[I][17181474.344000] ReiserFS: warning: is_leaf: item location seems wrong (second one): *3.6* [821952 824369 0x0 SD], item_len 12, item_location 1152, free_space(entry_count) 65501
[17181474.344000] ReiserFS: md0: warning: vs-5150: search_by_key: invalid format found in block 17695348. Fsck?
[17181474.344000] ReiserFS: md0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [821984 824362 0x0 SD]
[17181474.344000] ReiserFS: warning: is_leaf: item location seems wrong (second one): *3.6* [821952 824369 0x0 SD], item_len 12, item_location 1152, free_space(entry_count) 65501
[17181474.344000] ReiserFS: md0: warning: vs-5150: search_by_key: invalid format found in block 17695348. Fsck?
[17181474.344000] ReiserFS: md0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [821984 824363 0x0 SD]
[17181474.344000] ReiserFS: warning: is_leaf: item location seems wrong (second one): *3.6* [821952 824369 0x0 SD], item_len 12, item_location 1152, free_space(entry_count) 65501
[17181474.344000] ReiserFS: md0: warning: vs-5150: search_by_key: invalid format found in block 17695348. Fsck?
[17181474.344000] ReiserFS: md0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [821984 824364 0x0 SD]
[17181474.344000] ReiserFS: warning: is_leaf: item location seems wrong (second one): *3.6* [821952 824369 0x0 SD], item_len 12, item_location 1152, free_space(entry_count) 65501
[17181474.344000] ReiserFS: md0: warning: vs-5150: search_by_key: invalid format found in block 17695348. Fsck?
[17181474.344000] ReiserFS: md0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [821984 824365 0x0 SD]
[17181474.344000] ReiserFS: warning: is_leaf: item location seems wrong (second one): *3.6* [821952 824369 0x0 SD], item_len 12, item_location 1152, free_space(entry_count) 65501
[17181474.344000] ReiserFS: md0: warning: vs-5150: search_by_key: invalid format found in block 17695348. Fsck?
[17181474.344000] ReiserFS: md0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [821984 824366 0x0 SD]
[17181474.344000] ReiserFS: warning: is_leaf: item location seems wrong (second one): *3.6* [821952 824369 0x0 SD], item_len 12, item_location 1152, free_space(entry_count) 65501
[17181474.344000] ReiserFS: md0: warning: vs-5150: search_by_key: invalid format found in block 17695348. Fsck?
[17181474.344000] ReiserFS: md0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [821984 824367 0x0 SD]
[17181474.344000] ReiserFS: warning: is_leaf: item location seems wrong (second one): *3.6* [821952 824369 0x0 SD], item_len 12, item_location 1152, free_space(entry_count) 65501
[17181474.344000] ReiserFS: md0: warning: vs-5150: search_by_key: invalid format found in block 17695348. Fsck?
[17181474.344000] ReiserFS: md0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [821984 824368 0x0 SD]
[17181474.344000] ReiserFS: warning: is_leaf: item location seems wrong (second one): *3.6* [821952 824369 0x0 SD], item_len 12, item_location 1152, free_space(entry_count) 65501
[17181474.344000] ReiserFS: md0: warning: vs-5150: search_by_key: invalid format found in block 17695348. Fsck?
[17181474.344000] ReiserFS: md0: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [821984 824369 0x0 SD]
[/I]

Somehow the software raid cr*ps out on the 6.06 lts and AMD64bit cpu's

The short question is: "does anyone know of any raid bugs fixed that might rid me from this problem?"

---

### Post by fjgaude on 2008-09-22
Well, I can't say what might be the problem here except the motherboard, the controllers for the drives.

The **md** in the kernels have been getting better and better with each release. And the **mdadm** program, now at 2.6.3, is up to 2.6.7 in beta. What version of mdadm are you using?

---

### Post by RSaldo on 2008-09-23
The one that ships with 6.06LTS 
mdadm - v1.12.0 - 14 June 2005
but mdadm is just for tuning, not for running, or am I mistaken?
Everybody shouts 'hardware' all the time, it almost never is.
an I/O error should not occur on a md device with all UUUUU's.

---

### Post by fjgaude on 2008-09-23
Yes, **mdadm** is just for management, but it follows **md** in the kernel builds.

From what little I know it is hardware, the motherboard or controller. One other thing is the size of the arrays... when 6.06 came out those sizes were unheard of because drives were so small compared to now.

Wish I had more advice... but try:

```
sudo fdisk -l
```

That might give a clue as to the drive condition.

And use can run **fsck** on each array and see what it says.

---

### Post by RSaldo on 2008-09-23
I have installed 64bit 8.04lts server on one of the machines (mdadm v2.6.3 - 20th August 2007) and will run some tests.
Anyway, now I get some ext2 problems on an external usb drive.
I dont know what to make of it.
Could be left overs from the 606 system.

---

### Post by fjgaude on 2008-09-23
Have you run tests on the drives, arrays yet?

```
sudo fsck.reiserfs /dev/md[n]
```

Of course have the array unmounted.

---

